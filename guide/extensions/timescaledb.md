# timescaledb


Hypertable, chunk, and compression statistics:

**pgexporter_timescaledb_hypertable_overview_total_hypertables**

The total number of hypertables defined in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_timescaledb_hypertable_overview_total_chunks**

The total number of chunks across all hypertables in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_timescaledb_hypertable_overview_compressed_hypertables**

The number of hypertables that have compression enabled.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_timescaledb_hypertable_overview_dimension_types**

Count of hypertables grouped by their dimension types in TimescaleDB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing hypertables. |
| dimension_type | Type of hypertable dimension. |

**pgexporter_timescaledb_job_health_total_jobs**

The total number of TimescaleDB background jobs configured.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_timescaledb_job_health_failed_jobs**

The number of TimescaleDB background jobs that failed on their most recent execution.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_timescaledb_job_health_running_jobs**

Number of currently running background jobs in TimescaleDB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing jobs. |

**pgexporter_timescaledb_job_health_paused_jobs**

Number of paused background jobs in TimescaleDB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing jobs. |

**pgexporter_timescaledb_compression_effectiveness_total_chunks**

Total number of chunks for a TimescaleDB hypertable.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing hypertables. |
| hypertable_schema | Schema containing the hypertable. |
| hypertable_name | Name of the hypertable. |

**pgexporter_timescaledb_compression_effectiveness_compressed_chunks**

Number of compressed chunks for a TimescaleDB hypertable.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing hypertables. |
| hypertable_schema | Schema containing the hypertable. |
| hypertable_name | Name of the hypertable. |

**pgexporter_timescaledb_compression_effectiveness_compression_ratio_pct**

Compression ratio as percentage for TimescaleDB hypertable chunks.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing hypertables. |
| hypertable_schema | Schema containing the hypertable. |
| hypertable_name | Name of the hypertable. |

**pgexporter_timescaledb_compression_effectiveness_avg_chunk_age_days**

Average age in days of compressed chunks in TimescaleDB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing hypertables. |
| hypertable_schema | Schema containing the hypertable. |
| hypertable_name | Name of the hypertable. |

**pgexporter_timescaledb_compression_config_total_compressed_hypertables**

Total number of compressed hypertables in TimescaleDB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing hypertables. |

**pgexporter_timescaledb_compression_config_unique_compressed_hypertables**

Number of unique compressed hypertables in TimescaleDB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing hypertables. |

**pgexporter_timescaledb_columnstore_health_total_columnstore_hypertables**

Total number of columnstore hypertables in TimescaleDB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing hypertables. |

**pgexporter_timescaledb_columnstore_health_unique_columnstore_hypertables**

Number of unique columnstore hypertables in TimescaleDB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing hypertables. |

**pgexporter_timescaledb_recent_job_failures_seconds_since_failure**

Time elapsed in seconds since the most recent job failure in TimescaleDB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing jobs. |
| job_id | TimescaleDB background job identifier. |

**pgexporter_timescaledb_chunk_age_distribution_chunk_count**

Number of chunks in each age category for TimescaleDB hypertables.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing hypertables. |
| age_category | Age category of chunks. |