---
title: SQL Server, Latches 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f49ac00114065e971c0893f9217ab883eb2d7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647629"
---
# <a name="sql-server-latches-object"></a><span data-ttu-id="cd405-102">SQL Server, Latches 개체</span><span class="sxs-lookup"><span data-stu-id="cd405-102">SQL Server, Latches Object</span></span>
  <span data-ttu-id="cd405-103">Microsoft **의** SQLServer:Latches [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체는 래치라고 하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내부 리소스 잠금을 모니터링하는 카운터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cd405-103">The **SQLServer:Latches** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor internal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource locks called latches.</span></span> <span data-ttu-id="cd405-104">래치를 모니터링하면 사용자 동작 및 리소스 사용을 확인해 성능 병목 상태를 찾아낼 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="cd405-104">Monitoring the latches to determine user activity and resource usage can help you to identify performance bottlenecks.</span></span>  
  
 <span data-ttu-id="cd405-105">이 테이블에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cd405-105">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** counters.</span></span>  
  
|<span data-ttu-id="cd405-106">SQL Server Latches 카운터</span><span class="sxs-lookup"><span data-stu-id="cd405-106">SQL Server Latches counters</span></span>|<span data-ttu-id="cd405-107">Description</span><span class="sxs-lookup"><span data-stu-id="cd405-107">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="cd405-108">**Average Latch Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="cd405-108">**Average Latch Wait Time (ms)**</span></span>|<span data-ttu-id="cd405-109">기다린 래치 요청에 대한 밀리초 단위의 평균 래치 대기 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="cd405-109">Average latch wait time (in milliseconds) for latch requests that had to wait.</span></span>|  
|<span data-ttu-id="cd405-110">**Latch Waits/sec**</span><span class="sxs-lookup"><span data-stu-id="cd405-110">**Latch Waits/sec**</span></span>|<span data-ttu-id="cd405-111">즉시 충족시킬 수 없는 래치 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="cd405-111">Number of latch requests that could not be granted immediately.</span></span>|  
|<span data-ttu-id="cd405-112">**Number of SuperLatches**</span><span class="sxs-lookup"><span data-stu-id="cd405-112">**Number of SuperLatches**</span></span>|<span data-ttu-id="cd405-113">현재 SuperLatches인 래치 수입니다.</span><span class="sxs-lookup"><span data-stu-id="cd405-113">Number of latches that are currently SuperLatches.</span></span>|  
|<span data-ttu-id="cd405-114">**SuperLatch Demotions/sec**</span><span class="sxs-lookup"><span data-stu-id="cd405-114">**SuperLatch Demotions/sec**</span></span>|<span data-ttu-id="cd405-115">마지막 1초 동안 일반 래치로 강등된 SuperLatches 수 입니다.</span><span class="sxs-lookup"><span data-stu-id="cd405-115">Number of SuperLatches that have been demoted to regular latches in the last second.</span></span>|  
|<span data-ttu-id="cd405-116">**SuperLatch Promotions/sec**</span><span class="sxs-lookup"><span data-stu-id="cd405-116">**SuperLatch Promotions/sec**</span></span>|<span data-ttu-id="cd405-117">마지막 1초 동안 SuperLatches로 승격된 래치 수입니다.</span><span class="sxs-lookup"><span data-stu-id="cd405-117">Number of latches that have been promoted to SuperLatches in the last second.</span></span>|  
|<span data-ttu-id="cd405-118">**Total Latch Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="cd405-118">**Total Latch Wait Time (ms)**</span></span>|<span data-ttu-id="cd405-119">마지막 1초 동안 기다렸던 래치 요청에 대한 밀리초 단위의 총 래치 대기 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="cd405-119">Total latch wait time (in milliseconds) for latch requests in the last second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd405-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd405-120">See Also</span></span>  
 [<span data-ttu-id="cd405-121">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="cd405-121">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
