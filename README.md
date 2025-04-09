
# Docker Swarm Vagrant Demo

This is a demo project that provisions a multi-node Docker Swarm environment on Windows using Vagrant and VirtualBox.

## Project Overview

This repository creates three virtual machines:
- **Manager:** Initializes the Docker Swarm cluster.
- **Worker1 and Worker2:** Join the Docker Swarm.

After provisioning, you can use these VMs to deploy Docker services in a Swarm cluster.

## Prerequisites

- [Vagrant](https://www.vagrantup.com/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- Windows OS

## Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/jadeleke/docker-swarm-vagrant-demo.git
   cd docker-swarm-vagrant-demo
   ```

2. **Start the Vagrant environment:**

   ```bash
   vagrant up
   ```

   This command will:

   - Download the Ubuntu focal64 box (if not already cached).
   - Spin up three VMs (manager, worker1, worker2).
   - Install Docker on each VM.

3. **Access the VMs:**

   - Manager: `vagrant ssh manager`
   - Worker1: `vagrant ssh worker1`
   - Worker2: `vagrant ssh worker2`

## Usage

### Initialize Docker Swarm on the Manager:

```bash
sudo docker swarm init --advertise-addr 192.168.56.10
```

Copy the join token from the output.

### Join the Worker Nodes:

SSH into each worker node and run the join command:

```bash
sudo docker swarm join --token <JOIN_TOKEN> 192.168.56.10:2377
```

### Verify the Cluster:

On the Manager node, run:

```bash
sudo docker node ls
```

You should see all nodes listed as part of the swarm.

### Optional: Deploy a Test Service:

On the manager node, deploy a simple NGINX service:

```bash
sudo docker service create --name demo-nginx --replicas 3 -p 80:80 nginx
```

Verify with:

```bash
sudo docker service ls
sudo docker service ps demo-nginx
```

## Troubleshooting

### Permission Denied Errors:
Use `sudo` with Docker commands unless you add your user to the `docker` group.

### Vagrant Issues on Windows:
If encountering SSL/TLS errors, consider manually adding the box.

## Cleanup

To stop the VMs:

```bash
vagrant halt
```

To remove them:

```bash
vagrant destroy -f
```

## License

This project is provided under the MIT License.
