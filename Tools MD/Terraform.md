1. Explain Terraform architecture????

A. Terraform is a popular open-source tool used for infrastructure as code (IAC) management. It enables users 
to manage their infrastructure in a declarative way. Terraform is designed to be modular, extensible, and 
highly configurable. The combination of configuration files, providers, state files, and modules enables users
to manage their infrastructure in a declarative, version-controlled way that is scalable and easy to maintain 
over time.

Terraform architecture consists of the following components:

Configuration files: Terraform uses configuration files to define the desired state of infrastructure. 
Configuration files specify the resources to be created, their properties, and their interrelationships.

Providers: Terraform providers are plugins that enable Terraform to interact with different cloud platforms or
infrastructure services.

State files: Terraform uses state files to store the current state of the infrastructure managed by Terraform.

Terraform CLI: The Terraform command-line interface (CLI) is used to execute Terraform commands, such as 
applying or destroying infrastructure.

Modules: Terraform modules are reusable blocks of infrastructure code that encapsulate a specific set of 
resources and their configuration.
---------------------------------------------------------------------------------------------------
2. Explain Terraform commands????

A. terraform init: Initializes a Terraform working directory by downloading required providers and modules.

terraform plan: Generates an execution plan that describes what Terraform will do when applying the 
configuration to the infrastructure.

terraform apply: Applies the changes described in a Terraform execution plan to the infrastructure.

terraform destroy: Destroys all the resources created by Terraform for the given configuration.

terraform validate: Validates the syntax of the Terraform configuration files.

terraform refresh: Updates the state file of a previously applied configuration.

terraform output: Displays the values of outputs from a Terraform configuration.

terraform state: Manipulates the state file used by Terraform.

terraform graph: Generates a visual representation of the dependencies between resources in a Terraform 
configuration.

terraform import: Imports existing resources into Terraform state.

terraform taint: Manually marks a resource as tainted, forcing it to be recreated on the next Terraform apply.

terraform untaint: Removes the tainted state from a resource.
----------------------------------------------------------------------------------------------
3. Terraform architecture consists of three main components????

Terraform architecture consists of three main components:

Terraform Core:
The Terraform Core is the heart of the Terraform architecture. It is responsible for the core functionality of
the tool, including parsing and interpreting Terraform configurations, creating and managing resource graphs, 
and applying changes to infrastructure. It is implemented in Go and provides a command-line interface (CLI) 
that developers can use to interact with Terraform.

Providers:
Terraform uses providers to interact with infrastructure resources. Providers are plugins that implement 
resource types for a particular cloud provider, such as AWS, Azure, or GCP. Providers provide the necessary 
APIs to create, read, update, and delete resources from the cloud provider. Terraform supports over 200 
providers that can be easily installed and configured.

State Management:
Terraform uses state management to keep track of the current state of the infrastructure being managed. 
The state is stored in a backend that can be configured to use different storage providers, such as S3, GCS, 
or Azure Blob Storage. The state contains information about the resources that Terraform manages, such as their
current state, metadata, and dependencies. This allows Terraform to make informed decisions about what changes
need to be made to the infrastructure during each deployment.
----------------------------------------------------------------------------------------------
4. explain terraform modules????

A. Terraform modules are a way to organize and reuse Terraform code to create infrastructure resources. 
A module is a collection of Terraform configurations that represent a reusable piece of infrastructure, 
with its own inputs, outputs, and resources. It can be used to encapsulate infrastructure components, 
abstract away complexity, and make infrastructure code more modular and maintainable.

Some benefits of using Terraform modules include:

Reusability: Modules can be used to encapsulate reusable infrastructure components, making it easy to reuse 
code across projects and teams.
Abstraction: Modules can abstract away complexity, making infrastructure code more modular and easier to 
understand and maintain.
Consistency: Modules can ensure consistency across infrastructure configurations, reducing the risk of 
configuration errors and making it easier to manage infrastructure at scale.
-------------------------------------------------------------------------------------------------------
5. What is Terraform, and how does it work????
Answer: Terraform is an open-source infrastructure-as-code tool that allows developers to define and manage 
infrastructure resources using a high-level, declarative language. Terraform works by creating a resource 
graph that defines the relationships between infrastructure resources and applies changes to the infrastructure
to achieve the desired state.

6. What is the difference between Terraform and other infrastructure-as-code tools????
Answer: Terraform is different from other infrastructure-as-code tools because it uses a declarative language 
to define infrastructure resources, while other tools use imperative scripting. This allows Terraform to 
provide a more flexible and scalable way to manage complex infrastructure deployments across multiple 
environments and cloud providers.

7. What is a Terraform module, and why is it important????
Answer: A Terraform module is a collection of Terraform configurations that represent a reusable piece of 
infrastructure, with its own inputs, outputs, and resources. Modules are important because they allow 
developers to encapsulate infrastructure components, abstract away complexity, and make infrastructure code 
more modular and maintainable.

8. What are Terraform providers, and how do they work????
Answer: Terraform providers are plugins that implement resource types for a particular cloud provider, such as
AWS, Azure, or GCP. Providers provide the necessary APIs to create, read, update, and delete resources from 
the cloud provider. Terraform supports over 200 providers that can be easily installed and configured.

9. What is Terraform state, and why is it important????
Answer: Terraform state is a record of the current state of the infrastructure being managed. The state 
contains information about the resources that Terraform manages, such as their current state, metadata, and 
dependencies. This allows Terraform to make informed decisions about what changes need to be made to the 
infrastructure during each deployment.

10. What is the difference between Terraform plan and Terraform apply????
Answer: Terraform plan creates an execution plan that shows what actions Terraform will take to achieve the 
desired state of the infrastructure, while Terraform apply applies the changes necessary to achieve the 
desired state of the infrastructure, as defined in the Terraform configuration.

11. How do you troubleshoot Terraform issues????
Answer: Troubleshooting Terraform issues involves understanding the Terraform logs, using the debug mode, and 
checking for common errors in the Terraform configuration. It is also important to ensure that the Terraform 
version is up-to-date and that the required providers are installed and configured correctly.

12. What is a Terraform backend, and why is it important????
Answer: A Terraform backend is a storage location for the Terraform state file. Backends allow Terraform to 
store and share the state file across multiple users and environments. It is important to configure the 
backend correctly to ensure the safety of the Terraform state.

13. How do you manage Terraform state????
Answer: Terraform state can be managed using the Terraform state command, which allows for the management of 
the Terraform state, such as moving or deleting resources. It is also important to ensure that the Terraform 
state is stored securely and is backed up regularly.

14. What are some best practices for using Terraform????
Answer: Some best practices for using Terraform include version control, modularization, naming conventions, 
testing, and using infrastructure-as-code principles. It is also important to follow the security and 
compliance guidelines of the organization and to regularly update the Terraform configuration and provider 
versions.
-----------------------------------------------------------


terraform apply -target=resource name --auto-approve

ex: terraform apply -target=aws_instance.my_server --auto-approve
ex: terraform apply -target=aws_security_group.my_sg --auto-approve
ex: terraform apply -target=aws_security_group.my_sg

terraform plan -target=aws_instance.my_server

Terraform workspace commands>>
1. terraform workspace list
2. terraform workspace new dev  # to create workspace
3. terraform workspace select dev  # to go following workspace
4. terraform workspace new prod
5. terraform workspace select prod  # to go following workspace
6. terraform workspace delete prod  # to delete workspace
