---
title: 정렬 변환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sorttrans.f1
helpviewer_keywords:
- Sort transformation
- descending sorts
- ascending sorts
- sorting data [Integration Services]
- multiple sorts
- duplicate data [Integration Services]
ms.assetid: 728c9351-84a8-4a89-be4d-d50d4adc04e0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7039d02b6cc55355c3b27e5694474df4666570ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652229"
---
# <a name="sort-transformation"></a><span data-ttu-id="75617-102">정렬 변환</span><span class="sxs-lookup"><span data-stu-id="75617-102">Sort Transformation</span></span>
  <span data-ttu-id="75617-103">정렬 변환은 입력 데이터를 오름차순이나 내림차순으로 정렬하고 정렬된 데이터를 변환 출력에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="75617-103">The Sort transformation sorts input data in ascending or descending order and copies the sorted data to the transformation output.</span></span> <span data-ttu-id="75617-104">입력에 여러 가지 정렬을 적용할 수 있으며 각 정렬은 정렬 순서를 결정하는 숫자로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="75617-104">You can apply multiple sorts to an input; each sort is identified by a numeral that determines the sort order.</span></span> <span data-ttu-id="75617-105">숫자가 가장 적은 열이 맨 먼저 정렬되고 그 다음 숫자의 정렬 열이 다음에 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="75617-105">The column with the lowest number is sorted first, the sort column with the second lowest number is sorted next, and so on.</span></span> <span data-ttu-id="75617-106">예를 들어 **CountryRegion** 열이 정렬 순서 1이고 **City** 열이 정렬 순서 2인 경우 출력은 먼저 국가/지역별로 정렬된 다음 도시별로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="75617-106">For example, if a column named **CountryRegion** has a sort order of 1 and a column named **City** has a sort order of 2, the output is sorted by country/region and then by city.</span></span> <span data-ttu-id="75617-107">양수는 오름차순 정렬을 나타내고 음수는 내림차순 정렬을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="75617-107">A positive number denotes that the sort is ascending, and a negative number denotes that the sort is descending.</span></span> <span data-ttu-id="75617-108">정렬되지 않은 열의 정렬 순서는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="75617-108">Columns that are not sorted have a sort order of 0.</span></span> <span data-ttu-id="75617-109">정렬이 선택되지 않은 열은 정렬된 열과 함께 자동으로 변환 출력에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="75617-109">Columns that are not selected for sorting are automatically copied to the transformation output together with the sorted columns.</span></span>  
  
 <span data-ttu-id="75617-110">정렬 변환에는 변환에서 열의 문자열 데이터를 처리하는 방법을 정의하는 비교 옵션 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75617-110">The Sort transformation includes a set of comparison options to define how the transformation handles the string data in a column.</span></span> <span data-ttu-id="75617-111">자세한 내용은 [Comparing String Data](../comparing-string-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75617-111">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75617-112">정렬 변환은 Transact-SQL에서 ORDER BY 절이 수행하는 것과 동일한 순서로 GUID를 정렬하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75617-112">The Sort transformation does not sort GUIDs in the same order as the ORDER BY clause does in Transact-SQL.</span></span> <span data-ttu-id="75617-113">정렬 변환은 0-9로 시작하는 GUID를 A-F로 시작하는 GUID보다 먼저 정렬하지만, [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]에 구현된 ORDER BY 절은 GUID를 다르게 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="75617-113">While the Sort transformation sorts GUIDs that start with 0-9 before GUIDs that start with A-F, the ORDER BY clause, as implemented in the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], sorts them differently.</span></span> <span data-ttu-id="75617-114">자세한 내용은 [ORDER BY 절&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75617-114">For more information, see [ORDER BY Clause &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-order-by-clause-transact-sql).</span></span>  
  
 <span data-ttu-id="75617-115">정렬 변환은 정렬 중에 중복 행을 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75617-115">The Sort transformation can also remove duplicate rows as part of its sort.</span></span> <span data-ttu-id="75617-116">중복 행은 동일한 정렬 키 값을 가진 행입니다.</span><span class="sxs-lookup"><span data-stu-id="75617-116">Duplicate rows are rows with the same sort key values.</span></span> <span data-ttu-id="75617-117">정렬 키 값은 사용된 문자열 비교 옵션을 기반으로 생성되므로 서로 다른 리터럴 문자열이 동일한 정렬 키 값을 가질 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75617-117">The sort key value is generated based on the string comparison options being used, which means that different literal strings may have the same sort key values.</span></span> <span data-ttu-id="75617-118">이 변환은 값이 다르지만 동일한 정렬 키를 가진 입력 열의 행을 중복 행으로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="75617-118">The transformation identifies rows in the input columns that have different values but the same sort key as duplicates.</span></span>  
  
 <span data-ttu-id="75617-119">정렬 변환은 패키지 로드 시 속성 식을 사용하여 업데이트할 수 있는 `MaximumThreads` 사용자 지정 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="75617-119">The Sort transformation includes the `MaximumThreads` custom property that can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="75617-120">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../../expressions/integration-services-ssis-expressions.md), [패키지에서 속성 식 사용](../../expressions/use-property-expressions-in-packages.md) 및 [변환 사용자 지정 속성](transformation-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75617-120">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="75617-121">이 변환은 하나의 입력과 하나의 출력을 가지며</span><span class="sxs-lookup"><span data-stu-id="75617-121">This transformation has one input and one output.</span></span> <span data-ttu-id="75617-122">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75617-122">It does not support error outputs.</span></span>  
  
## <a name="configuration-of-the-sort-transformation"></a><span data-ttu-id="75617-123">정렬 변환 구성</span><span class="sxs-lookup"><span data-stu-id="75617-123">Configuration of the Sort Transformation</span></span>  
 <span data-ttu-id="75617-124">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75617-124">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="75617-125">**정렬 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Sort Transformation Editor](../../sort-transformation-editor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="75617-125">For information about the properties that you can set in the **Sort Transformation Editor** dialog box, see [Sort Transformation Editor](../../sort-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="75617-126">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="75617-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="75617-127">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="75617-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="75617-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="75617-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="75617-129">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="75617-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="75617-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="75617-130">Related Tasks</span></span>  
 <span data-ttu-id="75617-131">구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75617-131">For more information about how to set properties of the component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="75617-132">관련 내용</span><span class="sxs-lookup"><span data-stu-id="75617-132">Related Content</span></span>  
 <span data-ttu-id="75617-133">codeplex.com의 예제 - [SortDeDuplicateDelimitedString 사용자 지정 SSIS 구성 요소](https://go.microsoft.com/fwlink/?LinkId=220821)</span><span class="sxs-lookup"><span data-stu-id="75617-133">Sample, [SortDeDuplicateDelimitedString Custom SSIS Component](https://go.microsoft.com/fwlink/?LinkId=220821), on codeplex.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75617-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75617-134">See Also</span></span>  
 <span data-ttu-id="75617-135">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="75617-135">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="75617-136">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="75617-136">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
