---
title: For 루프 컨테이너 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainerdetails.f1
helpviewer_keywords:
- repeating control flow
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: 44cf7355-992b-4bbf-a28c-bfb012de06f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a6c864779237fdbf4dd249f87b7c06655293c047
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638955"
---
# <a name="for-loop-container"></a><span data-ttu-id="4fdfa-102">For 루프 컨테이너</span><span class="sxs-lookup"><span data-stu-id="4fdfa-102">For Loop Container</span></span>
  <span data-ttu-id="4fdfa-103">For 루프 컨테이너는 패키지의 반복 제어 흐름을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-103">The For Loop container defines a repeating control flow in a package.</span></span> <span data-ttu-id="4fdfa-104">루프 구현은 프로그래밍 언어에서의 **For** 루프 구조와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-104">The loop implementation is similar to the **For** looping structure in programming languages.</span></span> <span data-ttu-id="4fdfa-105">For 루프 컨테이너는 각 루프를 반복할 때마다 식을 계산하고 식이 `False`가 될 때까지 워크플로를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-105">In each repeat of the loop, the For Loop container evaluates an expression and repeats its workflow until the expression evaluates to `False`.</span></span>  
  
 <span data-ttu-id="4fdfa-106">For 루프 컨테이너는 다음 요소를 사용하여 루프를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-106">The For Loop container usesthe following elements to define the loop:</span></span>  
  
-   <span data-ttu-id="4fdfa-107">루프 카운터에 값을 할당하는 초기화 식(옵션)</span><span class="sxs-lookup"><span data-stu-id="4fdfa-107">An optional initialization expression that assigns values to the loop counters.</span></span>  
  
-   <span data-ttu-id="4fdfa-108">루프를 중지 또는 계속할지를 테스트하는 식이 포함된 계산 식</span><span class="sxs-lookup"><span data-stu-id="4fdfa-108">An evaluation expression that contains the expression used to test whether the loop should stop or continue.</span></span>  
  
-   <span data-ttu-id="4fdfa-109">루프 카운터를 증가 또는 감소시키는 반복 식(옵션)</span><span class="sxs-lookup"><span data-stu-id="4fdfa-109">An optional iteration expression that increments or decrements the loop counter.</span></span>  
  
 <span data-ttu-id="4fdfa-110">다음 다이어그램에서는 메일 보내기 태스크를 사용한 For 루프 컨테이너를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-110">The following diagram shows a For Loop container with a Send Mail task.</span></span> <span data-ttu-id="4fdfa-111">초기화 식이 `@Counter = 0`이고 계산 식이 `@Counter < 4`이고 반복 식이 `@Counter = @Counter + 1`이면 루프가 4번 반복되어 4개의 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-111">If the initialization expression is `@Counter = 0`, the evaluation expression is `@Counter < 4`, and the iteration expression is `@Counter = @Counter + 1`, the loop repeats four times and sends four e-mail messages.</span></span>  
  
 <span data-ttu-id="4fdfa-112">![한 태스크를 4번 반복하는 For 루프 컨테이너](../media/ssis-forloop.gif "한 태스크를 4번 반복하는 For 루프 컨테이너")</span><span class="sxs-lookup"><span data-stu-id="4fdfa-112">![A For Loop container repeats a task four times](../media/ssis-forloop.gif "A For Loop container repeats a task four times")</span></span>  
  
 <span data-ttu-id="4fdfa-113">식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]의 유효한 식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-113">The expressions must be valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions.</span></span>  
  
 <span data-ttu-id="4fdfa-114">초기화 식과 대입 식을 만들려면 대입 연산자(=)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-114">To create the initialization and assignment expressions, you can use the assignment operator (=).</span></span> <span data-ttu-id="4fdfa-115">이 연산자는 Integration Services 식 문법에서 다른 용도로 지원되지 않으며 For 루프 컨테이너의 초기화 및 대입 식 유형에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-115">This operator is not otherwise supported by the Integration Services expression grammar and can only be used by the initialization and assignment expression types in the For Loop container.</span></span> <span data-ttu-id="4fdfa-116">대입 연산자를 사용하는 식의 구문은 `@Var = <expression>`이어야 합니다. 여기서 **Var**은 런타임 변수이고 \<expression>은 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 식 구문의 규칙을 따르는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-116">Any expression that uses the assignment operator must have the syntax `@Var = <expression>`, where **Var** is a run-time variable and \<expression> is an expression that follows the rules of the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] expression syntax.</span></span> <span data-ttu-id="4fdfa-117">식은 변수, 리터럴 및 SSIS 식 문법에서 지원하는 모든 연산자와 함수를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-117">The expression can include the variables, literals, and any operators and functions that the SSIS expression grammar supports.</span></span> <span data-ttu-id="4fdfa-118">변수의 데이터 형식으로 캐스팅할 수 있는 데이터 형식으로 식이 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-118">The expression must evaluate to a data type that can be cast to the data type of the variable.</span></span>  
  
 <span data-ttu-id="4fdfa-119">For 루프 컨테이너는 하나의 계산 식만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-119">A For Loop container can have only one evaluation expression.</span></span> <span data-ttu-id="4fdfa-120">따라서 For 루프 컨테이너는 모든 제어 흐름 요소를 동일한 횟수만큼 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-120">This means that the For Loop container runs all its control flow elements the same number of times.</span></span> <span data-ttu-id="4fdfa-121">For 루프 컨테이너에 다른 For 루프 컨테이너가 포함될 수 있으므로 중첩 루프를 만들고 패키지에 복잡한 루프를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-121">Because the For Loop container can include other For Loop containers, you can build nested loops and implement complex looping in packages.</span></span>  
  
 <span data-ttu-id="4fdfa-122">For 루프 컨테이너의 트랜잭션 속성을 설정하여 패키지 제어 흐름의 하위 집합에 대해 트랜잭션을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-122">You can set a transaction property on the For Loop container to define a transaction for a subset of the package control flow.</span></span> <span data-ttu-id="4fdfa-123">이러한 방식으로 보다 세부적으로 트랜잭션을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-123">In this way, you can manage transactions at a more granular level.</span></span> <span data-ttu-id="4fdfa-124">예를 들어 For 루프 컨테이너가 테이블의 데이터를 업데이트하는 제어 흐름을 여러 번 반복하는 경우 For 루프와 해당 제어 흐름에서 트랜잭션을 사용하여 모든 데이터가 성공적으로 업데이트되지 않으면 데이터가 업데이트되지 않도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-124">For example, if a For Loop container repeats a control flow that updates data in a table multiple times, you can configure the For Loop and its control flow to use a transaction to ensure that if not all data is updated successfully, no data is updated.</span></span> <span data-ttu-id="4fdfa-125">자세한 내용은 [Integration Services 트랜잭션](../integration-services-transactions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-125">For more information, see [Integration Services Transactions](../integration-services-transactions.md).</span></span>  
  
## <a name="configuration-of-the-for-loop-container"></a><span data-ttu-id="4fdfa-126">For 루프 컨테이너 구성</span><span class="sxs-lookup"><span data-stu-id="4fdfa-126">Configuration of the For Loop Container</span></span>  
 <span data-ttu-id="4fdfa-127">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-127">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="4fdfa-128">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-128">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4fdfa-129">For 루프 편집기</span><span class="sxs-lookup"><span data-stu-id="4fdfa-129">For Loop Editor</span></span>](../for-loop-editor.md)  
  
-   [<span data-ttu-id="4fdfa-130">식 페이지</span><span class="sxs-lookup"><span data-stu-id="4fdfa-130">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="4fdfa-131">프로그래밍 방식으로 이러한 속성을 설정하는 방법은 개발자 가이드에서 **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** 클래스에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-131">For more information about programmatically setting these properties, see documentation for the **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** class in the Developer Guide.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="4fdfa-132">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4fdfa-132">Related Tasks</span></span>  
 <span data-ttu-id="4fdfa-133">For 루프 컨테이너를 구성하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4fdfa-133">For information about how to configure a For Loop Container, see the following topics.</span></span>  
  
-   [<span data-ttu-id="4fdfa-134">For 루프 컨테이너 구성</span><span class="sxs-lookup"><span data-stu-id="4fdfa-134">Configure a For Loop Container</span></span>](for-loop-container.md)  
  
-   [<span data-ttu-id="4fdfa-135">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="4fdfa-135">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="4fdfa-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4fdfa-136">See Also</span></span>  
 <span data-ttu-id="4fdfa-137">[제어 흐름](control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="4fdfa-137">[Control Flow](control-flow.md) </span></span>  
 [<span data-ttu-id="4fdfa-138">Integration Services&#40;SSIS&#41; 식</span><span class="sxs-lookup"><span data-stu-id="4fdfa-138">Integration Services &#40;SSIS&#41; Expressions</span></span>](../expressions/integration-services-ssis-expressions.md)  
  
  
