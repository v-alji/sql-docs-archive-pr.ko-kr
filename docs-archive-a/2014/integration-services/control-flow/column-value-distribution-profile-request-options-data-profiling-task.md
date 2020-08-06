---
title: 열 값 분포 프로필 요청 옵션(데이터 프로파일링 태스크) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: c1e5f5de-04f5-4d00-a9f0-55817186bdf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bba231bf46600d9608e1a55ad3a084534fec75e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650220"
---
# <a name="column-value-distribution-profile-request-options-data-profiling-task"></a><span data-ttu-id="68cf3-102">열 값 분포 프로필 요청 옵션(데이터 프로파일링 태스크)</span><span class="sxs-lookup"><span data-stu-id="68cf3-102">Column Value Distribution Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="68cf3-103">**프로필 요청** 페이지의 **요청 속성** 창을 사용하여 요청 창에서 선택한 **열 값 분포 프로필 요청** 의 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Value Distribution Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="68cf3-104">열 값 분포 프로필은 선택한 열에 있는 모든 고유 값 및 각 값이 나타내는 테이블 내 행의 비율을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-104">A Column Value Distribution profile reports all the distinct values in the selected column and the percentage of rows in the table that each value represents.</span></span> <span data-ttu-id="68cf3-105">또한 프로필은 테이블에서 지정된 행 비율을 초과하는 값을 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-105">The profile can also report values that represent more than a specified percentage of rows in the table.</span></span> <span data-ttu-id="68cf3-106">이 프로필을 사용하면 열에 포함된 잘못된 고유 값 수와 같은 데이터 문제를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-106">This profile can help you identify problems in your data such as an incorrect number of distinct values in a column.</span></span> <span data-ttu-id="68cf3-107">예를 들어 미국의 주가 포함된 열을 프로파일링하는 중 50개를 초과하는 고유 값이 검색될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-107">For example, you profile a United States state column and discover more than 50 distinct values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68cf3-108">이 항목에서 설명하는 옵션은 **데이터 프로파일링 태스크 편집기** 의 **프로필 요청 페이지**에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-108">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="68cf3-109">편집기의 이 페이지에 대한 자세한 내용은 [데이터 프로파일링 태스크 편집기&#40;프로필 요청 페이지&#41;](data-profiling-task-editor-profile-requests-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68cf3-109">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="68cf3-110">데이터 프로파일링 태스크를 사용하는 방법에 대한 자세한 내용은 [데이터 프로파일링 태스크 설정](data-profiling-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68cf3-110">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="68cf3-111">데이터 프로필 뷰어를 사용하여 데이터 프로파일링 태스크의 출력을 분석하는 방법에 대한 자세한 내용은 [데이터 프로필 뷰어](data-profile-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68cf3-111">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="68cf3-112">요청 속성 옵션</span><span class="sxs-lookup"><span data-stu-id="68cf3-112">Request Properties Options</span></span>  
 <span data-ttu-id="68cf3-113">**열 값 분포 프로필 요청**에 대해 **요청 속성** 창에는 다음 옵션 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-113">For a **Column Value Distribution Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="68cf3-114">**데이터**- **TableOrView** 및 **Column** 옵션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-114">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="68cf3-115">**일반**</span><span class="sxs-lookup"><span data-stu-id="68cf3-115">**General**</span></span>  
  
-   <span data-ttu-id="68cf3-116">**옵션**</span><span class="sxs-lookup"><span data-stu-id="68cf3-116">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="68cf3-117">데이터 옵션</span><span class="sxs-lookup"><span data-stu-id="68cf3-117">Data Options</span></span>  
 <span data-ttu-id="68cf3-118">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="68cf3-118">**ConnectionManager**</span></span>  
 <span data-ttu-id="68cf3-119">.NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient)를 사용하여 프로파일링할 테이블이나 뷰가 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-119">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="68cf3-120">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="68cf3-120">**TableOrView**</span></span>  
 <span data-ttu-id="68cf3-121">프로파일링할 열이 포함된 기존 테이블이나 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-121">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="68cf3-122">자세한 내용은 이 항목의 "TableorView 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="68cf3-122">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="68cf3-123">**열**</span><span class="sxs-lookup"><span data-stu-id="68cf3-123">**Column**</span></span>  
 <span data-ttu-id="68cf3-124">프로파일링할 기존 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-124">Select the existing column to be profiled.</span></span> <span data-ttu-id="68cf3-125">모든 열을 프로파일링하려면 **(\*)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-125">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="68cf3-126">자세한 내용은 이 항목의 "열 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="68cf3-126">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="68cf3-127">TableOrView 옵션</span><span class="sxs-lookup"><span data-stu-id="68cf3-127">TableOrView Options</span></span>  
 <span data-ttu-id="68cf3-128">**스키마**</span><span class="sxs-lookup"><span data-stu-id="68cf3-128">**Schema**</span></span>  
 <span data-ttu-id="68cf3-129">선택한 테이블이 속해 있는 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-129">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="68cf3-130">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-130">This option is read-only.</span></span>  
  
 <span data-ttu-id="68cf3-131">**테이블**</span><span class="sxs-lookup"><span data-stu-id="68cf3-131">**Table**</span></span>  
 <span data-ttu-id="68cf3-132">선택한 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-132">Displays the name of the selected table.</span></span> <span data-ttu-id="68cf3-133">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-133">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="68cf3-134">열 옵션</span><span class="sxs-lookup"><span data-stu-id="68cf3-134">Column Options</span></span>  
 <span data-ttu-id="68cf3-135">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="68cf3-135">**IsWildCard**</span></span>  
 <span data-ttu-id="68cf3-136">**(\*)** 와일드카드가 선택되었는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-136">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="68cf3-137">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 **True**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-137">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="68cf3-138">프로파일링할 개별 열을 선택한 경우에는 **False** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-138">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="68cf3-139">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-139">This option is read-only.</span></span>  
  
 <span data-ttu-id="68cf3-140">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="68cf3-140">**ColumnName**</span></span>  
 <span data-ttu-id="68cf3-141">선택한 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-141">Displays the name of the selected column.</span></span> <span data-ttu-id="68cf3-142">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-142">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="68cf3-143">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-143">This option is read-only.</span></span>  
  
 <span data-ttu-id="68cf3-144">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="68cf3-144">**StringCompareOptions**</span></span>  
 <span data-ttu-id="68cf3-145">문자열 값을 비교할 수 있는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-145">Select options for comparing string values.</span></span> <span data-ttu-id="68cf3-146">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-146">This property has the options listed in the following table.</span></span> <span data-ttu-id="68cf3-147">이 옵션의 기본값은 **Default**입니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-147">The default value of this option is **Default**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="68cf3-148">**ColumnName**에 대해 **(\*)** 와일드카드를 사용하는 경우 **CompareOptions**가 읽기 전용이 되며 **Default** 설정으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-148">If the **(\*)** wildcard is used for **ColumnName**, **CompareOptions** is read-only and is set to the **Default** setting.</span></span>  
  
|<span data-ttu-id="68cf3-149">값</span><span class="sxs-lookup"><span data-stu-id="68cf3-149">Value</span></span>|<span data-ttu-id="68cf3-150">Description</span><span class="sxs-lookup"><span data-stu-id="68cf3-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68cf3-151">**기본값**</span><span class="sxs-lookup"><span data-stu-id="68cf3-151">**Default**</span></span>|<span data-ttu-id="68cf3-152">원본 테이블에서 열의 데이터 정렬을 기준으로 데이터를 정렬 및 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-152">Sorts and compares data based on the column's collation in the source table.</span></span>|  
|<span data-ttu-id="68cf3-153">**BinarySort**</span><span class="sxs-lookup"><span data-stu-id="68cf3-153">**BinarySort**</span></span>|<span data-ttu-id="68cf3-154">각 문자에 대해 정의된 비트 패턴을 기준으로 데이터를 정렬 및 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-154">Sorts and compares data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="68cf3-155">이진 정렬 순서는 대/소문자와 악센트를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-155">Binary sort order is case sensitive and accent sensitive.</span></span> <span data-ttu-id="68cf3-156">이진은 가장 빠른 정렬 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-156">Binary is also the fastest sorting order.</span></span>|  
|<span data-ttu-id="68cf3-157">**DictionarySort**</span><span class="sxs-lookup"><span data-stu-id="68cf3-157">**DictionarySort**</span></span>|<span data-ttu-id="68cf3-158">관련된 언어 또는 알파벳에 대해 사전에 정의된 정렬 및 비교 규칙에 따라 데이터를 정렬 및 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-158">Sorts and compares data based on the sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>|  
  
 <span data-ttu-id="68cf3-159">**DictionarySort**를 선택하는 경우 다음 테이블에 나열된 옵션 조합을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-159">If you select **DictionarySort**, you can also select any combination of the options listed in the following table.</span></span> <span data-ttu-id="68cf3-160">이러한 추가 옵션은 기본적으로 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-160">By default, none of these additional options are selected.</span></span>  
  
|<span data-ttu-id="68cf3-161">값</span><span class="sxs-lookup"><span data-stu-id="68cf3-161">Value</span></span>|<span data-ttu-id="68cf3-162">Description</span><span class="sxs-lookup"><span data-stu-id="68cf3-162">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68cf3-163">**IgnoreCase**</span><span class="sxs-lookup"><span data-stu-id="68cf3-163">**IgnoreCase**</span></span>|<span data-ttu-id="68cf3-164">비교 시 대문자와 소문자를 구분할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-164">Specifies whether the comparison distinguishes between uppercase and lowercase letters.</span></span> <span data-ttu-id="68cf3-165">이 옵션을 설정하면 문자열 비교 시 대/소문자가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-165">If this option is set, the string comparison ignores case.</span></span> <span data-ttu-id="68cf3-166">예를 들어 "ABC"는 "abc"와 동일하게 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-166">For example, "ABC" becomes the same as "abc".</span></span>|  
|<span data-ttu-id="68cf3-167">**IgnoreNonSpace**</span><span class="sxs-lookup"><span data-stu-id="68cf3-167">**IgnoreNonSpace**</span></span>|<span data-ttu-id="68cf3-168">비교 시 공백 문자와 분음 기호를 구분할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-168">Specifies whether the comparison distinguishes between spacing characters and diacritics.</span></span> <span data-ttu-id="68cf3-169">이 옵션을 설정하면 비교 시 분음 기호가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-169">If this option is set, the comparison ignores diacritics.</span></span> <span data-ttu-id="68cf3-170">예를 들어 "å"와 "a"는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-170">For example, "å" is equal to "a".</span></span>|  
|<span data-ttu-id="68cf3-171">**IgnoreKanaType**</span><span class="sxs-lookup"><span data-stu-id="68cf3-171">**IgnoreKanaType**</span></span>|<span data-ttu-id="68cf3-172">비교 시 두 가지 형식의 일본어 가나 문자인 히라가나와 가타가나를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-172">Specifies whether the comparison distinguishes between the two types of Japanese kana characters: hiragana and katakana.</span></span> <span data-ttu-id="68cf3-173">이 옵션을 설정하면 문자열 비교 시 가나 형식이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-173">If this option is set, the string comparison ignores kana type.</span></span>|  
|<span data-ttu-id="68cf3-174">**IgnoreWidth**</span><span class="sxs-lookup"><span data-stu-id="68cf3-174">**IgnoreWidth**</span></span>|<span data-ttu-id="68cf3-175">비교 시 싱글바이트 문자와 동일 문자의 더블바이트 문자 표현을 구분할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-175">Specifies whether the comparison distinguishes between a single-byte character and the same character when it is represented as a double-byte character.</span></span> <span data-ttu-id="68cf3-176">이 옵션을 설정하면 문자열 비교 시 동일 문자에 대한 싱글바이트 표현과 더블바이트 표현이 동일하게 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-176">If this option is set, the string comparison treats single-byte and double-byte representations of the same character as identical.</span></span>|  
  
### <a name="general-options"></a><span data-ttu-id="68cf3-177">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="68cf3-177">General Options</span></span>  
 <span data-ttu-id="68cf3-178">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="68cf3-178">**RequestID**</span></span>  
 <span data-ttu-id="68cf3-179">이 프로필 요청을 식별할 설명이 포함된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-179">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="68cf3-180">일반적으로 자동 생성된 값은 변경하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-180">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="68cf3-181">옵션</span><span class="sxs-lookup"><span data-stu-id="68cf3-181">Options</span></span>  
 <span data-ttu-id="68cf3-182">**ValueDistributionOption**</span><span class="sxs-lookup"><span data-stu-id="68cf3-182">**ValueDistributionOption**</span></span>  
 <span data-ttu-id="68cf3-183">모든 열 값에 대해 분포를 컴퓨팅할 것인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-183">Specify whether to compute the distribution for all column values.</span></span> <span data-ttu-id="68cf3-184">이 옵션의 기본값은 **FrequentValues**입니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-184">The default value of this option is **FrequentValues**.</span></span>  
  
|<span data-ttu-id="68cf3-185">값</span><span class="sxs-lookup"><span data-stu-id="68cf3-185">Value</span></span>|<span data-ttu-id="68cf3-186">Description</span><span class="sxs-lookup"><span data-stu-id="68cf3-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68cf3-187">**AllValues**</span><span class="sxs-lookup"><span data-stu-id="68cf3-187">**AllValues**</span></span>|<span data-ttu-id="68cf3-188">모든 열 값에 대해 분포가 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-188">The distribution is computed for all column values.</span></span>|  
|<span data-ttu-id="68cf3-189">**FrequentValues**</span><span class="sxs-lookup"><span data-stu-id="68cf3-189">**FrequentValues**</span></span>|<span data-ttu-id="68cf3-190">빈도가 **FrequentValueThreshold**에 지정된 최소값을 초과하는 값에 대해서만 분포가 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-190">The distribution is computed only for values whose frequency exceeds the minimum value specified in **FrequentValueThreshold**.</span></span> <span data-ttu-id="68cf3-191">**FrequentValueThreshold** 를 충족하지 않는 값은 출력 보고서에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-191">Values that do not meet the **FrequentValueThreshold** are excluded from the output report.</span></span>|  
  
 <span data-ttu-id="68cf3-192">**FrequentValueThreshold**</span><span class="sxs-lookup"><span data-stu-id="68cf3-192">**FrequentValueThreshold**</span></span>  
 <span data-ttu-id="68cf3-193">0-1의 값을 사용하여 임계값을 지정합니다. 이 임계값을 초과하는 열 값은 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-193">Specify the threshold (by using a value between 0 and 1) above which the column value should be reported.</span></span> <span data-ttu-id="68cf3-194">**AllValues** 가 **ValueDistributionOption**으로 선택된 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-194">This option is disabled when you select **AllValues** as the **ValueDistributionOption**.</span></span> <span data-ttu-id="68cf3-195">이 옵션의 기본값은 0.001입니다.</span><span class="sxs-lookup"><span data-stu-id="68cf3-195">The default value of this option is 0.001.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68cf3-196">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68cf3-196">See Also</span></span>  
 <span data-ttu-id="68cf3-197">[데이터 프로파일링 태스크 편집기&#40;일반 페이지&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="68cf3-197">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="68cf3-198">단일 테이블 빠른 프로필 형식&#40;데이터 프로파일링 태스크&#41;</span><span class="sxs-lookup"><span data-stu-id="68cf3-198">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
