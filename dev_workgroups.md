# Motivation

Observe modern trends (circa 2020) in addressing developer onboarding of web applications.

There are three dominate themes in the research: GitOPs, Containers & Functions as a Service

# Concepts

## GitOPs

A CD (Continuous Development) pipeline attached to git.

"Awesome GitOPs" [https://github.com/weaveworks/awesome-gitops]

"GitOps is a way to do Kubernetes cluster management and application delivery. It works by using Git as a single source of truth for declarative infrastructure and applications, together with tools ensuring the actual state of infrastructure and applications converges towards the desired state declared in Git. With Git at the center of your delivery pipelines, developers can make pull requests to accelerate and simplify application deployments and operations tasks to your infrastructure or container-orchestration system (e.g. Kubernetes)."

## Developer Portal

Attempts to reduce environmental scope for the developer.
Emphasis on writing plugins or microservices.

"What is a Developer Portal?" [https://pronovix.com/blog/infographic-what-developer-portal]

"Yes, your developer portal needs to contain API reference documentation (no matter what specification format you use) but a developer portal should also be a sort of self-service support hub, a trust signal, a communication nexus for API stakeholders and a key DevRel tool that helps an organization to provide the best possible developer experience for its APIs."

## Developer Space

A common digital social enviroment, often means remote sessions into shared VMs.

# Observations

- container sharing is a means to shipping toolchains
- live environment sharing augments pair programming
- cloud computing may host environments
- cloud services tend to include video streaming for pair programming
- Dev spaces tend to address devOps by supporting k8s
- FaaS (Functions as a Service) can reduce required devOps knowledge
- Kubernetes may standardize required devOps knowledge
- GitOps reduces required devOps knowledge
- "Terraform is not a pipeline, it's an infrastructure automation tool." [https://www.reddit.com/r/devops/comments/f9tbqu/help_gitopsk8s_via_terraform_is_driving_me_nuts/]

# Developer Portals/Spaces

At the base there is sharing toolchains (often as environments) as well as code.
But many also offer hosted virtual machines to coordinate development.

## Auze Dev Spaces

https://docs.microsoft.com/en-us/azure/dev-spaces/

- Kubernetes cluster
- Visual Studio
- Cloud Storage & IDE

## CodeEnvy

https://codenvy.com/

- Docker cluster
- Eclipse IDE
- Cloud Storage & IDE
- Redhat

## Koding

https://www.koding.com/

- VM Sharing

## Backstage

https://github.com/spotify/backstage

- UI Devportal

# Kubernetes Provisioning

Tools for creating kubernetes clusters

## Kops

## Kubeadm

## Kubespray

# Kubernetes App Deployment

Tools to deploy user apps to kubernetes

## Devspace

https://devspace.cloud/

- namespaces & users

## Kompose

docker-compose to helm chart converter

# Kubernetes Serverless

Complete serverless stacks on top of kubernetes

## Kubeless

https://github.com/kubeless/kubeless

- GHub: 5.5k, 562

## Fission

https://github.com/fission/fission

- Ghub: 5k, 457

## OpenWhisk

https://github.com/apache/openwhisk

- Apache
- Docker-compose for local
- Nice feature spread: Kafka, websockets, alarms, pushnotifications
- Ghub: 4.6k, 901
