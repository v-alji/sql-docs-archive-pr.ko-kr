---
title: 지역 창
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f8f62eb69a50d7543af41dddb9c62c842d17151
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660469"
---
# <a name="locals-window"></a><span data-ttu-id="857f6-102">지역 창</span><span class="sxs-lookup"><span data-stu-id="857f6-102">Locals Window</span></span>
  <span data-ttu-id="857f6-103">**지역** 창에는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거의 현재 범위에 있는 지역 식에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-103">The **Locals** window displays information about the local expressions in the current scope of the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="857f6-104">범위는 **호출 스택** 창에서 선택한 현재 호출 스택 프레임으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-104">The scope is set to the current call stack frame that is selected in the **Call Stack** window.</span></span> <span data-ttu-id="857f6-105">지역 식을 표시하려면 디버그 모드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-105">You must be in debug mode to display the local expressions.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="857f6-106">작업 목록</span><span class="sxs-lookup"><span data-stu-id="857f6-106">Task List</span></span>  
 <span data-ttu-id="857f6-107">**지역 창에 액세스하려면**</span><span class="sxs-lookup"><span data-stu-id="857f6-107">**To access the Locals window**</span></span>  
  
-   <span data-ttu-id="857f6-108">**디버그** 메뉴에서 **창**을 선택한 다음 **지역**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-108">On the **Debug** menu, click **Windows**, and then click **Locals**.</span></span>  
  
 <span data-ttu-id="857f6-109">**식 값을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="857f6-109">**To change the value of an expression**</span></span>  
  
-   <span data-ttu-id="857f6-110">식을 마우스 오른쪽 단추로 클릭하고 **값 편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-110">Right-click the expression, and then select **Edit Value**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="857f6-111">열</span><span class="sxs-lookup"><span data-stu-id="857f6-111">Columns</span></span>  
 <span data-ttu-id="857f6-112">**이름**</span><span class="sxs-lookup"><span data-stu-id="857f6-112">**Name**</span></span>  
 <span data-ttu-id="857f6-113">지역 식의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-113">Is the name of the local expression.</span></span> <span data-ttu-id="857f6-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거는 변수, 매개 변수 및 @@ 기호로 시작하는 시스템 함수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-114">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger lists variables, parameters, and the system functions that have names that start with @@.</span></span>  
  
 <span data-ttu-id="857f6-115">**값**</span><span class="sxs-lookup"><span data-stu-id="857f6-115">**Value**</span></span>  
 <span data-ttu-id="857f6-116">현재 지역 식에 할당된 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-116">Displays the value that is currently assigned to the local expression.</span></span> <span data-ttu-id="857f6-117">식에 할당된 값이 없으면 이 열은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-117">This column is blank when no value has been assigned to the expression.</span></span>  
  
 <span data-ttu-id="857f6-118">식의 길이가 **값** 열의 너비보다 큰 경우 해당 식의 **값** 셀 위로 포인터를 움직이면 도구 설명에 전체 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-118">If the length of an expression is larger than the width of the **Value** column, a tooltip displays the full value when you move the pointer over the **Value** cell for that expression.</span></span>  
  
 <span data-ttu-id="857f6-119">**디버거 시각화 도우미를 사용할 수 있는 경우** 값 [!INCLUDE[tsql](../../includes/tsql-md.md)] 셀에 돋보기 모양의 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-119">A magnifying glass icon in a **Value** cell indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger visualizer is available.</span></span> <span data-ttu-id="857f6-120">목록에서 **텍스트 시각화 도우미**, **XML 시각화 도우미**또는 **HTML 시각화 도우미**중에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-120">In the list, you can specify **Text Visualizer**, **XML Visualizer**, or **HTML Visualizer**.</span></span> <span data-ttu-id="857f6-121">디버거 시각화 도우미를 시작하려면 돋보기 모양의 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-121">To start a debugger visualizer, click the magnifying glass icon.</span></span> <span data-ttu-id="857f6-122">그러면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 디버거에서 데이터 형식에 적합한 형식으로 데이터를 표시하는 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-122">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger opens a dialog box that displays the data in a format appropriate to the data type.</span></span>  
  
 <span data-ttu-id="857f6-123">**형식**</span><span class="sxs-lookup"><span data-stu-id="857f6-123">**Type**</span></span>  
 <span data-ttu-id="857f6-124">식의 데이터 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="857f6-124">Displays the data type of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="857f6-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="857f6-125">See Also</span></span>  
 <span data-ttu-id="857f6-126">[Transact-SQL 디버거](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="857f6-126">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="857f6-127">[Transact-SQL 디버거 정보](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="857f6-127">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="857f6-128">[조사식 창](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="857f6-128">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="857f6-129">[호출 스택 창](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="857f6-129">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="857f6-130">[간략한 조사식 대화 상자](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="857f6-130">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 [<span data-ttu-id="857f6-131">식&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="857f6-131">Expressions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/expressions-transact-sql)  
