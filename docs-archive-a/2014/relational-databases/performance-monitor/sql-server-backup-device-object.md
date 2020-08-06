---
title: SQL Server, Backup Device 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e3126310ad31dcc153fc79508dbfaccf86f5da78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649499"
---
# <a name="sql-server-backup-device-object"></a><span data-ttu-id="df843-102">SQL Server, Backup Device 개체</span><span class="sxs-lookup"><span data-stu-id="df843-102">SQL Server, Backup Device Object</span></span>
  <span data-ttu-id="df843-103">**Backup Device** 개체는 백업 및 복원 작업에 사용되는 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 디바이스를 모니터링하는 카운터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="df843-103">The **Backup Device** object provides counters to monitor Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices used for backup and restore operations.</span></span> <span data-ttu-id="df843-104">디바이스 단위로 백업 및 복원 작업의 처리량, 진행률, 성능 등을 결정하려면 백업 디바이스를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="df843-104">Monitor backup devices when you want to determine the throughput or the progress and performance of your backup and restore operations on a per device basis.</span></span> <span data-ttu-id="df843-105">전체 데이터베이스 백업이나 복원 작업의 처리량을 모니터링하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **데이터베이스** 개체의 **Backup/Restore Throughput/sec** 카운터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="df843-105">To monitor the throughput of the entire database backup or restore operation, use the **Backup/Restore Throughput/sec** counter of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object.</span></span> <span data-ttu-id="df843-106">자세한 내용은 [SQL Server, Databases Object](sql-server-databases-object.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df843-106">For more information, see [SQL Server, Databases Object](sql-server-databases-object.md).</span></span>  
  
 <span data-ttu-id="df843-107">이 테이블에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df843-107">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** counter.</span></span>  
  
|<span data-ttu-id="df843-108">SQL Server Backup Device 카운터</span><span class="sxs-lookup"><span data-stu-id="df843-108">SQL Server Backup Device counters</span></span>|<span data-ttu-id="df843-109">Description</span><span class="sxs-lookup"><span data-stu-id="df843-109">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="df843-110">**Device Throughput Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="df843-110">**Device Throughput Bytes/sec**</span></span>|<span data-ttu-id="df843-111">데이터베이스를 백업하거나 복원하는 데 사용되는 백업 디바이스의 읽기/쓰기 작업 처리량(초당 바이트 수)입니다.</span><span class="sxs-lookup"><span data-stu-id="df843-111">Throughput of read and write operations (in bytes per second) for a backup device used when backing up or restoring databases.</span></span> <span data-ttu-id="df843-112">이 카운터는 백업이나 복원 작업이 실행 중일 때만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="df843-112">This counter exists only while the backup or restore operation is executing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df843-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df843-113">See Also</span></span>  
 <span data-ttu-id="df843-114">[백업 디바이스&#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="df843-114">[Backup Devices &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="df843-115">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="df843-115">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
