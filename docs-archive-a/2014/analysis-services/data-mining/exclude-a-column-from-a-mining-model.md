---
title: 마이닝 모델에서 열 제외 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30affebc143184c6287858f60b5d4f5d089c322a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649270"
---
# <a name="exclude-a-column-from-a-mining-model"></a><span data-ttu-id="1b31e-102">마이닝 모델에서 열 제외</span><span class="sxs-lookup"><span data-stu-id="1b31e-102">Exclude a Column from a Mining Model</span></span>
  <span data-ttu-id="1b31e-103">새 마이닝 모델을 만들 때 모델의 기반이 되는 마이닝 구조의 일부 열만 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b31e-103">When you create a new mining model, you may not want to use all the columns that exist in the mining structure on which the model is based.</span></span> <span data-ttu-id="1b31e-104">예를 들어 드릴스루를 위해 고객 이름 열을 추가 했지만 모델링에는 사용 하지 않으려는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b31e-104">For example, you might have added a customer name column for drillthrough, but don't want to use it for modeling.</span></span> <span data-ttu-id="1b31e-105">또는 여러 다른 불연속화가 있는 열의 여러 복사본을 만든 후 각 모델에 해당 복사본 중 하나만 사용하고 나머지는 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b31e-105">Or, you might decide to create multiple copies of a column with different discretizations, and use only one of the copies in each model, and ignore the rest.</span></span> <span data-ttu-id="1b31e-106">여러 다른 모델에 입력 열을 선택적으로 추가하여 추가된 변수가 출력 열에 영향을 주는 방식을 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b31e-106">You could also selectively add input columns in several different models to see how the added variable affects the output column.</span></span>  
  
 <span data-ttu-id="1b31e-107">각 열 조합에 대해 새 마이닝 구조를 만들 필요가 없습니다. 대신, 특정 모델에서 사용되지 않도록 열에 플래그를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b31e-107">You do not need to create a new mining structure for each combination of columns; instead, you can simply flag a column as not being used in a particular model.</span></span>  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a><span data-ttu-id="1b31e-108">마이닝 모델에서 열을 제외하려면</span><span class="sxs-lookup"><span data-stu-id="1b31e-108">To exclude a column from a mining model</span></span>  
  
1.  <span data-ttu-id="1b31e-109">**의 데이터 마이닝 디자이너에서** 마이닝 모델 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭을 선택하고 해당 마이닝 모델에서 제외할 열에 해당하는 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1b31e-109">In the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the cell that corresponds to the column you want to exclude, under the appropriate mining model.</span></span>  
  
2.  <span data-ttu-id="1b31e-110">드롭다운 목록 상자에서 **무시** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1b31e-110">Select **Ignore** from the drop-down list box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b31e-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1b31e-111">See Also</span></span>  
 [<span data-ttu-id="1b31e-112">마이닝 모델 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="1b31e-112">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
