---
title: 식을 사용 하 여 설정할 수 있는 데이터 흐름 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, property expressions
- Integration Services packages, property expressions
- packages [Integration Services], properties
- SSIS packages, property expressions
- property expressions [Integration Services]
ms.assetid: cd0e171a-08be-45d6-81dc-ed94f37698b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1763a531b1d91a60d2bb3775ae9fbe9942c6b7e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729680"
---
# <a name="data-flow-properties-that-can-be-set-by-using-expressions"></a><span data-ttu-id="825d3-102">식을 사용하여 설정할 수 있는 데이터 흐름 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-102">Data Flow Properties that Can Be Set by Using Expressions</span></span>
  <span data-ttu-id="825d3-103">데이터 흐름 태스크 컨테이너에서 사용할 수 있는 속성 식을 사용하여 데이터 흐름 개체의 특정 속성 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-103">The values of certain properties of data flow objects can be specified by using property expressions available on the Data Flow task container.</span></span>  
  
 <span data-ttu-id="825d3-104">속성 식을 사용하는 방법은 [패키지에서 속성 식 사용](expressions/use-property-expressions-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="825d3-104">For information about using property expressions, see [Use Property Expressions in Packages](expressions/use-property-expressions-in-packages.md).</span></span>  
  
 <span data-ttu-id="825d3-105">속성 식을 사용하여 배포된 패키지의 각 인스턴스 구성을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-105">You can use property expressions to customize configurations for each deployed instance of a package.</span></span> <span data-ttu-id="825d3-106">또한 속성 식을 사용하여 **dtexec** 명령 프롬프트 유틸리티로 **/set** 옵션을 사용해 패키지의 런타임 제약 조건을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-106">You can also use property expressions to specify run-time constraints for a package by using the **/set** option with the **dtexec** command prompt utility.</span></span> <span data-ttu-id="825d3-107">예를 들어 정렬 변환에 사용된 `MaximumThreads` 또는 유사 항목 그룹화 및 유사 항목 조회 변환의 `MaxMemoryUsage`를 제약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-107">For example, you can constrain the `MaximumThreads` used by the Sort transformation, or the `MaxMemoryUsage` of the Fuzzy Grouping and Fuzzy Lookup transformations.</span></span> <span data-ttu-id="825d3-108">제약 받지 않을 경우 이러한 변환은 메모리에 대량의 데이터를 캐시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-108">If unconstrained, these transformations may cache large amounts of data in memory.</span></span>  
  
 <span data-ttu-id="825d3-109">이 항목에 나열된 데이터 흐름 개체의 속성 중 하나에 대한 속성 식을 지정하려면 디자이너의 **제어 흐름** 화면에서 데이터 흐름 태스크를 선택하거나 개별 구성 요소나 경로를 선택하지 않고 디자이너의 **데이터 흐름** 탭을 선택하여 데이터 흐름 태스크에 대한 **속성** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-109">To specify a property expression for one of the properties of data flow objects listed in this topic, display the **Properties** window for the Data Flow task by selecting the Data Flow task on the **Control Flow** surface of the designer, or by selecting the **Data Flow** tab of the designer without selecting any individual component or path.</span></span> <span data-ttu-id="825d3-110">**식** 속성을 선택하고 줄임표(...)를 클릭하여 **속성 식 편집기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-110">Select the **Expressions** property and click the ellipsis (...) to display the **Property Expressions Editor** dialog box.</span></span> <span data-ttu-id="825d3-111">**속성** 목록을 드롭다운하여 속성을 선택한 다음 **식** 입력란에 식을 입력하거나 줄임표(...)를 클릭하여 **식 작성기** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-111">Drop down the **Property** list to select a property, then type an expression in the **Expression** text box, or click the ellipsis (...) to display the **Expression Builder** dialog box.</span></span>  
  
 <span data-ttu-id="825d3-112">**속성** 목록에는 디자이너의 **데이터 흐름** 화면에 이미 배치한 이러한 데이터 흐름 개체에 사용할 수 있는 속성만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-112">The **Property** list displays available properties for only those data flow objects that you have already placed on the **Data Flow** surface of the designer.</span></span> <span data-ttu-id="825d3-113">따라서 **속성** 목록을 사용하여 속성 식을 지원하는 데이터 흐름 개체의 가능한 모든 속성을 확인할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-113">Therefore, you cannot use the **Property** list to view all the possible properties of data flow objects that support property expressions.</span></span> <span data-ttu-id="825d3-114">예를 들어 ADO NET 원본을 디자이너 화면에 배치한 경우 **속성** 목록에는 속성에 대 한 항목이 포함 `[ADO NET Source].[SqlCommand]` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-114">For example, if you have placed an ADO NET source on the designer surface, the **Property** list contains an entry for the `[ADO NET Source].[SqlCommand]` property.</span></span> <span data-ttu-id="825d3-115">목록에는 데이터 흐름 태스크 자체의 수많은 속성도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-115">The list also displays many properties of the Data Flow task itself.</span></span>  
  
## <a name="properties-of-data-flow-objects-that-support-property-expressions"></a><span data-ttu-id="825d3-116">속성 식을 지원하는 데이터 흐름 개체의 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-116">Properties of Data Flow Objects That Support Property Expressions</span></span>  
 <span data-ttu-id="825d3-117">다음 목록의 속성 값은 속성 식을 사용하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="825d3-117">The values of the properties in the following list can be specified by using property expressions.</span></span>  
  
### <a name="data-flow-sources"></a><span data-ttu-id="825d3-118">데이터 흐름 원본</span><span class="sxs-lookup"><span data-stu-id="825d3-118">Data Flow Sources</span></span>  
  
|<span data-ttu-id="825d3-119">데이터 흐름 개체</span><span class="sxs-lookup"><span data-stu-id="825d3-119">Data Flow object</span></span>|<span data-ttu-id="825d3-120">속성</span><span class="sxs-lookup"><span data-stu-id="825d3-120">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="825d3-121">ADO.NET 원본</span><span class="sxs-lookup"><span data-stu-id="825d3-121">ADO NET source</span></span>|<span data-ttu-id="825d3-122">TableOrViewName 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-122">TableOrViewName property</span></span><br /><br /> <span data-ttu-id="825d3-123">SQLCommand 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-123">SqlCommand property</span></span>|  
|<span data-ttu-id="825d3-124">XML 원본</span><span class="sxs-lookup"><span data-stu-id="825d3-124">XML source</span></span>|<span data-ttu-id="825d3-125">XMLData 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-125">XMLData property</span></span><br /><br /> <span data-ttu-id="825d3-126">XMLSchemaDefinition 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-126">XMLSchemaDefinition property</span></span>|  
  
### <a name="data-flow-transformations"></a><span data-ttu-id="825d3-127">데이터 흐름 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-127">Data Flow Transformations</span></span>  
 <span data-ttu-id="825d3-128">이러한 사용자 지정 속성에 대한 자세한 내용은 [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="825d3-128">For more information about these custom properties, see [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
|<span data-ttu-id="825d3-129">데이터 흐름 개체</span><span class="sxs-lookup"><span data-stu-id="825d3-129">Data Flow object</span></span>|<span data-ttu-id="825d3-130">속성</span><span class="sxs-lookup"><span data-stu-id="825d3-130">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="825d3-131">조건부 분할 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-131">Conditional Split transformation</span></span>|<span data-ttu-id="825d3-132">FriendlyExpression 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-132">FriendlyExpression property</span></span>|  
|<span data-ttu-id="825d3-133">파생 열 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-133">Derived Column transformation</span></span>|<span data-ttu-id="825d3-134">FriendlyExpression 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-134">FriendlyExpression property</span></span>|  
|<span data-ttu-id="825d3-135">유사 항목 그룹화 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-135">Fuzzy Grouping transformation</span></span>|<span data-ttu-id="825d3-136">MaxMemoryUsage 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-136">MaxMemoryUsage property</span></span>|  
|<span data-ttu-id="825d3-137">유사 항목 조회 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-137">Fuzzy Lookup transformation</span></span>|<span data-ttu-id="825d3-138">MaxMemoryUsage 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-138">MaxMemoryUsage property</span></span>|  
|<span data-ttu-id="825d3-139">조회 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-139">Lookup transformation</span></span>|<span data-ttu-id="825d3-140">SQLCommand 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-140">SqlCommand property</span></span><br /><br /> <span data-ttu-id="825d3-141">SqlCommandParam 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-141">SqlCommandParam property</span></span>|  
|<span data-ttu-id="825d3-142">OLE DB 명령 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-142">OLE DB Command transformation</span></span>|<span data-ttu-id="825d3-143">SQLCommand 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-143">SqlCommand property</span></span>|  
|<span data-ttu-id="825d3-144">비율 샘플링 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-144">Percentage Sampling transformation</span></span>|<span data-ttu-id="825d3-145">SamplingValue 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-145">SamplingValue property</span></span>|  
|<span data-ttu-id="825d3-146">피벗 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-146">Pivot transformation</span></span>|<span data-ttu-id="825d3-147">PivotKeyValue 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-147">PivotKeyValue property</span></span>|  
|<span data-ttu-id="825d3-148">행 샘플링 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-148">Row Sampling transformation</span></span>|<span data-ttu-id="825d3-149">SamplingValue 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-149">SamplingValue property</span></span>|  
|<span data-ttu-id="825d3-150">정렬 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-150">Sort transformation</span></span>|<span data-ttu-id="825d3-151">MaximumThreads 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-151">MaximumThreads property</span></span>|  
|<span data-ttu-id="825d3-152">피벗 해제 변환</span><span class="sxs-lookup"><span data-stu-id="825d3-152">Unpivot transformation</span></span>|<span data-ttu-id="825d3-153">PivotKeyValue 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-153">PivotKeyValue property</span></span>|  
  
### <a name="data-flow-destinations"></a><span data-ttu-id="825d3-154">데이터 흐름 대상</span><span class="sxs-lookup"><span data-stu-id="825d3-154">Data Flow Destinations</span></span>  
  
|<span data-ttu-id="825d3-155">데이터 흐름 개체</span><span class="sxs-lookup"><span data-stu-id="825d3-155">Data Flow object</span></span>|<span data-ttu-id="825d3-156">속성</span><span class="sxs-lookup"><span data-stu-id="825d3-156">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="825d3-157">ADO.NET 대상</span><span class="sxs-lookup"><span data-stu-id="825d3-157">ADO NET Destination</span></span>|<span data-ttu-id="825d3-158">TableOrViewName 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-158">TableOrViewName property</span></span><br /><br /> <span data-ttu-id="825d3-159">BatchSize 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-159">BatchSize property</span></span><br /><br /> <span data-ttu-id="825d3-160">CommandTimeout 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-160">CommandTimeout property</span></span>|  
|<span data-ttu-id="825d3-161">플랫 파일 대상</span><span class="sxs-lookup"><span data-stu-id="825d3-161">Flat File destination</span></span>|<span data-ttu-id="825d3-162">Header 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-162">Header property</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="825d3-163">Compact 대상</span><span class="sxs-lookup"><span data-stu-id="825d3-163">Compact destination</span></span>|<span data-ttu-id="825d3-164">TableName 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-164">TableName property</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="825d3-165">대상</span><span class="sxs-lookup"><span data-stu-id="825d3-165">destination</span></span>|<span data-ttu-id="825d3-166">BulkInsertTableName 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-166">BulkInsertTableName property</span></span><br /><br /> <span data-ttu-id="825d3-167">BulkInsertFirstRow 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-167">BulkInsertFirstRow property</span></span><br /><br /> <span data-ttu-id="825d3-168">BulkInsertLastRow 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-168">BulkInsertLastRow property</span></span><br /><br /> <span data-ttu-id="825d3-169">BulkInsertOrder 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-169">BulkInsertOrder property</span></span><br /><br /> <span data-ttu-id="825d3-170">Timeout 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-170">Timeout property</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="825d3-171">관련 작업</span><span class="sxs-lookup"><span data-stu-id="825d3-171">Related Tasks</span></span>  
  
-   [<span data-ttu-id="825d3-172">속성 식 추가 또는 변경</span><span class="sxs-lookup"><span data-stu-id="825d3-172">Add or Change a Property Expression</span></span>](expressions/add-or-change-a-property-expression.md)  
  
## <a name="related-content"></a><span data-ttu-id="825d3-173">관련 내용</span><span class="sxs-lookup"><span data-stu-id="825d3-173">Related Content</span></span>  
 <span data-ttu-id="825d3-174">pragmaticworks.com의 기술 문서 - [SSIS 식 치트 시트](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)</span><span class="sxs-lookup"><span data-stu-id="825d3-174">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825d3-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="825d3-175">See Also</span></span>  
 <span data-ttu-id="825d3-176">[패키지에서 속성 식 사용](expressions/use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="825d3-176">[Use Property Expressions in Packages](expressions/use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="825d3-177">[공용 속성](../../2014/integration-services/common-properties.md) </span><span class="sxs-lookup"><span data-stu-id="825d3-177">[Common Properties](../../2014/integration-services/common-properties.md) </span></span>  
 <span data-ttu-id="825d3-178">[변환 사용자 지정 속성](data-flow/transformations/transformation-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="825d3-178">[Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md) </span></span>  
 [<span data-ttu-id="825d3-179">경로 속성</span><span class="sxs-lookup"><span data-stu-id="825d3-179">Path Properties</span></span>](../../2014/integration-services/path-properties.md)  
  
  
