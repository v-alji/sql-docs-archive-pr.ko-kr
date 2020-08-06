---
title: FORMATED_VALUE의 언어 및 FORMAT_STRING | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7534ff5f-954e-47d4-a2ed-4b5b8ccb30e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: ba4aacbbd440da6048680054771c86c40ef96daa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639021"
---
# <a name="language-and-format_string-on-formated_value"></a><span data-ttu-id="307e9-102">FORMATED_VALUE에 대한 LANGUAGE 및 FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="307e9-102">LANGUAGE and FORMAT_STRING on FORMATED_VALUE</span></span>
  <span data-ttu-id="307e9-103">FORMATTED_VALUE 속성은 셀의 VALUE, FORMAT_STRING 속성 및 LANGUAGE 속성의 상호 작용을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-103">The FORMATTED_VALUE property is built on the interactions of the VALUE, FORMAT_STRING and LANGUAGE properties of the cell.</span></span> <span data-ttu-id="307e9-104">이 항목에서는 이러한 속성이 상호 작용하여 FORMATTED_VALUE 속성을 작성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-104">This topic explains how these properties interact to build the FORMATTED_VALUE property.</span></span>  
  
## <a name="value-format_string-language-properties"></a><span data-ttu-id="307e9-105">VALUE, FORMAT_STRING, LANGUAGE 속성</span><span class="sxs-lookup"><span data-stu-id="307e9-105">VALUE, FORMAT_STRING, LANGUAGE properties</span></span>  
 <span data-ttu-id="307e9-106">다음 표에서는 이러한 속성에 대해 설명합니다. 사용자는 이 내용을 통해 이러한 속성을 조합하여 사용하는 방법을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-106">The following table explains what these properties are, to help prepare us to use them in combination.</span></span>  
  
 <span data-ttu-id="307e9-107">값</span><span class="sxs-lookup"><span data-stu-id="307e9-107">VALUE</span></span>  
 <span data-ttu-id="307e9-108">형식이 지정되지 않은 셀 값입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-108">The unformatted value of the cell.</span></span>  
  
 <span data-ttu-id="307e9-109">FORMAT_STRING</span><span class="sxs-lookup"><span data-stu-id="307e9-109">FORMAT_STRING</span></span>  
 <span data-ttu-id="307e9-110">FORMATTED_VALUE 속성을 생성하기 위해 셀 값에 적용될 형식 지정 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-110">The formatting template to be applied to the value of the cell to generate FORMATTED_VALUE property</span></span>  
  
 <span data-ttu-id="307e9-111">LANGUAGE</span><span class="sxs-lookup"><span data-stu-id="307e9-111">LANGUAGE</span></span>  
 <span data-ttu-id="307e9-112">FORMATTED_VALUE의 지역화된 버전을 생성하기 위해 FORMAT_STRING과 함께 적용될 로캘 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-112">The locale specification to be applied alongside FORMAT_STRING to generate a localized version of FORMATTED_VALUE</span></span>  
  
## <a name="formatted_value-constructed"></a><span data-ttu-id="307e9-113">FORMATTED_VALUE 생성</span><span class="sxs-lookup"><span data-stu-id="307e9-113">FORMATTED_VALUE constructed</span></span>  
 <span data-ttu-id="307e9-114">VALUE 속성 값을 사용하고 해당 값에 FORMAT_STRING 속성에 지정된 형식 템플릿을 적용하여 FORMATTED_VALUE 속성을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-114">The FORMATTED_VALUE property is constructed by using the value from the VALUE property and applying the format template specified in the FORMAT_STRING property to that value.</span></span> <span data-ttu-id="307e9-115">또한 형식 지정 값이 `named formatting literal`인 경우 LANGUAGE 속성 사양이 명명된 형식 지정에 대한 언어 사용법에 따라 FORMAT_STRING의 출력을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-115">In addition, whenever the formatting value is a `named formatting literal` the LANGUAGE property specification modifies the output of FORMAT_STRING to follow the language usage for the named formatting.</span></span> <span data-ttu-id="307e9-116">명명된 형식 지정 리터럴은 모두 지역화할 수 있는 방법으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-116">Named formatting literals are all defined in a way that can be localized.</span></span> <span data-ttu-id="307e9-117">예를 들어 `"General Date"` 는 언어 사양에 상관없이 템플릿에서 정의하는 대로 날짜를 표시해야 함을 지정하는 `"YYYY-MM-DD hh:nn:ss",` 템플릿과는 반대로 지역화할 수 있는 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-117">For example, `"General Date"` is a specification that can be localized, as opposed to the following template `"YYYY-MM-DD hh:nn:ss",` which states that the date is to be presented as defined by the template regardless of the language specification.</span></span>  
  
 <span data-ttu-id="307e9-118">FORMAT_STRING 템플릿과 LANGUAGE 사양 사이에 충돌이 있으면 FORMAT_STRING 템플릿이 LANGUAGE 사양보다 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-118">If there is a conflict between the FORMAT_STRING template and the LANGUAGE specification, the FORMAT_STRING template overrides the LANGUAGE specification.</span></span> <span data-ttu-id="307e9-119">예를 들어 FORMAT_STRING="$ #0" 및 LANGUAGE=1034(스페인), VALUE=123.456인데 FORMATTED_VALUE="  123" 대신 FORMATTED_VALUE="$ 123"인 경우 형식 템플릿의 값이 지정된 언어보다 우선 적용되므로 예상 형식은 유로입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-119">For example, if FORMAT_STRING="$ #0" and LANGUAGE=1034 (Spain), and VALUE=123.456 then FORMATTED_VALUE="$ 123" instead of FORMATTED_VALUE="€ 123", the expected format is in Euros, because the value of the format template overrides the language specified.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="307e9-120">예</span><span class="sxs-lookup"><span data-stu-id="307e9-120">Examples</span></span>  
 <span data-ttu-id="307e9-121">다음 예에서는 LANGUAGE가 FORMAT_STRING과 함께 사용될 때 얻은 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-121">The following examples show the output obtained when LANGUAGE is used in conjunction with FORMAT_STRING.</span></span>  
  
 <span data-ttu-id="307e9-122">첫 번째 예에서는 숫자 값 형식 지정에 대해 설명하고 두 번째 예에서는 날짜 및 시간 값 형식 지정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-122">The first example explains formatting numerical values; the second example explains formatting date and time values.</span></span>  
  
 <span data-ttu-id="307e9-123">각 예에서 MDX(Multidimensional Expressions) 코드가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-123">For each example the Multidimensional Expressions (MDX) code is given.</span></span>  
  
 `with`  
  
 `member measures.A as 5040, FORMAT_STRING="Currency"`  
  
 `member measures.B as measures.A, LANGUAGE=1034`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="$#,##0.00"`  
  
 `member measures.D as measures.A, FORMAT_STRING="Scientific"`  
  
 `member measures.E as measures.A, LANGUAGE=1034 , FORMAT_STRING="Scientific"`  
  
 `member measures.F as 0.5040, FORMAT_STRING="Percent"`  
  
 `member measures.G as measures.F, LANGUAGE=1034`  
  
 `member measures.H as 0, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.I as 59, LANGUAGE=1034 , FORMAT_STRING="Yes/No"`  
  
 `member measures.J as 0, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `member measures.K as -312, LANGUAGE=1034 , FORMAT_STRING="ON/OFF"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F, measures.G, measures.H, measures.I, measures.J, measures.K} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 <span data-ttu-id="307e9-124">위의 MDX 쿼리를 로캘 1033가 있는 서버 및 클라이언트에서 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 실행한 경우 바뀐 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-124">The results, transposed, when the above MDX query was run using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] over a server and client with locale 1033 are as follows:</span></span>  
  
|<span data-ttu-id="307e9-125">멤버</span><span class="sxs-lookup"><span data-stu-id="307e9-125">Member</span></span>|<span data-ttu-id="307e9-126">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="307e9-126">FORMATTED_VALUE</span></span>|<span data-ttu-id="307e9-127">설명</span><span class="sxs-lookup"><span data-stu-id="307e9-127">Explanation</span></span>|  
|------------|----------------------|-----------------|  
|<span data-ttu-id="307e9-128">A</span><span class="sxs-lookup"><span data-stu-id="307e9-128">A</span></span>|<span data-ttu-id="307e9-129">$5,040.00</span><span class="sxs-lookup"><span data-stu-id="307e9-129">$5,040.00</span></span>|<span data-ttu-id="307e9-130">FORMAT_STRING이 `Currency` 로 설정되었고 LANGUAGE가 `1033`(시스템 로캘 값에서 상속)입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-130">FORMAT_STRING is set to `Currency` and LANGUAGE is `1033`, inherited from system locale value</span></span>|  
|<span data-ttu-id="307e9-131">b</span><span class="sxs-lookup"><span data-stu-id="307e9-131">B</span></span>|<span data-ttu-id="307e9-132">5.040,00</span><span class="sxs-lookup"><span data-stu-id="307e9-132">€5.040,00</span></span>|<span data-ttu-id="307e9-133">FORMAT_STRING이 `Currency` (A에서 상속)로 설정되었고 LANGUAGE가 명시적으로 `1034` (스페인)로 설정되었으므로 유로 기호, 다른 소수 구분 기호 및 다른 천 단위 구분 기호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-133">FORMAT_STRING is set to `Currency` (inherited from A) and LANGUAGE is explicitly set to `1034` (Spain) hence the Euro sign, the different decimal separator and the different thousand separator.</span></span>|  
|<span data-ttu-id="307e9-134">C</span><span class="sxs-lookup"><span data-stu-id="307e9-134">C</span></span>|<span data-ttu-id="307e9-135">$5.040,00</span><span class="sxs-lookup"><span data-stu-id="307e9-135">$5.040,00</span></span>|<span data-ttu-id="307e9-136">FORMAT_STRING이 `$#,##0.00` (A에서 상속된 Currency에 대한 재정의)으로 설정되었고 LANGUAGE가 명시적으로 `1034` (스페인)로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-136">FORMAT_STRING is set to `$#,##0.00` an override to Currency, from A, and LANGUAGE is explicitly set to `1034` (Spain).</span></span> <span data-ttu-id="307e9-137">FORMAT_STRING 속성이 명시적으로 통화 기호를 $로 설정했으므로 FORMATTED_VALUE가 $ 기호와 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-137">Because the FORMAT_STRING property explicitly set the currency symbol to $, the FORMATTED_VALUE is presented with the $ sign.</span></span> <span data-ttu-id="307e9-138">그러나 `.` (점) 및 `,` (쉼표)가 각각 소수 구분 기호와 천 단위 구분 기호의 자리 표시자이므로 언어 사양은 소수 구분 기호와 천 단위 구분 기호에 대해 지역화된 출력을 생성하면서 이러한 기호에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-138">However, because `.` (dot) and `,` (comma) are placeholders for decimal separator and thousand separator respectively, the language specification affects them generating an output that is localized for decimal and thousand separators.</span></span>|  
|<span data-ttu-id="307e9-139">D</span><span class="sxs-lookup"><span data-stu-id="307e9-139">D</span></span>|<span data-ttu-id="307e9-140">5.04E+03</span><span class="sxs-lookup"><span data-stu-id="307e9-140">5.04E+03</span></span>|<span data-ttu-id="307e9-141">FORMAT_STRING이 `Scientific` 로 설정되었고 LANGUAGE가 `1033`(시스템 로캘 값에서 상속)으로 설정되었으므로 `.` (점)이 소수 구분 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-141">FORMAT_STRING is set to `Scientific` and LANGUAGE is set to `1033`, inherited from system locale value, hence `.` (dot) is the decimal separator.</span></span>|  
|<span data-ttu-id="307e9-142">E</span><span class="sxs-lookup"><span data-stu-id="307e9-142">E</span></span>|<span data-ttu-id="307e9-143">5,04E+03</span><span class="sxs-lookup"><span data-stu-id="307e9-143">5,04E+03</span></span>|<span data-ttu-id="307e9-144">FORMAT_STRING이 `Scientific` 으로 설정되었고 LANGUAGE가 명시적으로 `1034,` 로 설정되었으므로 `,` (쉼표)가 소수 구분 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-144">FORMAT_STRING is set to `Scientific` and LANGUAGE is set explicitly to `1034,` hence `,` (comma) is the decimal separator.</span></span>|  
|<span data-ttu-id="307e9-145">F</span><span class="sxs-lookup"><span data-stu-id="307e9-145">F</span></span>|<span data-ttu-id="307e9-146">50.40%</span><span class="sxs-lookup"><span data-stu-id="307e9-146">50.40%</span></span>|<span data-ttu-id="307e9-147">FORMAT_STRING이 `Percent` 로 설정되었고 LANGUAGE가 `1033`(시스템 로캘 값에서 상속)으로 설정되었으므로 `.` (점)이 소수 구분 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-147">FORMAT_STRING is set to `Percent` and LANGUAGE is set to `1033`, inherited from system locale value, hence `.` (dot) is the decimal separator.</span></span><br /><br /> <span data-ttu-id="307e9-148">VALUE가 5040에서 0.5040으로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-148">Note that VALUE was changed from 5040 to 0.5040</span></span>|  
|<span data-ttu-id="307e9-149">G</span><span class="sxs-lookup"><span data-stu-id="307e9-149">G</span></span>|<span data-ttu-id="307e9-150">50,40%</span><span class="sxs-lookup"><span data-stu-id="307e9-150">50,40%</span></span>|<span data-ttu-id="307e9-151">FORMAT_STRING이 `Percent`(F에서 상속)로 설정되었고 LANGUAGE가 명시적으로 `1034` 로 설정되었으므로 `,` (쉼표)가 소수 구분 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-151">FORMAT_STRING is set to `Percent`, inherited from F, and LANGUAGE is set explicitly to `1034` hence `,` (comma) is the decimal separator.</span></span><br /><br /> <span data-ttu-id="307e9-152">VALUE가 F 값에서 상속되었습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-152">Note that VALUE was inherited from F value.</span></span>|  
|<span data-ttu-id="307e9-153">H</span><span class="sxs-lookup"><span data-stu-id="307e9-153">H</span></span>|<span data-ttu-id="307e9-154">아니요</span><span class="sxs-lookup"><span data-stu-id="307e9-154">No</span></span>|<span data-ttu-id="307e9-155">FORMAT_STRING이 `YES/NO`로 설정되었고 VALUE가 0으로 설정되었고 LANGUAGE가 명시적으로 `1034`로 설정되었습니다. 영어 NO와 스페인어 NO 사이의 차이가 없으므로 사용자는 FORMATTED_VALUE의 차이점을 발견할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-155">FORMAT_STRING is set to `YES/NO`, VALUE is set to 0 and LANGUAGE is set explicitly to `1034`; because there is no difference between English NO and Spanish NO the user sees no difference in the FORMATTED_VALUE.</span></span>|  
|<span data-ttu-id="307e9-156">I</span><span class="sxs-lookup"><span data-stu-id="307e9-156">I</span></span>|<span data-ttu-id="307e9-157">SI</span><span class="sxs-lookup"><span data-stu-id="307e9-157">SI</span></span>|<span data-ttu-id="307e9-158">FORMAT_STRING이 `YES/NO`로 설정되었고 VALUE가 59로 설정되었고 LANGUAGE가 명시적으로 `1034`로 설정되었습니다. YES/NO 형식 지정에 대해 정의된 대로 0과 다른 값은 YES이고 언어가 스페인어로 설정되었으므로 FORMATTED_VALUE가 SI입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-158">FORMAT_STRING is set to `YES/NO`, VALUE is set to 59 and LANGUAGE is set explicitly to `1034`; as defined for YES/NO formatting, any value different from zero (0) is a YES and because language is set to Spanish then the FORMATTED_VALUE is SI.</span></span>|  
|<span data-ttu-id="307e9-159">J</span><span class="sxs-lookup"><span data-stu-id="307e9-159">J</span></span>|<span data-ttu-id="307e9-160">Desactivado</span><span class="sxs-lookup"><span data-stu-id="307e9-160">Desactivado</span></span>|<span data-ttu-id="307e9-161">FORMAT_STRING이 `ON/OFF`로 설정되었고 VALUE가 0으로 설정되었고 LANGUAGE가 명시적으로 `1034`로 설정되었습니다. ON/OFF 형식 지정에 대해 정의된 대로 0과 같은 값은 OFF이고 언어가 스페인어로 설정되었으므로 FORMATTED_VALUE가 Desactivado입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-161">FORMAT_STRING is set to `ON/OFF`, VALUE is set to 0 and LANGUAGE is set explicitly to `1034`; as defined for ON/OFF formatting, any value equal to zero (0) is an OFF and because language is set to Spanish then the FORMATTED_VALUE is Desactivado.</span></span>|  
|<span data-ttu-id="307e9-162">K</span><span class="sxs-lookup"><span data-stu-id="307e9-162">K</span></span>|<span data-ttu-id="307e9-163">Activado</span><span class="sxs-lookup"><span data-stu-id="307e9-163">Activado</span></span>|<span data-ttu-id="307e9-164">FORMAT_STRING이 `ON/OFF`로 설정되었고 VALUE가 -312로 설정되었고 LANGUAGE가 명시적으로 `1034`로 설정되었습니다. ON/OFF 형식 지정에 대해 정의된 대로 0과 다른 값은 ON이고 언어가 스페인어로 설정되었으므로 FORMATTED_VALUE가 Activado입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-164">FORMAT_STRING is set to `ON/OFF`, VALUE is set to -312 and LANGUAGE is set explicitly to `1034`; as defined for ON/OFF formatting, any value different from zero (0) is an ON and because language is set to Spanish then the FORMATTED_VALUE is Activado.</span></span>|  
  
 `with`  
  
 `member measures.A as 'CDate("1959-03-12 06:30")'`  
  
 `member measures.B as measures.A, FORMAT_STRING="Long Date"`  
  
 `member measures.C as measures.A, LANGUAGE=1034 , FORMAT_STRING="General Date"`  
  
 `member measures.D as measures.A, LANGUAGE=1034, FORMAT_STRING="Long Date"`  
  
 `member measures.E as measures.A, LANGUAGE=1041 , FORMAT_STRING="General Date"`  
  
 `member measures.F as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Date"`  
  
 `member measures.G as measures.A, FORMAT_STRING="Long Time"`  
  
 `member measures.H as measures.A, FORMAT_STRING="Short Time"`  
  
 `member measures.I as measures.A, LANGUAGE=1034 , FORMAT_STRING="Long Time"`  
  
 `member measures.J as measures.A, LANGUAGE=1034 , FORMAT_STRING="Short Time"`  
  
 `member measures.K as measures.A, LANGUAGE=1041 , FORMAT_STRING="Long Time"`  
  
 `member measures.L as measures.A, LANGUAGE=1041 , FORMAT_STRING="Short Time"`  
  
 `Select {measures.A, measures.B, measures.C, measures.D, measures.E, measures.F`  
  
 `, measures.G, measures.H, measures.I, measures.J, measures.K, measures.L} on 0`  
  
 `from [Adventure Works]`  
  
 `cell properties VALUE, FORMAT_STRING, LANGUAGE, FORMATTED_VALUE`  
  
 <span data-ttu-id="307e9-165">위의 MDX 쿼리를 로캘 1033가 있는 서버 및 클라이언트에서 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 실행한 경우 바뀐 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-165">The results, transposed, when the above MDX query was run using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] over a server and client with locale 1033 are as follows:</span></span>  
  
|<span data-ttu-id="307e9-166">멤버</span><span class="sxs-lookup"><span data-stu-id="307e9-166">Member</span></span>|<span data-ttu-id="307e9-167">FORMATTED_VALUE</span><span class="sxs-lookup"><span data-stu-id="307e9-167">FORMATTED_VALUE</span></span>|<span data-ttu-id="307e9-168">설명</span><span class="sxs-lookup"><span data-stu-id="307e9-168">Explanation</span></span>|  
|------------|----------------------|-----------------|  
|<span data-ttu-id="307e9-169">A</span><span class="sxs-lookup"><span data-stu-id="307e9-169">A</span></span>|<span data-ttu-id="307e9-170">3/12/1959 6:30:00 AM</span><span class="sxs-lookup"><span data-stu-id="307e9-170">3/12/1959 6:30:00 AM</span></span>|<span data-ttu-id="307e9-171">FORMAT_STRING이 CDate() 식에 의해 암시적으로 `General Date` 로 설정되었고 LANGUAGE가 `1033` (영어)(시스템 로캘 값에서 상속)으로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-171">FORMAT_STRING is set implicitly to `General Date` by the CDate() expression and LANGUAGE is `1033` (English), inherited from system locale value</span></span>|  
|<span data-ttu-id="307e9-172">b</span><span class="sxs-lookup"><span data-stu-id="307e9-172">B</span></span>|<span data-ttu-id="307e9-173">Thursday, March 12, 1959</span><span class="sxs-lookup"><span data-stu-id="307e9-173">Thursday, March 12, 1959</span></span>|<span data-ttu-id="307e9-174">FORMAT_STRING이 명시적으로 `Long Date` 로 설정되었고 LANGUAGE가 `1033` (영어)(시스템 로캘 값에서 상속)입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-174">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is `1033` (English), inherited from system locale value</span></span>|  
|<span data-ttu-id="307e9-175">C</span><span class="sxs-lookup"><span data-stu-id="307e9-175">C</span></span>|<span data-ttu-id="307e9-176">12/03/1959 6:30:00</span><span class="sxs-lookup"><span data-stu-id="307e9-176">12/03/1959 6:30:00</span></span>|<span data-ttu-id="307e9-177">FORMAT_STRING이 명시적으로 `General Date` 로 설정되었고 LANGUAGE가 명시적으로 `1034` (스페인어)입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-177">FORMAT_STRING is set explicitly to `General Date` and LANGUAGE is explicitly `1034` (Spanish).</span></span><br /><br /> <span data-ttu-id="307e9-178">미국 형식 지정 스타일과 비교해 보면 월과 일이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-178">Note that month and day are switched when compared to U.S. formatting style</span></span>|  
|<span data-ttu-id="307e9-179">D</span><span class="sxs-lookup"><span data-stu-id="307e9-179">D</span></span>|<span data-ttu-id="307e9-180">jueves, 12 de marzo de 1959</span><span class="sxs-lookup"><span data-stu-id="307e9-180">jueves, 12 de marzo de 1959</span></span>|<span data-ttu-id="307e9-181">FORMAT_STRING이 명시적으로 `Long Date` 로 설정되었고 LANGUAGE가 명시적으로 `1034` (스페인어)입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-181">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is explicitly `1034` (Spanish).</span></span><br /><br /> <span data-ttu-id="307e9-182">월과 요일은 스페인어로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-182">Note that month and day of the week are worded in Spanish</span></span>|  
|<span data-ttu-id="307e9-183">E</span><span class="sxs-lookup"><span data-stu-id="307e9-183">E</span></span>|<span data-ttu-id="307e9-184">1959/03/12 6:30:00</span><span class="sxs-lookup"><span data-stu-id="307e9-184">1959/03/12 6:30:00</span></span>|<span data-ttu-id="307e9-185">FORMAT_STRING이 명시적으로 `General Date` 로 설정되었고 LANGUAGE가 명시적으로 `1041` (일본어)입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-185">FORMAT_STRING is set explicitly to `General Date` and LANGUAGE is explicitly `1041` (Japanese).</span></span><br /><br /> <span data-ttu-id="307e9-186">이제 날짜의 형식이 연도/월/일 시간:분:초입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-186">Note that the date is now formatted Year/Month/Day Hour:Minutes:Seconds</span></span>|  
|<span data-ttu-id="307e9-187">F</span><span class="sxs-lookup"><span data-stu-id="307e9-187">F</span></span>|<span data-ttu-id="307e9-188">1959年3月12日</span><span class="sxs-lookup"><span data-stu-id="307e9-188">1959年3月12日</span></span>|<span data-ttu-id="307e9-189">FORMAT_STRING이 명시적으로 `Long Date` 로 설정되었고 LANGUAGE가 명시적으로 `1041` (일본어)입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-189">FORMAT_STRING is set explicitly to `Long Date` and LANGUAGE is explicitly `1041` (Japanese).</span></span>|  
|<span data-ttu-id="307e9-190">G</span><span class="sxs-lookup"><span data-stu-id="307e9-190">G</span></span>|<span data-ttu-id="307e9-191">오전 6:30:00</span><span class="sxs-lookup"><span data-stu-id="307e9-191">6:30:00 AM</span></span>|<span data-ttu-id="307e9-192">FORMAT_STRING이 명시적으로 `Long Time` 으로 설정되었고 LANGUAGE가 `1033` (영어)(시스템 로캘 값에서 상속)입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-192">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is `1033` (English), inherited from system locale value.</span></span>|  
|<span data-ttu-id="307e9-193">H</span><span class="sxs-lookup"><span data-stu-id="307e9-193">H</span></span>|<span data-ttu-id="307e9-194">06:30</span><span class="sxs-lookup"><span data-stu-id="307e9-194">06:30</span></span>|<span data-ttu-id="307e9-195">FORMAT_STRING이 명시적으로 `Short Time` 으로 설정되었고 LANGUAGE가 `1033` (영어)(시스템 로캘 값에서 상속)입니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-195">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is `1033` (English), inherited from system locale value.</span></span>|  
|<span data-ttu-id="307e9-196">I</span><span class="sxs-lookup"><span data-stu-id="307e9-196">I</span></span>|<span data-ttu-id="307e9-197">6:30:00</span><span class="sxs-lookup"><span data-stu-id="307e9-197">6:30:00</span></span>|<span data-ttu-id="307e9-198">FORMAT_STRING이 명시적으로 `Long Time` 으로 설정되었고 LANGUAGE가 명시적으로 `1034` (스페인어)로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-198">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is set explicitly to `1034` (Spanish).</span></span>|  
|<span data-ttu-id="307e9-199">J</span><span class="sxs-lookup"><span data-stu-id="307e9-199">J</span></span>|<span data-ttu-id="307e9-200">06:30</span><span class="sxs-lookup"><span data-stu-id="307e9-200">06:30</span></span>|<span data-ttu-id="307e9-201">FORMAT_STRING이 명시적으로 `Short Time` 으로 설정되었고 LANGUAGE가 명시적으로 `1034` (스페인어)로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-201">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is set explicitly to `1034` (Spanish).</span></span>|  
|<span data-ttu-id="307e9-202">K</span><span class="sxs-lookup"><span data-stu-id="307e9-202">K</span></span>|<span data-ttu-id="307e9-203">6:30:00</span><span class="sxs-lookup"><span data-stu-id="307e9-203">6:30:00</span></span>|<span data-ttu-id="307e9-204">FORMAT_STRING이 명시적으로 `Long Time` 으로 설정되었고 LANGUAGE가 명시적으로 `1041` (일본어)로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-204">FORMAT_STRING is set explicitly to `Long Time` and LANGUAGE is set explicitly to `1041` (Japanese).</span></span>|  
|<span data-ttu-id="307e9-205">L</span><span class="sxs-lookup"><span data-stu-id="307e9-205">L</span></span>|<span data-ttu-id="307e9-206">06:30</span><span class="sxs-lookup"><span data-stu-id="307e9-206">06:30</span></span>|<span data-ttu-id="307e9-207">FORMAT_STRING이 명시적으로 `Short Time` 으로 설정되었고 LANGUAGE가 명시적으로 `1041` (일본어)로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="307e9-207">FORMAT_STRING is set explicitly to `Short Time` and LANGUAGE is set explicitly to `1041` (Japanese).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="307e9-208">참고 항목</span><span class="sxs-lookup"><span data-stu-id="307e9-208">See Also</span></span>  
 <span data-ttu-id="307e9-209">[MDX &#40;FORMAT_STRING 내용&#41;](mdx-cell-properties-format-string-contents.md) </span><span class="sxs-lookup"><span data-stu-id="307e9-209">[FORMAT_STRING Contents &#40;MDX&#41;](mdx-cell-properties-format-string-contents.md) </span></span>  
 <span data-ttu-id="307e9-210">[MDX &#40;셀 속성 사용&#41;](mdx-cell-properties-using-cell-properties.md) </span><span class="sxs-lookup"><span data-stu-id="307e9-210">[Using Cell Properties &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md) </span></span>  
 <span data-ttu-id="307e9-211">[MDX&#41;&#40;속성 값 만들기 및 사용](../../creating-and-using-property-values-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="307e9-211">[Creating and Using Property Values &#40;MDX&#41;](../../creating-and-using-property-values-mdx.md) </span></span>  
 [<span data-ttu-id="307e9-212">MDX 쿼리 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="307e9-212">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
