---
title: 테이블, 열 또는 행 필터 매핑 변경 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2124c526-5772-4f84-a019-9dd3e906e8dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: d8a597fb51804ea12caace63f3308b07bffc5899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649702"
---
# <a name="change-table-column-or-row-filter-mappings-ssas-tabular"></a><span data-ttu-id="4c29d-102">테이블, 열 또는 행 필터 매핑 변경(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="4c29d-102">Change table, column, or row filter mappings (SSAS Tabular)</span></span>
  <span data-ttu-id="4c29d-103">이 항목에서는 **에서** 테이블 속성 편집 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]대화 상자를 사용하여 테이블, 열 또는 행 필터 매핑을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-103">This topic describes how to change table, column, or row filter mappings by using the **Edit Table Properties** dialog box in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
 <span data-ttu-id="4c29d-104">**테이블 속성 편집** 대화 상자의 옵션은 원래 데이터를 가져올 때 목록에서 테이블을 선택하는 방법을 사용했는지 아니면 SQL 쿼리를 사용하는 방법을 사용했는지에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-104">Options in the **Edit Table Properties** dialog box are different depending on whether you originally imported data by selecting tables from a list or by using a SQL query.</span></span> <span data-ttu-id="4c29d-105">목록에서 선택하여 데이터를 가져온 경우 **테이블 속성 편집** 대화 상자에 테이블 미리 보기 모드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-105">If you originally imported the data by selecting from a list, the **Edit Table Properties** dialog box displays the Table Preview mode.</span></span> <span data-ttu-id="4c29d-106">이 모드에서는 원본 테이블의 첫 50개 행으로 제한된 하위 집합만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-106">This mode displays only a subset limited to the first fifty rows of the source table.</span></span> <span data-ttu-id="4c29d-107">SQL 문을 사용하여 데이터를 가져온 경우 **테이블 속성 편집** 대화 상자에 SQL 문만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-107">If you originally imported the data by using a SQL statement, the **Edit Table Properties** dialog box only displays a SQL statement.</span></span> <span data-ttu-id="4c29d-108">SQL 쿼리 문을 사용하면 필터를 디자인하거나 SQL 문을 직접 편집하여 행의 일부만 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-108">Using a SQL query statement, you can retrieve a subset of rows, either by designing a filter, or by manually editing the SQL statement.</span></span>  
  
 <span data-ttu-id="4c29d-109">현재 테이블과 다른 열이 있는 테이블로 원본을 변경하면 열이 다르다는 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-109">If you change the source to a table that has different columns than the current table, a message is displayed warning that the columns are different.</span></span> <span data-ttu-id="4c29d-110">그런 다음 현재 테이블에 넣을 열을 선택하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-110">You must then select the columns that you want to put in the current table and click **Save**.</span></span> <span data-ttu-id="4c29d-111">테이블 왼쪽의 확인란을 선택하여 테이블 전체를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-111">You can replace the entire table by selecting the check box at the left of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c29d-112">테이블에 파티션이 여러 개 있는 경우 테이블 속성 편집 대화 상자를 사용하여 행 필터 매핑을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-112">If your table has more than one partition, you cannot use the Edit Table Properties dialog box to change row filter mappings.</span></span> <span data-ttu-id="4c29d-113">파티션이 여러 개 있는 테이블에 대한 행 필터 매핑을 변경하려면 파티션 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-113">To change row filter mappings for tables with multiple partitions, use Partition Manager.</span></span> <span data-ttu-id="4c29d-114">자세한 내용은 [파티션&#40;SSAS 테이블 형식&#41;](partitions-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4c29d-114">For more information, see [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
#### <a name="to-change-table-column-or-row-filter-mappings"></a><span data-ttu-id="4c29d-115">테이블, 열 또는 행 필터 매핑을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="4c29d-115">To change table, column, or row filter mappings</span></span>  
  
1.  <span data-ttu-id="4c29d-116">모델 디자이너에서 테이블을 클릭한 다음 **테이블** 메뉴와 **테이블 속성**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-116">In the model designer, click the table, then click on the **Table** menu, and then click **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="4c29d-117">**테이블 속성 편집** 대화 상자에서 필터링할 조건이 포함된 열을 찾은 다음 열 머리글 오른쪽의 아래쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-117">In the **Edit Table Properties** dialog box, locate the column that contains the criteria you want to filter on, and then click the down arrow at the right of the column heading.</span></span>  
  
3.  <span data-ttu-id="4c29d-118">**자동 필터** 메뉴에서 다음 중 하나를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-118">In the **AutoFilter** menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="4c29d-119">열 값 목록에서 필터링 기준으로 사용할 값을 하나 이상 선택하거나 취소한 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-119">In the list of column values, select or clear one or more values to filter by, and then click OK.</span></span>  
  
         <span data-ttu-id="4c29d-120">값의 수가 너무 많은 경우 개별 항목이 목록에 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-120">If the number of values is extremely large, individual items might not be shown in the list.</span></span> <span data-ttu-id="4c29d-121">대신 "표시할 항목이 너무 많음"이라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-121">Instead, you will see the message, "Too many items to show."</span></span>  
  
    -   <span data-ttu-id="4c29d-122">열 형식에 따라 **숫자 필터** 또는 **텍스트 필터** 를 클릭한 다음 같음과 같은 비교 연산자 명령 중 하나를 클릭하거나 사용자 지정 필터를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-122">Click **Number Filters** or **Text Filters** (depending on the type of column), and then clicke of the comparison operator commands (such as Equals), or click Custom Filter.</span></span> <span data-ttu-id="4c29d-123">**사용자 지정 필터** 대화 상자에서 필터를 만든 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4c29d-123">In the **Custom Filter** dialog box, create the filter, and then click **OK**.</span></span>  
  
         <span data-ttu-id="4c29d-124">실수가 있어 새로 시작해야 하는 경우 **행 필터 지우기**를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="4c29d-124">If you make a mistake and need to start over, click **Clear Row Filters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c29d-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4c29d-125">See Also</span></span>  
 [<span data-ttu-id="4c29d-126">테이블 속성 편집 대화 상자&#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="4c29d-126">Edit Table Properties Dialog Box &#40;SSAS&#41;</span></span>](../edit-table-properties-dialog-box-ssas.md)  
  
  
