---
outline: deep
---

# Metrics

The following system metrics are available when `pgexporter_ext` is installed:

## Table of Contents
- [pgexporter_pgexporter_ext_cpu_info_clock_speed_hz](#pgexporter-pgexporter-ext-cpu-info-clock-speed-hz)
- [pgexporter_pgexporter_ext_cpu_info_l1dcache_size](#pgexporter-pgexporter-ext-cpu-info-l1dcache-size)
- [pgexporter_pgexporter_ext_cpu_info_l1icache_size](#pgexporter-pgexporter-ext-cpu-info-l1icache-size)
- [pgexporter_pgexporter_ext_cpu_info_l2cache_size](#pgexporter-pgexporter-ext-cpu-info-l2cache-size)
- [pgexporter_pgexporter_ext_cpu_info_l3cache_size](#pgexporter-pgexporter-ext-cpu-info-l3cache-size)
- [pgexporter_pgexporter_ext_cpu_info_number_of_cores](#pgexporter-pgexporter-ext-cpu-info-number-of-cores)
- [pgexporter_pgexporter_ext_load_avg_load_avg_five_minutes](#pgexporter-pgexporter-ext-load-avg-load-avg-five-minutes)
- [pgexporter_pgexporter_ext_load_avg_load_avg_one_minute](#pgexporter-pgexporter-ext-load-avg-load-avg-one-minute)
- [pgexporter_pgexporter_ext_load_avg_load_avg_ten_minutes](#pgexporter-pgexporter-ext-load-avg-load-avg-ten-minutes)
- [pgexporter_pgexporter_ext_memory_info_cache_total](#pgexporter-pgexporter-ext-memory-info-cache-total)
- [pgexporter_pgexporter_ext_memory_info_free_memory](#pgexporter-pgexporter-ext-memory-info-free-memory)
- [pgexporter_pgexporter_ext_memory_info_swap_free](#pgexporter-pgexporter-ext-memory-info-swap-free)
- [pgexporter_pgexporter_ext_memory_info_swap_total](#pgexporter-pgexporter-ext-memory-info-swap-total)
- [pgexporter_pgexporter_ext_memory_info_swap_used](#pgexporter-pgexporter-ext-memory-info-swap-used)
- [pgexporter_pgexporter_ext_memory_info_total_memory](#pgexporter-pgexporter-ext-memory-info-total-memory)
- [pgexporter_pgexporter_ext_memory_info_used_memory](#pgexporter-pgexporter-ext-memory-info-used-memory)
- [pgexporter_pgexporter_ext_network_info_link_speed_mbps](#pgexporter-pgexporter-ext-network-info-link-speed-mbps)
- [pgexporter_pgexporter_ext_network_info_rx_bytes](#pgexporter-pgexporter-ext-network-info-rx-bytes)
- [pgexporter_pgexporter_ext_network_info_rx_dropped](#pgexporter-pgexporter-ext-network-info-rx-dropped)
- [pgexporter_pgexporter_ext_network_info_rx_errors](#pgexporter-pgexporter-ext-network-info-rx-errors)
- [pgexporter_pgexporter_ext_network_info_rx_packets](#pgexporter-pgexporter-ext-network-info-rx-packets)
- [pgexporter_pgexporter_ext_network_info_tx_bytes](#pgexporter-pgexporter-ext-network-info-tx-bytes)
- [pgexporter_pgexporter_ext_network_info_tx_dropped](#pgexporter-pgexporter-ext-network-info-tx-dropped)
- [pgexporter_pgexporter_ext_network_info_tx_errors](#pgexporter-pgexporter-ext-network-info-tx-errors)
- [pgexporter_pgexporter_ext_network_info_tx_packets](#pgexporter-pgexporter-ext-network-info-tx-packets)
- [pgexporter_pgexporter_ext_os_info_process_count](#pgexporter-pgexporter-ext-os-info-process-count)
- [pgexporter_pgexporter_ext_os_info_uptime_seconds](#pgexporter-pgexporter-ext-os-info-uptime-seconds)

## pgexporter_pgexporter_ext_os_info_process_count

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

## pgexporter_pgexporter_ext_os_info_uptime_seconds

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

## pgexporter_pgexporter_ext_cpu_info_number_of_cores

Number of CPU cores available on the system.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

## pgexporter_pgexporter_ext_cpu_info_clock_speed_hz

CPU clock speed in Hz.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

## pgexporter_pgexporter_ext_cpu_info_l1dcache_size

L1 data cache size in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

## pgexporter_pgexporter_ext_cpu_info_l1icache_size

L1 instruction cache size in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

## pgexporter_pgexporter_ext_cpu_info_l2cache_size

L2 cache size in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

## pgexporter_pgexporter_ext_cpu_info_l3cache_size

L3 cache size in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| vendor | CPU vendor. |
| model_name | CPU model name. |

## pgexporter_pgexporter_ext_memory_info_total_memory

Total system memory in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

## pgexporter_pgexporter_ext_memory_info_used_memory

Used system memory in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

## pgexporter_pgexporter_ext_memory_info_free_memory

Free system memory in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

## pgexporter_pgexporter_ext_memory_info_swap_total

Total swap space in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

## pgexporter_pgexporter_ext_memory_info_swap_used

Used swap space in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

## pgexporter_pgexporter_ext_memory_info_swap_free

Free swap space in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

## pgexporter_pgexporter_ext_memory_info_cache_total

Total cache memory in KB.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

## pgexporter_pgexporter_ext_network_info_tx_bytes

Bytes transmitted on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

## pgexporter_pgexporter_ext_network_info_tx_packets

Packets transmitted on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

## pgexporter_pgexporter_ext_network_info_tx_errors

Transmission errors on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

## pgexporter_pgexporter_ext_network_info_tx_dropped

Transmitted packets dropped on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

## pgexporter_pgexporter_ext_network_info_rx_bytes

Bytes received on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

## pgexporter_pgexporter_ext_network_info_rx_packets

Packets received on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

## pgexporter_pgexporter_ext_network_info_rx_errors

Reception errors on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

## pgexporter_pgexporter_ext_network_info_rx_dropped

Received packets dropped on network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

## pgexporter_pgexporter_ext_network_info_link_speed_mbps

Link speed in Mbps for network interface.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |
| interface_name | Network interface name. |
| ip_address | IP address. |

## pgexporter_pgexporter_ext_load_avg_load_avg_one_minute

1-minute system load average.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

## pgexporter_pgexporter_ext_load_avg_load_avg_five_minutes

5-minute system load average.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

## pgexporter_pgexporter_ext_load_avg_load_avg_ten_minutes

15-minute system load average.

| Attribute | Description |
| :-------- | :---------- |
| server | The configured name/identifier for the PostgreSQL server. |
| database | The database being monitored. |

