---
title: 집계 디자인 (다차원 Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- aggregations [Analysis Services], partitions
- partitions [Analysis Services], aggregations
ms.assetid: 3072b7e0-6961-42ad-a287-16f391f2cec4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 18d8ea1adb645868a11b70966ba3be2ed1764fbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660716"
---
# <a name="designing-aggregations-analysis-services---multidimensional"></a><span data-ttu-id="574f9-102">집계 디자인(Analysis Services - 다차원)</span><span class="sxs-lookup"><span data-stu-id="574f9-102">Designing Aggregations (Analysis Services - Multidimensional)</span></span>
  <span data-ttu-id="574f9-103">집계는 큐브 데이터의 미리 계산된 요약으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 신속한 쿼리 응답을 제공할 수 있도록 도와 줍니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-103">Aggregations are precalculated summaries of cube data that help enable [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to provide rapid query responses.</span></span>  
  
 <span data-ttu-id="574f9-104">집계 디자인 마법사를 사용하여 파티션에 대한 스토리지 옵션을 설정하고 집계를 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-104">To set storage options and design aggregations for a partition, use the Aggregation Design Wizard.</span></span> <span data-ttu-id="574f9-105">이 마법사는 한 번에 개별 측정값 그룹의 단일 파티션에 대해 실행되므로 각 파티션마다 다른 옵션과 디자인을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-105">The wizard operates on a single partition of a measure group at a time so that you can select different options and designs for each partition.</span></span> <span data-ttu-id="574f9-106">스토리지 디자인 마법사는 파티션에 대한 스토리지를 구성하고 집계를 디자인하는 단계로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-106">The wizard takes you through steps to configure storage and design aggregation for a partition.</span></span> <span data-ttu-id="574f9-107">스토리지를 구성하는 방법에 대한 자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="574f9-107">For more information about configuring storage, see.</span></span>  
  
 <span data-ttu-id="574f9-108">마법사가 디자인할 집계 수의 제어 방법을 선택한 다음 마법사가 집계를 디자인하게 둡니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-108">Select a method for controlling the number of aggregations the wizard will design, and then let the wizard design the aggregations.</span></span>  
  
 <span data-ttu-id="574f9-109">여기서 목표는 최적의 집계 수를 디자인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-109">The goal is to design the optimal number of aggregations.</span></span> <span data-ttu-id="574f9-110">최적의 집계 수란 응답 시간을 빠르게 할 뿐만 아니라 파티션 크기가 필요 이상으로 커지는 것도 막을 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-110">This number should not only provide satisfactory response time, but also prevent excessive partition size.</span></span> <span data-ttu-id="574f9-111">집계 수가 커질수록 응답 속도는 빨라지지만 그에 따라 스토리지 공간도 많이 필요하고 컴퓨팅하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-111">A greater number of aggregations produces faster response times but it also requires more storage space and may take longer to compute.</span></span> <span data-ttu-id="574f9-112">뿐만 아니라 마법사가 점점 더 많은 집계를 디자인함에 따라 후반 집계보다 초반 집계에서 훨씬 많은 성능 향상이 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-112">Moreover, as the wizard designs more and more aggregations, earlier aggregations produce considerably larger performance gains than later aggregations.</span></span> <span data-ttu-id="574f9-113">자주 사용하지 않는 집계를 줄이면 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-113">Reduction in less useful aggregations increases performance as well.</span></span> <span data-ttu-id="574f9-114">마법사에서 사용할 수 있는 다음과 같은 방법 중 하나를 사용하면 마법사가 디자인하는 집계 수를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-114">You can control the number of aggregations the wizard designs by one of the following methods available in the wizard:</span></span>  
  
-   <span data-ttu-id="574f9-115">집계에 대한 스토리지 공간 제한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-115">Specify a storage space limit for the aggregations.</span></span>  
  
-   <span data-ttu-id="574f9-116">성능 향상 제한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-116">Specify a performance gain limit.</span></span>  
  
-   <span data-ttu-id="574f9-117">표시된 성능 대 크기 곡선이 적정 성능 향상 수준에서 평행을 이루기 시작하면 마법사를 수동으로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-117">Stop the wizard manually when the displayed performance versus size curve starts to level off at an acceptable performance gain.</span></span>  
  
-   <span data-ttu-id="574f9-118">집계를 디자인하지 않도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-118">Choose not to design aggregations.</span></span>  
  
 <span data-ttu-id="574f9-119">스토리지를 디자인하려면 마법사가 대상 서버의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에 연결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-119">To design storage, the wizard must be able to connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on the target server.</span></span> <span data-ttu-id="574f9-120">대상 서버에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 실행하고 있지 않거나 스토리지 디자인 프로세스에서 대상 서버에 연결할 수 없는 경우 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-120">The wizard will display an error message if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is not running on the target server or if the storage design process is otherwise unable to connect to the target server.</span></span>  
  
 <span data-ttu-id="574f9-121">마법사의 마지막 단계에서는 처리를 시작하거나 지연할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-121">The final step of the wizard allows you to process or defer processing.</span></span> <span data-ttu-id="574f9-122">처리하는 경우에는 마법사로 디자인한 집계가 생성되며, 연기하는 경우에는 디자인된 집계를 나중에 처리할 수 있도록 저장하여 처리 과정 없이 디자인 동작을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-122">Processing creates the aggregations you design with the wizard, while deferring processing saves the designed aggregations for future processing, thus allowing design activities to continue without processing.</span></span> <span data-ttu-id="574f9-123">파티션 크기에 따라 처리 시간이 오래 걸릴 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-123">Depending on the size of the partition, processing may take considerable time.</span></span> <span data-ttu-id="574f9-124">필요한 경우 파티션 처리를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="574f9-124">If you choose, you can interrupt processing a partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="574f9-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="574f9-125">See Also</span></span>  
 [<span data-ttu-id="574f9-126">Aggregations and Aggregation Designs</span><span class="sxs-lookup"><span data-stu-id="574f9-126">Aggregations and Aggregation Designs</span></span>](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
