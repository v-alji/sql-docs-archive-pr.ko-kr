---
title: 식 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 16f414bfad47ae92681de50eb576a6ac2cb3f5fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729055"
---
# <a name="add-an-expression-report-builder-and-ssrs"></a><span data-ttu-id="4e7c8-102">식 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="4e7c8-102">Add an Expression (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4e7c8-103">식은 보고서 항목 속성, 필터, 그룹, 정렬 순서, 연결 문자열 및 매개 변수 값을 정의하기 위해 보고서 전체에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-103">Expressions are used throughout a report for defining report item properties, filters, groups, sort order, connection strings, and parameter values.</span></span> <span data-ttu-id="4e7c8-104">식은 등호(=)로 시작하며 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]으로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-104">Expressions begin with an equal sign (=) and are written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="4e7c8-105">이러한 식은 보고서 처리기에 의해 런타임에 평가됩니다. 보고서 처리기는 평가 결과를 보고서 레이아웃 요소와 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-105">They are evaluated at run time by the report processor, which combines the evaluation result with report layout elements.</span></span>  
  
 <span data-ttu-id="4e7c8-106">식은 간단하거나 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-106">Expressions can be simple or complex.</span></span> <span data-ttu-id="4e7c8-107">간단한 식은 기본 제공 컬렉션의 단일 항목을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-107">Simple expression refer to a single item in a built-in collection.</span></span> <span data-ttu-id="4e7c8-108">복잡한 식에는 상수, 연산자, 전역 컬렉션 항목 및 함수 호출이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-108">Complex expressions can contain constants, operators, global collection items, and function calls.</span></span> <span data-ttu-id="4e7c8-109">자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-109">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-expression-to-a-text-box"></a><span data-ttu-id="4e7c8-110">입력란에 식을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="4e7c8-110">To add an expression to a text box</span></span>  
  
-   <span data-ttu-id="4e7c8-111">**디자인** 뷰에서 식을 추가할 디자인 화면의 입력란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-111">In **Design** view, click the text box on the design surface to which you want to add an expression.</span></span>  
  
    -   <span data-ttu-id="4e7c8-112">간단한 식의 경우 식에 대한 표시 텍스트를 입력란에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-112">For a simple expression, type the display text for the expression in the text box.</span></span> <span data-ttu-id="4e7c8-113">예를 들어 데이터 세트 필드 Sales의 경우 `[Sales]`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-113">For example, for the dataset field Sales, type `[Sales]`.</span></span>  
  
    -   <span data-ttu-id="4e7c8-114">복잡한 식의 경우 입력란을 마우스 오른쪽 단추로 클릭하고 **식**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-114">For a complex expression, right-click the text box, and select **Expression**.</span></span> <span data-ttu-id="4e7c8-115">**식** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-115">The **Expression** dialog box opens.</span></span> <span data-ttu-id="4e7c8-116">식 창에서 '=' 뒤에 식을 입력하거나 대화형으로 만든 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-116">Type or interactively create your expression after the '=' in the expression pane, and then click OK.</span></span>  
  
         <span data-ttu-id="4e7c8-117">식이 디자인 화면에 `<<Expr>>`로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4e7c8-117">The expression appears on the design surface as `<<Expr>>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7c8-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e7c8-118">See Also</span></span>  
 <span data-ttu-id="4e7c8-119">[텍스트 및 자리 표시자 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e7c8-119">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4e7c8-120">[입력란&#40;보고서 작성기 및 SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e7c8-120">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4e7c8-121">[보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e7c8-121">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4e7c8-122">[필터 수식 예&#40;보고서 작성기 및 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e7c8-122">[Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4e7c8-123">[그룹 식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e7c8-123">[Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4e7c8-124">[식 대화 상자&#40;보고서 작성기&#41;](../expression-dialog-box-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4e7c8-124">[Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md) </span></span>  
 <span data-ttu-id="4e7c8-125">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4e7c8-125">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4e7c8-126">보고서에 코드 추가&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4e7c8-126">Add Code to a Report &#40;SSRS&#41;</span></span>](add-code-to-a-report-ssrs.md)  
  
  
