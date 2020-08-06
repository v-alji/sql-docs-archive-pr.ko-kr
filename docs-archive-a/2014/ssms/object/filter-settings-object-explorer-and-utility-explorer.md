---
title: 필터 설정(개체 탐색기 및 유틸리티 탐색기) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.filtersettings.f1
- sql12.swb.common.filtersettings.f1
ms.assetid: 4aab04bc-e1ab-4d4b-ab74-b287fc805bc2
author: stevestein
ms.author: sstein
ms.openlocfilehash: c31fbcbef9cbab86a7bd3ab7b2fae21e626aaa59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638511"
---
# <a name="filter-settings-object-explorer-and-utility-explorer"></a><span data-ttu-id="5d083-102">필터 설정(개체 탐색기 및 유틸리티 탐색기)</span><span class="sxs-lookup"><span data-stu-id="5d083-102">Filter Settings (Object Explorer and Utility Explorer)</span></span>
  <span data-ttu-id="5d083-103">이 대화 상자를 사용하여 필터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-103">Use this dialog box to specify a filter.</span></span> <span data-ttu-id="5d083-104">필터를 사용하면 특정 조건에 맞는 항목만 표시하도록 개체 탐색기 및 유틸리티 탐색기를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-104">A filter allows you to configure Object Explorer and Utility Explorer to display only items that meet specific criteria.</span></span> <span data-ttu-id="5d083-105">예를 들어 필터를 사용하여 이름에 "Maintenance"라는 단어가 포함된 작업만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-105">For example, you can use a filter to show only jobs with names that contain the word "Maintenance."</span></span> <span data-ttu-id="5d083-106">**필터 설정** 대화 상자의 머리글에는 서버 이름이나 데이터베이스 이름이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-106">The header for the **Filter Settings** dialog box contains the name of the server, and it may contain the name of the database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="5d083-107">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="5d083-107">UI element list</span></span>  
 <span data-ttu-id="5d083-108">**속성**</span><span class="sxs-lookup"><span data-stu-id="5d083-108">**Property**</span></span>  
 <span data-ttu-id="5d083-109">필터링할 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-109">Displays the property to filter on.</span></span>  
  
 <span data-ttu-id="5d083-110">**연산자**</span><span class="sxs-lookup"><span data-stu-id="5d083-110">**Operator**</span></span>  
 <span data-ttu-id="5d083-111">필터가 속성에 값을 적용하는 방식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-111">Select the way that the filter applies the value to the property.</span></span> <span data-ttu-id="5d083-112">옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-112">There are the following options:</span></span>  
  
-   <span data-ttu-id="5d083-113">**같음**</span><span class="sxs-lookup"><span data-stu-id="5d083-113">**Equals**</span></span>  
  
     <span data-ttu-id="5d083-114">필터는 속성과 해당 값이 정확히 일치하는 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-114">The filter shows items where the property and the value are an exact match.</span></span>  
  
-   <span data-ttu-id="5d083-115">**포함**</span><span class="sxs-lookup"><span data-stu-id="5d083-115">**Contains**</span></span>  
  
     <span data-ttu-id="5d083-116">필터는 속성에 해당 값이 포함된 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-116">The filter shows items where the property contains the value.</span></span> <span data-ttu-id="5d083-117">속성에 다른 텍스트가 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-117">The property may contain other text.</span></span>  
  
-   <span data-ttu-id="5d083-118">**포함하지 않음**</span><span class="sxs-lookup"><span data-stu-id="5d083-118">**Does not contain**</span></span>  
  
     <span data-ttu-id="5d083-119">필터는 속성에 해당 값이 포함되지 않은 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-119">The filter shows items that where the property does not contain the value.</span></span>  
  
-   <span data-ttu-id="5d083-120">**보다 작음**</span><span class="sxs-lookup"><span data-stu-id="5d083-120">**Less than**</span></span>  
  
     <span data-ttu-id="5d083-121">이 필터는 날짜에 사용할 수 있으며 해당 날짜가 제공된 값보다 이전인 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-121">Available for dates, this filter shows items whose date is before the value provided.</span></span>  
  
-   <span data-ttu-id="5d083-122">**작거나 같음**</span><span class="sxs-lookup"><span data-stu-id="5d083-122">**Less than or equal**</span></span>  
  
     <span data-ttu-id="5d083-123">이 필터는 날짜에 사용할 수 있으며 해당 날짜가 제공된 값과 같거나 이전인 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-123">Available for dates, this filter shows items whose date contains or is before the value provided.</span></span>  
  
-   <span data-ttu-id="5d083-124">**보다 큼**</span><span class="sxs-lookup"><span data-stu-id="5d083-124">**Greater than**</span></span>  
  
     <span data-ttu-id="5d083-125">이 필터는 날짜에 사용할 수 있으며 해당 날짜가 제공된 값보다 이후인 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-125">Available for dates, this filter shows items whose date is after the value provided.</span></span>  
  
-   <span data-ttu-id="5d083-126">**크거나 같음**</span><span class="sxs-lookup"><span data-stu-id="5d083-126">**Greater than or equal**</span></span>  
  
     <span data-ttu-id="5d083-127">이 필터는 날짜에 사용할 수 있으며 해당 날짜가 제공된 값과 같거나 이후인 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-127">Available for dates, this filter shows items whose date contains or is after the value provided.</span></span>  
  
-   <span data-ttu-id="5d083-128">**사이**</span><span class="sxs-lookup"><span data-stu-id="5d083-128">**Between**</span></span>  
  
     <span data-ttu-id="5d083-129">이 필터는 날짜에 사용할 수 있으며 해당 날짜가 제공된 두 값 사이에 있는 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-129">Available for dates, this filter shows items whose date is between two dates provided.</span></span> <span data-ttu-id="5d083-130">**사이** 를 선택하고 Tab 키를 누르면 두 번째 날짜를 입력할 다른 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-130">Select **Between** and press TAB to add another row allowing entry of the second date.</span></span>  
  
-   <span data-ttu-id="5d083-131">**사이에 있지 않음**</span><span class="sxs-lookup"><span data-stu-id="5d083-131">**Not between**</span></span>  
  
     <span data-ttu-id="5d083-132">이 필터는 날짜에 사용할 수 있으며 해당 날짜가 제공된 두 날짜보다 이전이거나 이후인 항목을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-132">Available for dates, this filter shows items whose date is before or after two dates provided.</span></span> <span data-ttu-id="5d083-133">**사이에 있지 않음** 을 선택하고 **연산자** 열에서 Tab 키를 누르면 두 번째 날짜를 입력할 다른 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-133">Select **Not Between** and tab out of the **Operator** column to add another row allowing entry of the second date.</span></span>  
  
 <span data-ttu-id="5d083-134">**값**</span><span class="sxs-lookup"><span data-stu-id="5d083-134">**Value**</span></span>  
 <span data-ttu-id="5d083-135">속성과 비교할 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-135">Type the value to compare to the property.</span></span> <span data-ttu-id="5d083-136">날짜의 경우 아래쪽 화살표를 클릭하면 날짜를 선택할 수 있는 달력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-136">For dates, click the down arrow to show a calendar for selecting the date.</span></span>  
  
 <span data-ttu-id="5d083-137">**필터 지우기**</span><span class="sxs-lookup"><span data-stu-id="5d083-137">**Clear Filter**</span></span>  
 <span data-ttu-id="5d083-138">현재 필터 설정을 모두 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5d083-138">Removes all current filter settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d083-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d083-139">See Also</span></span>  
 <span data-ttu-id="5d083-140">[SQL Server Management Studio 사용](../sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="5d083-140">[Use SQL Server Management Studio](../sql-server-management-studio-ssms.md) </span></span>  
 [<span data-ttu-id="5d083-141">SQL Server 유틸리티 기능 및 태스크</span><span class="sxs-lookup"><span data-stu-id="5d083-141">SQL Server Utility Features and Tasks</span></span>](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
