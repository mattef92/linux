# API Elasticsearch
## Get all Indices from Elasticsearch
  curl 'localhost:9200/_cat/indices?v'

## Get Entry from Elasticsearch
  curl 'localhost:9200/index/type/id'

## Remove Entry from Elasticsearch
  curl -XDELETE 'localhost:9200/index/type/id'
