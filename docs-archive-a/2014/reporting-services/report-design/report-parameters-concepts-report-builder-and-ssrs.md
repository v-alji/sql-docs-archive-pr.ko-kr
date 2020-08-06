---
title: 보고서 매개 변수 개념 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b740362daea83b50a62f0b4453ce818ab21ace7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730171"
---
# <a name="report-parameters-concept-report-builder-and-ssrs"></a><span data-ttu-id="6654d-102">보고서 매개 변수 개념(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6654d-102">Report Parameters Concept (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6654d-103">보고서에 매개 변수를 추가하여 관련 보고서를 연결하거나 보고서 모양을 제어하거나 보고서 데이터를 필터링하거나 보고서 범위를 특정 사용자나 위치로 좁힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-103">You can add parameters to a report to link related reports, to control the report appearance, to filter report data, or to narrow the scope of a report to specific users or locations.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="6654d-104">보고서 매개 변수는 다음과 같은 방법으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-104">Report parameters are created in the following ways:</span></span>  
  
-   <span data-ttu-id="6654d-105">쿼리 변수가 포함된 데이터 세트 쿼리를 정의할 때 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-105">Automatically, when you define dataset query that contains query variables.</span></span> <span data-ttu-id="6654d-106">각 쿼리 변수의 경우 해당 데이터 세트 쿼리 매개 변수 및 보고서 매개 변수가 같은 이름으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-106">For each query variable, a corresponding dataset query parameter and report parameter with the same names are created.</span></span> <span data-ttu-id="6654d-107">쿼리 매개 변수는 저장 프로시저의 입력 매개 변수 또는 쿼리 변수에 대한 참조일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-107">A query parameter can be a reference to a query variable or to an input parameter for a stored procedure.</span></span>  
  
-   <span data-ttu-id="6654d-108">쿼리 매개 변수가 포함된 공유 데이터 세트에 참조를 추가할 때 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-108">Automatically, when you add a reference to a shared dataset that contains query parameters.</span></span>  
  
-   <span data-ttu-id="6654d-109">보고서 데이터 창에서 보고서 매개 변수를 만들 때 수동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-109">Manually, when you create report parameters in the Report Data pane.</span></span> <span data-ttu-id="6654d-110">매개 변수는 보고서의 식에 포함할 수 있는 기본 제공 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-110">Parameters are one of the built-in collections that you can include in an expression in a report.</span></span> <span data-ttu-id="6654d-111">보고서 정의 전반에서 값을 정의하는 데 식이 사용되기 때문에 매개 변수를 사용하여 보고서 모양을 제어하거나 관련 하위 보고서나 매개 변수를 사용하는 다른 보고서에 값을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-111">Because expressions are used to define values throughout a report definition, you can use parameters to control report appearance or to pass values to related subreports or reports that also use parameters.</span></span>  
  
 <span data-ttu-id="6654d-112">자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](report-parameters-report-builder-and-report-designer.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-112">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).</span></span>  
  
 <span data-ttu-id="6654d-113">데이터가 보고서에 반환되기 전과 후에 매개 변수가 보고서 데이터를 필터링하는 데 자주 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-113">Parameters are frequently used to filter report data both before and after the data is returned to the report.</span></span> <span data-ttu-id="6654d-114">자세한 내용은 [데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6654d-114">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="6654d-115">보고서를 디자인할 때는 보고서 매개 변수가 보고서 정의에 저장되고,</span><span class="sxs-lookup"><span data-stu-id="6654d-115">When you design a report, report parameters are saved in the report definition.</span></span> <span data-ttu-id="6654d-116">보고서를 게시할 때는 보고서 매개 변수가 보고서 정의와 별개로 저장되고 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-116">When you publish a report, report parameters are saved and managed separately from the report definition.</span></span> <span data-ttu-id="6654d-117">보고서를 보고서 서버에 저장한 후 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-117">After you save the report to the report server, you can do the following:</span></span>  
  
-   <span data-ttu-id="6654d-118">보고서 정의로부터 독립적으로 보고서 서버에서 보고서 매개 변수 값을 직접 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-118">Change report parameter values directly on the report server independently from the report definition.</span></span>  
  
-   <span data-ttu-id="6654d-119">각 링크된 보고서가 보고서 서버에서 독립적으로 관리될 수 있는 별도의 매개 변수 값 집합이 포함된 보고서 정의에 대한 링크인 여러 링크된 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-119">Create multiple linked reports in which each linked report is a link to the report definition with a separate set of parameter values that can be managed independently on the report server.</span></span>  
  
 <span data-ttu-id="6654d-120">보고서 스냅샷, 기록 또는 게시된 보고서에 대한 구독을 만들려는 경우 보고서 매개 변수가 보고서의 디자인 요구 사항에 미치는 영향을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6654d-120">If you plan to create report snapshots, histories, or subscriptions to a published report, you must understand how report parameters affect the design requirements for the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6654d-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6654d-121">See Also</span></span>  
 <span data-ttu-id="6654d-122">[보고서 작성기 및 SSRS &#40;보고서 제작 개념&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6654d-122">[Report Authoring Concepts &#40;Report Builder and SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6654d-123">[보고서 포함 된 데이터 집합 및 공유 데이터 집합 &#40;보고서 작성기 및 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6654d-123">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6654d-124">자습서: 보고서에 매개 변수 추가&#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="6654d-124">Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;</span></span>](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  
