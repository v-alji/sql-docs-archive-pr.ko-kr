---
title: 자체 조인 자동으로 만들기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a428a44d33b5990e849772b43841df472ca7f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639207"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a><span data-ttu-id="331db-102">자체 조인 자동으로 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="331db-102">Create Self-Joins Automatically (Visual Database Tools)</span></span>
  <span data-ttu-id="331db-103">데이터베이스에서 테이블에 반사 관계가 있는 경우 자동으로 자체 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="331db-103">If a table has a reflexive relationship in the database, you can join it to itself automatically.</span></span>  
  
### <a name="to-create-a-self-join-automatically"></a><span data-ttu-id="331db-104">자체 조인을 자동으로 만들려면</span><span class="sxs-lookup"><span data-stu-id="331db-104">To create a self-join automatically</span></span>  
  
1.  <span data-ttu-id="331db-105">작업할 테이블을 [다이어그램 창](visual-database-tools.md) 에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="331db-105">Add to the [Diagram pane](visual-database-tools.md) the table you want to work with.</span></span>  
  
2.  <span data-ttu-id="331db-106">다이어그램 창에 같은 테이블이 두 번 표시되도록 같은 테이블을 다시 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="331db-106">Add the same table again, so that the Diagram pane shows the same table twice within the Diagram pane.</span></span>  
  
     <span data-ttu-id="331db-107">[쿼리 및 뷰 디자이너](query-and-view-designer-tools-visual-database-tools.md) 는 테이블 이름에 일련 번호를 추가하여 두 번째 인스턴스에 별칭을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="331db-107">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) assigns an alias to the second instance by adding a sequential number to the table name.</span></span> <span data-ttu-id="331db-108">또한 쿼리 및 뷰 디자이너는 테이블이 쿼리와 관련되는 서로 다른 두 가지 방식을 나타내는 조인 선을 두 개의 사각형 사이에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="331db-108">In addition, the Query and View Designer creates a join line between the two rectangles representing the two different ways the table participates in the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="331db-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="331db-109">See Also</span></span>  
 [<span data-ttu-id="331db-110">조인을 사용한 쿼리&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="331db-110">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
