# API Elasticsearch

## Add new template to Elasticsearch
```
  curl -XPUT -H 'Content-Type: application/json' http://localhost:9200/_template/filebeat -d@/$PATH_TO_FILE
```

## Get all Indices from Elasticsearch
```
  curl 'localhost:9200/_cat/indices?v'
```

## Get Entry from Elasticsearch
```
  curl 'localhost:9200/index/type/id'
```

## Remove Entry from Elasticsearch
```
  curl -XDELETE 'localhost:9200/index/type/id'
```

## Get snapshots from repository
```
  curl -XGET 'http://127.0.0.1:9200/_cat/snapshots/backup?v&s=id'
```
