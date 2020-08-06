---
title: '3 단원: 열 이름 바꾸기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fc8ba1a-2b30-4775-9b3b-c09dee711b3e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 59904f1110455b65679b3d19e6e8b7c731465ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639007"
---
# <a name="lesson-3-rename-columns"></a><span data-ttu-id="e2313-102">3단원: 열 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="e2313-102">Lesson 3: Rename Columns</span></span>
  <span data-ttu-id="e2313-103">이 단원에서는 가져온 각 테이블에 있는 여러 열의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-103">In this lesson, you will rename many of the columns in each table you imported.</span></span> <span data-ttu-id="e2313-104">열 이름을 바꾸면 모델 디자이너에서 열을 명확하게 식별하고 탐색할 수 있을 뿐 아니라 사용자는 클라이언트 애플리케이션에서 필드를 손쉽게 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-104">Renaming makes columns more identifiable and easier to navigate in both the model designer as well by users selecting fields in a client application.</span></span> <span data-ttu-id="e2313-105">자세한 내용은 [테이블 또는 열 이름 바꾸기&#40;SSAS 테이블 형식&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2313-105">To learn more, see [Rename a Table or Column &#40;SSAS Tabular&#41;](tabular-models/rename-a-table-or-column-ssas-tabular.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e2313-106">이 자습서를 완료하기 위해 열 이름을 바꿀 필요는 없습니다. 그러나 관계 만들기, DAX 수식을 사용해 계산 열 및 측정값 만들기에 대해 소개하는 단원을 비롯한 나머지 단원에서는 이 단원에 설명된 알아보기 쉬운 열 이름을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-106">Renaming columns is not necessary to complete this tutorial; however, remaining lessons, in particular those that include creating relationships and creating calculated columns and measures using DAX formulas, refer to the column friendly names described in this lesson.</span></span> <span data-ttu-id="e2313-107">열 이름을 바꾸지 않으려는 경우 이 단원에 제공된 원래 원본 열 이름을 사용하도록 5, 6, 7단원에서 DAX 수식을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-107">If you choose not to rename columns, you will have to edit the DAX formulas in lessons 5, 6, and 7 to use the original source column names provided in this lesson.</span></span>  
  
 <span data-ttu-id="e2313-108">이 단원을 완료하기 위한 예상 시간: **20분**</span><span class="sxs-lookup"><span data-stu-id="e2313-108">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e2313-109">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e2313-109">Prerequisites</span></span>  
 <span data-ttu-id="e2313-110">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="e2313-111">이 단원의 태스크를 수행하려면 이전 단원인 [2단원: 데이터 추가](lesson-2-add-data.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 2: Add Data](lesson-2-add-data.md).</span></span>  
  
## <a name="rename-columns"></a><span data-ttu-id="e2313-112">열 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="e2313-112">Rename Columns</span></span>  
  
#### <a name="to-rename-columns"></a><span data-ttu-id="e2313-113">열 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="e2313-113">To rename columns</span></span>  
  
1.  <span data-ttu-id="e2313-114">모델 디자이너에서 **Customer** 테이블(탭)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-114">In the model designer, click the **Customer** table (tab).</span></span>  
  
     <span data-ttu-id="e2313-115">탭을 클릭하면 해당 테이블이 모델 디자이너 창에서 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-115">When you click a tab, that table becomes active in the model designer window.</span></span>  
  
2.  <span data-ttu-id="e2313-116">**Customerkey** 열 이름을 두 번 클릭 하 고를 입력 한 `Customer  Id` 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-116">Double click the **CustomerKey** column name, then type `Customer  Id`, and then press ENTER.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="e2313-117">열의 **속성** 창이 나 다이어그램 뷰에서 열 **이름** 속성의 열 이름을 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-117">You can also rename a column in the **Column Name** property in the column's **Properties** window, or in Diagram View.</span></span>  
  
3.  <span data-ttu-id="e2313-118">**Customer** 테이블의 나머지 열과 나머지 테이블에 있는 열의 이름을 바꿔 원본 이름을 알아보기 쉬운 이름으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e2313-118">Rename the remaining columns in the **Customer** table, as well as the columns in the remaining tables, replacing the source name with the friendly name:</span></span>  
  
     <span data-ttu-id="e2313-119">**Customer 테이블**</span><span class="sxs-lookup"><span data-stu-id="e2313-119">**Customer Table**</span></span>  
  
    |<span data-ttu-id="e2313-120">원본 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-120">Source Name</span></span>|<span data-ttu-id="e2313-121">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-121">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e2313-122">GeographyKey</span><span class="sxs-lookup"><span data-stu-id="e2313-122">GeographyKey</span></span>|<span data-ttu-id="e2313-123">Geography Id</span><span class="sxs-lookup"><span data-stu-id="e2313-123">Geography Id</span></span>|  
    |<span data-ttu-id="e2313-124">CustomerAlternateKey</span><span class="sxs-lookup"><span data-stu-id="e2313-124">CustomerAlternateKey</span></span>|<span data-ttu-id="e2313-125">Customer Alternate Id</span><span class="sxs-lookup"><span data-stu-id="e2313-125">Customer Alternate Id</span></span>|  
    |<span data-ttu-id="e2313-126">FirstName</span><span class="sxs-lookup"><span data-stu-id="e2313-126">FirstName</span></span>|<span data-ttu-id="e2313-127">이름</span><span class="sxs-lookup"><span data-stu-id="e2313-127">First Name</span></span>|  
    |<span data-ttu-id="e2313-128">MiddleName</span><span class="sxs-lookup"><span data-stu-id="e2313-128">MiddleName</span></span>|<span data-ttu-id="e2313-129">Middle Name</span><span class="sxs-lookup"><span data-stu-id="e2313-129">Middle Name</span></span>|  
    |<span data-ttu-id="e2313-130">LastName</span><span class="sxs-lookup"><span data-stu-id="e2313-130">LastName</span></span>|<span data-ttu-id="e2313-131">성</span><span class="sxs-lookup"><span data-stu-id="e2313-131">Last Name</span></span>|  
    |<span data-ttu-id="e2313-132">NameStyle</span><span class="sxs-lookup"><span data-stu-id="e2313-132">NameStyle</span></span>|<span data-ttu-id="e2313-133">Name Style</span><span class="sxs-lookup"><span data-stu-id="e2313-133">Name Style</span></span>|  
    |<span data-ttu-id="e2313-134">BirthDate</span><span class="sxs-lookup"><span data-stu-id="e2313-134">BirthDate</span></span>|<span data-ttu-id="e2313-135">Birth Date</span><span class="sxs-lookup"><span data-stu-id="e2313-135">Birth Date</span></span>|  
    |<span data-ttu-id="e2313-136">MaritalStatus</span><span class="sxs-lookup"><span data-stu-id="e2313-136">MaritalStatus</span></span>|<span data-ttu-id="e2313-137">Marital Status</span><span class="sxs-lookup"><span data-stu-id="e2313-137">Marital Status</span></span>|  
    |<span data-ttu-id="e2313-138">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="e2313-138">EmailAddress</span></span>|<span data-ttu-id="e2313-139">메일 주소</span><span class="sxs-lookup"><span data-stu-id="e2313-139">Email Address</span></span>|  
    |<span data-ttu-id="e2313-140">YearlyIncome</span><span class="sxs-lookup"><span data-stu-id="e2313-140">YearlyIncome</span></span>|<span data-ttu-id="e2313-141">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="e2313-141">Yearly Income</span></span>|  
    |<span data-ttu-id="e2313-142">TotalChildren</span><span class="sxs-lookup"><span data-stu-id="e2313-142">TotalChildren</span></span>|<span data-ttu-id="e2313-143">Total Children</span><span class="sxs-lookup"><span data-stu-id="e2313-143">Total Children</span></span>|  
    |<span data-ttu-id="e2313-144">NumberChildrenAtHome</span><span class="sxs-lookup"><span data-stu-id="e2313-144">NumberChildrenAtHome</span></span>|<span data-ttu-id="e2313-145">Number of Children At Home</span><span class="sxs-lookup"><span data-stu-id="e2313-145">Number of Children At Home</span></span>|  
    |<span data-ttu-id="e2313-146">EnglishEducation</span><span class="sxs-lookup"><span data-stu-id="e2313-146">EnglishEducation</span></span>|<span data-ttu-id="e2313-147">Education</span><span class="sxs-lookup"><span data-stu-id="e2313-147">Education</span></span>|  
    |<span data-ttu-id="e2313-148">EnglishOccupation</span><span class="sxs-lookup"><span data-stu-id="e2313-148">EnglishOccupation</span></span>|<span data-ttu-id="e2313-149">Occupation</span><span class="sxs-lookup"><span data-stu-id="e2313-149">Occupation</span></span>|  
    |<span data-ttu-id="e2313-150">HouseOwnerFlag</span><span class="sxs-lookup"><span data-stu-id="e2313-150">HouseOwnerFlag</span></span>|<span data-ttu-id="e2313-151">Owns House</span><span class="sxs-lookup"><span data-stu-id="e2313-151">Owns House</span></span>|  
    |<span data-ttu-id="e2313-152">NumberCarsOwned</span><span class="sxs-lookup"><span data-stu-id="e2313-152">NumberCarsOwned</span></span>|<span data-ttu-id="e2313-153">Number of Cars Owned</span><span class="sxs-lookup"><span data-stu-id="e2313-153">Number of Cars Owned</span></span>|  
    |<span data-ttu-id="e2313-154">AddressLine1</span><span class="sxs-lookup"><span data-stu-id="e2313-154">AddressLine1</span></span>|<span data-ttu-id="e2313-155">Address Line 1</span><span class="sxs-lookup"><span data-stu-id="e2313-155">Address Line 1</span></span>|  
    |<span data-ttu-id="e2313-156">AddressLine2</span><span class="sxs-lookup"><span data-stu-id="e2313-156">AddressLine2</span></span>|<span data-ttu-id="e2313-157">Address Line 2</span><span class="sxs-lookup"><span data-stu-id="e2313-157">Address Line 2</span></span>|  
    |<span data-ttu-id="e2313-158">전화</span><span class="sxs-lookup"><span data-stu-id="e2313-158">Phone</span></span>|<span data-ttu-id="e2313-159">전화 번호</span><span class="sxs-lookup"><span data-stu-id="e2313-159">Phone Number</span></span>|  
    |<span data-ttu-id="e2313-160">DateFirstPurchase</span><span class="sxs-lookup"><span data-stu-id="e2313-160">DateFirstPurchase</span></span>|<span data-ttu-id="e2313-161">Date of First Purchase</span><span class="sxs-lookup"><span data-stu-id="e2313-161">Date of First Purchase</span></span>|  
    |<span data-ttu-id="e2313-162">CommuteDistance</span><span class="sxs-lookup"><span data-stu-id="e2313-162">CommuteDistance</span></span>|<span data-ttu-id="e2313-163">Commute Distance</span><span class="sxs-lookup"><span data-stu-id="e2313-163">Commute Distance</span></span>|  
  
     <span data-ttu-id="e2313-164">**날짜**</span><span class="sxs-lookup"><span data-stu-id="e2313-164">**Date**</span></span>  
  
    |<span data-ttu-id="e2313-165">원본 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-165">Source Name</span></span>|<span data-ttu-id="e2313-166">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-166">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e2313-167">FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="e2313-167">FullDateAlternateKey</span></span>|<span data-ttu-id="e2313-168">Date</span><span class="sxs-lookup"><span data-stu-id="e2313-168">Date</span></span>|  
    |<span data-ttu-id="e2313-169">DayNumberOfWeek</span><span class="sxs-lookup"><span data-stu-id="e2313-169">DayNumberOfWeek</span></span>|<span data-ttu-id="e2313-170">Day Number of Week</span><span class="sxs-lookup"><span data-stu-id="e2313-170">Day Number of Week</span></span>|  
    |<span data-ttu-id="e2313-171">EnglishDayNameOfWeek</span><span class="sxs-lookup"><span data-stu-id="e2313-171">EnglishDayNameOfWeek</span></span>|<span data-ttu-id="e2313-172">Day Name</span><span class="sxs-lookup"><span data-stu-id="e2313-172">Day Name</span></span>|  
    |<span data-ttu-id="e2313-173">DayNumberOfMonth</span><span class="sxs-lookup"><span data-stu-id="e2313-173">DayNumberOfMonth</span></span>|<span data-ttu-id="e2313-174">월간 일자</span><span class="sxs-lookup"><span data-stu-id="e2313-174">Day of Month</span></span>|  
    |<span data-ttu-id="e2313-175">DayNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="e2313-175">DayNumberOfYear</span></span>|<span data-ttu-id="e2313-176">연간 일자</span><span class="sxs-lookup"><span data-stu-id="e2313-176">Day of Year</span></span>|  
    |<span data-ttu-id="e2313-177">WeekNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="e2313-177">WeekNumberOfYear</span></span>|<span data-ttu-id="e2313-178">Week Number of Year</span><span class="sxs-lookup"><span data-stu-id="e2313-178">Week Number of Year</span></span>|  
    |<span data-ttu-id="e2313-179">EnglishMonthName</span><span class="sxs-lookup"><span data-stu-id="e2313-179">EnglishMonthName</span></span>|<span data-ttu-id="e2313-180">월 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-180">Month Name</span></span>|  
    |<span data-ttu-id="e2313-181">MonthNumberOfYear</span><span class="sxs-lookup"><span data-stu-id="e2313-181">MonthNumberOfYear</span></span>|<span data-ttu-id="e2313-182">월</span><span class="sxs-lookup"><span data-stu-id="e2313-182">Month</span></span>|  
    |<span data-ttu-id="e2313-183">CalendarQuarter</span><span class="sxs-lookup"><span data-stu-id="e2313-183">CalendarQuarter</span></span>|<span data-ttu-id="e2313-184">Calendar Quarter</span><span class="sxs-lookup"><span data-stu-id="e2313-184">Calendar Quarter</span></span>|  
    |<span data-ttu-id="e2313-185">CalendarYear</span><span class="sxs-lookup"><span data-stu-id="e2313-185">CalendarYear</span></span>|<span data-ttu-id="e2313-186">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="e2313-186">Calendar Year</span></span>|  
    |<span data-ttu-id="e2313-187">CalendarSemester</span><span class="sxs-lookup"><span data-stu-id="e2313-187">CalendarSemester</span></span>|<span data-ttu-id="e2313-188">Calendar Semester</span><span class="sxs-lookup"><span data-stu-id="e2313-188">Calendar Semester</span></span>|  
    |<span data-ttu-id="e2313-189">FiscalQuarter</span><span class="sxs-lookup"><span data-stu-id="e2313-189">FiscalQuarter</span></span>|<span data-ttu-id="e2313-190">Fiscal Quarter</span><span class="sxs-lookup"><span data-stu-id="e2313-190">Fiscal Quarter</span></span>|  
    |<span data-ttu-id="e2313-191">FiscalYear</span><span class="sxs-lookup"><span data-stu-id="e2313-191">FiscalYear</span></span>|<span data-ttu-id="e2313-192">Fiscal Year</span><span class="sxs-lookup"><span data-stu-id="e2313-192">Fiscal Year</span></span>|  
    |<span data-ttu-id="e2313-193">FiscalSemester</span><span class="sxs-lookup"><span data-stu-id="e2313-193">FiscalSemester</span></span>|<span data-ttu-id="e2313-194">Fiscal Semester</span><span class="sxs-lookup"><span data-stu-id="e2313-194">Fiscal Semester</span></span>|  
  
     <span data-ttu-id="e2313-195">**지리**</span><span class="sxs-lookup"><span data-stu-id="e2313-195">**Geography**</span></span>  
  
    |<span data-ttu-id="e2313-196">원본 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-196">Source Name</span></span>|<span data-ttu-id="e2313-197">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-197">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e2313-198">GeographyKey</span><span class="sxs-lookup"><span data-stu-id="e2313-198">GeographyKey</span></span>|<span data-ttu-id="e2313-199">Geography Id</span><span class="sxs-lookup"><span data-stu-id="e2313-199">Geography Id</span></span>|  
    |<span data-ttu-id="e2313-200">StateProvinceCode</span><span class="sxs-lookup"><span data-stu-id="e2313-200">StateProvinceCode</span></span>|<span data-ttu-id="e2313-201">State Province Code</span><span class="sxs-lookup"><span data-stu-id="e2313-201">State Province Code</span></span>|  
    |<span data-ttu-id="e2313-202">StateProvinceName</span><span class="sxs-lookup"><span data-stu-id="e2313-202">StateProvinceName</span></span>|<span data-ttu-id="e2313-203">State Province Name</span><span class="sxs-lookup"><span data-stu-id="e2313-203">State Province Name</span></span>|  
    |<span data-ttu-id="e2313-204">CountryRegionCode</span><span class="sxs-lookup"><span data-stu-id="e2313-204">CountryRegionCode</span></span>|<span data-ttu-id="e2313-205">Country Region Code</span><span class="sxs-lookup"><span data-stu-id="e2313-205">Country Region Code</span></span>|  
    |<span data-ttu-id="e2313-206">EnglishCountryRegionName</span><span class="sxs-lookup"><span data-stu-id="e2313-206">EnglishCountryRegionName</span></span>|<span data-ttu-id="e2313-207">Country Region Name</span><span class="sxs-lookup"><span data-stu-id="e2313-207">Country Region Name</span></span>|  
    |<span data-ttu-id="e2313-208">우편 번호</span><span class="sxs-lookup"><span data-stu-id="e2313-208">PostalCode</span></span>|<span data-ttu-id="e2313-209">우편 번호</span><span class="sxs-lookup"><span data-stu-id="e2313-209">Postal Code</span></span>|  
    |<span data-ttu-id="e2313-210">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="e2313-210">SalesTerritoryKey</span></span>|<span data-ttu-id="e2313-211">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="e2313-211">Sales Territory Id</span></span>|  
  
     <span data-ttu-id="e2313-212">**Product**</span><span class="sxs-lookup"><span data-stu-id="e2313-212">**Product**</span></span>  
  
    |<span data-ttu-id="e2313-213">원본 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-213">Source Name</span></span>|<span data-ttu-id="e2313-214">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-214">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e2313-215">ProductKey</span><span class="sxs-lookup"><span data-stu-id="e2313-215">ProductKey</span></span>|<span data-ttu-id="e2313-216">Product Id</span><span class="sxs-lookup"><span data-stu-id="e2313-216">Product Id</span></span>|  
    |<span data-ttu-id="e2313-217">ProductAlternateKey</span><span class="sxs-lookup"><span data-stu-id="e2313-217">ProductAlternateKey</span></span>|<span data-ttu-id="e2313-218">Product Alternate Id</span><span class="sxs-lookup"><span data-stu-id="e2313-218">Product Alternate Id</span></span>|  
    |<span data-ttu-id="e2313-219">ProductSubcategoryKey</span><span class="sxs-lookup"><span data-stu-id="e2313-219">ProductSubcategoryKey</span></span>|<span data-ttu-id="e2313-220">Product Subcategory Id</span><span class="sxs-lookup"><span data-stu-id="e2313-220">Product Subcategory Id</span></span>|  
    |<span data-ttu-id="e2313-221">WeightUnitMeasureCode</span><span class="sxs-lookup"><span data-stu-id="e2313-221">WeightUnitMeasureCode</span></span>|<span data-ttu-id="e2313-222">Weight Unit Code</span><span class="sxs-lookup"><span data-stu-id="e2313-222">Weight Unit Code</span></span>|  
    |<span data-ttu-id="e2313-223">SizeUnitMeasureCode</span><span class="sxs-lookup"><span data-stu-id="e2313-223">SizeUnitMeasureCode</span></span>|<span data-ttu-id="e2313-224">Size Unit Code</span><span class="sxs-lookup"><span data-stu-id="e2313-224">Size Unit Code</span></span>|  
    |<span data-ttu-id="e2313-225">EnglishProductName</span><span class="sxs-lookup"><span data-stu-id="e2313-225">EnglishProductName</span></span>|<span data-ttu-id="e2313-226">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-226">Product Name</span></span>|  
    |<span data-ttu-id="e2313-227">StandardCost</span><span class="sxs-lookup"><span data-stu-id="e2313-227">StandardCost</span></span>|<span data-ttu-id="e2313-228">Standard Cost</span><span class="sxs-lookup"><span data-stu-id="e2313-228">Standard Cost</span></span>|  
    |<span data-ttu-id="e2313-229">FinishedGoodsFlag</span><span class="sxs-lookup"><span data-stu-id="e2313-229">FinishedGoodsFlag</span></span>|<span data-ttu-id="e2313-230">Is Finished Product</span><span class="sxs-lookup"><span data-stu-id="e2313-230">Is Finished Product</span></span>|  
    |<span data-ttu-id="e2313-231">SafetyStockLevel</span><span class="sxs-lookup"><span data-stu-id="e2313-231">SafetyStockLevel</span></span>|<span data-ttu-id="e2313-232">Safety Stock Level</span><span class="sxs-lookup"><span data-stu-id="e2313-232">Safety Stock Level</span></span>|  
    |<span data-ttu-id="e2313-233">ReorderPoint</span><span class="sxs-lookup"><span data-stu-id="e2313-233">ReorderPoint</span></span>|<span data-ttu-id="e2313-234">Reorder Point</span><span class="sxs-lookup"><span data-stu-id="e2313-234">Reorder Point</span></span>|  
    |<span data-ttu-id="e2313-235">ListPrice</span><span class="sxs-lookup"><span data-stu-id="e2313-235">ListPrice</span></span>|<span data-ttu-id="e2313-236">List Price</span><span class="sxs-lookup"><span data-stu-id="e2313-236">List Price</span></span>|  
    |<span data-ttu-id="e2313-237">SizeRange</span><span class="sxs-lookup"><span data-stu-id="e2313-237">SizeRange</span></span>|<span data-ttu-id="e2313-238">Size Range</span><span class="sxs-lookup"><span data-stu-id="e2313-238">Size Range</span></span>|  
    |<span data-ttu-id="e2313-239">DaysToManufacture</span><span class="sxs-lookup"><span data-stu-id="e2313-239">DaysToManufacture</span></span>|<span data-ttu-id="e2313-240">Days to Manufacture</span><span class="sxs-lookup"><span data-stu-id="e2313-240">Days to Manufacture</span></span>|  
    |<span data-ttu-id="e2313-241">ProductLine</span><span class="sxs-lookup"><span data-stu-id="e2313-241">ProductLine</span></span>|<span data-ttu-id="e2313-242">Product Line</span><span class="sxs-lookup"><span data-stu-id="e2313-242">Product Line</span></span>|  
    |<span data-ttu-id="e2313-243">Dealer Price</span><span class="sxs-lookup"><span data-stu-id="e2313-243">Dealer Price</span></span>|<span data-ttu-id="e2313-244">Dealer Price</span><span class="sxs-lookup"><span data-stu-id="e2313-244">Dealer Price</span></span>|  
    |<span data-ttu-id="e2313-245">ModelName</span><span class="sxs-lookup"><span data-stu-id="e2313-245">ModelName</span></span>|<span data-ttu-id="e2313-246">모델 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-246">Model Name</span></span>|  
    |<span data-ttu-id="e2313-247">LargePhoto</span><span class="sxs-lookup"><span data-stu-id="e2313-247">LargePhoto</span></span>|<span data-ttu-id="e2313-248">Large Photo</span><span class="sxs-lookup"><span data-stu-id="e2313-248">Large Photo</span></span>|  
    |<span data-ttu-id="e2313-249">EnglishDescription</span><span class="sxs-lookup"><span data-stu-id="e2313-249">EnglishDescription</span></span>|<span data-ttu-id="e2313-250">Description</span><span class="sxs-lookup"><span data-stu-id="e2313-250">Description</span></span>|  
    |<span data-ttu-id="e2313-251">StartDate</span><span class="sxs-lookup"><span data-stu-id="e2313-251">StartDate</span></span>|<span data-ttu-id="e2313-252">Product Start Date</span><span class="sxs-lookup"><span data-stu-id="e2313-252">Product Start Date</span></span>|  
    |<span data-ttu-id="e2313-253">EndDate</span><span class="sxs-lookup"><span data-stu-id="e2313-253">EndDate</span></span>|<span data-ttu-id="e2313-254">Product End Date</span><span class="sxs-lookup"><span data-stu-id="e2313-254">Product End Date</span></span>|  
    |<span data-ttu-id="e2313-255">상태</span><span class="sxs-lookup"><span data-stu-id="e2313-255">Status</span></span>|<span data-ttu-id="e2313-256">Product Status</span><span class="sxs-lookup"><span data-stu-id="e2313-256">Product Status</span></span>|  
  
     <span data-ttu-id="e2313-257">**제품 범주**</span><span class="sxs-lookup"><span data-stu-id="e2313-257">**Product Category**</span></span>  
  
    |<span data-ttu-id="e2313-258">원본 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-258">Source Name</span></span>|<span data-ttu-id="e2313-259">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-259">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e2313-260">ProductCategoryKey</span><span class="sxs-lookup"><span data-stu-id="e2313-260">ProductCategoryKey</span></span>|<span data-ttu-id="e2313-261">Product Category Id</span><span class="sxs-lookup"><span data-stu-id="e2313-261">Product Category Id</span></span>|  
    |<span data-ttu-id="e2313-262">ProductCategoryAlternateKey</span><span class="sxs-lookup"><span data-stu-id="e2313-262">ProductCategoryAlternateKey</span></span>|<span data-ttu-id="e2313-263">Product Category Alternate Id</span><span class="sxs-lookup"><span data-stu-id="e2313-263">Product Category Alternate Id</span></span>|  
    |<span data-ttu-id="e2313-264">EnglishProductCategoryName</span><span class="sxs-lookup"><span data-stu-id="e2313-264">EnglishProductCategoryName</span></span>|<span data-ttu-id="e2313-265">Product Category 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-265">Product Category Name</span></span>|  
  
     <span data-ttu-id="e2313-266">**Product Subcategory**</span><span class="sxs-lookup"><span data-stu-id="e2313-266">**Product Subcategory**</span></span>  
  
    |<span data-ttu-id="e2313-267">원본 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-267">Source Name</span></span>|<span data-ttu-id="e2313-268">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-268">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e2313-269">ProductSubcategoryKey</span><span class="sxs-lookup"><span data-stu-id="e2313-269">ProductSubcategoryKey</span></span>|<span data-ttu-id="e2313-270">Product Subcategory Id</span><span class="sxs-lookup"><span data-stu-id="e2313-270">Product Subcategory Id</span></span>|  
    |<span data-ttu-id="e2313-271">ProductSubcategoryAlternateKey</span><span class="sxs-lookup"><span data-stu-id="e2313-271">ProductSubcategoryAlternateKey</span></span>|<span data-ttu-id="e2313-272">Product Subcategory Alternate Id</span><span class="sxs-lookup"><span data-stu-id="e2313-272">Product Subcategory Alternate Id</span></span>|  
    |<span data-ttu-id="e2313-273">EnglishProductSubcategoryName</span><span class="sxs-lookup"><span data-stu-id="e2313-273">EnglishProductSubcategoryName</span></span>|<span data-ttu-id="e2313-274">Product Subcategory Name</span><span class="sxs-lookup"><span data-stu-id="e2313-274">Product Subcategory Name</span></span>|  
    |<span data-ttu-id="e2313-275">ProductCategoryKey</span><span class="sxs-lookup"><span data-stu-id="e2313-275">ProductCategoryKey</span></span>|<span data-ttu-id="e2313-276">Product Category Id</span><span class="sxs-lookup"><span data-stu-id="e2313-276">Product Category Id</span></span>|  
  
     <span data-ttu-id="e2313-277">**Internet Sales**</span><span class="sxs-lookup"><span data-stu-id="e2313-277">**Internet Sales**</span></span>  
  
    |<span data-ttu-id="e2313-278">원본 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-278">Source Name</span></span>|<span data-ttu-id="e2313-279">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="e2313-279">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="e2313-280">ProductKey</span><span class="sxs-lookup"><span data-stu-id="e2313-280">ProductKey</span></span>|<span data-ttu-id="e2313-281">Product Id</span><span class="sxs-lookup"><span data-stu-id="e2313-281">Product Id</span></span>|  
    |<span data-ttu-id="e2313-282">CustomerKey</span><span class="sxs-lookup"><span data-stu-id="e2313-282">CustomerKey</span></span>|<span data-ttu-id="e2313-283">Customer Id</span><span class="sxs-lookup"><span data-stu-id="e2313-283">Customer Id</span></span>|  
    |<span data-ttu-id="e2313-284">PromotionKey</span><span class="sxs-lookup"><span data-stu-id="e2313-284">PromotionKey</span></span>|<span data-ttu-id="e2313-285">Promotion Id</span><span class="sxs-lookup"><span data-stu-id="e2313-285">Promotion Id</span></span>|  
    |<span data-ttu-id="e2313-286">CurrencyKey</span><span class="sxs-lookup"><span data-stu-id="e2313-286">CurrencyKey</span></span>|<span data-ttu-id="e2313-287">Currency Id</span><span class="sxs-lookup"><span data-stu-id="e2313-287">Currency Id</span></span>|  
    |<span data-ttu-id="e2313-288">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="e2313-288">SalesTerritoryKey</span></span>|<span data-ttu-id="e2313-289">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="e2313-289">Sales Territory Id</span></span>|  
    |<span data-ttu-id="e2313-290">SalesOrderNumber</span><span class="sxs-lookup"><span data-stu-id="e2313-290">SalesOrderNumber</span></span>|<span data-ttu-id="e2313-291">Sales Order Number</span><span class="sxs-lookup"><span data-stu-id="e2313-291">Sales Order Number</span></span>|  
    |<span data-ttu-id="e2313-292">SalesOrderLineNumber</span><span class="sxs-lookup"><span data-stu-id="e2313-292">SalesOrderLineNumber</span></span>|<span data-ttu-id="e2313-293">Sales Order Line Number</span><span class="sxs-lookup"><span data-stu-id="e2313-293">Sales Order Line Number</span></span>|  
    |<span data-ttu-id="e2313-294">RevisionNumber</span><span class="sxs-lookup"><span data-stu-id="e2313-294">RevisionNumber</span></span>|<span data-ttu-id="e2313-295">Revision Number</span><span class="sxs-lookup"><span data-stu-id="e2313-295">Revision Number</span></span>|  
    |<span data-ttu-id="e2313-296">OrderQuantity</span><span class="sxs-lookup"><span data-stu-id="e2313-296">OrderQuantity</span></span>|<span data-ttu-id="e2313-297">Order Quantity</span><span class="sxs-lookup"><span data-stu-id="e2313-297">Order Quantity</span></span>|  
    |<span data-ttu-id="e2313-298">UnitPrice</span><span class="sxs-lookup"><span data-stu-id="e2313-298">UnitPrice</span></span>|<span data-ttu-id="e2313-299">Unit Price</span><span class="sxs-lookup"><span data-stu-id="e2313-299">Unit Price</span></span>|  
    |<span data-ttu-id="e2313-300">ExtendedAmount</span><span class="sxs-lookup"><span data-stu-id="e2313-300">ExtendedAmount</span></span>|<span data-ttu-id="e2313-301">Extended Amount</span><span class="sxs-lookup"><span data-stu-id="e2313-301">Extended Amount</span></span>|  
    |<span data-ttu-id="e2313-302">UnitPriceDiscountPct</span><span class="sxs-lookup"><span data-stu-id="e2313-302">UnitPriceDiscountPct</span></span>|<span data-ttu-id="e2313-303">Unit Price Discount Pct</span><span class="sxs-lookup"><span data-stu-id="e2313-303">Unit Price Discount Pct</span></span>|  
    |<span data-ttu-id="e2313-304">DiscountAmount</span><span class="sxs-lookup"><span data-stu-id="e2313-304">DiscountAmount</span></span>|<span data-ttu-id="e2313-305">Discount Amount</span><span class="sxs-lookup"><span data-stu-id="e2313-305">Discount Amount</span></span>|  
    |<span data-ttu-id="e2313-306">ProductStandardCost</span><span class="sxs-lookup"><span data-stu-id="e2313-306">ProductStandardCost</span></span>|<span data-ttu-id="e2313-307">Product Standard Cost</span><span class="sxs-lookup"><span data-stu-id="e2313-307">Product Standard Cost</span></span>|  
    |<span data-ttu-id="e2313-308">TotalProductCost</span><span class="sxs-lookup"><span data-stu-id="e2313-308">TotalProductCost</span></span>|<span data-ttu-id="e2313-309">Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="e2313-309">Total Product Cost</span></span>|  
    |<span data-ttu-id="e2313-310">SalesAmount</span><span class="sxs-lookup"><span data-stu-id="e2313-310">SalesAmount</span></span>|<span data-ttu-id="e2313-311">Sales Amount</span><span class="sxs-lookup"><span data-stu-id="e2313-311">Sales Amount</span></span>|  
    |<span data-ttu-id="e2313-312">TaxAmt</span><span class="sxs-lookup"><span data-stu-id="e2313-312">TaxAmt</span></span>|<span data-ttu-id="e2313-313">Tax Amt</span><span class="sxs-lookup"><span data-stu-id="e2313-313">Tax Amt</span></span>|  
    |<span data-ttu-id="e2313-314">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="e2313-314">CarrierTrackingNumber</span></span>|<span data-ttu-id="e2313-315">Carrier Tracking Number</span><span class="sxs-lookup"><span data-stu-id="e2313-315">Carrier Tracking Number</span></span>|  
    |<span data-ttu-id="e2313-316">CustomerPONumber</span><span class="sxs-lookup"><span data-stu-id="e2313-316">CustomerPONumber</span></span>|<span data-ttu-id="e2313-317">Customer PO Number</span><span class="sxs-lookup"><span data-stu-id="e2313-317">Customer PO Number</span></span>|  
    |<span data-ttu-id="e2313-318">OrderDate</span><span class="sxs-lookup"><span data-stu-id="e2313-318">OrderDate</span></span>|<span data-ttu-id="e2313-319">Order Date</span><span class="sxs-lookup"><span data-stu-id="e2313-319">Order Date</span></span>|  
    |<span data-ttu-id="e2313-320">DueDate</span><span class="sxs-lookup"><span data-stu-id="e2313-320">DueDate</span></span>|<span data-ttu-id="e2313-321">Due Date</span><span class="sxs-lookup"><span data-stu-id="e2313-321">Due Date</span></span>|  
    |<span data-ttu-id="e2313-322">ShipDate</span><span class="sxs-lookup"><span data-stu-id="e2313-322">ShipDate</span></span>|<span data-ttu-id="e2313-323">Ship Date</span><span class="sxs-lookup"><span data-stu-id="e2313-323">Ship Date</span></span>|  
  
## <a name="next-step"></a><span data-ttu-id="e2313-324">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e2313-324">Next Step</span></span>  
 <span data-ttu-id="e2313-325">이 자습서를 계속하려면 다음 단원인 [4단원: 날짜 테이블로 표시](lesson-3-mark-as-date-table.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="e2313-325">To continue this tutorial, go to the next lesson: [Lesson 4: Mark as Date Table](lesson-3-mark-as-date-table.md).</span></span>  
  
  
