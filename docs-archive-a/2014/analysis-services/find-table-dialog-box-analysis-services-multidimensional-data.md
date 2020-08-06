---
title: 테이블 찾기 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.findtabledialog.f1
helpviewer_keywords:
- Find Table dialog box
ms.assetid: 133d28e8-55eb-4783-bb8b-d3776a95ebda
author: minewiskan
ms.author: owend
ms.openlocfilehash: ee22c912a3121841a7827e31d53f7b8baba72174
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647981"
---
# <a name="find-table-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="86d66-102">테이블 찾기 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="86d66-102">Find Table Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="86d66-103">**의** 테이블 찾기 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 차원, 큐브 또는 마이닝 구조와 연결된 데이터 원본 뷰에서 테이블을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d66-103">Use the **Find Table** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to locate a table in the data source view associated with a dimension, cube, or mining structure.</span></span> <span data-ttu-id="86d66-104">다음과 같은 방법으로 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 에서 이 대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d66-104">You can display this dialog box in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] by:</span></span>  
  
-   <span data-ttu-id="86d66-105">**차원 디자이너\*\*\*\*차원 구조** 페이지의 **도구 모음** 창에서 **테이블 찾기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="86d66-105">Clicking **Find Table** from the **Toolbar** pane on the **Dimension Structure** page of the **Dimension Designer**.</span></span>  
  
-   <span data-ttu-id="86d66-106">**차원 디자이너** 의 **차원 구조** 페이지에서 **데이터 원본 뷰** 창의 배경을 마우스 오른쪽 단추로 클릭하고 **테이블 찾기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86d66-106">Right-clicking the background of the **Data Source View** pane on the **Dimension Structure** page of the **Dimension Designer** and selecting **Find Table**.</span></span>  
  
-   <span data-ttu-id="86d66-107">**큐브 디자이너\*\*\*\*큐브 구조** 페이지의 **도구 모음** 창에서 **테이블 찾기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="86d66-107">Clicking **Find Table** from the **Toolbar** pane on the **Cube Structure** page of the **Cube Designer**.</span></span>  
  
-   <span data-ttu-id="86d66-108">**큐브 디자이너** 의 **큐브 구조** 페이지에서 **데이터 원본 뷰** 창의 배경을 마우스 오른쪽 단추로 클릭하고 **테이블 찾기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86d66-108">Right-clicking the background of the **Data Source View** pane on the **Cube Structure** page of the **Cube Designer** and selecting **Find Table**.</span></span>  
  
-   <span data-ttu-id="86d66-109">**데이터 마이닝 모델 디자이너** 의 **마이닝 구조** 페이지에서 **데이터 원본 뷰** 창의 배경을 마우스 오른쪽 단추로 클릭하고 **테이블 찾기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86d66-109">Right-clicking the background of the **Data Source View** pane on the **Mining Structure** page of the **Data Mining Model Designer** and selecting **Find Table**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="86d66-110">옵션</span><span class="sxs-lookup"><span data-stu-id="86d66-110">Options</span></span>  
 <span data-ttu-id="86d66-111">**데이터 원본 뷰에서 테이블 선택**</span><span class="sxs-lookup"><span data-stu-id="86d66-111">**Select a table from data source view**</span></span>  
 <span data-ttu-id="86d66-112">**데이터 원본 뷰** 창에서 찾을 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86d66-112">Select the table to find in the **Data Source View** pane.</span></span> <span data-ttu-id="86d66-113">이 옵션은 **필터** 에서 설정한 필터( **필터** 를 설정하지 않은 경우 모든 테이블)와 일치하지만 아직 현재 다이어그램에 표시되지 않은 사용 가능한 개체 및 개체 유형의 표를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="86d66-113">This option displays a grid of available objects and their types that match the filter set in **Filter** (or all tables if **Filter** is not set) and have not yet been shown in the current diagram.</span></span>  
  
 <span data-ttu-id="86d66-114">**Filter**</span><span class="sxs-lookup"><span data-stu-id="86d66-114">**Filter**</span></span>  
 <span data-ttu-id="86d66-115">나열되는 개체를 제한하는 데 사용할 필터를 입력하고 이 단추를 클릭하여 **데이터 원본 뷰에서 테이블 선택**에 나열되는 테이블을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d66-115">Type the filter used to restrict the objects listed, and then click the button to filter the tables listed in **Select a table from data source view**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d66-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86d66-116">See Also</span></span>  
 <span data-ttu-id="86d66-117">[어셈블리 속성 대화 상자 &#40;Analysis Services 다차원 데이터&#41;](assembly-properties-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="86d66-117">[Assembly Properties Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](assembly-properties-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="86d66-118">[데이터 원본 뷰 &#40;차원 구조 탭, 차원 디자이너&#41; &#40;Analysis Services-다차원 데이터&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="86d66-118">[Data Source View &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="86d66-119">데이터 원본 뷰 &#40;큐브 구조 탭, 큐브 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="86d66-119">Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-cube-designer-analysis-services-multidimensional-data.md)  
  
  
