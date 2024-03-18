# Nginx基础

> Author: Sylvie233
>
> Date: 23/1/1
>
> Point：尚硅谷Nginx教程P125

[TOC]

## 基础介绍

Nginx版本：

- Nginx开源版
- Nginx plus 商业版
- Openresty
- Tengine



安装目录:

```
dir:
	/conf:
		mime.types:
		nginx.conf: 主配置文件
	/html: 静态文件目录
		index.html: 主页面
		50x.html: 50x错误页面
	/logs: 日志目录
		access.log:
		error.log:
		nginx.pid: 主进程pid
	/sbin:
		nginx: 可执行文件
	
```



Master进程、Worker子进程

多进程结构











### nginx

```
nginx: 启动
	-c: 指定配置文件
	-s:
		quit: 优雅关闭
		reload: 重新加载配置
		stop: 快速关闭
	-V:
```





### keepalived

```
keepalived:
	
	
```



配置文件：

```

global_defs {
	router_id ib111
}

vrrp_instance 实例名 {
	state MASTER 			# 状态：MASTER、BACKUP、
	interface ens33
	virtual_router_id 51
	priority 100
	advert_int 1
	authentication {
		auth_type PASS
		auth_pass 1111
	}
	virtual_ipaddress { # 虚拟的结果ip
		_ip1
		_ip2
		_ip3
	}
}
```



### openssl

```
openssl:
	
```

证书下载：

`xxx.key`和`xxx.pem`文件



### rsync

```
rsync:
	-a:
	-r: 同步目录
	-v:
	-z:
	--daemon: 后台运行
	--delete: 同步删除的文件
	--exclude: 排除文件
	--list-only:
	--pasword-file:
	
inotify:
	
```







## Nginx核心概念

### 反向代理

### 动静分离

### 高可用

keepalived、vip虚拟ip



### 数据缓存

协商缓存

```
etag:
last-modified:


if-modified-since:
if-none-match:
```



强制缓存

```
expires:
cache-control: 
	public/max-age/
```





### 资源静态化

ssi指令

```html
<!--# include file="xxx.html" -->

<!--# block name="xxx" -->
<!--# endblock -->


```





### sticky模块

静态服务器的会话保持



### Geo模块

动态dns解析ip地址





### redis模块











### Openresty

nginx+luajit



配置：

```
http {
	lua_package_path "/xxx";					# lua包路径
	lua_code_cache off;
	lua_shared_dict shared_data 1m;				# 进程缓存
    server {
        location /xxx {
            content_by_lua 'lua代码';
            content_by_lua_file lua文件;
            content_by_lua_block {
            	lua代码
            }
            
            set $template_root /xxx;			# 模板目录
        }
    }
}
```



lua代码：

```
ngx:
	req:
		get_body_data():
		get_headers():
		get_method():
		get_post_args():
		http_version():
		raw_header():
		read_body():
	shared:
		shared_data:
			get():
			incr():
			set():
	say(): 输出
	

cjson:
	encode():

resty:
	lrucache:
		new():
		---lrucache实例
        get():
        set():
    mysql:
    	new():
    	--- mysql实例
    	connect():
    	query():
    	set_keepalive():
    	set_timeout():
	redis:
		new():
		---redis实例
		connect():
		get():
		set():
		set_timeouts():
	template:
        caching():
		new():
		render():
		---template实例：view
		message:
		render():
	
	
	
	
```



模板引擎：

```
{{ xxx }}

{# xxx注释 #}

{( xxx.html引入 )}

{-raw-} 不解析内容 {-raw-}

{* lua表达式 *}
{% lua代码块 %}
```













## Nginx配置

```
load_module "xxx.so";			# 加载模块动态链接库

user nobody #

worker_processes 1; # Worker子进程个数

events { # 事件驱动模块
	worker_connections 1024; #
}

http { // http模块
	include mime.types; # 引入其他配置
	default_type application/octet-stream; # 默认类型
	
	sendfile on; # linux的sendfile零拷贝
	
	keepalive_timeout 65;				# keepalive
	keepalive_disable;
	keepalive_time 1h;					# 一个tcp连接总时间
	send_timeout 60;					# 
	keepalive_requests 1000;			# 一次tcp复用请求数
	
	
	client_body_buffer_size;
	client_body_temp_path;
	client_header_buffer_size;
	client_max_body_size;
	
	
    proxy_cache_path /xxx levels=1:2 keys_zone=test_cache:100m inactive=1d max_size=10g;		#代理缓存路径
    
	
	limit_req_zone $binary_remote_addr zone=one:10m rate=1r/s;		# 请求限制
	limit_conn_zone $$binary_remote_addr zone=one:10m;				# 请求连接数限制
	
	access_log /xxx format名 buffer=32k flush=1s gzip=6;			# access日志
	log_format;												# 日志format定义
	open_log_file_cache;
	error_log /xxx.log;
	
	
	upstream xxx { # ip组别名定义，可在proxy_pass中使用xxx组
		server _ip1 weight=权重值 down backup;
		server _ip2 ;
		
		ip_hash;			# ip hash
		hash $request_uri;	# 指定hash参数
		hash $cookie_jsessionid;
		
		sticky name=route expires=6d;	# sticky模块
										# cookie: route默认key
		
		keepalive 100;					# 保留连接数
		keepalive_timeout;
		keepalive_requests;
		
		
		check_http_send "HEAD / HTTP/1.0\r\n\r\n";		# 健康检查
		check_http_expect_alive http_2xx http_3xx;
		check_interval=3000 rise=2 fall=5 timeout=1000 type=http;
		
		
	}
	
	
	server { # server模块（虚拟主机）
		listen 80;
		server_name localhost; # 主机名、域名
							   # 可使用正则
		root html; 			   # 根目录配置
		index index.html;	   # 首页配置
		access_log: xxx.log;   # access日志配置
		
		resolver 8.8.8.8;	   # dns解析
		
		
		location / { # uri路径匹配
					 # uri匹配可使用正则：~*
			root html; # 主目录位置（相对安装目录）
			index index.html index.htm;
			
			charset utf-8;
			
			proxy_http_version 1.1;
			proxy_set_header Connection "";
			proxy_set_header X-Forwarded-For $remote_addr; # 获取真实请求ip
			proxy_pass http://xxx.com  # 反向代理（与root配置冲突）
			rewrite ^/xxx$ /yyy break; # url重写
									   # break、last、redirect、permanent	
			
			proxy_cache	test_cache;		# 代理缓存	
			add_header Nginx-Cache "$upstream_cache_status";
			proxy_cache_valid 168h;		# 代理缓存过期时间
			
			proxy_cache_purge test_cache _key值; # 代理缓存清除
			proxy_cache_key $uri;		# 自定义cache key
			
			proxy_set_header Range $http_range;	# 断点续传
			proxy_cache_max_range_offset
			proxy_cache_methods
			proxy_cache_use_stale
			proxy_cache_background_update
			proxy_no_cache
			proxy_cache_bypass
			proxy_cache_lock
			proxy_cache_lock_age
			proxy_cache_minuses
			
			proxy_next_upstream error timeout;
			proxy_next_upstream_timeout 0;
			proxy_next_upstream_tries 0;
			
			valid_referers _ip地址 none;     # referer防盗链，指定ip访问
											# none、
			if ($invalid_referer) {
				return 403;
			}
			
			
			fastcgi_pass unix:/dev/shm/php-cgi.sock; # php的cgi
			fastcgi_index index.phhp;
			include fastcgi.conf;
			
			
			access_log off;					# 关闭access的日志
			expires 30d;					# 配置资源请求过期时间
			deny all;						# 静止请求
			allow all;						# 允许请求
			stub_status on;					#
			
			
			return 301 https://xxx;			# server直接重定向
			
			
			gzip on;						# 开启gzip压缩，动态压缩默认与sendfile冲突
			gzip_buffers 16 8k;
			gzip_comp_level 6;
			gzip_http_version 1.1;
			gzip_min_length 256;
			gzip_proxied any;
			gzip_vary on;
			gzip_types text/plain text/css;
			gzip_disable "MSIE xxxx";
			gzip_static on;					# gzip静态压缩模块开启
			gunzip on;						# gunzip解压模块开启
			
			
			brotli on;						# br压缩
			brotli_comp_level 6;
			brotli_static on;
			brotli_types text/plain;
			
			
			concat on;						# concat请求合并模块开启
			concat_max_files 20;
			
			
			ssi on;							# 开启ssi模块：服务器端合并文件输出，通过ssi命令
			ssi_last_modified on; 
			
			
			etag off;						# 关闭协商缓存
			if_modified_since off;
			
			
			open_file_cache max=500 inactive=60s;	# 打开文件缓存，配合sendfile使用
			open_file_cache_valid 60s;
			open_file_cache_min_uses 1;
			open_file_cache_errors on;
			
			
			
			memecached_pass 127.0.0.1:11211;	# 连接memcached服务
			set $memcached_key "$uri?$args";
			add_header X-Cache-Status HIT;
			
			
			redis2_pass 127.0.0.1:6379;
			redis2_query set _k _v;
			redis2_raw_query "xxx";
			
			
			limit_req_zone=one burst=5 nodelay;
			
			limit_rate 1k;
			limit_rate_after 1m;
			limiit_req;
			limit_conn;
			
			empty_gif;
			
			check_status;				# 健康检查
			
			 
		}
		
		location ~ \.php$ {
			root html;
			
			fastcgi_pass 127.0.0.1:9000;										# 代理到php-cgi绑定的端口
			fastcgi_pass unix:/xxx/php7.4-fpm.sock;								# 代理到解析器绑定的socket
			fastcgi_index index.php;
			fastcgi_split_path_info ^(.+\.php)(/.+)$;
			fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
			include fastcgi_params;
		}
		
		
		location /50x.html {
			root html;
		}
		error_page 500 502 503 504 /50x.html; # 错误码映射
		
		
		listen 443 ssl; 				# https连接
		ssl_certificate /xxx.crt;		# 证书
		ssl_certificate_key: /xxx.key;	# 
		
	}
}

stream { 								# stream模块
	upstream xxx {}
	server {
		listen;
		proxy_pass xxx;
	}
}

types { # 类型定义模块
	application/octet-stream exe;
	text/html html htm;
}
```



### https
![[Pasted image 20240313174914.png]]