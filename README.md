# Enterprise DevSecOps GitOps Platform on AWS EKS



## Overview



This project demonstrates a complete enterprise-grade DevSecOps implementation using AWS, Kubernetes, GitOps, CI/CD, containerization, security scanning, monitoring, and Infrastructure as Code concepts.



The platform was designed and implemented to automate application build, security validation, containerization, deployment, monitoring, and GitOps-based delivery into Amazon EKS.



---



# Architecture Diagram


<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/97d9f004-12a5-4593-939b-d0e0a289dc7e" />




# Project Highlights



* Complete DevSecOps CI/CD implementation

* GitOps-based deployment using ArgoCD

* Kubernetes deployment on Amazon EKS

* Dockerized frontend and backend applications

* Helm-based Kubernetes packaging

* Security scanning using Trivy

* Static code analysis using SonarQube

* Jenkins multi-stage pipelines

* Environment separation (Dev \& Prod)

* Monitoring using Prometheus and Grafana

* Container image management using Amazon ECR

* Automated deployments through GitOps workflow

* Namespace-based Kubernetes architecture


---



# Tech Stack



| Category           | Technologies           |

| ------------------ | ---------------------- |

| Cloud              | AWS                    |

| Containerization   | Docker                 |

| Orchestration      | Kubernetes, Amazon EKS |

| CI/CD              | Jenkins                |

| GitOps             | ArgoCD                 |

| Package Management | Helm                   |

| Registry           | Amazon ECR             |

| Security Scanning  | Trivy                  |

| Code Quality       | SonarQube              |

| Monitoring         | Prometheus, Grafana    |

| Notifications      | AWS SNS                |

| Frontend           | Vue.js                 |

| Backend            | Node.js                |

| Version Control    | GitLab                 |



---



# Infrastructure Components



## Jenkins Master



Responsible for:



* Pipeline execution

* Docker image build

* Security scanning
* 
* SonarQube integration

* ECR image push

* Deployment automation



---



## SonarQube Server



Used for:



* Static code analysis

* Code smell detection

* Security hotspot analysis

* Quality gate validation



---



## Amazon ECR



Used as centralized container image registry for:



* web-dev

* web-prod

* api-dev

* api-prod



---



## Amazon EKS



Kubernetes orchestration platform hosting:



* Dev namespace

* Prod namespace

* Monitoring namespace

* ArgoCD namespace



---



## ArgoCD GitOps



Responsible for:



* Continuous synchronization

* Git-based deployment automation

* Drift detection

* Declarative Kubernetes delivery



\---



## Helm Charts



Used for:



* Kubernetes manifest templating

* Environment-specific configuration

* Version-controlled deployments


---



## Monitoring Stack



### Prometheus



\* Metrics collection

\* Kubernetes monitoring

\* Node metrics

\* Pod metrics



### Grafana



* Visualization dashboards

* Cluster monitoring

* Infrastructure insights



---



# CI/CD Workflow



## Step 1 — Developer Push



Developer pushes code changes into GitLab repositories.



---



## Step 2 — Jenkins Pipeline Trigger



Jenkins pipeline automatically starts.



Pipeline stages:



1. Git Checkout

2. Dependency Installation

3. SonarQube Analysis

4. Trivy Security Scan

5. Docker Image Build

6. Docker Push to Amazon ECR

7. Helm Repository Update

8. GitOps Deployment Trigger



---



## Step 3 — GitOps Deployment



ArgoCD continuously watches Helm repositories.



Whenever image tag or manifests change:



* ArgoCD syncs automatically

* Kubernetes deployment updates

* New pods are rolled out



---


\## Step 4 — Monitoring



Prometheus collects metrics from:



* Kubernetes cluster

* Nodes

* Pods

* Applications



Grafana visualizes all collected metrics.



---



# Kubernetes Resources Used



* Deployments

* Services

* Namespaces
* Pods

* ReplicaSets

* Configurations through Helm values

* ApplicationSets in ArgoCD



---



# Security Implementation



## Trivy



Implemented for:



* Container vulnerability scanning

* Dependency scanning

* Security issue identification



---



## SonarQube



Implemented for:



\* Static analysis

\* Security hotspot detection

* Code quality enforcement


---



# Project Structure



```bash

project/

├── api/

│   ├── Dockerfile

│   ├── Jenkinsfile

│   └── source code

│

├── web/

│   ├── Dockerfile

│   ├── nginx.conf

│   ├── Jenkinsfile

│   └── source code

│

├── application-helm-charts/

│   ├── api/

│   └── web/

│

└── monitoring/

```



---



# Docker Multi-Stage Build



The frontend application uses multi-stage Docker builds.



## Why Multi-Stage Builds?



Benefits:



* Smaller final image size
* Cleaner runtime container

* Faster deployments

* Improved security

* Optimized production containers



\### Build Stage



Node.js image used to:



\* Install dependencies

\* Build frontend assets



\### Runtime Stage



Nginx image used to:



\* Serve static production files

\* Handle frontend routing

\* Reverse proxy API requests



\---



\# Challenges Faced



\* Kubernetes image caching with latest tags

\* ArgoCD synchronization debugging

\* Frontend nginx reverse proxy configuration

\* Jenkins pipeline syntax troubleshooting

\* Container image versioning strategy

\* Service-to-service communication inside Kubernetes



\---



\# Key Learnings



\* Real-world GitOps workflow

\* Kubernetes troubleshooting

\* Helm templating

\* CI/CD debugging

\* DevSecOps implementation

\* Production-grade deployment practices

\* Monitoring and observability

\* Immutable image tagging strategy



\---



\# Future Improvements



\* Terraform-based infrastructure provisioning

\* Ingress Controller setup

\* SSL/TLS with cert-manager

\* Horizontal Pod Autoscaling

\* AWS Load Balancer Controller

\* Advanced Grafana dashboards

\* Secrets management using AWS Secrets Manager

\* Kubernetes Network Policies



\---



# Author



Lezin VM



AWS \& DevOps Engineer


* AWS Certified Solutions Architect – Associate

* Cloud \& DevOps Community Lead

* DevOps Enthusiast



