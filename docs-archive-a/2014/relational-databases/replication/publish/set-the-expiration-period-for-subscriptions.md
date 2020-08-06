---
title: 구독에 대한 만료 기간 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], expiration
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- deactivating subscriptions
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc0ecb449af64b88cf3ded032c78c2e399dd4234
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651645"
---
# <a name="set-the-expiration-period-for-subscriptions"></a><span data-ttu-id="08c8b-102">구독에 대한 만료 기간 설정</span><span class="sxs-lookup"><span data-stu-id="08c8b-102">Set the Expiration Period for Subscriptions</span></span>
  <span data-ttu-id="08c8b-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 구독 만료 기간을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-103">This topic describes how to set the expiration period for subscriptions in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="08c8b-104">구독 만료 기간은 구독이 만료되어 제거되기 전까지 유효한 기간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-104">The expiration period for subscriptions determines the period of time before a subscription expires and is removed.</span></span> <span data-ttu-id="08c8b-105">자세한 내용은 [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08c8b-105">For more information, see [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="08c8b-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="08c8b-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="08c8b-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="08c8b-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="08c8b-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="08c8b-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="08c8b-109">**다음을 사용하여 구독에 대한 만료 기간을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="08c8b-109">**To set the expiration period for subscriptions, using:**</span></span>  
  
     [<span data-ttu-id="08c8b-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="08c8b-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="08c8b-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="08c8b-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="08c8b-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="08c8b-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="08c8b-113">권장 사항</span><span class="sxs-lookup"><span data-stu-id="08c8b-113">Recommendations</span></span>  
  
-   <span data-ttu-id="08c8b-114">구독 만료 기간을 *게시 보존 기간*이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-114">The subscription expiration period is also referred to as the *publication retention period*.</span></span> <span data-ttu-id="08c8b-115">병합 복제 메타데이터의 정리는 다음과 같이 이 설정의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-115">Cleanup of merge replication metadata is dependent on this setting:</span></span>  
  
    -   <span data-ttu-id="08c8b-116">보존 기간에 도달하기 전까지는 복제 작업을 통해 게시 및 구독 데이터베이스의 메타데이터를 정리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-116">Replication cannot clean up metadata in the publication and subscription databases until the retention period is reached.</span></span> <span data-ttu-id="08c8b-117">보존 기간을 너무 길게 설정하면 복제 성능이 저하될 수 있으므로 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-117">Use caution in specifying a high value for the retention period, because it can negatively impact replication performance.</span></span> <span data-ttu-id="08c8b-118">보존 기간 내에 모든 구독자가 정기적으로 동기화될 가능성이 있으면 보존 기간을 낮은 값으로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-118">It is recommended that you use a lower setting if you can reliably predict that all Subscribers will synchronize regularly within that time period.</span></span>  
  
         <span data-ttu-id="08c8b-119">병합 게시의 보존 기간은 다양한 표준 시간대의 구독자를 수용하기 위해 24시간의 유예 기간을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-119">The retention period for merge publications has a 24-hour grace period to accommodate Subscribers in different time zones.</span></span> <span data-ttu-id="08c8b-120">예를 들어 보존 기간을 하루로 설정한 경우 실제 보존 기간은 48시간이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-120">If, for example, you set a retention period of one day, the actual retention period is 48 hours.</span></span>  
  
    -   <span data-ttu-id="08c8b-121">구독이 만료되지 않도록 지정할 수 있지만 이 경우 메타데이터를 정리할 수 없으므로 이 값은 사용하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-121">It is possible to specify that subscriptions never expire, but it is strongly recommended that you do not use this value, because metadata cannot be cleaned up.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="08c8b-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="08c8b-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="08c8b-123">**게시 속성 - \<Publication>** 대화 상자의 **일반** 페이지에서 구독의 만료 기간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-123">Set the expiration period for subscriptions on the **General** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="08c8b-124">이 대화 상자에 액세스하는 방법은 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08c8b-124">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-set-the-expiration-period-for-subscriptions"></a><span data-ttu-id="08c8b-125">구독에 대한 만료 기간을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="08c8b-125">To set the expiration period for subscriptions</span></span>  
  
1.  <span data-ttu-id="08c8b-126">**게시 속성 - \<Publication>** 대화 상자의 **일반** 페이지에 있는 **구독 만료** 섹션에서 구독을 만료해야 할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-126">In the **Subscription expiration** section on the **General** page of the **Publication Properties - \<Publication>** dialog box, specify whether subscriptions should expire.</span></span>  
  
2.  <span data-ttu-id="08c8b-127">구독이 만료되어야 하는 경우 만료 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-127">If they should expire, specify an expiration time period.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="08c8b-128">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="08c8b-128">Using Transact-SQL</span></span>  
 <span data-ttu-id="08c8b-129">복제 저장 프로시저를 사용하여 게시를 만들 때 이 값을 설정하거나 나중에 이 값을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-129">You can use replication stored procedures to either set this value when a publication is created or modify this value at a later time.</span></span>  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="08c8b-130">스냅샷 또는 트랜잭션 게시에 대한 구독 만료 기간을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="08c8b-130">To set the expiration period for a subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="08c8b-131">게시자에서 [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-131">At the Publisher, execute [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span> <span data-ttu-id="08c8b-132">이때 **\@retention**에 원하는 구독 만료 기간(시간)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-132">Specify the desired subscription expiration period, in hours, for **\@retention**.</span></span> <span data-ttu-id="08c8b-133">기본 만료 기간은 336시간입니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-133">The default expiration period is 336 hours.</span></span> <span data-ttu-id="08c8b-134">자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08c8b-134">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-merge-publication"></a><span data-ttu-id="08c8b-135">병합 게시에 대한 구독 만료 기간을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="08c8b-135">To set the expiration period for a subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="08c8b-136">게시자에서 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-136">At the Publisher, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="08c8b-137">이때 **\@retention**에 원하는 구독 만료 기간 값을 지정하고</span><span class="sxs-lookup"><span data-stu-id="08c8b-137">Specify the desired value for the subscription expiration period for **\@retention**.</span></span> <span data-ttu-id="08c8b-138">**\@retention_period_unit**에 다음과 같은 만료 기간 표현 단위 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-138">Specify the units in which the expiration period is expressed for **\@retention_period_unit**, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="08c8b-139">**1** = 주</span><span class="sxs-lookup"><span data-stu-id="08c8b-139">**1** = week</span></span>  
  
    -   <span data-ttu-id="08c8b-140">**2** = 개월</span><span class="sxs-lookup"><span data-stu-id="08c8b-140">**2** = month</span></span>  
  
    -   <span data-ttu-id="08c8b-141">**3** = 년</span><span class="sxs-lookup"><span data-stu-id="08c8b-141">**3** = year</span></span>  
  
     <span data-ttu-id="08c8b-142">기본 만료 기간은 14일입니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-142">The default expiration period is 14 days.</span></span> <span data-ttu-id="08c8b-143">자세한 내용은 [게시 만들기](create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="08c8b-143">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="08c8b-144">스냅샷 또는 트랜잭션 게시에 대한 구독 만료 기간을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="08c8b-144">To change the expiration period for a subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="08c8b-145">게시자에서 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-145">At the Publisher, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span> <span data-ttu-id="08c8b-146">이때 **\@property**에 **retention** , **\@value**에 새 구독 만료 기간(시간)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-146">Specify **retention** for **\@property** and the new subscription expiration period, in hours, for **\@value**.</span></span>  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-merge-publication"></a><span data-ttu-id="08c8b-147">병합 게시에 대한 구독의 만료 기간을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="08c8b-147">To change the expiration period for a subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="08c8b-148">게시자에서 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)을 실행하고 **\@publication** 및 **\@publisher**를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-148">At the Publisher, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying **\@publication** and **\@publisher**.</span></span> <span data-ttu-id="08c8b-149">결과 집합의 **retention_period_unit** 값은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-149">Note the value of **retention_period_unit** in the result set, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="08c8b-150">**0** = 일</span><span class="sxs-lookup"><span data-stu-id="08c8b-150">**0** = day</span></span>  
  
    -   <span data-ttu-id="08c8b-151">**1** = 주</span><span class="sxs-lookup"><span data-stu-id="08c8b-151">**1** = week</span></span>  
  
    -   <span data-ttu-id="08c8b-152">**2** = 개월</span><span class="sxs-lookup"><span data-stu-id="08c8b-152">**2** = month</span></span>  
  
    -   <span data-ttu-id="08c8b-153">**3** = 년</span><span class="sxs-lookup"><span data-stu-id="08c8b-153">**3** = year</span></span>  
  
2.  <span data-ttu-id="08c8b-154">게시자에서 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-154">At the Publisher, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="08c8b-155">이때 **\@property**에 **retention**을 지정하고 **\@value**에 1단계에서 만든 보존 기간 단위에 따라 텍스트로 새 구독 만료 기간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-155">Specify **retention** for **\@property** and the new subscription expiration period, as text based on the retention period unit from step 1, for **\@value**.</span></span>  
  
3.  <span data-ttu-id="08c8b-156">(옵션) 게시자에서 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-156">(Optional) At the Publisher, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="08c8b-157">이때 **\@property**에 **retention_period_unit**을 지정하고 **\@value**에 구독 만료 기간의 새 단위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08c8b-157">Specify **retention_period_unit** for **\@property** and a new unit for the subscription expiration period for **\@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c8b-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08c8b-158">See Also</span></span>  
 <span data-ttu-id="08c8b-159">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="08c8b-159">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="08c8b-160">구독 만료 및 비활성화</span><span class="sxs-lookup"><span data-stu-id="08c8b-160">Subscription Expiration and Deactivation</span></span>](../subscription-expiration-and-deactivation.md)  
  
  
