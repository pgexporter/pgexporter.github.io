---
outline: deep
---

# Metrics

The main task of `pgexporter` is to gather metrics from your database and format it according to [Prometheus metrics standards](https://prometheus.io/docs/concepts/metric_types/). `pgexporter` provides some [pre-defined metrics](#internal-metrics) that are necessary/useful, and also provides the capability of providing [custom metrics](#custom-metrics) to the user.


## Internal Metrics

`pgexporter` defines a lot of metrics out of the box. All of the internal metrics that are exported can be viewed [here](../../docs/pgexporter/metrics.md#internal-metrics). By default, all of them are enabled, and will be reflected in the output. However, if you need only specific metrics, you can enable only them as shown [here](../../docs/pgexporter/command_line_flags.md#enable-only-specific-collectors) (and thus, disable other metrics).

## Custom Metrics
_See [Custom Metrics](../../docs/pgexporter/metrics.md#custom-metrics)_.

## Extension Metrics
`pgexporter` also comes with support for metrics related to extensions:

- [pgexporter_ext](../extensions/pgexporter_ext) - Core extension metrics
- [pg_stat_statements](../extensions/pg_stat_statements) - Query performance and execution statistics
- [pg_buffercache](../extensions/pg_buffercache) - Shared buffer cache utilization and effectiveness
- [pgcrypto](../extensions/pgcrypto) - Cryptographic function usage patterns
- [postgis](../extensions/postgis) - Spatial data and geometry/geography column statistics
- [postgis_raster](../extensions/postgis_raster) - Raster data storage and processing metrics
- [postgis_topology](../extensions/postgis_topology) - Topology element counts and health monitoring
- [timescaledb](../extensions/timescaledb) - Hypertable, chunk, and compression statistics
- [vector](../extensions/vector) - Vector similarity search index performance and storage