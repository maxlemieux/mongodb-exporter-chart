# mongodb-exporter-chart
A Helm chart for https://github.com/percona/mongodb_exporter

# Instrumenting Confluent Cloud

Set `mongodbUri` in `values.yaml` to a user with clusterMonitor permissions in Confluent Cloud.

# Scraping with New Relic

Add `mongodb-exporter` to your Prometheus agent configuration. The integrations filter must be extended, as in this minimal example:

```
newrelic-prometheus-agent:
  enabled: true
  config:
    kubernetes:
      integrations_filter:
        source_labels: ["app.kubernetes.io/name", "app.newrelic.io/name"]
        app_values: ["redis", "traefik", "calico", "nginx", "coredns", "etcd", "cockroachdb", "mongodb-exporter"]
```
