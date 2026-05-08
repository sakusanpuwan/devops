# What Does Azure Offer?
Azure is a continually expanding set of cloud services to help meet business challenges. It provides a range of services, including those for computing, analytics, storage, and networking. Users can pick and choose from these services to develop and scale new applications or run existing applications in the public cloud.

- Build on a trusted platform.
- Efficiently manage your infrastructure across an integrated platform.
- Rely on a trusted and secure platform.

![Azure Services](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/azure-service-categories.png)

## The Azure Free Account Includes:

- Free access to popular Azure products for 12 months.
- A credit to use for the first 30 days.
- Access to more than 25 products that are always free.

## The Azure Free Student Account Offer Includes:

- Free access to certain Azure services for 12 months.
- A credit to use in the first 12 months.
- Free access to certain software developer tools.

## Microsoft Learn Sandbox

A temporary subscription added to your Azure account. Allows you to create and test Azure resources during learning at no cost.

## Core Architectural Components

### Physical Infrastructure


#### Data Centers
Servers arranged in racks with dedicated power, cooling, and networking infrastructure. Global infrastructure - Azure is a global cloud provider with centers around the world. Data centers are grouped into Azure Regions or Azure Availability Zones that are designed to increase resilience and reliability through proximity-based services.

![Azure Regions](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/azure-infrastructure-hierarchy.png)

#### Azure Regions

A geographical area that contains at least one, potentially multiple, datacenter that is deployed within a latency-defined perimeter connected through a low-latency (high speed) network. Azure assigns and controls resources within each region to ensure workloads are managed and balanced. Factors to consider when choosing a region include location, features, and price.

- **Region Pair**: Two closely linked regions for redundancy. Azure region is paired within the same geography/continent at least 300 miles away. Allows replication of resources across geography that reduces the likelihood of failure due to natural disasters or civil unrest that affect an entire region.
    - In the event of an extensive Azure outage, one region can be prioritized to make sure one is restored.
    - In the events of Azure updates, changes can be rolled out to one region in the pair to minimize downtime and risk of app outage.
    - Data within the same geography is in line with governance (tax).
    - **Sovereign Region**: Instances of Azure that are isolated from the main instance of Azure to ensure government compliance within specific jurisdictions. You may need to use a sovereign region to meet higher compliance or legal purposes (e.g., U.S. government agencies and partners, China). This is not part of Azure public cloud and needs approval to join with limited services available.

#### Azure Availability Zones

Physically separate datacenters within an Azure region. Each zone is made up of one or more datacenters equipped with independent power, cooling, and networking. If one zone goes down, others continue to work. Zones are connected through high-speed private fiber-optic networks.

- To ensure resiliency, a minimum of three separate availability zones are present in all availability zone-enabled regions. However, not all Azure Regions currently support availability zones.
- When hosting an app, availability zones can be used to co-locate/co-host your computing, storage, network, and database needs.
- Increased costs to duplicate services between zones.
- Used for VMs, load balancers, SQL databases.
- **Zonal Services**: You pin the resource to a specific zone (e.g., VMs, managed disks, IP addresses).
- **Zone-Redundant Services**: The platform replicates automatically across zones (e.g., zone-redundant storage, SQL Database).
- **Non-Regional Services**: Services are always available from Azure geographies and are resilient to zone-wide outages as well as region-wide outages.

### Management Infrastructure

Includes Azure resources, subscriptions, and accounts.
![Azure Hierarchy](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/_images/govern/large-enterprise-resource-organization.png)

![Azure Management Hierarchy](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/account-scope-levels.png)
#### Management Group

Centralized subscription management (optional). Can assign role based access control (RBAC) (who), policies/rules (what) and budget (how much). Child nodes, such as subscriptions and resource groups can inherit RBAC, policies, and budget from the parent management group.

#### Subscription

High-level billing and access control boundary.

#### Resource Group

Groups of resources with the common lifecycle/access needs. Resources that are created, used and deleted together can be coupled into a resource group. 

#### Resource

Everything you create in Azure.

- **Resource**: Basic building block of Azure. Anything you create, provision, or deploy is a resource. VMs, virtual networks, databases are usually assigned to a region with every resource having a name and cost.
- **Resource Group**: A resource is required to be placed into a resource group. A resource belongs only to one resource group, can be moved to a different group, and cannot be nested. Actions applied to a resource group apply to all resources within the group. Deleting a group deletes all resources. Grant access at the resource group level to all resources. Recommended to be grouped by access control or lifecycle needs.
- **Subscription**: A unit of management, billing, and scale. All resources/resource groups belong in a subscription. Allows you to organize resource groups and billing. Grants authenticated access to Azure products and services and defines boundaries around access/usage.
    - **Subscription Boundary**:
        - **Billing Boundary**: Determines how an Azure account is billed for usage. Can organize and manage costs by generating separate billing reports for multiple subscriptions.
        - **Access Control**: Applies access management policies at the subscription level and can create separate subscriptions at different hierarchy/organization structures to track costs.
        - Additional subscriptions to separate:
            - **Environments**: Dev/test/prod + isolate data.
            - **Organizational Structure**: Limit one to a small team but more to the whole IT department. Manage control according to demand/needs.
            - **Billing**: Separate billings for dev/test and prod as easier to track costs.
- **Management Groups**: Give you enterprise-grade level management to unify access, policies, and compliance for subscriptions across the organization.
    - 10,000 management groups can be supported in a single directory.
    - Policies applied at the management level apply to all child objects.
    - A management group tree can support up to six levels of depth. This limit doesn't include the root level or the subscription level.
    - Each management group and subscription can support only one parent.

### Azure Compute

An on-demand computing service that provides computing resources such as disks, processors, memory, networking, and operating systems. Simply put, it’s the engine running your code/application on Azure.

#### VMs (IaaS)

A customizable, scalable, and on-demand virtualized server without physical hardware.

- Control OS.
- Run customer software.
- Use custom hosting configurations.
- Hosted on an underlying hypervisor.

**Pros**:

- Greater control of all aspects of an environment or machine.
- Application compatibility - better legacy support.
- Can lift and shift existing infrastructure to Azure from on-premises or another cloud provider.
- Quicker testing of applications.
- Extend datacenter - extend on-premises servers with Azure.
- Can create or use predefined images to provide VMs. An image is a template used to create a VM and may include OS, etc., useful in scale sets.
- **Scaling**: Group VMs together to provide high availability, scalability, and redundancy.
    - **VM Scale Sets**: Lets you create and manage a group of identical, load-balanced VMs. Scale sets can centrally manage, configure, and update several VMs together. The number of VMs can auto-scale up/down in response to demand or based on a defined schedule. Manage load balancer to make sure resources are being used efficiently by directing traffic.
    - **VM Availability Set**: Lets you increase availability for static VMs in a single datacenter/zone by helping to build a more resilient, highly available environment. Ensure that VM updates are staggered and have varied power and network connectivity preventing mass VM loss. They achieve this through:
        - Non-identical VMs without auto-scaling in a single datacenter.
        - Spreading across different **Update Domains**: Groups VMs on hypervisors that can be rebooted at the same time. Allows you to apply updates knowing only one update domain group will be offline. All machines within the update domain group will be updated.
        - Spreading across different **Fault Domains**: Groups VMs on hypervisors by common power source and network meaning single fault domain. Helps protect against physical power or networking failure by having VMs in different fault domain groups.

**Cons**:

- More management overhead.
- OS updates, patches, software/database configurations.
- Higher costs compared to cloud-native applications.
- Scaling can be complex, especially if it's a manual process.

**Examples**:

- During testing/dev: VMs are a quick and easy way to create different OS and application configurations. Delete VMs when not needed.
- Running apps in Cloud: Pay as you go.
- Extending datacenter to cloud: Extend capabilities of physical servers by creating a virtual network and adding VMs to that network, making it easier/cheaper to deploy in Cloud than local servers.
- Disaster recovery: If the primary datacenter fails, you can recreate temp VMs then shut down when recovered and not needed.

**Configurations**:

- **Size**: Purpose, number of processor cores, and amount of RAM out of preconfigured combos, priced by usage (per min). If stopped, no charge.
- **Storage Disks**: Hard disk drives, solid-state drives, etc., charged independent of usage.
- **Networking**: Virtual network, public IP address, and port configuration. Dynamic address (no charge), static (charged regardless of VM state).
- **OS**: License costs.

**Components**:

- CPU/Memory.
- Disk.
- Networking.
- OS.
- Network control - firewall.

# Azure Virtual Desktop

Azure Virtual Desktop is a desktop and application virtualization service that runs on the cloud, Virtual Desktop Interface (VDI) powered by IaaS. It allows you to use a cloud-hosted version of Windows. Data and apps are separated from local hardware, minimizing the risk of data leaks. The actual desktop and apps are running in the Cloud, accessible from any device. It allows multiple concurrent users on a single VM, meaning apps, updates, and settings can be centrally managed.

**Example**:
- Remote work enabled via Windows desktops from anywhere, removing the need for company hardware.
- Secure, controlled access to sensitive patient data.

# App Services

Fully managed application hosting with minimal management overhead for web apps, webJobs, APIs, and mobile apps.

# Azure Functions

Serverless event-driven code execution, an extreme PaaS with no management overhead. No VMs to manage and only runs when triggered. Event-driven serverless compute option that doesn't require maintaining virtual machines or containers. For VMs and containers, you need those resources to be running. With Azure Functions, an event wakes the function, eliminating the need to keep the resources awake when there are no events.

**Use Case**:
When you need to perform work in response to an event such as a REST request, timer, or message. Only concerned with the code running service than the underlying platform or infrastructure. Functions scale automatically based on demand and automatically deallocate resources when the function is finished, so you are only charged when the CPU is on.


# Logic App

Serverless low/no code visual workflow automation service that allows you to automate business processes and integrate apps, data, services, and systems.

# Containers  

Virtual machine virtualises hardware. Container virtualises software. Containers are lightweight, scalable, and dynamic, increasing portability and efficiency. Containers can run multiple instances on a single host machine. No need to manage the OS, reducing overhead.

- Bundle an app and its dependencies, deploying to a virtualization environment.
- VMs are virtualized hardware; Containers are virtualized OS.
- VMs are limited to a single operating system per virtual machine. Containers can run multiple instances on a single host machine.
- No need to manage the OS, reducing overhead.
- Lightweight, scalable, and dynamic, increasing portability and efficiency.

## Azure Container Instances (ACI)

The fastest way to run a container in Azure without managing VMs. It is a PaaS that allows you to upload your containers, and the service will run the container. Minimum overhead required. Not scalable as single containers only without load balancing/auto-scaling.

## Azure Container Apps

A PaaS similar to container instances but more elastic as it can also add load balancing and scaling. Ideal for serverless microservices with auto-scaling, with high management but less customization than Kubernetes.

## Azure Kubernetes Service (AKS)

A container orchestration service that manages the lifecycle of containers. When a fleet of large-scale, high-volume, high-complexity containers is deployed as a cluster, AKS can manage with more control and customization. Allows auto-scaling, load balancing, and fail-safes. It is between IaaS and PaaS.

**Example**:
Containers can be used to create solutions using a microservice architecture. Break into smaller, independent pieces (e.g., website into backend, front, and storage), making it easier to maintain, scale, and update independently.

# Application Hosting

Azure App Service is an HTTP-based service that can be used to host opposed to VMs or containers.

**Enables build and host of**:
- Web apps
- Background jobs
- Back-ends
- RESTful APIs

**Offers**:
- Auto-scaling to handle higher loads.
- High availability with load-balancing and traffic manager.
- Enables integrated auto-deployment and management from GitHub, Azure DevOps.
- Secured endpoints.

# Virtual Network (VNet)

- Private, isolated network in Azure which is the home for all VMs.
- VM isolation/communication boundary.
- Can enable private/public networking.
- Easy to scale up - adding more VNets or addresses to one.
- High availability - peering VNets, load balancer, VPN gateway.
- Isolation - Manage and organize resources with subnets and network security groups.
- Can have one or more address spaces (VNet's overall IP range). Each address space contains one or more subnets (segmented, smaller IP ranges within the address space).

## Subnet

- **Resource Grouping**: Group resources into the same subnet to make it easier to control.
- **Address Allocation**: Efficient to allocate addresses to resources on smaller subnets.
- **Subnet Security**: Use network security groups to secure individual subnets.

**Regions**: A VNet belongs to a single region where each resource must be in the same region too.
**Subscription**: A VNet belongs to a single subscription, but a subscription can have multiple VNets.

## IP Address

Unique identifier for network devices.
- **Private**: Local network identifier which is invisible to the outside world.
- **Public**: Global network identifier which is accessible to the outside world.
- **Static**: Public IP which remains upon VM reallocation.
- **Dynamic**: Public IP changes upon VM reallocation.

## Network Security Groups

Primary traffic filter applied to subnets/VMs. Can apply granular rules for fine network traffic flow  control.
- Inbound/Outbound filters.
- Traffic types (TCP, UDP ports, ICMP).
- Allowed sources/destinations.

## Azure Firewall

Centralized traffic control for multiple VNets. More advanced than network security groups as it can apply rules to network as well as apps.
- Threat intelligence.
- Advanced filtering rules.
- URL filtering.
- DNS proxy.

## Azure Bastion

Secured SSH/RDP access to connect to private VMs with no public IP. Fully managed service deployed to VNet in a specific subnet.

## Network Peering

Connect multiple VNets to act as a single network, extending private networking across Azure regions, subscriptions with all traffic staying secure on Microsoft's private backbone.

**Benefits**:
- Speed - low latency.
- Privacy - traffic not exposed to the public.
- Control traffic between VNets with network security groups.

## Azure DNS (Domain Name System)

Translates domain names to IP addresses. Connection request is resolved by DNS host/server.

## Hybrid Networking

Connect trusted external networks over private IP networking.

### Site-to-Site (S2S) VPN

Encrypted network-to-network connection over the public internet. Has a local network gateway that acts as remote network configuration. Components: Virtual network gateway, gateway subnet, local network gateway.

### Point-to-Site (P2S) VPN

Encrypted network-to-device connection over the public internet. For remote work who need private network access to VNet.

### Policy-Based VPN Type

- Backwards compatible.
- Static routing.
- No point-to-site VPN.
- Connect to a single site.

### Route-Based VPN Type

- Not as backwards compatible.
- Dynamic routing.
- Supports point-to-site.
- Connect to multiple sites.

## Virtual Network Gateway

Core component of all Azure hybrid connectivity solutions.
- VNet gateway + VPN = VPN gateway.
- Managed Azure resource hosted in VNet as a dedicated subnet with a specific name, one network gateway per VNet.
- Acts as the endpoint connecting VNet and hybrid connection.
- **Active-Standby**: Default config = 1 VM running 1 tunnel, so if one fails, there will be a delay till another takes over.
- **Active-Active**: 2 active tunnels, maximum high availability.

## Peering

Used to connect VNets.
- No encryption between networks.
- Traffic stays on Microsoft.
- Low latency.
- Maximum bandwidth between networks.
- Less expensive, less to manage.

## VPN

- Provides encryption between networks.
- Involves public internet.
- Network gateway manages traffic.
- Bandwidth limited.
- Ideal for security.
- Network gateway = additional costs.

## ExpressRoute Gateway

Direct, private fast connection to Microsoft services (Azure).
- Not over the public internet / on-premises connections only.
- Can privately connect to VNets and Microsoft Cloud services.

**Benefits**:
- Reliable + fast with built-in redundancy (active-active).
- High-speed options available.
- More permanent.

**Cons**:
- More expensive.

Has the same virtual network gateway as VPN.
- With the same subnet naming requirement.
- Named as ExpressRoute Gateway rather than VPN gateway.
- Gateway connects to ExpressRoute circuit = Azure resource connecting to private connection.

## Public Endpoints

Publicly reachable PaaS services.
- Virtual network hits PaaS endpoint over the public internet.
- Also exposed to the public, but they cannot access without auth.
- Still a risk with sensitive resources.

## Private Endpoints

A managed network interface that sits inside VNet subnet provides private access to a specific instance of a service. Completely disable public access to connected services.

# Azure Storage - Data Services

## Storage Account

Management layer for Azure Storage services where performance, security, and access can be configured.

## Storage Services

- **Azure Blobs** (Binary Large Object = any file) - can store unstructured massive amounts of data in containers. Has a web address.
    - **Blob Types**:
        - **Block**: Stores text and binary data up to 4TB. Made up of individually managed blocks of data.
        - **Append**: Block blobs that are optimized for append operations. When data is constantly appended like logs.
        - **Page**: Stores files up to 8TB. Any part of the file can be accessed at any time. Like a virtual hard drive.

- **Disks** - VM disks are backed by Azure storage.
- **Disks** - VM disks are backed by Azure storage.
    - **Types**:
        - **HDD (Hard Drive Disks)**: Mechanical spinning disks, low cost and suitable for backups.
        - **SDD (Solid State Drives)**: Standard for production. High reliability, scalability, and lower latency over HDD.
        - **Premium SSD/v2**: Super fast and higher performance. Very low latency and used for critical workloads.
        - **Ultra Disk**: For the most demanding, data-intensive workloads.

- **Azure Files** - Fully managed cloud-based file share/server solution to replace/supplement on-premises file storage solution.
    - Replace/Sync file servers by maintaining application compatibility.
    - No need for hardware or operating system.
    - Use file server management tools.
    - Replicate across zones/regions.

- **Tables** - NoSQL database for structured, unstructured, semi-structured, scalable non-relational data.

- **Queues** - Message (small amount of data sent to/from application) storage for asynchronous task processing (can allow backlog of messages to be processed later).

- **Storage Redundancy** - If one copy of data is inaccessible due to hardware failure, zone/region outage, data is still available. Azure storage creates multiple copies automatically with a minimum of 3 copies invisible to the end user.
    - Redundancy options vary by cost and availability: single zone, multiple zones in a single region, across regions
      - Locally Redundant Storage (LRS): 3 copies in a single datacenter.
      - Zone-Redundant Storage (ZRS): 3 copies across multiple datacenters in a single region.
      - Geo-Redundant Storage (GRS): 6 copies across multiple datacenters in two regions. 3 in region and 3 in paired region.
      - Geo-Zone-Redundant Storage (GZRS): 6 copies across multiple datacenters in two regions. 3 across region and 3 in paired region with zone redundancy.

## Data Migration

Different solutions based on transfer frequency, data size, network bandwidth:
- **AzCopy** - Command-line utility, useful for automated scripting data transfers.
- **Storage Explorer** - A GUI with drag and drop operations.
- **Azure File Sync** - Sync files with on-premises file servers.

## Azure Key Vault

Contain secrets, keys, and certificates. Securely store and manage sensitive information by using RBACs and policies.

## Database

Azure SQL DB (Paas)  
Azure SQL MI (Managed Instance)  
PostgreSQL
MySQL 

## Azure IoT (Internet of Things) Hub
Register devices to enable IoT solutions via SDKs to read and manipulate data. 

## Azure IoT Central
Provides dashboard of simulated devices to monitor and manage IoT devices.

## Azure Sphere
Secure, connected microcontroller unit (MCU) devices. Runs the Azure Sphere OS, a custom Linux-based OS.

## Azure Data Lake
Store and analyze large amounts of data, even in raw format.

## Azure Data Factory
ETL (Extract, Transform, Load) service to move and orchestrate data between sources and destinations. E.g. Storm, Spark, Hadoop, Kafka.

## Azure Synapse Analytics
Data warehousing service to analyze large amounts of data. 

# Azure AI Services
Azure Machine Learning - Build, train, and deploy machine learning models.  
Azure Cognitive Services - Pre-built AI models for vision, speech, language, and decision-making.
Azure Bot Services - Build, test, and deploy intelligent bots that interact with humans.

# Azure DevOps 
Azure DevOps - Plan, build, test, and deploy applications.
- Repos - Store code in Git repositories.
- Boards - Track work with Kanban boards, backlogs, team dashboards, and custom reporting.
- Pipelines CI/CD - Automate build and deployment.
- Artifacts - Store packages
- Test plans - Test and track bugs.

Github - Code hosting platform for version control and collaboration.
- Repos - Store code in Git repositories.
- Actions CI/CD - Automate workflows.
- Projects - Manage work with Kanba n boards, backlogs, team dashboards, and custom reporting. 
