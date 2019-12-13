# Elasticsearch Playground

Elasticsearch Playground.

# Create local Elasticsearch with Kibana

```
docker network create playground
docker run -d --name elasticsearch --net playground -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.5.0
docker run -d --name kibana --net playground -p 5601:5601 kibana:7.5.0
```

Elasticsearch URL: http://localhost:9200
Kibana URL: http://localhost:5601

# Apply Platinum license trial

Enter Kibana > Management > License Management and start trial.

# Populate data

Apply mapping:

```
curl http://media.sundog-soft.com/es7/shakes-mapping.json > shakes-mapping.json
curl -H "Content-Type: application/json" -X PUT localhost:9200/shakespeare --data-binary @shakes-mapping.json
```

Ingest data:

```
curl http://media.sundog-soft.com/es7/shakespeare_7.0.json > shakespeare_7.0.json
curl -H "Content-Type: application/json" -X POST localhost:9200/shakespeare/_bulk --data-binary @shakespeare_7.0.json
```