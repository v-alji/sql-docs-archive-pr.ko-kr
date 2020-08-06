---
title: 리소스 관리자 작업 그룹 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group
- workload groups [SQL Server]
- workload groups [SQL Server], overview
ms.assetid: a84c3c3f-55b6-4a30-9c42-13f082d9281e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c6fa8f6fe960571f10d6a8505329fbe8f400e6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731459"
---
# <a name="resource-governor-workload-group"></a><span data-ttu-id="7381e-102">리소스 관리자 작업 그룹</span><span class="sxs-lookup"><span data-stu-id="7381e-102">Resource Governor Workload Group</span></span>
  <span data-ttu-id="7381e-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스 관리자에서 작업 그룹은 분류 기준이 유사한 세션 요청에 대한 컨테이너의 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-103">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resource Governor, a workload group serves as a container for session requests that have similar classification criteria.</span></span> <span data-ttu-id="7381e-104">작업 그룹을 사용하면 세션의 집계 모니터링이 가능하며 작업 그룹으로 세션의 정책을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-104">A workload allows for aggregate monitoring of the sessions, and defines policies for the sessions.</span></span> <span data-ttu-id="7381e-105">각 작업 그룹은 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스의 물리적 리소스의 하위 집합을 나타내는 리소스 풀에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-105">Each workload group is in a resource pool, which represents a subset of the physical resources of an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="7381e-106">세션이 시작되면 리소스 관리자 분류자가 세션을 특정 작업 그룹에 할당하고, 세션은 작업 그룹에 할당된 정책 및 리소스 풀에 정의된 리소스를 사용하여 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-106">When a session is started, the Resource Governor classifier assigns the session to a specific workload group, and the session must run using the policies assigned to the workload group and the resources defined for the resource pool.</span></span>  
  
## <a name="workload-group-concepts"></a><span data-ttu-id="7381e-107">작업 그룹 개념</span><span class="sxs-lookup"><span data-stu-id="7381e-107">Workload Group Concepts</span></span>  
 <span data-ttu-id="7381e-108">작업 그룹은 각 요청에 적용되는 분류 조건에 따라 유사한 세션 요청의 컨테이너 역할을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-108">A workload group serves as a container for session requests that are similar according to the classification criteria that are applied to each request.</span></span> <span data-ttu-id="7381e-109">작업 그룹을 사용하면 리소스 소비에 대해 집계 모니터링을 수행하고 그룹에 있는 모든 요청에 단일 정책을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-109">A workload group allows the aggregate monitoring of resource consumption and the application of a uniform policy to all the requests in the group.</span></span> <span data-ttu-id="7381e-110">그룹은 해당 멤버에 대한 정책을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-110">A group defines the policies for its members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7381e-111">사용자 정의 작업 그룹은 한 리소스 풀에서 다른 리소스 풀로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-111">User-defined workload groups can be moved from one resource pool to another.</span></span>  
  
 <span data-ttu-id="7381e-112">리소스 관리자는 내부 그룹과 기본 그룹이라는 두 개의 작업 그룹을 미리 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-112">Resource Governor predefines two workload groups: the internal group and the default group.</span></span> <span data-ttu-id="7381e-113">사용자는 내부 그룹으로 분류된 그룹을 변경할 수 없지만 모니터링은 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-113">A user cannot change anything classified as an internal group, but can monitor it.</span></span> <span data-ttu-id="7381e-114">다음 조건에 해당하는 경우 요청은 기본 그룹으로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-114">Requests are classified into the default group when the following conditions exist:</span></span>  
  
-   <span data-ttu-id="7381e-115">요청을 분류할 조건이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-115">There are no criteria to classify a request.</span></span>  
  
-   <span data-ttu-id="7381e-116">존재하지 않는 그룹으로 요청을 분류하려는 시도가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-116">There is an attempt to classify the request into a non-existent group.</span></span>  
  
-   <span data-ttu-id="7381e-117">일반 분류 실패가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-117">There is a general classification failure.</span></span>  
  
 <span data-ttu-id="7381e-118">리소스 관리자는 작업 그룹을 생성, 변경 및 삭제하는 DDL 문도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-118">Resource Governor also provides DDL statements for creating, changing, and dropping workload groups.</span></span>  
  
## <a name="workload-group-tasks"></a><span data-ttu-id="7381e-119">작업 그룹 태스크</span><span class="sxs-lookup"><span data-stu-id="7381e-119">Workload Group Tasks</span></span>  
  
|<span data-ttu-id="7381e-120">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="7381e-120">Task Description</span></span>|<span data-ttu-id="7381e-121">항목</span><span class="sxs-lookup"><span data-stu-id="7381e-121">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="7381e-122">작업 그룹을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-122">Describes how to create a workload group.</span></span>|[<span data-ttu-id="7381e-123">작업 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="7381e-123">Create a Workload Group</span></span>](create-a-workload-group.md)|  
|<span data-ttu-id="7381e-124">작업 그룹을 설정을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-124">Describes how to change workload group settings.</span></span>|[<span data-ttu-id="7381e-125">작업 그룹 설정 변경</span><span class="sxs-lookup"><span data-stu-id="7381e-125">Change Workload Group Settings</span></span>](change-workload-group-settings.md)|  
|<span data-ttu-id="7381e-126">작업 그룹을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7381e-126">Describes how to delete a workload group.</span></span>|[<span data-ttu-id="7381e-127">작업 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="7381e-127">Delete a Workload Group</span></span>](delete-a-workload-group.md)|  
  
## <a name="see-also"></a><span data-ttu-id="7381e-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7381e-128">See Also</span></span>  
 <span data-ttu-id="7381e-129">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="7381e-129">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="7381e-130">[리소스 관리자 사용](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="7381e-130">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="7381e-131">[리소스 관리자 리소스 풀](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="7381e-131">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="7381e-132">[리소스 관리자 분류자 함수](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="7381e-132">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="7381e-133">[템플릿을 사용하여 리소스 관리자 구성](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="7381e-133">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 [<span data-ttu-id="7381e-134">리소스 관리자 속성 보기</span><span class="sxs-lookup"><span data-stu-id="7381e-134">View Resource Governor Properties</span></span>](view-resource-governor-properties.md)  
  
  
