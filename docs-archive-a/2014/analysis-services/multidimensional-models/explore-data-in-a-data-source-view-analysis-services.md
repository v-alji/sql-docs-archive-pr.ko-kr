---
title: 데이터 원본 뷰에서 데이터 탐색 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adf9edecd807158ba1d0de3287cccd6fa8dd787
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661374"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a><span data-ttu-id="11c15-102">데이터 원본 뷰에서 데이터 탐색(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="11c15-102">Explore Data in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="11c15-103">**의 데이터 원본 뷰 디자이너에 있는** 데이터 탐색 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 대화 상자를 사용하여 DSV(데이터 원본 뷰)에서 테이블, 뷰 또는 명명된 쿼리의 데이터를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-103">You can use the **Explore Data** dialog box in Data Source View Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to browse data for a table, view, or named query in a data source view (DSV).</span></span> <span data-ttu-id="11c15-104">데이터 원본 뷰 디자이너에서 데이터를 탐색하면 선택한 테이블, 뷰 또는 명명된 쿼리에 있는 각 데이터 열의 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-104">When you explore the data in Data Source View Designer, you can view the contents of each column of data in a selected table, view, or named query.</span></span> <span data-ttu-id="11c15-105">실제 내용을 보면 모든 열이 필요한지 여부, 사용자에게 친숙함과 유용성을 높이기 위해 명명된 계산이 필요한지 여부 및 기존의 명명된 계산이나 명명된 쿼리에서 예상된 값을 반환하는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-105">Viewing the actual contents assists you in determining whether all columns are needed, if named calculations are required to increase user friendliness and usability, and whether existing named calculations or named queries return the anticipated values.</span></span>  
  
 <span data-ttu-id="11c15-106">데이터를 보려면 DSV에서 선택한 개체의 데이터 원본에 대한 활성 연결이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-106">To view data, you must have an active connection to the data source or sources for the selected object in the DSV.</span></span> <span data-ttu-id="11c15-107">테이블에 있는 모든 명명된 계산도 쿼리에서 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-107">Any named calculations in a table are also sent in the query.</span></span>  
  
 <span data-ttu-id="11c15-108">데이터는 정렬하고 복사할 수 있는 테이블 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-108">The data returned in a tabular format that you can sort and copy.</span></span> <span data-ttu-id="11c15-109">해당 열을 기준으로 행을 재정렬하려면 열 머리글을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-109">Click on the column headers to re-sort the rows by that column.</span></span> <span data-ttu-id="11c15-110">또한 표에서 데이터를 강조 표시하고 Ctrl+C를 눌러 선택 내용을 클립 보드로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-110">You can also highlight data in the grid and press Ctrl-C to copy the selection to the clipboard.</span></span>  
  
 <span data-ttu-id="11c15-111">샘플 방법과 샘플 개수를 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-111">You can also control the sample method and the sample count.</span></span> <span data-ttu-id="11c15-112">기본적으로 상위 5000갱의 행이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-112">By default, the top 5000 rows are returned.</span></span>  
  
## <a name="to-browse-data-or-change-sampling-options"></a><span data-ttu-id="11c15-113">데이터를 검색하거나 샘플링 옵션을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="11c15-113">To browse data or change sampling options</span></span>  
  
1.  <span data-ttu-id="11c15-114">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 프로젝트를 열거나 데이터를 찾아볼 데이터 원본 뷰를 포함하는 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-114">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to browse data.</span></span>  
  
2.  <span data-ttu-id="11c15-115">솔루션 탐색기에서 **데이터 원본 뷰** 폴더를 확장한 다음 해당 데이터 원본 뷰를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-115">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="11c15-116">확인할 데이터가 포함된 테이블, 뷰 또는 명명된 쿼리를 마우스 오른쪽 단추로 클릭한 다음 **데이터 탐색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-116">Right-click the table, view, or named query that contains the data you want to view, and then click **Explore Data**.</span></span>  
  
     <span data-ttu-id="11c15-117">데이터 원본 뷰의 테이블, 뷰 또는 명명 된 쿼리를 기반으로 하는 데이터 원본은 쿼리이 고 결과는 \*\* \<object name> 테이블 탐색\*\* 탭에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-117">The data source underlying the table, view, or named query in the data source view are queries, and the results appear in the **Explore \<object name> Table** tab.</span></span>  
  
4.  <span data-ttu-id="11c15-118">\*\* \<object name> 테이블 탐색\*\* 도구 모음에서 **샘플링 옵션** 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-118">On the **Explore \<object name> Table** toolbar, click the **Sampling options** icon.</span></span>  
  
     <span data-ttu-id="11c15-119">**데이터 탐색 옵션** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-119">The **Data Exploration Options** dialog box opens.</span></span> <span data-ttu-id="11c15-120">이 대화 상자에서 샘플링 방법(기본 샘플링 크기인 5000행보다 많거나 적은 레코드) 또는 샘플 개수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-120">In this dialog box you can specify the sampling method (fewer or more records than the default sampling size of 5000 rows), or sample count.</span></span>  
  
5.  <span data-ttu-id="11c15-121">필요에 따라 **확인** 또는 **취소** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-121">Click **OK** or **Cancel** as appropriate.</span></span>  
  
6.  <span data-ttu-id="11c15-122">데이터를 다시 샘플링 하려면 \*\* \<object name> 테이블 탐색\*\* 도구 모음에서 **데이터 다시 샘플링** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="11c15-122">To resample the data, click **Resample Data** on the **Explore \<object name> Table** toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c15-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="11c15-123">See Also</span></span>  
 [<span data-ttu-id="11c15-124">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="11c15-124">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
