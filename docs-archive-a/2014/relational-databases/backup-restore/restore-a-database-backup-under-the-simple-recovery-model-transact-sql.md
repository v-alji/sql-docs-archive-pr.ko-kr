---
title: 단순 복구 모델에서 데이터베이스 백업 복원(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- database restores [SQL Server], full backups
- backing up databases [SQL Server], full backups
- database backups [SQL Server], full backups
- restoring databases [SQL Server], full backups
ms.assetid: a928fa36-e285-476f-9a7b-6840a8bb7283
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e264dd380c3dff40dacc4eb576d34af5195dec01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730760"
---
# <a name="restore-a-database-backup-under-the-simple-recovery-model-transact-sql"></a><span data-ttu-id="97070-102">단순 복구 모델에서 데이터베이스 백업 복원(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="97070-102">Restore a Database Backup Under the Simple Recovery Model (Transact-SQL)</span></span>
  <span data-ttu-id="97070-103">이 항목에서는 전체 데이터베이스 백업을 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-103">This topic explains how to restore a full database backup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="97070-104">이 작업을 수행하려면 복원될 데이터베이스를 현재 사용하고 있는 사람이 전체 데이터베이스 백업을 복원하는 시스템 관리자뿐이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-104">The system administrator restoring the full database backup must be the only person currently using the database to be restored.</span></span>  
  
## <a name="prerequisites-and-recommendations"></a><span data-ttu-id="97070-105">필수 조건 및 권장 사항</span><span class="sxs-lookup"><span data-stu-id="97070-105">Prerequisites and Recommendations</span></span>  
  
-   <span data-ttu-id="97070-106">암호화된 데이터베이스를 복원하려면 데이터베이스를 암호화하는 데 사용된 인증서 또는 비대칭 키에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-106">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="97070-107">인증서 또는 비대칭 키가 없으면 데이터베이스를 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97070-107">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="97070-108">따라서 데이터베이스 암호화 키를 암호화하는 데 사용되는 인증서는 백업이 필요한 동안에는 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-108">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="97070-109">자세한 내용은 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97070-109">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
-   <span data-ttu-id="97070-110">보안을 위해서는 알 수 없거나 신뢰할 수 없는 출처의 데이터베이스는 연결 또는 복원하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="97070-110">For security purposes, we recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="97070-111">이러한 데이터베이스에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 실행하거나 스키마 또는 물리적 데이터베이스 구조를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97070-111">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="97070-112">알 수 없거나 신뢰할 수 없는 소스의 데이터베이스를 사용하기 전에 비프로덕션 서버의 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 를 실행하여 데이터베이스에서 코드(예: 저장 프로시저 또는 다른 사용자 정의 코드)를 시험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="97070-112">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
## <a name="database-compatibility-level-after-upgrade"></a><span data-ttu-id="97070-113">업그레이드 후 데이터베이스 호환성 수준</span><span class="sxs-lookup"><span data-stu-id="97070-113">Database Compatibility Level After Upgrade</span></span>  
 <span data-ttu-id="97070-114">업그레이드 후에는 **tempdb**, **모델**, **msdb** 및 **리소스** 데이터베이스의 호환성 수준이 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 의 호환성 수준으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="97070-114">The compatibility levels of the **tempdb**, **model**, **msdb** and **Resource** databases are set to the compatibility level of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] after upgrade.</span></span> <span data-ttu-id="97070-115">**마스터** 시스템 데이터베이스는 업그레이드 이전의 호환성 수준이 100 미만이 아니었다면 이전 호환성 수준으로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="97070-115">The **master** system database retains the compatibility level it had before upgrade, unless that level was less than 100.</span></span> <span data-ttu-id="97070-116">**마스터** 의 호환성 수준이 업그레이드 이전에 100 미만이었다면 업그레이드 후에는 100으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="97070-116">If the compatibility level of **master** was less than 100 before upgrade, it is set to 100 after upgrade.</span></span>  
  
 <span data-ttu-id="97070-117">사용자 데이터베이스의 호환성 수준이 업그레이드 이전에 100 이상이었다면 업그레이드 후에도 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="97070-117">If the compatibility level of a user database was 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="97070-118">업그레이드 이전에 호환성 수준이 90이었다면 업그레이드된 데이터베이스에서는 호환성 수준이 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 지원되는 가장 낮은 호환성 수준인 100으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="97070-118">If the compatibility level was 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97070-119">새 사용자 데이터베이스는 **모델** 데이터베이스의 호환성 수준을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-119">New user databases will inherit the compatibility level of the **model** database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="97070-120">프로시저</span><span class="sxs-lookup"><span data-stu-id="97070-120">Procedures</span></span>  
  
#### <a name="to-restore-a-full-database-backup"></a><span data-ttu-id="97070-121">전체 데이터베이스 백업을 복원하려면</span><span class="sxs-lookup"><span data-stu-id="97070-121">To restore a full database backup</span></span>  
  
1.  <span data-ttu-id="97070-122">RESTORE DATABASE 문을 실행하여 전체 데이터베이스 백업을 복원합니다. 이때 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-122">Execute the RESTORE DATABASE statement to restore the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="97070-123">복원할 데이터베이스의 이름</span><span class="sxs-lookup"><span data-stu-id="97070-123">The name of the database to restore.</span></span>  
  
    -   <span data-ttu-id="97070-124">복원할 전체 데이터베이스 백업이 있는 백업 디바이스</span><span class="sxs-lookup"><span data-stu-id="97070-124">The backup device from where the full database backup is restored.</span></span>  
  
    -   <span data-ttu-id="97070-125">전체 데이터베이스 백업을 복원한 후 적용할 트랜잭션 로그 또는 차등 데이터베이스 백업이 있을 경우 NORECOVERY 절</span><span class="sxs-lookup"><span data-stu-id="97070-125">The NORECOVERY clause if you have a transaction log or differential database backup to apply after restoring the full database backup.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="97070-126">암호화된 데이터베이스를 복원하려면 데이터베이스를 암호화하는 데 사용된 인증서 또는 비대칭 키에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-126">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="97070-127">인증서 또는 비대칭 키가 없으면 데이터베이스를 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97070-127">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="97070-128">따라서 데이터베이스 암호화 키를 암호화하는 데 사용되는 인증서는 백업이 필요한 동안에는 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-128">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="97070-129">자세한 내용은 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97070-129">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="97070-130">필요에 따라 다음을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97070-130">Optionally, specify:</span></span>  
  
    -   <span data-ttu-id="97070-131">복원할 백업 디바이스의 백업 세트를 식별하기 위한 FILE 절</span><span class="sxs-lookup"><span data-stu-id="97070-131">The FILE clause to identify the backup set on the backup device to restore.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97070-132">이전 버전 데이터베이스를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 복원하면 데이터베이스가 자동으로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="97070-132">If you restore an earlier version database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is automatically upgraded.</span></span> <span data-ttu-id="97070-133">일반적으로 데이터베이스는 즉시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97070-133">Typically, the database becomes available immediately.</span></span> <span data-ttu-id="97070-134">그러나 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터베이스에 전체 텍스트 인덱스가 있는 경우 업그레이드 프로세스는  **upgrade_option** 서버 속성의 설정에 따라 인덱스를 가져오거나 다시 설정하거나 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-134">However, if a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the  **upgrade_option** server property.</span></span> <span data-ttu-id="97070-135">업그레이드 옵션이 가져오기(**upgrade_option** = 2) 또는 다시 작성(**upgrade_option** = 0)으로 설정되어 있는 경우 업그레이드하는 동안 전체 텍스트 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97070-135">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="97070-136">인덱싱되는 데이터 양에 따라 가져오기 작업은 몇 시간씩 걸릴 수 있으며 다시 작성 작업은 10배 정도 더 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97070-136">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="97070-137">업그레이드 옵션이 가져오기로 설정되어 있으면 전체 텍스트 카탈로그를 사용할 수 없는 경우 관련된 전체 텍스트 인덱스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="97070-137">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="97070-138">**upgrade_option** 서버 속성의 설정을 변경하려면 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-138">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97070-139">예제</span><span class="sxs-lookup"><span data-stu-id="97070-139">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="97070-140">Description</span><span class="sxs-lookup"><span data-stu-id="97070-140">Description</span></span>  
 <span data-ttu-id="97070-141">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 전체 데이터베이스 백업을 테이프에서 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="97070-141">This example restores the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] full database backup from tape.</span></span>  
  
### <a name="example"></a><span data-ttu-id="97070-142">예제</span><span class="sxs-lookup"><span data-stu-id="97070-142">Example</span></span>  
  
```  
USE master;  
GO  
RESTORE DATABASE AdventureWorks2012  
   FROM TAPE = '\\.\Tape0';  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="97070-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97070-143">See Also</span></span>  
 <span data-ttu-id="97070-144">[전체 데이터베이스 복원&#40;전체 복구 모델&#41;](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="97070-144">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="97070-145">[전체 데이터베이스 복원&#40;단순 복구 모델&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="97070-145">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="97070-146">[전체 데이터베이스 백업&#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97070-146">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="97070-147">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="97070-147">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="97070-148">[백업 기록 및 헤더 정보&#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97070-148">[Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span></span>  
 [<span data-ttu-id="97070-149">시스템 데이터베이스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="97070-149">Rebuild System Databases</span></span>](../databases/system-databases.md)  
  
  
