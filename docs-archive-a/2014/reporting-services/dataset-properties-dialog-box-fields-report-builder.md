---
title: 데이터 집합 속성 대화 상자, 필드 (보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10021"
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b766aa23cce390bc3ffdcf10efdb38efc91f3e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647533"
---
# <a name="dataset-properties-dialog-box-fields-report-builder"></a><span data-ttu-id="e728d-102">데이터 세트 속성 대화 상자, 필드(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="e728d-102">Dataset Properties Dialog Box, Fields (Report Builder)</span></span>
  <span data-ttu-id="e728d-103">**데이터 세트 속성** 대화 상자에서 **필드**를 선택하여 보고서 데이터 세트의 필드 컬렉션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-103">Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset.</span></span> <span data-ttu-id="e728d-104">필드 목록은 자동으로 채워지지만 **필드** 를 사용하여 쿼리와 계산 필드를 추가, 편집 및 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-104">The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.</span></span>  
  
 <span data-ttu-id="e728d-105">계산 필드는 포함된 데이터 세트에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-105">Calculated fields are supported only on embedded datasets.</span></span> <span data-ttu-id="e728d-106">자세한 내용은 [보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e728d-106">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e728d-107">옵션</span><span class="sxs-lookup"><span data-stu-id="e728d-107">Options</span></span>  
 <span data-ttu-id="e728d-108">**추가**</span><span class="sxs-lookup"><span data-stu-id="e728d-108">**Add**</span></span>  
 <span data-ttu-id="e728d-109">데이터 세트에 새 쿼리나 계산 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-109">Add a new query or calculated field to the dataset.</span></span>  
  
 <span data-ttu-id="e728d-110">**삭제**</span><span class="sxs-lookup"><span data-stu-id="e728d-110">**Delete**</span></span>  
 <span data-ttu-id="e728d-111">선택한 필드를 데이터 세트에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-111">Delete the selected field from the dataset.</span></span>  
  
 <span data-ttu-id="e728d-112">**필드 이름**</span><span class="sxs-lookup"><span data-stu-id="e728d-112">**Field Name**</span></span>  
 <span data-ttu-id="e728d-113">필드의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-113">Type a name for the field.</span></span> <span data-ttu-id="e728d-114">필드는 데이터 세트 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-114">The field must be unique within the dataset.</span></span> <span data-ttu-id="e728d-115">데이터 세트의 기존 필드 각각에 대해서는 이름이 미리 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-115">For each existing field in the dataset, the name is pre-populated.</span></span>  
  
 <span data-ttu-id="e728d-116">**필드 원본**</span><span class="sxs-lookup"><span data-stu-id="e728d-116">**Field Source**</span></span>  
 <span data-ttu-id="e728d-117">필드의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-117">Enter a value for the field.</span></span>  
  
 <span data-ttu-id="e728d-118">계산 필드의 경우 필드 원본은 데이터 세트 쿼리 또는 사용자가 만든 식으로 검색된 기존 필드의 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-118">For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create.</span></span> <span data-ttu-id="e728d-119">예를 들어 Sales라는 쿼리 필드의 값에 10을 곱한 값을 표시하는 필드를 만들려면 `=10 * Fields!Sales.Value`식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-119">For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.</span></span>  
  
 <span data-ttu-id="e728d-120">쿼리 필드의 경우 필드 원본은 데이터 세트 쿼리로 검색된 기존 필드의 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-120">For a query field, the field source must be the name of an existing field retrieved by the dataset query.</span></span>  
  
 <span data-ttu-id="e728d-121">**식(fx)**</span><span class="sxs-lookup"><span data-stu-id="e728d-121">**Expression (fx)**</span></span>  
 <span data-ttu-id="e728d-122">새 계산 필드의 식을 추가하거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-122">Add or change an expression for the new calculated field.</span></span> <span data-ttu-id="e728d-123">이 단추는 **추가** 를 클릭하고 **계산 필드**를 선택했을 때만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e728d-123">This button only appears when you click **Add** and select **Calculated Field**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e728d-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e728d-124">See Also</span></span>  
 <span data-ttu-id="e728d-125">[데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e728d-125">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e728d-126">[공유 데이터 집합 또는 포함 된 데이터 집합 &#40;보고서 작성기 및 SSRS를 만듭니다&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e728d-126">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e728d-127">[대화 상자, 창 및 마법사에 대 한 보고서 작성기 도움말](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="e728d-127">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="e728d-128">[데이터 집합 속성 대화 상자, 옵션 &#40;보고서 작성기&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e728d-128">[Dataset Properties Dialog Box, Options &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md) </span></span>  
 <span data-ttu-id="e728d-129">[데이터 집합 속성 대화 상자, 필터 &#40;보고서 작성기&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e728d-129">[Dataset Properties Dialog Box, Filters &#40;Report Builder&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md) </span></span>  
 <span data-ttu-id="e728d-130">[데이터 집합 속성 대화 상자, 매개 변수 &#40;보고서 작성기&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e728d-130">[Dataset Properties Dialog Box, Parameters &#40;Report Builder&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md) </span></span>  
 <span data-ttu-id="e728d-131">[데이터 집합 속성 대화 상자, 쿼리 &#40;보고서 작성기&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e728d-131">[Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md) </span></span>  
 <span data-ttu-id="e728d-132">[식&#40;보고서 작성기 및 SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e728d-132">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e728d-133">보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="e728d-133">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
