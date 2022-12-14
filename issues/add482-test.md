```
oc patch kafkaconnect/my-connect-cluster -p  '{"""metadata""":{"""annotations""":{"""strimzi.io/use-connector-resources""":"""false"""} } }'  --type merge
```

```
curl -X POST '
http://localhost:8083/connectors '
-H 'Content-Type: application/json' '
-d '{ """name""": """elasticsearch-sink-connector""",
  """config""":
    {
       "connector.class": "org.apache.camel.kafkaconnector.elasticsearchrest.CamelElasticsearchrestSinkConnector", 
       "tasks.max": "1",
       "topics": "github-events", 
       "camel.sink.endpoint.hostAddresses": "elasticsearch-es-http:9200", 
       "camel.sink.endpoint.indexName": "github_events", 
       "camel.sink.endpoint.operation": "Index", 
       "camel.sink.path.clusterName": "elasticsearch", 
       "key.converter": "org.apache.kafka.connect.storage.StringConverter", 
       "value.converter": "org.apache.kafka.connect.storage.StringConverter" 
     }
}'
```

```
curl -X POST \
http://localhost:8083/connectors \
-H 'Content-Type: application/json' \
-d '{ "name": "elasticsearch-sink-connector",
  "config":
    {
       "connector.class": "org.apache.camel.kafkaconnector.elasticsearchrest.CamelElasticsearchrestSinkConnector", 
       "tasks.max": "1",
       "topics": "github-events", 
       "camel.sink.endpoint.hostAddresses": "elasticsearch-es-http:9200", 
       "camel.sink.endpoint.indexName": "github_events", 
       "camel.sink.endpoint.operation": "Index", 
       "camel.sink.path.clusterName": "elasticsearch", 
       "key.converter": "org.apache.kafka.connect.storage.StringConverter", 
       "value.converter": "org.apache.kafka.connect.storage.StringConverter" 
     }
}'
```