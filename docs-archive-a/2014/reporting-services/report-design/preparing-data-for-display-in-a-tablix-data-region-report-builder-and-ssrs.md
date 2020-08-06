---
title: 테이블릭스 데이터 영역에 표시하기 위한 데이터 준비(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fbb00dc6-7887-480c-b771-cab6fecb8dcc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 72ac150f2dcd227b1e3afb624a5ca5866fb4c360
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659820"
---
# <a name="preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs"></a><span data-ttu-id="f9adf-102">테이블릭스 데이터 영역에 표시하기 위한 데이터 준비(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f9adf-102">Preparing Data for Display in a Tablix Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f9adf-103">테이블릭스 데이터 영역에는 데이터 세트의 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-103">A tablix data region displays data from a dataset.</span></span> <span data-ttu-id="f9adf-104">데이터 세트에 대해 검색된 모든 데이터를 보거나 필터를 만들어 일부 데이터만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-104">You can view all the data retrieved for the dataset or you can create filters so that you see only a subset of the data.</span></span> <span data-ttu-id="f9adf-105">또한 조건 식을 추가하여 null 값을 채우거나 데이터 세트에 대한 쿼리를 수정하여 기존 열에 대한 정렬 순서를 정의하는 열을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-105">You can also add conditional expressions to fill in null values or modify the query for a dataset to include columns that define the sort order for an existing column.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="working-with-nulls-and-blanks-in-field-values"></a><span data-ttu-id="f9adf-106">Null 및 비어 있는 필드 값 작업</span><span class="sxs-lookup"><span data-stu-id="f9adf-106">Working with Nulls and Blanks in Field Values</span></span>  
 <span data-ttu-id="f9adf-107">데이터 세트에서 필드 컬렉션에 대한 데이터는 null과 빈 값을 포함하여 데이터 원본에서 런타임에 검색된 모든 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-107">Data for the field collection in a dataset includes all values retrieved from the data source at run time, including null values and blanks.</span></span> <span data-ttu-id="f9adf-108">일반적으로 Null 값과 비어 있는 값은 구분되지 않으며</span><span class="sxs-lookup"><span data-stu-id="f9adf-108">Normally null values and blanks are indistinguishable.</span></span> <span data-ttu-id="f9adf-109">대부분의 경우 이것이 정상입니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-109">In most cases, this is the desired behavior.</span></span> <span data-ttu-id="f9adf-110">예를 들어 [Sum](report-builder-functions-sum-function.md) 및 [Avg](report-builder-functions-avg-function.md) 와 같은 숫자 집계 함수는 Null 값을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-110">For example, Numeric aggregate functions like [Sum](report-builder-functions-sum-function.md) and [Avg](report-builder-functions-avg-function.md) ignore null values.</span></span> <span data-ttu-id="f9adf-111">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9adf-111">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
 <span data-ttu-id="f9adf-112">Null 값을 다르게 처리하려면 조건 식이나 사용자 지정 코드를 사용하여 Null 값에 대한 사용자 지정 값을 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-112">If you do want to handle null values differently, you can use conditional expressions or custom code to substitute a custom value for the null value.</span></span> <span data-ttu-id="f9adf-113">예를 들어 다음 식은 `Null` 필드에 Null 값이 나타날 때마다 `[Size]`이라는 텍스트로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-113">For example, the following expression substitutes the text `Null` wherever a null value occurs in the field `[Size]`.</span></span>  
  
```  
=IIF(Fields!Size.Value IS NOTHING,"Null",Fields!Size.Value)  
```  
  
 <span data-ttu-id="f9adf-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 쿼리를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 데이터 원본에서 데이터를 검색하기 전에 데이터에서 Null 값을 제거하는 방법은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server 온라인 설명서 [의](https://go.microsoft.com/fwlink/?linkid=120955)설명서에 있는 "Null 값" 및 "Null 값 및 조인"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f9adf-114">For more information about eliminating nulls in your data before retrieving the data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source using [!INCLUDE[tsql](../../includes/tsql-md.md)] queries, see "Null Values" and "Null Values and Joins" in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
## <a name="handling-null-field-names"></a><span data-ttu-id="f9adf-115">Null 필드 이름 처리</span><span class="sxs-lookup"><span data-stu-id="f9adf-115">Handling Null Field Names</span></span>  
 <span data-ttu-id="f9adf-116">식에서 Null 값을 테스트하는 것은 쿼리 결과 집합에 필드 자체가 있는 한 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-116">Testing for null values in an expression is fine as long as the field itself exists in the query result set.</span></span> <span data-ttu-id="f9adf-117">사용자 지정 코드에서는 런타임에 데이터 원본으로부터 반환된 컬렉션 필드에 Null 필드가 나타나는지 여부를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-117">From custom code, you can test whether the field itself is present in the collection fields returned from the data source at run time.</span></span> <span data-ttu-id="f9adf-118">자세한 내용은 [데이터 세트 필드 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;](built-in-collections-dataset-fields-collection-references-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9adf-118">For more information, see [Dataset Fields Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-dataset-fields-collection-references-report-builder.md).</span></span>  
  
## <a name="adding-a-sort-order-column"></a><span data-ttu-id="f9adf-119">정렬 순서 열 추가</span><span class="sxs-lookup"><span data-stu-id="f9adf-119">Adding a Sort Order Column</span></span>  
 <span data-ttu-id="f9adf-120">기본적으로 데이터 세트 필드의 값을 사전순으로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-120">By default, you can alphabetically sort values in a dataset field.</span></span> <span data-ttu-id="f9adf-121">다른 순서로 정렬하려면 데이터 세트에 데이터 영역에서의 정렬 순서를 정의하는 새 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-121">To sort in a different order, you can add a new column to your dataset that defines the sort order you want in a data region.</span></span> <span data-ttu-id="f9adf-122">예를 들어 `[Color]` 필드에 대해 정렬을 수행하고 흰색과 검정색 항목을 먼저 정렬하려면 다음 쿼리처럼 `[ColorSortOrder]`열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-122">For example, to sort on the field `[Color]` and sort white and black items first, you can add a column `[ColorSortOrder]`, shown in the following query:</span></span>  
  
```  
SELECT ProductID, p.Name, Color,  
   CASE  
      WHEN p.Color = 'White' THEN 1  
      WHEN p.Color = 'Black' THEN 2  
      WHEN p.Color = 'Blue' THEN 3  
      WHEN p.Color = 'Yellow' THEN 4  
      ELSE 5  
   END As ColorSortOrder  
FROM Production.Product p  
```  
  
 <span data-ttu-id="f9adf-123">이 정렬 순서에 따라 테이블 데이터 영역을 정렬하려면 세부 정보 그룹의 정렬 식을 `=Fields!ColorSortOrder.Value`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9adf-123">To sort a table data region according to this sort order, set the sort expression on the detail group to `=Fields!ColorSortOrder.Value`.</span></span> <span data-ttu-id="f9adf-124">자세한 내용은 [데이터 영역의 데이터 정렬&#40;보고서 작성기 및 SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9adf-124">For more information, see [Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9adf-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9adf-125">See Also</span></span>  
 <span data-ttu-id="f9adf-126">[데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f9adf-126">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f9adf-127">[식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f9adf-127">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f9adf-128">데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f9adf-128">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
