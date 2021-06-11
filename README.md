# Overview

- Filebeat collect logs from files then sent to Logstash
- Logstash filter and transform data then sent to ElasticSearch
- ElasticSearch keep the logs in `logstash-*` index (by default) and provides full-text search
- Kibana is a UI for ElasticSearch that has Dashboard, Query box , etc.

Mostly followed the [Gettng Started with Logstatsh](https://www.elastic.co/guide/en/logstash/7.13/getting-started-with-logstash.html). By the way, Logstash, ElasticSearch, and Kibana are containerized which can run by `docker-compose`

## Endpoint for each services

- Logstash http://localhost:5044
- ElasticSearch http://localhost:9200
- Kibana http://localhost:5601

# ElasticSearch

Get all indices

```
http://localhost:9200/_cat/indices
```

Get all documents in index

```
http://localhost:9200/{index-regex}/_search
```

# Kibana

- Kibana requires an index pattern to access the Elasticsearch data that you want. Go to
  `Menu -> Stack Management -> Index Patterns` then add the index

# Logstash

- Create pipeline in `logstash/configs`, then register pipeline in `settings/pipelines.yml`

# Filebeat

- Download binary package [Filebeat Download](https://www.elastic.co/downloads/beats/filebeat)
- Configure `filebeat.yml` (Need to set file permission `owner write-only`)
- Validate config `filebeat test config`
- Run `sudo ./filebeat -e -c filebeat.yml -d "publish"`
