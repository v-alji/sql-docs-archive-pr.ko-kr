---
title: 병합 기능 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
author: rothja
ms.author: jroth
ms.openlocfilehash: 8c2e2d3f0796396c0f3f451215f1fd685979a842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649556"
---
# <a name="implementing-merge-functionality"></a><span data-ttu-id="65185-102">MERGE 기능 구현</span><span class="sxs-lookup"><span data-stu-id="65185-102">Implementing MERGE Functionality</span></span>
  <span data-ttu-id="65185-103">데이터베이스에 특정 행 이 이미 있는지 여부에 따라 데이터베이스에서 삽입 또는 업데이트를 수행해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65185-103">A database may need to perform either an insert of an update, depending on whether a particular row already exists in the database.</span></span>  
  
 <span data-ttu-id="65185-104">`MERGE` 문을 사용하지 않는 경우 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 사용할 수 있는 방법 중 하나는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="65185-104">Without using the `MERGE` statement, the following is one approach you can use in [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
```sql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 <span data-ttu-id="65185-105">병합을 구현하는 다른 [!INCLUDE[tsql](../../includes/tsql-md.md)] 방법:</span><span class="sxs-lookup"><span data-stu-id="65185-105">Another [!INCLUDE[tsql](../../includes/tsql-md.md)] method to implement a merge:</span></span>  
  
```sql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE....  
ELSE  
    INSERT  
```  
  
 <span data-ttu-id="65185-106">고유하게 컴파일된 저장 프로시저의 경우</span><span class="sxs-lookup"><span data-stu-id="65185-106">For a natively compiled stored procedure</span></span>  
  
```sql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT....  
```  
  
## <a name="see-also"></a><span data-ttu-id="65185-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65185-107">See Also</span></span>  
 <span data-ttu-id="65185-108">[고유하게 컴파일된 저장 프로시저의 마이그레이션 문제](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="65185-108">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="65185-109">메모리 내 OLTP에서 지원되지 않는 Transact-SQL 구문</span><span class="sxs-lookup"><span data-stu-id="65185-109">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
