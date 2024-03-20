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

The pod in this deployment has the expected Prometheus scrape annotation. In order to decorate the metrics with the `mongodb_cluster_name` attribute as required by the quickstart dashboard, you will need to add configuration to your Prometheus scraper, as documented here: https://docs.newrelic.com/docs/infrastructure/host-integrations/host-integrations-list/mongodb/mongodb-monitoring-integration-new/#containerized-environments
