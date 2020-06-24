# Exercise 6: Azure Governance for Kubernetes on Azure Arc

## Task 1: Apply Policy
Policies can be applied to ARC enabled Kubernetes the same way they are applied to Microsoft Azure virtual machines. Policies can be applied to ensure the Azure resources are compliant with established practices such as ensuring that all resources are tagged with an owner. Policies can be applied to ensure the Azure arc enabled clusters are compliant such as ensuring the cluster configuration is set through a specific repo or enforcing a specific label on a pod.

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
   - Configuration resource name: cluster-config
   - Operator resource name: cluster-config
   - Operator namespace: cluster-config
   - Operator scope: cluster
   - Operator type: Flux
   - Operator Parameters: --git-readonly
   - Repository URL: https://github.com/<your personal github account name>/arc-k8s-demo 
   - Set the **Enable helm** option to **false**
   - **Leave the other options set to default**
     
   ![](./images/arc-0042.png)   ![](./images/arc-0043.png) 
   
8. Select the **Create a remediation task** check box and then click **Review+create** 

     ![](./images/arc-0044.png)

10. Navigate to **Azure-Arc RG** -> **AzureArcAKSCluster1** -> **Policies**.

11. You can check if your cluster is **compliant** or **not** against **“[Preview]:Deploy GitOps to Kubernetes cluster”** policy you assigned in previous step by looking at the Compliance State Column

     ![](./images/arc-0049.png)
     
   > **Note**: The Compliant shows as **non-compliant**, you will need to create a remediation task in the next task and after sometime you will see the complaint state changed to **Compliant**
   
## Task 2: Create a remediation task

    
