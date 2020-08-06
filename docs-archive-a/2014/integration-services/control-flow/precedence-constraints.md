---
title: 선행 제약 조건 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- control flow [Integration Services], precedence constraints
- precedence constraints [Integration Services]
- constraints [Integration Services]
- sequence execution options [Integration Services]
- containers [Integration Services], precedence constraints
ms.assetid: c5ce5435-fd89-4156-a11f-68470a69aa9f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a08fd1d66e43ede4c54284518bab191be8997a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652257"
---
# <a name="precedence-constraints"></a><span data-ttu-id="1ff09-102">선행 제약 조건</span><span class="sxs-lookup"><span data-stu-id="1ff09-102">Precedence Constraints</span></span>
  <span data-ttu-id="1ff09-103">선행 제약 조건은 패키지에 있는 실행 개체, 컨테이너 및 태스크를 제어 흐름으로 연결하고 실행 개체의 실행 여부를 결정하는 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-103">Precedence constraints link executables, containers, and tasks in packages in a control flow, and specify conditions that determine whether executables run.</span></span> <span data-ttu-id="1ff09-104">실행 개체는 For 루프, Foreach 루프 또는 시퀀스 컨테이너나 태스크 또는 이벤트 처리기일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-104">An executable can be a For Loop, Foreach Loop, or Sequence container; a task; or an event handler.</span></span> <span data-ttu-id="1ff09-105">또한 이벤트 처리기에서는 해당 실행 개체를 제어 흐름으로 연결하기 위해 선행 제약 조건이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-105">Event handlers also use precedence constraints to link their executables into a control flow.</span></span>

 <span data-ttu-id="1ff09-106">선행 제약 조건은 선행 실행 개체 및 제약 조건이 지정된 실행 개체의 두 실행 개체를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-106">A precedence constraint links two executables: the precedence executable and the constrained executable.</span></span> <span data-ttu-id="1ff09-107">선행 실행 개체는 제약 조건이 지정된 실행 개체 전에 실행되며, 선행 실행 개체의 실행 결과로 제약 조건이 지정된 실행 개체의 실행 여부가 결정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-107">The precedence executable runs before the constrained executable, and the execution result of the precedence executable may determine whether the constrained executable runs.</span></span> <span data-ttu-id="1ff09-108">다음 다이어그램에서는 선행 제약 조건으로 연결된 두 개의 실행 개체를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-108">The following diagram shows two executables linked by a precedence constraint.</span></span>

 <span data-ttu-id="1ff09-109">![선행 제약 조건으로 연결된 실행 파일](../media/ssis-pcsimple.gif "선행 제약 조건으로 연결된 실행 파일")</span><span class="sxs-lookup"><span data-stu-id="1ff09-109">![Executables connected by a precedence constraint](../media/ssis-pcsimple.gif "Executables connected by a precedence constraint")</span></span>

 <span data-ttu-id="1ff09-110">분기가 없는 선형 제어 흐름에서 선행 제약 조건은 태스크가 실행되는 시퀀스를 단독으로 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-110">In a linear control flow, that is, one without branching, precedence constraints alone govern the sequence in which tasks run.</span></span> <span data-ttu-id="1ff09-111">제어 흐름이 분기되는 경우 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 런타임 엔진은 해당 분기의 바로 다음에 오는 태스크 및 컨테이너에서의 실행 순서를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-111">If a control flow branches, the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine determines the execution order among the tasks and containers that immediately follow the branching.</span></span> <span data-ttu-id="1ff09-112">런타임 엔진은 또한 제어 흐름에서 연결되지 않은 워크플로 사이의 실행 순서를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-112">The run-time engine also determines execution order among unconnected workflows in a control flow.</span></span>

 <span data-ttu-id="1ff09-113">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 의 중첩된 컨테이너 아키텍처에서는 단일 태스크만 캡슐화하는 태스크 호스트를 제외한 모든 컨테이너에 다른 컨테이너가 포함될 수 있으며, 각 컨테이너에는 고유 제어 흐름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-113">The nested-container architecture of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enables all containers, except for the task host container that encapsulates only a single task, to include other containers, each with its own control flow.</span></span> <span data-ttu-id="1ff09-114">For 루프, Foreach 루프 및 시퀀스 컨테이너에는 여러 태스크와 다른 컨테이너가 포함될 수 있으며, 그 아래에도 다시 여러 태스크와 컨테이너가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-114">The For Loop, Foreach Loop, and Sequence containers can include multiple tasks and other containers, which in turn can include multiple tasks and containers.</span></span> <span data-ttu-id="1ff09-115">예를 들어 스크립트 태스크와 시퀀스 컨테이너가 포함된 패키지에 해당 스크립트 태스크 및 시퀀스 컨테이너로 연결되는 선행 제약 조건이 있는 경우를 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="1ff09-115">For example, a package with a Script task and a Sequence container has a precedence constraint that links the Script task and the Sequence container.</span></span> <span data-ttu-id="1ff09-116">시퀀스 컨테이너에는 3개의 스크립트 태스크가 들어 있으며, 해당 선행 제약 조건은 이 3개의 스크립트 태스크를 하나의 제어 흐름으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-116">The Sequence container includes three Script tasks, and its precedence constraints link the three Script tasks into a control flow.</span></span> <span data-ttu-id="1ff09-117">다음 다이어그램에서는 두 개의 중첩 수준이 포함된 패키지의 선행 제약 조건을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-117">The following diagram shows the precedence constraints in a package with two levels of nesting.</span></span>

 <span data-ttu-id="1ff09-118">![패키지의 선행 제약 조건](../media/mw-dts-12.gif "패키지의 선행 제약 조건")</span><span class="sxs-lookup"><span data-stu-id="1ff09-118">![Precedence contraints in a package](../media/mw-dts-12.gif "Precedence contraints in a package")</span></span>

 <span data-ttu-id="1ff09-119">패키지는 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 컨테이너 계층에서 최상위에 있으므로 선행 제약 조건으로 여러 패키지를 연결할 수 없습니다. 하지만 패키지에 패키지 실행 태스크를 추가하고 다른 패키지를 제어 흐름에 간접적으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-119">Because the package is at the top of the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] container hierarchy, multiple packages cannot be linked by precedence constraints; however, you can add an Execute Package task to a package and indirectly link another package into the control flow.</span></span>

 <span data-ttu-id="1ff09-120">선행 제약 조건은 다음과 같은 방식으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-120">You can configure precedence constraints in the following ways:</span></span>

-   <span data-ttu-id="1ff09-121">평가 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-121">Specify an evaluation operation.</span></span> <span data-ttu-id="1ff09-122">선행 제약 조건은 제약 조건 값이나 식 또는 둘을 모두 사용하여 제약 조건이 지정된 실행 개체가 실행되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-122">The precedence constraint uses a constraint value, an expression, both, or either to determine whether the constrained executable runs.</span></span>

-   <span data-ttu-id="1ff09-123">선행 제약 조건에서 실행 결과가 사용되는 경우 성공, 실패 또는 완료로 실행 결과를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-123">If the precedence constraint uses an execution result, you can specify the execution result to be success, failure, or completion.</span></span>

-   <span data-ttu-id="1ff09-124">선행 제약 조건에 계산 결과가 사용되는 경우 부울로 계산되는 식을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-124">If the precedence constraint uses an evaluation result, you can provide an expression that evaluates to a Boolean.</span></span>

-   <span data-ttu-id="1ff09-125">선행 제약 조건이 단독으로 계산되는지 아니면 제약 조건이 지정된 실행 개체에 적용되는 다른 제약 조건과 함께 계산되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-125">Specify whether the precedence constraint is evaluated singly or together with other constraints that apply to the constrained executable.</span></span>

## <a name="evaluation-operations"></a><span data-ttu-id="1ff09-126">계산 작업</span><span class="sxs-lookup"><span data-stu-id="1ff09-126">Evaluation Operations</span></span>
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="1ff09-127">는 다음과 같은 계산 작업을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-127">provides the following evaluation operations:</span></span>

-   <span data-ttu-id="1ff09-128">제약 조건이 지정된 실행 개체가 실행되는지 여부를 확인하기 위해 선행 실행 개체의 실행 결과만 사용하는 제약 조건.</span><span class="sxs-lookup"><span data-stu-id="1ff09-128">A constraint that uses only the execution result of the precedence executable to determine whether the constrained executable runs.</span></span> <span data-ttu-id="1ff09-129">선행 실행 개체의 실행 결과는 완료, 성공 또는 실패일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-129">The execution result of the precedence executable can be completion, success, or failure.</span></span> <span data-ttu-id="1ff09-130">이 작업이 기본 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-130">This is the default operation.</span></span>

-   <span data-ttu-id="1ff09-131">제약 조건이 지정된 실행 개체가 실행되는지 여부를 확인하기 위해 계산되는 식.</span><span class="sxs-lookup"><span data-stu-id="1ff09-131">An expression that is evaluated to determine whether the constrained executable runs.</span></span> <span data-ttu-id="1ff09-132">식이 True로 계산되면 제약 조건이 지정된 실행 개체가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-132">If the expression evaluates to true, the constrained executable runs.</span></span>

-   <span data-ttu-id="1ff09-133">선행 실행 개체의 실행 결과에 대한 요구 사항과 식을 계산한 반환 결과를 조합하는 제약 조건과 식</span><span class="sxs-lookup"><span data-stu-id="1ff09-133">An expression and a constraint that combines the requirements of execution results of the precedence executable and the return results of evaluating the expression.</span></span>

-   <span data-ttu-id="1ff09-134">선행 실행 개체의 실행 결과 또는 식을 계산한 반환 결과를 사용하는 제약 조건과 식</span><span class="sxs-lookup"><span data-stu-id="1ff09-134">An expression or a constraint that uses either the execution results of the precedence executable or the return results of evaluating the expression.</span></span>

 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="1ff09-135">디자이너에서는 색을 사용하여 선행 제약 조건의 유형을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-135">Designer uses color to identify the type of precedence constraint.</span></span> <span data-ttu-id="1ff09-136">Success 제약 조건은 녹색, Failure 제약 조건은 빨간색, Completion 제약 조건은 파란색입니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-136">The Success constraint is green, the Failure constraint is red, and the Completion constraint is blue.</span></span> <span data-ttu-id="1ff09-137">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에 제약 조건 유형을 나타내는 텍스트 레이블을 표시하려면 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너의 내게 필요한 옵션 기능을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-137">To display text labels in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] designer that show the type of the constraint, you must configure the accessibility features of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="1ff09-138">식은 유효한 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 식이어야 하며, 식에는 함수, 연산자, 시스템 변수 및 사용자 지정 변수가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-138">The expression must be a valid [!INCLUDE[ssIS](../../../includes/ssis-md.md)] expression, and it can include functions, operators, and system and custom variables.</span></span> <span data-ttu-id="1ff09-139">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../expressions/integration-services-ssis-expressions.md) 및 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ff09-139">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>

## <a name="execution-results"></a><span data-ttu-id="1ff09-140">실행 결과</span><span class="sxs-lookup"><span data-stu-id="1ff09-140">Execution Results</span></span>
 <span data-ttu-id="1ff09-141">선행 제약 조건에는 다음과 같은 식 결과만 단독으로 사용되거나 식이 함께 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-141">The precedence constraint can use the following execution results alone or in combination with an expression.</span></span>

-   <span data-ttu-id="1ff09-142">완료의 경우에는 출력 여부에 관계없이 선행 실행 개체가 완료되어야만 제약 조건이 지정된 실행 개체가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-142">Completion requires only that the precedence executable has completed, without regard to outcome, in order for the constrained executable to run.</span></span>

-   <span data-ttu-id="1ff09-143">성공의 경우에는 선행 실행 개체가 성공적으로 완료되어야만 제약 조건이 지정된 실행 개체가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-143">Success requires that the precedence executable must complete successfully for the constrained executable to run.</span></span>

-   <span data-ttu-id="1ff09-144">실패의 경우에는 선행 실행 개체가 실패해야만 제약 조건이 지정된 실행 개체가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-144">Failure requires that the precedence executable fail for the constrained executable to run.</span></span>

> [!NOTE]
>  <span data-ttu-id="1ff09-145">같은 `Precedence Constraint` 컬렉션의 멤버인 선행 제약 조건만 논리적 AND 조건으로 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-145">Only precedence constraints that are members of the same `Precedence Constraint` collection can be grouped in a logical AND condition.</span></span> <span data-ttu-id="1ff09-146">예를 들어 두 개의 Foreach 루프 컨테이너의 선행 제약 조건은 조합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-146">For example, you cannot combine precedence constraints from two Foreach Loop containers.</span></span>

## <a name="configuration-of-the-precedence-constraint"></a><span data-ttu-id="1ff09-147">선행 제약 조건 구성</span><span class="sxs-lookup"><span data-stu-id="1ff09-147">Configuration of the Precedence Constraint</span></span>
 <span data-ttu-id="1ff09-148">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-148">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>

 <span data-ttu-id="1ff09-149">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [선행 제약 조건 편집기](../precedence-constraint-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ff09-149">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Precedence Constraint Editor](../precedence-constraint-editor.md).</span></span>

 <span data-ttu-id="1ff09-150">이러한 속성을 프로그래밍 방식으로 설정하는 방법은 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ff09-150">For information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="1ff09-151">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1ff09-151">Related Tasks</span></span>
 <span data-ttu-id="1ff09-152">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ff09-152">For details about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>

-   [<span data-ttu-id="1ff09-153">선행 제약 조건의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="1ff09-153">Set the Properties of a Precedence Constraint</span></span>](../set-the-properties-of-a-precedence-constraint.md)

-   [<span data-ttu-id="1ff09-154">바로 가기 메뉴를 사용하여 선행 제약 조건 값 설정</span><span class="sxs-lookup"><span data-stu-id="1ff09-154">Set the Value of a Precedence Constraint by Using the Shortcut Menu</span></span>](../set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)

-   [<span data-ttu-id="1ff09-155">기본 선행 제약 조건을 사용하여 태스크 및 컨테이너 연결</span><span class="sxs-lookup"><span data-stu-id="1ff09-155">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)

     <span data-ttu-id="1ff09-156">이 항목에서는 선행 제약 조건에 대한 기본 동작을 설정하는 방법과 기본 선행 제약 조건을 사용하여 실행 개체를 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ff09-156">This topic provides information on how to set the default behavior for precedence constraints, and how to connect executables using the default precedence constraints, see.</span></span>

## <a name="related-content"></a><span data-ttu-id="1ff09-157">관련 내용</span><span class="sxs-lookup"><span data-stu-id="1ff09-157">Related Content</span></span>
 <span data-ttu-id="1ff09-158">social.technet.microsoft.com의 기술 문서 - [SSIS 식 예](https://go.microsoft.com/fwlink/?LinkId=220761)</span><span class="sxs-lookup"><span data-stu-id="1ff09-158">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>

## <a name="see-also"></a><span data-ttu-id="1ff09-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ff09-159">See Also</span></span>
 <span data-ttu-id="1ff09-160">[선행 제약 조건에](../add-expressions-to-precedence-constraints.md) [여러 선행 제약](../multiple-precedence-constraints.md) 조건에 식 추가</span><span class="sxs-lookup"><span data-stu-id="1ff09-160">[Add Expressions to Precedence Constraints](../add-expressions-to-precedence-constraints.md) [Multiple Precedence Constraints](../multiple-precedence-constraints.md)</span></span>


