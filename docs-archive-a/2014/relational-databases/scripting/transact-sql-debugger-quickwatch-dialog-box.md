---
title: 간략한 조사식 대화 상자
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.quickwatch
helpviewer_keywords:
- QuickWatch Dialog [Transact-SQL]
ms.assetid: d6bbb373-1452-41f2-bdc5-86ae689c3dc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 48e4bda558b75bec0c81815c90feff9d6500a803
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660467"
---
# <a name="quickwatch-dialog-box"></a><span data-ttu-id="f2110-102">간략한 조사식 대화 상자</span><span class="sxs-lookup"><span data-stu-id="f2110-102">QuickWatch Dialog Box</span></span>
  <span data-ttu-id="f2110-103">**간략한 조사식** 대화 상자를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 디버깅할 때 변수나 매개 변수와 같은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 식의 데이터 형식 및 값을 빨리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-103">Use the **QuickWatch** dialog box to quickly view the data type and value of one [!INCLUDE[tsql](../../includes/tsql-md.md)] expression, such as a variable or parameter, when you are debugging [!INCLUDE[tsql](../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="f2110-104">**조사식** 창에 식을 추가하여 여러 식을 조사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-104">To watch multiple expressions, you can also add the expression to a **Watch** window.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="f2110-105">작업 목록</span><span class="sxs-lookup"><span data-stu-id="f2110-105">Task List</span></span>  
 <span data-ttu-id="f2110-106">**간략한 조사식 대화 상자에 액세스하려면**</span><span class="sxs-lookup"><span data-stu-id="f2110-106">**To access the QuickWatch dialog box**</span></span>  
  
-   <span data-ttu-id="f2110-107">**디버그** 메뉴에서 **간략한 조사식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-107">On the **Debug** menu, click **QuickWatch**.</span></span>  
  
 <span data-ttu-id="f2110-108">**식에 대한 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="f2110-108">**To view the information about an expression**</span></span>  
  
1.  <span data-ttu-id="f2110-109">**식** 목록 상자에서 원하는 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-109">In the **Expression** list box, type or select the expression that you want.</span></span> <span data-ttu-id="f2110-110">다음의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-110">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] expressions are supported:</span></span>  
  
    -   <span data-ttu-id="f2110-111">변수</span><span class="sxs-lookup"><span data-stu-id="f2110-111">Variables.</span></span>  
  
    -   <span data-ttu-id="f2110-112">매개 변수.</span><span class="sxs-lookup"><span data-stu-id="f2110-112">Parameters.</span></span>  
  
    -   <span data-ttu-id="f2110-113">이름이 @@로 시작하는 시스템 함수</span><span class="sxs-lookup"><span data-stu-id="f2110-113">System functions whose name starts with @@.</span></span>  
  
    -   <span data-ttu-id="f2110-114">@IntegerCounter + 1 또는 FirstName + LastName과 같이 하나 이상의 변수, 매개 변수 또는 시스템 함수에 연산자를 적용하여 빌드한 식</span><span class="sxs-lookup"><span data-stu-id="f2110-114">Expressions built by applying operators to one or more variables, parameters, or system functions, such as @IntegerCounter + 1, or FirstName + LastName.</span></span>  
  
    -   <span data-ttu-id="f2110-115">SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1 등의 단일 값을 반환하는 Transact-SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-115">Transact-SQL statements that return a single value, such as: SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
2.  <span data-ttu-id="f2110-116">**다시 계산**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-116">Click **Reevaluate**.</span></span>  
  
 <span data-ttu-id="f2110-117">**조사식 창에 간략한 조사식을 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="f2110-117">**To add the QuickWatch expression to a Watch window**</span></span>  
  
-   <span data-ttu-id="f2110-118">**조사식 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-118">Click **Add Watch**.</span></span>  
  
 <span data-ttu-id="f2110-119">**간략한 조사식 값을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="f2110-119">**To change the value of the QuickWatch expression**</span></span>  
  
-   <span data-ttu-id="f2110-120">식을 마우스 오른쪽 단추로 클릭하고 **값 편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-120">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f2110-121">옵션</span><span class="sxs-lookup"><span data-stu-id="f2110-121">Options</span></span>  
 <span data-ttu-id="f2110-122">**식 목록**</span><span class="sxs-lookup"><span data-stu-id="f2110-122">**Expression list**</span></span>  
 <span data-ttu-id="f2110-123">현재 선택한 식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-123">Displays the currently selected expression.</span></span> <span data-ttu-id="f2110-124">드롭다운 목록에는 표시하도록 선택할 수 있는 식 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-124">The drop-down list contains a set of expressions that you can select to display.</span></span> <span data-ttu-id="f2110-125">목록에 있는 식은 현재 **호출 스택** 창에서 선택한 스택 프레임 범위에서 사용할 수 있는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-125">The expressions in the list are those available in the scope of the stack frame that is currently selected in the **Call Stack** window.</span></span> <span data-ttu-id="f2110-126">다른 식을 표시하려면 식을 입력하거나 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-126">To display a different expression, either enter the expression or select it from list.</span></span> <span data-ttu-id="f2110-127">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거는 변수, 매개 변수 및 @@ 기호로 시작하는 시스템 함수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-127">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger supports the following expressions: variables, parameters, and the system functions that have names that start with @@.</span></span>  
  
 <span data-ttu-id="f2110-128">**값 표**</span><span class="sxs-lookup"><span data-stu-id="f2110-128">**Value grid**</span></span>  
 <span data-ttu-id="f2110-129">현재 조사 중인 식의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-129">Displays the properties of the expression that is currently being watched.</span></span>  
  
 <span data-ttu-id="f2110-130">**이름**</span><span class="sxs-lookup"><span data-stu-id="f2110-130">**Name**</span></span>  
 <span data-ttu-id="f2110-131">조사 중인 [!INCLUDE[tsql](../../includes/tsql-md.md)] 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-131">Is the [!INCLUDE[tsql](../../includes/tsql-md.md)] expression being watched.</span></span>  
  
 <span data-ttu-id="f2110-132">**값**</span><span class="sxs-lookup"><span data-stu-id="f2110-132">**Value**</span></span>  
 <span data-ttu-id="f2110-133">현재 식에 할당된 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-133">Displays the value that is currently assigned to the expression.</span></span> <span data-ttu-id="f2110-134">현재 식에 값이 없으면 빈 상태로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-134">A blank is displayed when the expression currently has no value.</span></span>  
  
 <span data-ttu-id="f2110-135">식의 길이가 **값** 열의 너비보다 큰 경우 해당 식의 **값** 셀 위로 포인터를 움직이면 도구 설명에 전체 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-135">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="f2110-136">**디버거 시각화 도우미를 사용할 수 있는 경우** 값 [!INCLUDE[tsql](../../includes/tsql-md.md)] 셀에 돋보기 모양의 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-136">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="f2110-137">목록에서 **텍스트 시각화 도우미**, **XML 시각화 도우미**또는 **HTML 시각화 도우미**중에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-137">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="f2110-138">디버거 시각화 도우미를 시작하려면 돋보기 모양의 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-138">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="f2110-139">그러면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서 데이터 형식에 적합한 형식으로 데이터를 표시하는 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-139">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog box that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="f2110-140">**형식**</span><span class="sxs-lookup"><span data-stu-id="f2110-140">**Type**</span></span>  
 <span data-ttu-id="f2110-141">식의 데이터 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f2110-141">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2110-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2110-142">See Also</span></span>  
 <span data-ttu-id="f2110-143">[Transact-SQL 디버거](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="f2110-143">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="f2110-144">[Transact-SQL 디버거 정보](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="f2110-144">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="f2110-145">[조사식 창](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="f2110-145">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="f2110-146">[지역 창](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="f2110-146">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="f2110-147">[호출 스택 창](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="f2110-147">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 [<span data-ttu-id="f2110-148">식&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f2110-148">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
  
  
