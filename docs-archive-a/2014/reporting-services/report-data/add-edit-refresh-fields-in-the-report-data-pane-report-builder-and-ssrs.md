---
title: 보고서 데이터 창에서 필드 추가, 편집, 새로 고침(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2e36f0fe-8100-4513-b169-14d611646f81
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a20880b84383fc5d9f96c5611419a08facb9ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639346"
---
# <a name="add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs"></a><span data-ttu-id="a86a0-102">보고서 데이터 창에서 필드 추가, 편집, 새로 고침(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="a86a0-102">Add, Edit, Refresh Fields in the Report Data Pane (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a86a0-103">데이터 세트 필드는 외부 데이터 원본에서 데이터 세트 쿼리를 실행할 때 반환되는 데이터를 나타내는 기본 제공 필드 이름 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-103">Dataset fields are the built-in collection of field names that represent the data that is returned when a dataset query runs on an external data source.</span></span>  
  
 <span data-ttu-id="a86a0-104">포함된 데이터 세트의 경우 데이터 세트 필드는 쿼리 작성을 마치고 쿼리 디자이너 창을 닫은 후 만들어지는 필드와 사용자가 만드는 계산 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-104">For an embedded dataset, the dataset fields are the fields that are created after you finish building a query and close the Query Designer pane, and calculated fields that you create.</span></span>  
  
 <span data-ttu-id="a86a0-105">공유 데이터 세트의 경우 데이터 세트 필드는 보고서에 해당 데이터 세트를 추가했을 때 공유 데이터 세트 정의에 있는 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-105">For a shared dataset, the dataset fields are the fields from the shared dataset definition when you added it to your report.</span></span> <span data-ttu-id="a86a0-106">보고서 서버의 공유 데이터 세트 쿼리가 보고서를 실행할 때 항상 사용되지만 보고서의 데이터 세트 필드 목록은 고정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-106">Although the query from the shared dataset on the report server is always used when you run the report, the list of dataset fields in the report is static.</span></span>  
  
 <span data-ttu-id="a86a0-107">**필드 새로 고침**을 사용하여 보고서의 필드 목록을 공유 데이터 세트 쿼리에서의 현재 필드 목록과 일치하도록 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-107">Use **Refresh Fields** to update the list of fields in the report to match the current list of fields from the shared dataset query.</span></span> <span data-ttu-id="a86a0-108">필드 목록을 새로 고치는 경우 보고서에서 정의하는 계산 필드는 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-108">Refreshing the field list does not affect the calculated fields that you define in your report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-query-field"></a><span data-ttu-id="a86a0-109">쿼리 필드를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="a86a0-109">To add a query field</span></span>  
  
1.  <span data-ttu-id="a86a0-110">보고서 데이터 창에서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **쿼리 필드 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-110">In the Report Data pane, right-click the dataset, and then click **Add Query Field**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a86a0-111">보고서 데이터 창을 볼 수 없는 경우 **보기** 메뉴에서 **보고서 데이터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-111">If you cannot see the Report Data pane, from the **View** menu, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="a86a0-112">**데이터 세트 속성** 대화 상자의 **필드** 페이지에서 **추가**를 클릭한 다음, **쿼리 필드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-112">In the **Fields** page of the **Dataset Properties** dialog box, click **Add**, and then click **Query Field**.</span></span> <span data-ttu-id="a86a0-113">표 아래쪽에 새 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-113">A new row is added to the bottom of the grid.</span></span>  
  
3.  <span data-ttu-id="a86a0-114">**필드 이름** 입력란에 필드 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-114">In the **Field Name** text box, type the name for the field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a86a0-115">이름은 데이터 세트에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-115">Names must be unique in the dataset.</span></span>  
  
4.  <span data-ttu-id="a86a0-116">**필드 원본** 입력란에 데이터 원본의 기존 필드 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-116">In the **Field Source** text box, type the name of an existing field on the data source.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-calculated-field"></a><span data-ttu-id="a86a0-117">계산 필드를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="a86a0-117">To add a calculated field</span></span>  
  
1.  <span data-ttu-id="a86a0-118">보고서 데이터 창에서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **계산 필드 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-118">In the Report Data pane, right-click the dataset, and then click **Add Calculated Field**.</span></span>  
  
2.  <span data-ttu-id="a86a0-119">**데이터 세트 속성** 대화 상자의 **필드** 페이지에서 **추가**를 클릭한 다음, **계산 필드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-119">In the **Fields** page of the **Dataset Properties** dialog box, click **Add**, and then click **Calculated Field**.</span></span> <span data-ttu-id="a86a0-120">표 아래쪽에 새 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-120">A new row is added to the bottom of the grid.</span></span>  
  
3.  <span data-ttu-id="a86a0-121">**필드 이름** 입력란에 필드 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-121">In the **Field Name** text bo, type the name for the field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a86a0-122">이름은 데이터 세트에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-122">Names must be unique in the dataset.</span></span>  
  
4.  <span data-ttu-id="a86a0-123">**필드 원본** 입력란에 필드의 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-123">In the **Field Source** text box, type the expression for the field.</span></span> <span data-ttu-id="a86a0-124">식을 작성하려면 식 단추(**fx**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-124">Click the expression (**fx**) button to build an expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a86a0-125">계산 필드의 식은 보고서 항목에 대한 참조나 집계를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-125">The expression for a calculated field cannot contain aggregates or references to report items.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-a-query-field-or-a-dataset-field"></a><span data-ttu-id="a86a0-126">쿼리 필드 또는 데이터 세트 필드를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="a86a0-126">To edit a query field or a dataset field</span></span>  
  
1.  <span data-ttu-id="a86a0-127">보고서 데이터 창에서 필드를 마우스 오른쪽 단추로 클릭한 다음 **필드 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-127">In the Report Data pane, right-click the field, and then click **Field Properties**.</span></span>  
  
2.  <span data-ttu-id="a86a0-128">**데이터 세트 속성** 대화 상자의 **필드** 페이지에서 기존 필드를 클릭하여 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-128">In the **Fields** page of the **Dataset Properties** dialog box, click an existing field to select the row.</span></span>  
  
3.  <span data-ttu-id="a86a0-129">필드 이름 또는 필드 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-129">Change the name of the field or the value of the field.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-query-field-or-a-calculated-field"></a><span data-ttu-id="a86a0-130">쿼리 필드 또는 계산 필드를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="a86a0-130">To delete a query field or a calculated field</span></span>  
  
1.  <span data-ttu-id="a86a0-131">보고서 데이터 창에서 데이터 세트를 확장하여 필드 컬렉션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-131">In the Report Data pane, expand the dataset to display the field collection.</span></span>  
  
2.  <span data-ttu-id="a86a0-132">제거할 필드를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-132">Right-click the field you want to remove, and then click **Delete**.</span></span>  
  
### <a name="to-refresh-the-field-collection-in-the-report-data-pane-for-a-shared-dataset"></a><span data-ttu-id="a86a0-133">보고서 데이터 창에서 공유 데이터 세트에 대한 필드 컬렉션을 새로 고치려면</span><span class="sxs-lookup"><span data-stu-id="a86a0-133">To refresh the field collection in the Report Data Pane for a shared dataset</span></span>  
  
1.  <span data-ttu-id="a86a0-134">보고서 데이터 창에서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-134">In the Report Data pane, right-click the dataset, and then click **Query**.</span></span>  
  
2.  <span data-ttu-id="a86a0-135">**필드 새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-135">Click **Refresh Fields**.</span></span>  
  
     <span data-ttu-id="a86a0-136">보고서 서버에서 공유 데이터 세트 쿼리가 실행되고 현재 필드 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a86a0-136">On the report server, the shared dataset query runs and returns the current field collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a86a0-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a86a0-137">See Also</span></span>  
 <span data-ttu-id="a86a0-138">[데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a86a0-138">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a86a0-139">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a86a0-139">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="a86a0-140">[보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a86a0-140">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a86a0-141">[Reporting Services 쿼리 디자이너](../reporting-services-query-designers.md) </span><span class="sxs-lookup"><span data-stu-id="a86a0-141">[Reporting Services Query Designers](../reporting-services-query-designers.md) </span></span>  
 [<span data-ttu-id="a86a0-142">쿼리 디자이너&#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="a86a0-142">Query Designers &#40;Report Builder&#41;</span></span>](../query-designers-report-builder.md)  
  
  
