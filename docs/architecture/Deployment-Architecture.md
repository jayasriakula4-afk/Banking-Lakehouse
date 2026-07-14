\# Deployment Architecture



\## Overview



All platform services are deployed as Docker containers connected through a shared Docker network.



\## Containers



| Container | Purpose |

|------------|----------|

| PostgreSQL | Metadata database |

| SeaweedFS | Object storage |

| Apache Polaris | Iceberg REST Catalog |

| Apache Spark | Processing engine |

| Apache Kafka | Streaming platform |

| Apache NiFi | Data ingestion |

| Dremio OSS | SQL engine |

| Apache Superset | BI dashboards |

| Apache Airflow | Workflow orchestration |

| Prometheus | Metrics |

| Grafana | Monitoring |



\## Deployment Diagram



```mermaid

flowchart TB



subgraph Docker Host



Postgres

SeaweedFS

Polaris

Spark

Kafka

NiFi

Dremio

Superset

Airflow

Prometheus

Grafana



end



Network\[(Docker Network)]



Postgres --- Network

SeaweedFS --- Network

Polaris --- Network

Spark --- Network

Kafka --- Network

NiFi --- Network

Dremio --- Network

Superset --- Network

Airflow --- Network

Prometheus --- Network

Grafana --- Network

```

