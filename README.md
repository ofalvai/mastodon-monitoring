# Mastodon monitoring and metrics setup

My Docker-based setup for monitoring a Mastodon instance with Prometheus

## Overview

Mastodon can optionally send metrics to a StatsD endpoint. We can use [statsd-exporter](https://github.com/prometheus/statsd_exporter) to receive the metrics and map them to Prometheus metrics.

The setup consists of the following services:

- [statsd-exporter](https://github.com/prometheus/statsd_exporter): Receives StatsD metrics from the Mastodon processes and transforms them to Prometheus metrics
- [cAdvisor](https://github.com/google/cadvisor): Container metrics
- Prometheus: scrapes metrics from the above services

### Mappings

Mastodon collects the StatsD metrics listed [here](https://github.com/localshred/nsa#built-in-collectors). See `statsd-exporter/statsd_mapping.yml` for the rules that transforms these metrics.

