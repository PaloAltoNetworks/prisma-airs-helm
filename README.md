# Prisma AIRS AI Runtime Helm Deployment ⛵⎈ 

This repository contains charts and templates for deploying the Palo Alto Networks Prisma AIRS AI Runtime: Network intercept for on-prem installations firewall using the [Helm Package Manager for Kubernetes](https://helm.sh)

Please read the `README.md` in the `helm` folder for instructions to apply the Helm chart.

## Documentation

The Release Notes and Deployment Guide is at [Prisma AIRS AI Runtime Security](https://docs.paloaltonetworks.com/ai-runtime-security)

## Usage

### Method 1 - With Repo

1. Clone the repository from GitHub

    ```bash
    $ git clone https://github.com/PaloAltoNetworks/prisma-airs-helm.git
    ```

2. Change into the repo directory

    ```bash
    $ cd cn-series-airs-helm
    ```

3. Edit the `values.yaml` file and plug in your specific configs. 
Make sure to read through the values.yaml to chose the specific deployment tyoe and additional configurations.

4. To deploy the helm charts

    ```bash
    helm upgrade ai-runtime-security helm --namespace kube-system --values helm/values.yaml
    ```


## Helm Validation Instructions

To learn more about the release, try:

    ```bash
    helm list -A
    helm status <RELEASE_NAME> -n kube-system
    helm get all <RELEASE_NAME> -n kube-system
    ```

## Kubernetes Validation Instructions

Check the endpoint slices:

    ```bash
    kubectl get endpointslices -n kube-system | grep pan
    ```

Verify the Kubernetes resources were created properly:

    ```bash
    a. Check the service accounts

    kubectl get serviceaccounts -n kube-system | grep pan

    b. Check the secrets

    kubectl get secrets -n kube-system | grep pan

    c. Check the services:

    kubectl get svc -n kube-system | grep pan
    ```