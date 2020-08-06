---
title: 성능 기준선 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], baselines
- monitoring performance [SQL Server], baselines
- tuning databases [SQL Server], baselines
- server performance [SQL Server], baselines
- performance [SQL Server], baselines
- baseline performance [SQL Server]
- measurements for baseline statistics [SQL Server]
- monitoring server performance [SQL Server], establishing baseline
- database monitoring [SQL Server], baselines
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0cb85ae8ad370b816c6240b58aabd247c7593c16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729380"
---
# <a name="establish-a-performance-baseline"></a><span data-ttu-id="0e201-102">성능 기준선 설정</span><span class="sxs-lookup"><span data-stu-id="0e201-102">Establish a Performance Baseline</span></span>
  <span data-ttu-id="0e201-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템이 최적으로 실행되고 있는지 판단하려면 먼저 시간을 두고 정기적으로 서버의 성능을 측정하여 서버 성능 기준선을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e201-103">To determine whether your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system is performing optimally, take performance measurements at regular intervals over time, even when no problems occur, to establish a server performance baseline.</span></span> <span data-ttu-id="0e201-104">그런 다음 이전에 측정한 값과 각 새 집합을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="0e201-104">Compare each new set of measurements with those taken earlier.</span></span>  
  
 <span data-ttu-id="0e201-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]성능에 영향을 미치는 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0e201-105">The following areas affect the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="0e201-106">시스템 리소스(하드웨어)</span><span class="sxs-lookup"><span data-stu-id="0e201-106">System resources (hardware)</span></span>  
  
-   <span data-ttu-id="0e201-107">네트워크 아키텍처</span><span class="sxs-lookup"><span data-stu-id="0e201-107">Network architecture</span></span>  
  
-   <span data-ttu-id="0e201-108">운영 체제</span><span class="sxs-lookup"><span data-stu-id="0e201-108">The operating system</span></span>  
  
-   <span data-ttu-id="0e201-109">데이터베이스 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="0e201-109">Database applications</span></span>  
  
-   <span data-ttu-id="0e201-110">클라이언트 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="0e201-110">Client applications</span></span>  
  
 <span data-ttu-id="0e201-111">다음은 기준선 측정을 사용해 확인할 수 있는 기본 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="0e201-111">At a minimum, use baseline measurements to determine:</span></span>  
  
-   <span data-ttu-id="0e201-112">작업량이 많을 때와 많지 않을 때</span><span class="sxs-lookup"><span data-stu-id="0e201-112">Peak and off-peak hours of operation.</span></span>  
  
-   <span data-ttu-id="0e201-113">프로덕션 쿼리 또는 일괄 처리 명령 응답 시간</span><span class="sxs-lookup"><span data-stu-id="0e201-113">Production-query or batch-command response times.</span></span>  
  
-   <span data-ttu-id="0e201-114">데이터베이스 백업 및 복구 완료 시간</span><span class="sxs-lookup"><span data-stu-id="0e201-114">Database backup and restore completion times.</span></span>  
  
 <span data-ttu-id="0e201-115">서버 성능 기준선을 설정한 후 현재 서버의 성능을 기준선 통계와 비교하십시오.</span><span class="sxs-lookup"><span data-stu-id="0e201-115">After you establish a server performance baseline, compare the baseline statistics to current server performance.</span></span> <span data-ttu-id="0e201-116">기준선과 지나치게 많은 차이가 나면 더 자세하게 조사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e201-116">Numbers far above or far below your baseline are candidates for further investigation.</span></span> <span data-ttu-id="0e201-117">이것은 해당 영역에 대한 튜닝 또는 재구성이 필요함을 의미할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e201-117">They may indicate areas in need of tuning or reconfiguration.</span></span> <span data-ttu-id="0e201-118">예를 들어 쿼리 집합을 실행하는 시간이 늘어나면 쿼리를 검사하여 다시 작성할 수 있는지 확인하거나 열 통계 또는 새 인덱스를 추가해야 하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e201-118">For example, if the amount of time to execute a set of queries increases, examine the queries to determine if they can be rewritten, or if column statistics or new indexes must be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e201-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e201-119">See Also</span></span>  
 [<span data-ttu-id="0e201-120">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0e201-120">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
