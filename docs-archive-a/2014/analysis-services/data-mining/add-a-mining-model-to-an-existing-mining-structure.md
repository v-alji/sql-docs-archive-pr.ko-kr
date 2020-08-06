---
title: 기존 마이닝 구조에 마이닝 모델 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], adding
- mining structures [Analysis Services], mining models
- adding mining models
ms.assetid: fcf72300-0674-4e73-a826-9b8eeffefbb5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0afdf5f795303eaa8bb672aa80e68e0f1f891607
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653063"
---
# <a name="add-a-mining-model-to-an-existing-mining-structure"></a><span data-ttu-id="50b1d-102">기존 마이닝 구조에 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="50b1d-102">Add a Mining Model to an Existing Mining Structure</span></span>
  <span data-ttu-id="50b1d-103">초기 모델을 추가한 후 마이닝 구조에 마이닝 모델을 더 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50b1d-103">You can add more mining models to a mining structure, after you add the initial model.</span></span> <span data-ttu-id="50b1d-104">각 모델에 구조에 있는 열이 포함되어야 하지만 마이닝 모델마다 다르게 열 용도를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50b1d-104">Each model must contain columns that exist in the structure, but you can define the usage of the columns differently for each mining model.</span></span> <span data-ttu-id="50b1d-105">마이닝 모델 열을 정의하는 방법은 [마이닝 모델 열](mining-model-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50b1d-105">For more information about how to define mining models columns, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-add-a-mining-model-to-the-structure"></a><span data-ttu-id="50b1d-106">구조에 마이닝 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="50b1d-106">To add a mining model to the structure</span></span>  
  
1.  <span data-ttu-id="50b1d-107">**의** 마이닝 모델 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]메뉴 항목에서 **새 마이닝 모델**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50b1d-107">From the **Mining Model** menu item in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select **New Mining Model**.</span></span>  
  
     <span data-ttu-id="50b1d-108">**새 마이닝 모델** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="50b1d-108">The **New Mining Model** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="50b1d-109">**모델 이름**에 새 마이닝 모델의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50b1d-109">Under **Model name**, enter a name for the new mining model.</span></span>  
  
3.  <span data-ttu-id="50b1d-110">**알고리즘 이름**에서 마이닝 모델을 작성하는 데 사용할 알고리즘을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50b1d-110">Under **Algorithm name**, select the algorithm that the mining model will be built from.</span></span>  
  
4.  <span data-ttu-id="50b1d-111">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50b1d-111">Click **OK**.</span></span>  
  
 <span data-ttu-id="50b1d-112">**마이닝** 모델 탭에 새 마이닝 모델이 나타납니다. 모델에는 구조에 있는 기본 열이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50b1d-112">A new mining model appears in the **Mining Models** tab. The model uses the default columns that exist in the structure.</span></span> <span data-ttu-id="50b1d-113">열을 수정하는 방법은 [마이닝 모델의 속성 변경](change-the-properties-of-a-mining-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50b1d-113">For information about how to modify the columns, see [Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b1d-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50b1d-114">See Also</span></span>  
 [<span data-ttu-id="50b1d-115">마이닝 모델 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="50b1d-115">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
