---
title: 트랜잭션(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], about transactions
- transactions [Master Data Services]
ms.assetid: 4cd2fa6f-9c76-4b7a-ae18-d4e5fd2f03f5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c693b550e0c1adb8f5910d99c7125c85f41abb8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740107"
---
# <a name="transactions-master-data-services"></a><span data-ttu-id="ad511-102">트랜잭션(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ad511-102">Transactions (Master Data Services)</span></span>
  <span data-ttu-id="ad511-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 트랜잭션은 멤버에 대해 동작이 수행될 때마다 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a transaction is recorded each time action is taken on a member.</span></span> <span data-ttu-id="ad511-104">트랜잭션은 모든 사용자가 보고 관리자가 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-104">Transactions can be viewed by all users and reversed by administrators.</span></span> <span data-ttu-id="ad511-105">트랜잭션은 동작이 수행된 날짜와 시간, 동작을 수행한 사용자를 그 외 다른 세부 정보와 함께 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-105">Transactions show the date, time, and user who took the action, along with other details.</span></span> <span data-ttu-id="ad511-106">사용자는 트랜잭션에 주석을 추가하여 트랜잭션이 시작된 이유를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-106">Users can add an annotation to a transaction, to indicate why a transaction took place.</span></span>  
  
## <a name="when-transaction-are-recorded"></a><span data-ttu-id="ad511-107">트랜잭션이 기록되는 시기</span><span class="sxs-lookup"><span data-stu-id="ad511-107">When Transaction Are Recorded</span></span>  
 <span data-ttu-id="ad511-108">트랜잭션은 멤버에 대해 다음 동작이 수행될 때 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-108">Transactions are recorded when members:</span></span>  
  
-   <span data-ttu-id="ad511-109">생성, 삭제 또는 다시 활성화될 때</span><span class="sxs-lookup"><span data-stu-id="ad511-109">Are created, deleted, or reactivated.</span></span>  
  
-   <span data-ttu-id="ad511-110">특성 값이 변경될 때</span><span class="sxs-lookup"><span data-stu-id="ad511-110">Have attribute values changed.</span></span>  
  
-   <span data-ttu-id="ad511-111">계층 내에서 이동될 때</span><span class="sxs-lookup"><span data-stu-id="ad511-111">Are moved in a hierarchy.</span></span>  
  
 <span data-ttu-id="ad511-112">비즈니스 규칙에 의해 속성 값이 변경될 때는 트랜잭션이 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-112">Transactions are not recorded when business rules change attribute values.</span></span>  
  
## <a name="view-and-manage-transactions"></a><span data-ttu-id="ad511-113">트랜잭션 보기 및 관리</span><span class="sxs-lookup"><span data-stu-id="ad511-113">View and Manage Transactions</span></span>  
 <span data-ttu-id="ad511-114">**탐색기** 기능 영역에서 직접 만든 트랜잭션을 보고 주석(설명)을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-114">In the **Explorer** functional area, you can view and annotate (add comments to) the transactions that you made yourself.</span></span>  
  
 <span data-ttu-id="ad511-115">관리자는 **버전 관리** 기능 영역에서 액세스 권한을 가지고 있는 모델의 모든 사용자에 대한 모든 트랜잭션을 보고 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-115">In the **Version Management** functional area, administrators can view all transactions for all users for the models they have access to, and reverse any of these transactions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad511-116">관리자는 **버전 관리** 기능 영역에 읽기 전용 권한 수준이 적용되지 않는 한, 모든 사용자의 모든 트랜잭션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-116">Administrators can view all transactions for all users as long as they don't have the read-only permission level applied in the **Version Management** functional area .</span></span> <span data-ttu-id="ad511-117">예를 들어 관리자에 대해 읽기 전용 권한 및 업데이트 권한 수준이 설정된 경우 읽기 전용 권한이 업데이트 권한보다 우선하므로 관리자는 다른 사용자 트랜잭션을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-117">For example, if the read-only permission and update permission level is set for the administrator, the administrator will not be able to see other user transactions because the read-only permission will take precedence over the update permission.</span></span>

## <a name="system-settings"></a><span data-ttu-id="ad511-118">시스템 설정</span><span class="sxs-lookup"><span data-stu-id="ad511-118">System Settings</span></span>  
 <span data-ttu-id="ad511-119">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에는 레코드가 준비될 때 트랜잭션을 기록할지 여부를 결정하는 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-119">There is a setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affects whether or not transactions are recorded when records are staged.</span></span> <span data-ttu-id="ad511-120">이 설정은 SQL Server 2008 R2에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-120">This setting affects SQL Server 2008 R2 only.</span></span> <span data-ttu-id="ad511-121">이 설정은 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에서 조정하거나 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 시스템 설정 테이블에서 직접 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-121">You can adjust this setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="ad511-122">자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](system-settings-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad511-122">For more information, see [System Settings &#40;Master Data Services&#41;](system-settings-master-data-services.md).</span></span>  
  
 <span data-ttu-id="ad511-123">이 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 데이터를 가져올 경우 저장 프로시저를 시작할 때 트랜잭션을 기록할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-123">When importing data in this version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can specify whether or not to log transactions when initiating the stored procedure.</span></span> <span data-ttu-id="ad511-124">자세한 내용은 [준비 저장 프로시저&#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad511-124">For more information, see [Staging Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).</span></span>  
  
## <a name="concurrency"></a><span data-ttu-id="ad511-125">동시성</span><span class="sxs-lookup"><span data-stu-id="ad511-125">Concurrency</span></span>  
 <span data-ttu-id="ad511-126">특정 엔터티 값이 두 개 이상의 탐색기 세션에 동시에 표시될 경우 동일한 값에 대한 동시 편집이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-126">If a particular entity value is shown simultaneously in more than one Explorer session, concurrent edits to the same value are possible.</span></span> <span data-ttu-id="ad511-127">동시 편집은 MDS에서 자동으로 검색되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-127">Concurrent edits will not be detected automatically by MDS.</span></span> <span data-ttu-id="ad511-128">이러한 동작은 여러 사용자가 여러 세션으로부터(예: 여러 컴퓨터, 여러 브라우저 탭 또는 창, 여러 사용자 계정으로부터) 웹 브라우저에서 MDS 탐색기를 사용할 때 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-128">This can occur when multiple users use the MDS Explorer in the Web browser from multiple sessions, for example from multiple computers, multiple browser tabs or windows, or multiple user accounts.</span></span>  
  
 <span data-ttu-id="ad511-129">설정된 트랜잭션에도 불구하고 두 명 이상의 사용자가 오류 없이 동일한 엔터티 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-129">More than one user can update the same entity values without error despite transactions being enabled.</span></span> <span data-ttu-id="ad511-130">일반적으로 시간 시퀀스에서 마지막으로 편집된 값이 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-130">Typically the last edit to the value in a sequence of time will take precedence.</span></span> <span data-ttu-id="ad511-131">중복된 편집 충돌은 트랜잭션 기록에서 수동으로 관측할 수 있으며 관리자가 수동으로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-131">The duplicate edit conflict can be manually observed in the transaction history and can be reversed manually by the administrator.</span></span> <span data-ttu-id="ad511-132">트랜잭션 기록에는 각 세션에서 문제의 특성에 대해 **이전 값** 및 **새 값** 의 개별 트랜잭션이 표시되지만 동일한 이전 값에 대해 여러 **새 값** 이 존재하는 경우 충돌을 자동으로 해결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad511-132">The transaction history will show the individual transactions for the **Prior value** and **New value** for the attribute in question from each session, but will not automatically resolve the conflict when multiple **New Values** exist for the same old value.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ad511-133">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ad511-133">Related Tasks</span></span>  
  
|<span data-ttu-id="ad511-134">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="ad511-134">Task Description</span></span>|<span data-ttu-id="ad511-135">항목</span><span class="sxs-lookup"><span data-stu-id="ad511-135">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ad511-136">트랜잭션을 되돌려 동작을 실행 취소합니다(관리자에만 해당).</span><span class="sxs-lookup"><span data-stu-id="ad511-136">Undo an action by reversing a transaction (administrators only).</span></span>|[<span data-ttu-id="ad511-137">트랜잭션 되돌리기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ad511-137">Reverse a Transaction &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reverse-a-transaction-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="ad511-138">관련 내용</span><span class="sxs-lookup"><span data-stu-id="ad511-138">Related Content</span></span>  
  
-   [<span data-ttu-id="ad511-139">관리자&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ad511-139">Administrators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/administrators-master-data-services.md)  
  
-   [<span data-ttu-id="ad511-140">주석&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ad511-140">Annotations &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/annotations-master-data-services.md)  
  
  
