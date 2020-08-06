---
title: 명명되지 않은 매개 변수를 사용하여 쿼리 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ea53afd1fa4d44390f5805d6b28494428608b90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639208"
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a><span data-ttu-id="e573d-102">명명되지 않은 매개 변수를 사용하여 쿼리 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e573d-102">Create Queries with Unnamed Parameters (Visual Database Tools)</span></span>
  <span data-ttu-id="e573d-103">리터럴 값에 대한 자리 표시자로 물음표(?)를 지정하면 명명되지 않은 매개 변수를 사용하여 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e573d-103">You can create a query with an unnamed parameter by specifying a question mark (?) as a placeholder for a literal value.</span></span> <span data-ttu-id="e573d-104">쿼리 및 뷰 디자이너에서 이러한 매개 변수에 임시 이름이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e573d-104">Query and View Designer will give it a temporary name.</span></span> <span data-ttu-id="e573d-105">쿼리에서 지정할 수 있는 명명되지 않은 매개 변수의 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e573d-105">You can specify as many unnamed parameters in the query as you need.</span></span>  
  
 <span data-ttu-id="e573d-106">쿼리 및 뷰 디자이너에서 쿼리를 실행하면 임시 이름이 적용된 쿼리 매개 변수 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e573d-106">When you run the query in the Query and View Designer, the Query Parameters Dialog Box is displayed with the temporary name.</span></span>  
  
### <a name="to-specify-an-unnamed-parameter"></a><span data-ttu-id="e573d-107">명명되지 않은 매개 변수를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="e573d-107">To specify an unnamed parameter</span></span>  
  
1.  <span data-ttu-id="e573d-108">검색하려는 열이나 식을 [조건 창](visual-database-tools.md)에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e573d-108">Add the columns or expressions that you want to search to the [Criteria pane](visual-database-tools.md).</span></span> <span data-ttu-id="e573d-109">검색 열이나 식이 쿼리 출력에 표시되지 않도록 하려면 이를 출력 열에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e573d-109">If you do not want the search columns or expressions to appear in the query output, remove them as output columns.</span></span>  
  
2.  <span data-ttu-id="e573d-110">검색할 데이터 열이나 식이 포함된 행을 찾은 다음 표 형태의 **필터** 열에 물음표(?)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e573d-110">Locate the row containing the data column or expression to search, and then in the **Filter** grid column, enter a question mark (?).</span></span>  
  
     <span data-ttu-id="e573d-111">쿼리 및 뷰 디자이너에서는 "=" 연산자가 기본적으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e573d-111">By default, the Query and View Designer adds the "=" operator.</span></span> <span data-ttu-id="e573d-112">셀을 편집하여 이 연산자를 ">", "<" 또는 임의의 다른 SQL 비교 연산자로 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e573d-112">However, you can edit the cell to substitute ">", "<", or any other SQL comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e573d-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e573d-113">See Also</span></span>  
 [<span data-ttu-id="e573d-114">매개 변수를 사용하여 쿼리&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="e573d-114">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](query-with-parameters-visual-database-tools.md)  
  
  
