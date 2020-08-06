---
title: 사용자 정의 변수의 속성 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bf53be469e3d377f7efb379f78e85e31b26767b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742376"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a><span data-ttu-id="f2dec-102">사용자 정의 변수의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="f2dec-102">Set the Properties of a User-Defined Variable</span></span>
  <span data-ttu-id="f2dec-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서 사용자 정의 변수의 속성을 설정하려면 다음 기능 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-103">To set the properties of a user-defined variable in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], you can use one of the following features:</span></span>  
  
-   <span data-ttu-id="f2dec-104">변수 창.</span><span class="sxs-lookup"><span data-stu-id="f2dec-104">Variables window.</span></span>  
  
-   <span data-ttu-id="f2dec-105">속성 창.</span><span class="sxs-lookup"><span data-stu-id="f2dec-105">Properties window.</span></span> <span data-ttu-id="f2dec-106">**속성** 창에는 **변수** 창에서 사용할 수 없는 변수를 구성하기 위한 Description, EvaluateAsExpression, Expression, ReadOnly, ValueType 및 IncludeInDebugDump 속성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-106">The **Properties** window lists properties for configuring variables that are not available in the **Variables** window: Description, EvaluateAsExpression, Expression, ReadOnly, ValueType, and IncludeInDebugDump.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]<span data-ttu-id="f2dec-107">에서는 속성을 업데이트할 수 없는 시스템 변수 집합도 제공합니다(RaiseChangedEvent 속성은 제외).</span><span class="sxs-lookup"><span data-stu-id="f2dec-107">also provides a set of system variables whose properties cannot be updated, with the exception of the RaiseChangedEvent property.</span></span>  
  
 <span data-ttu-id="f2dec-108">**변수의 식 설정**</span><span class="sxs-lookup"><span data-stu-id="f2dec-108">**Setting Expressions on Variables**</span></span>  
  
 <span data-ttu-id="f2dec-109">**속성** 창을 사용하여 사용자 정의 변수의 식을 설정하는 경우 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2dec-109">When you use the **Properties** window to set expressions on a user-defined variable:</span></span>  
  
-   <span data-ttu-id="f2dec-110">변수 값은 Value 또는 Expression 속성에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-110">The value of a variable can be set by the Value or the Expression property.</span></span> <span data-ttu-id="f2dec-111">기본적으로 EvaluateAsExpression 속성은로 설정 되 `False` 고 변수 값은 value 속성으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-111">By default, the EvaluateAsExpression property is set to `False` and the value of the variable is set by the Value property.</span></span> <span data-ttu-id="f2dec-112">식을 사용 하 여 값을 설정 하려면 먼저 EvaluateAsExpression를로 설정한 `True` 다음 expression 속성에 식을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-112">To use an expression to set the value, you must first set EvaluateAsExpression to `True`, and then provide an expression in the Expression property.</span></span> <span data-ttu-id="f2dec-113">Value 속성은 이 식의 계산 결과로 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-113">The Value property is automatically set to the evaluation result of the expression.</span></span>  
  
-   <span data-ttu-id="f2dec-114">ValueType 속성에는 Value 속성에 있는 값의 데이터 형식이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-114">The ValueType property contains the data type of the value in the Value property.</span></span> <span data-ttu-id="f2dec-115">Value가 식에서 설정된 경우 ValueType은 해당 식의 계산 결과와 호환되는 데이터 형식으로 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-115">When Value is set by an expression, ValueType is automatically updated to a data type that is compatible with the evaluation result of the expression.</span></span> <span data-ttu-id="f2dec-116">예를 들어 값이 0이 고 ValueType 속성이 **Int32** 를 포함 하는 경우 식을 GETDATE ()로 설정 하면 Value에 현재 날짜와 시간이 포함 되 고 ValueType은로 설정 됩니다 `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="f2dec-116">For example, if Value contains 0 and ValueType property contains **Int32** and you then set Expression to GETDATE(), Value contains the current date and time and ValueType is set to `DateTime`.</span></span>  
  
-   <span data-ttu-id="f2dec-117">변수에 대한 **속성** 창에서 **식 작성기** 대화 상자에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-117">The **Properties** window for the variable provides access to the **Expression Builder** dialog box.</span></span> <span data-ttu-id="f2dec-118">이 도구를 사용하여 식 작성, 유효성 검사 및 계산을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-118">You can use this tool to build, validate, and evaluate expressions.</span></span> <span data-ttu-id="f2dec-119">자세한 내용은 [식 작성기](expressions/expression-builder.md) 및 [Integration Services&#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2dec-119">For more information, see [Expression Builder](expressions/expression-builder.md) and [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="f2dec-120">**변수** 창을 사용하여 사용자 정의 변수의 식을 설정하는 경우 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2dec-120">When you use the **Variables** window to set expressions on a user-defined variable:</span></span>  
  
-   <span data-ttu-id="f2dec-121">식을 사용 하 여 변수 값을 설정 하려면 먼저 변수 데이터 형식이 식의 계산 결과와 호환 되는지 확인 한 다음 `Expression` **변수** 창의 열에 식을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-121">To use an expression to set the variable value, first confirm that the variable data type is compatible with the evaluation result of the expression and then provide an expression in the `Expression` column of the **Variables** window.</span></span> <span data-ttu-id="f2dec-122">**속성** 창의 EvaluateAsExpression 속성은 자동으로로 설정 됩니다 `True` .</span><span class="sxs-lookup"><span data-stu-id="f2dec-122">The EvaluateAsExpression property in the **Properties** window is automatically set to `True`.</span></span>  
  
-   <span data-ttu-id="f2dec-123">변수에 식을 할당할 경우 해당 변수 옆에 특수 아이콘 표식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-123">When you assign an expression to a variable, a special icon marker displays next to the variable.</span></span> <span data-ttu-id="f2dec-124">이 특수 아이콘 표식은 식이 설정되어 있는 연결 관리자 및 태스크 옆에도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-124">This special icon marker also displays next to connection managers and tasks that have expressions set on them.</span></span>  
  
-   <span data-ttu-id="f2dec-125">변수에 대한 **변수** 창에서 **식 작성기** 대화 상자에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-125">The **Variables** window for the variable provides access to the **Expression Builder** dialog box.</span></span> <span data-ttu-id="f2dec-126">이 도구를 사용하여 식 작성, 유효성 검사 및 계산을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-126">You can use this tool to build, validate, and evaluate expressions.</span></span> <span data-ttu-id="f2dec-127">자세한 내용은 [식 작성기](expressions/expression-builder.md) 및 [Integration Services&#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2dec-127">For more information, see [Expression Builder](expressions/expression-builder.md) and [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="f2dec-128">**변수에 식을** 할당 하 고가로 설정 된 경우 변수 및 **속성** 창에서 `EvaluateAsExpression` `True` 변수 데이터 형식을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-128">In both the **Variables** and **Properties** window, if you assign an expression to the variable, and `EvaluateAsExpression` is set to `True`, you cannot change the variable data type.</span></span>  
  
 <span data-ttu-id="f2dec-129">**네임스페이스 및 이름 속성 설정**</span><span class="sxs-lookup"><span data-stu-id="f2dec-129">**Setting the Namespace and Name Properties**</span></span>  
  
 <span data-ttu-id="f2dec-130">`Name` 및 `Namespace` 속성 값은 Unicode Standard 2.0에 정의된 대로 영문자 또는 밑줄(_)로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-130">The values of the `Name` and `Namespace` properties must begin with an alphabetic character letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span> <span data-ttu-id="f2dec-131">후속 문자는 Unicode Standard 2.0에 정의된 문자 또는 숫자이거나 밑줄(\_)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-131">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, or the underscore (\_).</span></span>  
  
## <a name="using-the-variables-window-to-set-properties"></a><span data-ttu-id="f2dec-132">변수 창을 사용하여 속성 설정</span><span class="sxs-lookup"><span data-stu-id="f2dec-132">Using the Variables Window to Set Properties</span></span>  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a><span data-ttu-id="f2dec-133">변수 창을 사용하여 변수의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="f2dec-133">To set the properties of a variable by using the Variables window</span></span>  
  
1.  <span data-ttu-id="f2dec-134">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-134">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="f2dec-135">솔루션 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-135">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="f2dec-136">**SSIS** 메뉴에서 **변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-136">On the **SSIS** menu, click **Variables**.</span></span>  
  
     <span data-ttu-id="f2dec-137">**옵션** 대화 상자의 **키보드** 페이지에서 필요에 따라 선택한 키 조합에 View.Variables 명령을 매핑하여 **변수** 창을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-137">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="f2dec-138">필요에 따라 **변수** 창에서 **표 옵션**을 클릭하고 **변수** 창에 표시할 열을 선택한 다음 변수 목록에 적용할 필터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-138">Optionally, in the **Variables** window click **Grid Options**, and then select the columns to appear in the **Variables** window and select the filters to apply to the list of variables.</span></span>  
  
5.  <span data-ttu-id="f2dec-139">목록에서 변수를 선택한 다음 `Name` , **데이터 형식**,,, `Value` `Namespace` **변경 이벤트 발생**, **설명** 및 열에서 값을 업데이트 `Expression` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-139">Select the variable in the list, and then update values in the `Name`, **Data Type**, `Value`, `Namespace`, **Raise Change Event**, **Description,** and `Expression` columns.</span></span>  
  
6.  <span data-ttu-id="f2dec-140">목록에서 변수를 선택하고 **변수 이동** 을 클릭하여 범위를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-140">Select the variable in the list, and then click **Move Variable** to change the scope.</span></span>  
  
7.  <span data-ttu-id="f2dec-141">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-141">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="using-the-properties-window-to-set-properties"></a><span data-ttu-id="f2dec-142">속성 창을 사용하여 속성 설정</span><span class="sxs-lookup"><span data-stu-id="f2dec-142">Using the Properties Window to Set Properties</span></span>  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-properties-window"></a><span data-ttu-id="f2dec-143">속성 창을 사용하여 변수의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="f2dec-143">To set the properties of a variable by using the Properties window</span></span>  
  
1.  <span data-ttu-id="f2dec-144">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-144">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="f2dec-145">솔루션 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-145">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="f2dec-146">**보기** 메뉴에서 **속성 창**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-146">On the **View** menu, click **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="f2dec-147">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **패키지 탐색기** 탭을 클릭하고 패키지 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-147">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Package Explorer** tab and expand the Package node.</span></span>  
  
5.  <span data-ttu-id="f2dec-148">패키지 범위의 변수를 수정하려면 변수 노드를 확장합니다. 그렇지 않으면 수정할 변수가 있는 변수 노드를 찾을 때까지 이벤트 처리기 또는 실행 파일 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-148">To modify variables with package scope, expand the Variables node; otherwise, expand the Event Handlers or Executables nodes until you locate the Variables node that contains the variable that you want to modify.</span></span>  
  
6.  <span data-ttu-id="f2dec-149">속성을 수정할 변수를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-149">Click the variable whose properties you want to modify.</span></span>  
  
7.  <span data-ttu-id="f2dec-150">**속성** 창에서 읽기/쓰기 변수 속성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-150">In the **Properties** window, update the read/write variable properties.</span></span> <span data-ttu-id="f2dec-151">일부 속성은 사용자 정의 변수에 대해 읽기/읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-151">Some properties are read/read only for user-defined variables.</span></span>  
  
     <span data-ttu-id="f2dec-152">속성에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2dec-152">For more information about the properties, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
8.  <span data-ttu-id="f2dec-153">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2dec-153">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2dec-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2dec-154">See Also</span></span>  
 <span data-ttu-id="f2dec-155">[Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="f2dec-155">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="f2dec-156">[패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="f2dec-156">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 [<span data-ttu-id="f2dec-157">패키지에서 사용자 정의 변수의 범위 추가, 삭제, 변경</span><span class="sxs-lookup"><span data-stu-id="f2dec-157">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
