---
title: Azure HDInsight 클러스터 삭제 작업 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpdelcltask.f1
- sql11.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: chugugrace
ms.author: chugu
ms.openlocfilehash: db0a15aaea37c6d18c1d3c2136e0fd0c94eb7506
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659600"
---
# <a name="azure-hdinsight-delete-cluster-task"></a><span data-ttu-id="5d608-102">Azure HDInsight 클러스터 삭제 작업</span><span class="sxs-lookup"><span data-stu-id="5d608-102">Azure HDInsight Delete Cluster Task</span></span>
<span data-ttu-id="5d608-103">**Azure HDInsight 클러스터 삭제 작업**을 사용하면 SSIS 패키지에서 지정된 Azure 구독 및 리소스 그룹의 Azure HDInsight 클러스터를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d608-103">The **Azure HDInsight Delete Cluster Task** enables an SSIS package to delete an Azure HDInsight cluster in the specified Azure subscription and resource group.</span></span>
  
> [!NOTE]
> <span data-ttu-id="5d608-104">HDInsight 클러스터 삭제에는 10~20분이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="5d608-104">Deleting an HDInsight cluster may take 10~20 minutes.</span></span>  
  
<span data-ttu-id="5d608-105">**Azure HDInsight 클러스터 삭제 작업**을 추가하려면 작업을 SSIS 디자이너로 끌어다 놓고 두 번 클릭하거나 **편집** 을 클릭하여 다음과 같은 **Azure HDInsight 클러스터 삭제 작업 편집기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d608-105">To add an **Azure HDInsight Delete Cluster Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Delete Cluster Task Editor** dialog box.</span></span>  
  
<span data-ttu-id="5d608-106">다음 표에서는 대화 상자의 필드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5d608-106">The following table provides a description for the fields in the dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d608-107">**필드**</span><span class="sxs-lookup"><span data-stu-id="5d608-107">**Field**</span></span>|<span data-ttu-id="5d608-108">**설명**</span><span class="sxs-lookup"><span data-stu-id="5d608-108">**Description**</span></span>|  
|<span data-ttu-id="5d608-109">AzureResourceManagerConnection</span><span class="sxs-lookup"><span data-stu-id="5d608-109">AzureResourceManagerConnection</span></span>|<span data-ttu-id="5d608-110">기존 Azure Resource Manager 연결 관리자를 선택하거나 HDInsight 클러스터를 삭제하는 데 사용할 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5d608-110">Select an existing Azure Resource Manager Connection Manager or create a new one that will be used to delete the HDInsight cluster.</span></span>|
|<span data-ttu-id="5d608-111">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="5d608-111">SubscriptionId</span></span>|<span data-ttu-id="5d608-112">HDInsight 클러스터가 있는 구독 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d608-112">Specify the ID of the subscription the HDInsight cluster is in.</span></span>|
|<span data-ttu-id="5d608-113">ResourceGroup</span><span class="sxs-lookup"><span data-stu-id="5d608-113">ResourceGroup</span></span>|<span data-ttu-id="5d608-114">HDInsight 클러스터가 있는 Azure 리소스 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d608-114">Specify the Azure resource group the HDInsight cluster is in.</span></span>|
|<span data-ttu-id="5d608-115">ClusterName</span><span class="sxs-lookup"><span data-stu-id="5d608-115">ClusterName</span></span>|<span data-ttu-id="5d608-116">삭제할 클러스터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d608-116">Specify the name of the cluster to be deleted.</span></span>|  
|<span data-ttu-id="5d608-117">FailIfNotExists</span><span class="sxs-lookup"><span data-stu-id="5d608-117">FailIfNotExists</span></span>|<span data-ttu-id="5d608-118">클러스터가 없는 경우 작업이 실패하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d608-118">Specify whether the task should fail if the cluster does not exist.</span></span>|
