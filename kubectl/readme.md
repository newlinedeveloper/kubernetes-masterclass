Absolutely! Here's a categorized list of **essential `kubectl` commands** that every Kubernetes developer and Operator builder should know.

---

## 🔍 **Basic Cluster Info**

| Operation          | Command                 |
| ------------------ | ----------------------- |
| Show cluster info  | `kubectl cluster-info`  |
| Show all nodes     | `kubectl get nodes`     |
| Show API resources | `kubectl api-resources` |

---

## 📦 **Working with Namespaces**

| Operation               | Command                                                |
| ----------------------- | ------------------------------------------------------ |
| List all namespaces     | `kubectl get ns`                                       |
| Set a default namespace | `kubectl config set-context --current --namespace=dev` |
| Create a namespace      | `kubectl create ns staging`                            |
| Delete a namespace      | `kubectl delete ns staging`                            |

---

## 🚀 **Deployments, Pods, and Services**

| Resource           | Command                                        |
| ------------------ | ---------------------------------------------- |
| View all resources | `kubectl get all`                              |
| View pods          | `kubectl get pods`                             |
| View deployments   | `kubectl get deployments`                      |
| Describe a pod     | `kubectl describe pod POD_NAME`                |
| Logs of a pod      | `kubectl logs POD_NAME [-c CONTAINER_NAME]`    |
| Exec into a pod    | `kubectl exec -it POD_NAME -- /bin/sh`         |
| Create from YAML   | `kubectl apply -f deployment.yaml`             |
| Delete from YAML   | `kubectl delete -f deployment.yaml`            |
| Scale deployment   | `kubectl scale deployment my-app --replicas=5` |
| Rollout status     | `kubectl rollout status deployment/my-app`     |
| Restart deployment | `kubectl rollout restart deployment/my-app`    |

---

## 📂 **ConfigMaps and Secrets**

| Resource              | Command                                                       |             |
| --------------------- | ------------------------------------------------------------- | ----------- |
| List ConfigMaps       | `kubectl get configmaps`                                      |             |
| View ConfigMap        | `kubectl describe configmap my-config`                        |             |
| Create ConfigMap      | `kubectl create configmap my-config --from-literal=key=value` |             |
| Delete ConfigMap      | `kubectl delete configmap my-config`                          |             |
| View Secret (encoded) | `kubectl get secret my-secret -o yaml`                        |             |
| Decode secret         | \`kubectl get secret my-secret -o jsonpath="{.data.password}" | base64 -d\` |

---

## ⚙️ **Custom Resources & CRDs**

| Operation                        | Command                             |
| -------------------------------- | ----------------------------------- |
| List CRDs                        | `kubectl get crds`                  |
| Get custom resource (e.g. MyApp) | `kubectl get myapps`                |
| Describe custom resource         | `kubectl describe myapp myapp-name` |
| Apply CR from YAML               | `kubectl apply -f myapp.yaml`       |
| Delete CR from YAML              | `kubectl delete -f myapp.yaml`      |

---

## 🧪 **Debugging & Troubleshooting**

| Operation            | Command                                                      |
| -------------------- | ------------------------------------------------------------ |
| View events          | `kubectl get events --sort-by='.metadata.creationTimestamp'` |
| Dry-run create       | `kubectl apply -f file.yaml --dry-run=client -o yaml`        |
| Explain any resource | `kubectl explain deployment`                                 |
| Port forward a pod   | `kubectl port-forward pod/mypod 8080:80`                     |
| Port forward service | `kubectl port-forward svc/myservice 8080:80`                 |

---

## 📄 **YAML Generation & Editing**

| Operation               | Command                                 |
| ----------------------- | --------------------------------------- |
| Output resource as YAML | `kubectl get deployment my-app -o yaml` |
| Edit a resource         | `kubectl edit deployment my-app`        |
| Diff before apply       | `kubectl diff -f myapp.yaml`            |
| Replace resource        | `kubectl replace -f updated.yaml`       |

---

## 🧼 **Cleanup & Delete**

| Resource                         | Command                                              |
| -------------------------------- | ---------------------------------------------------- |
| Delete a pod                     | `kubectl delete pod my-pod`                          |
| Delete all pods                  | `kubectl delete pods --all`                          |
| Delete everything in a namespace | `kubectl delete all --all -n dev`                    |
| Force delete stuck pod           | `kubectl delete pod my-pod --grace-period=0 --force` |

---

