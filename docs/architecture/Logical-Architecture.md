\# Logical Architecture



\## Overview



The Banking Lakehouse is designed as a layered data platform where each component has a well-defined responsibility. The architecture separates ingestion, processing, storage, governance, analytics, orchestration, and monitoring.



\## Architecture Layers



| Layer | Components |

|--------|------------|

| Data Sources | Core Banking, CRM, Payment Systems, ATM, REST APIs |

| Ingestion | Apache NiFi |

| Streaming | Apache Kafka |

| Processing | Apache Spark |

| Storage | Apache Iceberg + SeaweedFS |

| Catalog | Apache Polaris |

| Metadata | PostgreSQL |

| Analytics | Dremio OSS |

| Visualization | Apache Superset |

| Orchestration | Apache Airflow |

| Monitoring | Prometheus + Grafana |



\## Service Interaction



```mermaid

flowchart LR



A\[Banking Systems] --> B\[Apache NiFi]

A --> C\[Apache Kafka]



B --> D\[Apache Spark]

C --> D



D --> E\[Apache Iceberg]

E --> F\[SeaweedFS]



E --> G\[Apache Polaris]

G --> H\[PostgreSQL]



I\[Dremio OSS] --> G

J\[Apache Superset] --> I



K\[Apache Airflow] --> D



L\[Prometheus] --> M\[Grafana]

```

