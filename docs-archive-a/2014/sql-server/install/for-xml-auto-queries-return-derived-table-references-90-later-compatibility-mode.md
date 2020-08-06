---
title: FOR XML AUTO 쿼리는 90 이상 호환성 모드에서 파생 테이블 참조를 반환 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FOR XML AUTO [SQL Server]
ms.assetid: 10c32f06-f7e1-40e0-8f79-6d921f2bef1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 702cb2ca1d437dff03cee09c98d72082500709d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661513"
---
# <a name="for-xml-auto-queries-return-derived-table-references-in-90-or-later-compatibility-modes"></a><span data-ttu-id="4b21b-102">FOR XML AUTO 쿼리는 호환성 모드 90 이상에서 파생 테이블 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4b21b-102">FOR XML AUTO queries return derived table references in 90 or later compatibility modes</span></span>
  <span data-ttu-id="4b21b-103">데이터베이스 호환성 수준이 90 이상으로 설정되어 있으면 AUTO 모드에서 실행되는 FOR XML 쿼리는 파생 테이블 별칭에 대한 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4b21b-103">When the database compatibility level is set to 90 or later, FOR XML queries that execute in AUTO mode return references to derived table aliases.</span></span> <span data-ttu-id="4b21b-104">호환성 수준이 80으로 설정되어 있으면 FOR XML AUTO 쿼리는 파생 테이블을 정의하는 기본 테이블에 대한 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4b21b-104">When the compatibility level is set to 80, FOR XML AUTO queries return references to the base tables that define a derived table.</span></span>  
  
## <a name="component"></a><span data-ttu-id="4b21b-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="4b21b-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="4b21b-106">Description</span><span class="sxs-lookup"><span data-stu-id="4b21b-106">Description</span></span>  
 <span data-ttu-id="4b21b-107">예를 들어 다음 테이블을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="4b21b-107">For example, consider the following table:</span></span>  
  
```  
CREATE TABLE Test(id int);  
INSERT INTO Test VALUES(1);  
INSERT INTO Test VALUES(2);  
```  
  
 <span data-ttu-id="4b21b-108">파생 테이블을 포함하는 다음 쿼리는 호환성 수준 80 또는 90 이상에서 서로 다른 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="4b21b-108">The following query, which includes a derived table, produces different results under compatibility levels 80, 90, or later:</span></span>  
  
```  
SELECT * FROM   
   (SELECT a.id AS a, b.id AS b   
    FROM Test a JOIN Test b ON a.id=b.id)  
AS DerivedTest   
FOR XML AUTO;  
```  
  
 <span data-ttu-id="4b21b-109">호환성 수준 80에서 이 쿼리는 다음 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4b21b-109">Under compatibility level 80, the query returns the following results.</span></span> <span data-ttu-id="4b21b-110">이 결과는 파생 테이블 별칭 대신 파생 테이블의 기본 테이블 별칭 `a` 와 `b` 를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="4b21b-110">The results reference the base table aliases `a` and `b` of the derived table instead of the derived table alias.</span></span>  
  
```  
<a a="1"><b b="1"/></a><a a="2"><b b="2"/></a>  
```  
  
 <span data-ttu-id="4b21b-111">호환성 수준 90 이상에서 이 쿼리는 파생 테이블의 기본 테이블 대신 파생 테이블 별칭 `DerivedTest` 에 대한 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4b21b-111">Under compatibility level 90 or later, the query returns references to the derived table alias `DerivedTest` instead of to the derived table's base tables.</span></span>  
  
```  
<DerivedTest a="1" b="1"/><DerivedTest a="2" b="2"/>  
```  
  
## <a name="corrective-action"></a><span data-ttu-id="4b21b-112">수정 동작</span><span class="sxs-lookup"><span data-stu-id="4b21b-112">Corrective Action</span></span>  
 <span data-ttu-id="4b21b-113">필요에 따라 파생 테이블을 포함하고 있고 호환성 수준 90 이상에서 실행되는 FOR XML AUTO 쿼리 결과의 변경 내용을 반영하도록 애플리케이션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b21b-113">Modify your application as required to account for the changes in results of FOR XML AUTO queries that include derived tables and that run under compatibility level 90 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b21b-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b21b-114">See Also</span></span>  
 <span data-ttu-id="4b21b-115">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="4b21b-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="4b21b-116">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="4b21b-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
