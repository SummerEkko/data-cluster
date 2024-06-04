# MySQL Cluster with Docker

## Project Overview

This project deploys a MySQL cluster using Docker containers, consisting of one master and two slave nodes. Additionally, it integrates Prometheus and Grafana for monitoring the cluster's status and includes a simple load testing.

## Setup Instructions

### Step 1: Configure Docker Containers

The `docker-compose.yml` file is configured with one master and two slave MySQL instances. Ensure each instance is properly set up with the correct environment variables and configurations.

### Step 2: Initialize Master-Slave Replication

1. Access each of the slave databases and connect them to the master database.
2. Use the command `SHOW SLAVE STATUS\G` to verify that each slave is successfully connected to the master.

### Step 3: Load Testing

Perform load testing on all three databases using sysbench. This step helps further verify that the slaves are correctly connected to the master database.

### Step 4: Set Up Monitoring with Prometheus and Grafana

Expand the `docker-compose.yml` file to include configurations for Prometheus, Grafana, and the mysqld-exporter.

1. Launch Grafana, and configure it to use Prometheus as the data source.
2. Add panels to visualize various metrics of the MySQL cluster.

## Additional Notes

- Make sure to expose the necessary ports for MySQL, Prometheus, and Grafana in the Docker configurations to allow proper connectivity.
- With the release of MySQL 8.4, any code involving the terms 'master' and 'slave' has been changed. Be aware of these changes if you are using the new version of MySQL.