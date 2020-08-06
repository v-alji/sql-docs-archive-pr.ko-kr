---
title: optimize for ad hoc workloads 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- optimize for ad hoc workloads option
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b217e48d6e4b0ffa0f687ff170f16d4d77ad17d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729803"
---
# <a name="optimize-for-ad-hoc-workloads-server-configuration-option"></a><span data-ttu-id="d0090-102">optimize for ad hoc workloads 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="d0090-102">optimize for ad hoc workloads Server Configuration Option</span></span>
  <span data-ttu-id="d0090-103">**optimize for ad hoc workloads** 옵션은 여러 개의 일회용 임시 일괄 처리를 포함하는 작업에서 계획 캐시의 효율성을 높이는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-103">The **optimize for ad hoc workloads** option is used to improve the efficiency of the plan cache for workloads that contain many single use ad hoc batches.</span></span> <span data-ttu-id="d0090-104">이 옵션을 1로 설정하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 일괄 처리가 처음으로 컴파일되었을 때 전체 컴파일된 계획 대신 계획 캐시에 포함된 작은 컴파일된 계획 스텁을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-104">When this option is set to 1, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores a small compiled plan stub in the plan cache when a batch is compiled for the first time, instead of the full compiled plan.</span></span> <span data-ttu-id="d0090-105">이렇게 하면 계획 캐시에 다시 사용할 수 없는 컴파일된 계획이 채워지지 않게 되므로 메모리 가중을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-105">This helps to relieve memory pressure by not allowing the plan cache to become filled with compiled plans that are not reused.</span></span>  
  
 <span data-ttu-id="d0090-106">컴파일된 계획 스텁은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 이러한 임시 일괄 처리가 이전에 컴파일되었지만 컴파일된 계획 스텁만 저장했다는 것을 인식하게 함으로써 이 일괄 처리(컴파일 또는 실행된)가 다시 호출될 때 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 일괄 처리를 컴파일하고, 계획 캐시에서 컴파일된 계획 스텁을 제거하고, 계획 캐시에 전체 컴파일된 계획을 추가하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-106">The compiled plan stub allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to recognize that this ad hoc batch has been compiled before but has only stored a compiled plan stub, so when this batch is invoked (compiled or executed) again, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] compiles the batch, removes the compiled plan stub from the plan cache, and adds the full compiled plan to the plan cache.</span></span>  
  
 <span data-ttu-id="d0090-107">**optimize for ad hoc workloads** 를 1로 설정하면 새 계획만 영향을 받으며, 이미 계획 캐시에 있던 계획은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-107">Setting the **optimize for ad hoc workloads** to 1 affects only new plans; plans that are already in the plan cache are unaffected.</span></span>  
  
 <span data-ttu-id="d0090-108">컴파일된 계획 스텁은 sys.dm_exec_cached_plans 카탈로그 뷰로 표시되는 cacheobjtype 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-108">The compiled plan stub is one of the cacheobjtypes displayed by the sys.dm_exec_cached_plans catalog view.</span></span> <span data-ttu-id="d0090-109">여기에는 고유한 SQL 핸들 및 계획 핸들이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-109">It has a unique sql handle and plan handle.</span></span> <span data-ttu-id="d0090-110">컴파일된 계획 스텁에는 연결된 실행 계획이 없으며 계획 핸들을 쿼리해도 XML 실행 계획이 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-110">The compiled plan stub does not have an execution plan associated with it and querying for the plan handle will not return an XML Showplan.</span></span>  
  
 <span data-ttu-id="d0090-111">추적 플래그 8032는 일반적으로 캐시가 더 커지도록 허용하는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] RTM 설정으로 캐시 제한 매개 변수를 복구합니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-111">Trace flag 8032 reverts the cache limit parameters to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] RTM setting which in general allows caches to be larger.</span></span> <span data-ttu-id="d0090-112">자주 재사용 되는 캐시 항목이 캐시 *에 맞지 않고 임시 작업을 위해 최적화 서버 구성 옵션* 으로 계획 캐시 관련 문제를 해결 하지 못한 경우이 설정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-112">Use this setting when frequently reused cache entries do not fit into the cache and when the *optimize for ad hoc workloads Server Configuration Option* has failed to resolve the problem with plan cache.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="d0090-113">추적 플래그 8032는 대형 캐시로 버퍼 풀과 같은 다른 메모리 소비자에 제공되는 메모리가 줄어들 수 있는 성능 문제를 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0090-113">Trace flag 8032 can cause poor performance if large caches make less memory available for other memory consumers, such as the buffer pool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0090-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0090-114">See Also</span></span>  
 <span data-ttu-id="d0090-115">[sys.dm_exec_cached_plans&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d0090-115">[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql) </span></span>  
 [<span data-ttu-id="d0090-116">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d0090-116">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
