---
outline: deep
---

# pgexporter 0.7.0

This is a feature release.

## Features

* Improvements to the core metrics, including new metrics for autovacuum
* New extension support
  * pgexporter/Extension
  * pg_stat_statements
  * PostGIS
  * pgcrypto
  * pg_buffercache
  * timescaledb
  * pgvector
* Improved the manual

Special thanks to @bassamadnan for his work on extension support as part of his Google Summer of Code project !

## Changelog

```
* 6fd1ec2 bassamadnan [#326] Add permission check on startup
* 4eecd87 bassamadnan [#320] Fix scraping script
* fb1cee9 bassamadnan [#323] Add metrics for pgexporter_ext
* cb60830 jesperpedersen Tired of MacOS
* 9e45a7a Haoran Zhang Removing from empty json should be no-op
* 742ca02 Haoran Zhang Fix json.c imports
* 0e8da70 Haoran Zhang [#319] Fix multiple bugs in ART
* f4cc43a bassamadnan [#307] Add default response
* 966fe36 bassamadnan [#309] Update documentation for extensions
* 6d33dab bassamadnan [#313] Add database in extension metrics
* ba6859e bassamadnan [#311] Fix contrib metrics for pg_stat_progress_vacuum
* fdab73e bassamadnan [#295] Add validation for extension name and version
* 07bfd39 bassamadnan [#292] Add metric for blocked vacuum
* 91d81ab bassamadnan [#294] Add bloat estimation metric
* cdd67f2 bassamadnan [#291] Add metrics for tracking vacuum
* 8f93916 bassamadnan [#302] Use PROMETHEUS_LENGTH
* b25ceb8 jesperpedersen [#301] Move to a single manual
* 16241c0 User1995 [#303] pgexporter-admin:Memory corruption when freeing command-line password argument
* 52b0625 bassamadnan [#298] Add metrics for pgcrypto
* 9696dc2 bassamadnan [#286] Add metrics for pgvector
* 8e5ea04 bassamadnan [#293] Add metrics from pg_stat_progress_vacuum
* bc227ae User1995 [#288] Replace strncpy with snprintf to ensure null termination.  Replace all strncpy calls with snprintf to eliminate -Wstringop-truncation warnings and ensure strings are always properly null-terminated.
* 4b3a8cf User1995 [#288] Metric_name warning
* a34eac0 jesperpedersen Add missing space
* 6b41bf8 jesperpedersen Add missing space
* f04411b jesperpedersen Add missing space
* 3557544 bassamadnan [#284] Add metrics for pg_buffercache
* aedc4f8 bassamadnan [#282] Add metrics for PostGIS
* 61ac360 User1995 [#279] Add directory configuration option
* 9960faf User1995 [#277] Standardize JSON Output Format for conf ls Command
* 33239b7 jesperpedersen [#276] Developer guide: Logging levels
* 9a557f3 User1995 [#274] Fix inconsistent JSON output format in pgexporter-cli conf get
* e0bc586 User1995 [#272] Replace inefficient snprintf calls with direct string assignment
* f217bff User1995 [#270] Use type-checked section extraction with pgexporter_json_get_typed in get_config_key_result
* 45c4a33 jesperpedersen [#267] Introduce ValueNone and get_typed functions
* deafd6b bassamadnan [#265] Add extensions in config
* 0916830 Haoran Zhang [#267] Introduce ValueNone and get_typed functions
* 95cf728 Saurav Pal [#263] Custom metrics: Memory leak
* 3f35f35 bassamadnan [#252] Add timescale metrics
* b083768 bassamadnan [#251] Use array to store metric names
* 078a852 Haoran Zhang [#260] Add manual for core APIs
* 6575d6e User1995 [#258] Add Two-Dot Notation Support to pgagroal-cli conf get Command
* 83635a0 bassamadnan [#251] Detect duplicate metric names
* 0860680 Saurav Pal [#239] Pull metrics from other databases
* 8d9d753 User1995 [#255] Add support for code coverage
* cfd8f62 User1995 [#253] Add FindCheck.cmake
* 2a26a3f bassamadnan [#248] Add queries for pg_stat_statements
* 01b6f01 bassamadnan [#235] Add test suite
* 500ed20 bassamadnan [#241] Use malloc in http_get
* 61b5718 bassamadnan [#241] Add dereference check for bridge
* 2d2ba63 Saurav Pal [#242] pgexporter_pg_stat_archiver_archived_count reported multiple times
* 78dad41 bassamadnan [#241] Destroy HTTP and free extension path
* ef29770 jesperpedersen uncrustify
* be0cdf6 User1995 [#237] Fix Memory leak in pgexporter-admin
* daf6884 bassamadnan [#229] Remove extra prefix
* e514ed6 jesperpedersen uncrustify
* 4eb8366 bassamadnan [#229] Add extension format
* be75954 User1995 [#233] Improve network byte order handling
* e8c7d12 bassamadnan [#223] Query Extensions on Startup
* 69bab2a bassamadnan [#226] Update HTTP APIs
* bd46d70 bassamadnan [#224] Use MAX_PATH for files
* f1ee453 bassamadnan [#224] Use MAX_PATH for files
* 03c0711 jesperpedersen [#220] Eisvogel 3.2.0
* 7fcf023 Haoran Zhang [#218] Bug fixes & debug func for values
* 99bb5a6 bassamadnan [#213] Add bash script for documentation
* 7f449cb Shikhar Soni [#161] Add HTTPS support for prometheus metrics
* 9159a3f jesperpedersen [#215] API: Support doxygen 1.13.x
* 88be7f1 User1995 [#211]Build: cmake 3.31+
* a6d1fbe jesperpedersen Switch to Eisvogel 3.1.0
* 1501e3d bassamadnan [#193] Add Grafana dashboard
* 56accb3 bassamadnan [#204] Add version coverage for clang and gcc
* 4110d0a nesangcode [#207] file-based path: environment variable support
* c2ee36c Arshdeep54 [#205] Add freeBSD support in CI
* f8f3685 jesperpedersen [#203] Message: Rename API
* e5b54e5 jesperpedersen Fix memory leak
* d6f2710 Ahmed Osama [pgexporter#197] feat/cli-parser
* 2c7a1ad Ahmed Osama [pgexporter#201] Fix broken Docker manual link in CONTRIBUTING.md
* 0a7c38b User1995 [#199] Enhance CI: Document Generation & Full Build Matrix
* 759a2e1 jesperpedersen [#192] Implement MacOS compatibility
* f01fc72 Arshdeep54 Dockerize pgexporter
* f5230de User1995 [#190] Improved pgexporter_os_kernel_version to align BSD version formatting.
* 50c21a3 jesperpedersen Fix CI
* 5754c2a jesperpedersen Fix CI
* 61800e7 jesperpedersen Add Release build to CI
* 2be93ab unconventional-guy [#185] Added pgexporter_linux_version function to extract Linux kernel Version.
* be23499 jesperpedersen Copy'n'paste errors
* 473c530 jchrys [#183] Utilize ParameterStatus Packet
* 55eafce bassamadnan [#181] Add view extracting script
* f206641 bassamadnan [#174] Add JSON configuration support for pgexporter metrics
* 988eba3 jesperpedersen Update email address
* 98bb1f3 jesperpedersen Add more author files
* 145f555 bassamadnan [#179] Migrate JSON, deque and ART
* cfaefb8 Georg Pfuetzenreuter admin: support password through environment
* 8129f56 jesperpedersen Update RPM section
* d98fcd8 jesperpedersen Mention bridge
* a6a4ce8 jesperpedersen Next is 0.7.0
```

## Download

- [Source Code](https://github.com/pgexporter/pgexporter/releases/download/0.7.0/pgexporter-0.7.0.tar.gz)
- [Guide](https://github.com/pgexporter/pgexporter/releases/download/0.7.0/pgexporter-en.pdf)
- [RPM](https://yum.postgresql.org/) for Fedora 40/41, RHEL 9.x and Rocky Linux 9.x
