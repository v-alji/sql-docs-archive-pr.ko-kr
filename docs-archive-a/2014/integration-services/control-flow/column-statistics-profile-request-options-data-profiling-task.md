---
title: 열 통계 프로필 요청 옵션(데이터 프로파일링 태스크) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 87205984-507a-49f3-b27c-36a0075c234d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9ce5c062a12e38d147f3cef95ea09b4c80f7c256
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650228"
---
# <a name="column-statistics-profile-request-options-data-profiling-task"></a><span data-ttu-id="ec337-102">열 통계 프로필 요청 옵션(데이터 프로파일링 태스크)</span><span class="sxs-lookup"><span data-stu-id="ec337-102">Column Statistics Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="ec337-103">**프로필 요청** 페이지의 **요청 속성** 창을 사용하여 요청 창에서 선택한 **열 통계 프로필 요청** 의 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Statistics Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="ec337-104">열 통계 프로필은 숫자 열의 최소값, 최대값, 평균, 표준 편차 및 `datetime` 열에 대한 최소값, 최대값과 같은 통계를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-104">A Column Statistics profile reports statistics such as minimum, maximum, average, and standard deviation for numeric columns, and minimum and maximum for `datetime` columns.</span></span> <span data-ttu-id="ec337-105">이 프로필을 사용하면 잘못된 날짜와 같은 데이터 문제를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-105">This profile can help you identify problems in your data such as invalid dates.</span></span> <span data-ttu-id="ec337-106">예를 들어 기록 날짜 열을 프로파일링하여 미래의 최대 날짜를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-106">For example, you profile a column of historical dates and discover a maximum date that is in the future.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec337-107">이 항목에서 설명하는 옵션은 **데이터 프로파일링 태스크 편집기** 의 **프로필 요청 페이지**에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-107">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="ec337-108">편집기의 이 페이지에 대한 자세한 내용은 [데이터 프로파일링 태스크 편집기&#40;프로필 요청 페이지&#41;](data-profiling-task-editor-profile-requests-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec337-108">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="ec337-109">데이터 프로파일링 태스크를 사용하는 방법에 대한 자세한 내용은 [데이터 프로파일링 태스크 설정](data-profiling-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec337-109">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="ec337-110">데이터 프로필 뷰어를 사용하여 데이터 프로파일링 태스크의 출력을 분석하는 방법에 대한 자세한 내용은 [데이터 프로필 뷰어](data-profile-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec337-110">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="ec337-111">요청 속성 옵션</span><span class="sxs-lookup"><span data-stu-id="ec337-111">Request Properties Options</span></span>  
 <span data-ttu-id="ec337-112">**열 통계 프로필 요청**에 대해 **요청 속성** 창에는 다음 옵션 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-112">For a **Column Statistics Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="ec337-113">**데이터**- **TableOrView** 및 **Column** 옵션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-113">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="ec337-114">**일반**</span><span class="sxs-lookup"><span data-stu-id="ec337-114">**General**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="ec337-115">데이터 옵션</span><span class="sxs-lookup"><span data-stu-id="ec337-115">Data Options</span></span>  
 <span data-ttu-id="ec337-116">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="ec337-116">**ConnectionManager**</span></span>  
 <span data-ttu-id="ec337-117">.NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient)를 사용하여 프로파일링할 테이블이나 뷰가 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-117">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="ec337-118">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="ec337-118">**TableOrView**</span></span>  
 <span data-ttu-id="ec337-119">프로파일링할 열이 포함된 기존 테이블이나 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-119">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="ec337-120">자세한 내용은 이 항목의 "TableorView 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec337-120">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="ec337-121">**열**</span><span class="sxs-lookup"><span data-stu-id="ec337-121">**Column**</span></span>  
 <span data-ttu-id="ec337-122">프로파일링할 기존 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-122">Select the existing column to be profiled.</span></span> <span data-ttu-id="ec337-123">모든 열을 프로파일링하려면 **(\*)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-123">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="ec337-124">자세한 내용은 이 항목의 "열 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ec337-124">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="ec337-125">TableOrView 옵션</span><span class="sxs-lookup"><span data-stu-id="ec337-125">TableOrView Options</span></span>  
 <span data-ttu-id="ec337-126">**스키마**</span><span class="sxs-lookup"><span data-stu-id="ec337-126">**Schema**</span></span>  
 <span data-ttu-id="ec337-127">선택한 테이블이 속해 있는 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-127">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="ec337-128">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-128">This option is read-only.</span></span>  
  
 <span data-ttu-id="ec337-129">**테이블**</span><span class="sxs-lookup"><span data-stu-id="ec337-129">**Table**</span></span>  
 <span data-ttu-id="ec337-130">선택한 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-130">Displays the name of the selected table.</span></span> <span data-ttu-id="ec337-131">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-131">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="ec337-132">열 옵션</span><span class="sxs-lookup"><span data-stu-id="ec337-132">Column Options</span></span>  
 <span data-ttu-id="ec337-133">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="ec337-133">**IsWildCard**</span></span>  
 <span data-ttu-id="ec337-134">**(\*)** 와일드카드가 선택되었는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-134">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="ec337-135">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 **True**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-135">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="ec337-136">프로파일링할 개별 열을 선택한 경우에는 **False** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-136">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="ec337-137">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-137">This option is read-only.</span></span>  
  
 <span data-ttu-id="ec337-138">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="ec337-138">**ColumnName**</span></span>  
 <span data-ttu-id="ec337-139">선택한 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-139">Displays the name of the selected column.</span></span> <span data-ttu-id="ec337-140">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-140">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="ec337-141">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="ec337-142">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="ec337-142">**StringCompareOptions**</span></span>  
 <span data-ttu-id="ec337-143">이 옵션은 열 통계 프로필에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-143">This option does not apply to the Column Statistics Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="ec337-144">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="ec337-144">General Options</span></span>  
 <span data-ttu-id="ec337-145">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="ec337-145">**RequestID**</span></span>  
 <span data-ttu-id="ec337-146">이 프로필 요청을 식별할 설명이 포함된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-146">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="ec337-147">일반적으로 자동 생성된 값은 변경하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec337-147">Typically, you do not have to change the autogenerated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec337-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec337-148">See Also</span></span>  
 <span data-ttu-id="ec337-149">[데이터 프로파일링 태스크 편집기&#40;일반 페이지&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="ec337-149">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="ec337-150">단일 테이블 빠른 프로필 형식&#40;데이터 프로파일링 태스크&#41;</span><span class="sxs-lookup"><span data-stu-id="ec337-150">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
