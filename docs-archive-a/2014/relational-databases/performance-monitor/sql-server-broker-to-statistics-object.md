---
title: SQL Server, Broker TO Statistics 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 93d9c24a175dedfee171eccfccb34673501660ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653813"
---
# <a name="sql-server-broker-to-statistics-object"></a><span data-ttu-id="e3837-102">SQL Server, Broker TO Statistics 개체</span><span class="sxs-lookup"><span data-stu-id="e3837-102">SQL Server, Broker TO Statistics Object</span></span>
  <span data-ttu-id="e3837-103">SQLServer:Broker TO Statistics 성능 개체는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 대화 상자에서 전송 개체를 요청하는 횟수와 전송 개체가 **tempdb**에 기록되는 빈도에 대한 정보를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-103">The SQLServer:Broker TO Statistics performance object reports information about how many times [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialogs request transmission objects, and how often transmission objects are written to **tempdb**.</span></span>  
  
 <span data-ttu-id="e3837-104">전송 개체는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 대화의 메시지 전송 상태를 기록하고,</span><span class="sxs-lookup"><span data-stu-id="e3837-104">Transmission objects record the state of message transmissions for a [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialog.</span></span> <span data-ttu-id="e3837-105">메모리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-105">They are stored in memory.</span></span> <span data-ttu-id="e3837-106">메모리를 늘리기 위해 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 는 정기적으로 비활성 전송 개체의 일괄 처리를 **tempdb**의 작업 테이블에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-106">To free memory, [!INCLUDE[ssSB](../../includes/sssb-md.md)] periodically writes batches of inactive transmission objects to work tables in **tempdb**.</span></span>  
  
 <span data-ttu-id="e3837-107">다음 표에서는 이 개체가 포함하는 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-107">The following table lists the counters that this object contains.</span></span>  
  
|<span data-ttu-id="e3837-108">SQL Server Broker TO Statistics 카운터</span><span class="sxs-lookup"><span data-stu-id="e3837-108">SQL Server Broker TO Statistics counters</span></span>|<span data-ttu-id="e3837-109">Description</span><span class="sxs-lookup"><span data-stu-id="e3837-109">Description</span></span>|  
|----------------------------------------------|-----------------|  
|<span data-ttu-id="e3837-110">**Avg. Length of Batched Writes**</span><span class="sxs-lookup"><span data-stu-id="e3837-110">**Avg. Length of Batched Writes**</span></span>|<span data-ttu-id="e3837-111">일괄 처리에 저장되는 평균 전송 개체 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-111">The average number of transmission objects saved in a batch.</span></span>|  
|<span data-ttu-id="e3837-112">**Avg. Time To Write Batch (ms)**</span><span class="sxs-lookup"><span data-stu-id="e3837-112">**Avg. Time To Write Batch (ms)**</span></span>|<span data-ttu-id="e3837-113">전송 개체 일괄 처리를 저장하는 데 필요한 평균 시간(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-113">The average number of milliseconds required to save a batch of transmission objects.</span></span>|  
|<span data-ttu-id="e3837-114">**Avg. Time Between Batches (ms)**</span><span class="sxs-lookup"><span data-stu-id="e3837-114">**Avg. Time Between Batches (ms)**</span></span>|<span data-ttu-id="e3837-115">전송 개체의 일괄 처리 기록 간 평균 시간(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-115">The average number of milliseconds between writes of transmission object batches.</span></span>|  
|<span data-ttu-id="e3837-116">**Tran Object Gets/sec**</span><span class="sxs-lookup"><span data-stu-id="e3837-116">**Tran Object Gets/sec**</span></span>|<span data-ttu-id="e3837-117">대화에서 전송 개체를 요청한 초당 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-117">The number of times per second that dialogs requested transmission objects.</span></span>|  
|<span data-ttu-id="e3837-118">**Tran Objects Marked Dirty/sec**</span><span class="sxs-lookup"><span data-stu-id="e3837-118">**Tran Objects Marked Dirty/sec**</span></span>|<span data-ttu-id="e3837-119">전송 개체가 커밋되지 않은 것으로 표시된 초당 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-119">The number of times per second that transmission objects were marked as dirty.</span></span> <span data-ttu-id="e3837-120">전송 개체는 처음 수정하면 커밋된 것으로 표시되어 메모리 내장 복사본이 **tempdb**에 저장된 복사본과 달라지게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-120">Transmission objects are marked as dirty by the first modification that causes the in-memory copy to differ from the copy stored in **tempdb**.</span></span> <span data-ttu-id="e3837-121">전송 개체는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 가 대화의 메시지 전송 상태에 변경 사항을 기록할 때 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-121">Transmission objects are modified when [!INCLUDE[ssSB](../../includes/sssb-md.md)] has to record a change in the state of message transmissions for the dialog.</span></span>|  
|<span data-ttu-id="e3837-122">**Tran Object Writes/sec**</span><span class="sxs-lookup"><span data-stu-id="e3837-122">**Tran Object Writes/sec**</span></span>|<span data-ttu-id="e3837-123">전송 개체의 일괄 처리가 **tempdb** 작업 테이블에 기록된 초당 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-123">The number of times per second that a batch of transmission objects were written to **tempdb** work tables.</span></span> <span data-ttu-id="e3837-124">기록된 횟수가 많으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리가 스트레스 상태임을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3837-124">Large numbers of writes could indicate that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory is being stressed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3837-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3837-125">See Also</span></span>  
 <span data-ttu-id="e3837-126">[SQL Server, Access Methods 개체](sql-server-access-methods-object.md) </span><span class="sxs-lookup"><span data-stu-id="e3837-126">[SQL Server, Access Methods Object](sql-server-access-methods-object.md) </span></span>  
 <span data-ttu-id="e3837-127">[SQL Server, Memory Manager 개체](sql-server-memory-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="e3837-127">[SQL Server, Memory Manager Object](sql-server-memory-manager-object.md) </span></span>  
 [<span data-ttu-id="e3837-128">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="e3837-128">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
