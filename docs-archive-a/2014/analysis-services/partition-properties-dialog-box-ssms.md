---
title: 파티션 속성 대화 상자 (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionpropertiesdialog.f1
ms.assetid: dfb5b7a0-7543-4e5e-8a30-4b734606e157
author: minewiskan
ms.author: owend
ms.openlocfilehash: b606a39ef99e5313b526ab0210448e295c5f04cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727392"
---
# <a name="partition-properties-dialog-box-ssms"></a><span data-ttu-id="ab633-102">파티션 속성 대화 상자(SSMS)</span><span class="sxs-lookup"><span data-stu-id="ab633-102">Partition Properties Dialog Box (SSMS)</span></span>
  <span data-ttu-id="ab633-103">SQL Server Management Studio의 **파티션 속성** 대화 상자를 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스의 큐브에 대한 파티션 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab633-103">Use the **Partition Properties** dialog box in SQL Server Management Studio to set the properties of a partition for a cube in an [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="ab633-104">**파티션 속성** 대화 상자를 열려면 **개체 탐색기**에서 파티션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ab633-104">To open the **Partition Properties** dialog box, in **Object Explorer**, right-click a partition, and then click **Properties**.</span></span>  
  
 <span data-ttu-id="ab633-105">**파티션 속성** 대화 상자에는 다음과 같은 페이지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab633-105">The **Partition Properties** dialog box contains the following pages:</span></span>  
  
## <a name="pages"></a><span data-ttu-id="ab633-106">페이지</span><span class="sxs-lookup"><span data-stu-id="ab633-106">Pages</span></span>  
  
|<span data-ttu-id="ab633-107">호출</span><span class="sxs-lookup"><span data-stu-id="ab633-107">Page</span></span>|<span data-ttu-id="ab633-108">Description</span><span class="sxs-lookup"><span data-stu-id="ab633-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="ab633-109">**선택**</span><span class="sxs-lookup"><span data-stu-id="ab633-109">**Selection**</span></span>|<span data-ttu-id="ab633-110">**선택** 페이지를 사용하여 속성을 표시 또는 수정할 측정값 그룹의 파티션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab633-110">Use the **Selection** page to select the partition in the measure group for which you want to display or modify properties.</span></span> <span data-ttu-id="ab633-111">이 페이지에 대한 자세한 내용은 [선택&#40;파티션 속성 대화 상자&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab633-111">For more information about this page, see [Selection &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="ab633-112">**일반**</span><span class="sxs-lookup"><span data-stu-id="ab633-112">**General**</span></span>|<span data-ttu-id="ab633-113">**일반** 페이지를 사용하여 **선택** 페이지에서 선택한 파티션의 일반 속성을 표시 및 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab633-113">Use the **General** page to display and modify the general properties of the partition selected in the **Selection** page.</span></span> <span data-ttu-id="ab633-114">이 페이지에 대한 자세한 내용은 [일반&#40;파티션 속성 대화 상자&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab633-114">For more information about this page, see [General &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](general-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="ab633-115">**자동 관리 캐싱**</span><span class="sxs-lookup"><span data-stu-id="ab633-115">**Proactive Caching**</span></span>|<span data-ttu-id="ab633-116">**자동 관리 캐싱** 페이지를 사용하여 **선택** 페이지에서 선택한 파티션의 스토리지 및 자동 관리 캐싱 설정을 표시 및 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab633-116">Use the **Proactive Caching** page to display and modify the storage and proactive caching settings of the partition selected in the **Selection** page.</span></span> <span data-ttu-id="ab633-117">이 페이지에 대한 자세한 내용은 [자동 관리 캐싱&#40;파티션 속성 대화 상자&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab633-117">For more information about this page, see [Proactive Caching &#40;Partition Properties Dialog Box&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md).</span></span>|  
|<span data-ttu-id="ab633-118">**오류 구성**</span><span class="sxs-lookup"><span data-stu-id="ab633-118">**Error Configuration**</span></span>|<span data-ttu-id="ab633-119">**오류 구성** 페이지를 사용하여 **선택** 페이지에서 선택한 파티션을 처리하기 위한 오류 구성 설정을 표시 및 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab633-119">Use the **Error Configuration** page to display and modify the error configuration settings for processing the partition selected in the **Selection** page.</span></span> <span data-ttu-id="ab633-120">이 페이지에 대한 자세한 내용은 [큐브, 파티션 및 차원 처리에 대한 오류 구성&#40;SSAS - 다차원&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab633-120">For more information about this page, see [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab633-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab633-121">See Also</span></span>  
 <span data-ttu-id="ab633-122">[파티션 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ab633-122">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="ab633-123">[원격 파티션](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="ab633-123">[Remote Partitions](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md) </span></span>  
 [<span data-ttu-id="ab633-124">Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="ab633-124">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
