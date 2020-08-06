---
title: 테이블 별칭 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f9e6269fe6e24e8d98922094e799fbf4b5af584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651988"
---
# <a name="create-table-aliases-visual-database-tools"></a><span data-ttu-id="cd745-102">테이블 별칭 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="cd745-102">Create Table Aliases (Visual Database Tools)</span></span>
  <span data-ttu-id="cd745-103">별칭을 사용하면 테이블 이름이 필요한 작업을 더 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd745-103">Aliases can make it easier to work with table names.</span></span> <span data-ttu-id="cd745-104">별칭은 다음과 같은 경우에 유용하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd745-104">Using aliases is helpful when:</span></span>  
  
-   <span data-ttu-id="cd745-105">[SQL 창](visual-database-tools.md) 에서 문을 더 간결하고 읽기 쉽게 만들려는 경우</span><span class="sxs-lookup"><span data-stu-id="cd745-105">You want to make the statement in the [SQL Pane](visual-database-tools.md) shorter and easier to read.</span></span>  
  
-   <span data-ttu-id="cd745-106">열 이름을 한정하는 경우 등과 같이 쿼리에서 테이블 이름을 자주 참조하고 쿼리에 대해 특정한 문자 길이 제한을 반드시 준수하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd745-106">You refer to the table name often in your query - such as in qualifying column names - and want to be sure you stay within a specific character-length limit for your query.</span></span> <span data-ttu-id="cd745-107">일부 데이터베이스에서는 쿼리의 최대 길이가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd745-107">(Some databases impose a maximum length for queries.)</span></span>  
  
-   <span data-ttu-id="cd745-108">자체 조인 등과 같이 동일한 테이블의 여러 인스턴스를 사용하여 작업할 때 특정 인스턴스를 지정해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="cd745-108">You are working with multiple instances of the same table (such as in a self-join) and need a way to refer to one instance or the other.</span></span>  
  
 <span data-ttu-id="cd745-109">예를 들어, 테이블 이름 `"e"` _ `employee`에 대한 별칭`information`를 만든 다음 쿼리의 나머지 부분 전반에 걸쳐 테이블을 `"e"` 로 지칭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd745-109">For example, you can create an alias `"e"` for a table name `employee`_`information`, and then refer to the table as `"e"` throughout the rest of the query.</span></span>  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a><span data-ttu-id="cd745-110">테이블이나 테이블 반환 개체에 대한 별칭을 만들려면</span><span class="sxs-lookup"><span data-stu-id="cd745-110">To create an alias for a table or table-valued object</span></span>  
  
1.  <span data-ttu-id="cd745-111">테이블이나 테이블 반환 개체를 쿼리에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cd745-111">Add the table or table-valued object to your query.</span></span>  
  
2.  <span data-ttu-id="cd745-112">**다이어그램 창**에서 별칭을 만들려는 개체를 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd745-112">In the **Diagram Pane**, right-click the object for which you want to create an alias, then select **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="cd745-113">**속성** 창의 **별칭** 필드에 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd745-113">In the **Properties** window, enter the alias in the **Alias** field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd745-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd745-114">See Also</span></span>  
 <span data-ttu-id="cd745-115">[Visual Database Tools&#41;&#40;쿼리에 테이블을 추가 합니다.](add-tables-to-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="cd745-115">[Add Tables to Queries &#40;Visual Database Tools&#41;](add-tables-to-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="cd745-116">[Visual Database Tools&#41;&#40;쿼리 결과 정렬 및 그룹화](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="cd745-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="cd745-117">[Visual Database Tools를 &#40;쿼리 결과 요약&#41;](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="cd745-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="cd745-118">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="cd745-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
