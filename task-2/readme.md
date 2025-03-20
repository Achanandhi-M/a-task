# Kubernetes Security Scan

## Overview
This project involves setting up a local Kubernetes cluster, performing a security scan using Kubescape, and generating a JSON report of security findings.

## Project Structure
```
├── results.json   # JSON file containing security findings
├── commands.sh   # Script containing the scan command used
├── README.md
```

## Step 1: Set Up a Local Kubernetes Cluster

### Install K3s
You can use any local Kubernetes cluster. For example, to install K3s:

```sh
curl -sfL https://get.k3s.io | sh -
```

Verify the installation:
```sh
sudo k3s kubectl get nodes
```

## Step 2: Install Kubescape

Install Kubescape using the following command:

```sh
curl -s https://raw.githubusercontent.com/kubescape/kubescape/master/install.sh | /bin/bash
```

Verify the installation:
```sh
kubescape version
```

## Step 3: Run a Security Scan

I scanned my K3s cluster using Kubescape. The command I used is stored in `commands.sh` for reference. The scan command was:

```sh
kubescape scan --format json --output results.json
```

This will generate a JSON file (`results.json`) containing the security findings.

## Step 4: Review Findings

To analyze the findings in the `results.json` file:

```sh
cat results.json | jq .
```

## Deliverables
- `results.json`: The full security scan report containing vulnerabilities and misconfigurations.
- `commands.sh`: The script containing the command used for scanning.

## Conclusion
This project demonstrates how to set up a local Kubernetes cluster, scan it using Kubescape, and generate a security report in JSON format. This helps identify vulnerabilities and misconfigurations in a Kubernetes environment.
