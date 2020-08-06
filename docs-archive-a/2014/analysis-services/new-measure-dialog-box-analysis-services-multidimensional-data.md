---
title: 새 측정값 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.newmeasuredialog.f1
helpviewer_keywords:
- New Measure dialog box
ms.assetid: 86dc9146-cc6d-4cef-b178-9a6b4cf616e8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1fb60bd598257d2de1f60900aafa43b085000fd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743532"
---
# <a name="new-measure-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="786ee-102">새 측정값 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="786ee-102">New Measure Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="786ee-103">**의** 새 측정값 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 큐브 디자이너에서 새 측정값을 측정값 그룹에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="786ee-103">Use the **New Measure** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to add a new measure to a measure group in Cube Designer.</span></span> <span data-ttu-id="786ee-104">다음을 수행하여 **새 측정값** 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="786ee-104">You can display the **New Measure** dialog box by:</span></span>  
  
-   <span data-ttu-id="786ee-105">큐브 디자이너의 **큐브 구조** 탭에 있는 **도구 모음** 창에서 **새 측정값** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="786ee-105">Clicking **New Measure** in the **Toolbar** pane on the **Cube Structure** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="786ee-106">큐브 디자이너의 **큐브 구조** 탭에 있는 **측정값** 창에서 측정값 그룹 또는 측정값을 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **새 측정값** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="786ee-106">Right-clicking a measure group or measure in the **Measures** pane on the **Cube Structure** tab in Cube Designer and selecting **New Measure** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="786ee-107">옵션</span><span class="sxs-lookup"><span data-stu-id="786ee-107">Options</span></span>  
 <span data-ttu-id="786ee-108">**사용 현황**</span><span class="sxs-lookup"><span data-stu-id="786ee-108">**Usage**</span></span>  
 <span data-ttu-id="786ee-109">새 측정값에서 사용할 집계 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="786ee-109">Select the aggregation function to be used by the new measure.</span></span>  
  
 <span data-ttu-id="786ee-110">**원본 테이블**</span><span class="sxs-lookup"><span data-stu-id="786ee-110">**Source table**</span></span>  
 <span data-ttu-id="786ee-111">새 측정값을 만들 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="786ee-111">Select the table from which the new measure is to be created.</span></span>  
  
 <span data-ttu-id="786ee-112">**원본 열**</span><span class="sxs-lookup"><span data-stu-id="786ee-112">**Source column**</span></span>  
 <span data-ttu-id="786ee-113">새 측정값이 기반으로 하는 **원본 테이블** 에서 선택한 테이블의 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="786ee-113">Select the column in the table selected in **Source table** on which the new measure is to be based.</span></span>  
  
 <span data-ttu-id="786ee-114">**모든 열 표시**</span><span class="sxs-lookup"><span data-stu-id="786ee-114">**Show all columns**</span></span>  
 <span data-ttu-id="786ee-115">새 측정값을 만들 측정값 그룹에 대한 팩트 테이블의 열을 모두 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="786ee-115">Select to display all columns in the fact table for the measure group in which the new measure is to be created.</span></span> <span data-ttu-id="786ee-116">이 옵션을 선택하지 않으면 **원본 열** 은 논리적 기본 키로 사용되지 않거나 관계에 관련되지 않은 숫자 열만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="786ee-116">If not selected, **Source column** only displays numeric columns that are not used as logical primary keys or involved in relationships.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="786ee-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="786ee-117">See Also</span></span>  
 <span data-ttu-id="786ee-118">[큐브 구조 &#40;큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="786ee-118">[Cube Structure &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="786ee-119">Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="786ee-119">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
