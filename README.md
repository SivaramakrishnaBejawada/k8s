Based on your terminal history, you have already practised several Kubernetes concepts in your Debian VM using Minikube.

I have extracted the Kubernetes commands, corrected spelling mistakes and invalid syntax, removed duplicates, and organized them concept-wise.

This will serve as your **Kubernetes command reference – Beginner to Intermediate**, based on your actual practice.

# **Kubernetes commands – concept-wise**

## **1. Cluster and node management**

You practised Minikube and Kubernetes cluster operations.

| Command                             | Purpose                       |
| ----------------------------------- | ----------------------------- |
| `minikube start`                    | Start Minikube cluster        |
| `minikube start --driver=docker`    | Start using Docker driver     |
| `minikube status`                   | Check cluster status          |
| `minikube stop`                     | Stop cluster                  |
| `minikube delete`                   | Delete cluster                |
| `minikube dashboard`                | Open Kubernetes dashboard     |
| `minikube ssh`                      | Connect to Minikube node      |
| `kubectl cluster-info`              | Display cluster information   |
| `kubectl get nodes`                 | List nodes                    |
| `kubectl get nodes -o wide`         | Detailed node information     |
| `kubectl describe node <node-name>` | Describe a node               |
| `kubectl get componentstatuses`     | Check legacy component status |

## **2. Kubernetes basic commands**

These are the commands you will use frequently.

| Command                   | Purpose                                    |
| ------------------------- | ------------------------------------------ |
| `kubectl version`         | Check kubectl version                      |
| `kubectl get all`         | List common resources in current namespace |
| `kubectl get pods`        | List Pods                                  |
| `kubectl get pod`         | List Pods                                  |
| `kubectl get services`    | List Services                              |
| `kubectl get svc`         | List Services                              |
| `kubectl get deployments` | List Deployments                           |
| `kubectl get rs`          | List ReplicaSets                           |
| `kubectl get rc`          | List ReplicationControllers                |
| `kubectl get namespaces`  | List namespaces                            |
| `kubectl get events`      | Display cluster events                     |
| `kubectl api-resources`   | List supported resource types              |
| `kubectl explain pod`     | Explain Pod specification                  |
| `kubectl explain service` | Explain Service specification              |

## **3. Pod management**

You have practised Pod creation, deletion, inspection, and troubleshooting.

| Command                               | Purpose                              |
| ------------------------------------- | ------------------------------------ |
| `kubectl apply -f pod.yaml`           | Create or update Pod                 |
| `kubectl create -f pod.yaml`          | Create Pod                           |
| `kubectl get pods`                    | List Pods                            |
| `kubectl get pods -o wide`            | Show Pod IP and node                 |
| `kubectl describe pod nginx`          | Detailed Pod information             |
| `kubectl get pod nginx -o yaml`       | Display Pod YAML                     |
| `kubectl logs nginx`                  | View Pod logs                        |
| `kubectl logs -f nginx`               | Follow logs                          |
| `kubectl logs nginx --previous`       | View previous container logs         |
| `kubectl exec -it nginx -- /bin/bash` | Enter container shell                |
| `kubectl exec -it nginx -- /bin/sh`   | Enter shell when Bash is unavailable |
| `kubectl delete pod nginx`            | Delete Pod                           |
| `kubectl delete pods --all`           | Delete all Pods in current namespace |
| `kubectl get pods --show-labels`      | Display Pod labels                   |
| `kubectl top pods`                    | Display Pod resource usage           |
| `kubectl top pod nginx --containers`  | Display container resource usage     |

## **4. ReplicationController**

You practised creating and deleting ReplicationControllers.

| Command                             | Purpose                      |
| ----------------------------------- | ---------------------------- |
| `kubectl create -f rc.yaml`         | Create ReplicationController |
| `kubectl apply -f rc.yaml`          | Create or update             |
| `kubectl get rc`                    | List ReplicationControllers  |
| `kubectl get replicationcontroller` | List RC resources            |
| `kubectl describe rc myapp-rc`      | Detailed RC information      |
| `kubectl get pods`                  | Check managed Pods           |
| `kubectl delete pod <pod-name>`     | Delete individual Pod        |
| `kubectl delete rc myapp-rc`        | Delete ReplicationController |

**Important:** If you delete a Pod managed by an RC, the controller creates a replacement to maintain the desired replica count.

## **5. ReplicaSet**

You also practised ReplicaSet creation and management.

| Command                                | Purpose                     |
| -------------------------------------- | --------------------------- |
| `kubectl create -f replicaset.yaml`    | Create ReplicaSet           |
| `kubectl apply -f replicaset.yaml`     | Create or update            |
| `kubectl get rs`                       | List ReplicaSets            |
| `kubectl get replicaset`               | List ReplicaSets            |
| `kubectl describe rs myapp-replicaset` | Describe ReplicaSet         |
| `kubectl get pods`                     | List managed Pods           |
| `kubectl delete pod <pod-name>`        | Delete a Pod                |
| `kubectl delete rs myapp-replicaset`   | Delete ReplicaSet           |
| `kubectl get rs -o wide`               | Detailed ReplicaSet listing |

## **6. Deployment management**

You have practised Deployment creation, rollout, history, and rollback.

| Command                                           | Purpose                                 |
| ------------------------------------------------- | --------------------------------------- |
| `kubectl create -f deployment.yaml`               | Create Deployment                       |
| `kubectl apply -f deployment.yaml`                | Create or update Deployment             |
| `kubectl get deployments`                         | List Deployments                        |
| `kubectl get deploy`                              | Short form                              |
| `kubectl describe deployment myapp-deployment`    | Describe Deployment                     |
| `kubectl get deployment myapp-deployment -o yaml` | Display Deployment YAML                 |
| `kubectl get rs`                                  | Check ReplicaSets created by Deployment |
| `kubectl get pods`                                | Check Deployment Pods                   |
| `kubectl delete deployment myapp-deployment`      | Delete Deployment                       |

## **7. Deployment rollout and rollback**

These are particularly important for DevOps interviews and production operations.

| Command                                                            | Purpose                       |
| ------------------------------------------------------------------ | ----------------------------- |
| `kubectl rollout status deployment/myapp-deployment`               | Check rollout status          |
| `kubectl rollout history deployment/myapp-deployment`              | View rollout history          |
| `kubectl rollout history deployment/myapp-deployment --revision=2` | View specific revision        |
| `kubectl rollout undo deployment/myapp-deployment`                 | Rollback to previous revision |
| `kubectl rollout undo deployment/myapp-deployment --to-revision=2` | Rollback to specific revision |
| `kubectl rollout restart deployment/myapp-deployment`              | Restart Deployment            |
| `kubectl rollout pause deployment/myapp-deployment`                | Pause rollout                 |
| `kubectl rollout resume deployment/myapp-deployment`               | Resume rollout                |
| `kubectl set image deployment/myapp-deployment nginx=nginx:1.27`   | Update container image        |
| `kubectl scale deployment myapp-deployment --replicas=5`           | Scale to five replicas        |
| `kubectl get rs`                                                   | Check new and old ReplicaSets |
| `kubectl describe deployment myapp-deployment`                     | Inspect Deployment            |

**Important correction from your history:**

You used:

```
kubectl rollout status myapp-replicaset
```

Correct syntax:

```
kubectl rollout status deployment/myapp-deployment
```

The resource type must be specified.

## **8. Service management – ClusterIP, NodePort and LoadBalancer**

You have started practising Kubernetes Services.

| Command                                   | Purpose                  |
| ----------------------------------------- | ------------------------ |
| `kubectl create -f service.yaml`          | Create Service           |
| `kubectl apply -f service.yaml`           | Create or update Service |
| `kubectl get svc`                         | List Services            |
| `kubectl get services`                    | List Services            |
| `kubectl describe svc nodeportservice`    | Describe Service         |
| `kubectl get svc -o wide`                 | Detailed Service listing |
| `kubectl get svc nodeportservice -o yaml` | Display Service YAML     |
| `kubectl delete svc nodeportservice`      | Delete Service           |
| `kubectl get endpoints nodeportservice`   | Check Service endpoints  |
| `kubectl get endpointslices`              | List EndpointSlices      |
| `kubectl get pods --show-labels`          | Check Pod labels         |

### **Service types**

**1. ClusterIP**

Internal communication

```
spec:
  type: ClusterIP
```

**2. NodePort**

External node access

```
spec:
  type: NodePort
```

**3. LoadBalancer**

External load balancer

```
spec:
  type: LoadBalancer
```

### **Access your Minikube NodePort Service**

```
kubectl get svc
minikube ip
minikube service nodeportservice --url
```

You can also use:

```
minikube service nodeportservice
```

## **9. Namespace management**

You haven't practised these much yet, but they are important for Kubernetes administration.

| Command                                                | Purpose                      |
| ------------------------------------------------------ | ---------------------------- |
| `kubectl get ns`                                       | List namespaces              |
| `kubectl create namespace dev`                         | Create namespace             |
| `kubectl describe ns dev`                              | Describe namespace           |
| `kubectl get pods -n dev`                              | List Pods in dev             |
| `kubectl get all -n dev`                               | List common resources in dev |
| `kubectl apply -f pod.yaml -n dev`                     | Deploy into dev              |
| `kubectl delete namespace dev`                         | Delete namespace             |
| `kubectl config set-context --current --namespace=dev` | Set default namespace        |

## **10. Labels and selectors**

These concepts are important because Services, ReplicaSets, and Deployments use selectors to identify Pods.

| Command                                            | Purpose               |
| -------------------------------------------------- | --------------------- |
| `kubectl get pods --show-labels`                   | Display labels        |
| `kubectl label pod nginx app=myapp`                | Add label             |
| `kubectl label pod nginx app=frontend --overwrite` | Update label          |
| `kubectl label pod nginx app-`                     | Remove label          |
| `kubectl get pods -l app=myapp`                    | Filter using label    |
| `kubectl get pods -l app=myapp,type=frontend`      | Match both labels     |
| `kubectl get pods -l 'app in (myapp,nginx)'`       | Match multiple values |

## **11. Troubleshooting and debugging**

These commands are essential when Pods are not starting, Services are not working, or Deployments are failing.

| Command                                                    | Purpose                                    |
| ---------------------------------------------------------- | ------------------------------------------ |
| `kubectl describe pod <pod-name>`                          | Find Pod issues                            |
| `kubectl logs <pod-name>`                                  | Check application logs                     |
| `kubectl logs <pod-name> --previous`                       | Check previous container logs              |
| `kubectl get events --sort-by=.metadata.creationTimestamp` | View latest events                         |
| `kubectl get pods -o wide`                                 | Check Pod IP and node                      |
| `kubectl get svc`                                          | Check Services                             |
| `kubectl get endpointslices`                               | Check Service backend endpoints            |
| `kubectl describe svc <service-name>`                      | Troubleshoot Service                       |
| `kubectl describe deployment <deployment-name>`            | Troubleshoot Deployment                    |
| `kubectl get pods -A`                                      | Check Pods across namespaces               |
| `kubectl get all -A`                                       | List common resources across namespaces    |
| `kubectl top nodes`                                        | Check node resource usage                  |
| `kubectl top pods -A`                                      | Check Pod resource usage across namespaces |

## **12. YAML and resource management**

| Command                           | Purpose                          |
| --------------------------------- | -------------------------------- |
| `kubectl create -f file.yaml`     | Create resource                  |
| `kubectl apply -f file.yaml`      | Create or update resource        |
| `kubectl delete -f file.yaml`     | Delete resources defined in file |
| `kubectl get pod nginx -o yaml`   | Export resource YAML             |
| `kubectl get pod nginx -o json`   | Export resource JSON             |
| `kubectl diff -f file.yaml`       | Preview changes                  |
| `kubectl replace -f file.yaml`    | Replace resource                 |
| `kubectl explain deployment.spec` | Understand Deployment fields     |
| `kubectl get all -o wide`         | Detailed resource list           |

## **13. Container image and Minikube commands**

| Command                            | Purpose                           |
| ---------------------------------- | --------------------------------- |
| `minikube image ls`                | List images available to Minikube |
| `minikube image load nginx:latest` | Load image into Minikube          |
| `minikube image rm nginx:latest`   | Remove Minikube image             |
| `minikube ssh`                     | Enter Minikube node               |
| `kubectl describe pod nginx`       | Check image and pull status       |
| `kubectl get pods`                 | Check container status            |

## **14. Resource monitoring**

| Command                              | Purpose                               |
| ------------------------------------ | ------------------------------------- |
| `kubectl top nodes`                  | Node CPU and memory usage             |
| `kubectl top pods`                   | Pod CPU and memory usage              |
| `kubectl top pods -A`                | All namespace Pod usage               |
| `kubectl top pod nginx --containers` | Individual container usage            |
| `kubectl describe node <node-name>`  | Node capacity and allocated resources |

Note: `kubectl top` requires Metrics Server to be available. In Minikube, you can enable it with:

```
minikube addons enable metrics-server
```

# **15. Mistakes identified in your terminal history**

I noticed several commands that you tried with spelling or syntax errors. Here are their corrections.

| Incorrect command                                       | Correct command                                    |
| ------------------------------------------------------- | -------------------------------------------------- |
| `kubectle get pods`                                     | `kubectl get pods`                                 |
| `kubectl get posd`                                      | `kubectl get pods`                                 |
| `kubectl get deployemnts`                               | `kubectl get deployments`                          |
| `kubectl get deployements`                              | `kubectl get deployments`                          |
| `kubectl get deployement`                               | `kubectl get deployment`                           |
| `kubectl get replicas`                                  | `kubectl get rs`                                   |
| `kubectl get rdeployment`                               | `kubectl get deployments`                          |
| `kubectl delete repliacationcontroller myapp-rc`        | `kubectl delete rc myapp-rc`                       |
| `kubectl undo rollout deployment.apps/myapp-deployment` | `kubectl rollout undo deployment/myapp-deployment` |
| `kubectl delete deployment.app/myapp-deployment`        | `kubectl delete deployment myapp-deployment`       |
| `kubectl delete nodeportservice`                        | `kubectl delete svc nodeportservice`               |
| `kubectl describe service service/kubernetes`           | `kubectl describe svc kubernetes`                  |


