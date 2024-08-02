# Ethereum Node Monitoring

## Services Running

1. **Ethereum (Geth)**

   - Image: `ethereum/client-go:stable`
   - Description: Ethereum node running on the Ropsten test network with snap synchronization.

2. **Geth Exporter**

   - Image: `hunterlong/geth_exporter`
   - Description: Exporter for Geth metrics to Prometheus.

3. **Prometheus**

   - Image: `prom/prometheus`
   - Description: Monitoring and alerting system. Collects metrics from Geth Exporter and Node Exporter.

4. **Grafana**

   - Image: `grafana/grafana`
   - Description: Visualization and analysis platform. Uses Prometheus and Loki as data sources.

5. **Loki**

   - Image: `grafana/loki`
   - Description: Log aggregation system. Receives logs sent by Promtail.

6. **Promtail**

   - Image: `grafana/promtail`
   - Description: Log collection agent. Sends Geth logs to Loki.

7. **Alertmanager**

   - Image: `prom/alertmanager`
   - Description: Alert manager. Sends notifications based on alert rules configured in Prometheus.

8. **Node Exporter**
   - Image: `prom/node-exporter`
   - Description: System metrics exporter for Prometheus.

## How to Run the Project

### Prerequisites

- Docker
- Docker Compose

### Steps to Run

1. **Clone the repository:**

   ```sh
   git clone <REPOSITORY_URL>
   cd <REPOSITORY_DIRECTORY>
   Start the containers:
   docker-compose up -d

   ```

## Access Grafana

- **URL:** [http://localhost:3000](http://localhost:3000)
- **Username:** admin
- **Password:** admin

## Configure Datasources in Grafana

### Add Loki Datasource

- **Type:** Loki
- **URL:** [http://loki:3100](http://loki:3100)

### Add Prometheus Datasource

- **Type:** Prometheus
- **URL:** [http://prometheus:9091](http://prometheus:9091)

## Mapped Alerts

- **EthereumNodeDown:** Alerts if the Ethereum node is down for more than 1 minute.
- **HighMemoryUsage:** Alerts if memory usage is above 80% for more than 5 minutes.
- **HighCPULoad:** Alerts if CPU load is above 2 for more than 5 minutes.

## Dashboards to Import

### Loki Dashboard

- **ID:** 13639
- **Description:** Monitors and visualizes logs collected by Promtail and stored in Loki.

### Geth Dashboard

- **ID:** 6976
- **Description:** Monitors specific metrics of the Ethereum node, such as CPU usage, memory usage, synchronization status, etc.

### Node Exporter Dashboard

- **ID:** 1860
- **Description:** Monitors system metrics of the servers, such as CPU usage, memory usage, disk usage, and network usage.

## Steps to Import Dashboards

1. **Import Dashboard in Grafana:**
   - Go to "Create" > "Import".
   - Enter the dashboard ID (13639, 6976, or 1860).
   - Click on "Load".
   - Configure the data source as needed (Loki or Prometheus).
   - Click on "Import".

```

```
