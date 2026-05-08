# Intro to Microsoft Azure Fundamentals
Microsoft Azure is a cloud computing platform with an ever-expanding set of services to help you build solutions that meet your technical goals. You can host simple web services for internet-facing apps, run fully virtualized computers for custom software solutions, or use cloud-based services like remote storage, database hosting, and centralized account management. Azure also offers capabilities in artificial intelligence (AI) and Internet of Things (IoT).

# Cloud Computing

Cloud Computing is the delivery of computing services (servers, storage, databases, networking, software, analytics, and intelligence) over the Internet/Cloud to offer faster innovation, flexible resources, and economies of scale. You normally pay only for cloud services you use (pay-as-you-go), helping you lower your operating costs, run your infrastructure more efficiently, and scale as your business needs change/grow without physical constraints. Services also include Internet of Things (IoT), Machine Learning (ML), and Artificial Intelligence (AI).

Cloud computing changes infrastructure planning from long procurement cycles to on-demand provisioning. Teams can test faster, recover faster, and adapt capacity as requirements change.

## Shared Responsibility Model 

Sharing of responsibilities between cloud provider and consumer where different cloud service types have different responsibilities such as efficiency, convenience, data privacy, and flexibility can be defined.

Service type (e.g., SaaS or PaaS) will determine shared responsibility.

![Shared Responsibility Model](https://learn.microsoft.com/en-us/training/wwl-azure/describe-cloud-compute/media/shared-responsibility-b3829bfe.svg)

## Cloud Models

![Cloud Models](https://learn.microsoft.com/en-us/training/wwl-azure/describe-cloud-compute/media/cloud-deployment-models.png)
### Public cloud 
A multi-tenanted environment operated by a third-party service provider in which businesses pay for provisioned services.  

| Advantages                           | Disadvantages                  |
| ------------------------------------ | ------------------------------ |
| No capital costs                     | Lack of customisation          |
| Low IT overheads                     | Governance & security concerns |
| High scalability, range of locations | Potential latency              |
| Consumption based - OpEx (PAYG expenses for services etc.)             |                                |
|                                      |                                |

### Private cloud
A single-tenanted environment over which businesses have complete control with regard to architecture and configuration.

| Advantages                | Disadvantages               |
| ------------------------- | --------------------------- |
| Highly customisable       | High capital cost           |
| Higher security           | Underutilisation = wastage |
| Higher performance        | High IT overhead            |
| Consumption based - CapEx (upfront investment in physical infrastructure etc. ) |                             |
|                           |                             |

### Hybrid cloud
A combination of both public and private clouds in an inter-connected environment. Can be used to allow a private cloud to surge for increased, temporary demand by deploying public cloud resources. Users can flexibly choose which services to run in public cloud and which to deploy to their private cloud infrastructure.

| Advantages                | Disadvantages               |
| ------------------------- | --------------------------- |
| Flexibility               | Complexity of management    |
| Cost efficiency           | Potential security concerns  |
| Scalability              | Data integration challenges |


### Multi-Cloud
Use multiple cloud providers. This is used when you need different features from different cloud providers or are migrating to a different provider.

| Advantages                | Disadvantages               |
| ------------------------- | --------------------------- |
| Avoid vendor lock-in       | Complexity of management    |
| Access to best services    | Higher costs                |
| Resilience and redundancy | Data integration challenges |

### Azure Arc

A set of technologies that helps manage your cloud environment, including non-Azure resources.

### Azure VMware Solution

Lets you run your VMware workloads in Azure with seamless integration and scalability.

## Consumption-Based Model

### Capital Expenditure (CapEx)

One-time, upfront expenditure to purchase tangible, long-term fixed resources (e.g., new building, datacenter, company car). Requires forecasting/predicting long-term use and cost-effectiveness.

### Operational Expenditure (OpEx)

Continuous ongoing service/products to help business operations (e.g., renting a center, leasing a car, cloud service subscription). No need for forecasting as it is pay-as-you-go. Cloud computing is OpEx as it is a consumption-based model.

## Benefits

- No upfront costs for hardware or datacenter infrastructure.
- No need to purchase and manage costly infrastructure that may be underutilized.
- The ability to pay and add more resources when they're needed.
- The ability to stop paying and release resources that are no longer needed.

Cloud providers use a pay-as-you-go pricing model. You typically pay only for the services you consume, which helps you:

* Plan and manage operating costs.
* Run infrastructure more efficiently.
* Scale as workload needs change.
  
The cloud provider maintains the underlying infrastructure, including power, cooling, hardware, and networking, so you can focus on solving business problems and delivering new capabilities to your users.


## Cloud Service Types

### Infrastructure as a Service (IaaS)

Pay for fixed managed computing infrastructure. Examples AWS (EC2), Azure (Virtual Machines), GCP (Compute Engine).

"Give me a computer in the cloud and I will manage it" - you rent the hardware and manage everything else.

- Most flexible category of cloud services - greater customization and control.
- Maximum amount of control over cloud resources.
- More responsibility/management on you as the customer.
- Pay for what you allocate.
- You’re essentially renting the hardware in a cloud datacenter, but what you do with that hardware is up to you.
- Managed over the internet.
- Example: multiple virtual machines hosted on a hypervisor (a single physical server that can host multiple VMs) - virtual version of a physical computer.

#### IaaS Scenarios

- **Lift-and-shift migration**: Setting up cloud resources similar to your on-prem datacenter, and then moving the things running on-prem to running on the IaaS infrastructure.
- **Testing and development**: Established configurations for development and test environments that you need to rapidly replicate. You can start up or shut down the different environments rapidly with an IaaS structure, while maintaining complete control.

### Platform as a Service (PaaS)

Platform to develop, run and deploy applications without managing the underlying physical infrastructure. Examples AWS (Elastic Beanstalk), Azure (App Service), GCP (App Engine).

"Here's my code and data, run it for me" - you manage the applications and data, but not the underlying infrastructure.

- Middle ground between renting space in a datacenter (IaaS) and paying for a complete and deployed solution (SaaS).
- Develop applications without managing infrastructure.
- Pre-packaged cloud services with limited choice over tools such as languages/frameworks.
- Pay for what you use.
- Low level of management - reduced OS, software licenses, database management.
- Less control over infrastructure.
- Example: Databases, Software Development, Web App Deployment, Storage, Analytics (e.g., GitHub, Docker, Kubernetes).

#### Serverless

An extreme version of PaaS which abstracts even further by removing even more management and configuration. Just runs code with no need to worry about where it runs, such as resource management. Better for microservice-based architecture. Example: AWS Lambda.

#### PaaS Scenarios

- **Development framework**: PaaS provides a framework that developers can build upon to develop or customize cloud-based applications. Similar to creating an Excel macro, PaaS lets developers create applications using built-in software components. Cloud features such as scalability, high-availability, and multi-tenant capability are included, reducing the amount of coding that developers must do.
- **Analytics or business intelligence**: Tools provided as a service with PaaS allow organizations to analyze and mine their data, finding insights and patterns and predicting outcomes to improve forecasting, product design decisions, investment returns, and other business decisions.

### Software as a Service (SaaS)

Cloud-based ready-to-use application/software no infrastructure or deployment management required. Examples AWS (Amazon Connect), Azure (Microsoft 365, Word), GCP (Google Workspace/ Gmail).

"Just use the software, I don't care how it works" - you just use the software and don't manage anything else.

- Hosted and accessed over the internet.
- Subscription pricing model.
- Ready-to-use applications.
- Hosting/Scaling is provided.
- Focus is on the end user.
- Minimal management overhead.
- Most complete cloud service model from a product perspective.
- Renting or using a fully developed application.
- Least flexible but easiest to get up and running.
- SaaS is powered by IaaS/PaaS services (e.g., Google Drive is hosted by GCP, Slack by AWS).

#### SaaS Scenarios

- Email and messaging.
- Business productivity applications.
- Finance and expense tracking.

## Defense in Depth

Slow or stop unauthorized data access by having multiple layered defenses. If one layer is breached, other layers can still stop attacks.

### Defense Layers

- **Physical Security**: Building/hardware access.
- **Identity and Access**: User authentication.
- **Perimeter**: Protects against network-based attacks (e.g., DDoS/Firewall protection).
- **Network**: Secure connectivity while limiting communication between apps.
- **Compute**: Secure virtual machines by updating OS.
- **Application**: Resolve application vulnerabilities and secure secrets.
- **Data**: Primary target (e.g., databases, disks, SaaS application).

## Benefits of Cloud Services

### High Availability

- Resources need to be available when needed and can add more if needed.
- Downtime is bad for critical applications for business/customers.
- Focus on ensuring maximum availability using clusters of VM paired with load balancers.
- Service level agreements (SLA) from Cloud vendors that guarantee uptime.

### Scalability

- Ability to adjust resources to meet demand.
- Scale up by adding more resources if higher traffic prevents systems from being overwhelmed.
- Consumption-based model so only pay for what you use.
- **Vertical Scaling**: Add more CPUs/RAM to the current existing VM. Manual requires downtime/reboot.
- **Horizontal Scaling**: Add more VM/containers. Usual cloud model. Load balancer distributes traffic across VMs. Automatic, no downtime.

### Reliability

- Ability of the system to recover from failure and continue to function with minimum downtime.
- No single point of failure - decentralized design across regions (e.g., if one VM / region goes down, others can pick up).
- Global scale computing - against regional failure/disaster.
- Multi-region decentralized cloud design allows automatic relocation to a different region when one fails.
- Can optimize performance based on proximity.

### Predictability

- Can predict performance or cost of the solution regardless of demand/customer location.
- **Performance**: Forecast the resources needed to deliver. Autoscaling, load balancing, high availability.
- **Cost**: Forecast the cost of cloud usage by tracking resources in real-time, monitor resources to maximize resource effectiveness. Data analytics to find patterns and trends to plan resource deployment.
- Design application around cloud-native best practices.

![Security and Governance](https://learn.microsoft.com/en-us/training/wwl-azure/describe-benefits-use-cloud-services/media/security-governance.png)

### Security

- Can choose cloud service type/solution and security control (e.g., if you want max control -> IaaS).
- Cloud vendors are well protected against DDoS attacks, keeping your network robust and secure.
- Auditing tools and automated patching.

### Governance

- Cloud features follow set templates to meet corporate standards and government regulations (e.g., encryption, location standards).
- Can update deployed resources as standards change.
- Automatic software patches and updates.

### Manageability

- **Of the cloud**: How the cloud manages your resources (e.g., autoscaling, monitoring health of resources, preconfigured template-based deployments, receive alerts).
- **In the cloud**: How you manage cloud resources (e.g., web portal, command line, APIs).

### Sustainability
- Cloud providers are committed to sustainability and have initiatives to reduce carbon footprint (e.g., renewable energy, efficient data centers).
- Scaling resources down when demand is low can reduce energy consumption and costs.
- Deactivating unused resources can save energy and costs.
- Choose efficient services and configurations to reduce overprovisioning
- Using governance and monitoring to track usage trends and optimise deployments

For example, a development environment that runs only during business hours can be automatically shut down overnight and on weekends. This practice reduces unnecessary consumption while still meeting team needs.