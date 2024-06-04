# Database Cluster with MySQL & Docker

## Project Overview

This project deploys a MySQL cluster using Docker containers, consisting of one master and two slave nodes. Additionally, it integrates Prometheus and Grafana for monitoring the cluster's status and includes a simple load testing.

## Setup Instructions

### Step 1: Configure Docker Containers

The `docker-compose.yml` file is configured with one master and two slave MySQL instances.

### Step 2: Initialize Master-Slave Replication

1. Access each of the slave databases and connect them to the master database.
2. Use the command `SHOW SLAVE STATUS\G` to verify that each slave is successfully connected to the master.  
[status-master](https://github.com/SummerEkko/data-cluster/blob/main/media/status-master.png) | [status-slave-1](https://github.com/SummerEkko/data-cluster/blob/main/media/status-slave-1.png) | [status-slave-2](https://github.com/SummerEkko/data-cluster/blob/main/media/status-slave-2.png)  

### Step 3: Load Testing

Perform load testing on all three databases using sysbench. This step helps further verify that the slaves are correctly connected to the master database.  
[load-test-master](https://github.com/SummerEkko/data-cluster/blob/main/media/load-test-master.png) | [load-test-slave-1](https://github.com/SummerEkko/data-cluster/blob/main/media/load-test-slave-1.png) | [load-test-slave-2](https://github.com/SummerEkko/data-cluster/blob/main/media/load-test-slave-2.png)  

### Step 4: Set Up Monitoring with Prometheus and Grafana

Expand the `docker-compose.yml` file to include configurations for Prometheus, Grafana, and the mysqld-exporter.

1. Launch Grafana, and configure it to use Prometheus as the data source.
2. Add panels to visualize various metrics of the MySQL cluster.  
  
![Grafana Dashboard](https://github.com/SummerEkko/data-cluster/blob/main/media/panel-1.png "Grafana Dashboard 1")  
![Grafana Dashboard](https://github.com/SummerEkko/data-cluster/blob/main/media/panel-2.png "Grafana Dashboard 2")  
![Grafana Dashboard](https://github.com/SummerEkko/data-cluster/blob/main/media/panel-3.png "Grafana Dashboard 3")  
![Grafana Dashboard](https://github.com/SummerEkko/data-cluster/blob/main/media/panel-4.png "Grafana Dashboard 4")  
![Grafana Dashboard](https://github.com/SummerEkko/data-cluster/blob/main/media/panel-5.png "Grafana Dashboard 5")  
![Grafana Dashboard](https://github.com/SummerEkko/data-cluster/blob/main/media/panel-6.png "Grafana Dashboard 6")  
  

## Additional Notes

- Make sure to expose the necessary ports for MySQL, Prometheus, and Grafana in the Docker configurations to allow proper connectivity.
- With the release of MySQL 8.4, any code involving the terms 'master' and 'slave' has been changed. Be aware of these changes if you are using the new version of MySQL.
