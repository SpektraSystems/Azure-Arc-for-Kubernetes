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

5. In the **Search** window for available definitions, type “Kubernetes ” and select the one called **Enforce labels on pods in Kubernetes cluster**.  Click the blue **Select** button below.

     ![](./images/arc-0017.png)

6. Click **Next** at the bottom of the window.

7. Provide  **app** against List of label field and Click **Next**

     ![](./images/arc-0029.png)
   
8. Select the **Create a Managed Identity** check box and then click **Next** again

     ![](./images/arc-0018.png)

9. Then at the bottom of the **Assign Policy** window click on **Create**.

10. Navigate to **Azure-Arc RG** -> **AzureArcAKSCluster1** -> **Policies**.

11. You can check if your cluster is **compliant** or **not** against **“[Preview]: Enforce labels on pods in Kubernetes cluster”** policy you assigned in previous step by looking at the Compliance State Column

     ![](./images/arc-0030.png)

12. You can check if the pods have app label or not by executing the following command in the powershell window:

    ```
    kubectl get pods --show-labels
    ```

     ![](./images/arc-0031.png)

   > **Note**: If you find **non-compliant**, you will need to update the configuration file to apply the tag and after sometime you will see the complaint state changed to **Compliant**

    
