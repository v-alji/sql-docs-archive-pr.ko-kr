---
title: 모델 열의 별칭 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- mining models [Analysis Services], columns
- column names [Analysis Services]
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 908c0a8d8caa810badf4b82dc3dd3f411d09f323
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647325"
---
# <a name="create-an-alias-for-a-model-column"></a><span data-ttu-id="5326e-102">모델 열의 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="5326e-102">Create an Alias for a Model Column</span></span>
  <span data-ttu-id="5326e-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 모델 열의 별칭을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5326e-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can create an alias for a model column.</span></span> <span data-ttu-id="5326e-104">이것은 마이닝 구조 이름이 너무 길어서 쉽게 사용할 수 없거나 모델에서 열의 내용과 사용을 잘 설명하도록 열 이름을 변경할 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="5326e-104">This might be useful when the mining structure name is too long to easily work with, or when you want to rename the column to be more descriptive of its contents or usage in the model.</span></span> <span data-ttu-id="5326e-105">예를 들어 구조 열의 복사본을 만든 다음 특정 모델과 다르게 열을 불연속화한 경우 내용을 보다 정확하게 나타내도록 열의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5326e-105">For example, if you make a copy of a structure column and then discretize the column differently for a particular model, you can rename the column to reflect the content more accurately.</span></span>  
  
 <span data-ttu-id="5326e-106">모델 열의 별칭을 만들려면 **속성** 창을 사용하여 열의 [Name](https://docs.microsoft.com/bi-reference/assl/properties/name-element-assl) 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5326e-106">To create an alias for a model column, you use the **Properties** pane and set the [Name](https://docs.microsoft.com/bi-reference/assl/properties/name-element-assl) property of the column.</span></span>  
  
 <span data-ttu-id="5326e-107">데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 별칭은 열 사용 레이블 옆 괄호 안에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5326e-107">On the **Mining Models** tab of Data Mining Designer, the alias appears enclosed in parentheses next to the column usage label.</span></span>  
  
 <span data-ttu-id="5326e-108">마이닝 모델의 속성을 설정하는 방법은 [마이닝 모델 열](mining-model-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5326e-108">For information about how to set the properties of a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a><span data-ttu-id="5326e-109">마이닝 모델 열에 별칭을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5326e-109">To add an alias to a mining model column</span></span>  
  
1.  <span data-ttu-id="5326e-110">데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 변경할 마이닝 열의 마이닝 모델에 있는 셀을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5326e-110">In the **Mining Models** tab in Data Mining Designer, right-click the cell in the mining model for the mining column that you want to change, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="5326e-111">화면 오른쪽의 **속성** 창에서 이름 속성 옆의 셀을 클릭하고 현재 값을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5326e-111">In the **Properties** window on the right side of the screen, click the cell next to the Name property and delete the current value.</span></span> <span data-ttu-id="5326e-112">열의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5326e-112">Type a new name for the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5326e-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5326e-113">See Also</span></span>  
 <span data-ttu-id="5326e-114">[마이닝 모델 태스크 및 방법](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="5326e-114">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="5326e-115">마이닝 모델 속성</span><span class="sxs-lookup"><span data-stu-id="5326e-115">Mining Model Properties</span></span>](mining-model-properties.md)  
  
  
