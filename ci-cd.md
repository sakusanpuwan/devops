# CI/CD Deployment Guide

This guide compares three common software delivery approaches:

1. Manual Deployment
2. Automated CI/CD (Jenkins Example)
3. Cloud-Native CI/CD
4. Harness DevSecOps CI/CD Pipeline

---

| Capability              | Jenkins CI/CD     | Cloud-Native CI/CD          | Harness DevSecOps                    |
| ----------------------- | ----------------- | --------------------------- | ------------------------------------ |
| Primary focus           | Automation server | Cloud deployment automation | Intelligent DevSecOps platform       |
| Pipeline creation       | Mostly scripted   | YAML + cloud services       | Visual + YAML pipelines              |
| Infrastructure          | Self-managed      | Kubernetes / cloud-managed  | Managed or self-managed              |
| CI (Build/Test)         | ✅                 | ✅                           | ✅                                    |
| CD (Deploy)             | ✅                 | ✅                           | ✅                                    |
| Security                | Plugin-based      | External tools              | Built-in integrations and governance |
| AI assistance           | ❌                 | ❌                           | ✅                                    |
| Continuous Verification | ❌                 | Limited                     | ✅                                    |
| Automated Rollback      | Scripted          | Kubernetes/cloud features   | AI-driven                            |
| Policy Enforcement      | Plugin/script     | Cloud policies              | Native governance                    |
| Deployment Strategies   | Plugin/script     | Kubernetes-native           | Built-in                             |
| Operational complexity  | High              | Medium                      | Lower                                |

---
# 1. Manual Deployment Guide

## Overview

In a manual deployment process, developers and release engineers perform each stage of the software delivery lifecycle manually. Although this approach provides full control over deployments, it is slower, more error-prone, and requires significant human intervention.

## Deployment Flow

### 1. Development

- Developer writes code locally.
- Unit tests are executed locally.
- Changes are committed to a feature branch in Git.

---

### 2. Build and Validation

- Push the feature branch to the Git repository.
- Create or merge a Pull Request into the `main` branch.
- Build the application using Maven.

```bash
mvn clean verify
```

or

```bash
mvn clean package
```

- Run automated unit tests.
- Review build results.

---

### 3. Package Artifacts

Package the application into the required deployment artifacts:

- WAR/JAR (Java applications)
- MSI (Windows installers)
- ZIP archives

---

### 4. Deploy to Development

- Manually deploy artifacts to the Development environment.
- Perform smoke testing (e.g., basic functionality checks).
- Validate core functionality.

---

### 5. QA Testing and Bug Fixes

- QA team performs functional testing.
- Log defects.
- Developers fix issues.
- Rebuild and redeploy as necessary.

---

### 6. User Acceptance Testing (UAT)

- Promote the validated build to UAT.
- Business users perform acceptance testing.
- Obtain business sign-off.

---

### 7. Production Release Preparation

- Schedule the production release.
- Take backups of production systems and databases.
- Freeze non-essential changes.
- Confirm deployment readiness.

---

### 8. Production Deployment

- Perform the deployment manually.
- Validate:

    - Application startup
    - Service availability
    - Critical business workflows

- Mark the release as live.

---

### 9. Monitoring and Rollback

- Monitor:

    - Application logs
    - Performance
    - Errors
    - Service health

- If required:

    - Roll back to the previous stable version.
    - Investigate the issue.
    - Redeploy after fixes.

---

# 2. Automated CI/CD Pipeline (Jenkins Example)

## Overview

An automated CI/CD pipeline removes repetitive manual tasks by automatically building, testing, analysing, packaging, and deploying software after code changes. Jenkins orchestrates the pipeline while integrating with various DevOps tools.

## Pipeline Flow

### 1. Development

- Developer writes code.
- Run local unit tests.
- Commit code to a feature branch.

---

### 2. Source Control

- Push code to Git.
- Create a Pull Request.
- Merge into the `main` branch.

---

### 3. Pipeline Trigger

The Jenkins pipeline starts automatically through one of the following:

- Git Webhook (recommended)
- Poll SCM (scheduled polling)

---

### 4. Build

Jenkins checks out the latest source code and builds the application.

```bash
mvn clean verify
```

or

```bash
mvn clean package
```

---

### 5. Static Code Analysis

Automatically perform code quality checks using:

- SonarQube
- Checkstyle

Checks include:

- Code smells
- Bugs
- Security vulnerabilities
- Coding standards
- Technical debt
- Quality Gate validation

---

### 6. Automated Testing

Execute automated tests including:

- Unit Tests
- Integration Tests
- Smoke Tests (optional)

If any test fails, the pipeline stops.

---

### 7. Package Artifacts

Automatically generate deployment packages:

- WAR
- JAR
- MSI
- ZIP

Store artifacts in an artifact repository if required.

---

### 8. Deploy to Development

Automatically deploy the build to the Development environment.

Validate:

- Application startup
- Health endpoints
- Smoke tests

---

### 9. QA / UAT

- QA performs testing.
- UAT validation occurs.
- Approval gates may be used before production.

---

### 10. Deploy to Production

Following successful approval, Jenkins automatically deploys the approved build to Production.

Deployment validation includes:

- Service health
- Startup verification
- Smoke testing

---

### 11. Monitoring & Notifications

Monitor:

- Application health
- Logs
- CPU and Memory
- Performance
- Errors

Automatically send notifications through:

- Email
- Slack
- Microsoft Teams

If failures occur:

- Notify the development team.
- Roll back if configured.

---

# 3. Cloud-Native CI/CD Pipeline

## Overview

Cloud-native CI/CD extends traditional automation by deploying containerised applications to cloud platforms such as Kubernetes, Azure Kubernetes Service (AKS), Amazon Elastic Kubernetes Service (EKS), or Google Kubernetes Engine (GKE). It supports scalable deployments with minimal downtime.

## Pipeline Flow

### 1. Development

- Developer writes code.
- Execute local tests.
- Commit code to Git.

---

### 2. Source Control

- Push changes.
- Merge Pull Request into the `main` branch.

---

### 3. Pipeline Trigger

Automatically start the pipeline using:

- Git Webhooks
- Poll SCM (optional)

---

### 4. Build Application

Compile and package the application.

```bash
mvn clean verify
```

---

### 5. Static Code Analysis

Run quality analysis using:

- SonarQube
- Checkstyle

Quality gates must pass before deployment continues.

---

### 6. Automated Testing

Run:

- Unit Tests
- Integration Tests
- Smoke Tests

Pipeline stops if tests fail.

---

### 7. Build Container Image

Package the application into a Docker container image.

Example:

```bash
docker build -t myapp:1.0 .
```

---

### 8. Push Image to Container Registry

Upload the container image to a registry such as:

- Docker Hub
- Azure Container Registry (ACR)
- Amazon Elastic Container Registry (ECR)
- Google Artifact Registry (GAR)

---

### 9. Deploy to Development

Deploy the container image to the Development environment using:

- Kubernetes
- Azure App Service
- AWS ECS
- Google Cloud Run

Run automated smoke tests.

---

### 10. Deploy to Staging

Promote the validated image to the Staging environment.

Perform:

- QA testing
- User Acceptance Testing (UAT)
- Performance testing
- Security validation

---

### 11. Deploy to Production

Deploy using modern deployment strategies:

- Blue-Green Deployment (one environment is live receiving user requests while the other tests the new version, a load balancer / router switches traffic to the new version after validation)
- Canary Deployment (one or a few instances of the new version are deployed alongside the old version, gradually increasing traffic to the new version while monitoring for issues)
- Rolling Update (gradually replace old instances with new ones, ensuring that a minimum number of instances are always available)

This minimises downtime and deployment risk.

---

### 12. Monitoring & Observability

Continuously monitor the application using tools such as:

- Prometheus
- Grafana
- Azure Monitor
- AWS CloudWatch
- ELK Stack
- OpenTelemetry

Monitor:

- CPU
- Memory
- Response times
- Errors
- Logs
- Traces
- Metrics

Alerts are automatically sent when thresholds are exceeded.

---

### 13. Automatic Rollback

If monitoring detects deployment failures:

- Roll back to the previous stable version automatically.
- Restore application availability.
- Notify the development team.
- Create incident reports for investigation.

---

# Comparison

| Feature | Manual Deployment | Automated CI/CD | Cloud-Native CI/CD |
|----------|-------------------|-----------------|--------------------|
| Build | Manual | Automated | Automated |
| Testing | Mostly Manual | Automated | Automated |
| Static Analysis | Optional | SonarQube + Checkstyle | SonarQube + Checkstyle |
| Pipeline Trigger | Manual | Webhook / Poll SCM | Webhook / Poll SCM |
| Artifact Packaging | Manual | Automated | Automated |
| Container Images | No | Optional | Yes |
| Container Registry | No | Optional | Yes |
| Development Deployment | Manual | Automated | Automated |
| Staging Deployment | Manual | Optional | Automated |
| Production Deployment | Manual | Automated | Automated |
| Deployment Strategy | Manual | Standard | Blue-Green / Canary / Rolling |
| Monitoring | Manual | Automated | Full Observability |
| Notifications | Manual | Automated | Automated |
| Rollback | Manual | Optional | Automatic |
| Scalability | Low | Medium | High |
| Reliability | Medium | High | Very High |
| Release Speed | Slow | Fast | Very Fast |

# 4. Harness DevSecOps CI/CD Pipeline

## Overview

Harness is an AI-native DevSecOps platform that automates Continuous Integration (CI), Continuous Delivery (CD), Continuous Verification (CV), Security Testing, Governance, and Deployment. Unlike traditional CI/CD tools, Harness embeds security, compliance, policy enforcement, and AI-assisted verification throughout the software delivery lifecycle.

The pipeline continuously validates code quality, security posture, deployment health, and production behaviour before allowing software to progress through each stage.

---

## Harness Pipeline Flow

### 1. Development

- Developer writes code locally.
- Execute local unit tests.
- Commit code to a feature branch.
- Push changes to the Git repository.
- Create a Pull Request for review.

---

## Continuous Integration (Harness CI)

### 2. Pipeline Trigger

The Harness CI pipeline starts automatically using:

- Git Webhooks (recommended)
- Poll SCM (optional)
- Pull Request events
- Merge to `main` branch

Harness provisions ephemeral build infrastructure (Kubernetes or cloud runners) to execute builds in isolated environments.

---

### 3. Source Checkout

Harness:

- Clones the repository
- Retrieves pipeline configuration
- Downloads required dependencies
- Prepares the build environment

---

### 4. Build Application

Compile the application.

Example:

```bash
mvn clean verify
```

or

```bash
mvn clean package
```

Build outputs include:

- JAR
- WAR
- ZIP
- MSI
- Other deployment artifacts

---

### 5. AI DevSecOps Quality Assessment

Harness AI evaluates the pipeline and build for quality before deployment.

Quality assessment includes:

- Build validation
- Dependency validation
- Pipeline health
- Build reliability
- AI recommendations
- Failed build analysis

---

### 6. Code Quality Analysis

Perform automated code quality checks.

Examples:

- SonarQube
- Checkstyle
- PMD
- SpotBugs

Checks include:

- Code smells
- Bugs
- Maintainability
- Technical debt
- Quality Gates
- Coding standards

Pipeline fails if quality gates are not met.

---

### 7. Automated Unit Testing

Execute automated tests such as:

- Unit Tests
- Integration Tests
- Smoke Tests

Harness collects:

- Test reports
- Coverage reports
- Test trends

Failed tests stop the pipeline automatically.

---

### 8. Security Assessment

Harness Security Testing (DevSecOps) performs multiple security scans before artifacts are built.

#### Static Application Security Testing (SAST)

Scans source code for:

- SQL Injection
- Cross-Site Scripting (XSS)
- Hardcoded credentials
- Unsafe coding patterns
- Security vulnerabilities

Examples:

- Semgrep
- SonarQube Security
- Checkmarx
- Fortify

---

#### Software Composition Analysis (SCA)

Scans third-party dependencies for:

- Known CVEs
- Outdated libraries
- Vulnerable packages
- Open-source license risks

Examples:

- Snyk
- Black Duck
- OWASP Dependency Check

---

#### Secrets Detection

Detect exposed secrets such as:

- AWS Keys
- Azure Keys
- GCP Credentials
- Passwords
- API Tokens
- SSH Keys

Pipeline fails if secrets are detected.

---

#### Container Security Scan

After container creation, scan images for:

- Operating system vulnerabilities
- Package vulnerabilities
- Malware
- Critical CVEs
- Configuration weaknesses

Examples:

- Trivy
- Aqua
- Prisma Cloud
- Grype

---

### 9. Risk Assessment & Policy Enforcement

Harness Governance validates deployments against organisational policies.

Policy checks include:

- Security policies
- Compliance requirements
- Infrastructure policies
- Deployment policies
- Environment restrictions
- Branch protection
- Required approvals

Policy engines may include:

- Open Policy Agent (OPA)
- Harness Governance
- Custom policy rules

Deployments violating policy are automatically blocked.

---

### 10. Compliance Validation

Validate organisational and regulatory compliance.

Examples include:

- CIS Benchmarks
- PCI DSS
- HIPAA
- SOC 2
- ISO 27001
- NIST
- Internal governance standards

---

### 11. Package Application

Generate deployment artifacts:

- JAR
- WAR
- ZIP
- MSI

Version and publish build artifacts.

---

### 12. Build Container Image

Create a container image from the application.

Example:

```bash
docker build -t myapp:1.0 .
```

Images are versioned using:

- Git Commit
- Build Number
- Semantic Version

---

### 13. Push Image to Container Registry

Publish the validated image to a container registry.

Supported registries include:

- Amazon Elastic Container Registry (ECR)
- Azure Container Registry (ACR)
- Docker Hub
- Google Artifact Registry (GAR)
- Harbor
- JFrog Artifactory

The image becomes the deployment artifact used throughout the CD pipeline.

---

# Continuous Delivery (Harness CD)

### 14. Deploy to Development

Deploy the validated container image into the Development environment.

Typical deployment targets:

- Kubernetes
- Amazon EKS
- Azure AKS
- Google GKE
- OpenShift
- ECS
- VM-based environments

Post-deployment validation includes:

- Smoke tests
- Health checks
- Service availability
- API validation

---

### 15. Deploy to QA

Automatically promote the same immutable artifact to QA.

Activities include:

- Functional testing
- Regression testing
- Integration testing
- Performance validation

---

### 16. Approval Gates

Before production promotion, Harness can require approval from:

- QA
- Security
- Product Owner
- Release Manager
- Change Advisory Board (CAB)

Approvals may be:

- Manual
- Automated
- Policy-driven

---

### 17. Deploy to Staging

Deploy the production candidate into the Staging environment.

Typical validation includes:

- Load testing
- End-to-end testing
- Production simulation
- User Acceptance Testing (UAT)

---

### 18. Progressive Production Deployment

Harness supports progressive delivery strategies to minimise deployment risk.

Supported strategies include:

#### Canary Deployment

- Deploy to a small percentage of users.
- Observe behaviour before wider rollout.

#### Blue-Green Deployment

- Deploy to a parallel production environment.
- Switch traffic after successful validation.

#### Rolling Update

- Replace application instances gradually.
- Maintain application availability throughout deployment.

---

### 19. Deploy to Production

Following successful verification and approvals, Harness deploys the application to Production.

Deployment validation includes:

- Health checks
- Readiness probes
- Liveness probes
- API availability
- Service validation

---

# Continuous Verification (Harness CV)

Unlike traditional monitoring, Harness continuously analyses application behaviour after deployment and compares it against historical baselines.

---

### 20. Continuous Verification

Harness continuously validates production health using AI and machine learning.

Verification includes:

- Deployment verification
- Service health analysis
- Error rate analysis
- Latency analysis
- Infrastructure health
- Application behaviour comparison
- Baseline anomaly detection

---

### 21. Log Analysis

Harness integrates with logging platforms to detect abnormal application behaviour.

Supported platforms include:

- Splunk
- ELK Stack (Elasticsearch, Logstash, Kibana)
- Datadog Logs
- New Relic Logs

Log analysis identifies:

- Exceptions
- Error spikes
- Failed requests
- Unexpected application behaviour

---

### 22. Monitoring Analysis

Harness analyses metrics collected from monitoring platforms.

Supported integrations include:

- Prometheus
- Grafana
- Datadog
- New Relic
- AWS CloudWatch
- Azure Monitor

Metrics evaluated include:

- CPU utilisation
- Memory usage
- Response times
- Request throughput
- Error rates
- Availability
- Service health

---

### 23. AI Risk Detection

Harness continuously evaluates deployment risk by analysing:

- Infrastructure metrics
- Application metrics
- Logs
- Traces
- Deployment history
- Historical baselines

The platform automatically identifies anomalies and determines whether the deployment is healthy or degrading.

---

### 24. Automated Rollback Analysis

If Continuous Verification detects unacceptable risk, Harness can automatically:

- Stop the deployment
- Roll back to the previous stable version
- Restore application health
- Notify engineering teams
- Preserve deployment diagnostics for investigation

Rollback decisions are based on AI-driven health analysis rather than simple health checks alone.

---

### 25. Continuous Monitoring & Feedback

After deployment, Harness continuously collects operational feedback to improve future releases.

Feedback includes:

- Deployment success trends
- Service reliability
- Application performance
- Security findings
- Build quality
- Release metrics
- Incident history
- Mean Time to Recovery (MTTR)
- Deployment Frequency
- Change Failure Rate (CFR)

This continuous feedback loop enables engineering teams to improve software quality, security, reliability, and deployment confidence over time.

---

## Harness DevSecOps Pipeline Summary

| Phase | Key Activities |
|---------|----------------|
| **Development** | Code, Commit, Pull Request |
| **Harness CI** | Source Checkout, Build, AI Quality Assessment |
| **Code Quality** | SonarQube, Checkstyle, PMD, SpotBugs |
| **Testing** | Unit, Integration, Smoke Tests |
| **DevSecOps Security** | SAST, SCA, Secrets Detection, Container Scanning |
| **Governance** | Risk Assessment, Policy Checks, Compliance Validation |
| **Packaging** | Build Artifacts, Container Image Creation |
| **Registry** | Push Images to ECR, ACR, Docker Hub, GAR |
| **Harness CD** | Deploy Dev → QA → Approval Gates → Staging → Production |
| **Deployment Strategy** | Rolling Update, Canary, Blue-Green |
| **Continuous Verification** | AI Health Analysis, Deployment Verification |
| **Observability** | Log Analysis (Splunk, ELK), Monitoring (Prometheus, Grafana) |
| **AI Operations** | Risk Detection, Automated Rollback |
| **Continuous Feedback** | Monitoring, Metrics, Reliability Insights, Deployment Analytics |