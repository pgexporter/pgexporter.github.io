# pg_stat_statements


Query performance and execution statistics:

## Table of Contents
- [pgexporter_pg_stat_statements_detailed_io_timing_blk_read_time](#pgexporter-pg-stat-statements-detailed-io-timing-blk-read-time)
- [pgexporter_pg_stat_statements_detailed_io_timing_blk_write_time](#pgexporter-pg-stat-statements-detailed-io-timing-blk-write-time)
- [pgexporter_pg_stat_statements_detailed_io_timing_temp_blk_read_time](#pgexporter-pg-stat-statements-detailed-io-timing-temp-blk-read-time)
- [pgexporter_pg_stat_statements_detailed_io_timing_temp_blk_write_time](#pgexporter-pg-stat-statements-detailed-io-timing-temp-blk-write-time)
- [pgexporter_pg_stat_statements_exec_time_detailed_mean_exec_time](#pgexporter-pg-stat-statements-exec-time-detailed-mean-exec-time)
- [pgexporter_pg_stat_statements_exec_time_detailed_total_exec_time](#pgexporter-pg-stat-statements-exec-time-detailed-total-exec-time)
- [pgexporter_pg_stat_statements_extension_info_tracked_queries](#pgexporter-pg-stat-statements-extension-info-tracked-queries)
- [pgexporter_pg_stat_statements_extension_metadata_dealloc](#pgexporter-pg-stat-statements-extension-metadata-dealloc)
- [pgexporter_pg_stat_statements_hierarchy_performance_avg_mean_exec_time](#pgexporter-pg-stat-statements-hierarchy-performance-avg-mean-exec-time)
- [pgexporter_pg_stat_statements_hierarchy_performance_avg_mean_plan_time](#pgexporter-pg-stat-statements-hierarchy-performance-avg-mean-plan-time)
- [pgexporter_pg_stat_statements_hierarchy_performance_total_wal_bytes](#pgexporter-pg-stat-statements-hierarchy-performance-total-wal-bytes)
- [pgexporter_pg_stat_statements_highest_wal_wal_bytes](#pgexporter-pg-stat-statements-highest-wal-wal-bytes)
- [pgexporter_pg_stat_statements_io_stats_local_blks_read](#pgexporter-pg-stat-statements-io-stats-local-blks-read)
- [pgexporter_pg_stat_statements_io_stats_local_blks_written](#pgexporter-pg-stat-statements-io-stats-local-blks-written)
- [pgexporter_pg_stat_statements_io_stats_shared_blks_hit](#pgexporter-pg-stat-statements-io-stats-shared-blks-hit)
- [pgexporter_pg_stat_statements_io_stats_shared_blks_read](#pgexporter-pg-stat-statements-io-stats-shared-blks-read)
- [pgexporter_pg_stat_statements_io_stats_shared_blks_written](#pgexporter-pg-stat-statements-io-stats-shared-blks-written)
- [pgexporter_pg_stat_statements_io_stats_temp_blks_read](#pgexporter-pg-stat-statements-io-stats-temp-blks-read)
- [pgexporter_pg_stat_statements_io_stats_temp_blks_written](#pgexporter-pg-stat-statements-io-stats-temp-blks-written)
- [pgexporter_pg_stat_statements_io_timing_blk_read_time](#pgexporter-pg-stat-statements-io-timing-blk-read-time)
- [pgexporter_pg_stat_statements_io_timing_blk_write_time](#pgexporter-pg-stat-statements-io-timing-blk-write-time)
- [pgexporter_pg_stat_statements_jit_stats_jit_emission_count](#pgexporter-pg-stat-statements-jit-stats-jit-emission-count)
- [pgexporter_pg_stat_statements_jit_stats_jit_emission_time](#pgexporter-pg-stat-statements-jit-stats-jit-emission-time)
- [pgexporter_pg_stat_statements_jit_stats_jit_functions](#pgexporter-pg-stat-statements-jit-stats-jit-functions)
- [pgexporter_pg_stat_statements_jit_stats_jit_generation_time](#pgexporter-pg-stat-statements-jit-stats-jit-generation-time)
- [pgexporter_pg_stat_statements_jit_stats_jit_inlining_count](#pgexporter-pg-stat-statements-jit-stats-jit-inlining-count)
- [pgexporter_pg_stat_statements_jit_stats_jit_inlining_time](#pgexporter-pg-stat-statements-jit-stats-jit-inlining-time)
- [pgexporter_pg_stat_statements_jit_stats_jit_optimization_count](#pgexporter-pg-stat-statements-jit-stats-jit-optimization-count)
- [pgexporter_pg_stat_statements_jit_stats_jit_optimization_time](#pgexporter-pg-stat-statements-jit-stats-jit-optimization-time)
- [pgexporter_pg_stat_statements_jit_summary_avg_jit_time](#pgexporter-pg-stat-statements-jit-summary-avg-jit-time)
- [pgexporter_pg_stat_statements_jit_summary_jit_enabled_queries](#pgexporter-pg-stat-statements-jit-summary-jit-enabled-queries)
- [pgexporter_pg_stat_statements_jit_summary_total_jit_functions](#pgexporter-pg-stat-statements-jit-summary-total-jit-functions)
- [pgexporter_pg_stat_statements_jit_summary_total_jit_time](#pgexporter-pg-stat-statements-jit-summary-total-jit-time)
- [pgexporter_pg_stat_statements_most_executed_calls](#pgexporter-pg-stat-statements-most-executed-calls)
- [pgexporter_pg_stat_statements_most_planned_plans](#pgexporter-pg-stat-statements-most-planned-plans)
- [pgexporter_pg_stat_statements_most_rows_rows](#pgexporter-pg-stat-statements-most-rows-rows)
- [pgexporter_pg_stat_statements_performance_summary_avg_mean_time](#pgexporter-pg-stat-statements-performance-summary-avg-mean-time)
- [pgexporter_pg_stat_statements_performance_summary_total_calls](#pgexporter-pg-stat-statements-performance-summary-total-calls)
- [pgexporter_pg_stat_statements_performance_summary_total_exec_time](#pgexporter-pg-stat-statements-performance-summary-total-exec-time)
- [pgexporter_pg_stat_statements_performance_summary_total_queries](#pgexporter-pg-stat-statements-performance-summary-total-queries)
- [pgexporter_pg_stat_statements_planning_stats_mean_plan_time](#pgexporter-pg-stat-statements-planning-stats-mean-plan-time)
- [pgexporter_pg_stat_statements_planning_stats_plans](#pgexporter-pg-stat-statements-planning-stats-plans)
- [pgexporter_pg_stat_statements_planning_stats_total_plan_time](#pgexporter-pg-stat-statements-planning-stats-total-plan-time)
- [pgexporter_pg_stat_statements_query_hierarchy_query_count](#pgexporter-pg-stat-statements-query-hierarchy-query-count)
- [pgexporter_pg_stat_statements_query_hierarchy_total_calls](#pgexporter-pg-stat-statements-query-hierarchy-total-calls)
- [pgexporter_pg_stat_statements_query_hierarchy_total_time](#pgexporter-pg-stat-statements-query-hierarchy-total-time)
- [pgexporter_pg_stat_statements_slowest_execution_total_exec_time](#pgexporter-pg-stat-statements-slowest-execution-total-exec-time)

## pgexporter_pg_stat_statements_most_executed_calls

Number of times the most frequently executed SQL query has been called

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_most_planned_plans

Number of times the most frequently planned SQL query has been planned

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_most_rows_rows

Number of rows affected by the SQL query that affects the most rows

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_slowest_execution_total_exec_time

Total execution time in milliseconds for the slowest SQL query

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_highest_wal_wal_bytes

Number of WAL bytes generated by the SQL query with highest WAL usage

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_planning_stats_plans

Number of times the query has been planned.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_planning_stats_total_plan_time

Total planning time for the statement in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_planning_stats_mean_plan_time

Mean planning time for the statement in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_exec_time_detailed_total_exec_time

Total execution time in milliseconds for detailed statement execution analysis.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_exec_time_detailed_mean_exec_time

Mean execution time in milliseconds for detailed statement execution analysis.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_io_stats_shared_blks_hit

Number of shared block cache hits by this statement.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_io_stats_shared_blks_read

From `pg_stat_statements`: total shared blocks read from disk by a specific query.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| queryid | The hash identifier for the normalized query. |
| query | The normalized text of the SQL query. |

## pgexporter_pg_stat_statements_io_stats_shared_blks_written

From `pg_stat_statements`: total shared blocks dirtied and written to disk by a specific query.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| queryid | The hash identifier for the normalized query. |
| query | The normalized text of the SQL query. |

## pgexporter_pg_stat_statements_io_stats_local_blks_read

Number of local block reads by this statement.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_io_stats_local_blks_written

Number of local block writes by this statement.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_io_stats_temp_blks_read

From `pg_stat_statements`: total temporary blocks read from disk by a specific query.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| queryid | The hash identifier for the normalized query. |
| query | The normalized text of the SQL query. |

## pgexporter_pg_stat_statements_io_stats_temp_blks_written

From `pg_stat_statements`: total temporary blocks written to disk by a specific query.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| queryid | The hash identifier for the normalized query. |
| query | The normalized text of the SQL query. |

## pgexporter_pg_stat_statements_io_timing_blk_read_time

Total time spent reading blocks by this statement, in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_io_timing_blk_write_time

Total time spent writing blocks by this statement, in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_performance_summary_total_queries

Total number of distinct normalized statements tracked.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being summarized. |

## pgexporter_pg_stat_statements_performance_summary_total_calls

Total number of calls across all tracked statements.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being summarized. |

## pgexporter_pg_stat_statements_performance_summary_total_exec_time

Total execution time across all tracked statements in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being summarized. |

## pgexporter_pg_stat_statements_performance_summary_avg_mean_time

Average mean execution time across all tracked statements in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being summarized. |

## pgexporter_pg_stat_statements_extension_info_tracked_queries

Total number of distinct normalized SQL statements tracked by pg_stat_statements extension.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

## pgexporter_pg_stat_statements_query_hierarchy_query_count

Number of distinct queries in the hierarchy level.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the queries. |
| toplevel | Whether this is a top-level statement. |

## pgexporter_pg_stat_statements_query_hierarchy_total_calls

Total number of calls for queries in the hierarchy level.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the queries. |
| toplevel | Whether this is a top-level statement. |

## pgexporter_pg_stat_statements_query_hierarchy_total_time

Total execution time for queries in the hierarchy level in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the queries. |
| toplevel | Whether this is a top-level statement. |

## pgexporter_pg_stat_statements_extension_metadata_dealloc

Number of times pg_stat_statements entries were deallocated due to lack of memory.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

## pgexporter_pg_stat_statements_hierarchy_performance_avg_mean_exec_time

Average mean execution time across queries in the performance hierarchy.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the queries. |
| toplevel | Whether this is a top-level statement. |

## pgexporter_pg_stat_statements_hierarchy_performance_avg_mean_plan_time

Average mean planning time across queries in the performance hierarchy.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the queries. |
| toplevel | Whether this is a top-level statement. |

## pgexporter_pg_stat_statements_hierarchy_performance_total_wal_bytes

Total WAL bytes generated by queries in the performance hierarchy.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the queries. |
| toplevel | Whether this is a top-level statement. |

## pgexporter_pg_stat_statements_detailed_io_timing_blk_read_time

Total time spent reading data file blocks by this statement, in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_detailed_io_timing_blk_write_time

Total time spent writing data file blocks by this statement, in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_detailed_io_timing_temp_blk_read_time

Total time spent reading temporary file blocks by this statement, in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_detailed_io_timing_temp_blk_write_time

Total time spent writing temporary file blocks by this statement, in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_jit_stats_jit_functions

Number of functions JIT-compiled for this statement.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_jit_stats_jit_generation_time

Total time spent in JIT code generation for this statement, in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_jit_stats_jit_inlining_count

Number of times JIT inlining was performed for this statement.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_jit_stats_jit_inlining_time

Total time spent in JIT inlining for this statement, in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_jit_stats_jit_optimization_count

Number of times JIT optimization was performed for this statement.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_jit_stats_jit_optimization_time

Total time spent in JIT optimization for this statement, in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_jit_stats_jit_emission_count

Number of times JIT emission was performed for this statement.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_jit_stats_jit_emission_time

Total time spent in JIT emission for this statement, in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the query. |
| queryid | Query identifier. |
| query | The SQL query text. |

## pgexporter_pg_stat_statements_jit_summary_jit_enabled_queries

Reports the number of distinct queries tracked by `pg_stat_statements` that have utilized JIT compilation.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_statements_jit_summary_total_jit_functions

The total number of functions that have been JIT-compiled across all tracked queries.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_statements_jit_summary_total_jit_time

The total cumulative time in milliseconds spent on JIT compilation for all tracked queries.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_statements_jit_summary_avg_jit_time

The average time in milliseconds spent on a single JIT compilation operation.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |