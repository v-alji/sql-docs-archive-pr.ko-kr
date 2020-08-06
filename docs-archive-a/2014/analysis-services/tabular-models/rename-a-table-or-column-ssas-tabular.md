---
title: 테이블 또는 열 이름 바꾸기 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.renametableorcolumn.f1
ms.assetid: 88061a39-c5aa-403d-a52b-7fdb365fc235
author: minewiskan
ms.author: owend
ms.openlocfilehash: d3a2e9a9f41434e64f9ec5ea2180861b459e8f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738836"
---
# <a name="rename-a-table-or-column-ssas-tabular"></a><span data-ttu-id="bf21d-102">테이블 또는 열 이름 바꾸기(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="bf21d-102">Rename a Table or Column (SSAS Tabular)</span></span>
  <span data-ttu-id="bf21d-103">가져오기 프로세스 동안 **테이블 가져오기 마법사** 의 **테이블 및 뷰 선택** 페이지에서 **이름**을 입력하여 테이블 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-103">You can change the name of a table during the import process by typing a **Friendly Name** in the **Select Tables and Views** page of the **Table Import Wizard**.</span></span> <span data-ttu-id="bf21d-104">**테이블 가져오기 마법사** 의 **SQL 쿼리 지정**페이지에서 쿼리를 지정하여 데이터를 가져오는 경우 테이블 및 열 이름을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-104">You can also change table and column names if you import data by specifying a query on the **Specify a SQL Query** page of the **Table Import Wizard**.</span></span>  
  
 <span data-ttu-id="bf21d-105">데이터를 모델에 추가하면 모델 디자이너 아래의 테이블 탭에 테이블의 이름 또는 제목이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-105">After you have added the data to the model, the name (or title) of a table appears on the table tab, at the bottom of the model designer.</span></span> <span data-ttu-id="bf21d-106">테이블의 이름을 보다 적절한 이름으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-106">You can change the name of your table to give it a more appropriate name.</span></span> <span data-ttu-id="bf21d-107">모델에 데이터를 추가한 후 열의 이름을 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-107">You can also rename a column after the data has been added to the model.</span></span> <span data-ttu-id="bf21d-108">이 옵션은 특히 여러 원본에서 데이터를 가져왔을 때 서로 다른 테이블의 열에 쉽게 구분할 수 있는 이름을 지정하려는 경우에 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-108">This option is especially important when you have imported data from multiple sources, and want to ensure that columns in different tables have names that are easy to distinguish.</span></span>  
  
### <a name="to-rename-a-table"></a><span data-ttu-id="bf21d-109">테이블 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="bf21d-109">To rename a table</span></span>  
  
1.  <span data-ttu-id="bf21d-110">모델 디자이너에서 이름을 바꾸려는 테이블이 포함된 탭을 마우스 오른쪽 단추로 클릭한 다음 **이름 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-110">In the model designer, right-click the tab that contains the table that you want to rename, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="bf21d-111">새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-111">Type the new name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bf21d-112">**테이블 속성 편집** 대화 상자를 사용하여 연결 정보 및 열 매핑을 비롯한 테이블의 다른 속성을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-112">You can edit other properties of a table, including the connection information and column mappings, by using the **Edit Table Properties** dialog box.</span></span> <span data-ttu-id="bf21d-113">그러나 이 대화 상자에서 이름을 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-113">However, you cannot change the name in this dialog box.</span></span>  
  
### <a name="to-rename-a-column"></a><span data-ttu-id="bf21d-114">열 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="bf21d-114">To rename a column</span></span>  
  
1.  <span data-ttu-id="bf21d-115">모델 디자이너에서 이름을 바꾸려는 열의 머리글을 두 번 클릭하거나 머리글을 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **열 이름 바꾸기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-115">In the model designer, double-click the header of the column that you want to rename, or right-click the header and select **Rename Column** from the context menu.</span></span>  
  
2.  <span data-ttu-id="bf21d-116">새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-116">Type the new name.</span></span>  
  
## <a name="naming-requirements-for-columns-and-tables"></a><span data-ttu-id="bf21d-117">열 및 테이블의 명명 요구 사항</span><span class="sxs-lookup"><span data-stu-id="bf21d-117">Naming Requirements for Columns and Tables</span></span>  
 <span data-ttu-id="bf21d-118">다음 단어 및 문자는 테이블 또는 열 이름으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-118">The following words and characters cannot be used in the name of a table or column:</span></span>  
  
-   <span data-ttu-id="bf21d-119">선행 또는 후행 공백</span><span class="sxs-lookup"><span data-stu-id="bf21d-119">Leading or trailing spaces</span></span>  
  
-   <span data-ttu-id="bf21d-120">제어 문자</span><span class="sxs-lookup"><span data-stu-id="bf21d-120">Control characters</span></span>  
  
-   <span data-ttu-id="bf21d-121">Analysis Services 개체의 이름에 사용할 수 없는 다음 문자는.,; ':/ \\ \*|? &% $! + = () [] {}<></span><span class="sxs-lookup"><span data-stu-id="bf21d-121">The following characters (which are not valid in the names of Analysis Services objects): .,;':/\\*|?&%$!+=()[]{}<></span></span>  
  
-   <span data-ttu-id="bf21d-122">MDX(Multidimensional Expressions) 및 DMX(Data Mining Extensions) 함수 이름과 연산자를 비롯한 Analysis Services의 예약된 키워드</span><span class="sxs-lookup"><span data-stu-id="bf21d-122">Analysis Services reserved keywords, including Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) function names and operators.</span></span>  
  
## <a name="effect-of-renaming-on-existing-tables-columns-and-calculations"></a><span data-ttu-id="bf21d-123">기존 테이블, 열 및 계산 이름을 바꿀 경우의 영향</span><span class="sxs-lookup"><span data-stu-id="bf21d-123">Effect of Renaming on Existing Tables, Columns, and Calculations</span></span>  
 <span data-ttu-id="bf21d-124">테이블의 이름을 변경할 때마다 여러 열이나 측정값이 포함될 수 있는 기본 테이블 개체의 이름을 변경하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-124">Whenever you change the name of a table, you change the name of the underlying table object, which may contain multiple columns or measures.</span></span> <span data-ttu-id="bf21d-125">따라서 테이블의 모든 열과 해당 테이블을 사용하는 모든 관계는 해당 정의의 새 이름을 사용하도록 업데이트되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-125">Therefore, any columns that are in the table, and any relationships that use the table, must be updated to use the new name in their definitions.</span></span> <span data-ttu-id="bf21d-126">경우에 따라 이러한 업데이트가 자동으로 수행되지만</span><span class="sxs-lookup"><span data-stu-id="bf21d-126">This update happens automatically in some cases.</span></span> <span data-ttu-id="bf21d-127">측정값은 자동으로 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-127">Measures are not updated automatically.</span></span>  
  
 <span data-ttu-id="bf21d-128">또한 이름이 바뀐 테이블을 사용하거나 이름이 바뀐 테이블의 열을 사용하는 모든 계산도 업데이트되어야 하고 해당 계산에서 파생된 데이터는 새로 고쳐지고 다시 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-128">Moreover, any calculations that use the renamed table, or that use columns from the renamed table, must also be updated, and the data derived from those calculations must be refreshed and recalculated.</span></span> <span data-ttu-id="bf21d-129">영향을 받는 테이블과 계산의 수에 따라서는 이러한 작업을 완료하는 데 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-129">Depending on how many tables and calculations are affected, this can take some time to complete.</span></span> <span data-ttu-id="bf21d-130">따라서 가져오기 프로세스를 진행하는 동안 또는 복잡한 관계와 계산을 만들기 전에 테이블 이름을 바꾸는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bf21d-130">Therefore, the best time to rename tables is either during the import process, or before you start to build complex relationships and calculations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf21d-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf21d-131">See Also</span></span>  
 <span data-ttu-id="bf21d-132">[SSAS 테이블 형식&#41;&#40;테이블 및 열](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="bf21d-132">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="bf21d-133">[PowerPivot &#40;SSAS 테이블 형식&#41;에서 가져오기](import-from-power-pivot-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="bf21d-133">[Import from PowerPivot &#40;SSAS Tabular&#41;](import-from-power-pivot-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="bf21d-134">Analysis Services에서 가져오기&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="bf21d-134">Import from Analysis Services &#40;SSAS Tabular&#41;</span></span>](import-from-analysis-services-ssas-tabular.md)  
  
  
