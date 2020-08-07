---
title: 중단점 조건 지정
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 659b6ca1149eb8f0412efbe2adbaf4c1ffce59d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733840"
---
# <a name="specify-a-breakpoint-condition"></a><span data-ttu-id="e1eee-102">중단점 조건 지정</span><span class="sxs-lookup"><span data-stu-id="e1eee-102">Specify a Breakpoint Condition</span></span>
  <span data-ttu-id="e1eee-103">중단점 조건은 중단점에 도달할 때마다 디버거가 평가하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 식입니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-103">A breakpoint condition is a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression that is evaluated by the debugger when the breakpoint is reached.</span></span> <span data-ttu-id="e1eee-104">지정한 조건을 만족하고 지정한 적중 횟수에 도달하면 디버거는 중단점에 대해 지정된 동작을 중단하거나 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-104">If the condition is satisfied and any specified hit count reached, the debugger either breaks or performs the action specified for the breakpoint.</span></span>  
  
## <a name="specifying-conditions"></a><span data-ttu-id="e1eee-105">조건 지정</span><span class="sxs-lookup"><span data-stu-id="e1eee-105">Specifying Conditions</span></span>  
 <span data-ttu-id="e1eee-106">부울 값으로 평가되는 올바른 Transact-SQL 식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-106">The expression specified must be a valid Transact-SQL expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="e1eee-107">자세한 내용은 [식&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e1eee-107">For more information, see [Expressions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql).</span></span>  
  
 <span data-ttu-id="e1eee-108">올바르지 않은 구문을 사용하여 중단점 조건을 지정하면 즉시 경고 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-108">If you specify a breakpoint condition with invalid syntax, a warning message appears immediately.</span></span> <span data-ttu-id="e1eee-109">구문은 올바르지만 의미 체계가 올바르지 않은 조건을 지정하면 처음 중단점에 도달할 때 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-109">If you specify a condition with valid syntax but invalid semantics, a warning message is displayed the first time the breakpoint is hit.</span></span> <span data-ttu-id="e1eee-110">두 경우 모두 올바르지 않은 중단점에 도달하면 디버거가 실행을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-110">In either case, the debugger breaks execution when the invalid breakpoint is hit.</span></span>  
  
#### <a name="to-specify-a-condition"></a><span data-ttu-id="e1eee-111">조건을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="e1eee-111">To Specify a Condition</span></span>  
  
1.  <span data-ttu-id="e1eee-112">편집기 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **조건** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-112">In the editor window, right-click the breakpoint glyph, and then click **Condition** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="e1eee-113">또는</span><span class="sxs-lookup"><span data-stu-id="e1eee-113">-or-</span></span>  
  
     <span data-ttu-id="e1eee-114">**중단점** 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **조건** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-114">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Condition** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e1eee-115">**중단점 조건** 대화 상자에서 **조건** 상자에 올바른 부울 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-115">In the **Breakpoint Condition** dialog box, enter a valid Boolean expression in the **Condition** box.</span></span>  
  
3.  <span data-ttu-id="e1eee-116">식이로 계산 될 때 중단 하려면 **true** 를 선택 하 고 `true` , 식의 값이 변경 될 때 중단 하려면 **변경 된** 경우를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-116">Choose **Is true** if you want to break when the expression evaluates to `true`, or choose **Has changed** if you want to break when the value of the expression has changed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1eee-117">중단점에 처음 도달할 때까지 디버거는 부울 식을 평가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-117">The debugger does not evaluate the Boolean expression until the first time the breakpoint is reached.</span></span> <span data-ttu-id="e1eee-118">**이(가) 변경된 경우**를 선택한 경우 디버거는 첫 번째 평가를 변경으로 간주하지 않으므로 첫 번째 평가 시에는 중단하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1eee-118">If you choose **Has changed**, the debugger does not consider the first evaluation to be a change, so the debugger will not break on the first evaluation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1eee-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1eee-119">See Also</span></span>  
 <span data-ttu-id="e1eee-120">[적중 횟수 지정](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="e1eee-120">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 [<span data-ttu-id="e1eee-121">중단점 동작 지정</span><span class="sxs-lookup"><span data-stu-id="e1eee-121">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)  
