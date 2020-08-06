---
title: 보고서에 다중 값 매개 변수 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 12ad0e77-4c28-4bbb-ab11-473ae89ec9f1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5269293b6a21f3b1d82eb6835efbd275e3be9620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729079"
---
# <a name="add-a-multi-value-parameter-to-a-report"></a><span data-ttu-id="88642-102">보고서에 다중 값 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="88642-102">Add a multi-value parameter to a Report</span></span>
  <span data-ttu-id="88642-103">사용자가 매개 변수에 둘 이상의 값을 선택할 수 있는 보고서에 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88642-103">You can add a parameter to a report that allows the user to select more than one value for the parameter.</span></span>  
  
 <span data-ttu-id="88642-104">여러 매개 변수 값을 보고서 URL 내의 보고서에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88642-104">You can pass multiple parameter values to the report within the report URL.</span></span> <span data-ttu-id="88642-105">다중 값 매개 변수를 포함하는 URL 예제는 [URL에 보고서 매개 변수 전달](../pass-a-report-parameter-within-a-url.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88642-105">For a URL example includes a multi-value parameter, see [Pass a Report Parameter Within a URL](../pass-a-report-parameter-within-a-url.md).</span></span>  
  
 <span data-ttu-id="88642-106">여러 매개 변수 값을 저장 프로시저에 전달하는 방법에 대한 자세한 내용은 mssqltips.com의 [SSRS 보고서에 다중 선택 매개 변수로 작업](https://go.microsoft.com/fwlink/?LinkId=321529) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88642-106">For information on how to pass multiple parameter values to a stored procedure, see [Working With Multi-Select Parameters for SSRS Reports](https://go.microsoft.com/fwlink/?LinkId=321529) on mssqltips.com.</span></span>  
  
### <a name="to-add-a-multi-value-parameter"></a><span data-ttu-id="88642-107">다중 값 매개 변수를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="88642-107">To add a multi-value parameter</span></span>  
  
1.  <span data-ttu-id="88642-108">보고서 작성기에서 다중 값 매개 변수를 추가하려는 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="88642-108">In Report Builder, open the report that you want to add the multi-value parameter to.</span></span>  
  
2.  <span data-ttu-id="88642-109">보고서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **데이터 세트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-109">Right-click the report dataset, and then click **Dataset Properties**</span></span>  
  
3.  <span data-ttu-id="88642-110">**쿼리** 상자에서 쿼리 텍스트를 편집하거나 쿼리 디자이너를 사용하여 필터를 추가하여 변수를 데이터 세트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-110">Add a variable to the dataset query by either editing the query text in the **Query** box, or by adding a filter by using the query designer.</span></span> <span data-ttu-id="88642-111">자세한 내용은 [관계형 쿼리 디자이너에서 쿼리 빌드&#40;보고서 작성기 및 SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88642-111">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="88642-112">쿼리 텍스트는 쿼리 변수에 대한 DECLARE 문을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-112">The query text must not include the DECLARE statement for the query variable.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="88642-113">쿼리 변수의 텍스트에는 다음 예와 같이 `IN` 연산자가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-113">The text for the query variable must include the `IN` operator, as shown in the following example.</span></span>  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="88642-114">위와 같이 변수 주위에 괄호를 포함 하지 않으면 보고서가 렌더링 되지 않고 "스칼라 변수를 선언 해야 합니다." 라는 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88642-114">If you don't include the parentheses around the variable as shown above, the report fails to render and the "must declare the scalar variable" error is displayed.</span></span>  
  
     <span data-ttu-id="88642-115">포함된 데이터 세트나 공유 데이터 세트에 대한 데이터 세트 매개 변수는 쿼리 변수에 대해 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="88642-115">A dataset parameter for an embedded dataset or a shared dataset is created automatically for the query variable.</span></span> <span data-ttu-id="88642-116">데이터 세트 매개 변수에 대해 보고서 매개 변수가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="88642-116">A report parameter is created automatically for the dataset parameter.</span></span>  
  
4.  <span data-ttu-id="88642-117">**보고서 데이터** 창에서 **매개 변수** 노드를 확장하고 데이터 세트 매개 변수에 대해 자동으로 생성된 보고서 매개 변수를 마우스 오른쪽 단추로 클릭한 다음, **매개 변수 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-117">In the **Report Data** pane, expand the **Parameters** node, right-click the report parameter that was automatically created for the dataset parameter, and then click **Parameter Properties**.</span></span>  
  
5.  <span data-ttu-id="88642-118">**일반** 탭에서 **다중 값 허용** 을 선택하여 매개 변수에 둘 이상의 값을 선택할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-118">In the **General** tab, select **Allow multiple values** to allow a user to select more than one value for the parameter.</span></span>  
  
6.  <span data-ttu-id="88642-119">(옵션) **사용 가능** 값 탭에서 사용자에게 표시할 사용 가능한 값 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-119">(Optionally) In the **Available** values tab, specify a list of available values to display to the user.</span></span>  
  
     <span data-ttu-id="88642-120">사용 가능한 값 목록은 사용자가 매개 변수에 적합한 값만 선택할 수 있도록 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-120">An available values list limits the choices a user can make to only valid values for the parameter.</span></span> <span data-ttu-id="88642-121">여러 값의 경우 목록 맨 위가 **모두 선택** 기능으로 시작되어 사용자가 클릭 한 번으로 모든 값을 선택하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88642-121">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span> <span data-ttu-id="88642-122">데이터 세트 쿼리에서 보고서 매개 변수에 사용 가능한 값을 가져오도록 선택하는 경우 동일한 보고서 매개 변수와 관련된 쿼리 변수를 포함하지 않는 데이터 세트를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-122">If you choose to get the available values for the report parameter from a dataset query, be sure to select a dataset that does not contain the query variable that is associated with the same report parameter.</span></span>  
  
     <span data-ttu-id="88642-123">자세한 내용은 [보고서 매개 변수의 사용 가능한 값 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88642-123">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
### <a name="to-add-a-multi-value-parameter"></a><span data-ttu-id="88642-124">다중 값 매개 변수를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="88642-124">To add a multi-value parameter</span></span>  
  
1.  <span data-ttu-id="88642-125">보고서 작성기에서 다중 값 매개 변수를 추가하려는 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="88642-125">In Report Builder, open the report that you want to add the multi-value parameter to.</span></span>  
  
2.  <span data-ttu-id="88642-126">보고서 데이터 세트를 마우스 오른쪽 단추로 클릭한 다음, **데이터 세트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-126">Right-click the report dataset, and then click **Dataset Properties**</span></span>  
  
3.  <span data-ttu-id="88642-127">**쿼리** 상자에서 쿼리 텍스트를 편집하거나 쿼리 디자이너를 사용하여 필터를 추가하여 변수를 데이터 세트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-127">Add a variable to the dataset query by either editing the query text in the **Query** box, or by adding a filter by using the query designer.</span></span> <span data-ttu-id="88642-128">자세한 내용은 [관계형 쿼리 디자이너에서 쿼리 빌드&#40;보고서 작성기 및 SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88642-128">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="88642-129">쿼리 텍스트는 쿼리 변수에 대한 DECLARE 문을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-129">The query text must not include the DECLARE statement for the query variable.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="88642-130">쿼리 변수의 텍스트에는 다음 예와 같이 `IN` 연산자가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-130">The text for the query variable must include the `IN` operator, as shown in the following example.</span></span>  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="88642-131">위와 같이 변수 주위에 괄호를 포함 하지 않으면 보고서가 렌더링 되지 않고 "스칼라 변수를 선언 해야 합니다." 라는 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88642-131">If you don't include the parentheses around the variable as shown above, the report fails to render and the "must declare the scalar variable" error is displayed.</span></span>  
  
     <span data-ttu-id="88642-132">포함된 데이터 세트나 공유 데이터 세트에 대한 데이터 세트 매개 변수는 쿼리 변수에 대해 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="88642-132">A dataset parameter for an embedded dataset or a shared dataset is created automatically for the query variable.</span></span> <span data-ttu-id="88642-133">데이터 세트 매개 변수에 대해 보고서 매개 변수가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="88642-133">A report parameter is created automatically for the dataset parameter.</span></span>  
  
4.  <span data-ttu-id="88642-134">**보고서 데이터** 창에서 **매개 변수** 노드를 확장하고 데이터 세트 매개 변수에 대해 자동으로 생성된 보고서 매개 변수를 마우스 오른쪽 단추로 클릭한 다음, **매개 변수 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-134">In the **Report Data** pane, expand the **Parameters** node, right-click the report parameter that was automatically created for the dataset parameter, and then click **Parameter Properties**.</span></span>  
  
5.  <span data-ttu-id="88642-135">**일반** 탭에서 **다중 값 허용** 을 선택하여 매개 변수에 둘 이상의 값을 선택할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-135">In the **General** tab, select **Allow multiple values** to allow a user to select more than one value for the parameter.</span></span>  
  
6.  <span data-ttu-id="88642-136">(옵션) **사용 가능** 값 탭에서 사용자에게 표시할 사용 가능한 값 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-136">(Optionally) In the **Available** values tab, specify a list of available values to display to the user.</span></span>  
  
     <span data-ttu-id="88642-137">사용 가능한 값 목록은 사용자가 매개 변수에 적합한 값만 선택할 수 있도록 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-137">An available values list limits the choices a user can make to only valid values for the parameter.</span></span> <span data-ttu-id="88642-138">여러 값의 경우 목록 맨 위가 **모두 선택** 기능으로 시작되어 사용자가 클릭 한 번으로 모든 값을 선택하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88642-138">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span> <span data-ttu-id="88642-139">데이터 세트 쿼리에서 보고서 매개 변수에 사용 가능한 값을 가져오도록 선택하는 경우 동일한 보고서 매개 변수와 관련된 쿼리 변수를 포함하지 않는 데이터 세트를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88642-139">If you choose to get the available values for the report parameter from a dataset query, be sure to select a dataset that does not contain the query variable that is associated with the same report parameter.</span></span>  
  
     <span data-ttu-id="88642-140">자세한 내용은 [보고서 매개 변수의 사용 가능한 값 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88642-140">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88642-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88642-141">See Also</span></span>  
 <span data-ttu-id="88642-142">[보고서 &#40;보고서 작성기 및 SSRS에 연계 매개 변수를 추가&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="88642-142">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="88642-143">보고서 매개 변수 추가, 변경 또는 삭제&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="88642-143">Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;</span></span>](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
  
