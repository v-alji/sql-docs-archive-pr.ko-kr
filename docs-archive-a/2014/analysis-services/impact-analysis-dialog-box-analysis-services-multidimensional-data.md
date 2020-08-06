---
title: 영향 분석 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.impactanalysisdialog.f1
ms.assetid: 208268eb-4e14-44db-9c64-6f74b776adb6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e47ab806b9bd10afc812113b69fe0849437068b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728928"
---
# <a name="impact-analysis-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="756fc-102">영향 분석 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="756fc-102">Impact Analysis Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="756fc-103">**및** 의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 영향 분석 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하면 **처리** 대화 상자에 나열된 개체를 처리하는 경우 영향을 받는 종속 개체를 식별하고 선택적으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-103">Use the **Impact Analysis** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to identify and optionally process dependent objects that are affected if the objects listed in the **Process** dialog box are processed.</span></span> <span data-ttu-id="756fc-104">**영향 분석** 대화 상자는 **처리** 대화 상자에서 **영향 분석** 을 클릭하여 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-104">You can display the **Impact Analysis** dialog box by clicking **Impact Analysis** from the **Process** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="756fc-105">두 가지 이상의 방식으로 영향을 받을 경우 한 개체가 두 번 이상 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-105">An object appears more than once if it is affected in more than one way.</span></span>  
  
## <a name="options"></a><span data-ttu-id="756fc-106">옵션</span><span class="sxs-lookup"><span data-stu-id="756fc-106">Options</span></span>  
 <span data-ttu-id="756fc-107">**개체 목록**</span><span class="sxs-lookup"><span data-stu-id="756fc-107">**Object list**</span></span>  
 <span data-ttu-id="756fc-108">종속 개체 목록을 표에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-108">Displays a list of dependent objects in a grid.</span></span> <span data-ttu-id="756fc-109">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-109">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="756fc-110">**개체 이름**</span><span class="sxs-lookup"><span data-stu-id="756fc-110">**Object Name**</span></span>  
 <span data-ttu-id="756fc-111">처리해야 하는 종속 개체의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-111">Displays the name of the dependent object that may need to be processed.</span></span> <span data-ttu-id="756fc-112">이름 왼쪽에 있는 아이콘은 개체 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-112">The icon to the left of the name indicates the object type.</span></span>  
  
 <span data-ttu-id="756fc-113">**형식**</span><span class="sxs-lookup"><span data-stu-id="756fc-113">**Type**</span></span>  
 <span data-ttu-id="756fc-114">처리해야 하는 종속 개체의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-114">Displays the type of dependent object that may need to be processed.</span></span>  
  
 <span data-ttu-id="756fc-115">**영향 유형**</span><span class="sxs-lookup"><span data-stu-id="756fc-115">**Impact Type**</span></span>  
 <span data-ttu-id="756fc-116">**처리** 대화 상자에서 개체를 처리할 경우 종속 개체에 미치는 영향을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-116">Displays the effect that processing the objects in the **Process** dialog box has on the dependent object.</span></span> <span data-ttu-id="756fc-117">다음 표에서는 처리 시 발생 가능한 영향을 나열하고 각 영향의 결과로 발생하는 경고 또는 오류를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-117">The following table lists the possible effects of processing and notes whether each one results in a warning or an error.</span></span>  
  
|<span data-ttu-id="756fc-118">영향</span><span class="sxs-lookup"><span data-stu-id="756fc-118">Impact</span></span>|<span data-ttu-id="756fc-119">메시지</span><span class="sxs-lookup"><span data-stu-id="756fc-119">Message</span></span>|  
|------------|-------------|  
|<span data-ttu-id="756fc-120">개체가 삭제됨(처리되지 않음)</span><span class="sxs-lookup"><span data-stu-id="756fc-120">Object will be cleared (unprocessed)</span></span>|<span data-ttu-id="756fc-121">경고</span><span class="sxs-lookup"><span data-stu-id="756fc-121">Warning</span></span>|  
|<span data-ttu-id="756fc-122">개체가 유효하지 않음</span><span class="sxs-lookup"><span data-stu-id="756fc-122">Object would be invalid</span></span>|<span data-ttu-id="756fc-123">오류</span><span class="sxs-lookup"><span data-stu-id="756fc-123">Error</span></span>|  
|<span data-ttu-id="756fc-124">집계가 삭제됨</span><span class="sxs-lookup"><span data-stu-id="756fc-124">Aggregation would be dropped</span></span>|<span data-ttu-id="756fc-125">경고</span><span class="sxs-lookup"><span data-stu-id="756fc-125">Warning</span></span>|  
|<span data-ttu-id="756fc-126">융통성 있는 집계가 삭제됨</span><span class="sxs-lookup"><span data-stu-id="756fc-126">Flexible aggregation would be dropped</span></span>|<span data-ttu-id="756fc-127">경고</span><span class="sxs-lookup"><span data-stu-id="756fc-127">Warning</span></span>|  
|<span data-ttu-id="756fc-128">인덱스가 삭제됨</span><span class="sxs-lookup"><span data-stu-id="756fc-128">Indexes will be dropped</span></span>|<span data-ttu-id="756fc-129">경고</span><span class="sxs-lookup"><span data-stu-id="756fc-129">Warning</span></span>|  
|<span data-ttu-id="756fc-130">자식이 아닌 개체가 처리됨</span><span class="sxs-lookup"><span data-stu-id="756fc-130">Non-child object will be processed</span></span>|<span data-ttu-id="756fc-131">경고</span><span class="sxs-lookup"><span data-stu-id="756fc-131">Warning</span></span>|  
  
 <span data-ttu-id="756fc-132">**개체 처리**</span><span class="sxs-lookup"><span data-stu-id="756fc-132">**Process Object**</span></span>  
 <span data-ttu-id="756fc-133">처리 작업으로 처리할 종속 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-133">Select the dependent objects that you want to process with the processing operation.</span></span> <span data-ttu-id="756fc-134">선택하지 않은 종속 개체는 처리 작업이 완료된 후 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-134">Dependent objects that are not selected must be processed after the processing operation is finished.</span></span> <span data-ttu-id="756fc-135">그렇지 않으면 해당 개체를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="756fc-135">Otherwise, they cannot be used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="756fc-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="756fc-136">See Also</span></span>  
 <span data-ttu-id="756fc-137">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="756fc-137">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="756fc-138">처리 대화 상자 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="756fc-138">Process Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
