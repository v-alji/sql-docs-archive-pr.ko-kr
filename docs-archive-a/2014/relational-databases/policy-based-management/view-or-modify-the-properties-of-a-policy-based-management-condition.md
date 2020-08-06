---
title: 정책 기반 관리 조건의 속성 보기 또는 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view policy conditions
- Policy-Based Management, modify policy conditions
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 08baec48bd13445ef56ea6a29520d23ebaf683b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648978"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-condition"></a><span data-ttu-id="ab95d-102">정책 기반 관리 조건의 속성 보기 또는 수정</span><span class="sxs-lookup"><span data-stu-id="ab95d-102">View or Modify the Properties of a Policy-Based Management Condition</span></span>
  <span data-ttu-id="ab95d-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 정책 기반 관리 조건의 속성을 보거나 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-103">This topic describes how to view or modify the properties of a Policy-Based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ab95d-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="ab95d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ab95d-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="ab95d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ab95d-106">보안</span><span class="sxs-lookup"><span data-stu-id="ab95d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ab95d-107">**다음을 사용하여 조건의 속성을 보거나 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="ab95d-107">**To view or modify a condition's properties, using:**</span></span>  
  
     [<span data-ttu-id="ab95d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab95d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ab95d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab95d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ab95d-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ab95d-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ab95d-111">보안</span><span class="sxs-lookup"><span data-stu-id="ab95d-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ab95d-112">권한</span><span class="sxs-lookup"><span data-stu-id="ab95d-112">Permissions</span></span>  
 <span data-ttu-id="ab95d-113">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-113">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ab95d-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ab95d-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-modify-a-conditions-properties"></a><span data-ttu-id="ab95d-115">조건의 속성을 보거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="ab95d-115">To view or modify a condition's properties</span></span>  
  
1.  <span data-ttu-id="ab95d-116">**개체 탐색기**에서 더하기 기호를 클릭하여 보거나 수정하려는 조건이 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-116">In **Object Explorer**, click the plus sign to expand the server that contains the condition that you want to view or modify.</span></span>  
  
2.  <span data-ttu-id="ab95d-117">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-117">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="ab95d-118">더하기 기호를 클릭하여 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-118">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="ab95d-119">더하기 기호를 클릭하여 **조건** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-119">Click the plus sign to expand the **Conditions** folder.</span></span>  
  
5.  <span data-ttu-id="ab95d-120">보거나 편집하려는 조건을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-120">Right-click the condition that you want to view or edit and select **Properties**.</span></span> <span data-ttu-id="ab95d-121">**조건 열기 –**_condition_name 대화 상자_에서 사용 가능한 옵션에 대한 자세한 내용은 [새 조건 만들기 또는 조건 열기 대화 상자, 일반 페이지](../../integration-services/general-page-of-integration-services-designers-options.md), [조건 열기 대화 상자, 종속 정책 페이지](open-condition-dialog-box-dependent-policies-page.md), [새 조건 만들기 또는 조건 열기 대화 상자, 설명 페이지](create-new-condition-or-open-condition-dialog-box-description-page.md) 및 [고급 편집&#40;조건&#41; 대화 상자](advanced-edit-condition-dialog-box.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab95d-121">For more information on the available options in the **Open Condition -**_condition_name_ dialog box, see [Create New Condition or Open Condition Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Open Condition Dialog Box, Dependent Policies Page](open-condition-dialog-box-dependent-policies-page.md), [Create New Condition or Open Condition Dialog Box, Description Page](create-new-condition-or-open-condition-dialog-box-description-page.md), and [Advanced Edit &#40;Condition&#41; Dialog Box](advanced-edit-condition-dialog-box.md).</span></span>  
  
6.  <span data-ttu-id="ab95d-122">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-122">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ab95d-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ab95d-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-conditions-properties"></a><span data-ttu-id="ab95d-124">조건의 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="ab95d-124">To view a condition's properties</span></span>  
  
1.  <span data-ttu-id="ab95d-125">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ab95d-126">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ab95d-127">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ab95d-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 <span data-ttu-id="ab95d-128">자세한 내용은 [syspolicy_conditions&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab95d-128">For more information, see [syspolicy_conditions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql).</span></span>  
  
  
