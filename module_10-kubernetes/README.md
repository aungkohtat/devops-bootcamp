# Kubernetes module

## Overview

- Kubernetes is the mostly used container orchestation tool.
- It offers: high availability, automatic scaling, disaster recovery and self-healing.


### K8s commands:

- minicube(start / stop) - for testing cluster setup on local
- kubectl - cmd line tool for K8s: talk to API server
- kubectl get nodes
- kubectl get pod
- kubectl get pod -o wide (display more info for pod like IP address)
- kubectl get deployment
- kubectl get services
- kubectl create deployment NAME --image=image
- kubectl edit deployment NAME
- kubectl logs NAME
- kubectl describe pod NAME
- kubectl exec -it NAME -- bin/bash
- kubctl delete deployment NAME
- kubectl apply -f FILENAME


**Pods**

- the smallest unit of k8s
- abstraction over container 
- tipically 1 pod contains 1 container
- ephemeral 
- new IP address is assign on re-creation

**Service**

- static IP for the pods
- lifecycle of the pods and service are not connected
- load balancer between pods
- could be internal (database) or external (app accessed through browser)
- Ingress is the only entrypoint in your cluster, it forwards traffic to service

1. Cluster IP type 

- internal service 
- pods are identified via selector 
- all the labels should be matched 
- when service is created, enpoints object is also created (keep track of which pods are enpoints of the service)
- when you have multiple ports open in a service, you have to name the ports in the yaml

2. Headless service type

- use case: statefull apps, where one pods needs to communicate directly with another specific pod
- setting `clusterIP: None` in the service configuration -> will return the IPs of the Pods, not the IP of the service

3. NodePort service type

- service can be of 3 types: `type: ClusterIP`, `type: NodePort` and `type: LoadBalancer`. ClusterIP is by default if not specified in the config.
- NodePort creates a static port on each Node in the cluster. That makes external traffic open from outside on every Node (range: 30000-32767)
- ClusterIP service is atomatically created

4. LoadBalancer service type

- service becomes accesible externaly through a cloud platform loadbalancer
- NodePort and ClusterIP service is created automatically

**ConfigMap**

- stores non-confidential data in key-value pairs
- external configuration for your application 
- it is a local volume type which can store individual key-value pairs which are passed as env variables to the app/pods or you can store a file which can be mounted inside the container (use case: config file used by the app)

**Secrets**

- same as ConfigMap, but used for sesitive data
- base64 encoded
- Secrets and ConfigMaps can be used inside the application as env variables or mounted as a properties file

**Volumes**

- used to persist data if a pod dies (could be local or outside of k8s cluster)
- volumes are mounted to every pod & when a pod dies, data is persisted in a volume

**Deployment**

- abstraction over pods
- it does not depened on previous data (also called stateless)

**StatefulSet**

- blueprint for stateful app (ex. database)
- it makes sure that data reads and writes are synchronized to avoid data inconsistencies
- it maintains a sticky identity for each of their pods
- pods are not interchangeable
- pods can't be created/deleted at the same time
- name of the pod in composed of $(statefulset name)-$(oridnal)

Scaling DB apps:
- only 1 replica can make changes
- each replica has it's own storage and those are constantly synchronized

Deploying StatefulSets are not easy, so a simpler solution would be to host all the stateless applications inside the k8s cluster and have separate DBs outside of k8s cluster.

**Namespace**

- used to organize resources inside a "virtual cluster"
- kube-system - master processes 
- kube-public - public info about the cluster
- kube-node-lease - heartbeat of nodes - determine the availability of nodes
- defult namespace - where you create resources by default
- specify namespace key in metadata of any resource you create
- each NS must define own ConfigMap, Secret
- service can be accessed on another NS
- not namespaced components: volume and node 

Use cases: 

- Resources grouped in ns. For ex: Database ns, Monitoring ns, Elastic stack ns, Nginx-ingress ns
- Conflicts:  many teams, same application name -> using only one namespace, one team will override components from the other team. 
- Resource sharing: dev and staging ns -> both will use resources from nginx-ingress controller ns nad Elastic Stack ns. 
- Blue/ green deployment 
- Access and resource limits on namespaces - each team has own isolated environment and limits on each namespace in terms of CPU and Memory.

You can use `kubens` to change the active namespace, and not use -n with every kubectl command.

**Ingress component**

- used to forward external traffic to the k8s cluster componenets, internal services.
- Ingress component just defines the rules of redirection and Ingress Controller (pod) evaluates those rules and makes the actual forwardin.
- Ingress controller is the entrypoint to the cluster. Many 3rd party implementations, for example: k8s nginx ingress controller
- each Ingress object configures one domain (or 1 domain and multiple subdomains of that domain). If you want 2 domains, you need 2 ingress objects. 
- to configure https, you need a Secret containing a tls certificate


---
