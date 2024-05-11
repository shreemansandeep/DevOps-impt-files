### 1. what is the difference between Agile and DevOps?

A. Agile and DevOps are both software development methodologies, but they have different focuses and goals.

**Agile** is a project management approach that emphasizes the rapid delivery of working software and encourages collaboration and flexibility throughout the development process. Agile teams use a set of principles and practices, such as Scrum or Kanban, to manage their work and deliver value to customers quickly and iteratively.

**DevOps**, on the other hand, is a set of practices and tools that aim to bring together development and operations teams to improve collaboration, automate processes, and increase the speed and reliability of software delivery. DevOps focuses on improving the entire software delivery process, from development to deployment, with an emphasis on automation, continuous integration, and continuous delivery.

While Agile focuses on delivering value to customers quickly and iteratively, DevOps focuses on improving the entire software delivery process through collaboration, automation and faster and reliable delivery. The two methodologies can be integrated together to achieve faster and more reliable software delivery.

### 2. what is difference between continuous delivery and continuous deployment?
A. **Continuous Delivery (CD)** is a software development practice that involves automating the software release process so that code changes can be built, tested, and made ready for deployment to production. However, the actual deployment to production is a manual process that requires human intervention. <br/>
**Continuous Deployment (CD)** is a software development practice that involves automatically deploying code changes to production as soon as they are ready and pass all tests. This means that every change that passes automated tests is automatically deployed to production without any human intervention. <br/>
**Continuous integration (CI):** is the practice of regularly merging code changes into a shared repository. This helps to identify and resolve conflicts early in the development process. <br/>
The main difference between the two is that Continuous Delivery automates the release process but deployment to production requires human intervention, while Continuous Deployment fully automates both the release and deployment processes.

### 3. what is blue green deployment strategy?
A. Blue-green deployment is a deployment strategy that reduces downtime and risk by running two identical production environments called Blue and Green.

In a blue-green deployment, the new version of the application is deployed to the green environment, while the old version continues to run in the blue environment. Once the new version is deployed and tested, traffic is switched from the blue environment to the green environment. If there are any problems with the new version, traffic can be switched back to the blue environment.

Blue-green deployment is a good choice for applications that have a high availability requirement. It can also be a good choice for applications that are complex or difficult to deploy.

Here are some of the benefits of blue-green deployment: <br/>
**Zero downtime:** Because the new version of the application is deployed to a separate environment, there is no downtime during the deployment process. <br/>
**Reduced risk:** If there are any problems with the new version of the application, traffic can be switched back to the old version. <br/>
**Increased scalability:** Because the new version of the application is deployed to a separate environment, it can be scaled independently of the old version.

### 4. what is Rolling Deployment strategy in Kubernetes?
A. Rolling deployment is the default deployment strategy in Kubernetes. It lets you update a set of pods with no downtime, by gradually replacing old pods with new pods that run a new version of the application. The new pods are scheduled on eligible nodes in the cluster.

## AWS Cloud
### 1. Explain AWS VPC architecture?
A. **AWS VPC (Virtual Private Cloud)** is a virtual network that allows you to launch and manage AWS resources in a private, isolated, and secure environment. The architecture of an AWS VPC is composed of several components, including:

**Subnets:** A subnet is a range of IP addresses in your VPC that can be used to launch AWS resources. Subnets can be public or private, depending on whether they have a route to the internet or not.

**Route Tables:** Route tables define the traffic flow in your VPC. They contain a set of rules, known as routes, that determine where network traffic is directed.

**Internet Gateway:** An Internet Gateway (IGW) allows resources in your VPC to connect to the internet. It acts as a bridge between your VPC and the public internet.

**NAT Gateway:** A NAT (Network Address Translation) Gateway allows private instances in your VPC to communicate with the internet while remaining private. The NAT Gateway acts as an intermediary between your private instances and the internet.

**Security Groups:** Security groups act as a virtual firewall for your resources. They allow you to control inbound and outbound traffic to your resources based on IP addresses, protocols, and ports.

**Network Access Control Lists (NACLs):** NACLs are an additional layer of security that controls inbound and outbound traffic at the subnet level. 

**VPN Connections:** A VPN (Virtual Private Network) connection allows you to establish a secure and encrypted connection between your VPC and your on-premises network.

**Transit Gateway:** Transit Gateway is a service that simplifies and centralizes network connectivity between multiple VPCs and on-premises networks. It allows you to build large, complex networks that are easy to manage and scale.

**VPC Peering:** VPC peering is a way to connect two Amazon Virtual Private Clouds (VPCs) together so that resources in each VPC can communicate with each other using private IP addresses. It enables secure and direct connectivity between VPCs without the need for internet gateways or VPN connections.

**VPC Flow Logs:** it is a feature in AWS that records information about IP traffic going to and from network interfaces in a VPC.

Overall, the AWS VPC architecture provides a flexible and scalable way to deploy and manage your AWS resources in a secure and isolated environment.

### 2. Explain AWS ELB architecture?
A. AWS Elastic Load Balancer (ELB) is a service that automatically distributes incoming traffic to multiple targets such as Amazon EC2 instances, containers, and IP addresses in one or more Availability Zones. It helps to improve the availability and scalability of your applications by spreading incoming traffic across healthy targets.
There are three types of Elastic Load Balancer available in AWS:

**Application Load Balancer (ALB):** ALB is designed to route traffic to multiple HTTP/HTTPS targets and supports content-based routing, which enables you to route traffic based on the content of the request. <br/>
**Network Load Balancer (NLB):** NLB is designed to handle traffic for TCP/UDP protocols and is suitable for low-latency and high-throughput workloads. <br/>
**Classic Load Balancer (CLB):** CLB is the legacy Elastic Load Balancer service, which supports both HTTP/HTTPS and TCP protocols.

**Some of the features of AWS Elastic Load Balancer include:**

**Automatic scaling:** Elastic Load Balancer can automatically adjust the number of instances based on the incoming traffic.
**Health checks:** Elastic Load Balancer performs health checks on each target to ensure that they are healthy and available to receive traffic.
**SSL termination:** Elastic Load Balancer can terminate SSL/TLS connections, which offloads the processing from the backend instances.
**Security:** Elastic Load Balancer integrates with AWS security services such as AWS WAF and AWS Shield to protect your applications from attacks.
**Access logs:** Elastic Load Balancer can log access logs for troubleshooting and analysis purposes.

Overall, AWS Elastic Load Balancer is a powerful and flexible service that helps to improve the availability, scalability, and security of your applications running on AWS.

### 3. what is AWS Auto Scaling architecture?
A. **AWS Auto Scaling** is a service that automatically scales resources based on the demand of your applications. An Auto Scaling group is a logical grouping of Amazon Elastic Compute Cloud (EC2) instances that are managed as a single entity. It helps to ensure that the number of instances running your applications is automatically adjusted to match the demand.
Here are some key features of AWS Auto Scaling group:

**Automatic scaling:** AWS Auto Scaling group can automatically increase or decrease the number of EC2 instances in response to changes in demand for your applications. <br/>
**Scale out and in:** AWS Auto Scaling group can scale out by launching new instances when demand increases and scale in by terminating instances when demand decreases. <br/>
**Health checks:** AWS Auto Scaling group performs health checks on each instance to ensure that they are healthy and available to receive traffic. <br/>
**Multiple Availability Zones:** AWS Auto Scaling group can launch instances in multiple Availability Zones to increase availability and reliability of your applications. <br/>
**Elastic Load Balancing integration:** AWS Auto Scaling group can be integrated with Elastic Load Balancing service to distribute traffic across instances. <br/>
**Instance launch configuration:** You can define the configuration details for instances that will be launched by the Auto Scaling group, such as the AMI, instance type, security groups, and user data. <br/>
**Instance termination policies:** You can define policies that determine which instances to terminate when scaling in.

Overall, AWS Auto Scaling group is a powerful service that helps to ensure your applications have the resources they need to handle the demand. It helps to improve the availability, scalability, and reliability of your applications running on AWS.

### 4. what is difference between launch template and launch configuration?
A. In AWS EC2, a Launch Configuration and a Launch Template are both used to define the configuration of your EC2 instances, but they have some differences.

A **Launch Configuration** is an older feature of EC2, while a Launch Template is a newer and more powerful feature.
A Launch Configuration is a set of instructions that define the configuration of your EC2 instances, including the AMI ID, instance type, security groups, and other settings. Once you create a Launch Configuration, you can use it to launch one or more EC2 instances. <br/>
**Launch Template** is a newer feature that allows you to define a set of configurations for your EC2 instances, similar to a Launch Configuration, but with more features and flexibility. With a Launch Template, you can define multiple versions of your template, manage permissions for who can launch instances using the template, and specify network settings, storage settings, and other advanced settings.

## Linux
### 1. what is difference between wget and curl command?
A. These commands are used to download a file from the internet using CLI.
The main difference between them is that curl will show the output in the console. On the other hand, wget will download it into a file.
We can save the data in a file with curl by using the -o parameter:

## Git and GitHub

### 1. Git Branching strategy?
A. We have multiple branches they are master, dev, Qa, Feature, Release. <br/>
**feature branch:** Developers are working on their features in feature branches it is created from dev branch. Once a feature is complete and tested, it's merged into dev branch. <br/>
**develop branch:** This is the development branch where ongoing work happens for future releases. <br/>
**Qa branch:** Once features are integrated into dev branch, they're pushed to the QA branch for testing to identify bugs and issues, and fixing before releasing to production. <br/>
**Release branch:** When features in dev branch are stable and QA is complete, a release branch is created from dev branch. This branch prepares the code for deployment to production. <br/>
**master branch:** This is the production-ready code of our software. It is "live" version used by our users. <br/>
**Hotfix branch:** If a critical bug is discovered in production, a hotfix branch is created directly from main branch. It is a branch that quickly fixes the bug and deploys it back to production, without affecting. <br/> <br/>
**Workflow:** <br/> -> Developers work on their features in feature branches it is created from dev branch. <br/>
-> Once a feature is complete and tested, it's merged into dev branch. <br/>
-> When dev branch is stable and tested, a release branch is created from dev branch. <br/>
-> If release branch is passing all tests merged into main branch and deployed to production. <br/>
-> If a critical bug is found in production, a hotfix branch is created from main to fix it and deploy quickly. <br/>
-> The hotfix branch is then merged back into both main and dev branch.


## Maven

### 1. what is difference between WAR and EAR?
A. **"WAR"** (Web Archive) files are used to deploy web applications. They contain all of the files that are needed to run a web application, including servlets, JSPs, HTML files, images, and other resources. <br/>
**"EAR"** (Enterprise Archive) files are used to deploy enterprise applications. They can contain multiple WAR files, as well as other types of files, such as EJBs (Enterprise Java Beans) and connectors.

### 2. what are Maven Default life cycle Phases?
A. **"validate** - validate the project is correct and all necessary information is available <br/>
**compile** - compile the source code of the project <br/>
**test** - test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed <br/>
**package** - take the compiled code and package it in its distributable format, such as a JAR. <br/>
**integration-test** - process and deploy the package if necessary into an environmentwhere integration tests can be run <br/>
**verify** - run any checks to verify the package is valid and meets quality criteria <br/>
**install** - install the package into the local repository, for use as a dependency in other projects locally <br/>
**Deploy** - done in an integration or release environment, copies the final package to the remote repository for sharing with other developers and projects.

## SonarQube

### 1. what is sonarqube?
A. SonarQube is a platform that analyzes software for bugs, vulnerabilities, and code smells. It performs static analysis on the source code and shows the results in reports. The reports help us to improve the security and stability of the application. It supports various languages and It can be integrated with build tools, such as Gradle and maven.

### 2. what is difference between code analysis and Quality Gate Status in sonarqube?
A. **"Code analysis"** is the process of examining source code to identify potential issues such as bugs, vulnerabilities. SonarQube provides a powerful code analysis engine that checks for various quality attributes in the code, such as coding standards, security, maintainability, and reliability. The code analysis results are displayed in the SonarQube UI as a set of metrics and issues that highlight areas that need attention. <br/>
**"Quality Gate status"**, is an indication of whether a project meets the required level of code quality, If the project meets all the quality criteria, the Quality Gate status is marked as "Passed," and if not, the status is marked as "Failed."

## Tomcat

## Jenkins

### 1.What is Jenkins and why is it used?
A. Jenkins is an open-source free automation tool used to build and test software projects.Jenkins is a continuous integration (CI) tool for real-time testing and reporting of builds. It is written in Java. It helps developers and testers working collaboratively to detect and close defects early in the software development lifecycle and encourage automated testing of builds.

### 2.What are the features of Jenkins? 
A. --> It is a free and open-source automation tool, <br/>
   --> Jenkins provides a number of plugins, <br/>
   --> It is easy to set up and install on multiple operating systems, <br/>
   --> Provides pipeline support, Fast release cycles, Easy upgrades, <br/>
   --> Supports distributed builds due to master-slave architecture, reducing the load on the CI server.
   
 ### 3.what is jenkins master slave architecture?
 A. Jenkins master-slave architecture is a distributed approach to running Jenkins jobs across multiple nodes.  In this architecture, there is a single Jenkins master server that manages the jobs and distributes them to one or more Jenkins slave nodes. The Jenkins master node is responsible for scheduling the jobs and managing the plugins and configurations.

## Ansible

## Docker
### 1. What is the difference between run and cmd and entry point?
A. The **"RUN" command** is used to execute commands during the build process of a Docker image. <br/>
The **"CMD" command** defines the default command and arguments that are executed when a container starts. However, these can be overridden by the user when running the container. <br/>
The **"ENTRYPOINT" command** defines the command and arguments that are always executed when a container starts. These cannot be overridden by the user.

### 2. what is difference between COPY and ADD?
A. **"COPY"** is a instruction that only copies files from the host machine (local system) to the image. <br/>
   **"ADD"** is a instruction that not only copies files from the host machine to the image, download files from URLs and also extract compressed archives (such as .tar or .zip files).
   
### 3. what is difference between VMs and Docker Containers?
A. **"VM":** VMs have the host OS and guest OS inside each VM. A guest OS can be any OS, like Linux or Windows. VMs takes a few minutes for VMs to boot. VMs runs on Hypervisor. <br/>
**"Container":** Docker is popular virtualization software that helps its users in developing, deploying, applications in a Docker Container with all their dependencies.
Docker Containers have the following benefits: Light-weight, Applications run in isolation, Occupies less space, Easily portable and highly secure, Short boot-up time.

## Kubernetes

### 1. Explain k8s architecture?
A.Kubernetes (K8s) architecture is composed of several key components, each responsible for different aspects of managing and running containerized workloads. Here's a high-level overview of the K8s architecture: <br/>
**"Master node":** The master node is the control plane for the Kubernetes cluster. It manages the overall state of the cluster and is responsible for scheduling workloads, maintaining cluster configuration, and scaling the cluster. The master node consists of several components, including the API server, etcd, controller manager, and scheduler. <br/>
**"API server":** The API server is the main interface for interacting with the Kubernetes cluster. It exposes the Kubernetes API, which allows users to manage and monitor the state of the cluster. <br/>
**"etcd":** etcd is a distributed key-value store that is used to store the configuration data for the Kubernetes cluster. It is used by the control plane to store information about pods, nodes, and other resources. <br/>
**"Controller manager":** The controller manager is responsible for running the various controllers that are responsible for maintaining the desired state of the cluster. Examples of controllers include the replication controller, which ensures that the desired number of replicas of a workload are running, and the node controller, which monitors and manages the nodes in the cluster. <br/>
**"Scheduler":** The scheduler is responsible for scheduling workloads to run on the available nodes in the cluster. It considers factors such as resource constraints, affinity and anti-affinity rules, and other policies to determine the best node for each workload. <br/>

**"Worker Node":** A node is a worker machine that runs containerized workloads. Each node has several components, including the Kubelet, container runtime, and kube-proxy. <br/>
**"Kubelet":** The Kubelet is the primary agent that runs on each node and is responsible for managing the containers on that node. It communicates with the API server to get information about the desired state of the cluster and ensures that the containers on the node match that state. <br/>
**"Container runtime":** The container runtime is the software that actually runs the containers. Kubernetes supports several container runtimes, including Docker and containerd. <br/>
**"kube-proxy":** kube-proxy is a network proxy that runs on each node and is responsible for routing traffic to the appropriate containers on that node. <br/>

### 2. Explain k8s services?
A. There are several types of services in Kubernetes, including: <br/>
**ClusterIP:** This is the default type of service. It exposes the service on a cluster-internal IP address, which is only reachable from within the cluster. <br/>
**NodePort:** This service type exposes the service on a static port on each node in the cluster, allowing external traffic to reach the service. <br/>
**LoadBalancer:** This service type creates an external load balancer that forwards traffic to the service. <br/>
**ExternalIP:** This service type maps the service to a DNS name instead of an IP address, allowing external clients to access the service using a DNS lookup. <br/>
**"Ingress controller":** Ingress is a controller that manages external access to Kubernetes services and it is responsible for routing traffic to pods. <br/>
In addition: <br/>
**"CNI plugin":** The CNI plugin is responsible for creating and managing the network interfaces for pods. <br/>
**"Service":** A service is a logical grouping of pods. Services provide a single point of access to a group of pods, and they can be used to load balance traffic across the pods.

### 3. Explain k8s Objects?
A. Here are some common Kubernetes objects: <br/>
**"Pod":** A pod is the smallest deployable unit in Kubernetes. It is a group of one or more containers that are scheduled and run together on a single node. <br/>
**"Deployment":** Deployments are used to manage the rollout of pods. It is used to create new pods, update existing pods, and rollback to previous versions of pods. <br/>
**"Service":** Services provide a way to expose applications that are running in the pods to the outside world. It can be used to load balance traffic, provide service discovery, and support other features. <br/>
**"ConfigMap":** ConfigMaps are used to store configuration data for our applications. It is used to store environment variables, command-line arguments, or other configuration data. <br/>
**"Secret":** Secrets are used to store sensitive data for our applications. It ise used to store passwords, API keys, or other sensitive data in a secure way. <br/>
**"PersistentVolume (PV)":** It represent a piece of storage in the cluster. It is created by the cluster administrator or dynamically by Kubernetes. PVs have a lifecycle independent of any individual Pod that uses the PV. <br/>
**"PersistentVolumeClaim (PVC)":** It represent a request for storage by a Pod. It is created by the user or application. PVCs specify the amount of storage and the access mode that is required. <br/>
**"Namespace":** A namespace is an object that provides a way to group of k8s resources within a cluster. It allows multiple teams or users to share a single cluster while maintaining their own isolated set of resources. <br/>
**"Volumes":** Volumes provide a way to store data that is shared between pods. It is used to store persistent data, such as database files, or to provide temporary storage, such as log files. <br/>
**"Replicaset":** ReplicaSets  are used to ensure that a certain number of pods are always running. It is a good way to scale our application up or down. <br/>
**DaemonSets:** DaemonSets are used to run a pod on every node in the cluster. They are a good way to run applications that need to be available on all nodes, such as logging or monitoring agents. <br/>
**Stateful workloads:** Stateful applications that require persistent storage and maintain state across restarts or migrations. Examples:  databases, messaging systems, and file systems. To manage stateful applications, we can use stateful sets, which provide stable network identities and persistent storage. <br/>
**Stateless workloads:** Stateless applications that do not require persistent storage and do not maintain state across restarts or migrations. Examples: web servers, application servers, and microservices. 
**Replication Controller:** A Replication Controller in Kubernetes is a resource that ensures that a specified number of replica pods are always running. It manages the pod lifecycle and maintains the desired state of a replicated application.


  Overall, Kubernetes objects provide a powerful way to manage and orchestrate containerized applications. They allow you to declaratively specify the desired state of your application and Kubernetes takes care of the underlying details to ensure that the application is deployed and managed correctly.

### 4. How to create eks k8s cluster uesing eksctl command?
```
 A1. eksctl create cluster --name test-cluster-1 --version 1.22 --region eu-central-1 --nodegroup-name worker-nodes --node-type t2.large --nodes 2 --nodes-min 2 --nodes-max 3
 A2. eksctl create cluster --name demo-eks --region us-east-2 --nodegroup-name my-nodes --node-type t3.small --managed --nodes 2 
```
### 5. what is pod affinity and node affinity in kubernetes?
A. Pod affinity and node affinity are Kubernetes features that allow you to control where pods are scheduled. <br/> **Pod affinity** lets you specify that a pod should be scheduled on the same node as other pods, <br/> while **node affinity** lets you specify that a pod should be scheduled on a node with certain labels. <br/>
**Here are some examples of pod affinity and node affinity:** <br/>
->You can use pod affinity to ensure that two pods that need to communicate frequently are scheduled on the same node. <br/>
->You can use node affinity to ensure that a pod is scheduled on a node with a certain amount of memory or CPU resources. <br/>
->You can use node affinity to ensure that a pod is scheduled on a node in a certain region or zone. <br/>

Pod affinity and node affinity can be used to improve the performance, reliability, and security of your Kubernetes applications.
