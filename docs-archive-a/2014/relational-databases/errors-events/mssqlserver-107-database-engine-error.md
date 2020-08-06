---
title: MSSQLSERVER_107 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b9388bbda6f00b1aafd02caee1b6a7b8387564f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653441"
---
# <a name="mssqlserver_107"></a><span data-ttu-id="9ebd5-102">MSSQLSERVER_107</span><span class="sxs-lookup"><span data-stu-id="9ebd5-102">MSSQLSERVER_107</span></span>
    
## <a name="details"></a><span data-ttu-id="9ebd5-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="9ebd5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ebd5-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="9ebd5-104">Product Name</span></span>|<span data-ttu-id="9ebd5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ebd5-105">SQL Server</span></span>|  
|<span data-ttu-id="9ebd5-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="9ebd5-106">Event ID</span></span>|<span data-ttu-id="9ebd5-107">107</span><span class="sxs-lookup"><span data-stu-id="9ebd5-107">107</span></span>|  
|<span data-ttu-id="9ebd5-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="9ebd5-108">Event Source</span></span>|<span data-ttu-id="9ebd5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9ebd5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9ebd5-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9ebd5-110">Component</span></span>|<span data-ttu-id="9ebd5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9ebd5-111">SQLEngine</span></span>|  
|<span data-ttu-id="9ebd5-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="9ebd5-112">Symbolic Name</span></span>|<span data-ttu-id="9ebd5-113">P_NOCORRMATCH</span><span class="sxs-lookup"><span data-stu-id="9ebd5-113">P_NOCORRMATCH</span></span>|  
|<span data-ttu-id="9ebd5-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="9ebd5-114">Message Text</span></span>|<span data-ttu-id="9ebd5-115">열 접두사 '%.\*ls'이(가) 쿼리에 사용된 테이블 이름 또는 별칭과 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebd5-115">The column prefix '%.\*ls' does not match with a table name or alias name used in the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9ebd5-116">설명</span><span class="sxs-lookup"><span data-stu-id="9ebd5-116">Explanation</span></span>  
 <span data-ttu-id="9ebd5-117">쿼리의 SELECT 목록에 열 접두사로 잘못 한정된 별표(\*)가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebd5-117">The select list of the query contains an asterisk (\*) that is incorrectly qualified with a column prefix.</span></span> <span data-ttu-id="9ebd5-118">이 오류는 다음과 같은 경우에 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebd5-118">This error can be returned under the following conditions:</span></span>  
  
-   <span data-ttu-id="9ebd5-119">열 접두사가 쿼리에 사용된 테이블 또는 별칭 이름과 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebd5-119">The column prefix does not correspond to any table or alias name used in the query.</span></span> <span data-ttu-id="9ebd5-120">예를 들어 다음 문에서는 별칭 이름(`T1`)을 열 접두사로 사용하고 있지만 FROM 절에는 별칭이 정의되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebd5-120">For example, the following statement uses an alias name (`T1`) as a column prefix, but the alias is not defined in the FROM clause.</span></span>  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   <span data-ttu-id="9ebd5-121">FROM 절에 테이블에 대한 별칭 이름을 제공하면 테이블 이름이 열 접두사로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ebd5-121">A table name is specified as a column prefix when an alias name for the table is supplied in the FROM clause.</span></span> <span data-ttu-id="9ebd5-122">예를 들어 다음 문에서는 테이블 이름 `ErrorLog`를 열 접두사로 사용하지만 테이블에는 FROM 절에 정의된 별칭(`T1`)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebd5-122">For example, the following statement uses the table name `ErrorLog` as the column prefix; however, the table has an alias (`T1`) defined in the FROM clause.</span></span>  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
     <span data-ttu-id="9ebd5-123">FROM 절에 테이블 이름에 대한 별칭을 제공한 경우 테이블에서 해당 별칭만 열 접두사로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebd5-123">If an alias has been provided for a table name in the FROM clause, you can only use the alias to prefix columns from the table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9ebd5-124">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="9ebd5-124">User Action</span></span>  
 <span data-ttu-id="9ebd5-125">쿼리의 FROM 절에 지정된 테이블 이름 또는 별칭 이름과 열 접두사가 일치하도록 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ebd5-125">Match the column prefixes against the table names or alias names specified in the FROM clause of the query.</span></span> <span data-ttu-id="9ebd5-126">예를 들어 위의 문은 다음과 같이 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebd5-126">For example, the statements above can be corrected as follows:</span></span>  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
 <span data-ttu-id="9ebd5-127">또는</span><span class="sxs-lookup"><span data-stu-id="9ebd5-127">or</span></span>  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ebd5-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ebd5-128">See Also</span></span>  
 [<span data-ttu-id="9ebd5-129">MSSQLSERVER_4104</span><span class="sxs-lookup"><span data-stu-id="9ebd5-129">MSSQLSERVER_4104</span></span>](mssqlserver-4104-database-engine-error.md)  
  
  
