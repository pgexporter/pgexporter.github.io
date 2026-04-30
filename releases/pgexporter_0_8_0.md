---
outline: deep
---

# pgexporter 0.8.0

This is a feature release.

## Features

* New vault security (migration needed)
* A lot of new metrics - including for PostgreSQL 18
* Use Grafana 12
* Initial alert subsystem
* Web console

and enhancements and bug fixes.

## Changelog

```
* 1cda464 jesperpedersen Fix log file creation
* e1f8f79 bassamadnan [#377] Update manual for pg_statio per-table metrics
* f3b1c31 Ben Li Make pg_statio metrics more useful.
* 142fdd2 Ameensakr [#519]support deque sort with different data types
* 9462250 Ameensakr [#520] resolved,  skip ValueNone
* 82f7c82 Vaibhav Bhembre [#515] Add per-server tls option for backend TLS negotiation
* b901558 Sakshi [#517] Cross-port ART prefix search
* 31f3730 abdelrhmansersawy [#513] Refactor pgagroal conf get output to decouple CLI and JSON format
* 82ece86 Somye [#446] Fixed socket only working on 2nd connection
* 8dbd535 Somye [#448] Added TLS config changes check during reload
* c1f42b5 Shashank Singh [#489] CI: Rocky Linux 10
* 768f7db abdelrhmansersawy [#410] implement internal pgexporter_alert
* e4fa119 Ahmed Mordi [#466] Add FIPS mode reporting
* b0abd57 Ahmed Mordi [#506] Update pgexporter_ext extension references
* 799c9df Ashwani Kumar Kamal [#449] Add O_NONBLOCK to systemd sockets
* 770a92a Frank Heikens [#505] Remove unnecessary packages from container runtime images
* 9b8ed65 Frank Heikens [#504] Add HEALTHCHECK to container Dockerfiles
* 0f0dda3 Frank Heikens [#503] Add .dockerignore for container builds
* e65d84f abdelrhmansersawy [#491] Support NULL values in metric sorting to prevent strcmp crash
* f74f3a5 Shashidhar B M [#498] docs: add mctf test framework to doxygen API documentation
* 4adf66b Shashidhar B M [#496] test: MCTF per-test max runtime to catch performance regressions
* 4213557 Shashank Singh [#478] Add per-test log slicing and ERROR checks to the MCTF test framework
* a3e0329 Shashank Singh Fix PG17 pg_stat_statements I/O timing queries
* 64ce338 Somye [#494] Added pg_wait_event
* ed34ce7 Shashank Singh [#490] Fix long string truncation in value serialization
* 35d9f20 bassamadnan [#481] Fix environ pointer seg fault
* 8d32689 Trevor Fix segmentation faults in cache.c and network.c
* aa19436 Trevor Jacob Mathews Upgrade AES to GCM
* 195ec67 Trevor Fix configuration segfault and assert() side-effects in test suite
* 320a94c Somye [472] Added search bar in console
* 353f23a jesperpedersen Fix password leak
* 24f0bd5 Ahmed Mordi [#467] Add pg_stat_get_backend_io metric for PostgreSQL 18+
* fe26893 Ashwani Kumar Kamal [#454] Fix conf crashes by initializing memory in child processes
* 896a091 Ashwani Kumar Kamal [#445] Fix uninitialized client_addr in accept()
* f527e92 jesperpedersen Move -Wextra-semi
* 2282888 jesperpedersen Add -Wextra-semi
* 4d327c3 Somye [#473] Added auto-refresh button in web console
* 53eeaf4 jesperpedersen [#250] Remove _info
* 01c7d3e abdelrhmansersawy [#441] Generate Version-Specific Grafana Dashboards
* 512f82d Trevor Add pgexporter_cleanse and replace OPENSSL_cleanse in aes.c
* a14e9a7 abdelrhmansersawy [#453] implement exclude collectors
* 046f885 Somye [#468] Updated web console documentation
* d6e03c0 Ahmed Mordi [#464] Fix memory leaks in process title, timestamp strings, and management payload
* f33db62 Trevor Jacob Mathews Upgrade vault key derivation to PBKDF2
* 383620c Shashank Singh [#452] Prevent addr2line failure on paths with spaces and remove popen()
* 10a978f abdelrhmansersawy [#458] fix broken image path inside doc/CONSOLE.md
* 58b370e Shashank Singh [#455] enforce RFC 4013 (SASLprep) compliance for ASCII control characters in passwords
* 8651a66 Zeyad Daowd [#456] Migrating SCRAM-SHA-256 to EVP_MAC
* d373ddc bassamadnan [#382] Increase unique metric columns
* ddf2750 Zeyad Daowd [#451] Optimizing salted password generation by reusing HMAC context
* 8eeeec6 shashidhar-bm [#442] Add MCTF fixture support and shared config isolation
* cabf97f Somye [#250] Added Web Console UI
* 84ac6dd abdelrhmansersawy [#422]: implement shared cache module
* b67cebf shashidhar-bm [#415] Replace libcheck with MCTF testing framework
* 4f5d599 abdelrhmansersawy [#438] fix LLVM Coverage generation fail
* 1487f5d jesperpedersen Update Committers
* 64998d5 jesperpedersen Eisvogel 3.4.0
* d92cca1 abdelrhmansersawy [#427] Update check.sh to run tests from the project directory
* 9ab8428 Somye [#416] Fixed Promtheus label parsing
* f9aae59 Trevor Jacob Mathews Use RAND_bytes
* ce06ff5 Trevor Jacob Mathews [#425] Missing SIGCHLD handler causes zombie process leak
* c72f391 abdelrhmansersawy [#175] implement prometheus support using ART
* dbe8a4c jesperpedersen [#423] Force pgexporter_start_logging
* 1cda464 jesperpedersen Fix log file creation
* e1f8f79 bassamadnan [#377] Update manual for pg_statio per-table metrics
* f3b1c31 Ben Li Make pg_statio metrics more useful.
* 142fdd2 Ameensakr [#519]support deque sort with different data types
* 9462250 Ameensakr [#520] resolved,  skip ValueNone
* 82f7c82 Vaibhav Bhembre [#515] Add per-server tls option for backend TLS negotiation
* b901558 Sakshi [#517] Cross-port ART prefix search
* 31f3730 abdelrhmansersawy [#513] Refactor pgagroal conf get output to decouple CLI and JSON format
* 82ece86 Somye [#446] Fixed socket only working on 2nd connection
* 8dbd535 Somye [#448] Added TLS config changes check during reload
* c1f42b5 Shashank Singh [#489] CI: Rocky Linux 10
* 768f7db abdelrhmansersawy [#410] implement internal pgexporter_alert
* e4fa119 Ahmed Mordi [#466] Add FIPS mode reporting
* b0abd57 Ahmed Mordi [#506] Update pgexporter_ext extension references
* 799c9df Ashwani Kumar Kamal [#449] Add O_NONBLOCK to systemd sockets
* 770a92a Frank Heikens [#505] Remove unnecessary packages from container runtime images
* 9b8ed65 Frank Heikens [#504] Add HEALTHCHECK to container Dockerfiles
* 0f0dda3 Frank Heikens [#503] Add .dockerignore for container builds
* e65d84f abdelrhmansersawy [#491] Support NULL values in metric sorting to prevent strcmp crash
* f74f3a5 Shashidhar B M [#498] docs: add mctf test framework to doxygen API documentation
* 4adf66b Shashidhar B M [#496] test: MCTF per-test max runtime to catch performance regressions
* 4213557 Shashank Singh [#478] Add per-test log slicing and ERROR checks to the MCTF test framework
* a3e0329 Shashank Singh Fix PG17 pg_stat_statements I/O timing queries
* 64ce338 Somye [#494] Added pg_wait_event
* ed34ce7 Shashank Singh [#490] Fix long string truncation in value serialization
* 35d9f20 bassamadnan [#481] Fix environ pointer seg fault
* 8d32689 Trevor Fix segmentation faults in cache.c and network.c
* aa19436 Trevor Jacob Mathews Upgrade AES to GCM
* 195ec67 Trevor Fix configuration segfault and assert() side-effects in test suite
* 320a94c Somye [472] Added search bar in console
* 353f23a jesperpedersen Fix password leak
* 24f0bd5 Ahmed Mordi [#467] Add pg_stat_get_backend_io metric for PostgreSQL 18+
* fe26893 Ashwani Kumar Kamal [#454] Fix conf crashes by initializing memory in child processes
* 896a091 Ashwani Kumar Kamal [#445] Fix uninitialized client_addr in accept()
* f527e92 jesperpedersen Move -Wextra-semi
* 2282888 jesperpedersen Add -Wextra-semi
* 4d327c3 Somye [#473] Added auto-refresh button in web console
* 53eeaf4 jesperpedersen [#250] Remove _info
* 01c7d3e abdelrhmansersawy [#441] Generate Version-Specific Grafana Dashboards
* 512f82d Trevor Add pgexporter_cleanse and replace OPENSSL_cleanse in aes.c
* a14e9a7 abdelrhmansersawy [#453] implement exclude collectors
* 046f885 Somye [#468] Updated web console documentation
* d6e03c0 Ahmed Mordi [#464] Fix memory leaks in process title, timestamp strings, and management payload
* f33db62 Trevor Jacob Mathews Upgrade vault key derivation to PBKDF2
* 383620c Shashank Singh [#452] Prevent addr2line failure on paths with spaces and remove popen()
* 10a978f abdelrhmansersawy [#458] fix broken image path inside doc/CONSOLE.md
* 58b370e Shashank Singh [#455] enforce RFC 4013 (SASLprep) compliance for ASCII control characters in passwords
* 8651a66 Zeyad Daowd [#456] Migrating SCRAM-SHA-256 to EVP_MAC
* d373ddc bassamadnan [#382] Increase unique metric columns
* ddf2750 Zeyad Daowd [#451] Optimizing salted password generation by reusing HMAC context
* 8eeeec6 shashidhar-bm [#442] Add MCTF fixture support and shared config isolation
* cabf97f Somye [#250] Added Web Console UI
* 84ac6dd abdelrhmansersawy [#422]: implement shared cache module
* b67cebf shashidhar-bm [#415] Replace libcheck with MCTF testing framework
* 4f5d599 abdelrhmansersawy [#438] fix LLVM Coverage generation fail
* 1487f5d jesperpedersen Update Committers
* 64998d5 jesperpedersen Eisvogel 3.4.0
* d92cca1 abdelrhmansersawy [#427] Update check.sh to run tests from the project directory
* 9ab8428 Somye [#416] Fixed Promtheus label parsing
* f9aae59 Trevor Jacob Mathews Use RAND_bytes
* ce06ff5 Trevor Jacob Mathews [#425] Missing SIGCHLD handler causes zombie process leak
* c72f391 abdelrhmansersawy [#175] implement prometheus support using ART
* dbe8a4c jesperpedersen [#423] Force pgexporter_start_logging
* 1ff93f6 jesperpedersen [#423] log_file isn't cleared
* 3ffd827 Trevor Jacob Mathews [#418] Fix process title truncation on short binary paths
* 3dc3d35 Trevor Jacob Mathews [#420] Sync contributor lists in AUTHORS and documentation
* 37c94d0 abdelrhmansersawy [#410] add alerting section to Grafana manual
* 89472d7 jesperpedersen Add string.h
* 35b5f8c jesperpedersen Fix image paths
* 01f2129 abdelrhmansersawy [#411] fix broken images path on grafana.md file
* dc5e295 abdelrhmansersawy [#408]: Add missing metrics to pg_stat_walreceiver
* 6c1d1ea abdelrhmansersawy [#406]: Add Multixact ID Age (datminmxid) metric
* 0a3d8a8 Amr-Shams [#404]http: parse headers separately and handle content-length/chunked responses
* 268a60b abdelrhmansersawy [#402]: implement metric for long-running transactions
* a60761b jesperpedersen Try and force linking against .so
* 0839de4 abdelrhmansersawy [#399]: fix incorrect metric names on Grafana dashboards
* d54b119 jesperpedersen Try and force linking against .so
* b6a6909 Somye [#397] Added query stats to grafan dashboard
* 8a0a20e abdelrhmansersawy [#194] implement time based configuration generalization
* 6ee2783 jesperpedersen Merge branch 'feature/query-stats' of github.com:sommye-ctr/pgexporter into sommye-ctr-feature/query-stats
* ebf3955 Somye [#373] Added query execution statistics
* 20d51f3 Andreas Wahlen Fix missing liburing-devel in RPM Dockerfile
* 123f712 Mazen Kamal [#393] Enhance CI workflow for coverage reporting
* caceb60 Amr-Shams [#389] fet: removed hard coded content type when building http request
* 8bf8997 jesperpedersen Add sponsors
* 1aade7a jesperpedersen PTAL policy
* 355579c abdelrhmansersawy [#371] Add optional flag for queries
* bd991cc User1995 [#385] Fix RPM build failures and add RPM build CI
* 90de9fb Andreas Wahlen Fix integer overflow and add required permissions documentation
* 59f6ab9 bassamadnan [#374] Fix SSL leaks
* fb3e7c6 jesperpedersen [#380] Histogram format error
* cbe3e8c jesperpedersen [#380] Histogram format error
* 5cc5033 Andreas Wahlen Fix missing libatomic in RPM Dockerfile
* e0b5753 Shashank Singh [#328] Grafana:update dashboards and provisioning for Grafana 12
* fa518bc jesperpedersen Change logging from _error to _warn
* ec43bce jesperpedersen Remove log statement
* 2c8e13a Somye Added script to generate contrib files
* d70d3a6 Somye [#369] Added global postgresql query timeout
* a4d0a35 jesperpedersen New doxygen versions
* 62a4063 jesperpedersen Run w/o --name-only
* 8b8b4dd jesperpedersen Document clang-format 21+ requirement
* 24401d3 jesperpedersen Happy 2026 !
* 74b5eca TutTrue Add clang-format configuration and script for code formatting; remove uncrustify support. Update documentation and CI workflow for clang-format integration.
* 7e55189 saraanbih Add pre-flight validation of the configuration file before attempting to parse it. This improves error reporting and avoids attempting to parse missing, non-regular, unreadable, or binary files
* 68958ad jesperpedersen Initial AI guidelines
* c730014 jesperpedersen Update actions
* 813389e jesperpedersen Eisvogel 3.3.0
* 5633f0c jesperpedersen Use DOCS flag
* dd185f3 jesperpedersen Use Eisvogel 3.2.1
* 491ae93 bassamadnan [#357] Add metrics for pg_qualstats
* 96545e9 jesperpedersen More logging
* d91bec9 jesperpedersen Update for clang
* 6791d79 bassamadnan [#355] Add metrics for pgstattuple
* 547f513 jesperpedersen Port logging
* 38dbdbd jesperpedersen Make doxygen optional
* 6d596c1 jesperpedersen [#353] Do a pgexporter_snprintf implementation
* 240fc85 jesperpedersen uncrustify 0.81
* 0d8e111 jesperpedersen Add newline after semicolon
* 9ce0940 jesperpedersen [#353] Do a pgexporter_snprintf implementation
* d488f9d bassamadnan [#351] Add metrics for pg_stat_kcache
* 68ec3e3 bassamadnan [#349] Add metrics for pg_stat_monitor
* af8632c bassamadnan [#316] Refactor test suite
* f2a274f bassamadnan [#343] Add core metrics for read/write ratios
* bc99c9f jesperpedersen Add DOCS option to build
* f409d06 bassamadnan [#344] Refactor HTTP code
* 3d0cccf jesperpedersen Use SHA256 for source package
* 3c7522c bassamadnan [#341] Add metrics for pg_wait_sampling
* b0e7f4b bassamadnan [#339] Add metrics for Citus
* 962a972 jesperpedersen Try FreeBSD 14.3
* f64f0da bassamadnan [#336] Add PostgreSQL 18 Metrics
* df9c1a1 User1995 [#335] feat: update Docker RPM build to use local source and fix CMake test dir handling
* 2e7ba41 Andreas Wahlen Fix pgexporter.spec and update RPM build info
* 6720b41 User1995 [#333] Support UTF8 passwords
* 5a93a67 bassamadnan [#331] Add type configuration
* 1589f20 jesperpedersen Exclude .cache and test from source package
* c9aba72 jesperpedersen Update AUTHORS paths
* f84c0fb jesperpedersen Next is 0.8.0
```

## New Contributors

* @saraanbih made their first contribution in #360
* @TutTrue made their first contribution in #362
* @sommye-ctr made their first contribution in #370
* @sksingh2005 made their first contribution in #372
* @Mazen050 made their first contribution in #392
* @Abdelrhmansersawy made their first contribution in #400
* @Amr-Shams made their first contribution in #405
* @trxvorr made their first contribution in #421
* @shashidhar-bm made their first contribution in #437
* @Zeyad-Daowd made their first contribution in #457
* @ahmedmmordi made their first contribution in #465
* @sneaky-potato made their first contribution in #475
* @fheikens made their first contribution in #500
* @Sakshii-27 made their first contribution in #518
* @neurodrone made their first contribution in #516
* @Ameensakr made their first contribution in #521
* @benjunmun made their first contribution in #379

## Download

- [Source Code](https://github.com/pgexporter/pgexporter/releases/download/0.8.0/pgexporter-0.8.0.tar.gz)
- [Guide](https://github.com/pgexporter/pgexporter/releases/download/0.8.0/pgexporter-en.pdf)
- [RPM](https://yum.postgresql.org/) for Fedora 42/43, RHEL 10.x and Rocky Linux 10.x
