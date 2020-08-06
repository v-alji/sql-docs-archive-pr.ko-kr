---
title: 다차원 데이터의 매개 변수 값에 대해 숨겨진 데이터 집합 표시 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eb01c4ca-4fd6-4629-b595-f0d2565915df
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f9c005b6e7c8927316c19a3302e32f4407f9885
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742855"
---
# <a name="show-hidden-datasets-for-parameter-values-for-multidimensional-data-report-builder-and-ssrs"></a><span data-ttu-id="6d362-102">다차원 데이터의 매개 변수 값에 대해 숨겨진 데이터 세트 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6d362-102">Show Hidden Datasets for Parameter Values for Multidimensional Data (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6d362-103">보고서에는 보고서 데이터 창에 기본적으로 표시되지 않는 자동 생성 데이터 세트(숨겨진 데이터 세트라고도 함)이 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d362-103">Your report might include automatically-generated datasets (also known as hidden datasets) that do not appear by default in the Report Data pane.</span></span> <span data-ttu-id="6d362-104">이러한 데이터 세트는 다음과 같은 방법으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d362-104">These datasets are created in the following ways:</span></span>  
  
-   <span data-ttu-id="6d362-105">다차원 데이터베이스에 대해 사용할 수 있는 일부 쿼리 디자이너에서는 쿼리 창의 필터 영역에서 필터링할 필드를 지정하고, 필터에 쿼리 매개 변수를 만들지 여부를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d362-105">In some query designers for multidimensional databases, you can specify fields to filter on in the filter area of the query pane, and select whether to create a query parameter for the filter.</span></span> <span data-ttu-id="6d362-106">매개 변수 옵션을 선택하면 보고서 매개 변수에 올바른 값을 제공하기 위해 보고서 데이터 세트가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6d362-106">If you select the parameter option, report datasets are automatically created to provide valid values for the report parameter.</span></span>  
  
-   <span data-ttu-id="6d362-107">다차원 데이터베이스를 기반으로 하는 쿼리를 가져올 경우 보고서에 숨겨진 데이터 세트도 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d362-107">If you import a query based on multidimensional databases, you might also include hidden datasets in your report.</span></span>  
  
 <span data-ttu-id="6d362-108">마법사에서는 숨겨진 데이터 세트를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d362-108">Hidden datasets are not available to use from a wizard.</span></span>  
  
 <span data-ttu-id="6d362-109">보고서 데이터 창의 뷰를 변경하여 보고서의 모든 데이터 세트를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d362-109">You can change the view in the Report Data pane to display all datasets in the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-hidden-datasets"></a><span data-ttu-id="6d362-110">숨겨진 데이터 세트를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="6d362-110">To display hidden datasets</span></span>  
  
-   <span data-ttu-id="6d362-111">보고서 데이터 창에서 데이터 세트 폴더를 마우스 오른쪽 단추로 클릭한 다음, **숨겨진 데이터 세트 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6d362-111">In the Report Data pane, right-click the Datasets folder, and then click **Show Hidden Datasets**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d362-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d362-112">See Also</span></span>  
 <span data-ttu-id="6d362-113">[쿼리 디자이너 &#40;보고서 작성기&#41;](../query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="6d362-113">[Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) </span></span>  
 <span data-ttu-id="6d362-114">[Reporting Services 쿼리 디자이너](../reporting-services-query-designers.md) </span><span class="sxs-lookup"><span data-stu-id="6d362-114">[Reporting Services Query Designers](../reporting-services-query-designers.md) </span></span>  
 <span data-ttu-id="6d362-115">[보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6d362-115">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6d362-116">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d362-116">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
  
  
