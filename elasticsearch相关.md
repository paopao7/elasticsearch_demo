### elasticsearch相关

##### 获取所有索引

- GET	localhost:9200/_all

  - 响应数据

  ```json
  {
      "aaa": {
          "aliases": {},
          "mappings": {},
          "settings": {
              "index": {
                  "creation_date": "1587958393152",
                  "number_of_shards": "5",
                  "number_of_replicas": "0",
                  "uuid": "IZiOGjTeQOeWLrIgL2mNbw",
                  "version": {
                      "created": "6040399"
                  },
                  "provided_name": "aaa"
              }
          }
      },
      "data_activity": {
          "aliases": {},
          "mappings": {
              "doc": {
                  "dynamic": "strict",
                  "properties": {
                      "activity_classify": {
                          "type": "long"
                      },
                      "activity_day": {
                          "type": "long"
                      },
                      "activity_id": {
                          "type": "long"
                      },
                      "activity_release_date": {
                          "type": "date"
                      },
                      "activity_type": {
                          "type": "long"
                      },
                      "add_cart_count": {
                          "type": "long"
                      },
                      "apply_member_count": {
                          "type": "long"
                      },
                      "biz_code": {
                          "type": "keyword"
                      },
                      "buying_count": {
                          "type": "long"
                      },
                      "conversion": {
                          "type": "long"
                      },
                      "day_stock_list": {
                          "type": "join",
                          "eager_global_ordinals": true,
                          "relations": {
                              "activity": "activity_day_stock"
                          }
                      },
                      "gmt_updated": {
                          "type": "date"
                      },
                      "id": {
                          "type": "long"
                      },
                      "item_category_id": {
                          "type": "long"
                      },
                      "item_category_second_id": {
                          "type": "long"
                      },
                      "item_name": {
                          "type": "text",
                          "fields": {
                              "keyword": {
                                  "type": "keyword",
                                  "ignore_above": 256
                              }
                          },
                          "analyzer": "ik_max_word"
                      },
                      "item_pic": {
                          "type": "keyword",
                          "fields": {
                              "keyword": {
                                  "type": "keyword",
                                  "ignore_above": 256
                              }
                          }
                      },
                      "item_price": {
                          "type": "long"
                      },
                      "item_url": {
                          "type": "keyword"
                      },
                      "lifecycle_status": {
                          "type": "integer"
                      },
                      "lottery_count": {
                          "type": "long"
                      },
                      "need_coin": {
                          "type": "long"
                      },
                      "operate_status": {
                          "type": "integer"
                      },
                      "reward": {
                          "type": "long"
                      },
                      "sales_coin_stock": {
                          "type": "long"
                      },
                      "sales_coupon_stock": {
                          "type": "long"
                      },
                      "sales_normal_stock": {
                          "type": "long"
                      },
                      "sales_stock": {
                          "type": "long"
                      },
                      "shop_type": {
                          "type": "long"
                      },
                      "sort_sink": {
                          "type": "long"
                      },
                      "surplus_buying_count": {
                          "type": "long"
                      },
                      "total_coin_stock": {
                          "type": "long"
                      },
                      "total_coupon_stock": {
                          "type": "long"
                      },
                      "total_normal_stock": {
                          "type": "long"
                      },
                      "total_stock": {
                          "type": "long"
                      },
                      "type": {
                          "type": "keyword",
                          "fields": {
                              "keyword": {
                                  "type": "keyword",
                                  "ignore_above": 256
                              }
                          }
                      },
                      "used_credit": {
                          "type": "long"
                      },
                      "used_huabei": {
                          "type": "long"
                      }
                  }
              }
          },
          "settings": {
              "index": {
                  "creation_date": "1585647804068",
                  "number_of_shards": "5",
                  "number_of_replicas": "1",
                  "uuid": "yAJSKJKjRUmaqYmK9zSByQ",
                  "version": {
                      "created": "6040399"
                  },
                  "provided_name": "data_activity"
              }
          }
      },
      "person": {
          "aliases": {},
          "mappings": {
              "_doc": {
                  "properties": {
                      "about": {
                          "type": "text",
                          "fields": {
                              "keyword": {
                                  "type": "keyword",
                                  "ignore_above": 256
                              }
                          }
                      },
                      "age": {
                          "type": "long"
                      },
                      "first_name": {
                          "type": "text",
                          "fields": {
                              "keyword": {
                                  "type": "keyword",
                                  "ignore_above": 256
                              }
                          }
                      },
                      "interests": {
                          "type": "text",
                          "fields": {
                              "keyword": {
                                  "type": "keyword",
                                  "ignore_above": 256
                              }
                          }
                      },
                      "last_name": {
                          "type": "text",
                          "fields": {
                              "keyword": {
                                  "type": "keyword",
                                  "ignore_above": 256
                              }
                          }
                      }
                  }
              }
          },
          "settings": {
              "index": {
                  "creation_date": "1587968550226",
                  "number_of_shards": "5",
                  "number_of_replicas": "1",
                  "uuid": "rfdcADfeSEeVXhiQFXJc6w",
                  "version": {
                      "created": "6040399"
                  },
                  "provided_name": "person"
              }
          }
      }
  }
  ```

  

  

##### 创建索引

- PUT	localhost:9200/test	直接跟需要创建的索引名称

  - 响应数据（不存在）：

  ```json
  {
      "acknowledged": true,
      "shards_acknowledged": true,
      "index": "test"
  }
  ```

  - 响应数据（存在）：

  ```json
  {
      "error": {
          "root_cause": [
              {
                  "type": "resource_already_exists_exception",
                  "reason": "index [person/rfdcADfeSEeVXhiQFXJc6w] already exists",
                  "index_uuid": "rfdcADfeSEeVXhiQFXJc6w",
                  "index": "person"
              }
          ],
          "type": "resource_already_exists_exception",
          "reason": "index [person/rfdcADfeSEeVXhiQFXJc6w] already exists",
          "index_uuid": "rfdcADfeSEeVXhiQFXJc6w",
          "index": "person"
      },
      "status": 400
  }
  ```



##### 创建索引（指定参数）

- PUT localhost:9200/school

- 请求参数

  ```json
  {
      "mappings": {
          "c2_1": {
              "properties": {
                  "no": {
                      "type": "keyword"
                  },
                  "name": {
                      "type": "text"
                  },
                  "age": {
                      "type": "integer"
                  }
              }
          }
      }
  }
  ```

- 响应数据

  ```json
  {
      "acknowledged": true,
      "shards_acknowledged": true,
      "index": "school"
  }
  ```

  

##### 删除索引

- DELETE	localhost:9200/test	直接跟需要创建的索引名称

  - 响应数据（存在）：

  ```json
  {
      "acknowledged": true
  }
  ```

  - 响应数据（不存在）：

  ```json
  {
      "error": {
          "root_cause": [
              {
                  "type": "index_not_found_exception",
                  "reason": "no such index",
                  "resource.type": "index_or_alias",
                  "resource.id": "test",
                  "index_uuid": "_na_",
                  "index": "test"
              }
          ],
          "type": "index_not_found_exception",
          "reason": "no such index",
          "resource.type": "index_or_alias",
          "resource.id": "test",
          "index_uuid": "_na_",
          "index": "test"
      },
      "status": 404
  }
  ```



##### 新增数据

- PUT 	localhost:9200/person/_doc/1

- _doc：新版及官方建议，一个库（index）下面最好只有一个表（type），可省略

  - 请求数据：

  ```json
  {
      "first_name": "John",
      "last_name": "Smith",
      "age": 25,
      "about": "I love to go rock climbing",
      "interests": [
          "sports",
          "music"
      ]
  }
  ```

  - 响应数据：

  ```json
  {
      "_index": "person",
      "_type": "_doc",
      "_id": "1",
      "_version": 1,
      "result": "created",
      "_shards": {
          "total": 2,
          "successful": 1,
          "failed": 0
      },
      "_seq_no": 0,
      "_primary_term": 1
  }
  ```

  同一条数据多次添加，则对应的_version则会跟着追加

  

##### 获取数据（获取特定索引下的全部数据）

- GET	localhost:9200/person/_search
- person：索引名称



##### 获取数据（根据id）

- GET	localhost:9200/person/_doc/1

- 1：对应数据的id，若创建的时候未执行，则官方会指定

  - 响应数据：

  ```json
  {
      "_index": "person",
      "_type": "_doc",
      "_id": "1",
      "_version": 3,
      "found": true,
      "_source": {
          "first_name": "John",
          "last_name": "Smith",
          "age": 25,
          "about": "I love to go rock climbing",
          "interests": [
              "sports",
              "music"
          ]
      }
  }
  ```



##### 获取数据（根据名称）

- GET	localhost:9200/person/_doc/_search?q=first_name:john

- q：query

- first_name:john：first_name字段等于john

  - 响应数据

  ```json
  {
      "took": 49,
      "timed_out": false,
      "_shards": {
          "total": 5,
          "successful": 5,
          "skipped": 0,
          "failed": 0
      },
      "hits": {
          "total": 1,
          "max_score": 0.2876821,
          "hits": [
              {
                  "_index": "person",
                  "_type": "_doc",
                  "_id": "1",
                  "_score": 0.2876821,
                  "_source": {
                      "first_name": "John",
                      "last_name": "Smith",
                      "age": 25,
                      "about": "I love to go rock climbing",
                      "interests": [
                          "sports",
                          "music"
                      ]
                  }
              }
          ]
      }
  }
  ```




##### 更新数据

- PUT	localhost:9200/animal/cat/eM-VvnEB7cL0Y_uMtRT_

- animal：index

- cat：type

- eM-VvnEB7cL0Y_uMtRT_： id

  - 请求数据（此处若只填写了name则只更新name字段，而未填写的字段则会被删除）

  ```json
  {
  	"name" : "叮当猫",
  	"age": 30
  }
  ```
  - 响应数据

  ```json
  {
      "_index": "animal",
      "_type": "cat",
      "_id": "eM-VvnEB7cL0Y_uMtRT_",
      "_version": 6,
      "result": "updated",
      "_shards": {
          "total": 1,
          "successful": 1,
          "failed": 0
      },
      "_seq_no": 5,
      "_primary_term": 1
  }
  ```

  

##### 删除数据

- DELETE	localhost:9200/person/_doc/cs9gvnEB7cL0Y_uMmBSw

- person：索引

- _doc：文档名称

- cs9gvnEB7cL0Y_uMmBSw：id

  ```json
  {
      "_index": "person",
      "_type": "_doc",
      "_id": "cs9gvnEB7cL0Y_uMmBSw",
      "_version": 2,
      "result": "deleted",
      "_shards": {
          "total": 1,
          "successful": 1,
          "failed": 0
      },
      "_seq_no": 1,
      "_primary_term": 1
  }
  ```

  

#### 使用Kibana查询

在Dev Tools下的Console输入如下命令：

- match 可写多个
- should：类似于mysqk的 or
- must：类似于mysql的 and

```json
POST /person/_search
{
    "query": {
        "bool": {
            "should": [
                {"match": {
                    "first_name": "Eric"
                }}
            ]
        }
    }
}
```

