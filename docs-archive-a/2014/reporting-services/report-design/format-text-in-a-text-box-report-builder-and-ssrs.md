---
title: 입력란의 텍스트 서식 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df0794b5-96b0-4034-bd17-1be7f31e29db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 522bc420f77b2e5e9d2163c28d3d688b7c47883c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649382"
---
# <a name="format-text-in-a-text-box-report-builder-and-ssrs"></a><span data-ttu-id="d93fa-102">입력란의 텍스트 서식 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d93fa-102">Format Text in a Text Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d93fa-103">입력란에 있는 텍스트 부분의 서식을 개별적으로 지정하고 한 입력란 내에 자리 표시자 텍스트와 정적 텍스트를 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-103">You can format any part of the text within a text box independently, and mix placeholder text and static text in one text box.</span></span> <span data-ttu-id="d93fa-104">여러 서식을 함께 사용하고 자리 표시자 텍스트를 추가하는 이 기능을 통해 보고서의 텍스트에 대한 편지 병합 또는 템플릿을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-104">This ability to mix formats and add placeholder text enables you to create mail merges or templates for text in your report.</span></span> <span data-ttu-id="d93fa-105">자리 표시자를 사용하여 모든 식을 개별적으로 정의하고 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-105">Any expression can be defined and formatted separately using a placeholder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-combine-multiple-formats-in-a-text-box"></a><span data-ttu-id="d93fa-106">입력란에서 여러 서식을 함께 사용하려면</span><span class="sxs-lookup"><span data-stu-id="d93fa-106">To combine multiple formats in a text box</span></span>  
  
1.  <span data-ttu-id="d93fa-107">**삽입** 탭에서 **입력란**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-107">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="d93fa-108">디자인 화면을 클릭한 다음 끌어 원하는 크기의 상자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-108">Click the design surface, and then drag to create a box that is the size you want.</span></span>  
  
2.  <span data-ttu-id="d93fa-109">입력란 내에서 서식을 지정할 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-109">Inside the text box, select the text you want to format.</span></span>  
  
3.  <span data-ttu-id="d93fa-110">선택한 텍스트를 마우스 오른쪽 단추로 클릭하고 **텍스트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-110">Right-click the selected text, and click **Text Properties**.</span></span>  
  
4.  <span data-ttu-id="d93fa-111">서식 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-111">Set formatting options.</span></span> <span data-ttu-id="d93fa-112">예를 들어 **일반** 탭에서 다음과 같이 작업합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-112">For example, on the **General** tab:</span></span>  
  
    -   <span data-ttu-id="d93fa-113">**도구 설명** 도구 설명을 반환하는 식 또는 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-113">**Tooltip** Type text or an expression that evaluates to a ToolTip.</span></span> <span data-ttu-id="d93fa-114">보고서의 항목 위에 포인터를 놓으면 도구 설명이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-114">The ToolTip appears when the user pauses the pointer over the item in a report</span></span>  
  
    -   <span data-ttu-id="d93fa-115">**태그 형식** 선택한 텍스트를 렌더링할 방식을 나타내기 위한 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-115">**Markup type** Select an option to indicate how the selected text will be rendered:</span></span>  
  
         <span data-ttu-id="d93fa-116">**일반 텍스트** 선택한 텍스트를 단순 텍스트로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-116">**Plain Text** Display the selected text as simple text.</span></span> <span data-ttu-id="d93fa-117">HTML은 리터럴 텍스트로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-117">HTML will be treated as literal text.</span></span>  
  
         <span data-ttu-id="d93fa-118">**HTML**  선택한 텍스트를 HTML로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-118">**HTML**  Display the selected text as HTML.</span></span> <span data-ttu-id="d93fa-119">자리 표시자의 식 값에 유효한 HTML 태그가 포함된 경우 이러한 태그는 HTML로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-119">If the expression value of the placeholder contains valid HTML tags, these tags will be rendered as HTML.</span></span> <span data-ttu-id="d93fa-120">자세한 내용은 [보고서로 HTML 가져오기&#40;보고서 작성기 및 SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d93fa-120">For more information, see [Importing HTML into a Report &#40;Report Builder and SSRS&#41;](importing-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
5.  <span data-ttu-id="d93fa-121">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-121">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="d93fa-122">서식을 지정할 나머지 텍스트에 대해 2~5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-122">Repeat steps 2 through 5 for the remaining text you want to format.</span></span>  
  
### <a name="to-format-text-and-placeholders-differently-in-the-same-text-box"></a><span data-ttu-id="d93fa-123">같은 입력란에서 텍스트 및 자리 표시자의 서식을 다르게 지정하려면</span><span class="sxs-lookup"><span data-stu-id="d93fa-123">To format text and placeholders differently in the same text box</span></span>  
  
1.  <span data-ttu-id="d93fa-124">**삽입** 탭에서 **목록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-124">On the **Insert** tab, click **List**.</span></span> <span data-ttu-id="d93fa-125">디자인 화면을 클릭한 다음 끌어 원하는 크기의 상자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-125">Click the design surface, and then drag to create a box that is the size you want.</span></span> <span data-ttu-id="d93fa-126">**데이터 세트 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-126">The **Dataset Properties** dialog box opens.</span></span> <span data-ttu-id="d93fa-127">보고서에 포함된 데이터 세트나 공유 데이터 세트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-127">You can use a shared dataset or a dataset embedded in your report.</span></span> <span data-ttu-id="d93fa-128">자세한 내용은 [데이터 세트 속성 대화 상자, 쿼리&#40;보고서 작성기&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md) 또는 [데이터 세트 속성 대화 상자, 쿼리](../dataset-properties-dialog-box-query.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d93fa-128">For more information, click [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../report-data/dataset-properties-dialog-box-query-report-builder.md) or [Dataset Properties Dialog Box, Query](../dataset-properties-dialog-box-query.md).</span></span>  
  
2.  <span data-ttu-id="d93fa-129">**삽입** 탭에서 **입력란**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-129">On the **Insert** tab, click **Text Box**.</span></span> <span data-ttu-id="d93fa-130">목록을 클릭한 다음 끌어 원하는 크기의 상자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-130">Click in the list, and then drag to create a box that is the size you want.</span></span>  
  
3.  <span data-ttu-id="d93fa-131">텍스트 상자에 **My Field**와 같은 레이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-131">Type a label in the text box - for example, **My Field**:.</span></span>  
  
4.  <span data-ttu-id="d93fa-132">데이터 세트의 필드를 입력란으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-132">Drag a field from your dataset into the text box.</span></span> <span data-ttu-id="d93fa-133">해당 필드에 대한 자리 표시자가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-133">A placeholder is created for your field.</span></span>  
  
5.  <span data-ttu-id="d93fa-134">기본 서식의 경우 자리 표시자 텍스트를 선택한 후 **홈** 탭의 **글꼴** 그룹에서 서식 옵션 중 하나를 클릭합니다. 예를 들어 **굵게** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-134">For basic formatting, select the placeholder text and then click one of the formatting options in the **Font** group on the **Home** tab. For example, click the **Bold** button.</span></span>  
  
     <span data-ttu-id="d93fa-135">다른 서식 옵션을 보려면 자리 표시자 텍스트를 마우스 오른쪽 단추로 클릭한 다음 **자리 표시자 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-135">For more formatting options, right-click the placeholder text, and then click **Placeholder Properties**.</span></span>  
  
6.  <span data-ttu-id="d93fa-136">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-136">Click **OK**.</span></span> <span data-ttu-id="d93fa-137">보고서 디자인 뷰의 입력란에 "**My Field**: [*FieldName*]"을 포함해야 합니다. 여기서 *FieldName* 은 필드 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-137">In report design view, the text box should contain "**My Field**: [*FieldName*]", where *FieldName* is the name of your field.</span></span>  
  
7.  <span data-ttu-id="d93fa-138">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-138">Click **Run**.</span></span>  
  
 <span data-ttu-id="d93fa-139">목록은 필드의 각 값에 대해 한 번씩 반복되고 매번 *FieldName* 은 데이터 세트에 있는 해당 필드의 값으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="d93fa-139">The list repeats one time for every value in the field, and the *FieldName* placeholder is replaced each time by the value of that field in the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d93fa-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d93fa-140">See Also</span></span>  
 <span data-ttu-id="d93fa-141">[입력란&#40;보고서 작성기 및 SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d93fa-141">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d93fa-142">[텍스트 및 자리 표시자 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d93fa-142">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d93fa-143">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d93fa-143">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d93fa-144">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d93fa-144">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d93fa-145">[보고서에 HTML 추가&#40;보고서 작성기 및 SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d93fa-145">[Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d93fa-146">[&#40;보고서 작성기 및 SSRS를 나열&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d93fa-146">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d93fa-147">[숫자 및 날짜 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d93fa-147">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d93fa-148">자리 표시자 속성 대화 상자, 일반&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d93fa-148">Placeholder Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../placeholder-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
