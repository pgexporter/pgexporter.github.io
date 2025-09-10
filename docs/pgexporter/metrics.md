---
outline: deep
---

# `pgexporter` Internal Metrics

The main task of `pgexporter` is to gather metrics from your database and format it according to [Prometheus metrics standards](https://prometheus.io/docs/concepts/metric_types/). `pgexporter` provides some built-in metrics that are necessary/useful, supports extension metrics, and also provides the capability of providing [custom metrics](./custom_metrics.md) to the user.

## Table of Contents
### General
- [pgexporter_state](#pgexporter-state)
- [pgexporter_version](#pgexporter-version)

### Logging
- [pgexporter_logging_error](#pgexporter-logging-error)
- [pgexporter_logging_fatal](#pgexporter-logging-fatal)
- [pgexporter_logging_info](#pgexporter-logging-info)
- [pgexporter_logging_warn](#pgexporter-logging-warn)

### Postgresql
- [pgexporter_pg_available_extensions](#pgexporter-pg-available-extensions)
- [pgexporter_pg_blocked_vacuum_blocked_duration_seconds](#pgexporter-pg-blocked-vacuum-blocked-duration-seconds)
- [pgexporter_pg_blocked_vacuum_blocking_duration_seconds](#pgexporter-pg-blocked-vacuum-blocking-duration-seconds)
- [pgexporter_pg_database_size](#pgexporter-pg-database-size)
- [pgexporter_pg_db_conn](#pgexporter-pg-db-conn)
- [pgexporter_pg_db_conn_ssl](#pgexporter-pg-db-conn-ssl)
- [pgexporter_pg_db_vacuum_age](#pgexporter-pg-db-vacuum-age)
- [pgexporter_pg_encrypted_conn](#pgexporter-pg-encrypted-conn)
- [pgexporter_pg_gss_auth](#pgexporter-pg-gss-auth)
- [pgexporter_pg_gssapi_credentials_delegated](#pgexporter-pg-gssapi-credentials-delegated)
- [pgexporter_pg_indexes](#pgexporter-pg-indexes)
- [pgexporter_pg_installed_extensions](#pgexporter-pg-installed-extensions)
- [pgexporter_pg_locks_count](#pgexporter-pg-locks-count)
- [pgexporter_pg_matviews](#pgexporter-pg-matviews)
- [pgexporter_pg_mem_ctx_contexts](#pgexporter-pg-mem-ctx-contexts)
- [pgexporter_pg_mem_ctx_free_bytes](#pgexporter-pg-mem-ctx-free-bytes)
- [pgexporter_pg_mem_ctx_total_bytes](#pgexporter-pg-mem-ctx-total-bytes)
- [pgexporter_pg_mem_ctx_used_bytes](#pgexporter-pg-mem-ctx-used-bytes)
- [pgexporter_pg_process_idle_seconds](#pgexporter-pg-process-idle-seconds)
- [pgexporter_pg_replication_slots_active](#pgexporter-pg-replication-slots-active)
- [pgexporter_pg_replication_slots_temporary](#pgexporter-pg-replication-slots-temporary)
- [pgexporter_pg_role](#pgexporter-pg-role)
- [pgexporter_pg_rule](#pgexporter-pg-rule)
- [pgexporter_pg_settings_DateStyle](#pgexporter-pg-settings-datestyle)
- [pgexporter_pg_settings_IntervalStyle](#pgexporter-pg-settings-intervalstyle)
- [pgexporter_pg_settings_TimeZone](#pgexporter-pg-settings-timezone)
- [pgexporter_pg_settings_allow_in_place_tablespaces](#pgexporter-pg-settings-allow-in-place-tablespaces)
- [pgexporter_pg_settings_allow_system_table_mods](#pgexporter-pg-settings-allow-system-table-mods)
- [pgexporter_pg_settings_application_name](#pgexporter-pg-settings-application-name)
- [pgexporter_pg_settings_archive_cleanup_command](#pgexporter-pg-settings-archive-cleanup-command)
- [pgexporter_pg_settings_archive_command](#pgexporter-pg-settings-archive-command)
- [pgexporter_pg_settings_archive_library](#pgexporter-pg-settings-archive-library)
- [pgexporter_pg_settings_archive_mode](#pgexporter-pg-settings-archive-mode)
- [pgexporter_pg_settings_archive_timeout](#pgexporter-pg-settings-archive-timeout)
- [pgexporter_pg_settings_array_nulls](#pgexporter-pg-settings-array-nulls)
- [pgexporter_pg_settings_authentication_timeout](#pgexporter-pg-settings-authentication-timeout)
- [pgexporter_pg_settings_autovacuum](#pgexporter-pg-settings-autovacuum)
- [pgexporter_pg_settings_autovacuum_analyze_scale_factor](#pgexporter-pg-settings-autovacuum-analyze-scale-factor)
- [pgexporter_pg_settings_autovacuum_analyze_threshold](#pgexporter-pg-settings-autovacuum-analyze-threshold)
- [pgexporter_pg_settings_autovacuum_freeze_max_age](#pgexporter-pg-settings-autovacuum-freeze-max-age)
- [pgexporter_pg_settings_autovacuum_max_workers](#pgexporter-pg-settings-autovacuum-max-workers)
- [pgexporter_pg_settings_autovacuum_multixact_freeze_max_age](#pgexporter-pg-settings-autovacuum-multixact-freeze-max-age)
- [pgexporter_pg_settings_autovacuum_naptime](#pgexporter-pg-settings-autovacuum-naptime)
- [pgexporter_pg_settings_autovacuum_vacuum_cost_delay](#pgexporter-pg-settings-autovacuum-vacuum-cost-delay)
- [pgexporter_pg_settings_autovacuum_vacuum_cost_limit](#pgexporter-pg-settings-autovacuum-vacuum-cost-limit)
- [pgexporter_pg_settings_autovacuum_vacuum_insert_scale_factor](#pgexporter-pg-settings-autovacuum-vacuum-insert-scale-factor)
- [pgexporter_pg_settings_autovacuum_vacuum_insert_threshold](#pgexporter-pg-settings-autovacuum-vacuum-insert-threshold)
- [pgexporter_pg_settings_autovacuum_vacuum_scale_factor](#pgexporter-pg-settings-autovacuum-vacuum-scale-factor)
- [pgexporter_pg_settings_autovacuum_vacuum_threshold](#pgexporter-pg-settings-autovacuum-vacuum-threshold)
- [pgexporter_pg_settings_autovacuum_work_mem](#pgexporter-pg-settings-autovacuum-work-mem)
- [pgexporter_pg_settings_backend_flush_after](#pgexporter-pg-settings-backend-flush-after)
- [pgexporter_pg_settings_backslash_quote](#pgexporter-pg-settings-backslash-quote)
- [pgexporter_pg_settings_backtrace_functions](#pgexporter-pg-settings-backtrace-functions)
- [pgexporter_pg_settings_bgwriter_delay](#pgexporter-pg-settings-bgwriter-delay)
- [pgexporter_pg_settings_bgwriter_flush_after](#pgexporter-pg-settings-bgwriter-flush-after)
- [pgexporter_pg_settings_bgwriter_lru_maxpages](#pgexporter-pg-settings-bgwriter-lru-maxpages)
- [pgexporter_pg_settings_bgwriter_lru_multiplier](#pgexporter-pg-settings-bgwriter-lru-multiplier)
- [pgexporter_pg_settings_block_size](#pgexporter-pg-settings-block-size)
- [pgexporter_pg_settings_bonjour](#pgexporter-pg-settings-bonjour)
- [pgexporter_pg_settings_bonjour_name](#pgexporter-pg-settings-bonjour-name)
- [pgexporter_pg_settings_bytea_output](#pgexporter-pg-settings-bytea-output)
- [pgexporter_pg_settings_check_function_bodies](#pgexporter-pg-settings-check-function-bodies)
- [pgexporter_pg_settings_checkpoint_completion_target](#pgexporter-pg-settings-checkpoint-completion-target)
- [pgexporter_pg_settings_checkpoint_flush_after](#pgexporter-pg-settings-checkpoint-flush-after)
- [pgexporter_pg_settings_checkpoint_timeout](#pgexporter-pg-settings-checkpoint-timeout)
- [pgexporter_pg_settings_checkpoint_warning](#pgexporter-pg-settings-checkpoint-warning)
- [pgexporter_pg_settings_client_connection_check_interval](#pgexporter-pg-settings-client-connection-check-interval)
- [pgexporter_pg_settings_client_encoding](#pgexporter-pg-settings-client-encoding)
- [pgexporter_pg_settings_client_min_messages](#pgexporter-pg-settings-client-min-messages)
- [pgexporter_pg_settings_cluster_name](#pgexporter-pg-settings-cluster-name)
- [pgexporter_pg_settings_commit_delay](#pgexporter-pg-settings-commit-delay)
- [pgexporter_pg_settings_commit_siblings](#pgexporter-pg-settings-commit-siblings)
- [pgexporter_pg_settings_compute_query_id](#pgexporter-pg-settings-compute-query-id)
- [pgexporter_pg_settings_config_file](#pgexporter-pg-settings-config-file)
- [pgexporter_pg_settings_constraint_exclusion](#pgexporter-pg-settings-constraint-exclusion)
- [pgexporter_pg_settings_cpu_index_tuple_cost](#pgexporter-pg-settings-cpu-index-tuple-cost)
- [pgexporter_pg_settings_cpu_operator_cost](#pgexporter-pg-settings-cpu-operator-cost)
- [pgexporter_pg_settings_cpu_tuple_cost](#pgexporter-pg-settings-cpu-tuple-cost)
- [pgexporter_pg_settings_createrole_self_grant](#pgexporter-pg-settings-createrole-self-grant)
- [pgexporter_pg_settings_cursor_tuple_fraction](#pgexporter-pg-settings-cursor-tuple-fraction)
- [pgexporter_pg_settings_data_checksums](#pgexporter-pg-settings-data-checksums)
- [pgexporter_pg_settings_data_directory](#pgexporter-pg-settings-data-directory)
- [pgexporter_pg_settings_data_directory_mode](#pgexporter-pg-settings-data-directory-mode)
- [pgexporter_pg_settings_data_sync_retry](#pgexporter-pg-settings-data-sync-retry)
- [pgexporter_pg_settings_db_user_namespace](#pgexporter-pg-settings-db-user-namespace)
- [pgexporter_pg_settings_deadlock_timeout](#pgexporter-pg-settings-deadlock-timeout)
- [pgexporter_pg_settings_debug_assertions](#pgexporter-pg-settings-debug-assertions)
- [pgexporter_pg_settings_debug_discard_caches](#pgexporter-pg-settings-debug-discard-caches)
- [pgexporter_pg_settings_debug_io_direct](#pgexporter-pg-settings-debug-io-direct)
- [pgexporter_pg_settings_debug_logical_replication_streaming](#pgexporter-pg-settings-debug-logical-replication-streaming)
- [pgexporter_pg_settings_debug_parallel_query](#pgexporter-pg-settings-debug-parallel-query)
- [pgexporter_pg_settings_debug_pretty_print](#pgexporter-pg-settings-debug-pretty-print)
- [pgexporter_pg_settings_debug_print_parse](#pgexporter-pg-settings-debug-print-parse)
- [pgexporter_pg_settings_debug_print_plan](#pgexporter-pg-settings-debug-print-plan)
- [pgexporter_pg_settings_debug_print_rewritten](#pgexporter-pg-settings-debug-print-rewritten)
- [pgexporter_pg_settings_default_statistics_target](#pgexporter-pg-settings-default-statistics-target)
- [pgexporter_pg_settings_default_table_access_method](#pgexporter-pg-settings-default-table-access-method)
- [pgexporter_pg_settings_default_tablespace](#pgexporter-pg-settings-default-tablespace)
- [pgexporter_pg_settings_default_text_search_config](#pgexporter-pg-settings-default-text-search-config)
- [pgexporter_pg_settings_default_toast_compression](#pgexporter-pg-settings-default-toast-compression)
- [pgexporter_pg_settings_default_transaction_deferrable](#pgexporter-pg-settings-default-transaction-deferrable)
- [pgexporter_pg_settings_default_transaction_isolation](#pgexporter-pg-settings-default-transaction-isolation)
- [pgexporter_pg_settings_default_transaction_read_only](#pgexporter-pg-settings-default-transaction-read-only)
- [pgexporter_pg_settings_dynamic_library_path](#pgexporter-pg-settings-dynamic-library-path)
- [pgexporter_pg_settings_dynamic_shared_memory_type](#pgexporter-pg-settings-dynamic-shared-memory-type)
- [pgexporter_pg_settings_effective_cache_size](#pgexporter-pg-settings-effective-cache-size)
- [pgexporter_pg_settings_effective_io_concurrency](#pgexporter-pg-settings-effective-io-concurrency)
- [pgexporter_pg_settings_enable_async_append](#pgexporter-pg-settings-enable-async-append)
- [pgexporter_pg_settings_enable_bitmapscan](#pgexporter-pg-settings-enable-bitmapscan)
- [pgexporter_pg_settings_enable_gathermerge](#pgexporter-pg-settings-enable-gathermerge)
- [pgexporter_pg_settings_enable_hashagg](#pgexporter-pg-settings-enable-hashagg)
- [pgexporter_pg_settings_enable_hashjoin](#pgexporter-pg-settings-enable-hashjoin)
- [pgexporter_pg_settings_enable_incremental_sort](#pgexporter-pg-settings-enable-incremental-sort)
- [pgexporter_pg_settings_enable_indexonlyscan](#pgexporter-pg-settings-enable-indexonlyscan)
- [pgexporter_pg_settings_enable_indexscan](#pgexporter-pg-settings-enable-indexscan)
- [pgexporter_pg_settings_enable_material](#pgexporter-pg-settings-enable-material)
- [pgexporter_pg_settings_enable_memoize](#pgexporter-pg-settings-enable-memoize)
- [pgexporter_pg_settings_enable_mergejoin](#pgexporter-pg-settings-enable-mergejoin)
- [pgexporter_pg_settings_enable_nestloop](#pgexporter-pg-settings-enable-nestloop)
- [pgexporter_pg_settings_enable_parallel_append](#pgexporter-pg-settings-enable-parallel-append)
- [pgexporter_pg_settings_enable_parallel_hash](#pgexporter-pg-settings-enable-parallel-hash)
- [pgexporter_pg_settings_enable_partition_pruning](#pgexporter-pg-settings-enable-partition-pruning)
- [pgexporter_pg_settings_enable_partitionwise_aggregate](#pgexporter-pg-settings-enable-partitionwise-aggregate)
- [pgexporter_pg_settings_enable_partitionwise_join](#pgexporter-pg-settings-enable-partitionwise-join)
- [pgexporter_pg_settings_enable_presorted_aggregate](#pgexporter-pg-settings-enable-presorted-aggregate)
- [pgexporter_pg_settings_enable_seqscan](#pgexporter-pg-settings-enable-seqscan)
- [pgexporter_pg_settings_enable_sort](#pgexporter-pg-settings-enable-sort)
- [pgexporter_pg_settings_enable_tidscan](#pgexporter-pg-settings-enable-tidscan)
- [pgexporter_pg_settings_escape_string_warning](#pgexporter-pg-settings-escape-string-warning)
- [pgexporter_pg_settings_event_source](#pgexporter-pg-settings-event-source)
- [pgexporter_pg_settings_exit_on_error](#pgexporter-pg-settings-exit-on-error)
- [pgexporter_pg_settings_extension_destdir](#pgexporter-pg-settings-extension-destdir)
- [pgexporter_pg_settings_external_pid_file](#pgexporter-pg-settings-external-pid-file)
- [pgexporter_pg_settings_extra_float_digits](#pgexporter-pg-settings-extra-float-digits)
- [pgexporter_pg_settings_from_collapse_limit](#pgexporter-pg-settings-from-collapse-limit)
- [pgexporter_pg_settings_fsync](#pgexporter-pg-settings-fsync)
- [pgexporter_pg_settings_full_page_writes](#pgexporter-pg-settings-full-page-writes)
- [pgexporter_pg_settings_geqo](#pgexporter-pg-settings-geqo)
- [pgexporter_pg_settings_geqo_effort](#pgexporter-pg-settings-geqo-effort)
- [pgexporter_pg_settings_geqo_generations](#pgexporter-pg-settings-geqo-generations)
- [pgexporter_pg_settings_geqo_pool_size](#pgexporter-pg-settings-geqo-pool-size)
- [pgexporter_pg_settings_geqo_seed](#pgexporter-pg-settings-geqo-seed)
- [pgexporter_pg_settings_geqo_selection_bias](#pgexporter-pg-settings-geqo-selection-bias)
- [pgexporter_pg_settings_geqo_threshold](#pgexporter-pg-settings-geqo-threshold)
- [pgexporter_pg_settings_gin_fuzzy_search_limit](#pgexporter-pg-settings-gin-fuzzy-search-limit)
- [pgexporter_pg_settings_gin_pending_list_limit](#pgexporter-pg-settings-gin-pending-list-limit)
- [pgexporter_pg_settings_gss_accept_delegation](#pgexporter-pg-settings-gss-accept-delegation)
- [pgexporter_pg_settings_hash_mem_multiplier](#pgexporter-pg-settings-hash-mem-multiplier)
- [pgexporter_pg_settings_hba_file](#pgexporter-pg-settings-hba-file)
- [pgexporter_pg_settings_hot_standby](#pgexporter-pg-settings-hot-standby)
- [pgexporter_pg_settings_hot_standby_feedback](#pgexporter-pg-settings-hot-standby-feedback)
- [pgexporter_pg_settings_huge_page_size](#pgexporter-pg-settings-huge-page-size)
- [pgexporter_pg_settings_huge_pages](#pgexporter-pg-settings-huge-pages)
- [pgexporter_pg_settings_icu_validation_level](#pgexporter-pg-settings-icu-validation-level)
- [pgexporter_pg_settings_ident_file](#pgexporter-pg-settings-ident-file)
- [pgexporter_pg_settings_idle_in_transaction_session_timeout](#pgexporter-pg-settings-idle-in-transaction-session-timeout)
- [pgexporter_pg_settings_idle_session_timeout](#pgexporter-pg-settings-idle-session-timeout)
- [pgexporter_pg_settings_ignore_checksum_failure](#pgexporter-pg-settings-ignore-checksum-failure)
- [pgexporter_pg_settings_ignore_invalid_pages](#pgexporter-pg-settings-ignore-invalid-pages)
- [pgexporter_pg_settings_ignore_system_indexes](#pgexporter-pg-settings-ignore-system-indexes)
- [pgexporter_pg_settings_in_hot_standby](#pgexporter-pg-settings-in-hot-standby)
- [pgexporter_pg_settings_integer_datetimes](#pgexporter-pg-settings-integer-datetimes)
- [pgexporter_pg_settings_jit](#pgexporter-pg-settings-jit)
- [pgexporter_pg_settings_jit_above_cost](#pgexporter-pg-settings-jit-above-cost)
- [pgexporter_pg_settings_jit_debugging_support](#pgexporter-pg-settings-jit-debugging-support)
- [pgexporter_pg_settings_jit_dump_bitcode](#pgexporter-pg-settings-jit-dump-bitcode)
- [pgexporter_pg_settings_jit_expressions](#pgexporter-pg-settings-jit-expressions)
- [pgexporter_pg_settings_jit_inline_above_cost](#pgexporter-pg-settings-jit-inline-above-cost)
- [pgexporter_pg_settings_jit_optimize_above_cost](#pgexporter-pg-settings-jit-optimize-above-cost)
- [pgexporter_pg_settings_jit_profiling_support](#pgexporter-pg-settings-jit-profiling-support)
- [pgexporter_pg_settings_jit_provider](#pgexporter-pg-settings-jit-provider)
- [pgexporter_pg_settings_jit_tuple_deforming](#pgexporter-pg-settings-jit-tuple-deforming)
- [pgexporter_pg_settings_join_collapse_limit](#pgexporter-pg-settings-join-collapse-limit)
- [pgexporter_pg_settings_krb_caseins_users](#pgexporter-pg-settings-krb-caseins-users)
- [pgexporter_pg_settings_krb_server_keyfile](#pgexporter-pg-settings-krb-server-keyfile)
- [pgexporter_pg_settings_lc_messages](#pgexporter-pg-settings-lc-messages)
- [pgexporter_pg_settings_lc_monetary](#pgexporter-pg-settings-lc-monetary)
- [pgexporter_pg_settings_lc_numeric](#pgexporter-pg-settings-lc-numeric)
- [pgexporter_pg_settings_lc_time](#pgexporter-pg-settings-lc-time)
- [pgexporter_pg_settings_listen_addresses](#pgexporter-pg-settings-listen-addresses)
- [pgexporter_pg_settings_lo_compat_privileges](#pgexporter-pg-settings-lo-compat-privileges)
- [pgexporter_pg_settings_local_preload_libraries](#pgexporter-pg-settings-local-preload-libraries)
- [pgexporter_pg_settings_lock_timeout](#pgexporter-pg-settings-lock-timeout)
- [pgexporter_pg_settings_log_autovacuum_min_duration](#pgexporter-pg-settings-log-autovacuum-min-duration)
- [pgexporter_pg_settings_log_checkpoints](#pgexporter-pg-settings-log-checkpoints)
- [pgexporter_pg_settings_log_connections](#pgexporter-pg-settings-log-connections)
- [pgexporter_pg_settings_log_destination](#pgexporter-pg-settings-log-destination)
- [pgexporter_pg_settings_log_directory](#pgexporter-pg-settings-log-directory)
- [pgexporter_pg_settings_log_disconnections](#pgexporter-pg-settings-log-disconnections)
- [pgexporter_pg_settings_log_duration](#pgexporter-pg-settings-log-duration)
- [pgexporter_pg_settings_log_error_verbosity](#pgexporter-pg-settings-log-error-verbosity)
- [pgexporter_pg_settings_log_executor_stats](#pgexporter-pg-settings-log-executor-stats)
- [pgexporter_pg_settings_log_file_mode](#pgexporter-pg-settings-log-file-mode)
- [pgexporter_pg_settings_log_filename](#pgexporter-pg-settings-log-filename)
- [pgexporter_pg_settings_log_hostname](#pgexporter-pg-settings-log-hostname)
- [pgexporter_pg_settings_log_line_prefix](#pgexporter-pg-settings-log-line-prefix)
- [pgexporter_pg_settings_log_lock_waits](#pgexporter-pg-settings-log-lock-waits)
- [pgexporter_pg_settings_log_min_duration_sample](#pgexporter-pg-settings-log-min-duration-sample)
- [pgexporter_pg_settings_log_min_duration_statement](#pgexporter-pg-settings-log-min-duration-statement)
- [pgexporter_pg_settings_log_min_error_statement](#pgexporter-pg-settings-log-min-error-statement)
- [pgexporter_pg_settings_log_min_messages](#pgexporter-pg-settings-log-min-messages)
- [pgexporter_pg_settings_log_parameter_max_length](#pgexporter-pg-settings-log-parameter-max-length)
- [pgexporter_pg_settings_log_parameter_max_length_on_error](#pgexporter-pg-settings-log-parameter-max-length-on-error)
- [pgexporter_pg_settings_log_parser_stats](#pgexporter-pg-settings-log-parser-stats)
- [pgexporter_pg_settings_log_planner_stats](#pgexporter-pg-settings-log-planner-stats)
- [pgexporter_pg_settings_log_recovery_conflict_waits](#pgexporter-pg-settings-log-recovery-conflict-waits)
- [pgexporter_pg_settings_log_replication_commands](#pgexporter-pg-settings-log-replication-commands)
- [pgexporter_pg_settings_log_rotation_age](#pgexporter-pg-settings-log-rotation-age)
- [pgexporter_pg_settings_log_rotation_size](#pgexporter-pg-settings-log-rotation-size)
- [pgexporter_pg_settings_log_startup_progress_interval](#pgexporter-pg-settings-log-startup-progress-interval)
- [pgexporter_pg_settings_log_statement](#pgexporter-pg-settings-log-statement)
- [pgexporter_pg_settings_log_statement_sample_rate](#pgexporter-pg-settings-log-statement-sample-rate)
- [pgexporter_pg_settings_log_statement_stats](#pgexporter-pg-settings-log-statement-stats)
- [pgexporter_pg_settings_log_temp_files](#pgexporter-pg-settings-log-temp-files)
- [pgexporter_pg_settings_log_timezone](#pgexporter-pg-settings-log-timezone)
- [pgexporter_pg_settings_log_transaction_sample_rate](#pgexporter-pg-settings-log-transaction-sample-rate)
- [pgexporter_pg_settings_log_truncate_on_rotation](#pgexporter-pg-settings-log-truncate-on-rotation)
- [pgexporter_pg_settings_logging_collector](#pgexporter-pg-settings-logging-collector)
- [pgexporter_pg_settings_logical_decoding_work_mem](#pgexporter-pg-settings-logical-decoding-work-mem)
- [pgexporter_pg_settings_maintenance_io_concurrency](#pgexporter-pg-settings-maintenance-io-concurrency)
- [pgexporter_pg_settings_maintenance_work_mem](#pgexporter-pg-settings-maintenance-work-mem)
- [pgexporter_pg_settings_max_connections](#pgexporter-pg-settings-max-connections)
- [pgexporter_pg_settings_max_files_per_process](#pgexporter-pg-settings-max-files-per-process)
- [pgexporter_pg_settings_max_function_args](#pgexporter-pg-settings-max-function-args)
- [pgexporter_pg_settings_max_identifier_length](#pgexporter-pg-settings-max-identifier-length)
- [pgexporter_pg_settings_max_index_keys](#pgexporter-pg-settings-max-index-keys)
- [pgexporter_pg_settings_max_locks_per_transaction](#pgexporter-pg-settings-max-locks-per-transaction)
- [pgexporter_pg_settings_max_logical_replication_workers](#pgexporter-pg-settings-max-logical-replication-workers)
- [pgexporter_pg_settings_max_parallel_apply_workers_per_subscription](#pgexporter-pg-settings-max-parallel-apply-workers-per-subscription)
- [pgexporter_pg_settings_max_parallel_maintenance_workers](#pgexporter-pg-settings-max-parallel-maintenance-workers)
- [pgexporter_pg_settings_max_parallel_workers](#pgexporter-pg-settings-max-parallel-workers)
- [pgexporter_pg_settings_max_parallel_workers_per_gather](#pgexporter-pg-settings-max-parallel-workers-per-gather)
- [pgexporter_pg_settings_max_pred_locks_per_page](#pgexporter-pg-settings-max-pred-locks-per-page)
- [pgexporter_pg_settings_max_pred_locks_per_relation](#pgexporter-pg-settings-max-pred-locks-per-relation)
- [pgexporter_pg_settings_max_pred_locks_per_transaction](#pgexporter-pg-settings-max-pred-locks-per-transaction)
- [pgexporter_pg_settings_max_prepared_transactions](#pgexporter-pg-settings-max-prepared-transactions)
- [pgexporter_pg_settings_max_replication_slots](#pgexporter-pg-settings-max-replication-slots)
- [pgexporter_pg_settings_max_slot_wal_keep_size](#pgexporter-pg-settings-max-slot-wal-keep-size)
- [pgexporter_pg_settings_max_stack_depth](#pgexporter-pg-settings-max-stack-depth)
- [pgexporter_pg_settings_max_standby_archive_delay](#pgexporter-pg-settings-max-standby-archive-delay)
- [pgexporter_pg_settings_max_standby_streaming_delay](#pgexporter-pg-settings-max-standby-streaming-delay)
- [pgexporter_pg_settings_max_sync_workers_per_subscription](#pgexporter-pg-settings-max-sync-workers-per-subscription)
- [pgexporter_pg_settings_max_wal_senders](#pgexporter-pg-settings-max-wal-senders)
- [pgexporter_pg_settings_max_wal_size](#pgexporter-pg-settings-max-wal-size)
- [pgexporter_pg_settings_max_worker_processes](#pgexporter-pg-settings-max-worker-processes)
- [pgexporter_pg_settings_min_dynamic_shared_memory](#pgexporter-pg-settings-min-dynamic-shared-memory)
- [pgexporter_pg_settings_min_parallel_index_scan_size](#pgexporter-pg-settings-min-parallel-index-scan-size)
- [pgexporter_pg_settings_min_parallel_table_scan_size](#pgexporter-pg-settings-min-parallel-table-scan-size)
- [pgexporter_pg_settings_min_wal_size](#pgexporter-pg-settings-min-wal-size)
- [pgexporter_pg_settings_old_snapshot_threshold](#pgexporter-pg-settings-old-snapshot-threshold)
- [pgexporter_pg_settings_parallel_leader_participation](#pgexporter-pg-settings-parallel-leader-participation)
- [pgexporter_pg_settings_parallel_setup_cost](#pgexporter-pg-settings-parallel-setup-cost)
- [pgexporter_pg_settings_parallel_tuple_cost](#pgexporter-pg-settings-parallel-tuple-cost)
- [pgexporter_pg_settings_password_encryption](#pgexporter-pg-settings-password-encryption)
- [pgexporter_pg_settings_pg_stat_statements_max](#pgexporter-pg-settings-pg-stat-statements-max)
- [pgexporter_pg_settings_pg_stat_statements_save](#pgexporter-pg-settings-pg-stat-statements-save)
- [pgexporter_pg_settings_pg_stat_statements_track](#pgexporter-pg-settings-pg-stat-statements-track)
- [pgexporter_pg_settings_pg_stat_statements_track_planning](#pgexporter-pg-settings-pg-stat-statements-track-planning)
- [pgexporter_pg_settings_pg_stat_statements_track_utility](#pgexporter-pg-settings-pg-stat-statements-track-utility)
- [pgexporter_pg_settings_plan_cache_mode](#pgexporter-pg-settings-plan-cache-mode)
- [pgexporter_pg_settings_port](#pgexporter-pg-settings-port)
- [pgexporter_pg_settings_post_auth_delay](#pgexporter-pg-settings-post-auth-delay)
- [pgexporter_pg_settings_pre_auth_delay](#pgexporter-pg-settings-pre-auth-delay)
- [pgexporter_pg_settings_primary_conninfo](#pgexporter-pg-settings-primary-conninfo)
- [pgexporter_pg_settings_primary_slot_name](#pgexporter-pg-settings-primary-slot-name)
- [pgexporter_pg_settings_quote_all_identifiers](#pgexporter-pg-settings-quote-all-identifiers)
- [pgexporter_pg_settings_random_page_cost](#pgexporter-pg-settings-random-page-cost)
- [pgexporter_pg_settings_recovery_end_command](#pgexporter-pg-settings-recovery-end-command)
- [pgexporter_pg_settings_recovery_init_sync_method](#pgexporter-pg-settings-recovery-init-sync-method)
- [pgexporter_pg_settings_recovery_min_apply_delay](#pgexporter-pg-settings-recovery-min-apply-delay)
- [pgexporter_pg_settings_recovery_prefetch](#pgexporter-pg-settings-recovery-prefetch)
- [pgexporter_pg_settings_recovery_target](#pgexporter-pg-settings-recovery-target)
- [pgexporter_pg_settings_recovery_target_action](#pgexporter-pg-settings-recovery-target-action)
- [pgexporter_pg_settings_recovery_target_inclusive](#pgexporter-pg-settings-recovery-target-inclusive)
- [pgexporter_pg_settings_recovery_target_lsn](#pgexporter-pg-settings-recovery-target-lsn)
- [pgexporter_pg_settings_recovery_target_name](#pgexporter-pg-settings-recovery-target-name)
- [pgexporter_pg_settings_recovery_target_time](#pgexporter-pg-settings-recovery-target-time)
- [pgexporter_pg_settings_recovery_target_timeline](#pgexporter-pg-settings-recovery-target-timeline)
- [pgexporter_pg_settings_recovery_target_xid](#pgexporter-pg-settings-recovery-target-xid)
- [pgexporter_pg_settings_recursive_worktable_factor](#pgexporter-pg-settings-recursive-worktable-factor)
- [pgexporter_pg_settings_remove_temp_files_after_crash](#pgexporter-pg-settings-remove-temp-files-after-crash)
- [pgexporter_pg_settings_reserved_connections](#pgexporter-pg-settings-reserved-connections)
- [pgexporter_pg_settings_restart_after_crash](#pgexporter-pg-settings-restart-after-crash)
- [pgexporter_pg_settings_restore_command](#pgexporter-pg-settings-restore-command)
- [pgexporter_pg_settings_restrict_nonsystem_relation_kind](#pgexporter-pg-settings-restrict-nonsystem-relation-kind)
- [pgexporter_pg_settings_row_security](#pgexporter-pg-settings-row-security)
- [pgexporter_pg_settings_scram_iterations](#pgexporter-pg-settings-scram-iterations)
- [pgexporter_pg_settings_search_path](#pgexporter-pg-settings-search-path)
- [pgexporter_pg_settings_segment_size](#pgexporter-pg-settings-segment-size)
- [pgexporter_pg_settings_send_abort_for_crash](#pgexporter-pg-settings-send-abort-for-crash)
- [pgexporter_pg_settings_send_abort_for_kill](#pgexporter-pg-settings-send-abort-for-kill)
- [pgexporter_pg_settings_seq_page_cost](#pgexporter-pg-settings-seq-page-cost)
- [pgexporter_pg_settings_server_encoding](#pgexporter-pg-settings-server-encoding)
- [pgexporter_pg_settings_server_version](#pgexporter-pg-settings-server-version)
- [pgexporter_pg_settings_server_version_num](#pgexporter-pg-settings-server-version-num)
- [pgexporter_pg_settings_session_preload_libraries](#pgexporter-pg-settings-session-preload-libraries)
- [pgexporter_pg_settings_session_replication_role](#pgexporter-pg-settings-session-replication-role)
- [pgexporter_pg_settings_shared_buffers](#pgexporter-pg-settings-shared-buffers)
- [pgexporter_pg_settings_shared_memory_size](#pgexporter-pg-settings-shared-memory-size)
- [pgexporter_pg_settings_shared_memory_size_in_huge_pages](#pgexporter-pg-settings-shared-memory-size-in-huge-pages)
- [pgexporter_pg_settings_shared_memory_type](#pgexporter-pg-settings-shared-memory-type)
- [pgexporter_pg_settings_shared_preload_libraries](#pgexporter-pg-settings-shared-preload-libraries)
- [pgexporter_pg_settings_ssl](#pgexporter-pg-settings-ssl)
- [pgexporter_pg_settings_ssl_ca_file](#pgexporter-pg-settings-ssl-ca-file)
- [pgexporter_pg_settings_ssl_cert_file](#pgexporter-pg-settings-ssl-cert-file)
- [pgexporter_pg_settings_ssl_ciphers](#pgexporter-pg-settings-ssl-ciphers)
- [pgexporter_pg_settings_ssl_crl_dir](#pgexporter-pg-settings-ssl-crl-dir)
- [pgexporter_pg_settings_ssl_crl_file](#pgexporter-pg-settings-ssl-crl-file)
- [pgexporter_pg_settings_ssl_dh_params_file](#pgexporter-pg-settings-ssl-dh-params-file)
- [pgexporter_pg_settings_ssl_ecdh_curve](#pgexporter-pg-settings-ssl-ecdh-curve)
- [pgexporter_pg_settings_ssl_key_file](#pgexporter-pg-settings-ssl-key-file)
- [pgexporter_pg_settings_ssl_library](#pgexporter-pg-settings-ssl-library)
- [pgexporter_pg_settings_ssl_max_protocol_version](#pgexporter-pg-settings-ssl-max-protocol-version)
- [pgexporter_pg_settings_ssl_min_protocol_version](#pgexporter-pg-settings-ssl-min-protocol-version)
- [pgexporter_pg_settings_ssl_passphrase_command](#pgexporter-pg-settings-ssl-passphrase-command)
- [pgexporter_pg_settings_ssl_passphrase_command_supports_reload](#pgexporter-pg-settings-ssl-passphrase-command-supports-reload)
- [pgexporter_pg_settings_ssl_prefer_server_ciphers](#pgexporter-pg-settings-ssl-prefer-server-ciphers)
- [pgexporter_pg_settings_standard_conforming_strings](#pgexporter-pg-settings-standard-conforming-strings)
- [pgexporter_pg_settings_statement_timeout](#pgexporter-pg-settings-statement-timeout)
- [pgexporter_pg_settings_stats_fetch_consistency](#pgexporter-pg-settings-stats-fetch-consistency)
- [pgexporter_pg_settings_superuser_reserved_connections](#pgexporter-pg-settings-superuser-reserved-connections)
- [pgexporter_pg_settings_synchronize_seqscans](#pgexporter-pg-settings-synchronize-seqscans)
- [pgexporter_pg_settings_synchronous_commit](#pgexporter-pg-settings-synchronous-commit)
- [pgexporter_pg_settings_synchronous_standby_names](#pgexporter-pg-settings-synchronous-standby-names)
- [pgexporter_pg_settings_syslog_facility](#pgexporter-pg-settings-syslog-facility)
- [pgexporter_pg_settings_syslog_ident](#pgexporter-pg-settings-syslog-ident)
- [pgexporter_pg_settings_syslog_sequence_numbers](#pgexporter-pg-settings-syslog-sequence-numbers)
- [pgexporter_pg_settings_syslog_split_messages](#pgexporter-pg-settings-syslog-split-messages)
- [pgexporter_pg_settings_tcp_keepalives_count](#pgexporter-pg-settings-tcp-keepalives-count)
- [pgexporter_pg_settings_tcp_keepalives_idle](#pgexporter-pg-settings-tcp-keepalives-idle)
- [pgexporter_pg_settings_tcp_keepalives_interval](#pgexporter-pg-settings-tcp-keepalives-interval)
- [pgexporter_pg_settings_tcp_user_timeout](#pgexporter-pg-settings-tcp-user-timeout)
- [pgexporter_pg_settings_temp_buffers](#pgexporter-pg-settings-temp-buffers)
- [pgexporter_pg_settings_temp_file_limit](#pgexporter-pg-settings-temp-file-limit)
- [pgexporter_pg_settings_temp_tablespaces](#pgexporter-pg-settings-temp-tablespaces)
- [pgexporter_pg_settings_timescaledb_auto_sparse_indexes](#pgexporter-pg-settings-timescaledb-auto-sparse-indexes)
- [pgexporter_pg_settings_timescaledb_bgw_launcher_poll_time](#pgexporter-pg-settings-timescaledb-bgw-launcher-poll-time)
- [pgexporter_pg_settings_timescaledb_bgw_log_level](#pgexporter-pg-settings-timescaledb-bgw-log-level)
- [pgexporter_pg_settings_timescaledb_bgw_scheduler_restart_time](#pgexporter-pg-settings-timescaledb-bgw-scheduler-restart-time)
- [pgexporter_pg_settings_timescaledb_compress_truncate_behaviour](#pgexporter-pg-settings-timescaledb-compress-truncate-behaviour)
- [pgexporter_pg_settings_timescaledb_compression_batch_size_limit](#pgexporter-pg-settings-timescaledb-compression-batch-size-limit)
- [pgexporter_pg_settings_timescaledb_compression_orderby_default_function](#pgexporter-pg-settings-timescaledb-compression-orderby-default-function)
- [pgexporter_pg_settings_timescaledb_compression_segmentby_default_function](#pgexporter-pg-settings-timescaledb-compression-segmentby-default-function)
- [pgexporter_pg_settings_timescaledb_debug_bgw_scheduler_exit_status](#pgexporter-pg-settings-timescaledb-debug-bgw-scheduler-exit-status)
- [pgexporter_pg_settings_timescaledb_debug_compression_path_info](#pgexporter-pg-settings-timescaledb-debug-compression-path-info)
- [pgexporter_pg_settings_timescaledb_default_hypercore_use_access_method](#pgexporter-pg-settings-timescaledb-default-hypercore-use-access-method)
- [pgexporter_pg_settings_timescaledb_disable_load](#pgexporter-pg-settings-timescaledb-disable-load)
- [pgexporter_pg_settings_timescaledb_enable_bool_compression](#pgexporter-pg-settings-timescaledb-enable-bool-compression)
- [pgexporter_pg_settings_timescaledb_enable_bulk_decompression](#pgexporter-pg-settings-timescaledb-enable-bulk-decompression)
- [pgexporter_pg_settings_timescaledb_enable_cagg_create](#pgexporter-pg-settings-timescaledb-enable-cagg-create)
- [pgexporter_pg_settings_timescaledb_enable_cagg_reorder_groupby](#pgexporter-pg-settings-timescaledb-enable-cagg-reorder-groupby)
- [pgexporter_pg_settings_timescaledb_enable_cagg_sort_pushdown](#pgexporter-pg-settings-timescaledb-enable-cagg-sort-pushdown)
- [pgexporter_pg_settings_timescaledb_enable_cagg_watermark_constify](#pgexporter-pg-settings-timescaledb-enable-cagg-watermark-constify)
- [pgexporter_pg_settings_timescaledb_enable_cagg_window_functions](#pgexporter-pg-settings-timescaledb-enable-cagg-window-functions)
- [pgexporter_pg_settings_timescaledb_enable_chunk_append](#pgexporter-pg-settings-timescaledb-enable-chunk-append)
- [pgexporter_pg_settings_timescaledb_enable_chunk_skipping](#pgexporter-pg-settings-timescaledb-enable-chunk-skipping)
- [pgexporter_pg_settings_timescaledb_enable_chunkwise_aggregation](#pgexporter-pg-settings-timescaledb-enable-chunkwise-aggregation)
- [pgexporter_pg_settings_timescaledb_enable_columnarscan](#pgexporter-pg-settings-timescaledb-enable-columnarscan)
- [pgexporter_pg_settings_timescaledb_enable_compressed_direct_batch_delete](#pgexporter-pg-settings-timescaledb-enable-compressed-direct-batch-delete)
- [pgexporter_pg_settings_timescaledb_enable_compressed_skipscan](#pgexporter-pg-settings-timescaledb-enable-compressed-skipscan)
- [pgexporter_pg_settings_timescaledb_enable_compression_indexscan](#pgexporter-pg-settings-timescaledb-enable-compression-indexscan)
- [pgexporter_pg_settings_timescaledb_enable_compression_ratio_warnings](#pgexporter-pg-settings-timescaledb-enable-compression-ratio-warnings)
- [pgexporter_pg_settings_timescaledb_enable_compression_wal_markers](#pgexporter-pg-settings-timescaledb-enable-compression-wal-markers)
- [pgexporter_pg_settings_timescaledb_enable_compressor_batch_limit](#pgexporter-pg-settings-timescaledb-enable-compressor-batch-limit)
- [pgexporter_pg_settings_timescaledb_enable_constraint_aware_append](#pgexporter-pg-settings-timescaledb-enable-constraint-aware-append)
- [pgexporter_pg_settings_timescaledb_enable_constraint_exclusion](#pgexporter-pg-settings-timescaledb-enable-constraint-exclusion)
- [pgexporter_pg_settings_timescaledb_enable_custom_hashagg](#pgexporter-pg-settings-timescaledb-enable-custom-hashagg)
- [pgexporter_pg_settings_timescaledb_enable_decompression_sorted_merge](#pgexporter-pg-settings-timescaledb-enable-decompression-sorted-merge)
- [pgexporter_pg_settings_timescaledb_enable_delete_after_compression](#pgexporter-pg-settings-timescaledb-enable-delete-after-compression)
- [pgexporter_pg_settings_timescaledb_enable_deprecation_warnings](#pgexporter-pg-settings-timescaledb-enable-deprecation-warnings)
- [pgexporter_pg_settings_timescaledb_enable_dml_decompression](#pgexporter-pg-settings-timescaledb-enable-dml-decompression)
- [pgexporter_pg_settings_timescaledb_enable_dml_decompression_tuple_filtering](#pgexporter-pg-settings-timescaledb-enable-dml-decompression-tuple-filtering)
- [pgexporter_pg_settings_timescaledb_enable_event_triggers](#pgexporter-pg-settings-timescaledb-enable-event-triggers)
- [pgexporter_pg_settings_timescaledb_enable_exclusive_locking_recompression](#pgexporter-pg-settings-timescaledb-enable-exclusive-locking-recompression)
- [pgexporter_pg_settings_timescaledb_enable_foreign_key_propagation](#pgexporter-pg-settings-timescaledb-enable-foreign-key-propagation)
- [pgexporter_pg_settings_timescaledb_enable_hypercore_scankey_pushdown](#pgexporter-pg-settings-timescaledb-enable-hypercore-scankey-pushdown)
- [pgexporter_pg_settings_timescaledb_enable_hypertable_compression](#pgexporter-pg-settings-timescaledb-enable-hypertable-compression)
- [pgexporter_pg_settings_timescaledb_enable_hypertable_create](#pgexporter-pg-settings-timescaledb-enable-hypertable-create)
- [pgexporter_pg_settings_timescaledb_enable_job_execution_logging](#pgexporter-pg-settings-timescaledb-enable-job-execution-logging)
- [pgexporter_pg_settings_timescaledb_enable_merge_on_cagg_refresh](#pgexporter-pg-settings-timescaledb-enable-merge-on-cagg-refresh)
- [pgexporter_pg_settings_timescaledb_enable_now_constify](#pgexporter-pg-settings-timescaledb-enable-now-constify)
- [pgexporter_pg_settings_timescaledb_enable_optimizations](#pgexporter-pg-settings-timescaledb-enable-optimizations)
- [pgexporter_pg_settings_timescaledb_enable_ordered_append](#pgexporter-pg-settings-timescaledb-enable-ordered-append)
- [pgexporter_pg_settings_timescaledb_enable_parallel_chunk_append](#pgexporter-pg-settings-timescaledb-enable-parallel-chunk-append)
- [pgexporter_pg_settings_timescaledb_enable_policy_create](#pgexporter-pg-settings-timescaledb-enable-policy-create)
- [pgexporter_pg_settings_timescaledb_enable_qual_propagation](#pgexporter-pg-settings-timescaledb-enable-qual-propagation)
- [pgexporter_pg_settings_timescaledb_enable_rowlevel_compression_locking](#pgexporter-pg-settings-timescaledb-enable-rowlevel-compression-locking)
- [pgexporter_pg_settings_timescaledb_enable_runtime_exclusion](#pgexporter-pg-settings-timescaledb-enable-runtime-exclusion)
- [pgexporter_pg_settings_timescaledb_enable_segmentwise_recompression](#pgexporter-pg-settings-timescaledb-enable-segmentwise-recompression)
- [pgexporter_pg_settings_timescaledb_enable_skipscan](#pgexporter-pg-settings-timescaledb-enable-skipscan)
- [pgexporter_pg_settings_timescaledb_enable_skipscan_for_distinct_aggregates](#pgexporter-pg-settings-timescaledb-enable-skipscan-for-distinct-aggregates)
- [pgexporter_pg_settings_timescaledb_enable_sparse_index_bloom](#pgexporter-pg-settings-timescaledb-enable-sparse-index-bloom)
- [pgexporter_pg_settings_timescaledb_enable_tiered_reads](#pgexporter-pg-settings-timescaledb-enable-tiered-reads)
- [pgexporter_pg_settings_timescaledb_enable_transparent_decompression](#pgexporter-pg-settings-timescaledb-enable-transparent-decompression)
- [pgexporter_pg_settings_timescaledb_enable_tss_callbacks](#pgexporter-pg-settings-timescaledb-enable-tss-callbacks)
- [pgexporter_pg_settings_timescaledb_enable_vectorized_aggregation](#pgexporter-pg-settings-timescaledb-enable-vectorized-aggregation)
- [pgexporter_pg_settings_timescaledb_hypercore_arrow_cache_max_entries](#pgexporter-pg-settings-timescaledb-hypercore-arrow-cache-max-entries)
- [pgexporter_pg_settings_timescaledb_hypercore_copy_to_behavior](#pgexporter-pg-settings-timescaledb-hypercore-copy-to-behavior)
- [pgexporter_pg_settings_timescaledb_hypercore_indexam_whitelist](#pgexporter-pg-settings-timescaledb-hypercore-indexam-whitelist)
- [pgexporter_pg_settings_timescaledb_lake_disable_load](#pgexporter-pg-settings-timescaledb-lake-disable-load)
- [pgexporter_pg_settings_timescaledb_last_tuned](#pgexporter-pg-settings-timescaledb-last-tuned)
- [pgexporter_pg_settings_timescaledb_last_tuned_version](#pgexporter-pg-settings-timescaledb-last-tuned-version)
- [pgexporter_pg_settings_timescaledb_license](#pgexporter-pg-settings-timescaledb-license)
- [pgexporter_pg_settings_timescaledb_materializations_per_refresh_window](#pgexporter-pg-settings-timescaledb-materializations-per-refresh-window)
- [pgexporter_pg_settings_timescaledb_max_background_workers](#pgexporter-pg-settings-timescaledb-max-background-workers)
- [pgexporter_pg_settings_timescaledb_max_cached_chunks_per_hypertable](#pgexporter-pg-settings-timescaledb-max-cached-chunks-per-hypertable)
- [pgexporter_pg_settings_timescaledb_max_open_chunks_per_insert](#pgexporter-pg-settings-timescaledb-max-open-chunks-per-insert)
- [pgexporter_pg_settings_timescaledb_max_tuples_decompressed_per_dml_transaction](#pgexporter-pg-settings-timescaledb-max-tuples-decompressed-per-dml-transaction)
- [pgexporter_pg_settings_timescaledb_osm_disable_load](#pgexporter-pg-settings-timescaledb-osm-disable-load)
- [pgexporter_pg_settings_timescaledb_restoring](#pgexporter-pg-settings-timescaledb-restoring)
- [pgexporter_pg_settings_timescaledb_skip_scan_run_cost_multiplier](#pgexporter-pg-settings-timescaledb-skip-scan-run-cost-multiplier)
- [pgexporter_pg_settings_timescaledb_telemetry_cloud](#pgexporter-pg-settings-timescaledb-telemetry-cloud)
- [pgexporter_pg_settings_timescaledb_telemetry_level](#pgexporter-pg-settings-timescaledb-telemetry-level)
- [pgexporter_pg_settings_timezone_abbreviations](#pgexporter-pg-settings-timezone-abbreviations)
- [pgexporter_pg_settings_trace_notify](#pgexporter-pg-settings-trace-notify)
- [pgexporter_pg_settings_trace_recovery_messages](#pgexporter-pg-settings-trace-recovery-messages)
- [pgexporter_pg_settings_trace_sort](#pgexporter-pg-settings-trace-sort)
- [pgexporter_pg_settings_track_activities](#pgexporter-pg-settings-track-activities)
- [pgexporter_pg_settings_track_activity_query_size](#pgexporter-pg-settings-track-activity-query-size)
- [pgexporter_pg_settings_track_commit_timestamp](#pgexporter-pg-settings-track-commit-timestamp)
- [pgexporter_pg_settings_track_counts](#pgexporter-pg-settings-track-counts)
- [pgexporter_pg_settings_track_functions](#pgexporter-pg-settings-track-functions)
- [pgexporter_pg_settings_track_io_timing](#pgexporter-pg-settings-track-io-timing)
- [pgexporter_pg_settings_track_wal_io_timing](#pgexporter-pg-settings-track-wal-io-timing)
- [pgexporter_pg_settings_transaction_deferrable](#pgexporter-pg-settings-transaction-deferrable)
- [pgexporter_pg_settings_transaction_isolation](#pgexporter-pg-settings-transaction-isolation)
- [pgexporter_pg_settings_transaction_read_only](#pgexporter-pg-settings-transaction-read-only)
- [pgexporter_pg_settings_transform_null_equals](#pgexporter-pg-settings-transform-null-equals)
- [pgexporter_pg_settings_unix_socket_directories](#pgexporter-pg-settings-unix-socket-directories)
- [pgexporter_pg_settings_unix_socket_group](#pgexporter-pg-settings-unix-socket-group)
- [pgexporter_pg_settings_unix_socket_permissions](#pgexporter-pg-settings-unix-socket-permissions)
- [pgexporter_pg_settings_update_process_title](#pgexporter-pg-settings-update-process-title)
- [pgexporter_pg_settings_vacuum_buffer_usage_limit](#pgexporter-pg-settings-vacuum-buffer-usage-limit)
- [pgexporter_pg_settings_vacuum_cost_delay](#pgexporter-pg-settings-vacuum-cost-delay)
- [pgexporter_pg_settings_vacuum_cost_limit](#pgexporter-pg-settings-vacuum-cost-limit)
- [pgexporter_pg_settings_vacuum_cost_page_dirty](#pgexporter-pg-settings-vacuum-cost-page-dirty)
- [pgexporter_pg_settings_vacuum_cost_page_hit](#pgexporter-pg-settings-vacuum-cost-page-hit)
- [pgexporter_pg_settings_vacuum_cost_page_miss](#pgexporter-pg-settings-vacuum-cost-page-miss)
- [pgexporter_pg_settings_vacuum_failsafe_age](#pgexporter-pg-settings-vacuum-failsafe-age)
- [pgexporter_pg_settings_vacuum_freeze_min_age](#pgexporter-pg-settings-vacuum-freeze-min-age)
- [pgexporter_pg_settings_vacuum_freeze_table_age](#pgexporter-pg-settings-vacuum-freeze-table-age)
- [pgexporter_pg_settings_vacuum_multixact_failsafe_age](#pgexporter-pg-settings-vacuum-multixact-failsafe-age)
- [pgexporter_pg_settings_vacuum_multixact_freeze_min_age](#pgexporter-pg-settings-vacuum-multixact-freeze-min-age)
- [pgexporter_pg_settings_vacuum_multixact_freeze_table_age](#pgexporter-pg-settings-vacuum-multixact-freeze-table-age)
- [pgexporter_pg_settings_wal_block_size](#pgexporter-pg-settings-wal-block-size)
- [pgexporter_pg_settings_wal_buffers](#pgexporter-pg-settings-wal-buffers)
- [pgexporter_pg_settings_wal_compression](#pgexporter-pg-settings-wal-compression)
- [pgexporter_pg_settings_wal_consistency_checking](#pgexporter-pg-settings-wal-consistency-checking)
- [pgexporter_pg_settings_wal_decode_buffer_size](#pgexporter-pg-settings-wal-decode-buffer-size)
- [pgexporter_pg_settings_wal_init_zero](#pgexporter-pg-settings-wal-init-zero)
- [pgexporter_pg_settings_wal_keep_size](#pgexporter-pg-settings-wal-keep-size)
- [pgexporter_pg_settings_wal_level](#pgexporter-pg-settings-wal-level)
- [pgexporter_pg_settings_wal_log_hints](#pgexporter-pg-settings-wal-log-hints)
- [pgexporter_pg_settings_wal_receiver_create_temp_slot](#pgexporter-pg-settings-wal-receiver-create-temp-slot)
- [pgexporter_pg_settings_wal_receiver_status_interval](#pgexporter-pg-settings-wal-receiver-status-interval)
- [pgexporter_pg_settings_wal_receiver_timeout](#pgexporter-pg-settings-wal-receiver-timeout)
- [pgexporter_pg_settings_wal_recycle](#pgexporter-pg-settings-wal-recycle)
- [pgexporter_pg_settings_wal_retrieve_retry_interval](#pgexporter-pg-settings-wal-retrieve-retry-interval)
- [pgexporter_pg_settings_wal_segment_size](#pgexporter-pg-settings-wal-segment-size)
- [pgexporter_pg_settings_wal_sender_timeout](#pgexporter-pg-settings-wal-sender-timeout)
- [pgexporter_pg_settings_wal_skip_threshold](#pgexporter-pg-settings-wal-skip-threshold)
- [pgexporter_pg_settings_wal_sync_method](#pgexporter-pg-settings-wal-sync-method)
- [pgexporter_pg_settings_wal_writer_delay](#pgexporter-pg-settings-wal-writer-delay)
- [pgexporter_pg_settings_wal_writer_flush_after](#pgexporter-pg-settings-wal-writer-flush-after)
- [pgexporter_pg_settings_work_mem](#pgexporter-pg-settings-work-mem)
- [pgexporter_pg_settings_xmlbinary](#pgexporter-pg-settings-xmlbinary)
- [pgexporter_pg_settings_xmloption](#pgexporter-pg-settings-xmloption)
- [pgexporter_pg_settings_zero_damaged_pages](#pgexporter-pg-settings-zero-damaged-pages)
- [pgexporter_pg_shmem_allocations](#pgexporter-pg-shmem-allocations)
- [pgexporter_pg_stat_all_indexes_idx_scans](#pgexporter-pg-stat-all-indexes-idx-scans)
- [pgexporter_pg_stat_all_indexes_idx_tup_fetchs](#pgexporter-pg-stat-all-indexes-idx-tup-fetchs)
- [pgexporter_pg_stat_all_indexes_idx_tup_reads](#pgexporter-pg-stat-all-indexes-idx-tup-reads)
- [pgexporter_pg_stat_all_indexes_time_elapsed_ms](#pgexporter-pg-stat-all-indexes-time-elapsed-ms)
- [pgexporter_pg_stat_archiver_archived_count](#pgexporter-pg-stat-archiver-archived-count)
- [pgexporter_pg_stat_archiver_failed_count](#pgexporter-pg-stat-archiver-failed-count)
- [pgexporter_pg_stat_archiver_failure_time_elapsed_ms](#pgexporter-pg-stat-archiver-failure-time-elapsed-ms)
- [pgexporter_pg_stat_archiver_success_time_elapsed_ms](#pgexporter-pg-stat-archiver-success-time-elapsed-ms)
- [pgexporter_pg_stat_bgwriter_buffers_alloc](#pgexporter-pg-stat-bgwriter-buffers-alloc)
- [pgexporter_pg_stat_bgwriter_buffers_backend](#pgexporter-pg-stat-bgwriter-buffers-backend)
- [pgexporter_pg_stat_bgwriter_buffers_backend_fsync](#pgexporter-pg-stat-bgwriter-buffers-backend-fsync)
- [pgexporter_pg_stat_bgwriter_buffers_checkpoint](#pgexporter-pg-stat-bgwriter-buffers-checkpoint)
- [pgexporter_pg_stat_bgwriter_buffers_clean](#pgexporter-pg-stat-bgwriter-buffers-clean)
- [pgexporter_pg_stat_bgwriter_checkpoint_sync_time](#pgexporter-pg-stat-bgwriter-checkpoint-sync-time)
- [pgexporter_pg_stat_bgwriter_checkpoint_write_time](#pgexporter-pg-stat-bgwriter-checkpoint-write-time)
- [pgexporter_pg_stat_bgwriter_checkpoints_req](#pgexporter-pg-stat-bgwriter-checkpoints-req)
- [pgexporter_pg_stat_bgwriter_checkpoints_timed](#pgexporter-pg-stat-bgwriter-checkpoints-timed)
- [pgexporter_pg_stat_bgwriter_maxwritten_clean](#pgexporter-pg-stat-bgwriter-maxwritten-clean)
- [pgexporter_pg_stat_database_active_time](#pgexporter-pg-stat-database-active-time)
- [pgexporter_pg_stat_database_blk_read_time](#pgexporter-pg-stat-database-blk-read-time)
- [pgexporter_pg_stat_database_blk_write_time](#pgexporter-pg-stat-database-blk-write-time)
- [pgexporter_pg_stat_database_blks_hit](#pgexporter-pg-stat-database-blks-hit)
- [pgexporter_pg_stat_database_blks_read](#pgexporter-pg-stat-database-blks-read)
- [pgexporter_pg_stat_database_checksum_failures](#pgexporter-pg-stat-database-checksum-failures)
- [pgexporter_pg_stat_database_conflicts](#pgexporter-pg-stat-database-conflicts)
- [pgexporter_pg_stat_database_conflicts_confl_active_logicalslot](#pgexporter-pg-stat-database-conflicts-confl-active-logicalslot)
- [pgexporter_pg_stat_database_conflicts_confl_bufferpin](#pgexporter-pg-stat-database-conflicts-confl-bufferpin)
- [pgexporter_pg_stat_database_conflicts_confl_deadlock](#pgexporter-pg-stat-database-conflicts-confl-deadlock)
- [pgexporter_pg_stat_database_conflicts_confl_lock](#pgexporter-pg-stat-database-conflicts-confl-lock)
- [pgexporter_pg_stat_database_conflicts_confl_snapshot](#pgexporter-pg-stat-database-conflicts-confl-snapshot)
- [pgexporter_pg_stat_database_conflicts_confl_tablespace](#pgexporter-pg-stat-database-conflicts-confl-tablespace)
- [pgexporter_pg_stat_database_deadlocks](#pgexporter-pg-stat-database-deadlocks)
- [pgexporter_pg_stat_database_idle_in_transaction_time](#pgexporter-pg-stat-database-idle-in-transaction-time)
- [pgexporter_pg_stat_database_numbackends](#pgexporter-pg-stat-database-numbackends)
- [pgexporter_pg_stat_database_session_time](#pgexporter-pg-stat-database-session-time)
- [pgexporter_pg_stat_database_sessions](#pgexporter-pg-stat-database-sessions)
- [pgexporter_pg_stat_database_sessions_abandoned](#pgexporter-pg-stat-database-sessions-abandoned)
- [pgexporter_pg_stat_database_sessions_fatal](#pgexporter-pg-stat-database-sessions-fatal)
- [pgexporter_pg_stat_database_sessions_killed](#pgexporter-pg-stat-database-sessions-killed)
- [pgexporter_pg_stat_database_temp_bytes](#pgexporter-pg-stat-database-temp-bytes)
- [pgexporter_pg_stat_database_temp_files](#pgexporter-pg-stat-database-temp-files)
- [pgexporter_pg_stat_database_tup_deleted](#pgexporter-pg-stat-database-tup-deleted)
- [pgexporter_pg_stat_database_tup_fetched](#pgexporter-pg-stat-database-tup-fetched)
- [pgexporter_pg_stat_database_tup_inserted](#pgexporter-pg-stat-database-tup-inserted)
- [pgexporter_pg_stat_database_tup_returned](#pgexporter-pg-stat-database-tup-returned)
- [pgexporter_pg_stat_database_tup_updated](#pgexporter-pg-stat-database-tup-updated)
- [pgexporter_pg_stat_database_xact_commit](#pgexporter-pg-stat-database-xact-commit)
- [pgexporter_pg_stat_database_xact_rollback](#pgexporter-pg-stat-database-xact-rollback)
- [pgexporter_pg_stat_io_evictions](#pgexporter-pg-stat-io-evictions)
- [pgexporter_pg_stat_io_extend_time](#pgexporter-pg-stat-io-extend-time)
- [pgexporter_pg_stat_io_extends](#pgexporter-pg-stat-io-extends)
- [pgexporter_pg_stat_io_fsync_time](#pgexporter-pg-stat-io-fsync-time)
- [pgexporter_pg_stat_io_fsyncs](#pgexporter-pg-stat-io-fsyncs)
- [pgexporter_pg_stat_io_hits](#pgexporter-pg-stat-io-hits)
- [pgexporter_pg_stat_io_op_bytes](#pgexporter-pg-stat-io-op-bytes)
- [pgexporter_pg_stat_io_read_time](#pgexporter-pg-stat-io-read-time)
- [pgexporter_pg_stat_io_reads](#pgexporter-pg-stat-io-reads)
- [pgexporter_pg_stat_io_reuses](#pgexporter-pg-stat-io-reuses)
- [pgexporter_pg_stat_io_write_time](#pgexporter-pg-stat-io-write-time)
- [pgexporter_pg_stat_io_writeback_time](#pgexporter-pg-stat-io-writeback-time)
- [pgexporter_pg_stat_io_writebacks](#pgexporter-pg-stat-io-writebacks)
- [pgexporter_pg_stat_io_writes](#pgexporter-pg-stat-io-writes)
- [pgexporter_pg_stat_progress_vacuum_heap_blks_scanned](#pgexporter-pg-stat-progress-vacuum-heap-blks-scanned)
- [pgexporter_pg_stat_progress_vacuum_heap_blks_total](#pgexporter-pg-stat-progress-vacuum-heap-blks-total)
- [pgexporter_pg_stat_progress_vacuum_heap_blks_vacuumed](#pgexporter-pg-stat-progress-vacuum-heap-blks-vacuumed)
- [pgexporter_pg_stat_progress_vacuum_index_vacuum_count](#pgexporter-pg-stat-progress-vacuum-index-vacuum-count)
- [pgexporter_pg_stat_progress_vacuum_max_dead_tuples](#pgexporter-pg-stat-progress-vacuum-max-dead-tuples)
- [pgexporter_pg_stat_progress_vacuum_num_dead_tuples](#pgexporter-pg-stat-progress-vacuum-num-dead-tuples)
- [pgexporter_pg_stat_progress_vacuum_pct_scan_completed](#pgexporter-pg-stat-progress-vacuum-pct-scan-completed)
- [pgexporter_pg_stat_replication](#pgexporter-pg-stat-replication)
- [pgexporter_pg_stat_user_functions_calls](#pgexporter-pg-stat-user-functions-calls)
- [pgexporter_pg_stat_user_functions_self_time](#pgexporter-pg-stat-user-functions-self-time)
- [pgexporter_pg_stat_user_functions_total_time](#pgexporter-pg-stat-user-functions-total-time)
- [pgexporter_pg_stat_user_tables_vacuum_analyze_count](#pgexporter-pg-stat-user-tables-vacuum-analyze-count)
- [pgexporter_pg_stat_user_tables_vacuum_autoanalyze_count](#pgexporter-pg-stat-user-tables-vacuum-autoanalyze-count)
- [pgexporter_pg_stat_user_tables_vacuum_autovacuum_count](#pgexporter-pg-stat-user-tables-vacuum-autovacuum-count)
- [pgexporter_pg_stat_user_tables_vacuum_dead_rows_pct](#pgexporter-pg-stat-user-tables-vacuum-dead-rows-pct)
- [pgexporter_pg_stat_user_tables_vacuum_idx_scan](#pgexporter-pg-stat-user-tables-vacuum-idx-scan)
- [pgexporter_pg_stat_user_tables_vacuum_idx_tup_fetch](#pgexporter-pg-stat-user-tables-vacuum-idx-tup-fetch)
- [pgexporter_pg_stat_user_tables_vacuum_last_analyze_seconds](#pgexporter-pg-stat-user-tables-vacuum-last-analyze-seconds)
- [pgexporter_pg_stat_user_tables_vacuum_last_autoanalyze_seconds](#pgexporter-pg-stat-user-tables-vacuum-last-autoanalyze-seconds)
- [pgexporter_pg_stat_user_tables_vacuum_last_autovacuum_seconds](#pgexporter-pg-stat-user-tables-vacuum-last-autovacuum-seconds)
- [pgexporter_pg_stat_user_tables_vacuum_last_idx_scan_seconds](#pgexporter-pg-stat-user-tables-vacuum-last-idx-scan-seconds)
- [pgexporter_pg_stat_user_tables_vacuum_last_seq_scan_seconds](#pgexporter-pg-stat-user-tables-vacuum-last-seq-scan-seconds)
- [pgexporter_pg_stat_user_tables_vacuum_last_vacuum_seconds](#pgexporter-pg-stat-user-tables-vacuum-last-vacuum-seconds)
- [pgexporter_pg_stat_user_tables_vacuum_n_dead_tup](#pgexporter-pg-stat-user-tables-vacuum-n-dead-tup)
- [pgexporter_pg_stat_user_tables_vacuum_n_ins_since_vacuum](#pgexporter-pg-stat-user-tables-vacuum-n-ins-since-vacuum)
- [pgexporter_pg_stat_user_tables_vacuum_n_live_tup](#pgexporter-pg-stat-user-tables-vacuum-n-live-tup)
- [pgexporter_pg_stat_user_tables_vacuum_n_mod_since_analyze](#pgexporter-pg-stat-user-tables-vacuum-n-mod-since-analyze)
- [pgexporter_pg_stat_user_tables_vacuum_n_tup_del](#pgexporter-pg-stat-user-tables-vacuum-n-tup-del)
- [pgexporter_pg_stat_user_tables_vacuum_n_tup_hot_upd](#pgexporter-pg-stat-user-tables-vacuum-n-tup-hot-upd)
- [pgexporter_pg_stat_user_tables_vacuum_n_tup_ins](#pgexporter-pg-stat-user-tables-vacuum-n-tup-ins)
- [pgexporter_pg_stat_user_tables_vacuum_n_tup_newpage_upd](#pgexporter-pg-stat-user-tables-vacuum-n-tup-newpage-upd)
- [pgexporter_pg_stat_user_tables_vacuum_n_tup_upd](#pgexporter-pg-stat-user-tables-vacuum-n-tup-upd)
- [pgexporter_pg_stat_user_tables_vacuum_seq_scan](#pgexporter-pg-stat-user-tables-vacuum-seq-scan)
- [pgexporter_pg_stat_user_tables_vacuum_seq_tup_read](#pgexporter-pg-stat-user-tables-vacuum-seq-tup-read)
- [pgexporter_pg_stat_user_tables_vacuum_vacuum_count](#pgexporter-pg-stat-user-tables-vacuum-vacuum-count)
- [pgexporter_pg_stat_wal_wal_buffers_full](#pgexporter-pg-stat-wal-wal-buffers-full)
- [pgexporter_pg_stat_wal_wal_bytes](#pgexporter-pg-stat-wal-wal-bytes)
- [pgexporter_pg_stat_wal_wal_fpi](#pgexporter-pg-stat-wal-wal-fpi)
- [pgexporter_pg_stat_wal_wal_records](#pgexporter-pg-stat-wal-wal-records)
- [pgexporter_pg_stat_wal_wal_sync](#pgexporter-pg-stat-wal-wal-sync)
- [pgexporter_pg_stat_wal_wal_sync_time](#pgexporter-pg-stat-wal-wal-sync-time)
- [pgexporter_pg_stat_wal_wal_write](#pgexporter-pg-stat-wal-wal-write)
- [pgexporter_pg_stat_wal_wal_write_time](#pgexporter-pg-stat-wal-wal-write-time)
- [pgexporter_pg_statio_all_sequences_blks_hit](#pgexporter-pg-statio-all-sequences-blks-hit)
- [pgexporter_pg_statio_all_sequences_blks_read](#pgexporter-pg-statio-all-sequences-blks-read)
- [pgexporter_pg_statio_all_tables_heap_blks_hit](#pgexporter-pg-statio-all-tables-heap-blks-hit)
- [pgexporter_pg_statio_all_tables_heap_blks_read](#pgexporter-pg-statio-all-tables-heap-blks-read)
- [pgexporter_pg_statio_all_tables_idx_blks_hit](#pgexporter-pg-statio-all-tables-idx-blks-hit)
- [pgexporter_pg_statio_all_tables_idx_blks_read](#pgexporter-pg-statio-all-tables-idx-blks-read)
- [pgexporter_pg_statio_all_tables_tidx_blks_hit](#pgexporter-pg-statio-all-tables-tidx-blks-hit)
- [pgexporter_pg_statio_all_tables_tidx_blks_read](#pgexporter-pg-statio-all-tables-tidx-blks-read)
- [pgexporter_pg_statio_all_tables_toast_blks_hit](#pgexporter-pg-statio-all-tables-toast-blks-hit)
- [pgexporter_pg_statio_all_tables_toast_blks_read](#pgexporter-pg-statio-all-tables-toast-blks-read)
- [pgexporter_pg_table_bloat_bloat_ratio_pct](#pgexporter-pg-table-bloat-bloat-ratio-pct)
- [pgexporter_pg_table_bloat_bloat_size](#pgexporter-pg-table-bloat-bloat-size)
- [pgexporter_pg_table_bloat_block_size](#pgexporter-pg-table-bloat-block-size)
- [pgexporter_pg_table_bloat_est_tblpages](#pgexporter-pg-table-bloat-est-tblpages)
- [pgexporter_pg_table_bloat_table_size](#pgexporter-pg-table-bloat-table-size)
- [pgexporter_pg_table_bloat_tblpages](#pgexporter-pg-table-bloat-tblpages)
- [pgexporter_pg_view_vacuum_age](#pgexporter-pg-view-vacuum-age)
- [pgexporter_pg_wal_prefetch_reset](#pgexporter-pg-wal-prefetch-reset)
- [pgexporter_postgresql_active](#pgexporter-postgresql-active)
- [pgexporter_postgresql_extension_info](#pgexporter-postgresql-extension-info)
- [pgexporter_postgresql_primary](#pgexporter-postgresql-primary)
- [pgexporter_postgresql_primary](#pgexporter-postgresql-primary)
- [pgexporter_postgresql_uptime](#pgexporter-postgresql-uptime)
- [pgexporter_postgresql_version](#pgexporter-postgresql-version)


## pgexporter_state

Provides the operational status of the pgexporter service itself, indicating if it's running (1) or stopped/failed (0).

| Attribute | Description | Values |
| :-------- | :---------- | :----- |
| server | The configured name/identifier for the PostgreSQL server. | 1: Running, 0: Stopped or encountered a fatal error during startup/runtime |

## pgexporter_logging_info

Counts the total number of informational (INFO level) log messages produced by pgexporter since its last startup.

## pgexporter_logging_warn

Accumulates the total count of warning (WARN level) messages logged by pgexporter, potentially indicating recoverable issues.

## pgexporter_logging_error

Tallies the total number of error (ERROR level) messages from pgexporter, often signaling problems needing investigation.

## pgexporter_logging_fatal

Records the total count of fatal (FATAL level) errors encountered by pgexporter, usually indicating service termination.

## pgexporter_version

Exposes the version of the running pgexporter service through labels.

| Attribute | Description |
| :-------- | :---------- |
| pgexporter_version | The semantic version string of the running pgexporter (e.g., "0.7.0"). |

## pgexporter_postgresql_active

Reports if the monitored PostgreSQL instance is fully active (1) or in a recovery/non-operational state (0).

| Attribute | Description | Values |
| :-------- | :---------- | :----- |
| server | The configured name/identifier for the PostgreSQL server being monitored. | 1: Server is active (not in recovery, accepting connections)., 0: Server is in recovery or otherwise not fully active. |

## pgexporter_postgresql_version

Displays the major and minor version numbers of the monitored PostgreSQL server via labels.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| version | Major PostgreSQL version number (e.g., 16). |
| minor_version | Minor PostgreSQL version number (e.g., 8). |
| Note | The metric value itself is often 1, the version info is in the labels. |

## pgexporter_postgresql_uptime

Measures the uptime of the monitored PostgreSQL server process in seconds since its last start.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_postgresql_primary

Identifies if the monitored PostgreSQL instance is operating as a primary (1, not in recovery) or a standby/replica (0, in recovery).

| Attribute | Description | Values |
| :-------- | :---------- | :----- |
| server | The configured name/identifier for the PostgreSQL server. | 1: This server is the primary (not in recovery)., 0: This server is a replica/standby (in recovery). |

## pgexporter_pg_settings_allow_in_place_tablespaces

Reflects the PostgreSQL `allow_in_place_tablespaces` setting, allowing tablespaces inside pg_tblspc for testing (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_allow_system_table_mods

Represents the PostgreSQL `allow_system_table_mods` setting, permitting structural changes to system tables (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_application_name

Mirrors the PostgreSQL `application_name` setting, which defines the name reported in logs and statistics (value is typically 1, name is not in the metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_archive_cleanup_command

Corresponds to the PostgreSQL `archive_cleanup_command` setting, specifying a shell command executed at each restartpoint (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_archive_command

Represents the PostgreSQL `archive_command` setting, defining the shell command used to archive completed WAL files (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_archive_library

Mirrors the PostgreSQL `archive_library` setting, specifying a shared library for WAL archiving instead of a command (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_archive_mode

Reflects the PostgreSQL `archive_mode` setting, controlling WAL archiving behavior (0=off, 1=on, 2=always).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_archive_timeout

Shows the PostgreSQL `archive_timeout` setting, the maximum time in seconds to wait before forcing a WAL file switch (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_array_nulls

Corresponds to the PostgreSQL `array_nulls` setting, controlling whether NULL elements are allowed in array inputs (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_authentication_timeout

Represents the PostgreSQL `authentication_timeout` setting, the maximum time in seconds allowed for client authentication.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum

Reflects the PostgreSQL `autovacuum` setting, indicating if the autovacuum launcher process is enabled (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_analyze_scale_factor

Shows the PostgreSQL `autovacuum_analyze_scale_factor`, the fraction of table size changes triggering an auto-analyze.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_analyze_threshold

Represents the PostgreSQL `autovacuum_analyze_threshold`, the minimum number of row changes triggering an auto-analyze.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_freeze_max_age

Mirrors the PostgreSQL `autovacuum_freeze_max_age`, the maximum transaction age before forcing autovacuum to prevent TXID wraparound.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_max_workers

Reflects the PostgreSQL `autovacuum_max_workers` setting, the maximum number of concurrent autovacuum worker processes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_multixact_freeze_max_age

Shows the PostgreSQL `autovacuum_multixact_freeze_max_age`, the maximum multixact age before forcing autovacuum to prevent MultiXact wraparound.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_naptime

Represents the PostgreSQL `autovacuum_naptime` setting, the sleep interval in seconds between autovacuum cycles.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_vacuum_cost_delay

Corresponds to the PostgreSQL `autovacuum_vacuum_cost_delay`, the cost delay in milliseconds applied specifically to autovacuum (-1 uses `vacuum_cost_delay`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_vacuum_cost_limit

Mirrors the PostgreSQL `autovacuum_vacuum_cost_limit`, the cost limit applied specifically to autovacuum before sleeping (-1 uses `vacuum_cost_limit`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_vacuum_insert_scale_factor

Reflects the PostgreSQL `autovacuum_vacuum_insert_scale_factor`, the fraction of inserts triggering an insert autovacuum.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_vacuum_insert_threshold

Shows the PostgreSQL `autovacuum_vacuum_insert_threshold`, the minimum number of inserts triggering an insert autovacuum (-1 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_vacuum_scale_factor

Represents the PostgreSQL `autovacuum_vacuum_scale_factor`, the fraction of updates/deletes triggering an autovacuum.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_vacuum_threshold

Corresponds to the PostgreSQL `autovacuum_vacuum_threshold`, the minimum number of updates/deletes triggering an autovacuum.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_autovacuum_work_mem

Mirrors the PostgreSQL `autovacuum_work_mem` setting, the maximum memory in kB per autovacuum worker process (-1 uses `maintenance_work_mem`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_backend_flush_after

Reflects the PostgreSQL `backend_flush_after` setting, the number of pages written by a backend before attempting to flush OS caches (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_backslash_quote

Shows the PostgreSQL `backslash_quote` setting, controlling how `\'` is treated in string literals (0=off, 1=on, 2=safe_encoding).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_backtrace_functions

Represents the PostgreSQL `backtrace_functions` setting, a list of C functions for which to log backtraces on error (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_bgwriter_delay

Corresponds to the PostgreSQL `bgwriter_delay` setting, the sleep time in milliseconds between background writer activity rounds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_bgwriter_flush_after

Mirrors the PostgreSQL `bgwriter_flush_after` setting, the number of pages written by the bgwriter before attempting to flush OS caches (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_bgwriter_lru_maxpages

Reflects the PostgreSQL `bgwriter_lru_maxpages` setting, the maximum number of LRU pages the bgwriter can flush per round.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_bgwriter_lru_multiplier

Shows the PostgreSQL `bgwriter_lru_multiplier`, a factor determining how many dirty buffers the bgwriter aims to clean per round.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_block_size

Displays the fundamental disk block size (in bytes) used by the PostgreSQL server (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_bonjour

Represents the PostgreSQL `bonjour` setting, enabling server advertisement via Bonjour (mDNS) (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_bonjour_name

Corresponds to the PostgreSQL `bonjour_name` setting, specifying the Bonjour service name (defaults to computer name if empty, value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_bytea_output

Mirrors the PostgreSQL `bytea_output` setting, controlling the output format for `bytea` values (1=hex, 2=escape).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_check_function_bodies

Reflects the PostgreSQL `check_function_bodies` setting, enabling validation of function bodies during `CREATE FUNCTION` (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_checkpoint_completion_target

Shows the PostgreSQL `checkpoint_completion_target`, the fraction of the checkpoint interval over which checkpoint writes should be spread.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_checkpoint_flush_after

Represents the PostgreSQL `checkpoint_flush_after` setting, the number of pages written during a checkpoint before attempting to flush OS caches (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_checkpoint_timeout

Corresponds to the PostgreSQL `checkpoint_timeout` setting, the maximum time in seconds between automatic WAL checkpoints.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_checkpoint_warning

Mirrors the PostgreSQL `checkpoint_warning` setting, the time threshold in seconds for warning about checkpoints occurring too frequently (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_client_connection_check_interval

Reflects the PostgreSQL `client_connection_check_interval` setting, the interval in milliseconds for checking client disconnection during queries (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_client_encoding

Shows the PostgreSQL `client_encoding` setting for the connection pgexporter uses (value is typically 1, actual encoding not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_client_min_messages

Represents the PostgreSQL `client_min_messages` setting, the minimum severity level of messages sent to the client (numeric representation, e.g., 1=notice).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_cluster_name

Corresponds to the PostgreSQL `cluster_name` setting, an identifier included in the process title (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_commit_delay

Mirrors the PostgreSQL `commit_delay` setting, a delay in microseconds between commit and WAL flush, potentially allowing group commit.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_commit_siblings

Reflects the PostgreSQL `commit_siblings` setting, the minimum number of concurrent transactions required to activate `commit_delay`.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_compute_query_id

Shows the PostgreSQL `compute_query_id` setting, controlling whether query IDs are computed for monitoring purposes (0=off, 1=on, 2=regress).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_config_file

Represents the PostgreSQL `config_file` setting, the path to the main server configuration file (value 1, path not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_constraint_exclusion

Corresponds to the PostgreSQL `constraint_exclusion` setting, enabling query optimization using CHECK constraints (0=off, 1=partition, 2=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_cpu_index_tuple_cost

Mirrors the PostgreSQL `cpu_index_tuple_cost`, the planner's estimated CPU cost for processing one index entry.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_cpu_operator_cost

Reflects the PostgreSQL `cpu_operator_cost`, the planner's estimated CPU cost for processing one operator or function call.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_cpu_tuple_cost

Shows the PostgreSQL `cpu_tuple_cost`, the planner's estimated CPU cost for processing one tuple (row).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_createrole_self_grant

Represents the PostgreSQL `createrole_self_grant` setting, controlling automatic role granting upon creation (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_cursor_tuple_fraction

Corresponds to the PostgreSQL `cursor_tuple_fraction`, the planner's estimated fraction of rows retrieved from a cursor.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_data_checksums

Indicates if data checksums are enabled for this PostgreSQL cluster (0=off, 1=on, read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_data_directory

Shows the path to the PostgreSQL data directory (value 1, path not in metric, read-only at runtime).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_data_directory_mode

Displays the file system permissions (octal) of the PostgreSQL data directory (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_data_sync_retry

Represents the PostgreSQL `data_sync_retry` setting, whether to continue after a data file sync failure (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_DateStyle

Corresponds to the PostgreSQL `DateStyle` setting, controlling the display format for date/time values (value 1, style not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_db_user_namespace

Mirrors the PostgreSQL `db_user_namespace` setting, enabling per-database usernames (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_deadlock_timeout

Reflects the PostgreSQL `deadlock_timeout` setting, the time in milliseconds to wait on a lock before checking for deadlocks.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_debug_assertions

Shows if the PostgreSQL server was compiled with assertion checks enabled (0=off, 1=on, read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_debug_discard_caches

Represents the PostgreSQL `debug_discard_caches` setting, used for debugging cache behavior (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_debug_io_direct

Corresponds to the PostgreSQL `debug_io_direct` setting, forcing direct I/O usage (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_debug_logical_replication_streaming

Mirrors the PostgreSQL `debug_logical_replication_streaming` setting for logical replication debugging (0=off, 1=on, 2=force_immediate).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_debug_parallel_query

Reflects the PostgreSQL `debug_parallel_query` setting, forcing parallel query plan usage for debugging (0=off, 1=on, 2=regress).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_debug_pretty_print

Shows the PostgreSQL `debug_pretty_print` setting, enabling indented output for debug plan/parse trees (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_debug_print_parse

Represents the PostgreSQL `debug_print_parse` setting, enabling logging of query parse trees (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_debug_print_plan

Corresponds to the PostgreSQL `debug_print_plan` setting, enabling logging of query execution plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_debug_print_rewritten

Mirrors the PostgreSQL `debug_print_rewritten` setting, enabling logging of query rewritten parse trees (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_default_statistics_target

Reflects the PostgreSQL `default_statistics_target`, the default number of samples used by ANALYZE for column statistics.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_default_table_access_method

Shows the PostgreSQL `default_table_access_method` setting for newly created tables (value 1, method name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_default_tablespace

Represents the PostgreSQL `default_tablespace` setting, the default tablespace used if none is specified (value 1 if set, 0 if empty/pg_default).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_default_text_search_config

Corresponds to the PostgreSQL `default_text_search_config` setting, the default configuration for text search functions (value 1, config name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_default_toast_compression

Mirrors the PostgreSQL `default_toast_compression` setting, the default compression method for TOASTable values (1=pglz, 2=lz4).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_default_transaction_deferrable

Reflects the PostgreSQL `default_transaction_deferrable` setting for new transactions (0=off/NOT DEFERRABLE, 1=on/DEFERRABLE).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_default_transaction_isolation

Shows the PostgreSQL `default_transaction_isolation` level for new transactions (numeric representation, e.g., 1 = read committed).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_default_transaction_read_only

Represents the PostgreSQL `default_transaction_read_only` status for new transactions (0=off/read write, 1=on/read only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_dynamic_library_path

Corresponds to the PostgreSQL `dynamic_library_path` setting, the search path for loadable modules (value 1, path not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_dynamic_shared_memory_type

Mirrors the PostgreSQL `dynamic_shared_memory_type` setting, the implementation used for dynamic shared memory (numeric representation, e.g., 1=posix).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_effective_cache_size

Reflects the PostgreSQL `effective_cache_size` setting, the planner's estimate of total available cache memory (in 8kB blocks).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_effective_io_concurrency

Shows the PostgreSQL `effective_io_concurrency` setting, the number of concurrent disk I/O operations the system can handle efficiently.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_async_append

Represents the PostgreSQL `enable_async_append` setting, allowing the planner to use asynchronous append plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_bitmapscan

Corresponds to the PostgreSQL `enable_bitmapscan` setting, allowing the planner to use bitmap index scan plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_gathermerge

Mirrors the PostgreSQL `enable_gathermerge` setting, allowing the planner to use gather merge plans for parallel queries (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_hashagg

Reflects the PostgreSQL `enable_hashagg` setting, allowing the planner to use hash aggregation plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_hashjoin

Shows the PostgreSQL `enable_hashjoin` setting, allowing the planner to use hash join plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_incremental_sort

Represents the PostgreSQL `enable_incremental_sort` setting, allowing the planner to use incremental sort steps (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_indexonlyscan

Corresponds to the PostgreSQL `enable_indexonlyscan` setting, allowing the planner to use index-only scan plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_indexscan

Mirrors the PostgreSQL `enable_indexscan` setting, allowing the planner to use regular index scan plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_material

Reflects the PostgreSQL `enable_material` setting, allowing the planner to use materialization steps (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_memoize

Shows the PostgreSQL `enable_memoize` setting, allowing the planner to use memoization for caching subplan results (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_mergejoin

Represents the PostgreSQL `enable_mergejoin` setting, allowing the planner to use merge join plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_nestloop

Corresponds to the PostgreSQL `enable_nestloop` setting, allowing the planner to use nested loop join plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_parallel_append

Mirrors the PostgreSQL `enable_parallel_append` setting, allowing the planner to use parallel append plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_parallel_hash

Reflects the PostgreSQL `enable_parallel_hash` setting, allowing the planner to use parallel hash join plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_partition_pruning

Shows the PostgreSQL `enable_partition_pruning` setting, enabling partition elimination optimizations (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_partitionwise_aggregate

Represents the PostgreSQL `enable_partitionwise_aggregate` setting, allowing partition-aware aggregation plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_partitionwise_join

Corresponds to the PostgreSQL `enable_partitionwise_join` setting, allowing partition-aware join plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_presorted_aggregate

Mirrors the PostgreSQL `enable_presorted_aggregate` setting, allowing optimization of aggregates with presorted input (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_seqscan

Reflects the PostgreSQL `enable_seqscan` setting, allowing the planner to use sequential scan plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_sort

Shows the PostgreSQL `enable_sort` setting, allowing the planner to use explicit sort steps (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_enable_tidscan

Represents the PostgreSQL `enable_tidscan` setting, allowing the planner to use TID scan plans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_escape_string_warning

Corresponds to the PostgreSQL `escape_string_warning` setting, controlling warnings for backslash escapes in standard strings (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_event_source

Mirrors the PostgreSQL `event_source` setting, the application name used for Windows Event Log messages (value 1, name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_exit_on_error

Reflects the PostgreSQL `exit_on_error` setting, controlling whether a session terminates on any error (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_extension_destdir

Shows the PostgreSQL `extension_destdir` setting, a directory path prepended for extension script loading (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_external_pid_file

Represents the PostgreSQL `external_pid_file` setting, the location of an additional PID file (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_extra_float_digits

Corresponds to the PostgreSQL `extra_float_digits` setting, controlling the number of digits displayed for floating-point numbers.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_from_collapse_limit

Mirrors the PostgreSQL `from_collapse_limit`, the threshold beyond which the planner avoids collapsing subqueries in the FROM list.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_fsync

Reflects the PostgreSQL `fsync` setting, controlling whether updates are physically written to disk using fsync (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_full_page_writes

Shows the PostgreSQL `full_page_writes` setting, determining if full pages are written to WAL after checkpoints (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_geqo

Represents the PostgreSQL `geqo` setting, enabling the Genetic Query Optimizer for large joins (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_geqo_effort

Corresponds to the PostgreSQL `geqo_effort` setting, controlling the trade-off between planning time and query quality for GEQO (range 1-10).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_geqo_generations

Mirrors the PostgreSQL `geqo_generations` setting, the number of iterations used by GEQO (0 uses default).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_geqo_pool_size

Reflects the PostgreSQL `geqo_pool_size` setting, the number of individuals in the GEQO population (0 uses default).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_geqo_seed

Shows the PostgreSQL `geqo_seed` setting, the seed for the random number generator used by GEQO (range 0-1).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_geqo_selection_bias

Represents the PostgreSQL `geqo_selection_bias`, the selective pressure within the GEQO population (range 1.5-2.0).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_geqo_threshold

Corresponds to the PostgreSQL `geqo_threshold`, the number of FROM items triggering the use of GEQO.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_gin_fuzzy_search_limit

Mirrors the PostgreSQL `gin_fuzzy_search_limit`, the maximum result size for exact GIN searches (0 means no limit).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_gin_pending_list_limit

Reflects the PostgreSQL `gin_pending_list_limit`, the maximum size in kB of the pending list for GIN indexes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_gss_accept_delegation

Shows the PostgreSQL `gss_accept_delegation` setting, controlling GSSAPI credential delegation acceptance (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_hash_mem_multiplier

Represents the PostgreSQL `hash_mem_multiplier`, a factor applied to `work_mem` determining memory limits for hash operations.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_hba_file

Corresponds to the PostgreSQL `hba_file` setting, the path to the client authentication configuration file (value 1, path not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_hot_standby

Mirrors the PostgreSQL `hot_standby` setting, enabling connections and queries on a standby server during recovery (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_hot_standby_feedback

Reflects the PostgreSQL `hot_standby_feedback` setting, allowing standby servers to send feedback to the primary to prevent query conflicts (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_huge_page_size

Shows the PostgreSQL `huge_page_size` setting, the requested size in kB for huge pages (0 uses default).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_huge_pages

Represents the PostgreSQL `huge_pages` setting, controlling the use of huge memory pages (0=off, 1=try, 2=require).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_icu_validation_level

Corresponds to the PostgreSQL `icu_validation_level` setting, the log level for reporting invalid ICU locale strings (numeric representation).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ident_file

Mirrors the PostgreSQL `ident_file` setting, the path to the ident authentication configuration file (value 1, path not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_idle_in_transaction_session_timeout

Reflects the PostgreSQL `idle_in_transaction_session_timeout` setting, the maximum idle time in milliseconds allowed within a transaction (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_idle_session_timeout

Shows the PostgreSQL `idle_session_timeout` setting, the maximum idle time in milliseconds allowed outside a transaction (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ignore_checksum_failure

Represents the PostgreSQL `ignore_checksum_failure` setting, determining if processing continues after a data checksum failure (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ignore_invalid_pages

Corresponds to the PostgreSQL `ignore_invalid_pages` setting, whether recovery continues after encountering invalid pages (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ignore_system_indexes

Mirrors the PostgreSQL `ignore_system_indexes` setting, disabling reads from system table indexes for debugging (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_in_hot_standby

Indicates if the server is currently operating in hot standby mode (0=off, 1=on, read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_integer_datetimes

Shows if the PostgreSQL server was built with 64-bit integer datetimes (0=off, 1=on, read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_IntervalStyle

Represents the PostgreSQL `IntervalStyle` setting, controlling the display format for interval values (numeric representation).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_jit

Corresponds to the PostgreSQL `jit` setting, enabling Just-In-Time compilation of queries (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_jit_above_cost

Mirrors the PostgreSQL `jit_above_cost` setting, the query cost threshold above which JIT compilation is attempted (-1 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_jit_debugging_support

Reflects the PostgreSQL `jit_debugging_support` setting, enabling registration of JIT functions with debuggers (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_jit_dump_bitcode

Shows the PostgreSQL `jit_dump_bitcode` setting, enabling output of LLVM bitcode for JIT debugging (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_jit_expressions

Represents the PostgreSQL `jit_expressions` setting, allowing JIT compilation of expressions (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_jit_inline_above_cost

Corresponds to the PostgreSQL `jit_inline_above_cost` setting, the query cost threshold for attempting JIT inlining (-1 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_jit_optimize_above_cost

Mirrors the PostgreSQL `jit_optimize_above_cost` setting, the query cost threshold for attempting JIT optimization (-1 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_jit_profiling_support

Reflects the PostgreSQL `jit_profiling_support` setting, enabling registration of JIT functions with perf profilers (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_jit_provider

Shows the PostgreSQL `jit_provider` setting, the JIT implementation library being used (value 1, provider name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_jit_tuple_deforming

Represents the PostgreSQL `jit_tuple_deforming` setting, allowing JIT compilation for tuple deforming (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_join_collapse_limit

Corresponds to the PostgreSQL `join_collapse_limit`, the FROM-list size threshold beyond which explicit JOIN syntax is not flattened.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_krb_caseins_users

Mirrors the PostgreSQL `krb_caseins_users` setting, controlling case-insensitivity for Kerberos/GSSAPI usernames (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_krb_server_keyfile

Reflects the PostgreSQL `krb_server_keyfile` setting, the location of the Kerberos server keytab file (value 1, path not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_lc_messages

Shows the PostgreSQL `lc_messages` setting, the locale used for message display language (value 1, locale not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_lc_monetary

Represents the PostgreSQL `lc_monetary` setting, the locale used for formatting monetary amounts (value 1, locale not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_lc_numeric

Corresponds to the PostgreSQL `lc_numeric` setting, the locale used for formatting numbers (value 1, locale not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_lc_time

Mirrors the PostgreSQL `lc_time` setting, the locale used for formatting dates and times (value 1, locale not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_listen_addresses

Reflects the PostgreSQL `listen_addresses` setting, the IP addresses or hostnames the server listens on (value 1, addresses not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_lo_compat_privileges

Shows the PostgreSQL `lo_compat_privileges` setting, enabling backward compatibility for large object privilege checks (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_local_preload_libraries

Represents the PostgreSQL `local_preload_libraries` setting, libraries preloaded for non-superuser sessions (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_lock_timeout

Corresponds to the PostgreSQL `lock_timeout` setting, the maximum time in milliseconds to wait for any lock (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_autovacuum_min_duration

Mirrors the PostgreSQL `log_autovacuum_min_duration` setting, the minimum duration in milliseconds for logging autovacuum actions (-1 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_checkpoints

Reflects the PostgreSQL `log_checkpoints` setting, enabling logging of checkpoint start and end times (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_connections

Shows the PostgreSQL `log_connections` setting, enabling logging of successful client connections (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_destination

Represents the PostgreSQL `log_destination` setting, controlling where server logs are sent (value 1, destinations not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_directory

Corresponds to the PostgreSQL `log_directory` setting, the directory for log files when logging to files (value 1, path not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_disconnections

Mirrors the PostgreSQL `log_disconnections` setting, enabling logging of session disconnections and duration (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_duration

Reflects the PostgreSQL `log_duration` setting, enabling logging of the duration for every completed statement (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_error_verbosity

Shows the PostgreSQL `log_error_verbosity` setting, controlling the detail level of logged messages (numeric representation: 1=default, 2=verbose, 3=terse).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_executor_stats

Represents the PostgreSQL `log_executor_stats` setting, enabling logging of executor performance statistics (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_file_mode

Corresponds to the PostgreSQL `log_file_mode` setting, the file permissions (octal) for newly created log files.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_filename

Mirrors the PostgreSQL `log_filename` setting, the pattern for log file names (value 1, pattern not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_hostname

Reflects the PostgreSQL `log_hostname` setting, including the client hostname in connection logs (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_line_prefix

Shows the PostgreSQL `log_line_prefix` setting, a format string defining the prefix for each log line (value 1, format not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_lock_waits

Represents the PostgreSQL `log_lock_waits` setting, enabling logging when a session waits longer than `deadlock_timeout` for a lock (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_min_duration_sample

Corresponds to the PostgreSQL `log_min_duration_sample` setting, the minimum duration (ms) for sampled statement logging (-1 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_min_duration_statement

Mirrors the PostgreSQL `log_min_duration_statement` setting, the minimum statement duration (ms) to log unconditionally (-1 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_min_error_statement

Reflects the PostgreSQL `log_min_error_statement`, the minimum error severity level that causes the statement text to be logged (numeric representation).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_min_messages

Shows the PostgreSQL `log_min_messages` setting, the minimum message severity level written to the server log (numeric representation).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_parameter_max_length

Represents the PostgreSQL `log_parameter_max_length`, the maximum length (bytes) of bind parameters logged with statements (-1 unlimited, 0 disable).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_parameter_max_length_on_error

Corresponds to the PostgreSQL `log_parameter_max_length_on_error`, the maximum length (bytes) of bind parameters logged on error (-1 unlimited, 0 disable).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_parser_stats

Mirrors the PostgreSQL `log_parser_stats` setting, enabling logging of parser performance statistics (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_planner_stats

Reflects the PostgreSQL `log_planner_stats` setting, enabling logging of planner performance statistics (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_recovery_conflict_waits

Shows the PostgreSQL `log_recovery_conflict_waits` setting, enabling logging of waits due to recovery conflicts on standby (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_replication_commands

Represents the PostgreSQL `log_replication_commands` setting, enabling logging of each replication command (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_rotation_age

Corresponds to the PostgreSQL `log_rotation_age` setting, the maximum age (minutes) of a log file before rotation (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_rotation_size

Mirrors the PostgreSQL `log_rotation_size` setting, the maximum size (kB) of a log file before rotation (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_startup_progress_interval

Reflects the PostgreSQL `log_startup_progress_interval` setting, the interval (ms) for logging long-running startup operation progress (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_statement

Shows the PostgreSQL `log_statement` setting, controlling which SQL statements are logged (numeric representation: 1=none, 2=ddl, 3=mod, 4=all).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_statement_sample_rate

Represents the PostgreSQL `log_statement_sample_rate`, the fraction (0-1) of long statements (above sample threshold) to log.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_statement_stats

Corresponds to the PostgreSQL `log_statement_stats` setting, enabling logging of cumulative statement performance statistics (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_temp_files

Mirrors the PostgreSQL `log_temp_files` setting, logging temporary files larger than this size in kB (-1 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_timezone

Reflects the PostgreSQL `log_timezone` setting, the time zone used for timestamps in server logs (value 1, zone name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_transaction_sample_rate

Shows the PostgreSQL `log_transaction_sample_rate`, the fraction (0-1) of transactions for which all statements are logged (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_log_truncate_on_rotation

Represents the PostgreSQL `log_truncate_on_rotation` setting, controlling whether log files are truncated or appended upon rotation (0=off/append, 1=on/truncate).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_logging_collector

Corresponds to the PostgreSQL `logging_collector` setting, enabling a dedicated process to capture log output (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_logical_decoding_work_mem

Mirrors the PostgreSQL `logical_decoding_work_mem` setting, the maximum memory in kB used for logical decoding operations.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_maintenance_io_concurrency

Reflects the PostgreSQL `maintenance_io_concurrency` setting, the `effective_io_concurrency` value used specifically for maintenance tasks.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_maintenance_work_mem

Shows the PostgreSQL `maintenance_work_mem` setting, the maximum memory in kB used for maintenance operations like VACUUM and CREATE INDEX.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_connections

Represents the PostgreSQL `max_connections` setting, the maximum number of concurrent client connections allowed.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_files_per_process

Corresponds to the PostgreSQL `max_files_per_process` setting, the maximum number of open files allowed per server process.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_function_args

Displays the maximum number of arguments allowed in a function definition (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_identifier_length

Shows the maximum length in bytes allowed for identifiers (e.g., table names, column names) (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_index_keys

Displays the maximum number of columns allowed in an index definition (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_locks_per_transaction

Reflects the PostgreSQL `max_locks_per_transaction` setting, controlling the average number of object locks allocated per transaction.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_logical_replication_workers

Shows the PostgreSQL `max_logical_replication_workers` setting, the maximum number of logical replication worker processes system-wide.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_parallel_apply_workers_per_subscription

Represents the PostgreSQL `max_parallel_apply_workers_per_subscription` setting, the maximum parallel workers for logical replication apply per subscription.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_parallel_maintenance_workers

Corresponds to the PostgreSQL `max_parallel_maintenance_workers` setting, the maximum parallel workers usable by a single utility command.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_parallel_workers

Mirrors the PostgreSQL `max_parallel_workers` setting, the maximum total number of parallel workers available system-wide.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_parallel_workers_per_gather

Reflects the PostgreSQL `max_parallel_workers_per_gather` setting, the maximum parallel workers usable by a single Gather or Gather Merge node.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_pred_locks_per_page

Shows the PostgreSQL `max_pred_locks_per_page` setting, controlling predicate lock allocation per page for serializable transactions.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_pred_locks_per_relation

Represents the PostgreSQL `max_pred_locks_per_relation` setting, controlling predicate lock allocation per relation for serializable transactions.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_pred_locks_per_transaction

Corresponds to the PostgreSQL `max_pred_locks_per_transaction` setting, controlling predicate lock allocation per transaction for serializable transactions.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_prepared_transactions

Mirrors the PostgreSQL `max_prepared_transactions` setting, the maximum number of transactions that can be in the prepared state simultaneously (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_replication_slots

Reflects the PostgreSQL `max_replication_slots` setting, the maximum number of replication slots that can exist concurrently.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_slot_wal_keep_size

Shows the PostgreSQL `max_slot_wal_keep_size` setting, the maximum total size in MB of WAL files retained by replication slots (-1 unlimited).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_stack_depth

Represents the PostgreSQL `max_stack_depth` setting, the maximum safe stack depth in kilobytes for server processes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_standby_archive_delay

Corresponds to the PostgreSQL `max_standby_archive_delay`, the maximum delay (ms) for canceling standby queries conflicting with WAL archive processing (-1 indefinite).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_standby_streaming_delay

Mirrors the PostgreSQL `max_standby_streaming_delay`, the maximum delay (ms) for canceling standby queries conflicting with WAL streaming (-1 indefinite).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_sync_workers_per_subscription

Reflects the PostgreSQL `max_sync_workers_per_subscription` setting, the maximum number of synchronization workers per logical replication subscription.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_wal_senders

Shows the PostgreSQL `max_wal_senders` setting, the maximum number of concurrent WAL sender processes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_wal_size

Represents the PostgreSQL `max_wal_size` setting, the target maximum total WAL size in MB that triggers a checkpoint.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_max_worker_processes

Corresponds to the PostgreSQL `max_worker_processes` setting, the maximum number of background worker processes the system can support.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_min_dynamic_shared_memory

Mirrors the PostgreSQL `min_dynamic_shared_memory` setting, the amount of dynamic shared memory in MB reserved at startup (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_min_parallel_index_scan_size

Reflects the PostgreSQL `min_parallel_index_scan_size`, the minimum index size (in 8kB blocks) to consider for a parallel scan.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_min_parallel_table_scan_size

Shows the PostgreSQL `min_parallel_table_scan_size`, the minimum table size (in 8kB blocks) to consider for a parallel scan.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_min_wal_size

Represents the PostgreSQL `min_wal_size` setting, the minimum total WAL size in MB to maintain.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_old_snapshot_threshold

Corresponds to the PostgreSQL `old_snapshot_threshold`, the minimum time (minutes) a snapshot can be used without risk of snapshot too old errors (-1 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_parallel_leader_participation

Mirrors the PostgreSQL `parallel_leader_participation` setting, allowing the leader process to execute parallel plan nodes (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_parallel_setup_cost

Reflects the PostgreSQL `parallel_setup_cost`, the planner's estimated cost of launching parallel worker processes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_parallel_tuple_cost

Shows the PostgreSQL `parallel_tuple_cost`, the planner's estimated cost of transferring one tuple between parallel workers.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_password_encryption

Represents the PostgreSQL `password_encryption` algorithm used for `CREATE/ALTER USER` (numeric representation: 1=scram-sha-256, 2=md5).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_pg_stat_statements_max

Reflects the PostgreSQL `pg_stat_statements.max` setting, the maximum number of statements tracked by pg_stat_statements extension.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_pg_stat_statements_save

Reflects the PostgreSQL `pg_stat_statements.save` setting, whether pg_stat_statements saves statistics across server shutdowns.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_pg_stat_statements_track

Reflects the PostgreSQL `pg_stat_statements.track` setting, which statements are tracked by pg_stat_statements.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_pg_stat_statements_track_planning

Reflects the PostgreSQL `pg_stat_statements.track_planning` setting, whether planning statistics are collected.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_pg_stat_statements_track_utility

Reflects the PostgreSQL `pg_stat_statements.track_utility` setting, whether utility commands are tracked.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_plan_cache_mode

Corresponds to the PostgreSQL `plan_cache_mode`, influencing when generic vs. custom plans are used for prepared statements (numeric representation: 1=auto, 2=force_custom, 3=force_generic).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_port

Displays the TCP port number the PostgreSQL server is listening on.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_post_auth_delay

Mirrors the PostgreSQL `post_auth_delay` setting, an artificial delay in seconds introduced after successful authentication.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_pre_auth_delay

Reflects the PostgreSQL `pre_auth_delay` setting, an artificial delay in seconds introduced before authentication begins.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_primary_conninfo

Shows the PostgreSQL `primary_conninfo` setting, the connection string used by a standby to connect to the primary (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_primary_slot_name

Represents the PostgreSQL `primary_slot_name` setting, the replication slot name used on the primary by a standby (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_quote_all_identifiers

Corresponds to the PostgreSQL `quote_all_identifiers` setting, forcing all identifiers to be quoted in SQL output, e.g., by `pg_dump` (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_random_page_cost

Mirrors the PostgreSQL `random_page_cost`, the planner's estimated cost of fetching a disk page non-sequentially.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_end_command

Reflects the PostgreSQL `recovery_end_command`, a shell command executed once at the successful completion of recovery (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_init_sync_method

Shows the PostgreSQL `recovery_init_sync_method`, how data files are synced before recovery starts (numeric representation: 1=fsync, 2=syncfs).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_min_apply_delay

Represents the PostgreSQL `recovery_min_apply_delay`, a minimum delay in milliseconds applied before replaying WAL records during recovery (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_prefetch

Corresponds to the PostgreSQL `recovery_prefetch` setting, enabling block prefetching during recovery (0=off, 1=on, 2=try).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_target

Mirrors the PostgreSQL `recovery_target` setting, currently only supports 'immediate' to stop recovery upon reaching consistency (value 1 if set to 'immediate', 0 otherwise).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_target_action

Reflects the PostgreSQL `recovery_target_action`, the server action upon reaching the recovery target (numeric representation: 1=pause, 2=promote, 3=shutdown).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_target_inclusive

Shows the PostgreSQL `recovery_target_inclusive` setting, controlling whether recovery stops just before (0=off) or just after (1=on) the target.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_target_lsn

Represents the PostgreSQL `recovery_target_lsn`, the LSN determining the recovery stop point (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_target_name

Corresponds to the PostgreSQL `recovery_target_name`, a named restore point determining the recovery stop point (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_target_time

Mirrors the PostgreSQL `recovery_target_time`, a timestamp determining the recovery stop point (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_target_timeline

Reflects the PostgreSQL `recovery_target_timeline`, specifying the timeline to recover into (numeric representation: 1=current, 2=latest).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recovery_target_xid

Shows the PostgreSQL `recovery_target_xid`, a transaction ID determining the recovery stop point (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_recursive_worktable_factor

Represents the PostgreSQL `recursive_worktable_factor`, the planner's estimate of recursive query working table size relative to non-recursive term size.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_remove_temp_files_after_crash

Corresponds to the PostgreSQL `remove_temp_files_after_crash` setting, controlling automatic cleanup of temporary files post-crash (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_reserved_connections

Mirrors the PostgreSQL `reserved_connections` setting, the number of connection slots reserved for roles having `pg_use_reserved_connections`.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_restart_after_crash

Reflects the PostgreSQL `restart_after_crash` setting, determining if the server automatically restarts after a backend crash (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_restore_command

Shows the PostgreSQL `restore_command`, the shell command used to fetch archived WAL files during recovery (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_restrict_nonsystem_relation_kind

Represents the PostgreSQL `restrict_nonsystem_relation_kind` setting, prohibiting access to specific non-system relation types (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_row_security

Corresponds to the PostgreSQL `row_security` setting, enabling row-level security policy enforcement (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_scram_iterations

Mirrors the PostgreSQL `scram_iterations` setting, the iteration count used for SCRAM password hashing.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_search_path

Reflects the PostgreSQL `search_path` setting, the order of schemas searched for unqualified object names (value 1, path not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_segment_size

Displays the number of blocks constituting a single disk file segment (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_send_abort_for_crash

Shows the PostgreSQL `send_abort_for_crash` setting, sending SIGABRT instead of SIGQUIT to children after a crash (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_send_abort_for_kill

Represents the PostgreSQL `send_abort_for_kill` setting, sending SIGABRT instead of SIGKILL to stuck children (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_seq_page_cost

Corresponds to the PostgreSQL `seq_page_cost`, the planner's estimated cost of fetching a disk page sequentially.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_server_encoding

Displays the character set encoding of the database server (value 1, encoding name not in metric, read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_server_version

Shows the PostgreSQL server version string (value 1, version string not in metric, read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_server_version_num

Displays the PostgreSQL server version as a numeric integer (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_session_preload_libraries

Reflects the PostgreSQL `session_preload_libraries` setting, libraries preloaded at the start of each session (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_session_replication_role

Shows the PostgreSQL `session_replication_role` setting, controlling trigger and rule firing behavior (numeric representation: 1=origin, 2=replica, 3=local).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_shared_buffers

Represents the PostgreSQL `shared_buffers` setting, indicating the amount of memory dedicated to the shared buffer cache (in 8kB blocks).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_shared_memory_size

Displays the total size in MB of the server's main shared memory area (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_shared_memory_size_in_huge_pages

Shows the estimated number of huge pages required for the main shared memory area (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_shared_memory_type

Corresponds to the PostgreSQL `shared_memory_type` setting for the main shared memory region (numeric representation: 1=mmap, 2=sysv, 3=windows).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_shared_preload_libraries

Mirrors the PostgreSQL `shared_preload_libraries` setting, libraries preloaded at server start (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl

Reflects the PostgreSQL `ssl` setting, enabling SSL/TLS encrypted connections (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_ca_file

Shows the PostgreSQL `ssl_ca_file` setting, the path to the SSL Certificate Authority file (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_cert_file

Represents the PostgreSQL `ssl_cert_file` setting, the path to the server's SSL certificate file (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_ciphers

Corresponds to the PostgreSQL `ssl_ciphers` setting, the list of allowed SSL/TLS cipher suites (value 1, list not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_crl_dir

Mirrors the PostgreSQL `ssl_crl_dir` setting, the path to the directory containing SSL Certificate Revocation Lists (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_crl_file

Reflects the PostgreSQL `ssl_crl_file` setting, the path to the SSL Certificate Revocation List file (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_dh_params_file

Shows the PostgreSQL `ssl_dh_params_file` setting, the path to the Diffie-Hellman parameters file for SSL (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_ecdh_curve

Represents the PostgreSQL `ssl_ecdh_curve` setting, the curve used for ECDH key exchange (value 1, curve name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_key_file

Corresponds to the PostgreSQL `ssl_key_file` setting, the path to the server's SSL private key file (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_library

Displays the name of the underlying SSL library being used (e.g., OpenSSL) (value 1, name not in metric, read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_max_protocol_version

Mirrors the PostgreSQL `ssl_max_protocol_version` setting, the maximum allowed SSL/TLS protocol version (numeric representation, 0=default).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_min_protocol_version

Reflects the PostgreSQL `ssl_min_protocol_version` setting, the minimum allowed SSL/TLS protocol version (numeric representation, 0=default).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_passphrase_command

Shows the PostgreSQL `ssl_passphrase_command` setting, an external command to retrieve SSL key passphrases (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_passphrase_command_supports_reload

Represents the PostgreSQL `ssl_passphrase_command_supports_reload` setting, indicating if the passphrase command is re-run on reload (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_ssl_prefer_server_ciphers

Corresponds to the PostgreSQL `ssl_prefer_server_ciphers` setting, preferring the server's cipher order during SSL negotiation (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_standard_conforming_strings

Mirrors the PostgreSQL `standard_conforming_strings` setting, controlling whether backslashes are treated literally in standard strings (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_statement_timeout

Reflects the PostgreSQL `statement_timeout` setting, the maximum execution time in milliseconds for any single statement (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_stats_fetch_consistency

Shows the PostgreSQL `stats_fetch_consistency` setting, controlling consistency guarantees when fetching statistics (numeric representation: 1=none, 2=cache, 3=snapshot).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_superuser_reserved_connections

Represents the PostgreSQL `superuser_reserved_connections` setting, the number of connection slots reserved exclusively for superusers.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_synchronize_seqscans

Corresponds to the PostgreSQL `synchronize_seqscans` setting, enabling synchronized sequential scans to potentially start reads at the same block (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_synchronous_commit

Mirrors the PostgreSQL `synchronous_commit` setting, the level of transaction commit synchronization (numeric representation, e.g., 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_synchronous_standby_names

Reflects the PostgreSQL `synchronous_standby_names` setting, the list defining synchronous standby servers (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_syslog_facility

Shows the PostgreSQL `syslog_facility` setting used when logging to syslog (numeric representation of facility).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_syslog_ident

Represents the PostgreSQL `syslog_ident` setting, the program identification string used in syslog messages (value 1, ident name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_syslog_sequence_numbers

Corresponds to the PostgreSQL `syslog_sequence_numbers` setting, adding sequence numbers to syslog messages (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_syslog_split_messages

Mirrors the PostgreSQL `syslog_split_messages` setting, splitting long syslog messages into multiple lines (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_tcp_keepalives_count

Reflects the PostgreSQL `tcp_keepalives_count` setting, the number of TCP keepalive retransmits before considering the connection dead (0 uses system default).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_tcp_keepalives_idle

Shows the PostgreSQL `tcp_keepalives_idle` setting, the idle time in seconds before sending a TCP keepalive probe (0 uses system default).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_tcp_keepalives_interval

Represents the PostgreSQL `tcp_keepalives_interval` setting, the time in seconds between TCP keepalive retransmits (0 uses system default).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_tcp_user_timeout

Corresponds to the PostgreSQL `tcp_user_timeout` setting, the TCP user timeout in milliseconds (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_temp_buffers

Mirrors the PostgreSQL `temp_buffers` setting, the maximum amount of memory (in 8kB blocks) used for temporary buffers per session.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_temp_file_limit

Reflects the PostgreSQL `temp_file_limit` setting, the maximum total size in kB of temporary files usable per process (-1 unlimited).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_temp_tablespaces

Shows the PostgreSQL `temp_tablespaces` setting, the list of tablespaces used for temporary objects (value 1 if set, 0 if empty/default).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_auto_sparse_indexes

Reflects the TimescaleDB `timescaledb.auto_sparse_indexes` setting, automatically creating sparse indexes on compressed chunks (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_bgw_launcher_poll_time

Represents the TimescaleDB `timescaledb.bgw_launcher_poll_time` setting, the polling interval in milliseconds for the background worker launcher.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_bgw_log_level

Corresponds to the TimescaleDB `timescaledb.bgw_log_level` setting, the log level for TimescaleDB background workers (numeric representation).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_bgw_scheduler_restart_time

Mirrors the TimescaleDB `timescaledb.bgw_scheduler_restart_time` setting, the restart delay in seconds for the job scheduler if it crashes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_compress_truncate_behaviour

Reflects the TimescaleDB `timescaledb.compress_truncate_behaviour` setting for compression truncation behavior.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_compression_batch_size_limit

Reflects the TimescaleDB `timescaledb.compression_batch_size_limit` setting for compression batch size limits.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_compression_orderby_default_function

Reflects the TimescaleDB `timescaledb.compression_orderby_default_function` setting, the function defining default `ORDER BY` columns for compression (value 1, function name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_compression_segmentby_default_function

Shows the TimescaleDB `timescaledb.compression_segmentby_default_function` setting, the function defining default `SEGMENT BY` columns for compression (value 1, function name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_debug_bgw_scheduler_exit_status

Represents the TimescaleDB `timescaledb.debug_bgw_scheduler_exit_status` setting, a debug parameter controlling the scheduler's exit code.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_debug_compression_path_info

Corresponds to the TimescaleDB `timescaledb.debug_compression_path_info` setting, enabling debug output for compression planning (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_default_hypercore_use_access_method

Mirrors the TimescaleDB `timescaledb.default_hypercore_use_access_method` setting, forcing usage of Hypercore TAM for compression (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_disable_load

Reflects the TimescaleDB `timescaledb.disable_load` setting, preventing the TimescaleDB extension from loading (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_bool_compression

Reflects the TimescaleDB `timescaledb.enable_bool_compression` setting for boolean compression.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_bulk_decompression

Shows the TimescaleDB `timescaledb.enable_bulk_decompression` setting, enabling optimized decompression of entire batches (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_cagg_create

Represents the TimescaleDB `timescaledb.enable_cagg_create` setting, allowing the creation of continuous aggregates (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_cagg_reorder_groupby

Corresponds to the TimescaleDB `timescaledb.enable_cagg_reorder_groupby` setting, enabling GROUP BY clause reordering optimization for CAGGs (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_cagg_sort_pushdown

Mirrors the TimescaleDB `timescaledb.enable_cagg_sort_pushdown` setting, enabling sort pushdown optimization for continuous aggregates (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_cagg_watermark_constify

Reflects the TimescaleDB `timescaledb.enable_cagg_watermark_constify` setting, enabling optimization of CAGG watermarks (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_cagg_window_functions

Reflects the TimescaleDB `timescaledb.enable_cagg_window_functions` setting for continuous aggregate window functions.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_chunk_append

Shows the TimescaleDB `timescaledb.enable_chunk_append` setting, enabling the custom ChunkAppend plan node (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_chunk_skipping

Represents the TimescaleDB `timescaledb.enable_chunk_skipping` setting, enabling skipping of unnecessary chunks during scans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_chunkwise_aggregation

Corresponds to the TimescaleDB `timescaledb.enable_chunkwise_aggregation` setting, enabling aggregation performed per-chunk (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_columnarscan

Mirrors the TimescaleDB `timescaledb.enable_columnarscan` setting, enabling columnar-optimized scans when applicable (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_compressed_direct_batch_delete

Reflects the TimescaleDB `timescaledb.enable_compressed_direct_batch_delete` setting, enabling optimized deletion of entire compressed batches (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_compressed_skipscan

Reflects the TimescaleDB `timescaledb.enable_compressed_skipscan` setting for compressed skip scan optimization.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_compression_indexscan

Shows the TimescaleDB `timescaledb.enable_compression_indexscan` setting, allowing index scans during compression operations (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_compression_ratio_warnings

Reflects the TimescaleDB `timescaledb.enable_compression_ratio_warnings` setting for compression ratio warnings.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_compression_wal_markers

Represents the TimescaleDB `timescaledb.enable_compression_wal_markers` setting, adding WAL markers for compression operations (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_compressor_batch_limit

Reflects the TimescaleDB `timescaledb.enable_compressor_batch_limit` setting for compressor batch limits.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_constraint_aware_append

Corresponds to the TimescaleDB `timescaledb.enable_constraint_aware_append` setting, enabling append plans that use constraints for pruning (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_constraint_exclusion

Mirrors the TimescaleDB `timescaledb.enable_constraint_exclusion` setting, enabling TimescaleDB-specific constraint exclusion (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_custom_hashagg

Reflects the TimescaleDB `timescaledb.enable_custom_hashagg` setting, enabling custom hash aggregation optimizations (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_decompression_sorted_merge

Shows the TimescaleDB `timescaledb.enable_decompression_sorted_merge` setting, enabling sorted merge for decompressed batches (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_delete_after_compression

Represents the TimescaleDB `timescaledb.enable_delete_after_compression` setting, using DELETE instead of TRUNCATE after compressing a chunk (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_deprecation_warnings

Corresponds to the TimescaleDB `timescaledb.enable_deprecation_warnings` setting, issuing warnings for deprecated features (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_dml_decompression

Mirrors the TimescaleDB `timescaledb.enable_dml_decompression` setting, enabling on-the-fly decompression for DML operations on compressed chunks (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_dml_decompression_tuple_filtering

Reflects the TimescaleDB `timescaledb.enable_dml_decompression_tuple_filtering` setting, enabling tuple filtering during DML decompression (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_event_triggers

Reflects the TimescaleDB `timescaledb.enable_event_triggers` setting for event triggers.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_exclusive_locking_recompression

Reflects the TimescaleDB `timescaledb.enable_exclusive_locking_recompression` setting for exclusive locking during recompression.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_foreign_key_propagation

Shows the TimescaleDB `timescaledb.enable_foreign_key_propagation` setting, enabling propagation of foreign key constraints to chunks (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_hypercore_scankey_pushdown

Represents the TimescaleDB `timescaledb.enable_hypercore_scankey_pushdown` setting, pushing down qualifiers to Hypercore TAM scans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_hypertable_compression

Corresponds to the TimescaleDB `timescaledb.enable_hypertable_compression` setting, allowing compression features to be used (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_hypertable_create

Mirrors the TimescaleDB `timescaledb.enable_hypertable_create` setting, allowing the creation of new hypertables (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_job_execution_logging

Reflects the TimescaleDB `timescaledb.enable_job_execution_logging` setting, enabling logging for background job executions (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_merge_on_cagg_refresh

Shows the TimescaleDB `timescaledb.enable_merge_on_cagg_refresh` setting, enabling use of MERGE statements during CAGG refresh (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_now_constify

Represents the TimescaleDB `timescaledb.enable_now_constify` setting, enabling optimization of `now()` calls in queries (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_optimizations

Corresponds to the TimescaleDB `timescaledb.enable_optimizations` setting, the master switch for enabling most TimescaleDB query optimizations (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_ordered_append

Mirrors the TimescaleDB `timescaledb.enable_ordered_append` setting, enabling optimized append plans that preserve sort order (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_parallel_chunk_append

Reflects the TimescaleDB `timescaledb.enable_parallel_chunk_append` setting, enabling parallel execution of ChunkAppend nodes (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_policy_create

Shows the TimescaleDB `timescaledb.enable_policy_create` setting, allowing creation of automation policies (e.g., compression, retention) (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_qual_propagation

Represents the TimescaleDB `timescaledb.enable_qual_propagation` setting, enabling propagation of query qualifiers down plan trees (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_rowlevel_compression_locking

Corresponds to the TimescaleDB `timescaledb.enable_rowlevel_compression_locking` setting, using row-level locks during compression (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_runtime_exclusion

Mirrors the TimescaleDB `timescaledb.enable_runtime_exclusion` setting, enabling chunk exclusion based on runtime parameters (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_segmentwise_recompression

Reflects the TimescaleDB `timescaledb.enable_segmentwise_recompression` setting, enabling recompression of individual segments (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_skipscan

Shows the TimescaleDB `timescaledb.enable_skipscan` setting, enabling SkipScan optimization for certain index scans (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_skipscan_for_distinct_aggregates

Reflects the TimescaleDB `timescaledb.enable_skipscan_for_distinct_aggregates` setting for skip scan optimization in distinct aggregates.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_sparse_index_bloom

Reflects the TimescaleDB `timescaledb.enable_sparse_index_bloom` setting for sparse index bloom filters.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_tiered_reads

Represents the TimescaleDB `timescaledb.enable_tiered_reads` setting, enabling queries against tiered storage (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_transparent_decompression

Corresponds to the TimescaleDB `timescaledb.enable_transparent_decompression` setting, automatically decompressing data during SELECT queries (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_tss_callbacks

Mirrors the TimescaleDB `timescaledb.enable_tss_callbacks` setting, enabling callbacks for `ts_stat_statements` (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_enable_vectorized_aggregation

Reflects the TimescaleDB `timescaledb.enable_vectorized_aggregation` setting, enabling vectorized aggregation optimizations (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_hypercore_arrow_cache_max_entries

Reflects the TimescaleDB `timescaledb.hypercore_arrow_cache_max_entries` setting for Arrow cache size.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_hypercore_copy_to_behavior

Shows the TimescaleDB `timescaledb.hypercore_copy_to_behavior` setting, controlling `COPY TO` behavior for Hypercore tables (numeric representation).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_hypercore_indexam_whitelist

Represents the TimescaleDB `timescaledb.hypercore_indexam_whitelist`, a list of index access methods compatible with Hypercore (value 1, list not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_last_tuned

Corresponds to the TimescaleDB `timescaledb.last_tuned` setting, the timestamp of the last `timescaledb-tune` execution (value 1, timestamp not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_last_tuned_version

Mirrors the TimescaleDB `timescaledb.last_tuned_version` setting, the version of `timescaledb-tune` last used (value 1, version not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_license

Reflects the TimescaleDB `timescaledb.license` key currently active (value 1, key type not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_materializations_per_refresh_window

Shows the TimescaleDB `timescaledb.materializations_per_refresh_window` setting, the maximum number of materializations per CAGG refresh window.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_max_background_workers

Represents the TimescaleDB `timescaledb.max_background_workers` setting, the maximum number of background workers TimescaleDB can use.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_max_cached_chunks_per_hypertable

Corresponds to the TimescaleDB `timescaledb.max_cached_chunks_per_hypertable` setting, the limit on cached chunk metadata per hypertable.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_max_open_chunks_per_insert

Mirrors the TimescaleDB `timescaledb.max_open_chunks_per_insert` setting, the maximum number of chunks kept open concurrently during inserts.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_max_tuples_decompressed_per_dml_transaction

Reflects the TimescaleDB `timescaledb.max_tuples_decompressed_per_dml_transaction` setting, the limit on tuples decompressed per DML transaction.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_restoring

Shows the TimescaleDB `timescaledb.restoring` setting, indicating if the extension is operating in restore mode (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_skip_scan_run_cost_multiplier

Reflects the TimescaleDB `timescaledb.skip_scan_run_cost_multiplier` setting for skip scan cost calculation.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_telemetry_level

Represents the TimescaleDB `timescaledb.telemetry_level` setting, controlling the level of telemetry data sent (numeric representation: 1=basic, 2=off).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_lake_disable_load

Reflects the TimescaleDB `timescaledb.lake_disable_load` setting for disabling lake loading.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_osm_disable_load

Reflects the TimescaleDB OpenStreetMap `timescaledb_osm.disable_load` setting, preventing the OSM extension from loading (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timescaledb_telemetry_cloud

Corresponds to the TimescaleDB `timescaledb.telemetry.cloud` setting, identifying the cloud provider environment if applicable (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_TimeZone

Mirrors the PostgreSQL `TimeZone` setting, the time zone used for displaying and interpreting timestamps (value 1, zone name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_timezone_abbreviations

Reflects the PostgreSQL `timezone_abbreviations` setting, specifying the file containing time zone abbreviations (value 1, file name not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_trace_notify

Shows the PostgreSQL `trace_notify` setting, enabling debug output for LISTEN/NOTIFY operations (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_trace_recovery_messages

Represents the PostgreSQL `trace_recovery_messages` setting, the minimum severity level for logging recovery-related debug messages (numeric representation).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_trace_sort

Corresponds to the PostgreSQL `trace_sort` setting, enabling logging of resource usage during sort operations (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_track_activities

Mirrors the PostgreSQL `track_activities` setting, enabling collection of current command information for active sessions (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_track_activity_query_size

Reflects the PostgreSQL `track_activity_query_size` setting, the size in bytes reserved for storing active query text in `pg_stat_activity`.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_track_commit_timestamp

Shows the PostgreSQL `track_commit_timestamp` setting, enabling tracking of transaction commit timestamps (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_track_counts

Represents the PostgreSQL `track_counts` setting, enabling collection of table and index access statistics (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_track_functions

Corresponds to the PostgreSQL `track_functions` setting, controlling the level of function execution statistics tracking (numeric representation: 1=none, 2=pl, 3=all).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_track_io_timing

Mirrors the PostgreSQL `track_io_timing` setting, enabling collection of timing data for block I/O operations (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_track_wal_io_timing

Reflects the PostgreSQL `track_wal_io_timing` setting, enabling collection of timing data for WAL I/O operations (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_transaction_deferrable

Shows the PostgreSQL `transaction_deferrable` setting for the current transaction, allowing deferral of serializable read-only transactions (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_transaction_isolation

Represents the PostgreSQL `transaction_isolation` level for the current transaction (numeric representation, e.g., 1=read committed).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_transaction_read_only

Corresponds to the PostgreSQL `transaction_read_only` status for the current transaction (0=off/read write, 1=on/read only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_transform_null_equals

Mirrors the PostgreSQL `transform_null_equals` setting, treating `expr = NULL` as `expr IS NULL` (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_unix_socket_directories

Reflects the PostgreSQL `unix_socket_directories` setting, the directory paths for Unix-domain sockets (value 1, paths not in metric).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_unix_socket_group

Shows the PostgreSQL `unix_socket_group` setting, the group owner for Unix-domain sockets (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_unix_socket_permissions

Represents the PostgreSQL `unix_socket_permissions` setting, the access permissions (octal) for Unix-domain sockets.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_update_process_title

Corresponds to the PostgreSQL `update_process_title` setting, enabling updates to the process title to show the active command (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_buffer_usage_limit

Mirrors the PostgreSQL `vacuum_buffer_usage_limit` setting, the size in kB of the special buffer pool used by VACUUM/ANALYZE.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_cost_delay

Reflects the PostgreSQL `vacuum_cost_delay`, the duration in milliseconds that VACUUM pauses when its cost limit is reached.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_cost_limit

Shows the PostgreSQL `vacuum_cost_limit`, the accumulated cost that causes VACUUM to pause.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_cost_page_dirty

Represents the PostgreSQL `vacuum_cost_page_dirty`, the estimated cost for vacuuming a block that requires modification.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_cost_page_hit

Corresponds to the PostgreSQL `vacuum_cost_page_hit`, the estimated cost for vacuuming a block already in shared buffers.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_cost_page_miss

Mirrors the PostgreSQL `vacuum_cost_page_miss`, the estimated cost for vacuuming a block that must be read from disk.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_failsafe_age

Reflects the PostgreSQL `vacuum_failsafe_age`, the transaction age triggering an emergency VACUUM to prevent wraparound.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_freeze_min_age

Shows the PostgreSQL `vacuum_freeze_min_age`, the minimum transaction age before VACUUM considers freezing a tuple.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_freeze_table_age

Represents the PostgreSQL `vacuum_freeze_table_age`, the transaction age triggering a full table scan by VACUUM to freeze tuples.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_multixact_failsafe_age

Corresponds to the PostgreSQL `vacuum_multixact_failsafe_age`, the multixact age triggering an emergency VACUUM to prevent wraparound.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_multixact_freeze_min_age

Mirrors the PostgreSQL `vacuum_multixact_freeze_min_age`, the minimum multixact age before VACUUM considers freezing a tuple's multixact ID.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_vacuum_multixact_freeze_table_age

Reflects the PostgreSQL `vacuum_multixact_freeze_table_age`, the multixact age triggering a full table scan by VACUUM to freeze multixact IDs.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_block_size

Displays the block size in bytes used within WAL files (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_buffers

Shows the PostgreSQL `wal_buffers` setting, the amount of shared memory (in 8kB blocks) used for WAL data before writing to disk (-1 auto-tuned).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_compression

Represents the PostgreSQL `wal_compression` setting, enabling compression of full-page images written to WAL (0=off, 1=pglz, 2=lz4, 3=zstd).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_consistency_checking

Corresponds to the PostgreSQL `wal_consistency_checking` setting, enabling checks for specific WAL record types (value 1 if set, 0 if empty).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_decode_buffer_size

Mirrors the PostgreSQL `wal_decode_buffer_size` setting, the buffer size in bytes for WAL reading during recovery.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_init_zero

Reflects the PostgreSQL `wal_init_zero` setting, controlling whether new WAL files are pre-filled with zeros (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_keep_size

Shows the PostgreSQL `wal_keep_size` setting, the minimum total size in MB of past WAL files kept for standby servers.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_level

Represents the PostgreSQL `wal_level` setting, the amount of information written to WAL (numeric representation: 1=minimal, 2=replica, 3=logical).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_log_hints

Corresponds to the PostgreSQL `wal_log_hints` setting, forcing full-page writes for hint bit updates after checkpoints (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_receiver_create_temp_slot

Mirrors the PostgreSQL `wal_receiver_create_temp_slot` setting, allowing WAL receivers to create temporary slots if none is specified (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_receiver_status_interval

Reflects the PostgreSQL `wal_receiver_status_interval`, the maximum interval in seconds for standby status reports to the primary (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_receiver_timeout

Shows the PostgreSQL `wal_receiver_timeout`, the maximum time in milliseconds to wait for communication from the primary before disconnecting (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_recycle

Represents the PostgreSQL `wal_recycle` setting, enabling recycling (renaming) of WAL files instead of deleting them (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_retrieve_retry_interval

Corresponds to the PostgreSQL `wal_retrieve_retry_interval`, the delay in milliseconds before retrying failed WAL fetches during recovery.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_segment_size

Displays the size in bytes of individual WAL segment files (read-only).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_sender_timeout

Mirrors the PostgreSQL `wal_sender_timeout`, the maximum time in milliseconds to wait for activity on replication connections before disconnecting (0 disables).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_skip_threshold

Reflects the PostgreSQL `wal_skip_threshold`, the minimum file size in kB to skip WAL logging and use fsync instead for certain operations.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_sync_method

Shows the PostgreSQL `wal_sync_method` used to force WAL writes to disk (numeric representation, e.g., 1=fsync).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_writer_delay

Represents the PostgreSQL `wal_writer_delay`, the sleep time in milliseconds between WAL flushes performed by the WAL writer process.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_wal_writer_flush_after

Corresponds to the PostgreSQL `wal_writer_flush_after`, the amount of WAL (in 8kB blocks) that triggers a flush by the WAL writer.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_work_mem

Mirrors the PostgreSQL `work_mem` setting, the maximum amount of memory in kB used for internal sort operations and hash tables per query operation.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_xmlbinary

Reflects the PostgreSQL `xmlbinary` setting, controlling how binary values are encoded in XML (numeric representation: 1=base64, 2=hex).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_xmloption

Shows the PostgreSQL `xmloption` setting, determining if XML data is treated as documents or content fragments (numeric representation: 1=content, 2=document).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_settings_zero_damaged_pages

Represents the PostgreSQL `zero_damaged_pages` setting, allowing processing to continue past damaged page headers (use with extreme caution) (0=off, 1=on).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_postgresql_extension_info

Exposes information about installed PostgreSQL extensions, including their version and comment. The metric value is always 1.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| extension | The name of the installed extension (e.g., "pg_stat_statements"). |
| version | The version string of the installed extension. |
| comment | The comment or description associated with the extension. |

## pgexporter_postgresql_primary

Identifies if the monitored PostgreSQL instance is operating as a primary (1, not in recovery) or a standby/replica (0, in recovery).

| Attribute | Description | Values |
| :-------- | :---------- | :----- |
| server | The configured name/identifier for the PostgreSQL server. | 1: This server is the primary (not in recovery)., 0: This server is a replica/standby (in recovery). |

## pgexporter_pg_database_size

Reports the total disk space used by each database, measured in bytes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database being measured. |

## pgexporter_pg_locks_count

Counts the current number of active locks, broken down by database and lock mode (e.g., AccessShareLock, RowExclusiveLock).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| mode | The lock mode (accesssharelock, rowsharelock, rowexclusivelock, etc.). |

## pgexporter_pg_replication_slots_active

Shows the activity status of defined replication slots.

| Attribute | Description | Values |
| :-------- | :---------- | :----- |
| server | The configured name/identifier for the PostgreSQL server. | 1: Slot is active and being used by a connection., 0: Slot is inactive. |
| slot_name | The name of the replication slot. | |
| slot_type | The type of replication (physical or logical). | |
| database | The database associated with the slot (for logical slots). | |

## pgexporter_pg_replication_slots_temporary

Indicates whether a defined replication slot is temporary or permanent.

| Attribute | Description | Values |
| :-------- | :---------- | :----- |
| server | The configured name/identifier for the PostgreSQL server. | 1: Slot is temporary and will be removed on session exit or if unused., 0: Slot is permanent. |
| slot_name | The name of the replication slot. | |
| slot_type | The type of replication (physical or logical). | |
| database | The database associated with the slot (for logical slots). | |

## pgexporter_pg_stat_bgwriter_buffers_alloc

Reflects `buffers_alloc` from `pg_stat_bgwriter`: the total number of buffers allocated directly by backend processes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_bgwriter_buffers_backend

Reflects `buffers_backend` from `pg_stat_bgwriter`: the number of buffers written out directly by backend processes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_bgwriter_buffers_backend_fsync

Reflects `buffers_backend_fsync` from `pg_stat_bgwriter`: the number of times backends had to execute their own fsync calls.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_bgwriter_buffers_checkpoint

Reflects `buffers_checkpoint` from `pg_stat_bgwriter`: the number of buffers written out during checkpoint processes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_bgwriter_buffers_clean

Reflects `buffers_clean` from `pg_stat_bgwriter`: the number of buffers successfully written out by the background writer process.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_bgwriter_checkpoint_sync_time

Reflects `checkpoint_sync_time` from `pg_stat_bgwriter`: total time (ms) spent syncing files to disk during checkpoints.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_bgwriter_checkpoint_write_time

Reflects `checkpoint_write_time` from `pg_stat_bgwriter`: total time (ms) spent writing files to disk during checkpoints.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_bgwriter_checkpoints_req

Reflects `checkpoints_req` from `pg_stat_bgwriter`: the number of checkpoints initiated by explicit requests (e.g., CHECKPOINT command).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_bgwriter_checkpoints_timed

Reflects `checkpoints_timed` from `pg_stat_bgwriter`: the number of checkpoints initiated automatically based on time (`checkpoint_timeout`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_bgwriter_maxwritten_clean

Reflects `maxwritten_clean` from `pg_stat_bgwriter`: the count of times the background writer stopped cleaning due to writing its limit (`bgwriter_lru_maxpages`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_process_idle_seconds

Provides a histogram distribution of the duration (in seconds) that backend processes have been idle.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| application_name | The application name reported by the idle process. |
| le | The upper bound of the histogram bucket (in seconds). |

## pgexporter_pg_available_extensions

Shows the total count of extensions available for installation in the current PostgreSQL instance.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_installed_extensions

Reports the total count of extensions currently installed in the connected database, with names listed in a label.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| extensions | Comma-separated list of installed extension names (as a label). |

## pgexporter_pg_indexes

Counts the number of indexes defined on each table within each schema.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| schemaname | The name of the schema. |
| tablename | The name of the table. |

## pgexporter_pg_matviews

Reports the count of materialized views that are currently populated (data is present).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| ispopulated | Hardcoded to 't' in the query, indicating populated views. |

## pgexporter_pg_role

Provides the total number of roles (users and groups) defined within the PostgreSQL cluster.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_rule

Counts the number of rewrite rules defined for each table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| tablename | The name of the table associated with the rule(s). |

## pgexporter_pg_db_conn

Shows the current number of active backend connections established to each specific database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_db_conn_ssl

SSL connection status for database connections

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_statio_all_tables_heap_blks_read

Aggregates `heap_blks_read` from `pg_statio_all_tables`: total disk blocks read for all table heaps in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_statio_all_tables_heap_blks_hit

Aggregates `heap_blks_hit` from `pg_statio_all_tables`: total buffer cache hits for all table heaps in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_statio_all_tables_idx_blks_read

Aggregates `idx_blks_read` from `pg_statio_all_tables`: total disk blocks read for all table indexes in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_statio_all_tables_idx_blks_hit

Aggregates `idx_blks_hit` from `pg_statio_all_tables`: total buffer cache hits for all table indexes in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_statio_all_tables_toast_blks_read

Aggregates `toast_blks_read` from `pg_statio_all_tables`: total disk blocks read for all TOAST tables in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_statio_all_tables_toast_blks_hit

Aggregates `toast_blks_hit` from `pg_statio_all_tables`: total buffer cache hits for all TOAST tables in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_statio_all_tables_tidx_blks_read

Aggregates `tidx_blks_read` from `pg_statio_all_tables`: total disk blocks read for all TOAST table indexes in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_statio_all_tables_tidx_blks_hit

Aggregates `tidx_blks_hit` from `pg_statio_all_tables`: total buffer cache hits for all TOAST table indexes in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_statio_all_sequences_blks_read

Aggregates `blks_read` from `pg_statio_all_sequences`: total disk blocks read for all sequences in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_statio_all_sequences_blks_hit

Aggregates `blks_hit` from `pg_statio_all_sequences`: total buffer cache hits for all sequences in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_user_functions_calls

Reflects `calls` from `pg_stat_user_functions`: the number of times this specific user-defined function has been called.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| funcname | The name of the user-defined function. |

## pgexporter_pg_stat_user_functions_self_time

Reflects `self_time` from `pg_stat_user_functions`: total time (ms) spent executing within the function itself (excludes time in called functions).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| funcname | The name of the user-defined function. |

## pgexporter_pg_stat_user_functions_total_time

Reflects `total_time` from `pg_stat_user_functions`: total time (ms) spent executing the function, including time spent in functions it called.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| funcname | The name of the user-defined function. |

## pgexporter_pg_stat_replication

Counts active WAL streaming replication connections, grouped by the `application_name` reported by the standby.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| application_name | The application name reported by the replication connection. |
| state | Hardcoded to 'streaming' in the query. |

## pgexporter_pg_stat_archiver_archived_count

Reflects `archived_count` from `pg_stat_archiver`: the total number of WAL files successfully archived since server start.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_archiver_success_time_elapsed_ms

Time elapsed (in milliseconds) since the last successful WAL file archival operation, based on `pg_stat_archiver`.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_archiver_failed_count

Reflects `failed_count` from `pg_stat_archiver`: the total number of failed WAL file archival attempts since server start.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_archiver_failure_time_elapsed_ms

Time elapsed (in milliseconds) since the last failed WAL file archival operation, based on `pg_stat_archiver`.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_db_vacuum_age

Represents the age (number of transactions) of the oldest unfrozen transaction ID (`datfrozenxid`) within each database. Useful for monitoring autovacuum progress and wraparound risk.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| datname | The name of the database. |

## pgexporter_pg_view_vacuum_age

Reports the age (number of transactions) of the oldest unfrozen transaction ID (`relfrozenxid`) for each table or materialized view (including TOAST tables). Indicates need for vacuuming.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| datname | The name of the relation (table or materialized view). |

## pgexporter_pg_blocked_vacuum_blocked_duration_seconds

Duration in seconds that vacuum operations have been blocked

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_blocked_vacuum_blocking_duration_seconds

Duration in seconds that operations are blocking vacuum

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_gss_auth

Counts the number of currently active database connections that authenticated using GSSAPI.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_encrypted_conn

Counts the number of currently active database connections that are encrypted using SSL/TLS.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_shmem_allocations

Provides a histogram distribution of shared memory allocation sizes made by the connected backend.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| le | The upper bound of the histogram bucket (derived from size calculation). |

## pgexporter_pg_stat_progress_vacuum_heap_blks_total

Total number of heap blocks to scan during vacuum operation

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| pid | Process ID of the vacuum operation. |
| datname | Database name being vacuumed. |
| usename | Username running the vacuum. |

## pgexporter_pg_stat_progress_vacuum_heap_blks_scanned

Number of heap blocks scanned during vacuum operation

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| pid | Process ID of the vacuum operation. |
| datname | Database name being vacuumed. |
| usename | Username running the vacuum. |

## pgexporter_pg_stat_progress_vacuum_heap_blks_vacuumed

Number of heap blocks vacuumed during vacuum operation

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| pid | Process ID of the vacuum operation. |
| datname | Database name being vacuumed. |
| usename | Username running the vacuum. |

## pgexporter_pg_stat_progress_vacuum_index_vacuum_count

Number of index vacuum cycles completed

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| pid | Process ID of the vacuum operation. |
| datname | Database name being vacuumed. |
| usename | Username running the vacuum. |

## pgexporter_pg_stat_progress_vacuum_max_dead_tuples

Maximum dead tuples that can be stored before vacuum must process indexes

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| pid | Process ID of the vacuum operation. |
| datname | Database name being vacuumed. |
| usename | Username running the vacuum. |

## pgexporter_pg_stat_progress_vacuum_num_dead_tuples

Current number of dead tuples collected during vacuum

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| pid | Process ID of the vacuum operation. |
| datname | Database name being vacuumed. |
| usename | Username running the vacuum. |

## pgexporter_pg_stat_progress_vacuum_pct_scan_completed

Percentage of heap scan completed during vacuum operation

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| pid | Process ID of the vacuum operation. |
| datname | Database name being vacuumed. |
| usename | Username running the vacuum. |

## pgexporter_pg_stat_user_tables_vacuum_seq_scan

Reflects `seq_scan` from `pg_stat_user_tables`: the number of sequential scans initiated on this table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_last_seq_scan_seconds

Time elapsed in seconds since the last sequential scan on this table. Based on `last_seq_scan`. -1 if never.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_seq_tup_read

Reflects `seq_tup_read` from `pg_stat_user_tables`: the number of live rows fetched by sequential scans.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_idx_scan

Reflects `idx_scan` from `pg_stat_user_tables`: the number of index scans initiated on this table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_last_idx_scan_seconds

Time elapsed in seconds since the last index scan on this table. Based on `last_idx_scan`. -1 if never.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_idx_tup_fetch

Reflects `idx_tup_fetch` from `pg_stat_user_tables`: the number of live rows fetched by index scans.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_n_tup_ins

Reflects `n_tup_ins` from `pg_stat_user_tables`: the number of rows inserted in this table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_n_tup_upd

Reflects `n_tup_upd` from `pg_stat_user_tables`: the number of rows updated in this table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_n_tup_del

Reflects `n_tup_del` from `pg_stat_user_tables`: the number of rows deleted in this table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_n_tup_hot_upd

Reflects `n_tup_hot_upd` from `pg_stat_user_tables`: the number of rows HOT updated in this table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_n_tup_newpage_upd

Reflects `n_tup_newpage_upd` from `pg_stat_user_tables`: the number of rows updated to a new page in this table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_n_live_tup

Reflects `n_live_tup` from `pg_stat_user_tables`: the estimated number of live rows in this table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_n_dead_tup

Reflects `n_dead_tup` from `pg_stat_user_tables`: the estimated number of dead rows in this table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_dead_rows_pct

A derived metric showing the percentage of dead rows relative to the total estimated rows in the table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_n_mod_since_analyze

Reflects `n_mod_since_analyze` from `pg_stat_user_tables`: the estimated number of rows modified since this table was last analyzed.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_n_ins_since_vacuum

Reflects `n_ins_since_vacuum` from `pg_stat_user_tables`: the estimated number of rows inserted since this table was last vacuumed.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_last_vacuum_seconds

Time elapsed in seconds since this table was last manually vacuumed. Based on `last_vacuum`. -1 if never.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_last_autovacuum_seconds

Time elapsed in seconds since this table was last vacuumed by the autovacuum daemon. Based on `last_autovacuum`. -1 if never.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_last_analyze_seconds

Time elapsed in seconds since this table was last manually analyzed. Based on `last_analyze`. -1 if never.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_last_autoanalyze_seconds

Time elapsed in seconds since this table was last analyzed by the autovacuum daemon. Based on `last_autoanalyze`. -1 if never.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_vacuum_count

Reflects `vacuum_count` from `pg_stat_user_tables`: the number of times this table has been manually vacuumed.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_autovacuum_count

Reflects `autovacuum_count` from `pg_stat_user_tables`: the number of times this table has been vacuumed by the autovacuum daemon.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_analyze_count

Reflects `analyze_count` from `pg_stat_user_tables`: the number of times this table has been manually analyzed.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_stat_user_tables_vacuum_autoanalyze_count

Reflects `autoanalyze_count` from `pg_stat_user_tables`: the number of times this table has been analyzed by the autovacuum daemon.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the table. |
| schemaname | The schema containing the table. |
| relname | The table name. |

## pgexporter_pg_table_bloat_table_size

Reports the actual total size of a table on disk, in bytes, including the main relation, TOAST table, and all indexes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| schemaname | The name of the schema containing the table. |
| tblname | The name of the table. |

## pgexporter_pg_table_bloat_bloat_size

Estimates the amount of wasted space (bloat) in a table, in bytes. A negative value may indicate a table that is smaller than estimated, which is normal.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| schemaname | The name of the schema containing the table. |
| tblname | The name of the table. |

## pgexporter_pg_table_bloat_bloat_ratio_pct

The estimated bloat as a percentage of the total table size. High values suggest that a VACUUM or REINDEX could reclaim space.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| schemaname | The name of the schema containing the table. |
| tblname | The name of the table. |

## pgexporter_pg_table_bloat_tblpages

The actual number of disk pages used by the table's main heap.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| schemaname | The name of the schema containing the table. |
| tblname | The name of the table. |

## pgexporter_pg_table_bloat_est_tblpages

The estimated number of disk pages that the table should require, based on its contents and fillfactor.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| schemaname | The name of the schema containing the table. |
| tblname | The name of the table. |

## pgexporter_pg_table_bloat_block_size

The server's block size in bytes, provided for context with page counts.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| schemaname | The name of the schema containing the table. |
| tblname | The name of the table. |

## pgexporter_pg_mem_ctx_contexts

Reports the count of memory contexts, grouped by parent context name, within the backend pgexporter connects to.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| parent | The name of the parent memory context. |

## pgexporter_pg_mem_ctx_free_bytes

Reports the total amount of free space (in bytes) within memory contexts, grouped by parent context name, for the connected backend.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| parent | The name of the parent memory context. |

## pgexporter_pg_mem_ctx_used_bytes

Reports the total amount of used space (in bytes) within memory contexts, grouped by parent context name, for the connected backend.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| parent | The name of the parent memory context. |

## pgexporter_pg_mem_ctx_total_bytes

Reports the total allocated size (in bytes) of memory contexts, grouped by parent context name, for the connected backend.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| parent | The name of the parent memory context. |

## pgexporter_pg_stat_wal_wal_records

Reflects `wal_records` from `pg_stat_wal`: the total number of WAL records generated since the last statistics reset.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_wal_wal_fpi

Reflects `wal_fpi` from `pg_stat_wal`: the total number of WAL full-page images generated since the last statistics reset.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_wal_wal_bytes

Reflects `wal_bytes` from `pg_stat_wal`: the total volume of WAL generated in bytes since the last statistics reset.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_wal_wal_buffers_full

Reflects `wal_buffers_full` from `pg_stat_wal`: the number of times WAL writes occurred because the WAL buffers were full.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_wal_wal_write

Reflects `wal_write` from `pg_stat_wal`: the number of times WAL buffers were written to disk via explicit WAL write requests.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_wal_wal_sync

Reflects `wal_sync` from `pg_stat_wal`: the number of times WAL files were explicitly synced to disk.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_wal_wal_write_time

Reflects `wal_write_time` from `pg_stat_wal`: total time (ms) spent writing WAL buffers to disk (requires `track_wal_io_timing`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_wal_wal_sync_time

Reflects `wal_sync_time` from `pg_stat_wal`: total time (ms) spent syncing WAL files to disk (requires `track_wal_io_timing`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_database_blk_read_time

Reflects `blk_read_time` from `pg_stat_database`: total time (ms) backends spent reading data blocks in this database (requires `track_io_timing`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_blk_write_time

Reflects `blk_write_time` from `pg_stat_database`: total time (ms) backends spent writing data blocks in this database (requires `track_io_timing`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_blks_hit

Reflects `blks_hit` from `pg_stat_database`: total number of buffer cache hits (reads satisfied from cache) in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_blks_read

Reflects `blks_read` from `pg_stat_database`: total number of data blocks read from disk (cache misses) in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_deadlocks

Reflects `deadlocks` from `pg_stat_database`: total number of deadlocks detected within this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_temp_files

Reflects `temp_files` from `pg_stat_database`: total number of temporary files created by queries in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_temp_bytes

Reflects `temp_bytes` from `pg_stat_database`: total amount of data (bytes) written to temporary files by queries in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_tup_returned

Reflects `tup_returned` from `pg_stat_database`: total number of rows returned (yielded) by queries executed in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_tup_fetched

Reflects `tup_fetched` from `pg_stat_database`: total number of rows fetched (read from tables) by queries executed in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_tup_inserted

Reflects `tup_inserted` from `pg_stat_database`: total number of rows inserted by queries executed in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_tup_updated

Reflects `tup_updated` from `pg_stat_database`: total number of rows updated by queries executed in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_tup_deleted

Reflects `tup_deleted` from `pg_stat_database`: total number of rows deleted by queries executed in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_xact_commit

Reflects `xact_commit` from `pg_stat_database`: total number of transactions committed in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_xact_rollback

Reflects `xact_rollback` from `pg_stat_database`: total number of transactions rolled back in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_conflicts

Reflects `conflicts` from `pg_stat_database`: total number of queries canceled due to recovery conflicts in this database (sum of specific conflict types).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_numbackends

Shows the current number of active backend processes connected to this specific database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_checksum_failures

Reflects `checksum_failures` from `pg_stat_database`: total number of data block checksum failures detected in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_session_time

Reflects `session_time` from `pg_stat_database`: total time (ms) spent by all sessions connected to this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_active_time

Reflects `active_time` from `pg_stat_database`: total time (ms) sessions spent actively executing SQL statements in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_idle_in_transaction_time

Reflects `idle_in_transaction_time` from `pg_stat_database`: total time (ms) sessions spent idle within an open transaction in this database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_sessions

Reflects `sessions` from `pg_stat_database`: total cumulative number of sessions established to this database since statistics were reset.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_sessions_abandoned

Reflects `sessions_abandoned` from `pg_stat_database`: total number of sessions to this database terminated due to client connection failures.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_sessions_fatal

Reflects `sessions_fatal` from `pg_stat_database`: total number of sessions to this database terminated by unrecoverable errors.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_sessions_killed

Reflects `sessions_killed` from `pg_stat_database`: total number of sessions to this database terminated by administrator command.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_wal_prefetch_reset

Time elapsed (in seconds) since WAL prefetch statistics (`pg_stat_get_wal_prefetch()`) were last reset.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_gssapi_credentials_delegated

Counts the number of currently active database connections that have delegated GSSAPI credentials.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

## pgexporter_pg_stat_io_reads

Counts the total read operations performed, sourced from `pg_stat_io` and aggregated by backend type (e.g., client backend, autovacuum worker).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend (e.g., client backend, autovacuum worker, checkpointer). |

## pgexporter_pg_stat_io_read_time

Aggregates total time (ms) spent by backend types performing read I/O operations (from `pg_stat_io`, requires `track_io_timing`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_writes

Counts the total write operations performed, sourced from `pg_stat_io` and aggregated by backend type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_write_time

Aggregates total time (ms) spent by backend types performing write I/O operations (from `pg_stat_io`, requires `track_io_timing`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_writebacks

Counts the total OS-level writeback requests initiated, sourced from `pg_stat_io` and aggregated by backend type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_writeback_time

Aggregates total time (ms) spent by backend types performing writeback operations (from `pg_stat_io`, requires `track_io_timing`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_extends

Counts the total relation file extension operations performed, sourced from `pg_stat_io` and aggregated by backend type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_extend_time

Aggregates total time (ms) spent by backend types performing relation extension operations (from `pg_stat_io`, requires `track_io_timing`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_op_bytes

Reports the size (typically 8192 bytes) associated with I/O operations tracked by `pg_stat_io`, per backend type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_hits

Counts the total number of shared buffer cache hits, sourced from `pg_stat_io` and aggregated by backend type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_evictions

Counts the total number of buffer blocks evicted from caches, sourced from `pg_stat_io` and aggregated by backend type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_reuses

Counts the total number of times buffers in I/O ring buffers were reused, sourced from `pg_stat_io` and aggregated by backend type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_fsyncs

Counts the total number of fsync calls made, sourced from `pg_stat_io` and aggregated by backend type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_io_fsync_time

Aggregates total time (ms) spent by backend types performing fsync operations (from `pg_stat_io`, requires `track_io_timing`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| backend_type | Type of backend. |

## pgexporter_pg_stat_database_conflicts_confl_tablespace

Reflects `confl_tablespace` from `pg_stat_database_conflicts`: number of queries canceled due to dropped tablespaces during recovery.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_conflicts_confl_lock

Reflects `confl_lock` from `pg_stat_database_conflicts`: number of queries canceled due to lock timeouts during recovery.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_conflicts_confl_snapshot

Reflects `confl_snapshot` from `pg_stat_database_conflicts`: number of queries canceled due to old snapshots during recovery.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_conflicts_confl_bufferpin

Reflects `confl_bufferpin` from `pg_stat_database_conflicts`: number of queries canceled due to pinned buffers during recovery.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_conflicts_confl_deadlock

Reflects `confl_deadlock` from `pg_stat_database_conflicts`: number of queries canceled due to deadlocks during recovery.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_database_conflicts_confl_active_logicalslot

Reflects `confl_active_logicalslot` from `pg_stat_database_conflicts`: number of queries canceled due to active logical replication slots during recovery.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The name of the database. |

## pgexporter_pg_stat_all_indexes_idx_scans

Aggregates `idx_scan` from `pg_stat_all_indexes`: total number of index scans initiated on all indexes for this relation.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| relname | The name of the table or materialized view the index belongs to. |

## pgexporter_pg_stat_all_indexes_idx_tup_reads

Aggregates `idx_tup_read` from `pg_stat_all_indexes`: total number of index entries returned by scans on all indexes for this relation.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| relname | The name of the table or materialized view the index belongs to. |

## pgexporter_pg_stat_all_indexes_idx_tup_fetchs

Aggregates `idx_tup_fetch` from `pg_stat_all_indexes`: total number of live table rows fetched by index scans using this relation's indexes.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| relname | The name of the table or materialized view the index belongs to. |

## pgexporter_pg_stat_all_indexes_time_elapsed_ms

Time elapsed (in milliseconds) since the last index scan occurred on any index of this relation (based on `pg_stat_get_last_idx_scan_time`).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| relname | The name of the table or materialized view the index belongs to. |



## Custom Metrics

pgexporter supports user-defined custom metrics through YAML configuration files. These allow you to create tailored metrics for your specific PostgreSQL monitoring needs.

For detailed information about custom metrics, including schema definitions, configuration examples, and usage instructions, see the [Custom Metrics Guide](./custom_metrics.md).
