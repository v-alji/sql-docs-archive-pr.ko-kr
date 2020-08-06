---
title: 속성 식 추가 또는 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- expressions [Integration Services], creating
- expressions [Integration Services], property expressions
ms.assetid: cb5da499-065f-4fa6-9f6d-5bc5f385241e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d6d12fbe46930818af2b47b59620963d39616e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652974"
---
# <a name="add-or-change-a-property-expression"></a><span data-ttu-id="4e495-102">속성 식 추가 또는 변경</span><span class="sxs-lookup"><span data-stu-id="4e495-102">Add or Change a Property Expression</span></span>
  <span data-ttu-id="4e495-103">패키지, 태스크, Foreach 루프 컨테이너, For 루프 컨테이너, 시퀀스 컨테이너, 이벤트 처리기, 패키지 및 프로젝트 수준의 연결 관리자 및 로그 공급자에 속성 식을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-103">You can create property expressions for packages, tasks, Foreach Loop containers, For Loop containers, Sequence containers, event handlers, package and project level connection managers, and log providers.</span></span>  
  
 <span data-ttu-id="4e495-104">속성 식을 만들거나 변경하려면 **속성 식 편집기** 또는 **식 작성기**를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-104">To create or change property expressions, you can use either the **Property Expressions Editor** or **Expression Builder**.</span></span> <span data-ttu-id="4e495-105">**속성 식 편집기** 는 태스크와 컨테이너에 사용할 수 있는 사용자 지정 편집기나 **속성** 창에서 액세스할 수 있고,</span><span class="sxs-lookup"><span data-stu-id="4e495-105">The **Property Expressions Editor** can be accessed from either the custom editors that are available for tasks and containers, or from the **Properties** window.</span></span> <span data-ttu-id="4e495-106">**식 작성기** 는 **속성 식 편집기**내에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-106">**Expression Builder** can be accessed from inside the **Property Expressions Editor**.</span></span> <span data-ttu-id="4e495-107">**속성 식 편집기** 와 **식 작성기**모두에서 식을 작성할 수 있지만 **식 작성기** 에서는 복잡한 식을 간단하게 작성할 수 있게 해주는 그래픽 도구 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-107">While you can write expressions in either the **Property Expressions Editor** or **Expression Builder**, **Expression Builder** provides a graphical set of tools that makes it simple to build complex expressions.</span></span>  
  
 <span data-ttu-id="4e495-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 제공하는 구문, 연산자 및 함수에 대한 자세한 내용은 [연산자&#40;SSIS 식&#41;](operators-ssis-expression.md) 및 [함수&#40;SSIS 식&#41;](functions-ssis-expression.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e495-108">To learn more about the syntax, operators, and functions that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides, see [Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) and [Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md).</span></span> <span data-ttu-id="4e495-109">각 연산자 또는 함수에 대한 항목에는 식에 해당 연산자나 함수를 사용하는 예가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-109">The topic for each operator or function includes examples of using that operator or function in an expression.</span></span> <span data-ttu-id="4e495-110">더 복잡한 식의 예는 [패키지에서 속성 식 사용](use-property-expressions-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e495-110">For examples of more complex expressions, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
### <a name="to-create-or-change-a-property-expression"></a><span data-ttu-id="4e495-111">속성 식을 만들거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="4e495-111">To create or change a property expression</span></span>  
  
1.  <span data-ttu-id="4e495-112">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지가 들어 있는 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project that contains the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="4e495-113">솔루션 탐색기에서 패키지를 두 번 클릭하여 열고 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-113">In Solution Explorer, double-click the package to open it, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="4e495-114">항목이 태스크 또는 컨테이너인 경우 항목을 두 번 클릭한 다음 편집기에서 **식** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-114">If the item is a task or a container, double-click the item, and then click **Expressions** in the editor.</span></span>  
  
    -   <span data-ttu-id="4e495-115">항목을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-115">Right-click the item and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4e495-116">**식** 상자를 클릭한 다음, 줄임표(...)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-116">Click in the **Expressions** box and then click the ellipsis (...).</span></span>  
  
4.  <span data-ttu-id="4e495-117">**속성 식 편집기**에서 **속성** 목록의 속성을 선택하고 다음 중 하나를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="4e495-117">In the **Property Expressions Editor**, select a property in the **Property** list, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="4e495-118">**식** 열에서 속성 식을 직접 입력하거나 변경한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-118">Type or change the property expression directly in the **Expression** column, and then click **OK**.</span></span>  
  
         <span data-ttu-id="4e495-119">또는</span><span class="sxs-lookup"><span data-stu-id="4e495-119">-or-</span></span>  
  
    -   <span data-ttu-id="4e495-120">속성의 식 행에서 줄임표(...)를 클릭하여 **식 작성기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-120">Click the ellipsis (...) in the expression row of the property to open the **Expression Builder**.</span></span>  
  
5.  <span data-ttu-id="4e495-121">(옵션) **식 작성기**에서 다음 태스크 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-121">(Optional) In the **Expression Builder**, do any of the following tasks:</span></span>  
  
    -   <span data-ttu-id="4e495-122">사용자 정의 변수에 액세스하려면 **변수**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-122">To access system and user-defined variables, expand **Variables**.</span></span>  
  
    -   <span data-ttu-id="4e495-123">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 식 언어가 제공하는 함수, 캐스트 및 연산자에 액세스하려면 **수치 연산 함수**, **문자열 함수**, **날짜/시간 함수**, **NULL 함수**, **형식 캐스팅**및 **연산자**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-123">To access the functions, the casts, and the operators that the [!INCLUDE[ssIS](../../includes/ssis-md.md)] expression language provides, expand **Mathematical Functions**, **String Functions**, **Date/Time Functions**, **NULL Functions**, **Type Casts**, and **Operators**.</span></span>  
  
    -   <span data-ttu-id="4e495-124">**식 작성기**에서 식을 작성하거나 변경하려면 변수, 열, 함수, 연산자 및 캐스트를 **식** 입력란으로 끌어 놓거나 이 입력란에 식을 직접 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-124">To build or change an expression in the **Expression Builder**, drag variables, columns, functions, operators, and casts to the **Expression** box, or type the expression in the box.</span></span>  
  
    -   <span data-ttu-id="4e495-125">식의 계산 결과를 보려면 **식 작성기** 에서 **식 계산**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-125">To view the evaluation result of the expression, click **Evaluate Expression** in the **Expression Builder**.</span></span>  
  
         <span data-ttu-id="4e495-126">식이 유효하지 않으면 식의 구문 오류를 설명하는 경고가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-126">If the expression is not valid, an alert appears that describes the syntax errors in the expression.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="4e495-127">식 계산은 계산 결과를 속성에 할당하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e495-127">Evaluating an expression does not assign the evaluation result to the property.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e495-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e495-128">See Also</span></span>  
 <span data-ttu-id="4e495-129">[Integration Services&#40;SSIS&#41; 식](integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="4e495-129">[Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="4e495-130">[패키지에서 속성 식 사용](use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="4e495-130">[Use Property Expressions in Packages](use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="4e495-131">[Integration Services&#40;SSIS&#41; 패키지](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="4e495-131">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 <span data-ttu-id="4e495-132">[Integration Services 컨테이너](../control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="4e495-132">[Integration Services Containers](../control-flow/integration-services-containers.md) </span></span>  
 <span data-ttu-id="4e495-133">[Integration Services 태스크](../control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="4e495-133">[Integration Services Tasks](../control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="4e495-134">[Integration Services&#40;SSIS&#41; 이벤트 처리기](../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="4e495-134">[Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md) </span></span>  
 <span data-ttu-id="4e495-135">[Integration Services&#40;SSIS&#41; 연결](../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="4e495-135">[Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="4e495-136">Integration Services&#40;SSIS&#41; 로깅</span><span class="sxs-lookup"><span data-stu-id="4e495-136">Integration Services &#40;SSIS&#41; Logging</span></span>](../performance/integration-services-ssis-logging.md)  
  
  
