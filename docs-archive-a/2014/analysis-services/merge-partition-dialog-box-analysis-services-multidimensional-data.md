---
title: 병합 파티션 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.mergepartition.f1
ms.assetid: 1c94e250-ee18-4f98-b112-985f6346102a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1978c187bfb5097d286f78650b5bda6645c7a054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659707"
---
# <a name="merge-partition-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="2d686-102">병합 파티션 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="2d686-102">Merge Partition Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="2d686-103">**SQL Server Management Studio** 의 **파티션 병합** 대화 상자를 사용하여 큐브에 있는 측정값 그룹의 파티션을 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-103">Use the **Merge Partition** dialog box in **SQL Server Management Studio** to merge partitions for a measure group in a cube.</span></span> <span data-ttu-id="2d686-104">**개체 탐색기** 에서 파티션 폴더 또는 파티션을 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **파티션 병합** 을 선택하면 **파티션 병합** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-104">You can display the **Merge Partition** dialog box by right-clicking the Partitions folder or a partition in **Object Explorer** and selecting **Merge Partitions** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2d686-105">옵션</span><span class="sxs-lookup"><span data-stu-id="2d686-105">Options</span></span>  
 <span data-ttu-id="2d686-106">**Server**</span><span class="sxs-lookup"><span data-stu-id="2d686-106">**Server**</span></span>  
 <span data-ttu-id="2d686-107">대상 파티션이 포함된 Analysis Services 인스턴스 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-107">Select the name of the Analysis Services instance that contains the target partition.</span></span>  
  
 <span data-ttu-id="2d686-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="2d686-108">**Name**</span></span>  
 <span data-ttu-id="2d686-109">대상 파티션으로 사용할 기존 파티션의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-109">Select the name of an existing partition to use as the target partition.</span></span>  
  
 <span data-ttu-id="2d686-110">**폴더**</span><span class="sxs-lookup"><span data-stu-id="2d686-110">**Folder**</span></span>  
 <span data-ttu-id="2d686-111">이름에서 선택한 파티션이 Analysis Services 인스턴스에 대한 기본 폴더를 사용하지 않는 경우 대상 파티션이 포함된 폴더의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-111">Displays the name of the folder that contains the target partition, if the partition selected in Name does not use the default folder for the Analysis Services instance.</span></span>  
  
 <span data-ttu-id="2d686-112">**원본 파티션**</span><span class="sxs-lookup"><span data-stu-id="2d686-112">**Source Partitions**</span></span>  
 <span data-ttu-id="2d686-113">대상 파티션에 병합할 수 있는 원본 파티션이 포함된 표를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-113">Displays a grind containing the source partitions that can be merged into the target partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d686-114">동일한 집계 디자인을 공유하는 같은 측정값 그룹의 파티션만 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-114">Only partitions in the same measure group that share the same aggregation design can be merged.</span></span>  
  
 <span data-ttu-id="2d686-115">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-115">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="2d686-116">열</span><span class="sxs-lookup"><span data-stu-id="2d686-116">Column</span></span>|<span data-ttu-id="2d686-117">Description</span><span class="sxs-lookup"><span data-stu-id="2d686-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2d686-118">**병합**</span><span class="sxs-lookup"><span data-stu-id="2d686-118">**Merge**</span></span>|<span data-ttu-id="2d686-119">원본 파티션을 대상 파티션에 병합하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-119">Select to merge the source partition into the target partition.</span></span>|  
|<span data-ttu-id="2d686-120">**파티션 이름**</span><span class="sxs-lookup"><span data-stu-id="2d686-120">**Partition Name**</span></span>|<span data-ttu-id="2d686-121">원본 파티션 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-121">Displays the name of the source partition.</span></span>|  
|<span data-ttu-id="2d686-122">**마지막 처리**</span><span class="sxs-lookup"><span data-stu-id="2d686-122">**Last Processed**</span></span>|<span data-ttu-id="2d686-123">원본 파티션을 마지막으로 처리한 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2d686-123">Displays the date and time at which the source partition was last processed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d686-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d686-124">See Also</span></span>  
 <span data-ttu-id="2d686-125">[파티션 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="2d686-125">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="2d686-126">Analysis Services의 파티션 병합&#40;SSAS - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="2d686-126">Merge Partitions in Analysis Services &#40;SSAS - Multidimensional&#41;</span></span>](multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  
