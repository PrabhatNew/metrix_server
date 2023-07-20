# Manifest File Deployment for Metrix Server

This script deploys the manifest file for the Metrix server using Kubernetes command-line tool, `kubectl`. 

## Usage

To run the script, execute the following command:

To install the chart, follow these steps:

1. Clone this repository to your local machine:

```bash
git clone https://github.com/PrabhatNew/metrix_server.git
```

2. Change the file permession:

```bash
sudo chmod -R 777 metrix_server
```
3. Run the script:
```bash
cd metrix_server
```
```bash
bash install-metrixserver.sh
```


## Manifest File

The manifest file for the Metrix server is located in `metrixserver.yaml`.

## Horizontal Pod Autoscaler

The manifest file contains two Horizontal Pod Autoscaler objects for the `nginx` deployment, one for HPA based on memory usage and one HPA based on CPU usage. You have to deploy these yaml files manually according to the deployment you want to scale.

### hpa-mem.yaml

The `hpa-mem.yaml` HPA object scales the deployment based on resource utilization, specifically memory usage. The HPA scales the deployment to maintain an average memory utilization of 50%.

### hpa-cpu.yaml

The `hpa-cpu.yaml` HPA object scales the deployment based on CPU utilization. The HPA scales the deployment to maintain a target CPU utilization percentage of 50%. 

Both HPAs have a minimum of 1 replica and a maximum of 5 replicas. The `scaleTargetRef` refers to the `nginx` deployment object in Kubernetes.