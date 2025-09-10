---
outline: deep
---

# Custom Metrics

::: tip Related Documentation
See also: [pgexporter Metrics](./metrics.md) for built-in metrics documentation.
:::

Custom metrics are either defined in a single `YAML` file, or inside multiple `YAML` files inside a **single** directory.

:::tip NOTE
Examples of custom `YAML` files can be found [here](https://github.com/pgexporter/pgexporter/tree/main/contrib/yaml).
:::

The overall schema for the custom metrics are:
```
YAML = {
  version : number,
  metrics : Metric[]
};

Metric = {
  queries : Query[],
  tag : string,
  collector : string,
  sort : "name" (default) | "data",
  server : "both" (default) | "primary" | "replica",
};

Query = {
  query : string,
  columns : Column[],
  version ?: number
};

Column = Label | Counter | Gauge;

Label = {
  name: string,
  type: "label"
};

Counter = {
  name ?: string,
  type: "counter",
  description: string
};

Gauge = {
  name ?: string,
  type: "gauge",
  description: string
};
```

Custom metrics have to be defined in `yaml` files. There may be a single file or multiple of them (within a **single** directory).

::: tip
Some examples of user-defined metrics can be found [here](https://github.com/pgexporter/pgexporter/tree/main/contrib/yaml) and can be used as a reference while going through this guide.
:::

The structure of these custom `yaml` files can be approached in a top-down manner as follows.

## Top Level
At the top-most level of the `yaml` file, there are two keys `version` and `metrics`:

```yml
version: ...
metrics: ...
```

- `version` specifies a default minimum PostgreSQL support version for the queries (more on this [below](#queries)).
- `metrics` is a list of user defined metrics.

## Metrics

The `metrics` key is a list of metrics and has the following structure:

```yml
...
metrics:

  - queries: ...
    tag: ...
    collector: ...
    sort: ...
    server: ...

  - queries: ...
    tag: ...
    collector: ...
    sort: ...
    server: ...

  - queries: ...
    tag: ...
    collector: ...
    sort: ...
    server: ...
  ...
```

- `queries` are a list of query alternatives (more on this [below](#queries)).
- `tag`: This specifies the tag of the metics (more on this [below](#columns)).
- `collector`: This specifies a `collector` name for the metric. This allows you to disable a collector by using the `-C` flag (see [here](./command_line_flags.md#enable-only-specific-collectors) for details).
- `sort` (*optional*): This specifies how the output of each metric will be sorted. Currently there are two supported values:
  - `name` (*default*): This will sort the output according to server's name.
  - `data`: This will sort the output according to the data of the first column of the SQL query that will be run on the server (more on this [below](#queries)).
- `server` (*optional*): This specifies on which type of server the metric should query. There are three possible values to this:
  - `primary`: This means that this metric is only for primary servers.
  - `replica`: This means that this metric is only for replica servers.
  - `both` (*default*): This means that this metric is for both types of servers.

## Queries

Each `queries` key is an object of the following structure:
```yml
- queries:
  - query: ...
    columns: ...
    version: ...
  - query: ...
    columns: ...
    version: ...
    ...
```

- `query`: Query String for the query alternative (explained [below](#query-selection-based-on-server-version)).
- `version` (*optional*): Minimum PostgreSQL version required to run the query (explained [below](#query-selection-based-on-server-version)). If this value is not provided, then the default is taken from the top level `version`.
- `columns`: List of columns (explained [below](#columns))

There are multiple queries for each metrics. They exist because not all queries are supported across all versions of PostgreSQL. The solution is to provide a query, as well as the minimum version of PostgreSQL it will run on.

Thus `queries` contains multiple entries, each containing a `query` and a minimum PostgreSQL `version` required to run it.

### Query Selection Based On Server Version

Depending on the version of the server, a suitable query is picked. It is picked according to the following rule:

If your server has a version `v`, then it will select the query with the maximum value of `version` that it can find which is also **less than or equal to** `v`.

For example:

::: code-group

```txt [Query Entries]
|Server mininum supported PostgreSQL version|Query|
|-------------------------------------------|-----|
|                  10                       |  Q1 |
|                  12                       |  Q2 |
|                  14                       |  Q3 |
|                  16                       |  Q4 |
|                  18                       |  Q5 |
|                  20                       |  Q6 |
|                  22                       |  Q7 |
```

```txt [Output for different servers]
Server is v9: Not Supported (No query is sent)
Server is v10: Q1 sent
Server is v11: Q1 sent
Server is v12: Q2 sent
Server is v13: Q2 sent
Server is v14: Q3 sent
Server is v15: Q3 sent
Server is v16: Q4 sent
Server is v17: Q4 sent
Server is v18: Q5 sent
Server is v19: Q5 sent
Server is v21: Q6 sent
Server is v25: Q7 sent
```
:::

## Columns

Labels, Gauges, Counters and Histograms are the types of Prometheus metrics currently supported by pgexporter. Histogram metric type is a bit different from the rest:

### Labels, Gauges and Counters

For labels, gauges and counters, `columns` contains a list of columns, which can be either one of the following:

```yml
- name: ...
  type: label
```

or,

```yml
- name: ...
  type: gauge
  description: ...
```

or,

```yml
- name: ...
  type: counter
  description: ...
```

Gauges or Counters do not strictly need names. It will, by default, take the name from the `tag` of the metric like `pgexporter_tag`. However, any `name`s provided will be appended to the `tag` like: `pgexporter_tag_name`, and hence names should be provided when dealing with multiple metrics derived from a single query.

:::warning NOTE
Names are required for distinction when the same metric has more than one counter/gauge as if not provided, all of these will have the same metric name.
:::

### Histograms

## How to Use Custom Metrics

Suppose the user defines their metrics in `custom.yml`, having the path `/location/to/custom.yml`. To run `pgepxorter` with the metrics defined in this file:

```sh
$ pgexporter -c pgexporter.conf -u pgexporter_users.conf -Y /location/to/custom.yml
```

or, if all the custom `yaml` files are kept in a directory having path `/location/to/custom/dir`, `pgexporter` is run as:

```sh
$ pgexporter -c pgexporter.conf -u pgexporter_users.conf -Y /location/to/custom/dir
```

Examples can be refered from [here](https://github.com/pgexporter/pgexporter/tree/main/contrib/yaml).