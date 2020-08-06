---
title: SQL Server, ExecStatistics 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d1a50c97add4708a58b9edc45fd49982b97a51ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647632"
---
# <a name="sql-server-execstatistics-object"></a><span data-ttu-id="0977b-102">SQL Server, ExecStatistics 개체</span><span class="sxs-lookup"><span data-stu-id="0977b-102">SQL Server, ExecStatistics Object</span></span>
  <span data-ttu-id="0977b-103">Microsoft SQL Server의 **SQLServer:ExecStatistics** 개체는 다양한 실행을 모니터링하는 카운터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-103">The **SQLServer:ExecStatistics** object in Microsoft SQL Server provides counters to monitor various executions.</span></span>  
  
 <span data-ttu-id="0977b-104">이 표에서는 SQL Server **Exec Statistics** 카운터를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-104">This table describes the SQL Server **Exec Statistics** counters.</span></span>  
  
|<span data-ttu-id="0977b-105">SQL Server Exec Statistics 카운터</span><span class="sxs-lookup"><span data-stu-id="0977b-105">SQL Server Exec Statistics counters</span></span>|<span data-ttu-id="0977b-106">Description</span><span class="sxs-lookup"><span data-stu-id="0977b-106">Description</span></span>|  
|-----------------------------------------|-----------------|  
|<span data-ttu-id="0977b-107">**Distributed Query**</span><span class="sxs-lookup"><span data-stu-id="0977b-107">**Distributed Query**</span></span>|<span data-ttu-id="0977b-108">분산 쿼리의 실행과 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-108">Statistics relevant to execution of distributed queries.</span></span>|  
|<span data-ttu-id="0977b-109">**DTC calls**</span><span class="sxs-lookup"><span data-stu-id="0977b-109">**DTC calls**</span></span>|<span data-ttu-id="0977b-110">DTC 호출의 실행과 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-110">Statistics relevant to execution of DTC calls.</span></span>|  
|<span data-ttu-id="0977b-111">**Extended Procedures**</span><span class="sxs-lookup"><span data-stu-id="0977b-111">**Extended Procedures**</span></span>|<span data-ttu-id="0977b-112">확장 프로시저의 실행과 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-112">Statistics relevant to execution of extended procedures.</span></span>|  
|<span data-ttu-id="0977b-113">**OLEDB calls**</span><span class="sxs-lookup"><span data-stu-id="0977b-113">**OLEDB calls**</span></span>|<span data-ttu-id="0977b-114">OLEDB 호출의 실행과 관련된 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-114">Statistics relevant to execution of OLEDB calls.</span></span>|  
  
 <span data-ttu-id="0977b-115">개체의 각 카운터는 다음 인스턴스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-115">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="0977b-116">항목</span><span class="sxs-lookup"><span data-stu-id="0977b-116">Item</span></span>|<span data-ttu-id="0977b-117">Description</span><span class="sxs-lookup"><span data-stu-id="0977b-117">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="0977b-118">**평균 실행 시간(ms)**</span><span class="sxs-lookup"><span data-stu-id="0977b-118">**Average execution time (ms)**</span></span>|<span data-ttu-id="0977b-119">선택된 실행 유형의 평균 실행 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-119">Average execution time of the selected type of execution.</span></span>|  
|<span data-ttu-id="0977b-120">**초당 누적 실행 시간(ms)**</span><span class="sxs-lookup"><span data-stu-id="0977b-120">**Cumulative execution time (ms) per second**</span></span>|<span data-ttu-id="0977b-121">선택된 실행 유형의 초당 총 실행 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-121">Aggregated execution time per second, of the selected type of execution.</span></span>|  
|<span data-ttu-id="0977b-122">**진행 중인 실행 작업**</span><span class="sxs-lookup"><span data-stu-id="0977b-122">**Execs in progress**</span></span>|<span data-ttu-id="0977b-123">선택된 실행 유형의 진행 중인 실행 작업 수입니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-123">Number of execs in progress of the selected type of execution.</span></span>|  
|<span data-ttu-id="0977b-124">**초당 시작된 실행 작업**</span><span class="sxs-lookup"><span data-stu-id="0977b-124">**Exec started per second**</span></span>|<span data-ttu-id="0977b-125">선택된 실행 유형의 초당 시작된 실행 작업 수입니다.</span><span class="sxs-lookup"><span data-stu-id="0977b-125">Number of exes started per second of the selected type of execution.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0977b-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0977b-126">See Also</span></span>  
 [<span data-ttu-id="0977b-127">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="0977b-127">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
