---
title: 번역 세부 정보 (번역 탭, 차원 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.translations.translationpane.tranlationdetails.f1
ms.assetid: 0aa61df3-f2b0-4703-a63b-124da672dcc3
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7cbe4a3c69111d0f82f96ff5125f80fe0c2c57f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738769"
---
# <a name="translation-details-translations-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="71a55-102">번역 세부 정보(번역 탭, 차원 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="71a55-102">Translation Details (Translations Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="71a55-103">차원 디자이너에서 **번역** 탭의 **번역 세부 정보** 창을 사용하여 현재 선택한 차원의 번역을 정의하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-103">Use the **Translation Details** pane on the **Translations** tab of Dimension Designer to define and manage translations for the currently selected dimension.</span></span>  
  
 <span data-ttu-id="71a55-104">**번역 세부 정보 창을 표시하려면**</span><span class="sxs-lookup"><span data-stu-id="71a55-104">**To display the Translations Details pane**</span></span>  
  
1.  <span data-ttu-id="71a55-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 연 다음 원하는 차원을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then open the dimension that you want.</span></span>  
  
2.  <span data-ttu-id="71a55-106">**번역** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-106">Click the **Translations** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="71a55-107">옵션</span><span class="sxs-lookup"><span data-stu-id="71a55-107">Options</span></span>  
 <span data-ttu-id="71a55-108">**기본 언어**</span><span class="sxs-lookup"><span data-stu-id="71a55-108">**Default Language**</span></span>  
 <span data-ttu-id="71a55-109">차원 개체의 이름을 기본 언어로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-109">Sets the names of the dimension objects in the default language.</span></span>  
  
 <span data-ttu-id="71a55-110">**개체 형식**</span><span class="sxs-lookup"><span data-stu-id="71a55-110">**Object Type**</span></span>  
 <span data-ttu-id="71a55-111">번역될 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-111">Displays the property that will be translated.</span></span> <span data-ttu-id="71a55-112">값이 지정된 개체와 속성만 번역할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-112">Only objects and properties for which values have been specified can be translated.</span></span> <span data-ttu-id="71a55-113">다음은 번역할 수 있는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-113">The following properties can be translated:</span></span>  
  
-   <span data-ttu-id="71a55-114">차원</span><span class="sxs-lookup"><span data-stu-id="71a55-114">Dimension</span></span>  
  
     <span data-ttu-id="71a55-115">`Caption` 및 `AttributeAllMember` 속성</span><span class="sxs-lookup"><span data-stu-id="71a55-115">`Caption` and `AttributeAllMember` properties</span></span>  
  
-   <span data-ttu-id="71a55-116">특성</span><span class="sxs-lookup"><span data-stu-id="71a55-116">Attribute</span></span>  
  
     <span data-ttu-id="71a55-117">`Caption`, `AttributeHierarchyDisplayFolder` 및 `NamingTemplate` 속성</span><span class="sxs-lookup"><span data-stu-id="71a55-117">`Caption`, `AttributeHierarchyDisplayFolder`, and `NamingTemplate` properties</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="71a55-118">`NamingTemplate` 속성은 부모 특성에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-118">The `NamingTemplate` property is available only for parent attributes.</span></span>  
  
-   <span data-ttu-id="71a55-119">계층</span><span class="sxs-lookup"><span data-stu-id="71a55-119">Hierarchy</span></span>  
  
     <span data-ttu-id="71a55-120">`Caption` 및 `AllMemberName` 속성</span><span class="sxs-lookup"><span data-stu-id="71a55-120">`Caption` and `AllMemberName` properties</span></span>  
  
-   <span data-ttu-id="71a55-121">Level</span><span class="sxs-lookup"><span data-stu-id="71a55-121">Level</span></span>  
  
     <span data-ttu-id="71a55-122">`Caption` 속성</span><span class="sxs-lookup"><span data-stu-id="71a55-122">`Caption` property</span></span>  
  
 **\<Language>**  
 <span data-ttu-id="71a55-123">차원 개체의 속성 값을 선택한 언어로 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-123">Type or select the property value of the dimension object in the selected language.</span></span> <span data-ttu-id="71a55-124">줄임표 단추(**...**)를 클릭하면 편집 중인 속성에 따라 추가 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-124">Clicking the ellipsis button (**...**) opens additional dialog boxes, depending on the property being edited:</span></span>  
  
-   <span data-ttu-id="71a55-125">`NamingTemplate` 속성</span><span class="sxs-lookup"><span data-stu-id="71a55-125">`NamingTemplate` property</span></span>  
  
     <span data-ttu-id="71a55-126">[수준 명명 템플릿 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](level-naming-template-dialog-box-analysis-services-multidimensional-data.md)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-126">Displays the [Level Naming Template Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](level-naming-template-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
-   <span data-ttu-id="71a55-127">`Caption` 속성(특성의 경우)</span><span class="sxs-lookup"><span data-stu-id="71a55-127">`Caption` property (for attributes)</span></span>  
  
     <span data-ttu-id="71a55-128">[특성 데이터 번역 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-128">Displays the [Attribute Data Translation Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="shortcut-menu"></a><span data-ttu-id="71a55-129">바로 가기 메뉴</span><span class="sxs-lookup"><span data-stu-id="71a55-129">Shortcut Menu</span></span>  
 <span data-ttu-id="71a55-130">다음 옵션은 **번역 세부 정보** 창에서 번역을 마우스 오른쪽 단추로 클릭하면 표시되는 바로 가기 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-130">The following options are available in the shortcut menu displayed by right-clicking a translation in the **Translation Details** pane:</span></span>  
  
 <span data-ttu-id="71a55-131">**새 번역**</span><span class="sxs-lookup"><span data-stu-id="71a55-131">**New Translation**</span></span>  
 <span data-ttu-id="71a55-132">**언어 선택** 대화 상자를 표시하여 새 번역을 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-132">Select to display the **Select Language** dialog box and create a new translation.</span></span> <span data-ttu-id="71a55-133">해당 번역은 **번역 세부 정보** 표에 새 열로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-133">The translation will appear as a new column in the **Translation Details** grid.</span></span>  
  
 <span data-ttu-id="71a55-134">**번역 삭제**</span><span class="sxs-lookup"><span data-stu-id="71a55-134">**Delete Translation**</span></span>  
 <span data-ttu-id="71a55-135">선택한 번역을 삭제하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-135">Select to delete the selected translation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71a55-136">이 옵션은 셀을 마우스 오른쪽 단추로 클릭하여 번역을 삭제한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-136">The option is enabled only if you right-clicked a cell to delete the translation.</span></span>  
  
 <span data-ttu-id="71a55-137">**새 캡션 열**</span><span class="sxs-lookup"><span data-stu-id="71a55-137">**New Caption Column**</span></span>  
 <span data-ttu-id="71a55-138">**특성 데이터 번역** 대화 상자를 표시하고 **번역 세부 정보** 표에서 특성을 수정할 때 새 캡션 열을 정의하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-138">Select to display the **Attribute Data Translation** dialog box and define a new caption column when you modify an attribute in the **Translation Details** grid.</span></span> <span data-ttu-id="71a55-139">이 옵션을 사용하려면 **번역 세부 정보** 표에서 특성에 대한 번역 열의 셀을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-139">To enable this option, a cell in a translation column for an attribute must be selected in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71a55-140">이 옵션은 셀을 마우스 오른쪽 단추로 클릭하여 특성의 번역 열을 삭제한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-140">The option is enabled only if you right-clicked a cell to delete the translation column of an attribute.</span></span>  
  
 <span data-ttu-id="71a55-141">**캡션 열 편집**</span><span class="sxs-lookup"><span data-stu-id="71a55-141">**Edit Caption Column**</span></span>  
 <span data-ttu-id="71a55-142">**특성 데이터 번역** 대화 상자를 표시하고 **번역 세부 정보** 표에서 특성을 수정할 때 기존 캡션 열을 수정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-142">Select to display the **Attribute Data Translation** dialog box and modify an existing caption column when you modify an attribute in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71a55-143"> 이 옵션은 **번역 세부 정보** 표에서 특성에 대한 캡션 열이 포함된 번역 열의 셀을 선택하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-143">The option is enabled only if a cell in a translation column that contains a caption column for an attribute must be selected in the **Translation Details** grid.</span></span>  
  
 <span data-ttu-id="71a55-144">**캡션 열 삭제**</span><span class="sxs-lookup"><span data-stu-id="71a55-144">**Delete Caption Column**</span></span>  
 <span data-ttu-id="71a55-145">**번역 세부 정보** 표에서 선택한 특성의 캡션 열을 삭제하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-145">Select to delete the caption column for the selected attribute in the **Translation Details** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71a55-146">이 옵션은 특성의 캡션 열이 포함된 번역 열의 셀을 마우스 오른쪽 단추로 클릭한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-146">The option is enabled only if you right-clicked a cell in a translation column that contains a caption column for an attribute.</span></span>  
  
 <span data-ttu-id="71a55-147">**모든 특성 표시**</span><span class="sxs-lookup"><span data-stu-id="71a55-147">**Show All Attributes**</span></span>  
 <span data-ttu-id="71a55-148">특성 계층이 해제된 특성을 포함하여 선택한 차원에 대해 정의된 모든 특성을 표시하거나 숨기려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71a55-148">Select to toggle the display of all attributes defined for the selected dimension, including attributes for which attribute hierarchies are disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a55-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71a55-149">See Also</span></span>  
 [<span data-ttu-id="71a55-150">번역 &#40;차원 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="71a55-150">Translations &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
