---
title: Integration Services(SSIS) 식 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], expressions
- Integration Services packages, expressions
- SQL Server Integration Services packages, expressions
- expressions [Integration Services], packages
- SSIS packages, expressions
ms.assetid: 26d2e242-7f60-4fa9-a70d-548a80eee667
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff0bd46034108537ebede7567b042997c94871ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732832"
---
# <a name="integration-services-ssis-expressions"></a><span data-ttu-id="940f3-102">Integration Services(SSIS) 식</span><span class="sxs-lookup"><span data-stu-id="940f3-102">Integration Services (SSIS) Expressions</span></span>
  <span data-ttu-id="940f3-103">식은 하나의 데이터 값을 생성하는 기호(식별자, 리터럴, 함수 및 연산자)의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-103">An expression is a combination of symbols-identifiers, literals, functions, and operators-that yields a single data value.</span></span> <span data-ttu-id="940f3-104">간단한 식으로는 단일 상수, 변수 또는 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-104">Simple expressions can be a single constant, variable, or function.</span></span> <span data-ttu-id="940f3-105">그러나 식이 여러 개의 연산자와 함수를 사용하고 여러 개의 열과 변수를 참조하는 경우가 더 많습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-105">More frequently, expressions are complex, using multiple operators and functions and referencing multiple columns and variables.</span></span> <span data-ttu-id="940f3-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 식은 CASE 문의 조건 정의, 데이터 열의 값 만들기 및 업데이트, 변수에 값 할당, 런타임에 속성 업데이트 또는 채우기, 선행 제약 조건에 제약 조건 정의, For Loop 컨테이너에 사용되는 식 제공 등에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-106">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], expressions can be used to define conditions for CASE statements, create and update values in data columns, assign values to variables, update or populate properties at run time, define constraints in precedence constraints, and provide the expressions used by the For Loop container.</span></span>  
  
 <span data-ttu-id="940f3-107">식은 식 언어 및 식 계산기를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-107">Expressions are based on an expression language, and the expression evaluator.</span></span> <span data-ttu-id="940f3-108">식 계산기는 식을 구분 분석하고 식이 식 언어의 규칙을 따를지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-108">The expression evaluator parses the expression and determines whether the expression follows the rules of the expression language.</span></span> <span data-ttu-id="940f3-109">식 구문과 지원되는 리터럴 및 식별자에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="940f3-109">For more information about the expression syntax and supported literals and identifiers, see the following topics.</span></span>  
  
-   [<span data-ttu-id="940f3-110">구문&#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="940f3-110">Syntax &#40;SSIS&#41;</span></span>](syntax-ssis.md)  
  
-   [<span data-ttu-id="940f3-111">리터럴&#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="940f3-111">Literals &#40;SSIS&#41;</span></span>](numeric-string-and-boolean-literals.md)  
  
-   [<span data-ttu-id="940f3-112">식별자&#40;SSIS&#41;</span><span class="sxs-lookup"><span data-stu-id="940f3-112">Identifiers &#40;SSIS&#41;</span></span>](identifiers-ssis.md)  
  
## <a name="components-that-use-expressions"></a><span data-ttu-id="940f3-113">식을 사용하는 구성 요소</span><span class="sxs-lookup"><span data-stu-id="940f3-113">Components that Use Expressions</span></span>  
 <span data-ttu-id="940f3-114">식을 사용할 수 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-114">The following elements in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] can use expressions:</span></span>  
  
-   <span data-ttu-id="940f3-115">식을 기반으로 데이터 행을 여러 대상으로 보내는 결정 구조를 구현하는 조건부 분할 변환.</span><span class="sxs-lookup"><span data-stu-id="940f3-115">The Conditional Split transformation implements a decision structure based on expressions to direct data rows to different destinations.</span></span> <span data-ttu-id="940f3-116">조건부 분할 변환에 사용된 식은 `true` 또는 `false`로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-116">Expressions used in a Conditional Split transformation must evaluate to `true` or `false`.</span></span> <span data-ttu-id="940f3-117">예를 들어 "Column1 > Column2" 식의 조건에 맞는 행을 별도의 출력으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-117">For example, rows that meet the condition in the expression "Column1 > Column2" can be routed to a separate output.</span></span>  
  
-   <span data-ttu-id="940f3-118">식에서 생성한 값을 사용하여 데이터 흐름에 새 열을 채우거나 기존 열을 업데이트하는 파생 열 변환.</span><span class="sxs-lookup"><span data-stu-id="940f3-118">The Derived Column transformation uses values created by using expressions either to populate new columns in a data flow, or to update existing columns.</span></span> <span data-ttu-id="940f3-119">예를 들어 Column1 + " ABC" 식은 값을 업데이트하거나 연결 문자열을 포함하는 새 값을 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-119">For example, the expression Column1 + " ABC" can be used to update a value or to create a new value with the concatenated string.</span></span>  
  
-   <span data-ttu-id="940f3-120">식을 사용하여 값이 설정되는 변수.</span><span class="sxs-lookup"><span data-stu-id="940f3-120">Variables use an expression to set their value.</span></span> <span data-ttu-id="940f3-121">예를 들어 GETDATE()는 변수의 값을 현재 날짜로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-121">For example, GETDATE() sets the value of the variable to the current date.</span></span>  
  
-   <span data-ttu-id="940f3-122">식을 사용하여 패키지에서 제약된 태스크 또는 컨테이너의 실행 여부를 결정을 위한 조건을 지정하는 선행 제약 조건.</span><span class="sxs-lookup"><span data-stu-id="940f3-122">Precedence constraints can use expressions to specify the conditions that determine whether the constrained task or container in a package runs.</span></span> <span data-ttu-id="940f3-123">선행 제약 조건에 사용된 식은 `true` 또는 `false`로 계산 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-123">Expressions used in a precedence constraint must evaluate to `true` or `false`.</span></span> <span data-ttu-id="940f3-124">예를 들어 \@A > \@B 식은 두 개의 사용자 정의 변수를 비교하여 제약된 태스크를 실행할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-124">For example, the expression \@A > \@B compares two user-defined variables to determine whether the constrained task runs.</span></span>  
  
-   <span data-ttu-id="940f3-125">식을 사용하여 루프 구조의 초기값, 비교값 및 증가값 문을 작성하는 For Loop 컨테이너.</span><span class="sxs-lookup"><span data-stu-id="940f3-125">The For Loop container can use expressions to build the initialization, evaluation, and the incrementing statements that the looping structure uses.</span></span> <span data-ttu-id="940f3-126">예를 들어 \@Counter = 1 식은 루프 카운터를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-126">For example, the expression \@Counter = 1 initializes the loop counter.</span></span>  
  
 <span data-ttu-id="940f3-127">또한 패키지의 속성 값, For Loop 및 Foreach Loop와 같은 컨테이너, 태스크, 패키지 및 프로젝트 수준의 연결 관리자, 로그 공급자, Foreach 열거자를 업데이트하는 데 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-127">Expressions can also be used to update the values of properties of packages, containers such as the For Loop and Foreach Loop, tasks, package and project level connection managers, log providers, and Foreach enumerators.</span></span> <span data-ttu-id="940f3-128">예를 들어 속성 식을 사용하여 "Localhost.AdventureWorks" 문자열을 SQL 실행 태스크의 ConnectionName 속성에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-128">For example, using a property expression, the string "Localhost.AdventureWorks" can be assigned to the ConnectionName property of the Execute SQL task.</span></span> <span data-ttu-id="940f3-129">자세한 내용은 [패키지에서 속성 식 사용](use-property-expressions-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="940f3-129">For more information, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
## <a name="icon-markers-for-expressions"></a><span data-ttu-id="940f3-130">식에 대한 아이콘 표식</span><span class="sxs-lookup"><span data-stu-id="940f3-130">Icon Markers for Expressions</span></span>  
 <span data-ttu-id="940f3-131">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 식이 설정되어 있는 태스크, 연결 관리자 및 변수 옆에 특수 아이콘 표식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-131">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], a special icon marker displays next to connection managers, variables, and tasks that have expressions set on them.</span></span> <span data-ttu-id="940f3-132">**HasExpressions** 속성은 변수를 제외하고 식을 지원하는 모든 SSIS 개체에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-132">The **HasExpressions** property is available on all SSIS objects that support expresions, with the exception of variables.</span></span> <span data-ttu-id="940f3-133">이 속성을 사용하면 식이 있는 개체를 쉽게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-133">The property enables you to easily identy which objects have expressions.</span></span>  
  
## <a name="expression-builder"></a><span data-ttu-id="940f3-134">식 작성기</span><span class="sxs-lookup"><span data-stu-id="940f3-134">Expression Builder</span></span>  
 <span data-ttu-id="940f3-135">식 작성기는 식을 작성하는 그래픽 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-135">The expression builder is a graphical tool for building expressions.</span></span> <span data-ttu-id="940f3-136">**조건부 분할 변환 편집기**, **파생 열 변환 편집기** 대화 상자, **식 작성기** 대화 상자에서 사용할 수 있는 식 작성기는 식을 작성하는 그래픽 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-136">It is available in the **Conditional Split Transformation Editor**, **Derived Column Transformation Editor** dialog boxes, and in the **Expression Builder** dialog box, is a graphical tool for building expressions.</span></span>  
  
 <span data-ttu-id="940f3-137">식 작성기는 패키지 관련 요소를 포함하는 폴더, 함수를 포함하는 폴더, 유형 변환 및 식 언어가 제공하는 연산자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-137">The expression builder provides folders that contain package-specific elements, and folders that contain the functions, type casts, and operators that the expression language provides.</span></span> <span data-ttu-id="940f3-138">패키지 관련 요소에는 시스템 변수 및 사용자 정의 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-138">The package-specific elements include system variables and user-defined variables.</span></span> <span data-ttu-id="940f3-139">**조건부 분할 변환 편집기** 및 **파생 열 변환 편집기** 대화 상자에도 데이터 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-139">In the **Conditional Split Transformation Editor** and **Derived Column Transformation Editor** dialog boxes, you can also view data columns.</span></span> <span data-ttu-id="940f3-140">변환을 위한 식을 작성하기 위해 항목을 폴더에서 **조건** 또는 **식** 열로 끌어다 놓거나 해당 열에 직접 식을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-140">To build expressions for the transformations, you can drag items from the folders to the **Condition** or **Expression** column or you can type the expression directly in the column.</span></span> <span data-ttu-id="940f3-141">식 작성기가 변수 이름의 \@ 접두사와 같은 필요한 구문 요소를 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-141">The expression builder automatically adds needed syntax elements such as the \@ prefix on variable names.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="940f3-142">사용자 정의 변수 및 시스템 변수의 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-142">The names of user-defined and system variables are case-sensitive.</span></span>  
  
 <span data-ttu-id="940f3-143">변수에는 범위가 있으며 식 작성기의 **변수** 폴더에는 범위 내에 있고 사용할 수 있는 변수만 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="940f3-143">Variables have scope, and the **Variables** folder in the expression builder lists only variables that are in scope and available to use.</span></span> <span data-ttu-id="940f3-144">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="940f3-144">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="940f3-145">관련 작업</span><span class="sxs-lookup"><span data-stu-id="940f3-145">Related Tasks</span></span>  
 [<span data-ttu-id="940f3-146">데이터 흐름 구성 요소에서 식 사용</span><span class="sxs-lookup"><span data-stu-id="940f3-146">Use an Expression in a Data Flow Component</span></span>](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="940f3-147">관련 내용</span><span class="sxs-lookup"><span data-stu-id="940f3-147">Related Content</span></span>  
 <span data-ttu-id="940f3-148">social.technet.microsoft.com의 기술 문서 - [SSIS 식 예](https://go.microsoft.com/fwlink/?LinkId=220761)</span><span class="sxs-lookup"><span data-stu-id="940f3-148">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="940f3-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="940f3-149">See Also</span></span>  
 [<span data-ttu-id="940f3-150">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="940f3-150">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
