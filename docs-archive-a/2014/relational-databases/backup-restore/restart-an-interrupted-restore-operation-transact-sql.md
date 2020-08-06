---
title: 중단된 복원 작업 다시 시작(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- interrupted restore operation
- restoring databases [SQL Server], restarting interrupted operation
- resetting options changed after backup
- database restores [SQL Server], restarting interrupted operation
- restarting interrupted restore operation
- restoring interrupted operation [SQL Server]
ms.assetid: 6413a07d-fd90-448d-8f29-12c5a1972618
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a6fa09ce66865d61c8f3a86feedc04eaf8deec2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728372"
---
# <a name="restart-an-interrupted-restore-operation-transact-sql"></a><span data-ttu-id="75903-102">중단된 복원 작업 다시 시작(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="75903-102">Restart an Interrupted Restore Operation (Transact-SQL)</span></span>
  <span data-ttu-id="75903-103">이 항목에서는 인터럽트된 복원 작업을 다시 시작하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="75903-103">This topic explains how to restart an interrupted restore operation.</span></span>  
  
### <a name="to-restart-an-interrupted-restore-operation"></a><span data-ttu-id="75903-104">중단된 복원 작업을 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="75903-104">To restart an interrupted restore operation</span></span>  
  
1.  <span data-ttu-id="75903-105">인터럽트된 RESTORE 문을 다시 실행합니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="75903-105">Execute the interrupted RESTORE statement again, specifying:</span></span>  
  
    -   <span data-ttu-id="75903-106">원래 RESTORE 문에 사용한 것과 동일한 절</span><span class="sxs-lookup"><span data-stu-id="75903-106">The same clauses used in the original RESTORE statement.</span></span>  
  
    -   <span data-ttu-id="75903-107">RESTART 절</span><span class="sxs-lookup"><span data-stu-id="75903-107">The RESTART clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75903-108">예제</span><span class="sxs-lookup"><span data-stu-id="75903-108">Example</span></span>  
 <span data-ttu-id="75903-109">다음은 중단된 복원 작업을 다시 시작하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="75903-109">This example restarts an interrupted restore operation.</span></span>  
  
```sql  
-- Restore a full database backup of the AdventureWorks database.  
RESTORE DATABASE AdventureWorks  
   FROM DISK = 'C:\AdventureWorks.bck'  
GO  
-- The restore operation halted prematurely.  
-- Repeat the original RESTORE statement specifying WITH RESTART.  
RESTORE DATABASE AdventureWorks   
   FROM DISK = 'C:\AdventureWorks.bck'  
   WITH RESTART  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="75903-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75903-110">See Also</span></span>  
 <span data-ttu-id="75903-111">[전체 데이터베이스 복원&#40;전체 복구 모델&#41;](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="75903-111">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="75903-112">[전체 데이터베이스 복원&#40;단순 복구 모델&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="75903-112">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="75903-113">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="75903-113">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
