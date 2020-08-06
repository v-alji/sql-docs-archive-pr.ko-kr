---
title: 정책 기반 관리 정책의 속성 보기 또는 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, modify policies
- Policy-Based Management, view policies
ms.assetid: ba805504-5db5-4731-a8da-a0e89cb20c37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: da2226d3049a84098eb8e561635161f73b71ab10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648979"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-policy"></a><span data-ttu-id="59b51-102">정책 기반 관리 정책의 속성 보기 또는 수정</span><span class="sxs-lookup"><span data-stu-id="59b51-102">View or Modify the Properties of a Policy-Based Management Policy</span></span>
  <span data-ttu-id="59b51-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 정책 기반 관리 정책의 속성을 보거나 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-103">This topic describes how to view or modify a Policy-Based Management policy's properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="59b51-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="59b51-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="59b51-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="59b51-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="59b51-106">보안</span><span class="sxs-lookup"><span data-stu-id="59b51-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="59b51-107">**다음을 사용하여 정책의 속성을 보거나 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="59b51-107">**To view or modify a policy's properties, using:**</span></span>  
  
     [<span data-ttu-id="59b51-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="59b51-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="59b51-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="59b51-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="59b51-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="59b51-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="59b51-111">보안</span><span class="sxs-lookup"><span data-stu-id="59b51-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="59b51-112">권한</span><span class="sxs-lookup"><span data-stu-id="59b51-112">Permissions</span></span>  
 <span data-ttu-id="59b51-113">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-113">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="59b51-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="59b51-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-all-policies-on-an-object"></a><span data-ttu-id="59b51-115">개체에 있는 모든 정책의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="59b51-115">To view the properties of all policies on an object</span></span>  
  
1.  <span data-ttu-id="59b51-116">개체 탐색기에서 서버, 서버 개체, 데이터베이스 또는 데이터베이스 개체를 마우스 오른쪽 단추로 클릭하고 **정책** 을 가리킨 다음 **보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-116">In Object Explorer, right-click a server, server object, database, or database object, point to **Policies** and select **View**.</span></span> <span data-ttu-id="59b51-117">**정책 보기 –**_object_name_ 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [정책 보기 대화 상자](view-policies-dialog-box.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59b51-117">For more information on the available options in the **View Policies -**_object_name_ dialog box, see [View Policies Dialog Box](view-policies-dialog-box.md).</span></span>  
  
2.  <span data-ttu-id="59b51-118">완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-118">When finished, click **Close**.</span></span>  
  
#### <a name="to-view-or-modify-a-specific-policys-properties"></a><span data-ttu-id="59b51-119">특정 정책의 속성을 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="59b51-119">To view or modify a specific policy's properties</span></span>  
  
1.  <span data-ttu-id="59b51-120">**개체 탐색기**에서 더하기 기호를 클릭하여 보거나 수정하려는 정책 기반 관리 정책이 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-120">In **Object Explorer**, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to view or modify.</span></span>  
  
2.  <span data-ttu-id="59b51-121">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-121">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="59b51-122">더하기 기호를 클릭하여 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-122">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="59b51-123">더하기 기호를 클릭하여 **정책** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-123">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="59b51-124">보거나 수정하려는 정책을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-124">Right-click the policy that you want to view or modify and select **Properties**.</span></span> <span data-ttu-id="59b51-125">**정책 열기 –**_policy_name_ 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [새 정책 만들기 또는 정책 열기 대화 상자, 일반 페이지](../../integration-services/general-page-of-integration-services-designers-options.md) 또는 [새 정책 만들기 또는 정책 열기 대화 상자, 설명 페이지](create-new-policy-or-open-policy-dialog-box-description-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59b51-125">For more information on the available options in the **Open Policy -**_policy_name_ dialog box, see [Create New Policy or Open Policy Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md) and [Create New Policy or Open Policy Dialog Box, Description Page](create-new-policy-or-open-policy-dialog-box-description-page.md).</span></span>  
  
6.  <span data-ttu-id="59b51-126">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="59b51-127">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="59b51-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-policys-properties"></a><span data-ttu-id="59b51-128">정책의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="59b51-128">To view a policy's properties</span></span>  
  
1.  <span data-ttu-id="59b51-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="59b51-130">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="59b51-131">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="59b51-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       execution_mode,  
       description,  
       is_enabled,  
       job_id  
    FROM syspolicy_policies;  
    GO  
    ```  
  
 <span data-ttu-id="59b51-132">자세한 내용은 [syspolicy_policies&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-policies-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59b51-132">For more information, see [syspolicy_policies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-policies-transact-sql).</span></span>  
  
  
