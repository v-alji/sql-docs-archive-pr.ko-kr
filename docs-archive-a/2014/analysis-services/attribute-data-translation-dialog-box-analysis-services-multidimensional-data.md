---
title: 특성 데이터 번역 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.dimensionstoragesettings.f1
helpviewer_keywords:
- Attribute Data Translation dialog box
ms.assetid: bed286de-1e9b-49de-b09e-3cd076aba152
author: minewiskan
ms.author: owend
ms.openlocfilehash: b61022ec2cb8726fc034e13a0d63e432df6ec151
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648170"
---
# <a name="attribute-data-translation-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="d11c9-102">특성 데이터 번역 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="d11c9-102">Attribute Data Translation Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="d11c9-103">**특성 데이터 번역** 대화 상자를 사용하여 번역 캡션 데이터가 포함된 열을 설정하고 번역된 데이터에 사용할 데이터 정렬 및 정렬 순서를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-103">Use the **Attribute Data Translation** dialog box to set the column that contains the translation caption data, as well as the collation and sort order to be used with the translated data.</span></span> <span data-ttu-id="d11c9-104">다음을 수행하여 **특성 데이터 번역** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-104">You can display the **Attribute Data Translation** dialog box by:</span></span>  
  
-   <span data-ttu-id="d11c9-105">**차원 디자이너** 의 **번역** 탭에 있는 **도구 모음** 창에서 **새 캡션 열** 또는 **캡션 열 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-105">Clicking **New caption column** or **Edit caption column** from the **Toolbar** pane on the **Translations** tab of **Dimension Designer**.</span></span>  
  
-   <span data-ttu-id="d11c9-106">**차원 디자이너** 의 **번역** 탭에서 **번역 세부 정보** 창을 마우스 오른쪽 단추로 클릭한 다음 **새 캡션 열** 또는 **캡션 열 편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-106">Right-clicking the **Translation Details** pane on the **Translations** tab of **Dimension Designer** and selecting **New caption column** or **Edit caption column**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d11c9-107">옵션</span><span class="sxs-lookup"><span data-stu-id="d11c9-107">Options</span></span>  
 <span data-ttu-id="d11c9-108">**특성**</span><span class="sxs-lookup"><span data-stu-id="d11c9-108">**Attribute**</span></span>  
 <span data-ttu-id="d11c9-109">선택한 특성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-109">Displays the selected attribute.</span></span>  
  
 <span data-ttu-id="d11c9-110">**언어**</span><span class="sxs-lookup"><span data-stu-id="d11c9-110">**Language**</span></span>  
 <span data-ttu-id="d11c9-111">선택한 언어를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-111">Displays the selected language.</span></span>  
  
 <span data-ttu-id="d11c9-112">**번역된 캡션**</span><span class="sxs-lookup"><span data-stu-id="d11c9-112">**Translated caption**</span></span>  
 <span data-ttu-id="d11c9-113">선택한 특성에 대해 현재 번역된 캡션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-113">Sets the current translated caption for the selected attribute.</span></span>  
  
 <span data-ttu-id="d11c9-114">**번역 열**</span><span class="sxs-lookup"><span data-stu-id="d11c9-114">**Translation columns**</span></span>  
 <span data-ttu-id="d11c9-115">번역 열 데이터가 저장되는 열을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-115">Sets the column where the translation caption data is stored.</span></span> <span data-ttu-id="d11c9-116">열은 하나만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-116">Only one column can be selected.</span></span> <span data-ttu-id="d11c9-117">주 차원 테이블에서 참조하는 모든 관련 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-117">All related tables that are referred to by the primary dimension table will be displayed.</span></span>  
  
 <span data-ttu-id="d11c9-118">**데이터 정렬 지정자**</span><span class="sxs-lookup"><span data-stu-id="d11c9-118">**Collation designator**</span></span>  
 <span data-ttu-id="d11c9-119">선택한 특성에 대해 데이터 정렬 지정자를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-119">Sets the collation designator for the selected attribute.</span></span> <span data-ttu-id="d11c9-120">기본적으로 현재 Windows 데이터 정렬이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-120">By default, the current Windows collation is selected.</span></span> <span data-ttu-id="d11c9-121">아래쪽 화살표를 클릭하여 사용 가능한 데이터 정렬에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-121">Click the down arrow to select from the available collations.</span></span>  
  
 <span data-ttu-id="d11c9-122">**이진**</span><span class="sxs-lookup"><span data-stu-id="d11c9-122">**Binary**</span></span>  
 <span data-ttu-id="d11c9-123">각 문자에 대해 정의된 비트 패턴을 기준으로 데이터를 정렬 및 비교하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-123">Select this option to sort and compare data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="d11c9-124">이진 정렬 순서는 대/소문자(소문자가 대문자 앞에 와야 함) 및 악센트를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-124">Binary sort order is case-sensitive, that is, lowercase precedes uppercase, and accent-sensitive.</span></span> <span data-ttu-id="d11c9-125">이것은 가장 빠른 정렬 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-125">This is the fastest sorting order.</span></span>  
  
 <span data-ttu-id="d11c9-126">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 관련된 언어 또는 알파벳에 대해 사전에 정의된 정렬 및 비교 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-126">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] follows sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d11c9-127">이 옵션을 선택하면 **대/소문자 구분**, **악센트 구분**, **일본어 가나 구분**및 **전자/반자 구분** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-127">If this option is selected, the **Case sensitive**, **Accent sensitive**, **Kana sensitive**, and **Width sensitive** options are disabled.</span></span>  
  
 <span data-ttu-id="d11c9-128">**대/소문자 구분**</span><span class="sxs-lookup"><span data-stu-id="d11c9-128">**Case sensitive**</span></span>  
 <span data-ttu-id="d11c9-129">관련된 언어 또는 알파벳에 대해 제공된 사전 규칙을 기준으로 데이터를 정렬 및 비교하고 대문자와 소문자를 구분하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-129">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between uppercase and lowercase letters.</span></span>  
  
 <span data-ttu-id="d11c9-130">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 대문자와 소문자가 동일한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-130">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the uppercase and lowercase versions of letters to be equal.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="d11c9-131">는 **대/소문자 구분** 을 선택 하지 않은 경우 대문자와 관련 하 여 소문자 정렬 순서를 정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-131">does not define whether lowercase letters sort lower or higher in relation to uppercase letters when **Case-sensitive** is not selected.</span></span>  
  
 <span data-ttu-id="d11c9-132">**악센트 구분**</span><span class="sxs-lookup"><span data-stu-id="d11c9-132">**Accent sensitive**</span></span>  
 <span data-ttu-id="d11c9-133">관련된 언어 또는 알파벳에 대해 제공된 사전 규칙을 기준으로 데이터를 정렬 및 비교하고 악센트가 있는 문자와 악센트가 없는 문자를 구분하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-133">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between accented and unaccented characters.</span></span> <span data-ttu-id="d11c9-134">예를 들어 'a'와 'á'는 같지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-134">For example, 'a' is not equal to 'á'.</span></span>  
  
 <span data-ttu-id="d11c9-135">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 악센트가 있는 문자와 없는 문자를 동일한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-135">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the accented and unaccented versions of letters to be equal.</span></span>  
  
 <span data-ttu-id="d11c9-136">**일본어 가나 구분**</span><span class="sxs-lookup"><span data-stu-id="d11c9-136">**Kana sensitive**</span></span>  
 <span data-ttu-id="d11c9-137">관련된 언어 또는 알파벳에 대해 제공된 사전 규칙을 기준으로 데이터를 정렬 및 비교하고 히라가나와 가타카나라는 두 가지 유형의 일본어 가나 문자를 구분하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-137">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between the two types of Japanese kana characters: Hiragana and Katakana.</span></span>  
  
 <span data-ttu-id="d11c9-138">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 히라가나와 가타카나 문자를 동일한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-138">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers Hiragana and Katakana characters to be equal.</span></span>  
  
 <span data-ttu-id="d11c9-139">**전자/반자 구분**</span><span class="sxs-lookup"><span data-stu-id="d11c9-139">**Width sensitive**</span></span>  
 <span data-ttu-id="d11c9-140">관련된 언어 또는 알파벳에 대해 제공된 사전 규칙을 기준으로 데이터를 정렬 및 비교하고 단일 바이트 문자(반자)와 더블바이트 문자로 표시될 때의 동일한 문자(전자)를 구분하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-140">Select this option to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between a single-byte character (half-width) and the same character when represented as a double-byte character (full-width).</span></span>  
  
 <span data-ttu-id="d11c9-141">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 같은 문자의 싱글바이트 표시와 더블바이트 표시를 동일한 문자로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="d11c9-141">If not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the single-byte and double-byte representation of the same character to be equal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d11c9-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d11c9-142">See Also</span></span>  
 <span data-ttu-id="d11c9-143">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d11c9-143">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="d11c9-144">번역 세부 정보 &#40;번역 탭, 차원 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="d11c9-144">Translation Details &#40;Translations Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](translation-details-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
