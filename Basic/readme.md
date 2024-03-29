### Kubernetes Basics

#### Key concepts

- Pods
- Replica sets
- Deployments
- Services
- Namespaces
- Configmaps
- Secrets
- Volumes
- Persistent volumes
- Persistent Volume Claims
- Statefulsets
- Damonsets


### Prerequisties

- Docker setup: https://docs.docker.com/engine/install/
- Kubectl installation: https://kubernetes.io/docs/tasks/tools/
- Minikube setup : https://minikube.sigs.k8s.io/docs/start/


```
docker version

kubectl version

minikube version

minikube start
```

#### Pods

The smallest unit in Kubernetes, representing one or more containers running together on a shared network and storage. Pods are the basic building blocks of applications.

```
kubectl apply -f pod.yml

kubectl get pods -w

kubectl delete -f pod.yml

```

#### Replica sets

a specified number of identical pod replicas are running at all times

```
kubectl apply -f replicaset.yml

kubectl get pods -w

kubectl delete -f replicaset.yml

```

#### Deployments

A higher-level abstraction that manages ReplicaSets and provides declarative updates to pods. Deployments allow rolling updates and rollbacks of application changes.

```
kubectl apply -f deployment.yml

kubectl get pods -w

kubectl get deployment

kubectl rollout history deployment myapp

kubectl rollout undo deployment myapp --to-revision=1

```


#### Services

An abstraction that provides a stable network endpoint to access one or more pods. Services enable load balancing and service discovery within a cluster

**Node port**
```
kubectl apply -f nodeport.service.yml

kubectl get svc

kubectl port-forward service/myapp 7000:80

http://localhost:7000

kubectl delete -f nodeport.service.yml
```

**Load Balancer**
```
kubectl apply -f loadbalancer.service.yml

kubectl get svc -w

minikube tunnel (on next terminal)

kubectl delete -f loadbalancer.service.yml
```

**Ingress controller**
```
kubectl apply -f ingress.service.yml

kubectl get ingress

minikube tunnel (on next terminal)

kubectl delete -f ingress.service.yml
```



#### Namespaces

logically divide a Kubernetes cluster into multiple virtual clusters

```
kubectl apply -f namespace.yml

kubectl get ns

kubectl apply -f pod.yml -n my-namespace

kubectl get pods -n my-namespace

kubectl delete -f namespace.yml

```

#### Configmaps

A configuration mechanism to decouple configuration data from container images. ConfigMaps store key-value pairs or configuration files that can be consumed by pods.

```
kubectl apply -f configmap.yml

kubectl get pods -w

kubectl delete -f configmap.yml

```

#### Secrets

Secrets store sensitive information such as passwords, tokens, or certificates. They are encoded or encrypted to protect the data.

```
kubectl apply -f secrets.yml

kubectl get pods -w

kubectl delete -f secrets.yml

```

#### Volumes

A directory accessible to containers within a pod, used to persist data or share files between containers.

```
kubectl apply -f podvolume.yml

kubectl get pods

kubectl delete -f podvolume.yml

```

- Persistent volumes
A Persistent Volume is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using a StorageClass. It is a physical storage resource available in the cluster, such as a disk or network-attached storage.

```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mongodb-pv
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  storageClassName: standard
  hostPath:
    path: /path/to/host/folder

```

- Persistent Volume Claims

A Persistent Volume Claim is a request for storage by a user or application. It is used to claim a specific amount of storage from a Persistent Volume. When a PVC is created, Kubernetes finds an available PV that satisfies the PVC's requirements and binds it to the claim.

```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mongodb-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
  storageClassName: standard

```


```
kubectl apply -f persistentvolume.yml

kubectl delete -f persistentvolume.yml


```

- Statefulsets

It is used to manage stateful applications, where each pod has a unique identity and requires stable network identifiers, persistent storage, and ordered deployment or scaling.

```
kubectl apply -f statefulset.yml

kubectl get statefulset

kubectl get pods

kubectl apply -f statefulset.yml
```


- Damonsets

A controller that ensures a copy of a pod is running on each node in the cluster. DaemonSets are useful for running monitoring agents, log collectors, or other system-level tasks

```
kubectl apply -f daemonset.yml

kubectl delete -f daemonset.yml

```








