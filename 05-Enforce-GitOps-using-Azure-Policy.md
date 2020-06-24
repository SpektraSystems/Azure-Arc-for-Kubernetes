# Exercise 5: Enforce GitOps using Azure Policy
In this exercise, you will see how to use Azure Policy to enforce that each Microsoft.Kubernetes/connectedclusters resource or Git-Ops enabled Microsoft.ContainerService/managedClusters resource has specific Microsoft.KubernetesConfiguration/sourceControlConfigurations applied on it.

## Task 1: Create a Policy Assignment
In this task you will select an existing policy definition and create a policy assignment. When creating the policy assignment you set the scope for the assignment: this will be the Azure Arc enabled Kubernetes Cluster. You will also set the parameters for the sourceControlConfiguration that will be created. Once the assignment is created the Policy engine will identify all connectedCluster or managedCluster resources that are located within the scope and will apply the sourceControlConfiguration to each one.

1. From the Azure Portal (https://portal.azure.com ), navigate to the resource group you have access to and click on AzureArcAKSCluster1 resource. 

     ![](./images/arc-0013.png)

2. From the **Azure Arc Enabled Kuberenetes** blade, click on **Go to Policies** under Configure Azure Policy.

     ![](./images/arc-0014.png)

3. Click **Assign policy**.

     ![](./images/arc-0015.png)

4. On the Basics Tab, click on the ellipses (…) to the right of **Policy definition**.

     ![](./images/arc-0016.png)

5. In the **Search** window for available definitions, type “Kubernetes ” and select the one called **Deploy GitOps to Kubernetes cluster**.  Click the blue **Select** button below.

     ![](./images/arc-0041.png)

6. Click **Next** at the bottom of the window.

7. Provide the following details under **Parameters** tab and Click **Next**
   - Configuration resource name: **cluster-config**
   - Operator resource name: **cluster-config**
   - Operator namespace: **cluster-config**
   - Operator scope: **cluster**
   - Operator type: **Flux**
   - Operator Parameters: **--git-readonly**
   - Repository URL: The forked repo of **https://github.com/Azure/arc-k8s-demo** that you are using for performing the lab
   - Set the **Enable helm** option to **false**
   - **Leave the other options set to default**
     
   ![](./images/arc-0042.png)   ![](./images/arc-0043.png) 
   
8. Select the **Create a remediation task** check box and then click **Review+create** 

     ![](./images/arc-0044.png)

10. Navigate to **Azure-Arc RG** -> **AzureArcAKSCluster1** -> **Policies**.

11. You can check if your cluster is **compliant** or **not** against **“[Preview]:Deploy GitOps to Kubernetes cluster”** policy you assigned in previous step by looking at the Compliance State Column

     ![](./images/arc-0049.png)
     
   > **Note**: The Compliant shows as **non-compliant**, you will need to create a remediation task in the next task and after sometime you will see the complaint state changed to **Compliant**
   
