---
title: MSSQLSERVER_8621 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 48c36cf936475e3deea37a172c7dc59f88d0a31a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652854"
---
# <a name="mssqlserver_8621"></a><span data-ttu-id="d25ca-102">MSSQLSERVER_8621</span><span class="sxs-lookup"><span data-stu-id="d25ca-102">MSSQLSERVER_8621</span></span>
    
## <a name="details"></a><span data-ttu-id="d25ca-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="d25ca-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d25ca-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d25ca-104">Product Name</span></span>|<span data-ttu-id="d25ca-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d25ca-105">SQL Server</span></span>|  
|<span data-ttu-id="d25ca-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d25ca-106">Event ID</span></span>|<span data-ttu-id="d25ca-107">8621</span><span class="sxs-lookup"><span data-stu-id="d25ca-107">8621</span></span>|  
|<span data-ttu-id="d25ca-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d25ca-108">Event Source</span></span>|<span data-ttu-id="d25ca-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d25ca-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d25ca-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d25ca-110">Component</span></span>|<span data-ttu-id="d25ca-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d25ca-111">SQLEngine</span></span>|  
|<span data-ttu-id="d25ca-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d25ca-112">Symbolic Name</span></span>|<span data-ttu-id="d25ca-113">OPTIMIZER_STACK_OVERFLOW_ERR</span><span class="sxs-lookup"><span data-stu-id="d25ca-113">OPTIMIZER_STACK_OVERFLOW_ERR</span></span>|  
|<span data-ttu-id="d25ca-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d25ca-114">Message Text</span></span>|<span data-ttu-id="d25ca-115">쿼리 최적화 중 쿼리 프로세서에 스택 공간이 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="d25ca-115">The query processor ran out of stack space during query optimization.</span></span> <span data-ttu-id="d25ca-116">쿼리를 단순하게 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="d25ca-116">Please simplify the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d25ca-117">설명</span><span class="sxs-lookup"><span data-stu-id="d25ca-117">Explanation</span></span>  
 <span data-ttu-id="d25ca-118">확장된 쿼리의 크기가 오류의 원인일 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="d25ca-118">The size of the expanded query is the most likely cause of the error.</span></span> <span data-ttu-id="d25ca-119">확장된 쿼리는 보조 인덱스 및 뷰의 업데이트나 트리거와 같은 연계 동작은 물론 각 뷰, 계산 열, [!INCLUDE[tsql](../../includes/tsql-md.md)] 함수 및 참조하는 공통 테이블 식 등의 정의로 원래 쿼리를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="d25ca-119">The expanded query substitutes into the original query the definitions of each of the views, computed columns, [!INCLUDE[tsql](../../includes/tsql-md.md)] functions, and common table expressions it references, as well as cascading actions like updating secondary indexes, views, and triggers.</span></span>  
  
 <span data-ttu-id="d25ca-120">쿼리의 특정 수치가 너무 크기 때문일 가능성이 높습니다. 예를 들어 뷰 정의에서 참조하는 테이블의 수가 지나치게 많거나 스칼라 식이 너무 크기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d25ca-120">Most likely the query is large in some dimension; for example, the number of tables referenced by view definitions, or a very large scalar expression.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d25ca-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="d25ca-121">User Action</span></span>  
 <span data-ttu-id="d25ca-122">가장 큰 수치를 기준으로 쿼리를 여러 개로 나누어 단순하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d25ca-122">Simplify the query by breaking the query into multiple queries along the largest dimension.</span></span> <span data-ttu-id="d25ca-123">먼저 불필요한 쿼리 요소를 제거한 후 임시 테이블을 추가하고 쿼리를 두 개로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="d25ca-123">First remove any query elements that are not really necessary, then try adding a temp table and splitting the query in two.</span></span>  <span data-ttu-id="d25ca-124">[!INCLUDE[tsql](../../includes/tsql-md.md)] 컴파일러가 이들을 다시 결합하므로 단지 쿼리의 일부를 하위 쿼리, 함수 또는 공통 테이블 식으로 옮기는 것만으로는 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="d25ca-124">Merely moving a part of the query to a subquery, function, or common table expression is insufficient because they get recombined by the [!INCLUDE[tsql](../../includes/tsql-md.md)] compiler.</span></span>  
  
  
