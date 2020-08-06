---
title: 집계 디자인 할당 대화 상자 (다차원 데이터 Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.copyaggregationdesign.f1
ms.assetid: 50c26cb1-c294-4f17-8b9e-435fdbd4806d
author: minewiskan
ms.author: owend
ms.openlocfilehash: dfc4f7a0847373360a79ddda366ad7aa3f02c5de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648215"
---
# <a name="assign-aggregation-design-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="1b1a5-102">집계 디자인 할당 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="1b1a5-102">Assign Aggregation Design Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="1b1a5-103">**의** 집계 디자인 할당 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 집계 디자인을 하나 이상의 대상 파티션에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-103">Use the **Assign Aggregation Design** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to assign aggregation designs to one or more destination partitions.</span></span> <span data-ttu-id="1b1a5-104">**개체 탐색기** 에서 파티션이나 집계 디자인을 마우스 오른쪽 단추로 클릭하고 **집계 디자인 할당** 를 선택하면 **집계 디자인 할당**대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-104">You can display the **Assign Aggregation Design** dialog box by right-clicking a partition or aggregation design in **Object Explorer** and selecting **Assign Aggregation Design**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1b1a5-105">옵션</span><span class="sxs-lookup"><span data-stu-id="1b1a5-105">Options</span></span>  
  
|<span data-ttu-id="1b1a5-106">용어</span><span class="sxs-lookup"><span data-stu-id="1b1a5-106">Term</span></span>|<span data-ttu-id="1b1a5-107">정의</span><span class="sxs-lookup"><span data-stu-id="1b1a5-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="1b1a5-108">**집계 디자인**</span><span class="sxs-lookup"><span data-stu-id="1b1a5-108">**Aggregation designs**</span></span>|<span data-ttu-id="1b1a5-109">하나 이상의 대상 파티션에 할당할 집계 디자인을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-109">Select an aggregation design to assign to one or more destination partitions.</span></span>|  
|<span data-ttu-id="1b1a5-110">**대상 파티션**</span><span class="sxs-lookup"><span data-stu-id="1b1a5-110">**Destination partitions**</span></span>|<span data-ttu-id="1b1a5-111">집계 디자인을 할당할 파티션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-111">Select the partitions to which to assign the aggregation design.</span></span> <span data-ttu-id="1b1a5-112">다음 표를 사용하여 대상 파티션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-112">The following grid is used to specify destination partitions:</span></span><br /><br /> <span data-ttu-id="1b1a5-113">\<check box>: 나열 된 모든 파티션을 대상 파티션으로 포함 하거나 제외 하려면 열 머리글의 확인란을 선택 하거나 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-113">\<check box>: Select or clear the check box in the column header to include or exclude all listed partitions as destination partitions.</span></span> <span data-ttu-id="1b1a5-114">특정 파티션을 대상 파티션으로 포함하거나 제외하려면 해당 파티션 옆에 있는 확인란을 선택하거나 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-114">Select or clear a check box next to a partition to include or exclude that partition as a destination partition.</span></span><br /><br /> <span data-ttu-id="1b1a5-115">**파티션**: 파티션의 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-115">**Partition**: Displays the name of the partition.</span></span><br /><br /> <span data-ttu-id="1b1a5-116">**원본**: 파티션에 대 한 원본 테이블 또는 쿼리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-116">**Source**: Displays the source table or query for the partition.</span></span><br /><br /> <span data-ttu-id="1b1a5-117">**집계 디자인**: 파티션에 대 한 기존 집계 디자인의 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-117">**Aggregation Design**: Displays the name of the existing aggregation design for the partition.</span></span>|  
|<span data-ttu-id="1b1a5-118">**집계 디자인으로 파티션 숨기**</span><span class="sxs-lookup"><span data-stu-id="1b1a5-118">**Hide partitions with aggregation designs**</span></span>|<span data-ttu-id="1b1a5-119">집계 디자인이 할당되어 있지 않은 파티션만 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1b1a5-119">Select to show only the partitions that do not have aggregation designs assigned to them.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b1a5-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1b1a5-120">See Also</span></span>  
 [<span data-ttu-id="1b1a5-121">Aggregations and Aggregation Designs</span><span class="sxs-lookup"><span data-stu-id="1b1a5-121">Aggregations and Aggregation Designs</span></span>](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
