# Kubernetes Fundamentals - 46%
This part of the repository demonstrate the **Kubernetes Fundamentals** part of exam objectives, which covers 46% of the KCNA exam. First, it explains the Kubernetes Architecture and after that the Kubernetes Objects.  
For clarity this part is demonstrated in two separated files (03_kubernetes-architecture.md and [03.1_kubernetes-objects.md](./03.1_kubernetes-objects.md))

---

## Chapter outcomes
- Describe the Kubernetes Architecture and understand the task of every single components in much details and deep dive.

---

## Describe every single component of Kubernetes (K8s) Architecture in details.
![Kubernetes Architecture](./00_images/k8s-architecture.png)

A k8s cluster consists at two different server nodes to run a containerized application:  

### **Controle Plane Node**  
This the brain of operations and administration tasks. It's a collection of Linux machines (must be!) and  contains various components which manage the cluster and control various tasks like deployment, scheduling and self-healing of containerized workloads.  
These components are:
- **API Server:**
    - Primary access point as a communication hub for whole k8s cluster.
	- All the communication between the components in k8s is done through this.
    - API and this where users would access the cluster.
	- Without it, communication with the cluster is not possible.
    - API Server itself is stateless, therefore stored the state of the system in etcd.
- **etcd:**
    - A database which stores the state of the k8s objects in key-value pairs.
    - Every activitiy (e.g. assigning a container to a node, etc.) in the k8s cluster going to be stored here.
- **Schedular:**
    - Describes the process of automatically choosing the right Worker Node for newly created or unassigned Pods, but it's not responsible for actually starting the workload!
    - Bevor assigning a Pod to a node, the existing nodes must be filtered according to specific scheduling requirements. A node that meet the scheduler requirements called *feasible nodes*. If none of the nodes are suitable, the Pod remains unscheduled until the Scheduler is able to place it.
    - Scheduler selects a node for the Pod in a 2 steps operations:
        - **Filtering:** finds feasible Nodes for a Pod and then runs a set of functions to score the feasible Nodes and picks a Node with the highest score among the feasible ones. The Scheduler then notifies the API server about this decision in a process called *binding*.
        - **Scoring:** the Scheduler ranks the remaining nodes to choose the most suitable Pod placement. The scheduler assigns a score to each Node that survived filtering, basing this score on the active scoring rules.
    - Finally, the Scheduler assigns the Pod to the Node with the highest ranking. If there is more than one node with equal scores, kube-scheduler selects one of these at random.
    - Factors that need to be taken into account for scheduling decisions include individual and collective resource requirements, hardware, software, policy constraints, data locality, etc.
- **Controller Manager:**
    - It hast the responsibility of keeping things in the desired state.
    - For example, one of these control loops can make sure that a desired number of your application is available all the time.
- **Cloud Controller Manager (optional):**
    - Can be used to interact with the API of cloud providers, to create external resources like load balancers, storage or security groups.

### **Worker Node:**  
A Worker Node is a single machine (physical or VM) and it can be either Linux or Windows. It's where the containerized applications run.  
Inside a Worker Node runs Pods and inside Pods runs containerized application based on an image.  
A Workder Node has following components:
- **Pod:**
    - A Pod is the smallest compute component within k8s cluster.
    - Insider a Pod runs usually a single containerized application instance based on an image, but can contain multiple containers, e.g. including *util containers* or *logging containers*.
- **Container Runtime:**
    - Is the underlying software that runs containers on a k8s cluster.
	- It's responsible for pulling, running, starting, and stopping container images.
    - Popular runtimes are *containerd, CRI-O, Docker* (Docker is deprecated in k8s 1.20 & in k8s 1.23 will be removed!)
    - [An article about deprecation of Docker in k8s](https://kubernetes.io/blog/2020/12/02/dont-panic-kubernetes-and-docker/)
- **kubelet:**
    - A small agent that runs on every Worker Node and make sure that containers are running in a Pod.
    - Is responsible for starting up Pods on the Worker Node.
    - It monitor the API Server for changes and responsible also for Pod lifecycle.
    - The kubelet takes a set of `PodSpecs` that are provided through various mechanisms and ensures that the containers described in those `PodSpecs` are running and healthy.
    - The kubelet doesn't manage containers which were not created by k8s.
- **kube-proxy:**
    - Responsible for Pod networking and implementing Service objects (Service and Ingress) abstraction on each Worker Node.
    - It ensures that each Pod has a unique IP address.
    - It also implements rules to handle routing and load balancing of traffic by using *iptables* (default) and *IPVS*.
    - kube-proxy makes networking available for your application.

---

### An overview of Kubernetes Architecture with short description of every components.

![k8s components short description](./00_images/k8s-architecture-components.png)



