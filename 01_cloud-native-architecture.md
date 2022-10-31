# Cloud Native Architecture - 16%
This part of the repository demonstrate the cloud-native architecture and core components, which covers 16% of the KCNA exam.

---

## Chapter outcomes
At the end of this page you should be able to describe and answer following questions:
- How CNCF defines the cloud-native terms and what're it's the core characteristics.
- Describe Monolith vs. Microservices architecture approaches with examples, as well as the benefits and drawbacks of both approaches.
- Describe different Autoscaling options in cloud-native environments.
- Describe the concept of Serverless Computing, as well as it'd benefits.
- Community and Governance 
- Which Roles and Personas are existing within cloud-native environments and what're thier tasks?
- Which Open Standards are available in cloud-native world and for what it's used.

---

### 1. What's Cloud Native?
CNCF defines the term of Cloud Native as follow:

_“Cloud native technologies empower organizations to build and run scalable applications in modern, dynamic environments such as public, private, and hybrid clouds.
**Containers, service meshes, microservices, immutable infrastructure, and declarative APIs** exemplify this approach._
_These techniques enable loosely coupled systems that are resilient, manageable, and observable. Combined with robust automation, they allow engineers to make high-impact changes frequently and predictably with minimal toil. [...]”_ - CNCF

---

### 2. Describe Monolithic vs. Microservices architecture approaches as well as thier benefits and drawbacks.
- **Monolithic:**
Monolithic approch based applications designed as a self-contained application and include all the functionality and components as single system, e.g. an e-commerce application which includes an online shop, GUI, products, shopping cart, order process, etc.
    - **Benefits:**
        -  Is good for scenarios, application has different modules that are completely dependent on each other from a transactional context.
        - Makes sense for simple, lightweight applications.
    - **Drawbacks:**
        - Difficult to manage complexity.
        - Reliability, because all modules are running within the same process, a bug in any module, such as a memory leak, can potentially bring down the entire process.
        - Scale development across multiple teams.
        - You can't implement changes fast, fixing bugs, and can't have continuous deployment.
        - Extremely difficult to adopt new frameworks.
        - Be able to scale out the application efficiently when it comes under a lot of load.

- **Microservices:**
An architectural approach for designing an app as a collection of small services; each service implements business logic or functionalities, runs in its own process, and communicates via HTTP APIs or messaging.
    - **Benefits:**
        - Much faster to develop, and much easier to understand and maintain.
        - Can be deployed, upgraded, scaled, and restarted independent of other services in the same application.
        - Enabling frequent updates and continuous deployment.
        - Free to choose whatever technologies make sense.
        - Better choice for complex, evolving applications.
    - **Drawbacks:**
        - Can be very complex to integrate.
        - Partitioned database architecture.
        - Testing much more complex, e.g. with a modern framework such as Spring Boot it is trivial to write a test class that starts up a monolithic web application and tests its REST API. In contrast, a similar test class for a service would need to launch that service and any services that it depends upon.
        - Implementing changes that span multiple services, but happens rarely.
        - Successfully deploying a microservices application requires greater control of deployment methods, and a high level of automation.

---

### What're Cloud Native characteristics?
- **High level Automation:**
    - In every step from development to deployment (CI/CD, IaC, etc.)
    - Minimal human involvement
    - **Benefits:** Fast and frequent incremental changes to production, easier disaster recovery, etc.
- **Self healing:**
    - Health check, monitoring, automatically restart, etc.
    - **Benefits:** if one Microservice fails, only this parts of the app stops working and going to be fixed and not all the application like Monolithic approach-based apps.
- **Scalable:**
    - Automatically scaling the underlined resources of the application based on CPU, memory, etc
    - **Benefits:** Ensures availability, better performance, etc.
- **(Cost-) Efficient:**
    - Scale up/down based on the application traffic.
    - **Benefits:** efficient usage of infrastructure resources.
- **Easy to maintain:**
    - Using Microservices allows to break down applications in smaller pieces.
    - **Benefits:** more portable, easier to test and to distribute across multiple teams.
- **Secure by default:**
    - Cloud environments are used by many customers and cloud providers secures the data centers at rest
    - **Benefits:** the customer don't have to cover all physical securities.

---

### Describe the twelve-factor app.
The twelve-factor is a developement methodology for building cloud-native applications that ...
- use declarative formats,
- that offer maximum portability,
- are suitable for deployment on cloud platforms,
- minimize divergence between development and production,
- enabling continious deployments for maximum agility,
- allow easy scaling of applications without significant changes to tooling, architecture, or development practices.
For more details about twelve-factor app: [The Twelve-Factor App](https://12factor.net/)

---

### Describe Autoscaling pattern with an example.
Autoscaling describes the dynamic adjustment of resources based on the current demand. Typically CPU and memory are the metrics, but time and business metrics can be also considered.
There're two types of autoscaling in common:
- **Vertical scaling:** Adding more CPU and memory to existing VMs.
- **Horizontal scaling:** Adding more physical or virtual machines.
- **The difference in example:**
    - Carry a heavy object that you can‘t pick up, but you can build muscle and then —> *Vertical*
    - Carry together with friends —> *Horizontal*

**Note:** You will learn about Autoscaling in much more details in [03.1_kubernernetes-objects.md](/Users/mustafaemal/Documents/repos/kcna/03.1_kubernernetes-objects.md)

---

### Describe the concept of Serverless Computing.
a. Serverless Computing provides just the code of your application and the cloud provider chooses the right environments and abstracts the underlying infrastructures.
b. No upfront provisioning, no management of servers, and pay-what-you-use economics for building applications.
c. Stronger focus on on-demand provisioning and scaling of apps.
d. Bring your code as .zip or container image
Writing small, stateless applications make them a perfect fit for event or data streams, scheduled tasks, business logic or batch processing.

---

### Describe Cloud Native Open Standards.
- **Open Container Initiative (OCI) :** image, runtime and distribution specification on how to run, build, and distribute containers.
    - **Image-spec:** Defines how to build and package container images.
    - **Runtime-spec:** Specifies the configuration, execution environment and lifecycle of containers
    - **Distribution-spec:** Provides a standard for the distribution of content in general and container images in particular
- **Container Network Interface (CNI):** A specification on how to implement networking for containers.
- **Container Runtime Interface (CRI):** A specification on how to implement container runtimes in container orchestration systems.
- **Container Storage Interface (CSI):** A specification on how to implement storage in container orchestration systems.
- **Service Mesh Interface (SMI):** A specification on how to implement Service Meshes in container orchestration systems with a focus on Kubernetes.

---

### Describe the Cloud Native job roles.
- **Cloud Architect:** Adopt Cloud technologies, designing aplication landscape and infrastructures with focus on security, scalability, and deployment.
- **DevOps Engineer:** Use Tools, Processes to balance Software development and operations.
- **Security Engineer:** Cloud technologies created new attack vendors. Most significantly changed role.
- **DevSecOps:** Make security an integral part of modern environment.
- **Data Engineer:** Collecting, storing, and analyzing a big amount of data.
- **Full-Stack Engineer:** All around Frontend, Backend, and Infrastructure.
- **Site Reliability Engineer (SRE):** SRE is founded 2003 from Google and it's goal is to create and maintain Software which is reliable and scalable. To achieve this goal Software Engineering approaches used to solve operational problems and automate operation tasks.
To measure the performance and reliability of an application or the whole environment, SREs have following three main tasks:
- **Service Level Objectives (SLO):** Specify a target level for the reliability of your service. A goal that‘s set, for example reaching a service latency of less than 100ms.
- **Service Level Indicators (SLI):** A carefully defined quantitative measure of some aspect of the level of service that‘s provided, e.g. how long a request  needs to be answered.
- **Service Level Aggreements (SLA):** An explicit or implicit contract with user that incl. consequences of meeting (or missing) the SLAs the contain. The consequences are most easily recognized when they are financial - a rebate or penalty - but they can take other forms. Answer the question what happens if SLAs are not met.

**Note:** In exam there's at least one conceptual understanding question about SRE role, so therefor, you should really understand this role well!

---

## Do you want to jump more deep dive?
- [What's Cloud Native Applications? | VMware](https://tanzu.vmware.com/cloud-native)
- 