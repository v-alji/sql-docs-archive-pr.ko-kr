---
title: MSSQLSERVER_137 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e0142cd53006609e9274972e4f5964132f5982c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653962"
---
# <a name="mssqlserver_137"></a><span data-ttu-id="ff9b2-102">MSSQLSERVER_137</span><span class="sxs-lookup"><span data-stu-id="ff9b2-102">MSSQLSERVER_137</span></span>
    
## <a name="details"></a><span data-ttu-id="ff9b2-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ff9b2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff9b2-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ff9b2-104">Product Name</span></span>|<span data-ttu-id="ff9b2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ff9b2-105">SQL Server</span></span>|  
|<span data-ttu-id="ff9b2-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ff9b2-106">Event ID</span></span>|<span data-ttu-id="ff9b2-107">137</span><span class="sxs-lookup"><span data-stu-id="ff9b2-107">137</span></span>|  
|<span data-ttu-id="ff9b2-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ff9b2-108">Event Source</span></span>|<span data-ttu-id="ff9b2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ff9b2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ff9b2-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ff9b2-110">Component</span></span>|<span data-ttu-id="ff9b2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ff9b2-111">SQLEngine</span></span>|  
|<span data-ttu-id="ff9b2-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="ff9b2-112">Symbolic Name</span></span>|<span data-ttu-id="ff9b2-113">P_SCALAR_VAR_NOTFOUND</span><span class="sxs-lookup"><span data-stu-id="ff9b2-113">P_SCALAR_VAR_NOTFOUND</span></span>|  
|<span data-ttu-id="ff9b2-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="ff9b2-114">Message Text</span></span>|<span data-ttu-id="ff9b2-115">스칼라 변수 "%.\*ls"을(를) 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9b2-115">Must declare the scalar variable "%.\*ls".</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ff9b2-116">설명</span><span class="sxs-lookup"><span data-stu-id="ff9b2-116">Explanation</span></span>  
 <span data-ttu-id="ff9b2-117">이 오류는 SQL 스크립트에서 변수를 먼저 선언하지 않고 사용하는 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9b2-117">This error occurs when a variable is used in a SQL script without first declaring the variable.</span></span> <span data-ttu-id="ff9b2-118">다음 예에서는가 선언 되지 않았으므로 SET 및 SELECT 문에 대해 모두 오류 137을 반환 합니다 **@mycol** .</span><span class="sxs-lookup"><span data-stu-id="ff9b2-118">The following example returns error 137 for both the SET and SELECT statements because **@mycol** is not declared.</span></span>  
  
 <span data-ttu-id="ff9b2-119">SET @mycol = 'ContactName';</span><span class="sxs-lookup"><span data-stu-id="ff9b2-119">SET @mycol = 'ContactName';</span></span>  
  
 <span data-ttu-id="ff9b2-120">SELECT @mycol;</span><span class="sxs-lookup"><span data-stu-id="ff9b2-120">SELECT @mycol;</span></span>  
  
 <span data-ttu-id="ff9b2-121">이 오류의 좀 더 복잡한 원인 중 하나로 EXECUTE 문 외부에서 선언된 변수를 사용하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9b2-121">One of the more complicated causes of this error includes the use of a variable that is declared outside the EXECUTE statement.</span></span> <span data-ttu-id="ff9b2-122">예를 들어 **@mycol** select 문에 지정 된 변수는 select 문에 로컬인 것 이므로 EXECUTE 문 외부에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9b2-122">For example, the variable **@mycol** specified in the SELECT statement is local to the SELECT statement; thus it is outside the EXECUTE statement.</span></span>  
  
 <span data-ttu-id="ff9b2-123">USE AdventureWorks2012;</span><span class="sxs-lookup"><span data-stu-id="ff9b2-123">USE AdventureWorks2012;</span></span>  
  
 <span data-ttu-id="ff9b2-124">이동</span><span class="sxs-lookup"><span data-stu-id="ff9b2-124">GO</span></span>  
  
 <span data-ttu-id="ff9b2-125">DECLARE @mycol nvarchar(20);</span><span class="sxs-lookup"><span data-stu-id="ff9b2-125">DECLARE @mycol nvarchar(20);</span></span>  
  
 <span data-ttu-id="ff9b2-126">SET @mycol = 'Name';</span><span class="sxs-lookup"><span data-stu-id="ff9b2-126">SET @mycol = 'Name';</span></span>  
  
 <span data-ttu-id="ff9b2-127">EXECUTE ('SELECT @mycol FROM Production.Product;');</span><span class="sxs-lookup"><span data-stu-id="ff9b2-127">EXECUTE ('SELECT @mycol FROM Production.Product;');</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ff9b2-128">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="ff9b2-128">User Action</span></span>  
 <span data-ttu-id="ff9b2-129">SQL 스크립트에서 변수를 사용하기 전에 해당 변수를 선언했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff9b2-129">Verify that any variables used in a SQL script are declared before being used elsewhere in the script.</span></span>  
  
 <span data-ttu-id="ff9b2-130">EXECUTE 문 외부에서 선언된 변수를 참조하지 않도록 스크립트를 다시 작성하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff9b2-130">Rewrite the script so that it does not reference variables in the EXECUTE statement that are declared outside of it.</span></span> <span data-ttu-id="ff9b2-131">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9b2-131">For example:</span></span>  
  
 <span data-ttu-id="ff9b2-132">USE AdventureWorks2012;</span><span class="sxs-lookup"><span data-stu-id="ff9b2-132">USE AdventureWorks2012;</span></span>  
  
 <span data-ttu-id="ff9b2-133">이동</span><span class="sxs-lookup"><span data-stu-id="ff9b2-133">GO</span></span>  
  
 <span data-ttu-id="ff9b2-134">DECLARE @mycol nvarchar(20) ;</span><span class="sxs-lookup"><span data-stu-id="ff9b2-134">DECLARE @mycol nvarchar(20) ;</span></span>  
  
 <span data-ttu-id="ff9b2-135">SET @mycol = 'Name';</span><span class="sxs-lookup"><span data-stu-id="ff9b2-135">SET @mycol = 'Name';</span></span>  
  
 <span data-ttu-id="ff9b2-136">EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;</span><span class="sxs-lookup"><span data-stu-id="ff9b2-136">EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff9b2-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff9b2-137">See Also</span></span>  
 <span data-ttu-id="ff9b2-138">[EXECUTE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ff9b2-138">[EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span></span>  
 <span data-ttu-id="ff9b2-139">[SET 문&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ff9b2-139">[SET Statements &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span></span>  
 [<span data-ttu-id="ff9b2-140">DECLARE @local_variable&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ff9b2-140">DECLARE @local_variable &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
  
