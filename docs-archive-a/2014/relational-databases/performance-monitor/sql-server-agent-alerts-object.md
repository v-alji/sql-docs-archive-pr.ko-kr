---
title: SQL Server 에이전트, Alerts 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9aa6fa871730af8cf129b3ea6b0aa4f1853d7e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648347"
---
# <a name="sql-server-agent-alerts-object"></a><span data-ttu-id="f09b4-102">SQL Server 에이전트, Alerts 개체</span><span class="sxs-lookup"><span data-stu-id="f09b4-102">SQL Server Agent, Alerts Object</span></span>
  <span data-ttu-id="f09b4-103">SQL Server 에이전트 **Alerts** 성능 개체는 SQL Server 에이전트 경고에 대한 정보를 보고하는 성능 카운터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f09b4-103">The SQL Server Agent **Alerts** performance object contains performance counters that report information about SQL Server Agent alerts.</span></span> <span data-ttu-id="f09b4-104">다음 표에서는 이 개체가 포함하는 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f09b4-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="f09b4-105">다음 표에서는 **SQLAgent:Alerts** 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f09b4-105">The table below contains the **SQLAgent:Alerts** counters.</span></span>  
  
|<span data-ttu-id="f09b4-106">Name</span><span class="sxs-lookup"><span data-stu-id="f09b4-106">Name</span></span>|<span data-ttu-id="f09b4-107">Description</span><span class="sxs-lookup"><span data-stu-id="f09b4-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="f09b4-108">**Activated alerts**</span><span class="sxs-lookup"><span data-stu-id="f09b4-108">**Activated alerts**</span></span>|<span data-ttu-id="f09b4-109">이 카운터는 SQL Server 에이전트가 마지막으로 다시 시작된 이후 SQL Server 에이전트가 활성화한 총 경고 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f09b4-109">This counter reports the total number of alerts that SQL Server Agent has activated since the last time that SQL Server Agent restarted.</span></span>|  
|<span data-ttu-id="f09b4-110">**Alerts activated/minute**</span><span class="sxs-lookup"><span data-stu-id="f09b4-110">**Alerts activated/minute**</span></span>|<span data-ttu-id="f09b4-111">이 카운터는 마지막 시간(분) 내에 SQL Server 에이전트가 활성화한 경고의 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f09b4-111">This counter reports the number of alerts that SQL Server Agent activated within the last minute.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f09b4-112">이 SQL Server 에이전트 개체를 사용하려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f09b4-112">To use this SQL Server Agent object, users must be a member of the **sysadmin** fixed server role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f09b4-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f09b4-113">See Also</span></span>  
 <span data-ttu-id="f09b4-114">[Alerts](../../ssms/agent/alerts.md) </span><span class="sxs-lookup"><span data-stu-id="f09b4-114">[Alerts](../../ssms/agent/alerts.md) </span></span>  
 <span data-ttu-id="f09b4-115">[성능 개체 사용](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="f09b4-115">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="f09b4-116">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="f09b4-116">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
