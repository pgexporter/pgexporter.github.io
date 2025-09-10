# postgis_raster


Raster data storage and processing metrics:

**pgexporter_postgis_raster_raster_table_count_raster_table_count**

The total number of tables containing columns of the `raster` type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_postgis_raster_raster_columns_info_num_bands**

Number of bands in PostGIS raster columns.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_srid_distribution_raster_count**

Number of raster objects using each Spatial Reference System ID.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| srid | Spatial Reference System Identifier. |

**pgexporter_postgis_raster_raster_band_stats_num_bands**

Number of bands in PostGIS raster columns.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_band_stats_table_count**

Number of tables with specific raster band configurations.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| num_bands | Number of bands in the raster. |

**pgexporter_postgis_raster_raster_pixel_types_usage_count**

Usage count for different pixel types in PostGIS raster data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| pixel_type | Raster pixel data type. |

**pgexporter_postgis_raster_raster_nodata_stats_nodata_value**

NoData value used in PostGIS raster data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_nodata_stats_usage_count**

Usage count for specific NoData values in PostGIS raster data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| nodata_value | The NoData value. |

**pgexporter_postgis_raster_raster_overview_count_overview_count**

Number of overview levels for PostGIS raster data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_overview_factors_overview_factor**

Overview reduction factor for PostGIS raster data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_overview_factors_overview_count**

Count of raster overviews with specific factor configurations.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| overview_factor | Overview reduction factor. |

**pgexporter_postgis_raster_raster_constraints_same_alignment**

Indicates if raster data has same alignment constraints enabled.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_constraints_regular_blocking**

Indicates if raster data has regular blocking constraints enabled.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_constraints_table_count**

Number of raster tables with specific constraint configurations.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| regular_blocking | Regular blocking constraint status. |
| same_alignment | Same alignment constraint status. |

**pgexporter_postgis_raster_raster_schema_distribution_raster_table_count**

Number of tables containing raster data in each schema.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing raster tables. |

**pgexporter_postgis_raster_raster_schema_distribution_unique_srids**

Number of unique Spatial Reference System IDs used in raster data per schema.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing raster tables. |

**pgexporter_postgis_raster_raster_schema_distribution_avg_bands**

Average number of bands per raster column in each schema.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing raster tables. |

**pgexporter_postgis_raster_raster_scale_stats_scale_x**

X-axis scale factor for PostGIS raster data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_scale_stats_scale_y**

Y-axis scale factor for PostGIS raster data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_scale_stats_table_count**

Number of raster tables with specific scale configurations.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| scale_x | X-axis scale factor. |
| scale_y | Y-axis scale factor. |

**pgexporter_postgis_raster_raster_block_sizes_blocksize_x**

X-dimension block size for PostGIS raster data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_block_sizes_blocksize_y**

Y-dimension block size for PostGIS raster data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the raster table. |
| table_name | Table containing raster data. |
| column_name | Name of the raster column. |

**pgexporter_postgis_raster_raster_block_sizes_table_count**

Number of raster tables with specific block size configurations.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| blocksize_x | X-dimension block size. |
| blocksize_y | Y-dimension block size. |