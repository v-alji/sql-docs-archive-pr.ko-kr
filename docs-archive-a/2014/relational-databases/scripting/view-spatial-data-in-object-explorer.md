---
title: 개체 탐색기에서 공간 데이터 보기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 881adf69ee83ee4b7536afae0b190fbec90f132c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651618"
---
# <a name="view-spatial-data-in-object-explorer"></a><span data-ttu-id="68b2b-102">개체 탐색기에서 공간 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="68b2b-102">View Spatial Data in Object Explorer</span></span>
  <span data-ttu-id="68b2b-103">쿼리 편집기의 **공간 데이터 결과** 창은 공간 데이터 결과와 **결과** 창에 표 형식으로 표시되는 데이터를 볼 수 있는 시각적인 매핑 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-103">The **Spatial results** window in Query Editor provides visual mapping tools for viewing spatial data results in addition to the data displayed in grid format in the **Results** window.</span></span> <span data-ttu-id="68b2b-104">**공간 데이터 결과** 창에 공간 데이터를 표시하려면 쿼리 결과에서 기하 도형 또는 지리 데이터가 포함된 적어도 하나 이상의 공간 데이터 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-104">To display spatial data in the **Spatial Results** window, your query results must contain at least one spatial data column with either geometry or geography data.</span></span>  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a><span data-ttu-id="68b2b-105">공간 데이터 결과 창에서 공간 데이터를 보려면</span><span class="sxs-lookup"><span data-stu-id="68b2b-105">To view spatial data in the Spatial results window</span></span>  
  
1.  <span data-ttu-id="68b2b-106">쿼리 편집기에서 **공간 데이터 결과** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-106">In Query Editor, click the **Spatial results** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="68b2b-107">쿼리 결과에 공간 데이터가 포함되어 있지 않거나 결과가 텍스트로 반환되도록 지정한 경우에는 이 창을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-107">This window is not available if your query results do not contain spatial data or if you specify that your results are returned as text.</span></span>  
  
2.  <span data-ttu-id="68b2b-108">**공간 열 선택** 목록에서 보려는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-108">Select the column you want to view from the **Select spatial column** list.</span></span> <span data-ttu-id="68b2b-109">테이블에 공간 열이 하나만 있는 경우 이 열이 목록의 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-109">If there is only one spatial column in your table, this column is the default option in the list.</span></span>  
  
3.  <span data-ttu-id="68b2b-110">**레이블 열 선택** 목록에서 데이터 레이블로 사용할 공간이 아닌 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-110">Select the non-spatial column you want to use as data labels from the **Select label columns** list.</span></span>  
  
4.  <span data-ttu-id="68b2b-111">**투영 선택** 목록에서 지리 데이터에 사용할 투영 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-111">Select the projection you want for geography data from the **Select projection** list.</span></span> <span data-ttu-id="68b2b-112">기본 투영 모드는 Equirectangular이며 Mercator, Robinson 또는 Bonne도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-112">The default projection is Equirectangular; other projections available are Mercator, Robinson, or Bonne.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="68b2b-113">공간 열에 기하 도형 데이터가 포함되어 있지 않으면**투영 선택** 을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-113">**Select projection** is not available if your spatial column contains geometry data.</span></span>  
  
5.  <span data-ttu-id="68b2b-114">**확대/축소** 슬라이더를 조정하여 매핑된 요소의 시각적 크기를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-114">Adjust the **Zoom** slider to increase the visual size of mapped elements.</span></span> <span data-ttu-id="68b2b-115">다각형 모양의 경우 레이블 텍스트를 넣을 수 있을 만큼 큰 경우에만 레이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="68b2b-115">For polygon shapes, the label is visible only when the shape is large enough to hold the label text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68b2b-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68b2b-116">See Also</span></span>  
 <span data-ttu-id="68b2b-117">[공간 데이터 결과 창](spatial-results-window.md) </span><span class="sxs-lookup"><span data-stu-id="68b2b-117">[Spatial Results Window](spatial-results-window.md) </span></span>  
 <span data-ttu-id="68b2b-118">[데이터베이스 엔진 쿼리 편집기&#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="68b2b-118">[Database Engine Query Editor &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="68b2b-119">쿼리 및 텍스트 편집기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="68b2b-119">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](query-and-text-editors-sql-server-management-studio.md)  
  
  
