---
title: 동기화 하는 동안 트리거 및 제약 조건 동작 제어 (복제 Transact-sql 프로그래밍) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88176f43295fe2ab1f5f5643a46db1ce6132c5f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646368"
---
# <a name="control-the-behavior-of-triggers-and-constraints-during-synchronization-replication-transact-sql-programming"></a><span data-ttu-id="8ce91-102">동기화하는 동안 트리거 및 제약 조건 동작 제어(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="8ce91-102">Control the Behavior of Triggers and Constraints During Synchronization (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="8ce91-103">동기화하는 동안 복제 에이전트는 복제된 테이블에서 [INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [UPDATE&#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) 및 [DELETE&#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) 문을 실행합니다. 그러면 이 테이블에서 DML(데이터 조작 언어) 트리거가 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ce91-103">During synchronization, replication agents execute [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql), and [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) statements on replicated tables, which can cause data manipulation language (DML) triggers on these tables to be executed.</span></span> <span data-ttu-id="8ce91-104">그러나 동기화하는 동안 이러한 트리거 실행을 방지하거나 제약 조건을 적용하지 않아야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ce91-104">There are cases when you may need to prevent these triggers from firing or constraints from being enforced during synchronization.</span></span> <span data-ttu-id="8ce91-105">이 동작은 트리거 또는 제약 조건을 만드는 방법에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8ce91-105">This behavior depends on how the trigger or constraint is created.</span></span>  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a><span data-ttu-id="8ce91-106">동기화하는 동안 트리거 실행을 방지하려면</span><span class="sxs-lookup"><span data-stu-id="8ce91-106">To prevent triggers from executing during synchronization</span></span>  
  
1.  <span data-ttu-id="8ce91-107">새 트리거를 만들 때 [CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)의 NOT FOR REPLICATION 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce91-107">When creating a new trigger, specify the NOT FOR REPLICATION option of [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
2.  <span data-ttu-id="8ce91-108">기존 트리거에 대해서는 [ALTER TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql)의 NOT FOR REPLICATION 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce91-108">For an existing trigger, specify the NOT FOR REPLICATION option of [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql).</span></span>  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a><span data-ttu-id="8ce91-109">동기화하는 동안 제약 조건을 적용하지 않으려면</span><span class="sxs-lookup"><span data-stu-id="8ce91-109">To prevent constraints from being enforced during synchronization</span></span>  
  
1.  <span data-ttu-id="8ce91-110">새 CHECK 또는 FOREIGN KEY 제약 조건을 만들 때 [CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)의 제약 조건 정의에서 CHECK NOT FOR REPLICATION 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce91-110">When creating a new CHECK or FOREIGN KEY constraint, specify CHECK NOT FOR REPLICATION option in the constraint definition of [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce91-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ce91-111">See Also</span></span>  
 [<span data-ttu-id="8ce91-112">테이블 만들기&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="8ce91-112">Create Tables &#40;Database Engine&#41;</span></span>](../tables/create-tables-database-engine.md)  
  
  
