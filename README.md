# Grafana_Prometheus_Monitoring

## Project Structure
```
monitoring/
├── docker-compose.yml
└── prometheus.yml
```

## Deployment Steps

**Launch the stack:**

Open your terminal in the project folder and run:

`$ docker compose up -d`

**Access the services:**
- Prometheus: http://localhost:9090
- Grafana: http://localhost:3500 (User: admin / Pass: admin)
- cAdvisor: http://localhost:8088

**Configure Grafana:**
- Login to Grafana.
- Go to Connections > Data Sources.
- Click Add data source and select Prometheus.
- In the URL field, enter: http://prometheus:9090 (since they are in the same Docker network).
- Click Save & Test.

**Import Dashboards:** 
Go to Dashboards > New > Import and use these IDs:
- **1860**: To monitor the Server (Node Exporter).
- **14282**: To monitor Containers (cAdvisor).

**A quick tip:** If you don't see any data when trying to view cAdvisor metrics, make sure the container has sufficient permissions (that's why we add privileged: true in the compose file), as access to Docker stats is more restricted in some modern Linux distributions.
