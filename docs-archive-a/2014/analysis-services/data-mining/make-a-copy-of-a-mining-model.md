---
title: 마이닝 모델의 복사본 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], copying
- mining models [Analysis Services], creating
- mining models [Analysis Services], how-to topics
- copying mining models
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
author: minewiskan
ms.author: owend
ms.openlocfilehash: a05eb75210ce9f601aeca515cd299f4204908705
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639112"
---
# <a name="make-a-copy-of-a-mining-model"></a><span data-ttu-id="83f37-102">마이닝 모델 복사본 만들기</span><span class="sxs-lookup"><span data-stu-id="83f37-102">Make a Copy of a Mining Model</span></span>
  <span data-ttu-id="83f37-103">마이닝 모델의 복사본을 만들면 동일한 데이터를 기반으로 여러 마이닝 모델을 빠르게 만들 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-103">Creating a copy of a mining model is useful when you want to quickly create several mining models that are based on the same data.</span></span> <span data-ttu-id="83f37-104">모델을 복사한 후 매개 변수를 변경하거나 필터를 추가하여 새 복사본을 편집할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-104">After you copy the model, you can then edit the new copy by changing parameters or adding a filter.</span></span>  
  
 <span data-ttu-id="83f37-105">예를 들어 구매 테이블에 연결된 Customers 테이블이 있는 경우 나이 또는 지역과 같은 특성을 기준으로 필터링하여 각 고객 인구 통계에 대한 별도의 마이닝 모델을 생성하도록 복사본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-105">For example, if you have a Customers table that is linked to a table of purchases, you could create copies to generate separate mining models for each customer demographic, filtering on attributes such as age or region.</span></span>  
  
 <span data-ttu-id="83f37-106">다른 프로그램에서 사용할 수 있도록 그래픽 표현 또는 모델 패턴과 같은 모델 내용을 클립보드에 복사하는 방법에 대한 자세한 내용은 [마이닝 모델의 뷰 복사](copy-a-view-of-a-mining-model.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83f37-106">For information about how to copy the content of the model (such as the graphical representation or the model patterns) to the Clipboard for use in other programs, see [Copy a View of a Mining Model](copy-a-view-of-a-mining-model.md).</span></span>  
  
### <a name="to-create-a-related-mining-model"></a><span data-ttu-id="83f37-107">관련 마이닝 모델을 만들려면</span><span class="sxs-lookup"><span data-stu-id="83f37-107">To create a related mining model</span></span>  
  
1.  <span data-ttu-id="83f37-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 마이닝 모델이 포함된 마이닝 구조를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model.</span></span>  
  
2.  <span data-ttu-id="83f37-109">**마이닝 모델** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-109">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="83f37-110">모델을 선택하고 마우스 오른쪽 단추를 클릭하여 바로 가기 메뉴를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-110">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="83f37-111">또는</span><span class="sxs-lookup"><span data-stu-id="83f37-111">-or-</span></span>  
  
     <span data-ttu-id="83f37-112">모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-112">Select the model.</span></span> <span data-ttu-id="83f37-113">**마이닝 모델** 메뉴에서 **새 마이닝 모델**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-113">On the **Mining Model** menu, select **New Mining Model**.</span></span>  
  
4.  <span data-ttu-id="83f37-114">새 마이닝 모델의 이름을 입력하고 알고리즘을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-114">Type a name for the new mining model, and select an algorithm.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a><span data-ttu-id="83f37-115">복사된 마이닝 모델에서 필터를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="83f37-115">To edit the filter on the copied mining model</span></span>  
  
1.  <span data-ttu-id="83f37-116">마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-116">Select the mining model.</span></span>  
  
2.  <span data-ttu-id="83f37-117">**속성** 창에서 **필터** 속성의 입력란을 클릭 하 고 빌드 **(...)** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-117">In the **Properties** window, click the text box for the **Filter** property, and the click the build **(...)** button.</span></span>  
  
3.  <span data-ttu-id="83f37-118">필터 조건을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-118">Change the filter conditions.</span></span>  
  
     <span data-ttu-id="83f37-119">필터 편집기 대화 상자를 사용하는 방법에 대한 자세한 내용은 [마이닝 모델에 필터 적용](apply-a-filter-to-a-mining-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83f37-119">For more information about how to use the filter editor dialog boxes, see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
4.  <span data-ttu-id="83f37-120">**속성** 창의 `AlgorithmParameters` 텍스트 상자에서 **setalgorithm 매개 변수**를 클릭 하 고 원하는 경우 알고리즘 매개 변수를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="83f37-120">In the **Properties** window, in the `AlgorithmParameters` text box, click **Setalgorithm parameters**, and change algorithm parameters, if desired.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="83f37-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83f37-121">See Also</span></span>  
 <span data-ttu-id="83f37-122">[마이닝 모델 &#40;Analysis Services 데이터 마이닝&#41;필터](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="83f37-122">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="83f37-123">[마이닝 모델 태스크 및 방법](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="83f37-123">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="83f37-124">마이닝 모델에서 필터 삭제</span><span class="sxs-lookup"><span data-stu-id="83f37-124">Delete a Filter from a Mining Model</span></span>](delete-a-filter-from-a-mining-model.md)  
  
  
