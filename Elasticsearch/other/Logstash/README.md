# Logstash - README

## 📌 What is Logstash?

Logstash is a server-side data processing pipeline that collects, processes, and forwards data to different destinations. It is a key part of the ELK Stack (Elasticsearch, Logstash, Kibana) and is used for log and event data processing.

## 🚀 How Logstash Works?

Logstash processes data in three stages:

### 🔹 Input Plugins (Collecting Data)

Logstash ingests data from multiple sources like:

- Log files (CSV, JSON, XML)
- Databases
- APIs (HTTP)
- Kafka
- Syslogs, Cloud logs, etc.

### 🔹 Filter Plugins (Processing Data)

The data is transformed, parsed, and filtered, including:

- Removing unnecessary fields
- Extracting values (like timestamps, IP addresses)
- Enriching data (geo-location, log levels)

### 🔹 Output Plugins (Sending Data)

The processed data is then sent to:

- Elasticsearch (for searching & analytics)
- Kafka (for further streaming)
- Email Alerts
- HTTP APIs

## 📜 Example Logstash Pipeline

```yaml
input {
  file {
    path => "/var/log/syslog"
    start_position => "beginning"
  }
}

filter {
  grok {
    match => { "message" => "%{SYSLOGTIMESTAMP:timestamp} %{WORD:log_level} %{GREEDYDATA:message}" }
  }
}

output {
  elasticsearch {
    hosts => ["http://localhost:9200"]
    index => "syslog_data"
  }
}
```

### 🔹 What happens here?

✅ Reads logs from syslog  
✅ Parses logs to extract timestamp, log level, and message  
✅ Sends the structured data to Elasticsearch
