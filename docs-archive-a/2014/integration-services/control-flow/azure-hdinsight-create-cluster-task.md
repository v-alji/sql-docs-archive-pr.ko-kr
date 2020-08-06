---
title: Azure HDInsight 클러스터 만들기 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpcreatecltask.f1
- sql11.dts.designer.afpcreatecltask.f1
ms.assetid: a8ec413a-38d3-45df-887e-6f5f4d9f8465
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4029e3a01cbcfe04be5f2879a9b60866bfc867a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729711"
---
# <a name="azure-hdinsight-create-cluster-task"></a><span data-ttu-id="b82d2-102">Azure HDInsight 클러스터 만들기 태스크</span><span class="sxs-lookup"><span data-stu-id="b82d2-102">Azure HDInsight Create Cluster Task</span></span>
<span data-ttu-id="b82d2-103">**Azure HDInsight 클러스터 만들기 태스크** 를 사용하면 SSIS 패키지에서 지정된 Azure 구독 및 리소스 그룹에 Azure HDInsight 클러스터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-103">The **Azure HDInsight Create Cluster Task** enables an SSIS package to create an Azure HDInsight cluster in the specified Azure subscription and resource group.</span></span>
  
> [!NOTE]  
> - <span data-ttu-id="b82d2-104">새 HDInsight 클러스터 만들기에는 10~20분이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-104">Creating a new HDInsight cluster may take 10~20 minutes.</span></span>  
> - <span data-ttu-id="b82d2-105">Azure HDInsight 클러스터 만들기 및 실행과 관련하여 비용이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-105">There is a cost associated with creating and running an Azure HDInsight cluster.</span></span> <span data-ttu-id="b82d2-106">자세한 내용은 [HDInsight 가격 책정](https://azure.microsoft.com/pricing/details/hdinsight/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b82d2-106">See [HDInsight Pricing](https://azure.microsoft.com/pricing/details/hdinsight/) for details.</span></span>  
  
<span data-ttu-id="b82d2-107">**Azure HDInsight 클러스터 만들기 태스크**를 추가하려면 해당 태스크를 SSIS 디자이너로 끌어서 놓고 두 번 클릭하거나 마우스 오른쪽 단추를 클릭하고 **편집** 을 클릭하여 다음과 같은 **Azure HDInsight 클러스터 만들기 태스크 편집기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-107">To add an **Azure HDInsight Create Cluster Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Create Cluster Task Editor** dialog box.</span></span>  
  
<span data-ttu-id="b82d2-108">다음 표에서는 이 대화 상자의 필드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-108">The following table provides a description of the fields in this dialog box.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b82d2-109">**필드**</span><span class="sxs-lookup"><span data-stu-id="b82d2-109">**Field**</span></span>|<span data-ttu-id="b82d2-110">**설명**</span><span class="sxs-lookup"><span data-stu-id="b82d2-110">**Description**</span></span>|  
|<span data-ttu-id="b82d2-111">AzureResourceManagerConnection</span><span class="sxs-lookup"><span data-stu-id="b82d2-111">AzureResourceManagerConnection</span></span>|<span data-ttu-id="b82d2-112">기존 Azure Resource Manager 연결 관리자를 선택하거나 HDInsight 클러스터를 만드는 데 사용할 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-112">Select an existing Azure Resource Manager Connection Manager or create a new one that will be used to create the HDInsight cluster.</span></span>|  
|<span data-ttu-id="b82d2-113">AzureStorageConnection</span><span class="sxs-lookup"><span data-stu-id="b82d2-113">AzureStorageConnection</span></span>|<span data-ttu-id="b82d2-114">기존 Azure 스토리지 연결 관리자를 선택하거나 HDInsight 클러스터에 연결할 Azure 스토리지 계정을 참조하는 스토리지 연결 관리자를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-114">Select an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account that will be associated with the HDInsight cluster.</span></span>|
|<span data-ttu-id="b82d2-115">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="b82d2-115">SubscriptionId</span></span>|<span data-ttu-id="b82d2-116">HDInsight 클러스터가 만들어질 구독 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-116">Specify the ID of the subscription the HDInsight cluster will be created in.</span></span>|
|<span data-ttu-id="b82d2-117">ResourceGroup</span><span class="sxs-lookup"><span data-stu-id="b82d2-117">ResourceGroup</span></span>|<span data-ttu-id="b82d2-118">HDInsight 클러스터가 만들어질 Azure 리소스 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-118">Specify the Azure resource group the HDInsight cluster will be created in.</span></span>|
|<span data-ttu-id="b82d2-119">위치</span><span class="sxs-lookup"><span data-stu-id="b82d2-119">Location</span></span>|<span data-ttu-id="b82d2-120">HDInsight 클러스터의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-120">Specify the location of the HDInsight cluster.</span></span> <span data-ttu-id="b82d2-121">Azure Storage 계정과 동일한 위치에 클러스터를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-121">The cluster must be created in the same location as the Azure Storage Account specified.</span></span>|  
|<span data-ttu-id="b82d2-122">ClusterName</span><span class="sxs-lookup"><span data-stu-id="b82d2-122">ClusterName</span></span>|<span data-ttu-id="b82d2-123">만들 HDInsight 클러스터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-123">Specify a name for the HDInsight cluster to be created.</span></span>|  
|<span data-ttu-id="b82d2-124">clusterSize</span><span class="sxs-lookup"><span data-stu-id="b82d2-124">ClusterSize</span></span>|<span data-ttu-id="b82d2-125">클러스터에 만들 노드의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-125">Specify the number of nodes to create in the cluster.</span></span>|  
|<span data-ttu-id="b82d2-126">BlobContainer</span><span class="sxs-lookup"><span data-stu-id="b82d2-126">BlobContainer</span></span>|<span data-ttu-id="b82d2-127">HDInsight 클러스터와 연결될 기본 스토리지 컨테이너의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-127">Specify the name of the default storage container to be associated with the HDInsight cluster.</span></span>|  
|<span data-ttu-id="b82d2-128">UserName</span><span class="sxs-lookup"><span data-stu-id="b82d2-128">UserName</span></span>|<span data-ttu-id="b82d2-129">HDInsight 클러스터에 연결하는 데 사용할 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-129">Specify the user name to be used for connecting to the HDInsight cluster.</span></span>|  
|<span data-ttu-id="b82d2-130">암호</span><span class="sxs-lookup"><span data-stu-id="b82d2-130">Password</span></span>|<span data-ttu-id="b82d2-131">HDInsight 클러스터에 연결하는 데 사용할 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-131">Specify the password to be used for connecting to the HDInsight cluster.</span></span>|
|<span data-ttu-id="b82d2-132">SshUserName</span><span class="sxs-lookup"><span data-stu-id="b82d2-132">SshUserName</span></span>|<span data-ttu-id="b82d2-133">SSH를 사용하여 HDInsight 클러스터에 원격으로 액세스하는 데 사용할 사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-133">Specify the user name used to remotely access the HDInsight cluster using SSH.</span></span>|
|<span data-ttu-id="b82d2-134">SshPassword</span><span class="sxs-lookup"><span data-stu-id="b82d2-134">SshPassword</span></span>|<span data-ttu-id="b82d2-135">SSH를 사용하여 HDInsight 클러스터에 원격으로 액세스하는 데 사용할 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-135">Specify the password used to remotely access the HDInsight cluster using SSH.</span></span>|
|<span data-ttu-id="b82d2-136">FailIfExists</span><span class="sxs-lookup"><span data-stu-id="b82d2-136">FailIfExists</span></span>|<span data-ttu-id="b82d2-137">클러스터가 이미 있는 경우 태스크가 실패하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-137">Specify whether the task should fail if the cluster already exists.</span></span>|  
  
> [!NOTE]  
> <span data-ttu-id="b82d2-138">HDInsight 클러스터와 Azure Storage 계정의 위치는 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b82d2-138">The locations of the HDInsight cluster and the Azure Storage Account must be the same.</span></span>
