---
title: 필터 수식 예(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- filtering data [Reporting Services], filter equation examples
ms.assetid: 66bec93d-7c3b-4d4a-8cb6-7a7bb2f34ec6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9b4d7c7c561c9185c141190e26f37bc29fe52eb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649388"
---
# <a name="filter-equation-examples-report-builder-and-ssrs"></a><span data-ttu-id="acc55-102">필터 수식 예(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="acc55-102">Filter Equation Examples (Report Builder and SSRS)</span></span>
  <span data-ttu-id="acc55-103">필터를 만들려면 하나 이상의 필터 수식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-103">To create a filter, you must specify one or more filter equations.</span></span> <span data-ttu-id="acc55-104">필터 수식에는 식, 데이터 형식, 연산자 및 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-104">A filter equation includes an expression, a data type, an operator, and a value.</span></span> <span data-ttu-id="acc55-105">이 항목에서는 일반적으로 사용되는 필터의 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-105">This topic provides examples of commonly used filters.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a><span data-ttu-id="acc55-106">필터 예</span><span class="sxs-lookup"><span data-stu-id="acc55-106">Filter Examples</span></span>  
 <span data-ttu-id="acc55-107">다음 표에서는 다양한 데이터 형식 및 연산자를 사용하는 필터 수식의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-107">The following table shows examples of filter equations that use different data types and different operators.</span></span> <span data-ttu-id="acc55-108">비교 범위는 필터가 정의된 보고서 항목에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-108">The scope for the comparison is determined by report item for which a filter is defined.</span></span> <span data-ttu-id="acc55-109">예를 들어 데이터 세트에 대해 정의된 필터의 경우 **TOP % 10**은 데이터 세트의 상위 10% 값이며 그룹에 대해 정의된 필터의 경우 **TOP % 10**은 그룹의 상위 10% 값입니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-109">For example, for a filter defined on a dataset, **TOP % 10** is the top 10 percent of values in the dataset; for a filter defined on a group, **TOP % 10** is the top 10 percent of values in the group.</span></span>  
  
|<span data-ttu-id="acc55-110">간단한 식</span><span class="sxs-lookup"><span data-stu-id="acc55-110">Simple Expression</span></span>|<span data-ttu-id="acc55-111">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="acc55-111">Data Type</span></span>|<span data-ttu-id="acc55-112">연산자</span><span class="sxs-lookup"><span data-stu-id="acc55-112">Operator</span></span>|<span data-ttu-id="acc55-113">값</span><span class="sxs-lookup"><span data-stu-id="acc55-113">Value</span></span>|<span data-ttu-id="acc55-114">Description</span><span class="sxs-lookup"><span data-stu-id="acc55-114">Description</span></span>|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|`Integer`|`>`|`7`|<span data-ttu-id="acc55-115">7보다 큰 데이터 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-115">Includes data values that are greater than 7.</span></span>|  
|`[SUM(Quantity)]`|`Integer`|`TOP N`|`10`|<span data-ttu-id="acc55-116">상위 10개 데이터 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-116">Includes the top 10 data values.</span></span>|  
|`[SUM(Quantity)]`|`Integer`|`TOP %`|`20`|<span data-ttu-id="acc55-117">데이터 값의 상위 20%를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-117">Includes the top 20% of data values.</span></span>|  
|`[Sales]`|`Text`|`>`|`=CDec(100)`|<span data-ttu-id="acc55-118">$100보다 큰 System.Decimal 형식(SQL "money" 데이터 형식)의 모든 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-118">Includes all values of type System.Decimal (SQL "money" data types) greater than $100.</span></span>|  
|`[OrderDate]`|`DateTime`|`>`|`2008-01-01`|<span data-ttu-id="acc55-119">2008년 1월 1일부터 현재 날짜까지의 모든 날짜를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-119">Includes all dates from January 1, 2008 to the present date.</span></span>|  
|`[OrderDate]`|`DateTime`|`BETWEEN`|`2008-01-01`<br /><br /> `2008-02-01`|<span data-ttu-id="acc55-120">2008년 1월 1일부터 2008년 2월 1일까지의 날짜를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-120">Includes dates from January 1, 2008 up to and including February 1, 2008.</span></span>|  
|`[Territory]`|`Text`|`LIKE`|`*east`|<span data-ttu-id="acc55-121">"east"로 끝나는 모든 지역 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-121">All territory names that end in "east".</span></span>|  
|`[Territory]`|`Text`|`LIKE`|`%o%th*`|<span data-ttu-id="acc55-122">이름의 시작 부분에 North와 South를 포함하는 모든 지역 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-122">All territory names that include North and South at the beginning of the name.</span></span>|  
|`=LEFT(Fields!Subcat.Value,1)`|`Text`|`IN`|`B, C, T`|<span data-ttu-id="acc55-123">B, C 또는 T 문자로 시작하는 모든 하위 범주 값입니다.</span><span class="sxs-lookup"><span data-stu-id="acc55-123">All subcategory values that begin with the letters B, C, or T.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="acc55-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="acc55-124">See Also</span></span>  
 <span data-ttu-id="acc55-125">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="acc55-125">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="acc55-126">[데이터 집합 필터, 데이터 영역 필터 및 그룹 필터를 추가 하 여 보고서 작성기 및 SSRS &#40;&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="acc55-126">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="acc55-127">[식의 데이터 형식 &#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="acc55-127">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="acc55-128">[보고서 &#40;보고서 작성기 및 SSRS에서 사용 하는 식&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="acc55-128">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="acc55-129">식 예&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="acc55-129">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
