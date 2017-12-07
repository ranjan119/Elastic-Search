# Elastic Search Documentation
 Priyaranjan Singh | Nineleaps | ranjan@nineleaps.com | 1st Nov 2017
#### Introduction
* A detailed documentation regarding the implementation for elastic search in    linux and windows environments.

#### What is Elastic Search ?
* Elasticsearch is an open-source, restful, distributed search and analytics engine built on Apache Lucene.

#### Why Elastic search?
* Elasticsearch search and analytics engine is capable of solving a growing number of use cases.
* Elasticsearch lets you perform and combine many types of searches — 
structured, unstructured, geo, metric.
* Since everything is indexed, you're never left with index envy and access all your data at awesome speed.

#### Let’ s move on to implementation, shall we? 
###### Note : Download specified version of elastic search according to the requirement. In this example I’m using elastic search version 2.4.4.

###### For linux users : 
* Download elastic-search-2.4.4.zip file from [link](https://www.elastic.co/downloads/past-releases/elasticsearch-2-4-4) 
* Unzip elastic-search-2.4.4.zip file.
* Navigate to elastic-search-2.4.4/bin.
* Type the below commands to check and run the elasticsearch in your env: 
   ```sh
   ls -lhrt
   ./elasticsearch
   ```
* In order to create elastic search index and view the mapping you need to download an extension elasticsearch head from chrome webstore.

* After downloading the extensions open terminal to follow the below commands :
* To create elastic search index (assuming you have curl installed):
  ```sh
  curl -X PUT ‘http://localhost:9200/elasticsearchIndexName’ -d ‘{
   “mappings” :
     { 
          “tweet” : 
          {   
               “properties” : 
               {
                  “message” : 
                   { 
                      “type” : “text” 
                   }
               }
          }
      }
  }’
  ```
* To get the elastic search index mapping : 
  ```sh
  curl -X GET ‘http://localhost:9200/elasticsearchIndexName?pretty=true’
  ```
* To insert data into elastic search index : 
  ```sh
  curl -X POST ‘http://localhost:9200/policymanagement/’ -d ‘{ 
  “message”  : “ Inserting data into elastic search index ” 
  }’
  ```
* To query the created document in elastic search :
  * Terminal
    ```sh
    curl -X GET ‘http://localhost:9200/policymanagement/tweet/1?pretty=true ’ 
    ```
    
  * Navigate to “Any Request” tab in Elastic search Head and paste the query: 
    ```sh
    {
      "query": {
        "bool": {
          "must": [
            {
              "match": {
                "message": "Inserting data into elasticsearch index"
              }
            }
          ]
        }
      }
    }
    ``` 
* To delete the elastic search index mapping :
  ```sh
  curl -X DELETE ‘http://localhost:9200/elasticsearchIndexName’ 
  ``` 
#### References
* [https://www.elastic.co/blog/found-elasticsearch-mapping-introduction](https://www.elastic.co/blog/found-elasticsearch-mapping-introduction)
* [https://www.elastic.co/guide/en/elasticsearch/guide/current/mapping-intro.html](https://www.elastic.co/guide/en/elasticsearch/guide/current/mapping-intro.html)
* [https://www.elastic.co/guide/en/elasticsearch/reference/current/_executing_searches.html](https://www.elastic.co/guide/en/elasticsearch/reference/current/_executing_searches.html )
