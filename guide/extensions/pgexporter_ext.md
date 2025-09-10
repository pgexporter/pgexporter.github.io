---
outline: deep
---

# Metrics

The following system metrics are available when `pgexporter_ext` is installed:

**pgexporter_pgexporter_ext_os_info_process_count**

Number of running processes on the system.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| name | Operating system name. |
| version | Operating system version. |
| architecture | System architecture. |
| host_name | Hostname. |
| domain_name | Domain name. |

**pgexporter_pgexporter_ext_os_info_uptime_seconds**

System uptime in seconds.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| name | Operating system name. |
| version | Operating system version. |
| architecture | System architecture. |
| host_name | Hostname. |
| domain_name | Domain name. |

**pgexporter_pgexporter_ext_cpu_info_number_of_cores**

Number of CPU cores available on the system.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

**pgexporter_pgexporter_ext_cpu_info_clock_speed_hz**

CPU clock speed in Hz.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

**pgexporter_pgexporter_ext_cpu_info_l1dcache_size**

L1 data cache size in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

**pgexporter_pgexporter_ext_cpu_info_l1icache_size**

L1 instruction cache size in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

**pgexporter_pgexporter_ext_cpu_info_l2cache_size**

L2 cache size in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

**pgexporter_pgexporter_ext_cpu_info_l3cache_size**

L3 cache size in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

**pgexporter_pgexporter_ext_memory_info_total_memory**

Total system memory in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pgexporter_ext_memory_info_used_memory**

Used system memory in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pgexporter_ext_memory_info_free_memory**

Free system memory in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pgexporter_ext_memory_info_swap_total**

Total swap space in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pgexporter_ext_memory_info_swap_used**

Used swap space in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pgexporter_ext_memory_info_swap_free**

Free swap space in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pgexporter_ext_memory_info_cache_total**

Total cache memory in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pgexporter_ext_network_info_tx_bytes**

Bytes transmitted on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

**pgexporter_pgexporter_ext_network_info_tx_packets**

Packets transmitted on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

**pgexporter_pgexporter_ext_network_info_tx_errors**

Transmission errors on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

**pgexporter_pgexporter_ext_network_info_tx_dropped**

Transmitted packets dropped on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

**pgexporter_pgexporter_ext_network_info_rx_bytes**

Bytes received on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

**pgexporter_pgexporter_ext_network_info_rx_packets**

Packets received on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

**pgexporter_pgexporter_ext_network_info_rx_errors**

Reception errors on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

**pgexporter_pgexporter_ext_network_info_rx_dropped**

Received packets dropped on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

**pgexporter_pgexporter_ext_network_info_link_speed_mbps**

Link speed in Mbps for network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

**pgexporter_pgexporter_ext_load_avg_load_avg_one_minute**

1-minute system load average.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pgexporter_ext_load_avg_load_avg_five_minutes**

5-minute system load average.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

**pgexporter_pgexporter_ext_load_avg_load_avg_ten_minutes**

15-minute system load average.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

