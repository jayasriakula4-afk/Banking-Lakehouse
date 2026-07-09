\# Banking Lakehouse Implementation Specification



\## Document Information



| Field | Value |

|------|------|

| Project | Banking Lakehouse |

| Version | 1.0 |

| Status | Draft |

| Author | Jayasri |

| Date | July 2026 |



\---



\# 1. Purpose



This document defines the implementation standards, software versions, Docker images, networking, storage, and deployment conventions for the Banking Lakehouse platform.



It acts as the implementation reference for all Docker Compose files, configuration files, and deployment scripts.



\---



\# 2. Supported Software Versions



| Component | Version |

|-----------|----------|

| Docker | 29.x |

| Docker Compose | v2 |

| PostgreSQL | 16 |

| RustFS | Latest Stable |

| Apache Polaris | 1.0.x |

| Apache Spark | 3.5.6 |

| Apache Iceberg | 1.9.2 |

| Apache Kafka | Confluent Platform 7.5.x |

| Apache NiFi | 2.x |

| Dremio OSS | 26.x |

| Apache Airflow | 3.x |

| Prometheus | Latest Stable |

| Grafana | Latest Stable |



\---



\# 3. Docker Network



Network Name



banking-network



Driver



bridge



\---



\# 4. Persistent Volumes



postgres-data



rustfs-data



spark-warehouse



kafka-data



dremio-data



grafana-data



prometheus-data



\---



\# 5. Environment Variables



All runtime configuration must be stored in:



.env



No credentials will be hardcoded inside Docker Compose files.



\---



\# 6. Container Naming Standard



banking-postgres



banking-rustfs



banking-polaris



banking-spark



banking-kafka



banking-nifi



banking-dremio



banking-airflow



banking-prometheus



banking-grafana



\---



\# 7. Port Allocation



| Service | Port |

|----------|------|

| PostgreSQL | 5432 |

| RustFS API | 9000 |

| RustFS Console | 9001 |

| Polaris | 8181 |

| Spark Master | 7077 |

| Spark UI | 8080 |

| Kafka | 9092 |

| NiFi | 8443 |

| Dremio | 9047 |

| Airflow | 8081 |

| Prometheus | 9090 |

| Grafana | 3000 |



\---



\# 8. Docker Compose Strategy



Compose files will be separated by functional domain.



docker-compose.storage.yml



docker-compose.processing.yml



docker-compose.streaming.yml



docker-compose.analytics.yml



docker-compose.monitoring.yml



docker-compose.yml



\---



\# 9. Git Strategy



main



feature/documentation



feature/storage-foundation



feature/processing



feature/streaming



feature/analytics



feature/orchestration



feature/monitoring



\---



\# 10. Deployment Order



1\. PostgreSQL

2\. RustFS

3\. Apache Polaris

4\. Spark

5\. Iceberg

6\. Kafka

7\. NiFi

8\. Dremio

9\. Superset

10\. Airflow

11\. Prometheus

12\. Grafana



\---



\# 11. Validation Strategy



Each service will be validated independently before integrating with the next layer.



Integration tests will be performed after every sprint.



\---



\# 12. Success Criteria



\- All containers healthy

\- Services communicate over Docker network

\- Iceberg tables created successfully

\- Spark reads/writes data

\- Dremio queries Iceberg tables

\- Dashboards accessible

\- Monitoring operational

