---
title: 미러된 미디어 세트에 백업(TRANSACT-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 255a3c190139c029f5211dcab9780b6d07d975a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651733"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a><span data-ttu-id="ced30-102">미러된 미디어 세트에 백업(TRANSACT-SQL)</span><span class="sxs-lookup"><span data-stu-id="ced30-102">Back Up to a Mirrored Media Set (Transact-SQL)</span></span>
  <span data-ttu-id="ced30-103">이 항목에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 데이터베이스를 백업할 때 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 문을 사용 하 여 미러된 미디어 세트를 지정 하는 방법에 대해 설명 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ced30-103">This topic describes how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement to specify a mirrored media set when backing up a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="ced30-104">BACKUP 문에서 TO 절에 첫 번째 미러를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ced30-104">In your BACKUP statement, specify the first mirror in the TO clause.</span></span> <span data-ttu-id="ced30-105">그런 다음 해당 MIRROR TO 절에 각 미러를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ced30-105">Then, specify each mirror in its own MIRROR TO clause.</span></span> <span data-ttu-id="ced30-106">TO절과 MIRROR TO 절은 같은 개수와 유형의 백업 디바이스를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ced30-106">The TO and MIRROR TO clauses must specify the same number and type of backup devices.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ced30-107">예제</span><span class="sxs-lookup"><span data-stu-id="ced30-107">Example</span></span>  
 <span data-ttu-id="ced30-108">다음 예에서는 이전 그림에 표시된 미러된 미디어 세트를 만들고 두 미러 모두에 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="ced30-108">The following example creates the mirrored media set illustrated in the previous illustration and backs up the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to both mirrors.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="ced30-109">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ced30-109">Related Tasks</span></span>  
 <span data-ttu-id="ced30-110">**미러된 백업에서 복원하려면**</span><span class="sxs-lookup"><span data-stu-id="ced30-110">**To restore from a mirrored backup**</span></span>  
  
-   [<span data-ttu-id="ced30-111">RESTORE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ced30-111">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="ced30-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ced30-112">See Also</span></span>  
 <span data-ttu-id="ced30-113">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ced30-113">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="ced30-114">미러된 백업 미디어 세트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ced30-114">Mirrored Backup Media Sets &#40;SQL Server&#41;</span></span>](mirrored-backup-media-sets-sql-server.md)  
  
  
