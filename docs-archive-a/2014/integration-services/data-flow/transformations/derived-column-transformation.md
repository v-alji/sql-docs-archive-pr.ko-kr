---
title: 파생 열 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntrans.f1
helpviewer_keywords:
- multiple derived columns
- expressions [Integration Services], derived columns
- derived columns
- columns [Integration Services], derivations
- Derived Column transformation
ms.assetid: 8eba755e-8e48-4233-bd1e-09a46bf2692f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bbdc46f2e67b1b859fcfa446c584373cfbeca0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646563"
---
# <a name="derived-column-transformation"></a><span data-ttu-id="c67a8-102">파생 열 변환</span><span class="sxs-lookup"><span data-stu-id="c67a8-102">Derived Column Transformation</span></span>
  <span data-ttu-id="c67a8-103">파생 열 변환은 변환 입력 열에 식을 적용하여 새로운 열 값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-103">The Derived Column transformation creates new column values by applying expressions to transformation input columns.</span></span> <span data-ttu-id="c67a8-104">변환 입력의 변수, 함수, 연산자 및 열의 모든 조합이 식에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-104">An expression can contain any combination of variables, functions, operators, and columns from the transformation input.</span></span> <span data-ttu-id="c67a8-105">결과는 새 열로 추가하거나 기존 열에 대체 값으로 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-105">The result can be added as a new column or inserted into an existing column as a replacement value.</span></span> <span data-ttu-id="c67a8-106">파생 열 변환은 여러 개의 파생 열을 정의할 수 있으며 임의의 변수 또는 입력 열이 여러 개의 식에 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-106">The Derived Column transformation can define multiple derived columns, and any variable or input columns can appear in multiple expressions.</span></span>  
  
 <span data-ttu-id="c67a8-107">이 변환을 사용하여 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-107">You can use this transformation to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="c67a8-108">여러 열의 데이터를 하나의 파생 열로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-108">Concatenate data from different columns into a derived column.</span></span> <span data-ttu-id="c67a8-109">예를 들어 식 **을 사용하여** FirstName **열과** LastName **열의 값을**FullName `FirstName + " " + LastName`이라는 단일 파생 열로 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-109">For example, you can combine values from the **FirstName** and **LastName** columns into a single derived column named **FullName**, by using the expression `FirstName + " " + LastName`.</span></span>  
  
-   <span data-ttu-id="c67a8-110">SUBSTRING과 같은 함수를 사용하여 문자열 데이터에서 문자를 추출한 다음 결과를 파생 열에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-110">Extract characters from string data by using functions such as SUBSTRING, and then store the result in a derived column.</span></span> <span data-ttu-id="c67a8-111">예를 들어 식 **을 사용하여** FirstName `SUBSTRING(FirstName,1,1)`열에서 특정인의 이니셜을 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-111">For example, you can extract a person's initial from the **FirstName** column, by using the expression `SUBSTRING(FirstName,1,1)`.</span></span>  
  
-   <span data-ttu-id="c67a8-112">숫자 데이터에 수치 연산 함수를 적용하고 계산 결과를 파생 열에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-112">Apply mathematical functions to numeric data and store the result in a derived column.</span></span> <span data-ttu-id="c67a8-113">예를 들어 식 **를 사용하여 숫자 열**SalesTax `ROUND(SalesTax, 2)`의 길이와 전체 자릿수를 소수 두 자리 수로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-113">For example, you can change the length and precision of a numeric column, **SalesTax**, to a number with two decimal places, by using the expression `ROUND(SalesTax, 2)`.</span></span>  
  
-   <span data-ttu-id="c67a8-114">입력 열과 변수를 비교하는 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-114">Create expressions that compare input columns and variables.</span></span> <span data-ttu-id="c67a8-115">예를 들어 식 **을 사용하여 변수** Version **을**ProductVersion **열의 데이터와 비교하고 비교 결과에 따라** Version **또는**ProductVersion `ProductVersion == @Version? ProductVersion : @Version`중 하나의 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-115">For example, you can compare the variable **Version** against the data in the column **ProductVersion**, and depending on the comparison result, use the value of either **Version** or **ProductVersion**, by using the expression `ProductVersion == @Version? ProductVersion : @Version`.</span></span>  
  
-   <span data-ttu-id="c67a8-116">datetime 값의 일부를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-116">Extract parts of a datetime value.</span></span> <span data-ttu-id="c67a8-117">예를 들어 식 `DATEPART("year",GETDATE())`를 사용하여 GETDATE 및 DATEPART 함수로 현재 연도를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-117">For example, you can use the GETDATE and DATEPART functions to extract the current year, by using the expression `DATEPART("year",GETDATE())`.</span></span>  
  
-   <span data-ttu-id="c67a8-118">식을 사용하여 날짜 문자열을 특정 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-118">Convert date strings to a specific format using an expression.</span></span>  
  
## <a name="configuration-of-the-derived-column-transformation"></a><span data-ttu-id="c67a8-119">파생 열 변환 구성</span><span class="sxs-lookup"><span data-stu-id="c67a8-119">Configuration of the Derived Column Transformation</span></span>  
 <span data-ttu-id="c67a8-120">다음과 같은 방법으로 파생 열 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-120">You can configure the Derived column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="c67a8-121">변경될 각 입력 열이나 새 열에 대한 식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-121">Provide an expression for each input column or new column that will be changed.</span></span> <span data-ttu-id="c67a8-122">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../../expressions/integration-services-ssis-expressions.md)가 될 때까지 워크플로를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-122">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c67a8-123">파생 열 변환에서 덮어쓰는 입력 열을 참조하는 식은 파생 값이 아닌 원래 열 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-123">If an expression references an input column that is overwritten by the Derived Column transformation, the expression uses the original value of the column, not the derived value.</span></span>  
  
-   <span data-ttu-id="c67a8-124">새 열에 결과를 추가하고 데이터 형식이 `string`인 경우 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-124">If adding results to new columns and the data type is `string`, specify a code page.</span></span> <span data-ttu-id="c67a8-125">자세한 내용은 [Comparing String Data](../comparing-string-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c67a8-125">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="c67a8-126">파생 열 변환에는 FriendlyExpression 사용자 지정 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-126">The Derived Column transformation includes the FriendlyExpression custom property.</span></span> <span data-ttu-id="c67a8-127">이 속성은 패키지가 로드되면 속성 식을 사용하여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-127">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="c67a8-128">자세한 내용은 [패키지에서 속성 식 사용](../../expressions/use-property-expressions-in-packages.md)및 [변환 사용자 지정 속성](transformation-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c67a8-128">For more information, see [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="c67a8-129">이 변환에는 하나의 입력, 하나의 일반 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-129">This transformation has one input, one regular output, and one error output.</span></span>  
  
 <span data-ttu-id="c67a8-130">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-130">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c67a8-131">**파생 열 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Derived Column Transformation Editor](../../derived-column-transformation-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c67a8-131">For more information about the properties that you can set in the **Derived Column Transformation Editor** dialog box, see [Derived Column Transformation Editor](../../derived-column-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="c67a8-132">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c67a8-132">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="c67a8-133">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="c67a8-133">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c67a8-134">Common Properties</span><span class="sxs-lookup"><span data-stu-id="c67a8-134">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="c67a8-135">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="c67a8-135">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="c67a8-136">속성 설정 방법을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="c67a8-136">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c67a8-137">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="c67a8-137">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="c67a8-138">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c67a8-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="c67a8-139">파생 열 변환을 사용하여 열 값 파생</span><span class="sxs-lookup"><span data-stu-id="c67a8-139">Derive Column Values by Using the Derived Column Transformation</span></span>](derived-column-transformation.md)  
  
## <a name="related-content"></a><span data-ttu-id="c67a8-140">관련 내용</span><span class="sxs-lookup"><span data-stu-id="c67a8-140">Related Content</span></span>  
 <span data-ttu-id="c67a8-141">social.technet.microsoft.com의 기술 문서 - [SSIS 식 예](https://go.microsoft.com/fwlink/?LinkId=220761)</span><span class="sxs-lookup"><span data-stu-id="c67a8-141">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>  
  
 <span data-ttu-id="c67a8-142">블로그, [SSIS를 사용 하 여 열 데이터를 분할 하는 방법](https://microsoft-ssis.blogspot.com/2012/10/split-multi-value-column-into-multiple.html)</span><span class="sxs-lookup"><span data-stu-id="c67a8-142">Blog, [How to Split Column Data using SSIS](https://microsoft-ssis.blogspot.com/2012/10/split-multi-value-column-into-multiple.html).</span></span>  
  
  
