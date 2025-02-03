---
outline: deep
---

# pgexporter 0.6.0

This is a feature release.

## Features

- [#139](https://github.com/pgexporter/pgexporter/issues/139) Prometheus: Logging
- [#141](https://github.com/pgexporter/pgexporter/issues/141) Core APIs
- [#143](https://github.com/pgexporter/pgexporter/issues/143) Management: All commands need to support JSON output
- [#145](https://github.com/pgexporter/pgexporter/issues/145) Support BASE64 as a value
- [#147](https://github.com/pgexporter/pgexporter/issues/147) Remove PostgreSQL 12 support
- [#148](https://github.com/pgexporter/pgexporter/issues/148) Add PostgreSQL 17 support
- [#151](https://github.com/pgexporter/pgexporter/issues/151) Bridge support
- [#162](https://github.com/pgexporter/pgexporter/issues/162) Support -F/--format flag for pgexporter-admin

## Enhancements

- [#128](https://github.com/pgexporter/pgexporter/issues/128) relfrozenxid metric
- [#129](https://github.com/pgexporter/pgexporter/issues/129) datfrozenxid metric
- [#135](https://github.com/pgexporter/pgexporter/issues/135) User / developer guides
- [#137](https://github.com/pgexporter/pgexporter/issues/137) Update metrics link in README.md
- [#144](https://github.com/pgexporter/pgexporter/issues/144) Align base64 function signature
- [#146](https://github.com/pgexporter/pgexporter/issues/146) API documentation
- [#150](https://github.com/pgexporter/pgexporter/issues/150) Advanced monitoring with pgexporter
- [#152](https://github.com/pgexporter/pgexporter/issues/152) Remove RHEL 8.x description
- [#156](https://github.com/pgexporter/pgexporter/issues/156) CLI: Redo conf

## Bug fixes

- [#127](https://github.com/pgexporter/pgexporter/issues/127) Fix sprintf of size_t
- [#131](https://github.com/pgexporter/pgexporter/issues/131) Force master-key to abort if file exist
- [#133](https://github.com/pgexporter/pgexporter/issues/133) Multiple instances can be run if the pid file is specified as a relative path
- [#140](https://github.com/pgexporter/pgexporter/issues/140) pgexporter-admin: SegFault with -P
- [#158](https://github.com/pgexporter/pgexporter/issues/158) YAML: Check for tag / collector

## Thanks to

- @JohnHVancouver: #137
- @Jubilee101: #141
- @ashu3103: #156
- @jirutka
- @resyfer: #128, #129, #148
- @shikharish: #162

## Download

- [Source Code](https://github.com/pgexporter/pgexporter/releases/download/0.6.0/pgexporter-0.6.0.tar.gz)
- [User guide](https://github.com/pgexporter/pgexporter/releases/download/0.6.0/pgexporter-user-guide.pdf)
- [Advanced guide](https://github.com/pgexporter/pgexporter/releases/download/0.6.0/pgexporter-advanced.pdf)
- [Developer guide](https://github.com/pgexporter/pgexporter/releases/download/0.6.0/pgexporter-dev-guide.pdf)
- [RPM](https://yum.postgresql.org/) for Fedora 40/41, RHEL 9.x and Rocky Linux 9.x
