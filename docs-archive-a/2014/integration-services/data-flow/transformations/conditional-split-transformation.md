---
title: 조건부 분할 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittrans.f1
helpviewer_keywords:
- Conditional Split transformation
- route rows to different outputs [Integration Services]
ms.assetid: 3f8b5825-226f-413c-ba8f-0bb931ca3770
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 96ff4b177992c329908ebc93df8f6220168e634d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652239"
---
# <a name="conditional-split-transformation"></a><span data-ttu-id="1f28a-102">조건부 분할 변환</span><span class="sxs-lookup"><span data-stu-id="1f28a-102">Conditional Split Transformation</span></span>
  <span data-ttu-id="1f28a-103">조건부 분할 변환은 데이터 내용에 따라 각 데이터 행을 서로 다른 출력으로 라우팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-103">The Conditional Split transformation can route data rows to different outputs depending on the content of the data.</span></span> <span data-ttu-id="1f28a-104">조건부 분할 변환의 구현은 프로그래밍 언어의 CASE 결정 구조체와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-104">The implementation of the Conditional Split transformation is similar to a CASE decision structure in a programming language.</span></span> <span data-ttu-id="1f28a-105">이 변환은 식을 평가한 후 평가 결과를 기준으로 데이터 행을 지정된 출력으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-105">The transformation evaluates expressions, and based on the results, directs the data row to the specified output.</span></span> <span data-ttu-id="1f28a-106">이 변환은 기본 출력도 제공하므로, 행과 일치하는 식이 없을 경우 기본 출력으로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-106">This transformation also provides a default output, so that if a row matches no expression it is directed to the default output.</span></span>  
  
## <a name="configuration-of-the-conditional-split-transformation"></a><span data-ttu-id="1f28a-107">조건부 분할 변환 구성</span><span class="sxs-lookup"><span data-stu-id="1f28a-107">Configuration of the Conditional Split Transformation</span></span>  
 <span data-ttu-id="1f28a-108">다음과 같은 방법으로 조건부 분할 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-108">You can configure the Conditional Split transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="1f28a-109">변환에서 테스트할 각 조건에 대해 부울로 평가되는 식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-109">Provide an expression that evaluates to a Boolean for each condition you want the transformation to test.</span></span>  
  
-   <span data-ttu-id="1f28a-110">조건 평가 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-110">Specify the order in which the conditions are evaluated.</span></span> <span data-ttu-id="1f28a-111">True가 되는 첫 번째 조건에 따라 행을 출력으로 보내기 때문에 순서가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-111">Order is significant, because a row is sent to the output corresponding to the first condition that evaluates to true.</span></span>  
  
-   <span data-ttu-id="1f28a-112">변환에 기본 출력을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-112">Specify the default output for the transformation.</span></span> <span data-ttu-id="1f28a-113">이 변환은 기본 출력을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-113">The transformation requires that a default output be specified.</span></span>  
  
 <span data-ttu-id="1f28a-114">각 입력 행은 true가 되는 첫 번째 조건의 출력 한 개로만 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-114">Each input row can be sent to only one output, that being the output for the first condition that evaluates to true.</span></span> <span data-ttu-id="1f28a-115">예를 들어 다음 조건은 **A** 문자로 시작하는 *FirstName* 열의 모든 행을 특정 출력으로 보내고 *B* 문자로 시작하는 행을 다른 출력으로 보내고 다른 모든 행을 기본 출력으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-115">For example, the following conditions direct any rows in the **FirstName** column that begin with the letter *A* to one output, rows that begin with the letter *B* to a different output, and all other rows to the default output.</span></span>  
  
 <span data-ttu-id="1f28a-116">출력 1</span><span class="sxs-lookup"><span data-stu-id="1f28a-116">Output 1</span></span>  
  
 `SUBSTRING(FirstName,1,1) == "A"`  
  
 <span data-ttu-id="1f28a-117">출력 2</span><span class="sxs-lookup"><span data-stu-id="1f28a-117">Output 2</span></span>  
  
 `SUBSTRING(FirstName,1,1) == "B"`  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="1f28a-118">에는 입력 데이터를 평가하고 출력 데이터를 전달하는 식을 만들 때 사용할 수 있는 함수와 연산자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-118">includes functions and operators that you can use to create the expressions that evaluate input data and direct output data.</span></span> <span data-ttu-id="1f28a-119">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../../expressions/integration-services-ssis-expressions.md)가 될 때까지 워크플로를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-119">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="1f28a-120">조건부 분할 변환은 `FriendlyExpression` 사용자 지정 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-120">The Conditional Split transformation includes the `FriendlyExpression` custom property.</span></span> <span data-ttu-id="1f28a-121">이 속성은 패키지가 로드되면 속성 식을 사용하여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-121">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="1f28a-122">자세한 내용은 [패키지에서 속성 식 사용](../../expressions/use-property-expressions-in-packages.md) 및 [변환 사용자 지정 속성](transformation-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1f28a-122">For more information, see [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md) and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="1f28a-123">이 변환에는 하나의 입력, 여러 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-123">This transformation has one input, one or more outputs, and one error output.</span></span>  
  
 <span data-ttu-id="1f28a-124">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="1f28a-125">**조건부 분할 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Conditional Split Transformation Editor](../../conditional-split-transformation-editor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1f28a-125">For more information about the properties that you can set in the **Conditional Split Transformation Editor** dialog box, see [Conditional Split Transformation Editor](../../conditional-split-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="1f28a-126">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f28a-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="1f28a-127">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="1f28a-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="1f28a-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="1f28a-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="1f28a-129">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="1f28a-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="1f28a-130">속성 설정 방법을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="1f28a-130">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="1f28a-131">조건부 분할 변환을 사용하여 데이터 세트 분할</span><span class="sxs-lookup"><span data-stu-id="1f28a-131">Split a Dataset by Using the Conditional Split Transformation</span></span>](conditional-split-transformation.md)  
  
-   [<span data-ttu-id="1f28a-132">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="1f28a-132">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="1f28a-133">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1f28a-133">Related Tasks</span></span>  
 [<span data-ttu-id="1f28a-134">조건부 분할 변환을 사용하여 데이터 세트 분할</span><span class="sxs-lookup"><span data-stu-id="1f28a-134">Split a Dataset by Using the Conditional Split Transformation</span></span>](conditional-split-transformation.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f28a-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f28a-135">See Also</span></span>  
 <span data-ttu-id="1f28a-136">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="1f28a-136">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="1f28a-137">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="1f28a-137">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
