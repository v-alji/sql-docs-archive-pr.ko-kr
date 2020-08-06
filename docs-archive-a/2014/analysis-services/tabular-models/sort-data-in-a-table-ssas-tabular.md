---
title: 테이블의 데이터 정렬 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
author: minewiskan
ms.author: owend
ms.openlocfilehash: d9a6636c2c11fc571e8d4c1bcbc25c1e02d815fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727359"
---
# <a name="sort-data-in-a-table-ssas-tabular"></a><span data-ttu-id="0ce0c-102">테이블의 데이터 정렬(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="0ce0c-102">Sort Data in a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="0ce0c-103">하나 이상의 열에 있는 데이터를 텍스트 및 숫자별로 오름차순 또는 내림차순으로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-103">You can sort data by text (A to Z or Z to A) and numbers (smallest to largest or largest to smallest) in one or more columns.</span></span>  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a><span data-ttu-id="0ce0c-104">텍스트 열을 기준으로 테이블의 데이터를 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="0ce0c-104">To sort the data in a table based on a text column</span></span>  
  
1.  <span data-ttu-id="0ce0c-105">모델 디자이너에서 영숫자 데이터 열의 셀 범위를 선택하거나 활성 셀이 영숫자 데이터를 포함하는 테이블 열에 있는지 확인합니다. 그런 다음 필터링하려는 열의 머리글에 있는 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-105">In the model designer, select a column of alphanumeric data, a range of cells in a column, or make sure that the active cell is in a table column that contains alphanumeric data, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="0ce0c-106">자동 필터 메뉴에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-106">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="0ce0c-107">오름차순 영숫자 순서로 정렬하려면 **텍스트 오름차순 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-107">To sort in ascending alphanumeric order, click **Sort A to Z**.</span></span>  
  
    -   <span data-ttu-id="0ce0c-108">내림차순 영숫자 순서로 정렬하려면 **텍스트 내림차순 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-108">To sort in descending alphanumeric order, click **Sort Z to A**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0ce0c-109">다른 애플리케이션에서 가져온 데이터의 경우 데이터 앞에 선행 공백이 삽입되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-109">In some cases, data imported from another application might have leading spaces inserted before data.</span></span> <span data-ttu-id="0ce0c-110">데이터를 제대로 정렬하려면 선행 공백을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-110">You must remove the leading spaces in order to correctly sort the data.</span></span>  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a><span data-ttu-id="0ce0c-111">숫자 열을 기준으로 테이블의 데이터를 정렬하려면</span><span class="sxs-lookup"><span data-stu-id="0ce0c-111">To sort the data in a table based on a numeric column</span></span>  
  
1.  <span data-ttu-id="0ce0c-112">모델 디자이너에서 영숫자 데이터 열의 셀 범위를 선택하거나 활성 셀이 영숫자 데이터를 포함하는 테이블 열에 있는지 확인합니다. 그런 다음 필터링하려는 열의 머리글에 있는 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-112">In the model designer, select a column of alphanumeric data, a range of cells in a column, or make sure that the active cell is in a table column that contains alphanumeric data, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="0ce0c-113">자동 필터 메뉴에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-113">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="0ce0c-114">가장 작은 숫자에서 가장 큰 숫자 순서로 정렬하려면 **숫자 오름차순 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-114">To sort from low numbers to high numbers, click **Sort Smallest to Largest**.</span></span>  
  
    -   <span data-ttu-id="0ce0c-115">가장 큰 숫자에서 가장 작은 숫자 순서로 정렬하려면 **숫자 내림차순 정렬**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-115">To sort from high numbers to low numbers, click **Sort Largest to Smallest**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0ce0c-116">결과가 예상과 다른 경우 열에 숫자가 아니라 텍스트로 저장된 숫자가 포함되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-116">If the results are not what you expected, the column might contain numbers stored as text and not as numbers.</span></span> <span data-ttu-id="0ce0c-117">예를 들어 일부 재무 회계 시스템에서 가져온 음수 또는 '(아포스트로피)와 함께 입력한 숫자는 텍스트로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce0c-117">For example, negative numbers imported from some accounting systems, or a number entered with a leading ' (apostrophe), are stored as text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce0c-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0ce0c-118">See Also</span></span>  
 <span data-ttu-id="0ce0c-119">[SSAS 테이블 형식&#41;&#40;데이터 필터링 및 정렬](../filter-and-sort-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="0ce0c-119">[Filter and Sort Data &#40;SSAS Tabular&#41;](../filter-and-sort-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="0ce0c-120">[SSAS 테이블 형식&#41;&#40;큐브 뷰](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="0ce0c-120">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="0ce0c-121">역할&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="0ce0c-121">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
