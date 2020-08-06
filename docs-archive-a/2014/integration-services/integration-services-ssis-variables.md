---
title: Integration Services(SSIS) 변수 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- user-defined variables [Integration Services]
- scope [Integration Services]
- system variables [Integration Services]
- variables [Integration Services]
- variables [Integration Services], about variables
- values [Integration Services]
ms.assetid: c1e81ad6-628b-46d4-9b09-d2866517b6ca
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 956211ec971d69dc2fdb430dcada82a097280808
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651151"
---
# <a name="integration-services-ssis-variables"></a><span data-ttu-id="dc312-102">Integration Services(SSIS) 변수</span><span class="sxs-lookup"><span data-stu-id="dc312-102">Integration Services (SSIS) Variables</span></span>
  <span data-ttu-id="dc312-103">변수에는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지와 해당 컨테이너, 태스크 및 이벤트 처리기가 런타임에 사용할 수 있는 값이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-103">Variables store values that a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and its containers, tasks, and event handlers can use at run time.</span></span> <span data-ttu-id="dc312-104">스크립트 태스크와 스크립트 구성 요소의 스크립트에서도 변수가 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-104">The scripts in the Script task and the Script component can also use variables.</span></span> <span data-ttu-id="dc312-105">태스크 및 컨테이너의 순서를 워크플로에 지정하는 선행 제약 조건에서는 해당 제약 조건 정의에 식이 포함된 경우에 변수가 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-105">The precedence constraints that sequence tasks and containers into a workflow can use variables when their constraint definitions include expressions.</span></span>  
  
 <span data-ttu-id="dc312-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지에서 변수는 다음 용도로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-106">You can use variables in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages for the following purposes:</span></span>  
  
-   <span data-ttu-id="dc312-107">패키지 요소의 속성을 런타임에 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-107">Updating properties of package elements at run time.</span></span> <span data-ttu-id="dc312-108">예를 들어 Foreach 루프 컨테이너에서 허용하는 동시 실행 파일 수를 동적으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-108">For example, you can dynamically set the number of concurrent executables that a Foreach Loop container allows.</span></span>  
  
-   <span data-ttu-id="dc312-109">메모리 내 조회 테이블을 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-109">Including an in-memory lookup table.</span></span> <span data-ttu-id="dc312-110">예를 들어 패키지에서 데이터 값이 포함된 변수를 로드하는 SQL 실행 태스크가 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-110">For example, a package can run an Execute SQL task that loads a variable with data values.</span></span>  
  
-   <span data-ttu-id="dc312-111">데이터 값이 포함된 변수를 로드하고 이를 사용하여 WHERE 절에서 검색 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-111">Loading variables with data values and then using them to specify a search condition in a WHERE clause.</span></span> <span data-ttu-id="dc312-112">예를 들어 스크립트 태스크의 스크립트는 SQL 실행 태스크의 Transact-SQL 문에서 사용하는 변수 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-112">For example, the script in a Script task can update the value of a variable that is used by a Transact-SQL statement in an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="dc312-113">정수가 포함된 변수를 로드하고 이 값을 사용하여 패키지 제어 흐름 내의 반복 작업을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-113">Loading a variable with an integer and then using the value to control looping within a package control flow.</span></span> <span data-ttu-id="dc312-114">예를 들어 For 루프 컨테이너의 계산 식에서 변수를 사용하여 반복 횟수를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-114">For example, you can use a variable in the evaluation expression of a For Loop container to control iteration.</span></span>  
  
-   <span data-ttu-id="dc312-115">런타임 시 Transact-SQL 문에 대한 매개 변수 값을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-115">Populating parameter values for Transact-SQL statements at run time.</span></span> <span data-ttu-id="dc312-116">예를 들어 패키지에서 SQL 실행 태스크를 실행하고 변수를 사용하여 Transact-SQL 문의 매개 변수를 동적으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-116">For example, a package can run an Execute SQL task and then use variables to dynamically set the parameters in a Transact-SQL statement.</span></span>  
  
-   <span data-ttu-id="dc312-117">변수 값이 포함된 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-117">Building expressions that include variable values.</span></span> <span data-ttu-id="dc312-118">예를 들어 파생 열 변환에서 변수 값을 열 값으로 곱하여 얻은 결과를 열에 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-118">For example, the Derived Column transformation can populate a column with the result obtained by multiplying a variable value by a column value.</span></span>  
  
## <a name="system-and-user-defined-variables"></a><span data-ttu-id="dc312-119">시스템 및 사용자 정의 변수</span><span class="sxs-lookup"><span data-stu-id="dc312-119">System and User-Defined Variables</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="dc312-120">에서는 사용자 정의 변수와 시스템 변수라는 두 가지 유형의 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-120">supports two types of variables: user-defined variables and system variables.</span></span> <span data-ttu-id="dc312-121">사용자 정의 변수는 패키지 개발자에 의해 정의되며 시스템 변수는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-121">User-defined variables are defined by package developers, and system variables are defined by [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="dc312-122">사용자 정의 변수는 패키지에 필요한 만큼 얼마든지 만들 수 있지만 시스템 변수는 추가로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-122">You can create as many user-defined variables as a package requires, but you cannot create additional system variables.</span></span>  
  
 <span data-ttu-id="dc312-123">SQL 실행 태스크에서 SQL 문의 매개 변수에 변수를 매핑하는 데 사용하는 매개 변수 바인딩에 모든 변수, 즉 시스템 변수와 사용자 정의 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-123">All variables-system and user-defined-can be used in the parameter bindings that the Execute SQL task uses to map variables to parameters in SQL statements.</span></span> <span data-ttu-id="dc312-124">자세한 내용은 [SQL 실행 태스크](control-flow/execute-sql-task.md) 및 [SQL 실행 태스크의 매개 변수 및 반환 코드](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc312-124">For more information, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc312-125">사용자 정의 변수 및 시스템 변수의 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-125">The names of user-defined and system variables are case sensitive.</span></span>  
  
 <span data-ttu-id="dc312-126">사용자 정의 변수는 패키지, Foreach 루프 컨테이너, For 루프 컨테이너, 시퀀스 컨테이너, 태스크 및 이벤트 처리기와 같은 모든 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 컨테이너 유형에 대해 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-126">You can create user-defined variables for all [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] container types: packages, Foreach Loop containers, For Loop containers, Sequence containers, tasks, and event handlers.</span></span> <span data-ttu-id="dc312-127">사용자 정의 변수는 해당 컨테이너에 대한 Variables 컬렉션의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-127">User-defined variables are members of the Variables collection of the container.</span></span>  
  
 <span data-ttu-id="dc312-128">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너를 사용하여 패키지를 만드는 경우에는 **디자이너의** 패키지 탐색기 **탭에 있는** 변수 [!INCLUDE[ssIS](../includes/ssis-md.md)] 폴더에서 Variables 컬렉션의 멤버를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-128">If you create the package using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, you can see the members of the Variables collections in the **Variables** folders on the **Package Explorer** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="dc312-129">폴더에는 사용자 정의 변수와 시스템 변수가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-129">The folders list user-defined variables and system variables.</span></span>  
  
 <span data-ttu-id="dc312-130">사용자 정의 변수는 다음과 같은 방식으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-130">You can configure user-defined variables in the following ways:</span></span>  
  
-   <span data-ttu-id="dc312-131">변수에 대한 이름 및 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-131">Provide a name and description for the variable.</span></span>  
  
-   <span data-ttu-id="dc312-132">변수에 대한 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-132">Specify a namespace for the variable.</span></span>  
  
-   <span data-ttu-id="dc312-133">값이 변경될 때 변수가 이벤트를 발생시킬지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-133">Indicate whether the variable raises an event when its value changes.</span></span>  
  
-   <span data-ttu-id="dc312-134">변수가 읽기 전용 또는 읽기/쓰기인지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-134">Indicate whether the variable is read-only or read/write.</span></span>  
  
-   <span data-ttu-id="dc312-135">식의 계산 결과를 사용하여 변수 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-135">Use the evaluation result of an expression to set the variable value.</span></span>  
  
-   <span data-ttu-id="dc312-136">패키지 범위 또는 태스크와 같은 패키지 개체의 범위의 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-136">Create the variable in the scope of the package or a package object such as a task.</span></span>  
  
-   <span data-ttu-id="dc312-137">변수의 값과 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-137">Specify the value and data type of the variable.</span></span>  
  
 <span data-ttu-id="dc312-138">시스템 변수에서 구성할 수 있는 유일한 옵션은 값이 변경될 때 이벤트를 발생시키는지 여부를 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-138">The only configurable option on system variables is specifying whether they raise an event when they change value.</span></span>  
  
 <span data-ttu-id="dc312-139">각 컨테이너 유형에 따라 서로 다른 시스템 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-139">A different set of system variables is available for different container types.</span></span> <span data-ttu-id="dc312-140">패키지 및 해당 요소에서 사용되는 시스템 변수에 대한 자세한 내용은 [System Variables](system-variables.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc312-140">For more information about the system variables used by packages and their elements, see [System Variables](system-variables.md).</span></span>  
  
 <span data-ttu-id="dc312-141">변수의 실제 사용 시나리오에 대한 자세한 내용은 [패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc312-141">For more information about real-life use scenarios for variables, see [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
## <a name="variable-properties"></a><span data-ttu-id="dc312-142">변수 속성</span><span class="sxs-lookup"><span data-stu-id="dc312-142">Variable Properties</span></span>  
 <span data-ttu-id="dc312-143">**변수** 창이나 **속성** 창에서 다음 속성을 설정하여 사용자 정의 변수를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-143">You can configure user-defined variables by setting the following properties in either the **Variables** window or the **Properties** window.</span></span> <span data-ttu-id="dc312-144">일부 속성은 속성 창에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-144">Certain properties are available only in the Properties window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc312-145">시스템 변수에서 구성할 수 있는 유일한 옵션은 값이 변경될 때 이벤트를 발생시키는지 여부를 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-145">The only configurable option on system variables is specifying whether they raise an event when they change value.</span></span>  
  
 <span data-ttu-id="dc312-146">Description</span><span class="sxs-lookup"><span data-stu-id="dc312-146">Description</span></span>  
 <span data-ttu-id="dc312-147">변수에 대한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-147">Specifies the description of the variable.</span></span>  
  
 <span data-ttu-id="dc312-148">EvaluateAsExpression</span><span class="sxs-lookup"><span data-stu-id="dc312-148">EvaluateAsExpression</span></span>  
 <span data-ttu-id="dc312-149">속성이로 설정 되 면 `True` 제공 된 식이 변수 값을 설정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-149">When the property is set to `True`, the expression provided is used to set the variable value.</span></span>  
  
 <span data-ttu-id="dc312-150">식</span><span class="sxs-lookup"><span data-stu-id="dc312-150">Expression</span></span>  
 <span data-ttu-id="dc312-151">변수에 할당되는 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-151">Specifies the expression that is assigned to the variable.</span></span>  
  
 <span data-ttu-id="dc312-152">Name</span><span class="sxs-lookup"><span data-stu-id="dc312-152">Name</span></span>  
 <span data-ttu-id="dc312-153">변수 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-153">Specifies the variable name.</span></span>  
  
 <span data-ttu-id="dc312-154">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="dc312-154">Namespace</span></span>  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]<span data-ttu-id="dc312-155">은 **User** 및 **System**의 두 가지 네임스페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-155">provides two namespaces, **User** and **System**.</span></span> <span data-ttu-id="dc312-156">기본적으로 사용자 지정 변수는 **사용자** 네임스페이스에 속하고 시스템 변수는 **시스템** 네임스페이스에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-156">By default, custom variables are in the **User** namespace, and system variables are in the **System** namespace.</span></span> <span data-ttu-id="dc312-157">사용자 정의 변수에 대한 추가 네임스페이스를 만들고 **User** 네임스페이스의 이름을 변경할 수 있지만 **System** 네임스페이스의 이름을 변경하거나, **System** 네임스페이스에 변수를 추가하거나, 시스템 변수를 다른 네임스페이스에 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-157">You can create additional namespaces for user-defined variables and change the name of the **User** namespace, but you cannot change the name of the **System** namespace, add variables to the **System** namespace, or assign system variables to a different namespace.</span></span>  
  
 <span data-ttu-id="dc312-158">RaiseChangedEvent</span><span class="sxs-lookup"><span data-stu-id="dc312-158">RaiseChangedEvent</span></span>  
 <span data-ttu-id="dc312-159">이 속성을 `True`로 설정하면 변수에서 값을 변경할 때 `OnVariableValueChanged` 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-159">When the property is set to `True`, the `OnVariableValueChanged` event is raised when the variable changes value.</span></span>  
  
 <span data-ttu-id="dc312-160">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="dc312-160">ReadOnly</span></span>  
 <span data-ttu-id="dc312-161">이 속성을 `False`로 설정하면 변수는 읽기/쓰기 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-161">When the property is set to `False`, the variable is read\write.</span></span>  
  
 <span data-ttu-id="dc312-162">Scope</span><span class="sxs-lookup"><span data-stu-id="dc312-162">Scope</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="dc312-163">이 속성 설정은 **변수** 창에서 **변수 이동** 을 클릭한 경우에만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-163">You can change this property setting only by clicking **Move Variable** in the **Variables** window.</span></span>  
  
 <span data-ttu-id="dc312-164">변수는 패키지의 범위나 패키지에 들어 있는 컨테이너, 태스크 또는 이벤트 처리기의 범위 내에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-164">A variable is created within the scope of a package or within the scope of a container, task, or event handler in the package.</span></span> <span data-ttu-id="dc312-165">패키지 컨테이너는 컨테이너의 최상위 계층에 있으므로 패키지 범위의 변수는 전역 변수와 같은 기능을 수행하며 패키지의 모든 컨테이너에서 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-165">Because the package container is at the top of the container hierarchy, variables with package scope function like global variables and can be used by all containers in the package.</span></span> <span data-ttu-id="dc312-166">이와 비슷하게 For 루프 컨테이너와 같은 컨테이너의 범위 내에서 정의된 변수는 해당 For 루프 컨테이너 내의 모든 태스크 또는 컨테이너에서 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-166">Similarly, variables defined within the scope of a container such as a For Loop container can be used by all tasks or containers within the For Loop container.</span></span>  
  
 <span data-ttu-id="dc312-167">패키지에서 패키지 실행 태스크를 사용하여 다른 패키지가 실행되는 경우 호출한 패키지 또는 실행 패키지 태스크의 범위 내에서 정의된 변수는 부모 패키지 변수 구성 유형을 통해 호출된 패키지에서 사용할 수 있도록 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-167">If a package runs other packages by using the Execute Package task, the variables defined in the scope of the calling package or the Execute Package task can be made available to the called package by using the Parent Package Variable configuration type.</span></span> <span data-ttu-id="dc312-168">자세한 내용은 [Package Configurations](../../2014/integration-services/package-configurations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc312-168">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
 <span data-ttu-id="dc312-169">IncludeInDebugDump</span><span class="sxs-lookup"><span data-stu-id="dc312-169">IncludeInDebugDump</span></span>  
 <span data-ttu-id="dc312-170">디버그 덤프 파일에 변수 값이 포함되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-170">Indicate whether the variable value is included in the debug dump files.</span></span>  
  
 <span data-ttu-id="dc312-171">사용자 정의 변수 및 시스템 변수의 경우 **경우 inclueindebugdump** 옵션의 기본값은 `true` 입니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-171">For user-defined variables and system variables, the default value for the **InclueInDebugDump** option is `true`.</span></span>  
  
 <span data-ttu-id="dc312-172">그러나 사용자 정의 변수의 경우 **IncludeInDebugDump** `false` 다음 조건이 충족 될 때 시스템에서 IncludeInDebugDump 옵션을로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-172">However, for user-defined variables, the system resets the **IncludeInDebugDump** option to `false` when the following conditions are met:</span></span>  
  
-   <span data-ttu-id="dc312-173">**EvaluateAsExpression** variable 속성이로 설정 된 경우 `true` 시스템에서는 **IncludeInDebugDump** 옵션을로 다시 설정 합니다 `false` .</span><span class="sxs-lookup"><span data-stu-id="dc312-173">If the **EvaluateAsExpression** variable property is set to `true`, the system resets the **IncludeInDebugDump** option to `false`.</span></span>  
  
     <span data-ttu-id="dc312-174">디버그 덤프 파일에 식의 텍스트를 변수 값으로 포함 하려면 **IncludeInDebugDump** 옵션을로 설정 `true` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-174">To include the text of the expression as the variable value in the debug dump files, set the **IncludeInDebugDump** option to `true`.</span></span>  
  
-   <span data-ttu-id="dc312-175">변수 데이터 형식이 문자열로 변경 되 면 시스템은 **IncludeInDebugDump** 옵션을로 다시 설정 `false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-175">If the variable data type is changed to a string, the system resets the **IncludeInDebugDump** option to `false`.</span></span>  
  
 <span data-ttu-id="dc312-176">시스템에서 **IncludeInDebugDump** 옵션을로 다시 설정 하면 `false` 사용자가 선택한 값이 재정의 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-176">When the system resets the **IncludeInDebugDump** option to `false`, this might override the value selected by the user.</span></span>  
  
 <span data-ttu-id="dc312-177">값</span><span class="sxs-lookup"><span data-stu-id="dc312-177">Value</span></span>  
 <span data-ttu-id="dc312-178">사용자 정의 변수의 값은 문자 또는 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-178">The value of a user-defined variable can be a literal or an expression.</span></span> <span data-ttu-id="dc312-179">변수에는 변수 값과 값의 데이터 형식을 설정하기 위한 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-179">A variable includes options for setting the variable value and the data type of the value.</span></span> <span data-ttu-id="dc312-180">이 두 속성은 호환되어야 합니다. 예를 들어 정수 데이터 형식에는 문자열 값을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-180">The two properties must be compatible: for example, the use of a string value together with an integer data type is not valid.</span></span>  
  
 <span data-ttu-id="dc312-181">변수가 식으로 계산되도록 구성된 경우에는 식을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-181">If the variable is configured to evaluate as an expression, you must provide an expression.</span></span> <span data-ttu-id="dc312-182">런타임에 식이 계산되고 변수에는 해당 계산의 결과가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-182">At run time, the expression is evaluated, and the variable is set to the evaluation result.</span></span> <span data-ttu-id="dc312-183">예를 들어 변수에 `DATEPART("month", GETDATE())` 식이 사용된 경우 이 변수의 값은 현재 날짜의 월에 해당하는 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-183">For example, if a variable uses the expression `DATEPART("month", GETDATE())` the value of the variable is the number equivalent of the month for the current date.</span></span> <span data-ttu-id="dc312-184">식은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 식 문법 구문을 사용하는 유효한 식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-184">The expression must be a valid expression that uses the [!INCLUDE[ssIS](../includes/ssis-md.md)] expression grammar syntax.</span></span> <span data-ttu-id="dc312-185">변수에 식이 사용되는 경우 이 식에는 식 문법에서 제공하는 연산자와 함수 및 리터럴을 사용할 수 있지만 식에서 패키지의 데이터 흐름에 있는 열을 참조할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-185">When an expression is used with variables, the expression can use literals and the operators and functions that the expression grammar provides, but the expression cannot reference the columns from a data flow in the package.</span></span> <span data-ttu-id="dc312-186">식의 최대 길이는 4000자입니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-186">The maximum length of an expression is 4000 characters.</span></span> <span data-ttu-id="dc312-187">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md)가 될 때까지 워크플로를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-187">For more information, see [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="dc312-188">ValueType</span><span class="sxs-lookup"><span data-stu-id="dc312-188">ValueType</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="dc312-189"> 이 속성 값은 **변수** 창의 **데이터 형식** 열에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-189">The property value appears in the **Data type** column in the **Variables** window.</span></span>  
  
 <span data-ttu-id="dc312-190">변수 값의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-190">Specifies the data type of the variable value.</span></span>  
  
## <a name="configuring-variables"></a><span data-ttu-id="dc312-191">변수 구성</span><span class="sxs-lookup"><span data-stu-id="dc312-191">Configuring Variables</span></span>  
 <span data-ttu-id="dc312-192">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc312-192">You can set properties through [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="dc312-193">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [변수 창](../../2014/integration-services/variables-window.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc312-193">For more information about the properties that you can set in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, see [Variables Window](../../2014/integration-services/variables-window.md).</span></span>  
  
 <span data-ttu-id="dc312-194">변수 속성에 대한 자세한 내용과 이러한 변수를 프로그래밍 방식으로 설정하는 방법은 <xref:Microsoft.SqlServer.Dts.Runtime.Variable>을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc312-194">To learn more about variable properties, and for more information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.Variable>.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="dc312-195">관련 작업</span><span class="sxs-lookup"><span data-stu-id="dc312-195">Related Tasks</span></span>  
 [<span data-ttu-id="dc312-196">패키지에서 사용자 정의 변수의 범위 추가, 삭제, 변경</span><span class="sxs-lookup"><span data-stu-id="dc312-196">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
 [<span data-ttu-id="dc312-197">사용자 정의 변수의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="dc312-197">Set the Properties of a User-Defined Variable</span></span>](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)  
  
 [<span data-ttu-id="dc312-198">자식 패키지에서 변수 및 매개 변수의 값 사용</span><span class="sxs-lookup"><span data-stu-id="dc312-198">Use the Values of Variables and Parameters in a Child Package</span></span>](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
 [<span data-ttu-id="dc312-199">쿼리 매개 변수를 데이터 흐름 구성 요소의 변수에 매핑</span><span class="sxs-lookup"><span data-stu-id="dc312-199">Map Query Parameters to Variables in a Data Flow Component</span></span>](data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
  
