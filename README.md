# Server Monitoring and Metrics Collection Project

This project consists of two Docker Compose files that work together to gather and monitor server metrics. One of the Compose files is responsible for gathering data from the server, while the other handles monitoring and displaying the data using Prometheus and Grafana.

## Project Structure

- `docker-compose.metrics.yml`: This file configures services to collect server metrics using `node-exporter` and `cAdvisor`.
- `docker-compose.monitoring.yml`: This file configures services to monitor and display the collected data using `Prometheus`, `Grafana`, and `nginx`.

## Prerequisites

Before running this project, make sure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Setup and Usage

### 1. Clone the repository

```bash
git clone <repository-url>
cd <repository-directory>
```

## Configure environment variables
Ensure that you have a .env file in the root directory with the following variables:
```bash
GF_SECURITY_ADMIN_USER=your_admin_username
GF_SECURITY_ADMIN_PASSWORD=your_admin_password
```
### 3. Run the metrics collection stack

First, run the `docker-compose.metrics.yml` file to start collecting server metrics:

```bash
docker-compose -f docker-compose.metrics.yml up -d
```
This will start the following services:

- node-exporter: Exposes hardware and OS metrics.
- cAdvisor: Collects container metrics.

### 4. Run the monitoring stack

Next, run the `docker-compose.monitoring.yml` file to start monitoring and visualizing the collected data:

```bash
docker-compose -f docker-compose.monitoring.yml up -d
```

### 5. Access Grafana Dashboard

Once everything is up and running, you can access Grafana by navigating to:

```
http://<your-server-ip>:7012
```
### 6. Stopping the Services

To stop the services, use the following commands:

```bash
docker-compose -f docker-compose.metrics.yml down
docker-compose -f docker-compose.monitoring.yml down
```

### 7. Customizing Configuration

- **Prometheus Configuration**: You can customize the Prometheus configuration by editing the `prometheus.yml` file located in the root directory.
- **Grafana Dashboards**: Grafana dashboards can be customized and new ones can be created through the Grafana UI.


### Troubleshooting

If you encounter any issues, ensure that the required ports (9100, 7011, 7010, 7012) are not being used by other applications. You can also check the logs of individual services by using:

```bash
docker-compose -f <compose-file-name> logs <service-name>
```
## License

This project is licensed under the MIT License - see the `LICENSE` file for details.

## Contributing

Feel free to fork this project and submit pull requests. Any contributions are welcome!

## Acknowledgments

- Prometheus
- Grafana
- node-exporter
- cAdvisor

