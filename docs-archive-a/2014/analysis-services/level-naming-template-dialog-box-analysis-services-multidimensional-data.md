---
title: 수준 명명 템플릿 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dd704e619e49f0dd1adb8fed8f1e743b61309af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743575"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="d4fb0-102">수준 명명 템플릿 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="d4fb0-102">Level Naming Template Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="d4fb0-103">**의** 수준 명명 템플릿 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 차원의 부모 특성에 대한 수준 명명 템플릿을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-103">Use the **Level Naming Template** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to construct the level naming template for a parent attribute in a dimension.</span></span> <span data-ttu-id="d4fb0-104">수준 명명 템플릿에 대한 자세한 내용은 [NamingTemplate 요소&#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-104">For more information about level naming templates, see [NamingTemplate Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl).</span></span> <span data-ttu-id="d4fb0-105">차원 디자이너의 번역 탭에 있는 **...** 번역 세부 정보 창에서 특성에 대 한 번역의 값에서 줄임표 단추 (...)를 클릭 하 여 **수준 명명 템플릿** 대화 상자를 표시할 수 있습니다 `NamingTemplate` . **Translation Details** **Translations** **Dimension Designer**</span><span class="sxs-lookup"><span data-stu-id="d4fb0-105">You can display the **Level Naming Template** dialog box by clicking the ellipsis button (**...**) on the `NamingTemplate` value of a translation for an attribute in the **Translation Details** pane on the **Translations** tab of **Dimension Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d4fb0-106">옵션</span><span class="sxs-lookup"><span data-stu-id="d4fb0-106">Options</span></span>  
  
|<span data-ttu-id="d4fb0-107">용어</span><span class="sxs-lookup"><span data-stu-id="d4fb0-107">Term</span></span>|<span data-ttu-id="d4fb0-108">정의</span><span class="sxs-lookup"><span data-stu-id="d4fb0-108">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="d4fb0-109">**수준 템플릿 정의**</span><span class="sxs-lookup"><span data-stu-id="d4fb0-109">**Define the level template**</span></span>|<span data-ttu-id="d4fb0-110">부모 특성의 수준 계층을 디자인할 수 있는 표를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-110">Displays a grid in which you can design the hierarchy of levels in the parent attribute.</span></span> <span data-ttu-id="d4fb0-111">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-111">The grid contains the following columns:</span></span><br /><br /> <span data-ttu-id="d4fb0-112">**수준**: **이름** 에 지정 된 이름이 사용 되는 수준의 서 수 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-112">**Level**: Displays the ordinal position of the level for which the name specified in **Name** is used.</span></span> <span data-ttu-id="d4fb0-113">수준에 대한 새 명명 템플릿을 추가하려면 **수준** 에 별표(\*)가 포함된 행에서 **이름**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-113">To add a new naming template for a level, select **Name** on the row that contains an asterisk (\*) in **Level**.</span></span><br /><br /> <span data-ttu-id="d4fb0-114">**이름**: **수준**에 지정 된 수준에 사용 되는 명명 템플릿을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-114">**Name**: Contains the naming template used for the level indicated in **Level**.</span></span> <span data-ttu-id="d4fb0-115">명명 템플릿의 수준 서수 위치에 대한 자리 표시자를 추가하려면 별표를 한 개(\*) 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-115">To add a placeholder for the level ordinal position in the naming template, add a single asterisk (\*).</span></span> <span data-ttu-id="d4fb0-116">명명 템플릿에서 만든 이름의 일부로 별표를 추가 하려면 별표 두 개 ()를 추가 \* \* 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-116">To add an asterisk as part of the name created by the naming template, add two asterisks (\*\*).</span></span>|  
|<span data-ttu-id="d4fb0-117">**모두 지우기**</span><span class="sxs-lookup"><span data-stu-id="d4fb0-117">**Clear All**</span></span>|<span data-ttu-id="d4fb0-118">**수준 템플릿 정의**에 있는 행을 모두 제거하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-118">Select to remove all rows in **Define the level template**.</span></span>|  
|<span data-ttu-id="d4fb0-119">**결과**</span><span class="sxs-lookup"><span data-stu-id="d4fb0-119">**Result**</span></span>|<span data-ttu-id="d4fb0-120">대화 상자를 사용하여 생성한 수준 명명 템플릿을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fb0-120">Displays the level naming template constructed by the dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4fb0-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4fb0-121">See Also</span></span>  
 <span data-ttu-id="d4fb0-122">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d4fb0-122">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="d4fb0-123">번역 &#40;차원 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="d4fb0-123">Translations &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
