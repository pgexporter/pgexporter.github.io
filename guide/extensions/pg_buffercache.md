# pg_buffercache


Shared buffer cache utilization and effectiveness:

**pgexporter_pg_buffercache_buffer_utilization_total_buffers**

The total number of buffers available in the `shared_buffers` pool, as configured.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_pg_buffercache_buffer_utilization_used_buffers**

The number of buffers in the `shared_buffers` pool that are currently holding data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_pg_buffercache_buffer_utilization_utilization_pct**

The percentage of the `shared_buffers` pool that is currently in use.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_pg_buffercache_dirty_buffers_dirty_buffers**

The number of used buffers that contain modified data (are "dirty") and need to be written to disk.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_pg_buffercache_dirty_buffers_used_buffers**

Number of dirty buffers currently in use in the shared buffer cache.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pg_buffercache_dirty_buffers_dirty_pct**

The percentage of used buffers that are currently dirty.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_pg_buffercache_top_cached_relations_buffer_count**

The number of shared buffers currently used by one of the top N most cached relations.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| relation_name | The name of the table or index. 'unknown' for dropped or unidentifiable relations. |

**pgexporter_pg_buffercache_top_cached_relations_cache_pct**

The percentage of the total used buffer cache that is occupied by one of the top N most cached relations.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| relation_name | The name of the table or index. |

**pgexporter_pg_buffercache_cache_effectiveness_avg_usage_count**

The average `usage_count` for all buffers currently in use, indicating how frequently cached data is being accessed.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_pg_buffercache_cache_effectiveness_high_usage_buffers**

The number of buffers with a high access frequency (usage_count >= 3), indicating "hot" data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_pg_buffercache_cache_effectiveness_low_usage_buffers**

The number of buffers with a low access frequency (usage_count = 1), indicating "cold" data that may be a candidate for eviction.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_pg_buffercache_cache_effectiveness_total_used_buffers**

Total number of used buffers in the shared buffer cache from pg_buffercache extension.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pg_buffercache_cache_pressure_total_buffers**

Total number of buffers in the shared buffer cache.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pg_buffercache_cache_pressure_used_buffers**

Number of used buffers in the shared buffer cache.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pg_buffercache_cache_pressure_dirty_buffers**

Number of dirty (modified) buffers in the shared buffer cache.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pg_buffercache_cache_pressure_pinned_buffers**

The number of buffers currently pinned by active backends, which cannot be evicted.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| pressure_level | A qualitative assessment (LOW, MEDIUM, HIGH) of cache pressure based on utilization. |

**pgexporter_pg_buffercache_usage_distribution_buffers**

A distribution of used buffers, grouped by their `usage_count`, showing how many buffers have been accessed a certain number of times.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| usage_count | The number of times a buffer has been accessed. |

**pgexporter_pg_buffercache_usage_distribution_dirty**

Distribution of dirty buffers across different usage patterns.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| usage_count | Buffer usage count. |

**pgexporter_pg_buffercache_usage_distribution_pinned**

Distribution of pinned buffers across different usage patterns.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| usage_count | Buffer usage count. |