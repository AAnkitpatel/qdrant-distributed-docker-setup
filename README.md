# Distributed Qdrant Cluster Setup

This repository contains a Docker Compose configuration for setting up a distributed Qdrant vector search engine cluster. The configuration defines a cluster with 5 Qdrant peers, facilitating scalable and efficient vector search capabilities.

## Overview

Qdrant is a vector search engine designed for machine learning-powered applications. It allows for storing, searching, and managing millions of vectors. This setup enables Qdrant's cluster mode for distributed processing and fault tolerance.

## Prerequisites

- Docker
- Docker Compose

Ensure Docker and Docker Compose are installed on your system. For installation instructions, refer to the [official Docker documentation](https://docs.docker.com/get-docker/).

## Configuration

The `docker-compose.yml` file includes definitions for 5 Qdrant nodes (peers). Each peer is configured to participate in cluster operations, with one peer acting as the initial cluster seed (qdrant_peer_1).

### Highlights:

- **Cluster Mode Enabled**: Each Qdrant service instance is configured with clustering enabled.
- **Data Volume Mapping**: Separate data volumes for each peer to ensure data persistence.
- **Ports**: Ports 6333 (HTTP API) and 6335 (peer-to-peer communication) are exposed.
- **Environment Variables**: Configurations such as data path, peer address, and consensus tick period are specified.

## Getting Started

1. **Clone the Repository**
git clone https://github.com/AAnkitpatel/qdrant-distributed-docker-setup.git 

cd qdrant-distributed-docker

2. **Launch the Cluster**

docker-compose up -d

This command starts all the services defined in `docker-compose.yml` in detached mode.

3. **Verify Cluster Nodes**

You can verify the status of the Qdrant nodes by accessing the HTTP API of any peer, for example:

curl http://localhost:6333/cluster

Replace `localhost` with the appropriate hostname or IP address if accessing remotely.

## Managing the Cluster

- **Scaling Up/Down**: To scale the cluster, you can modify the `docker-compose.yml` file to add or remove peers and then re-deploy.

- **Monitoring and Logs**: Use Docker Compose commands to monitor the logs and status of your services.

docker-compose logs -f

- **Stopping the Cluster**:

docker-compose down

This will stop and remove all running containers defined in the compose file.

## Additional Information

For more detailed documentation on Qdrant, visit the [official Qdrant documentation](https://qdrant.tech/docs).
