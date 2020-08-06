---
title: SQL Server 속성 (AlwaysOn 고가용성 탭) | Microsoft Docs
description: 2014 SQL Server에서 AlwaysOn 가용성 그룹 기능을 설정 하거나 해제 하는 방법에 대해 알아봅니다. 서버 인스턴스가이 기능에 대해 충족 해야 하는 필수 구성 요소를 확인 합니다.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d8630923-a600-4f1c-aca1-027453a3ec82
author: mikeraymsft
ms.author: mikeray
ms.openlocfilehash: 3939b40a334746e9ee96441338e2e50791987103
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734827"
---
# <a name="sql-server-properties-alwayson-high-availability-tab"></a><span data-ttu-id="13aa0-104">SQL Server 속성(AlwaysOn 고가용성 탭)</span><span class="sxs-lookup"><span data-stu-id="13aa0-104">SQL Server Properties (AlwaysOn High Availability Tab)</span></span>
  <span data-ttu-id="13aa0-105">\*\*\*\* 구성 관리자에서 **SQL Server 속성** 대화 상자의 AlwaysOn 고가용성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 탭을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 AlwaysOn 가용성 그룹 기능을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-105">Use the **AlwaysOn High Availability** tab of the **SQL Server Properties** dialog box in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to enable or disable the AlwaysOn Availability Groups feature in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="13aa0-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 고가용성 및 재해 복구 솔루션으로 가용성 그룹을 사용하려면 먼저 AlwaysOn 가용성 그룹을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-106">Enabling AlwaysOn Availability Groups is a prerequisite for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use availability groups as a high availability and disaster recovery solution.</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="13aa0-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="13aa0-107">Prerequisites</span></span>  
 <span data-ttu-id="13aa0-108">AlwaysOn 가용성 그룹을 사용하도록 설정하려면 서버 인스턴스가 다음과 같은 사전 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-108">To be enabled for AlwaysOn Availability Groups, a server instance must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="13aa0-109">서버 인스턴스는 WSFC(Windows Server 장애 조치(failover) 클러스터링) 노드에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-109">The server instance must reside on a Windows Server Failover Clustering (WSFC) node.</span></span>  
  
-   <span data-ttu-id="13aa0-110">동일한 가용성 그룹에 있으려면 인스턴스가 동일한 WSFC 클러스터에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-110">To be in the same availability group, instances must be in the same WSFC cluster.</span></span> <span data-ttu-id="13aa0-111">가용성 그룹은 여러 WSFC 클러스터에 걸쳐 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-111">An availability group cannot span WSFC clusters.</span></span>  
  
-   <span data-ttu-id="13aa0-112">서버 인스턴스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 지원하는 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]버전을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-112">The server instance must be running an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
-   <span data-ttu-id="13aa0-113">한 번에 한 서버 인스턴스에 대해서만 AlwaysOn 가용성 그룹을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-113">Enable AlwaysOn Availability Groups for only one server instance at a time.</span></span> <span data-ttu-id="13aa0-114">AlwaysOn 가용성 그룹을 사용하도록 설정한 후에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 다시 시작될 때까지 기다렸다가 다음 서버 인스턴스를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-114">After enabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service has restarted before you enable the next server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13aa0-115">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]에 대한 기능 지원과 추가 사전 요구 사항, 제한 사항 및 권장 사항에 대한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 온라인 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13aa0-115">For information about feature support and for information about additional prerequisites, restrictions, and recommendations for [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
## <a name="dialog-options"></a><span data-ttu-id="13aa0-116">대화 상자 옵션</span><span class="sxs-lookup"><span data-stu-id="13aa0-116">Dialog Options</span></span>  
 <span data-ttu-id="13aa0-117">**Windows 장애 조치(failover) 클러스터 이름**</span><span class="sxs-lookup"><span data-stu-id="13aa0-117">**Windows failover cluster name**</span></span>  
 <span data-ttu-id="13aa0-118">로컬 컴퓨터가 노드인 WSFC 클러스터의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-118">Displays the name of the WSFC cluster in which the local computer is a node.</span></span>  
  
 <span data-ttu-id="13aa0-119">**AlwaysOn 가용성 그룹 사용**</span><span class="sxs-lookup"><span data-stu-id="13aa0-119">**Enable AlwaysOn Availability Groups**</span></span>  
 <span data-ttu-id="13aa0-120">다음과 같이 해당 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 AlwaysOn 가용성 그룹을 사용하거나 사용하지 않도록 설정하려면 이 확인란을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-120">Use this check box to enable or disable AlwaysOn Availability Groups on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], as follows:</span></span>  
  
-   <span data-ttu-id="13aa0-121">이 확인란이 비어 있으면 현재 AlwaysOn 가용성 그룹을 사용하지 않도록 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-121">If this check box is empty, AlwaysOn Availability Groups is currently disabled.</span></span> <span data-ttu-id="13aa0-122">AlwaysOn 가용성 그룹을 사용하도록 설정하려면 이 확인란을 선택하고 **확인**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 수동으로 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-122">To enable AlwaysOn Availability Groups, select this check box, click **OK**, and manually restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="13aa0-123">이 확인란이 이미 선택되어 있으면 현재 AlwaysOn 가용성 그룹을 사용하도록 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-123">If this check box is already selected, AlwaysOn Availability Groups is currently enabled.</span></span> <span data-ttu-id="13aa0-124">AlwaysOn 가용성 그룹을 사용하지 않도록 설정하려면 이 확인란의 선택을 취소하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-124">To disable AlwaysOn Availability Groups, uncheck the check box and click **OK**.</span></span> <span data-ttu-id="13aa0-125">이렇게 하면 서버 인스턴스가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-125">This causes the server instance to restart.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="13aa0-126">AlwaysOn 가용성 그룹을 사용하지 않도록 설정한 후 서버 인스턴스에서 모든 로컬 가용성 복제본을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-126">After disabling AlwaysOn Availability Groups, you should remove any local availability replicas from the server instance.</span></span> <span data-ttu-id="13aa0-127">지정된 가용성 그룹의 마지막 복제본을 제거하는 경우 그룹도 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13aa0-127">If you remove the last replica of a given availability group, you should also remove the group.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="13aa0-128">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="13aa0-128">UI element list</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13aa0-129">AlwaysOn 가용성 그룹을 사용하지 않도록 설정한 후의 후속 작업과 가용성 그룹을 만들고 구성하는 방법에 대한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="13aa0-129">For more information about follow up after you disable AlwaysOn Availability Groups and for information about how to create and configure availability groups, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
  
