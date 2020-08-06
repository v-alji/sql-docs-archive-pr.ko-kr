---
title: MDX 작성기 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.mdxbuilderdialof.f1
helpviewer_keywords:
- MDX Builder dialog box
ms.assetid: fecbf093-65ea-4e1b-b637-f04876f1cb0f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 391f4abe953184470be60cca41d53ee20e965423
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651939"
---
# <a name="mdx-builder-analysis-services---multidimensional-data"></a><span data-ttu-id="71bcc-102">MDX 작성기( Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="71bcc-102">MDX Builder (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="71bcc-103">**또는** 의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] MDX 작성기 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 MDX(Multidimensional Expression) 식을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71bcc-103">Use the **MDX Builder** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to build a Multidimensional Expressions (MDX) expression.</span></span> <span data-ttu-id="71bcc-104">**역할 디자이너**의 **셀 데이터** 페이지에서 **큐브 내용을 읽을 수** 있습니다 옵션, **셀 보안 설정에 따라 셀 내용을** 읽을**수 있습니다 옵션**또는 **큐브 내용을 읽고 쓸** 수 있음 옵션을 클릭 하 여 **mdx 작성기** 대화 **상자를 표시할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71bcc-104">You can display the **MDX Builder** dialog box by clicking the **Edit MDX** ellipsis button (**...**) for the **Allow reading of cube content** option, the **Allow reading of cell content contingent on cell security** option, or the **Allow reading and writing of cube content** option on the **Cell Data** page of **Role Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="71bcc-105">옵션</span><span class="sxs-lookup"><span data-stu-id="71bcc-105">Options</span></span>  
  
|<span data-ttu-id="71bcc-106">용어</span><span class="sxs-lookup"><span data-stu-id="71bcc-106">Term</span></span>|<span data-ttu-id="71bcc-107">정의</span><span class="sxs-lookup"><span data-stu-id="71bcc-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="71bcc-108">**식**</span><span class="sxs-lookup"><span data-stu-id="71bcc-108">**Expression**</span></span>|<span data-ttu-id="71bcc-109">사용할 MDX 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="71bcc-109">Type the MDX expression to be used.</span></span>|  
|<span data-ttu-id="71bcc-110">**확인**</span><span class="sxs-lookup"><span data-stu-id="71bcc-110">**Check**</span></span>|<span data-ttu-id="71bcc-111">**식** 에서 정의한 MDX 식을 테스트하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71bcc-111">Click **Check** to test the MDX expression defined in **Expression**.</span></span>|  
|<span data-ttu-id="71bcc-112">**메타데이터**</span><span class="sxs-lookup"><span data-stu-id="71bcc-112">**Metadata**</span></span>|<span data-ttu-id="71bcc-113">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 식 **에서 정의한 MDX 식에 포함시킬 수 있는 현재**개체에 대한 메타데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71bcc-113">Displays metadata for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object that can be included in the MDX expression defined in **Expression**.</span></span><br /><br /> <span data-ttu-id="71bcc-114">선택한 항목을 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **복사** 를 선택하거나 선택한 항목을 **식**으로 끌어서 해당 항목에 대한 MDX 구문을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71bcc-114">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy** from the context menu, or by dragging the selected item to **Expression**.</span></span>|  
|<span data-ttu-id="71bcc-115">**함수**</span><span class="sxs-lookup"><span data-stu-id="71bcc-115">**Functions**</span></span>|<span data-ttu-id="71bcc-116">현재 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 사용 가능한 MDX 함수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71bcc-116">Displays available MDX functions for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="71bcc-117">나열된 항목은 MDSCHEMA_FUNCTIONS 스키마 행 집합에서 검색된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="71bcc-117">The items listed are retrieved from the MDSCHEMA_FUNCTIONS schema rowset.</span></span><br /><br /> <span data-ttu-id="71bcc-118">선택한 항목을 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **복사** 를 선택하거나 선택한 항목을 **식**으로 끌어서 해당 항목에 대한 MDX 구문을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71bcc-118">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy** from the context menu, or by dragging the selected item to **Expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71bcc-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71bcc-119">See Also</span></span>  
 <span data-ttu-id="71bcc-120">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="71bcc-120">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="71bcc-121">[셀 데이터 &#40;역할 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](https://msdn.microsoft.com/library/ms177279(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="71bcc-121">[Cell Data &#40;Role Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](https://msdn.microsoft.com/library/ms177279(v=sql.120).aspx)</span></span>  
  
  
