---
title: 보고서에 계기 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 45da4fef-2b02-40e1-977c-f8f80d87155e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7125080d95e9c7b882df8d715cce5c6cf8aa6344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738007"
---
# <a name="add-a-gauge-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="6c746-102">보고서에 계기 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6c746-102">Add a Gauge to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6c746-103">시각적 형식으로 데이터를 요약하려는 경우 계기 데이터 영역을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-103">When you want to summarize data in a visual format, you can use a Gauge data region.</span></span> <span data-ttu-id="6c746-104">디자인 화면에 계기 데이터 영역을 추가한 후에는 보고서 데이터 세트 필드를 계기의 데이터 창으로 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-104">After you add a Gauge data region to the design surface, you can drag report dataset fields to a data pane on the gauge.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-gauge-to-your-report"></a><span data-ttu-id="6c746-105">보고서에 계기를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="6c746-105">To add a gauge to your report</span></span>  
  
1.  <span data-ttu-id="6c746-106">보고서를 만들거나 기존 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-106">Create a report or open an existing report.</span></span>  
  
2.  <span data-ttu-id="6c746-107">삽입 탭에서 계기를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-107">On the Insert tab, double-click Gauge.</span></span> <span data-ttu-id="6c746-108">**계기 유형 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-108">The **Select Gauge Type** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="6c746-109">추가할 계기 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-109">Select the type of gauge you want to add.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c746-110">차트와 달리 계기에는 선형과 방사형이라는 두 가지 유형만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-110">Unlike Chart, Gauge has only two types: linear and radial.</span></span> <span data-ttu-id="6c746-111">**계기 유형 선택** 대화 상자의 사용 가능한 계기는 이 두 유형의 계기에 대한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-111">The available gauges in the **Select a Gauge Type** dialog box are templates for these two types of gauges.</span></span> <span data-ttu-id="6c746-112">따라서 보고서에 계기를 추가한 후에는 계기 유형을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-112">For this reason, you cannot change the gauge type after you add the gauge to your report.</span></span> <span data-ttu-id="6c746-113">계기 유형을 변경하려면 계기를 삭제한 다음 다시 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-113">You must delete and re-add a gauge to change its type.</span></span>  
  
     <span data-ttu-id="6c746-114">보고서에 데이터 원본 및 데이터 세트가 없으면 **데이터 원본 속성** 대화 상자가 열려 데이터 원본과 데이터 세트를 만드는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-114">If the report has no data source and dataset the **Data Source Properties** dialog box opens and takes you through the steps to create both.</span></span> <span data-ttu-id="6c746-115">자세한 내용은 [데이터 연결이 나 데이터 원본 &#40;보고서 작성기 및 SSRS&#41;추가 및 확인 ](../report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6c746-115">For more information see, [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](../report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
     <span data-ttu-id="6c746-116">보고서에 데이터 원본은 있지만 데이터 세트가 없는 경우에는 **데이터 세트 속성** 대화 상자가 열려 데이터 세트를 만드는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-116">If the report has a data source, but no dataset the **Dataset Properties** dialog box opens and takes you through the steps to create one.</span></span> <span data-ttu-id="6c746-117">자세한 내용은 [공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;](../report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c746-117">For more information, see [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="6c746-118">계기를 클릭하여 데이터 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-118">Click the gauge to display the data pane.</span></span> <span data-ttu-id="6c746-119">기본적으로 계기에는 하나의 값에 해당하는 하나의 포인터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-119">By default, a gauge has one pointer corresponding to one value.</span></span> <span data-ttu-id="6c746-120">하지만 포인터를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-120">You can add additional pointers.</span></span>  
  
5.  <span data-ttu-id="6c746-121">데이터 세트의 필드 하나를 데이터 필드 끌어 놓기 영역에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-121">Add one field from the dataset to the data field drop-zone.</span></span> <span data-ttu-id="6c746-122">필드를 하나만 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-122">You can add only one field.</span></span> <span data-ttu-id="6c746-123">여러 필드를 표시하려면 각 필드에 하나씩 추가 포인터를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-123">If you want to display multiple fields, you must add additional pointers, one for each field.</span></span>  
  
     <span data-ttu-id="6c746-124">계기 눈금을 마우스 오른쪽 단추로 클릭하고 **눈금 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-124">Right-click the gauge scale, and select **Scale Properties**.</span></span> <span data-ttu-id="6c746-125">눈금의 **최소값** 및 **최대값** 에 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c746-125">Type a value for the **Minimum** and **Maximum** of the scale.</span></span> <span data-ttu-id="6c746-126">자세한 내용은 [계기의 최소값 또는 최대값 설정&#40;보고서 작성기 및 SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c746-126">For more information, see [Set a Minimum or Maximum on a Gauge &#40;Report Builder and SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c746-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c746-127">See Also</span></span>  
 <span data-ttu-id="6c746-128">[중첩된 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6c746-128">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6c746-129">계기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6c746-129">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
