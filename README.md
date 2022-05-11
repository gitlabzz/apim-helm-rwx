# Helmchart for Amplify API-Management

## Introduction

This Helmchart can be used to deploy the Axway API management solution on a Kubernetes environment. It is not tied to any dedicated version, i.e. you can deploy any version >=7.7 (e.g. 7.7.20210830) by configuring the corresponding ImageTag. 
Axway does not provide pre-built images as of today, so you have to build them yourself in advance, store them in your container registry and reference them accordingly in your local-values.

## Prerequisite

This Helmchart requires the following capabilities on the Kubernetes cluster:

- A minimal Kubernetes version 1.11
- `kubectl` installed and configured to your Kubernetes cluster
- Helm is installed and configured
- A configured Ingress-Controller depending on your platform - for BCT, Tanzu HTTPProxy has been used
- If persistence is enabled 
  - A storage class with in RWM.
  - A storage class with in RWO.
- A container registry with API-Gateway and API-Portal images
  - To learn more how to build API-Gateway Docker-Image [click here](https://docs.axway.com/bundle/axway-open-docs/page/docs/apim_installation/apigw_containers/docker_script_baseimage/index.html)
  - To learn more how to build/use the API-Portal Docker image [click here](https://docs.axway.com/bundle/axway-open-docs/page/docs/apim_installation/apiportal_docker/index.html)

Even though this documentation tries to explain the deployment as best as possible, a solid understanding of your Kubernetes-Distribution, your underlying platform, Internet-Naming-Service and of course Helm is absolutely necessary for the installation.  

## SIT DNS entries to access APIM components

| APIM Component Names      | FQDN                                            | Comment                                        | 
| :---                      | :---                                            | :---                                           |
| API Node Manager Console  | https://anm-sitk8apim.bcthk.info                | To manage APIG and APIM runtimes
| API Manager Console       | https://manager-sitk8apim.bcthk.info            | API Lifecycle Management
| API Manager Traffic       | https://traffic-sitk8apim.bcthk.info            | APIM traffic port for Client endpoints
| API Analytics             | https://aga-sitk8apim.bcthk.info                | API Monitoring dashboard
| API OAuth                 | https://oauth-sitk8apim.bcthk.info              | OAuth traffic port
| Default TLS Traffic       | https://tls-sitk8apim.bcthk.info                | APIG traffic port
| API Portal Console        | https://apiportal-sitk8apim.bcthk.info                | Self-service endpoint to access API Portal
| API Portal Admin Console  | https://apiportal-sitk8apim.bcthk.info/administrator  | Portal Administration endpoint

## UAT DNS entries to access APIM components

| APIM Component Names      | FQDN                                            | Comment                                        | 
| :---                      | :---                                            | :---                                           |
| API Node Manager Console  | https://anm-uatk8apim.bcthk.info                | To manage APIG and APIM runtimes
| API Manager Console       | https://manager-uatk8apim.bcthk.info            | API Lifecycle Management
| API Manager Traffic       | https://traffic-uatk8apim.bcthk.info            | APIM traffic port for Client endpoints
| API Analytics             | https://aga-uatk8apim.bcthk.info                | API Monitoring dashboard
| API OAuth                 | https://oauth-uatk8apim.bcthk.info              | OAuth traffic port
| Default TLS Traffic       | https://tls-uatk8apim.bcthk.info                | APIG traffic port
| API Portal Console        | https://apiportal-uatk8apim.bcthk.info                | Self-service endpoint to access API Portal
| API Portal Admin Console  | https://apiportal-uatk8apim.bcthk.info/administrator  | Portal Administration endpoint

