---
title: 식의 상수(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b8ae650b-0f46-4848-b62b-15f8a40751b8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d95005a04482cb03d3bb3860aea695c7e7969255
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649442"
---
# <a name="constants-in-expressions-report-builder-and-ssrs"></a><span data-ttu-id="9e05b-102">식의 상수(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9e05b-102">Constants in Expressions (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9e05b-103">상수는 리터럴 텍스트 또는 미리 정의된 텍스트로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-103">A constant consists of literal text or predefined text.</span></span> <span data-ttu-id="9e05b-104">보고서 처리기는 미리 정의된 상수에 액세스할 수 있으므로 사용자가 식에 상수를 포함하면 이러한 상수가 나타내는 값은 식이 계산되기 전에 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-104">The report processor has access to predefined constants so that when you include them in an expression, the values they represent are substituted in the expression before it is evaluated.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="literal-text"></a><span data-ttu-id="9e05b-105">리터럴 텍스트</span><span class="sxs-lookup"><span data-stu-id="9e05b-105">Literal Text</span></span>  
 <span data-ttu-id="9e05b-106">식에서 리터럴 텍스트는 큰따옴표로 묶인 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-106">In an expression, literal text is text that is in double quotation marks.</span></span> <span data-ttu-id="9e05b-107">텍스트가 식의 일부가 아닌 경우에는 큰따옴표를 사용하지 않고 입력란에 직접 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-107">You can also type text directly into a text box without double quotation marks if it is not part of an expression.</span></span> <span data-ttu-id="9e05b-108">입력란 값이 등호(=)로 시작하지 않으면 해당 텍스트는 리터럴 텍스트로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-108">If the text box value does not begin with an equal sign (=), the text is treated as literal text.</span></span> <span data-ttu-id="9e05b-109">다음 표에서는 식에 사용되는 몇 가지 리터럴 텍스트의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-109">The following table shows several examples of literal text in an expression.</span></span>  
  
|<span data-ttu-id="9e05b-110">지속적임</span><span class="sxs-lookup"><span data-stu-id="9e05b-110">Constant</span></span>|<span data-ttu-id="9e05b-111">표시 텍스트</span><span class="sxs-lookup"><span data-stu-id="9e05b-111">Display text</span></span>|<span data-ttu-id="9e05b-112">식 텍스트</span><span class="sxs-lookup"><span data-stu-id="9e05b-112">Expression text</span></span>|  
|--------------|------------------|---------------------|  
|<span data-ttu-id="9e05b-113">Report run at:</span><span class="sxs-lookup"><span data-stu-id="9e05b-113">Report run at:</span></span>|<\<Expr>>|`="Report run at: " & Globals!ExecutionTime`|  
|<span data-ttu-id="9e05b-114">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="9e05b-114">Adventure Works Cycles</span></span>|<span data-ttu-id="9e05b-115">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="9e05b-115">Adventure Works Cycles</span></span>|<span data-ttu-id="9e05b-116">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="9e05b-116">Adventure Works Cycles</span></span>|  
|<span data-ttu-id="9e05b-117">[Bracketed display text]</span><span class="sxs-lookup"><span data-stu-id="9e05b-117">[Bracketed display text]</span></span>|<span data-ttu-id="9e05b-118">\\[Bracketed display text\\]</span><span class="sxs-lookup"><span data-stu-id="9e05b-118">\\[Bracketed display text\\]</span></span>|<span data-ttu-id="9e05b-119">[Bracketed display text]</span><span class="sxs-lookup"><span data-stu-id="9e05b-119">[Bracketed display text]</span></span>|  
  
## <a name="rdl-constants"></a><span data-ttu-id="9e05b-120">RDL 상수</span><span class="sxs-lookup"><span data-stu-id="9e05b-120">RDL Constants</span></span>  
 <span data-ttu-id="9e05b-121">식에서 RDL(Report Definition Language)로 정의된 상수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-121">You can use constants defined in Report Definition Language (RDL) in an expression.</span></span> <span data-ttu-id="9e05b-122">**식** 대화 상자에서는 열거 형식이라고도 하는 특정 유효 값만 허용하는 보고서 속성에 대한 식을 만들 경우 상수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-122">In the **Expression** dialog box, constants appear when you create an expression for a report property that only accepts certain valid values, also known as enumerated types.</span></span> <span data-ttu-id="9e05b-123">다음 표에서는 두 가지 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-123">The following table shows two examples.</span></span>  
  
|<span data-ttu-id="9e05b-124">속성</span><span class="sxs-lookup"><span data-stu-id="9e05b-124">Property</span></span>|<span data-ttu-id="9e05b-125">설명</span><span class="sxs-lookup"><span data-stu-id="9e05b-125">Description</span></span>|<span data-ttu-id="9e05b-126">값</span><span class="sxs-lookup"><span data-stu-id="9e05b-126">Values</span></span>|  
|--------------|-----------------|------------|  
|<span data-ttu-id="9e05b-127">TextAlign</span><span class="sxs-lookup"><span data-stu-id="9e05b-127">TextAlign</span></span>|<span data-ttu-id="9e05b-128">입력란의 텍스트 정렬을 위한 유효한 값</span><span class="sxs-lookup"><span data-stu-id="9e05b-128">Valid values for aligning text in a text box.</span></span>|<span data-ttu-id="9e05b-129">General, Left, Center, Right</span><span class="sxs-lookup"><span data-stu-id="9e05b-129">General, Left, Center, Right</span></span>|  
|<span data-ttu-id="9e05b-130">BorderStyle</span><span class="sxs-lookup"><span data-stu-id="9e05b-130">BorderStyle</span></span>|<span data-ttu-id="9e05b-131">보고서에 추가된 선에 대한 유효한 값</span><span class="sxs-lookup"><span data-stu-id="9e05b-131">Valid values for a line added to a report.</span></span>|<span data-ttu-id="9e05b-132">Default, None, Dotted, Dashed, Solid, Double, DashDot, DashDotdot</span><span class="sxs-lookup"><span data-stu-id="9e05b-132">Default, None, Dotted, Dashed, Solid, Double, DashDot, DashDotdot</span></span>|  
  
## <a name="visual-basic-constants"></a><span data-ttu-id="9e05b-133">Visual Basic 상수</span><span class="sxs-lookup"><span data-stu-id="9e05b-133">Visual Basic Constants</span></span>  
 <span data-ttu-id="9e05b-134">식에서 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 런타임 라이브러리에 정의된 상수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-134">You can use constants defined in the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library in an expression.</span></span> <span data-ttu-id="9e05b-135">예를 들어 `DateInterval.Day` 상수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-135">For example, you can use the constant `DateInterval.Day`.</span></span> <span data-ttu-id="9e05b-136">2008년 1월 10일에 대한 다음 식은 숫자 10을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-136">The following expression for the date January 10, 2008 returns the number 10:</span></span>  
  
 `=DatePart("d",Globals!ExecutionTime)`  
  
## <a name="clr-constants"></a><span data-ttu-id="9e05b-137">CLR 상수</span><span class="sxs-lookup"><span data-stu-id="9e05b-137">CLR Constants</span></span>  
 <span data-ttu-id="9e05b-138">식에서 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR(공용 언어 런타임)에 정의된 상수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-138">You can use constants defined in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language run-time (CLR) classes in an expression.</span></span> <span data-ttu-id="9e05b-139">다음 표에서는 시스템 정의 색의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-139">The following table shows an example of a system-defined color.</span></span>  
  
|<span data-ttu-id="9e05b-140">상수</span><span class="sxs-lookup"><span data-stu-id="9e05b-140">Constant</span></span>|<span data-ttu-id="9e05b-141">설명</span><span class="sxs-lookup"><span data-stu-id="9e05b-141">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="9e05b-142">MistyRose</span><span class="sxs-lookup"><span data-stu-id="9e05b-142">MistyRose</span></span>|<span data-ttu-id="9e05b-143">배경색을 기반으로 하는 보고서 속성에 대한 식을 만드는 경우 이름으로 색을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-143">When you create an expression for a report property that is based on background color, you can specify a color by name.</span></span> <span data-ttu-id="9e05b-144">유효한 이름은 **식** 대화 상자에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e05b-144">Valid names are listed in the **Expression** dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e05b-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e05b-145">See Also</span></span>  
 <span data-ttu-id="9e05b-146">[식 대화 상자](../expression-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="9e05b-146">[Expression Dialog Box](../expression-dialog-box.md) </span></span>  
 <span data-ttu-id="9e05b-147">[식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e05b-147">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9e05b-148">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e05b-148">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9e05b-149">[식의 데이터 형식 &#40;보고서 작성기 및 SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9e05b-149">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9e05b-150">식 대화 상자&#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="9e05b-150">Expression Dialog Box &#40;Report Builder&#41;</span></span>](../expression-dialog-box-report-builder.md)  
  
  
