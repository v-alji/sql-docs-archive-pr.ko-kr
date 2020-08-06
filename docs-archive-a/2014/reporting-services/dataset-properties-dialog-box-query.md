---
title: 데이터 집합 속성 대화 상자, 쿼리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10160"
- sql12.rtp.rptdesigner.datasetproperties.query.f1
ms.assetid: 1fa34a4b-7de0-4e92-99fa-bc28a206773f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bffb14155d37e67333eb626747e1fcc54e618bbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660907"
---
# <a name="dataset-properties-dialog-box-query"></a><span data-ttu-id="20e9e-102">데이터 세트 속성 대화 상자, 쿼리</span><span class="sxs-lookup"><span data-stu-id="20e9e-102">Dataset Properties Dialog Box, Query</span></span>
  <span data-ttu-id="20e9e-103">데이터 **집합 속성** 대화 상자에서 **쿼리** 를 선택 하 여 데이터 원본을 선택 하 고 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-103">Select **Query** on the **Dataset Properties** dialog box to choose a data source and create a query.</span></span>  
  
 <span data-ttu-id="20e9e-104">**데이터 세트 속성** 대화 상자에는 다음과 같은 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-104">The **Dataset Properties** dialog box includes the following:</span></span>  
  
-   [<span data-ttu-id="20e9e-105">데이터 세트 속성 대화 상자, 매개 변수</span><span class="sxs-lookup"><span data-stu-id="20e9e-105">Dataset Properties Dialog Box, Parameters</span></span>](report-data/dataset-properties-dialog-box-parameters.md)  
  
-   [<span data-ttu-id="20e9e-106">데이터 세트 속성 대화 상자, 필드</span><span class="sxs-lookup"><span data-stu-id="20e9e-106">Dataset Properties Dialog Box, Fields</span></span>](../../2014/reporting-services/dataset-properties-dialog-box-fields.md)  
  
-   [<span data-ttu-id="20e9e-107">데이터 세트 속성 대화 상자, 옵션</span><span class="sxs-lookup"><span data-stu-id="20e9e-107">Dataset Properties Dialog Box, Options</span></span>](../../2014/reporting-services/dataset-properties-dialog-box-options.md)  
  
-   [<span data-ttu-id="20e9e-108">데이터 세트 속성 대화 상자, 필터</span><span class="sxs-lookup"><span data-stu-id="20e9e-108">Dataset Properties Dialog Box, Filters</span></span>](report-data/dataset-properties-dialog-box-filters.md)  
  
## <a name="options"></a><span data-ttu-id="20e9e-109">옵션</span><span class="sxs-lookup"><span data-stu-id="20e9e-109">Options</span></span>  
 <span data-ttu-id="20e9e-110">**이름**</span><span class="sxs-lookup"><span data-stu-id="20e9e-110">**Name**</span></span>  
 <span data-ttu-id="20e9e-111">데이터 세트의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-111">Type a name for the dataset.</span></span> <span data-ttu-id="20e9e-112">이 이름이 보고서의 다른 데이터 영역이나 그룹의 이름과 같아서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-112">The name cannot be the same as a name for any data region or group in the report.</span></span>  
  
 <span data-ttu-id="20e9e-113">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="20e9e-113">**Data Source**</span></span>  
 <span data-ttu-id="20e9e-114">데이터 세트의 기준이 되는 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-114">Select the data source on which to base the dataset.</span></span> <span data-ttu-id="20e9e-115">새 데이터 원본을 만들려면 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-115">To create a new data source, click **New**.</span></span>  
  
 <span data-ttu-id="20e9e-116">**쿼리 유형**</span><span class="sxs-lookup"><span data-stu-id="20e9e-116">**Query type**</span></span>  
 <span data-ttu-id="20e9e-117">데이터 세트에 사용할 명령 또는 쿼리의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-117">Select the type of command or query to use for the dataset.</span></span> <span data-ttu-id="20e9e-118">쿼리를 실행하여 데이터베이스에서 데이터를 검색하려면 **텍스트** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-118">Select **Text** to run a query to retrieve data from the database.</span></span> <span data-ttu-id="20e9e-119">**의** TableDirect **기능을 사용하여 테이블 내의 모든 필드를 선택하려면** 테이블 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-119">Select **Table** to use the **TableDirect** feature of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to select all the fields within a table.</span></span> <span data-ttu-id="20e9e-120">저장 프로시저를 이름으로 실행하려면 **저장 프로시저** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-120">Select **Stored Procedure** to run a stored procedure by name.</span></span> <span data-ttu-id="20e9e-121">기본값은**텍스트** 이며 대부분의 쿼리에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-121">**Text** is selected by default and is used for most queries.</span></span> <span data-ttu-id="20e9e-122">선택한 데이터 원본 쿼리를 편집하려면 **쿼리 디자이너**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-122">To edit the selected data source query, click **Query Designer**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20e9e-123">모든 데이터 원본에서 모든 쿼리 유형을 지원하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-123">Not all query types are supported by all data sources.</span></span> <span data-ttu-id="20e9e-124">예를 들어 **테이블** 은 데이터 원본 유형 **OLE DB** 와 **ODBC**에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-124">For example, **Table** is supported only by data source types **OLE DB** and **ODBC**.</span></span>  
  
 <span data-ttu-id="20e9e-125">**쿼리**</span><span class="sxs-lookup"><span data-stu-id="20e9e-125">**Query**</span></span>  
 <span data-ttu-id="20e9e-126">이 옵션은 **텍스트** 명령 유형 옵션을 선택하면 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-126">This option appears when you choose the **Text** command type option.</span></span> <span data-ttu-id="20e9e-127">쿼리를 입력하거나 **가져오기**를 클릭하여 이미 존재하는 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-127">Type a query or import a pre-existing query by clicking **Import**.</span></span> <span data-ttu-id="20e9e-128">식을 편집 하려면 **식** 단추 (*fx*)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-128">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20e9e-129">쿼리 디자이너를 사용하여 쿼리를 작성한 경우 쿼리의 텍스트가 이 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-129">If you used a query designer to build a query, the text of the query appears in this box.</span></span>  
  
 <span data-ttu-id="20e9e-130">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="20e9e-130">**Table name**</span></span>  
 <span data-ttu-id="20e9e-131">데이터 세트로 사용할 테이블의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-131">Enter the name of the table that you want to use as a dataset.</span></span> <span data-ttu-id="20e9e-132">이 옵션은 **테이블**을 선택하면 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-132">This option appears when you select **Table**.</span></span>  
  
 <span data-ttu-id="20e9e-133">**저장 프로시저 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="20e9e-133">**Select or enter stored procedure name**</span></span>  
 <span data-ttu-id="20e9e-134">사용할 저장 프로시저의 이름을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-134">Type or choose the name of the stored procedure that you want to use.</span></span> <span data-ttu-id="20e9e-135">식을 편집 하려면 **식** 단추 (*fx*)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-135">Click the **Expression** (*fx*) button to edit the expression.</span></span> <span data-ttu-id="20e9e-136">이 옵션은 저장 프로시저 명령 유형 옵션을 선택하면 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-136">This option appears when you choose the Stored Procedure command type option.</span></span>  
  
 <span data-ttu-id="20e9e-137">**제한 시간(초)**</span><span class="sxs-lookup"><span data-stu-id="20e9e-137">**Time out (in seconds)**</span></span>  
 <span data-ttu-id="20e9e-138">쿼리 시간이 초과 될 때 까지의 시간 (초)을 입력 합니다. 기본값은 30 초입니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-138">Type the number of seconds until the query times out. The default is 30 seconds.</span></span> <span data-ttu-id="20e9e-139">**제한 시간** 값은 비워 두거나 0보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-139">The value for **Time out** must be empty or greater than zero.</span></span> <span data-ttu-id="20e9e-140">값을 비워 두면 쿼리 시간이 제한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20e9e-140">If it is empty, the query does not time out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e9e-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20e9e-141">See Also</span></span>  
 <span data-ttu-id="20e9e-142">[Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="20e9e-142">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="20e9e-143">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="20e9e-143">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="20e9e-144">[쿼리 디자이너 &#40;보고서 작성기&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="20e9e-144">[Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span></span>  
 [<span data-ttu-id="20e9e-145">Reporting Services 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="20e9e-145">Reporting Services Query Designers</span></span>](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
