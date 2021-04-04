# DevOps Pipeline With Tekton

# Install K0S

1. sudo curl -sSLf k0s.sh | sudo sh

2. sudo k0s install controller --enable-worker

3. sudo systemctl start k0scontroller

4. sudo systemctl status k0scontroller

5. sudo cp /var/lib/k0s/pki/admin.conf ~/admin.conf
export KUBECONFIG=~/admin.conf

# Install Metallb

kubectl create secret generic -n metallb-system memberlist --from-literal=secretkey="$(openssl rand -base64 128)"

kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.9.5/manifests/metallb.yaml

kubectl apply -f ./metallb

## Check Status

kubectl get all -n metallb-system

# Install Tekton

kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml

## Install Tekton Dashboard

kubectl apply --filename https://storage.googleapis.com/tekton-releases/dashboard/latest/tekton-dashboard-release.yaml

### Port Forwarding 

kubectl proxy --port=8080

### Ingress to the URL 

http://localhost:8080/api/v1/namespaces/tekton-pipelines/services/tekton-dashboard:http/proxy/#/namespaces/default/taskruns

## Monitoring Tekton Install 

kubectl get pods --namespace tekton-pipelines --watch
