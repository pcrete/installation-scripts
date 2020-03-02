# Helm

### **Install Helm**

```bash
curl -LO https://storage.googleapis.com/kubernetes-helm/helm-v2.8.2-linux-amd64.tar.gz
tar -xvf helm-v2.8.2-linux-amd64.tar.gz
mv linux-amd64/helm /usr/local/bin/

# initialise update the local cache to sync 
# the latest availablepackages with the environment.
helm init
helm repo update
```

### **Search For Chart**

You can now start deploying software. To find available charts you can use the search command.

`helm search redis`

We can identify more information with the _inspect_ command.

`helm inspect stable/redis`

### **Deploy Redis**

Use the _install_ command to deploy the chart to your cluster.

`helm install stable/redis`

Helm will now launch the required pods. You can view all packages using `helm ls`

If you receive an error that Helm _could not find a ready tiller pod_, it means that helm is still deploying. Wait a few moments for the tiller Docker Image to finish downloading.

In the next step we'll verify the deployment status.

### **See Results**

Helm deploys all the pods, replication controllers and services. Use _kubectl_ to find out what was deployed.

`kubectl get all`

The pod will be in a _pending_ state while the Docker Image is downloaded and until a Persistent Volume is available.

`kubectl apply -f pv.yaml`

Redis needs permissions to write `chmod 777 -R /mnt/data*`

Once complete it will move into a _running_ state. You'll now have a Redis Cluster running on top of Kubernetes.

The helm could be provided with a more friendly name, such as:

`helm install --name my-release stable/redis`

{% embed url="https://www.katacoda.com/courses/helm" %}

{% embed url="https://docs.bitnami.com/kubernetes/how-to/create-your-first-helm-chart/" %}

{% embed url="https://banzaicloud.com/blog/creating-helm-charts/" %}

{% embed url="https://www.baeldung.com/kubernetes-helm" %}

{% embed url="https://alexioannides.com/2019/01/10/deploying-python-ml-models-with-flask-docker-and-kubernetes/" %}

