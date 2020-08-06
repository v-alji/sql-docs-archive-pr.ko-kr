---
title: 보고서로 HTML 가져오기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dd0410ea-8839-4e8c-9944-8cdfe5465591
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f978e67c67556184012db6b809e4f5754f2374c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730175"
---
# <a name="importing-html-into-a-report-report-builder-and-ssrs"></a><span data-ttu-id="f9ed9-102">보고서로 HTML 가져오기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f9ed9-102">Importing HTML into a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f9ed9-103">입력란을 사용하면 데이터 세트의 필드에서 검색한 HTML 서식의 텍스트를 보고서에 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-103">You can use a text box to insert HTML-formatted text that you have retrieved from a field in your dataset into a report.</span></span> <span data-ttu-id="f9ed9-104">텍스트는 올바른 형식의 HTML로 평가되는 단순 또는 복합 식에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-104">The text can come from any simple or complex expression that evaluates to correctly formatted HTML.</span></span> <span data-ttu-id="f9ed9-105">서식이 지정된 텍스트는 PDF를 비롯한 모든 지원되는 출력 형식으로 렌더링될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-105">Formatted text can be rendered to all supported output formats, including PDF.</span></span>  
  
 <span data-ttu-id="f9ed9-106">![rs_HTMLFormatting](../media/rs-htmlformatting.gif "rs_HTMLFormatting")</span><span class="sxs-lookup"><span data-stu-id="f9ed9-106">![rs_HTMLFormatting](../media/rs-htmlformatting.gif "rs_HTMLFormatting")</span></span>  
  
 <span data-ttu-id="f9ed9-107">다음 그림에서는 보고서 디자인 뷰의 HTML 서식을 사용한 텍스트와 보고서가 실행될 때 렌더링되는 것과 동일한 텍스트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-107">This illustration shows text with HTML formatting in report design view, and the same text as it is rendered when the report is run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9ed9-108">HTML 태그가 들어 있는 텍스트를 가져오면 입력란에서 항상 데이터 구문을 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-108">When you import text that contains HTML markup, the data must always be parsed by the text box first.</span></span> <span data-ttu-id="f9ed9-109">HTML 태그의 하위 집합만 지원되기 때문에 렌더링된 보고서에 표시되는 HTML이 원래 HTML과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-109">Because only a subset of HTML tags is supported, the HTML that is shown in the rendered report may differ from your original HTML.</span></span>  
  
 <span data-ttu-id="f9ed9-110">빠르게 시작하려면 [자습서: 텍스트 서식 지정&#40;보고서 작성기&#41;](../tutorial-format-text-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-110">To quickly get started, see [Tutorial: Format Text &#40;Report Builder&#41;](../tutorial-format-text-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="supported-html-tags"></a><span data-ttu-id="f9ed9-111">지원되는 HTML 태그</span><span class="sxs-lookup"><span data-stu-id="f9ed9-111">Supported HTML Tags</span></span>  
 <span data-ttu-id="f9ed9-112">다음은 자리 표시자 텍스트로 정의될 때 HTML로 렌더링될 전체 태그 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-112">The following is a complete list of tags that will render as HTML when defined as placeholder text:</span></span>  
  
-   <span data-ttu-id="f9ed9-113">머리글, 스타일 및 블록 요소: \<H{n}> , \<DIV> , \<SPAN> , \<P> ,\<LI></span><span class="sxs-lookup"><span data-stu-id="f9ed9-113">Header, style and block elements: \<H{n}>, \<DIV>, \<SPAN>,\<P>, \<LI></span></span>  
  
 <span data-ttu-id="f9ed9-114">나머지 모든 HTML 태그는 보고서를 처리하는 동안 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-114">Any other HTML markup tags will be ignored during report processing.</span></span> <span data-ttu-id="f9ed9-115">자리 표시자 텍스트에 있는 식이 나타내는 HTML의 형식이 잘못된 경우에는 자리 표시자가 일반 텍스트로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-115">If the HTML represented by the expression in the placeholder text is not well formed, the placeholder is rendered as plain text.</span></span> <span data-ttu-id="f9ed9-116">모든 HTML 태그는 대소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-116">All HTML tags are case-insensitive.</span></span>  
  
 <span data-ttu-id="f9ed9-117">입력란에 있는 텍스트가 한 텍스트 블록만 포함하는 경우 블록 요소를 정의하는 자리 표시자의 HTML은 올바르게 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-117">If the text in your text box contains only one block of text, any HTML in the placeholder that defines block elements will render correctly.</span></span> <span data-ttu-id="f9ed9-118">그러나 입력란에 여러 텍스트 블록이 있는 경우에는 HTML 태그가 무시되고 텍스트 구조가 텍스트 블록에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-118">However, if the text box has multiple blocks of text, the HTML tags are ignored and the structure of the text is defined by the blocks of text.</span></span>  
  
 <span data-ttu-id="f9ed9-119">텍스트에 태그가 여러 개 정의되어 있고 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에서 HTML과 기존 보고서 제약 조건 사이에 충돌을 발견한 경우에는 가장 안쪽의 HTML 태그만 HTML로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-119">If more than one tag is defined for text, and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] detects a conflict between the HTML and existing report constraints, only the innermost HTML tag will be treated as HTML.</span></span>  
  
 <span data-ttu-id="f9ed9-120">목록 처리 태그를 사용할 경우 모든 글머리 기호 및 번호 접두사의 글꼴 및 스타일이 Arial black으로 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-120">When using the list handling tags, the font and style of all bullets and number prefixes will be fixed to Arial black.</span></span>  
  
 <span data-ttu-id="f9ed9-121">자세한 내용은 [보고서에 HTML 추가&#40;보고서 작성기 및 SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-121">For more information, see [Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
## <a name="limitations-of-cascading-style-sheet-attributes"></a><span data-ttu-id="f9ed9-122">CSS 특성의 제한</span><span class="sxs-lookup"><span data-stu-id="f9ed9-122">Limitations of Cascading Style Sheet Attributes</span></span>  
 <span data-ttu-id="f9ed9-123">CSS 특성을 사용할 때는 기본적인 태그 집합만 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-123">When using cascading style sheet (CSS) attributes, only a basic set of tags are defined.</span></span> <span data-ttu-id="f9ed9-124">다음은 지원되는 특성의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-124">The following is a list of attributes that are supported:</span></span>  
  
-   <span data-ttu-id="f9ed9-125">text-align, text-indent</span><span class="sxs-lookup"><span data-stu-id="f9ed9-125">text-align, text-indent</span></span>  
  
-   <span data-ttu-id="f9ed9-126">font-family</span><span class="sxs-lookup"><span data-stu-id="f9ed9-126">font-family</span></span>  
  
-   <span data-ttu-id="f9ed9-127">font-size</span><span class="sxs-lookup"><span data-stu-id="f9ed9-127">font-size</span></span>  
  
    -   <span data-ttu-id="f9ed9-128">절대 CSS 길이 단위의 유효한 RDL 크기 값만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-128">Only valid RDL size values, in absolute CSS length units are supported.</span></span> <span data-ttu-id="f9ed9-129">지원되는 단위는 in, cm, mm, pt, pc 입니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-129">Supported units are: in, cm, mm, pt, pc.</span></span>  
  
    -   <span data-ttu-id="f9ed9-130">상대 CSS 길이 단위는 무시되고 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-130">Relative CSS length units are ignored and not supported.</span></span> <span data-ttu-id="f9ed9-131">지원되지 않는 단위에는 em, ex, px, %, rem이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-131">Unsupported units include em, ex, px,%,rem.</span></span>  
  
-   <span data-ttu-id="f9ed9-132">색</span><span class="sxs-lookup"><span data-stu-id="f9ed9-132">color</span></span>  
  
-   <span data-ttu-id="f9ed9-133">padding, padding-bottom, padding-top, padding-right, padding-left</span><span class="sxs-lookup"><span data-stu-id="f9ed9-133">padding, padding-bottom, padding-top, padding-right, padding-left</span></span>  
  
-   <span data-ttu-id="f9ed9-134">font-weight</span><span class="sxs-lookup"><span data-stu-id="f9ed9-134">font-weight</span></span>  
  
 <span data-ttu-id="f9ed9-135">다음은 CSS를 사용할 때 고려해야 할 몇 가지 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-135">Here are some considerations for using CSS:</span></span>  
  
-   <span data-ttu-id="f9ed9-136">형식이 잘못된 CSS 값은 형식이 잘못된 HTML과 마찬가지로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-136">Malformed CSS values are ignored in the same way as malformed HTML.</span></span>  
  
-   <span data-ttu-id="f9ed9-137">같은 태그에 특성 및 CSS 스타일 특성이 모두 있는 경우에는 CSS 속성의 우선 순위가 더 높습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-137">When both attribute and CSS style attributes exist in the same tag, the CSS property has a higher precedence.</span></span> <span data-ttu-id="f9ed9-138">예를 들어 텍스트가 이면 텍스트 **\<p style="text-align: right" align="left">** 맞춤 특성만 적용 되 고 텍스트는 오른쪽 맞춤 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-138">For example, if your text is **\<p style="text-align: right" align="left">**, only the text-align attribute will be applied and the text will be right-aligned.</span></span>  
  
-   <span data-ttu-id="f9ed9-139">특성 및 CSS 스타일에 대해 속성이 여러 번 지정된 경우에는 속성의 마지막 인스턴스만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-139">For attributes and CSS styles, if a property is specified more than once, only the last instance of the property is applied.</span></span> <span data-ttu-id="f9ed9-140">예를 들어 텍스트가 이면 **\<p align="left" align="right">** 텍스트가 오른쪽 맞춤 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ed9-140">For example, if your text is **\<p align="left" align="right">**, the text will be right-aligned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ed9-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9ed9-141">See Also</span></span>  
 [<span data-ttu-id="f9ed9-142">HTML로 렌더링&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f9ed9-142">Rendering to HTML &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/rendering-to-html-report-builder-and-ssrs.md)  
  
  
