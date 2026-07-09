# Day 11 — Developer Tools & Deployment Services

## Introduction
AWS provides a rich set of developer tools and managed deployment services. These services help developers build, test, and deploy applications faster — and are increasingly tested on the CLF-C02 exam.

---

## AWS Developer Tools (CI/CD)

### AWS CodeCommit
- Managed **Git repository** service (like GitHub on AWS)
- Stores code privately in AWS
- Integrates with other CodeSuite tools

### AWS CodeBuild
- Managed **build service** — compiles code, runs tests, produces deployable artifacts
- Pay per build minute
- Scales automatically

### AWS CodeDeploy
- **Automates code deployments** to EC2, Lambda, on-premises servers
- Deployment strategies:
  - **In-place:** Updates existing instances
  - **Blue/Green:** Deploy to new instances, switch traffic, retire old
- Rollback on failure

### AWS CodePipeline
- **CI/CD orchestration** service
- Automates the full release process: source → build → test → deploy
- Integrates with CodeCommit, CodeBuild, CodeDeploy, GitHub, Jenkins

### AWS CodeStar
- Unified UI to manage all CodeSuite services in one place
- Quickly create CI/CD projects
- Pre-built project templates

### AWS Cloud9
- Browser-based **IDE (Integrated Development Environment)**
- Write, run, and debug code in the browser
- Pre-installed AWS CLI and development tools
- Supports pair programming (share environment with teammates)

---

## Infrastructure as Code (IaC)

### AWS CloudFormation
- Provision and manage AWS resources using **JSON or YAML templates**
- Declarative — define what you want, AWS creates it
- **Stack:** A collection of resources created from a template
- Free to use (pay only for resources created)
- Supports rollback on failure
- **Template → Stack → Resources**

### AWS CDK (Cloud Development Kit)
- Define infrastructure using **programming languages** (TypeScript, Python, Java, .NET)
- Synthesises to CloudFormation templates under the hood
- Familiar programming constructs (loops, conditions)

### AWS SAM (Serverless Application Model)
- Extension of CloudFormation for **serverless applications**
- Simplified syntax for Lambda, API Gateway, DynamoDB
- Includes local testing capabilities

---

## Application Deployment Services

### AWS Elastic Beanstalk
- **PaaS** — deploy web applications without managing infrastructure
- Supports: Node.js, Python, Java, .NET, PHP, Ruby, Go, Docker
- AWS handles: provisioning, load balancing, scaling, health monitoring
- You retain full control of underlying resources
- **Use when:** Developers want to deploy apps without infrastructure knowledge

### AWS App Runner
- Fully managed service to **deploy containerised web apps and APIs**
- No infrastructure management, auto-scaling
- Source: Container image or source code repository
- Simpler than ECS for straightforward web app deployments

### AWS Amplify
- Build and deploy **full-stack web and mobile** applications
- Hosting, authentication, storage, APIs — all managed
- Integrated with React, Angular, Vue, iOS, Android, Flutter
- CI/CD built-in from Git repositories

---

## AWS Migration Services

### AWS Application Migration Service (MGN)
- **Lift-and-shift** migration of physical, virtual, and cloud servers
- Replicates source servers in real-time
- Minimal cutover window

### AWS Database Migration Service (DMS)
- Migrate databases with minimal downtime
- Supports homogeneous and heterogeneous migrations
- Continuous replication

### AWS Migration Hub
- **Central dashboard** to track migration progress
- Aggregates data from multiple migration tools

### AWS Application Discovery Service
- **Discover on-premises infrastructure** before migration
- Collects server utilisation and dependency data
- Helps plan migration

### AWS Transfer Family
- Managed SFTP, FTPS, FTP, AS2 file transfers to/from S3 and EFS
- Use for migrating workflows that use traditional file transfer protocols

---

## Amazon API Gateway

- Fully managed service to **create, publish, maintain, and secure APIs**
- Supports REST, HTTP, and WebSocket APIs
- Integrates with Lambda, EC2, any HTTP backend
- Features: Authentication (Cognito, IAM), throttling, caching, monitoring
- Pay per API call

---

## AWS AppConfig

- Deploy **application configuration** changes safely
- Validate configuration before deployment
- Gradual rollout with automatic rollback on errors

---

## AWS X-Ray

- **Distributed tracing** for applications
- Trace requests as they travel through microservices
- Identify bottlenecks and errors in distributed applications
- Works with Lambda, EC2, ECS, Elastic Beanstalk

---

## CI/CD Pipeline Summary

```
Developer pushes code
        ↓
AWS CodeCommit (source repo)
        ↓
AWS CodePipeline (orchestrates)
        ↓
AWS CodeBuild (compile, test)
        ↓
AWS CodeDeploy (deploy to EC2/Lambda)
        ↓
Application running in production
```

---

## Practice Questions

1. A company wants to automate their deployment pipeline from code commit through build, test, and production deployment. Which service orchestrates this workflow?
   - A) CodeCommit  B) CodeBuild  C) CodePipeline ✓  D) CodeDeploy

2. A developer wants to write infrastructure as code using Python instead of JSON/YAML. Which service should they use?
   - A) CloudFormation  B) AWS CDK ✓  C) SAM  D) Elastic Beanstalk

3. Which service provides a browser-based IDE for writing and debugging code directly on AWS?
   - A) CodeStar  B) Cloud9 ✓  C) CodeCommit  D) Amplify

4. A startup wants to deploy their Node.js web application without managing any infrastructure. Which is the SIMPLEST option?
   - A) EC2 with Auto Scaling  B) ECS with Fargate  C) Elastic Beanstalk ✓  D) Lambda
