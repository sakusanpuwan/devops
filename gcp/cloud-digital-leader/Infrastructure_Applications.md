# Modernise Infrastructure and Applications with Google Cloud
## Modernising Infrastructure
**Workload** - a specific application, service, or capability that can be run in the Cloud or on premises, such as containers, databases and virtual machines. 

Retiring a workload means removing it from a platform (decommissioning) and is retired when it's deemed unnecessary, not cost effective, secure or compatible with a specific platform.

Retaining a workload means intentionally keeping it as currently typically on premises or in a hybrid Cloud environment. This means the workload will continue to be managed by the business and will not be subject to the same level of Cloud provider control. 

Rehosting a workload means migrating the workload to the Cloud / different hosting environment without changing anything in the workload's code or architecture. Often referred to as "lift and shift," this approach allows organizations to move applications to the Cloud while minimizing the need for extensive modifications but may involve high complexity. It also doesn't use all of the benefits offered by Cloud computing. Scaling rehosted workloads without custom changes can also be difficult, may lead to vendor lock-in. GCP offers Google Cloud VMware Engine which helps migrate existing VMware workloads to the cloud without having to rearchitect the applications. For orgs with legacy applications on Oracle, Google Cloud offers Bare Metal Solution, which is a fully managed cloud infrastructure solution that lets organisations run their Oracle workloads on dedicated, bare metal servers (a physical server / hardware dedicated to one workload with no virtualization) in the cloud. 

Replatforming a workload means migrating a workload to the Cloud / new platform while making some optimisation changes to the workloads code or architecture. Often referred to as "move and improve," this approach allows organizations to take advantage of Cloud-native features and services, improving performance, scalability, cost-effectiveness and maintainability. However replatforming can be complex and time consuming as changes to the workload's code or architecture can be difficult to test and validate.

Refactoring a workload means changing the code of the workload. An org may refactor a workload to use either a Cloud-based microservice architecture or a Cloud-based server-less architecture. Refactoring can make the workload more efficient, scalable, secure and a valuable investment for an org to maximise Cloud capabilities. However refactoring can be complex and time consuming. 

Reimagining refers to the redesigning and rebuilding project and the process of rethinking how an org uses tech to achieve its business goals. This can help orgs improve their efficiency, reduce costs and increase agility. 

### Benefits of running compute workloads in cloud
- Total Cost of Ownership (TCO): TCO is the measure of the total cost of a system or solution over its lifetime, and includes the cost of the initial purchase, maintenance and operation (non - consumption)etc. Cloud environments can reduce the total cost of ownership by eliminating the need for on-premises hardware, reducing maintenance costs, and providing flexible pricing models. Cloud providers offer pay-as-you-go pricing models as well as discounts for long term commitments which can further reduce TCO. 
- Scalability: This is the ability to increase or decrease the number of resources such as servers, storage, and bandwidth that are available to a Cloud based application to meet changing demand. 
- Reliability: Cloud provides high level of reliability and up-time, which gives business confidence that their data and applications will be available when needed. Multiple data centers in different regions ensure if one has an outage, others can take over.
- Security: Cloud offers data encryption, identity and access management, network security, virtual private Clouds and monitoring services that can detect and respond to security threats in real time. 
- Abstraction: Cloud providers remove the need for customers to understand the finer details of the underlying infrastructure of hardware, software, security and network. This allows customers to focus on building and deploying applications rather than managing infrastructure.

### Virtual Machines (VMs)
Virtualization is a form of resource optimization that lets multiple systems run on the same hardware. These systems are called virtual machines (VMs) and they run on a physical server where they share the same pool of processing, storage and networking resources. Each VM has its own operating system, applications, and resources, and can be managed independently. VMs provide flexibility and scalability, allowing businesses to quickly provision and deprovision resources as needed. However VMs can be resource intensive and may require more maintenance compared to other Cloud computing models.

Compute Engine is Google Cloud's Infrastructure as a Service (IaaS) product, that lets users create and run VM on Google infrastructure. There are no upfront investments, and many virtual CPUs can run on a system with a single physical CPU. Each VM contains the power and functionality of a full fledged operating system meaning a VM can be configured much like a physical server by choosing CPU, memory, amount and type of storage and OS etc. 

Preemptible VMs are a type of VM offered by Google Cloud that are cost-effective and ideal for batch jobs and fault-tolerant workloads. They are short-lived and can be terminated by Google Cloud at any time if the resources are needed for other tasks. However, they are significantly cheaper than regular VMs, making them an attractive option for certain use cases. Preemptible VMs can only run for a maximum of 24 hours but Spot VMs don't have a fixed max runtime.

### Containers
IaaS lets users share compute resources with other devs by using VMs to virtualise hardware. This lets each dev deploy their own OS, applications and services on the same physical server. However, VMs can be resource intensive and may require more maintenance compared to other Cloud computing models.

Containers follow the same principle as VMs. They provide an isolated environment to run software services and optimise resources from one piece of hardware. However, instead of virtualising the hardware, containers virtualise the operating system. This means that multiple containers can run on the same OS and share resources more efficiently than VMs. Containers are lightweight, portable and can be easily deployed across different environments, making them ideal for modern application development and deployment compared to booting an entire OS.

A container is packaged with all the necessary dependencies, libraries and configuration files needed to run the application. This makes it easy to deploy and run applications consistently across different environments, such as development, testing and production. Containers can be easily scaled up or down based on demand, making them ideal for applications with variable workloads.

Containers improve agility, enhance security, optimise resources and simplify managing applications in the cloud. However as IT infrastructure becomes more complex, orgs require a way to keep them secure and ensure that they operate efficiently. Container orchestration platforms like Kubernetes can help manage and automate the deployment, scaling and management of containerized applications. This improves application reliability and reduces the time and resources needed to spend on management and operations.

Google Kubernetes Engine (GKE) is a Google hosted Kubernetes service in the Cloud. The GKE environment consists of multiple machines, specifically compute engine instances grouped to form a cluster. GKE clusters can be customised, and they support different machine types, number of nodes and network settings. GKE makes it easy to deploy applications by providing an API and a web-based console for managing the cluster and its resources. Apps can be deployed in minutes and be scaled up/down.  

GKE Enterprise is a managed production ready platform for running Kubernetes applications across multiple cloud environments. GKE enterprise can run Kubernetes clusters on Google Cloud, AWS, Azure, and other public clouds. GKE Enterprise includes many features that help secure Kubernetes clusters and applications and comply with industry regulations, networking and load balancing.


Cloud Run is a fully managed serverless platform to deploy and run containerised applications without needing to worry about the underlying infrastructure. After app is containerised and deployed to Cloud Run, Google Cloud takes care of scaling and managing the infrastructure automatically. Cloud Run is ideal for running stateless applications that need to scale up/down quickly in response to traffic. 

**GKE is ideal when lots of control is required over a Kubernetes Environment and there are complex applications to run.**

**Cloud Run is ideal for when a simple, fully managed serverless platform that can scale up and down quickly is required.**

### Serverless Computing
Is a computing model where compute power is automatically provisioned in the background when needed. The advantage being orgs won't pay for compute power unless they're running a query or application. Serverless means that the business provides the code for whatever function they want and the public Cloud provider does everything else. 

**Function as a Service (FaaS)** is a serverless computing model that allows developers to run individual functions or pieces of code in response to events without having to manage the underlying infrastructure. FaaS automatically scales the execution of functions based on demand and charges only for the actual compute time consumed during execution.

**Cloud Run** is a fully managed environment for deploying and running containerized applications without the need to manage the underlying infrastructure. It automatically scales the application based on incoming traffic and only charges for the resources consumed during execution.

**Cloud Run functions** a platform for hosting simple, single-purpose functions that are attached to events emitted from your Cloud infrastructure and services.

**App Engine** a service to build and deploy web apps. Abstracts away all infrastructure management, allowing developers to focus on writing code. App Engine automatically scales applications based on traffic and only charges for the resources consumed during execution.

Serverless computing has many benefits:
- Reduced operational costs - the cloud provider manages the infrastructure, allowing organizations to focus on their applications and reduce costs associated with managing servers.
- Scalability - serverless architectures can automatically scale up or down based on demand, ensuring that applications can handle varying levels of traffic without manual intervention.
- Faster time to market - serverless computing enables organizations to quickly develop and deploy applications without worrying about the underlying infrastructure, allowing them to respond faster to changing business needs.
- Reduce development costs - serverless computing can lower development costs by eliminating the need for infrastructure management and allowing developers to focus on writing code.
- Improved resilience - serverless architectures can enhance application resilience by automatically handling failures and scaling resources as needed.
- Pay-per-use pricing - serverless computing typically follows a pay-per-use pricing model, where organizations only pay for the resources they consume during execution, leading to cost savings.

## Modernising Applications
An application is a computer, program or software that performs a specific function or set of functions for the user. With Cloud technology businesses can modernise, develop and manage applications in new ways, which makes them more agile, scalable and efficient.

Benefits of modernising applications include:
- Improved architectural design - modern cloud apps are typically built as a collection of microservices which are independently deployable and scalable, allowing for greater flexibility and resilience compared to traditional monolithic applications as they can be updated and deployed independently without affecting the entire application.
- Cost effective - typically follow pay-as-you-go pricing models, allowing businesses to only pay for the resources they consume, which can lead to cost savings compared to traditional on-premises applications that require upfront investments in hardware and software.
- Scalable - modern cloud applications can automatically scale up or down based on demand, ensuring that they can handle varying levels of traffic without manual intervention.
- Highly available and resilient - modern cloud applications have built-in redundancy and failover mechanisms that ensure they can continue to operate even in the event of hardware or software failures.
- Robust monitoring and management - cloud providers offer a range of tools and services for monitoring and managing applications, allowing businesses to quickly identify and resolve issues, optimize performance, and ensure the security of their applications.

**Microservices** - independently deployable, scalable, and maintainable components that can be used to build a wide range of applications

### API 
An API (Application Programming Interface) is a set of rules and protocols that allow different software applications to communicate and interact with each other. APIs define how requests and responses should be structured, what data can be accessed, and how different components of a system can work together. APIs are essential for modern application development as they enable developers to build applications that can easily integrate with other services and platforms, allowing for greater flexibility and functionality.

They can used to create:
- New products and services - APIs can be used to create new products and services by allowing developers to access and integrate with existing systems and data sources.
- Generate new revenue streams - APIs can be monetized by charging developers for access to the API or by using the API to drive traffic to a website or application.
- Create new partnerships - APIs can be used to create new partnerships by allowing other businesses to access and integrate with a company's systems and data.

**Apigee** - Google Cloud's API management platform to operate API's with enhanced scale, security and automation. It provides feautres like authentication, authorisation and data encryption. It tracks and analyses API usage with real time analytics and monitoring. It also helps with developing and deploying APIs through the API editor and test sandbox. It offers API versioning, documentation and API request throttling to manage and control API traffic.
