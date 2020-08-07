---
title: Management Studio에 사용자 지정 보고서 추가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 3cf8d726-0a90-4f80-98d0-352a2a59be0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07263edfb9b255257e0c79733c2c34b279b61cd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638527"
---
# <a name="add-a-custom-report-to-management-studio"></a><span data-ttu-id="47e33-102">Management Studio에 사용자 지정 보고서 추가</span><span class="sxs-lookup"><span data-stu-id="47e33-102">Add a Custom Report to Management Studio</span></span>
  <span data-ttu-id="47e33-103">이 항목에서는 .rdl 파일로 저장되는 간단한 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서를 만든 다음 이 rdl 파일을 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에 사용자 지정 보고서로 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-103">This topic describes how to create a simple [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that is saved as an .rdl file, and then add that rdl file to [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] as a custom report.</span></span> [!INCLUDE[ssRS](../../includes/ssrs.md)] <span data-ttu-id="47e33-104">다양한 고급 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-104">can create a wide variety of sophisticated reports.</span></span> <span data-ttu-id="47e33-105">이 항목을 사용하여 보고서를 만들려면 컴퓨터에 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-105">To create a report by using this topic, you must have [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] installed on the computer.</span></span> <span data-ttu-id="47e33-106">[!INCLUDE[ssRS](../../includes/ssrs.md)] 를 사용하여 사용자 지정 보고서를 실행하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 설치할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-106">You do not have to install [!INCLUDE[ssRS](../../includes/ssrs.md)] on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to run a custom report using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
  
### <a name="to-create-a-simple-report-saved-as-an-rdl-file"></a><span data-ttu-id="47e33-107">.rdl 파일로 저장되는 간단한 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="47e33-107">To create a simple report saved as an .rdl file</span></span>  
  
1.  <span data-ttu-id="47e33-108">**시작**을 클릭하고 **프로그램**, **Microsoft SQL Server**를 차례로 가리킨 후 **SQL Server Data Tools**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-108">Click **Start**, point to **Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="47e33-109">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-109">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="47e33-110">**프로젝트 형식** 목록에서 **비즈니스 인텔리전스 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-110">In the **Project Types** list, click **Business Intelligence Projects**.</span></span>  
  
4.  <span data-ttu-id="47e33-111">**템플릿** 목록에서 **보고서 서버 프로젝트 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-111">In the **Templates** list, click **Report Server Project Wizard**.</span></span>  
  
5.  <span data-ttu-id="47e33-112">**이름**에 **ConnectionsReport**를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-112">In **Name**, type **ConnectionsReport**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="47e33-113">**보고서 마법사** 시작 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-113">On the **Report Wizard** introduction page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="47e33-114">**데이터 원본 선택** 페이지의 이름 입력란에 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 대한 이 연결의 이름을 입력한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-114">On the **Select the Data Source** page, in the Name box type a name for this connection to your [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Edit**.</span></span>  
  
8.  <span data-ttu-id="47e33-115">**연결 속성** 대화 상자의 **서버 이름** 입력란에 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-115">In the **Connection Properties** dialog box, in the **Server name** box, type the name of your instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
9. <span data-ttu-id="47e33-116">**데이터베이스 이름 선택 또는 입력** 상자에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 있는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]등의 데이터베이스 이름을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-116">In the **Select or enter a database name** box, type the name of any database on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **OK**.</span></span>  
  
10. <span data-ttu-id="47e33-117">**데이터 원본 선택** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-117">On the **Select the Data Source** page, click **Next**.</span></span>  
  
11. <span data-ttu-id="47e33-118">**쿼리 디자인** 페이지의 **쿼리 문자열** 입력란에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 에 대한 현재 연결을 나열하는 다음 [!INCLUDE[ssDE](../../includes/ssde-md.md)]문을 입력한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-118">On the **Design the Query** page, in the **Query string** box, type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that lists the current connections to your [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Next**.</span></span> <span data-ttu-id="47e33-119">보고서 마법사 쿼리 문자열 입력란에는 보고서 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-119">The Report Wizard Query string box will not accept report parameters.</span></span> <span data-ttu-id="47e33-120">더 복잡한 사용자 지정 보고서는 수동으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-120">More complex custom reports must be created manually.</span></span>  
  
     `SELECT session_id, net_transport FROM sys.dm_exec_connections;`  
  
12. <span data-ttu-id="47e33-121">**보고서 유형 선택** 페이지에서 **테이블 형식**을 선택한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-121">On the **Select the Report Type** page, select **Tabular**, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="47e33-122">**마법사 완료** 페이지의 **보고서 이름** 입력란에 **ConnectionsReport**를 입력한 다음 **마침** 을 클릭하여 보고서를 만들고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-122">On the **Completing the Wizard** page, in the **Report name** box, type **ConnectionsReport**, and then click **Finish** to create and save the report.</span></span>  
  
14. <span data-ttu-id="47e33-123">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-123">Close [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
15. <span data-ttu-id="47e33-124">사용자 지정 보고서를 위해 데이터베이스 서버에 만든 폴더에 **ConnectionsReport.rdl** 을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-124">Copy **ConnectionsReport.rdl** to a folder that you created on the database server for custom reports.</span></span>  
  
### <a name="to-add-a-report-to-management-studio"></a><span data-ttu-id="47e33-125">Management Studio에 보고서를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="47e33-125">To add a report to Management Studio</span></span>  
  
-   <span data-ttu-id="47e33-126">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 개체 탐색기의 노드를 마우스 오른쪽 단추로 클릭하고 **보고서**를 가리킨 다음 **사용자 지정 보고서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-126">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click a node in Object Explorer, point to **Reports**, click **Custom Reports**.</span></span> <span data-ttu-id="47e33-127">**파일 열기** 대화 상자에서 사용자 지정 보고서 폴더를 찾고 **ConnectionsReport.rdl** 파일을 선택한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-127">In the **Open File** dialog box, locate the custom reports folder and select the **ConnectionsReport.rdl** file, and then click **Open**.</span></span>  
  
     <span data-ttu-id="47e33-128">개체 탐색기 노드에서 새 사용자 지정 보고서를 처음으로 열면 해당 노드의 바로 가기 메뉴에 있는 **사용자 지정 보고서** 의 가장 최근에 사용한 목록에 이 보고서가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-128">When a new custom report is first opened from an Object Explorer node, the custom report is added to the most recently used list under **Custom Reports** on the shortcut menu of that node.</span></span> <span data-ttu-id="47e33-129">표준 보고서를 처음으로 열면 이 보고서도 **사용자 지정 보고서**의 가장 최근에 사용한 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-129">When a standard report is opened for the first time, it will also appear on the most recently used list under **Custom Reports**.</span></span> <span data-ttu-id="47e33-130">사용자 지정 보고서 파일을 삭제하면 다음에 이 항목을 선택할 때 가장 최근에 사용한 목록에서 해당 항목을 삭제하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-130">If a custom report file is deleted, the next time that the item is selected, a prompt will appear to delete the item from the most recently used list.</span></span>  
  
    1.  <span data-ttu-id="47e33-131">최근에 사용한 목록에 표시되는 파일 수를 변경하려면 **도구** 메뉴에서 **옵션** 을 클릭하고 **환경** 폴더를 확장한 다음 **일반**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-131">To change the number of files that are displayed on the recently used list, on the **Tools** menu, click **Options,** expand the **Environment** folder, and then click **General**.</span></span>  
  
    2.  <span data-ttu-id="47e33-132">**최근 사용 목록에 n개 파일 표시**의 개수를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="47e33-132">Adjust the number for **Display files in recently used list**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e33-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47e33-133">See Also</span></span>  
 <span data-ttu-id="47e33-134">[Management Studio의 사용자 지정 보고서](custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="47e33-134">[Custom Reports in Management Studio](custom-reports-in-management-studio.md) </span></span>  
 <span data-ttu-id="47e33-135">[개체 탐색기 노드 속성으로 사용자 지정 보고서 사용](use-custom-reports-with-object-explorer-node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="47e33-135">[Use Custom Reports with Object Explorer Node Properties](use-custom-reports-with-object-explorer-node-properties.md) </span></span>  
 <span data-ttu-id="47e33-136">[표시 사용자 지정 보고서 경고 실행](unsuppress-run-custom-report-warnings.md) </span><span class="sxs-lookup"><span data-stu-id="47e33-136">[Unsuppress Run Custom Report Warnings](unsuppress-run-custom-report-warnings.md) </span></span>  
 [<span data-ttu-id="47e33-137">Reporting Services&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="47e33-137">Reporting Services &#40;SSRS&#41;</span></span>](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
