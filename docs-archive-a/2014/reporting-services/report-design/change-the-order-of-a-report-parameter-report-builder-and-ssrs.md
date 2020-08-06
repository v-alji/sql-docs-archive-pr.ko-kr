---
title: 보고서 매개 변수의 순서 변경(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad9dd25be7a87fee089a48849fcc716e682e4c64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737935"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="e30d0-102">보고서 매개 변수의 순서 변경(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e30d0-102">Change the Order of a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e30d0-103">종속 매개 변수가 종속 대상 매개 변수 앞에 나열된 경우 보고서 매개 변수의 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e30d0-103">Change the order of report parameters when you have a dependent parameter that is listed before the parameter it is dependent on.</span></span> <span data-ttu-id="e30d0-104">매개 변수 순서는 연계 매개 변수가 있거나 사용자가 한 매개 변수의 기본값을 본 다음 다른 매개 변수의 값을 선택하도록 하려는 경우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="e30d0-104">Parameter order is important when you have cascading parameters, or when you want to show users the default value for one parameter before they choose values for other parameters.</span></span> <span data-ttu-id="e30d0-105">종속 보고서 매개 변수에는 보고서 데이터 창의 매개 변수 목록에서 해당 매개 변수 뒤에 오는 보고서 매개 변수를 가리키는 쿼리 매개 변수에 대한 참조가 기본값 쿼리 또는 유효한 값 쿼리에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e30d0-105">A dependent report parameter contains a reference, in either its default values query or valid values query, to a query parameter that points to a report parameter that is after it in the parameter list in the Report Data pane.</span></span>  
  
 <span data-ttu-id="e30d0-106">보고서 뷰어 도구 모음에서 매개 변수가 표시되는 순서는 보고서 데이터 창의 매개 변수 순서에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e30d0-106">The order that you see parameters display on the report viewer toolbar is determined by the order of the parameters in the Report Data pane.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-order-of-report-parameters"></a><span data-ttu-id="e30d0-107">보고서 매개 변수의 순서를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="e30d0-107">To change the order of report parameters</span></span>  
  
1.  <span data-ttu-id="e30d0-108">보고서 데이터 창에서 매개 변수 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e30d0-108">In the Report Data pane, expand the Parameters node.</span></span>  
  
2.  <span data-ttu-id="e30d0-109">매개 변수를 클릭하고 보고서 데이터 창 도구 모음의 위쪽 및 아래쪽 화살표 단추를 사용하여 매개 변수를 목록의 위 또는 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e30d0-109">Click a parameter and use the up and down arrow buttons on the Report Data pane toolbar to move the parameter higher or lower in the list.</span></span> <span data-ttu-id="e30d0-110">다음 이미지에는 보고서 작성기의 보고서 데이터 창이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e30d0-110">The following image shows the Report Data pane in Report Builder.</span></span>  
  
     <span data-ttu-id="e30d0-111">![보고서 데이터 창](../media/reportdatapane.png "보고서 데이터 창")</span><span class="sxs-lookup"><span data-stu-id="e30d0-111">![Report Data Pane](../media/reportdatapane.png "Report Data Pane")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e30d0-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e30d0-112">See Also</span></span>  
 <span data-ttu-id="e30d0-113">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e30d0-113">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="e30d0-114">[대화 상자, 창 및 마법사에 대 한 보고서 작성기 도움말](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="e30d0-114">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="e30d0-115">[보고서 &#40;보고서 작성기 및 SSRS에 연계 매개 변수를 추가&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e30d0-115">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e30d0-116">[자습서: 보고서에 매개 변수를 추가 &#40;보고서 작성기&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e30d0-116">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="e30d0-117">[데이터 집합 필터, 데이터 영역 필터 및 그룹 필터를 추가 하 여 보고서 작성기 및 SSRS &#40;&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="e30d0-117">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 [<span data-ttu-id="e30d0-118">매개 변수 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e30d0-118">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
