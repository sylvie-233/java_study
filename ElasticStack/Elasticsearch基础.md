# Elasticsearch基础

> Author: Sylvie233
>
> Date: 23/1/22
>
> Point:

[TOC]

## 基础介绍

Lucene基础



文档得分

<img src="Elasticsearch基础.assets/image-20230123030242950.png" alt="image-20230123030242950" style="zoom:67%;" />





安装目录：

```
elasticsearch:
	/bin:
		elasticsearch-certutil
	/config:
		elasticsearch.yml
		custom.dic
	/jdk:
	/lib:
	/logs:
	/modules:
	/plugins:
```



9300端口为集群间组件的通信端口，9200端口为restful接口端口



数据格式：

<img src="Elasticsearch基础.assets/image-20230122020405499.png" alt="image-20230122020405499" style="zoom:67%;" />

types弱化移除



文档刷写：

<img src="Elasticsearch基础.assets/image-20230122175116409.png" alt="image-20230122175116409" style="zoom:67%;" />





文档分析：

分析器：

- 字符过滤器
- 分词器
- 词汇单元过滤器

ik中文分词器`IKAnalyzer.cfg.xml`

`custom.dic`自定义字典：

```xml
<properties>
	<comment></comment>
    <entry key="ext_dict">xxx</entry>
    <entry key="ext_stopwords">xxx</entry>
</properties>
```



pinyin拼音分词器



自定义分词器

<img src="Elasticsearch基础.assets/image-20230211161310927.png" alt="image-20230211161310927" style="zoom:67%;" />





文档控制

并发修改文档时可使用乐观锁添加版本号

<img src="Elasticsearch基础.assets/image-20230211132721995.png" alt="image-20230211132721995" style="zoom:67%;" />



function score自定义得分

<img src="Elasticsearch基础.assets/image-20230211152422834.png" alt="image-20230211152422834" style="zoom:67%;" />



聚合

<img src="Elasticsearch基础.assets/image-20230211153227598.png" alt="image-20230211153227598" style="zoom:67%;" />



<img src="Elasticsearch基础.assets/image-20230211155304482.png" alt="image-20230211155304482" style="zoom:67%;" />





自动补全

suggest

<img src="Elasticsearch基础.assets/image-20230211164202510.png" alt="image-20230211164202510" style="zoom:67%;" />



<img src="Elasticsearch基础.assets/image-20230211164652140.png" alt="image-20230211164652140" style="zoom:67%;" />























### elasticsearch

```
elasticsearch:
	-d:
```



### elasticsearch.yml

```
cluster:
	initial_master_nodes:
	name:
	routing:
		allocation:
			cluster_concurrent_rebalance:
			node_concurrent_recoveries:
			node_initial_primaries_recoveries:
discovery:
	seed_hosts:
	zen:
		minimum_master_nodes:

gateway:
	recover_after_nodes:

path:
	data:
	logs:

xpack:
	security:
		enabled:
		enrollment:
			enabled:
		http:
			ssl:
				enabled:
				keystore.path:
				truststore.path:


node:
	name:
	master:
	data:
	ingest:


network:
	host:
	tcp:
		keep_alive:
		no_delay:
http:
	cors:
		allow-origin:
		enabled:
	max_content_length:
	port:
action.destructive_requires_name:
transport.tcp:
	port:
	compress:

discovery.seed_hosts: []
discovery.zen.fd.ping_timeout:
discovery.zen.fd.ping_retries:
```





## 核心内容

### Restful

DSL







#### DELETE

```
DELETE:
	/xxx: 删除索引
		/_doc:
			/自定义id:
			
```



#### GET

```
GET:
	/:
		响应对象:
			name:
			cluster_name:
			cluster_uuid:
			tagline:
			version:
				number:
				build_flavor:
				build_type:
				bugild_hash:
				build_date:
				build_snapshot:
				build_snapshot:
				lucene_version:
				minimum_wire_compatibility_version:
				minimum_index_compatibility_version:
	/_analyze:
		请求对象:
			analyzer: ik_max_word|ik_smart|standard
			text:
		响应对象:
			tokens: []
				token:
				start_offset:
				end_offset:
				type:
				position:
	/_cat:
		/indices: 查看索引
		/nodes:
	/_cluster:
		/health:
	/xxx: 获取索引信息
		/_doc:
			/自定义id:
				响应对象:
					_index:
					_type:
					_id:
					_version:
					_seq_no:
					_primary_term:
					found:
					_source: {}
		/_search:	
			?q: 设置查询条件
			查询对象:
				_source: 映射投影
				aggs:
					xxx聚合名称:
						aggs:
							xxx聚合名称:
								stats:
									field:
						avg:
						terms: 分组
							field:
							order:
								_count: asc|
							size:
				bool:
					filter:
						range:
							自定义field:
								gt:
					must: [] //参与算分
						match:
					must_not:
					should: [] //参与算分
						match:
							all:
				explain: true
				from:
				highlight:
					fields: []
						xxx:
							require_field_match: false|
							pre_tags:
							post_tags:
				query:
					function_score:
						query:
						functions: []
							filter:
								term:
							weight:
						boost_mode: multiply|
					geo_bounding_box:
						xxx:
							top_left:
							bottom_right:
					get_distance:
						xxx:
						distance:
					match:
					match_all:
					match_phrase:
					multi_match:
						query:
						fields:
					range:
						xxx:
							gte:
							lte:
					term:
						xxx:
							value:
				size:
				sort: []
					xxx:
						order: desc|asc
					_geo_distance:
						xxx:
							lon:
							lat:
						order:
						unit: km|
                suggest:
                	xxx提示名称:
                		text:
                		completion:
                			field: 补全查询的字段
                			skip_duplicates:
                			size:
			响应对象:
				took:
				timed_out:
				_shards:
				hits:
					total:
						value:
						relation:
					max_score:
					hits: []
						_index:
						_type:
						_id:
						_score:
						_source:
						highlight:
						sort:
                aggregations:
                	xxx聚合名:
                		doc_count_error_upper_bound:
                		sum_other_doc_count:
                		buckets:
                			key:
                			doc_count:
                			xxx聚合名:
                				count:
                				min:
                				max:
                				avg:
                				sum:
                suggest:
                	xxx提示名: []
                		texxt:
                		offset:
                		length: 
                		options: [] 提示	结果
                			text:
                			_index:
                			_type:
                			_id:
                			_score:
                			_source:
		请求对象:
        	settings:
                analysis:
                	char_filter: 字符过滤器
                		xxx:
                			type:
                			mappings:
                	filter: 词汇单元过滤器
                		xxx:
                			type:
                            stopwords:
                	analyzer:
                		xxx:
                			type:
                			charfilter: 
                			tokenizer: 分词器
                			filter:
                number_of_replicas:
        		number_of_shards:
        		
        		
		响应:
            xxx:
                aliases:
                mappings:
                settings:
                    index:
                        create_date:
                        number_of_shards:
                        number_of_replicas:
                        uuid:
                        version:
                            created:
                        provided_name:
```



#### HEAD

```
HEAD:
	/xxx: 判断索引是否存在
```



#### POST

```
POST:
	/xxx:
		/_doc: 创建文档
			/自定义id:
			响应:
				_index:
				_type:
				_id:
				_version:
				result:
				_shards:
					total:
					successful:
					failed:
		/_mapping:
			自定义field:
				type: text|keyword|integer|float|date|object|boolean|long
				index:
		/_update: 增量更新
			/自定义id
			更新对象:
				doc: {}
```



#### PUT

```
PUT:
	/_template:
		
	/xxx: 创建索引
		/_bulk:
		/_doc:
			/自定义id:
				响应对象:
					_index:
					_type:
					_id:
					_version:
					result: updated|
					_shards:
						total:
						successful:
						failed:
					_seq_no:
					_primary_term:
		/_mapping:
			请求对象:
				properties:
					xxx字段:
						type:
		settings:
			number_of_shards:
			number_of_replicas:
			analysis:
				analyzer:
					xxx分词器名称:
						tokenizer: ik_max_word|
						filter: pinyin|自定义过滤器|
				filter:
					xxx过滤器名称:
						type: pinyin
						keep_full_pinyin:
						kee-_joined_full_pinyin:
						keep_original:
						limit_first_letter_length:
						remove_duplicated_term:
						none_chinese_pinyin_tokenize:
        mappings:
            properties:
                xxx字段:
                    analayzer: ik_smart|
                    search_analyzer: ik_smart|
                    type: geo_point|completion|
                    index:
                    properties:
                    copy_to:
		响应:
			acknowledged:
			shards_acknowledged:
			index:
```





### JavaAPI

依赖：

```
elasticsearch:
	org.elasticsearch
		elasticsearch
			7.8.0
	org.elasticsearch.client
		elasticsearch-rest-high-level-client
			7.8.0
```



基础使用：

```
RestHighLevelClient cli
	.bulk():
		BulkRequest:
	.close()
	.delete()
		DeleteRequest:
	.get()
		GetRequest:
	.index()
		IndexRequest:
	.indices()
		.create():
			CreateIndexRequest:
		.delete()
		exists():
		.get()
	.search()
		SearchRequest:
	.update()
		UpdateRequest:
		
		
CreateIndexRequest:
	source():
CreateIndexResponse

GetIndexRequest
GetIndexResponse

DeleteIndexRequest
DeleteIndexResponse

IndexRequest:
	id():
    source():
IndexResponse

UpdateRequest:
	doc():
UpdateResponse

GetRequest
GetResponse:
	getSourceAsString():

DeleteRequest:
	
DeleteResponse

BulkRequest:
	add():
BulkResponse

SearchRequest
	.indices()
	.source()
		SearchSourceBuilder
			.aggregation()
				AggregationBuilders
					.max()
					.terms()
					.field()
					.size()
					.stats()
					.avg()
					.count()
					.filter()
			.fetchSource()
			.from()
			.highlighter()
				HighlightBuilder
					.field()
					.requireFieldMatch()
					.preTags()
					.postTags()
			.query()
                QueryBuilders
                	.boolQuery()
                		BoolQueryBuilder
                			.filter()
                			.must()
                			.mustNot()
                			.should()
                	.boostingQuery()
                	.functionScoreQuery()
                		FunctionScoreQueryBuilder:
                			FilterFunctionBuilder:
                		ScoreFunctionBuilders:
                			.weightFactorFunction()
                	.fuzzyQuery()
                		fuzziness()
                    .matchAllQuery()
                    .matchQuery()
                    .multiMatchQuery()
                    .rangQuery()
                    	RangeQueryBuilder
                    		.gte()
                    		.lte()
                    .termQuery()
                    	TermsQueryBuilder
                    .wrapperQuery()
            .size()
            .sort()
            	SortBuilders:
            		.geoDistanceSort()
            			GeoPoint:
                    .unit()
                    .order()
           	.suggest()
            	SuggestBuilder()
            		.addSuggestion()
            			SuggestBuilders:
            				.completionSuggestion()
            				.prefix()
            				.skipDuplicates()
            				.size()
SearchResponse
	.getHits()
		SearchHits:
			.getHits()
				SearchHit:
					.getSourceAsString()
					.getHighlightFields()
						HighlightField:
							.getFragments()
								.string()
                    .getSortValues()
			.getTotalHits()
				value:
    .getAggregations()
    	Aggregations:
    		.get()
    			Terms:
    				.getBuckets()
    					Terms.Bucket:
    						.getKeyAsString()
    .getSuggest()
    	Suggest:
    		.getSuggestion()
    			CompletionSuggestion:
    				.getOptions()
    					CompletionSuggestion.Entry.Option:
    						.getText().string()
```





### SpringDataAPI

依赖：

```
:
	org.springframework.boot
		spring-boot-starter-data-elasticsearch
```



配置：

```

```



基础使用：

```
配置类
AbstractElasticsearchConfiguration:
	es客户端
	RestHighLevelClient elasticsearchClient():
		
		
		
		
DAO类
ElasticsearchRepository<Entity实体, Long主键>
	
	实例方法:
		delete()
		findAll()
			PageRequest:
				Sort:
		findById()
		save()
		saveAll()
		search():
			QueryBuilders:
				termQuery():
					TermQueryBuilder:
		
		
	
实体类（文档关联）
@Document(
	indexName:
	shards:
	replicas:
)
@Id
@Field(
	type,
	index
)



ElasticsearchRestTemplate template
	.deleteIndex()
```









### SparkAPI

### FlinkAPI







### EQL

### SQL









## API





## 应用场景

### 集群

elasticsearch-head插件查看集群情况

路由计算、分片控制

数据写：

<img src="Elasticsearch基础.assets/image-20230122172944878.png" alt="image-20230122172944878" style="zoom:67%;" />

数据读：

<img src="Elasticsearch基础.assets/image-20230122173306750.png" alt="image-20230122173306750" style="zoom:67%;" />

数据更新：

<img src="Elasticsearch基础.assets/image-20230122173419464.png" alt="image-20230122173419464" style="zoom:67%;" />





master选举流程

zenDiscovery模块选主



cerebro监控es集群状态

Web界面





集群节点角色

<img src="Elasticsearch基础.assets/image-20230211175045460.png" alt="image-20230211175045460" style="zoom:67%;" />



集群结构

<img src="Elasticsearch基础.assets/image-20230211175453356.png" alt="image-20230211175453356" style="zoom:67%;" />







数据分片

<img src="Elasticsearch基础.assets/image-20230211180213378.png" alt="image-20230211180213378" style="zoom:67%;" />



分片数据存储

<img src="Elasticsearch基础.assets/image-20230211180409291.png" alt="image-20230211180409291" style="zoom:67%;" />

<img src="Elasticsearch基础.assets/image-20230211180453524.png" alt="image-20230211180453524" style="zoom:67%;" />





## Kibana







