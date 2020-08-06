---
title: 식 예(보고서 작성기 및 SSRS) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/08/2017
ms.openlocfilehash: c7ef06143dafdb5034d0f6202fdc16bc51f74ca8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649404"
---
# <a name="expression-examples-report-builder-and-ssrs"></a><span data-ttu-id="73ba2-102">식 예(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="73ba2-102">Expression Examples (Report Builder and SSRS)</span></span>

<span data-ttu-id="73ba2-103">식은 보고서에서 내용과 보고서 모양을 제어하는 데 자주 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-103">Expressions are used frequently in reports to control content and report appearance.</span></span> <span data-ttu-id="73ba2-104">식은에서 작성 되며 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 기본 제공 함수 사용자 지정 코드, 보고서 및 그룹 변수 및 사용자 정의 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-104">Expressions are written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], and can use built-in functions custom code, report and group variables, and user-defined variables.</span></span> <span data-ttu-id="73ba2-105">식은 등호(=)로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-105">Expressions begin with an equal sign (=).</span></span> <span data-ttu-id="73ba2-106">식 편집기와 포함할 수 있는 참조 형식에 대한 자세한 내용은 [보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) 및 [식 추가&#40;보고서 작성기 및 SSRS&#41;](add-an-expression-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-106">For more information about the expression editor and the types of references that you can include, see [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md), and [Add an Expression &#40;Report Builder and SSRS&#41;](add-an-expression-report-builder-and-ssrs.md).</span></span>  

> [!IMPORTANT]  
>  <span data-ttu-id="73ba2-107">RDL 샌드박싱 기능이 설정되면 보고서를 게시할 때 특정 형식 및 멤버만 식 텍스트에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-107">When RDL Sandboxing is enabled, only certain types and members can be used in expression text at report publish time.</span></span> <span data-ttu-id="73ba2-108">자세한 내용은 [Enable and Disable RDL Sandboxing](../enable-and-disable-rdl-sandboxing.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-108">For more information, see [Enable and Disable RDL Sandboxing](../enable-and-disable-rdl-sandboxing.md).</span></span>  

<span data-ttu-id="73ba2-109">이 항목에서는 보고서의 일반적인 태스크에 사용할 수 있는 식 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-109">This topic provides examples of expressions that can be used for common tasks in a report.</span></span>  

-   <span data-ttu-id="73ba2-110">[Visual Basic 함수](#VisualBasicFunctions) 날짜, 문자열, 변환 및 조건부 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 함수 예</span><span class="sxs-lookup"><span data-stu-id="73ba2-110">[Visual Basic Functions](#VisualBasicFunctions) Examples for date, string, conversion and conditional [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions.</span></span>  

-   <span data-ttu-id="73ba2-111">[보고서 함수](#ReportFunctions) 집계 및 기타 기본 제공 보고서 함수 예</span><span class="sxs-lookup"><span data-stu-id="73ba2-111">[Report Functions](#ReportFunctions) Examples for aggregates and other built-in report functions.</span></span>  

-   <span data-ttu-id="73ba2-112">[보고서 데이터 모양](#AppearanceofReportData) 보고서 모양 변경 예</span><span class="sxs-lookup"><span data-stu-id="73ba2-112">[Appearance of Report Data](#AppearanceofReportData) Examples for changing the appearance of a report.</span></span>  

-   <span data-ttu-id="73ba2-113">[속성](#Properties) 형식 또는 표시 유형을 제어하는 보고서 항목 속성 설정 예</span><span class="sxs-lookup"><span data-stu-id="73ba2-113">[Properties](#Properties) Examples for setting report item properties to control format or visibility.</span></span>  

-   <span data-ttu-id="73ba2-114">[매개 변수](#Parameters) 식에서의 매개 변수 사용 예</span><span class="sxs-lookup"><span data-stu-id="73ba2-114">[Parameters](#Parameters) Examples for using parameters in an expression.</span></span>  

-   <span data-ttu-id="73ba2-115">[사용자 지정 코드](#CustomCode) 포함된 사용자 지정 코드 예</span><span class="sxs-lookup"><span data-stu-id="73ba2-115">[Custom Code](#CustomCode) Examples of embedded custom code.</span></span>  

<span data-ttu-id="73ba2-116">특정 용도에 맞는 식 예는 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="73ba2-116">For expression examples for specific uses, see the following topics:</span></span>  

-   [<span data-ttu-id="73ba2-117">그룹 식 예&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="73ba2-117">Group Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="73ba2-118">필터 수식 예&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="73ba2-118">Filter Equation Examples &#40;Report Builder and SSRS&#41;</span></span>](filter-equation-examples-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="73ba2-119">일반적으로 사용되는 필터&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="73ba2-119">Commonly Used Filters &#40;Report Builder and SSRS&#41;</span></span>](commonly-used-filters-report-builder-and-ssrs.md)  

-   [<span data-ttu-id="73ba2-120">보고서 및 그룹 변수 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="73ba2-120">Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-report-and-group-variables-references-report-builder.md)  

<span data-ttu-id="73ba2-121">간단한 식과 복잡한 식, 식을 사용할 수 있는 위치 및 식에 포함할 수 있는 참조 유형에 대한 자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-121">For more information about simple and complex expressions, where you can use expressions, and the types of references that you can include in an expression, see topics under [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="73ba2-122">집계 계산을 위해 식이 계산되는 컨텍스트에 대한 자세한 내용은 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-122">For more information about the context in which expressions are evaluated for calculating aggregates, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  

<span data-ttu-id="73ba2-123">이 항목의 식 예제에서도 사용하는 함수와 연산자 중 상당수를 사용하는 식을 작성하는 방법을 보고서 작성의 맥락에서 알아보려면 [자습서: 식 소개](../tutorial-introducing-expressions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-123">To learn how to write expressions that use many of the functions and operators also used by expression examples in this topic, but in the context of writing a report, see [Tutorial: Introducing Expressions](../tutorial-introducing-expressions.md).</span></span>  

<span data-ttu-id="73ba2-124">식 편집기에서는 기본 제공 함수를 계층적으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-124">The expression editor includes a hierarchical view of built-in functions.</span></span> <span data-ttu-id="73ba2-125">함수를 선택하면 값 창에 코드 예가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-125">When you select the function, a code example appears in the Values pane.</span></span> <span data-ttu-id="73ba2-126">자세한 내용은 [식 대화](../expression-dialog-box.md) 상자 또는 [식 대화 상자 &#40;보고서 작성기&#41;](../expression-dialog-box-report-builder.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-126">For more information, see the [Expression Dialog Box](../expression-dialog-box.md) or [Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md).</span></span>  

## <a name="functions"></a><span data-ttu-id="73ba2-127">함수</span><span class="sxs-lookup"><span data-stu-id="73ba2-127">Functions</span></span>  

<span data-ttu-id="73ba2-128">보고서의 여러 식에는 함수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-128">Many expressions in a report contain functions.</span></span> <span data-ttu-id="73ba2-129">이러한 함수를 사용하여 데이터의 형식을 지정하고, 논리를 적용하고, 보고서 메타데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-129">You can format data, apply logic, and access report metadata using these functions.</span></span> <span data-ttu-id="73ba2-130">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 런타임 라이브러리와 <xref:System.Convert> 및 네임 스페이스의 함수를 사용 하는 식을 작성할 수 있습니다 <xref:System.Math> .</span><span class="sxs-lookup"><span data-stu-id="73ba2-130">You can write expressions that use functions from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library, and from the <xref:System.Convert> and <xref:System.Math> namespaces.</span></span> <span data-ttu-id="73ba2-131">다른 어셈블리 또는 사용자 지정 코드에서 함수에 대한 참조를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-131">You can add references to functions from other assemblies or custom code.</span></span> <span data-ttu-id="73ba2-132">을 포함 하 여의 클래스를 사용할 수도 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Text.RegularExpressions> .</span><span class="sxs-lookup"><span data-stu-id="73ba2-132">You can also use classes from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], including <xref:System.Text.RegularExpressions>.</span></span>  

###  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> <span data-ttu-id="73ba2-133">Visual Basic 함수</span><span class="sxs-lookup"><span data-stu-id="73ba2-133">Visual Basic Functions</span></span>  
<span data-ttu-id="73ba2-134">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 함수를 사용하여 입력란에 표시되는 데이터나 매개 변수, 속성 또는 보고서의 다른 영역에 사용되는 데이터를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-134">You can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to manipulate the data that is displayed in text boxes or that is used for parameters, properties, or other areas of the report.</span></span> <span data-ttu-id="73ba2-135">이 섹션에서는 이러한 함수 중 몇 가지를 보여 주는 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-135">This section provides examples demonstrating some of these functions.</span></span> <span data-ttu-id="73ba2-136">자세한 내용은 MSDN의 [Visual Basic 런타임 라이브러리 멤버](https://go.microsoft.com/fwlink/?LinkId=198941) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-136">For more information, see [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) on MSDN.</span></span>  

<span data-ttu-id="73ba2-137">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 에서는 특정 데이터 형식 등에 대한 다양한 사용자 지정 형식 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-137">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides many custom format options, for example, for specific date formats.</span></span> <span data-ttu-id="73ba2-138">자세한 내용은 MSDN의 [형식 지정](https://go.microsoft.com/fwlink/?LinkId=112024) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="73ba2-138">For more information, see [Formatting Types](https://go.microsoft.com/fwlink/?LinkId=112024) on MSDN.</span></span>  

#### <a name="math-functions"></a><span data-ttu-id="73ba2-139">수학 함수</span><span class="sxs-lookup"><span data-stu-id="73ba2-139">Math Functions</span></span>  

-   <span data-ttu-id="73ba2-140">`Round` 함수는 숫자를 가장 가까운 정수로 반올림하거나 내림하려는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-140">The `Round` function is useful to round numbers to the nearest integer.</span></span> <span data-ttu-id="73ba2-141">다음 식에서는 1.3을 1로 반내림합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-141">The following expression rounds a 1.3 to 1:</span></span>  

```  
= Round(1.3)  
```  

<span data-ttu-id="73ba2-142">Excel의 `MRound` 함수와 같이 지정한 배수로 값을 반올림하거나 내림하는 식을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-142">You can also write an expression to round a value to a multiple that you specify, similar to the `MRound` function in Excel.</span></span> <span data-ttu-id="73ba2-143">정수를 만드는 계수로 값을 곱해 숫자를 반올림하거나 내림한 다음 동일한 계수로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-143">Multiply the value by a factor that creates an integer, round the number, and then divide by the same factor.</span></span> <span data-ttu-id="73ba2-144">예를 들어 1.3을 .2의 배수 중 가장 가까운 배수인 1.4로 반올림하려면 다음 식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-144">For example, to round 1.3 to the nearest multiple of .2 (1.4), use the following expression:</span></span>  

```  
= Round(1.3*5)/5  
```  

####  <a name="date-functions"></a><a name="DateFunctions"></a><span data-ttu-id="73ba2-145">날짜 함수</span><span class="sxs-lookup"><span data-stu-id="73ba2-145">Date Functions</span></span>  

-   <span data-ttu-id="73ba2-146">`Today` 함수는 현재 날짜를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-146">The `Today` function provides the current date.</span></span> <span data-ttu-id="73ba2-147">이 식은 보고서에 날짜를 표시할 경우 입력란에 사용하거나 현재 날짜를 기반으로 데이터를 필터링할 경우 매개 변수에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-147">This expression can be used in a text box to display the date on the report, or in a parameter to filter data based on the current date.</span></span>  

```  
=Today()  
```  

-   <span data-ttu-id="73ba2-148">`DateAdd` 함수는 단일 매개 변수를 기반으로 날짜 범위를 제공하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-148">The `DateAdd` function is useful for supplying a range of dates based on a single parameter.</span></span> <span data-ttu-id="73ba2-149">다음 식에서는 *StartDate*라는 매개 변수로부터 6개월 후의 날짜를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-149">The following expression provides a date that is six months after the date from a parameter named *StartDate*.</span></span>  

```  
=DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
```  

-   <span data-ttu-id="73ba2-150">`Year` 함수는 특정 날짜의 연도를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-150">The `Year` function displays the year for a particular date.</span></span> <span data-ttu-id="73ba2-151">이 함수를 사용하여 날짜를 그룹화하거나 연도를 일련의 날짜 레이블로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-151">You can use this to group dates together or to display the year as a label for a set of dates.</span></span> <span data-ttu-id="73ba2-152">이 식은 지정된 판매 주문 날짜 그룹에 대한 연도를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-152">This expression provides the year for a given group of sales order dates.</span></span> <span data-ttu-id="73ba2-153">날짜 처리에 `Month` 함수 및 다른 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-153">The `Month` function and other functions can also be used to manipulate dates.</span></span> <span data-ttu-id="73ba2-154">자세한 내용은 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-154">For more information, see the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] documentation.</span></span>  

```  
=Year(Fields!OrderDate.Value)  
```  

-   <span data-ttu-id="73ba2-155">식에서 함수를 결합하여 형식을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-155">You can combine functions in an expression to customize the format.</span></span> <span data-ttu-id="73ba2-156">다음 식에서는 월-일-연도 형식의 날짜를 월-주-주 번호 형식의 날짜로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-156">The following expression changes the format of a date in the form month-day-year to month-week-week number.</span></span> <span data-ttu-id="73ba2-157">예를 들어 12/23/2009를 12월 주 3으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-157">For example, 12/23/2009 to December Week 3:</span></span>  

```  
=Format(Fields!MyDate.Value, "MMMM") & " Week " &   
(Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
```  

<span data-ttu-id="73ba2-158">이 식을 데이터 세트에서 계산 필드로 사용할 경우 차트에서 이 식을 사용하면 각 달의 주를 기준으로 값을 집계할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-158">When used as a calculated field in a dataset, you can use this expression on a chart to aggregate values by week within each month.</span></span>  

-   <span data-ttu-id="73ba2-159">다음 식은 SellStartDate 값을 MMM-YY 형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-159">The following expression formats the SellStartDate value as MMM-YY.</span></span> <span data-ttu-id="73ba2-160">SellStartDate 필드는 datetime 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-160">SellStartDate field is a datetime data type.</span></span>  

```  
=FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
```  

-   <span data-ttu-id="73ba2-161">다음 식은 SellStartDate 값을 dd/MM/yyyy 형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-161">The following expression formats the SellStartDate value as dd/MM/yyyy.</span></span> <span data-ttu-id="73ba2-162">SellStartDate 필드는 datetime 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-162">The SellStartDate field is a datetime data type.</span></span>  

```  
=FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
```  

-   <span data-ttu-id="73ba2-163">`CDate` 함수는 값을 날짜로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-163">The `CDate` function converts the value to a date.</span></span> <span data-ttu-id="73ba2-164">`Now` 함수는 현재 날짜와 시스템에 따른 시간을 포함하는 날짜 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-164">The `Now` function returns a date value containing the current date and time according to your system.</span></span> <span data-ttu-id="73ba2-165">`DateDiff`는 두 날짜 값 사이의 시간 간격을 지정하는 Long 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-165">`DateDiff` returns a Long value specifying the number of time intervals between two Date values.</span></span>  

<span data-ttu-id="73ba2-166">다음 예제는 현재 연도의 시작 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-166">The following example displays the start date of the current year</span></span>  

```  
=DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
```  

-   <span data-ttu-id="73ba2-167">다음 예제는 현재 달을 기준으로 이전 달의 시작 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-167">The following example displays the start date for the previous month based on the current month.</span></span>  

```  
=DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
```  

-   <span data-ttu-id="73ba2-168">다음 식은 SellStartDate와 LastReceiptDate 사이의 간격 연도를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-168">The following expression generates the interval years between SellStartDate and LastReceiptDate.</span></span> <span data-ttu-id="73ba2-169">이러한 필드는 두 가지 다른 데이터 세트 즉, DataSet1 및 DataSet2에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-169">These fields are in two different datasets, DataSet1 and DataSet2.</span></span> <span data-ttu-id="73ba2-170">집계 함수인 [첫 번째 함수&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-first-function.md)는 DataSet1에 있는 SellStartDate의 첫 번째 값과 DataSet2에 있는 LastReceiptDate의 첫 번째 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-170">The [First Function &#40;Report Builder and SSRS&#41;](report-builder-functions-first-function.md), which is an aggregate function, returns the first value of SellStartDate in DataSet1 and the first value of LastReceiptDate in DataSet2.</span></span>  

```  
=DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
```  

-   <span data-ttu-id="73ba2-171">`DatePart` 함수는 주어진 날짜 값의 지정된 구성 요소를 포함하는 정수 값을 반환합니다. 다음 식은 DataSet1에 있는 SellStartDate의 첫 번째 값에 대한 연도를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-171">The `DatePart` function returns an Integer value containing the specified component of a given Date value.The following expression returns the year for the first value of the SellStartDate in DataSet1.</span></span> <span data-ttu-id="73ba2-172">보고서에 여러 개의 데이터 세트가 있으므로 데이터 세트 범위가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-172">The dataset scope is specified because there are multiple datasets in the report.</span></span>  

```  
=Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  

```  

-   <span data-ttu-id="73ba2-173">`DateSerial` 함수는 자정으로 설정된 시간 정보와 함께 지정된 년, 월, 일을 나타내는 날짜 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-173">The `DateSerial` function returns a Date value representing a specified year, month, and day, with the time information set to midnight.</span></span> <span data-ttu-id="73ba2-174">다음 예제는 현재 달을 기준으로 이전 달의 마지막 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-174">The following example displays the ending date for the prior month, based on the current month.</span></span>  

```  
=DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
```  

-   <span data-ttu-id="73ba2-175">다음 식은 사용자가 선택한 날짜 매개 변수 값을 기준으로 여러 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-175">The following expressions display various dates based on a date parameter value selected by the user.</span></span>  

|<span data-ttu-id="73ba2-176">예제 설명</span><span class="sxs-lookup"><span data-stu-id="73ba2-176">Example Description</span></span>|<span data-ttu-id="73ba2-177">예제</span><span class="sxs-lookup"><span data-stu-id="73ba2-177">Example</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="73ba2-178">어제</span><span class="sxs-lookup"><span data-stu-id="73ba2-178">Yesterday</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|<span data-ttu-id="73ba2-179">2일 전</span><span class="sxs-lookup"><span data-stu-id="73ba2-179">Two Days Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|<span data-ttu-id="73ba2-180">1개월 전</span><span class="sxs-lookup"><span data-stu-id="73ba2-180">One Month Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="73ba2-181">2개월 전</span><span class="sxs-lookup"><span data-stu-id="73ba2-181">Two Months Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="73ba2-182">1년 전</span><span class="sxs-lookup"><span data-stu-id="73ba2-182">One Year Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|<span data-ttu-id="73ba2-183">2년 전</span><span class="sxs-lookup"><span data-stu-id="73ba2-183">Two Years Ago</span></span>|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  

####  <a name="string-functions"></a><a name="StringFunctions"></a><span data-ttu-id="73ba2-184">문자열 함수</span><span class="sxs-lookup"><span data-stu-id="73ba2-184">String Functions</span></span>  

-   <span data-ttu-id="73ba2-185">연결 연산자와 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 상수를 사용하여 둘 이상의 필드를 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-185">Combine more than one field by using concatenation operators and [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] constants.</span></span> <span data-ttu-id="73ba2-186">다음 식에서는 두 필드를 같은 입력란에서 별도의 줄에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-186">The following expression returns two fields, each on a separate line in the same text box:</span></span>  

```  
=Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
```  

-   <span data-ttu-id="73ba2-187">`Format` 함수를 사용하여 문자열의 날짜와 숫자 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-187">Format dates and numbers in a string with the `Format` function.</span></span> <span data-ttu-id="73ba2-188">다음 식에서는 *StartDate* 와 *EndDate* 매개 변수의 값을 자세한 날짜 형식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-188">The following expression displays values of the *StartDate* and *EndDate* parameters in long date format:</span></span>  

```  
=Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
```  

<span data-ttu-id="73ba2-189">텍스트 상자에 날짜 또는 숫자만 있는 경우 텍스트 상자 내에서 함수 대신 텍스트 상자의 Format 속성을 사용 하 여 서식을 적용 해야 합니다 `Format` .</span><span class="sxs-lookup"><span data-stu-id="73ba2-189">If the text box contains only a date or number, you should use the Format property of the text box to apply formatting instead of the `Format` function within the text box.</span></span>  

-   <span data-ttu-id="73ba2-190">`Right`, `Len` 및 함수는 부분 문자열을 반환 하는 데 유용 합니다 `InStr` . 예를 들어 *도메인*사용자 이름만 \\ *username* 사용자 이름으로 트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-190">The `Right`, `Len`, and `InStr` functions are useful for returning a substring, for example, trimming *DOMAIN*\\*username* to just the user name.</span></span> <span data-ttu-id="73ba2-191">다음 식에서는\\User *라는 매개 변수에서 백슬래시(*) 문자의 오른쪽에 있는 문자열 부분을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-191">The following expression returns the part of the string to the right of a backslash (\\) character from a parameter named *User*:</span></span>  

```  
=Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
```  

<span data-ttu-id="73ba2-192">다음 식에서는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.String> 함수 대신 클래스의 멤버를 사용 하 여 이전 값과 동일한 값을 반환 합니다 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="73ba2-192">The following expression results in the same value as the previous one, using members of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.String> class instead of [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions:</span></span>  

```  
=Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
```  

-   <span data-ttu-id="73ba2-193">다중값 매개 변수에서 선택한 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-193">Display the selected values from a multivalue parameter.</span></span> <span data-ttu-id="73ba2-194">다음 예에서는 함수를 사용 하 여 `Join` *myselection* 매개 변수의 선택한 값을 보고서 항목에 있는 입력란의 값에 대 한 식으로 설정할 수 있는 단일 문자열에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-194">The following example uses the `Join` function to concatenate the selected values of the parameter *MySelection* into a single string that can be set as an expression for the value of a text box in a report item:</span></span>  

```  
= Join(Parameters!MySelection.Value)  
```  

<span data-ttu-id="73ba2-195">다음 예에서는 선택한 값 목록 이전의 텍스트 문자열을 표시할 뿐 아니라 위의 예와 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-195">The following example does the same as the above example, as well as displays a text string prior to the list of selected values.</span></span>  

```  
="Report for " & JOIN(Parameters!MySelection.Value, " & ")  

```  

-   <span data-ttu-id="73ba2-196">의 `Regex` 함수는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Text.RegularExpressions> 전화 번호 형식을 지정 하는 등 기존 문자열의 형식을 변경 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-196">The `Regex` functions from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] <xref:System.Text.RegularExpressions> are useful for changing the format of existing strings, for example, formatting a telephone number.</span></span> <span data-ttu-id="73ba2-197">다음 식에서는 함수를 사용 하 여 `Replace` 필드의 10 자리 전화 번호 형식을 "*nnn* - *nnn* - *nnnn*"에서 "(*nnn*) *nnn* - *nnnn*"으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-197">The following expression uses the `Replace` function to change the format of a ten-digit telephone number in a field from "*nnn*-*nnn*-*nnnn*" to "(*nnn*) *nnn*-*nnnn*":</span></span>  

```  
=System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
```  

> [!NOTE]  
>  <span data-ttu-id="73ba2-198">Fields!Phone.Value의 값에 추가 공백이 없고 <xref:System.String>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-198">Verify that the value for Fields!Phone.Value has no extra spaces and is of type <xref:System.String>.</span></span>  

#### <a name="lookup"></a><span data-ttu-id="73ba2-199">조회</span><span class="sxs-lookup"><span data-stu-id="73ba2-199">Lookup</span></span>  

-   <span data-ttu-id="73ba2-200">키 필드를 지정하면 `Lookup` 함수를 사용하여 키-값 쌍과 같이 일 대 일 관계가 있는 데이터 세트에서 값을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-200">By specifying a key field, you can use the `Lookup` function to retrieve a value from a dataset for a one-to-one relationship, for example, a key-value pair.</span></span> <span data-ttu-id="73ba2-201">일치시킬 제품 식별자가 제공된 경우 다음 식은 데이터 세트에서 제품 이름("Product")을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-201">The following expression displays the product name from a dataset ("Product"), given the product identifier to match on:</span></span>  

```  
=Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields!ProductName.Value, "Product")  
```  

#### <a name="lookupset"></a><span data-ttu-id="73ba2-202">LookupSet</span><span class="sxs-lookup"><span data-stu-id="73ba2-202">LookupSet</span></span>  

-   <span data-ttu-id="73ba2-203">키 필드를 지정하면 `LookupSet` 함수를 사용하여 일 대 다 관계가 있는 데이터 세트에서 값 집합을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-203">By specifying a key field, you can use the `LookupSet` function to retrieve a set of values from a dataset for a one-to-many relationship.</span></span> <span data-ttu-id="73ba2-204">예를 들어 한 사람이 전화 번호를 여러 개 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-204">For example, a person can have multiple telephone numbers.</span></span> <span data-ttu-id="73ba2-205">다음 예에서는 PhoneList 데이터 세트의 각 행에 개인 식별자와 전화 번호가 포함되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-205">In the following example, assume the dataset PhoneList contains a person identifier and a telephone number in each row.</span></span> <span data-ttu-id="73ba2-206">`LookupSet`은 값 배열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-206">`LookupSet` returns an array of values.</span></span> <span data-ttu-id="73ba2-207">다음 식은 반환 값을 단일 문자열로 결합하고 ContactID로 지정된 사람의 전화 번호 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-207">The following expression combines the return values into a single string and displays the list of telephone numbers for the person specified by ContactID:</span></span>  

```  
=Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
```  

####  <a name="conversion-functions"></a><a name="ConversionFunctions"></a><span data-ttu-id="73ba2-208">변환 함수</span><span class="sxs-lookup"><span data-stu-id="73ba2-208">Conversion Functions</span></span>  
<span data-ttu-id="73ba2-209">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 함수를 사용하여 필드를 한 데이터 형식에서 다른 데이터 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-209">You can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions to convert a field from the one data type to a different data type.</span></span> <span data-ttu-id="73ba2-210">필드의 기본 데이터 형식을 계산이나 텍스트 결합에 필요한 다른 데이터 형식으로 변환하는 데에 변환 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-210">Conversion functions can be used to convert the default data type for a field to the data type needed for calculations or to combine text.</span></span>  

-   <span data-ttu-id="73ba2-211">다음 식에서는 상수 500을 필터 식의 값 필드에 있는 [!INCLUDE[tsql](../../includes/tsql-md.md)] money 데이터 형식과 비교하기 위해 10진수 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-211">The following expression converts the constant 500 to type Decimal in order to compare it to a [!INCLUDE[tsql](../../includes/tsql-md.md)] money data type in the Value field for a filter expression.</span></span>  

```  
=CDec(500)  
```  

-   <span data-ttu-id="73ba2-212">다음 식에서는 다중값 매개 변수 *MySelection*에 대해 선택된 값의 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-212">The following expression displays the number of values selected for the multivalue parameter *MySelection*.</span></span>  

```  
=CStr(Parameters!MySelection.Count)  
```  

####  <a name="decision-functions"></a><a name="DecisionFunctions"></a> <span data-ttu-id="73ba2-213">의사 결정 함수</span><span class="sxs-lookup"><span data-stu-id="73ba2-213">Decision Functions</span></span>  

-   <span data-ttu-id="73ba2-214">`Iif` 함수는 식이 True인지 여부에 따라 두 값 중 하나를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-214">The `Iif` function returns one of two values depending on whether the expression is true or not.</span></span> <span data-ttu-id="73ba2-215">다음 식에서는 `Iif` 함수를 사용하여 `LineTotal` 값이 100을 초과하면 부울 값 `True`를 반환하며</span><span class="sxs-lookup"><span data-stu-id="73ba2-215">The following expression uses the `Iif` function to return a Boolean value of `True` if the value of `LineTotal` exceeds 100.</span></span> <span data-ttu-id="73ba2-216">그렇지 않으면 `False`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-216">Otherwise it returns `False`:</span></span>  

```  
=IIF(Fields!LineTotal.Value > 100, True, False)  
```  

-   <span data-ttu-id="73ba2-217">`IIF` 함수(“중첩 IIF”라고도 함)를 사용하여 `PctComplete`의 값에 따라 3개의 값 중 하나를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-217">Use multiple `IIF` functions (also known as "nested IIFs") to return one of three values depending on the value of `PctComplete`.</span></span> <span data-ttu-id="73ba2-218">다음 식을 입력란의 채우기 색에 배치하면 입력란의 값에 따라 배경색을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-218">The following expression can be placed in the fill color of a text box to change the background color depending on the value in the text box.</span></span>  

```  
=IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
```  

<span data-ttu-id="73ba2-219">값이 10 이상이면 녹색 배경을 표시하고 1에서 9 사이면 파란색 배경을, 1 미만이면 빨간색 배경을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-219">Values greater than or equal to 10 display with a green background, between 1 and 9 display with a blue background, and less than 1 display with a red background.</span></span>  

-   <span data-ttu-id="73ba2-220">같은 기능을 구현하는 다른 방법으로 `Switch` 함수를 사용하는 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-220">A different way to get the same functionality uses the `Switch` function.</span></span> <span data-ttu-id="73ba2-221">`Switch` 함수는 테스트할 조건이 3개 이상인 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-221">The `Switch` function is useful when you have three or more conditions to test.</span></span> <span data-ttu-id="73ba2-222">`Switch` 함수는 계열에서 True로 계산되는 첫 번째 식과 연결된 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-222">The `Switch` function returns the value associated with the first expression in a series that evaluates to true:</span></span>  

```  
=Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red",)  
```  

<span data-ttu-id="73ba2-223">값이 10 이상이면 녹색 배경을 표시하고 1에서 9 사이면 파란색 배경을 표시하고 1이면 노란색 배경을 표시하고 0 이하면 빨간색 배경을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-223">Values greater than or equal to 10 display with a green background, between 1 and 9 display with a blue background, equal to 1 display with a yellow background, and 0 or less display with a red background.</span></span>  

-   <span data-ttu-id="73ba2-224">`ImportantDate` 필드의 값을 테스트하여 해당 날짜가 1주 넘게 경과된 경우 "Red"를 반환하고, 그렇지 않은 경우 "Blue"를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-224">Test the value of the `ImportantDate` field and return "Red" if it is more than a week old, and "Blue" otherwise.</span></span> <span data-ttu-id="73ba2-225">이 식은 보고서 항목에 있는 입력란의 Color 속성을 제어하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-225">This expression can be used to control the Color property of a text box in a report item:</span></span>  

```  
=IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
```  

-   <span data-ttu-id="73ba2-226">`PhoneNumber` 필드의 값을 테스트하여 `null`([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]의 `Nothing`)인 경우 "No Value"를 반환하고 그렇지 않으면 전화 번호 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-226">Test the value of the `PhoneNumber` field and return "No Value" if it is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]); otherwise return the phone number value.</span></span> <span data-ttu-id="73ba2-227">이 식은 보고서 항목에 있는 입력란의 값을 제어하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-227">This expression can be used to control the value of a text box in a report item.</span></span>  

```  
=IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
```  

-   <span data-ttu-id="73ba2-228">`Department` 필드의 값을 테스트하여 하위 보고서의 이름 또는 `null`([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]의 `Nothing`)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-228">Test the value of the `Department` field and return either a subreport name or a `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="73ba2-229">이 식은 포함된 조건부 드릴스루 하위 보고서에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-229">This expression can be used for conditional drillthrough subreports.</span></span>  

```  
=IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
```  

-   <span data-ttu-id="73ba2-230">필드 값이 Null인지 여부를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-230">Test if a field value is null.</span></span> <span data-ttu-id="73ba2-231">이 식은 이미지 보고서 항목의 `Hidden` 속성을 제어하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-231">This expression can be used to control the `Hidden` property of an image report item.</span></span> <span data-ttu-id="73ba2-232">다음 예에서 [LargePhoto] 필드로 지정된 이미지는 필드의 값이 Null이 아닌 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-232">In the following example, the image specified by the field [LargePhoto] is displayed only if the value of the field is not null.</span></span>  

```  
=IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
```  

-   <span data-ttu-id="73ba2-233">`MonthName` 함수는 지정한 월의 이름을 포함하는 문자열 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-233">The `MonthName` function returns a string value containing the name of the specified month.</span></span> <span data-ttu-id="73ba2-234">다음 예제는 필드에 0 값이 포함된 경우 NA를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-234">The following example displays NA in the Month field when the field contains the value of 0.</span></span>  

```  
IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  

```  

###  <a name="report-functions"></a><a name="ReportFunctions"></a> <span data-ttu-id="73ba2-235">보고서 함수</span><span class="sxs-lookup"><span data-stu-id="73ba2-235">Report Functions</span></span>  
<span data-ttu-id="73ba2-236">식에서 보고서의 데이터를 조작하는 데 사용할 수 있는 추가 보고서 함수에 대한 참조를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-236">In an expression, you can add a reference to additional report functions that manipulate data in a report.</span></span> <span data-ttu-id="73ba2-237">이 섹션에서는 이러한 함수 중 두 가지 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-237">This section provides examples for two of these functions.</span></span> <span data-ttu-id="73ba2-238">집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;보고서 함수 및 예제에 대한 자세한 내용은 [집계 함수 참조 & #40; 보고서 작성기 및 SSRS & #41;](report-builder-functions-aggregate-functions-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-238">For more information about report functions and examples, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  

#####  <a name="sum"></a><a name="Sum"></a><span data-ttu-id="73ba2-239">총합</span><span class="sxs-lookup"><span data-stu-id="73ba2-239">Sum</span></span>  

-   <span data-ttu-id="73ba2-240">`Sum` 함수는 그룹 또는 데이터 영역에서 값의 합계를 구합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-240">The `Sum` function can total the values in a group or data region.</span></span> <span data-ttu-id="73ba2-241">이 함수는 그룹의 머리글 또는 바닥글에서 유용하게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-241">This function can be useful in the header or footer of a group.</span></span> <span data-ttu-id="73ba2-242">다음 식에서는 Order 그룹 또는 데이터 영역에 데이터의 합계를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-242">The following expression displays the sum of data in the Order group or data region:</span></span>  

```  
=Sum(Fields!LineTotal.Value, "Order")  
```  

-   <span data-ttu-id="73ba2-243">조건부 집계 계산에도 `Sum` 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-243">You can also use the `Sum` function for conditional aggregate calculations.</span></span> <span data-ttu-id="73ba2-244">예를 들어 가능한 값이 Not Started, Started, Finished인 State라는 필드가 데이터 세트에 있는 경우 다음 식을 그룹 머리글에 배치하면 Finished 값에 대해서만 집계 합을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-244">For example, if a dataset has a field that is named State with possible values Not Started, Started, Finished, the following expression, when placed in a group header, calculates the aggregate sum for only the value Finished:</span></span>  

```  
=Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
```  

#####  <a name="rownumber"></a><a name="RowNumber"></a><span data-ttu-id="73ba2-245">RowNumber</span><span class="sxs-lookup"><span data-stu-id="73ba2-245">RowNumber</span></span>  

-   <span data-ttu-id="73ba2-246">`RowNumber` 함수는 데이터 영역의 입력란에 사용될 경우 식이 나타나는 입력란의 각 인스턴스에 대한 행 번호를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-246">The `RowNumber` function, when used in a text box within a data region, displays the row number for each instance of the text box in which the expression appears.</span></span> <span data-ttu-id="73ba2-247">이 함수는 테이블에서 행 번호를 지정하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-247">This function can be useful to number rows in a table.</span></span> <span data-ttu-id="73ba2-248">또한 행 수에 따라 페이지를 나누는 등 더욱 복잡한 태스크에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-248">It can also be useful for more complex tasks, such as providing page breaks based on number of rows.</span></span> <span data-ttu-id="73ba2-249">자세한 내용은 이 항목에서 [페이지 나누기](#PageBreaks) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="73ba2-249">For more information, see [Page Breaks](#PageBreaks) in this topic.</span></span>  

<span data-ttu-id="73ba2-250">`RowNumber`에 지정한 범위는 번호 다시 매기기를 시작하는 시점을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-250">The scope you specify for `RowNumber` controls when renumbering begins.</span></span> <span data-ttu-id="73ba2-251">`Nothing` 키워드는 함수가 가장 바깥쪽 데이터 영역의 첫 번째 행부터 계산을 시작하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-251">The `Nothing` keyword indicates that the function will start counting at the first row in the outermost data region.</span></span> <span data-ttu-id="73ba2-252">중첩 데이터 영역에서 계산을 시작하려면 데이터 영역 이름을 사용하고,</span><span class="sxs-lookup"><span data-stu-id="73ba2-252">To start counting within nested data regions, use the name of the data region.</span></span> <span data-ttu-id="73ba2-253">그룹 내에서 계산을 시작하려면 그룹 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-253">To start counting within a group, use the name of the group.</span></span>  

```  
=RowNumber(Nothing)  
```  

##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> <span data-ttu-id="73ba2-254">보고서 데이터 모양</span><span class="sxs-lookup"><span data-stu-id="73ba2-254">Appearance of Report Data</span></span>  
<span data-ttu-id="73ba2-255">식을 사용하여 데이터가 보고서에 나타나는 모양을 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-255">You can use expressions to manipulate how data appears on a report.</span></span> <span data-ttu-id="73ba2-256">예를 들어 단일 입력란에서 두 필드의 값을 표시하거나, 보고서에 대한 정보를 표시하거나, 페이지 나누기가 보고서에 삽입되는 모양에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-256">For example, you can display the values of two fields in a single text box, display information about the report, or affect how page breaks are inserted in the report.</span></span>  

###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a><span data-ttu-id="73ba2-257">페이지 머리글 및 바닥글</span><span class="sxs-lookup"><span data-stu-id="73ba2-257">Page Headers and Footers</span></span>  
<span data-ttu-id="73ba2-258">보고서를 디자인할 때 보고서 이름 및 보고서 바닥글에 페이지 번호를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-258">When designing a report, you may want to display the name of the report and page number in the report footer.</span></span> <span data-ttu-id="73ba2-259">이렇게 하려면 다음 식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-259">To do this, you can use the following expressions:</span></span>  

-   <span data-ttu-id="73ba2-260">다음 식에서는 보고서 이름과 보고서가 실행된 시간을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-260">The following expression provides the name of the report and the time it was run.</span></span> <span data-ttu-id="73ba2-261">식은 보고서 바닥글이나 보고서 본문의 입력란에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-261">It can be placed in a text box in the report footer or in the body of the report.</span></span> <span data-ttu-id="73ba2-262">시간 형식은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 형식 문자열(간단한 날짜)로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-262">The time is formatted with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] formatting string for short date:</span></span>  

```  
=Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
```  

-   <span data-ttu-id="73ba2-263">다음 식을 보고서 바닥글에 사용하면 보고서의 페이지 번호와 총 페이지 수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-263">The following expression, placed in a text box in the footer of a report, provides page number and total pages in the report:</span></span>  

```  
=Globals.PageNumber & " of " & Globals.TotalPages  
```  

<span data-ttu-id="73ba2-264">다음 예에서는 디렉터리 목록에서 찾을 수 있는 페이지와 유사한 페이지의 첫 번째와 마지막 값을 페이지 머리글에 표시하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-264">The following examples describe how to display the first and last values from a page in the page header, similar to what you might find in a directory listing.</span></span> <span data-ttu-id="73ba2-265">이 예에서는 데이터 영역에 `LastName`라는 입력란이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-265">The example assumes a data region that contains a text box named `LastName`.</span></span>  

-   <span data-ttu-id="73ba2-266">다음 식을 페이지 머리글 왼쪽의 입력란에 사용하면 페이지에서 `LastName` 입력란의 첫 번째 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-266">The following expression, placed in a text box on the left side of the page header, provides the first value of the `LastName` text box on the page:</span></span>  

```  
=First(ReportItems("LastName").Value)  
```  

-   <span data-ttu-id="73ba2-267">다음 식을 페이지 머리글 오른쪽의 입력란에 사용하면 페이지에서 `LastName` 입력란의 마지막 값이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-267">The following expression, placed in a text box on the right side of the page header, provides the last value of the `LastName` text box on the page:</span></span>  

```  
=Last(ReportItems("LastName").Value)  
```  

<span data-ttu-id="73ba2-268">다음 예에서는 총 페이지 수를 표시하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-268">The following example describes how to display a page total.</span></span> <span data-ttu-id="73ba2-269">이 예에서는 데이터 영역에 `Cost`라는 입력란이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-269">The example assumes a data region that contains a text box named `Cost`.</span></span>  

-   <span data-ttu-id="73ba2-270">다음 식을 페이지 머리글 또는 바닥글에 사용하면 페이지의 `Cost` 입력란에 값의 합계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-270">The following expression, placed in the page header or footer, provides the sum of the values in the `Cost` text box for the page:</span></span>  

```  
=Sum(ReportItems("Cost").Value)  
```  

> [!NOTE]  
>  <span data-ttu-id="73ba2-271">페이지 머리글 또는 바닥글에서 식마다 보고서 항목을 하나만 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-271">You can refer to only one report item per expression in a page header or footer.</span></span> <span data-ttu-id="73ba2-272">또한 페이지 머리글과 바닥글 식에서 입력란 이름을 참조할 수 있지만 입력란 내의 실제 데이터 식은 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-272">Also, you can refer to the text box name, but not the actual data expression within the text box, in page header and footer expressions.</span></span>  

###  <a name="page-breaks"></a><a name="PageBreaks"></a> <span data-ttu-id="73ba2-273">페이지 나누기</span><span class="sxs-lookup"><span data-stu-id="73ba2-273">Page Breaks</span></span>  
<span data-ttu-id="73ba2-274">일부 보고서에서는 페이지 나누기를 그룹 또는 보고서 항목 외에도 지정된 행 수의 끝에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-274">In some reports, you may want to place a page break at the end of a specified number of rows instead of, or in addition to, on groups or report items.</span></span> <span data-ttu-id="73ba2-275">이렇게 하려면 그룹이나 원하는 세부 레코드를 포함하는 그룹을 만들고, 페이지 나누기를 그룹에 추가한 다음 그룹 식을 지정된 행 수에 따라 그룹에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-275">To do this, create a group that contains the groups or detail records you want, add a page break to the group, and then add a group expression to group by a specified number of rows.</span></span>  

-   <span data-ttu-id="73ba2-276">다음 식을 그룹 식에 사용하면 25행마다 번호를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-276">The following expression, when placed in the group expression, assigns a number to each set of 25 rows.</span></span> <span data-ttu-id="73ba2-277">그룹에 페이지 나누기가 정의되어 있는 경우 이 식을 사용하면 25행마다 페이지가 나눠집니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-277">When a page break is defined for the group, this expression results in a page break every 25 rows.</span></span>  

```  
=Ceiling(RowNumber(Nothing)/25)  
```  

<span data-ttu-id="73ba2-278">사용자가 페이지당 행 수에 대한 값을 설정하도록 허용하려면 `RowsPerPage` 라는 매개 변수를 만들고 다음 식에서 볼 수 있듯이 그룹 식이 매개 변수에 기반을 두도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-278">To allow the user to set a value for the number of rows per page, create a parameter named `RowsPerPage` and base the group expression on the parameter, as shown in the following expression:</span></span>  

```  
=Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
```  

<span data-ttu-id="73ba2-279">그룹의 페이지 나누기 설정에 대한 자세한 내용은 [페이지 나누기 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-page-break-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-279">For more information about setting page breaks for a group, see [Add a Page Break &#40;Report Builder and SSRS&#41;](add-a-page-break-report-builder-and-ssrs.md).</span></span>  

##  <a name="properties"></a><a name="Properties"></a> <span data-ttu-id="73ba2-280">속성</span><span class="sxs-lookup"><span data-stu-id="73ba2-280">Properties</span></span>  
<span data-ttu-id="73ba2-281">식은 입력란에서 데이터를 표시하는 데 사용될 뿐만 아니라</span><span class="sxs-lookup"><span data-stu-id="73ba2-281">Expressions are not only used to display data in text boxes.</span></span> <span data-ttu-id="73ba2-282">속성이 보고서 항목에 적용되는 방식을 변경하는 데에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-282">They can also be used to change how properties are applied to report items.</span></span> <span data-ttu-id="73ba2-283">보고서 항목에 대한 스타일 정보를 변경하거나 보고서 항목의 표시 유형을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-283">You can change style information for a report item, or change its visibility.</span></span>  

###  <a name="formatting"></a><a name="Formatting"></a><span data-ttu-id="73ba2-284">서식 지정</span><span class="sxs-lookup"><span data-stu-id="73ba2-284">Formatting</span></span>  

-   <span data-ttu-id="73ba2-285">다음 식을 입력란의 Color 속성에 사용하면 `Profit` 필드의 값에 따라 텍스트 색이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-285">The following expression, when used in the Color property of a text box, changes the color of the text depending on the value of the `Profit` field:</span></span>  

```  
=Iif(Fields!Profit.Value < 0, "Red", "Black")  
```  

<span data-ttu-id="73ba2-286">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 개체 변수 `Me`를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-286">You can also use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] object variable `Me`.</span></span> <span data-ttu-id="73ba2-287">이 변수는 입력란의 값을 참조할 수 있는 다른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-287">This variable is another way of referring to the value of a text box.</span></span>  

`=Iif(Me.Value < 0, "Red", "Black")`  

-   <span data-ttu-id="73ba2-288">다음 식을 데이터 영역에 있는 보고서 항목의 BackgroundColor 속성에 사용하면 각 행의 배경색을 흐린 녹색과 흰색으로 번갈아 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-288">The following expression, when used in the BackgroundColor property of a report item in a data region, alternates the background color of each row between pale green and white:</span></span>  

```  
=Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
```  

<span data-ttu-id="73ba2-289">특정 범위에 식을 사용할 경우 집계 함수의 데이터 세트를 나타내야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-289">If you are using an expression for a specified scope, you may have to indicate the dataset for the aggregate function:</span></span>  

```  
=Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
```  

> [!NOTE]  
>  <span data-ttu-id="73ba2-290">사용 가능한 색은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] KnownColor 열거형에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-290">Available colors come from the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] KnownColor enumeration.</span></span>  

### <a name="chart-colors"></a><span data-ttu-id="73ba2-291">차트 색</span><span class="sxs-lookup"><span data-stu-id="73ba2-291">Chart Colors</span></span>  
<span data-ttu-id="73ba2-292">셰이프 차트의 색을 지정하려면 사용자 지정 코드를 사용하여 색이 데이터 요소 값에 매핑되는 순서를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-292">To specify colors for a Shape chart, you can use custom code to control the order that colors are mapped to data point values.</span></span> <span data-ttu-id="73ba2-293">이렇게 하면 범주 그룹이 동일한 여러 차트에 일관된 색을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-293">This helps you use consistent colors for multiple charts that have the same category groups.</span></span> <span data-ttu-id="73ba2-294">자세한 내용은 [여러 셰이프 차트에 일관된 색 지정&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-294">For more information, see [Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  

###  <a name="visibility"></a><a name="Visibility"></a><span data-ttu-id="73ba2-295">잘</span><span class="sxs-lookup"><span data-stu-id="73ba2-295">Visibility</span></span>  
<span data-ttu-id="73ba2-296">보고서 항목에 대해 표시 유형 속성을 사용하여 보고서에서 항목을 표시하거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-296">You can show and hide items in a report using the visibility properties for the report item.</span></span> <span data-ttu-id="73ba2-297">테이블과 같은 데이터 영역에서 처음에 식의 값을 기반으로 정보 행을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-297">In a data region such as a table, you can initially hide detail rows based on the value in an expression.</span></span>  

-   <span data-ttu-id="73ba2-298">다음 식을 그룹에서 정보 행의 초기 표시 유형에 사용하면 `PctQuota` 필드에서 90%를 초과하는 모든 판매액에 대해 정보 행을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-298">The following expression, when used for initial visibility of detail rows in a group, shows the detail rows for all sales exceeding 90 percent in the `PctQuota` field:</span></span>  

```  
=Iif(Fields!PctQuota.Value>.9, False, True)  
```  

-   <span data-ttu-id="73ba2-299">다음 식을 테이블의 Hidden 속성에 설정하면 테이블에 13개 이상의 행이 있는 경우에만 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-299">The following expression, when set in the Hidden property of a table, shows the table only if it has more than 12 rows:</span></span>  

```  
=IIF(CountRows()>12,false,true)  
```  

-   <span data-ttu-id="73ba2-300">다음 식을 열의 속성에 설정 하면 `Hidden` 데이터 원본에서 데이터를 검색 한 후 보고서 데이터 집합에 필드가 있는 경우에만 열이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-300">The following expression, when set in the `Hidden` property of a column, shows the column only if the field exists in the report dataset after the data is retrieved from the data source:</span></span>  

```  
=IIF(Fields!Column_1.IsMissing, true, false)  
```  

###  <a name="urls"></a><a name="Hyperlinks"></a><span data-ttu-id="73ba2-301">Url</span><span class="sxs-lookup"><span data-stu-id="73ba2-301">URLs</span></span>  
<span data-ttu-id="73ba2-302">보고서 데이터를 사용하여 URL을 사용자 지정할 수 있으며 입력란에 대한 동작으로 URL을 추가할지 여부를 조건부로 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-302">You can customize URLs by using report data and also conditionally control whether URLs are added as an action for a text box.</span></span>  

-   <span data-ttu-id="73ba2-303">다음 식을 입력란에서 동작으로 사용하면 데이터 세트 필드 `EmployeeID`를 URL 매개 변수로 지정하는 사용자 지정 URL이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-303">The following expression, when used as an action on a text box, generates a customized URL that specifies the dataset field `EmployeeID` as a URL parameter.</span></span>  

```  
="http://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
```  

<span data-ttu-id="73ba2-304">자세한 내용은 [URL에 하이퍼링크 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-304">For more information, see [Add a Hyperlink to a URL &#40;Report Builder and SSRS&#41;](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md).</span></span>  

-   <span data-ttu-id="73ba2-305">다음 식은 입력란에 URL을 추가할지 여부를 조건부로 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-305">The following expression conditionally controls whether to add a URL in a text box.</span></span> <span data-ttu-id="73ba2-306">이 식은 보고서에 활성 URL을 포함할지 여부를 사용자가 결정하도록 허용하는 `IncludeURLs` 라는 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-306">This expression depends on a parameter named `IncludeURLs` that allows a user to decide whether to include active URLs in a report.</span></span> <span data-ttu-id="73ba2-307">이 식은 입력란의 동작으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-307">This expression is set as an action on a text box.</span></span> <span data-ttu-id="73ba2-308">이 매개 변수를 False로 설정하고 보고서를 보면 하이퍼링크 없이 Microsoft Excel로 보고서를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-308">By setting the parameter to False and then viewing the report, you can export the report Microsoft Excel without hyperlinks.</span></span>  

```  
=IIF(Parameters!IncludeURLs.Value,"http://adventure-works.com/productcatalog",Nothing)  
```  

##  <a name="report-data"></a><a name="ReportData"></a><span data-ttu-id="73ba2-309">보고서 데이터</span><span class="sxs-lookup"><span data-stu-id="73ba2-309">Report Data</span></span>  
<span data-ttu-id="73ba2-310">식을 사용하여 보고서에 사용되는 데이터를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-310">Expressions can be used to manipulate the data that is used in the report.</span></span> <span data-ttu-id="73ba2-311">매개 변수 및 다른 보고서 정보를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-311">You can refer to parameters and other report information.</span></span> <span data-ttu-id="73ba2-312">보고서 데이터 검색에 사용하는 쿼리를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-312">You can even change the query that is used to retrieve data for the report.</span></span>  

###  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="73ba2-313">매개 변수</span><span class="sxs-lookup"><span data-stu-id="73ba2-313">Parameters</span></span>  
<span data-ttu-id="73ba2-314">매개 변수의 식을 사용하여 매개 변수에 대한 기본값을 다양화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-314">You can use expressions in a parameter to vary the default value for the parameter.</span></span> <span data-ttu-id="73ba2-315">예를 들어 매개 변수를 사용하여 보고서 실행에 사용하는 사용자 ID에 따라 특정 사용자에 대한 데이터를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-315">For example, you can use a parameter to filter data to a particular user based on the user ID that is used to run the report.</span></span>  

-   <span data-ttu-id="73ba2-316">다음 식을 매개 변수에 대한 기본값으로 사용하면 보고서를 실행하는 사람의 사용자 ID를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-316">The following expression, when used as the default value for a parameter, collects the user ID of the person running the report:</span></span>  

```  
=User!UserID  
```  

-   <span data-ttu-id="73ba2-317">쿼리 매개 변수, 필터 식, 입력란 또는 보고서의 다른 영역에서 매개 변수를 참조하려면 `Parameters` 전역 컬렉션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-317">To refer to a parameter in a query parameter, filter expression, text box, or other area of the report, use the `Parameters` global collection.</span></span> <span data-ttu-id="73ba2-318">이 예에서는 매개 변수 이름을 *Department*라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-318">This example assumes that the parameter is named *Department*:</span></span>  

```  
=Parameters!Department.Value  
```  

-   <span data-ttu-id="73ba2-319">매개 변수는 보고서에서 만들 수 있지만 숨김으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-319">Parameters can be created in a report but set to hidden.</span></span> <span data-ttu-id="73ba2-320">보고서 서버에서 보고서를 실행할 때 매개 변수는 도구 모음에 나타나지 않으며 보고서를 읽는 사용자는 기본값을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-320">When the report runs on the report server, the parameter does not appear in the toolbar and the report reader cannot change the default value.</span></span> <span data-ttu-id="73ba2-321">기본값으로 설정된 숨겨진 매개 변수를 사용자 지정 상수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-321">You can use a hidden parameter set to a default value as custom constant.</span></span> <span data-ttu-id="73ba2-322">이 값을 필드 식을 포함한 모든 식에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-322">You can use this value in any expression, including a field expression.</span></span> <span data-ttu-id="73ba2-323">다음 식은 *ParameterField*라는 매개 변수에 대한 기본 매개 변수 값으로 지정된 필드를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-323">The following expression identifies the field specified by the default parameter value for the parameter named *ParameterField*:</span></span>  

```  
=Fields(Parameters!ParameterField.Value).Value  
```  

## <a name="custom-code"></a><a name="CustomCode"></a><span data-ttu-id="73ba2-324">사용자 지정 코드</span><span class="sxs-lookup"><span data-stu-id="73ba2-324">Custom Code</span></span>

<span data-ttu-id="73ba2-325">보고서에 사용자 지정 코드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-325">You can use custom code in a report.</span></span> <span data-ttu-id="73ba2-326">사용자 지정 코드는 보고서에 포함되거나 보고서에서 사용되는 사용자 지정 어셈블리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-326">Custom code is either embedded in a report or stored in a custom assembly which is used in the report.</span></span> <span data-ttu-id="73ba2-327">사용자 지정 코드에 대한 자세한 내용은 [보고서 디자이너의 식에 포함된 사용자 지정 코드 및 어셈블리 참조&#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-327">For more information about custom code, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  

### <a name="using-group-variables-for-custom-aggregation"></a><span data-ttu-id="73ba2-328">사용자 지정 집계를 위해 그룹 변수 사용</span><span class="sxs-lookup"><span data-stu-id="73ba2-328">Using Group Variables for Custom Aggregation</span></span>

<span data-ttu-id="73ba2-329">특정 그룹 범위에 대해 로컬인 그룹 변수의 값을 초기화한 다음 해당 변수에 대한 참조를 식에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-329">You can initialize the value for a group variable that is local to a particular group scope and then include a reference to that variable in expressions.</span></span> <span data-ttu-id="73ba2-330">사용자 지정 코드가 있는 그룹 변수를 사용하려면 사용자 지정 집계를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-330">One of the ways that you can use a group variable with custom code is to implement a custom aggregate.</span></span> <span data-ttu-id="73ba2-331">자세한 내용은 [사용자 지정 집계를 위해 Reporting Services 2008의 그룹 변수 사용(Using Group Variables in Reporting Services 2008 for Custom Aggregation)](https://go.microsoft.com/fwlink/?LinkId=128714)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="73ba2-331">For more information, see [Using Group Variables in Reporting Services 2008 for Custom Aggregation](https://go.microsoft.com/fwlink/?LinkId=128714).</span></span>  

<span data-ttu-id="73ba2-332">변수에 대한 자세한 내용은 [보고서 및 그룹 변수 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73ba2-332">For more information about variables, see [Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md).</span></span>  

## <a name="suppressing-null-or-zero-values-at-run-time"></a><span data-ttu-id="73ba2-333">런타임에 Null 또는 0 값 표시하지 않기</span><span class="sxs-lookup"><span data-stu-id="73ba2-333">Suppressing Null or Zero Values at Run Time</span></span>

<span data-ttu-id="73ba2-334">식의 일부 값은 보고서를 처리할 때 Null이나 정의되지 않은 값으로 계산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-334">Some values in an expression can evaluate to null or undefined at report processing time.</span></span> <span data-ttu-id="73ba2-335">이 경우 런타임 오류가 발생하여 입력란에 계산된 식이 아닌 **#Error** 가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-335">This can create run-time errors that result in **#Error** displaying in the text box instead of the evaluated expression.</span></span> <span data-ttu-id="73ba2-336">`IIF` 함수는 이러한 동작에 특히 민감합니다. If-Then-Else 문과 달리 `IIF` 문의 각 부분(함수 호출 포함)은 `true` 또는 `false`를 테스트하는 루틴에 전달되기 전에 계산되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-336">The `IIF` function is particularly sensitive to this behavior because, unlike an If-Then-Else statement, each part of the `IIF` statement is evaluated (including function calls) before being passed to the routine that tests for `true` or `false`.</span></span> <span data-ttu-id="73ba2-337">`=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` 문은 **가 NOTHING인 경우 렌더링된 보고서에서** #Error `Fields!Sales.Value` 를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-337">The statement `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` generates **#Error** in the rendered report if `Fields!Sales.Value` is NOTHING.</span></span>  

<span data-ttu-id="73ba2-338">이러한 상황을 방지하려면 다음 전략 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-338">To avoid this condition, use one of the following strategies:</span></span>  

-   <span data-ttu-id="73ba2-339">필드 B의 값이 0이거나 정의되지 않은 경우 분자를 0으로, 분모를 1로 설정합니다. 그렇지 않은 경우 분자를 필드 A의 값으로, 분모를 필드 B의 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-339">Set the numerator to 0 and the denominator to 1 if the value for field B is 0 or undefined; otherwise, set the numerator to the value for field A and the denominator to the value for field B.</span></span>  

```  
=IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
```  

-   <span data-ttu-id="73ba2-340">사용자 지정 코드 함수를 사용하여 식의 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-340">Use a custom code function to return the value for the expression.</span></span> <span data-ttu-id="73ba2-341">다음 예에서는 현재 값과 이전 값의 차이를 백분율로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-341">The following example returns the percentage difference between a current value and a previous value.</span></span> <span data-ttu-id="73ba2-342">이 식은 연속하는 두 값의 차이를 계산하는 데에 사용할 수 있으며 경계 사례인 첫 번째 비교(이전 값이 없는 경우)와 이전 값이나 현재 값이 `null`([!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]의 `Nothing`)인 경우도 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-342">This can be used to calculate the difference between any two successive values and it handles the edge case of the first comparison (when there is no previous value) and cases whether either the previous value or the current value is `null` (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).</span></span>  

```  
Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
     If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
          Return Nothing  
     Else if PreviousValue = 0 OR CurrentValue = 0 Then  
          Return Nothing  
     Else
          Return (CurrentValue - PreviousValue) / CurrentValue  
     End If  
End Function  
```  

<span data-ttu-id="73ba2-343">다음 식은 "ColumnGroupByYear" 컨테이너(그룹 또는 데이터 영역)에 대해 입력란에서 이 사용자 지정 코드를 호출하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-343">The following expression shows how to call this custom code from a text box, for the "ColumnGroupByYear" container (group or data region).</span></span>  

```  
=Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
```  

<span data-ttu-id="73ba2-344">이 방법으로 런타임 예외를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-344">This helps to avoid run-time exceptions.</span></span> <span data-ttu-id="73ba2-345">이제 입력란의 `Color` 속성에서 `=IIF(Me.Value < 0, "red", "black")`와 같은 식을 사용하여 값이 0보다 큰지 작은지에 따라 조건부로 텍스트를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73ba2-345">You can now use an expression like `=IIF(Me.Value < 0, "red", "black")` in the `Color` property of the text box to conditionally the display text based on whether the values are greater than or less than 0.</span></span>  

## <a name="see-also"></a><span data-ttu-id="73ba2-346">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73ba2-346">See Also</span></span>

- [<span data-ttu-id="73ba2-347">필터 수식 예&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="73ba2-347">Filter Equation Examples &#40;Report Builder and SSRS&#41;</span></span>](filter-equation-examples-report-builder-and-ssrs.md)
- [<span data-ttu-id="73ba2-348">그룹 식 예&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="73ba2-348">Group Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)
- [<span data-ttu-id="73ba2-349">보고서에 사용되는 식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="73ba2-349">Expression Uses in Reports &#40;Report Builder and SSRS&#41;</span></span>](expression-uses-in-reports-report-builder-and-ssrs.md)
- [<span data-ttu-id="73ba2-350">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="73ba2-350">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)
- [<span data-ttu-id="73ba2-351">일반적으로 사용되는 필터&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="73ba2-351">Commonly Used Filters &#40;Report Builder and SSRS&#41;</span></span>](commonly-used-filters-report-builder-and-ssrs.md)