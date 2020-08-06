---
title: 마법사 완료 (파티션 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.finish.f1
ms.assetid: 68a4dd5d-94d9-4a02-be31-949a6da0ef51
author: minewiskan
ms.author: owend
ms.openlocfilehash: d60be28170e8f8ec156d1c37149ddbc04b64bf8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648043"
---
# <a name="completing-the-wizard-partition-wizard"></a><span data-ttu-id="3aedf-102">마법사 완료(파티션 마법사)</span><span class="sxs-lookup"><span data-stu-id="3aedf-102">Completing the Wizard (Partition Wizard)</span></span>
  <span data-ttu-id="3aedf-103">**마법사 완료** 페이지를 사용하여 파티션의 이름을 지정하고, 파티션에 대한 집계 디자인을 정의하고, 필요에 따라 파티션 마법사를 완료한 후 파티션을 배포 및 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-103">Use the **Completing the Wizard** page to name the partition, define the aggregation design for your partition, and optionally deploy and process the partition after completing the Partition Wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3aedf-104">옵션</span><span class="sxs-lookup"><span data-stu-id="3aedf-104">Options</span></span>  
 <span data-ttu-id="3aedf-105">**이름**</span><span class="sxs-lookup"><span data-stu-id="3aedf-105">**Name**</span></span>  
 <span data-ttu-id="3aedf-106">새 파티션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-106">Type the name for the new partition.</span></span> <span data-ttu-id="3aedf-107">여러 테이블에 대한 작업을 수행하는 경우 각 파티션 이름을 만들기 위해 테이블 이름과 결합할 접두사를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-107">If you are working with multiple tables, enter the prefix that will be combined with the table name to create each partition name.</span></span>  
  
 <span data-ttu-id="3aedf-108">**집계 옵션**</span><span class="sxs-lookup"><span data-stu-id="3aedf-108">**Aggregation options**</span></span>  
 <span data-ttu-id="3aedf-109">파티션에 대한 집계 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-109">Specifies the aggregation option for the partition.</span></span>  
  
 <span data-ttu-id="3aedf-110">다음 표에서는 사용 가능한 집계 옵션을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-110">The following table lists the aggregation options that are available.</span></span>  
  
|<span data-ttu-id="3aedf-111">옵션</span><span class="sxs-lookup"><span data-stu-id="3aedf-111">Option</span></span>|<span data-ttu-id="3aedf-112">Description</span><span class="sxs-lookup"><span data-stu-id="3aedf-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3aedf-113">**지금 파티션에 대한 집계 디자인**</span><span class="sxs-lookup"><span data-stu-id="3aedf-113">**Design aggregations for the partition now**</span></span>|<span data-ttu-id="3aedf-114">파티션 마법사가 새 파티션을 만든 후 새 파티션에 대한 집계를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-114">Designs aggregations for the new partition after the Partition Wizard creates the new partition.</span></span> <span data-ttu-id="3aedf-115">이 옵션을 선택하면 파티션 마법사에서 **마침** 을 클릭한 후 집계 디자인 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-115">Selecting this option starts the Aggregation Design Wizard after you click **Finish** in the Partition Wizard.</span></span> <span data-ttu-id="3aedf-116">집계 디자인 마법사에 대한 자세한 내용은 [집계 디자인 마법사 F1 도움말](aggregation-design-wizard-f1-help.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3aedf-116">For more information about the Aggregation Design Wizard, see [Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md).</span></span>|  
|<span data-ttu-id="3aedf-117">**나중에 집계 디자인**</span><span class="sxs-lookup"><span data-stu-id="3aedf-117">**Design the aggregations later**</span></span>|<span data-ttu-id="3aedf-118">집계를 지금 디자인하지 않고 파티션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-118">Creates the partition without designing aggregations at this time.</span></span>|  
|<span data-ttu-id="3aedf-119">**기존 파티션에서 집계 디자인 복사**</span><span class="sxs-lookup"><span data-stu-id="3aedf-119">**Copy the aggregation design from an existing partition**</span></span>|<span data-ttu-id="3aedf-120">측정값 그룹의 기존 파티션에서 새 파티션으로 집계 디자인을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-120">Copies the aggregation design from an existing partition in the measure group to the new partition.</span></span> <span data-ttu-id="3aedf-121">이 옵션을 클릭하면 **원본** 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-121">Clicking this option makes the **Copy from** option available.</span></span> <span data-ttu-id="3aedf-122">**원본** 옵션을 사용하여 집계 디자인을 복사할 파티션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-122">Use the **Copy from** option to select the partition from which to copy the aggregation design.</span></span><br /><br /> <span data-ttu-id="3aedf-123">나중에 병합할 수 있는 파티션에는 동일한 테이블 구조와 집계 디자인이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-123">Note that partitions that may be merged in the future must have the same table structure and aggregation design.</span></span> <span data-ttu-id="3aedf-124">새 파티션을 측정값 그룹의 기존 파티션과 병합할 경우 기존 파티션의 집계 디자인을 새 파티션에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-124">If you might merge the new partition with an existing partition in the measure group, you should copy the aggregation design of the existing partition into the new partition.</span></span>|  
  
 <span data-ttu-id="3aedf-125">**지금 배포 및 처리**</span><span class="sxs-lookup"><span data-stu-id="3aedf-125">**Deploy and Process Now**</span></span>  
 <span data-ttu-id="3aedf-126">**처리 및 스토리지 위치** 페이지에서 지정한 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 파티션을 배포 및 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-126">Deploys and processes the partition to the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance specified on the **Processing and Storage Locations** page.</span></span> <span data-ttu-id="3aedf-127">이 페이지에서 **마침** 을 클릭하면 마법사가 파티션을 배포 및 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="3aedf-127">The wizard deploys and processes the partition after you click **Finish** on this page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aedf-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3aedf-128">See Also</span></span>  
 [<span data-ttu-id="3aedf-129">파티션&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="3aedf-129">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
