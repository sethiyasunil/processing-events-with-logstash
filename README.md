This repository contains all of the configuration files used within the [Processing Events with Logstash course](https://l.codingexplained.com/course/logstash?src=github).

## Basics of Logstash
Processing 1st event
```
cd /usr/share/logstash
sudo bin/logstash -e "input {stdin{}} output {stdout{}}"

scp -P 2200 io-pipeline.conf e@localhost:/etc/logstash/conf.d/pipeline.conf
sudo /usr/share/logstash/bin/logstash -f /etc/logstash/conf.d/pipeline.conf

hello-world-1.conf : basic
hello-world-2.conf: basic
handling-json-input.conf : input json
file-output.conf : output to a file
json-http.conf : input over http
filtering-events.conf: convert quantity to integer
common-filter-options.conf: remove field from input
```

## Project Apache

automatic reload apache logs file
```
Param to reload config file automatically and monitor apache logs (--config.reload.automatic)
sudo /usr/share/logstash/bin/logstash -f /etc/logstash/conf.d/pipeline.conf --config.reload.automatic
automatic-config-reload-file-input.conf

parsing-events-with-grok.conf
https://github.com/logstash-plugins/logstash-patterns-core/

working-with-conditional-statements.conf
geographical-data-enrichment.conf
parsing-user-agents.conf
finishing-up-the-pipeline.conf
sending-processed-events-to-elasticsearch.conf
handling-multiline-events.conf
handling-multiline-events-the-easy-way.conf
parsing-stack-traces-with-grok.conf
working-with-metadata.conf
config\pipelines.yml
config\pipelines\access.conf
config\pipelines\errors.conf
```


## Collection Logs with Filebeat
```
modules location are given at https://www.elastic.co/guide/en/beats/filebeat/current/directory-layout.html
modules presnet on ubantu at /usr/share/filebeat/
```

Tell filebeat to push read apache and push event to logstash
```
/etc/filebeat/modules.d/apache.yml : Filebeat reads apache logs from the location given in this file.
/etc/filebeat/filebeat.yml : Filebeat sends log events to logstash as on port given in logstash section.
/etc/logstash/conf.d/pipeline.conf  : Logstach reads evens from port given in input section ( same as output port in filebeat.yml)

sudo /usr/share/logstash/bin/logstash -f /etc/logstash/conf.d/pipeline.conf
sudo filebeat -e
````

Load template
```
https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-template.html#load-template-manually-alternate
```
sudo filebeat setup --dashboards

Registry location to reset read pointer :/var/lib/filebeat/registry/filebeat/data.json

pipelines
pipelines\finishing-up-the-pipeline.conf
pipelines\processing-apache-error-logs.conf
handling-multiline-logs-approach-1.yml
handling-multiline-logs-approach-2.yml
```
