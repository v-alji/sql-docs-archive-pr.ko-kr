---
title: 데이터 흐름 구성 요소에서 식 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], data flow
- expressions [Integration Services], data flow components
ms.assetid: 9181b998-d24a-41fb-bb3c-14eee34f910d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 653bf468d0af6d44c5abe7344fcc13f93f86b430
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734260"
---
# <a name="use-an-expression-in-a-data-flow-component"></a><span data-ttu-id="70e7f-102">데이터 흐름 구성 요소에서 식 사용</span><span class="sxs-lookup"><span data-stu-id="70e7f-102">Use an Expression in a Data Flow Component</span></span>
  <span data-ttu-id="70e7f-103">이 절차에서는 조건부 분할 변환 또는 파생 열 변환에 식을 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-103">This procedure describes how to add an expression to the Conditional Split transformation or to the Derived Column transformation.</span></span> <span data-ttu-id="70e7f-104">조건부 분할 변환에서는 데이터 행을 변환 출력으로 바꾸는 조건을 정의하는 데 식을 사용하며 파생 열 변환에서는 열에 할당된 값을 정의하는 데 식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-104">The Conditional Split transformation uses expressions to define the conditions that direct data rows to a transformation output, and the Derived Column transformation uses expressions to define values assigned to columns.</span></span>  
  
 <span data-ttu-id="70e7f-105">변환에서 식을 구현하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-105">To implement an expression in a transformation, the package must already include at least one Data Flow task and a source.</span></span> <span data-ttu-id="70e7f-106">패키지에 항목을 추가하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="70e7f-106">For information about adding items to packages, see the following topics:</span></span>  
  
-   [<span data-ttu-id="70e7f-107">제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="70e7f-107">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
    
  
-   [<span data-ttu-id="70e7f-108">데이터 흐름에서 구성 요소 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="70e7f-108">Add or Delete a Component in a Data Flow</span></span>](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
-   [<span data-ttu-id="70e7f-109">데이터 흐름의 구성 요소 연결</span><span class="sxs-lookup"><span data-stu-id="70e7f-109">Connect Components in a Data Flow</span></span>](data-flow/connect-components-in-a-data-flow.md)  
  
### <a name="to-create-an-expression"></a><span data-ttu-id="70e7f-110">식을 만들려면</span><span class="sxs-lookup"><span data-stu-id="70e7f-110">To create an expression</span></span>  
  
1.  <span data-ttu-id="70e7f-111">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-111">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="70e7f-112">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-112">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="70e7f-113">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **제어 흐름** 탭을 클릭하고 식을 구현할 데이터 흐름이 포함된 데이터 흐름 태스크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-113">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow** tab, and then click the Data Flow task that contains the data flow in which you want to implement an expression.</span></span>  
  
4.  <span data-ttu-id="70e7f-114">**데이터 흐름** 탭을 클릭하고 **도구 상자** 에서 조건부 분할 변환 또는 파생 열 변환을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-114">Click the **Data Flow** tab, and drag either a Conditional Split or Derived Column transformation from the **Toolbox** to the design surface.</span></span>  
  
5.  <span data-ttu-id="70e7f-115">원본 또는 변환의 녹색 연결선을 조건부 분할 변환 또는 파생 열 변환으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-115">Drag the green connector from the source or a transformation to the Conditional Split or Derived Column transformation.</span></span>  
  
6.  <span data-ttu-id="70e7f-116">변환을 두 번 클릭하여 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-116">Double-click the transformation to open its dialog box.</span></span>  
  
7.  <span data-ttu-id="70e7f-117">왼쪽 창에서 **변수** 를 확장하여 시스템 및 사용자 정의 변수를 표시하고 **열** 을 확장하여 변환 입력 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-117">In the left pane, expand **Variables** to display system and user-defined variables, and expand **Columns** to display the transformation input columns.</span></span>  
  
8.  <span data-ttu-id="70e7f-118">오른쪽 창에서 **수치 연산 함수**, **문자열 함수**, **날짜/시간 함수**, **NULL 함수**, **형식 캐스트**및 **연산자** 를 확장하여 식 문법이 제공하는 함수, 캐스트 및 연산자에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-118">In the right pane, expand **Mathematical Functions**, **String Functions**, **Date/Time Functions**, **NULL Functions**, **Type Casts**, and **Operators** to access the functions, the casts, and the operators that the expression grammar provides.</span></span>  
  
9. <span data-ttu-id="70e7f-119">변환에 따라 다음 중 하나를 수행하여 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-119">Depending on the transformation, do one of the following to build an expression:</span></span>  
  
    -   <span data-ttu-id="70e7f-120">**조건부 분할 변환 편집기** 대화 상자에서 변수, 열, 함수, 연산자 및 캐스트를 **조건** 열로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-120">In the **Conditional Split Transformation Editor** dialog box, drag variables, columns, functions, operators, and casts to the **Condition** column.</span></span> <span data-ttu-id="70e7f-121">또는 **조건** 열에 직접 식을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-121">Alternatively, you can type an expression directly in the **Condition** column.</span></span>  
  
    -   <span data-ttu-id="70e7f-122">**파생 열 변환 편집기** 대화 상자에서 변수, 열, 함수, 연산자 및 캐스트를 **식** 열로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-122">In the **Derived Column Transformation Editor** dialog box, drag variables, columns, functions, operators, and casts to the **Expression** column.</span></span> <span data-ttu-id="70e7f-123">또는 **식** 열에 직접 식을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-123">Alternatively, you can type an expression directly in the **Expression** column.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="70e7f-124">**조건** 열이나 **식** 열에서 포커스가 제거될 때 식 구문이 유효하지 않은 경우 식 텍스트가 강조 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-124">When you remove the focus from the **Condition** column or the **Expression** column, the expression text might be highlighted to indicate that the expression syntax is incorrect.</span></span>  
  
10. <span data-ttu-id="70e7f-125">**확인**을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-125">Click **OK** to exit the dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="70e7f-126">식이 유효하지 않으면 식의 구문 오류를 설명하는 경고가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="70e7f-126">If the expression is not valid, an alert appears describing the syntax errors in the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e7f-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70e7f-127">See Also</span></span>  
 <span data-ttu-id="70e7f-128">[Integration Services &#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="70e7f-128">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="70e7f-129">[조건부 분할 변환](data-flow/transformations/conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="70e7f-129">[Conditional Split Transformation](data-flow/transformations/conditional-split-transformation.md) </span></span>  
 <span data-ttu-id="70e7f-130">[Derived Column Transformation](data-flow/transformations/derived-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="70e7f-130">[Derived Column Transformation](data-flow/transformations/derived-column-transformation.md) </span></span>  
 <span data-ttu-id="70e7f-131">[데이터 흐름 태스크](control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="70e7f-131">[Data Flow Task](control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="70e7f-132">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="70e7f-132">Data Flow</span></span>](data-flow/data-flow.md)  
  
  
