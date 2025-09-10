# vector


Vector similarity search index performance and storage:

## Table of Contents
- [pgexporter_vector_hnsw_index_performance_idx_scan](#pgexporter-vector-hnsw-index-performance-idx-scan)
- [pgexporter_vector_hnsw_index_performance_idx_tup_fetch](#pgexporter-vector-hnsw-index-performance-idx-tup-fetch)
- [pgexporter_vector_hnsw_index_performance_idx_tup_read](#pgexporter-vector-hnsw-index-performance-idx-tup-read)
- [pgexporter_vector_hnsw_index_performance_index_size_bytes](#pgexporter-vector-hnsw-index-performance-index-size-bytes)
- [pgexporter_vector_ivfflat_index_performance_idx_scan](#pgexporter-vector-ivfflat-index-performance-idx-scan)
- [pgexporter_vector_ivfflat_index_performance_idx_tup_fetch](#pgexporter-vector-ivfflat-index-performance-idx-tup-fetch)
- [pgexporter_vector_ivfflat_index_performance_idx_tup_read](#pgexporter-vector-ivfflat-index-performance-idx-tup-read)
- [pgexporter_vector_ivfflat_index_performance_index_size_bytes](#pgexporter-vector-ivfflat-index-performance-index-size-bytes)
- [pgexporter_vector_vector_column_inventory_vector_columns](#pgexporter-vector-vector-column-inventory-vector-columns)
- [pgexporter_vector_vector_index_distribution_index_count](#pgexporter-vector-vector-index-distribution-index-count)
- [pgexporter_vector_vector_table_storage_table_size_bytes](#pgexporter-vector-vector-table-storage-table-size-bytes)
- [pgexporter_vector_vector_table_storage_total_size_bytes](#pgexporter-vector-vector-table-storage-total-size-bytes)

## pgexporter_vector_vector_column_inventory_vector_columns

Number of vector columns in each table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing vector data. |
| schema_name | Schema containing the table. |
| table_name | Table containing vector columns. |

## pgexporter_vector_hnsw_index_performance_index_size_bytes

The size on disk, in bytes, of a specific HNSW (Hierarchical Navigable Small World) index from the pgvector extension.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the index. |
| schemaname | The schema of the index. |
| tablename | The table the index is on. |
| indexname | The name of the HNSW index. |

## pgexporter_vector_hnsw_index_performance_idx_scan

The total number of scans initiated on a specific HNSW index.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the index. |
| schemaname | The schema of the index. |
| tablename | The table the index is on. |
| indexname | The name of the HNSW index. |

## pgexporter_vector_hnsw_index_performance_idx_tup_read

Number of index entries returned by scans on this HNSW vector index

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the index. |
| schemaname | Schema containing the index. |
| tablename | Table containing the index. |
| indexname | Name of the HNSW index. |

## pgexporter_vector_hnsw_index_performance_idx_tup_fetch

Number of live table rows fetched by index scans on this HNSW vector index

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the index. |
| schemaname | Schema containing the index. |
| tablename | Table containing the index. |
| indexname | Name of the HNSW index. |

## pgexporter_vector_ivfflat_index_performance_index_size_bytes

The size on disk, in bytes, of a specific IVFFlat (Inverted File with Flat compression) index from the pgvector extension.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the index. |
| schemaname | The schema of the index. |
| tablename | The table the index is on. |
| indexname | The name of the IVFFlat index. |

## pgexporter_vector_ivfflat_index_performance_idx_scan

The total number of scans initiated on a specific IVFFlat index.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database containing the index. |
| schemaname | The schema of the index. |
| tablename | The table the index is on. |
| indexname | The name of the IVFFlat index. |

## pgexporter_vector_ivfflat_index_performance_idx_tup_read

Number of index entries returned by scans on this IVFFlat vector index.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the index. |
| schemaname | Schema containing the index. |
| tablename | Table containing the index. |
| indexname | Name of the IVFFlat index. |

## pgexporter_vector_ivfflat_index_performance_idx_tup_fetch

Number of live table rows fetched by index scans on this IVFFlat vector index.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the index. |
| schemaname | Schema containing the index. |
| tablename | Table containing the index. |
| indexname | Name of the IVFFlat index. |

## pgexporter_vector_vector_table_storage_total_size_bytes

Total size in bytes including indexes for tables containing vector data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing vector data. |
| schema_name | Schema containing the table. |
| table_name | Table containing vector columns. |

## pgexporter_vector_vector_table_storage_table_size_bytes

Size in bytes of tables containing vector data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing vector data. |
| schema_name | Schema containing the table. |
| table_name | Table containing vector columns. |

## pgexporter_vector_vector_index_distribution_index_count

The total count of vector indexes in the database, grouped by access method type (e.g., hnsw, ivfflat).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| index_type | The access method of the vector index. |