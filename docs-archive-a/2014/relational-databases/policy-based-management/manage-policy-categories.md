---
title: 정책 범주 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.policycategories.f1
ms.assetid: d188a819-731f-4029-98aa-780d3299a0ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 168d05dd88286263da1dca5456a2c6072e946786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649000"
---
# <a name="manage-policy-categories"></a><span data-ttu-id="8ad5a-102">정책 범주 관리</span><span class="sxs-lookup"><span data-stu-id="8ad5a-102">Manage Policy Categories</span></span>
  <span data-ttu-id="8ad5a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 전체 [!INCLUDE[tsql](../../includes/tsql-md.md)]인스턴스에 한 범주의 사용 가능한 정책을 임의로 또는 모두 적용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-103">This topic describes how to apply any or all available policies in a category to the whole instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8ad5a-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="8ad5a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8ad5a-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="8ad5a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8ad5a-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8ad5a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8ad5a-107">보안</span><span class="sxs-lookup"><span data-stu-id="8ad5a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8ad5a-108">**다음을 사용하여 SQL Server 인스턴스에 범주 정책을 적용하려면**</span><span class="sxs-lookup"><span data-stu-id="8ad5a-108">**To apply category policies to a SQL Server instance, using:**</span></span>  
  
     [<span data-ttu-id="8ad5a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8ad5a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8ad5a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8ad5a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8ad5a-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8ad5a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8ad5a-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8ad5a-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8ad5a-113">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]를 사용할 경우, **데이터베이스 구독 위임** 확인란이 선택되어 있지 않으면 하나 이상의 데이터베이스 또는 테이블과 같은 서버의 각 관련 부분에 정책 범주를 개별적으로 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-113">When using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], if the **Mandate Database Subscriptions** check box is not selected, the policy category must be individually applied to each relevant portion of the server, such as one or more databases or tables.</span></span>  
  
-   <span data-ttu-id="8ad5a-114">없는 정책 범주를 지정하면 새 정책 범주가 만들어지고 저장 프로시저를 실행할 때 모든 데이터베이스에 대해 구독이 위임됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-114">If you specify a policy category that does not exist, a new policy category is created and the subscription is mandated for all databases when you execute the stored procedure.</span></span> <span data-ttu-id="8ad5a-115">이후에 새 범주의 위임된 구독을 제거하면 *target_object*로 지정한 데이터베이스에 대해서만 구독이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-115">If you then clear the mandated subscription for the new category, the subscription will only apply for the database that you specified as the *target_object*.</span></span> <span data-ttu-id="8ad5a-116">위임된 구독 설정을 변경하는 방법은 [sp_syspolicy_update_policy_category&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-116">For more information about how to change a mandated subscription setting, see [sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8ad5a-117">보안</span><span class="sxs-lookup"><span data-stu-id="8ad5a-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8ad5a-118">권한</span><span class="sxs-lookup"><span data-stu-id="8ad5a-118">Permissions</span></span>  
 <span data-ttu-id="8ad5a-119">이 저장 프로시저는 현재 저장 프로시저 소유자의 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-119">This stored procedure runs in the context of the current owner of the stored procedure.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8ad5a-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="8ad5a-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a><span data-ttu-id="8ad5a-121">SQL Server 인스턴스에 범주 정책을 적용하려면</span><span class="sxs-lookup"><span data-stu-id="8ad5a-121">To apply category policies to a SQL Server instance</span></span>  
  
1.  <span data-ttu-id="8ad5a-122">**개체 탐색기**에서 더하기 기호를 클릭하여 범주 정책을 적용할 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-122">In **Object Explorer**, click the plus sign to expand the server where you will apply category policies.</span></span>  
  
2.  <span data-ttu-id="8ad5a-123">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-123">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="8ad5a-124">**정책 관리** 를 마우스 오른쪽 단추로 클릭하고 **범주 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-124">Right-click **Policy Management** and select **Manage Categories**.</span></span>  
  
     <span data-ttu-id="8ad5a-125">**정책 범주 관리** 대화 상자에 다음 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-125">The following information is available in the **Manage Policy Categories** dialog box:</span></span>  
  
     <span data-ttu-id="8ad5a-126">**이름**</span><span class="sxs-lookup"><span data-stu-id="8ad5a-126">**Name**</span></span>  
     <span data-ttu-id="8ad5a-127">정책 범주의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-127">The name of the policy category.</span></span>  
  
     <span data-ttu-id="8ad5a-128">**데이터베이스 구독 위임**</span><span class="sxs-lookup"><span data-stu-id="8ad5a-128">**Mandate Database Subscriptions**</span></span>  
     <span data-ttu-id="8ad5a-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 모든 데이터베이스가 정책 범주의 정책을 적용하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-129">Forces all databases on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to enforce policies in the policy category.</span></span>  
  
4.  <span data-ttu-id="8ad5a-130">**데이터베이스 구독 위임** 아래의 확인란을 임의로 또는 모두 선택하거나 선택 취소하여 해당 정책 범주를 SQL Server 인스턴스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-130">Select or clear any or all check boxes under **Mandate Database Subscriptions** to apply that policy category to the SQL Server instance.</span></span>  
  
5.  <span data-ttu-id="8ad5a-131">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8ad5a-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="8ad5a-132">Using Transact-SQL</span></span>  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a><span data-ttu-id="8ad5a-133">SQL Server 인스턴스에 범주 정책을 적용하려면</span><span class="sxs-lookup"><span data-stu-id="8ad5a-133">To apply category policies to a SQL Server instance</span></span>  
  
1.  <span data-ttu-id="8ad5a-134">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8ad5a-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8ad5a-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    -- configures the specified database to subscribe to a policy category that is named 'Table Naming Policies'.  
    EXEC dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
    , @target_object = N'AdventureWorks2012'  
    , @policy_category = N'Table Naming Policies';  
    GO  
    ```  
  
 <span data-ttu-id="8ad5a-137">자세한 내용은 [sp_syspolicy_add_policy_category_subscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ad5a-137">For more information, see [sp_syspolicy_add_policy_category_subscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql).</span></span>  
  
  
