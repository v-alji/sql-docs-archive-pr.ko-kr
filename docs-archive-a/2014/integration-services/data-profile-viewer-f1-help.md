---
title: F1 도움말 데이터 프로필 뷰어 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dataprofileviewer.f1
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], viewer
ms.assetid: 3469c60a-8f4f-46ba-999a-cb9070197fea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7003e1299938bd53a6d16a5597d4566ba5c46579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647772"
---
# <a name="data-profile-viewer-f1-help"></a><span data-ttu-id="09de2-102">데이터 프로필 뷰어 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="09de2-102">Data Profile Viewer F1 Help</span></span>
  <span data-ttu-id="09de2-103">데이터 프로필 뷰어를 사용하여 데이터 프로파일링 태스크의 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-103">Use the Data Profile Viewer to view the output of the Data Profiling task.</span></span>  
  
 <span data-ttu-id="09de2-104">데이터 프로필 뷰어를 사용하는 방법에 대한 자세한 내용은 [데이터 프로필 뷰어](control-flow/data-profile-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="09de2-104">For more information about how to use the Data Profile Viewer, see [Data Profile Viewer](control-flow/data-profile-viewer.md).</span></span> <span data-ttu-id="09de2-105">데이터 프로필 뷰어에서 분석하는 프로필 출력을 만드는 데이터 프로파일링 태스크를 사용하는 방법에 대한 자세한 내용은 [데이터 프로파일링 태스크 설정](control-flow/data-profiling-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="09de2-105">For more information about how to use the Data Profiling task, which creates the profile output that you analyze in the Data Profile Viewer, see [Setup of the Data Profiling Task](control-flow/data-profiling-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="09de2-106">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="09de2-106">Static Options</span></span>  
 <span data-ttu-id="09de2-107">**열기**</span><span class="sxs-lookup"><span data-stu-id="09de2-107">**Open**</span></span>  
 <span data-ttu-id="09de2-108">데이터 프로파일링 태스크의 출력을 포함하는 저장된 파일을 찾아보려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-108">Click to browse for the saved file that contains the output of the Data Profiling task.</span></span>  
  
 <span data-ttu-id="09de2-109">**프로필** 창</span><span class="sxs-lookup"><span data-stu-id="09de2-109">**Profiles** pane</span></span>  
 <span data-ttu-id="09de2-110">출력에 포함된 프로필을 보려면 **프로필** 창에서 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-110">Expand the tree in the **Profiles** pane to see the profiles that are included in the output.</span></span> <span data-ttu-id="09de2-111">해당 프로필의 결과를 보려면 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-111">Select a profile to view the results for that profile.</span></span>  
  
 <span data-ttu-id="09de2-112">**메시지** 창</span><span class="sxs-lookup"><span data-stu-id="09de2-112">**Message** pane</span></span>  
 <span data-ttu-id="09de2-113">상태 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-113">Displays status messages.</span></span>  
  
 <span data-ttu-id="09de2-114">**드릴다운** 창</span><span class="sxs-lookup"><span data-stu-id="09de2-114">**Drilldown** pane</span></span>  
 <span data-ttu-id="09de2-115">데이터 프로파일링 태스크에 사용되는 데이터 원본을 사용할 수 있는 경우 출력의 값과 일치하는 데이터의 행을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-115">Displays the rows of data that match a value in the output, if the data source that is used by the Data Profiling task is available.</span></span>  
  
 <span data-ttu-id="09de2-116">예를 들어 US State 열에 대한 열 값 분포 프로필의 출력을 보는 경우 **세부 값 분포** 창에 "WA"에 대한 행이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-116">For example, if you are viewing the output of a Column Value Distribution profile for a US State column, the **Detailed Value Distribution** pane might contain a row for "WA".</span></span> <span data-ttu-id="09de2-117">드릴다운 창에서 주 열의 값이 "WA"인 데이터의 행을 보려면 **세부 값 분포** 창에서 해당 행을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-117">Double-click the row in the **Detailed Value Distribution** pane to see the rows of data where the value of the state column is "WA" in the drilldown pane.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="09de2-118">동적 옵션</span><span class="sxs-lookup"><span data-stu-id="09de2-118">Dynamic Options</span></span>  
  
### <a name="profile-type--column-length-distribution-profile"></a><span data-ttu-id="09de2-119">프로필 유형 = 열 길이 분포 프로필</span><span class="sxs-lookup"><span data-stu-id="09de2-119">Profile Type = Column Length Distribution Profile</span></span>  
  
#### <a name="column-length-distribution-profile---column-pane"></a><span data-ttu-id="09de2-120">열 길이 분포 프로필 - \<column> 창</span><span class="sxs-lookup"><span data-stu-id="09de2-120">Column Length Distribution Profile - \<column> pane</span></span>  
 <span data-ttu-id="09de2-121">**최소 길이**</span><span class="sxs-lookup"><span data-stu-id="09de2-121">**Minimum Length**</span></span>  
 <span data-ttu-id="09de2-122">이 열의 값에 대한 최소 길이를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-122">Displays the minimum length of values in this column.</span></span>  
  
 <span data-ttu-id="09de2-123">**최대 길이**</span><span class="sxs-lookup"><span data-stu-id="09de2-123">**Maximum Length**</span></span>  
 <span data-ttu-id="09de2-124">이 열의 값에 대한 최대 길이를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-124">Displays the maximum length of values in this column.</span></span>  
  
 <span data-ttu-id="09de2-125">**선행 공백 무시**</span><span class="sxs-lookup"><span data-stu-id="09de2-125">**Ignore Leading Spaces**</span></span>  
 <span data-ttu-id="09de2-126">이 프로필이 True 또는 False의 `IgnoreLeadingSpaces` 값으로 계산되었는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-126">Displays whether this profile was computed with an `IgnoreLeadingSpaces` value of True or False.</span></span> <span data-ttu-id="09de2-127">이 속성은 데이터 프로파일링 태스크 편집기의 **프로필 요청** 페이지에서 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-127">This property was set on the **Profile Requests** page of the Data Profiling Task Editor.</span></span>  
  
 <span data-ttu-id="09de2-128">**후행 공백 무시**</span><span class="sxs-lookup"><span data-stu-id="09de2-128">**Ignore Trailing Spaces**</span></span>  
 <span data-ttu-id="09de2-129">이 프로필이 True 또는 False의 `IgnoreTrailingSpaces` 값으로 계산되었는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-129">Displays whether this profile was computed with an `IgnoreTrailingSpaces` value of True or False.</span></span> <span data-ttu-id="09de2-130">이 속성은 데이터 프로파일링 태스크 편집기의 **프로필 요청** 페이지에서 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-130">This property was set on the **Profile Requests** page of the Data Profiling Task Editor.</span></span>  
  
 <span data-ttu-id="09de2-131">**행 개수**</span><span class="sxs-lookup"><span data-stu-id="09de2-131">**Row Count**</span></span>  
 <span data-ttu-id="09de2-132">테이블 또는 뷰의 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-132">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="detailed-length-distribution-pane"></a><span data-ttu-id="09de2-133">세부 길이 분포 창</span><span class="sxs-lookup"><span data-stu-id="09de2-133">Detailed Length Distribution pane</span></span>  
 <span data-ttu-id="09de2-134">**길이**</span><span class="sxs-lookup"><span data-stu-id="09de2-134">**Length**</span></span>  
 <span data-ttu-id="09de2-135">프로파일링된 열에서 찾은 열 길이를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-135">Displays the column lengths found in the profiled column.</span></span>  
  
 <span data-ttu-id="09de2-136">**Count**</span><span class="sxs-lookup"><span data-stu-id="09de2-136">**Count**</span></span>  
 <span data-ttu-id="09de2-137">프로파일링된 열의 값에 **길이** 열에 표시된 길이가 지정된 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-137">Displays the number of rows in which the value of the profiled column has the length shown in the **Length** column.</span></span>  
  
 <span data-ttu-id="09de2-138">**Percentage**</span><span class="sxs-lookup"><span data-stu-id="09de2-138">**Percentage**</span></span>  
 <span data-ttu-id="09de2-139">프로파일링된 열의 값에 **길이** 열에 표시된 길이가 지정된 행의 비율을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-139">Displays the percentage of rows in which the value of the profiled column has the length shown in the **Length** column.</span></span>  
  
### <a name="profile-type--column-null-ratio-profile"></a><span data-ttu-id="09de2-140">프로필 유형 = 열 Null 비율 프로필</span><span class="sxs-lookup"><span data-stu-id="09de2-140">Profile Type = Column Null Ratio Profile</span></span>  
  
#### <a name="column-null-ratio-profile---column-pane"></a><span data-ttu-id="09de2-141">열 Null 비율 프로필 - \<column> 창</span><span class="sxs-lookup"><span data-stu-id="09de2-141">Column Null Ratio Profile - \<column> pane</span></span>  
 <span data-ttu-id="09de2-142">**Null 개수**</span><span class="sxs-lookup"><span data-stu-id="09de2-142">**Null Count**</span></span>  
 <span data-ttu-id="09de2-143">프로파일링된 열에 Null 값이 있는 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-143">Displays the number of rows in which the profiled column has a null value.</span></span>  
  
 <span data-ttu-id="09de2-144">**Null 백분율**</span><span class="sxs-lookup"><span data-stu-id="09de2-144">**Null Percentage**</span></span>  
 <span data-ttu-id="09de2-145">프로파일링된 열에 Null 값이 있는 행의 비율을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-145">Displays the percentage of rows in which the profiled column has a null value.</span></span>  
  
 <span data-ttu-id="09de2-146">**행 개수**</span><span class="sxs-lookup"><span data-stu-id="09de2-146">**Row Count**</span></span>  
 <span data-ttu-id="09de2-147">테이블 또는 뷰의 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-147">Displays the number of rows in the table or view.</span></span>  
  
### <a name="profile-type--column-pattern-profile"></a><span data-ttu-id="09de2-148">프로필 유형 = 열 패턴 프로필</span><span class="sxs-lookup"><span data-stu-id="09de2-148">Profile Type = Column Pattern Profile</span></span>  
  
#### <a name="column-pattern-profile---column-pane"></a><span data-ttu-id="09de2-149">열 패턴 프로필 - \<column> 창</span><span class="sxs-lookup"><span data-stu-id="09de2-149">Column Pattern Profile - \<column> pane</span></span>  
 <span data-ttu-id="09de2-150">**행 개수**</span><span class="sxs-lookup"><span data-stu-id="09de2-150">**Row Count**</span></span>  
 <span data-ttu-id="09de2-151">테이블 또는 뷰의 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-151">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="pattern-distribution-pane"></a><span data-ttu-id="09de2-152">패턴 분포 창</span><span class="sxs-lookup"><span data-stu-id="09de2-152">Pattern Distribution pane</span></span>  
 <span data-ttu-id="09de2-153">**패턴**</span><span class="sxs-lookup"><span data-stu-id="09de2-153">**Pattern**</span></span>  
 <span data-ttu-id="09de2-154">프로파일링된 열에 대해 계산된 패턴을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-154">Displays the patterns computed for the profiled column.</span></span>  
  
 <span data-ttu-id="09de2-155">**Percentage**</span><span class="sxs-lookup"><span data-stu-id="09de2-155">**Percentage**</span></span>  
 <span data-ttu-id="09de2-156">값이 **패턴** 열에 표시된 패턴과 일치하는 행의 비율을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-156">Displays the percentage of rows whose values match the pattern displayed in the **Pattern** column.</span></span>  
  
### <a name="profile-type--column-statistics-profile"></a><span data-ttu-id="09de2-157">프로필 유형 = 열 통계 프로필</span><span class="sxs-lookup"><span data-stu-id="09de2-157">Profile Type = Column Statistics Profile</span></span>  
  
#### <a name="column-statistics-profile---column-pane"></a><span data-ttu-id="09de2-158">열 통계 프로필 - \<column> 창</span><span class="sxs-lookup"><span data-stu-id="09de2-158">Column Statistics Profile - \<column> pane</span></span>  
 <span data-ttu-id="09de2-159">**최소**</span><span class="sxs-lookup"><span data-stu-id="09de2-159">**Minimum**</span></span>  
 <span data-ttu-id="09de2-160">프로파일링된 열에서 찾은 최소값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-160">Displays the minimum value found in the profiled column.</span></span>  
  
 <span data-ttu-id="09de2-161">**최댓값**</span><span class="sxs-lookup"><span data-stu-id="09de2-161">**Maximum**</span></span>  
 <span data-ttu-id="09de2-162">프로파일링된 열에서 찾은 최대값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-162">Displays the maximum value found in the profiled column.</span></span>  
  
 <span data-ttu-id="09de2-163">**평균값**</span><span class="sxs-lookup"><span data-stu-id="09de2-163">**Mean**</span></span>  
 <span data-ttu-id="09de2-164">프로파일링된 열에서 찾은 값의 평균을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-164">Displays the mean of the values found in the profiled column.</span></span>  
  
 <span data-ttu-id="09de2-165">**표준 편차**</span><span class="sxs-lookup"><span data-stu-id="09de2-165">**Standard Deviation**</span></span>  
 <span data-ttu-id="09de2-166">프로파일링된 열에서 찾은 값의 표준 편차를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-166">Displays the standard deviation of the values found in the profiled column.</span></span>  
  
### <a name="profile-type--column-value-distribution-profile"></a><span data-ttu-id="09de2-167">프로필 유형 = 열 값 분포 프로필</span><span class="sxs-lookup"><span data-stu-id="09de2-167">Profile Type = Column Value Distribution Profile</span></span>  
  
#### <a name="column-value-distribution-profile---column-pane"></a><span data-ttu-id="09de2-168">열 값 분포 프로필 - \<column> 창</span><span class="sxs-lookup"><span data-stu-id="09de2-168">Column Value Distribution Profile - \<column> pane</span></span>  
 <span data-ttu-id="09de2-169">**고유 값 수**</span><span class="sxs-lookup"><span data-stu-id="09de2-169">**Number of Distinct Values**</span></span>  
 <span data-ttu-id="09de2-170">프로파일링된 열에서 찾은 고유 값의 개수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-170">Displays the count of distinct values found in the profiled column.</span></span>  
  
 <span data-ttu-id="09de2-171">**행 개수**</span><span class="sxs-lookup"><span data-stu-id="09de2-171">**Row Count**</span></span>  
 <span data-ttu-id="09de2-172">테이블 또는 뷰의 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-172">Displays the number of rows in the table or view.</span></span>  
  
#### <a name="detailed-value-distribution-pane"></a><span data-ttu-id="09de2-173">세부 값 분포 창</span><span class="sxs-lookup"><span data-stu-id="09de2-173">Detailed Value Distribution pane</span></span>  
 <span data-ttu-id="09de2-174">**값**</span><span class="sxs-lookup"><span data-stu-id="09de2-174">**Value**</span></span>  
 <span data-ttu-id="09de2-175">프로파일링된 열에서 찾은 고유 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-175">Displays the distinct values found in the profiled column.</span></span>  
  
 <span data-ttu-id="09de2-176">**Count**</span><span class="sxs-lookup"><span data-stu-id="09de2-176">**Count**</span></span>  
 <span data-ttu-id="09de2-177">프로파일링된 열에 **값** 열에 표시된 값이 있는 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-177">Displays the number of rows in which the profiled column has the value shown in the **Value** column.</span></span>  
  
 <span data-ttu-id="09de2-178">**Percentage**</span><span class="sxs-lookup"><span data-stu-id="09de2-178">**Percentage**</span></span>  
 <span data-ttu-id="09de2-179">프로파일링된 열에 **값** 열에 표시된 값이 있는 행의 비율을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-179">Displays the percentage of rows in which the profiled column has the value shown in the **Value** column.</span></span>  
  
### <a name="profile-type--candidate-key-profile"></a><span data-ttu-id="09de2-180">프로필 유형 = 후보 키 프로필</span><span class="sxs-lookup"><span data-stu-id="09de2-180">Profile Type = Candidate Key Profile</span></span>  
  
#### <a name="candidate-key-profile---table-pane"></a><span data-ttu-id="09de2-181">후보 키 프로필 - \<table> 창</span><span class="sxs-lookup"><span data-stu-id="09de2-181">Candidate Key Profile - \<table> pane</span></span>  
 <span data-ttu-id="09de2-182">**키 열**</span><span class="sxs-lookup"><span data-stu-id="09de2-182">**Key Columns**</span></span>  
 <span data-ttu-id="09de2-183">프로파일링에 대해 후보 키로 선택된 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-183">Displays the columns that were selected for profiling as a candidate key.</span></span>  
  
 <span data-ttu-id="09de2-184">**키 수준**</span><span class="sxs-lookup"><span data-stu-id="09de2-184">**Key Strength**</span></span>  
 <span data-ttu-id="09de2-185">후보 키 열 또는 열 조합의 수준(비율)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-185">Displays the strength (as a percentage) of the candidate key column or combination of columns.</span></span> <span data-ttu-id="09de2-186">100% 미만의 키 수준은 중복 값이 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-186">A key strength of less than 100% indicates that duplicate values exist.</span></span>  
  
#### <a name="key-violations-pane"></a><span data-ttu-id="09de2-187">키 위반 창</span><span class="sxs-lookup"><span data-stu-id="09de2-187">Key Violations pane</span></span>  
 <span data-ttu-id="09de2-188">**\<column1>, \<column2>, 등**</span><span class="sxs-lookup"><span data-stu-id="09de2-188">**\<column1>, \<column2>, etc.**</span></span>  
 <span data-ttu-id="09de2-189">프로파일링된 열에서 찾은 중복 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-189">Displays the duplicate values that were found in the profiled column.</span></span>  
  
 <span data-ttu-id="09de2-190">**Count**</span><span class="sxs-lookup"><span data-stu-id="09de2-190">**Count**</span></span>  
 <span data-ttu-id="09de2-191">지정된 열에 첫 번째 열에 표시된 값이 있는 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-191">Displays the number of rows in which the specified column has the value shown in the first column.</span></span>  
  
### <a name="profile-type--functional-dependency-profile"></a><span data-ttu-id="09de2-192">프로필 유형 = 함수 종속성 프로필</span><span class="sxs-lookup"><span data-stu-id="09de2-192">Profile Type = Functional Dependency Profile</span></span>  
  
#### <a name="functional-dependency-profile-pane"></a><span data-ttu-id="09de2-193">함수 종속성 프로필 창</span><span class="sxs-lookup"><span data-stu-id="09de2-193">Functional Dependency Profile pane</span></span>  
 <span data-ttu-id="09de2-194">**결정 열**</span><span class="sxs-lookup"><span data-stu-id="09de2-194">**Determinant Columns**</span></span>  
 <span data-ttu-id="09de2-195">결정 열로 선택된 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-195">Displays the column or columns selected as the determinant column.</span></span> <span data-ttu-id="09de2-196">같은 미국 우편 번호가 항상 같은 주여야 하는 예에서는 우편 번호가 결정 열입니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-196">In the example where the same United States Zip Code should always have the same state, the Zip Code is the determinant column.</span></span>  
  
 <span data-ttu-id="09de2-197">**종속 열**</span><span class="sxs-lookup"><span data-stu-id="09de2-197">**Dependent Columns**</span></span>  
 <span data-ttu-id="09de2-198">종속 열로 선택된 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-198">Displays the column or columns selected as the dependent column.</span></span> <span data-ttu-id="09de2-199">같은 미국 우편 번호가 항상 같은 주여야 하는 예에서는 주가 종속 열입니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-199">In the example where the same United States Zip Code should always have the same state, the state is the dependent column.</span></span>  
  
 <span data-ttu-id="09de2-200">**함수 종속성 수준**</span><span class="sxs-lookup"><span data-stu-id="09de2-200">**Functional Dependency Strength**</span></span>  
 <span data-ttu-id="09de2-201">열 간 함수 종속성의 수준(비율)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-201">Displays the strength (as a percentage) of the functional dependency between columns.</span></span> <span data-ttu-id="09de2-202">100% 미만의 키 수준은 결정 값이 종속 값을 결정하지 않는 경우가 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-202">A key strength of less than 100% indicates that there are cases where the determinant value does not determine the dependent value.</span></span> <span data-ttu-id="09de2-203">같은 미국 우편 번호가 항상 같은 주여야 하는 예에서 이는 일부 주 값이 잘못되었음을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-203">In the example where the same United States Zip Code should always have the same state, this probably indicates some state values are not valid.</span></span>  
  
#### <a name="functional-dependency-violations-pane"></a><span data-ttu-id="09de2-204">함수 종속성 위반 창</span><span class="sxs-lookup"><span data-stu-id="09de2-204">Functional Dependency Violations pane</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09de2-205">데이터에서 잘못된 값의 비율이 높으면 함수 종속성 프로필에서 예기치 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-205">A high percentage of erroneous values in the data could lead to unexpected results from a Functional Dependency profile.</span></span> <span data-ttu-id="09de2-206">예를 들어 Postal Code 값 "98052"에 대한 State 값이 행의 90%에 대해 "WI"인 경우</span><span class="sxs-lookup"><span data-stu-id="09de2-206">For example, 90% of the rows have a State value of "WI" for a Postal Code value of "98052."</span></span> <span data-ttu-id="09de2-207">프로필은 올바른 주 값 "WA"를 포함하는 행을 위반으로 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-207">The profile reports rows that contain the correct state value of "WA" as violations.</span></span>  
  
 **\<determinant column name>**  
 <span data-ttu-id="09de2-208">이 함수 종속성 위반 인스턴스에서 결정 열 또는 열 조합의 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-208">Displays the value of the determinant column or combination of columns in this instance of a functional dependency violation.</span></span>  
  
 **\<dependent column name>**  
 <span data-ttu-id="09de2-209">이 함수 종속성 위반 인스턴스에서 종속 열의 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-209">Displays the value of the dependent column in this instance of a functional dependency violation.</span></span>  
  
 <span data-ttu-id="09de2-210">**지원 개수**</span><span class="sxs-lookup"><span data-stu-id="09de2-210">**Support Count**</span></span>  
 <span data-ttu-id="09de2-211">결정 열 값이 종속 열을 결정하는 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-211">Displays the number of rows in which the determinant column value determines the dependent column.</span></span>  
  
 <span data-ttu-id="09de2-212">**위반 개수**</span><span class="sxs-lookup"><span data-stu-id="09de2-212">**Violation Count**</span></span>  
 <span data-ttu-id="09de2-213">결정 열 값이 종속 열을 결정하지 않는 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-213">Displays the number of rows in which the determinant column value does not determine the dependent column.</span></span> <span data-ttu-id="09de2-214">이는 종속 값이 **\<dependent column name>** 열에 표시된 값인 행입니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-214">(These are the rows where the dependent value is the value shown in the **\<dependent column name>** column.)</span></span>  
  
 <span data-ttu-id="09de2-215">**지원 백분율**</span><span class="sxs-lookup"><span data-stu-id="09de2-215">**Support Percentage**</span></span>  
 <span data-ttu-id="09de2-216">결정 열이 종속 열을 결정하는 행의 비율을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-216">Displays the percentage of rows in which the determinant column determines the dependent column.</span></span>  
  
### <a name="profile-type--value-inclusion-profile"></a><span data-ttu-id="09de2-217">프로필 유형 = 값 포함 프로필</span><span class="sxs-lookup"><span data-stu-id="09de2-217">Profile Type = Value Inclusion Profile</span></span>  
  
#### <a name="value-inclusion-profile-pane"></a><span data-ttu-id="09de2-218">값 포함 프로필 창</span><span class="sxs-lookup"><span data-stu-id="09de2-218">Value Inclusion Profile pane</span></span>  
 <span data-ttu-id="09de2-219">**하위 집합측 열**</span><span class="sxs-lookup"><span data-stu-id="09de2-219">**Subset Side Columns**</span></span>  
 <span data-ttu-id="09de2-220">상위 집합 열에 있는지 여부를 확인하기 위해 프로파일링된 열 또는 열 조합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-220">Displays the column or combination of columns that were profiled to determine whether they are in the superset columns.</span></span>  
  
 <span data-ttu-id="09de2-221">**상위 집합측 열**</span><span class="sxs-lookup"><span data-stu-id="09de2-221">**Superset Side Columns**</span></span>  
 <span data-ttu-id="09de2-222">하위 집합 열의 값을 포함하는지 여부를 확인하기 위해 프로파일링된 열 또는 열 조합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-222">Displays the column or combination of columns that were profiled to determine whether they include the values in the subset columns.</span></span>  
  
 <span data-ttu-id="09de2-223">**포함 수준**</span><span class="sxs-lookup"><span data-stu-id="09de2-223">**Inclusion Strength**</span></span>  
 <span data-ttu-id="09de2-224">열 간 겹침의 수준(비율)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-224">Displays the strength (as a percentage) of the overlap between columns.</span></span> <span data-ttu-id="09de2-225">100% 미만의 키 수준은 하위 집합 값이 상위 집합 값에 없는 경우가 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-225">A key strength of less than 100% indicates that there are cases where the subset value is not found among the superset values.</span></span>  
  
#### <a name="inclusion-violations-pane"></a><span data-ttu-id="09de2-226">포함 위반 창</span><span class="sxs-lookup"><span data-stu-id="09de2-226">Inclusion Violations pane</span></span>  
 <span data-ttu-id="09de2-227">**\<column1>, \<column2>, 등**</span><span class="sxs-lookup"><span data-stu-id="09de2-227">**\<column1>, \<column2>, etc.**</span></span>  
 <span data-ttu-id="09de2-228">상위 집합 열에서 찾지 못한 하위 집합 열의 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-228">Displays the values in the subset column or columns that were not found in the superset column or columns.</span></span>  
  
 <span data-ttu-id="09de2-229">**Count**</span><span class="sxs-lookup"><span data-stu-id="09de2-229">**Count**</span></span>  
 <span data-ttu-id="09de2-230">지정된 열에 첫 번째 열에 표시된 값이 있는 행 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="09de2-230">Displays the number of rows in which the specified column has the value shown in the first column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09de2-231">참고 항목</span><span class="sxs-lookup"><span data-stu-id="09de2-231">See Also</span></span>  
 <span data-ttu-id="09de2-232">[데이터 프로필 뷰어](control-flow/data-profile-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="09de2-232">[Data Profile Viewer](control-flow/data-profile-viewer.md) </span></span>  
 [<span data-ttu-id="09de2-233">데이터 프로파일링 태스크 및 뷰어</span><span class="sxs-lookup"><span data-stu-id="09de2-233">Data Profiling Task and Viewer</span></span>](control-flow/data-profiling-task-and-viewer.md)  
  
  
