# Lab 7: Azure Monitor & Log Analytics

## 🎯 Objective
Set up Azure Monitor and Log Analytics to collect and analyze telemetry data.  
Configure alert rules for proactive monitoring (via Azure Portal) and run KQL queries to gain insights into VM activity.

## ⚙️ Resources Deployed
- Resource Group: rg-monitor-lab
- Log Analytics Workspace: log-monitor-lab
- Virtual Machine: lab-vm
- Action Group: ag-cpu-alert (email notification)
- Alert Rule: CPU usage > 80% with email notification (created in Azure Portal)

## 💰 Cost
FREE – Basic monitoring and log analytics in trial environments

## 📸 Screenshots

**SKU Error While Creating Workspace (Troubleshooting)**  
Initially attempted to create the Log Analytics workspace with the 'Standard' SKU, which failed because older SKUs are deprecated.  
![SKU Error](sku-error-while-creating-workspace.png)

**Log Analytics Workspace Creation**  
Fixed the issue by creating the workspace with the supported 'PerGB2018' SKU.  
![Workspace Creation](Workspace-Creation.png)

**Workspace Listing**  
Confirmed the workspace exists and is properly configured in the resource group.  
![Workspace Listing](Workspace-Listing.png)

**VM Connection to Workspace**  
Connected 'vm-monitor-test' to the Log Analytics workspace for telemetry collection.  
![VM Connection](VM-Connection.png)

**Action Group Creation Error (Troubleshooting)**  
Encountered subscription registration error for 'Microsoft.Insights' namespace while creating the action group. Registered the provider to resolve it.  
![Action Group Creation Error](Action-group-creation-error.png)

**Action Group Creation**  
Successfully created the action group 'ag-cpu-alert' with email receiver for notifications.  
![Action Group](Action-Group.png)

**Alert Rule Configuration (Portal)**  
Created a CPU alert rule in the **Azure Portal** with threshold >80% and linked to the action group.  
![Alert Rule](Alert-Rule.png)

**KQL Query Execution (Heartbeat)**  
Ran sample queries on Activity Logs to analyze VM performance and events.  
Example:  
Heartbeat
| summarize Count = count() by Computer, bin(TimeGenerated, 1h)
![Query Execution](Heartbeat-query.png)


##**📚 Key Learnings**

How to provision and configure a Log Analytics Workspace.

How to connect Azure VMs to the workspace for telemetry.

How to create action groups and alert rules in the Azure Portal for proactive monitoring.

How to troubleshoot common errors (namespace registration, SKU mismatch).

How to run KQL queries (Heartbeat) to analyze logs and performance data.

##**📌 Resume Bullets**

Configured Azure Monitor and Log Analytics Workspace to collect VM telemetry.

Created CPU alert rules in the Azure Portal with action groups for proactive monitoring.

Executed KQL queries (Heartbeat) to analyze Activity Logs and performance metrics.

Troubleshot and resolved Azure Monitor setup issues (namespace registration, SKU tier errors).
