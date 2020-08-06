---
title: 열 Null 비율 프로필 요청 옵션(데이터 프로파일링 태스크) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 157ef8e4-fd23-4f81-8194-eebf74e9fd86
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e47c09a9a19eae4aed21c0c518430bc19a45648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650231"
---
# <a name="column-null-ratio-profile-request-options-data-profiling-task"></a><span data-ttu-id="66fd4-102">열 Null 비율 프로필 요청 옵션(데이터 프로파일링 태스크)</span><span class="sxs-lookup"><span data-stu-id="66fd4-102">Column Null Ratio Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="66fd4-103">**프로필 요청** 페이지의 **요청 속성** 창을 사용하여 요청 창에서 선택한 **열 Null 비율 프로필 요청** 의 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Null Ratio Request** selected in the requests pane.</span></span> <span data-ttu-id="66fd4-104">열 Null 비율 프로필은 선택한 열에 있는 Null 값의 비율을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-104">A Column Null Ratio profile reports the percentage of null values in the selected column.</span></span> <span data-ttu-id="66fd4-105">이 프로필을 사용하면 예기치 않게 높은 열 내 Null 값의 비율과 같은 데이터 문제를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-105">This profile can help you identify problems in your data such as an unexpectedly high ratio of null values in a column.</span></span> <span data-ttu-id="66fd4-106">예를 들어 열 Null 비율 프로필은 ZIP Code/Postal Code 열을 프로파일링하는 중 허용 불가능한 수준으로 높은 누락된 코드 비율을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-106">For example, a Column Null Ratio profile can profile a ZIP Code/Postal Code column and discover an unacceptably high percentage of missing postal codes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66fd4-107">이 항목에서 설명하는 옵션은 **데이터 프로파일링 태스크 편집기** 의 **프로필 요청 페이지**에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="66fd4-108">편집기의 이 페이지에 대한 자세한 내용은 [데이터 프로파일링 태스크 편집기&#40;프로필 요청 페이지&#41;](data-profiling-task-editor-profile-requests-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66fd4-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="66fd4-109">데이터 프로파일링 태스크를 사용하는 방법에 대한 자세한 내용은 [데이터 프로파일링 태스크 설정](data-profiling-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66fd4-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="66fd4-110">데이터 프로필 뷰어를 사용하여 데이터 프로파일링 태스크의 출력을 분석하는 방법에 대한 자세한 내용은 [데이터 프로필 뷰어](data-profile-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66fd4-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="66fd4-111">요청 속성 옵션</span><span class="sxs-lookup"><span data-stu-id="66fd4-111">Request Properties Options</span></span>  
 <span data-ttu-id="66fd4-112">**열 Null 비율 프로필 요청**에 대해 **요청 속성** 창에는 다음 옵션 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-112">For a **Column Null Ratio Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="66fd4-113">**데이터**- **TableOrView** 및 **Column** 옵션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="66fd4-114">**일반**</span><span class="sxs-lookup"><span data-stu-id="66fd4-114">**General**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="66fd4-115">데이터 옵션</span><span class="sxs-lookup"><span data-stu-id="66fd4-115">Data Options</span></span>  
 <span data-ttu-id="66fd4-116">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="66fd4-116">**ConnectionManager**</span></span>  
 <span data-ttu-id="66fd4-117">.NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient)를 사용하여 프로파일링할 테이블이나 뷰가 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-117">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="66fd4-118">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="66fd4-118">**TableOrView**</span></span>  
 <span data-ttu-id="66fd4-119">프로파일링할 열이 포함된 기존 테이블이나 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-119">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="66fd4-120">자세한 내용은 이 항목의 "TableorView 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="66fd4-120">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="66fd4-121">**열**</span><span class="sxs-lookup"><span data-stu-id="66fd4-121">**Column**</span></span>  
 <span data-ttu-id="66fd4-122">프로파일링할 기존 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-122">Select the existing column to be profiled.</span></span> <span data-ttu-id="66fd4-123">모든 열을 프로파일링하려면 **(\*)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-123">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="66fd4-124">자세한 내용은 이 항목의 "열 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="66fd4-124">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="66fd4-125">TableOrView 옵션</span><span class="sxs-lookup"><span data-stu-id="66fd4-125">TableOrView Options</span></span>  
 <span data-ttu-id="66fd4-126">**스키마**</span><span class="sxs-lookup"><span data-stu-id="66fd4-126">**Schema**</span></span>  
 <span data-ttu-id="66fd4-127">선택한 테이블이 속해 있는 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-127">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="66fd4-128">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-128">This option is read-only.</span></span>  
  
 <span data-ttu-id="66fd4-129">**테이블**</span><span class="sxs-lookup"><span data-stu-id="66fd4-129">**Table**</span></span>  
 <span data-ttu-id="66fd4-130">선택한 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-130">Displays the name of the selected table.</span></span> <span data-ttu-id="66fd4-131">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-131">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="66fd4-132">열 옵션</span><span class="sxs-lookup"><span data-stu-id="66fd4-132">Column Options</span></span>  
 <span data-ttu-id="66fd4-133">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="66fd4-133">**IsWildCard**</span></span>  
 <span data-ttu-id="66fd4-134">**(\*)** 와일드카드가 선택되었는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-134">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="66fd4-135">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 **True**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-135">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="66fd4-136">프로파일링할 개별 열을 선택한 경우에는 **False** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-136">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="66fd4-137">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-137">This option is read-only.</span></span>  
  
 <span data-ttu-id="66fd4-138">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="66fd4-138">**ColumnName**</span></span>  
 <span data-ttu-id="66fd4-139">선택한 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-139">Displays the name of the selected column.</span></span> <span data-ttu-id="66fd4-140">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-140">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="66fd4-141">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="66fd4-142">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="66fd4-142">**StringCompareOptions**</span></span>  
 <span data-ttu-id="66fd4-143">이 옵션은 열 Null 비율 프로필에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-143">This option does not apply to the Column Null Ratio Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="66fd4-144">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="66fd4-144">General Options</span></span>  
 <span data-ttu-id="66fd4-145">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="66fd4-145">**RequestID**</span></span>  
 <span data-ttu-id="66fd4-146">이 프로필 요청을 식별할 설명이 포함된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-146">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="66fd4-147">일반적으로 자동 생성된 값은 변경하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66fd4-147">Typically, you do not have to change the autogenerated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66fd4-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66fd4-148">See Also</span></span>  
 <span data-ttu-id="66fd4-149">[데이터 프로파일링 태스크 편집기&#40;일반 페이지&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="66fd4-149">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="66fd4-150">단일 테이블 빠른 프로필 형식&#40;데이터 프로파일링 태스크&#41;</span><span class="sxs-lookup"><span data-stu-id="66fd4-150">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
