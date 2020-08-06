---
title: 데이터 세트 속성 대화 상자, 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10150"
- sql12.rtp.rptdesigner.datasetproperties.parameters.f1
ms.assetid: 43b00aab-e2c3-4e85-abe1-a2b5a21efeed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0073971de373321ce347f416657671e1f497dd1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742891"
---
# <a name="dataset-properties-dialog-box-parameters"></a><span data-ttu-id="93765-102">데이터 세트 속성 대화 상자, 매개 변수</span><span class="sxs-lookup"><span data-stu-id="93765-102">Dataset Properties Dialog Box, Parameters</span></span>
  <span data-ttu-id="93765-103">**데이터 세트 속성** 대화 상자에서 **매개 변수**를 선택하여 보고서 매개 변수에 연결되는 쿼리 매개 변수를 비롯한 쿼리 매개 변수를 추가, 변경 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93765-103">Select **Parameters** on the **Dataset Properties** dialog box to add, change, and delete query parameters, including query parameters that link to report parameters.</span></span>  
  
 <span data-ttu-id="93765-104">쿼리 탭에서 쿼리가 변경될 때마다 쿼리 명령이 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="93765-104">Whenever the query is changed on the query tab, the query command is parsed.</span></span> <span data-ttu-id="93765-105">식별된 각 쿼리 매개 변수에 대해 대/소문자를 구분하는 동일한 이름의 보고서 매개 변수가 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="93765-105">For each query parameter that is identified, a report parameter with an identical case-sensitive name is created.</span></span> <span data-ttu-id="93765-106">기본적으로 쿼리 매개 변수는 자동으로 쿼리 매개 변수 목록에 추가되고 해당 보고서 매개 변수에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="93765-106">By default, the query parameter is automatically added to the query parameter list and linked to the corresponding report parameter.</span></span>  
  
 <span data-ttu-id="93765-107">한 보고서 매개 변수의 기본값이 쿼리 매개 변수에 연결된 다른 보고서 매개 변수에 종속된 경우 보고서 매개 변수의 순서( **보고서 매개 변수 속성** 대화 상자에 표시되는 순서)가 중요한 의미를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="93765-107">If there are dependencies for the default values of one report parameter on another report parameter that is linked to a query parameter, the order of report parameters (as they appear in the **Report Parameters Properties** dialog box) is important.</span></span> <span data-ttu-id="93765-108">목록의 아래쪽에 있는 보고서 매개 변수는 목록의 위쪽에 있는 보고서 매개 변수를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93765-108">Report parameters later in the list can refer to report parameters earlier in the list.</span></span> <span data-ttu-id="93765-109">보고서 매개 변수에 대한 자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93765-109">For more information about report parameters, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="93765-110">옵션</span><span class="sxs-lookup"><span data-stu-id="93765-110">Options</span></span>  
 <span data-ttu-id="93765-111">**추가**</span><span class="sxs-lookup"><span data-stu-id="93765-111">**Add**</span></span>  
 <span data-ttu-id="93765-112">목록에 새 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="93765-112">Add a new parameter to the list.</span></span>  
  
 <span data-ttu-id="93765-113">**Delete**</span><span class="sxs-lookup"><span data-stu-id="93765-113">**Delete**</span></span>  
 <span data-ttu-id="93765-114">선택한 매개 변수를 목록에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="93765-114">Remove the selected parameter from the list.</span></span>  
  
 <span data-ttu-id="93765-115">**매개 변수 이름**</span><span class="sxs-lookup"><span data-stu-id="93765-115">**Parameter name**</span></span>  
 <span data-ttu-id="93765-116">**데이터 세트 속성** 대화 상자의 **쿼리** 탭에서 데이터 세트에 추가한 쿼리 매개 변수의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="93765-116">Type the name of a query parameter that you added to the dataset on the **Query** tab of the **Dataset Properties** dialog box.</span></span>  
  
 <span data-ttu-id="93765-117">**매개 변수 값**</span><span class="sxs-lookup"><span data-stu-id="93765-117">**Parameter value**</span></span>  
 <span data-ttu-id="93765-118">쿼리 매개 변수의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="93765-118">Enter a value for the query parameter.</span></span> <span data-ttu-id="93765-119">이 값은 정적 값 또는 보고서 내의 개체를 참조하는 식일 수 있지만 보고서 항목이나 필드는 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93765-119">This can be a static value or an expression that refers to an object within the report, but it cannot refer to any report items or fields.</span></span> <span data-ttu-id="93765-120">기본적으로 **값** 에는 보고서 매개 변수를 가리키는 식이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="93765-120">By default, **Value** contains an expression that points to a report parameter.</span></span>  
  
 <span data-ttu-id="93765-121">**위쪽 화살표**</span><span class="sxs-lookup"><span data-stu-id="93765-121">**Up arrow**</span></span>  
 <span data-ttu-id="93765-122">선택한 매개 변수를 목록에서 위쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="93765-122">Move the selected parameter up in the list.</span></span>  
  
 <span data-ttu-id="93765-123">**아래쪽 화살표**</span><span class="sxs-lookup"><span data-stu-id="93765-123">**Down arrow**</span></span>  
 <span data-ttu-id="93765-124">선택한 매개 변수를 목록에서 아래쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="93765-124">Move the selected parameter down in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93765-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93765-125">See Also</span></span>  
 <span data-ttu-id="93765-126">[보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="93765-126">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="93765-127">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93765-127">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="93765-128">보고서 매개 변수의 순서 변경&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="93765-128">Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;</span></span>](../report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)  
  
  
