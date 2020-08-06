---
title: 쿼리 정의 다름 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69639
- vdtsql.chm:69640
- vdt.dlgbox.querydefinitionsdiffer
ms.assetid: 90383473-2922-40e5-9682-3850849aa856
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9a39d5d6b739fa4ab1a96ea95b513ecb7f6682f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735820"
---
# <a name="query-definitions-differ-dialog-box-visual-database-tools"></a><span data-ttu-id="c3be1-102">쿼리 정의 다름 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c3be1-102">Query Definitions Differ Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="c3be1-103">이 대화 상자에는 다이어그램 창과 조건 창에서 쿼리를 그래픽 방식으로 표현할 수 없고 SQL 창에서만 쿼리를 편집할 수 있다는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c3be1-103">This dialog box notifies you that your query cannot be represented graphically in the Diagram and Criteria panes, and that you can edit your query only in the SQL pane.</span></span>  
  
 <span data-ttu-id="c3be1-104">SQL 창에서 SQL 문을 입력하거나 편집한 다음 다른 창으로 이동하거나 쿼리를 확인하거나 쿼리를 실행하려 할 때 다음 조건 중 하나라도 충족되면 이 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c3be1-104">This dialog box may appear when you enter or edit an SQL statement in the SQL pane; you then move to another pane, verify the query, or attempt to execute the query; and one of the following conditions applies:</span></span>  
  
-   <span data-ttu-id="c3be1-105">SQL 문이 불완전하거나 하나 이상의 구문 오류가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="c3be1-105">The SQL statement is incomplete or contains one or more syntax errors.</span></span>  
  
-   <span data-ttu-id="c3be1-106">SQL 문이 유효하지만 그래픽 창에서 이 SQL 문을 지원하지 않는 경우(예: 통합 쿼리)</span><span class="sxs-lookup"><span data-stu-id="c3be1-106">The SQL statement is valid but is not supported in the graphical panes (for example, a Union query).</span></span>  
  
-   <span data-ttu-id="c3be1-107">SQL 문이 유효하지만 현재 사용 중인 데이터 연결에만 한정된 구문이 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="c3be1-107">The SQL statement is valid but contains syntax specific to the data connection you are using.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="c3be1-108">문이 유효한지 여부는 **쿼리** 도구 모음의 **SQL 문 확인** 단추를 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3be1-108">You can check whether a statement is valid using the **Verify SQL Statement** button on the **Query** toolbar.</span></span>  
  
 <span data-ttu-id="c3be1-109">이 대화 상자에는 SQL 문을 표현할 수 없는 이유가 표시되고 작업을 어떻게 진행할지 묻는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c3be1-109">The dialog box displays a message with the reason that the SQL statement cannot be represented, and then asks how you want to proceed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3be1-110">다이어그램 창과 조건 창을 숨기면 **쿼리 정의 다름** 대화 상자가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3be1-110">The **Query Definitions Differ** dialog box does not appear if you have hidden the Diagram and Criteria panes.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c3be1-111">옵션</span><span class="sxs-lookup"><span data-stu-id="c3be1-111">Options</span></span>  
 <span data-ttu-id="c3be1-112">**무시 단추**</span><span class="sxs-lookup"><span data-stu-id="c3be1-112">**Ignore Button**</span></span>  
 <span data-ttu-id="c3be1-113">이 단추를 선택하면 SQL 문을 받아들여 계속 편집하거나 실행하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3be1-113">Choose this button to specify that you want to accept the SQL statement, either to edit it further or to execute it.</span></span> <span data-ttu-id="c3be1-114">문을 받아들이면 다이어그램 창과 조건 창이 흐리게 표시됩니다. 이는 SQL 창의 문을 해당 창에서 표현하지 않는다는 사실을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3be1-114">If you accept the statement, the Diagram and Criteria panes appear dimmed to indicate that they do not represent the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="c3be1-115">**실행 취소 단추**</span><span class="sxs-lookup"><span data-stu-id="c3be1-115">**Undo Button**</span></span>  
 <span data-ttu-id="c3be1-116">이 단추를 선택하면 SQL 창에 대한 변경 내용을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3be1-116">Choose this button to discard your changes to the SQL pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3be1-117">문이 올바르지만 쿼리 및 뷰 디자이너에서 그래픽 방식으로 나타낼 수 없는 경우 다이어그램 창과 조건 창에 이 문이 표현되지 않더라도 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3be1-117">If the statement is correct but not supported graphically by the Query and View Designer, you can execute it even though it cannot be represented in the Diagram and Criteria panes.</span></span> <span data-ttu-id="c3be1-118">예를 들어, 통합 쿼리를 입력한 경우 문을 실행할 수 있지만 다른 창에는 표현되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3be1-118">For example, if you enter a Union query, the statement can be executed but not represented in the other panes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3be1-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3be1-119">See Also</span></span>  
 [<span data-ttu-id="c3be1-120">쿼리 및 뷰 디자이너 도구&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="c3be1-120">Query and View Designer Tools &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
