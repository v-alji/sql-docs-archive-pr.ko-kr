---
title: 쿼리 작성기 (보고서 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.dataview.vdtquerydesigner.f1
- sql12.rtp.rptwizard.querybuilder.f1
helpviewer_keywords:
- Query Builder [Reporting Services]
ms.assetid: 1b0904ea-28c1-448e-b56c-c0fdfbc8b222
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34369bc72fadae75afbc93eb03c0e40509dd27a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639378"
---
# <a name="query-builder-report-wizard"></a><span data-ttu-id="2a3ef-102">쿼리 작성기(보고서 마법사)</span><span class="sxs-lookup"><span data-stu-id="2a3ef-102">Query Builder (Report Wizard)</span></span>
  <span data-ttu-id="2a3ef-103">쿼리 작성기를 사용하여 보고서에 사용할 결과 집합을 검색하는 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-103">Use the Query Builder to specify a query that retrieves a result set to use in a report.</span></span> <span data-ttu-id="2a3ef-104">다음과 같은 두 개의 쿼리 작성기 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-104">You can choose between two query builders:</span></span>  
  
-   <span data-ttu-id="2a3ef-105">쿼리를 지정하고 결과를 보기 위한 매우 단순한 작업 영역을 제공하는 텍스트 기반 쿼리 작성기(기본값).</span><span class="sxs-lookup"><span data-stu-id="2a3ef-105">The text-based query builder (default) provides a simple workspace for specifying a query and viewing the results.</span></span> <span data-ttu-id="2a3ef-106">여러 개의 [!INCLUDE[tsql](../includes/tsql-md.md)] 문, 사용자 지정 데이터 처리 확장 프로그램에 대한 쿼리 또는 명령 구문, 식으로 지정된 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-106">You can specify multiple [!INCLUDE[tsql](../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="2a3ef-107">일반 쿼리 작성기는 쿼리를 전처리하지 않고 모든 종류의 쿼리 구문을 포함할 수 있으므로 보고서 디자이너의 기본 쿼리 작성기 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-107">Because the generic query builder does not preprocess the query and can accommodate any kind of query syntax, it is the default query builder tool for Report Designer.</span></span>  
  
-   <span data-ttu-id="2a3ef-108">보다 뛰어난 화면을 제공하는 그래픽 쿼리 작성기.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-108">The graphical query builder provides a richer visual experience.</span></span> <span data-ttu-id="2a3ef-109">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 여러 부분에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-109">It is used in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] and in other parts of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2a3ef-110">식 또는 여러 부분으로 구성된 SQL 문을 작성하지 않는 경우 그래픽 쿼리 작성기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-110">You can use the graphical query builder if you are not creating expressions or multi-part SQL statements.</span></span>  
  
     <span data-ttu-id="2a3ef-111">그래픽 쿼리 작성기로 전환하려면 창의 왼쪽 위 모퉁이에 있는 **텍스트로 편집** 단추를 토글합니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-111">To switch to the graphical query builder, toggle the **Edit As Text** button in the top left corner of the window.</span></span>  
  
 <span data-ttu-id="2a3ef-112">또한 다른 보고서에서 쿼리를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-112">You can also import a query from another report.</span></span>  
  
## <a name="query-builder-options"></a><span data-ttu-id="2a3ef-113">쿼리 작성기 옵션</span><span class="sxs-lookup"><span data-stu-id="2a3ef-113">Query Builder Options</span></span>  
 <span data-ttu-id="2a3ef-114">**텍스트로 편집**</span><span class="sxs-lookup"><span data-stu-id="2a3ef-114">**Edit As Text**</span></span>  
 <span data-ttu-id="2a3ef-115">텍스트 기반 쿼리 디자이너와 그래픽 쿼리 디자이너가 모두 쿼리에 대해 작동하는 경우 이 두 디자이너 사이를 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-115">Toggles between the text-based and graphical query designers, if both will work for the query.</span></span>  
  
 <span data-ttu-id="2a3ef-116">**가져오기**</span><span class="sxs-lookup"><span data-stu-id="2a3ef-116">**Import**</span></span>  
 <span data-ttu-id="2a3ef-117">**쿼리 가져오기** 대화 상자를 열고 사용 가능한 모든 보고서에 대한 .rdl 및 .sql 파일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-117">Opens the **Import Query** dialog box and displays .rdl and .sql files for any available report.</span></span> <span data-ttu-id="2a3ef-118">가져온 쿼리를 그대로 사용하거나 쿼리 작성기에서 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-118">You can use the imported query as it is, or you can modify it in the query builder.</span></span>  
  
 <span data-ttu-id="2a3ef-119">**!(실행)**</span><span class="sxs-lookup"><span data-stu-id="2a3ef-119">**! (Run)**</span></span>  
 <span data-ttu-id="2a3ef-120">쿼리를 실행하고 쿼리가 유효한 경우 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-120">Runs the query and returns a result set if the query is valid.</span></span> <span data-ttu-id="2a3ef-121">쿼리가 식인 경우에는 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-121">Note that you cannot execute the query if it is an expression.</span></span> <span data-ttu-id="2a3ef-122">식 기반 쿼리인지 확인하려면 보고서 미리 보기를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-122">To verify an expression-based query, you must preview the report.</span></span>  
  
 <span data-ttu-id="2a3ef-123">**명령 유형**</span><span class="sxs-lookup"><span data-stu-id="2a3ef-123">**Command type**</span></span>  
 <span data-ttu-id="2a3ef-124">텍스트, 저장 프로시저 또는 테이블을 직접 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-124">Specifies text, stored procedure, or table direct.</span></span> <span data-ttu-id="2a3ef-125">명령 유형의 사용 가능 여부는 지정한 데이터 처리 확장 프로그램에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-125">Availability of a command type depends on the data processing extension you specified.</span></span>  
  
 <span data-ttu-id="2a3ef-126">**쿼리 창**</span><span class="sxs-lookup"><span data-stu-id="2a3ef-126">**Query pane**</span></span>  
 <span data-ttu-id="2a3ef-127">쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-127">Type the query.</span></span>  
  
 <span data-ttu-id="2a3ef-128">**결과 창**</span><span class="sxs-lookup"><span data-stu-id="2a3ef-128">**Result pane**</span></span>  
 <span data-ttu-id="2a3ef-129">쿼리에서 반환된 결과 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2a3ef-129">Shows the result set returned from the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a3ef-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a3ef-130">See Also</span></span>  
 <span data-ttu-id="2a3ef-131">[보고서 포함 된 데이터 집합 및 공유 데이터 집합 &#40;보고서 작성기 및 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2a3ef-131">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2a3ef-132">보고서 마법사 도움말</span><span class="sxs-lookup"><span data-stu-id="2a3ef-132">Report Wizard Help</span></span>](../../2014/reporting-services/report-wizard-help.md)  
  
  
