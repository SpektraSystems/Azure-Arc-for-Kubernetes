# Azure Arc for Kubernetes: Hands-on Lab

#### Lab time: 3 Hours

Azure Arc-enabled Kubernetes (preview) allows you to attach and configure Kubernetes clusters inside or outside of Azure . When a Kubernetes cluster is attached to Azure Arc, it will appear in the Azure portal. It will have an Azure Resource Manager ID and a managed identity. Clusters are attached to standard Azure subscriptions, are located in a resource group, and can receive tags just like any other Azure resource.

To connect a Kubernetes cluster to Azure, the cluster administrator needs to deploy agents. These agents run in a Kubernetes namespace named azure-arc and are standard Kubernetes deployments. The agents are responsible for connectivity to Azure, collecting Azure Arc logs and metrics, and watching for configuration requests.

Azure Arc-enabled Kubernetes supports industry-standard SSL to secure data in transit. Also, data is stored encrypted at rest in an Azure Cosmos DB database to ensure data confidentiality.

## Exercise 1: Getting started with Azure Governance 

In this exercise, you will walk through some of the Azure Governance capabilities including Azure Activity Logs, Resource tags and policies. We’ll be trying out these capabilities with Azure resources and then extend to Azure Arc enabled Kubernetes later during the lab.  
 
## Exercise 2: Getting started with On-Premise Kubernetes Cluster
In the provided lab environment, you would already have one single node kubernetes cluster deployed through Minikube running on-prem in a Hyper-V host. In this exercise, we’ll explore how to verify if the cluster is running or not and access the cluster.

## Exercise 3: Onboard Kubernetes Cluster to Azure Arc
Azure Arc extends Azure Resource Manager capabilities to Kubernetes clusters on any infrastructure across on-premises, multi-cloud, and edge. Azure Arc-enabled Kubernetes is currently in public preview.

In this exercise, you will browse through the on-prem kubernetes cluster which is hosted on Hyper-V and connect the Cluster to Azure Arc using the az connectk8s command.

## Exercise 4: Setup GitOps workflow on connected Cluster
In this exercise, you will deploy a sample kubernetes app using az k8sconfiguration command and link the cluster to a git repository containing the sourceControlConfiguration and also update the configuration in the repository which you have linked to connected cluster and verify if cluster is getting updated based on the changes made. 

The configuration is described declaratively in .yaml files and stored in Git. An agent watches the Git repo for changes and applies them. The same agent also periodically assures that the cluster state matches the state declared in the Git repo and returns the cluster to the desired state if any unmanaged changes have occurred.

The Azure Arc enabled Kubernetes config-agent running in your cluster is responsible for watching for new or updated sourceControlConfiguration resources and orchestrates adding, updating, or removing the Git repo links automatically.

The Git repository can contain any valid Kubernetes resources, including Namespaces, ConfigMaps, Deployments, DaemonSets, etc. It may also contain Helm charts for deploying applications. A common set of scenarios includes defining a baseline configuration for your organization, which might include common RBAC roles and bindings, monitoring or logging agents, or cluster-wide services.

## Exercise 5: Enforce GitOps using Azure Policy
In this exercise, you will see how to use Azure Policy to enforce that each Microsoft.Kubernetes/connectedclusters resource or Git-Ops enabled Microsoft.ContainerService/managedClusters resource has specific Microsoft.KubernetesConfiguration/sourceControlConfigurations applied on it.

## Exercise 6: Setup Azure Monitor On Connected Cluster
In this exercise, you will setup Azure Monitor on connected clusters and you can use the performance charts and health status to monitor the workload of Kubernetes clusters

## Exercise 7: Use Azure Policy for runtime enforcement of policies on Azure Arc Enabled Kubernetes
In this exercise, you will install Azure Policy Add-on for Azure Arc enabled Kubernetes to manage Policy assignment and also, you will Tag the Azure Arc Enabled Kubernetes and check Activity logs of resource group and azure arc resource.

## Exercise 8: Setting up GitOps Workflow with a repo having Helm Charts [Optional]
In this exercise, you will see how to configure and use Helm with Azure Arc enabled Kubernetes
