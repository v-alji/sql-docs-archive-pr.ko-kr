---
title: 열 길이 분포 프로필 요청 옵션(데이터 프로파일링 태스크) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 1a4de41f-f38d-40ea-ba1b-6c0ef67ea52a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4c0ebb6f1e0a6df2c0e47311f7b8217c5ce6f2df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650233"
---
# <a name="column-length-distribution-profile-request-options-data-profiling-task"></a><span data-ttu-id="0db43-102">열 길이 분포 프로필 요청 옵션(데이터 프로파일링 태스크)</span><span class="sxs-lookup"><span data-stu-id="0db43-102">Column Length Distribution Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="0db43-103">**프로필 요청** 페이지의 **요청 속성** 창을 사용하여 요청 창에서 선택한 **열 길이 분포 프로필 요청** 의 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Length Distribution Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="0db43-104">열 길이 분포 프로필은 선택한 열에 있는 문자열 값의 모든 고유 길이 및 각 길이가 나타내는 테이블 내 행의 비율을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-104">A Column Length Distribution profile reports all the distinct lengths of string values in the selected column and the percentage of rows in the table that each length represents.</span></span> <span data-ttu-id="0db43-105">이 프로필을 사용하면 잘못된 값과 같은 데이터 문제를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-105">This profile can help you identify problems in your data such as invalid values.</span></span> <span data-ttu-id="0db43-106">예를 들어 두 개의 문자로 구성된 미국 주 코드 열을 프로파일링하는 중 3자 이상의 값이 검색될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-106">For example, you profile a column of two-character United States state codes and discover values longer than two characters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0db43-107">이 항목에서 설명하는 옵션은 **데이터 프로파일링 태스크 편집기** 의 **프로필 요청 페이지**에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="0db43-108">편집기의 이 페이지에 대한 자세한 내용은 [데이터 프로파일링 태스크 편집기&#40;프로필 요청 페이지&#41;](data-profiling-task-editor-profile-requests-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0db43-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="0db43-109">데이터 프로파일링 태스크를 사용하는 방법에 대한 자세한 내용은 [데이터 프로파일링 태스크 설정](data-profiling-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0db43-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="0db43-110">데이터 프로필 뷰어를 사용하여 데이터 프로파일링 태스크의 출력을 분석하는 방법에 대한 자세한 내용은 [데이터 프로필 뷰어](data-profile-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0db43-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="0db43-111">요청 속성 옵션</span><span class="sxs-lookup"><span data-stu-id="0db43-111">Request Properties Options</span></span>  
 <span data-ttu-id="0db43-112">**열 길이 분포 프로필 요청**에 대해 **요청 속성** 창에는 다음 옵션 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-112">For a **Column Length Distribution Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="0db43-113">**데이터**- **TableOrView** 및 **Column** 옵션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="0db43-114">**일반**</span><span class="sxs-lookup"><span data-stu-id="0db43-114">**General**</span></span>  
  
-   <span data-ttu-id="0db43-115">**옵션**</span><span class="sxs-lookup"><span data-stu-id="0db43-115">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="0db43-116">데이터 옵션</span><span class="sxs-lookup"><span data-stu-id="0db43-116">Data Options</span></span>  
 <span data-ttu-id="0db43-117">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="0db43-117">**ConnectionManager**</span></span>  
 <span data-ttu-id="0db43-118">.NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient)를 사용하여 프로파일링할 테이블이나 뷰가 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-118">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="0db43-119">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="0db43-119">**TableOrView**</span></span>  
 <span data-ttu-id="0db43-120">프로파일링할 열이 포함된 기존 테이블이나 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-120">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="0db43-121">자세한 내용은 이 항목의 "TableorView 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0db43-121">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="0db43-122">**열**</span><span class="sxs-lookup"><span data-stu-id="0db43-122">**Column**</span></span>  
 <span data-ttu-id="0db43-123">프로파일링할 기존 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-123">Select the existing column to be profiled.</span></span> <span data-ttu-id="0db43-124">모든 열을 프로파일링하려면 **(\*)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-124">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="0db43-125">자세한 내용은 이 항목의 "열 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0db43-125">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="0db43-126">TableOrView 옵션</span><span class="sxs-lookup"><span data-stu-id="0db43-126">TableOrView Options</span></span>  
 <span data-ttu-id="0db43-127">**스키마**</span><span class="sxs-lookup"><span data-stu-id="0db43-127">**Schema**</span></span>  
 <span data-ttu-id="0db43-128">선택한 테이블이 속해 있는 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-128">Specify the schema to which the selected table belongs.</span></span> <span data-ttu-id="0db43-129">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-129">This option is read-only.</span></span>  
  
 <span data-ttu-id="0db43-130">**테이블**</span><span class="sxs-lookup"><span data-stu-id="0db43-130">**Table**</span></span>  
 <span data-ttu-id="0db43-131">선택한 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-131">Displays the name of the selected table.</span></span> <span data-ttu-id="0db43-132">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-132">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="0db43-133">열 옵션</span><span class="sxs-lookup"><span data-stu-id="0db43-133">Column Options</span></span>  
 <span data-ttu-id="0db43-134">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="0db43-134">**IsWildCard**</span></span>  
 <span data-ttu-id="0db43-135">**(\*)** 와일드카드가 선택되었는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-135">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="0db43-136">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 **True**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-136">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="0db43-137">프로파일링할 개별 열을 선택한 경우에는 **False** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-137">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="0db43-138">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-138">This option is read-only.</span></span>  
  
 <span data-ttu-id="0db43-139">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="0db43-139">**ColumnName**</span></span>  
 <span data-ttu-id="0db43-140">선택한 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-140">Displays the name of the selected column.</span></span> <span data-ttu-id="0db43-141">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-141">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="0db43-142">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-142">This option is read-only.</span></span>  
  
 <span data-ttu-id="0db43-143">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="0db43-143">**StringCompareOptions**</span></span>  
 <span data-ttu-id="0db43-144">이 옵션은 열 길이 분포 프로필에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-144">This option does not apply to the Column Length Distribution Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="0db43-145">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="0db43-145">General Options</span></span>  
 <span data-ttu-id="0db43-146">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="0db43-146">**RequestID**</span></span>  
 <span data-ttu-id="0db43-147">이 프로필 요청을 식별할 설명이 포함된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-147">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="0db43-148">일반적으로 자동 생성된 값은 변경하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-148">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="0db43-149">옵션</span><span class="sxs-lookup"><span data-stu-id="0db43-149">Options</span></span>  
 <span data-ttu-id="0db43-150">**IgnoreLeadingSpaces**</span><span class="sxs-lookup"><span data-stu-id="0db43-150">**IgnoreLeadingSpaces**</span></span>  
 <span data-ttu-id="0db43-151">프로필에서 문자열 값을 비교할 때 선행 공백을 무시해야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-151">Indicate whether to ignore leading spaces when the profile compares string values.</span></span> <span data-ttu-id="0db43-152">이 옵션의 기본값은 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-152">The default value of this option is **False**.</span></span>  
  
 <span data-ttu-id="0db43-153">**IgnoreTrailingSpaces**</span><span class="sxs-lookup"><span data-stu-id="0db43-153">**IgnoreTrailingSpaces**</span></span>  
 <span data-ttu-id="0db43-154">프로필에서 문자열 값을 비교할 때 후행 공백을 무시해야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-154">Indicate whether to ignore trailing spaces when the profile compares string values.</span></span> <span data-ttu-id="0db43-155">이 옵션의 기본값은 **True**입니다.</span><span class="sxs-lookup"><span data-stu-id="0db43-155">The default value of this option is **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db43-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0db43-156">See Also</span></span>  
 <span data-ttu-id="0db43-157">[데이터 프로파일링 태스크 편집기&#40;일반 페이지&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="0db43-157">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="0db43-158">단일 테이블 빠른 프로필 형식&#40;데이터 프로파일링 태스크&#41;</span><span class="sxs-lookup"><span data-stu-id="0db43-158">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
