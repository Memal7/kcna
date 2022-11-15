# Cloud Native Architecture - 16%
This part of the repository demonstrates the **Cloud Native Architecture** part of exam objectives, which covers 22% of the KCNA exam.

---

## Chapter outcomes
At the end of this page you should be able to describe and answer the following questions:
- How does CNCF define the Cloud Native terms and what are its core characteristics?
- Describe Monolith vs. Microservices architecture approaches with examples, as well as the benefits and drawbacks of both approaches.
- Describe different Autoscaling options in Cloud Native environments.
- Describe the concept of Serverless Computing, as well as its benefits.
- Community and Governance 
- Which Roles and Personas are existing within Cloud Native environments and what are their tasks?
- Which Open Standards are available in Cloud Native world and what is it used for?

---

## What's Cloud Native?
CNCF defines the term Cloud Native as follows:  
*“Cloud Native technologies empower organizations to build and run scalable applications in modern, dynamic environments such as public, private, and hybrid clouds.
**Containers, service meshes, microservices, immutable infrastructure, and declarative APIs** exemplify this approach.*
*These techniques enable loosely coupled systems that are resilient, manageable, and observable. Combined with robust automation, they allow engineers to make high-impact changes frequently and predictably with minimal toil. [...]”* - ***CNCF***

---

## Describe Monolithic vs. Microservices architecture approaches as well as their benefits and drawbacks.
- **Monolithic:**
Monolithic approach-based applications are designed as self-contained applications and include all the functionality and components as a single application, e.g., an E-Commerce application that consists of an online shop, GUI, products, shopping cart, order process, etc.
    - **Benefits:**
        - Suitable for scenarios, the application has different modules entirely dependent on each other from a transactional context.
        - It makes sense for simple and lightweight applications.
    - **Drawbacks:**
        - Difficult to manage complexity.
        - Reliability because all modules are running within the same process. A bug in any module, such as a memory leak, can affect the entire process.
        - Scale development across multiple teams.
        - You can't implement changes fast, fix bugs, and have continuous deployment.
        - Extremely difficult to adopt new frameworks
        - Be able to scale out the application efficiently when it comes under a lot of load.

- **Microservices:**
An architectural approach for designing an application as a collection of small services; each service implements business logic or functionalities, runs its process, and communicates via HTTP APIs or messaging.
    - **Benefits:**
        - Much faster to develop and much easier to understand and maintain.
        - Can be deployed, upgraded, scaled, and restarted independently of other services in the same application.
        - Enabling frequent updates and continuous deployment.
        - Free to choose whatever technologies make sense.
        - The Better choice for complex and evolving applications.
    - **Drawbacks:**
        - It can be very complex to integrate.
        - Partitioned database architecture.
        - Testing is much more complex, e.g., with a modern framework such as Spring Boot, it is trivial to write a test class that starts up a monolithic web application and tests its REST API. In contrast, a similar test class for a service would need to launch that service and any services that it depends upon.
        - Implementing changes that span multiple services, but it happens rarely.
        - Successfully deploying a microservices application requires greater control of deployment methods and a high level of automation.

    ![Monolithic vs. Microservices Architecture](./00_images/monolith-vs-microservices.png)

---

## What are Cloud Native characteristics?
- **High-level Automation:**
    - In every step from development to deployment (CI/CD, IaC, etc.)
    - Minimal human involvement
    - **Benefits:** fast and frequent incremental changes to production, easier disaster recovery, etc.
- **Self-healing:**
    - Health check, monitoring, automatic restart, etc.
    - **Benefits:** if one Microservice fails, only this part of the application stops working and will be fixed.
- **Scalable:**
    - It automatically scales the underlined resources of the application based on CPU, memory, etc.
    - **Benefits:** ensures availability, better performance, etc.
- **(Cost-) Efficient:**
    - Scale up/down based on the application traffic
    - **Benefits:** efficient usage of infrastructure resources
- **Easy to maintain:**
    - Using Microservices allows us to break down applications into smaller pieces.
    - **Benefits:** more portable, easier to test, and to distribute across multiple teams
- **Secure by default:**
    - Many customers use cloud environments, and cloud providers secure the data centers at rest.
    - **Benefits:** the customer doesn't have to cover all physical securities.

---

## Describe the Twelve-Factor-App.
The Twelve-Factor-App is a development methodology for building Cloud Native applications that 
- use declarative formats
- offer maximum portability
- is suitable for deployment on cloud platforms
- minimize divergence between development and production
- enable continuous deployments for maximum agility
- allow easy scaling of applications without significant changes to tooling, architecture, or development practices  
For more details about the twelve-factor app: [The Twelve-Factor App](https://12factor.net/)

---

## Describe the Autoscaling pattern with an example.
Autoscaling describes the dynamic adjustment of resources based on the current demand. Typically CPU and memory are the metrics, but time and business metrics can also be considered.
There are two types of autoscaling in common:
- **Vertical scaling:** Adding more CPU and memory to existing VMs.
- **Horizontal scaling:** Adding more physical or virtual machines.
- **The difference in example:**
    - Carry a heavy object that you can't pick up, but you can build muscle —> *Vertical*
    - Carry together with friends —> *Horizontal*

**Note:** You will learn about Autoscaling in more detail in [03.1_kubernernetes-objects.md](/Users/mustafaemal/Documents/repos/kcna/03.1_kubernernetes-objects.md)

---

## Describe the concept of Serverless Computing.
- In Serverless Computing you provide just the code of your application and the cloud provider chooses the right environment and abstracts all the underlying infrastructures.
- There's no upfront provisioning, no management of servers, and a pay-per-use cost model for building applications.
- Stronger focus on on-demand provisioning and scaling of applications.
- Bring your code as a .zip or container image.
- Typical use cases are writing small, stateless applications making them a perfect fit for event or data streams, scheduled tasks, business logic, or batch processing.

---

## Describe Cloud Native Open Standards.
- **Open Container Initiative (OCI):** image, runtime and distribution specification on how to run, build and distribute containers.
    - **Image-spec:** defines how to build and package container images.
    - **Runtime-spec:** specifies the configuration, execution environment, and lifecycle of containers.
    - **Distribution-spec:** provides a standard for the distribution of content in general and container images in particular.
- **Container Network Interface (CNI):** a specification on how to implement networking for containers.
- **Container Runtime Interface (CRI):** a specification on how to implement container runtimes in container orchestration systems.
- **Container Storage Interface (CSI):** a specification on how to implement storage in container orchestration systems.
- **Service Mesh Interface (SMI):** a specification on how to implement Service Meshes in container orchestration systems with a focus on Kubernetes.

---

## Describe the Cloud Native job roles.
- **Cloud Architect:** adopting Cloud technologies, designing app landscapes and infrastructures with a focus on security, scalability, and deployment.
- **DevOps Engineer:** use tools and processes to balance Software development and operations.
- **Security Engineer:** cloud technologies create new attack vendors. Most significantly changed role.
- **DevSecOps:** make security an integral part of a modern environment.
- **Data Engineer:** collecting, storing, and analyzing a vast amount of data.
- **Full-Stack Engineer:** all around Frontend, Backend, and Infrastructure.
- **Site Reliability Engineer (SRE):** SRE was founded in 2003 by Google and its goal is to create and maintain reliable and scalable Software. Software Engineering approaches are used to solve operational problems and automate operational tasks.
To measure the performance and reliability of an application, SREs use three main tasks:
- **Service Level Objectives (SLO):**  specify a target level for the reliability of your service. A goal that's set, for example, reaching a service latency of less than 100ms.
- **Service Level Indicators (SLI):** a carefully defined quantitative measure of some aspect of the level of service that‘s provided, e.g., how long a request needs to be answered.
- **Service Level Agreements (SLA):** an explicit or implicit contract with the user that includes consequences of meeting (or missing) the SLAs they contain. The results are easily recognized when they are financial, a rebate, or a penalty, but they can take other forms. Answer the question what happens if SLAs are not met.(Did u mean to answer this.)

**Note:** In the exam there's at least one conceptual understanding question about the SRE role, so, therefore, you should understand this role well!

---

## Do you want to jump more deep dive?
- [What's Cloud Native Applications? | VMware](https://tanzu.vmware.com/cloud-native)

---

[Next Part ▶ 02_Container Orchestration](./02_container-orchestration.md)