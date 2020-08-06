---
title: DirectQuery 모드의 DAX 수식 호환성 (SSAS 2014) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: de83cfa9-9ffe-4e24-9c74-96a3876cb4bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: acaac82d6930787a45281c0e942def8df764f4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649815"
---
# <a name="dax-formula-compatibility-in-directquery-mode-ssas-2014"></a><span data-ttu-id="80b83-102">DirectQuery 모드에서의 DAX 수식 호환성(SSAS 2014)</span><span class="sxs-lookup"><span data-stu-id="80b83-102">DAX Formula Compatibility in DirectQuery Mode (SSAS 2014)</span></span>
<span data-ttu-id="80b83-103">DAX (Data Analysis Expression language)를 사용 하 여 Analysis Services 테이블 형식 모델, [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Excel 통합 문서의 데이터 모델 및 Power BI Desktop 데이터 모델에서 사용할 측정값 및 기타 사용자 지정 수식을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-103">The Data Analysis Expression language (DAX) can be used to create measures and other custom formulas for use in Analysis Services Tabular models, [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] data models in Excel workbooks, and Power BI Desktop data models.</span></span> <span data-ttu-id="80b83-104">대부분의 측면에서 이러한 환경에서 만드는 모델은 동일 하며 동일한 측정값, 관계 및 Kpi 등을 사용할 수 있습니다. 그러나 Analysis Services 테이블 형식 모델을 작성 하 고 DirectQuery 모드에서 배포 하는 경우 사용할 수 있는 수식에 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-104">In most respects, the models you create in these environments are identical, and you can use the same measures, relationships, and KPIs, etc. However, if you author an Analysis Services Tabular model and deploy it in DirectQuery mode, there are some restrictions on the formulas that you can use.</span></span> <span data-ttu-id="80b83-105">이 항목에서는 이러한 차이점에 대 한 개요를 제공 하 고 호환성 수준 1100 또는 1103 및 DirectQuery 모드에서 SQL Server 2014 Analysis Services tabulars 모델에서 지원 되지 않는 함수를 나열 하 고, 지원 되지만 다른 결과를 반환할 수 있는 함수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-105">This topic provides an overview of those differences, lists the functions that are not supported in SQL Server 2014 Analysis Services tabulars model at compatibility level 1100 or 1103 and in DirectQuery mode, and lists the functions that are supported but might return different results.</span></span>  
  
<span data-ttu-id="80b83-106">이 항목에서는 *메모리 내 모델* 이라는 용어를 사용 하 여 테이블 형식 모드에서 실행 되는 Analysis Services 서버에서 완전히 호스팅되는 메모리 내 캐시 된 데이터 인 테이블 형식 모델을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-106">Within this topic, we use the term *in-memory model* to refer to  Tabular models, which are fully hosted in-memory cached data on an Analysis Services server running in Tabular mode.</span></span> <span data-ttu-id="80b83-107">Directquery *모델* 을 사용 하 여 directquery 모드로 제작 및/또는 배포 된 테이블 형식 모델을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-107">We use *DirectQuery models* to refer to Tabular models that have been authored and/or deployed in DirectQuery mode.</span></span> <span data-ttu-id="80b83-108">DirectQuery 모드에 대 한 자세한 내용은 [Directquery 모드 (SSAS 테이블 형식)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80b83-108">For information about DirectQuery mode, see [DirectQuery Mode (SSAS Tabular)](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5).</span></span>  
  
  
## <a name="differences-between-in-memory-and-directquery-mode"></a><a name="bkmk_SemanticDifferences"></a><span data-ttu-id="80b83-109">메모리 내 모드와 DirectQuery 모드 간의 차이점</span><span class="sxs-lookup"><span data-stu-id="80b83-109">Differences between in-memory and DirectQuery mode</span></span>  
<span data-ttu-id="80b83-110">DirectQuery 모드로 배포된 모델에 대한 쿼리에서는 동일한 모델이 메모리 내 모드로 배포되었을 때와 다른 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-110">Queries on a model deployed in DirectQuery mode can return different results than the same model deployed in in-memory mode.</span></span> <span data-ttu-id="80b83-111">DirectQuery를 사용 하는 경우 데이터가 관계형 데이터 저장소에서 직접 쿼리 되 고 수식에 필요한 집계가 저장소 및 계산에 대 한 VertiPaq (메모리 내 분석 엔진)의 xVelocity를 사용 하는 대신 관련 관계형 엔진을 사용 하 여 수행 되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-111">This is because with DirectQuery, data is queried directly from a relational data store and aggregations required by formulas are performed using the relevant relational engine, rather than using the xVelocity in-memory analytics engine (VertiPaq) for storage and calculation.</span></span>  
  
<span data-ttu-id="80b83-112">예를 들어 일부 관계형 데이터 저장소는 숫자 값, 날짜, Null 등을 처리하는 방식에 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-112">For example, there are differences in the way that certain relational data stores handle numeric values, dates, nulls, and so forth.</span></span>  
  
<span data-ttu-id="80b83-113">반면 DAX 언어는 Microsoft Excel의 함수 동작을 가능한 한 비슷하게 에뮬레이트하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-113">In contrast, the DAX language is intended to emulate as closely as possible the behavior of functions in Microsoft Excel.</span></span> <span data-ttu-id="80b83-114">예를 들어 Null, 빈 문자열 및 0 값을 처리할 때 Excel에서는 정확한 데이터 형식에 관계없이 최상의 답을 제공하려고 하므로 xVelocity 엔진에서도 이와 동일하게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-114">For example, when handling nulls, empty strings and zero values, Excel attempts to provide the best answer regardless of the precise data type, and therefore the xVelocity engine does the same.</span></span> <span data-ttu-id="80b83-115">그러나 DirectQuery 모드로 배포된 테이블 형식 모델에서 평가를 위해 관계형 데이터 원본에 수식을 전달할 경우 데이터는 관계형 데이터 원본의 의미 체계에 따라 처리되어야 합니다. 이 경우 일반적으로 빈 문자열과 Null은 서로 다르게 처리되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-115">However, when a tabular model is deployed in DirectQuery mode and passes formulas to a relational data source for evaluation, the data must be handled according to the semantics of the relational data source, which typically require distinct handling of empty strings vs. nulls.</span></span> <span data-ttu-id="80b83-116">이 때문에 동일한 수식이라도 캐시된 데이터에 대해 실행될 때와 관계형 저장소에서만 인출된 데이터에 대해 실행될 때 서로 다른 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-116">For this reason, the same formula might return a different result when evaluated against cached data and against data returned solely from the relational store.</span></span>  
  
<span data-ttu-id="80b83-117">또한 일부 함수는 현재 컨텍스트의 데이터를 관계형 데이터 원본에 매개 변수로 전송 해야 하므로 일부 함수는 DirectQuery 모드에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-117">Additionally, some functions cannot be used at all in DirectQuery mode because the calculation would require the data in the current context be sent to the relational data source as a parameter.</span></span> <span data-ttu-id="80b83-118">예를 들어 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 통합 문서의 측정값은 통합 문서 내에서 사용할 수 있는 날짜 범위를 참조 하는 시간 인텔리전스 함수를 사용 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-118">For example, measures in a [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] workbook often use time-intelligence functions that reference date ranges available within the workbook.</span></span> <span data-ttu-id="80b83-119">이러한 수식은 일반적으로 DirectQuery 모드에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-119">Such formulas generally cannot be used in DirectQuery mode.</span></span>  
  
## <a name="semantic-differences"></a><span data-ttu-id="80b83-120">의미 체계 차이점</span><span class="sxs-lookup"><span data-stu-id="80b83-120">Semantic differences</span></span>  
<span data-ttu-id="80b83-121">이 섹션에서는 예상 가능한 의미 체계 차이점의 유형을 나열하고 함수 사용 또는 쿼리 결과에 적용될 수 있는 제한 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-121">This section lists the types of semantic differences that you can expect, and describes any limitations that might apply to the usage of functions or to query results.</span></span>  
  
### <a name="comparisons"></a><a name="bkmk_Comparisons"></a><span data-ttu-id="80b83-122">비교</span><span class="sxs-lookup"><span data-stu-id="80b83-122">Comparisons</span></span>  
<span data-ttu-id="80b83-123">메모리 내 모델에서 DAX는 서로 다른 데이터 형식의 스칼라 값으로 확인되는 두 식의 비교를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-123">DAX in in-memory models support comparisons of two expressions that resolve to scalar values of different data types.</span></span> <span data-ttu-id="80b83-124">그러나 DirectQuery 모드로 배포된 모델에서는 관계형 엔진의 데이터 형식 및 비교 연산자를 사용하므로 다른 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-124">However, models that are deployed in DirectQuery mode use the data types and comparison operators of the relational engine, and therefore might return different results.</span></span>  
  
<span data-ttu-id="80b83-125">다음 비교는 DirectQuery 데이터 원본에 대한 계산에 사용될 경우 항상 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-125">The following comparisons will always return an error when used in a calculation on a DirectQuery data source:</span></span>  
  
-   <span data-ttu-id="80b83-126">숫자 데이터 형식과 문자열 데이터 형식 비교</span><span class="sxs-lookup"><span data-stu-id="80b83-126">Numeric data type compared to any string data type</span></span>  
  
-   <span data-ttu-id="80b83-127">숫자 데이터 형식과 부울 값 비교</span><span class="sxs-lookup"><span data-stu-id="80b83-127">Numeric data type compared to a Boolean value</span></span>  
  
-   <span data-ttu-id="80b83-128">문자열 데이터 형식과 부울 값 비교</span><span class="sxs-lookup"><span data-stu-id="80b83-128">Any string data type compared to a Boolean value</span></span>  
  
<span data-ttu-id="80b83-129">일반적으로 메모리 내 모델에서 DAX는 데이터 형식 불일치에 보다 관대하며, 이 섹션에 설명된 것과 같이 최대 두 번까지 값을 암시적으로 캐스팅하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-129">In general, DAX is more forgiving of data type mismatches in in-memory models and will attempt an implicit cast of values up to two times, as described in this section.</span></span> <span data-ttu-id="80b83-130">그러나 DirectQuery 모드에서 관계형 데이터 저장소로 보내진 수식은 관계형 엔진의 규칙에 따라 더 엄격하게 평가되므로 실패할 가능성이 더 높습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-130">However, formulas sent to a relational data store in DirectQuery mode are evaluated more strictly, following the rules of the relational engine, and are more likely to fail.</span></span>  
  
<span data-ttu-id="80b83-131">**문자열과 숫자 비교**</span><span class="sxs-lookup"><span data-stu-id="80b83-131">**Comparisons of strings and numbers**</span></span>  
<span data-ttu-id="80b83-132">예: `"2" < 3`</span><span class="sxs-lookup"><span data-stu-id="80b83-132">EXAMPLE: `"2" < 3`</span></span>  
  
<span data-ttu-id="80b83-133">이 수식은 텍스트 문자열과 숫자를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-133">The formula compares a text string to a number.</span></span> <span data-ttu-id="80b83-134">이 식은 DirectQuery 모드와 메모리 내 모델 모두에서 **true** 가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-134">The expression is **true** in both DirectQuery mode and in-memory models.</span></span>  
  
<span data-ttu-id="80b83-135">메모리 내 모델에서는 문자열로 표현된 숫자가 다른 숫자와의 비교를 위해 숫자 데이터 형식으로 암시적으로 캐스팅되므로 결과가 **true** 가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-135">In an in-memory model, the result is **true** because numbers as strings are implicitly cast to a numerical data type for comparisons with other numbers.</span></span> <span data-ttu-id="80b83-136">SQL에서도 텍스트 숫자를 숫자 데이터 형식과 비교하기 위해 암시적으로 숫자로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-136">SQL also implicitly casts text numbers as numbers for comparison to numerical data types.</span></span>  
  
<span data-ttu-id="80b83-137">이는 첫 번째 버전의 동작 변경을 나타냅니다 .이는 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 텍스트 "2"가 항상 모든 숫자 보다 큰 것으로 간주 되기 때문에 **false**를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-137">Note that this represents a change in behavior from the first version of [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], which would return **false**, because the text "2" would always be considered larger than any number.</span></span>  
  
<span data-ttu-id="80b83-138">**텍스트와 부울 비교**</span><span class="sxs-lookup"><span data-stu-id="80b83-138">**Comparison of text with Boolean**</span></span>  
<span data-ttu-id="80b83-139">예: `"VERDADERO" = TRUE`</span><span class="sxs-lookup"><span data-stu-id="80b83-139">EXAMPLE: `"VERDADERO" = TRUE`</span></span>  
  
<span data-ttu-id="80b83-140">이 식은 텍스트 문자열을 부울 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-140">This expression compares a text string with a Boolean value.</span></span> <span data-ttu-id="80b83-141">일반적으로 DirectQuery 또는 메모리 내 모델에서는 문자열 값을 부울 값과 비교하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-141">In general, for DirectQuery or In-Memory models, comparing a string value to a Boolean value results in an error.</span></span> <span data-ttu-id="80b83-142">이 규칙의 유일한 예외는 문자열에 **true** 또는 **false**라는 단어가 포함된 경우입니다. 문자열에 true 또는 false 값이 포함되어 있으면 부울로 변환 후 비교가 수행되어 논리적 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-142">The only exceptions to the rule are when the string contains the word **true** or the word **false**; if the string contains any of true or false values, a conversion to Boolean is made and the comparison takes place giving the logical result.</span></span>  
  
<span data-ttu-id="80b83-143">**Null 비교**</span><span class="sxs-lookup"><span data-stu-id="80b83-143">**Comparison of nulls**</span></span>  
<span data-ttu-id="80b83-144">예: `EVALUATE ROW("X", BLANK() = BLANK())`</span><span class="sxs-lookup"><span data-stu-id="80b83-144">EXAMPLE: `EVALUATE ROW("X", BLANK() = BLANK())`</span></span>  
  
<span data-ttu-id="80b83-145">이 수식은 SQL에서 Null에 해당하는 값과 Null을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-145">This formula compares the SQL equivalent of a null to a null.</span></span> <span data-ttu-id="80b83-146">메모리 내 모델과 DirectQuery 모델에서 반환 값은 **true** 이며, DirectQuery 모델에서는 메모리 내 모델과 비슷한 동작을 보장하기 위해 프로비전이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-146">It returns **true** in in-memory and DirectQuery models; a provision is made in DirectQuery model to guarantee similar behavior to in-memory model.</span></span>  
  
<span data-ttu-id="80b83-147">Transact-SQL에서는 Null이 Null과 같을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-147">Note that in Transact-SQL, a null is never equal to a null.</span></span> <span data-ttu-id="80b83-148">그러나 DAX에서는 빈 값이 다른 빈 값과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-148">However, in DAX, a blank is equal to another blank.</span></span> <span data-ttu-id="80b83-149">이 동작은 모든 메모리 내 모델에 대해 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-149">This behavior is the same for all in-memory models.</span></span> <span data-ttu-id="80b83-150">DirectQuery 모드에서는 대부분의 SQL Server 의미 체계를 사용하지만 이 경우에는 NULL 비교에 새로운 동작을 제공하여 SQL Server 의미 체계와 구별된다는 점을 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-150">It is important to note that DirectQuery mode uses, most of, the semantics of SQL Server; but, in this case it separates from it giving a new behavior to NULL comparisons.</span></span>  
  
### <a name="casts"></a><a name="bkmk_Casts"></a><span data-ttu-id="80b83-151">경향성</span><span class="sxs-lookup"><span data-stu-id="80b83-151">Casts</span></span>  
  
<span data-ttu-id="80b83-152">DAX에는 일반적인 의미의 캐스팅 함수는 없지만 많은 비교 및 산술 연산에서 암시적 캐스팅이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-152">There is no cast function as such in DAX, but implicit casts are performed in many comparison and arithmetic operations.</span></span> <span data-ttu-id="80b83-153">결과의 데이터 형식은 비교 또는 산술 연산에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-153">It is the comparison or arithmetic operation that determines the data type of the result.</span></span> <span data-ttu-id="80b83-154">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-154">For example,</span></span>  
  
-   <span data-ttu-id="80b83-155">TRUE + 1과 같은 산술 연산이나 부울 값 열에 적용된 MIN 함수에서 부울 값은 숫자로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-155">Boolean values are treated as numeric in arithmetic operations, such as TRUE + 1, or the function MIN applied to a column of Boolean values.</span></span> <span data-ttu-id="80b83-156">NOT 연산에서도 숫자 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-156">A NOT operation also returns a numeric value.</span></span>  
  
-   <span data-ttu-id="80b83-157">비교에 사용될 때와 EXACT, AND, OR, &amp;&amp;또는 ||와 함께 사용될 때 부울 값은 항상 논리적 값으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-157">Boolean values are always treated as logical values in comparisons and when used with EXACT, AND, OR, &amp;&amp;, or ||.</span></span>  
  
<span data-ttu-id="80b83-158">**문자열에서 부울로 캐스팅**</span><span class="sxs-lookup"><span data-stu-id="80b83-158">**Cast from string to Boolean**</span></span>  
<span data-ttu-id="80b83-159">메모리 내 및 DirectQuery 모델에서는 **""** (빈 문자열), **"true"**, **"False"** 등의 문자열만 부울 값으로 캐스팅할 수 있습니다. 빈 문자열은 false 값으로 캐스팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-159">In in-memory and DirectQuery models, casts are permitted to Boolean values from these strings only: **""** (empty string), **"true"**, **"false"**; where an empty string casts to false value.</span></span>  
  
<span data-ttu-id="80b83-160">다른 문자열을 부울 데이터 형식으로 캐스팅하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-160">Casts to the Boolean data type of any other string results in an error.</span></span>  
  
<span data-ttu-id="80b83-161">**문자열에서 날짜/시간으로 캐스팅**</span><span class="sxs-lookup"><span data-stu-id="80b83-161">**Cast from string to date/time**</span></span>  
<span data-ttu-id="80b83-162">DirectQuery 모드에서 날짜 및 시간의 문자열 표현을 실제 **datetime** 값으로 캐스팅하는 동작은 SQL Server에서와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-162">In DirectQuery mode, casts from string representations of dates and times to actual **datetime** values behave the same way as they do in SQL Server.</span></span>  
  
<span data-ttu-id="80b83-163">모델의 문자열에서 **datetime** 데이터 형식으로의 캐스트를 관리 하는 규칙에 대 한 자세한 내용은 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] [DAX 구문 참조](/dax/dax-syntax-reference)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80b83-163">For information about the rules governing casts from string to **datetime** data types in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] models, see the [DAX Syntax Reference](/dax/dax-syntax-reference).</span></span>
  
<span data-ttu-id="80b83-164">메모리 내 데이터 저장소를 사용하는 모델에서 지원되는 텍스트 형식 날짜의 범위는 SQL Server에서 지원되는 문자열 형식 날짜의 범위보다 제한적입니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-164">Models that use the in-memory data store support a more limited range of text formats for dates than the string formats for dates that are supported by SQL Server.</span></span> <span data-ttu-id="80b83-165">그러나 DAX에서는 사용자 지정 날짜 및 시간 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-165">However, DAX supports custom date and time formats.</span></span>  
  
<span data-ttu-id="80b83-166">**문자열에서 부울이 아닌 다른 값으로 캐스팅**</span><span class="sxs-lookup"><span data-stu-id="80b83-166">**Cast from string to other non Boolean values**</span></span>  
<span data-ttu-id="80b83-167">문자열에서 부울이 아닌 값으로 캐스팅할 때 DirectQuery 모드는 SQL Server와 동일하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-167">When casting from strings to non-Boolean values, DirectQuery mode behaves the same as SQL Server.</span></span> <span data-ttu-id="80b83-168">자세한 내용은 [CAST 및 CONVERT(Transact-SQL)](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80b83-168">For more information, see [CAST and CONVERT (Transact-SQL)](https://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8).</span></span>  
  
<span data-ttu-id="80b83-169">**숫자에서 문자열로의 캐스팅이 허용되지 않음**</span><span class="sxs-lookup"><span data-stu-id="80b83-169">**Cast from numbers to string not allowed**</span></span>  
<span data-ttu-id="80b83-170">예: `CONCATENATE(102,",345")`</span><span class="sxs-lookup"><span data-stu-id="80b83-170">EXAMPLE: `CONCATENATE(102,",345")`</span></span>  
  
<span data-ttu-id="80b83-171">SQL Server에서는 숫자에서 문자열로의 캐스팅이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-171">Casting from numbers to strings is not allowed in SQL Server.</span></span>  
  
<span data-ttu-id="80b83-172">이 수식은 테이블 형식 모델과 DirectQuery 모드에서 오류를 반환하지만 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]에서는 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-172">This formula returns an error in tabular models and in DirectQuery mode; however, the formula produces a result in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)].</span></span>  
  
<span data-ttu-id="80b83-173">**DirectQuery에서 2번의 캐스팅 시도가 지원되지 않음**</span><span class="sxs-lookup"><span data-stu-id="80b83-173">**No support for two-try casts in DirectQuery**</span></span>  
<span data-ttu-id="80b83-174">메모리 내 모델에서는 대개 첫 번째 캐스팅 시도가 실패하면 두 번째 캐스팅을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-174">In-memory models often attempt a second cast when the first one fails.</span></span> <span data-ttu-id="80b83-175">DirectQuery 모드에서는 두 번째 시도가 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-175">This never happens in DirectQuery mode.</span></span>  
  
<span data-ttu-id="80b83-176">예: `TODAY() + "13:14:15"`</span><span class="sxs-lookup"><span data-stu-id="80b83-176">EXAMPLE: `TODAY() + "13:14:15"`</span></span>  
  
<span data-ttu-id="80b83-177">이 식에서 첫 번째 매개 변수는 **datetime** 형식이고 두 번째 매개 변수는 **string**형식입니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-177">In this expression, the first parameter has type **datetime** and second parameter has type **string**.</span></span> <span data-ttu-id="80b83-178">그러나 피연산자를 결합할 때 캐스팅은 다르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-178">However, the casts when combining the operands are handled differently.</span></span> <span data-ttu-id="80b83-179">DAX에서는 **string** 에서 **double**로의 암시적 캐스팅을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-179">DAX will perform an implicit cast from **string** to **double**.</span></span> <span data-ttu-id="80b83-180">메모리 내 모델에서는 수식 엔진이 **double**로 직접 캐스팅하려고 시도하고, 이 시도가 실패하면 문자열을 **datetime**으로 캐스팅하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-180">In in-memory models, the formula engine attempts to cast directly to **double**, and if that fails, it will try to cast the string to **datetime**.</span></span>  
  
<span data-ttu-id="80b83-181">DirectQuery 모드에서는 **string** 에서 **double** 로의 직접 캐스팅만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-181">In DirectQuery mode, only the direct cast from **string** to **double** will be applied.</span></span> <span data-ttu-id="80b83-182">이 캐스팅이 실패하면 수식에서 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-182">If this cast fails, the formula will return an error.</span></span>  
  
### <a name="math-functions-and-arithmetic-operations"></a><a name="bkmk_Math"></a><span data-ttu-id="80b83-183">수학 함수 및 산술 연산</span><span class="sxs-lookup"><span data-stu-id="80b83-183">Math functions and arithmetic operations</span></span>  
<span data-ttu-id="80b83-184">일부 수학 함수의 경우 DirectQuery 모드에서는 기본 데이터 형식과 연산에서 적용할 수 있는 캐스팅에 차이가 있기 때문에 다른 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-184">Some mathematical functions will return different results in DirectQuery mode because of differences in the underlying data type or the casts that can be applied in operations.</span></span> <span data-ttu-id="80b83-185">또한 위에서 설명한 허용되는 값 범위에 대한 제한으로 인해 산술 연산의 결과가 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-185">Also, the restrictions described above on the allowed range of values might affect the outcome of arithmetic operations.</span></span>  
  
<span data-ttu-id="80b83-186">**더하기 순서**</span><span class="sxs-lookup"><span data-stu-id="80b83-186">**Order of addition**</span></span>  
<span data-ttu-id="80b83-187">일련의 숫자를 더하는 수식을 만들 때 메모리 내 모델에서는 DirectQuery 모델에서와 다른 순서로 숫자를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-187">When you create a formula that adds a series of numbers, an in-memory model might process the numbers in a different order than a DirectQuery model.</span></span>  <span data-ttu-id="80b83-188">따라서 매우 큰 양수와 매우 큰 음수가 여러 개 있을 경우 연산에 따라 오류가 발생할 수도 있고 결과가 반환될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-188">Therefore, when you have many very large positive numbers and very large negative numbers, you may get an error in one operation and results in another operation.</span></span>  
  
<span data-ttu-id="80b83-189">**POWER 함수 사용**</span><span class="sxs-lookup"><span data-stu-id="80b83-189">**Use of the POWER function**</span></span>  
<span data-ttu-id="80b83-190">예: `POWER(-64, 1/3)`</span><span class="sxs-lookup"><span data-stu-id="80b83-190">EXAMPLE: `POWER(-64, 1/3)`</span></span>  
  
<span data-ttu-id="80b83-191">DirectQuery 모드에서 POWER 함수는 분수 지수로 제곱할 경우 음수 값을 밑수로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-191">In DirectQuery mode, the POWER function cannot use negative values as the base when raised to a fractional exponent.</span></span> <span data-ttu-id="80b83-192">이는 SQL Server에서 예상되는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-192">This is the expected behavior in SQL Server.</span></span>  
  
<span data-ttu-id="80b83-193">메모리 내 모델에서 이 수식은 -4를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-193">In an in-memory model, the formula returns -4.</span></span>  
  
<span data-ttu-id="80b83-194">**숫자 오버플로 연산**</span><span class="sxs-lookup"><span data-stu-id="80b83-194">**Numerical overflow operations**</span></span>  
<span data-ttu-id="80b83-195">Transact-SQL에서 숫자 오버플로를 발생시키는 연산을 수행하면 오버플로 오류가 반환됩니다. 따라서 오버플로를 발생시키는 수식은 DirectQuery 모드에서도 오류를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-195">In Transact-SQL, operations that result in a numerical overflow return an overflow error; therefore, formulas that result in an overflow also raise an error in DirectQuery mode.</span></span>  
  
<span data-ttu-id="80b83-196">그러나 동일한 수식을 메모리 내 모델에서 사용할 경우에는 8바이트 정수가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-196">However, the same formula when used in an in-memory model returns an eight-byte integer.</span></span> <span data-ttu-id="80b83-197">이는 수식 엔진이 숫자 오버플로에 대한 검사를 수행하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-197">That is because the formula engine does not perform checks for numerical overflows.</span></span>  
  
<span data-ttu-id="80b83-198">**빈 값을 사용하는 LOG 함수에서 다른 결과가 반환됨**</span><span class="sxs-lookup"><span data-stu-id="80b83-198">**LOG functions with blanks return different results**</span></span>  
<span data-ttu-id="80b83-199">SQL Server에서는 Null과 빈 값을 xVelocity 엔진과는 다르게 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-199">SQL Server handles nulls and blanks differently than the xVelocity engine.</span></span> <span data-ttu-id="80b83-200">따라서 다음 수식은 DirectQuery 모드에서 오류를 반환 하지만 메모리 내 모드에서는 infinity (-inf)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-200">As a result, the following formula returns an error in DirectQuery mode, but return infinity (-inf) in in-memory mode.</span></span>  
  
`EXAMPLE: LOG(blank())`  
  
<span data-ttu-id="80b83-201">LOG10 및 LN 등의 다른 로그 함수에도 동일한 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-201">The same limitations apply to the other logarithmic functions: LOG10 and LN.</span></span>  
  
<span data-ttu-id="80b83-202">DAX에서의 **blank** 데이터 형식에 대한 자세한 내용은 [DAX 구문 참조](/dax/dax-syntax-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80b83-202">For more information about the **blank** data type in DAX, see [DAX Syntax Reference](/dax/dax-syntax-reference).</span></span>
  
<span data-ttu-id="80b83-203">**0으로 나누기 및 빈 값으로 나누기**</span><span class="sxs-lookup"><span data-stu-id="80b83-203">**Division by 0 and division by Blank**</span></span>  
<span data-ttu-id="80b83-204">DirectQuery 모드에서 0으로 나누기나 빈 값으로 나누기는 항상 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-204">In DirectQuery mode, division by zero (0) or division by BLANK will always result in an error.</span></span> <span data-ttu-id="80b83-205">SQL Server에서는 무한대 개념이 지원되지 않으며 0으로 나누기의 자연적인 결과는 무한대이므로 결과가 오류가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-205">SQL Server does not support the notion of infinity, and because the natural result of any division by 0 is infinity, the result is an error.</span></span> <span data-ttu-id="80b83-206">그러나 SQL Server에서 Null로 나누기는 지원되므로 결과가 항상 Null과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-206">However, SQL Server supports division by nulls, and the result must always equal null.</span></span>  
  
<span data-ttu-id="80b83-207">DirectQuery 모드에서는 이러한 연산에 대해 다른 결과가 반환되지 않고 대신 두 유형의 연산(0으로 나누기 및 Null로 나누기) 모두 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-207">Rather than return different results for these operations, in DirectQuery mode, both types of operations (division by zero and division by null) return an error.</span></span>  
  
<span data-ttu-id="80b83-208">Excel 및 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 모델에서도 0으로 나누기는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-208">Note that, in Excel and in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] models, division by zero also returns an error.</span></span> <span data-ttu-id="80b83-209">빈 값으로 나누기는 빈 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-209">Division by a blank returns a blank.</span></span>  
  
<span data-ttu-id="80b83-210">다음 식은 메모리 내 모델에서는 모두 유효하지만 DirectQuery 모드에서는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-210">The following expressions are all valid in in-memory models, but will fail in DirectQuery mode:</span></span>  
  
`1/BLANK`  
  
`1/0`  
  
`0.0/BLANK`  
  
`0/0`  
  
<span data-ttu-id="80b83-211">`BLANK/BLANK` 식은 메모리 내 모델과 DirectQuery 모드 모두에서 `BLANK` 를 반환하는 특수한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-211">The expression `BLANK/BLANK` is a special case that returns `BLANK` in both for in-memory models, and in DirectQuery mode.</span></span>  
  
### <a name="supported-numeric-and-date-time-ranges"></a><a name="bkmk_Ranges"></a><span data-ttu-id="80b83-212">지원되는 숫자 및 날짜-시간 범위</span><span class="sxs-lookup"><span data-stu-id="80b83-212">Supported numeric and date-time ranges</span></span>  
<span data-ttu-id="80b83-213">[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]및 테이블 형식 모델의 수식은 실수 및 날짜에 대 한 최대 허용 값과 관련 하 여 Excel과 동일한 제한 사항이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-213">Formulas in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] and tabular models in-memory are subject to the same limitations as Excel with regard to maximum allowed values for real numbers and dates.</span></span> <span data-ttu-id="80b83-214">그러나 계산 또는 쿼리에서 최대값이 반환되거나 값에 변환, 캐스팅, 반올림 또는 잘림이 적용되는 경우에는 차이점이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-214">However, differences can arise when the maximum value is returned from a calculation or query, or when values are converted, cast, rounded, or truncated.</span></span>  
  
-   <span data-ttu-id="80b83-215">**Currency** 및 **Real** 형식의 값을 곱할 경우 결과가 가능한 최대값보다 크면 DirectQuery 모드에서는 오류가 발생하지 않고 Null이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-215">If values of types **Currency** and **Real** are multiplied, and the result is larger than the maximum possible value, in DirectQuery mode, no error is raised, and a null is returned.</span></span>  
  
-   <span data-ttu-id="80b83-216">메모리 내 모델에서는 오류가 발생하지 않고 최대값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-216">In in-memory models, no error is raised, but the maximum value is returned.</span></span>  
  
<span data-ttu-id="80b83-217">일반적으로 Excel과 SQL Server에서는 허용되는 날짜 범위가 다르므로 날짜가 다음 날짜를 포함하여 일반적인 날짜 범위 내에 있는 경우에만 결과가 일치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-217">In general, because the accepted date ranges are different for Excel and SQL Server, results can be guaranteed to match only when dates are within the common date range, which is inclusive of the following dates:</span></span>  
  
-   <span data-ttu-id="80b83-218">가장 빠른 날짜: 1990년 3월 1일</span><span class="sxs-lookup"><span data-stu-id="80b83-218">Earliest date: March 1, 1990</span></span>  
  
-   <span data-ttu-id="80b83-219">가장 늦은 날짜: 9999년 12월 31일</span><span class="sxs-lookup"><span data-stu-id="80b83-219">Latest date: December 31, 9999</span></span>  
  
<span data-ttu-id="80b83-220">수식에 사용된 날짜가 이 범위를 벗어나면 수식에서 오류가 발생하거나 결과가 일치하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-220">If any dates used in formulas fall outside this range, either the formula will result in an error, or the results will not match.</span></span>  
  
<span data-ttu-id="80b83-221">**CEILING에서 지원되는 부동 소수점 값**</span><span class="sxs-lookup"><span data-stu-id="80b83-221">**Floating point values supported by CEILING**</span></span>  
<span data-ttu-id="80b83-222">예: `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`</span><span class="sxs-lookup"><span data-stu-id="80b83-222">EXAMPLE: `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`</span></span>  
  
<span data-ttu-id="80b83-223">DAX CEILING에 해당하는 Transact-SQL 함수는 크기가 10^19 이하인 값만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-223">The Transact-SQL equivalent of the DAX CEILING function only supports values with magnitude of 10^19 or less.</span></span> <span data-ttu-id="80b83-224">일반적으로 부동 소수점 값은 **bigint**에 맞출 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-224">A rule of thumb is that floating point values should be able to fit into **bigint**.</span></span>  
  
<span data-ttu-id="80b83-225">**범위 외의 날짜를 사용하는 Datepart 함수**</span><span class="sxs-lookup"><span data-stu-id="80b83-225">**Datepart functions with dates that are out of range**</span></span>  
<span data-ttu-id="80b83-226">인수로 사용된 날짜가 유효한 날짜 범위에 있는 경우에만 DirectQuery 모드의 결과와 메모리 내 모델의 결과가 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-226">Results in DirectQuery mode are guaranteed to match those in in-memory models only when the date used as the argument is in the valid date range.</span></span> <span data-ttu-id="80b83-227">이러한 조건이 충족되지 않으면 오류가 발생하거나, DirectQuery에서 반환되는 수식 결과와 메모리 내 모드에서 반환되는 수식 결과가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-227">If these conditions are not satisfied, either an error will be raised, or the formula will return different results in DirectQuery than in in-memory mode.</span></span>  
  
<span data-ttu-id="80b83-228">예: `MONTH(0)` 또는 `YEAR(0)`</span><span class="sxs-lookup"><span data-stu-id="80b83-228">EXAMPLE: `MONTH(0)` or `YEAR(0)`</span></span>  
  
<span data-ttu-id="80b83-229">DirectQuery 모드에서 이 두 식은 각각 12와 1899를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-229">In DirectQuery mode, the expressions return 12 and 1899, respectively.</span></span>  
  
<span data-ttu-id="80b83-230">메모리 내 모델에서 이 두 식은 각각 1과 1900을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-230">In in-memory models, the expressions return 1 and 1900, respectively.</span></span>  
  
<span data-ttu-id="80b83-231">예:  `EOMONTH(0.0001, 1)`</span><span class="sxs-lookup"><span data-stu-id="80b83-231">EXAMPLE:  `EOMONTH(0.0001, 1)`</span></span>  
  
<span data-ttu-id="80b83-232">이 식의 결과는 매개 변수로 제공된 데이터가 유효한 날짜 범위 내에 있는 경우에만 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-232">The results of this expression will match only when the data supplied as a parameter is within the valid date range.</span></span>  
  
<span data-ttu-id="80b83-233">예: `EOMONTH(blank(), blank())` 또는 `EDATE(blank(), blank())`</span><span class="sxs-lookup"><span data-stu-id="80b83-233">EXAMPLE: `EOMONTH(blank(), blank())` or `EDATE(blank(), blank())`</span></span>  
  
<span data-ttu-id="80b83-234">이 식의 결과는 DirectQuery 모드와 메모리 내 모드에서 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-234">The results of this expression should be the same in DirectQuery mode and in-memory mode.</span></span>  
  
<span data-ttu-id="80b83-235">**시간 값 잘림**</span><span class="sxs-lookup"><span data-stu-id="80b83-235">**Truncation of time values**</span></span>  
<span data-ttu-id="80b83-236">예: `SECOND(1231.04097222222)`</span><span class="sxs-lookup"><span data-stu-id="80b83-236">EXAMPLE: `SECOND(1231.04097222222)`</span></span>  
  
<span data-ttu-id="80b83-237">DirectQuery 모드에서는 SQL Server 규칙에 따라 결과가 잘리고 식은 59로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-237">In DirectQuery mode, the result is truncated, following the rules of SQL Server, and the expression evaluates to 59.</span></span>  
  
<span data-ttu-id="80b83-238">메모리 내 모델에서는 각 중간 연산의 결과가 반올림되므로 식이 0으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-238">In in-memory models, the results of each interim operation are rounded; therefore, the expression evaluates to 0.</span></span>  
  
<span data-ttu-id="80b83-239">다음 예에서는 이 값이 계산되는 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-239">The following example demonstrates how this value is calculated:</span></span>  
  
1.  <span data-ttu-id="80b83-240">입력의 소수 부분(0.04097222222)에 24를 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-240">The fraction of the input (0.04097222222) is multiplied by 24.</span></span>  
  
2.  <span data-ttu-id="80b83-241">결과 시간 값(0.98333333328)에 60을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-241">The resulting hour value (0.98333333328) is multiplied by 60.</span></span>  
  
3.  <span data-ttu-id="80b83-242">결과 분 값은 58.9999999968입니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-242">The resulting minute value is 58.9999999968.</span></span>  
  
4.  <span data-ttu-id="80b83-243">분 값의 소수 부분(0.9999999968)에 60을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-243">The fraction of the minute value (0.9999999968) is multiplied by 60.</span></span>  
  
5.  <span data-ttu-id="80b83-244">결과 초 값(59.999999808)이 60으로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-244">The resulting second value (59.999999808) rounds up to 60.</span></span>  
  
6.  <span data-ttu-id="80b83-245">60은 0과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-245">60 is equivalent to 0.</span></span>  
  
<span data-ttu-id="80b83-246">**SQL Time 데이터 형식이 지원되지 않음**</span><span class="sxs-lookup"><span data-stu-id="80b83-246">**SQL Time data type not supported**</span></span>  
<span data-ttu-id="80b83-247">메모리 내 모델은 새로운 SQL **Time** 데이터 형식의 사용을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-247">In-memory models do not support use of the new SQL **Time** data type.</span></span> <span data-ttu-id="80b83-248">DirectQuery 모드에서 이 데이터 형식의 열을 참조하는 수식은 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-248">In DirectQuery mode, formulas that reference columns with this data type will return an error.</span></span> <span data-ttu-id="80b83-249">Time 데이터 열은 메모리 내 모델로 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-249">Time data columns cannot be imported into an in-memory model.</span></span>  
  
<span data-ttu-id="80b83-250">그러나 캐시 된 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 모델에서는 엔진이 시간 값을 허용 가능한 데이터 형식으로 캐스팅 하 고 수식에서 결과를 반환 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-250">However, in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] and in cached models, sometimes the engine casts the time value to an acceptable data type, and the formula returns a result.</span></span>  
  
<span data-ttu-id="80b83-251">이 동작은 날짜 열을 매개 변수로 사용하는 모든 함수에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-251">This behavior affects all functions that use a date column as a parameter.</span></span>  
  
### <a name="currency"></a><a name="bkmk_Currency"></a><span data-ttu-id="80b83-252">최신</span><span class="sxs-lookup"><span data-stu-id="80b83-252">Currency</span></span>  
<span data-ttu-id="80b83-253">DirectQuery 모드에서는 산술 연산의 결과가 **Currency**형식일 경우 값이 다음 범위 내에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-253">In DirectQuery mode, if the result of an arithmetic operation has the type **Currency**, the value must be within the following range:</span></span>  
  
-   <span data-ttu-id="80b83-254">최소: -922337203685477.5808</span><span class="sxs-lookup"><span data-stu-id="80b83-254">Minimum: -922337203685477.5808</span></span>  
  
-   <span data-ttu-id="80b83-255">최대: 922337203685477.5807</span><span class="sxs-lookup"><span data-stu-id="80b83-255">Maximum: 922337203685477.5807</span></span>  
  
<span data-ttu-id="80b83-256">**Currency 및 Real 데이터 형식 결합**</span><span class="sxs-lookup"><span data-stu-id="80b83-256">**Combining currency and REAL data types**</span></span>  
<span data-ttu-id="80b83-257">예: `Currency sample 1`</span><span class="sxs-lookup"><span data-stu-id="80b83-257">EXAMPLE: `Currency sample 1`</span></span>  
  
<span data-ttu-id="80b83-258">**Currency** 및 **Real** 형식을 곱할 경우 결과가 9223372036854774784(0x7ffffffffffffc00)보다 크면 DirectQuery 모드에서 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-258">If **Currency** and **Real** types are multiplied, and the result is larger than 9223372036854774784 (0x7ffffffffffffc00), DirectQuery mode will not raise an error.</span></span>  
  
<span data-ttu-id="80b83-259">메모리 내 모델에서는 결과의 절대값이 922337203685477.4784보다 크면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-259">In an in-memory model, an error is raised if the absolute value of the result is larger than 922337203685477.4784.</span></span>  
  
<span data-ttu-id="80b83-260">**연산 결과 값이 범위를 벗어남**</span><span class="sxs-lookup"><span data-stu-id="80b83-260">**Operation results in an out-of-range value**</span></span>  
<span data-ttu-id="80b83-261">예: `Currency sample 2`</span><span class="sxs-lookup"><span data-stu-id="80b83-261">EXAMPLE: `Currency sample 2`</span></span>  
  
<span data-ttu-id="80b83-262">두 통화 값에 대한 연산 결과 값이 지정된 범위를 벗어날 경우 메모리 내 모델에서는 오류가 발생하지만 DirectQuery 모델에서는 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-262">If operations on any two currency values result in a value that is outside the specified range, an error is raised in in-memory models, but not in DirectQuery models.</span></span>  
  
<span data-ttu-id="80b83-263">**Currency 및 기타 데이터 형식 결합**</span><span class="sxs-lookup"><span data-stu-id="80b83-263">**Combining currency with other data types**</span></span>  
<span data-ttu-id="80b83-264">통화 값을 다른 숫자 형식의 값으로 나눌 경우 다른 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-264">Division of currency values by values of other numeric types can result in different results.</span></span>  
  
### <a name="aggregation-functions"></a><a name="bkmk_Aggregations"></a><span data-ttu-id="80b83-265">집계 함수</span><span class="sxs-lookup"><span data-stu-id="80b83-265">Aggregation functions</span></span>  
<span data-ttu-id="80b83-266">한 개의 행이 있는 테이블에 대한 통계 함수는 다른 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-266">Statistical functions on a table with one row return different results.</span></span> <span data-ttu-id="80b83-267">빈 테이블에 대한 집계 함수도 메모리 내 모델과 DirectQuery 모드에서 서로 다르게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-267">Aggregation functions over empty tables also behave differently in in-memory models than they do in DirectQuery mode.</span></span>  
  
<span data-ttu-id="80b83-268">**단일 행이 있는 테이블에 대한 통계 함수**</span><span class="sxs-lookup"><span data-stu-id="80b83-268">**Statistical functions over a table with a single row**</span></span>  
<span data-ttu-id="80b83-269">인수로 사용되는 테이블에 단일 행이 포함되어 있으면 DirectQuery 모드에서 STDEV 및 VAR 등의 통계 함수가 Null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-269">If the table that is used as argument contains a single row, in DirectQuery mode, statistical functions such as STDEV and VAR return null.</span></span>  
  
<span data-ttu-id="80b83-270">메모리 내 모델에서 단일 행이 있는 테이블에 대해 STDEV 또는 VAR을 사용하는 수식은 0으로 나누기 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-270">In an in-memory model, a formula that uses STDEV or VAR over a table with a single row returns a division by zero error.</span></span>  
  
### <a name="text-functions"></a><a name="bkmk_Text"></a><span data-ttu-id="80b83-271">텍스트 함수</span><span class="sxs-lookup"><span data-stu-id="80b83-271">Text functions</span></span>  
<span data-ttu-id="80b83-272">관계형 데이터 저장소에서는 Excel과는 다른 텍스트 데이터 형식을 제공하므로 문자열을 검색하거나 부분 문자열에 대한 작업을 수행할 때 다른 결과가 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-272">Because relational data stores provide different text data types than does Excel, you may see different results when searching strings or working with substrings.</span></span> <span data-ttu-id="80b83-273">문자열 길이도 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-273">The length of strings also can be different.</span></span>  
  
<span data-ttu-id="80b83-274">일반적으로 고정 길이의 열을 인수로 사용하는 모든 문자열 조작 함수에서 다른 결과가 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-274">In general, any string manipulation functions that use fixed-size columns as arguments can have different results.</span></span>  
  
<span data-ttu-id="80b83-275">또한 SQL Server에서 일부 텍스트 함수는 Excel에서 제공되지 않는 추가 인수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-275">Additionally, in SQL Server, some text functions support additional arguments that are not provided in Excel.</span></span> <span data-ttu-id="80b83-276">누락된 인수가 필요한 수식의 경우 메모리 내 모델에서는 다른 결과가 반환되거나 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-276">If the formula requires the missing argument you can get different results or errors in the in-memory model.</span></span>  
  
<span data-ttu-id="80b83-277">**LEFT, RIGHT 등을 사용하여 문자를 반환하는 연산에서는 올바르지만 대/소문자가 다른 형태의 문자가 반환되거나 결과가 반환되지 않을 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="80b83-277">**Operations that return a character using LEFT, RIGHT, etc. may return the correct character but in a different case, or no results**</span></span>  
<span data-ttu-id="80b83-278">예: `LEFT(["text"], 2)`</span><span class="sxs-lookup"><span data-stu-id="80b83-278">EXAMPLE: `LEFT(["text"], 2)`</span></span>  
  
<span data-ttu-id="80b83-279">DirectQuery 모드에서는 반환되는 문자의 대/소문자가 항상 데이터베이스에 저장된 문자와 정확히 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-279">In DirectQuery mode, the case of the character that is returned is always exactly the same as the letter that is stored in the database.</span></span> <span data-ttu-id="80b83-280">그러나 xVelocity 엔진에서는 성능 향상을 위해 값 압축 및 인덱싱에 다른 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-280">However, the xVelocity engine uses a different algorithm for compression and indexing of values, to improve performance.</span></span>  
  
<span data-ttu-id="80b83-281">기본적으로는 대/소문자를 구분하지 않지만 악센트는 구분하는 Latin1_General 데이터 정렬이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-281">By default, the Latin1_General collation is used, which is case-insensitive but accent-sensitive.</span></span> <span data-ttu-id="80b83-282">따라서 소문자, 대문자 또는 대/소문자로 된 텍스트 문자열 인스턴스가 여러 개 있는 경우 모든 인스턴스가 동일한 문자열로 간주되어 첫 번째 문자열 인스턴스만 인덱스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-282">Therefore, if there are multiple instances of a text string in lower case, upper case, or mixed case, all instances are considered the same string, and only the first instance of the string is stored in the index.</span></span> <span data-ttu-id="80b83-283">저장된 문자열에 대해 작동하는 모든 텍스트 함수는 인덱싱된 형태의 지정된 부분을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-283">All text functions that operate on stored strings will retrieve the specified portion of the indexed form.</span></span> <span data-ttu-id="80b83-284">따라서 위의 수식 예에서는 전체 열에 대해 첫 번째 인스턴스를 입력으로 사용하여 동일한 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-284">Therefore, the example formula would return the same value for the entire column, using the first instance as the input.</span></span>  
  
[<span data-ttu-id="80b83-285">테이블 형식 모델의 문자열 스토리지 및 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="80b83-285">String Storage and Collation in Tabular Models</span></span>](https://msdn.microsoft.com/8516f0ad-32ee-4688-a304-e705143642ca)  
  
<span data-ttu-id="80b83-286">이 동작은 RIGHT, MID 등의 다른 텍스트 함수에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-286">This behavior also applies to other text functions, including RIGHT, MID, and so forth.</span></span>  
  
<span data-ttu-id="80b83-287">**문자열 길이가 결과에 영향을 줌**</span><span class="sxs-lookup"><span data-stu-id="80b83-287">**String length affects results**</span></span>  
<span data-ttu-id="80b83-288">예: `SEARCH("within string", "sample target  text", 1, 1)`</span><span class="sxs-lookup"><span data-stu-id="80b83-288">EXAMPLE: `SEARCH("within string", "sample target  text", 1, 1)`</span></span>  
  
<span data-ttu-id="80b83-289">SEARCH 함수를 사용하여 문자열을 검색할 경우 대상 문자열이 within string보다 길면 DirectQuery 모드에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-289">If you search for a string using the SEARCH function, and the target string is longer than the within string, DirectQuery mode raises an error.</span></span>  
  
<span data-ttu-id="80b83-290">메모리 내 모델에서는 검색된 문자열이 반환되지만 문자열 길이는 &lt;텍스트 내&gt;의 길이로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-290">In an in-memory model, the searched string is returned, but with its length truncated to the length of &lt;within text&gt;.</span></span>  
  
<span data-ttu-id="80b83-291">예: `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`</span><span class="sxs-lookup"><span data-stu-id="80b83-291">EXAMPLE: `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`</span></span>  
  
<span data-ttu-id="80b83-292">바꿀 문자열의 길이가 원래 문자열의 길이보다 길 경우 DirectQuery 모드에서 이 수식은 Null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-292">If the length of the replacement string is greater than the length of the original string, in DirectQuery mode, the formula returns null.</span></span>  
  
<span data-ttu-id="80b83-293">메모리 내 모델의 경우 이 수식은 원본 문자열과 바꿀 문자열을 연결하는 Excel의 동작을 따라 CACalifornia를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-293">In in-memory models, the formula follows the behavior of Excel, which concatenates the source string and the replacement string, which returns CACalifornia.</span></span>  
  
<span data-ttu-id="80b83-294">**문자열 중간에서 암시적 TRIM**</span><span class="sxs-lookup"><span data-stu-id="80b83-294">**Implicit TRIM in the middle of strings**</span></span>  
<span data-ttu-id="80b83-295">예: `TRIM(" A sample sentence with leading white space")`</span><span class="sxs-lookup"><span data-stu-id="80b83-295">EXAMPLE: `TRIM(" A sample sentence with leading white space")`</span></span>  
  
<span data-ttu-id="80b83-296">DirectQuery 모드에서는 DAX TRIM 함수를 SQL 문 `LTRIM(RTRIM(<column>))`으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-296">DirectQuery mode translates the DAX TRIM function to the SQL statement `LTRIM(RTRIM(<column>))`.</span></span> <span data-ttu-id="80b83-297">따라서 선행 및 후행 공백만 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-297">As a result, only leading and trailing white space is removed.</span></span>  
  
<span data-ttu-id="80b83-298">반면, 메모리 내 모델에서는 동일한 수식이 Excel의 동작을 따라 문자열 내의 공백을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-298">In contrast, the same formula in an in-memory model removes spaces within the string, following the behavior of Excel.</span></span>  
  
<span data-ttu-id="80b83-299">**LEN 함수 사용 시 암시적 RTRIM**</span><span class="sxs-lookup"><span data-stu-id="80b83-299">**Implicit RTRIM with use of LEN function**</span></span>  
<span data-ttu-id="80b83-300">예: `LEN('string_column')`</span><span class="sxs-lookup"><span data-stu-id="80b83-300">EXAMPLE: `LEN('string_column')`</span></span>  
  
<span data-ttu-id="80b83-301">SQL Server와 마찬가지로, DirectQuery 모드에서는 문자열 열의 끝에서 공백을 제거합니다. 즉, 암시적 RTRIM을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-301">Like SQL Server, DirectQuery mode automatically removes white space from the end of string columns: that is, it performs an implicit RTRIM.</span></span> <span data-ttu-id="80b83-302">따라서 문자열에 후행 공백이 있는 경우 LEN 함수를 사용하는 수식에서 다른 값이 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-302">Therefore, formulas that use the LEN function can return different values if the string has trailing spaces.</span></span>  
  
<span data-ttu-id="80b83-303">**메모리 내 모드에서는 SUBSTITUTE에 대한 추가 매개 변수를 지원함**</span><span class="sxs-lookup"><span data-stu-id="80b83-303">**In-memory supports additional parameters for SUBSTITUTE**</span></span>  
<span data-ttu-id="80b83-304">예: `SUBSTITUTE([Title],"Doctor","Dr.")`</span><span class="sxs-lookup"><span data-stu-id="80b83-304">EXAMPLE: `SUBSTITUTE([Title],"Doctor","Dr.")`</span></span>  
  
<span data-ttu-id="80b83-305">예: `SUBSTITUTE([Title],"Doctor","Dr.", 2)`</span><span class="sxs-lookup"><span data-stu-id="80b83-305">EXAMPLE: `SUBSTITUTE([Title],"Doctor","Dr.", 2)`</span></span>  
  
<span data-ttu-id="80b83-306">DirectQuery 모드에서는 세 개의 매개 변수, 즉 열에 대한 참조, 이전 텍스트 및 새 텍스트만 사용하는 이 버전의 함수만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-306">In DirectQuery mode, you can use only the version of this function that has three (3) parameters: a reference to a column, the old text, and the new text.</span></span> <span data-ttu-id="80b83-307">두 번째 수식을 사용하면 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-307">If you use the second formula, an error is raised.</span></span>  
  
<span data-ttu-id="80b83-308">메모리 내 모델에서는 선택적인 네 번째 매개 변수를 사용하여 바꿀 문자열의 인스턴스 번호를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-308">In in-memory models, you can use an optional fourth parameter to specify the instance number of the string to replace.</span></span> <span data-ttu-id="80b83-309">예를 들어 두 번째 인스턴스만 바꾸는 등의 작업을 수행할 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-309">For example, you can replace only the second instance, etc.</span></span>  
  
<span data-ttu-id="80b83-310">**REPT 연산의 문자열 길이에 대한 제한**</span><span class="sxs-lookup"><span data-stu-id="80b83-310">**Restrictions on string lengths for REPT operations**</span></span>  
<span data-ttu-id="80b83-311">메모리 내 모델에서 REPT를 사용하는 연산을 통해 반환되는 문자열의 길이는 32,767자보다 짧아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-311">In in-memory models, the length of a string resulting from an operation using REPT must be less than 32,767 characters.</span></span>  
  
<span data-ttu-id="80b83-312">DirectQuery 모드에서는 이 제한이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-312">This limitation does not apply in DirectQuery mode.</span></span>  
  
<span data-ttu-id="80b83-313">**부분 문자열 연산에서는 문자 형식에 따라 다른 결과가 반환됩니다.**</span><span class="sxs-lookup"><span data-stu-id="80b83-313">**Substring operations return different results depending on character type**</span></span>  
<span data-ttu-id="80b83-314">예: `MID([col], 2, 5)`</span><span class="sxs-lookup"><span data-stu-id="80b83-314">EXAMPLE: `MID([col], 2, 5)`</span></span>  
  
<span data-ttu-id="80b83-315">입력 텍스트가 **varchar** 또는 **nvarchar**일 경우 수식 결과는 항상 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-315">If the input text is **varchar** or **nvarchar**, the result of the formula is always the same.</span></span>  
  
<span data-ttu-id="80b83-316">그러나 텍스트가 고정 길이 문자이 고 \* &lt; num_chars &gt; \* 값이 대상 문자열의 길이 보다 크면 DirectQuery 모드에서는 결과 문자열의 끝에 공백이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-316">However, if the text is a fixed-length character and the value for *&lt;num_chars&gt;* is greater than the length of the target string, in DirectQuery mode, a blank is added at the end of the result string.</span></span>  
  
<span data-ttu-id="80b83-317">메모리 내 모델에서는 결과가 패딩 없이 마지막 문자열 문자에서 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-317">In an in-memory model, the result terminates at the last string character, with no padding.</span></span>  
  
## <a name="functions-supported-in-directquery-mode"></a><a name="bkmk_SupportedFunc"></a><span data-ttu-id="80b83-318">DirectQuery 모드에서 지원 되는 함수</span><span class="sxs-lookup"><span data-stu-id="80b83-318">Functions supported in DirectQuery mode</span></span>  
<span data-ttu-id="80b83-319">다음 DAX 함수는 DirectQuery 모드에서 사용할 수 있지만 앞의 섹션에 설명된 것과 같은 조건이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-319">The following DAX functions can be used in DirectQuery mode, but with the qualifications as described in the preceding section.</span></span>  
  
<span data-ttu-id="80b83-320">**텍스트 함수**</span><span class="sxs-lookup"><span data-stu-id="80b83-320">**Text functions**</span></span>  
  
<span data-ttu-id="80b83-321">CONCATENATE</span><span class="sxs-lookup"><span data-stu-id="80b83-321">CONCATENATE</span></span>  
  
<span data-ttu-id="80b83-322">FIND</span><span class="sxs-lookup"><span data-stu-id="80b83-322">FIND</span></span>  
  
<span data-ttu-id="80b83-323">LEFT</span><span class="sxs-lookup"><span data-stu-id="80b83-323">LEFT</span></span>  
  
<span data-ttu-id="80b83-324">LEN</span><span class="sxs-lookup"><span data-stu-id="80b83-324">LEN</span></span>  
  
<span data-ttu-id="80b83-325">MID</span><span class="sxs-lookup"><span data-stu-id="80b83-325">MID</span></span>  
  
<span data-ttu-id="80b83-326">REPLACE</span><span class="sxs-lookup"><span data-stu-id="80b83-326">REPLACE</span></span>  
  
<span data-ttu-id="80b83-327">REPT</span><span class="sxs-lookup"><span data-stu-id="80b83-327">REPT</span></span>  
  
<span data-ttu-id="80b83-328">RIGHT</span><span class="sxs-lookup"><span data-stu-id="80b83-328">RIGHT</span></span>  
  
<span data-ttu-id="80b83-329">SUBSTITUTE</span><span class="sxs-lookup"><span data-stu-id="80b83-329">SUBSTITUTE</span></span>  
  
<span data-ttu-id="80b83-330">TRIM</span><span class="sxs-lookup"><span data-stu-id="80b83-330">TRIM</span></span>  
  
<span data-ttu-id="80b83-331">**통계 함수**</span><span class="sxs-lookup"><span data-stu-id="80b83-331">**Statistical functions**</span></span>  
  
<span data-ttu-id="80b83-332">COUNT</span><span class="sxs-lookup"><span data-stu-id="80b83-332">COUNT</span></span>  
  
<span data-ttu-id="80b83-333">STDEV.P</span><span class="sxs-lookup"><span data-stu-id="80b83-333">STDEV.P</span></span>  
  
<span data-ttu-id="80b83-334">STDEV.S</span><span class="sxs-lookup"><span data-stu-id="80b83-334">STDEV.S</span></span>  
  
<span data-ttu-id="80b83-335">STDEVX.P</span><span class="sxs-lookup"><span data-stu-id="80b83-335">STDEVX.P</span></span>  
  
<span data-ttu-id="80b83-336">STDEVX.S</span><span class="sxs-lookup"><span data-stu-id="80b83-336">STDEVX.S</span></span>  
  
<span data-ttu-id="80b83-337">VAR.P</span><span class="sxs-lookup"><span data-stu-id="80b83-337">VAR.P</span></span>  
  
<span data-ttu-id="80b83-338">VAR.S</span><span class="sxs-lookup"><span data-stu-id="80b83-338">VAR.S</span></span>  
  
<span data-ttu-id="80b83-339">VARX.P</span><span class="sxs-lookup"><span data-stu-id="80b83-339">VARX.P</span></span>  
  
<span data-ttu-id="80b83-340">VARX.S</span><span class="sxs-lookup"><span data-stu-id="80b83-340">VARX.S</span></span>  
  
<span data-ttu-id="80b83-341">**날짜/시간 함수**</span><span class="sxs-lookup"><span data-stu-id="80b83-341">**Date/time functions**</span></span>  
  
<span data-ttu-id="80b83-342">DATE</span><span class="sxs-lookup"><span data-stu-id="80b83-342">DATE</span></span>  
  
<span data-ttu-id="80b83-343">EDATE</span><span class="sxs-lookup"><span data-stu-id="80b83-343">EDATE</span></span>  
  
<span data-ttu-id="80b83-344">EOMONTH</span><span class="sxs-lookup"><span data-stu-id="80b83-344">EOMONTH</span></span>  
  
<span data-ttu-id="80b83-345">DATE</span><span class="sxs-lookup"><span data-stu-id="80b83-345">DATE</span></span>  
  
<span data-ttu-id="80b83-346">TIME</span><span class="sxs-lookup"><span data-stu-id="80b83-346">TIME</span></span>  
  
<span data-ttu-id="80b83-347">SECOND</span><span class="sxs-lookup"><span data-stu-id="80b83-347">SECOND</span></span>  
  
<span data-ttu-id="80b83-348">**수치 연산 및 숫자 함수**</span><span class="sxs-lookup"><span data-stu-id="80b83-348">**Math and number functions**</span></span>  
  
<span data-ttu-id="80b83-349">CEILING</span><span class="sxs-lookup"><span data-stu-id="80b83-349">CEILING</span></span>  
  
<span data-ttu-id="80b83-350">LN</span><span class="sxs-lookup"><span data-stu-id="80b83-350">LN</span></span>  
  
<span data-ttu-id="80b83-351">LOG</span><span class="sxs-lookup"><span data-stu-id="80b83-351">LOG</span></span>  
  
<span data-ttu-id="80b83-352">LOG10</span><span class="sxs-lookup"><span data-stu-id="80b83-352">LOG10</span></span>  
  
<span data-ttu-id="80b83-353">POWER</span><span class="sxs-lookup"><span data-stu-id="80b83-353">POWER</span></span>  
  
<span data-ttu-id="80b83-354">**DAX 테이블 쿼리**</span><span class="sxs-lookup"><span data-stu-id="80b83-354">**DAX Table queries**</span></span>  
  
<span data-ttu-id="80b83-355">DAX 테이블 쿼리를 사용하여 DirectQuery 모델에 대해 수식을 계산할 때는 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-355">There are some limitations when you evaluate formulas against a DirectQuery model by using DAX Table queries.</span></span> <span data-ttu-id="80b83-356">DirectQuery의 경우 ORDER BY 절에서 동일한 열을 두 번 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-356">DirectQuery does not support referring to the same column twice in an ORDER BY clause.</span></span> <span data-ttu-id="80b83-357">해당하는 Transact-SQL 문을 만들 수 없으며 쿼리가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-357">The equivalent Transact-SQL statement cannot be created and the query fails.</span></span>  
  
<span data-ttu-id="80b83-358">메모리 내 모델에서는 ORDER BY 절을 반복해도 결과에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-358">In an in-memory model, repeating the ORDER by clause has no effect on the results.</span></span>  
  
## <a name="functions-not-supported-in-directquery-mode"></a><a name="bkmk_NotSupportedFunc"></a><span data-ttu-id="80b83-359">DirectQuery 모드에서 지원 되지 않는 함수</span><span class="sxs-lookup"><span data-stu-id="80b83-359">Functions not supported in DirectQuery Mode</span></span>  
<span data-ttu-id="80b83-360">DirectQuery 모드로 배포된 모델에서는 일부 DAX 함수가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-360">Some DAX functions are not supported in models that are deployed in DirectQuery mode.</span></span> <span data-ttu-id="80b83-361">특정 함수가 지원되지 않는 이유에는 다음 중 하나 또는 여러 개가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-361">The reasons that a particular function is not supported can include any or a combination of these reasons:</span></span>  
  
-   <span data-ttu-id="80b83-362">기본 관계형 엔진에서 xVelocity 엔진이 수행하는 계산에 해당하는 계산을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-362">The underlying relational engine cannot perform calculations equivalent to those performed by the xVelocity engine.</span></span>  
  
-   <span data-ttu-id="80b83-363">수식을 해당하는 SQL 식으로 변환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-363">The formula cannot be converted to en equivalent SQL expression.</span></span>  
  
-   <span data-ttu-id="80b83-364">변환된 식 및 결과 계산의 성능이 허용 가능한 수준이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-364">The performance of the converted expression and the resulting calculations would be unacceptable.</span></span>  
  
<span data-ttu-id="80b83-365">다음 DAX 함수는 DirectQuery 모델에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80b83-365">The following DAX functions cannot be used in DirectQuery models.</span></span>  
  
<span data-ttu-id="80b83-366">**경로 함수**</span><span class="sxs-lookup"><span data-stu-id="80b83-366">**Path functions**</span></span>  
  
<span data-ttu-id="80b83-367">PATH</span><span class="sxs-lookup"><span data-stu-id="80b83-367">PATH</span></span>  
  
<span data-ttu-id="80b83-368">PATHCONTAINS</span><span class="sxs-lookup"><span data-stu-id="80b83-368">PATHCONTAINS</span></span>  
  
<span data-ttu-id="80b83-369">PATHITEM</span><span class="sxs-lookup"><span data-stu-id="80b83-369">PATHITEM</span></span>  
  
<span data-ttu-id="80b83-370">PATHITEMREVERSE</span><span class="sxs-lookup"><span data-stu-id="80b83-370">PATHITEMREVERSE</span></span>  
  
<span data-ttu-id="80b83-371">PATHLENGTH</span><span class="sxs-lookup"><span data-stu-id="80b83-371">PATHLENGTH</span></span>  
  
<span data-ttu-id="80b83-372">**기타 함수**</span><span class="sxs-lookup"><span data-stu-id="80b83-372">**Misc functions**</span></span>  
  
<span data-ttu-id="80b83-373">COUNTBLANK</span><span class="sxs-lookup"><span data-stu-id="80b83-373">COUNTBLANK</span></span>  
  
<span data-ttu-id="80b83-374">FIXED</span><span class="sxs-lookup"><span data-stu-id="80b83-374">FIXED</span></span>  
  
<span data-ttu-id="80b83-375">FORMAT</span><span class="sxs-lookup"><span data-stu-id="80b83-375">FORMAT</span></span>  
  
<span data-ttu-id="80b83-376">RAND</span><span class="sxs-lookup"><span data-stu-id="80b83-376">RAND</span></span>  
  
<span data-ttu-id="80b83-377">RANDBETWEEN</span><span class="sxs-lookup"><span data-stu-id="80b83-377">RANDBETWEEN</span></span>  
  
<span data-ttu-id="80b83-378">**시간 인텔리전스 함수: 시작 및 끝 날짜**</span><span class="sxs-lookup"><span data-stu-id="80b83-378">**Time intelligence functions: Start and end dates**</span></span>  
  
<span data-ttu-id="80b83-379">DATESQTD</span><span class="sxs-lookup"><span data-stu-id="80b83-379">DATESQTD</span></span>  
  
<span data-ttu-id="80b83-380">DATESYTD</span><span class="sxs-lookup"><span data-stu-id="80b83-380">DATESYTD</span></span>  
  
<span data-ttu-id="80b83-381">DATESMTD</span><span class="sxs-lookup"><span data-stu-id="80b83-381">DATESMTD</span></span>  
  
<span data-ttu-id="80b83-382">DATESQTD</span><span class="sxs-lookup"><span data-stu-id="80b83-382">DATESQTD</span></span>  
  
<span data-ttu-id="80b83-383">DATESINPERIOD</span><span class="sxs-lookup"><span data-stu-id="80b83-383">DATESINPERIOD</span></span>  
  
<span data-ttu-id="80b83-384">TOTALMTD</span><span class="sxs-lookup"><span data-stu-id="80b83-384">TOTALMTD</span></span>  
  
<span data-ttu-id="80b83-385">TOTALQTD</span><span class="sxs-lookup"><span data-stu-id="80b83-385">TOTALQTD</span></span>  
  
<span data-ttu-id="80b83-386">TOTALYTD</span><span class="sxs-lookup"><span data-stu-id="80b83-386">TOTALYTD</span></span>  
  
<span data-ttu-id="80b83-387">DATESINPERIOD</span><span class="sxs-lookup"><span data-stu-id="80b83-387">DATESINPERIOD</span></span>  
  
<span data-ttu-id="80b83-388">SAMEPERIODLASTYEAR</span><span class="sxs-lookup"><span data-stu-id="80b83-388">SAMEPERIODLASTYEAR</span></span>  
  
<span data-ttu-id="80b83-389">PARALLELPERIOD</span><span class="sxs-lookup"><span data-stu-id="80b83-389">PARALLELPERIOD</span></span>  
  
<span data-ttu-id="80b83-390">**시간 인텔리전스 함수: 잔액**</span><span class="sxs-lookup"><span data-stu-id="80b83-390">**Time-intelligence functions: Balances**</span></span>  
  
<span data-ttu-id="80b83-391">OPENINGBALANCEMONTH</span><span class="sxs-lookup"><span data-stu-id="80b83-391">OPENINGBALANCEMONTH</span></span>  
  
<span data-ttu-id="80b83-392">OPENINGBALANCEQUARTER</span><span class="sxs-lookup"><span data-stu-id="80b83-392">OPENINGBALANCEQUARTER</span></span>  
  
<span data-ttu-id="80b83-393">OPENINGBALANCEYEAR</span><span class="sxs-lookup"><span data-stu-id="80b83-393">OPENINGBALANCEYEAR</span></span>  
  
<span data-ttu-id="80b83-394">CLOSINGBALANCEMONTH</span><span class="sxs-lookup"><span data-stu-id="80b83-394">CLOSINGBALANCEMONTH</span></span>  
  
<span data-ttu-id="80b83-395">CLOSINGBALANCEQUARTER</span><span class="sxs-lookup"><span data-stu-id="80b83-395">CLOSINGBALANCEQUARTER</span></span>  
  
<span data-ttu-id="80b83-396">CLOSINGBALANCEYEAR</span><span class="sxs-lookup"><span data-stu-id="80b83-396">CLOSINGBALANCEYEAR</span></span>  
  
<span data-ttu-id="80b83-397">**시간 인텔리전스 함수: 이전 및 다음 기간**</span><span class="sxs-lookup"><span data-stu-id="80b83-397">**Time intelligence functions: Previous and next periods**</span></span>  
  
<span data-ttu-id="80b83-398">PREVIOUSDAY</span><span class="sxs-lookup"><span data-stu-id="80b83-398">PREVIOUSDAY</span></span>  
  
<span data-ttu-id="80b83-399">PREVIOUSMONTH</span><span class="sxs-lookup"><span data-stu-id="80b83-399">PREVIOUSMONTH</span></span>  
  
<span data-ttu-id="80b83-400">PREVIOUSQUARTER</span><span class="sxs-lookup"><span data-stu-id="80b83-400">PREVIOUSQUARTER</span></span>  
  
<span data-ttu-id="80b83-401">PREVIOUSYEAR</span><span class="sxs-lookup"><span data-stu-id="80b83-401">PREVIOUSYEAR</span></span>  
  
<span data-ttu-id="80b83-402">NEXTDAY</span><span class="sxs-lookup"><span data-stu-id="80b83-402">NEXTDAY</span></span>  
  
<span data-ttu-id="80b83-403">NEXTMONTH</span><span class="sxs-lookup"><span data-stu-id="80b83-403">NEXTMONTH</span></span>  
  
<span data-ttu-id="80b83-404">NEXTQUARTER</span><span class="sxs-lookup"><span data-stu-id="80b83-404">NEXTQUARTER</span></span>  
  
<span data-ttu-id="80b83-405">NEXTYEAR</span><span class="sxs-lookup"><span data-stu-id="80b83-405">NEXTYEAR</span></span>  
  
<span data-ttu-id="80b83-406">**시간 인텔리전스 함수: 기간 및 기간에 대한 계산**</span><span class="sxs-lookup"><span data-stu-id="80b83-406">**Time intelligence functions: Periods and calculations over periods**</span></span>  
  
<span data-ttu-id="80b83-407">STARTOFMONTH</span><span class="sxs-lookup"><span data-stu-id="80b83-407">STARTOFMONTH</span></span>  
  
<span data-ttu-id="80b83-408">STARTOFQUARTER</span><span class="sxs-lookup"><span data-stu-id="80b83-408">STARTOFQUARTER</span></span>  
  
<span data-ttu-id="80b83-409">STARTOFYEAR</span><span class="sxs-lookup"><span data-stu-id="80b83-409">STARTOFYEAR</span></span>  
  
<span data-ttu-id="80b83-410">ENDOFMONTH</span><span class="sxs-lookup"><span data-stu-id="80b83-410">ENDOFMONTH</span></span>  
  
<span data-ttu-id="80b83-411">ENDOFQUARTER</span><span class="sxs-lookup"><span data-stu-id="80b83-411">ENDOFQUARTER</span></span>  
  
<span data-ttu-id="80b83-412">ENDOFYEAR</span><span class="sxs-lookup"><span data-stu-id="80b83-412">ENDOFYEAR</span></span>  
  
<span data-ttu-id="80b83-413">FIRSTDATE</span><span class="sxs-lookup"><span data-stu-id="80b83-413">FIRSTDATE</span></span>  
  
<span data-ttu-id="80b83-414">LASTDATE</span><span class="sxs-lookup"><span data-stu-id="80b83-414">LASTDATE</span></span>  
  
<span data-ttu-id="80b83-415">DATEADD</span><span class="sxs-lookup"><span data-stu-id="80b83-415">DATEADD</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80b83-416">참조</span><span class="sxs-lookup"><span data-stu-id="80b83-416">See also</span></span>  
[<span data-ttu-id="80b83-417">DirectQuery 모드(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="80b83-417">DirectQuery Mode (SSAS Tabular)</span></span>](https://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)  
  

