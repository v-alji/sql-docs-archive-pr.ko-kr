---
title: XTP 저장소 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: efd4a9eba36060d3d4bab9b371678ab2b2c409ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651669"
---
# <a name="xtp-storage"></a><span data-ttu-id="f964d-102">XTP 스토리지</span><span class="sxs-lookup"><span data-stu-id="f964d-102">XTP Storage</span></span>
  <span data-ttu-id="f964d-103">XTP 스토리지 성능 개체에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 XTP 스토리지와 관련된 카운터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-103">The XTP Storage performance object contains counters related to XTP storage in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f964d-104">이 표에서는 **XTP 스토리지** 카운터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-104">This table describes the **XTP Storage** counters.</span></span>  
  
|<span data-ttu-id="f964d-105">카운터</span><span class="sxs-lookup"><span data-stu-id="f964d-105">Counter</span></span>|<span data-ttu-id="f964d-106">Description</span><span class="sxs-lookup"><span data-stu-id="f964d-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f964d-107">**Checkpoints Closed**</span><span class="sxs-lookup"><span data-stu-id="f964d-107">**Checkpoints Closed**</span></span>|<span data-ttu-id="f964d-108">온라인 에이전트에 의해 닫힌 검사점 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-108">Count of checkpoints closed done by online agent.</span></span>|  
|<span data-ttu-id="f964d-109">**Checkpoints Completed**</span><span class="sxs-lookup"><span data-stu-id="f964d-109">**Checkpoints Completed**</span></span>|<span data-ttu-id="f964d-110">오프라인 검사점 스레드에서 처리된 검사점 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-110">Count of checkpoints processed by offline checkpoint thread.</span></span>|  
|<span data-ttu-id="f964d-111">**Core Merges Completed**</span><span class="sxs-lookup"><span data-stu-id="f964d-111">**Core Merges Completed**</span></span>|<span data-ttu-id="f964d-112">병합 작업자 스레드에서 완료한 코어 병합 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-112">The number of core merges completed by the merge worker thread.</span></span> <span data-ttu-id="f964d-113">이러한 병합은 계속 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-113">These merges still need to be installed.</span></span>|  
|<span data-ttu-id="f964d-114">**Merge Policy Evaluations**</span><span class="sxs-lookup"><span data-stu-id="f964d-114">**Merge Policy Evaluations**</span></span>|<span data-ttu-id="f964d-115">서버를 시작한 이후 병합 정책 평가 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-115">The number of merge policy evaluations since the server started.</span></span>|  
|<span data-ttu-id="f964d-116">**Merge Requests Outstanding**</span><span class="sxs-lookup"><span data-stu-id="f964d-116">**Merge Requests Outstanding**</span></span>|<span data-ttu-id="f964d-117">서버를 시작한 이후 해결되지 않은 병합 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-117">The number of merge requests outstanding since the server started.</span></span>|  
|<span data-ttu-id="f964d-118">**Merges Abandoned**</span><span class="sxs-lookup"><span data-stu-id="f964d-118">**Merges Abandoned**</span></span>|<span data-ttu-id="f964d-119">오류로 인해 중단된 병합 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-119">The number of merges abandoned due to failure.</span></span>|  
|<span data-ttu-id="f964d-120">**Merges Installed**</span><span class="sxs-lookup"><span data-stu-id="f964d-120">**Merges Installed**</span></span>|<span data-ttu-id="f964d-121">설치된 병합 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-121">The number of merges successfully installed.</span></span>|  
|<span data-ttu-id="f964d-122">**Total Files Merged**</span><span class="sxs-lookup"><span data-stu-id="f964d-122">**Total Files Merged**</span></span>|<span data-ttu-id="f964d-123">병합된 총 원본 파일 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-123">The total number of source files merged.</span></span> <span data-ttu-id="f964d-124">이 카운트는 병합에서 평균 원본 파일 수를 찾는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f964d-124">This count can be used to find the average number of source files in the merge.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f964d-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f964d-125">See Also</span></span>  
 [<span data-ttu-id="f964d-126">XTP &#40;메모리 내 OLTP&#41; 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="f964d-126">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
