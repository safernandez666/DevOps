# DevOps Pipeline With Tekton

# Install K0S

# Install Metallb

# Install Tekton

kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml

## Install Tekton Dashboard

kubectl apply --filename https://storage.googleapis.com/tekton-releases/dashboard/latest/tekton-dashboard-release.yaml

## Monitoring Tekton Install 

kubectl get pods --namespace tekton-pipelines --watch
