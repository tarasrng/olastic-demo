# Olastic demo
## Simple project to demonstrate how to use Olastic

### Install Elasticsearch 
* Download Elasticsearch from https://www.elastic.co/products/elasticsearch
* Unzip and run ../bin/elasticsearch.bat

### Index some test data
* Install curl: http://www.confusedbycode.com/curl/#downloads
* Download accounts json from: https://raw.githubusercontent.com/elastic/elasticsearch/master/docs/src/test/resources/accounts.json
* Download employee json from: http://ikeptwalking.com/wp-content/uploads/2017/03/Employee50K.zip
* Index employee data: *<addr>curl -X POST "http://localhost:9200/_bulk?pretty" --data-binary @c:\Employee50K.json</addr>*
* Index accounts data: *<addr>curl -X POST "localhost:9200/bank/account/_bulk?pretty" --data-binary @c:\Accounts.json</addr>*

### Run the service
This example uses Olastic *war* dependency. It already has web.xml and defaut servlet. Just deploy the service on some servlet container and you are ready to browse your data :thumbsup:

### Sample queries
* http://localhost:8080/OData.svc/ - Service root
* http://localhost:8080/OData.svc/$metadata - Metadata
* http://localhost:8080/OData.svc/account - get first 25 accounts
* http://localhost:8080/OData.svc/account?$top=5&$skip=10 - Get 5 account starting from 10
* http://localhost:8080/OData.svc/account('227') - get account with id 227
* http://localhost:8080/OData.svc/account('227')?$format=xml - get xml
* http://localhost:8080/OData.svc/account('227')?$format=json - get json
* http://localhost:8080/OData.svc/employees?$filter=Age ge 55 and Age lt 60 - filter employees by their age
* http://localhost:8080/OData.svc/account?$apply=groupby((city)) - group by city
* http://localhost:8080/OData.svc/account?$apply=groupby((state),aggregate($count as Total))&$orderby=Total desc - group by state, aggregate total count for each state, and sort descending.
* http://localhost:8080/OData.svc/account?$apply=groupby((state),aggregate(balance with max as MaxBalance)) - group by state, aggregate maximum balance for each state
* http://localhost:8080/OData.svc/account?$apply=search(Coleman) - full text search

### Customization 
Olastic is built with possibility to extend it's classes in order to implement custom functionality.
It is implemented using Apache Olingo Java library. Please read Olingo documentation before implementing custom logic: https://olingo.apache.org/doc/odata4/index.html
