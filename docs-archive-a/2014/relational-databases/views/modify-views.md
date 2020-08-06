---
title: 뷰 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- views [SQL Server], modifying
- modifying views
- renaming views
ms.assetid: 2d3c14dc-43e5-4324-b8fb-f2692d330b16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10cf9ecc860d8f9b46a06ac679b0f1a8241000bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650855"
---
# <a name="modify-views"></a><span data-ttu-id="bde0a-102">뷰 수정</span><span class="sxs-lookup"><span data-stu-id="bde0a-102">Modify Views</span></span>
  <span data-ttu-id="bde0a-103">뷰를 정의한 후 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 해당 뷰를 삭제하고 다시 만들지 않고 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 해당 정의를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-103">After you define a view, you can modify its definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] without dropping and re-creating the view by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="bde0a-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="bde0a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bde0a-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="bde0a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bde0a-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="bde0a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="bde0a-107">보안</span><span class="sxs-lookup"><span data-stu-id="bde0a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bde0a-108">**뷰를 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="bde0a-108">**To modify a view, using:**</span></span>  
  
     [<span data-ttu-id="bde0a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bde0a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bde0a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bde0a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bde0a-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="bde0a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bde0a-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="bde0a-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="bde0a-113">종속 개체를 무효화하는 방식으로 뷰 정의를 변경하지 않는 한 뷰를 수정해도 저장 프로시저나 트리거 등의 종속 개체에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-113">Modifying a view does not affect any dependent objects, such as stored procedures or triggers, unless the definition of the view changes in such a way that the dependent object is no longer valid.</span></span>  
  
-   <span data-ttu-id="bde0a-114">현재 사용 중인 뷰를 ALTER VIEW를 사용하여 수정하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 해당 뷰에 대한 배타적 스키마 잠금을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-114">If a view currently used is modified by using ALTER VIEW, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] takes an exclusive schema lock on the view.</span></span> <span data-ttu-id="bde0a-115">잠금이 부여되고 현재 뷰를 사용 중인 사용자가 없으면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 프로시저 캐시에서 뷰의 복사본을 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-115">When the lock is granted, and there are no active users of the view, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] deletes all copies of the view from the procedure cache.</span></span> <span data-ttu-id="bde0a-116">해당 뷰를 참조하는 기존 계획은 캐시에 남아 있지만 다음 호출 시 다시 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-116">Existing plans referencing the view remain in the cache but are recompiled when invoked.</span></span>  
  
-   <span data-ttu-id="bde0a-117">인덱싱된 뷰에도 ALTER VIEW를 적용할 수 있지만 ALTER VIEW는 뷰에 대한 모든 인덱스를 무조건 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-117">ALTER VIEW can be applied to indexed views; however, ALTER VIEW unconditionally drops all indexes on the view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bde0a-118">보안</span><span class="sxs-lookup"><span data-stu-id="bde0a-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bde0a-119">권한</span><span class="sxs-lookup"><span data-stu-id="bde0a-119">Permissions</span></span>  
 <span data-ttu-id="bde0a-120">ALTER VIEW를 실행하려면 최소 OBJECT에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-120">To execute ALTER VIEW, at a minimum, ALTER permission on OBJECT is required.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bde0a-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="bde0a-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-view"></a><span data-ttu-id="bde0a-122">뷰를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="bde0a-122">To modify a view</span></span>  
  
1.  <span data-ttu-id="bde0a-123">**개체 탐색기**에서 뷰가 있는 데이터베이스 옆의 더하기 기호를 클릭한 다음 **뷰** 폴더 옆의 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-123">In **Object Explorer**, click the plus sign next to the database where your view is located and then click the plus sign next to the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="bde0a-124">수정할 뷰를 마우스 오른쪽 단추로 클릭하고 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-124">Right-click on the view you wish to modify and select **Design**.</span></span>  
  
3.  <span data-ttu-id="bde0a-125">쿼리 디자이너의 다이어그램 창에서 다음과 같은 방법으로 뷰를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-125">In the diagram pane of the query designer, make changes to the view in one or more of the following ways:</span></span>  
  
    1.  <span data-ttu-id="bde0a-126">추가하거나 제거할 요소의 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-126">Select or clear the check boxes of any elements you wish to add or remove.</span></span>  
  
    2.  <span data-ttu-id="bde0a-127">다이어그램 창 내부를 마우스 오른쪽 단추로 클릭하고 **테이블 추가...** 를 선택한 다음, **테이블 추가** 대화 상자에서 뷰에 추가할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-127">Right-click within the diagram pane, select **Add Table...**, and then select the additional columns you want to add to the view from the **Add Table** dialog box.</span></span>  
  
    3.  <span data-ttu-id="bde0a-128">제거할 테이블의 제목 표시줄을 마우스 오른쪽 단추로 클릭하고 **제거**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-128">Right-click the title bar of the table you wish to remove and select **Remove**.</span></span>  
  
4.  <span data-ttu-id="bde0a-129">**파일** 메뉴에서 **저장**_view name_을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-129">On the **File** menu, click **Save**_view name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bde0a-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="bde0a-130">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-view"></a><span data-ttu-id="bde0a-131">뷰를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="bde0a-131">To modify a view</span></span>  
  
1.  <span data-ttu-id="bde0a-132">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bde0a-133">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bde0a-134">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="bde0a-135">다음 예에서는 먼저 뷰를 만든 다음 ALTER VIEW를 사용하여 이 뷰를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-135">The example first creates a view and then modifies the view by using ALTER VIEW.</span></span> <span data-ttu-id="bde0a-136">WHERE 절이 뷰 정의에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bde0a-136">A WHERE clause is added to the view definition.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    -- Create a view.  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
  
    -- Modify the view by adding a WHERE clause to limit the rows returned.  
    ALTER VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID  
    WHERE HireDate < CONVERT(DATETIME,'20020101',101) ;   
    GO  
    ```  
  
 <span data-ttu-id="bde0a-137">자세한 내용은 [ALTER VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-view-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bde0a-137">For more information, see [ALTER VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-view-transact-sql).</span></span>  
  
  
