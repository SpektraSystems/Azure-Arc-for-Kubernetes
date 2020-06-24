# Exercise : Setup Azure Monitor On Connected Cluster

Azure Monitor for containers provides rich monitoring experience for the Azure Kubernetes Service (AKS) and AKS Engine clusters. With Azure Monitor for containers, you can use the performance charts and health status to monitor the workload of Kubernetes clusters
In this exercise, we will see how to enable monitoring of your Kubernetes clusters hosted outside of Azure that are enabled with Azure Arc, to achieve a similar monitoring experience.

## Task 1: Identify Log Analytics Workspace Resource Id

To enable monitoring of the connected cluster and integrate with an existing Log Analytics workspace, perform the following steps to first identify the full resource ID of the existing Log Analytics workspace. 
This is required for the workspaceResourceId parameter when you run the command to enable the monitoring add-on against the specified workspace

1.  Run the following command in Powershell window to get the resource Id of the Log Analytics workspace. Copy this Id to be used in the next tasks.

    ```
    az resource list --resource-type Microsoft.OperationalInsights/workspaces -o json --query [].id
    ```
    ![](./images/arc-0041.png)   


## Task2: Enable monitoring using PowerShell

1.  Open **Windows Powershell** from the Desktop 

    ![](./images/arc-0042.png) 

2.  Run the following command in Powershell to login to Azure Portal using Az Powershell Module. When Prompted for Username/Password, provide the details from Lab Environment Tab on the right.
 
    ```
    Set-ExecutionPolicy -ExecutionPolicy Bypass -Force
    Connect-AzAccount
    ```
    ![](./images/arc-0043.png)   
    
3.  Provide Log Analytics Workspace Id and Azure Arc Cluster ID in the following commands:
 
    ```
    $azureArcClusterResourceId = "Update Azure Arc Enabled Kubernetes Id here"
    $logAnalyticsWorkspaceResourceId = "Update Log Analytics Workspace Id here"
    $kubeContext = ""
    $proxyEndpoint = ""
    ```
    
4.  Run the following command to change the directory to C:\LabFiles
 
    ```
    cd C:\LabFiles
    ```
    
5.  Now, Run the following command to enable monitoring
 
    ```
    .\enable-monitoring.ps1 -clusterResourceId $azureArcClusterResourceId -kubeContext $kubeContext -workspaceResourceId $logAnalyticsWorkspaceResourceId -proxyEndpoint $proxyEndpoint
    ```
    ![](./images/arc-0044.png)  
    
6.  Once the executing is complete, you will see the output as shown below
 
    ![](./images/arc-0045.png)  
    
7.  After you've enabled monitoring, it might take about 15 minutes before you can view health metrics for the cluster.
 
8.  Open a new tab in browser in the VM and navigate to 
 
    ```
    https://aka.ms/azmon-containers
    ```
    
    This will take you to the Monitor page.
    
    ![](./images/arc-0046.png)     
    
9.  On the monitor page, scroll down and Click on **View monitored clusters** button 
 
    ![](./images/arc-0047.png)  
    
10.  Then Click on the Cluster that is listed 

    ![](./images/arc-0048.png) 

11.  On the blade that comes up, you 
 
    ```
    Set
    ```
    ![](./images/arc-0043.png) 
    
12.  On the monitor page, scroll down and Click on **View monitored clusters** button 
 
    ```
    Set
    ```
    ![](./images/arc-0043.png) 
    
13.  On the monitor page, scroll down and Click on **View monitored clusters** button 
 
    ```
    Set
    ```
    ![](./images/arc-0043.png) 
