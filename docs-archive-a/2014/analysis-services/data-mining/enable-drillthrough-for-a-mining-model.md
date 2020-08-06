---
title: 마이닝 모델에 드릴스루 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- drillthrough [Analysis Services]
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a6adfc389776f91132e527130f50f61c9783d9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646714"
---
# <a name="enable-drillthrough-for-a-mining-model"></a><span data-ttu-id="4424f-102">마이닝 모델에 드릴스루 사용</span><span class="sxs-lookup"><span data-stu-id="4424f-102">Enable Drillthrough for a Mining Model</span></span>
  <span data-ttu-id="4424f-103">마이닝 모델에 드릴스루를 사용하는 경우 모델을 찾을 때 모델을 만드는 데 사용된 사례에 대한 세부 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-103">If you have enabled drillthrough for a mining model, when you browse the model you can retrieve detailed information about the cases that were used to create the model.</span></span> <span data-ttu-id="4424f-104">이 정보를 보려면 필요한 사용 권한이 있어야 하고 구조가 이미 처리되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-104">To view this information, you must have the necessary permissions, and the structure must have already been processed.</span></span>  
  
 <span data-ttu-id="4424f-105">**권한** 사용자가 모델 데이터 또는 구조 데이터로 드릴스루하려면 마이닝 모델 또는 마이닝 구조에 대한 [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) 권한이 있는 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-105">**Permissions** For a user to drill through to either model data or structure data, the user must be a member of a role that has [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) permissions on the mining model or mining structure.</span></span> <span data-ttu-id="4424f-106">드릴스루 권한은 구조와 모델에 개별적으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-106">Drillthrough permissions are set separately on the structure and model.</span></span>  
  
-   <span data-ttu-id="4424f-107">모델에 대한 드릴스루 권한이 있으면 구조에 대한 사용 권한이 없는 경우에도 모델에서 드릴스루할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-107">Drillthrough permissions on the model enable you to drill through from the model, even if you do not have permissions on the structure.</span></span>  
  
-   <span data-ttu-id="4424f-108">구조에 대한 드릴스루 권한이 있으면 추가적으로 [StructureColumn&#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) 함수를 사용하여 모델에서 드릴스루 쿼리에 구조 열을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-108">Drillthrough permissions on the structure provide the additional ability to include structure columns in drillthrough queries from the model, by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span> <span data-ttu-id="4424f-109">SELECT ...를 사용 하 여 구조에서 학습 및 테스트 사례를 쿼리할 수도 있습니다. 에서 \<structure> . CASE 구문.</span><span class="sxs-lookup"><span data-stu-id="4424f-109">You can also query the training and test cases in the structure by using the SELECT... FROM \<structure>.CASES syntax.</span></span>  
  
 <span data-ttu-id="4424f-110">**학습 사례의 캐싱** 드릴스루는 마이닝 구조의 학습 사례에 대한 정보를 검색하는 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-110">**Caching of training cases** Drillthrough works by retrieving information about the training cases in the mining structure.</span></span> <span data-ttu-id="4424f-111">이 정보는 구조가 처리될 때 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-111">This information is cached when the structure is processed.</span></span> <span data-ttu-id="4424f-112">따라서 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 속성을 `ClearAfterProcessing`으로 변경하여 캐시된 모든 데이터를 지우도록 선택한 경우에는 드릴스루가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-112">Therefore, if you choose to clear all cached data by changing the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to `ClearAfterProcessing`, drillthrough will not work.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4424f-113">학습 사례가 캐시되지 않은 경우에는 사례 데이터를 보기 전에 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 속성을 **KeepTrainingCases** 로 변경한 다음 모델을 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-113">If the training cases have not been cached, you must change the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property to **KeepTrainingCases** and then reprocess the model before you can view the case data.</span></span>  
  
 <span data-ttu-id="4424f-114">자세한 내용은 [드릴스루 쿼리&#40;데이터 마이닝&#41;](drillthrough-queries-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4424f-114">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a><span data-ttu-id="4424f-115">마이닝 모델에서 드릴스루를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="4424f-115">To enable drillthrough on a mining model</span></span>  
  
1.  <span data-ttu-id="4424f-116">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에 있는 데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 드릴스루를 사용할 마이닝 모델의 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Mining Models** tab of Data Mining Designer, right-click the name of the mining model on which you want to enable drillthrough, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="4424f-117">**속성** 창에서 **allowdrillthrough**를 클릭 하 고 **True**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-117">In the **Properties** windows, click **AllowDrillthrough**, and select **True**.</span></span>  
  
3.  <span data-ttu-id="4424f-118">**마이닝 모델** 탭에서 모델을 마우스 오른쪽 단추로 클릭하고 **모델 처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-118">In the **Mining Models** tab, right-click the model, and select **Process Model**.</span></span>  
  
### <a name="to-enable-caching-for-a-mining-structure"></a><span data-ttu-id="4424f-119">마이닝 구조에 캐싱을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="4424f-119">To enable caching for a mining structure</span></span>  
  
1.  <span data-ttu-id="4424f-120">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 데이터 마이닝 디자이너에 있는 **마이닝 구조** 탭에서 마이닝 구조 이름을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-120">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], on the **Mining Structure** tab of Data Mining Designer, right-click the name of the mining structure.</span></span>  
  
2.  <span data-ttu-id="4424f-121">**속성** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-121">Open the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="4424f-122">**속성** 창에서 **CacheMode** 속성을 찾고 목록에서 **KeepTrainingCases** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-122">In the **Properties** window, locate the **CacheMode** property, and select **KeepTrainingCases** from the list.</span></span>  
  
4.  <span data-ttu-id="4424f-123">**데이터베이스** 메뉴에서 **처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4424f-123">On the **Database** menu, select **Process**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4424f-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4424f-124">See Also</span></span>  
 [<span data-ttu-id="4424f-125">드릴스루 쿼리&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="4424f-125">Drillthrough Queries &#40;Data Mining&#41;</span></span>](drillthrough-queries-data-mining.md)  
  
  
