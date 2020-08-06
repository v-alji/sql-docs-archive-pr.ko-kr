---
title: 디스크 사용량 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 51479b024864322d34dc3b0208e29e93d7454184
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739742"
---
# <a name="monitor-disk-usage"></a><span data-ttu-id="a1596-102">디스크 사용량 모니터링</span><span class="sxs-lookup"><span data-stu-id="a1596-102">Monitor Disk Usage</span></span>
  <span data-ttu-id="a1596-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 Microsoft Windows 운영 체제 I/O(입/출력) 호출을 사용하여 디스크에서 읽기 및 쓰기 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a1596-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses Microsoft Windows operating system input/output (I/O) calls to perform read and write operations on your disk.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a1596-104">에서는 디스크 I/O가 수행되는 시간과 방법을 관리하지만 기본 I/O 작업은 Windows 운영 체제에서 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a1596-104">manages when and how disk I/O is performed, but the Windows operating system performs the underlying I/O operations.</span></span> <span data-ttu-id="a1596-105">I/O 하위 시스템에는 시스템 버스, 디스크 컨트롤러 카드, 디스크, 테이프 드라이브, CD-ROM 드라이브 및 기타 여러 I/O 디바이스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1596-105">The I/O subsystem includes the system bus, disk controller cards, disks, tape drives, CD-ROM drive, and many other I/O devices.</span></span> <span data-ttu-id="a1596-106">디스크 I/O는 시스템에서 자주 병목 현상을 일으킵니다.</span><span class="sxs-lookup"><span data-stu-id="a1596-106">Disk I/O is frequently the cause of bottlenecks in a system.</span></span>  
  
 <span data-ttu-id="a1596-107">디스크 작업 모니터링은 다음 두 가지 핵심 영역으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1596-107">Monitoring disk activity involves two areas of focus:</span></span>  
  
-   <span data-ttu-id="a1596-108">디스크 I/O 모니터링 및 초과 페이징 검색</span><span class="sxs-lookup"><span data-stu-id="a1596-108">Monitoring Disk I/O and Detecting Excess Paging</span></span>  
  
-   <span data-ttu-id="a1596-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 만드는 디스크 작업 격리</span><span class="sxs-lookup"><span data-stu-id="a1596-109">Isolating Disk Activity That [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Creates</span></span>  
  
 <span data-ttu-id="a1596-110">자세한 내용은 [디스크 사용 모니터링](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1596-110">For more information see, [Monitoring Disk Usage](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)</span></span>  
  
  
