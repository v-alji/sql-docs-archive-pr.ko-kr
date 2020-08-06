---
title: 실패 한 파일 추가 작업 문제 해결 (AlwaysOn 가용성 그룹) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary databases [SQL Server], Availability Groups
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2551080c214f18473caa71a3e17797c34fcc943a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741271"
---
# <a name="troubleshoot-a-failed-add-file-operation-alwayson-availability-groups"></a><span data-ttu-id="061fe-102">실패한 파일 추가 작업 문제 해결(AlwaysOn 가용성 그룹)</span><span class="sxs-lookup"><span data-stu-id="061fe-102">Troubleshoot a Failed Add-File Operation (AlwaysOn Availability Groups)</span></span>
  <span data-ttu-id="061fe-103">일부 AlwaysOn 가용성 그룹 배포의 경우 주 복제본을 호스팅하는 시스템과 보조 복제본을 호스팅하는 시스템 간의 파일 경로가 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-103">In some AlwaysOn availability group deployments, file paths differ between the system that hosts the primary replica and systems that host a secondary replica.</span></span> <span data-ttu-id="061fe-104">파일 추가 작업의 파일 경로가 보조 복제본에 존재하지 않는 경우 파일 추가 작업이 기본 데이터베이스에서 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-104">If the file path of an add-file operation does not exist on a secondary replica, the add-file operation will succeed on the primary database.</span></span> <span data-ttu-id="061fe-105">하지만 파일 추가 작업으로 인해 보조 데이터베이스가 일시 중지될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-105">But the add-file operation will cause the secondary database to be suspended.</span></span> <span data-ttu-id="061fe-106">이로 인해 보조 복제본이 NOT SYNCHRONIZING 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-106">This, in turn, causes the secondary replica to enter the NOT SYNCHRONIZING state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="061fe-107">지정된 보조 데이터베이스의 드라이브 문자를 포함한 파일 경로는 가급적 해당 주 데이터베이스의 경로와 동일한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-107">We recommend that, if possible, the file path (including the drive letter) of a given secondary database be identical to the path of the corresponding primary database.</span></span>  
  
## <a name="problem-resolution"></a><span data-ttu-id="061fe-108">문제 해결</span><span class="sxs-lookup"><span data-stu-id="061fe-108">Problem Resolution</span></span>  
 <span data-ttu-id="061fe-109">이 문제를 해결하려면 데이터베이스 소유자가 다음 단계를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-109">To resolve this problem the database owner must complete the following steps:</span></span>  
  
1.  <span data-ttu-id="061fe-110">가용성 그룹에서 보조 데이터베이스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-110">Remove the secondary database from the availability group.</span></span> <span data-ttu-id="061fe-111">자세한 내용은 [가용성 그룹에서 보조 데이터베이스 제거&#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="061fe-111">For more information, see [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="061fe-112">기존 보조 데이터베이스에서 보조 복제본을 호스팅하는 서버 인스턴스에 대한 파일 경로를 지정하고 WITH NORECOVERY 및 WITH MOVE를 사용하여 보조 데이터베이스에 추가된 파일을 포함하는 파일 그룹의 전체 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-112">On the existing secondary database, restore a full backup of the filegroup that contains the added file to the secondary database, using WITH NORECOVERY and WITH MOVE (specifying the file path on the server instance that hosts the secondary replica).</span></span> <span data-ttu-id="061fe-113">자세한 내용은 [데이터베이스를 새 위치로 복원&#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="061fe-113">For more information, see [Restore a Database to a New Location &#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="061fe-114">주 데이터베이스에서 파일 추가 작업을 포함하는 트랜잭션 로그를 백업하고 WITH NORECOVERY 및 WITH MOVE를 사용하여 보조 데이터베이스에서 로그 백업을 수동으로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-114">Back up the transaction log that contains the add-file operation on the primary database, and manually restore the log backup on the secondary database using WITH NORECOVERY and WITH MOVE.</span></span>  
  
4.  <span data-ttu-id="061fe-115">WITH NO RECOVERY를 사용하여 주 데이터베이스에서 다른 처리 중인 로그 백업을 복원하여 가용성 그룹을 다시 조인할 수 있도록 보조 데이터베이스를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-115">Prepare the secondary database for re-joining the availability group, by restoring, WITH NO RECOVERY, any other outstanding log backups from the primary database.</span></span>  
  
5.  <span data-ttu-id="061fe-116">가용성 그룹에 보조 데이터베이스를 다시 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-116">Rejoin the secondary database to the availability group.</span></span> <span data-ttu-id="061fe-117">자세한 내용은 [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)인스턴스에 AlwaysOn 가용성 그룹을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="061fe-117">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061fe-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="061fe-118">See Also</span></span>  
 <span data-ttu-id="061fe-119">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="061fe-119">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="061fe-120">[가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="061fe-120">[Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="061fe-121">[분리된 사용자 문제 해결&#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="061fe-121">[Troubleshoot Orphaned Users &#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span></span>  
 [<span data-ttu-id="061fe-122">삭제&#41;SQL Server AlwaysOn 가용성 그룹 구성 &#40;문제 해결</span><span class="sxs-lookup"><span data-stu-id="061fe-122">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
