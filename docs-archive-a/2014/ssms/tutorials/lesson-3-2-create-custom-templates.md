---
title: 사용자 지정 템플릿 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 771547b9c47672d2c075b5e7215d78744fe5f18e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733403"
---
# <a name="create-custom-templates"></a><span data-ttu-id="3d444-102">사용자 지정 템플릿 만들기</span><span class="sxs-lookup"><span data-stu-id="3d444-102">Create Custom Templates</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="3d444-103">와 함께 많은 일반 태스크에 사용할 템플릿이 제공되지만 템플릿의 진정한 힘은 자주 만들어야 할 복잡한 스크립트의 사용자 지정 템플릿을 만드는 기능에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-103">comes with templates for many common tasks, but the real power of templates lies in the ability to create a custom template for a complex script that you must create frequently.</span></span> <span data-ttu-id="3d444-104">이 연습에서 소수의 매개 변수가 있는 단순 스크립트를 만들지만 템플릿은 반복되는 긴 스크립트에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-104">In this practice you will create a simple script with few parameters, but templates are useful for long, repetitive scripts, too.</span></span>  
  
## <a name="using-custom-templates"></a><span data-ttu-id="3d444-105">사용자 지정 템플릿 사용</span><span class="sxs-lookup"><span data-stu-id="3d444-105">Using Custom Templates</span></span>  
  
#### <a name="to-create-a-custom-template"></a><span data-ttu-id="3d444-106">사용자 지정 템플릿을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3d444-106">To create a custom template</span></span>  
  
1.  <span data-ttu-id="3d444-107">템플릿 탐색기에서 **SQL Server 템플릿**을 확장하고 **Stored Procedure**를 마우스 오른쪽 단추로 클릭한 다음 **새로 만들기**를 가리키고 **폴더**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-107">In Template Explorer, expand **SQL Server Templates**, right-click **Stored Procedure**, point to **New**, and then click **Folder**.</span></span>  
  
2.  <span data-ttu-id="3d444-108">새 템플릿 폴더 이름으로 **Custom** 을 입력한 다음 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-108">Type **Custom** as the name of your new template folder, and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="3d444-109">**Custom**을 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **템플릿**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-109">Right-click **Custom**, point to **New**, and then click **Template**.</span></span>  
  
4.  <span data-ttu-id="3d444-110">새 템플릿 이름으로 **WorkOrdersProc** 를 입력한 다음 **Enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-110">Type **WorkOrdersProc** as the name of your new template, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="3d444-111">**WorkOrdersProc**를 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-111">Right-click **WorkOrdersProc**, and then click **Edit**.</span></span>  
  
6.  <span data-ttu-id="3d444-112">**데이터베이스 엔진에 연결** 대화 상자에서 연결 정보를 확인한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-112">In the **Connect to Database Engine** dialog box, verify the connection information and then click **Connect**.</span></span>  
  
7.  <span data-ttu-id="3d444-113">쿼리 편집기에 다음 스크립트를 입력하여 특정 부품(이 경우 Blade)에 대한 순서를 조회하는 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-113">In Query Editor, type the following script to create a stored procedure that looks up orders for a particular part, in this case the Blade.</span></span> <span data-ttu-id="3d444-114">자습서 창에서 코드를 복사하여 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-114">(You can copy and paste the code from the Tutorial window.)</span></span>  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  <span data-ttu-id="3d444-115">F5 키를 눌러 이 스크립트를 실행하면 **WorkOrdersForBlade** 프로시저가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-115">Press F5 to execute this script, creating the **WorkOrdersForBlade** procedure.</span></span>  
  
9. <span data-ttu-id="3d444-116">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-116">In Object Explorer, right-click your server, and then click **New Query**.</span></span> <span data-ttu-id="3d444-117">새 쿼리 편집기 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-117">A new Query Editor window opens.</span></span>  
  
10. <span data-ttu-id="3d444-118">쿼리 편집기에 **EXECUTE dbo.WorkOrdersForBlade**를 입력한 다음 F5 키를 눌러 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-118">In Query Editor, type **EXECUTE dbo.WorkOrdersForBlade**, and then press F5 to execute the query.</span></span> <span data-ttu-id="3d444-119">**결과** 창에서 Blade에 대한 작업 주문 목록이 반환되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-119">Confirm that the **Results** pane returns a list of work orders for blades.</span></span>  
  
11. <span data-ttu-id="3d444-120">템플릿 스크립트 (7 단계의 스크립트)를 편집 하 고 네 곳에서 제품 이름 블레이드를, <strong> *<* </strong> `nvarchar(50)` <strong>이름 *>* </strong>product_name 매개 변수로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-120">Edit the template script (the script in step 7), replacing the product name Blade with the parameter <strong>*<* product_name</strong>, `nvarchar(50)`, <strong>name*>*</strong>, in four places.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3d444-121">매개 변수에는 바꾸려는 매개 변수의 이름, 매개 변수의 데이터 형식 및 매개 변수 기본값의 세 가지 요소가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-121">Parameters require three elements: the name of the parameter that you want to replace, the data type of the parameter, and a default value for the parameter.</span></span>  
  
12. <span data-ttu-id="3d444-122">이제 스크립트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-122">Now the script should look like:</span></span>  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. <span data-ttu-id="3d444-123">**파일** 메뉴에서 **WorkOrdersProc.sql 저장** 을 클릭하여 템플릿을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-123">On the **File** menu, click **Save WorkOrdersProc.sql** to save your template.</span></span>  
  
#### <a name="to-test-the-custom-template"></a><span data-ttu-id="3d444-124">사용자 지정 템플릿을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="3d444-124">To test the custom template</span></span>  
  
1.  <span data-ttu-id="3d444-125">템플릿 탐색기에서 **Stored Procedure**, **Custom**을 차례로 확장한 다음 **WorkOrderProc**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-125">In Template Explorer, expand **Stored Procedure**, expand **Custom**, and then double-click **WorkOrderProc**.</span></span>  
  
2.  <span data-ttu-id="3d444-126">**데이터베이스 엔진에 연결** 대화 상자에서 연결 정보를 지정한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-126">In the **Connect to Database Engine** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="3d444-127">**WorkOrderProc** 템플릿의 내용이 포함된 새 쿼리 편집기 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-127">A new Query Editor window opens, containing the contents of the **WorkOrderProc** template.</span></span>  
  
3.  <span data-ttu-id="3d444-128">**쿼리** 메뉴에서 **템플릿 매개 변수 값 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-128">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
4.  <span data-ttu-id="3d444-129">**템플릿 매개 변수 바꾸기** 대화 상자에서 값에 대해 `product_name` **freewheel** (기본 내용 덮어쓰기)을 입력 한 다음 **확인** 을 클릭 하 여 **템플릿 매개 변수 바꾸기** 대화 상자를 닫고 쿼리 편집기에서 스크립트를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-129">In the **Replace Template Parameters** dialog box, for the `product_name` value, type **FreeWheel** (overwriting the default contents), and then click **OK** to close the **Replace Template Parameters** dialog box and modify the script in the Query Editor.</span></span>  
  
5.  <span data-ttu-id="3d444-130">F5 키를 눌러 쿼리를 실행하면 프로시저가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d444-130">Press F5 to execute the query, creating the procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3d444-131">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="3d444-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3d444-132">스크립트를 프로젝트 또는 솔루션으로 저장</span><span class="sxs-lookup"><span data-stu-id="3d444-132">Save Scripts as Projects or Solutions</span></span>](lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
