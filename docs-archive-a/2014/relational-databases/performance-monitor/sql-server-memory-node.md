---
title: SQL Server, Memory Node | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5bbc3f581ea9ececeb7d55a614ef27c3c72de7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660508"
---
# <a name="sql-server-memory-node"></a><span data-ttu-id="951f5-102">SQL Server, Memory Node</span><span class="sxs-lookup"><span data-stu-id="951f5-102">SQL Server, Memory Node</span></span>
  <span data-ttu-id="951f5-103">Microsoft **의** Memory Node [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체는 NUMA 노드의 서버 메모리 사용량을 모니터링하는 카운터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="951f5-103">The **Memory Node** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor server memory usage on NUMA nodes.</span></span>  
  
## <a name="memory-node-counters"></a><span data-ttu-id="951f5-104">Memory Node 카운터</span><span class="sxs-lookup"><span data-stu-id="951f5-104">Memory Node Counters</span></span>  
 <span data-ttu-id="951f5-105">다음 테이블에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="951f5-105">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** counters.</span></span>  
  
|<span data-ttu-id="951f5-106">SQL Server Memory Manager 카운터</span><span class="sxs-lookup"><span data-stu-id="951f5-106">SQL Server Memory Manager counters</span></span>|<span data-ttu-id="951f5-107">Description</span><span class="sxs-lookup"><span data-stu-id="951f5-107">Description</span></span>|  
|----------------------------------------|-----------------|  
|<span data-ttu-id="951f5-108">**Database Node Memory(KB)**</span><span class="sxs-lookup"><span data-stu-id="951f5-108">**Database Node Memory (KB)**</span></span>|<span data-ttu-id="951f5-109">서버가 현재 이 노드에서 데이터베이스 페이지에 사용 중인 메모리의 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="951f5-109">Specifies the amount of memory the server is currently using on this node for database pages.</span></span>|  
|<span data-ttu-id="951f5-110">**Free Node Memory(KB)**</span><span class="sxs-lookup"><span data-stu-id="951f5-110">**Free Node Memory (KB)**</span></span>|<span data-ttu-id="951f5-111">서버가 이 노드에서 사용하고 있지 않은 메모리의 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="951f5-111">Specifies the amount of memory the server is not using on this node.</span></span>|  
|<span data-ttu-id="951f5-112">**Foreign Node Memory(KB)**</span><span class="sxs-lookup"><span data-stu-id="951f5-112">**Foreign Node Memory (KB)**</span></span>|<span data-ttu-id="951f5-113">이 노드의 비-NUMA 로컬 메모리의 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="951f5-113">Specifies the amount of non NUMA-local memory on this node.</span></span>|  
|<span data-ttu-id="951f5-114">**Stolen Memory Node(KB)**</span><span class="sxs-lookup"><span data-stu-id="951f5-114">**Stolen Memory Node (KB)**</span></span>|<span data-ttu-id="951f5-115">서버가 이 노드에서 데이터베이스 페이지가 아닌 다른 용도로 사용 중인 메모리의 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="951f5-115">Specifies the amount of memory the server is using on this node for purposes other than database pages.</span></span>|  
|<span data-ttu-id="951f5-116">**Target Node Memory**</span><span class="sxs-lookup"><span data-stu-id="951f5-116">**Target Node Memory**</span></span>|<span data-ttu-id="951f5-117">이 노드에 적합한 메모리의 양을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="951f5-117">Specifies the ideal amount of memory for this node.</span></span>|  
|<span data-ttu-id="951f5-118">**Total Node Memory**</span><span class="sxs-lookup"><span data-stu-id="951f5-118">**Total Node Memory**</span></span>|<span data-ttu-id="951f5-119">서버가 이 노드에서 커밋한 총 메모리의 양을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="951f5-119">Indicates the total amount of memory the server has committed on this node.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="951f5-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="951f5-120">See Also</span></span>  
 <span data-ttu-id="951f5-121">[리소스 사용 모니터링&#40;시스템 모니터&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="951f5-121">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="951f5-122">[SQL Server, Buffer Manager 개체](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="951f5-122">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="951f5-123">sys.dm_os_performance_counters&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="951f5-123">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
