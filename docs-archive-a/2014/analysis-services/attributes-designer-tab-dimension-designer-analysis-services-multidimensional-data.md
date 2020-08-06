---
title: 특성 (특성 관계 디자이너 탭, 차원 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.ardesigner.attributes.f1
ms.assetid: 850a68aa-1d70-4f0f-ba39-aeca834596c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: baced7debe540827d603d39f9978a1e18bc17762
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648157"
---
# <a name="attributes-attribute-relationship-designer-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="39990-102">특성(특성 관계 디자이너 탭, 차원 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="39990-102">Attributes (Attribute Relationship Designer Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="39990-103">**특성** 목록을 사용하여 특성 관계 다이어그램에서 특정 특성을 찾거나 새 특성 관계를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39990-103">Use the **Attributes** list to locate a specific attribute in the attribute relationship diagram or to define a new attribute relationship.</span></span> <span data-ttu-id="39990-104">이 창은 특성 관계 다이어그램이 있는 창 바로 아래에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="39990-104">This pane appears immediately under the pane that contains the attribute relationship diagram.</span></span>  
  
 <span data-ttu-id="39990-105">**특성 창을 보려면**</span><span class="sxs-lookup"><span data-stu-id="39990-105">**To view the Attributes pane**</span></span>  
  
1.  <span data-ttu-id="39990-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 차원을 두 번 클릭하여 차원 디자이너를 연 다음 **특성 관계** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39990-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, double-click a dimension to open the Dimension Designer, and then click the **Attribute Relationship** tab.</span></span>  
  
2.  <span data-ttu-id="39990-107">도구 모음에서 **목록 뷰 표시** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39990-107">On the toolbar, click the **Show List Views** icon.</span></span>  
  
## <a name="using-the-attributes-list"></a><span data-ttu-id="39990-108">특성 목록 사용</span><span class="sxs-lookup"><span data-stu-id="39990-108">Using the Attributes List</span></span>  
 <span data-ttu-id="39990-109">**특성** 목록은 차원의 모든 특성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="39990-109">The **Attributes** list displays all of the attributes in the dimension.</span></span>  
  
 <span data-ttu-id="39990-110">특성 관계 다이어그램에서 특정 특성을 찾으려면 목록에서 해당 특성을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39990-110">To locate a specific attribute in the attribute relationship diagram, double-click the attribute in the list.</span></span> <span data-ttu-id="39990-111">특성이 특성 관계 다이어그램에 강조 표시되고 해당 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="39990-111">The attribute will be highlighted in the attribute relationship diagram and its properties will appear in the Properties window.</span></span> <span data-ttu-id="39990-112">특성 관계 다이어그램에 특성이 표시되지 않으면 **속성** 창에 특성의 속성만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="39990-112">If the attribute is not shown in the attribute relationship diagram, only the attribute's properties will appear in the **Properties** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39990-113">목록에서 여러 특성을 선택하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39990-113">You can select multiple attributes in the list and make changes.</span></span>  
  
 <span data-ttu-id="39990-114">새 관계를 정의하거나 특성의 이름을 바꾸려면 특성을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 해당 명령을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39990-114">To define a new relationship or rename the attribute, right-click the attribute and click the corresponding command in the shortcut menu.</span></span>  
  
### <a name="shortcut-menu-options"></a><span data-ttu-id="39990-115">바로 가기 메뉴 옵션</span><span class="sxs-lookup"><span data-stu-id="39990-115">Shortcut Menu Options</span></span>  
 <span data-ttu-id="39990-116">**새 특성 관계**</span><span class="sxs-lookup"><span data-stu-id="39990-116">**New Attribute Relationship**</span></span>  
 <span data-ttu-id="39990-117">새 특성 관계를 정의할 수 있는 **특성 관계 만들기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="39990-117">Opens the **Create Attribute Relationship** dialog box in which you can define a new attribute relationship.</span></span>  
  
 <span data-ttu-id="39990-118">자세한 내용은 [특성 관계 만들기 및 특성 관계 편집 대화 상자&#40;특성 관계 디자이너 탭, 차원 디자이너&#41;&#40;Analysis Services - 다차원 데이터&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) 및 [특성 관계 정의](multidimensional-models/attribute-relationships-define.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39990-118">For more information, see [Create Attribute Relationship and Edit Attribute Relationship Dialog Boxes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) and [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md).</span></span>  
  
 <span data-ttu-id="39990-119">**이름 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="39990-119">**Rename**</span></span>  
 <span data-ttu-id="39990-120">목록에서 특성의 이름을 강조 표시하고 이 텍스트를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39990-120">Highlights the attribute's name in the list and enables you to modify this text.</span></span>  
  
 <span data-ttu-id="39990-121">**속성**</span><span class="sxs-lookup"><span data-stu-id="39990-121">**Properties**</span></span>  
 <span data-ttu-id="39990-122">**속성** 창에 특성의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="39990-122">Displays the attribute's properties in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39990-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39990-123">See Also</span></span>  
 <span data-ttu-id="39990-124">[차원 디자이너&#41; &#40;Analysis Services 다차원 데이터를 &#40;특성 관계&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="39990-124">[Attribute Relationships &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="39990-125">[도구 모음 &#40;특성 관계 디자이너 탭, 차원 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="39990-125">[Toolbar &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="39990-126">[특성 관계 다이어그램 &#40;특성 관계 디자이너 탭, 차원 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](attribute-relationship-diagram-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="39990-126">[Attribute Relationship Diagram &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attribute-relationship-diagram-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="39990-127">특성 관계 &#40;특성 관계 디자이너 탭, 차원 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="39990-127">Attribute Relationships &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](attribute-relationships-designer-tab-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
