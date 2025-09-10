# postgis_topology


Topology element counts and health monitoring:

**pgexporter_postgis_topology_topology_inventory_topology_count**

The total number of defined topologies in the database.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |

**pgexporter_postgis_topology_topology_details_precision**

Precision value for the PostGIS topology.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_details_hasz**

Indicates if the topology has Z-coordinate support.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_node_counts_live_node_count**

Current number of active nodes in the topology.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_node_counts_inserted_nodes**

Total number of nodes that have been inserted into the topology.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_node_counts_updated_nodes**

Total number of nodes that have been updated in the topology.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_node_counts_deleted_nodes**

Total number of nodes that have been deleted from the topology.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_edge_counts_live_edge_count**

Current number of active edges in the topology.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_edge_counts_inserted_edges**

Total number of edges that have been inserted into the topology.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_face_counts_live_face_count**

Current number of active faces in the topology.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_face_counts_inserted_faces**

Total number of faces that have been inserted into the topology.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_primitives_summary_precision**

Average precision across all topologies.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_primitives_summary_node_count**

Total number of nodes across all topologies.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_primitives_summary_edge_count**

Total number of edges across all topologies.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_primitives_summary_face_count**

Total number of faces across all topologies.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_primitives_summary_total_primitives**

Total number of topology primitives (nodes + edges + faces).

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_system_stats_total_topologies**

Total number of topologies defined in the system.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_system_stats_unique_srids**

Number of unique Spatial Reference System IDs used across all topologies.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_system_stats_avg_precision**

Average precision across all topologies in the system.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_system_stats_total_nodes**

Total number of nodes across all topologies in the system.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_system_stats_total_edges**

Total number of edges across all topologies in the system.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_system_stats_total_faces**

Total number of faces across all topologies in the system.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |

**pgexporter_postgis_topology_topology_srid_distribution_topology_count**

Number of topologies using each Spatial Reference System ID.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| srid | Spatial Reference System Identifier. |

**pgexporter_postgis_topology_topology_srid_distribution_total_nodes_for_srid**

Total number of nodes across all topologies using a specific SRID.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| srid | Spatial Reference System Identifier. |

**pgexporter_postgis_topology_topology_srid_distribution_total_edges_for_srid**

Total number of edges across all topologies using a specific SRID.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database being monitored. |
| srid | Spatial Reference System Identifier. |

**pgexporter_postgis_topology_topology_health_current_node_count**

Current number of nodes for topology health monitoring.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |

**pgexporter_postgis_topology_topology_health_current_edge_count**

Current number of edges for topology health monitoring.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | Database containing the topology. |
| topology_name | Name of the topology. |