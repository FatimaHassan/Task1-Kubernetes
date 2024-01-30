# Kubernetes/Helm Charts
Helm chart for deploying a web application accessible to the public for different environments
This Helm chart provides an easy and efficient way to deploy a web application that is accessible to the public. It allows for configuration of the application for different environments and includes support for calling secured endpoints using a bearer token specified as an environment variable.
## Description
This README describes a simple deployment of a Flask app using the ```digitalocean/flask-helloworld``` image. The deployment is exposed through a service that receives traffic from the ingress deployment. Additionally, a bearer token is passed as a rule using secrets within the Ingress.
```
annotations:
     nginx.ingress.kubernetes.io/auth-type: basic
     nginx.ingress.kubernetes.io/auth-secret: flask-app-secrets
```

## Configuration for Different Environments
This Helm chart includes separate values.yaml files for each environment. The following files are included:

- values-dev.yaml: Contains configuration for the development environment.  
- values.prod.yaml: Contains configuration for the production environment.

To deploy the Helm chart for a specific environment, you can specify the appropriate values.yaml file using the --values flag when running the helm install command. For example, to install the Helm chart for the production environment, you would run:
```
helm install flask-app-prod flask-app/ --values flask-app/values.yaml -f flask-app/values-prod.yaml -n prod
```
