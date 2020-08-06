---
title: 쿼리에 TOP 절 지정(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- TOP clause, queries
- percentage of rows returned [SQL Server]
- number of rows
- search conditions [SQL Server], TOP clause
- restricting rows returned
- search criteria [SQL Server], limiting rows returned
- inspecting portion of results
- limiting rows returned
- search criteria [SQL Server], TOP clause
ms.assetid: ba7d7c10-9bb3-4d9b-90b0-5fa94ecae59b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8228779703b1bbe3753f1e2728e83b4b5c3a3d17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740648"
---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a><span data-ttu-id="39ebd-102">쿼리에 TOP 절 지정(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="39ebd-102">Specify the TOP Clause in Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="39ebd-103">TOP 절은 쿼리에서 처음 *n*개 또는 *n%* 의 행만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-103">The TOP clause returns only the first *n* or *n percent* rows from a query.</span></span> <span data-ttu-id="39ebd-104">TOP 절은 쿼리 결과를 모두 반환하는 데 필요한 리소스를 사용하지 않은 채 쿼리가 의도한 대로 올바르게 작동하는지 확인하기 위해 결과의 일부만 검사하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-104">The TOP clause is useful when you want to inspect a portion of your results to find out if your query does what you expect it to do, without taking the resources necessary to return all of the query results.</span></span>  
  
### <a name="to-specify-the-top-clause-in-queries"></a><span data-ttu-id="39ebd-105">쿼리에 TOP 절을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="39ebd-105">To specify the TOP clause in queries</span></span>  
  
1.  <span data-ttu-id="39ebd-106">솔루션 탐색기에서 쿼리를 열거나 새 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-106">Open a query from Solution Explorer or create a new one.</span></span>  
  
2.  <span data-ttu-id="39ebd-107">**보기** 메뉴에서 **속성 창**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-107">From the **View** menu, click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="39ebd-108">**속성 창**에서 **Top 사양** 속성을 찾아 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-108">In the **Properties Window**, locate and expand the **Top Specification** property.</span></span>  
  
4.  <span data-ttu-id="39ebd-109">**(Top)** 자식 속성을 클릭하고 이를 **예**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-109">Click the **(Top)** child property and set it to **Yes**.</span></span>  
  
5.  <span data-ttu-id="39ebd-110">**식** 자식 속성에 숫자 결과가 있는 식(예: "10" 또는 "2\*5")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-110">In the **Expression** child property, type an expression that has a numeric result (for example, "10" or "2\*5").</span></span>  
  
6.  <span data-ttu-id="39ebd-111">**Percent** 자식 속성을 클릭하고 **식** 속성을 반환된 행 전체의 백분율로 간주할지(예) 반환된 행의 절대 수로 간주할지(아니요) 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-111">Click the **Percent** child property and indicate whether or not to treat the **Expression** property as a percentage of all rows returned (Yes) or as the absolute number of rows returned (No).</span></span>  
  
7.  <span data-ttu-id="39ebd-112">쿼리에 ORDER BY 절이 사용되는 경우 그룹의 일부만 포함된 상태에서 그룹의 행 전체를 표시하려면 **With Ties** 자식 속성을 클릭한 다음 **예** 를 선택하고 표시되지 않은 행을 잘라내려면 **아니요** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-112">If your query uses the ORDER BY clause, click the **With Ties** child property and choose **Yes** to display all rows in a group if only part of the group is included or **No** to truncate them.</span></span>  
  
 <span data-ttu-id="39ebd-113">위에서 설명한 작업을 진행할 때는 SQL 창에 표시된 TOP 절이 속성의 현재 설정을 반영하도록 변경되는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-113">As you work through the preceding procedure, notice that the TOP clause, displayed in the SQL pane, changes to reflect the current settings of the properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39ebd-114">SQL 창에서 TOP 절을 편집하여 **Top 사양** 의 자식 속성 값을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ebd-114">You can also change the values of the child properties of the **Top Specification** by editing the TOP clause in the SQL pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39ebd-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39ebd-115">See Also</span></span>  
 <span data-ttu-id="39ebd-116">[쿼리 및 뷰 디자인 방법 도움말 항목 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="39ebd-116">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="39ebd-117">쿼리 속성&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="39ebd-117">Query Properties &#40;Visual Database Tools&#41;</span></span>](query-properties-visual-database-tools.md)  
  
  
