---
title: 90 이상 호환성 모드에서는 외부 조인 연산자 *= 및 =* 가 지원 되지 않습니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 357c729e6d53cc17f2e4c169dd66613b6cfd2f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735887"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a><span data-ttu-id="aeeae-102">호환성 모드 90 이상에서는 외부 조인 연산자 \*= 및 =\*가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aeeae-102">Outer join operators \*= and =\* are not supported in 90 or later compatibility modes</span></span>
  <span data-ttu-id="aeeae-103">업그레이드 관리자가 외부 조인 연산자 = 및 =를 사용 하는 것을 감지 했습니다 \* \* .</span><span class="sxs-lookup"><span data-stu-id="aeeae-103">Upgrade Advisor detected the use of outer join operators \*= and =\*.</span></span> <span data-ttu-id="aeeae-104">호환성 모드가 90 이상일 때는 이러한 연산자가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aeeae-104">These operators are not supported in 90 or later compatibility modes.</span></span> <span data-ttu-id="aeeae-105">업그레이드할 때 사용자 데이터베이스는 호환성 모드를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="aeeae-105">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="aeeae-106">이러한 연산자를 사용하는 문은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="aeeae-106">Statements that use these operators will fail.</span></span>  
  
## <a name="component"></a><span data-ttu-id="aeeae-107">구성 요소</span><span class="sxs-lookup"><span data-stu-id="aeeae-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="aeeae-108">수정 동작</span><span class="sxs-lookup"><span data-stu-id="aeeae-108">Corrective Action</span></span>  
 <span data-ttu-id="aeeae-109">데이터베이스 호환성 모드를 90 이상으로 변경 하기 전에 외부 조인 연산자 = 및 =를 사용 하는 문을 수정 하 여 해당 하는 \* \* outer join 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeeae-109">Before you change the database compatibility mode to 90 or later, modify statements that use the outer join operators \*= and =\* to use equivalent OUTER JOIN keywords.</span></span> <span data-ttu-id="aeeae-110">다음 예에서는 `\*=` 연산자를 사용하는 쿼리와 `LEFT OUTER JOIN` 키워드를 사용하는 동일한 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aeeae-110">The following example shows a query that uses the `\*=` operator and an equivalent query that uses the `LEFT OUTER JOIN` keywords.</span></span>  
  
```  
-- This query uses an old-style outer join operator.  
USE pubs  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee, jobs   
WHERE employee.job_id *= jobs.job_id  
ORDER BY employee.job_id  
  
-- This query uses the ANSI standard keywords LEFT OUTER JOIN.  
USE pubs;  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
ORDER BY employee.job_id  
```  
  
 <span data-ttu-id="aeeae-111">외부 조인에 대한 자세한 내용은 SQL Server 온라인 설명서에서 "외부 조인 사용"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aeeae-111">For more information about outer joins, see "Using Outer Joins" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeeae-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aeeae-112">See Also</span></span>  
 <span data-ttu-id="aeeae-113">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="aeeae-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="aeeae-114">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="aeeae-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
