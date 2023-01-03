# ArgoCD Applicationset Manager
* This repository demonstrates the ability to use an app-of-apps model for managing ArgoCD Applicationsets with Kustomize as configuration management.

## Important Notes About ArgoCD

* **The word applicaitons(s) will be used ALOT**

* **Argo CD applications are NOT the same as web applications, although web applications can be deployed using Argo CD.**

* **Argo CD can be used to deploy and manage web applications, as well as other types of applications, on a Kubernetes cluster. However, Argo CD is not a platform for building or running web applications itself.**

## App-Of-Apps & Applicationset Model

* The app-of-apps model in Argo CD is a pattern for organizing and managing applications in a way that allows you to reuse common components and resources across multiple applications.

* In Argo CD, an ApplicationSet is a collection of applications that are managed as a unit. An ApplicationSet allows you to define a set of applications that should be deployed together and to specify the deployment order and other details such as the deployment strategy.

* Kustomize is a Kubernetes configuration transformation tool that enables you to customize untemplated YAML files, leaving the original files untouched.

# How This Works

* Essentially one ArgoCD application (app-of-apps) will manage an ArgoCD applicationset which using a list generator. This will deploy several web applications at once in different enviornments with one command. In this case, the ```qa, stage, and prod``` namespaces. The web applications will create their own namespaces inside the Kubernetes once deployed. The goal is to provide easy management and visibility for your web applications in Kubernetes.

# Deploying Applications to ArgoCD

* Since we are using Kustomize, navigate to the ```argocd-overlays``` folder to deploy applications.

* Best practice is to use a repository utilizing your ssh private key, HOWEVER for demo purposes here replace this repository in the configuration files with an https clone. For example: ```https://github.com/jcquiles/ArgoCD.git```

* **Make sure the repository you are using is configured inside ArgoCD and can be recongninzed by Argo.**

* Inside the ```argocd-overlays``` folder simply execute the following Kustomize command ```kubectl apply -k .```
