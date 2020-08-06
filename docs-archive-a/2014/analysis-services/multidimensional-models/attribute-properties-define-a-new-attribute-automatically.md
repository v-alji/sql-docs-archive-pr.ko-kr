---
title: 자동으로 새 특성 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40f9ae1f00dd0a6520c6d1b06111864fba02e8f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741448"
---
# <a name="define-a-new-attribute-automatically"></a><span data-ttu-id="31e35-102">자동으로 새 특성 정의</span><span class="sxs-lookup"><span data-stu-id="31e35-102">Define a New Attribute Automatically</span></span>
  <span data-ttu-id="31e35-103">차원 디자이너에서 끌어서 놓기 편집을 사용하여 차원에 새 특성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31e35-103">You can create a new attribute in a dimension by using drag-and-drop editing in the Dimension Designer.</span></span>  
  
### <a name="to-create-a-new-attribute-automatically"></a><span data-ttu-id="31e35-104">자동으로 새 특성을 만들려면</span><span class="sxs-lookup"><span data-stu-id="31e35-104">To create a new attribute automatically</span></span>  
  
1.  <span data-ttu-id="31e35-105">차원 디자이너에서 특성을 만들려는 차원을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="31e35-105">In Dimension Designer, open the dimension in which you want to create the attribute.</span></span>  
  
2.  <span data-ttu-id="31e35-106">**차원 구조** 탭의 **데이터 원본 뷰** 창에 있는 특성을 바인딩할 테이블에서 열을 선택한 다음 **특성** 창으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="31e35-106">On the **Dimension Structure** tab, in the **Data Source View** pane, in the table to which you want to bind the attribute, select the column, and then drag the column to the **Attributes** pane.</span></span>  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="31e35-107">에서는 바인딩되는 열과 동일한 이름의 새 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31e35-107">creates the new attribute that has the same name as the column to which it is bound.</span></span> <span data-ttu-id="31e35-108">동일한 열을 사용하는 특성이 여러 개 있는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 특성 이름에 숫자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31e35-108">If there are multiple attributes that use the same column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] appends a number to the attribute name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e35-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31e35-109">See Also</span></span>  
 <span data-ttu-id="31e35-110">[다차원 모델의 차원](dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="31e35-110">[Dimensions in Multidimensional Models](dimensions-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="31e35-111">차원 특성 속성 참조</span><span class="sxs-lookup"><span data-stu-id="31e35-111">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
