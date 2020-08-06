---
title: '5단원: 보고서 서식 지정(Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00f0d780e957fd9ff995fefb1d033275a7da428d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660346"
---
# <a name="lesson-5-formatting-a-report-reporting-services"></a><span data-ttu-id="a1ca8-102">Lesson 5: Formatting a Report (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="a1ca8-102">Lesson 5: Formatting a Report (Reporting Services)</span></span>
  <span data-ttu-id="a1ca8-103">이제 Sales Orders 보고서에 데이터 영역과 일부 필드를 추가했으므로 날짜 및 통화 필드와 열 머리글의 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-103">Now that you've added a data region and some fields to the Sales Orders report, you can format the date and currency fields and the column headers.</span></span>  
  
 <span data-ttu-id="a1ca8-104">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="a1ca8-104">In this topic:</span></span>  
  
-   [<span data-ttu-id="a1ca8-105">날짜 형식 지정</span><span class="sxs-lookup"><span data-stu-id="a1ca8-105">Format the Date</span></span>](#bkmk_format_date)  
  
-   [<span data-ttu-id="a1ca8-106">통화 서식 지정</span><span class="sxs-lookup"><span data-stu-id="a1ca8-106">Format the Currency</span></span>](#bkmk_format_currency)  
  
-   [<span data-ttu-id="a1ca8-107">텍스트 스타일 및 열 너비 변경</span><span class="sxs-lookup"><span data-stu-id="a1ca8-107">Change Text Style and Column Widths</span></span>](#bkmk_change_textstyle)  
  
##  <a name="format-the-date"></a><a name="bkmk_format_date"></a><span data-ttu-id="a1ca8-108">날짜 형식 지정</span><span class="sxs-lookup"><span data-stu-id="a1ca8-108">Format the Date</span></span>  
 <span data-ttu-id="a1ca8-109">기본적으로 Date 필드에 날짜 및 시간 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-109">The Date field displays date and time information by default.</span></span> <span data-ttu-id="a1ca8-110">날짜만 표시되도록 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-110">You can format it to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field"></a><span data-ttu-id="a1ca8-111">날짜 필드의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="a1ca8-111">To format a date field</span></span>  
  
1.  <span data-ttu-id="a1ca8-112">**디자인** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-112">Click the **Design** tab.</span></span>  
  
2.  <span data-ttu-id="a1ca8-113">`[Date]` 필드 식이 있는 셀을 마우스 오른쪽 단추로 클릭한 다음 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-113">Right-click the cell with the `[Date]` field expression and then click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="a1ca8-114">**숫자**를 클릭 한 다음 **범주** 필드에서를 선택 `Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-114">Click **Number**, and then in the **Category** field, select `Date`.</span></span>  
  
4.  <span data-ttu-id="a1ca8-115">**형식** 상자에서 **January 31, 2000**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-115">In the **Type** box, select **January 31, 2000**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="a1ca8-116">보고서를 미리 보기하여 `[Date]` 필드의 변경 내용을 확인하고 다시 디자인 보기로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-116">Preview the report to see the change to the `[Date]` field and then change back to design view.</span></span>  
  
##  <a name="format-the-currency"></a><a name="bkmk_format_currency"></a><span data-ttu-id="a1ca8-117">통화 서식 지정</span><span class="sxs-lookup"><span data-stu-id="a1ca8-117">Format the Currency</span></span>  
 <span data-ttu-id="a1ca8-118">LineTotal 필드에는 일반 숫자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-118">The LineTotal field displays a general number.</span></span> <span data-ttu-id="a1ca8-119">서식을 지정하여 숫자가 통화로 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-119">Format it to display the number as currency.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="a1ca8-120">통화 필드의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="a1ca8-120">To format a currency field</span></span>  
  
1.  <span data-ttu-id="a1ca8-121">`[LineTotal]` 필드 식이 있는 셀을 마우스 오른쪽 단추로 클릭한 다음 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-121">Right-click the cell with the `[LineTotal]` field expression and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="a1ca8-122">**숫자**를 클릭한 다음 **범주** 필드에서 **통화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-122">Click **Number**, and in the **Category** field, select **Currency**.</span></span>  
  
3.  <span data-ttu-id="a1ca8-123">국가별 설정이 영어(미국)인 경우 기본값은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-123">If your regional setting is English (United States), the defaults should be:</span></span>  
  
    -   <span data-ttu-id="a1ca8-124">**소수 자릿수: 2**</span><span class="sxs-lookup"><span data-stu-id="a1ca8-124">**Decimal places: 2**</span></span>  
  
    -   <span data-ttu-id="a1ca8-125">**음수: ($12345.00)**</span><span class="sxs-lookup"><span data-stu-id="a1ca8-125">**Negative numbers: ($12345.00)**</span></span>  
  
    -   <span data-ttu-id="a1ca8-126">**기호: $ 영어(미국)**</span><span class="sxs-lookup"><span data-stu-id="a1ca8-126">**Symbol: $ English (United States)**</span></span>  
  
4.  <span data-ttu-id="a1ca8-127">**천 단위 구분 기호(,) 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-127">Select **Use 1000 separator (,)**.</span></span>  
  
     <span data-ttu-id="a1ca8-128">샘플 텍스트가 **$12,345.00**이면 설정이 올바른 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-128">If the sample text is:**$12,345.00**, then your settings are correct.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="a1ca8-129">보고서를 미리 보기하여 `[LineTotal]` 필드의 변경 내용을 확인하고 다시 디자인 보기로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-129">Preview the report to see the change to the `[LineTotal]` field and then change back to design view.</span></span>  
  
##  <a name="change-text-style-and-column-widths"></a><a name="bkmk_change_textstyle"></a><span data-ttu-id="a1ca8-130">텍스트 스타일 및 열 너비 변경</span><span class="sxs-lookup"><span data-stu-id="a1ca8-130">Change Text Style and Column Widths</span></span>  
 <span data-ttu-id="a1ca8-131">보고서 데이터의 행과 구분하기 위해 머리글 행의 서식 지정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-131">You can also change the formatting of the header row to differentiate it from the rows of data in the report.</span></span> <span data-ttu-id="a1ca8-132">마지막으로 열의 너비를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-132">Lastly, you will adjust the widths of the columns.</span></span>  
  
#### <a name="to-format-header-rows-and-table-columns"></a><span data-ttu-id="a1ca8-133">머리글 행 및 테이블 너비의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="a1ca8-133">To format header rows and table columns</span></span>  
  
1.  <span data-ttu-id="a1ca8-134">테이블을 클릭하여 열 핸들과 행 핸들이 테이블 위와 옆에 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-134">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="a1ca8-135">![디자인, 머리글 행과 정보 행이 있는 테이블](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "디자인, 머리글 행과 정보 행이 있는 테이블")</span><span class="sxs-lookup"><span data-stu-id="a1ca8-135">![Design, Table with header row and detail row](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "Design, Table with header row and detail row")</span></span>  
  
     <span data-ttu-id="a1ca8-136">테이블 위쪽 및 옆쪽을 따라 표시되는 회색 막대는 행 및 열 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-136">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
2.  <span data-ttu-id="a1ca8-137">열 핸들 사이의 선에 커서를 두면 커서가 양방향 화살표로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-137">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="a1ca8-138">이 상태에서 열을 끌어 크기를 원하는 대로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-138">Drag the columns to the size you want.</span></span>  
  
3.  <span data-ttu-id="a1ca8-139">열 머리글 레이블이 있는 행을 선택하고 **서식** 메뉴에서 **글꼴** 을 가리킨 다음 **굵게**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-139">Select the row containing column header labels and from the **Format** menu, point to **Font** and then click **Bold**.</span></span>  
  
4.  <span data-ttu-id="a1ca8-140">보고서를 미리 보려면 **미리 보기** 탭을 클릭 합니다. 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-140">To preview your report, click the **Preview** tab. It should look something like this:</span></span>  
  
     <span data-ttu-id="a1ca8-141">![열 머리글이 굵게 설정된 테이블의 미리 보기](../../2014/tutorials/media/rs-basictabledetailsformattedpreview.gif "열 머리글이 굵게 설정된 테이블의 미리 보기")</span><span class="sxs-lookup"><span data-stu-id="a1ca8-141">![Preview of table with bold column headers](../../2014/tutorials/media/rs-basictabledetailsformattedpreview.gif "Preview of table with bold column headers")</span></span>  
  
5.  <span data-ttu-id="a1ca8-142">**파일** 메뉴에서 **모두 저장** 을 클릭하여 보고서를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-142">On the **File** menu, click **Save All** to save the report.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a1ca8-143">다음 단계</span><span class="sxs-lookup"><span data-stu-id="a1ca8-143">Next Steps</span></span>  
 <span data-ttu-id="a1ca8-144">열 머리글과 날짜 및 통화 값의 서식을 성공적으로 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-144">You have successfully formatted column headers and date and currency values.</span></span> <span data-ttu-id="a1ca8-145">그 다음은 보고서에 그룹화 및 합계를 추가하는 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-145">Next, you will add grouping and totals to your report.</span></span> <span data-ttu-id="a1ca8-146">[6단원: 그룹화 및 합계 추가&#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1ca8-146">See [Lesson 6: Adding Grouping and Totals &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ca8-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1ca8-147">See Also</span></span>  
 <span data-ttu-id="a1ca8-148">[숫자 및 날짜 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a1ca8-148">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a1ca8-149">렌더링 동작&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a1ca8-149">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](report-design/rendering-behaviors-report-builder-and-ssrs.md)  
  
  
