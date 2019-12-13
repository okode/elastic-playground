# Elasticsearch Playground

Elasticsearch Playground.

# Create local Elasticsearch with Kibana

```
docker run -d --name elasticsearch -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.5.0
docker run -d --name kibana -p 5601:5601 kibana:7.5.0
```

Elasticsearch URL: http://localhost:9200
Kibana URL: http://localhost:5601