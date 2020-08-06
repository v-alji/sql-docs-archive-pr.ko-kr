---
title: 입력란(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10134"
- sql12.rtp.rptdesigner.textproperties.general.f1
- "10120"
- sql12.rtp.rptdesigner.textboxproperties.general.f1
ms.assetid: df49e4e3-f279-4c63-a03b-b70c095f4ba2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3bc9d9d645fe2a966197af9059eb90c64ce3954
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650642"
---
# <a name="text-boxes-report-builder-and-ssrs"></a><span data-ttu-id="85336-102">입력란(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="85336-102">Text Boxes (Report Builder and SSRS)</span></span>
  <span data-ttu-id="85336-103">일반적으로 입력란은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office PowerPoint 같이 화면상에서 텍스트가 들어 있는 독립 실행형 상자로 인식되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-103">When you think of a text box, you probably think of a stand-alone box containing text on a surface like [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office PowerPoint.</span></span> <span data-ttu-id="85336-104">보고서 작성기에도 이와 같은 입력란이 있으며, 여기에는 제목, 설명 및 레이블이나 식 기반의 동적 텍스트와 같은 리터럴 텍스트를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-104">In Report Builder, some text boxes are like that, and they can display literal text for titles, descriptions, and labels, or dynamic text based on expressions.</span></span> <span data-ttu-id="85336-105">그러나 테이블 또는 행렬(테이블릭스 데이터 영역)의 모든 셀에는 보고서의 독립 실행형 입력란과 같은 방법으로 서식을 지정할 수 있는 입력란도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-105">But every cell in a table or matrix (a tablix data region) also contains a text box, which can be formatted in the same way as stand-alone text boxes in your report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85336-106">보고서 데이터 세트 필드 값을 직접 보고서 디자인 화면이나 보고서 디자인 화면의 입력란으로 끌어서 놓으면 보고서를 실행할 때 결과 집합의 첫 번째 값만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="85336-106">If you drag a report dataset field value directly to the report design surface, or to a text box on the report design surface, you only see the first value in the result set when you run the report.</span></span> <span data-ttu-id="85336-107">필드에 대한 모든 값을 보려면 필드를 테이블 또는 행렬의 셀로 끌어 놓아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85336-107">To see all the values for a field, you must drag the field to a cell in a table or matrix.</span></span> <span data-ttu-id="85336-108">이렇게 하면 보고서를 실행할 때 해당 필드의 모든 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="85336-108">That way, when you run the report, you will see all the values in that field.</span></span>  
  
 <span data-ttu-id="85336-109">자유 형식 레이아웃으로 반복 입력란을 표시하려면 입력란을 목록 데이터 영역에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="85336-109">To show repeating text in a free-form layout, place a text box in a list data region.</span></span> <span data-ttu-id="85336-110">여러 값에 대해 이 형식을 반복하려면 목록을 사용합니다. 예를 들어 고객 송장 양식은 각 고객에 대해 한 번씩 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="85336-110">Use a list when you want to repeat a form for multiple values, for example, a customer invoice form repeated once for each customer.</span></span> <span data-ttu-id="85336-111">자세한 내용은 [목록 &#40;보고서 작성기 및 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="85336-111">For more information, see [Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="85336-112">입력란 레이아웃 및 마지막 입력란 아래 공백을 제어하려면 사각형 컨테이너를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="85336-112">Use a rectangle container when you want to control the text box layout and white space below the last text box.</span></span> <span data-ttu-id="85336-113">자세한 내용은 [사각형 및 선&#40;보고서 작성기 및 SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85336-113">For more information, see [Rectangles and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="85336-114">입력란의 식은 리터럴 텍스트를 포함하거나, 데이터베이스의 필드를 가리키거나, 데이터를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-114">The expressions in a text box can contain literal text, point to a field in the database, or calculate data.</span></span> <span data-ttu-id="85336-115">모든 식은 자리 표시자 텍스트로 표시되므로 숫자, 색 및 기타 모양 속성 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-115">All expressions are shown as placeholder text so that you can format numbers, colors, and other appearance properties.</span></span> <span data-ttu-id="85336-116">또한 같은 입력란에서 자리 표시자와 리터럴 텍스트를 조합하여 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-116">You can also combine placeholders with literal text in the same text box.</span></span>  
  
 <span data-ttu-id="85336-117">여러 글꼴, 색, 스타일 및 동작을 사용하여 단일 입력란의 텍스트 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-117">You can format text in any single text box with multiple fonts, colors, styles, and actions.</span></span> <span data-ttu-id="85336-118">자세한 내용은 [텍스트 및 자리 표시자 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="85336-118">For more information, see [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="growing-and-shrinking-a-text-box"></a><a name="GrowShrinkTextBox"></a> <span data-ttu-id="85336-119">입력란 늘리기 및 줄이기</span><span class="sxs-lookup"><span data-stu-id="85336-119">Growing and Shrinking a Text Box</span></span>  
 <span data-ttu-id="85336-120">기본적으로 입력란은 고정된 크기를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="85336-120">By default, text boxes are a fixed size.</span></span> <span data-ttu-id="85336-121">입력란을 해당 내용에 따라 세로로 줄이거나 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-121">You can allow a text box to shrink or expand vertically based on its contents.</span></span> <span data-ttu-id="85336-122">자세한 내용은 [입력란을 늘리거나 줄이도록 허용&#40;보고서 작성기 및 SSRS&#41;](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="85336-122">For more information, see [Allow a Text Box to Grow or Shrink &#40;Report Builder and SSRS&#41;](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md).</span></span>  
  
## <a name="orienting-a-text-box"></a><span data-ttu-id="85336-123">입력란 방향 지정</span><span class="sxs-lookup"><span data-stu-id="85336-123">Orienting a Text Box</span></span>  
 <span data-ttu-id="85336-124">입력란 방향을 지정하면 보다 쉽게 읽을 수 있는 보고서를 만들고, 로캘별 텍스트 방향을 지원하고, 페이지 크기가 고정된 인쇄 보고서에 더 많은 열을 포함하고, 눈에 잘 띄는 그래픽을 포함하여 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-124">Orienting text boxes can help you create more readable reports, support locale-specific text orientation, fit more columns on a printed report that has fixed page size, and create reports with more graphical appeal.</span></span> <span data-ttu-id="85336-125">입력란의 방향을 가로 또는 세로로 지정하거나 270도 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-125">A text box can be oriented in different directions: horizontal, vertical, or rotated by 270 degrees.</span></span> <span data-ttu-id="85336-126">세로 옵션은 위에서 아래로 쓰는 동아시아 언어에서 가장 일반적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="85336-126">The vertical option is most commonly used for East Asian languages that are written top to bottom.</span></span> <span data-ttu-id="85336-127">대부분의 렌더러에서 세로 옵션은 문자 모양 회전 속성을 처리하므로 텍스트를 위에서 아래로 써도 문자는 누워 있는 상태로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-127">In most renderers the vertical option handles the glyph rotation property so that the text is written top to bottom, but the characters are not on their sides.</span></span> <span data-ttu-id="85336-128">그러나 기타 언어의 경우에는 세로 및 270도 옵션을 사용하면 텍스트를 쓸 때 누워 있는 상태로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="85336-128">For other languages, in the vertical and 270-degree options the text is written sideways.</span></span>  
  
 <span data-ttu-id="85336-129">리터럴 텍스트, 보고서 데이터 세트의 필드 또는 계산된 데이터가 포함된 입력란에 방향을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-129">You can apply orientation to text boxes that contain literal text, fields from a report dataset, or calculated data.</span></span> <span data-ttu-id="85336-130">입력란은 보고서 본문, 테이블이나 행렬 또는 보고서 머리글 및 바닥글에서 독립 실행형으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-130">The text box can be stand-alone in the report body, in a table or matrix, or in a report header and footer.</span></span>  
  
 <span data-ttu-id="85336-131">다음 그림에는 데이터를 월별로 그룹화하는 테이블 보고서의 세 버전이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-131">The following picture shows three versions of a table report that groups data by month.</span></span> <span data-ttu-id="85336-132">월 값이 포함된 입력란에서는 다른 입력란 방향을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="85336-132">The text box that contains the month value uses a different text box orientation.</span></span>  
  
 <span data-ttu-id="85336-133">![rs_TextBoxOrientation](../media/rs-textboxorientation.gif "rs_TextBoxOrientation")</span><span class="sxs-lookup"><span data-stu-id="85336-133">![rs_TextBoxOrientation](../media/rs-textboxorientation.gif "rs_TextBoxOrientation")</span></span>  
  
 <span data-ttu-id="85336-134">방향은 입력란에 대해 설정되며 입력란의 모든 텍스트에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="85336-134">Orientation is set on the text box and applies to all the text in the box.</span></span> <span data-ttu-id="85336-135">입력란의 일부에 대해 다른 방향을 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85336-135">You cannot specify a different orientation for parts of the text box.</span></span>  
  
 <span data-ttu-id="85336-136">텍스트 방향 변경을 빠르게 시작 하려면 [자습서: 텍스트 &#40;서식 지정 보고서 작성기&#41;](../tutorial-format-text-report-builder.md)에서 텍스트 회전 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="85336-136">To quickly get started with changing text orientation, see the section on rotating text in the [Tutorial: Format Text &#40;Report Builder&#41;](../tutorial-format-text-report-builder.md).</span></span> <span data-ttu-id="85336-137">자세한 내용은 [텍스트 상자 방향 설정 &#40;보고서 작성기 및 SSRS&#41;](set-text-box-orientation-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="85336-137">For more information, see [Set Text Box Orientation &#40;Report Builder and SSRS&#41;](set-text-box-orientation-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="85336-138">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="85336-138">How-To Topics</span></span>  
 [<span data-ttu-id="85336-139">입력란 추가, 이동 또는 삭제&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="85336-139">Add, Move, or Delete a Text Box &#40;Report Builder and SSRS&#41;</span></span>](add-move-or-delete-a-text-box-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="85336-140">입력란의 텍스트 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="85336-140">Format Text in a Text Box &#40;Report Builder and SSRS&#41;</span></span>](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="85336-141">입력란 방향 설정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="85336-141">Set Text Box Orientation &#40;Report Builder and SSRS&#41;</span></span>](set-text-box-orientation-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="85336-142">입력란을 늘리거나 줄이도록 허용&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="85336-142">Allow a Text Box to Grow or Shrink &#40;Report Builder and SSRS&#41;</span></span>](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="85336-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85336-143">See Also</span></span>  
 <span data-ttu-id="85336-144">[텍스트 및 자리 표시자 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85336-144">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="85336-145">숫자 및 날짜 서식 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="85336-145">Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;</span></span>](formatting-numbers-and-dates-report-builder-and-ssrs.md)  
  
  
