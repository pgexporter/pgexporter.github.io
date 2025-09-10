# postgis


Spatial data and geometry/geography column statistics:

**pgexporter_postgis_spatial_tables_geometry_tables**

The total number of tables in the database that have at least one column of the `geometry` type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_postgis_spatial_tables_geography_tables**

The total number of tables in the database that have at least one column of the `geography` type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_postgis_spatial_tables_srid_count**

The total count of Spatial Reference System Identifiers (SRIDs) defined in the `spatial_ref_sys` table.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_postgis_srid_usage_usage_count**

Usage count for each Spatial Reference System ID across all spatial data.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| srid | Spatial Reference System Identifier. |

**pgexporter_postgis_geometry_columns_detail_coord_dimension**

Coordinate dimension for geometry columns in PostGIS.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the geometry column. |
| table_name | Table containing the geometry column. |
| column_name | Name of the geometry column. |

**pgexporter_postgis_geography_columns_detail_coord_dimension**

Coordinate dimension for geography columns in PostGIS.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing the geography column. |
| table_name | Table containing the geography column. |
| column_name | Name of the geography column. |

**pgexporter_postgis_spatial_index_summary_total_spatial_indexes**

The total number of GIST spatial indexes found in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_postgis_spatial_index_summary_geometry_indexes**

Total number of spatial indexes on geometry columns.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_spatial_index_summary_geography_indexes**

Total number of spatial indexes on geography columns.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_geometry_type_stats_column_count**

Number of geometry columns grouped by geometry type.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| geometry_type | Type of geometry (Point, LineString, Polygon, etc.). |

**pgexporter_postgis_coordinate_dimensions_coord_dimension**

The coordinate dimension value for PostGIS geometry/geography columns.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| coord_dimension | Coordinate dimension count. |

**pgexporter_postgis_coordinate_dimensions_column_count**

Number of geometry/geography columns with specific coordinate dimensions.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| coord_dimension | Coordinate dimension count. |

**pgexporter_postgis_schema_spatial_stats_geometry_columns**

Number of geometry columns in each schema.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing spatial data. |

**pgexporter_postgis_schema_spatial_stats_spatial_tables**

Number of tables containing spatial data in each schema.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing spatial data. |

**pgexporter_postgis_schema_spatial_stats_unique_srids**

Number of unique Spatial Reference System IDs used in each schema.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| table_schema | Schema containing spatial data. |