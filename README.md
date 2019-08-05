# kafka-prometheus-monitoring
Dockerised example of monitoring [Apache Kafka](https://kafka.apache.org/) with [Prometheus](https://prometheus.io/) and [Grafana](http://grafana.org/).  This project makes use of the prometheus-jmx-exporter which is configured to extract metrics from Kafka's JMX server.  These metrics are then exposed via HTTP GET and polled by Prometheus.

* [kafka.yml](../master/prometheus-jmx-exporter/confd/templates/kafka.yml.tmpl) - Kafka JMX polling configuration
* [prometheus.yml](../master/mount/prometheus/prometheus.yml) - Prometheus metric polling configuration

## Pre-Requisites
* install Docker and Docker Compose - https://docs.docker.com/

## Usage

```
docker-compose up
```

- View Prometheus UI - `http://$DOCKER_HOST_IP:9090`
- Grafana UI - `http://$DOCKER_HOST_IP:3000` (admin:admin)
- Kafka metrics - `http://$DOCKER_HOST_IP:8080/metrics`

```

### Viewing Prometheus Metrics
The kafka metrics are pulled into Prometheus via the JMX exporter.  These can be viewed in Prometheus by navigating to `http://$DOCKER_HOST_IP:9090/graph`, enter a metric name to view the graphs.

![Prometheus UI](images/prometheus-ui.png?raw=true)

### Viewing Graphs in Grafana
Grafana can be used to build a more meaningful dashboard of the metrics in Prometheus, navigate to Grafana on `http://$DOCKER_HOST_IP:3000` (admin:admin).  An example dashboard is available to import in `dashboards/Kafka.json`.

![Grafana Kafka Dashboard](images/grafana-ui.png?raw=true)

