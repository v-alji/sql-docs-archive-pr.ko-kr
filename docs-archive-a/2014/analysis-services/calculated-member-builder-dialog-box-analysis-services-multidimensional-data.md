---
title: 계산 멤버 작성기 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.calculatedmemberbuilderdialog.f1
ms.assetid: 73b89a9f-f403-4ab8-99f7-e3ceb870c260
author: minewiskan
ms.author: owend
ms.openlocfilehash: 240e2f2471bf77c403119fd51278a975badc8358
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648090"
---
# <a name="calculated-member-builder-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="f0ebc-102">계산 멤버 작성기 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="f0ebc-102">Calculated Member Builder Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f0ebc-103">**의** 계산 멤버 작성기 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 계산 멤버를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-103">Use the **Calculated Member Builder** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to build a calculated member.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f0ebc-104">옵션</span><span class="sxs-lookup"><span data-stu-id="f0ebc-104">Options</span></span>  
  
|<span data-ttu-id="f0ebc-105">용어</span><span class="sxs-lookup"><span data-stu-id="f0ebc-105">Term</span></span>|<span data-ttu-id="f0ebc-106">정의</span><span class="sxs-lookup"><span data-stu-id="f0ebc-106">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="f0ebc-107">**이름**</span><span class="sxs-lookup"><span data-stu-id="f0ebc-107">**Name**</span></span>|<span data-ttu-id="f0ebc-108">계산 멤버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-108">Type the name of the calculated member.</span></span>|  
|<span data-ttu-id="f0ebc-109">**부모 계층**</span><span class="sxs-lookup"><span data-stu-id="f0ebc-109">**Parent Hierarchy**</span></span>|<span data-ttu-id="f0ebc-110">계산 멤버를 만들 계층을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-110">Select the hierarchy in which to create the calculated member.</span></span>|  
|<span data-ttu-id="f0ebc-111">**부모 멤버**</span><span class="sxs-lookup"><span data-stu-id="f0ebc-111">**Parent Member**</span></span>|<span data-ttu-id="f0ebc-112">수준이 두 개 이상인 부모 계층(`Measures` 차원 제외)을 선택한 경우 이 옵션이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-112">This option is enabled if you select a parent hierarchy (other than the `Measures` dimension) that has more than one level.</span></span> <span data-ttu-id="f0ebc-113">부모 멤버를 선택 하려면 줄임표 (**...**) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-113">Click the ellipsis (**...**) button to select a parent member.</span></span> <span data-ttu-id="f0ebc-114">부모 멤버는 차원 구조에서 계산 멤버의 위치를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-114">The parent member determines the location of the calculated member in the dimension structure.</span></span>|  
|<span data-ttu-id="f0ebc-115">**식**</span><span class="sxs-lookup"><span data-stu-id="f0ebc-115">**Expression**</span></span>|<span data-ttu-id="f0ebc-116">사용할 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-116">Type the MDX expression that will be used.</span></span>|  
|<span data-ttu-id="f0ebc-117">**확인**</span><span class="sxs-lookup"><span data-stu-id="f0ebc-117">**Check**</span></span>|<span data-ttu-id="f0ebc-118">**식** 에서 정의한 MDX 식을 테스트하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-118">Click **Check** to test the MDX expression defined in **Expression**.</span></span>|  
|<span data-ttu-id="f0ebc-119">**메타데이터**</span><span class="sxs-lookup"><span data-stu-id="f0ebc-119">**Metadata**</span></span>|<span data-ttu-id="f0ebc-120">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 식 **에서 정의한 MDX 식에 포함시킬 수 있는 현재**개체에 대한 메타데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-120">Displays metadata for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object that can be included in the MDX expression defined in **Expression**.</span></span><br /><br /> <span data-ttu-id="f0ebc-121">선택한 항목을 마우스 오른쪽 단추로 클릭하고 **복사**를 선택하거나 선택한 항목을 **식**으로 끌어서 해당 항목에 대한 MDX 구문을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-121">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy**, or by dragging the selected item to **Expression**.</span></span>|  
|<span data-ttu-id="f0ebc-122">**함수**</span><span class="sxs-lookup"><span data-stu-id="f0ebc-122">**Functions**</span></span>|<span data-ttu-id="f0ebc-123">현재 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 사용 가능한 MDX 함수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-123">Displays the available MDX functions for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="f0ebc-124">나열된 항목은 MDSCHEMA_FUNCTIONS 스키마 행 집합에서 검색된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-124">The items listed are retrieved from the MDSCHEMA_FUNCTIONS schema rowset.</span></span><br /><br /> <span data-ttu-id="f0ebc-125">선택한 항목을 마우스 오른쪽 단추로 클릭하고 **복사**를 선택하거나 선택한 항목을 **식**으로 끌어서 해당 항목에 대한 MDX 구문을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebc-125">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy**, or by dragging the selected item to **Expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0ebc-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0ebc-126">See Also</span></span>  
 [<span data-ttu-id="f0ebc-127">MDX&#40;Multidimensional Expression&#41; 참조</span><span class="sxs-lookup"><span data-stu-id="f0ebc-127">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
