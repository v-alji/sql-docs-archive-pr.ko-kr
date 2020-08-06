---
title: 보고서 또는 입력란에 대한 로캘 설정(Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- locales [Reporting Services]
ms.assetid: df115b01-184b-47f0-b5ec-0ad965ff9bee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb2b0cbd6e4216138520834216358ee455729386
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647434"
---
# <a name="set-the-locale-for-a-report-or-text-box-reporting-services"></a><span data-ttu-id="f61c0-102">보고서 또는 입력란에 대한 로캘 설정(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="f61c0-102">Set the Locale for a Report or Text Box (Reporting Services)</span></span>
  <span data-ttu-id="f61c0-103">보고서 또는 입력란의 **Language** 속성에는 날짜, 통화 또는 숫자 값과 같이 언어 및 국가에 따라 다른 보고서 데이터를 표시하기 위한 기본 형식을 결정하는 로캘 설정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-103">The **Language** property on a report or a text box contains the locale setting, which determines the default formats for displaying report data that differ by language and region, for example, date, currency, or number values.</span></span> <span data-ttu-id="f61c0-104">입력란의 **Language** 속성은 보고서의 **Language** 속성을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-104">The **Language** property on a text box overrides the **Language** property on the report.</span></span> <span data-ttu-id="f61c0-105">**Language**에 값을 지정하지 않을 경우 Reporting Services는 게시된 보고서에 대해서는 보고서 서버의 운영 체제 로캘을 사용하고 보고서 미리 보기에 대해서는 보고서 작성 컴퓨터의 로캘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-105">If no value is specified for **Language**, Reporting Services uses the locale of the operating system on the report server for published reports or of the report authoring computer for report preview.</span></span>  
  
 <span data-ttu-id="f61c0-106">HTML 보고서의 경우 보고서 또는 입력란의 **Language** 속성에 대한 식에 기본 제공 필드 User!Language를 사용하여 기본 **Language** 값을 재정의하고 브라우저 클라이언트의 HTTP 헤더로 지정된 언어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-106">For HTML reports, you can override the default **Language** value and use the language specified by the HTTP header of the browser client by using the built-in field User!Language in an expression for the **Language** property of a report or a text box.</span></span>  
  
 <span data-ttu-id="f61c0-107">보고서의 **Language** 속성을 URL로 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-107">You can also specify the **Language** property for a report in a URL.</span></span> <span data-ttu-id="f61c0-108">자세한 내용은 [URL에 보고서 매개 변수 언어 설정](../set-the-language-for-report-parameters-in-a-url.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f61c0-108">For more information, see [Set the Language for Report Parameters in a URL](../set-the-language-for-report-parameters-in-a-url.md).</span></span>  
  
### <a name="to-set-the-locale-for-a-report"></a><span data-ttu-id="f61c0-109">보고서에 대한 로캘을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="f61c0-109">To set the locale for a report</span></span>  
  
1.  <span data-ttu-id="f61c0-110">디자인 뷰에서 보고서 디자인 화면 바깥쪽을 클릭하여 보고서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-110">In Design view, click outside the report design surface to select the report.</span></span>  
  
2.  <span data-ttu-id="f61c0-111">속성 창의 **Language** 속성에서 보고서에 사용할 언어를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-111">In the Properties pane, for the **Language** property, type or select the language that you want to use for the report.</span></span>  
  
### <a name="to-set-the-locale-for-a-text-box"></a><span data-ttu-id="f61c0-112">입력란에 대한 로캘을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="f61c0-112">To set the locale for a text box</span></span>  
  
1.  <span data-ttu-id="f61c0-113">디자인 뷰에서 로캘 설정을 적용할 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-113">In Design view, select the text box to which you want to apply the locale settings.</span></span>  
  
2.  <span data-ttu-id="f61c0-114">속성 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-114">In the Properties pane, do the following:</span></span>  
  
    -   <span data-ttu-id="f61c0-115">**Calendar** 속성에서 날짜에 사용할 달력을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-115">For the **Calendar** property, type or select the calendar that you want to use for dates.</span></span>  
  
    -   <span data-ttu-id="f61c0-116">**Direction** 속성에서 텍스트의 방향을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-116">For the **Direction** property, type or select the direction in which the text is written.</span></span>  
  
    -   <span data-ttu-id="f61c0-117">**Language** 속성에서 입력란에 사용할 언어를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-117">For the **Language** property, type or select the language that you want to use for the text box.</span></span> <span data-ttu-id="f61c0-118">이 값은 보고서의 **Language** 속성을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-118">This value overrides the **Language** property for the Report.</span></span>  
  
    -   <span data-ttu-id="f61c0-119">**NumeralLanguage** 속성에서 입력란의 숫자에 사용할 형식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-119">For the **NumeralLanguage** property, type or select the format to use for numbers in the text box.</span></span>  
  
    -   <span data-ttu-id="f61c0-120">**NumeralVariant** 속성에서 입력란의 숫자에 사용할 형식의 변형을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-120">For the **NumeralVariant** property, type or select the variant of the format to use for numbers in the text box.</span></span>  
  
    -   <span data-ttu-id="f61c0-121">**UnicodeBiDi** 속성에서 입력란에 사용할 양방향 포함 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f61c0-121">For the **UnicodeBiDi** property, select the level of bidirectional embedding to use in the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61c0-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f61c0-122">See Also</span></span>  
 [<span data-ttu-id="f61c0-123">보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f61c0-123">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
