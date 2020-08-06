---
title: 쿼리 확인(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7bf24de9bdc0e8b7b7ceb33bb881812b180ce112
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651959"
---
# <a name="verify-queries-visual-database-tools"></a><span data-ttu-id="90681-102">쿼리 확인(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="90681-102">Verify Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="90681-103">문제를 방지하기 위해 작성된 쿼리를 검사하고 구문이 올바른지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90681-103">To avoid problems, you can check the query you have built to ensure its syntax is correct.</span></span> <span data-ttu-id="90681-104">이 옵션은 [SQL 창](visual-database-tools.md)에 문을 입력할 때 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="90681-104">This option is especially useful when you enter statements in the [SQL pane](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="90681-105">쿼리를 확인할 때는 다음과 같은 사항을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90681-105">Some notes to keep in mind about verifying queries:</span></span>  
  
-   <span data-ttu-id="90681-106">문의 유효성 여부는 **다이어그램 창** 과 **조건 창**에 문을 나타낼 수 있는지 여부와 상관 없으므로 이러한 창에 문이 표시되지 않더라도 문이 올바른지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90681-106">A statement can be valid, and therefore be verified successfully, even if it cannot be represented in the **Diagram Pane** and **Criteria Pane**.</span></span>  
  
-   <span data-ttu-id="90681-107">SQL 확인 과정에서 일부 SQL 오류는 발견되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90681-107">SQL Verification can detect some, but not all SQL errors.</span></span> <span data-ttu-id="90681-108">SQL 확인 과정에서 발견되지 않은 오류가 쿼리에 포함되어 있으면 쿼리를 실행할 때 데이터베이스에서 오류가 감지됩니다.</span><span class="sxs-lookup"><span data-stu-id="90681-108">If a query contains an error not detected during SQL verification, the database will detect the error when you run the query.</span></span>  
  
-   <span data-ttu-id="90681-109">매개 변수가 포함된 쿼리는 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90681-109">Queries that contain parameters cannot be verified.</span></span>  
  
### <a name="to-verify-an-sql-statement"></a><span data-ttu-id="90681-110">SQL 문을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="90681-110">To verify an SQL statement</span></span>  
  
-   <span data-ttu-id="90681-111">**SQL 창**을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **SQL 구문 검증** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="90681-111">Right-click in the **SQL Pane**, and select **Verify SQL Syntax** from the shortcut menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90681-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="90681-112">See Also</span></span>  
 <span data-ttu-id="90681-113">[Visual Database Tools를 &#40;쿼리 실행&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="90681-113">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="90681-114">쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="90681-114">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
