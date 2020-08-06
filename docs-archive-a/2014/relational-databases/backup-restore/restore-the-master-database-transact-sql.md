---
title: master 데이터베이스 복원(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], restoring
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c9cb078b7af60fc5e060bcb144fc9cbaee8ecf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653453"
---
# <a name="restore-the-master-database-transact-sql"></a><span data-ttu-id="8ce4d-102">master 데이터베이스 복원(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8ce4d-102">Restore the master Database (Transact-SQL)</span></span>
  <span data-ttu-id="8ce4d-103">이 항목에서는 전체 데이터베이스 백업에서 **master** 데이터베이스를 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-103">This topic explains how to restore the **master** database from a full database backup.</span></span>  
  
### <a name="to-restore-the-master-database"></a><span data-ttu-id="8ce4d-104">master 데이터베이스를 복원하려면</span><span class="sxs-lookup"><span data-stu-id="8ce4d-104">To restore the master database</span></span>  
  
1.  <span data-ttu-id="8ce4d-105">서버 인스턴스를 단일 사용자 모드로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-105">Start the server instance in single-user mode.</span></span>  
  
     <span data-ttu-id="8ce4d-106">단일 사용자 시작 매개 변수( **-m**)를 지정하는 방법은 [서버 시작 옵션 구성&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-106">For information about how to specify the single-user startup parameter (**-m**), see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).</span></span>  
  
2.  <span data-ttu-id="8ce4d-107">**master**의 전체 데이터베이스 백업을 복원하려면 다음 [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-107">To restore a full database backup of **master**, use the following [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
     <span data-ttu-id="8ce4d-108">`RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`</span><span class="sxs-lookup"><span data-stu-id="8ce4d-108">`RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`</span></span>  
  
     <span data-ttu-id="8ce4d-109">REPLACE 옵션은 동일한 이름을 가진 데이터베이스가 이미 있는 경우에도 지정된 데이터베이스를 복원하도록 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-109">The REPLACE option instructs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to restore the specified database even when a database of the same name already exists.</span></span> <span data-ttu-id="8ce4d-110">이 경우 기존 데이터베이스는 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-110">The existing database, if any, is deleted.</span></span> <span data-ttu-id="8ce4d-111">단일 사용자 모드에서는 [sqlcmd 유틸리티](../../tools/sqlcmd-utility.md)에 RESTORE DATABASE 문을 입력하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-111">In single-user mode, we recommend that you enter the RESTORE DATABASE statement in the [sqlcmd utility](../../tools/sqlcmd-utility.md).</span></span> <span data-ttu-id="8ce4d-112">자세한 내용은 [sqlcmd 유틸리티 사용](../scripting/sqlcmd-use-the-utility.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-112">For more information, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8ce4d-113">**마스터** 를 복원한 후 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 종료되고 **sqlcmd** 프로세스가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-113">After **master** is restored, the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] shuts down and terminates the **sqlcmd** process.</span></span> <span data-ttu-id="8ce4d-114">서버 인스턴스를 다시 시작하기 전에 단일 사용자 시작 매개 변수를 제거하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-114">Before you restart the server instance, remove the single-user startup parameter.</span></span> <span data-ttu-id="8ce4d-115">자세한 내용은 [서버 시작 옵션 구성&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-115">For more information, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).</span></span>  
  
3.  <span data-ttu-id="8ce4d-116">서버 인스턴스를 다시 시작하고 다른 데이터베이스 복원, 데이터베이스 연결 및 사용자 불일치 교정 등의 기타 복구 단계를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-116">Restart the server instance and continue other recovery steps such as restoring other databases, attaching databases, and correcting user mismatches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ce4d-117">예제</span><span class="sxs-lookup"><span data-stu-id="8ce4d-117">Example</span></span>  
 <span data-ttu-id="8ce4d-118">다음 예에서는 기본 서버 인스턴스에 `master` 데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-118">The following example restores the `master` database on the default server instance.</span></span> <span data-ttu-id="8ce4d-119">이 예에서는 서버 인스턴스가 이미 단일 사용자 모드로 실행되고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-119">The example assumes that the server instance is already running in single-user mode.</span></span> <span data-ttu-id="8ce4d-120">다음 예에서는 `sqlcmd` 를 시작하고 디스크 디바이스에서 `RESTORE DATABASE` 의 전체 데이터베이스 백업을 복원하는 `master` 문을 실행합니다. `Z:\SQLServerBackups\master.bak`</span><span class="sxs-lookup"><span data-stu-id="8ce4d-120">The example starts `sqlcmd` and executes a `RESTORE DATABASE` statement that restores a full database backup of `master` from a disk device: `Z:\SQLServerBackups\master.bak`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ce4d-121">명명된 인스턴스의 경우 **sqlcmd** 명령은 **-S** _\<ComputerName>_ \\ *\<InstanceName>* 옵션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ce4d-121">For a named instance, the **sqlcmd** command must specify the **-S**_\<ComputerName>_\\*\<InstanceName>* option.</span></span>  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ce4d-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ce4d-122">See Also</span></span>  
 <span data-ttu-id="8ce4d-123">[전체 데이터베이스 복원&#40;단순 복구 모델&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4d-123">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="8ce4d-124">[전체 데이터베이스 복원&#40;전체 복구 모델&#41;](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4d-124">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="8ce4d-125">[분리된 사용자 문제 해결&#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4d-125">[Troubleshoot Orphaned Users &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span></span>  
 <span data-ttu-id="8ce4d-126">[데이터베이스 분리 및 연결&#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4d-126">[Database Detach and Attach &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="8ce4d-127">[시스템 데이터베이스 다시 작성](../databases/system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4d-127">[Rebuild System Databases](../databases/system-databases.md) </span></span>  
 <span data-ttu-id="8ce4d-128">[데이터베이스 엔진 서비스 시작 옵션](../../database-engine/configure-windows/database-engine-service-startup-options.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4d-128">[Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md) </span></span>  
 <span data-ttu-id="8ce4d-129">[SQL Server 구성 관리자](../sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4d-129">[SQL Server Configuration Manager](../sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="8ce4d-130">[시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8ce4d-130">[Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span></span>  
 <span data-ttu-id="8ce4d-131">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8ce4d-131">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="8ce4d-132">단일 사용자 모드로 SQL Server 시작</span><span class="sxs-lookup"><span data-stu-id="8ce4d-132">Start SQL Server in Single-User Mode</span></span>](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
