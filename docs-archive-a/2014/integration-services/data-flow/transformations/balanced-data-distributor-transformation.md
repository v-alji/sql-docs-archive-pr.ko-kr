---
title: 균형 있는 데이터 배포자 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.balanceddatadistributor.f1
ms.assetid: ae0b33dd-f44b-42df-b6f6-69861770ce10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 09591013bc1f21659720fa9fec2e94167be93a1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650215"
---
# <a name="balanced-data-distributor-transformation"></a><span data-ttu-id="f8863-102">분산 데이터 배포자 변환</span><span class="sxs-lookup"><span data-stu-id="f8863-102">Balanced Data Distributor Transformation</span></span>
  <span data-ttu-id="f8863-103">BDD(분산 데이터 배포자) 변환은 최신 CPU의 동시 처리 기능을 이용하며,</span><span class="sxs-lookup"><span data-stu-id="f8863-103">The Balanced Data Distributor (BDD) transformation takes advantage of concurrent processing capability of modern CPUs.</span></span> <span data-ttu-id="f8863-104">들어오는 행의 버퍼를 여러 스레드의 출력에 균일하게 분산합니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-104">It distributes buffers of incoming rows uniformly across outputs on separate threads.</span></span> <span data-ttu-id="f8863-105">BDD 구성 요소는 각 출력 경로에 별도의 스레드를 사용하여 다중 코어 또는 다중 프로세서 컴퓨터에서 SSIS 패키지의 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-105">By using separate threads for each output path, the BDD component improves the performance of an SSIS package on multi-core or multi-processor machines.</span></span> <span data-ttu-id="f8863-106">BDD 구성 요소는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 기능 팩의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-106">The BDD component is part of the Feature Pack for [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="f8863-107">[여기](https://go.microsoft.com/fwlink/p/?LinkId=391999)에서 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-107">Download and install it from [here](https://go.microsoft.com/fwlink/p/?LinkId=391999).</span></span>  
  
 <span data-ttu-id="f8863-108">다음 다이어그램에서는 BDD 변환을 사용하는 간단한 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-108">The following diagram shows a simple example of using the BDD transformation.</span></span> <span data-ttu-id="f8863-109">이 예에서 BDD 변환은 플랫 파일 원본의 입력 데이터에서 파이프라인 버퍼를 한 번에 하나씩 선택하여 라운드 로빈 방식으로 세 출력 경로 중 하나로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-109">In this example, the BDD transformation picks one pipeline buffer at a time from the input data from a flat file source and sends it down one of the three output paths in a round robin fashion.</span></span> <span data-ttu-id="f8863-110">데이터 흐름 태스크의 속성을 보여주는 SQL Server Data Tools의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferSize%2A>창에서 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferMaxRows%2A>(파이프라인 버퍼의 기본 크기) 및 **DefaultBufferMaxRows** (파이프라인 버퍼의 기본 최대 행 수)의 값을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-110">In SQL Server Data Tools, you can check the values of a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferSize%2A>(default size of the pipeline buffer) and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.DefaultBufferMaxRows%2A>(default maximum number of rows in a pipeline buffer) in the **Properties** window displaying properties of a data flow task.</span></span>  
  
 <span data-ttu-id="f8863-111">![균형 있는 데이터 배포자](../../media/balanceddatadistributor.JPG "분산 데이터 배포자")</span><span class="sxs-lookup"><span data-stu-id="f8863-111">![Balanced Data Distributor](../../media/balanceddatadistributor.JPG "Balanced Data Distributor")</span></span>  
  
 <span data-ttu-id="f8863-112">분산 데이터 배포자 변환은 다음 조건을 충족하는 시나리오에서 패키지의 성능을 향상시키는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-112">The Balanced Data Distributor transformation helps improve performance of a package in a scenario that satisfies the following conditions:</span></span>  
  
1.  <span data-ttu-id="f8863-113">BDD 변환으로 많은 양의 데이터가 들어오는 경우.</span><span class="sxs-lookup"><span data-stu-id="f8863-113">There is large amount of data coming into the BDD transformation.</span></span> <span data-ttu-id="f8863-114">데이터 크기가 작고 한 버퍼만 데이터를 저장할 수 있는 경우 BDD 변환을 사용할 이유가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-114">If the data size is small and only one buffer can hold the data, there is no point in using the BDD transformation.</span></span> <span data-ttu-id="f8863-115">데이터 크기가 크고 여러 개의 버퍼가 데이터를 저장하는 데 필요한 경우 BDD는 여러 스레드를 사용하여 병렬로 데이터 버퍼를 효율적으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-115">If the data size is large and several buffers are required to hold the data, BDD can efficiently process buffers of data in parallel by using separate threads.</span></span>  
  
2.  <span data-ttu-id="f8863-116">데이터를 읽는 속도가 데이터 흐름의 나머지 부분에서 데이터를 처리할 수 있는 속도보다 빠른 경우.</span><span class="sxs-lookup"><span data-stu-id="f8863-116">The data can be read faster than the rest of the data flow can process it.</span></span> <span data-ttu-id="f8863-117">이 시나리오에서는 데이터에 수행되는 변환이 데이터가 들어오는 속도에 비해 느리게 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-117">In this scenario, the transformations that are performed on the data run slowly compared to the rate at which data is coming.</span></span> <span data-ttu-id="f8863-118">대상에 병목 상태가 발생한 경우 대상이 병렬 처리될 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-118">If the bottleneck is at the destination, the destination must be parallelizable though.</span></span>  
  
3.  <span data-ttu-id="f8863-119">데이터의 순서를 정렬할 필요가 없는 경우.</span><span class="sxs-lookup"><span data-stu-id="f8863-119">The data does not need to be ordered.</span></span> <span data-ttu-id="f8863-120">예를 들어 데이터를 정렬된 상태로 유지해야 하는 경우 BDD 변환을 사용하여 데이터를 분할하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-120">For example, if the data needs to stay sorted, you should not split the data using the BDD transformation.</span></span>  
  
 <span data-ttu-id="f8863-121">SSIS 패키지의 병목 현상이 원본에서 데이터를 읽을 수 있는 속도 때문에 발생하는 경우 BDD 구성 요소는 성능을 향상시키는 데 도움이 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-121">Note that if the bottleneck in an SSIS package is due to the rate at which data can be read from the source, the BDD component does not help improve the performance.</span></span> <span data-ttu-id="f8863-122">SSIS 패키지의 병목 현상이 대상에서 병렬 처리를 지원하지 않기 때문에 발생하는 경우 BDD는 도움이 되지 않지만, 모든 변환을 병렬로 수행하고 UNION ALL 변환을 사용하여 BDD 변환의 여러 출력 경로에서 들어오는 출력 데이터를 결합한 후 대상에 데이터를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8863-122">If the bottleneck in an SSIS package is because the destination does not support parallelism, the BDD does not help; however, you can perform all the transformations in parallel and use the Union All transformation to combine the output data coming out of different output paths of the BDD transformation before sending the data to the destination.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f8863-123"> 변환 사용에 대한 데모를 보려면 TechNet 라이브러리에서 [분산 데이터 배포자 비디오](https://go.microsoft.com/fwlink/?LinkID=226278) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f8863-123">See the [Balanced Data Distributor video](https://go.microsoft.com/fwlink/?LinkID=226278) on the TechNet Library for a presentation with a demo on using the transformation.</span></span>  
  
  
