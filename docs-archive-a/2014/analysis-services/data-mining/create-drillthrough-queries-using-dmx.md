---
title: DMX를 사용 하 여 드릴스루 쿼리 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
author: minewiskan
ms.author: owend
ms.openlocfilehash: 618732bfe48f7b1fe777f7841d686b07877d10ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653056"
---
# <a name="create-drillthrough-queries-using-dmx"></a><span data-ttu-id="fc589-102">DMX를 사용하여 드릴스루 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="fc589-102">Create Drillthrough Queries using DMX</span></span>
  <span data-ttu-id="fc589-103">드릴스루를 지원하는 모든 모델의 경우 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 DMX를 지원하는 다른 모든 클라이언트에서 DMX 쿼리를 만들어 사례 데이터 및 구조 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc589-103">For all models that support drillthrough, you can retrieve case data and structure data by creating a DMX query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any other client that supports DMX.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="fc589-104">데이터를 보려면 드릴스루를 사용하도록 설정되었으며 필요한 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc589-104">To view the data, drillthrough must have been enabled, and you must have the necessary permissions.</span></span>  
  
## <a name="specifying-drillthrough-options"></a><span data-ttu-id="fc589-105">드릴스루 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="fc589-105">Specifying Drillthrough Options</span></span>  
 <span data-ttu-id="fc589-106">모델 사례 및 구조 사례를 검색하는 일반 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fc589-106">The general syntax is for retrieving model cases and structure cases is as follows:</span></span>  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 <span data-ttu-id="fc589-107">DMX 쿼리를 사용하여 사례 데이터를 반환하는 방법에 대한 자세한 내용은 [SELECT FROM &#60;model&#62;.CASES&#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) 및 [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc589-107">For additional information about using DMX queries to return case data, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) and [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fc589-108">예</span><span class="sxs-lookup"><span data-stu-id="fc589-108">Examples</span></span>  
 <span data-ttu-id="fc589-109">다음 DMX 쿼리는 시계열 모델의 특정 제품 계열에 대한 사례 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fc589-109">The following DMX query returns the case data for a specific product series, from a time series model.</span></span> <span data-ttu-id="fc589-110">또한 이 쿼리는 모델에 사용되지 않았지만 마이닝 구조에서는 사용할 수 있는 `Amount` 열도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fc589-110">The query also returns the column `Amount`, which was not used in the model but is available in the mining structure.</span></span>  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 <span data-ttu-id="fc589-111">이 예에서는 별칭을 사용하여 구조 열의 이름을 바꾸었습니다.</span><span class="sxs-lookup"><span data-stu-id="fc589-111">Note that in this example, an alias has been used to rename the structure column.</span></span> <span data-ttu-id="fc589-112">구조 열에 별칭을 할당하지 않는 경우 열은 'Expression'이라는 이름으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc589-112">If you do not assign an alias to the structure column, the column is returned with the name 'Expression'.</span></span> <span data-ttu-id="fc589-113">이 동작은 명명되지 않은 모든 열의 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="fc589-113">This is the default behavior for all unnamed columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc589-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc589-114">See Also</span></span>  
 <span data-ttu-id="fc589-115">[드릴스루 쿼리 &#40;데이터 마이닝&#41;](drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="fc589-115">[Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md) </span></span>  
 [<span data-ttu-id="fc589-116">마이닝 구조에서의 드릴스루</span><span class="sxs-lookup"><span data-stu-id="fc589-116">Drillthrough on Mining Structures</span></span>](drillthrough-on-mining-structures.md)  
  
  
