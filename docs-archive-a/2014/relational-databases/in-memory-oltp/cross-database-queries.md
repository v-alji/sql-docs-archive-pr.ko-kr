---
title: 데이터베이스 간 쿼리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
author: rothja
ms.author: jroth
ms.openlocfilehash: 4afbb580a55273ec241005493fd37f99e98ec0e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648384"
---
# <a name="cross-database-queries"></a><span data-ttu-id="d52d1-102">데이터베이스 간 쿼리</span><span class="sxs-lookup"><span data-stu-id="d52d1-102">Cross-Database Queries</span></span>
  <span data-ttu-id="d52d1-103">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]에서 메모리 최적화 테이블은 데이터베이스 간 트랜잭션을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d52d1-103">In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], memory-optimized tables do not support cross-database transactions.</span></span> <span data-ttu-id="d52d1-104">메모리 최적화 테이블에도 액세스하는 동일한 쿼리 또는 동일한 트랜잭션에서 다른 데이터베이스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d52d1-104">You cannot access another database from the same transaction or the same query that also accesses a memory-optimized table.</span></span> <span data-ttu-id="d52d1-105">데이터베이스의 테이블에서 다른 데이터베이스에 있는 메모리 최적화 테이블로 데이터를 쉽게 복사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d52d1-105">You cannot easily copy data from a table in one database, to a memory-optimized table in another database.</span></span>  
  
 <span data-ttu-id="d52d1-106">테이블 변수는 트랜잭션 변수가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d52d1-106">Table variables are not transactional.</span></span> <span data-ttu-id="d52d1-107">메모리 최적화 테이블 변수는 데이터베이스 간 쿼리에 사용할 수 있으므로, 데이터베이스의 데이터를 다른 데이터베이스에 있는 메모리 최적화 테이블로 쉽게 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52d1-107">Therefore, memory-optimized table variables can be used in cross-database queries, and can thus facilitate moving data from one database into memory-optimized tables in another.</span></span> <span data-ttu-id="d52d1-108">두 트랜잭션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52d1-108">You can use two transactions.</span></span> <span data-ttu-id="d52d1-109">첫 번째 트랜잭션에서 원격 테이블의 데이터를 변수에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="d52d1-109">In the first transaction, insert the data from the remote table into the variable.</span></span> <span data-ttu-id="d52d1-110">두 번째 트랜잭션에서 변수의 데이터를 메모리 최적화 로컬 테이블에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="d52d1-110">In the second transaction, insert the data into the local memory-optimized table from the variable.</span></span>  
  
 <span data-ttu-id="d52d1-111">예를 들어 하려면 dbo.tt1 형식의 변수를 사용 하 여 데이터베이스 db1의 t1 테이블에서 d b 2의 테이블 t2로 행을 복사 하려면 @v1 다음과 같은 항목을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d52d1-111">For example, to copy the row from table t1 in database db1 to table t2 in db2, using variable @v1 of type dbo.tt1, you can use something like:</span></span>  
  
```sql  
USE db2   
GO   
DECLARE @v1 dbo.tt1   
INSERT @v1 SELECT * FROM db1.dbo.t1   
INSERT dbo.t2 SELECT * FROM @v1   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d52d1-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d52d1-112">See Also</span></span>  
 [<span data-ttu-id="d52d1-113">메모리 내 OLTP로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="d52d1-113">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
