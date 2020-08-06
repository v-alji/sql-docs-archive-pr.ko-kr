---
title: 뷰 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], creating
ms.assetid: 0b7bd2a1-544c-42ba-8e7b-4822f34d7b64
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8280f6d65d7252cad423abef849207111492c044
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646263"
---
# <a name="create-views"></a><span data-ttu-id="04f81-102">뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="04f81-102">Create Views</span></span>
  <span data-ttu-id="04f81-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-103">You can create views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="04f81-104">뷰는 다음과 같은 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-104">A view can be used for the following purposes:</span></span>  
  
-   <span data-ttu-id="04f81-105">각 사용자가 데이터베이스를 보는 시각에 초점을 맞추고 데이터 조작을 간소화하며 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-105">To focus, simplify, and customize the perception each user has of the database.</span></span>  
  
-   <span data-ttu-id="04f81-106">뷰는 원본이 되는 기본 테이블에 직접 액세스할 수 있는 권한을 부여하지 않고 뷰를 통해 데이터에 액세스하도록 하기 때문에 보안 메커니즘으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-106">As a security mechanism by allowing users to access data through the view, without granting the users permissions to directly access the underlying base tables.</span></span>  
  
-   <span data-ttu-id="04f81-107">이전 버전과 호환되는 인터페이스를 통해 스키마가 변경된 기존 테이블을 에뮬레이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-107">To provide a backward compatible interface to emulate a table whose schema has changed.</span></span>  
  
 <span data-ttu-id="04f81-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="04f81-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="04f81-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="04f81-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="04f81-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="04f81-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="04f81-111">보안</span><span class="sxs-lookup"><span data-stu-id="04f81-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="04f81-112">**뷰를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="04f81-112">**To create a view, using:**</span></span>  
  
     [<span data-ttu-id="04f81-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="04f81-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="04f81-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="04f81-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="04f81-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="04f81-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="04f81-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="04f81-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="04f81-117">현재 데이터베이스에서만 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-117">A view can be created only in the current database.</span></span>  
  
 <span data-ttu-id="04f81-118">최대 1,024개의 열을 뷰에 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-118">A view can have a maximum of 1,024 columns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="04f81-119">보안</span><span class="sxs-lookup"><span data-stu-id="04f81-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="04f81-120">권한</span><span class="sxs-lookup"><span data-stu-id="04f81-120">Permissions</span></span>  
 <span data-ttu-id="04f81-121">데이터베이스에는 CREATE VIEW 권한이 필요하고 뷰를 만들 구성표에는 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-121">Requires CREATE VIEW permission in the database and ALTER permission on the schema in which the view is being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="04f81-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="04f81-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-view-by-using-the-query-and-view-designer"></a><span data-ttu-id="04f81-123">쿼리 및 뷰 디자이너를 사용하여 뷰를 만들려면</span><span class="sxs-lookup"><span data-stu-id="04f81-123">To create a view by using the Query and View Designer</span></span>  
  
1.  <span data-ttu-id="04f81-124">**개체 탐색기**에서 새 뷰를 만들 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-124">In **Object Explorer**, expand the database where you want to create your new view.</span></span>  
  
2.  <span data-ttu-id="04f81-125">**뷰** 폴더를 마우스 오른쪽 단추로 클릭한 다음, **새 뷰...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-125">Right-click the **Views** folder, then click **New View...**.</span></span>  
  
3.  <span data-ttu-id="04f81-126">**테이블 추가** 대화 상자의 테이블, 뷰, 함수 및 동의어 탭 중 하나에서 새 뷰에 포함할 요소를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-126">In the **Add Table** dialog box, select the element or elements that you want to include in your new view from one of the following tabs: Tables, Views, Functions, and Synonyms.</span></span>  
  
4.  <span data-ttu-id="04f81-127">**추가**를 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-127">Click **Add**, then click **Close**.</span></span>  
  
5.  <span data-ttu-id="04f81-128">**다이어그램 창**에서 새 뷰에 포함할 열 또는 다른 요소를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-128">In the **Diagram Pane**, select the columns or other elements to include in the new view.</span></span>  
  
6.  <span data-ttu-id="04f81-129">**조건 창**에서 열에 대한 추가 정렬 또는 필터 조건을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-129">In the **Criteria Pane**, select additional sort or filter criteria for the columns.</span></span>  
  
7.  <span data-ttu-id="04f81-130">**파일** 메뉴에서 **저장**_view name_을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-130">On the **File** menu, click **Save**_view name_.</span></span>  
  
8.  <span data-ttu-id="04f81-131">**이름 선택** 대화 상자에서 새 뷰의 이름을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-131">In the **Choose Name** dialog box, enter a name for the new view and click **OK**.</span></span>  
  
     <span data-ttu-id="04f81-132">쿼리 및 뷰 디자이너에 대한 자세한 내용은 [쿼리 및 뷰 디자이너 도구&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04f81-132">For more information about the query and view designer, see [Query and View Designer Tools &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="04f81-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="04f81-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-view"></a><span data-ttu-id="04f81-134">뷰를 만들려면</span><span class="sxs-lookup"><span data-stu-id="04f81-134">To create a view</span></span>  
  
1.  <span data-ttu-id="04f81-135">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="04f81-136">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="04f81-137">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04f81-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
    GO  
    -- Query the view  
    SELECT FirstName, LastName, HireDate  
    FROM HumanResources.EmployeeHireDate  
    ORDER BY LastName;  
  
    ```  
  
 <span data-ttu-id="04f81-138">자세한 내용은 [CREATE VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04f81-138">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
  
