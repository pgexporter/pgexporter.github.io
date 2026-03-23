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
    details: Define your own PostgreSQL queries and expose the exact Prometheus metrics your environment needs.
  - title: Bridge
    details: Combine metrics from multiple Prometheus endpoints into one streamlined scrape target.
  - title: Bridge/JSON
    details: Publish the same aggregated monitoring data as JSON for integrations and external tooling.
  - title: Remote management
    details: Control and manage running pgexporter instances remotely without logging into each host.
  - title: TLS Support
    details: Protect exporter traffic with modern TLS support for encrypted and authenticated connections.
  - title: Daemon Mode
    details: Run pgexporter as a background service so it stays available without occupying a terminal session.
---
