---
title: 선행 제약 조건의 속성 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Precedence Constraint Editor dialog box
- precedence constraints [Integration Services], properties
ms.assetid: d990f600-5c09-4cd5-8528-0a58d79dc9f2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55b95bdb79d801156bef6198bc0f57accb5d9517
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660039"
---
# <a name="set-the-properties-of-a-precedence-constraint"></a><span data-ttu-id="9f90c-102">선행 제약 조건의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="9f90c-102">Set the Properties of a Precedence Constraint</span></span>
  <span data-ttu-id="9f90c-103">선행 제약 조건의 속성을 설정하려면 다음 도구 중 하나를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-103">To set properties on precedence constraints, you can use one of these tools:</span></span>  
  
-   <span data-ttu-id="9f90c-104">**선행 제약 조건 편집기** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-104">You can use the **Precedence Constraint Editor** dialog box.</span></span>  
  
-   <span data-ttu-id="9f90c-105">속성 창을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-105">You can use the Properties window.</span></span> <span data-ttu-id="9f90c-106">속성 창에는 **선행 제약 조건 편집기** 대화 상자에서 사용할 수 없는 선행 제약 조건을 구성하기 위한 속성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-106">The Properties window lists properties for configuring precedence constraints that are not available in the **Precedence Constraint Editor** dialog box.</span></span> <span data-ttu-id="9f90c-107">속성 창에서는 선행 제약 조건의 설명과 이름을 제공하고 디자인 화면에서 선행 제약 조건에 표시할 주석을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-107">In the Properties window, you can provide a description and name of the precedence constraint, and configure the annotation to display for the precedence constraint on the design surface.</span></span>  
  
 <span data-ttu-id="9f90c-108">다음 절차에서는 이러한 각 도구를 사용하여 선행 제약 조건의 속성을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-108">The following procedures describe how to set properties on precedence constraints by using each of these tools.</span></span>  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-precedence-constraint-editor"></a><span data-ttu-id="9f90c-109">선행 제약 조건 편집기를 사용하여 선행 제약 조건의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="9f90c-109">To set the properties of a precedence constraint by using the Precedence Constraint Editor</span></span>  
  
1.  <span data-ttu-id="9f90c-110">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-110">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="9f90c-111">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="9f90c-112">**제어 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-112">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="9f90c-113">선행 제약 조건을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-113">Double-click the precedence constraint.</span></span>  
  
     <span data-ttu-id="9f90c-114">**선행 제약 조건 편집기** 가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-114">The **Precedence Constraint Editor** opens.</span></span>  
  
5.  <span data-ttu-id="9f90c-115">**평가 작업** 드롭다운 목록에서 평가 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-115">In the **Evaluation operation** drop-down list, select an evaluation operation.</span></span>  
  
6.  <span data-ttu-id="9f90c-116">`Value`드롭다운 목록에서 선행 실행 파일의 실행 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-116">In the `Value` drop-down list, select the execution result of the precedence executable.</span></span>  
  
7.  <span data-ttu-id="9f90c-117">계산 작업에 식이 사용 되는 경우 상자에 식을 `Expression` 입력 하 고 **테스트** 를 클릭 하 여 식을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-117">If the evaluation operation uses an expression, in the `Expression` box, type an expression, and click **Test** to evaluate the expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9f90c-118">변수 이름은 대소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-118">Variable names are case-sensitive.</span></span>  
  
8.  <span data-ttu-id="9f90c-119">제약 조건이 지정 된 실행 파일에 여러 태스크 또는 컨테이너가 연결 된 경우에는 **논리적 AND** 를 선택 하 여 모든 선행 실행 파일의 실행 결과가로 계산 되어야 하도록 지정 합니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="9f90c-119">If multiple tasks or containers are connected to the constrained executable, select **Logical AND** to specify that the execution results of all preceding executables must evaluate to `true`.</span></span> <span data-ttu-id="9f90c-120">단일 실행 결과만로 계산 되도록 지정 하려면 **논리적 OR** 을 선택 합니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="9f90c-120">Select **Logical OR** to specify that only one execution result must evaluate to `true`.</span></span>  
  
9. <span data-ttu-id="9f90c-121">**확인** 을 클릭하여 **선행 제약 조건 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-121">Click **OK** to close the **Precedence Constraint Editor**.</span></span>  
  
10. <span data-ttu-id="9f90c-122">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-properties-window"></a><span data-ttu-id="9f90c-123">속성 창을 사용하여 선행 제약 조건의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="9f90c-123">To set the properties of a precedence constraint by using the Properties window</span></span>  
  
1.  <span data-ttu-id="9f90c-124">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 수정할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to modify.</span></span>  
  
2.  <span data-ttu-id="9f90c-125">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-125">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="9f90c-126">**제어 흐름** 탭을 클릭 합니다. **제어 흐름** 탭의 디자인 화면에서 선행 제약 조건을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-126">Click the **Control Flow** tab. On the design surface of the **Control Flow** tab, right-click the precedence constraint, and then click **Properties**.</span></span> <span data-ttu-id="9f90c-127">속성 창에서 속성 값을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-127">In the Properties window, modify the property values.</span></span>  
  
4.  <span data-ttu-id="9f90c-128">**속성** 창에서 다음과 같은 선행 제약 조건의 읽기/쓰기 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-128">In the **Properties** window, set the following read/write properties of precedence constraints:</span></span>  
  
    |<span data-ttu-id="9f90c-129">읽기/쓰기 속성</span><span class="sxs-lookup"><span data-stu-id="9f90c-129">Read/write property</span></span>|<span data-ttu-id="9f90c-130">구성 동작</span><span class="sxs-lookup"><span data-stu-id="9f90c-130">Configuration action</span></span>|  
    |--------------------------|--------------------------|  
    |<span data-ttu-id="9f90c-131">Description</span><span class="sxs-lookup"><span data-stu-id="9f90c-131">Description</span></span>|<span data-ttu-id="9f90c-132">설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-132">Provide a description.</span></span>|  
    |<span data-ttu-id="9f90c-133">EvalOp</span><span class="sxs-lookup"><span data-stu-id="9f90c-133">EvalOp</span></span>|<span data-ttu-id="9f90c-134">계산 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-134">Select an evaluation operation.</span></span> <span data-ttu-id="9f90c-135">`Expression`, **Expressionandconstant**또는 **expressionandconstant** 작업을 선택할 경우 식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-135">If the `Expression`, **ExpressionAndConstant**, or **ExpressionOrConstant** operation is selected, you can specify an expression.</span></span>|  
    |<span data-ttu-id="9f90c-136">식</span><span class="sxs-lookup"><span data-stu-id="9f90c-136">Expression</span></span>|<span data-ttu-id="9f90c-137">계산 작업에 식이 포함된 경우 식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-137">If the evaluation operation includes and expression, provide an expression.</span></span> <span data-ttu-id="9f90c-138">식은 부울로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-138">The expression must evaluate to a Boolean.</span></span> <span data-ttu-id="9f90c-139">식 언어에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f90c-139">For more information about the expression language, see [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>|  
    |<span data-ttu-id="9f90c-140">LogicalAnd</span><span class="sxs-lookup"><span data-stu-id="9f90c-140">LogicalAnd</span></span>|<span data-ttu-id="9f90c-141">`LogicalAnd`선행 제약 조건이 다른 선행 제약 조건과 함께 계산 되는지 여부를 지정 하려면 설정 하 고, 여러 실행 파일이 제약 조건이 있는 실행 파일에 연결 된 경우</span><span class="sxs-lookup"><span data-stu-id="9f90c-141">Set `LogicalAnd` to specify whether the precedence constraint is evaluated in concert with other precedence constraints, when multiple executables precede and are linked to the constrained executable</span></span>|  
    |<span data-ttu-id="9f90c-142">Name</span><span class="sxs-lookup"><span data-stu-id="9f90c-142">Name</span></span>|<span data-ttu-id="9f90c-143">선행 제약 조건의 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-143">Update the name of the precedence constraint.</span></span>|  
    |<span data-ttu-id="9f90c-144">ShowAnnotation</span><span class="sxs-lookup"><span data-stu-id="9f90c-144">ShowAnnotation</span></span>|<span data-ttu-id="9f90c-145">사용할 주석의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-145">Specify the type of annotation to use.</span></span> <span data-ttu-id="9f90c-146">주석을 사용하지 않으려면 **Never** 를 선택하고, 요청 시 주석을 사용하려면 **AsNeeded** 를 선택하고, Name 속성의 값을 사용하여 자동으로 주석을 달려면 **ConstraintName** 을 선택합니다. 또한 Description 속성의 값을 사용하여 자동으로 주석을 달려면 **ConstraintDescription** 을 선택하고, Value 및 Expression 속성의 값을 사용하여 자동으로 주석을 달려면 **ConstraintOptions** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-146">Choose **Never** to disable annotations, **AsNeeded** to enable annotation on demand, **ConstraintName** to automatically annotate using the value of the Name property, **ConstraintDescription** to automatically annotate using the value of the Description property, and **ConstraintOptions** to automatically annotate using the values of the Value and Expression properties.</span></span>|  
    |<span data-ttu-id="9f90c-147">값</span><span class="sxs-lookup"><span data-stu-id="9f90c-147">Value</span></span>|<span data-ttu-id="9f90c-148">EvalOP 속성에 지정된 계산 작업에 제약 조건이 포함된 경우 제약 조건이 지정된 실행 개체의 실행 결과를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-148">If the evaluation operation specified in the EvalOP property includes a constraint, select the execution result of the constraining executable.</span></span>|  
  
5.  <span data-ttu-id="9f90c-149">속성 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-149">Close the Properties window.</span></span>  
  
6.  <span data-ttu-id="9f90c-150">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f90c-150">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f90c-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f90c-151">See Also</span></span>  
 <span data-ttu-id="9f90c-152">[선행 제약 조건](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="9f90c-152">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="9f90c-153">[기본 선행 제약 조건을 사용 하 여 태스크 및 컨테이너 연결](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="9f90c-153">[Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 <span data-ttu-id="9f90c-154">[바로 가기 메뉴를 사용 하 여 선행 제약 조건 값 설정](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="9f90c-154">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 [<span data-ttu-id="9f90c-155">선행 제약 조건에서 식 사용</span><span class="sxs-lookup"><span data-stu-id="9f90c-155">Use an Expression in a Precedence Constraint</span></span>](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
