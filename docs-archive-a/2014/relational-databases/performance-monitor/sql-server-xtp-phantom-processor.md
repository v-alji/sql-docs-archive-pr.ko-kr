---
title: XTP 가상 프로세서 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 14158b7097427b6704cf5e747fa998a11217ecd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730568"
---
# <a name="xtp-phantom-processor"></a><span data-ttu-id="3a2c0-102">XTP 가상 프로세서</span><span class="sxs-lookup"><span data-stu-id="3a2c0-102">XTP Phantom Processor</span></span>
  <span data-ttu-id="3a2c0-103">XTP 가상 프로세서 성능 개체에는 XTP 엔진의 가상 처리 하위 시스템과 관련된 카운터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a2c0-103">The XTP Phantom Processor performance object contains counters related to the XTP engine's phantom processing subsystem.</span></span> <span data-ttu-id="3a2c0-104">이 구성 요소는 SERIALIZABLE 격리 수준에서 실행되는 트랜잭션에서 가상 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3a2c0-104">This component is responsible for detecting phantom rows in transactions running at the SERIALIZABLE isolation level.</span></span>  
  
 <span data-ttu-id="3a2c0-105">이 표에서는 **XTP 가상 프로세서** 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3a2c0-105">This table describes the **XTP Phantom Processor** counters.</span></span>  
  
|<span data-ttu-id="3a2c0-106">카운터</span><span class="sxs-lookup"><span data-stu-id="3a2c0-106">Counter</span></span>|<span data-ttu-id="3a2c0-107">Description</span><span class="sxs-lookup"><span data-stu-id="3a2c0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a2c0-108">**Dusty corner scan retries/sec (Phantom-issued)**</span><span class="sxs-lookup"><span data-stu-id="3a2c0-108">**Dusty corner scan retries/sec (Phantom-issued)**</span></span>|<span data-ttu-id="3a2c0-109">가상 프로세서에 의해 실행된 불량 영역 청소(dusty corner sweeps) 중 발생한 초당 검색 재시도 횟수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="3a2c0-109">The number of scan retries due to write conflicts during dusty corner sweeps issued by the phantom processor (on average), per second.</span></span> <span data-ttu-id="3a2c0-110">이 카운터는 사용자용이 아닌 매우 낮은 수준의 카운터입니다.</span><span class="sxs-lookup"><span data-stu-id="3a2c0-110">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="3a2c0-111">**Phantom expired rows removed/sec**</span><span class="sxs-lookup"><span data-stu-id="3a2c0-111">**Phantom expired rows removed/sec**</span></span>|<span data-ttu-id="3a2c0-112">가상 검사에 의해 제거된 만료된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="3a2c0-112">The number of expired rows removed by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="3a2c0-113">**Phantom expired rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="3a2c0-113">**Phantom expired rows touched/sec**</span></span>|<span data-ttu-id="3a2c0-114">가상 검사에 의해 처리된 만료된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="3a2c0-114">The number of expired rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="3a2c0-115">**Phantom expiring rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="3a2c0-115">**Phantom expiring rows touched/sec**</span></span>|<span data-ttu-id="3a2c0-116">가상 검사에 의해 처리된 만료되는 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="3a2c0-116">The number of expiring rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="3a2c0-117">**Phantom rows touched/sec**</span><span class="sxs-lookup"><span data-stu-id="3a2c0-117">**Phantom rows touched/sec**</span></span>|<span data-ttu-id="3a2c0-118">가상 검사에 의해 처리된 초당 행 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="3a2c0-118">The number of rows touched by phantom scans (on average), per second.</span></span>|  
|<span data-ttu-id="3a2c0-119">**Phantom scans started/sec**</span><span class="sxs-lookup"><span data-stu-id="3a2c0-119">**Phantom scans started/sec**</span></span>|<span data-ttu-id="3a2c0-120">초당 시작된 가상 검사 수입니다(평균).</span><span class="sxs-lookup"><span data-stu-id="3a2c0-120">The number of phantom scans started (on average), per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a2c0-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a2c0-121">See Also</span></span>  
 [<span data-ttu-id="3a2c0-122">XTP &#40;메모리 내 OLTP&#41; 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="3a2c0-122">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
