---
title: 조사식 창
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Watch Window [Transact-SQL]
ms.assetid: 23f3baa4-14c2-4262-92f7-3f43fcfa0436
author: rothja
ms.author: jroth
ms.openlocfilehash: c2a3db9b095902fcb5620af91fb86d80f773d606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653257"
---
# <a name="watch-window"></a><span data-ttu-id="e1607-102">조사식 창</span><span class="sxs-lookup"><span data-stu-id="e1607-102">Watch Window</span></span>
  <span data-ttu-id="e1607-103">**조사식** 창은 선택한 식에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-103">The **Watch** window displays information about the expressions that you have selected.</span></span> <span data-ttu-id="e1607-104">**조사식 1**, **조사식 2, 조사식 3**및 **조사식 4**의 최대 4개의 창으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-104">There can be up to four watch windows: **Watch 1**, **Watch 2, Watch 3**, and **Watch 4**.</span></span> <span data-ttu-id="e1607-105">식은 **호출 스택** 창에서 선택한 현재 호출 스택 프레임 범위 내에서 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-105">The expressions are evaluated within the scope of the current call stack frame that is selected in the **Call Stack** window.</span></span> <span data-ttu-id="e1607-106">변수 및 식을 조사하려면 디버그 모드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-106">You must be in debug mode to watch variables and expressions.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="e1607-107">작업 목록</span><span class="sxs-lookup"><span data-stu-id="e1607-107">Task List</span></span>  
 <span data-ttu-id="e1607-108">**조사식 창에 액세스하려면**</span><span class="sxs-lookup"><span data-stu-id="e1607-108">**To access the Watch windows**</span></span>  
  
-   <span data-ttu-id="e1607-109">**디버그** 메뉴에서 **창**, **조사식**을 차례로 클릭하고 **조사식 1**, **조사식 2, 조사식 3**또는 **조사식 4**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-109">On the **Debug** menu, click **Windows**, click **Watch**, and then click **Watch 1**, **Watch 2, Watch 3**, or **Watch 4**.</span></span>  
  
 <span data-ttu-id="e1607-110">**식 값을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="e1607-110">**To change the value of an expression**</span></span>  
  
-   <span data-ttu-id="e1607-111">식을 마우스 오른쪽 단추로 클릭하고 **값 편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-111">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="e1607-112">열</span><span class="sxs-lookup"><span data-stu-id="e1607-112">Columns</span></span>  
 <span data-ttu-id="e1607-113">**이름**</span><span class="sxs-lookup"><span data-stu-id="e1607-113">**Name**</span></span>  
 <span data-ttu-id="e1607-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에 표시된 식입니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-114">Are the expressions that are listed by the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="e1607-115">지원되는 식은</span><span class="sxs-lookup"><span data-stu-id="e1607-115">The following expressions are supported:</span></span>  
  
-   <span data-ttu-id="e1607-116">변수</span><span class="sxs-lookup"><span data-stu-id="e1607-116">Variables.</span></span>  
  
-   <span data-ttu-id="e1607-117">매개 변수.</span><span class="sxs-lookup"><span data-stu-id="e1607-117">Parameters.</span></span>  
  
-   <span data-ttu-id="e1607-118">이름이 @@로 시작하는 시스템 함수</span><span class="sxs-lookup"><span data-stu-id="e1607-118">System functions whose name starts with @@.</span></span>  
  
-   <span data-ttu-id="e1607-119">@IntegerCounter + 1 또는 FirstName + LastName과 같이 하나 이상의 변수, 매개 변수 또는 시스템 함수에 연산자를 적용하여 빌드한 식</span><span class="sxs-lookup"><span data-stu-id="e1607-119">Expressions built by applying operators to one or more variables, parameters, or system functions, such as @IntegerCounter + 1, or FirstName + LastName.</span></span>  
  
-   <span data-ttu-id="e1607-120">SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1 등의 단일 값을 반환하는 Transact-SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-120">Transact-SQL statements that return a single value, such as: SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
 <span data-ttu-id="e1607-121">**값**</span><span class="sxs-lookup"><span data-stu-id="e1607-121">**Value**</span></span>  
 <span data-ttu-id="e1607-122">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서 **이름**에 지정된 식을 평가한 후 반환되는 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-122">Displays the value that is returned after the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger evaluates the expression specified in **Name**.</span></span>  
  
 <span data-ttu-id="e1607-123">식의 길이가 **값** 열의 너비보다 큰 경우 해당 식의 **값** 셀 위로 포인터를 움직이면 도구 설명에 전체 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-123">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="e1607-124">**디버거 시각화 도우미를 사용할 수 있는 경우** 값 [!INCLUDE[tsql](../../includes/tsql-md.md)] 셀에 돋보기 모양의 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-124">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="e1607-125">목록에서 **텍스트 시각화 도우미**, **XML 시각화 도우미**또는 **HTML 시각화 도우미**중에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-125">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="e1607-126">디버거 시각화 도우미를 시작하려면 돋보기 모양의 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-126">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="e1607-127">그러면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서 데이터 형식에 적합한 형식으로 데이터를 표시하는 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-127">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="e1607-128">**형식**</span><span class="sxs-lookup"><span data-stu-id="e1607-128">**Type**</span></span>  
 <span data-ttu-id="e1607-129">식의 데이터 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e1607-129">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1607-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1607-130">See Also</span></span>  
 <span data-ttu-id="e1607-131">[Transact-SQL 디버거](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="e1607-131">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="e1607-132">[Transact-SQL 디버거 정보](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="e1607-132">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="e1607-133">[지역 창](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="e1607-133">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="e1607-134">[호출 스택 창](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="e1607-134">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="e1607-135">[간략한 조사식 대화 상자](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="e1607-135">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 [<span data-ttu-id="e1607-136">식&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e1607-136">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
