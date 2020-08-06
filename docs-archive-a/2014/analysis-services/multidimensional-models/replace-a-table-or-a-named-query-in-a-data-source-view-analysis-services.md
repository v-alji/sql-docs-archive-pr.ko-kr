---
title: 데이터 원본 뷰의 테이블 또는 명명 된 쿼리 바꾸기 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- replacing tables
- data source views [Analysis Services], tables
- named queries [Analysis Services], replacing tables
- tables [Analysis Services], data source views
- partitions [Analysis Services], named queries
ms.assetid: 60c2a018-1299-4915-b60e-e73316524def
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b5055de60ba757c9dcfa118e4e2c4748c6534e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652400"
---
# <a name="replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services"></a><span data-ttu-id="37bf3-102">데이터 원본 뷰의 테이블 또는 명명된 쿼리 바꾸기(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="37bf3-102">Replace a Table or a Named Query in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="37bf3-103">데이터 원본 뷰 디자이너에서 데이터 원본 뷰(DSV)의 테이블, 뷰 또는 명명된 쿼리를 같은 데이터 원본이나 다른 데이터 원본의 다른 테이블 또는 뷰와 바꾸거나 DSV에 정의된 명명된 쿼리와 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-103">In Data Source View Designer, you can replace a table, view, or named query in a data source view (DSV) with a different table or view from the same or a different data source, or with a named query defined in the DSV.</span></span> <span data-ttu-id="37bf3-104">테이블을 바꾸는 경우 DSV의 테이블에 대한 개체 ID는 변경되지 않으므로 해당 테이블에 대한 참조를 포함하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 또는 프로젝트의 다른 모든 개체는 계속해서 이 테이블을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-104">When you replace a table, all other objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project that have references to the table continue to reference the table because the object ID for the table in the DSV does not change.</span></span> <span data-ttu-id="37bf3-105">이름 및 열 유형 일치를 기반으로 관련된 모든 관계는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-105">Any relationships that are still relevant (based on name and column-type matching) are retained.</span></span> <span data-ttu-id="37bf3-106">반면 테이블을 삭제한 다음 추가하면 참조 및 관계가 모두 손실되며 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-106">In contrast, if you delete and then add a table, references and relationships are lost and must be recreated.</span></span>  
  
 <span data-ttu-id="37bf3-107">테이블을 다른 테이블로 바꾸려면 프로젝트 모드에서 데이터 원본 뷰 디자이너의 원본 데이터에 대한 활성 연결이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-107">To replace a table with another table, you must have an active connection to the source data in Data Source View Designer in project mode.</span></span>  
  
 <span data-ttu-id="37bf3-108">데이터 원본 뷰의 테이블을 동일한 데이터 원본의 다른 테이블로 바꾸는 경우가 가장 많습니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-108">You most frequently replace a table in the data source view with another table in the data source.</span></span> <span data-ttu-id="37bf3-109">그러나 명명된 쿼리를 테이블로 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-109">However, you can also replace a named query with a table.</span></span> <span data-ttu-id="37bf3-110">예를 들어 이전에 명명된 쿼리로 바꾼 테이블을 다시 테이블로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-110">For example, you previously replaced a table with a named query, and now want to revert to a table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="37bf3-111">데이터 원본의 테이블 이름을 바꾸는 경우 테이블 바꾸기 단계를 수행한 다음 DSV를 새로 고치기 전에 이름을 바꾼 테이블을 DSV의 해당 테이블 원본으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-111">If you rename a table in a data source, follow the steps for replacing a table and specify the renamed table as the source of the corresponding table in the DSV before you refresh a DSV.</span></span> <span data-ttu-id="37bf3-112">바꾸기 및 이름 바꾸기 프로세스를 완료하면 DSV의 테이블, 테이블 참조 및 테이블 관계가 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-112">Completing the replacement and renaming process preserves the table, the table's references, and the table's relationships in the DSV.</span></span> <span data-ttu-id="37bf3-113">그렇게 하지 않으면 DSV를 새로 고칠 때 데이터 원본에서 이름을 바꾼 테이블이 삭제된 것으로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-113">Otherwise, when you refresh the DSV, a renamed table in data source is interpreted as being deleted.</span></span> <span data-ttu-id="37bf3-114">자세한 내용은 [데이터 원본 뷰에서 스키마 새로 고침&#40;Analysis Services&#41;](refresh-the-schema-in-a-data-source-view-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37bf3-114">For more information, see [Refresh the Schema in a Data Source View &#40;Analysis Services&#41;](refresh-the-schema-in-a-data-source-view-analysis-services.md).</span></span>  
  
##  <a name="replace-a-table-with-a-named-query"></a><a name="bkmk_nq"></a> <span data-ttu-id="37bf3-115">테이블을 명명된 쿼리로 바꾸기</span><span class="sxs-lookup"><span data-stu-id="37bf3-115">Replace a table with a named query</span></span>  
  
1.  <span data-ttu-id="37bf3-116">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 테이블이나 명명된 쿼리를 바꿀 데이터 원본 뷰가 포함된 프로젝트를 열거나 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to replace a table or a named query.</span></span>  
  
2.  <span data-ttu-id="37bf3-117">솔루션 탐색기에서 **데이터 원본 뷰** 폴더를 확장한 다음 해당 데이터 원본 뷰를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-117">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="37bf3-118">**명명된 쿼리 만들기** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-118">Open the **Create Named Query** dialog box.</span></span> <span data-ttu-id="37bf3-119">**테이블** 또는 **다이어그램** 창에서 바꿀 테이블을 마우스 오른쪽 단추로 클릭하고 **테이블 바꾸기** 를 가리킨 다음 **새 명명된 쿼리로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-119">In either **Tables** or **Diagram** pane, right-click the table that you wish to replace, point to **Replace Table** and then click **With New Named Query**.</span></span>  
  
4.  <span data-ttu-id="37bf3-120">**명명된 쿼리 만들기** 대화 상자에서 명명된 쿼리를 정의한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-120">In the **Create Named Query** dialog box, define the named query and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="37bf3-121">수정된 데이터 원본 뷰를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-121">Save the modified data source view.</span></span>  
  
## <a name="replace-a-table-or-named-query-with-a-table"></a><span data-ttu-id="37bf3-122">테이블이나 명명된 쿼리를 테이블로 바꾸기</span><span class="sxs-lookup"><span data-stu-id="37bf3-122">Replace a table or named query with a table</span></span>  
  
1.  <span data-ttu-id="37bf3-123">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 테이블이나 명명된 쿼리를 바꿀 데이터 원본 뷰가 포함된 프로젝트를 열거나 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-123">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to replace a table or a named query.</span></span>  
  
2.  <span data-ttu-id="37bf3-124">솔루션 탐색기에서 **데이터 원본 뷰** 폴더를 확장한 다음 해당 데이터 원본 뷰를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-124">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="37bf3-125">**다른 테이블로 테이블 바꾸기** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-125">Open the **Replace Table with Other Table** dialog box.</span></span> <span data-ttu-id="37bf3-126">**테이블** 또는 **다이어그램** 창에서 바꿀 테이블이나 명명된 쿼리를 마우스 오른쪽 단추로 클릭하고 **테이블 바꾸기** 를 가리킨 다음 **다른 테이블로**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-126">In either **Tables** or **Diagram** pane, right-click the table or named query that you wish to replace, point to **Replace Table** and then click **With Other Table**.</span></span>  
  
4.  <span data-ttu-id="37bf3-127">**다른 테이블로 테이블 바꾸기** 대화 상자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-127">In the **Replace Table with Other Table** dialog box:</span></span>  
  
    1.  <span data-ttu-id="37bf3-128">**데이터 원본** 드롭다운 목록 상자에서 원하는 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-128">In the **DataSource** drop-down list box, select the desired data source</span></span>  
  
    2.  <span data-ttu-id="37bf3-129">테이블이나 명명된 쿼리를 바꿀 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-129">Select the table with which you wish to replace the table or named query</span></span>  
  
5.  <span data-ttu-id="37bf3-130">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-130">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="37bf3-131">수정된 데이터 원본 뷰를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="37bf3-131">Save the modified data source view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37bf3-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37bf3-132">See Also</span></span>  
 [<span data-ttu-id="37bf3-133">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="37bf3-133">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
