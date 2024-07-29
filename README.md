# cAdvisorMonitor

This repository contains the configuration for a monitoring stack using Prometheus, cAdvisor, Node Exporter, Alertmanager, and Grafana. The setup collects and monitors metrics from Docker containers and the host system, sending alerts to Slack when certain conditions are met and providing a visualization dashboard.

## Prerequisites

- Docker
- Docker Compose

## Services

- **Prometheus**: Collects and stores metrics.
- **cAdvisor**: Monitors container metrics.
- **Node Exporter**: Monitors host system metrics.
- **Alertmanager**: Manages alerts and sends notifications to Slack.
- **Grafana**: Visualizes the collected metrics.

## Configuration

### Prometheus

Prometheus is configured to scrape metrics from cAdvisor and Node Exporter every 2 minutes. Alerts are defined to check for high memory and CPU usage.

### Alertmanager

Alertmanager is configured to send notifications to Slack when alerts are triggered.

### Grafana

Grafana is configured to provide a web-based dashboard for visualizing the metrics collected by Prometheus.

## Setup Instructions

1. **Clone the repository:**

    ```sh
    git clone https://git.manavira.com/bhosseini/cadvisormonitor
    cd cAdvisorMonitor
    ```

2. **Create and Configure `.env` file:**

    Create a file named `.env` in the root directory of the project and add your Slack Webhook URL and Grafana credentials:

    ```env
    SLACK_WEBHOOK_URL=https://hooks.slack.com/services/YOUR/SLACK/WEBHOOK
    GF_SECURITY_ADMIN_USER=admin
    GF_SECURITY_ADMIN_PASSWORD=admin
    ```

3. **Start the services:**

    Use Docker Compose to start the services:

    ```sh
    docker-compose up -d
    ```

## Accessing Services

### Prometheus

- URL: `http://localhost:7010`

### cAdvisor

- URL: `http://localhost:7011`

### Grafana

- URL: `http://localhost:3000`
- Default Username: `admin`
- Default Password: `admin`

## Alerting Rules

### High Container Memory Usage

Triggers if any container's memory usage exceeds 30GB for more than 1 minute.

### High Server Memory Usage

Triggers if the server's memory usage exceeds 25GB for more than 1 minute.

### High CPU Usage

Triggers if the server's CPU usage exceeds 80% for more than 1 minute.
