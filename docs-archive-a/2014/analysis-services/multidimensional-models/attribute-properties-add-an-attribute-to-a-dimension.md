---
title: 차원에 특성 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- adding attributes
- automatic attribute creation
- attributes [Analysis Services], creating
- attributes [Analysis Services], adding
- manual attribute creation [Analysis Services]
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
author: minewiskan
ms.author: owend
ms.openlocfilehash: 776591e94deedc679592cfe36d53fb1fea4093d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660722"
---
# <a name="add-an--attribute-to-a-dimension"></a><span data-ttu-id="99596-102">차원에 특성 추가</span><span class="sxs-lookup"><span data-stu-id="99596-102">Add an  Attribute to a Dimension</span></span>
  <span data-ttu-id="99596-103">에서 자동으로 또는 수동으로 차원에 특성을 추가할 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="99596-103">You can add an attribute to a dimension either automatically or manually in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="99596-104">특성을 자동으로 만들려면 **에 있는 차원 디자이너의** 차원 구조 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭에서 특성에 매핑할 열을 선택하고 **데이터 원본 뷰** 창에서 **특성** 창으로 해당 열을 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="99596-104">To create an attribute automatically, on the **Dimension Structure** tab of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the column that you want to map to an attribute, and then drag that column from the **Data Source View** pane to the **Attributes** pane.</span></span> <span data-ttu-id="99596-105">이렇게 하면 열에 매핑되는 특성이 생성되고 특성에 열과 동일한 이름이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="99596-105">This creates an attribute that is mapped to the column, and assigns the same name to the attribute as the name of the column.</span></span> <span data-ttu-id="99596-106">해당 이름으로 된 특성이 이미 있는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 첫 번째 중복 이름에 대해 "1"로 시작하는 서수 접미사 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="99596-106">If an attribute that uses that name already exists, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] adds an ordinal number suffix, starting with "1" for the first duplicate name.</span></span>  
  
 <span data-ttu-id="99596-107">특성을 수동으로 만들려면 **특성** 창을 표 뷰로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="99596-107">To create an attribute manually, set the **Attributes** pane to grid view.</span></span> <span data-ttu-id="99596-108">표에서 마지막 행의 이름 열에서 항목을 클릭 **\<new attribute>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="99596-108">In the name column of the last row in the grid, click the **\<new attribute>** item.</span></span> <span data-ttu-id="99596-109">새 특성의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="99596-109">Type a name for the new attribute.</span></span> <span data-ttu-id="99596-110">이렇게 하면 열에 매핑되지 않고 모든 해당 속성에 대한 기본 설정이 있는 특성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="99596-110">This creates an attribute that is not mapped to a column and that has default settings for all its properties.</span></span> <span data-ttu-id="99596-111">새 특성에 대한 **KeyColumns** 속성을 구성하여 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 의 **속성** 창에서 매핑을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99596-111">You can set the mapping in the **Properties** window of [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] by configuring the **KeyColumns** property for the new attribute.</span></span>  
  
 <span data-ttu-id="99596-112">자세한 내용은 [자동으로 새 특성 정의](attribute-properties-define-a-new-attribute-automatically.md), [수동으로 새 특성 정의](../define-a-new-attribute-manually.md), [이름 열로 특성 바인딩](attribute-properties-bind-an-attribute-to-a-name-column.md), [특성의 KeyColumn 속성 수정](attribute-properties-modify-the-keycolumn-property.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99596-112">For more information, see [Define a New Attribute Automatically](attribute-properties-define-a-new-attribute-automatically.md), [Define a New Attribute Manually](../define-a-new-attribute-manually.md), [Bind an Attribute to a Name Column](attribute-properties-bind-an-attribute-to-a-name-column.md), and [Modify the KeyColumn Property of an Attribute](attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99596-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99596-113">See Also</span></span>  
 [<span data-ttu-id="99596-114">차원 특성 속성 참조</span><span class="sxs-lookup"><span data-stu-id="99596-114">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
