---
# https://vitepress.dev/reference/default-theme-home-page
layout: home

hero:
  name: "pgexporter"
  tagline: A Prometheus exporter for PostgreSQL
  actions:
    - theme: brand
      text: pgexporter
      link: /pgexporter
    - theme: brand
      text: pgexporter_ext
      link: /pgexporter_ext
    - theme: alt
      text: Releases
      link: /releases

features:
  - title: Custom metrics
    details: Custom user-defined metrics to get the metrics in the form you want
  - title: Bridge
    details: Aggregate multiple Prometheus endpoints into a single Prometheus endpoint
  - title: Bridge/JSON
    details: Serve aggregated Prometheus information as JSON
  - title: Remote management
    details: Remotely manage the pgexporter instance
  - title: TLS Support
    details: Transport Layer Security (TLS) v1.2+ support
  - title: Daemon Mode
    details: Run as a daemon without hogging the terminal
---
