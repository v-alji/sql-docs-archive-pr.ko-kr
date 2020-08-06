---
title: 성능 문제 격리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- isolating performance problems [SQL Server]
- monitoring performance [SQL Server], isolating problems
- database monitoring [SQL Server], isolating problems
- tuning databases [SQL Server], isolating problems
- monitoring server performance [SQL Server], isolating problems
- database performance [SQL Server], isolating problems
- server performance [SQL Server], isolating problems
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b42d780a8174ab57d00de72e8b00ef7af0abc17e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732608"
---
# <a name="isolate-performance-problems"></a><span data-ttu-id="eea26-102">성능 문제 격리</span><span class="sxs-lookup"><span data-stu-id="eea26-102">Isolate Performance Problems</span></span>
  <span data-ttu-id="eea26-103">도구를 하나씩 사용하는 것보다는 여러 개의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 Microsoft Windows 도구를 함께 사용하여 데이터베이스 성능 문제를 격리하는 것이 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="eea26-103">It is often more effective to use several [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or Microsoft Windows tools together to isolate database performance problems than to use one tool at a time.</span></span> <span data-ttu-id="eea26-104">예를 들어 실행 계획이라고도 하는 그래픽 실행 계획 기능을 사용하여 쿼리 하나에 발생한 교착 상태를 즉시 인식할 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="eea26-104">For example, the graphical Execution Plan feature, also called Showplan, helps you quickly recognize deadlocks in a single query.</span></span> <span data-ttu-id="eea26-105">그러나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 Windows의 모니터링 기능을 함께 사용하면 다른 성능 문제도 쉽게 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eea26-105">However, you can recognize some other performance problems more easily if you use the monitoring features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows together.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="eea26-106">를 사용하면 Transact-SQL 및 애플리케이션 관련 문제를 모니터링하고 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eea26-106">can be used to monitor and troubleshoot Transact-SQL and application-related problems.</span></span> <span data-ttu-id="eea26-107">시스템 모니터를 사용하면 하드웨어와 그 밖의 시스템 관련 문제를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eea26-107">System Monitor can be used to monitor hardware and other system-related problems.</span></span>  
  
 <span data-ttu-id="eea26-108">문제를 해결하려면 다음 영역을 모니터링하십시오.</span><span class="sxs-lookup"><span data-stu-id="eea26-108">You can monitor the following areas to troubleshoot problems:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="eea26-109">저장 프로시저 또는 사용자 애플리케이션이 제출한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="eea26-109">stored procedures or batches of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements submitted by user applications.</span></span>  
  
-   <span data-ttu-id="eea26-110">차단 잠금이나 교착 상태와 같은 사용자 동작</span><span class="sxs-lookup"><span data-stu-id="eea26-110">User activity, such as blocking locks or deadlocks.</span></span>  
  
-   <span data-ttu-id="eea26-111">디스크 사용과 같은 하드웨어 동작</span><span class="sxs-lookup"><span data-stu-id="eea26-111">Hardware activity, such as disk usage.</span></span>  
  
 <span data-ttu-id="eea26-112">다음과 같은 문제가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eea26-112">Problems can include:</span></span>  
  
-   <span data-ttu-id="eea26-113">잘못 작성된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 비롯한 애플리케이션 개발 오류</span><span class="sxs-lookup"><span data-stu-id="eea26-113">Application development errors involving incorrectly written [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
-   <span data-ttu-id="eea26-114">디스크나 네트워크 관련 오류와 같은 하드웨어 오류</span><span class="sxs-lookup"><span data-stu-id="eea26-114">Hardware errors, such as disk- or network-related errors.</span></span>  
  
-   <span data-ttu-id="eea26-115">잘못 지정된 데이터베이스로 인한 과도한 차단</span><span class="sxs-lookup"><span data-stu-id="eea26-115">Excessive blocking due to an incorrectly designed database.</span></span>  
  
## <a name="tools-for-common-performance-problems"></a><span data-ttu-id="eea26-116">일반적인 성능 문제를 위한 도구</span><span class="sxs-lookup"><span data-stu-id="eea26-116">Tools for Common Performance Problems</span></span>  
 <span data-ttu-id="eea26-117">각 도구를 사용하여 모니터링하거나 튜닝할 성능 문제를 신중하게 선택하는 것 역시 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="eea26-117">Equally important is careful selection of the performance problem that you want each tool to monitor or tune.</span></span> <span data-ttu-id="eea26-118">도구와 유틸리티는 해결할 성능 문제의 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="eea26-118">The tool and the utility depend on the type of performance problem you want to resolve.</span></span>  
  
 <span data-ttu-id="eea26-119">다음 항목에서는 다양한 모니터링 및 튜닝 도구와 이러한 도구로 해결할 수 있는 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eea26-119">The following topics describe a variety of monitoring and tuning tools and the problems they uncover.</span></span>  
  
 [<span data-ttu-id="eea26-120">병목 상태 식별</span><span class="sxs-lookup"><span data-stu-id="eea26-120">Identify Bottlenecks</span></span>](identify-bottlenecks.md)  
  
 [<span data-ttu-id="eea26-121">메모리 사용량 모니터링</span><span class="sxs-lookup"><span data-stu-id="eea26-121">Monitor Memory Usage</span></span>](../performance-monitor/monitor-memory-usage.md)  
  
  
