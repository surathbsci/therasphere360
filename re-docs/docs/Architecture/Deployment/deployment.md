---
sidebar_position: 1
---

# Deployment

The SaMD solution is being containerized and deployed to the Digital Health Platform (AWS EKS).

A namespace has been provisioned `radcals` where all resources will be deployed and configured.

## Environments

### Development

Cluster: `awseks-dev-us-east-1`

Activity Calculator Frontend: `https://re.dev.apps.bsci.com`

Activity Calculator Backend: `https://re-api.dev.apps.bsci.com`

### Stage

Cluster: `awseks-stage-us-east-1`

Activity Calculator Frontend: `https://re.stage.apps.bsci.com`

Activity Calculator Backend: `https://re-api.stage.apps.bsci.com`

### Production

Cluster: `TBD`

Activity Calculator Frontend: `TBD`

Activity Calculator Backend: `TBD`

## Deployment Diagram

![Deployment](/deployment/deployment.svg "Deployment")
