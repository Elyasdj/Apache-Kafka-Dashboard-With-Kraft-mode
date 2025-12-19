# Kafka Dashboard Full-Overview

[![Grafana](https://img.shields.io/badge/Grafana-v12.2.1-orange?logo=grafana)](https://grafana.com/)
[![Prometheus](https://img.shields.io/badge/Prometheus-v3.5.0-orange?logo=prometheus)](https://prometheus.io/)

A comprehensive, production-ready Grafana dashboard for monitoring Apache Kafka clusters using **kafka_exporter** metrics. Get real-time insights into cluster health, consumer lag, topic performance, and consumer group behavior.

---

## 📸 Screenshots

| Cluster Overview | Consumer Lag Analysis |
|:---:|:---:|
| ![image png](https://github.com/user-attachments/assets/d0c6df04-5e74-4aef-b64f-080a7711c2a3) | ![image png (1)](https://github.com/user-attachments/assets/799b27e5-8ef6-4887-bd4a-9446fc8b86c3) |
| Consumer Group Details | Topic Details |
| ![image png (2)](https://github.com/user-attachments/assets/3950a779-ab6f-44df-8b3d-4cdda8e849bc) | ![image png (3)](https://github.com/user-attachments/assets/0e257f24-32af-49da-8796-00274bde10bf) |

---

## ✨ Features

### 🔷 Cluster Overview
Monitor the overall health and status of your Kafka cluster at a glance.

| Panel | Description |
|-------|-------------|
| **Total Brokers** | Number of active Kafka brokers in the cluster |
| **Total Topics** | Count of all topics across the cluster |
| **Total Partitions** | Sum of all partitions across all topics |
| **Total Consumer Groups** | Number of registered consumer groups |
| **Under-Replicated Partitions** | Partitions with insufficient replicas (critical alert) |
| **Broker List** | List of active brokers and their availability status |
| **Partitions per Topic** | Number of partitions per topic to assess parallelism and load distribution |
| **Topics Overview** | High-level view of topic count, partitions, and overall status |

### 🔶 Consumer Lag Analysis
Deep dive into consumer lag metrics to identify bottlenecks and performance issues.

| Panel | Description |
|-------|-------------|
| **Top 10 Lag by Consumer Group** | Top 10 consumer groups with the highest lag |
| **Top 10 Lag by Topic** | Top 10 topics with the highest consumer lag |
| **Lag Trend by Consumer Group** | Lag changes over time per consumer group |
| **Lag by Partitions (Detail)** | Detailed lag at partition level for deeper troubleshooting |

### 🟢 Consumer Group Details
Comprehensive view of consumer group behavior and health.

| Panel | Description |
|-------|-------------|
| **Consumer Group Summary** | Overview of consumer group status and health |
| **Consumption Rate (msg/sec)** | Message consumption throughput per second |
| **Production Rate (msg/sec)** | Message production throughput per second |


### 🟣 Topic Details
In-depth topic-level metrics for performance tuning.

| Panel | Description |
|-------|-------------|
| **Topic Offset Growth** | Growth rate of topic offsets over time |
| **Under-Replicated Partitions per Topic** | Count of partitions without full replica synchronization |
| **Under-Replicated Trend** | Trend of under-replicated partitions over time |

---

## 📋 Prerequisites

Before installing this dashboard, ensure you have:

- ✅ **Grafana** v12.2.1 or higher
- ✅ **Prometheus** configured as a data source
- ✅ **kafka_exporter** running and scraping your Kafka cluster

---

## 🚀 Installation

### Step 1: Configure kafka_exporter (With Kraft Mode)

https://github.com/Elyasdj/Prometheus-Exporters-Handbook

### Step 2: Configure Prometheus

Add the following to your `prometheus.yml`:

```yaml
  - job_name: Kafka-Exporter
    metrics_path: /metrics
    static_configs:

      - targets:
        - 192.168.1.5:9308
        labels:
          enviroment: 'Production'
          project: 'Kafka_Cluster1'

      - targets:
        - 192.168.2.5:9308
        labels:
          enviroment: 'Production'
          project: 'Kafka_Cluster2'

```

### Step 3: Import Dashboard

1. Open Grafana and navigate to **Dashboards → Import**
2. Upload the `kafka-dashboard.json` file or paste its contents
3. Select your Prometheus data source
4. Click **Import**

---

## 🎛️ Dashboard Variables

The dashboard includes powerful template variables for filtering:

| Variable | Description | Multi-Select |
|----------|-------------|:------------:|
| `instance` | Filter by kafka_exporter instance | ✅ |
| `topic` | Filter by Kafka topic name | ✅ |
| `consumergroup` | Filter by consumer group | ✅ |
| `Project` | Filter by Project | ✅ |
| `Enviroment` | Filter by Enviroment | ✅ |

---

## 💡 Quick Tips

- 🔍 Use the **topic** and **consumergroup** dropdowns to focus on specific areas
- 📈 Set the time range to **Last 1 hour** for real-time monitoring
- 🔔 Configure Grafana alerts on **Consumer Lag** and **Under-Replicated Partitions**
- 📊 Export panels as PNG for incident reports

---

## ⏱️ Auto-Refresh

Default refresh interval: **30 seconds**

Available intervals: `5s`, `10s`, `30s`, `1m`, `5m`, `15m`, `30m`, `1h`

---

## 📝 Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2024 | Initial release with full Kafka monitoring capabilities |

---

<p align="center">
  Create By Elyasdj
</p>
