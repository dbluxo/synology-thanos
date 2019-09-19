# Run Prometheus & Thanos stack on your Synology NAS

Get up and running with [Thanos](https://github.com/improbable-eng/thanos), [Prometheus](https://github.com/prometheus/prometheus), [Grafana](https://github.com/grafana/grafana) and [Blackbox exporter](https://github.com/prometheus/blackbox_exporter) on your [Synology NAS](https://www.synology.com/en-global/products) for learning purposes.

# Running the example

0. This project assumes that your Synology NAS has the IP address: 192.168.2.12 (otherwise it will need to be customized in the files).
1. Upload [this](./volume/docker) directory to the Synology Shared Folder for Docker.
2. Make sure to set the right access rights to the subdirectories.
3. Upload [this](./imports) directory to the Synology.
4. Download all required Docker images in the Docker App under `Image`.
5. Import all in step `3.` uploaded files via Docker App under `Container` and start the Docker containers!

The following services will be installed (and some are accessible via browser):

| Component                     | Description                                                               | URL                           |
| -----------------------       | ------------------------------------------------------                    | ----------------------------- |
| prometheus-1                  | Prometheus Server 1 (labels: cluster=synology, replica=r1)       | http://192.168.2.12:9080/        |
| prometheus-2                  | Prometheus Server 2 (labels: cluster=synology, replica=r2)        | http://192.168.2.12:9090/       |
| thanos-sidecar-1              | Thanos Sidecar for Prometheus Server 1                                    | not accessible via browser    |
| thanos-sidecar-2              | Thanos Sidecar for Prometheus Server 2                                    | not accessible via browser    |
| thanos-querier                | Thanos Query Gateway                                                             | http://192.168.2.12:10904/        |
| thanos-store-gateway          | Thanos Store Gateway                                                             | not accessible via browser    |
| thanos-compactor              | Thanos Compactor                                                                 | not accessible via browser    |
| minio                         | Minio - Amazon S3 Compatible Object Storage  | http://192.168.2.12:8000/ |
| grafana                       | Grafana                              | https://192.168.2.12:3001/login       |
| blackbox-exporter                      | Blackbox exporter                                                                 | http://192.168.2.12:9115/         |

# Credentials

Grafana:

	username - admin
	password - admin (must be changed on first login)
  
Minio:

	Access Key - smth
	Secret Key - Need8Chars (Keys are stored in the `minio.json` file)

# Notes

This project is intended to be a quick-start to get up and running with Prometheus & Thanos. Security has not been implemented in this project.
