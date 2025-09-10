# pgcrypto


Cryptographic function usage patterns:

**pgexporter_pgcrypto_function_usage_by_category_function_count**

The total count of available `pgcrypto` functions, grouped by their functional category (e.g., encryption, digest).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| function_category | The category of the pgcrypto function. |

**pgexporter_pgcrypto_user_crypto_function_usage_calls**

The number of times a specific user-defined function that utilizes `pgcrypto` functions has been called, based on `pg_stat_user_functions`.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| schemaname | The schema of the function. |
| funcname | The name of the function. |

**pgexporter_pgcrypto_user_crypto_function_usage_total_time**

Total execution time for cryptographic function calls in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the function. |
| funcname | Name of the cryptographic function. |

**pgexporter_pgcrypto_user_crypto_function_usage_self_time**

Self time (excluding called functions) for cryptographic function execution in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the function. |
| funcname | Name of the cryptographic function. |

**pgexporter_pgcrypto_user_crypto_function_usage_avg_time_per_call**

Average time per call for cryptographic functions in milliseconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the function. |
| funcname | Name of the cryptographic function. |

**Note:** To see metrics from `user_crypto_function_usage`, you need to enable function tracking:
```sql
ALTER SYSTEM SET track_functions = 'all';
SELECT pg_reload_conf();
```