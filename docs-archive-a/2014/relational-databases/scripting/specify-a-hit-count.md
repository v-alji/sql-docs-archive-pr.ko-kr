---
title: 적중 횟수 지정
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.hitcount
helpviewer_keywords:
- Transact-SQL debugger, breakpoint hit count
ms.assetid: 24836939-94ed-4e57-aa85-5d6938d859e4
author: rothja
ms.author: jroth
ms.openlocfilehash: 34c75e990bce1ea5e64c0b45f7acbcaa52fc3c40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653264"
---
# <a name="specify-a-hit-count"></a><span data-ttu-id="cc448-102">적중 횟수 지정</span><span class="sxs-lookup"><span data-stu-id="cc448-102">Specify a Hit Count</span></span>
  <span data-ttu-id="cc448-103">중단점 적중 횟수는 중단점에 도달할 때마다 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거가 증가시키는 카운터입니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-103">A breakpoint hit count is a counter that is incremented by the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger each time the breakpoint is reached.</span></span> <span data-ttu-id="cc448-104">지정한 적중 횟수에 도달하고 지정한 중단 조건을 만족하면 디버거는 해당 중단점에 대해 지정된 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-104">If the specified hit count is reached and any specified breakpoint condition is satisfied, the debugger performs the action specified for the breakpoint.</span></span>  
  
## <a name="hit-count-considerations"></a><span data-ttu-id="cc448-105">적중 횟수 고려 사항</span><span class="sxs-lookup"><span data-stu-id="cc448-105">Hit Count Considerations</span></span>  
 <span data-ttu-id="cc448-106">기본적으로 중단점에 도달할 때마다 실행이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-106">By default, execution breaks every time a breakpoint is hit.</span></span> <span data-ttu-id="cc448-107">다음 옵션 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-107">You can choose between the following options:</span></span>  
  
-   <span data-ttu-id="cc448-108">항상 중단(기본값)</span><span class="sxs-lookup"><span data-stu-id="cc448-108">Break always (the default).</span></span>  
  
-   <span data-ttu-id="cc448-109">적중 횟수가 지정한 값과 같으면 중단</span><span class="sxs-lookup"><span data-stu-id="cc448-109">Break when the hit count equals a specified value.</span></span>  
  
-   <span data-ttu-id="cc448-110">적중 횟수가 지정한 값의 배이면 중단</span><span class="sxs-lookup"><span data-stu-id="cc448-110">Break when the hit count equals a multiple of a specified value.</span></span>  
  
-   <span data-ttu-id="cc448-111">적중 횟수가 지정한 값보다 크거나 같으면 중단</span><span class="sxs-lookup"><span data-stu-id="cc448-111">Break when the hit count is greater than or equal to a specified value.</span></span>  
  
 <span data-ttu-id="cc448-112">중단점 적중 횟수는 디버깅 세션의 범위 내에서 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-112">Breakpoint hit counts are incremented within the scope of a debugging session.</span></span> <span data-ttu-id="cc448-113">모든 적중 횟수는 각 디버깅 세션이 시작될 때 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-113">All hit counts are set to zero at the start of each debugging session.</span></span>  
  
 <span data-ttu-id="cc448-114">중단점 중단을 실행하지 않고 중단점 적중 횟수를 추적하려면 중단점이 중단되지 않도록 적중 횟수를 매우 높은 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-114">If you want to track how many times a breakpoint is hit without having the breakpoint break execution, specify a hit count with a very high value so the breakpoint never breaks.</span></span>  
  
 <span data-ttu-id="cc448-115">중단점의 기본 동작은 적중 횟수와 중단점 조건을 모두 만족하면 실행을 중단하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-115">The default action for a breakpoint is to break execution when both the hit count and breakpoint condition have been satisfied.</span></span> <span data-ttu-id="cc448-116">다른 동작을 지정하는 방법은 [중단점 동작 지정](specify-a-breakpoint-action.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cc448-116">For information about specifying other actions, see [Specify a Breakpoint Action](specify-a-breakpoint-action.md).</span></span>  
  
#### <a name="to-specify-a-hit-count"></a><span data-ttu-id="cc448-117">적중 횟수를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="cc448-117">To Specify a Hit Count</span></span>  
  
1.  <span data-ttu-id="cc448-118">편집기 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **적중 횟수** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-118">In the editor window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="cc448-119">또는</span><span class="sxs-lookup"><span data-stu-id="cc448-119">-or-</span></span>  
  
     <span data-ttu-id="cc448-120">**중단점** 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **적중 횟수** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-120">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="cc448-121">**중단점 적중 횟수** 대화 상자의 **중단점이 적중될 때** 상자에서 원하는 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-121">In the **Breakpoint Hit Count** dialog box, select the behavior you want from the **When the breakpoint is hit** box.</span></span>  
  
     <span data-ttu-id="cc448-122">**항상 중단**이 아닌 다른 설정을 선택하면 목록 오른쪽에 입력란이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-122">If you choose any setting other than **Break Always**, a text box appears to the right of the list.</span></span> <span data-ttu-id="cc448-123">이 입력란에 정수를 입력하여 원하는 적중 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-123">Enter an integer in the text box to specify the hit count you want.</span></span>  
  
3.  <span data-ttu-id="cc448-124">**확인** 을 클릭하여 변경 내용을 구현하거나 **취소** 를 클릭하여 변경 내용을 적용하지 않고 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-124">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
#### <a name="to-view-or-reset-the-current-hit-count"></a><span data-ttu-id="cc448-125">현재 적중 횟수를 보거나 다시 설정하려면</span><span class="sxs-lookup"><span data-stu-id="cc448-125">To View or Reset the Current Hit Count</span></span>  
  
1.  <span data-ttu-id="cc448-126">편집기 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **적중 횟수** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-126">In the editor window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="cc448-127">또는</span><span class="sxs-lookup"><span data-stu-id="cc448-127">-or-</span></span>  
  
     <span data-ttu-id="cc448-128">**중단점** 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **적중 횟수** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-128">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="cc448-129">**중단점 적중 횟수** 대화 상자의 **다시 설정** 단추 바로 위에 **현재 적중 횟수:** 가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-129">In the **Breakpoint Hit Count** dialog box, the **Current hit count:** is displayed just above the **Reset** button.</span></span>  
  
3.  <span data-ttu-id="cc448-130">현재 적중 횟수를 0으로 설정하려면 **다시 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-130">Click **Reset** if you want to set the current hit count to zero.</span></span>  
  
4.  <span data-ttu-id="cc448-131">**확인** 이나 **취소** 를 클릭하여 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="cc448-131">Click **OK** or **Cancel** to exit the dialog.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc448-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cc448-132">See Also</span></span>  
 [<span data-ttu-id="cc448-133">중단점 조건 지정</span><span class="sxs-lookup"><span data-stu-id="cc448-133">Specify a Breakpoint Condition</span></span>](specify-a-breakpoint-condition.md)  
  
  
