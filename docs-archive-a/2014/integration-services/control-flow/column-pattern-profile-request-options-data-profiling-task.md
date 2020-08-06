---
title: 열 패턴 프로필 요청 옵션(데이터 프로파일링 태스크) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 9ccb8fc5-f65e-41a2-9511-7fa55586eb8b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9293d19baaee95cee77b075447dcfe1061d20bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650221"
---
# <a name="column-pattern-profile-request-options-data-profiling-task"></a><span data-ttu-id="cd865-102">열 패턴 프로필 요청 옵션(데이터 프로파일링 태스크)</span><span class="sxs-lookup"><span data-stu-id="cd865-102">Column Pattern Profile Request Options (Data Profiling Task)</span></span>
  <span data-ttu-id="cd865-103">**프로필 요청** 페이지의 **요청 속성** 창을 사용하여 요청 창에서 선택한 **열 패턴 프로필 요청** 의 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-103">Use the **Request Properties** pane of the **Profile Requests** page to set the options for the **Column Pattern Profile Request** selected in the requests pane.</span></span> <span data-ttu-id="cd865-104">열 패턴 프로필은 문자열 열에서 지정된 값의 비율을 포괄하는 정규식 집합을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-104">A Column Pattern profile reports a set of regular expressions that cover the specified percentage of values in a string column.</span></span> <span data-ttu-id="cd865-105">이 프로필을 사용하면 잘못된 문자열과 같은 데이터 문제를 식별하는 데 도움이 되며 앞으로 새 값의 유효성 검사에 사용할 수 있는 정규식을 제안 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-105">This profile can help you identify problems in your data, such as invalid strings, and can suggest regular expressions that can be used in the future to validate new values.</span></span> <span data-ttu-id="cd865-106">예를 들어 US Zip Code 열의 패턴 프로필이 \d{5}-\d{4}, \d{5} 및 \d{9} 정규식을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-106">For example, a pattern profile of a column of United States Zip Codes might produce the regular expressions \d{5}-\d{4}, \d{5}, and \d{9}.</span></span> <span data-ttu-id="cd865-107">다른 정규식이 보이면 데이터에 유효하지 않거나 잘못된 형식의 값이 포함되어 있을 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-107">If you see other regular expressions, your data likely contains values that are invalid or in an incorrect format.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd865-108">이 항목에서 설명하는 옵션은 **데이터 프로파일링 태스크 편집기** 의 **프로필 요청 페이지**에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-108">The options described in this topic appear on the **Profile Requests page** of the **Data Profiling Task Editor**.</span></span> <span data-ttu-id="cd865-109">편집기의 이 페이지에 대한 자세한 내용은 [데이터 프로파일링 태스크 편집기&#40;프로필 요청 페이지&#41;](data-profiling-task-editor-profile-requests-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd865-109">For more information about this page of the editor, see [Data Profiling Task Editor &#40;Profile Requests Page&#41;](data-profiling-task-editor-profile-requests-page.md).</span></span>  
  
 <span data-ttu-id="cd865-110">데이터 프로파일링 태스크를 사용하는 방법에 대한 자세한 내용은 [데이터 프로파일링 태스크 설정](data-profiling-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd865-110">For more information about how to use the Data Profiling Task, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span> <span data-ttu-id="cd865-111">데이터 프로필 뷰어를 사용하여 데이터 프로파일링 태스크의 출력을 분석하는 방법에 대한 자세한 내용은 [데이터 프로필 뷰어](data-profile-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd865-111">For more information about how to use the Data Profile Viewer to analyze the output of the Data Profiling Task, see [Data Profile Viewer](data-profile-viewer.md).</span></span>  
  
## <a name="understanding-the-use-of-delimiters-and-symbols"></a><span data-ttu-id="cd865-112">구분 기호 및 기호 사용 이해</span><span class="sxs-lookup"><span data-stu-id="cd865-112">Understanding the Use of Delimiters and Symbols</span></span>  
 <span data-ttu-id="cd865-113">**열 패턴 프로필 요청**에 대한 패턴을 계산하기 전에 데이터 프로파일링 태스크에서는 데이터를 토큰화합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-113">Before computing the patterns for a **Column Pattern Profile Request**, the Data Profiling Task tokenizes the data.</span></span> <span data-ttu-id="cd865-114">즉, 이 태스크에서는 문자열 값을 토큰이라는 더 작은 단위로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-114">That is, the task separates the string values into smaller units known as tokens.</span></span> <span data-ttu-id="cd865-115">이 태스크에서는 **Delimiters** 및 **Symbols** 속성에 대해 지정하는 구분 기호 및 기호를 기반으로 문자열을 토큰으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-115">The task separates strings into tokens based on the delimiters and symbols that you specify for the **Delimiters** and **Symbols** properties:</span></span>  
  
-   <span data-ttu-id="cd865-116">**Delimiters** 기본적으로 Delimiters 목록에는 공백 문자, 가로 탭 문자(\t), 줄 바꿈 문자(\n) 및 캐리지 리턴 문자(\r)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-116">**Delimiters** By default, the list of delimiters contains the following characters: space, horizontal tab (\t), new line (\n), and carriage return (\r).</span></span> <span data-ttu-id="cd865-117">추가 구분 기호를 지정할 수 있지만 기본 구분 기호는 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-117">You can specify additional delimiters, but you cannot remove the default delimiters.</span></span>  
  
-   <span data-ttu-id="cd865-118">**기호** 기본적으로 **기호** 목록에는 다음 문자가 포함 됩니다. `,.;:-"'` ~ =&/@!? () <> [] {} | # \* ^% `. For example, if the symbols are "` ()-' ", 값" (425) 123-4567 "은 [" ("," 425 ",") "," 123 ","-"," 4567 ",") "]로 토큰화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-118">**Symbols** By default, the list of **Symbols** contains the following characters: `,.;:-"'`~=&/@!?()<>[]{}|#\*^%`. For example, if the symbols are "`()-\`", the value "(425) 123-4567" is tokenized as ["(", "425", ")", "123", "-", "4567", ")"].</span></span>  
  
 <span data-ttu-id="cd865-119">한 문자가 동시에 구분 기호이면서 기호일 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-119">A character cannot be both a delimiter and a symbol.</span></span>  
  
 <span data-ttu-id="cd865-120">모든 구분 기호는 토큰화 프로세스의 일환으로 단일 공백으로 정규화됩니다. 반면 기호는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-120">All delimiters are normalized to a single space as part of the tokenizing process, while symbols are retained.</span></span>  
  
## <a name="understanding-the-use-of-the-tag-table"></a><span data-ttu-id="cd865-121">태그 테이블 사용 이해</span><span class="sxs-lookup"><span data-stu-id="cd865-121">Understanding the Use of the Tag Table</span></span>  
 <span data-ttu-id="cd865-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 만든 특수 테이블에 태그 및 관련 용어를 저장하여 관련 토큰을 단일 태그를 사용하여 그룹화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-122">You can optionally group related tokens with a single tag by storing tags and the related terms in a special table that you create in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="cd865-123">태그 테이블에는 이름이 하나는 "Tag"이고 다른 하나는 "Term"인 두 개의 문자열 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-123">The tag table must have two string columns, one named "Tag" and the other named "Term".</span></span> <span data-ttu-id="cd865-124">이러한 열의 유형은 `char`, `nchar`, `varchar` 또는 `nvarchar`일 수 있지만 `text` 또는 `ntext`일 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-124">These columns can be of type `char`, `nchar`, `varchar`, or `nvarchar`, but not `text` or `ntext`.</span></span> <span data-ttu-id="cd865-125">단일 테이블에서 여러 태그와 해당 용어를 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-125">You can combine multiple tags and the corresponding terms in a single table.</span></span> <span data-ttu-id="cd865-126">열 패턴 프로필 요청은 하나의 태그 테이블만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-126">A Column Pattern Profile Request can use only one tag table.</span></span> <span data-ttu-id="cd865-127">별도의 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자를 사용하여 태그 테이블에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-127">You can use a separate [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to connect to the tag table.</span></span> <span data-ttu-id="cd865-128">따라서 태그 테이블은 다른 데이터베이스에 있거나 원본 데이터와 다른 서버에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-128">Therefore, the tag table can be located in a different database or on a different server than the source data.</span></span>  
  
 <span data-ttu-id="cd865-129">예를 들어 단일 태그 "Direction"을 사용하여 주소에 나타날 수 있는 값 "East", "West", "North" 및 "South"를 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-129">For example, you could group the values "East", "West", "North", and "South" that might appear in street addresses by using the single tag, "Direction".</span></span> <span data-ttu-id="cd865-130">다음 테이블은 이러한 태그 테이블의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-130">The following table is an example of such a tag table.</span></span>  
  
|<span data-ttu-id="cd865-131">태그</span><span class="sxs-lookup"><span data-stu-id="cd865-131">Tag</span></span>|<span data-ttu-id="cd865-132">용어</span><span class="sxs-lookup"><span data-stu-id="cd865-132">Term</span></span>|  
|---------|----------|  
|<span data-ttu-id="cd865-133">Direction</span><span class="sxs-lookup"><span data-stu-id="cd865-133">Direction</span></span>|<span data-ttu-id="cd865-134">East</span><span class="sxs-lookup"><span data-stu-id="cd865-134">East</span></span>|  
|<span data-ttu-id="cd865-135">Direction</span><span class="sxs-lookup"><span data-stu-id="cd865-135">Direction</span></span>|<span data-ttu-id="cd865-136">West</span><span class="sxs-lookup"><span data-stu-id="cd865-136">West</span></span>|  
|<span data-ttu-id="cd865-137">Direction</span><span class="sxs-lookup"><span data-stu-id="cd865-137">Direction</span></span>|<span data-ttu-id="cd865-138">North</span><span class="sxs-lookup"><span data-stu-id="cd865-138">North</span></span>|  
|<span data-ttu-id="cd865-139">Direction</span><span class="sxs-lookup"><span data-stu-id="cd865-139">Direction</span></span>|<span data-ttu-id="cd865-140">South</span><span class="sxs-lookup"><span data-stu-id="cd865-140">South</span></span>|  
  
 <span data-ttu-id="cd865-141">다른 태그를 사용하여 주소에서 "번지"의 개념을 나타내는 다른 단어를 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-141">You could use another tag to group the different words that express the notion of a "street" in street addresses:</span></span>  
  
|<span data-ttu-id="cd865-142">태그</span><span class="sxs-lookup"><span data-stu-id="cd865-142">Tag</span></span>|<span data-ttu-id="cd865-143">용어</span><span class="sxs-lookup"><span data-stu-id="cd865-143">Term</span></span>|  
|---------|----------|  
|<span data-ttu-id="cd865-144">Street</span><span class="sxs-lookup"><span data-stu-id="cd865-144">Street</span></span>|<span data-ttu-id="cd865-145">Street</span><span class="sxs-lookup"><span data-stu-id="cd865-145">Street</span></span>|  
|<span data-ttu-id="cd865-146">Street</span><span class="sxs-lookup"><span data-stu-id="cd865-146">Street</span></span>|<span data-ttu-id="cd865-147">Avenue</span><span class="sxs-lookup"><span data-stu-id="cd865-147">Avenue</span></span>|  
|<span data-ttu-id="cd865-148">Street</span><span class="sxs-lookup"><span data-stu-id="cd865-148">Street</span></span>|<span data-ttu-id="cd865-149">위치</span><span class="sxs-lookup"><span data-stu-id="cd865-149">Place</span></span>|  
|<span data-ttu-id="cd865-150">Street</span><span class="sxs-lookup"><span data-stu-id="cd865-150">Street</span></span>|<span data-ttu-id="cd865-151">Way</span><span class="sxs-lookup"><span data-stu-id="cd865-151">Way</span></span>|  
  
 <span data-ttu-id="cd865-152">이러한 태그의 조합을 기반으로 주소에 대한 결과 패턴은 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-152">Based on this combination of tags, the resulting pattern for a street address might resemble the following pattern:</span></span>  
  
 `\d+\ LookupTag=Direction \d+\p{L}+\ LookupTag=Street`  
  
> [!NOTE]  
>  <span data-ttu-id="cd865-153">태그 테이블을 사용하면 데이터 프로파일링 태스크의 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-153">Using a tag table decreases the performance of the Data Profiling task.</span></span> <span data-ttu-id="cd865-154">태그를 11개 이상 사용하거나 태그 당 용어를 101개 이상 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="cd865-154">Do not use more than 10 tags or more than 100 terms per tag.</span></span>  
  
 <span data-ttu-id="cd865-155">같은 용어는 두 개 이상의 태그에 속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-155">The same term can belong to more than one tag.</span></span>  
  
## <a name="request-properties-options"></a><span data-ttu-id="cd865-156">요청 속성 옵션</span><span class="sxs-lookup"><span data-stu-id="cd865-156">Request Properties Options</span></span>  
 <span data-ttu-id="cd865-157">**열 패턴 프로필 요청**에 대해 **요청 속성** 창에는 다음 옵션 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-157">For a **Column Pattern Profile Request**, the **Request Properties** pane displays the following groups of options:</span></span>  
  
-   <span data-ttu-id="cd865-158">**데이터**- **TableOrView** 및 **Column** 옵션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-158">**Data**, which includes the **TableOrView** and **Column** options</span></span>  
  
-   <span data-ttu-id="cd865-159">**일반**</span><span class="sxs-lookup"><span data-stu-id="cd865-159">**General**</span></span>  
  
-   <span data-ttu-id="cd865-160">**Options**</span><span class="sxs-lookup"><span data-stu-id="cd865-160">**Options**</span></span>  
  
### <a name="data-options"></a><span data-ttu-id="cd865-161">데이터 옵션</span><span class="sxs-lookup"><span data-stu-id="cd865-161">Data Options</span></span>  
 <span data-ttu-id="cd865-162">**ConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="cd865-162">**ConnectionManager**</span></span>  
 <span data-ttu-id="cd865-163">.NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient)를 사용하여 프로파일링할 테이블이나 뷰가 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-163">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the table or view to be profiled.</span></span>  
  
 <span data-ttu-id="cd865-164">**TableOrView**</span><span class="sxs-lookup"><span data-stu-id="cd865-164">**TableOrView**</span></span>  
 <span data-ttu-id="cd865-165">프로파일링할 열이 포함된 기존 테이블이나 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-165">Select the existing table or view that contains the column to be profiled.</span></span>  
  
 <span data-ttu-id="cd865-166">자세한 내용은 이 항목의 "TableorView 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cd865-166">For more information, see the section, "TableorView Options," in this topic.</span></span>  
  
 <span data-ttu-id="cd865-167">**열**</span><span class="sxs-lookup"><span data-stu-id="cd865-167">**Column**</span></span>  
 <span data-ttu-id="cd865-168">프로파일링할 기존 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-168">Select the existing column to be profiled.</span></span> <span data-ttu-id="cd865-169">모든 열을 프로 파일링 하려면 **( \* )** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-169">Select **(\*)** to profile all columns.</span></span>  
  
 <span data-ttu-id="cd865-170">자세한 내용은 이 항목의 "열 옵션" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cd865-170">For more information, see the section, "Column Options," in this topic.</span></span>  
  
#### <a name="tableorview-options"></a><span data-ttu-id="cd865-171">TableOrView 옵션</span><span class="sxs-lookup"><span data-stu-id="cd865-171">TableOrView Options</span></span>  
 <span data-ttu-id="cd865-172">**스키마**</span><span class="sxs-lookup"><span data-stu-id="cd865-172">**Schema**</span></span>  
 <span data-ttu-id="cd865-173">선택한 테이블이 속해 있는 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-173">Specifies the schema to which the selected table belongs.</span></span> <span data-ttu-id="cd865-174">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-174">This option is read-only.</span></span>  
  
 <span data-ttu-id="cd865-175">**테이블**</span><span class="sxs-lookup"><span data-stu-id="cd865-175">**Table**</span></span>  
 <span data-ttu-id="cd865-176">선택한 테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-176">Displays the name of the selected table.</span></span> <span data-ttu-id="cd865-177">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-177">This option is read-only.</span></span>  
  
#### <a name="column-options"></a><span data-ttu-id="cd865-178">열 옵션</span><span class="sxs-lookup"><span data-stu-id="cd865-178">Column Options</span></span>  
 <span data-ttu-id="cd865-179">**IsWildCard**</span><span class="sxs-lookup"><span data-stu-id="cd865-179">**IsWildCard**</span></span>  
 <span data-ttu-id="cd865-180">**( \* )** 와일드 카드가 선택 되었는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-180">Specifies whether the **(\*)** wildcard has been selected.</span></span> <span data-ttu-id="cd865-181">이 옵션은 모든 열을 프로파일링하도록 **(\*)** 를 선택한 경우 **True**로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-181">This option is set to **True** if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="cd865-182">프로파일링할 개별 열을 선택한 경우에는 **False** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-182">It is **False** if you have selected an individual column to be profiled.</span></span> <span data-ttu-id="cd865-183">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-183">This option is read-only.</span></span>  
  
 <span data-ttu-id="cd865-184">**ColumnName**</span><span class="sxs-lookup"><span data-stu-id="cd865-184">**ColumnName**</span></span>  
 <span data-ttu-id="cd865-185">선택한 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-185">Displays the name of the selected column.</span></span> <span data-ttu-id="cd865-186">이 옵션은 모든 열을 프로 파일링 하도록 **( \* )** 를 선택한 경우 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-186">This option is blank if you have selected **(\*)** to profile all columns.</span></span> <span data-ttu-id="cd865-187">이 옵션은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-187">This option is read-only.</span></span>  
  
 <span data-ttu-id="cd865-188">**StringCompareOptions**</span><span class="sxs-lookup"><span data-stu-id="cd865-188">**StringCompareOptions**</span></span>  
 <span data-ttu-id="cd865-189">이 옵션은 열 패턴 프로필에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-189">This option does not apply to the Column Pattern Profile.</span></span>  
  
### <a name="general-options"></a><span data-ttu-id="cd865-190">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="cd865-190">General Options</span></span>  
 <span data-ttu-id="cd865-191">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="cd865-191">**RequestID**</span></span>  
 <span data-ttu-id="cd865-192">이 프로필 요청을 식별할 설명이 포함된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-192">Type a descriptive name to identify this profile request.</span></span> <span data-ttu-id="cd865-193">일반적으로 자동 생성된 값은 변경하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-193">Typically, you do not have to change the autogenerated value.</span></span>  
  
### <a name="options"></a><span data-ttu-id="cd865-194">옵션</span><span class="sxs-lookup"><span data-stu-id="cd865-194">Options</span></span>  
 <span data-ttu-id="cd865-195">**MaxNumberOfPatterns**</span><span class="sxs-lookup"><span data-stu-id="cd865-195">**MaxNumberOfPatterns**</span></span>  
 <span data-ttu-id="cd865-196">프로필에서 컴퓨팅할 최대 패턴 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-196">Specify the maximum number of patterns that you want the profile to compute.</span></span> <span data-ttu-id="cd865-197">이 옵션의 기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-197">The default value of this option is 10.</span></span> <span data-ttu-id="cd865-198">최대값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-198">The maximum value is 100.</span></span>  
  
 <span data-ttu-id="cd865-199">**PercentageDataCoverageDesired**</span><span class="sxs-lookup"><span data-stu-id="cd865-199">**PercentageDataCoverageDesired**</span></span>  
 <span data-ttu-id="cd865-200">계산된 패턴에 포괄할 데이터의 비율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-200">Specify the percentage of the data that you want the computed patterns to cover.</span></span> <span data-ttu-id="cd865-201">이 옵션의 기본값은 95%입니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-201">The default value of this option is 95 (percent).</span></span>  
  
 <span data-ttu-id="cd865-202">**CaseSensitive**</span><span class="sxs-lookup"><span data-stu-id="cd865-202">**CaseSensitive**</span></span>  
 <span data-ttu-id="cd865-203">패턴에서 대/소문자를 구분할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-203">Indicate whether the patterns should be case-sensitive.</span></span> <span data-ttu-id="cd865-204">이 옵션의 기본값은 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-204">The default value of this option is **False**.</span></span>  
  
 <span data-ttu-id="cd865-205">**구분 기호**</span><span class="sxs-lookup"><span data-stu-id="cd865-205">**Delimiters**</span></span>  
 <span data-ttu-id="cd865-206">텍스트를 토큰화할 때 단어 간 공백과 동일하게 처리할 문자를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-206">List the characters that should be treated as the equivalent of spaces between words when tokenizing text.</span></span> <span data-ttu-id="cd865-207">기본적으로 **Delimiters** 목록에는 공백 문자, 가로 탭 문자(\t), 줄 바꿈 문자(\n) 및 캐리지 리턴 문자(\r)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-207">By default, the list of **Delimiters** contains the following characters: the space, horizontal tab (\t), new line (\n), and carriage return (\r).</span></span> <span data-ttu-id="cd865-208">추가 구분 기호를 지정할 수 있지만 기본 구분 기호는 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-208">You can specify additional delimiters, but you cannot remove the default delimiters.</span></span>  
  
 <span data-ttu-id="cd865-209">자세한 내용은 이 항목의 앞부분에 나오는 "구분 기호 및 기호 사용 이해"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cd865-209">For more information, see "Understanding the Use of Delimiters and Symbols" earlier in this topic.</span></span>  
  
 <span data-ttu-id="cd865-210">**기호만**</span><span class="sxs-lookup"><span data-stu-id="cd865-210">**Symbols**</span></span>  
 <span data-ttu-id="cd865-211">패턴의 일부로 유지할 기호를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-211">List the symbols that should be retained as part of patterns.</span></span> <span data-ttu-id="cd865-212">이러한 기호에는 날짜의 "/", 시간의 ":" 및 전자 메일 주소의 "@"이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-212">Examples might include "/" for dates, ":" for times, and "@" for e-mail addresses.</span></span> <span data-ttu-id="cd865-213">기본적으로 **기호** 목록에는 다음 문자가 포함 됩니다. `,.;:-"'` ~ =&/@!? () <> [] {} | # \* ^% '입니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-213">By default, the list of **Symbols** contains the following characters: `,.;:-"'`~=&/@!?()<>[]{}|#\*^%\`.</span></span>  
  
 <span data-ttu-id="cd865-214">자세한 내용은 이 항목의 앞부분에 나오는 "구분 기호 및 기호 사용 이해"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cd865-214">For more information, see "Understanding the Use of Delimiters and Symbols" earlier in this topic.</span></span>  
  
 <span data-ttu-id="cd865-215">**TagTableConnectionManager**</span><span class="sxs-lookup"><span data-stu-id="cd865-215">**TagTableConnectionManager**</span></span>  
 <span data-ttu-id="cd865-216">.NET Data Provider for [!INCLUDE[vstecado](../../includes/vstecado-md.md)] (SqlClient)를 사용하여 태그 테이블이 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 연결하는 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-216">Select the existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the .NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the tag table.</span></span>  
  
 <span data-ttu-id="cd865-217">자세한 내용은 이 항목의 앞부분에 나오는 "태그 테이블 사용 이해"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cd865-217">For more information, see "Understanding the Use of the Tag Table" earlier in this topic.</span></span>  
  
 <span data-ttu-id="cd865-218">**TagTableName**</span><span class="sxs-lookup"><span data-stu-id="cd865-218">**TagTableName**</span></span>  
 <span data-ttu-id="cd865-219">Tag 및 Term이라는 두 개의 문자열 열이 있어야 하는 기존 태그 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd865-219">Select the existing tag table, which must have two string columns named Tag and Term.</span></span>  
  
 <span data-ttu-id="cd865-220">자세한 내용은 이 항목의 앞부분에 나오는 "태그 테이블 사용 이해"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cd865-220">For more information, see "Understanding the Use of the Tag Table" earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd865-221">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd865-221">See Also</span></span>  
 <span data-ttu-id="cd865-222">[데이터 프로 파일링 태스크 편집기 &#40;일반 페이지&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="cd865-222">[Data Profiling Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="cd865-223">단일 테이블 빠른 프로필 형식&#40;데이터 프로파일링 태스크&#41;</span><span class="sxs-lookup"><span data-stu-id="cd865-223">Single Table Quick Profile Form &#40;Data Profiling Task&#41;</span></span>](single-table-quick-profile-form-data-profiling-task.md)  
  
  
