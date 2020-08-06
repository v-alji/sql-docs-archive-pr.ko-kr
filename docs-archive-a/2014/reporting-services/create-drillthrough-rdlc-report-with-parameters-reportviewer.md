---
title: ReportViewer를 사용 하 여 매개 변수가 있는 드릴스루 (.RDLC) 보고서 만들기 (SSRS 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02864ea8bdd80d6f46b7aad552fa30241322370c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738032"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a><span data-ttu-id="0c503-102">ReportViewer를 사용하여 매개 변수가 있는 드릴스루(RDLC) 보고서 만들기(SSRS 자습서)</span><span class="sxs-lookup"><span data-stu-id="0c503-102">Create a Drillthrough (RDLC) Report with Parameters using ReportViewer (SSRS Tutorial)</span></span>
  <span data-ttu-id="0c503-103">[드릴스루](https://technet.microsoft.com/library/ff519554.aspx) 보고서는 다른 보고서 내에서 링크를 클릭했을 때 열리는 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="0c503-103">A [drillthrough](https://technet.microsoft.com/library/ff519554.aspx) report is a report that a user opens by clicking a link within another report.</span></span> <span data-ttu-id="0c503-104">드릴스루 보고서는 원본 요약 보고서에 포함된 항목에 대한 세부 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0c503-104">Drillthrough reports commonly contain details about an item that is contained in an original summary report.</span></span> <span data-ttu-id="0c503-105">이 자습서에서는 [로컬 모드 보고](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)에서 매개 변수 및 쿼리가 있는 드릴스루 보고서를 만드는 다음과 같은 단원을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0c503-105">This tutorial will walk you through the following lessons of creating a drillthrough report with parameters and a query, in [local mode reporting](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c503-106">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0c503-106">Requirements</span></span>  
 <span data-ttu-id="0c503-107">이 연습을 사용하려면 **AdventureWorks2008** 예제 데이터베이스에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c503-107">To use this walkthrough, you must have access to the **AdventureWorks2008** sample database.</span></span> <span data-ttu-id="0c503-108">이 연습에서 사용하는 쿼리는 **AdventureWorks2012** 데이터베이스에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0c503-108">The query used in this walkthrough will also work with **AdventureWorks2012** database.</span></span> <span data-ttu-id="0c503-109">**AdventureWorks2008** 예제 데이터베이스를 가져오는 방법에 대한 자세한 내용은 Microsoft Visual Studio 2010을 위한 [연습: AdventureWorks 데이터베이스 설치](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0c503-109">For more information about how to get the **AdventureWorks2008** sample database, see [Walkthrough: Installing the AdventureWorks Database](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx) for Microsoft Visual Studio 2010.</span></span>  
  
 <span data-ttu-id="0c503-110">이 연습에서는 Transaction-SQL 쿼리와 ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) 및 [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) 개체를 잘 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c503-110">This walkthrough assumes that you are familiar with Transaction-SQL queries and ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) and [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) objects.</span></span>  
  
 <span data-ttu-id="0c503-111">Visual Studio 2010 또는 Visual Studio 2012 및 ASP.NET 웹 사이트 템플릿을 사용하여 ReportViewer 컨트롤이 있는 ASP.NET 웹 페이지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c503-111">Use Visual Studio 2010, or Visual Studio 2012, and the ASP.NET website template to create an ASP.NET webpage with a ReportViewer control.</span></span> <span data-ttu-id="0c503-112">컨트롤은 사용자가 만드는 보고서를 보도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c503-112">The control is configured to view a report that you create.</span></span> <span data-ttu-id="0c503-113">이 연습에서는 Microsoft Visual C#에서 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0c503-113">For this walkthrough, you create the application in Microsoft Visual C#.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="0c503-114">작업</span><span class="sxs-lookup"><span data-stu-id="0c503-114">Tasks</span></span>  
 <span data-ttu-id="0c503-115">[1 단원: 새 웹 사이트 만들기](../reporting-services/lesson-1-create-a-new-web-site.md) </span><span class="sxs-lookup"><span data-stu-id="0c503-115">[Lesson 1: Create a New Web Site](../reporting-services/lesson-1-create-a-new-web-site.md) </span></span>  
 <span data-ttu-id="0c503-116">[2 단원: 부모 보고서에 대 한 데이터 연결 및 데이터 테이블 정의](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md) </span><span class="sxs-lookup"><span data-stu-id="0c503-116">[Lesson 2: Define a Data Connection and Data Table for Parent Report](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md) </span></span>  
 <span data-ttu-id="0c503-117">[3 단원: 보고서 마법사를 사용 하 여 부모 보고서 디자인](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="0c503-117">[Lesson 3: Design the Parent Report using the Report Wizard](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md) </span></span>  
 <span data-ttu-id="0c503-118">[4 단원: 자식 보고서에 대 한 데이터 연결 및 데이터 테이블 정의](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md) </span><span class="sxs-lookup"><span data-stu-id="0c503-118">[Lesson 4: Define a Data Connection and Data Table for Child Report](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md) </span></span>  
 <span data-ttu-id="0c503-119">[5 단원: 보고서 마법사를 사용 하 여 자식 보고서 디자인](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="0c503-119">[Lesson 5: Design the Child Report using the Report Wizard](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md) </span></span>  
 <span data-ttu-id="0c503-120">[6 단원: 응용 프로그램에 ReportViewer 컨트롤 추가](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md) </span><span class="sxs-lookup"><span data-stu-id="0c503-120">[Lesson 6: Add a ReportViewer Control to the Application](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md) </span></span>  
 <span data-ttu-id="0c503-121">[7 단원: 부모 보고서에 드릴스루 동작 추가](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md) </span><span class="sxs-lookup"><span data-stu-id="0c503-121">[Lesson 7: Add Drillthrough Action on Parent Report](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md) </span></span>  
 <span data-ttu-id="0c503-122">[8 단원: 데이터 필터 만들기](../reporting-services/lesson-8-create-a-data-filter.md) </span><span class="sxs-lookup"><span data-stu-id="0c503-122">[Lesson 8: Create a Data Filter](../reporting-services/lesson-8-create-a-data-filter.md) </span></span>  
 [<span data-ttu-id="0c503-123">9단원: 애플리케이션 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="0c503-123">Lesson 9: Build and Run the Application</span></span>](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c503-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0c503-124">See Also</span></span>  
 <span data-ttu-id="0c503-125">[SSRS를 &#40;Reporting Services 자습서&#41;](../reporting-services/reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0c503-125">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md) </span></span>  
 [<span data-ttu-id="0c503-126">보고서 디자이너로 보고서 디자인&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0c503-126">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
