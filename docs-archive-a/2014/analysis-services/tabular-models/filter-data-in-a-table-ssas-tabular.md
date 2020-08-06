---
title: 테이블의 데이터 필터링 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f4003457df4068713e75e6bb5c0ab78c15ac03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728839"
---
# <a name="filter-data-in-a-table-ssas-tabular"></a><span data-ttu-id="7ba61-102">테이블의 데이터 필터링(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="7ba61-102">Filter Data in a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="7ba61-103">데이터를 가져올 때 필터를 적용하여 테이블에 로드되는 행을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-103">You can apply filters when you import data to control the rows that are loaded into a table.</span></span> <span data-ttu-id="7ba61-104">데이터를 가져온 후에는 개별 행을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-104">After you have imported the data, you cannot delete individual rows.</span></span> <span data-ttu-id="7ba61-105">그러나 사용자 지정 필터를 적용하여 행이 표시되는 방식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-105">However, you can apply custom filters to control the way that rows are displayed.</span></span> <span data-ttu-id="7ba61-106">필터링 조건을 충족하지 않는 행은 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-106">Rows that do not meet the filtering criteria are hidden.</span></span> <span data-ttu-id="7ba61-107">하나 이상의 열을 기준으로 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-107">You can filter by one or more columns.</span></span> <span data-ttu-id="7ba61-108">필터는 가산적이므로 현재 필터를 기준으로 필터를 추가할 때마다 데이터의 하위 집합이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-108">Filters are additive, which means that each additional filter is based on the current filter and further reduces the subset of data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ba61-109">필터 미리 보기 창에서는 표시되는 서로 다른 값의 수가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-109">The filter preview window limits the number of different values displayed.</span></span> <span data-ttu-id="7ba61-110">제한을 초과하는 경우 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-110">If the limit is exceeded, a message is displayed.</span></span>  
  
### <a name="to-filter-data-based-on-column-values"></a><span data-ttu-id="7ba61-111">열 값을 기준으로 데이터를 필터링하려면</span><span class="sxs-lookup"><span data-stu-id="7ba61-111">To filter data based on column values</span></span>  
  
1.  <span data-ttu-id="7ba61-112">모델 디자이너에서 테이블을 선택한 다음 필터링 기준으로 사용할 열의 머리글에 있는 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-112">In the model designer, select a table, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="7ba61-113">자동 필터 메뉴에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-113">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="7ba61-114">열 값 목록에서 필터링 기준으로 하나 이상의 값을 선택 하거나 선택을 취소 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-114">In the list of column values, select or clear one or more values to filter by, and then click **OK**.</span></span>  
  
         <span data-ttu-id="7ba61-115">값의 수가 너무 많은 경우 개별 항목이 목록에 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-115">If the number of values is extremely large, individual items might not be shown in the list.</span></span> <span data-ttu-id="7ba61-116">대신 "표시할 항목이 너무 많음"이라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-116">Instead, you will see the message, "Too many items to show."</span></span>  
  
    -   <span data-ttu-id="7ba61-117">열 형식에 따라 **숫자 필터** 또는 **텍스트 필터** 를 클릭 한 다음 비교 연산자 명령 (예: **Equals**) 중 하나을 클릭 하거나 **사용자 지정 필터**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-117">Click **Number Filters** or **Text Filters** (depending on the type of column), and then clicke of the comparison operator commands (such as **Equals**), or click **Custom Filter**.</span></span> <span data-ttu-id="7ba61-118">**사용자 지정 필터** 대화 상자에서 필터를 만든 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-118">In the **Custom Filter** dialog box, create the filter, and then click **OK**.</span></span>  
  
### <a name="to-clear-a-filter-for-a-column"></a><span data-ttu-id="7ba61-119">열에 대한 필터를 지우려면</span><span class="sxs-lookup"><span data-stu-id="7ba61-119">To clear a filter for a column</span></span>  
  
1.  <span data-ttu-id="7ba61-120">필터를 지우려는 열의 머리글에 있는 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-120">Click the arrow in the header of the column for which you want to clear a filter.</span></span>  
  
2.  <span data-ttu-id="7ba61-121">\*\*필터 지우기를 \<Column Name> \*\*클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-121">Click **Clear Filter from \<Column Name>**.</span></span>  
  
### <a name="to-clear-all-filters-for-a-table"></a><span data-ttu-id="7ba61-122">테이블에 대한 필터를 모두 지우려면</span><span class="sxs-lookup"><span data-stu-id="7ba61-122">To clear all filters for a table</span></span>  
  
1.  <span data-ttu-id="7ba61-123">모델 디자이너에서 필터를 지우려는 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-123">In the model designer, select the table for which you want to clear filters.</span></span>  
  
2.  <span data-ttu-id="7ba61-124">**열** 메뉴에서 **필터 모두 지우기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba61-124">Click on the **Column** menu, and then click **Clear All Filters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba61-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ba61-125">See Also</span></span>  
 <span data-ttu-id="7ba61-126">[SSAS 테이블 형식&#41;&#40;데이터 필터링 및 정렬](../filter-and-sort-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="7ba61-126">[Filter and Sort Data &#40;SSAS Tabular&#41;](../filter-and-sort-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="7ba61-127">[SSAS 테이블 형식&#41;&#40;큐브 뷰](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="7ba61-127">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="7ba61-128">역할&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="7ba61-128">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
