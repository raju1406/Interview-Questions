Terraform Interview Questions:-
Explain core Terraform end-to-end workflow to deploy and delete resources in Azure or aws cloud?
Ans: Workflow:-

Write:- Author insfrastructure as code
INIT:- Intialize working directory containing Terraform configuration files
Validate:- Validate Terraform configuration files for syntactical and internal consistent
Plan:- Preview changes before applying
Apply:- Provision reproducible infrastructure
Destroy:- Delete Terraform managed infrastructure
Terraform fmt command is used to rewrite Terraform configuration to a canonical formal

We have existing Terraform infrastructure created in Azure/AWS cloud , now one particular resource needs to be re-created ,whenever we do the next Apply?
Terraform Taint:-

Terraform taint command informs Terraform that a particular object has become degaraded or damaged and needed to be replaced in next Apply

terraform state list

terraform taint "resource_name" (check the resource status in .tfstate file)

terraform apply

Terraform taint command is deprecated use -replace option with terraform apply instead terrform apply -replace="resource_name"

Explain or walk-through step by step process to secure .tfstate file and by making it readily available for other developers within the team?
Terraform Backends:-

terrform {
   backend "azurerm" {
      resource_group_name = "StorageAccount-ResourceGroup"
      storage_account_name = "abacd234"
      container_name = "tfstate"
      key = "prod.terraform.tfstate"
   }
}
Explain the various type of META-Arguments in terraform and their benefits?
Meta-Arguments changes the default behaviours of Terraform Configuration
depends_on
count
for_each
provider
lifecycle
who creates the terraform.tfstate.backup file and under which scenario it is created?
Backup state file is automatically created, when terrraform destroy command is executed
The above is done to restore infrastructure to the same state, prior running terraform destroy command
What is Terraform D?
Terraform D is a plugin used on most in-service systems and Windows. Terraform init by default searches next directories for plugins.
Why is Terraform used for DevOps?
Terraform uses a JSON-like configuration language called the HashiCorp Configuration Language (HCL). HCL has a very simple syntax that makes it easy for DevOps teams to define and enforce infrastructure configurations across multiple clouds and on-premises data centers.
Define null resource in Terraform.
null_resource implements standard resource library, but no further action is taken. The triggers argument allows an arbitrary set of values that will cause the replacement of resources when changed.
What do you mean by Terraform cloud?
Terraform Cloud is a platform that enables teams to use Terraform together, either on-demand or in response to various events. It is deeply integrated with Terraform's workflows and data, unlike a general-purpose continuous integration system.
It includes easy access to shared state and secret data, detailed policy controls for updating infrastructure and governing the contents of Terraform, a private registry for sharing Terraform modules, and lots more.
What is a Private Module Registry?
A Private Module Registry is a feature from Terraform Cloud that allows you to share Terraform modules across the organization. You can enforce rules or “sentinel policies” on the registry that specify how members of your organization can use the modules.
Is Terraform usable for an on-prem infrastructure?
Yes, Terraform can be used for on-prem infrastructure. As there are a lot of obtainable providers, we can decide which suits us the best. All that we need is an API.
Does Terraform support multi-provider deployments?
Yes, multi-provider deployments are supported by Terraform, which includes on-prem like Openstack, VMware, and we can manage SDN even using Terram too.
How is duplicate resource error ignored during terraform apply?
We can try the following options:
Delete those resources from the cloud provider(API) and recreate them using Terraform
Delete those resources from Terraform code to stop its management with it
Carry out a terraform import of the resource and remove the code that is trying to recreate them
What are some of the built-in provisioners available in Terraform?
Here is the list of built-in provisioners in Terraform:

Salt-masterless Provisioner

Remote-exec Provisioner

Puppet Provisioner

Local-exec Provisioner

Habitat Provisioner

File Provisioner

Chef Provisioner

Explain State File Locking?
State file locking is Terraform mechanism in which operations on a specific state file are blocked to avoid conflicts between multiple users performing the same process. When one user releases the lock, then only the other one can operate on that state. This helps in preventing state file corruption. This is a backend operation.
How to lock Terraform module versions?
A proven way of locking Terraform module version is using the Terraform module registry as a source. + We can use the ‘version’ attribute in module of the Terraform configuration file. As the Github repository is being used as a source, we need to specify versions, branch, and query string with ‘?ref’.
How will you upgrade plugins on Terraform?
Run ‘terraform init’ with ‘-upgrade’ option. This command rechecks the releases.hashicorp.com to find new acceptable provider versions.
It also downloads available provider versions. “.terraform/plugins/_” is the automatic downloads directory.
How will you make an object of one module available for the other module at a high level?
Ab output variable is defined in resource configuration.
Declare the output variable of module_A.
Create a file variable.tf for module B.
Establish the input variable inside this file having the same name as the key defined in module_B.
Replicate the process for making variable available to other modules
How will you control and handle rollbacks when something goes wrong?
I need to recommit the previous code version to be the new and current version in my VCS.
This would trigger as terraform run, which would be responsible for running the old code.
As Terraform is more declarative, I will make sure all things in the code roll back to the old code.
I would use the State Rollback Feature of Terraform Enterprise to roll back to the latest state if the state file got corrupted.
What is Sentinel?
Sentinel is a policy as a code tool used to enforce standard configurations for resources being deployed by Terraform. It can be used by organizations for compliance and governance purposes.
How can we export data from one module to another?
We can export data from a module by defining output blocks in the module configuration files. This data can then be transferred as a parameter to the destination module.
How can you define dependencies in Terraform?
Terraform has built-in dependency management. Terraform has two kinds of dependencies between resources- implicit and explicit dependencies.

Implicit dependencies, as the name suggests, are detected by Terraform automatically. This is when the output of a “resource A” is used in “resource B”. Terraform automatically detects that “resource B” needs to be created only after “resource A”

Explicit dependencies can be specified in cases where two resources are internally dependent on each other without sharing any outputs. This can be done by using the depends_on parameter in the configuration block

What is the external data block in Terraform?
Just like the local-exec provisioner, external data bock can be used to run scripts on machines running Terraform.
The difference between a provisioner and the external data block is that the scripts in the external data block can return data in JSON format, whereas provisioners cannot return any outputs.
It is important to note that external data blocks are also meant to be a last resort and should not be used if there is a better alternative.
How can two people using the Terraform cloud can create two different sets of infrastructure using the same working directory?
By using different workspaces. These users can start Terraform runs in two separate workspaces. Each workspace has a state file of its own, so as long as the resources do not overlap, both the users can successfully provision two different sets of infrastructure using the same code.
What happens when multiple engineers start deploying infrastructure using the same state file?
Terraform has a very important feature called “state locking”.
This feature ensures that no changes are made to the state file during a run and prevents the state file from getting corrupt.
It is important to note that not all Terraform Backends support the state locking feature. You should choose the right backend if this feature is a requirement
How can you use the same provider in Terraform with different configurations?
By using alias argument in the provider block.
You have a Terraform configuration file with no resources. What happens when you run the terraform apply command?
Terraform will destroy all the resources. Starting an empty run with terraform apply command is exactly the same as starting the terraform destroy run.
What happens if a resource was created successfully in terraform but failed during provisioning?
This is an unlikely scenario, but when this happens, the resource is marked as tainted and can be recreated by restarting the terraform run.
Which value of the TF_LOG variable provides the MOST verbose logging?
TRACE is the most verbose and the default value of the TF_LOG variable.
How can you import existing resources under Terraform Management?
By using the terraform import command.
Which command can be used to reconcile the Terraform state with the actual real-world infrastructure?
The terraform apply -refresh-only command is used to reconcile Terraform state with the actual real-world infrastructure. It is the new alternative to the terraform refresh command, which is now deprecated.
Which command can be used to switch between workspaces when using Terraform Cloud?
The terraform workspace select command is used to choose a different workspace.
Some other important terraform commands for technical interviews.
terraform init: Initializes remote backends; downloads providers and remote modules defined in your configuration.
terraform init -upgrade: used to upgrade the existing downloaded providers.
terraform plan: generates the execution plan for the infrastructure creation or updation.
terraform apply: creates or updates the infrastructure after requesting confirmation from user.
terraform apply –auto-approve: creates or updates the infrastructure; user approval stage is skipped.
terraform destroy: deletes the infrastructure after requesting confirmation from user.
terraform destroy –auto-approve: deletes the infrastructure; user approval stage is skipped.
terraform fmt: scans the current directory for configuration files and formats them according to the HCP canonical style and format.
terraform fmt –recursive: scans the current directory as well as the sub directories for configuration files and formats them according to the HCP canonical style and format.
terraform show: provides a human-readable output from a state or plan file.
