---
title: Management Studio의 사용자 지정 보고서 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.summary.new.custom.report.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 1ba3f758-f39b-4f5f-91ca-516cedc78979
author: stevestein
ms.author: sstein
ms.openlocfilehash: bc93157100738610c8576f0af40e75613c3cff62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638523"
---
# <a name="custom-reports-in-management-studio"></a><span data-ttu-id="98bdb-102">Management Studio의 사용자 지정 보고서</span><span class="sxs-lookup"><span data-stu-id="98bdb-102">Custom Reports in Management Studio</span></span>
  <span data-ttu-id="98bdb-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 많은 개체 탐색기 노드에는 [!INCLUDE[msCoName](../../includes/msconame-md.md)]에서 만든 표준 보고서 집합이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-103">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], many Object Explorer nodes display a set of standard reports that are created by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span> <span data-ttu-id="98bdb-104">이러한 보고서는 일반적으로 요청되는 서버 정보를 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-104">These reports summarize typically requested server information.</span></span> <span data-ttu-id="98bdb-105">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 서비스 팩 2부터 관리자는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용하여 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 만든 사용자 지정 보고서를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-105">Starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2, administrators can run custom reports that were created in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] from [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="98bdb-106">구현</span><span class="sxs-lookup"><span data-stu-id="98bdb-106">Implementation</span></span>  
 <span data-ttu-id="98bdb-107">사용자 지정 보고서는 보고서 정의 파일(.rdl)로 저장되며 RDL(Report Definition Language)을 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-107">Custom reports are stored as report definition (.rdl) files and are created by using Report Definition Language (RDL).</span></span> <span data-ttu-id="98bdb-108">RDL에는 보고서에 대한 데이터 검색 및 레이아웃 정보가 XML 형식으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-108">RDL contains data retrieval and layout information for a report in an XML format.</span></span> <span data-ttu-id="98bdb-109">RDL은 개방형 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-109">RDL is an open schema.</span></span> <span data-ttu-id="98bdb-110">개발자는 추가 특성 및 요소를 사용하여 RDL을 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-110">Developers can extend RDL with additional attributes and elements.</span></span> <span data-ttu-id="98bdb-111">보고서는 보고서 내의 모든 유효한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-111">Reports can execute any valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within the report.</span></span>  
  
 <span data-ttu-id="98bdb-112">개체 탐색기가 서버에 연결되어 있는 경우 사용자 지정 보고서가 현재 개체 탐색기 노드의 보고서 매개 변수를 참조하면 사용자 지정 보고서를 해당 노드의 컨텍스트에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-112">If Object Explorer is connected to a server, custom reports can execute in the context of the current Object Explorer selection if the reports reference report parameters of that node.</span></span> <span data-ttu-id="98bdb-113">이렇게 하면 보고서가 현재 컨텍스트(예: 현재 데이터베이스)나 일관된 컨텍스트(예: 지정된 데이터베이스를 사용자 지정 보고서에 포함된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 일부로 지정)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-113">This enables a report to use the current context, such as the current database; or a consistent context, such as specifying a designated database as part of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that is contained in the custom report.</span></span>  
  
## <a name="running-a-custom-report"></a><span data-ttu-id="98bdb-114">사용자 지정 보고서 실행</span><span class="sxs-lookup"><span data-stu-id="98bdb-114">Running a Custom Report</span></span>  
 <span data-ttu-id="98bdb-115">다음과 같은 방법으로 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 사용자 지정 보고서를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-115">You can run a custom report in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="98bdb-116">개체 탐색기의 노드를 마우스 오른쪽 단추로 클릭하고 **보고서** 를 가리킨 다음 **사용자 지정 보고서**를 마우스 왼쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-116">Right-click a node in Object Explorer, point to **Reports** and left-click **Custom Reports**.</span></span> <span data-ttu-id="98bdb-117">**파일 열기** 대화 상자에서 .rdl 파일이 포함된 폴더를 찾은 다음 적절한 보고서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-117">In the **Open File** dialog box, locate a folder that contains .rdl files, and then open the appropriate report file.</span></span>  
  
-   <span data-ttu-id="98bdb-118">개체 탐색기의 노드를 마우스 오른쪽 단추로 클릭하고 **보고서**, **사용자 지정 보고서**를 차례로 가리킨 다음 가장 최근에 사용한 파일 목록에서 사용자 지정 보고서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-118">Right-click a node in Object Explorer, point to **Reports**, point to **Custom Reports**, and then select a custom report from the most recently used file list.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="98bdb-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="98bdb-119">Limitations</span></span>  
 <span data-ttu-id="98bdb-120">사용자 지정 보고서를 사용할 때는 다음과 같은 제한 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-120">When you work with custom reports, consider the following limitations:</span></span>  
  
-   <span data-ttu-id="98bdb-121">악의적인 코드를 실수로 실행할 수 있으므로 .rdl 파일이 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 와 연결되도록 파일 시스템을 구성한 경우에도 보고서를 자동으로 실행하도록 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-121">To prevent the unintended execution of malicious code, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] cannot be configured to automatically run a report, even if the file system is configured to associate .rdl files with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="98bdb-122">보고서는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 프로그래밍 방식으로 실행할 수 없으며 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 통해 명령줄에서 실행할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-122">Reports cannot be programmatically executed in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and cannot run from the command line through [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="98bdb-123">예상한 값을 산출하지 않는 컨텍스트에서 사용자 지정 보고서를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-123">You can run custom reports in a context that does not produce the expected values.</span></span> <span data-ttu-id="98bdb-124">예를 들어 복제와 관련되지 않은 데이터베이스의 컨텍스트에서 복제에 대한 보고서를 실행하거나 정확한 보고서를 생성하는 데 필요한 정보에 대한 액세스 권한이 없는 사용자로 보고서를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-124">For example, you can run a report about replication in the context of a database that is not involved in replication, or run a report as a user who does not have permission to access information that is required to generate an accurate report.</span></span> <span data-ttu-id="98bdb-125">사용자 지정 보고서의 작성자는 보고서 구조와 해당 컨텍스트의 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-125">The creator of the custom report is responsible for the validity of the report structure and its context.</span></span>  
  
-   <span data-ttu-id="98bdb-126">사용자 지정 보고서는 표준 보고서 목록에 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-126">You cannot add a custom report to the list of standard reports.</span></span>  
  
-   <span data-ttu-id="98bdb-127">보고서에서 처리하는 코드는 서버 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-127">The code processed by the report might affect server performance.</span></span>  
  
-   <span data-ttu-id="98bdb-128">사용자 지정 보고서는 하위 보고서를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-128">Custom reports will not support subreports.</span></span>  
  
-   <span data-ttu-id="98bdb-129">보고서 내의 각 쿼리에 대한 명령 텍스트는 식을 통해 정의하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-129">The command text for each query within the report must not be defined through an expression.</span></span>  
  
-   <span data-ttu-id="98bdb-130">명령(쿼리)에 사용되는 모든 쿼리 매개 변수는 단일 보고서 매개 변수만 참조할 수 있으며 식 연산자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-130">Any query parameter that is used in a command (query) can only reference a single report parameter and cannot use any expression operators.</span></span>  
  
-   <span data-ttu-id="98bdb-131">Text 및 StoredProcedure 명령 유형만 보고서 명령(쿼리)에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-131">Only Text and Stored Procedure command types are supported for report commands (queries).</span></span>  
  
-   <span data-ttu-id="98bdb-132">보고서 프레임워크는 쿼리에 대해 매개 변수 이스케이프를 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-132">The report framework does not provide any parameter escaping for the queries.</span></span> <span data-ttu-id="98bdb-133">쿼리 작성자는 쿼리가 SQL 인젝션 공격으로부터 안전한지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-133">Query authors must make sure that their queries are free from SQL injection attacks.</span></span>  
  
## <a name="managing-custom-reports"></a><span data-ttu-id="98bdb-134">사용자 지정 보고서 관리</span><span class="sxs-lookup"><span data-stu-id="98bdb-134">Managing Custom Reports</span></span>  
 <span data-ttu-id="98bdb-135">많은 사용자 지정 보고서를 보유하고 있는 사용자의 경우 적절한 NTFS 파일 시스템 권한이 있는 파일 시스템 폴더를 사용하여 보고서를 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-135">We recommend that users who have many custom reports organize them by using file system folders that have appropriate NTFS file system permissions.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="98bdb-136">사용 권한</span><span class="sxs-lookup"><span data-stu-id="98bdb-136">Permissions</span></span>  
 <span data-ttu-id="98bdb-137">사용자 지정 보고서는 현재 사용자의 사용 권한을 사용하여 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-137">Custom reports run by using the permissions of the current user.</span></span> <span data-ttu-id="98bdb-138">보고서에서 실행하는 쿼리를 악의적인 사용자가 변경하지 못하게 하려면 보고서 파일이 있는 파일 시스템 폴더에 대한 액세스가 제한되도록 사용 권한을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-138">To prevent a malicious user from changing the queries run by the report, permissions on the file system folder that contains the report files should be set to restrict access.</span></span>  
  
 <span data-ttu-id="98bdb-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스에 사용되는 사용자와 계정 모두에는 보고서 파일이 있는 파일 시스템 폴더에 대한 읽기 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-139">Both the user and the account that is used by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service require read access to the file system folder that contains the report files.</span></span>  
  
 <span data-ttu-id="98bdb-140">유효한 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 명령은 보고서에 포함할 수 있지만 명령이 실행되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-140">Any valid [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] command can be embedded in a report, but the command will not be executed.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="98bdb-141">유효한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 보고서에 포함할 수 있으며 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-141">Any valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be embedded in and executed from a report.</span></span> <span data-ttu-id="98bdb-142">권한이 높은 사용자 계정에서 보고서를 실행하면 포함된 모든 명령을 문제 없이 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98bdb-142">Running a report under a high-privileged user account makes it possible for any of these embedded instructions to execute without challenge.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="98bdb-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98bdb-143">See Also</span></span>  
 <span data-ttu-id="98bdb-144">[Management Studio에 사용자 지정 보고서 추가](add-a-custom-report-to-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="98bdb-144">[Add a Custom Report to Management Studio](add-a-custom-report-to-management-studio.md) </span></span>  
 <span data-ttu-id="98bdb-145">[표시 사용자 지정 보고서 경고 실행](unsuppress-run-custom-report-warnings.md) </span><span class="sxs-lookup"><span data-stu-id="98bdb-145">[Unsuppress Run Custom Report Warnings](unsuppress-run-custom-report-warnings.md) </span></span>  
 [<span data-ttu-id="98bdb-146">개체 탐색기 노드 속성과 함께 사용자 지정 보고서 사용</span><span class="sxs-lookup"><span data-stu-id="98bdb-146">Use Custom Reports with Object Explorer Node Properties</span></span>](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
