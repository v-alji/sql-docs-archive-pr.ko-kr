---
title: 시스템 모니터 실행 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3dd0baf32402d69e36dc5120d0259b2f8d689897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739723"
---
# <a name="run-system-monitor"></a><span data-ttu-id="05088-102">시스템 모니터 실행</span><span class="sxs-lookup"><span data-stu-id="05088-102">Run System Monitor</span></span>
  <span data-ttu-id="05088-103">시스템 모니터는 RPC(원격 프로시저 호출)를 사용하여 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 정보를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05088-103">System Monitor uses remote procedure calls (RPCs) to collect information from Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05088-104">Microsoft Windows에서 시스템 모니터를 실행할 권한을 가진 모든 사용자는 시스템 모니터를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05088-104">Any user who has Microsoft Windows permissions to run System Monitor can use System Monitor to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05088-105">시스템 모니터 또는 성능 모니터를 사용하면 Windows 98에서 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05088-105">When using System Monitor or Performance Monitor, you cannot connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on Windows 98.</span></span>  
  
 <span data-ttu-id="05088-106">시스템 모니터를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 모니터링하면 다른 성능 모니터링 도구로 모니터링할 때와 마찬가지로 성능 오버헤드가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05088-106">As with all performance monitoring tools, expect some performance overhead when you use System Monitor to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05088-107">특정 인스턴스에서 실제 오버헤드의 발생 여부는 하드웨어 플랫폼, 카운터 수, 선택된 업데이트 간격에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="05088-107">The actual overhead in any specific instance depends on the hardware platform, the number of counters, and the selected update interval.</span></span> <span data-ttu-id="05088-108">그러나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 시스템 모니터가 통합되면서 성능 감소를 최소화하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="05088-108">However, the integration of System Monitor with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is designed to minimize any reduction in performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05088-109">시스템 모니터 스냅인에서 모니터링할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 성능 카운터를 선택했으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 실행되지 않은 경우에도 해당 카운터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05088-109">If you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performance counters to monitor in the System Monitor snap-in, you will see the counters even if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running.</span></span>  
  
 <span data-ttu-id="05088-110">시스템 모니터를 시작하는 방법은 [시스템 모니터 시작&#40;Windows&#41;](../performance/start-system-monitor-windows.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05088-110">For information about starting System Monitor, see [Start System Monitor &#40;Windows&#41;](../performance/start-system-monitor-windows.md).</span></span>  
  
  
