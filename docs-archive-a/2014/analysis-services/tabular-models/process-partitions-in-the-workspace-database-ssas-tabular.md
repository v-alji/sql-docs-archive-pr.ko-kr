---
title: 작업 영역 데이터베이스에서 파티션 처리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3a369705-43fa-4961-9045-32e06fbdde33
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4a996e90b30794882535327ea3192d7e72818422
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728760"
---
# <a name="process-partitions-in-the-workspace-database-ssas-tabular"></a><span data-ttu-id="65cb4-102">작업 영역 데이터베이스에서 파티션 처리 (SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="65cb4-102">Process Partitions in the Workspace Database (SSAS Tabular)</span></span>
  <span data-ttu-id="65cb4-103">파티션은 테이블을 논리적 부분으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="65cb4-104">각 파티션은 다른 파티션과 별개로 처리(새로 고침)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="65cb4-105">이 항목의 태스크에서는 **의** 파티션 처리 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]대화 상자를 사용하여 모델 작업 영역 데이터베이스에서 파티션을 처리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-105">The tasks in this topic describe how to process partitions in the model workspace database by using the **Process Partitions** dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="65cb4-106">다른 Analysis Services 인스턴스로 모델을 배포한 후 데이터베이스 관리자는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 스크립트 또는 IS 패키지를 사용하여 (배포된) 모델에서 파티션을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-106">After a model has been deployed to another Analysis Services instance, database administrators can create and manage partitions in the (deployed) model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], by script, or by using an IS package.</span></span> <span data-ttu-id="65cb4-107">자세한 내용은 [테이블 형식 모델 파티션 만들기 및 관리&#40;SSAS 테이블 형식&#41;](partitions-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65cb4-107">For more information, see [Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
###  <a name="to-process-a-partition"></a><a name="bkmk_create_new"></a> <span data-ttu-id="65cb4-108">파티션을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="65cb4-108">To process a partition</span></span>  
  
1.  <span data-ttu-id="65cb4-109">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **처리** (새로 고침) 및 **파티션 처리**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-109">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Process** (Refresh), and then click **Process Partitions**.</span></span>  
  
2.  <span data-ttu-id="65cb4-110">**모드** 목록 상자에서 다음 처리 모드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-110">In the **Mode** listbox, select one of the following process modes:</span></span>  
  
    |<span data-ttu-id="65cb4-111">Mode</span><span class="sxs-lookup"><span data-stu-id="65cb4-111">Mode</span></span>|<span data-ttu-id="65cb4-112">Description</span><span class="sxs-lookup"><span data-stu-id="65cb4-112">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="65cb4-113">**기본값 처리**</span><span class="sxs-lookup"><span data-stu-id="65cb4-113">**Process Default**</span></span>|<span data-ttu-id="65cb4-114">파티션 개체의 처리 상태를 검색하고 필요한 처리를 수행하여 처리되지 않거나 부분적으로 처리된 파티션 개체를 완전히 처리된 상태로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-114">Detects the process state of a partition object, and performs processing necessary to deliver unprocessed or partially processed partition objects to a fully processed state.</span></span> <span data-ttu-id="65cb4-115">빈 테이블 및 파티션에 대한 데이터를 로드하고 계층, 계산 열 및 관계를 작성 또는 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-115">Data for empty tables and partitions is loaded; hierarchies, calculated columns, and relationships are built or rebuilt.</span></span>|  
    |<span data-ttu-id="65cb4-116">**전체 처리**</span><span class="sxs-lookup"><span data-stu-id="65cb4-116">**Process Full**</span></span>|<span data-ttu-id="65cb4-117">파티션 개체와 여기에 포함된 모든 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-117">Processes a partition object and all the objects that it contains.</span></span> <span data-ttu-id="65cb4-118">이미 처리된 개체에 대해 전체 처리를 실행하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 개체의 모든 데이터를 삭제한 다음 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-118">When Process Full is run for an object that has already been processed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] drops all data in the object, and then processes the object.</span></span> <span data-ttu-id="65cb4-119">개체에 구조적 변경이 발생한 경우 이러한 종류의 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-119">This kind of processing is required when a structural change has been made to an object.</span></span>|  
    |<span data-ttu-id="65cb4-120">**데이터 처리**</span><span class="sxs-lookup"><span data-stu-id="65cb4-120">**Process Data**</span></span>|<span data-ttu-id="65cb4-121">계층 또는 관계를 다시 작성하거나 계산 열 및 측정값을 다시 계산하지 않고 파티션 또는 테이블에 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-121">Load data into a partition or a table without rebuilding hierarchies or relationships or recalculating calculated columns and measures.</span></span>|  
    |<span data-ttu-id="65cb4-122">**지우기 처리**</span><span class="sxs-lookup"><span data-stu-id="65cb4-122">**Process Clear**</span></span>|<span data-ttu-id="65cb4-123">파티션에서 모든 데이터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-123">Removes all data from a partition.</span></span>|  
    |<span data-ttu-id="65cb4-124">**증분 처리**</span><span class="sxs-lookup"><span data-stu-id="65cb4-124">**Process Add**</span></span>|<span data-ttu-id="65cb4-125">새 데이터로 파티션을 증분 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-125">Incrementally update partition with new data.</span></span>|  
  
3.  <span data-ttu-id="65cb4-126">**처리** 확인란 열에서 선택된 모드로 처리할 파티션을 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65cb4-126">In the **Process** checkbox column, select the partitions you want to process with the selected mode, and then click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65cb4-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65cb4-127">See Also</span></span>  
 <span data-ttu-id="65cb4-128">[SSAS 테이블 형식&#41;&#40;파티션](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="65cb4-128">[Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="65cb4-129">작업 영역 데이터베이스에서 파티션 만들기 및 관리&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="65cb4-129">Create and Manage Partitions in the Workspace Database &#40;SSAS Tabular&#41;</span></span>](workspace-database-ssas-tabular.md)  
  
  
