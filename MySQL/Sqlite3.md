# Sqlite3

>Author: Sylvie233
>
>Date: 23/5/13
>
>Point: 

[TOC]

## 基础介绍

`.db`文件











### sqlite3

```
sqlite3:
	.databse:
	.exit: 退出
	.help:
	.open: 打开数据库文件
	.schema: 查看表结构（默认显示所有表结构）
	.tables:
```



### SQL语法

```
sql:
	create table:
	delete:
	drop table:
	insert into: 
	select:
	update table:
```





## 核心内容

### C接口

```
<sqlite3.h>:
	SQLITE_OK:
	sqlite3_errmsg():
	sqlite3_exec():
	sqlite3_get_table():
	sqlite3_open():
```



基础使用

```cpp
#include <sqlite3.h>
#include <stdio.h>

int main() {
    sqlite3 *db;
    int ret = sqlite3_open("test.db", &db);
}
```









