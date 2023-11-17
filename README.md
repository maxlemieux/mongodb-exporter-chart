# mongodb-exporter-chart
A Helm chart for https://github.com/percona/mongodb_exporter

This is experimental and not intended for production.

# Installation

```
git clone git@github.com:maxlemieux/mongodb-exporter-chart.git
cd mongodb-exporter-chart/chart
```

Set your connection info in values.yaml, then install the chart:

```
helm upgrade --install -n prometheus mongodb-exporter . --create-namespace
```

# Instrumenting Atlas MongoDB

Set `mongodbUri` in `values.yaml` to a user with clusterMonitor permissions for an M10+ cluster in Atlas MongoDB.

# Scraping with New Relic

The pod in this deployment has the expected Prometheus scrape annotation. In the simplest case, the integrations filter can be extended. Here is an example for a typical [newrelic-bundle](https://docs.newrelic.com/docs/kubernetes-pixie/kubernetes-integration/installation/kubernetes-integration-install-configure/#installing-and-configuring-nri-bundle-with-helm) configuration:

```
newrelic-prometheus-agent:
  enabled: true
  config:
    kubernetes:
      integrations_filter:
        source_labels: ["app.kubernetes.io/name", "app.newrelic.io/name"]
        app_values: ["redis", "traefik", "calico", "nginx", "coredns", "etcd", "cockroachdb", "mongodb-exporter"]
```
