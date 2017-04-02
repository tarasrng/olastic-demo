# Olastic demo
## Simple project to demonstrate how to use Olastic

### Install Elasticsearch 
* Download Elasticsearch from https://www.elastic.co/products/elasticsearch
* Unzip and run ../bin/elasticsearch.bat

### Index some test data
* Install curl: http://www.confusedbycode.com/curl/#downloads
* Download accounts json from: https://raw.githubusercontent.com/elastic/elasticsearch/master/docs/src/test/resources/accounts.json
* Download employee json from: http://ikeptwalking.com/wp-content/uploads/2017/03/Employee50K.zip
* Index employee data: <addr>curl -X POST "http://localhost:9200/_bulk?pretty" --data-binary @c:\Employee50K.json</addr>
* Index accounts data: <addr>curl -X POST "localhost:9200/bank/account/_bulk?pretty" --data-binary @c:\Accounts.json</addr>

### Run the service
This example uses olastic war dependency, that already has web.xml and defaut servlet. Just deploy the service on some servlet container.

### Sample queries
http://localhost:8080/OData.svc/ - Service root
http://localhost:8080/OData.svc/$metadata - Metadata
http://localhost:8080/OData.svc/account - get first 25 accounts
http://localhost:8080/OData.svc/account?$top=5&$skip=10 - Get 5 account starting from 10
http://localhost:8080/OData.svc/account('227') - get account with id 227
http://localhost:8080/OData.svc/account('227')?$format=xml - get xml
http://localhost:8080/OData.svc/account('227')?$format=json - get json

### Customization 
Olastic is build with possibility to extend its classes in order to implement custom functionality.
It is implemented using Apache Olingo Java library. Please read Olingo documentation before implementing custom logic: https://olingo.apache.org/doc/odata4/index.html
