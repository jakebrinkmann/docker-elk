# Leaf-Nosed-Snake-LogParse

**PROVISIONAL SOFTWARE DISCLAIMER**: This software is preliminary and is subject to revision.

Codename leaf-nosed-snake provides the ability to parse NGINX server logs. 

* [Logstash](https://www.elastic.co/guide/en/logstash/current/docker.html)
  * [Filebeats](https://www.elastic.co/guide/en/logstash/current/plugins-inputs-beats.html)
* [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html)
* [Kibana](https://www.elastic.co/guide/en/kibana/current/docker.html)

## Dependencies

* Docker 1.13
* Docker Compose 1.10

## Startup


Startup the multi-container architecture using:

```bash
cd leaf-nosed-snake-logparse
docker-compose up -d [--build]
```

The results can then be queried with: 
```bash
$ curl -s 'localhost:9200/logstash-*/_search?pretty&size=1' | head
```
```json
{
  "took" : 2,
  "timed_out" : false,
  "_shards" : {
    "total" : 5,
    "successful" : 5,
    "failed" : 0
  },
  "hits" : {
    "total" : 50,
```

Once Kibana is done "Optimizing", it will log: `"message":"Server running at http://0:5601"`,
then, navigate to [Kibana Dashboard](http://localhost:5601/app/kibana)


![Kibana Dashboard](docs/kibana_visual_example.png)

## References

* [Config grok](https://www.elastic.co/guide/en/logstash/5.2/plugins-filters-grok.html)
* [Grok Patterns](https://github.com/elastic/logstash/blob/v1.4.2/patterns/grok-patterns)
* [Grok matching tool](http://grokconstructor.appspot.com/do/match)
* [Elastic Search API](https://www.elastic.co/guide/en/elasticsearch/reference/1.4/search.html)

## Additional

<details>
<summary>[optional] Shorten a log:</summary>

Shorten a log to only the first 50 lines (inplace)

```bash
sed -i '51,$ d' example_log
```

</details>

