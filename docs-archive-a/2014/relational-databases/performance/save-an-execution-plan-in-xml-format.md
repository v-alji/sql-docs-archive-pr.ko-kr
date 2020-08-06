---
title: XML 형식으로 실행 계획 저장 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- XML query plans [SQL Server]
- opening execution plans
- XML Showplans [SQL Server]
- execution plans [SQL Server], saving
- saving execution plans
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 84ed341d186993ed77260e8361156b324c597839
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652774"
---
# <a name="save-an-execution-plan-in-xml-format"></a><span data-ttu-id="eed4f-102">XML 형식으로 실행 계획 저장</span><span class="sxs-lookup"><span data-stu-id="eed4f-102">Save an Execution Plan in XML Format</span></span>
  <span data-ttu-id="eed4f-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 실행 계획을 XML 파일로 저장하고 열어서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-103">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to save execution plans as an XML file, and to open them for viewing.</span></span>  
  
 <span data-ttu-id="eed4f-104">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 실행 계획 기능을 사용하거나 XML 실행 계획 SET 옵션을 사용하려면 사용자에게 실행 계획을 생성할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 실행하는 데 적합한 권한이 있어야 하며 쿼리에서 참조하는 모든 데이터베이스에 대한 SHOWPLAN 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-104">To use the execution plan feature in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or to use the XML Showplan SET options, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] query for which an execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-save-a-query-plan-by-using-the-xml-showplan-set-options"></a><span data-ttu-id="eed4f-105">XML 실행 계획 SET 옵션을 사용하여 쿼리 계획을 저장하려면</span><span class="sxs-lookup"><span data-stu-id="eed4f-105">To save a query plan by using the XML Showplan SET options</span></span>  
  
1.  <span data-ttu-id="eed4f-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 쿼리 편집기를 열고 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] open a query editor and connect to [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eed4f-107">다음 문으로 SHOWPLAN_XML을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-107">Turn SHOWPLAN_XML on with the following statement:</span></span>  
  
    ```  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     <span data-ttu-id="eed4f-108">STATISTICS XML을 설정하려면 다음 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-108">To turn STATISTICS XML on, use the following statement:</span></span>  
  
    ```  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     <span data-ttu-id="eed4f-109">SHOWPLAN_XML은 쿼리에 대한 컴파일 시간 쿼리 실행 계획 정보를 생성하지만 쿼리를 실행하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-109">SHOWPLAN_XML generates compile-time query execution plan information for a query, but does not execute the query.</span></span> <span data-ttu-id="eed4f-110">STATISTICS XML은 쿼리에 대한 런타임 쿼리 실행 계획 정보를 생성하고 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-110">STATISTICS XML generates run-time query execution plan information for a query, and executes the query.</span></span>  
  
3.  <span data-ttu-id="eed4f-111">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-111">Execute a query.</span></span> <span data-ttu-id="eed4f-112">예제:</span><span class="sxs-lookup"><span data-stu-id="eed4f-112">Example:</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SET SHOWPLAN_XML ON;  
    GO  
    -- Execute a query.  
    SELECT BusinessEntityID   
    FROM HumanResources.Employee  
    WHERE NationalIDNumber = '509647174';  
    GO  
    SET SHOWPLAN_XML OFF;  
    ```  
  
4.  <span data-ttu-id="eed4f-113">**결과** 창에서 쿼리 계획을 포함하는 **Microsoft SQL Server XML Showplan** 을 마우스 오른쪽 단추로 클릭한 다음 **다른 이름으로 결과 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-113">In the **Results** pane, right-click the **Microsoft SQL Server XML Showplan** that contains the query plan, and then click **Save Results As**.</span></span>  
  
5.  <span data-ttu-id="eed4f-114">\<Grid or Text> **결과** **저장** 대화 상자의 **다른 이름으로 저장** 상자에서 **모든 파일(\*.\*)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-114">In the **Save** \<Grid or Text> **Results** dialog box, in the **Save as type** box, click **All files (\*.\*)**.</span></span>  
  
6.  <span data-ttu-id="eed4f-115">**파일 이름** 상자에 \<name**>.sqlplan\*\* 형식으로 이름을 입력한 후 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-115">In the **File name** box provide a name, in the format \<name**>.sqlplan\*\*, and then click **Save**.</span></span>  
  
### <a name="to-save-an-execution-plan-by-using-sql-server-management-studio-options"></a><span data-ttu-id="eed4f-116">SQL Server Management Studio 옵션을 사용하여 실행 계획을 저장하려면</span><span class="sxs-lookup"><span data-stu-id="eed4f-116">To save an execution plan by using SQL Server Management Studio options</span></span>  
  
1.  <span data-ttu-id="eed4f-117">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용하여 예상 실행 계획이나 실제 실행 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-117">Generate either an estimated execution plan or an actual execution plan by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="eed4f-118">자세한 내용은 [예상 실행 계획 표시](display-the-estimated-execution-plan.md) 또는 [실제 실행 계획 표시](display-an-actual-execution-plan.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eed4f-118">For more information, see [Display the Estimated Execution Plan](display-the-estimated-execution-plan.md) or [Display an Actual Execution Plan](display-an-actual-execution-plan.md).</span></span>  
  
2.  <span data-ttu-id="eed4f-119">결과 창의 **실행 계획** 탭에서 그래픽 실행 계획을 마우스 오른쪽 단추로 클릭하고 **실행 계획을 다른 이름으로 저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-119">In the **Execution plan** tab of the results pane, right-click the graphical execution plan, and choose **Save Execution Plan As**.</span></span>  
  
     <span data-ttu-id="eed4f-120">또는 **파일** 메뉴에서 **실행 계획을 다른 이름으로 저장** 을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-120">As an alternative, you can also choose **Save Execution Plan As** on the **File** menu.</span></span>  
  
3.  <span data-ttu-id="eed4f-121">**다른 이름으로 저장** 대화 상자에서 **파일 형식**이 **실행 계획 파일(\*.sqlplan)** 로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-121">In the **Save As** dialog box, make sure that the **Save as type** is set to **Execution Plan Files (\*.sqlplan)**.</span></span>  
  
4.  <span data-ttu-id="eed4f-122">**파일 이름** 상자에 \<name**>.sqlplan\*\* 형식으로 이름을 입력한 후 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-122">In the **File name** box provide a name, in the format \<name**>.sqlplan\*\*, and then click **Save**.</span></span>  
  
### <a name="to-open-a-saved-xml-query-plan-in-sql-server-management-studio"></a><span data-ttu-id="eed4f-123">SQL Server Management Studio에서 저장된 XML 쿼리 계획을 열려면</span><span class="sxs-lookup"><span data-stu-id="eed4f-123">To open a saved XML query plan in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="eed4f-124">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **파일** 메뉴에서 **열기**를 선택한 다음 **파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **File** menu, choose **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="eed4f-125">**파일 열기** 대화 상자에서 **파일 형식**을 **실행 계획 파일(\*.sqlplan)** 로 설정하여 저장된 XML 쿼리 계획 파일의 필터링된 목록을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-125">In the **Open File** dialog box, set **Files of type** to **Execution Plan Files (\*.sqlplan)** to produce a filtered list of saved XML query plan files.</span></span>  
  
3.  <span data-ttu-id="eed4f-126">보려는 XML 쿼리 계획 파일을 선택하고 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-126">Select the XML query plan file that you want to view, and click **Open**.</span></span>  
  
     <span data-ttu-id="eed4f-127">또는 Windows 탐색기에서 확장명이 **.sqlplan**인 파일을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-127">As an alternative, in Windows Explorer, double-click a file with extension **.sqlplan**.</span></span> <span data-ttu-id="eed4f-128">계획이 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="eed4f-128">The plan opens in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed4f-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eed4f-129">See Also</span></span>  
 <span data-ttu-id="eed4f-130">[SET SHOWPLAN_XML&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-showplan-xml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eed4f-130">[SET SHOWPLAN_XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-showplan-xml-transact-sql) </span></span>  
 [<span data-ttu-id="eed4f-131">SET STATISTICS XML&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eed4f-131">SET STATISTICS XML &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
  
