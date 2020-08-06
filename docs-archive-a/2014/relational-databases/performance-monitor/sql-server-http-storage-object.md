---
title: SQL Server, HTTP_STORAGE_OBJECT | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62cd5b8422213624cfd8609027c477760f682239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647631"
---
# <a name="sql-server-http_storage_object"></a><span data-ttu-id="8475d-102">SQL Server, HTTP_STORAGE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="8475d-102">SQL Server, HTTP_STORAGE_OBJECT</span></span>
  <span data-ttu-id="8475d-103">**SQLServer: HTTP_STORAGE_OBJECT** 성능 개체는 Azure Storage 계정을 모니터링 하는 성능 카운터로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-103">The **SQLServer:HTTP_STORAGE_OBJECT** performance object consists of performance counters that monitor Azure Storage account.</span></span> <span data-ttu-id="8475d-104">[Azure의 SQL Server 데이터 파일](../databases/sql-server-data-files-in-microsoft-azure.md) 기능을 사용 하면 Azure Storage blob에 데이터베이스 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-104">Using [SQL Server Data Files in Azure](../databases/sql-server-data-files-in-microsoft-azure.md) feature, you can store database files in Azure Storage Blobs.</span></span> <span data-ttu-id="8475d-105">이 성능 개체는 각 Azure 스토리지 계정을 각각 다른 드라이브로 취급합니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-105">This performance object treats each Azure Storage account as a different drive.</span></span>  
  
|<span data-ttu-id="8475d-106">카운터 이름</span><span class="sxs-lookup"><span data-stu-id="8475d-106">Counter Name</span></span>|<span data-ttu-id="8475d-107">Description</span><span class="sxs-lookup"><span data-stu-id="8475d-107">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="8475d-108">**Read Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="8475d-108">**Read Bytes/sec**</span></span>|<span data-ttu-id="8475d-109">읽기 작업 중 HTTP 스토리지에서 초당 전송되는 데이터의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-109">Amount of data being transferred from the HTTP storage per second during read operations.</span></span>|  
|<span data-ttu-id="8475d-110">**Write Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="8475d-110">**Write Bytes/sec**</span></span>|<span data-ttu-id="8475d-111">쓰기 작업 중 HTTP 스토리지에서 초당 전송되는 데이터의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-111">Amount of data being transferred from the HTTP storage per second during write operations.</span></span>|  
|<span data-ttu-id="8475d-112">**Total Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="8475d-112">**Total Bytes/sec**</span></span>|<span data-ttu-id="8475d-113">읽기 또는 쓰기 작업 중 HTTP 스토리지에서 초당 전송되는 데이터의 양입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-113">Amount of data being transferred from the HTTP storage per second during read or write operations.</span></span>|  
|<span data-ttu-id="8475d-114">**읽기/초**</span><span class="sxs-lookup"><span data-stu-id="8475d-114">**Reads/sec**</span></span>|<span data-ttu-id="8475d-115">HTTP 스토리지의 초당 읽기 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-115">Number of reads per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="8475d-116">**쓰기/초**</span><span class="sxs-lookup"><span data-stu-id="8475d-116">**Writes/sec**</span></span>|<span data-ttu-id="8475d-117">HTTP 스토리지의 초당 쓰기 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-117">Number of writer per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="8475d-118">**Transfers/sec**</span><span class="sxs-lookup"><span data-stu-id="8475d-118">**Transfers/sec**</span></span>|<span data-ttu-id="8475d-119">HTTP 스토리지의 초당 읽기 및 쓰기 작업 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-119">Number of read and write operations per second on the HTTP storage.</span></span>|  
|<span data-ttu-id="8475d-120">**Avg. Bytes/Read**</span><span class="sxs-lookup"><span data-stu-id="8475d-120">**Avg. Bytes/Read**</span></span>|<span data-ttu-id="8475d-121">읽기당 HTTP 스토리지에서 전송된 평균 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-121">Average number of bytes transferred from the HTTP storage per read.</span></span>|  
|<span data-ttu-id="8475d-122">**Avg. Bytes/Write**</span><span class="sxs-lookup"><span data-stu-id="8475d-122">**Avg. Bytes/Write**</span></span>|<span data-ttu-id="8475d-123">쓰기당 HTTP 스토리지에서 전송된 평균 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-123">Average number of bytes transferred from the HTTP storage per write.</span></span>|  
|<span data-ttu-id="8475d-124">**Avg. Bytes/Transfer**</span><span class="sxs-lookup"><span data-stu-id="8475d-124">**Avg. Bytes/Transfer**</span></span>|<span data-ttu-id="8475d-125">읽기 또는 쓰기 작업 중 HTTP 스토리지에서 전송되는 평균 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-125">Average number of bytes transferred from the HTTP storage during read or write operations.</span></span>|  
|<span data-ttu-id="8475d-126">**Avg. microsec/Read**</span><span class="sxs-lookup"><span data-stu-id="8475d-126">**Avg. microsec/Read**</span></span>|<span data-ttu-id="8475d-127">HTTP 스토리지에서 각 읽기를 수행하는 데 걸리는 평균 마이크로초 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-127">The average number of microseconds it takes to do each read from the HTTP storage.</span></span>|  
|<span data-ttu-id="8475d-128">**Avg. microsec/Write**</span><span class="sxs-lookup"><span data-stu-id="8475d-128">**Avg. microsec/Write**</span></span>|<span data-ttu-id="8475d-129">HTTP 스토리지에서 각 쓰기를 수행하는 데 걸리는 평균 마이크로초 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-129">The average number of microseconds it takes to do each write to the HTTP storage.</span></span>|  
|<span data-ttu-id="8475d-130">**Avg. microsec/Transfer**</span><span class="sxs-lookup"><span data-stu-id="8475d-130">**Avg. microsec/Transfer**</span></span>|<span data-ttu-id="8475d-131">HTTP 스토리지로 각 전송을 수행하는 데 걸리는 평균 마이크로초 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-131">The average number of microseconds it takes to do each transfer to the HTTP storage.</span></span>|  
|<span data-ttu-id="8475d-132">**Outstanding HTTP 스토리지 I/O**</span><span class="sxs-lookup"><span data-stu-id="8475d-132">**Outstanding HTTP Storage I/O**</span></span>|<span data-ttu-id="8475d-133">HTTP 스토리지에 대한 총 미해결 I/O 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-133">The total number of outstanding I/Os towards a HTTP storage.</span></span>|  
|<span data-ttu-id="8475d-134">**HTTP 저장소 i/o 다시 시도/초**</span><span class="sxs-lookup"><span data-stu-id="8475d-134">**HTTP Storage I/O Retry/sec**</span></span>|<span data-ttu-id="8475d-135">HTTP 스토리지로 보낸 초당 재시도 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8475d-135">Number of retry requests sent to the HTTP storage per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8475d-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8475d-136">See Also</span></span>  
 [<span data-ttu-id="8475d-137">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="8475d-137">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
