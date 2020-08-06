---
title: ORDER BY 절의 열 별칭 앞에 테이블 별칭을 붙일 수 없습니다. Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], columns
ms.assetid: fee7328f-6e8d-4005-930b-56fb6f17e0b2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 44333d778753a2f8761d32d181681b798e3bc409
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650490"
---
# <a name="column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias"></a><span data-ttu-id="26985-102">ORDER BY 절의 열 별칭에 접두사로 테이블 별칭을 붙일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26985-102">Column aliases in ORDER BY clause cannot be prefixed by table alias</span></span>
  <span data-ttu-id="26985-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 ORDER BY 절의 열 별칭에 접두사로 테이블 별칭을 붙일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26985-103">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later, column aliases in the ORDER BY clause cannot be prefixed by the table alias.</span></span>  
  
## <a name="component"></a><span data-ttu-id="26985-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="26985-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="26985-105">Description</span><span class="sxs-lookup"><span data-stu-id="26985-105">Description</span></span>  
 <span data-ttu-id="26985-106">예를 들어 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 다음 쿼리가 실행되지만 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서는 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="26985-106">For example, the following query executes in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], but returns an error in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.l  
```  
  
 <span data-ttu-id="26985-107">[!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)]은 `p.l` 절의 `ORDER BY`을 테이블의 유효한 열에 일치시키지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26985-107">The [!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)] does not match `p.l` in the `ORDER BY` clause to a valid column in the table.</span></span>  
  
### <a name="exception"></a><span data-ttu-id="26985-108">예외</span><span class="sxs-lookup"><span data-stu-id="26985-108">Exception</span></span>  
 <span data-ttu-id="26985-109">ORDER BY 절에 지정되어 있으며 접두사가 있는 열 별칭이 지정된 테이블의 유효한 열 이름이면 쿼리가 오류 없이 실행됩니다. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 문의 의미 체계가 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26985-109">If the prefixed column alias that is specified in the ORDER BY clause is a valid column name in the specified table, the query executes without error; in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the semantics of the statement might be different.</span></span> <span data-ttu-id="26985-110">예를 들어 다음 문에 지정된 열 별칭(`id`)은 `sysobjects` 테이블의 유효한 열 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="26985-110">For example, the column alias (`id`) specified in the following statement is a valid column name in the `sysobjects` table.</span></span> <span data-ttu-id="26985-111">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 문을 실행하면 결과 집합이 정렬된 후에 `CAST` 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="26985-111">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], when the statement executes, the `CAST` operation is performed after the result set is sorted.</span></span> <span data-ttu-id="26985-112">즉, `name` 열이 정렬 작업에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="26985-112">This means the `name` column is used in the sort operation.</span></span> <span data-ttu-id="26985-113">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서는 `CAST` 작업이 정렬 작업보다 먼저 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="26985-113">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the `CAST` operation occurs before the sort operation.</span></span> <span data-ttu-id="26985-114">즉, 테이블의 `id` 열이 정렬 작업에 사용되고 결과 집합을 예기치 않은 순서로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="26985-114">This means the `id` column in the table is used in the sort operation and returns the result set in an unexpected order.</span></span>  
  
```  
SELECT CAST (o.name AS char(128)) AS id  
FROM sysobjects AS o  
ORDER BY o.id;  
```  
  
## <a name="corrective-action"></a><span data-ttu-id="26985-115">수정 동작</span><span class="sxs-lookup"><span data-stu-id="26985-115">Corrective Action</span></span>  
 <span data-ttu-id="26985-116">다음 방법 중 하나로 ORDER BY 절의 테이블 별칭이 접두사로 지정된 열 별칭을 사용하는 쿼리를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="26985-116">Modify queries that use column aliases prefixed by table aliases in the ORDER BY clause in either of the following ways:</span></span>  
  
-   <span data-ttu-id="26985-117">가능하면 ORDER BY 절의 열 별칭에 접두사를 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26985-117">Do not prefix the column alias in the ORDER BY clause, if possible.</span></span>  
  
-   <span data-ttu-id="26985-118">열 별칭을 열 이름으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="26985-118">Replace the column alias with the column name.</span></span>  
  
 <span data-ttu-id="26985-119">예를 들어 다음 두 쿼리는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서 오류 없이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="26985-119">For example, both of the following queries execute without error in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY l  
  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.LastName  
```  
  
## <a name="see-also"></a><span data-ttu-id="26985-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26985-120">See Also</span></span>  
 <span data-ttu-id="26985-121">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="26985-121">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="26985-122">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="26985-122">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
