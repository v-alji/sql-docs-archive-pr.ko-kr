---
title: 보고서 매개 변수와 쿼리 매개 변수 연결(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- queries [Reporting Services], parameters
- parameters [Reporting Services], queries
ms.assetid: 6d297e1a-ff71-472a-addc-349e863092b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f65aa36e8910378d68963c8c9990518b661025ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730215"
---
# <a name="associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="1fa84-102">보고서 매개 변수와 쿼리 매개 변수 연결(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1fa84-102">Associate a Query Parameter with a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1fa84-103">쿼리 변수가 포함된 데이터 세트 쿼리를 정의할 경우 쿼리 명령이 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-103">When you define a dataset query that contains a query variable, the query command is parsed.</span></span> <span data-ttu-id="1fa84-104">각 쿼리 변수에 대해 해당 데이터 세트 매개 변수 및 보고서 매개 변수가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-104">For each query variable, a corresponding dataset parameter and report parameter are created.</span></span> <span data-ttu-id="1fa84-105">데이터 세트 매개 변수는 보고서 매개 변수를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-105">The dataset parameter points to the report parameter.</span></span> <span data-ttu-id="1fa84-106">이를 통해 사용자는 쿼리에 직접 전달되는 값을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-106">This enables a user to enter a value that passes directly to the query.</span></span> <span data-ttu-id="1fa84-107">쿼리 명령을 편집할 때마다 동일한 프로세스가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-107">Each time you edit the query command, the same process takes place.</span></span>  
  
 <span data-ttu-id="1fa84-108">쿼리 매개 변수에 바인딩된 보고서 매개 변수의 이름을 바꾸는 경우 이 항목의 절차를 사용하여 쿼리 매개 변수를 이름이 바뀐 보고서 매개 변수에 직접 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-108">If you rename a report parameter that is bound to a query parameter, you need to manually link the query parameters to the renamed report parameter by using the procedure in this topic.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-query-parameter-with-a-report-parameter"></a><span data-ttu-id="1fa84-109">쿼리 매개 변수를 보고서 매개 변수와 연결하려면</span><span class="sxs-lookup"><span data-stu-id="1fa84-109">To associate a query parameter with a report parameter</span></span>  
  
1.  <span data-ttu-id="1fa84-110">보고서 데이터 창에서 데이터 세트를 마우스 오른쪽 단추로 클릭하고 **데이터 세트 속성**을 클릭한 다음, **매개 변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-110">In the Report Data pane, right-click the dataset, click **Dataset Properties**, and then click **Parameters**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1fa84-111">보고서 데이터 창이 표시되지 않는 경우 **보기** 메뉴에서 **보고서 데이터** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-111">If the Report Data pane is not visible, click **Report Data** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="1fa84-112">열 **매개 변수 이름**에서 쿼리 매개 변수의 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-112">In the column **Parameter Name**, find the name of the query parameter.</span></span> <span data-ttu-id="1fa84-113">매개 변수 이름은 쿼리를 기반으로 자동 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-113">Parameter names are automatically populated based on the query.</span></span> <span data-ttu-id="1fa84-114">쿼리를 변경할 때마다 새 쿼리 매개 변수가 있는지 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-114">Every time you change the query, the query is checked for new query parameters.</span></span> <span data-ttu-id="1fa84-115">직접 만드는 쿼리 매개 변수는 쿼리가 변경될 때 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-115">Query parameters that you create manually are not changed when the query changes.</span></span>  
  
    -   <span data-ttu-id="1fa84-116">**매개 변수 이름**에서 쿼리에 있는 것과 같은 쿼리 매개 변수 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-116">In **Parameter Name**, find the query parameter name as it exists in the query.</span></span> <span data-ttu-id="1fa84-117">직접 새 쿼리 매개 변수를 추가하고 이름을 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-117">You can also manually add a new query parameter and enter a name.</span></span>  
  
    -   <span data-ttu-id="1fa84-118">**매개 변수 값**에서 쿼리 매개 변수에 전달할 값을 반환하는 식을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-118">In **Parameter Value**, type or select an expression that evaluates to the value to pass to the query parameter.</span></span> <span data-ttu-id="1fa84-119">이는 일반적으로 보고서 매개 변수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-119">This is typically the name of the report parameter.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="1fa84-120">보고서 매개 변수는 쿼리 매개 변수에 대한 값으로 제한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-120">You are not limited to report parameters as values for a query parameter.</span></span> <span data-ttu-id="1fa84-121">값을 반환하는 식을 매개 변수 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-121">You can use any expression that evaluates to a value for the parameter value.</span></span>  
  
3.  <span data-ttu-id="1fa84-122">쿼리 매개 변수를 추가하려면 2단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="1fa84-122">Repeat step 2 for additional query parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa84-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1fa84-123">See Also</span></span>  
 <span data-ttu-id="1fa84-124">[보고서 포함 된 데이터 집합 및 공유 데이터 집합 &#40;보고서 작성기 및 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1fa84-124">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1fa84-125">보고서 매개 변수 개념 &#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1fa84-125">Report Parameters Concept &#40;Report Builder and SSRS&#41;</span></span>](../report-design/report-parameters-concepts-report-builder-and-ssrs.md)  
  
  
