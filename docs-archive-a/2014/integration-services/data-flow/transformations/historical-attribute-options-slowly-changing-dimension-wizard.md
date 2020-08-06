---
title: 기록 특성 옵션(느린 변경 차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.histattriboption.f1
ms.assetid: a176ec66-ec39-4c99-99d1-c1afa8450e1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad005d6b8f80973abeb47dd881ef02b669d7b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659575"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a><span data-ttu-id="8870f-102">기록 특성 옵션(느린 변경 차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="8870f-102">Historical Attribute Options (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="8870f-103">**기록 특성 옵션** 대화 상자를 사용하여 시작 및 종료 날짜별로 기록 특성을 표시하거나 이 용도로 특별히 만든 열에 기록 특성을 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8870f-103">Use the **Historical Attributes Options** dialog box to show historical attributes by start and end dates, or to record historical attributes in a column specially created for this purpose.</span></span>  
  
 <span data-ttu-id="8870f-104">이 마법사에 대한 자세한 내용은 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8870f-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8870f-105">옵션</span><span class="sxs-lookup"><span data-stu-id="8870f-105">Options</span></span>  
 <span data-ttu-id="8870f-106">**단일 열을 사용하여 현재 및 만료 레코드 표시**</span><span class="sxs-lookup"><span data-stu-id="8870f-106">**Use a single column to show current and expired records**</span></span>  
 <span data-ttu-id="8870f-107">단일 열을 사용하여 기록 특성의 상태를 기록하도록 선택한 경우 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8870f-107">If you choose to use a single column to record the status of historical attributes, the following options are available:</span></span>  
  
|<span data-ttu-id="8870f-108">옵션</span><span class="sxs-lookup"><span data-stu-id="8870f-108">Option</span></span>|<span data-ttu-id="8870f-109">Description</span><span class="sxs-lookup"><span data-stu-id="8870f-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8870f-110">**현재 레코드 표시 열**</span><span class="sxs-lookup"><span data-stu-id="8870f-110">**Column to indicate current record**</span></span>|<span data-ttu-id="8870f-111">현재 레코드를 표시할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8870f-111">Select a column in which to indicate the current record.</span></span>|  
|<span data-ttu-id="8870f-112">**현재 값**</span><span class="sxs-lookup"><span data-stu-id="8870f-112">**Value when current**</span></span>|<span data-ttu-id="8870f-113">**True** 또는 **현재** 를 사용하여 현재 레코드인지 여부를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8870f-113">Use either **True** or **Current** to show whether the record is current.</span></span>|  
|<span data-ttu-id="8870f-114">**만료 값**</span><span class="sxs-lookup"><span data-stu-id="8870f-114">**Expiration value**</span></span>|<span data-ttu-id="8870f-115">**False** 또는 **만료됨** 을 사용하여 레코드가 기록 값인지 여부를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8870f-115">Use either **False** or **Expired** to show whether the record is a historical value.</span></span>|  
  
 <span data-ttu-id="8870f-116">**시작 및 종료 날짜를 사용하여 현재 및 만료 레코드 식별**</span><span class="sxs-lookup"><span data-stu-id="8870f-116">**Use start and end dates to identify current and expired records**</span></span>  
 <span data-ttu-id="8870f-117">이 옵션의 차원 테이블에는 날짜 열이 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8870f-117">The dimension table for this option must include a date column.</span></span> <span data-ttu-id="8870f-118">시작 및 종료 날짜별로 기록 특성을 표시하도록 선택한 경우 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8870f-118">If you choose to show historical attributes by start and end dates, the following options are available:</span></span>  
  
|<span data-ttu-id="8870f-119">옵션</span><span class="sxs-lookup"><span data-stu-id="8870f-119">Option</span></span>|<span data-ttu-id="8870f-120">Description</span><span class="sxs-lookup"><span data-stu-id="8870f-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8870f-121">**시작 날짜 열**</span><span class="sxs-lookup"><span data-stu-id="8870f-121">**Start date column**</span></span>|<span data-ttu-id="8870f-122">시작 날짜를 포함할 차원 테이블의 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8870f-122">Select the column in the dimension table to contain the start date.</span></span>|  
|<span data-ttu-id="8870f-123">**종료 날짜 열**</span><span class="sxs-lookup"><span data-stu-id="8870f-123">**End date column**</span></span>|<span data-ttu-id="8870f-124">종료 날짜를 포함할 차원 테이블의 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8870f-124">Select the column in the dimension table to contain the end date.</span></span>|  
|<span data-ttu-id="8870f-125">**날짜 값 설정 변수**</span><span class="sxs-lookup"><span data-stu-id="8870f-125">**Variable to set date values**</span></span>|<span data-ttu-id="8870f-126">목록에서 날짜 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8870f-126">Select a date variable from the list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8870f-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8870f-127">See Also</span></span>  
 [<span data-ttu-id="8870f-128">느린 변경 차원 마법사를 사용하여 출력 구성</span><span class="sxs-lookup"><span data-stu-id="8870f-128">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
