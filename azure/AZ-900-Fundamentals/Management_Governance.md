# Management & Governance

Financial tools available to anyone with access to billing account, subscription, resource group. Effective cost management ensures optimal utilization of resources and financial efficiency.

The process involved in planning, evaluating, and controlling the budget of a project and how Azure resources are used and billed.

Unmonitored cloud expenses can lead to unplanned significant costs. Cost management can help:

- Predict monthly bills
- Use resources efficiently
- Reduce waste
- Improve financial forecasting and planning

## Azure CMB (Cost Management & Billing)

Allows viewing, analyzing, monitoring, optimizing costs:
- **Cost Analysis**: Breaks down costs to understand spending patterns.
- **Budgets**: Set spending limits and monitor expenditures.
- **Cost Alerts**: Be notified when spending exceeds limit.

## Azure Advisor

Provides personalized best practices to reduce costs for free:
- Continuously analyzes deployed services and usage patterns to provide recommendations.
- Offers personalized suggestions and actionable steps to reduce cost (kill idle resources) and implement new efficiencies.
- Analyzes resource configurations in 4 areas:
    - Cost
    - Security
    - Reliability
    - Performance

## Azure Budgets

Sets budgets and creates alerts to monitor spending:
- Proactive approach by setting spending limits.
- Set alert criteria (>70% of limit), notification channels (email), automated actions (shutdown VM).

## Subscription Offers

- **PAYG**: Just pay for what you use without upfront costs.
- **Enterprise Agreement**: Commit to a certain level of usage in exchange for discounted rates.
- **Azure Dev/Test**: Discounted rates for development and testing environments excluding production.
- **Free Account**: Includes a limited number of free services to a threshold.

## Subscription Pricing Models

- **Reserved Instances**: Discounts offered by committing to certain services.
- **Spot Pricing**: Use spare capacity at discounted rates.
- **Hybrid Use**: On-premises Windows Server licenses can offer savings when migrating to Azure.

## Cost Factors

- **VMs**: Billed on compute power, memory, storage, time.
- **Storage**: Based on type and redundancy.
- **Data Transfers**: Inbound data is free but outbound costs.
- **Databases**: Billed based on transactions/dedicated resources.
- **Location**: Local regulations, energy costs, demand within region.
- **Service Tiers**: VMs (HDD, SDD), Storage accounts (Premium, Hot, Cold), Databases (Single, Elastic) tier selected is balance between costs and functionality.
- **On-Premise Benefits**: Azure Hybrid Benefit allows leveraging existing on-prem licenses with add-ons having separate costs.

## Azure Pricing Calculator

- **Input**: Type & scale of deployment requirements, flexible requirements (tiers, instance), hard requirements (regions, data transfer needs).
- **Output**: Cost breakdown, monthly cost estimate, other costs (add-ons, support, licensing).

## Financial Forecasting Benefits

- Export results to formats integrated into financial tools.
- Adjust parameters to see changes in costs.
- Use estimates in larger cost management strategy.
- Budget costs and continually monitor.

## Tips for Better Forecasting

- Regularly update usage patterns.
- Factor in growth.
- Use Azure pricing examples.
- Stay up to date with pricing changes.

## Azure Total Cost of Ownership (TCO) Calculator

Tool to help businesses determine the cost benefits of migrating to Azure by comparing the cost of on-premises infrastructure with Azure services. Considers direct and indirect costs (labor, utilities, and licensing). Don't overlook incomplete inventory, ancillary costs, growth, and licensing.

## Tags

Organize resources for effective cost management by purpose, owner, environment. Name/value pairs applied to Azure resources. Can be filtered in cost analysis.

## Azure Budgets & Reservations

Effective cost management ensures optimal utilization of resources and financial efficiency. Budgets and reservations are two key ways to mitigate cost sprawl and provide cost efficiency by proactively setting budgets at various levels (subscription, resource group).

- **Azure Reservations**: Committing to Azure for savings by prepaying for multiple years of Azure resources saving money compared to pay-as-you-go pricing. Can be applied to VMs, databases.

## To Maximize Return on Azure Investments

- Monitor reservation with Azure Cost Management.
- Modify reservations based on evolving needs.
- Review and adjust based on newly discovered usage patterns.

## Tags

- **Granular Categorization**: Detailed labeling of resources enabling precise categorized tracking and reporting.
- **Consistent Framework**: Ensures coherent and accurate cost reports.
- **Extensive Flexibility**: In leveraging tags.

## Advisory

- **Real-Time Recommendations**: For cost savings.
- **Holistic View**: Provides insights into security, reliability, and performance.
- **Tailored Advice**: To organizations' usage patterns and configurations.