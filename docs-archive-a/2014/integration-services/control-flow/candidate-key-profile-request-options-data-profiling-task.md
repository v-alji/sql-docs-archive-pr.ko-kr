---
title: 후보 키 프로필 요청 옵션(데이터 프로파일링 태스크) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 8632dbc4-4394-4dc7-b19c-f9adeb21ba52
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86d7135059a315ad6504beb8e7a9408ef20e4fcc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647800"
---
# <a name="candidate-key-profile-request-options-data-profiling-task"></a><span data-ttu-id="dfc4e-102">후보 키 프로필 요청 옵션(데이터 프로파일링 태스크)</span><span class="sxs-lookup"><span data-stu-id="dfc4e-102">Candidate Key Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="dfc4e-103">**프로필 요청** 페이지의 **요청 속성** 창을 사용하여 요청 창에서 선택한 **후보 키 프로필 요청** 의 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Candidate Key Profile Request** that is selected in the requests pane.</span></span> <span data-ttu-id="dfc4e-104">후보 키 프로필은 열 또는 열 집합이 선택한 테이블에 대해 키, 아니면 근사 키인지 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-104">A Candidate Key profile reports whether a column or set of columns is a key, or an approximate key, for the selected table.</span></span> <span data-ttu-id="dfc4e-105">또한 이 프로필을 사용하면 잠재적 키 열의 중복 값과 같은 데이터 문제를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-105">This profile can also help you identify problems in your data such as duplicate values in a potential key column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfc4e-106">이 항목에서 설명하는 옵션은 **데이터 프로파일링 태스크 편집기** 의 **프로필 요청 페이지**에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-106">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="dfc4e-107">편집기의 이 페이지에 대한 자세한 내용은 [데이터 프로파일링 태스크 편집기&#40;프로필 요청 페이지&#41;](data-profiling-task-editor-profile-requests-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-107">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="dfc4e-108">데이터 프로파일링 태스크를 사용하는 방법에 대한 자세한 내용은 [데이터 프로파일링 태스크 설정](data-profiling-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-108">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="dfc4e-109">데이터 프로필 뷰어를 사용하여 데이터 프로파일링 태스크의 출력을 분석하는 방법에 대한 자세한 내용은 [데이터 프로필 뷰어](data-profile-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-109">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-selection-of-columns-for-the-keycolumns-property"></a><span data-ttu-id="dfc4e-110">KeyColumns 속성에 대한 열 선택 이해</span><span class="sxs-lookup"><span data-stu-id="dfc4e-110">Understanding the Selection of Columns for the KeyColumns Property</span></span>  
 <span data-ttu-id="dfc4e-111">각 **후보 키 프로필 요청** 은 단일 열 또는 여러 열로 구성된 단일 키 후보의 키 수준을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-111">Each **Candidate Key Profile Request** computes the key strength of a single key candidate that consists of a single column or of multiple columns:</span></span>  
  
-   <span data-ttu-id="dfc4e-112">**KeyColumns**에서 한 열만 선택하면 태스크에서는 이 한 열의 키 수준을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-112">When you select only one column in **KeyColumns**, the task computes the key strength of that one column.</span></span>  
  
-   <span data-ttu-id="dfc4e-113">**KeyColumns**에서 여러 열을 선택하면 태스크에서는 선택한 모든 열로 구성된 복합 키의 키 수준을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-113">When you select multiple columns in **KeyColumns**, the task computes the key strength of the composite key that consists of all the selected columns.</span></span>  
  
-   <span data-ttu-id="dfc4e-114">**KeyColumns**에서 와일드카드 문자 **(\*)** 를 선택하면 태스크에서는 테이블 또는 뷰에 있는 각 열의 키 수준을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-114">When you select the wildcard character, **(\*)**, in **KeyColumns**, the task computers the key strength of each column in the table or view.</span></span>  
  
 <span data-ttu-id="dfc4e-115">예를 들어 열 A, B, C를 포함하는 예제 테이블의 경우 **KeyColumns**에 대해 다음과 같이 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-115">For example, consider a sample table that contains columns A, B, and C. You make the following selections for **KeyColumns**:</span></span>  
  
-   <span data-ttu-id="dfc4e-116">\*KeyColumns **에서 (** ) 및 열 C를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-116">You select (\*) and column C in **KeyColumns**.</span></span> <span data-ttu-id="dfc4e-117">태스크에서는 열 C의 키 수준을 계산한 다음 복합 키 후보 (A, C) 및 (B, C)의 키 수준을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-117">The task computes the key strength of column C, and then of composite key candidates (A, C) and (B, C).</span></span>  
  
-   <span data-ttu-id="dfc4e-118">\*KeyColumns\*에서 ( **) 및 (** )를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-118">You select (\*) and (\*) in **KeyColumns**.</span></span> <span data-ttu-id="dfc4e-119">태스크에서는 개별 열 A, B, C의 키 수준을 계산한 다음 복합 키 후보 (A, B), (A, C) 및 (B, C)의 키 수준을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-119">The task computes the key strength of individual columns A, B, and C, and then of composite key candidates (A, B), (A, C) and (B, C).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfc4e-120">(\*)를 선택하는 경우 이 옵션으로 인해 계산이 많이 발생하여 태스크의 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-120">If you select (\*), this option might result in a large number of computations and decrease the performance of the task.</span></span> <span data-ttu-id="dfc4e-121">그러나 태스크에서 키의 임계값을 만족하는 하위 집합을 찾으면 추가 조합을 분석하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-121">However, if the task finds a subset that satisfies the threshold for a key, the task does not analyze additional combinations.</span></span> <span data-ttu-id="dfc4e-122">예를 들어 위에서 설명한 예제 테이블의 태스크에서 열 C가 키임을 확인하면 복합 키 후보를 더 이상 분석하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-122">For example, in the sample table described above, if the task determines that column C is a key, the task does not continue to analyze the composite key candidates.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="dfc4e-123">요청 속성 옵션</span><span class="sxs-lookup"><span data-stu-id="dfc4e-123">Request Properties Options</span></span>  
 <span data-ttu-id="dfc4e-124">**후보 키 프로필 요청**에 대해 **요청 속성** 창에는 다음 옵션 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-124">For a **Candidate Key Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="dfc4e-125">**데이터**- **TableOrView** 및 **KeyColumns** 옵션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-125">**Data**, which includes the **TableOrView** and **KeyColumns** options</span></span>  
  
-   <span data-ttu-id="dfc4e-126">**일반**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-126">**General**</span></span>  
  
-   <span data-ttu-id="dfc4e-127">**옵션**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-127">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="dfc4e-128">데이터 옵션</span><span class="sxs-lookup"><span data-stu-id="dfc4e-128">Data Options</span></span>  
 <span data-ttu-id="dfc4e-129">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-129">**ConnectionManager**</span></span>  
 <span data-ttu-id="dfc4e-130">.NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient)를 사용하여 프로파일링할 테이블이나 뷰가 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-130">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="dfc4e-131">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-131">**TableOrView**</span></span>  
 <span data-ttu-id="dfc4e-132">프로파일링할 기존 테이블이나 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-132">Select the existing table or view to be profiled.</span></span>  
  
 <span data-ttu-id="dfc4e-133">자세한 내용은 이 항목의 "TableorView 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-133">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="dfc4e-134">**KeyColumns**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-134">**KeyColumns**</span></span>  
 <span data-ttu-id="dfc4e-135">프로파일링할 기존 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-135">Select the existing column or columns to be profiled.</span></span> <span data-ttu-id="dfc4e-136">모든 열을 프로파일링하려면 **(\*)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-136">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="dfc4e-137">자세한 내용은 이 항목의 "KeyColumns 속성에 대한 열 선택 이해" 및 "KeyColumns 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-137">For more information, see the sections, "Understanding the Selection of Columns for the KeyColumns Property" and "KeyColumns Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="dfc4e-138">TableOrView 옵션</span><span class="sxs-lookup"><span data-stu-id="dfc4e-138">TableOrView Options</span></span>  
 <span data-ttu-id="dfc4e-139">**스키마**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-139">**Schema**</span></span>  
 <span data-ttu-id="dfc4e-140">선택한 테이블이 속해 있는 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-140">Specify the schema to which the selected table belongs.</span></span> <span data-ttu-id="dfc4e-141">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-141">This option is read-only.</span></span>  
  
 <span data-ttu-id="dfc4e-142">**테이블**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-142">**Table**</span></span>  
 <span data-ttu-id="dfc4e-143">선택한 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-143">Displays the name of the selected table.</span></span> <span data-ttu-id="dfc4e-144">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-144">This option is read-only.</span></span>  
  
#### <a name="keycolumns-options"></a><span data-ttu-id="dfc4e-145">KeyColumns 옵션</span><span class="sxs-lookup"><span data-stu-id="dfc4e-145">KeyColumns Options</span></span>  
 <span data-ttu-id="dfc4e-146">**KeyColumns**에서 프로파일링 또는 **(\*)** 옵션을 대상으로 선택한 각 열에 대해 다음 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-146">The following options are presented for each column selected for profiling in **KeyColumns**, or for the **(\*)** option.</span></span>  
  
 <span data-ttu-id="dfc4e-147">자세한 내용은 이 항목의 앞부분에 나오는 "KeyColumns 속성에 대한 열 선택 이해" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-147">For more information, see the section, "Understanding the Selection of Columns for the KeyColumns Property," earlier in this topic.</span></span>  
  
 <span data-ttu-id="dfc4e-148">**IsWildcard**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-148">**IsWildcard**</span></span>  
 <span data-ttu-id="dfc4e-149">**(\*)** 와일드카드가 선택되었는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-149">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="dfc4e-150">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 **True**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-150">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="dfc4e-151">프로파일링할 개별 열을 선택한 경우에는 **False** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-151">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="dfc4e-152">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-152">This option is read-only.</span></span>  
  
 <span data-ttu-id="dfc4e-153">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-153">**ColumnName**</span></span>  
 <span data-ttu-id="dfc4e-154">선택한 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-154">Displays the name of the selected column.</span></span> <span data-ttu-id="dfc4e-155">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-155">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="dfc4e-156">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-156">This option is read-only.</span></span>  
  
 <span data-ttu-id="dfc4e-157">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-157">**StringCompareOptions**</span></span>  
 <span data-ttu-id="dfc4e-158">문자열 값을 비교할 수 있는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-158">Select options for comparing string values.</span></span> <span data-ttu-id="dfc4e-159">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-159">This property has the options listed in the following table.</span></span> <span data-ttu-id="dfc4e-160">이 옵션의 기본값은 **Default**입니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-160">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfc4e-161">**ColumnName**에 대해 **(\*)** 와일드카드를 사용하는 경우 **CompareOptions**는 읽기 전용이며 **Default** 설정으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-161">When you use a **(\*)** wildcard for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="dfc4e-162">값</span><span class="sxs-lookup"><span data-stu-id="dfc4e-162">Value</span></span>|<span data-ttu-id="dfc4e-163">Description</span><span class="sxs-lookup"><span data-stu-id="dfc4e-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dfc4e-164">**기본값**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-164">**Default**</span></span>|<span data-ttu-id="dfc4e-165">원본 테이블에서 열의 데이터 정렬을 기준으로 데이터를 정렬 및 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-165">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="dfc4e-166">**BinarySort**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-166">**BinarySort**</span></span>|<span data-ttu-id="dfc4e-167">각 문자에 대해 정의된 비트 패턴을 기준으로 데이터를 정렬 및 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-167">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="dfc4e-168">이진 정렬 순서는 대/소문자와 악센트를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-168">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="dfc4e-169">이진은 가장 빠른 정렬 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-169">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="dfc4e-170">**DictionarySort**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-170">**DictionarySort**</span></span>|<span data-ttu-id="dfc4e-171">관련된 언어 또는 알파벳에 대해 사전에 정의된 정렬 및 비교 규칙에 따라 데이터를 정렬 및 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-171">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="dfc4e-172">**DictionarySort**를 선택하는 경우 다음 테이블에 나열된 옵션 조합을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-172">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="dfc4e-173">이러한 추가 옵션은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-173">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="dfc4e-174">값</span><span class="sxs-lookup"><span data-stu-id="dfc4e-174">Value</span></span>|<span data-ttu-id="dfc4e-175">Description</span><span class="sxs-lookup"><span data-stu-id="dfc4e-175">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dfc4e-176">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-176">**IgnoreCase**</span></span>|<span data-ttu-id="dfc4e-177">비교 시 대문자와 소문자를 구분할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-177">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="dfc4e-178">이 옵션을 설정하면 문자열 비교 시 대/소문자가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-178">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="dfc4e-179">예를 들어 "ABC"는 "abc"와 동일하게 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-179">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="dfc4e-180">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-180">**IgnoreNonSpace**</span></span>|<span data-ttu-id="dfc4e-181">비교 시 공백 문자와 분음 기호를 구분할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-181">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="dfc4e-182">이 옵션을 설정하면 비교 시 분음 기호가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-182">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="dfc4e-183">예를 들어 "å"와 "a"는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-183">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="dfc4e-184">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-184">**IgnoreKanaType**</span></span>|<span data-ttu-id="dfc4e-185">비교 시 두 가지 형식의 일본어 가나 문자인 히라가나와 가타가나를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-185">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="dfc4e-186">이 옵션을 설정하면 문자열 비교 시 가나 형식이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-186">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="dfc4e-187">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-187">**IgnoreWidth**</span></span>|<span data-ttu-id="dfc4e-188">비교 시 싱글바이트 문자와 동일 문자의 더블바이트 문자 표현을 구분할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-188">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="dfc4e-189">이 옵션을 설정하면 문자열 비교 시 동일 문자에 대한 싱글바이트 표현과 더블바이트 표현이 동일하게 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-189">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="dfc4e-190">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="dfc4e-190">General Options</span></span>  
 <span data-ttu-id="dfc4e-191">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-191">**RequestID**</span></span>  
 <span data-ttu-id="dfc4e-192">이 프로필 요청을 식별할 설명이 포함된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-192">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="dfc4e-193">일반적으로 자동 생성된 값은 변경하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-193">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="dfc4e-194">옵션</span><span class="sxs-lookup"><span data-stu-id="dfc4e-194">Options</span></span>  
 <span data-ttu-id="dfc4e-195">**ThresholdSetting**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-195">**ThresholdSetting**</span></span>  
 <span data-ttu-id="dfc4e-196">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-196">This property has the options listed in the following table.</span></span> <span data-ttu-id="dfc4e-197">이 속성의 기본값은 **Specified**입니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-197">The default value of this property is **Specified**.</span></span>  
  
|<span data-ttu-id="dfc4e-198">값</span><span class="sxs-lookup"><span data-stu-id="dfc4e-198">Value</span></span>|<span data-ttu-id="dfc4e-199">Description</span><span class="sxs-lookup"><span data-stu-id="dfc4e-199">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dfc4e-200">**없음**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-200">**None**</span></span>|<span data-ttu-id="dfc4e-201">임계값이 지정되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-201">No threshold is specified.</span></span> <span data-ttu-id="dfc4e-202">키 수준은 해당 값에 관계없이 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-202">The key strength is reported regardless of its value.</span></span>|  
|<span data-ttu-id="dfc4e-203">**Specified**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-203">**Specified**</span></span>|<span data-ttu-id="dfc4e-204">임계값이 **KeyStrengthThreshold**에 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-204">A threshold is specified in **KeyStrengthThreshold**.</span></span> <span data-ttu-id="dfc4e-205">키 수준이 임계값보다 큰 경우에만 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-205">The key strength is reported only if it is greater than the threshold.</span></span>|  
|<span data-ttu-id="dfc4e-206">**Exact**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-206">**Exact**</span></span>|<span data-ttu-id="dfc4e-207">임계값이 지정되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-207">No threshold is specified.</span></span> <span data-ttu-id="dfc4e-208">선택한 열이 정확한 키인 경우에만 키 수준이 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-208">The key strength is reported only if the selected columns are an exact key.</span></span>|  
  
 <span data-ttu-id="dfc4e-209">**KeyStrengthThreshold**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-209">**KeyStrengthThreshold**</span></span>  
 <span data-ttu-id="dfc4e-210">0-1의 값을 사용하여 임계값을 지정합니다. 이 임계값을 초과하는 키 수준은 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-210">Specify the threshold (by using a value between 0 and 1) above which the key strength should be reported.</span></span> <span data-ttu-id="dfc4e-211">이 속성의 기본값은 0.95입니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-211">The default value of this property is 0.95.</span></span> <span data-ttu-id="dfc4e-212">**Specified** 가 **KeyStrengthThresholdSetting**으로 선택된 경우에만 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-212">This option is enabled only when **Specified** is selected as the **KeyStrengthThresholdSetting**.</span></span>  
  
 <span data-ttu-id="dfc4e-213">**MaxNumberOfViolations**</span><span class="sxs-lookup"><span data-stu-id="dfc4e-213">**MaxNumberOfViolations**</span></span>  
 <span data-ttu-id="dfc4e-214">출력에 보고할 최대 후보 키 위반 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-214">Specify the maximum number of candidate key violations to report in the output.</span></span> <span data-ttu-id="dfc4e-215">이 속성의 기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-215">The default value of this property is 100.</span></span> <span data-ttu-id="dfc4e-216">**Exact** 가 **KeyStrengthThresholdSetting**으로 선택된 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc4e-216">This option is disabled when **Exact** is selected as the **KeyStrengthThresholdSetting**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc4e-217">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dfc4e-217">See Also</span></span>  
 <span data-ttu-id="dfc4e-218">[데이터 프로파일링 태스크 편집기&#40;일반 페이지&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="dfc4e-218">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="dfc4e-219">단일 테이블 빠른 프로필 형식&#40;데이터 프로파일링 태스크&#41;</span><span class="sxs-lookup"><span data-stu-id="dfc4e-219">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
