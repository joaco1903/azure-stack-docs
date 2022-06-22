---
title: Pricing for  Azure Kubernetes Service on Azure Stack HCI and Windows Server
description: Learn about the pricing for  Azure Kubernetes Service on Azure Stack HCI and Windows Server.
author: sethmanheim
ms.topic: conceptual
ms.date: 05/13/2022
ms.author: sethm 
ms.lastreviewed: 03/16/2022
ms.reviewer: mamezgeb

# Intent: As a Kubernetes administrator, I want to learn about pricing for AKS on Azure Stack HCI and Windows Server
# Keyword: cost of on-premises Kubernetes

---

# Pricing for Azure Kubernetes Service (AKS) on Azure Stack HCI and Windows Server

Azure Kubernetes Service (AKS) on Azure Stack HCI is a subscription-based on-premises Kubernetes offering that can be run on Azure Stack HCI version 20H2 or Windows Server 2019 Hyper-V clusters. The pricing for AKS on Azure Stack HCI and Windows Server is based on usage, and the billing data is sent to Azure.

Use the following list to explore pricing for AKS:

- Billing unit: **per vCPU of running worker nodes within workload clusters**:
  - AKS on Azure Stack HCI and Windows Server the management cluster usage is *not* charged
  - The workload cluster control plane and load balancer nodes are *not* charged
  - If you enable hyper-threading on the physical computer, which reduces the measured vCPU count by 50 percent.
- Pricing: **US $1.33 per vCPU (of running worker nodes) per day**:
  - All AKS on Azure Stack HCI and Windows Server deployments include a free 60-day evaluation period
- Includes Linux (CBL-Mariner) Container Hosts:
  - Pricing does not include Windows container hosts as they are licensed separately through regular licensing channels
  - Windows Server Standard: Unlimited Windows containers and two Hyper-V containers
  - Windows Server Datacenter: Unlimited Windows and Hyper-V containers
- Includes Azure Arc-enabled Kubernetes at no extra charge and also the following items:
  - **Inventory, grouping, and tagging** in Azure
  - **Deployment of apps and configurations with GitOps**: Included at no extra charge (normally, the initial six vCPUs are free, and then afterwards, the charge is $2 per vCPU per month)
  - **Azure Policy for Kubernetes**: Included at no extra charge (normally, the charge is $3 per vCPU per cluster for each month)

## Impact of hyper-threading on pricing for AKS 

The AKS on Azure Stack HCI and Windows Server billing unit is a virtual core. If you enable hyper-threading on your physical computer, AKS on Azure Stack HCI and Windows Server will also enable hyper-threading on the worker nodes.  If you enable hyper-threading, it will effectively halve the number of virtual cores needed in each worker node.

![Pricing for A K S is affected by hyper-threading.](media/concepts/hyper-thread-hyperv-manager.png)

##  Pricing for AKS comparison summary

Use the table below to compare pricing for AKS.

> [!NOTE]
> There are additional details on pricing in the section that follows the table.

|Workload cluster configuration| AKS on Azure Stack HCI and Windows Server *with* hyper-threading (most common scenario) | AKS on Azure Stack HCI and Windows Server *without* hyper-threading |   AKS in Azure  |
|-----------------|---|---|---|
|**-2 Worker Nodes <br> -1 x (2 vCPU VM with Linux) <br> -1 x (8 vCPU VM with Windows) <br> -10 vCPUs Total**|~US $200 per month   |~US $400 per month    | ~US $350 per month   |
|**-4 Worker Nodes <br> -2 x (4 vCPU VM with Linux) <br> -2 x (4 vCPU VM with Windows) <br> -16 vCPUs Total**|~US $320 per month   |~US $640 per month    | ~US $561 per month   | 
|**Other information**| Includes Azure Arc enabled Kubernetes. <br> Does not include the cost of hardware, hypervisor, or Windows Server licenses. | Includes Azure Arc enabled Kubernetes. <br> Does not include the cost of hardware, hypervisor, or Windows Server licenses.   | Includes Arc-enabled Kubernetes and the underlying infrastructure. <br> Does not include the cost of running Windows Server on Azure.  | 


### Additional pricing notes

- AKS is consistently priced across on-premises deployment scenarios using either Windows Server or Azure Stack HCI as the host system. 
-	AKS on Azure Stack HCI and Windows Server pricing is based on the US currency list pricing with no discounts applied.
-	Running Windows Server containers on AKS on Azure Stack HCI and Windows Server requires a Windows Server license. The license can be acquired separately through regular licensing channels, or it can be added into the cost of running a Windows virtual machine on Azure. For users with Windows Server Software Assurance, Azure Hybrid benefits may apply, reducing or eliminating the Windows Server license fees.
-	Price assumes hyper-threading is available and enabled on physical systems.
-	Azure Pricing for running workloads on AKS is based on US currency list pricing in the East US region with:
    - pay-as-you-go pricing
    - D-series general purpose VM sizes (D2s v4, D4s V4, and D8s V4)
    - standard HDD
    - no uptime SLA (included in the support level)
-	Monthly price estimates are based on 730 hours of usage. Price assumes that systems are running for the entire month.
