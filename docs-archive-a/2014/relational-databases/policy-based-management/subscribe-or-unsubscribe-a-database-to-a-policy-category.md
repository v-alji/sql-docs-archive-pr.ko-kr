---
title: 정책 범주에 데이터베이스 구독 또는 구독 취소 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.groupsubscription.f1
ms.assetid: d2c31769-7098-428e-ad9c-ef56541b7c52
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2b4ca6f804352b57b30b42012da93e0d031be8d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731511"
---
# <a name="subscribe-or-unsubscribe-a-database--to-a-policy-category"></a><span data-ttu-id="5b563-102">정책 범주에 데이터베이스 구독 또는 구독 취소</span><span class="sxs-lookup"><span data-stu-id="5b563-102">Subscribe or Unsubscribe a Database  to a Policy Category</span></span>
  <span data-ttu-id="5b563-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터베이스에 정책 범주를 구독하거나 구독 취소하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-103">This topic describes how to subscribe or unsubscribe a database to a policy category.in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="5b563-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="5b563-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5b563-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5b563-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5b563-106">보안</span><span class="sxs-lookup"><span data-stu-id="5b563-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5b563-107">**다음을 사용하여 데이터베이스에 정책 범주를 구독하거나 구독 취소하려면**</span><span class="sxs-lookup"><span data-stu-id="5b563-107">**To subscribe or unsubscribe a database to a policy category., using:**</span></span>  
  
     [<span data-ttu-id="5b563-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5b563-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5b563-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5b563-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5b563-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5b563-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5b563-111">보안</span><span class="sxs-lookup"><span data-stu-id="5b563-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5b563-112">권한</span><span class="sxs-lookup"><span data-stu-id="5b563-112">Permissions</span></span>  
 <span data-ttu-id="5b563-113">db_owner 고정 데이터베이스 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-113">Requires membership in the db_owner fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5b563-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="5b563-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-subscribe-or-unsubscribe-a-database-to-a-policy-category"></a><span data-ttu-id="5b563-115">데이터베이스에 정책 범주를 구독하거나 구독 취소하려면</span><span class="sxs-lookup"><span data-stu-id="5b563-115">To subscribe or unsubscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="5b563-116">**개체 탐색기**에서 더하기 기호를 클릭하여 범주 구독을 관리할 데이터베이스를 포함하는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-116">In **Object Explorer**, click the plus sign to expand the server that contains the database wherein you want to manage category subscriptions.</span></span>  
  
2.  <span data-ttu-id="5b563-117">더하기 기호를 클릭하여 **데이터베이스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-117">Click the plus sign to expand the **Databases** folder.</span></span>  
  
3.  <span data-ttu-id="5b563-118">범주 구독을 관리할 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **정책**을 가리킨 다음 **범주**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-118">Right-click the database wherein you want to manage category subscriptions, point to **Policies**, and select **Categories**</span></span>  
  
     <span data-ttu-id="5b563-119">**범주** 대화 상자에서 사용 가능한 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-119">The following options are available in the **Categories** dialog box:</span></span>  
  
     <span data-ttu-id="5b563-120">열 확장</span><span class="sxs-lookup"><span data-stu-id="5b563-120">Expand column</span></span>  
     <span data-ttu-id="5b563-121">정책 범주를 확장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-121">Click to expand a policy category.</span></span> <span data-ttu-id="5b563-122">그러면 범주에 포함된 모든 정책이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-122">This lists all the policies that are included in the category.</span></span>  
  
     <span data-ttu-id="5b563-123">**이름**</span><span class="sxs-lookup"><span data-stu-id="5b563-123">**Name**</span></span>  
     <span data-ttu-id="5b563-124">정책 범주의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-124">The name of the policy category.</span></span>  
  
     <span data-ttu-id="5b563-125">**구독**</span><span class="sxs-lookup"><span data-stu-id="5b563-125">**Subscribed**</span></span>  
     <span data-ttu-id="5b563-126">대상이 정책 범주로 구독되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-126">Indicates whether the target has subscribed to the policy category.</span></span> <span data-ttu-id="5b563-127">이 확인란을 해제하면 **데이터베이스 구독 위임**에 대한 정책 범주가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-127">If this check box is disabled, the policy category is set for **Mandate Database Subscriptions**.</span></span> <span data-ttu-id="5b563-128">즉, 서버의 모든 데이터베이스에 정책 범주가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-128">This means that the policy category applies to all databases on the server.</span></span>  
  
     <span data-ttu-id="5b563-129">**정책**</span><span class="sxs-lookup"><span data-stu-id="5b563-129">**Policy**</span></span>  
     <span data-ttu-id="5b563-130">정책 그룹이 확장되면 정책 범주의 정책이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-130">When policy groups are expanded, displays the policies in the policy category.</span></span>  
  
     <span data-ttu-id="5b563-131">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="5b563-131">**Enabled**</span></span>  
     <span data-ttu-id="5b563-132">정책의 사용 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-132">Indicates whether the policies are enabled or disabled.</span></span>  
  
     <span data-ttu-id="5b563-133">**실행 모드**</span><span class="sxs-lookup"><span data-stu-id="5b563-133">**Execution Mode**</span></span>  
     <span data-ttu-id="5b563-134">정책의 실행 모드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-134">Displays the execution mode of the policy.</span></span>  
  
     <span data-ttu-id="5b563-135">**History**</span><span class="sxs-lookup"><span data-stu-id="5b563-135">**History**</span></span>  
     <span data-ttu-id="5b563-136">로그 파일 뷰어를 열어 정책 기록을 보려면 기록 보기 하이퍼링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-136">Click the View History hyperlink to open the Log File Viewer to see the policy history.</span></span>  
  
4.  <span data-ttu-id="5b563-137">정책 기반 관리 범주를 구독하려면 **가입** 열 아래의 범주 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-137">To subscribe to a Policy-Based Management category, select the category's check box under the **Subscribed** column.</span></span> <span data-ttu-id="5b563-138">범주에서 구독을 취소하려면 해당 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-138">To unsubscribe from a category, clear the check box.</span></span>  
  
5.  <span data-ttu-id="5b563-139">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-139">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5b563-140">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="5b563-140">Using Transact-SQL</span></span>  
  
#### <a name="to-subscribe-a-database-to-a-policy-category"></a><span data-ttu-id="5b563-141">데이터베이스에 정책 범주를 구독하려면</span><span class="sxs-lookup"><span data-stu-id="5b563-141">To subscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="5b563-142">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5b563-143">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5b563-144">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    -- Adds a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_subscribe_to_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 <span data-ttu-id="5b563-145">자세한 내용은 [sp_syspolicy_subscribe_to_policy_category&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b563-145">For more information, see [sp_syspolicy_subscribe_to_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql).</span></span>  
  
#### <a name="to-unsubscribe-a-database-to-a-policy-category"></a><span data-ttu-id="5b563-146">데이터베이스에서 정책 범주를 구독 취소하려면</span><span class="sxs-lookup"><span data-stu-id="5b563-146">To unsubscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="5b563-147">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-147">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5b563-148">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-148">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5b563-149">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b563-149">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    -- Deletes a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_unsubscribe_from_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 <span data-ttu-id="5b563-150">자세한 내용은 [sp_syspolicy_unsubscribe_from_policy_category&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b563-150">For more information, see [sp_syspolicy_unsubscribe_from_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql).</span></span>  
  
  
