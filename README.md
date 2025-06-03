# Telegraf, InfluxDB, Grafana (TIG) Stack

Gain the ability to analyze and monitor telemetry data by deploying the TIG stack within minutes using [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/).

## ⚡️ Getting Started

Clone the project

```bash
git clone https://github.com/huntabyte/tig-stack.git
```

Navigate to the project directory

```bash
cd tig-stack
```

## 🔧 Environment Configuration

Create a `.env` file in the root directory with the following environment variables:

```bash
├── telegraf/
├── .env         <--- Create this file
├── docker-compose.yml
├── entrypoint.sh
└── ...
```

### Required Environment Variables

Create a `.env` file with the following variables:

```bash
# InfluxDB Configuration
DOCKER_INFLUXDB_INIT_MODE=setup
DOCKER_INFLUXDB_INIT_USERNAME=admin
DOCKER_INFLUXDB_INIT_PASSWORD=your_secure_password
DOCKER_INFLUXDB_INIT_ORG=my-org
DOCKER_INFLUXDB_INIT_BUCKET=my-bucket
DOCKER_INFLUXDB_INIT_RETENTION=1w
DOCKER_INFLUXDB_INIT_ADMIN_TOKEN=your_admin_token_here
DOCKER_INFLUXDB_INIT_PORT=8086
DOCKER_INFLUXDB_INIT_HOST=influxdb

# Grafana Configuration
GRAFANA_PORT=3000

# Telegraf Configuration
TELEGRAF_CFG_PATH=./telegraf/telegraf.conf
```

### Environment Variables Description

| Variable                           | Description                          | Example Value              |
| ---------------------------------- | ------------------------------------ | -------------------------- |
| `DOCKER_INFLUXDB_INIT_MODE`        | InfluxDB initialization mode         | `setup`                    |
| `DOCKER_INFLUXDB_INIT_USERNAME`    | Initial admin username for InfluxDB  | `admin`                    |
| `DOCKER_INFLUXDB_INIT_PASSWORD`    | Initial admin password for InfluxDB  | `your_secure_password`     |
| `DOCKER_INFLUXDB_INIT_ORG`         | Default organization name            | `my-org`                   |
| `DOCKER_INFLUXDB_INIT_BUCKET`      | Default bucket name for storing data | `my-bucket`                |
| `DOCKER_INFLUXDB_INIT_RETENTION`   | Default data retention period        | `1w` (1 week)              |
| `DOCKER_INFLUXDB_INIT_ADMIN_TOKEN` | Admin token for API access           | `your_admin_token_here`    |
| `DOCKER_INFLUXDB_INIT_PORT`        | Port for InfluxDB service            | `8086`                     |
| `DOCKER_INFLUXDB_INIT_HOST`        | Hostname for InfluxDB service        | `influxdb`                 |
| `GRAFANA_PORT`                     | Port for Grafana web interface       | `3000`                     |
| `TELEGRAF_CFG_PATH`                | Path to Telegraf configuration file  | `./telegraf/telegraf.conf` |

## 📝 Telegraf Configuration

Customize the `telegraf.conf` file which will be mounted to the container as a persistent volume

```bash
├── telegraf/
│   ├── telegraf.conf <--- Configure your inputs and outputs here
├── .env
├── docker-compose.yml
├── entrypoint.sh
└── ...
```

## 🚀 Deployment

Start the services

```bash
docker-compose up -d
```

## 🌐 Access the Services

After deployment, you can access:

- **InfluxDB UI**: http://localhost:8086
- **Grafana Dashboard**: http://localhost:3000
- **Telegraf**: Runs as a background service (no web interface)

### Default Login Credentials

- **InfluxDB**: Use the username and password defined in your `.env` file
- **Grafana**: Default is `admin/admin` (you'll be prompted to change on first login)

## Docker Images Used (Official & Verified)

[**Telegraf**](https://hub.docker.com/_/telegraf) / `latest`

[**InfluxDB**](https://hub.docker.com/_/influxdb) / `2`

[**Grafana-OSS**](https://hub.docker.com/r/grafana/grafana-oss) / `latest`

## Contributing

Contributions are always welcome!
