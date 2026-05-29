# Scaling with Google Cloud Operations
## Financial Governance and Managing Cloud Costs
### Fundamentals of Cloud Financial Governance
Having cloud financial governance is a set of processes and controls that organisations use to manage cloud spend without budget overruns. This includes establishing clear policies for cloud usage, implementing cost monitoring and reporting mechanisms, and leveraging cloud provider tools and services to optimize spending. Effective financial governance helps organisations maintain control over their cloud costs, ensuring that they stay within budget while still meeting their business objectives.

The variable nature of cloud costs impacts people, process and technology. 
- People: Refers to different roles involved in managing cloud costs. For smaller orgs, one person might fulfill multiple roles and be responsible for managing all aspects of a cloud infrastructure and finance. For larger orgs, a dedicated finance team will take on financial planning and advisory roles. Teams might struggle to understand or monitor cloud spending effectively, therefore technical members are needed to advise on how cloud resources are being used to meet org business strategy. 
- Process: Involves the workflows and procedures that govern cloud usage and spending. This includes budgeting, forecasting, and reporting processes that help organisations track and manage their cloud costs effectively. Helps orgs identify waste to quickly eliminate to ensure their cloud investment is maximised.
- Technology: GCP provides built-in tools to help orgs monitor and manage costs. These tools help orgs gain greater visibility, drive a culture of accountability, and optimize resource usage.

Best practices for cloud financial governance include:
- Define ownership: Who manages cloud costs? Should be a mix of technical and financial roles.
- Define accountability: Establish clear accountability for cloud spending at all levels of the organization. Control who can spend and view costs across org.
- Implement cost monitoring: Use GCP tools to monitor and report on cloud spending in real time. This helps orgs identify and address cost overruns quickly. Set alerts to notify stakeholders of any unexpected spending and set budget controls. An invoice is a doc sent by cloud service provider to a customer to request payment for services that were used. Cost management tools is a software to help track, analyse and optimise cloud spend. To optimize their cloud costs, orgs first need to understand what they're spending, whether there are any trends, and what their forecasted costs are. Google Cloud Pricing Calculator lets you estimate how changes to cloud usage will affect costs. Cloud billing reports is a reactive method to help you track Google Cloud resources and ways to optimise costs.

**Resource hierarchy**  
With on-prem infra, physical access controls were used but in the cloud, the resource hierarchy enables access to be managed through IAM policies and roles. This allows for more granular control over who can access specific resources, assign roles and what actions they can perform. This inheritance simplifies access management and reduces the need for manual configuration at each individual resource level. The resource hierarchy enhances security and compliance through least privilege principles.

The Google Cloud resource hierarchy is a powerful tool that can be used to organize and manage resources in a logical and efficient manner. It provides a way to group resources together and apply policies and permissions at different levels of the hierarchy. This helps organizations maintain control over their cloud resources and ensures that they are used in accordance with organizational policies and best practices.

- 1st level: Resources which are virtual machines, Cloud Storage buckets, BigQuery tables
- 2nd level: Projects which are collection of organised resources
- 3rd level: Folders which are used to group projects
- 4th level: Organizations which are used to group folders

**Policy** - a set of rules that define who can access a resource and what they can do with it. Policies can be defined at the project, folder and org node levels. 

Google Cloud offers several tools to help control cloud consumption, including resource quota policies, budget threshold rules, and Cloud Billing reports.
- Resource quota policies: set limits on the amount of resources that can be used by a project or user.
- Budget threshold rules: allow you to set spending limits and receive alerts when spending approaches those limits.
- Cloud Billing reports: provide detailed insights into your cloud spending, helping you identify trends and optimize costs. Billing data can be exported to BigQuery for further analysis. Looker Studio can be used to visualise data. Org can optimise costs through committed use discounts (CUDs). If workloads have predictable resource needs, Google Cloud commitment can be made, which gives discounted prices in exchange for your commitment to use a minimum level of resources for a specific term.

## Operational Excellence and Reliability at Scale
Developers write code for systems and applications. Operators ensure those systems and applications operate reliably. Developers are expected to be agile by writing and deploying code quickly to release new functions frequently, increase business value with new features and release fixes fast for better user experience. Operators are expected to keep system stable and work diligently to ensure reliability and consistency. 

DevOps is a software development approach that emphasizes collaboration and communication between development and operations teams to enhance the efficiency, speed, and reliability of software delivery. It aims to break down silos between these teams and foster a culture of shared responsibility, automation, and continuous improvement.

Site Reliability Engineering (SRE) is a discipline that incorporates aspects of software engineering and applies them to infrastructure and operations problems. SRE ensures the reliability, availability, and efficiency of software systems and services deployed in the cloud. SRE combines aspects of software engineering and operations to design, build, and maintain scalable and reliable infrastructure.

4 Golden Signals to measure system performance and reliability:
- Latency: the time it takes to process a request.
- Traffic: the number of requests being processed.
- Saturation: the degree to which resources are close to capacity.
- Errors: the rate of failed requests.

4 Golden Signal targets
- Service Level Indicators (SLIs): metrics that measure the performance of a service from the user's perspective. E.g. response time, error rate, percentage uptime
- Service Level Objectives (SLOs): specific targets for SLIs that define acceptable levels of service performance.
- Service Level Agreements (SLAs): formal agreements between service providers and customers that outline expected service levels and remedies for non-compliance. SLAs include the agreed-upon SLOs, performance metrics, uptime guarantees, and any penalties or remedies if the provider fails to meet those commitments. This might include refunds or credits when the service has an outage that’s longer than this agreement allows.
- Error Budgets: a defined amount of error that is acceptable within a given time period, used to balance innovation and reliability.

When infrastructure and processes in a cloud environment are designed so they need to be resilient, fault-tolerant and scalable for high availability and disaster recovery. High availability refers to the ability of a system to remain operational and accessible for users even if hardware or software failures occur. Disaster recovery refers to the process of restoring a system to a functional state after a major disruption or disaster. 

Redundancy refers to duplicating critical components or resources to provide backup alternatives. Redundancy can be implemented at various levels, such as hardware, network, or application layers. For example, having redundant power supplies, network switches, or load balancers ensures that if one fails, the redundant component takes over seamlessly.

Replication refers to creating multiple copies of data or services and distributing them across different servers or locations. It ensures redundancy and fault tolerance by allowing systems to continue functioning even if certain components or servers fail. By replicating data across multiple servers, the impact of hardware failures or outages is minimized and data availability is improved. By distributing resources across regions, businesses can ensure that if an entire region becomes unavailable due to natural disasters, network issues, or other incidents, their services can continue running from another region.

Building a scalable infrastructure allows organizations to handle varying workloads and accommodate increased demand without compromising performance or availability. Cloud technologies enable the dynamic allocation and deallocation of resources based on workload fluctuations. Autoscaling mechanisms can automatically adjust resource capacity to match demand, ensuring that services remain available and responsive during peak periods or sudden spikes in traffic.

Cloud providers often offer backup services, and they let organizations automate backups, store them securely, and easily restore data when needed. Backups should be stored in geographically separate locations to protect against regional outages or disasters.

It's important to regularly test and validate, monitor and alert on backup processes to ensure data integrity and availability.

Google Cloud Operations provides collecting, monitoring, logging, and diagnostics capabilities to help organizations gain insights into their applications and infrastructure performance, health and behavior. It enables users to collect and analyze metrics, set up alerts, and visualize performance data, making it easier to identify and resolve issues proactively.
- Cloud Monitoring provides a comprehensive view of your cloud infrastructure and applications. It collected metrics, logs and traces
- Cloud Logging allows you to store, search, analyze, and alert on log data from your applications and services.
- Cloud Trace helps you analyze the latency of your applications by providing detailed insights into request processing times and bottlenecks. Collects latency data
- Cloud Profiler helps you understand the resource consumption of your applications by providing insights into CPU and memory usage. It helps identify performance bottlenecks and optimize resource allocation.
- Error Reporting counts, analyses and aggregates the crashes in running cloud services in real-time
- Cloud Debugger enables you to inspect the state of your applications in real-time without affecting performance, making it easier to diagnose issues.

Google Cloud Customer Care: is a support service with scalable and flexible options to assist organizations in managing their cloud environments effectively. It provides access to technical support, best practices, and resources to help organizations optimize their use of Google Cloud services.
- Basic: free and included for all Google Cloud customers with Active Assist recommendations
- Standard: for workloads under development with unlimited access to tech support, which lets you troubleshoot, test and explore. Unlimited individual access to support reps 5 days a week. Also provides access to Cloud Support API, which lets you integrate Cloud Customer Care with your orgs CRM. 
- Enhanced support: for workloads in production, with fast response times and additional services. 24/7 support and quicker than standard.
- Premium support: for mission-critical workloads, with the highest level of support and dedicated resources. Includes all features of Enhanced support, plus a designated Technical Account Manager (TAM) and proactive support services.

Support case lifecycle:
- Customer initiates support via request (requires Tech Support Editor role) with issue details and priority level (P4 low impact, P1 critical)
- Enters triage process, support team reviews info to understand problem and determine severity
- Customer Care rep may resolve case if not case is assigned to support engineer
- Team starts troubleshooting and investigation process
- Escalation when flagging process breaks or for the rare occasion that a case is stuck
- After resolution, Customer Care team collaborates with the customer to validate the effectiveness of solution
- When customer confirms that the issue is resolved, support case is closed.

## Sustainability with Google Cloud
The virtual world, which includes Google Cloud’s network, is built on physical infrastructure, and those servers require huge amounts of energy, nearly 2% of the world's electricity. Google Cloud customers have environmental goals of their own, and running their workloads on Google Cloud can be a part of meeting those goals. 

Important to note that Google's data centers were the first to achieve ISO 14001 certification which is a standard that outlines a framework for an organisation to improve its environmental performance through improving resource efficiency and reducing waste.

In founding decade (2007), Google became the first major company to be carbon neutral. Since then Google also became the first company to achieve 100% renewable energy. By 2030, Google aims to run all of its data centers and campuses on 24/7 carbon-free energy.
