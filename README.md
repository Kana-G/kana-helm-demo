# Helm Chart Demo application

This Helm chart deploys a multi-service application on Kubernetes. The stack includes Nginx as a reverse proxy, a Java-based web application, a React-based UI, and two Python services.

## Prerequisites

- Kubernetes cluster
- Helm 3.x

## Chart Structure

├── Chart.yaml<br>
├── values.yaml<br>
├── templates/<br>
│ ├── _helpers.tpl<br>
│ ├── nginx-deployment.yaml<br>
│ ├── nginx-service.yaml<br>
│ ├── nginx-configmap.yaml<br>
│ ├── java-webapp-deployment.yaml<br>
│ ├── java-webapp-service.yaml<br>
│ ├── react-ui-deployment.yaml<br>
│ ├── react-ui-service.yaml<br>
│ ├── python-service1-deployment.yaml<br>
│ ├── python-service1-service.yaml<br>
│ ├── python-service2-deployment.yaml<br>
│ ├── python-service2-service.yaml<br>
│ └── ingress.yaml<br>
└── nginx/<br>
   └── nginx.conf<br>


## Installation

1. Add your custom configuration to the `values.yaml` file if needed.
2. Install the chart using Helm:

```helm install kana-helm-demo ./kana-helm-demo```


Accessing the Application
Once the chart is successfully deployed, you can access the services as follows:

Nginx (Reverse Proxy): http://nginx-service-IP<br>
React UI: http://react-ui-service-IP:3000<br>
Java Web Application: http://java-webapp-service-IP:8080<br>
Python Service 1: http://python-service1-IP:5000<br>
Python Service 2: http://python-service2-IP:5001<br>
If Ingress is enabled and configured, access the application via the Ingress host:

http://kana-helm-demo.local

## Customizing the Chart
You can override the default values by creating your own values.yaml file and using it when installing the chart:

```helm install kana-helm-demo ./kana-helm-demo -f your-values.yaml```

## Nginx Configuration
The Nginx reverse proxy configuration is specified in nginx/nginx.conf and applied using a ConfigMap:
Refer config from ```nginx/nginx.conf```

## Cleaning up
To uninstall the chart and remove all deployed resources, run:

```helm uninstall kana-helm-demo```

## GitHub Actions Workflow
The deployment github action is part of ```helm-deployment-workflow.yaml``` Please move that to ```.github/workflows/deploy.yaml``` to reflect in github actions workflow.

### Adding secrets
To add the KUBE_CONFIG_DATA secret to your GitHub repository:
Convert your kubeconfig file to base64:
```cat ~/.kube/config | base64```
Go to your GitHub repository, navigate to Settings > Secrets and variables > Actions, and click New repository secret.
Name the secret KUBE_CONFIG_DATA and paste the base64-encoded content.

