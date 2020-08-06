---
title: 세계화 팁과 모범 사례 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- translations [Analysis Services], client applications
- date comparisons
- day-of-week comparisons [Analysis Services]
- time [Analysis Services]
- month comparisons [Analysis Services]
ms.assetid: 71a8c438-1370-4c69-961e-d067ee4e47c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: c5bf99878a08e3d2ca57b76e3f902fded2099381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660745"
---
# <a name="globalization-tips-and-best-practices-analysis-services"></a><span data-ttu-id="06e7c-102">세계화 팁과 모범 사례(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="06e7c-102">Globalization Tips and Best Practices (Analysis Services)</span></span>
  <span data-ttu-id="06e7c-103">**[!INCLUDE[applies](../includes/applies-md.md)]** 다차원 전용</span><span class="sxs-lookup"><span data-stu-id="06e7c-103">**[!INCLUDE[applies](../includes/applies-md.md)]**  Multidimensional only</span></span>  
  
 <span data-ttu-id="06e7c-104">다음의 팁 및 지침은 비즈니스 인텔리전스 솔루션의 이식성을 향상시키고 언어 및 데이터 정렬 설정과 직접적으로 관련이 있는 오류를 방지하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-104">These tips and guidelines can help increase the portability of your business intelligence solutions and avoid errors that are directly related to language and collation settings.</span></span>  
  
-   [<span data-ttu-id="06e7c-105">스택 전체에서 유사한 데이터 정렬 사용</span><span class="sxs-lookup"><span data-stu-id="06e7c-105">Use similar collations throughout the stack</span></span>](#bkmk_sameColl)  
  
-   [<span data-ttu-id="06e7c-106">일반적인 데이터 정렬 권장 사항</span><span class="sxs-lookup"><span data-stu-id="06e7c-106">Common collation recommendations</span></span>](#bkmk_recos)  
  
-   [<span data-ttu-id="06e7c-107">개체 식별자의 대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="06e7c-107">Case sensitivity of object identifiers</span></span>](#bkmk_objid)  
  
-   [<span data-ttu-id="06e7c-108">Excel 및 SQL Server Profiler를 사용한 로캘 테스트</span><span class="sxs-lookup"><span data-stu-id="06e7c-108">Locale testing using Excel and SQL Server Profiler</span></span>](#bkmk_test)  
  
-   [<span data-ttu-id="06e7c-109">번역이 포함 된 솔루션에서 MDX 쿼리 작성</span><span class="sxs-lookup"><span data-stu-id="06e7c-109">Writing MDX queries in a solution containing Translations</span></span>](#bkmk_mdx)  
  
-   [<span data-ttu-id="06e7c-110">날짜 및 시간 값이 포함 된 MDX 쿼리 작성</span><span class="sxs-lookup"><span data-stu-id="06e7c-110">Writing MDX queries containing Date and Time Values</span></span>](#bkmk_datetime)  
  
##  <a name="use-similar-collations-throughout-the-stack"></a><a name="bkmk_sameColl"></a><span data-ttu-id="06e7c-111">스택 전체에서 유사한 데이터 정렬 사용</span><span class="sxs-lookup"><span data-stu-id="06e7c-111">Use similar collations throughout the stack</span></span>  
 <span data-ttu-id="06e7c-112">가능하면 데이터베이스 엔진에 사용하는 것과 동일한 데이터 정렬 설정을 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 사용하여 전자/반자 구분 및 대/소문자 구분과 액세스 민감도를 일치시키도록 하세요.</span><span class="sxs-lookup"><span data-stu-id="06e7c-112">If possible, try to use the same collation settings in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you use for the database engine, striving for correspondence in width-sensitivity and case-sensitivity, and access-sensitivity.</span></span>  
  
 <span data-ttu-id="06e7c-113">각 서비스에는 데이터베이스 엔진의 기본값이 SQL_Latin1_General_CP1_CI_AS로 설정되어 있고 Analysis Services가 Latin1_General_AS로 설정되어 있는 자체 데이터 정렬 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-113">Each service has its own collation settings, with the database engine default set to SQL_Latin1_General_CP1_CI_AS and Analysis Services set to Latin1_General_AS.</span></span> <span data-ttu-id="06e7c-114">기본값은 대/소문자, 전자/반자 및 악센트 구분 측면에서 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-114">The defaults are compatible in term of case, width, and accent sensitivity.</span></span> <span data-ttu-id="06e7c-115">두 데이터 정렬 중 하나의 설정을 변경하는 경우 데이터 정렬 속성이 기본 방법에서 벗어나면 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-115">Be forewarned that if you vary the settings of either collation, you can run into problems when the collation properties diverge in fundamental ways.</span></span>  
  
 <span data-ttu-id="06e7c-116">데이터 정렬 설정이 기능적으로 동일한 경우에도 문자열 내 빈 공백이 각 서비스에 의해 다르게 해석되는 특별한 경우가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-116">Even when collation settings are functionally equivalent, you can run into a special case where an empty space anywhere within a string is interpreted differently by each service.</span></span>  
  
 <span data-ttu-id="06e7c-117">공백 문자는 유니코드에서 싱글바이트(SBCS)나 더블바이트 문자 집합(DBCS)으로 표현될 수 있으므로 '특별한 경우'입니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-117">The space character is a 'special case' because it can be represented as a single-byte (SBCS) or double-byte character set (DBCS) in Unicode.</span></span> <span data-ttu-id="06e7c-118">관계형 엔진에서 공백으로 구분되는 두 개의 복합 문자열(SBCS를 사용하는 문자열과 DBCS 문자열)은 동일한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-118">In the relational engine, two compound strings separated by a space -- one using SBCS, the other in DBCS -- are considered identical.</span></span> <span data-ttu-id="06e7c-119">Analysis Services에서는 처리하는 동안 동일한 두 개의 복합 문자열이 동일하지 않고 두 번째 인스턴스는 중복으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-119">In Analysis Services, during processing, the same two compound strings are not identical, and the second instance will be flagged as a duplicate.</span></span>  
  
 <span data-ttu-id="06e7c-120">자세한 내용과 권장 해결 방법에 대해 알려면 [유니코드 문자열의 공백에 데이터 정렬을 기반으로 한 서로 다른 처리 결과가 있는 경우](https://social.technet.microsoft.com/wiki/contents/articles/23979.ssas-processing-error-blanks-in-a-unicode-string-have-different-processing-outcomes-based-on-collation-and-character-set.aspx)(영문)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="06e7c-120">For more details and suggested workarounds, see [Blanks in a Unicode string have different processing outcomes based on collation](https://social.technet.microsoft.com/wiki/contents/articles/23979.ssas-processing-error-blanks-in-a-unicode-string-have-different-processing-outcomes-based-on-collation-and-character-set.aspx).</span></span>  
  
##  <a name="common-collation-recommendations"></a><a name="bkmk_recos"></a> <span data-ttu-id="06e7c-121">일반적인 데이터 정렬 권장 사항</span><span class="sxs-lookup"><span data-stu-id="06e7c-121">Common collation recommendations</span></span>  
 <span data-ttu-id="06e7c-122">Analysis Services에서는 항상 모든 사용 가능한 언어 및 데이터 정렬의 전체 목록을 제공하며, 선택된 언어에 따라 데이터 정렬을 필터링하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-122">Analysis Services always presents the full list of all available languages and collations; it does not filter the collations based on the language you selected.</span></span> <span data-ttu-id="06e7c-123">실행 가능한 조합을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-123">Be sure to choose a workable combination.</span></span>  
  
 <span data-ttu-id="06e7c-124">자주 사용되는 일부 데이터 정렬이 다음 목록에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-124">Some of the more commonly used collations include those in the following list.</span></span>  
  
 <span data-ttu-id="06e7c-125">이 목록은 다른 옵션을 제외하는 분명한 권장 사항이 아니라 추가 조사의 시작점으로 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-125">You should consider this list to be a starting point for further investigation, rather than a definitive recommendation that excludes other options.</span></span> <span data-ttu-id="06e7c-126">특별히 권장되지 않는 데이터 정렬이 데이터에 가장 적합한 데이터 정렬임을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-126">You might find that a collation not specifically recommended is the one that works best for your data.</span></span> <span data-ttu-id="06e7c-127">철저한 테스트는 데이터 값이 적절히 정렬 및 비교되는지 확인하는 유일한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-127">Thorough testing is the only way to verify whether data values are sorted and compared appropriately.</span></span> <span data-ttu-id="06e7c-128">항상 데이터 정렬을 테스트할 때 처리 및 쿼리 작업을 둘 다 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-128">As always, be sure to run both processing and query workloads when testing collation.</span></span>  
  
-   <span data-ttu-id="06e7c-129">Latin1_General_100_AS는 [ISO 기본 라틴어 알파벳](http://en.wikipedia.org/wiki/ISO_basic_Latin_alphabet)의 26자를 사용하는 애플리케이션에 종종 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-129">Latin1_General_100_AS is often used for applications that use the 26 characters of the [ISO basic Latin alphabet](http://en.wikipedia.org/wiki/ISO_basic_Latin_alphabet).</span></span>  
  
-   <span data-ttu-id="06e7c-130">스칸디나비아어 문자(예: ø)를 포함하는 북부 유럽 언어에는 Finnish_Swedish_100을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-130">North European languages that include Scandinavian letters (such as ø) can use Finnish_Swedish_100.</span></span>  
  
-   <span data-ttu-id="06e7c-131">러시아어 같은 동부 유럽 언어에는 종종 Cyrillic_General_100을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-131">East European languages, such as Russian, often use Cyrillic_General_100.</span></span>  
  
-   <span data-ttu-id="06e7c-132">중국어 언어 및 데이터 정렬은 지역에 따라 달라지지만 일반적으로 중국어 언어 또는 중국어 번체의 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-132">Chinese language and collations vary by region, but are generally either Chinese Simplified or Chinese Traditional.</span></span>  
  
     <span data-ttu-id="06e7c-133">PRC 및 싱가포르에서 Microsoft 지원은 중국어 간체를 한어병음과 함께 기본 정렬 순서로 확인하는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-133">In PRC and Singapore, Microsoft Support tends to see Simplified Chinese, with Pinyin as the preferred sort order.</span></span> <span data-ttu-id="06e7c-134">권장 데이터 정렬은 Chinese_PRC(SQL Server 2000), Chinese_PRC_90(SQL Server 2005) 또는 Chinese_Simplified_Pinyin_100(SQL Server 2008 이상)입니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-134">The recommended collations are Chinese_PRC (for SQL Server 2000), Chinese_PRC_90 (for SQL Server 2005) or Chinese_Simplified_Pinyin_100 (for SQL Server 2008 and later).</span></span>  
  
     <span data-ttu-id="06e7c-135">대만에서는 획수에 따른 권장 정렬 순서 Chinese_Taiwan_Stroke(SQL Server 2000), Chinese_Taiwan_Stroke_90(SQL Server 2005) 또는 Chinese_Traditional_Stroke_Count_100(SQL Server 2008 이상)으로 중국어 번체를 확인하는 것이 더 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-135">In Taiwan, it is more common to see Traditional Chinese with the recommended sort order is based on Stroke Count: Chinese_Taiwan_Stroke (for SQL Server 2000), Chinese_Taiwan_Stroke_90 (for SQL Server 2005) or Chinese_Traditional_Stroke_Count_100 (for SQL Server 2008 and later).</span></span>  
  
     <span data-ttu-id="06e7c-136">기타 지역 (예: 홍콩 특별 행정구 및 마카오 특별 행정구)에서는 중국어 번체도 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-136">Other regions (such as Hong Kong SAR and Macao SAR) also use Traditional Chinese.</span></span> <span data-ttu-id="06e7c-137">홍콩에서는 데이터 정렬로 Chinese_Hong_Kong_Stroke_90(SQL Server 2005)을 확인하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-137">For collations, in Hong Kong, it's not unusual to see Chinese_Hong_Kong_Stroke_90 (on SQL Server 2005).</span></span> <span data-ttu-id="06e7c-138">마카오 Chinese_Traditional_Stroke_Count_100 (SQL Server 2008 이상)가 매우 자주 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-138">In Macao, Chinese_Traditional_Stroke_Count_100 (on SQL Server 2008 and later) is used fairly often.</span></span>  
  
-   <span data-ttu-id="06e7c-139">일본어에서 가장 자주 사용되는 데이터 정렬은 Japanese_CI_AS입니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-139">For Japanese, the most commonly used collation is Japanese_CI_AS.</span></span> <span data-ttu-id="06e7c-140">Japanese_XJIS_100은 [JIS2004](http://en.wikipedia.org/wiki/JIS_X_0213)를 지원하는 설치에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-140">Japanese_XJIS_100 is used in installations supporting [JIS2004](http://en.wikipedia.org/wiki/JIS_X_0213).</span></span> <span data-ttu-id="06e7c-141">Japanese_BIN2는 일반적으로 Windows 이외의 플랫폼에서 또는 SQL Server 관계형 데이터베이스 엔진 이외의 데이터 원본에서 가져온 데이터를 사용한 데이터 마이그레이션 프로젝트에서 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-141">Japanese_BIN2 is typically seen in data migration projects, with data originating from non-Windows platforms, or from data sources other than the SQL Server relational database engine.</span></span>  
  
     <span data-ttu-id="06e7c-142">Japanese_Bushu_Kakusu_100은 Analysis Services 작업을 실행하는 서버에서 거의 확인되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-142">Japanese_Bushu_Kakusu_100 is rarely seen in servers that run Analysis Services workloads.</span></span>  
  
-   <span data-ttu-id="06e7c-143">Korean_100은 한국어에 대해 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-143">Korean_100 is recommended for Korean.</span></span> <span data-ttu-id="06e7c-144">Korean_Wansung_Unicode도 목록에 있지만 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-144">Although Korean_Wansung_Unicode is still available in the list, it has been deprecated.</span></span>  
  
##  <a name="case-sensitivity-of-object-identifiers"></a><a name="bkmk_objid"></a> <span data-ttu-id="06e7c-145">개체 식별자의 대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="06e7c-145">Case sensitivity of object identifiers</span></span>  
 <span data-ttu-id="06e7c-146">SQL Server 2012 SP2부터는 개체 ID의 대/소문자 구분이 데이터 정렬과 관계없이 적용됩니다. 하지만 동작은 언어에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-146">Starting in SQL Server 2012 SP2, case sensitivity of object IDs is enforced independently of the collation, but the behavior varies by language:</span></span>  
  
|<span data-ttu-id="06e7c-147">언어 스크립트</span><span class="sxs-lookup"><span data-stu-id="06e7c-147">Language script</span></span>|<span data-ttu-id="06e7c-148">대/소문자 구분</span><span class="sxs-lookup"><span data-stu-id="06e7c-148">Case sensitivity</span></span>|  
|---------------------|----------------------|  
|<span data-ttu-id="06e7c-149">**기본 라틴어 알파벳**</span><span class="sxs-lookup"><span data-stu-id="06e7c-149">**Basic Latin alphabet**</span></span>|<span data-ttu-id="06e7c-150">라틴어 스크립트(26개의 영어 대문자 또는 소문자 중 사용)로 표현되는 개체 식별자는 데이터 정렬과 상관없이 대/소문자를 구분하는 것으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-150">Object identifiers expressed in Latin script (any of the 26 English upper or lower case letters) are treated as case-insensitive, regardless of collation.</span></span> <span data-ttu-id="06e7c-151">예를 들어, 개체 ID 54321**abcdef**, 54321**ABCDEF**, 54321**AbCdEf**는 같다고 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-151">For example, the following object IDs are considered identical: 54321**abcdef**, 54321**ABCDEF**, 54321**AbCdEf**.</span></span> <span data-ttu-id="06e7c-152">내부적으로 Analysis Services에서는 문자열의 문자들을 모두 대문자인 것처럼 처리한 다음 언어에 상관없는 간단한 바이트 비교를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-152">Internally, Analysis Services treats the characters in the string as if all are uppercase, and then performs a simple byte comparison that is independent of language.</span></span><br /><br /> <span data-ttu-id="06e7c-153">26개 문자에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-153">Note that only the 26 characters are affected.</span></span> <span data-ttu-id="06e7c-154">서부 유럽 언어에 스칸디나비아어 문자가 사용되면 추가 문자는 대문자로 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-154">If the language is West European, but uses Scandinavian characters, the additional character will not be upper-cased.</span></span>|  
|<span data-ttu-id="06e7c-155">**키릴자모, 그리스어, 콥트어, 아르메니아어**</span><span class="sxs-lookup"><span data-stu-id="06e7c-155">**Cyrillic, Greek, Coptic, Armenian**</span></span>|<span data-ttu-id="06e7c-156">키릴자모와 같은 비라틴 bicameral 스크립트의 개체 식별자는 항상 대/소문자 구분입니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-156">Object identifiers in non-Latin bicameral script, such as Cyrillic, are always case-sensitive.</span></span> <span data-ttu-id="06e7c-157">예를 들어, Измерение 및 измерение은 유일한 차이점이 첫 글자의 대소문자 여부임에도 불구하고 두 개의 서로 다른 값으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-157">For example, Измерение and измерение are considered two distinct values, even though the only difference is the case of the first letter.</span></span>|  
  
 <span data-ttu-id="06e7c-158">**개체 식별자에 대한 대/소문자 구분의 의미**</span><span class="sxs-lookup"><span data-stu-id="06e7c-158">**Implications of case-sensitivity for object identifiers**</span></span>  
  
 <span data-ttu-id="06e7c-159">개체 이름이 아니라 개체 식별자만 표에 설명된 대/소문자 구분 동작이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-159">Only object identifiers, and not object names, are subject to the casing behaviors described in the table.</span></span> <span data-ttu-id="06e7c-160">솔루션 작동 방식에 변화가 있는 경우(전후 비교 -- SQL Server 2012 SP2 이상 설치 후), 처리 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-160">If you see a change in how your solution works (a before and after comparison -- after installing SQL Server 2012 SP2 or later), it will most likely be a processing issue.</span></span> <span data-ttu-id="06e7c-161">쿼리는 개체 식별자에 의해 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-161">Queries are not impacted by object identifiers.</span></span> <span data-ttu-id="06e7c-162">두 쿼리 언어(DAX 및 MDX)에서 수식 엔진에 개체 이름(식별자 아님)이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-162">For both query languages (DAX and MDX), the formula engine uses the object name (not the identifier).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06e7c-163">대/소문자 구분과 관련된 코드 변경 내용은 일부 애플리케이션에 대한 주요 변경 내용이었습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-163">Code changes related to case-sensitivity have been a breaking change for some applications.</span></span> <span data-ttu-id="06e7c-164">자세한 내용은 [SQL Server 2014에서 Analysis Services 기능의 주요 변경](breaking-changes-to-analysis-services-features-in-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="06e7c-164">See [Breaking Changes to Analysis Services Features in SQL Server 2014](breaking-changes-to-analysis-services-features-in-sql-server-2014.md) for more information.</span></span>  
  
##  <a name="locale-testing-using-excel-sql-server-profiler-and-sql-server-management-studio"></a><a name="bkmk_test"></a> <span data-ttu-id="06e7c-165">Excel, SQL Server Profiler 및 SQL Server Management Studio를 사용한 로캘 테스트</span><span class="sxs-lookup"><span data-stu-id="06e7c-165">Locale testing using Excel, SQL Server Profiler and SQL Server Management Studio</span></span>  
 <span data-ttu-id="06e7c-166">번역을 테스트할 때 연결에서 번역의 LCID를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-166">When testing translations, the connection must specify the LCID of the translation.</span></span> <span data-ttu-id="06e7c-167">[다른 언어를 SSAS에서 Excel로 가져오기](http://extremeexperts.com/sql/Tips/ExcelDiffLocale.aspx)(영문)에 설명된 대로 Excel을 사용하여 번역을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-167">As documented in [Get Different Language from SSAS into Excel](http://extremeexperts.com/sql/Tips/ExcelDiffLocale.aspx), you can use Excel to test your translations.</span></span>  
  
 <span data-ttu-id="06e7c-168">다음 작업은 로캘 식별자 연결 문자열 속성을 포함하도록 .odc 파일을 편집하여 손으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-168">You can do this by hand editing the .odc file to include the locale identifier connection string property.</span></span> <span data-ttu-id="06e7c-169">Adventure Works 샘플 다차원 데이터베이스에서 이렇게 해보세요.</span><span class="sxs-lookup"><span data-stu-id="06e7c-169">Try this out with the Adventure Works sample multidimensional database.</span></span>  
  
-   <span data-ttu-id="06e7c-170">기존 .odc 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-170">Search for existing .odc files.</span></span> <span data-ttu-id="06e7c-171">Adventure Works 다차원 데이터용으로 하나를 찾았으면 이 파일을 마우스 오른쪽 단추로 클릭하여 메모장에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-171">When you find the one for Adventure Works multidimensional, right-click the file to open it in Notepad.</span></span>  
  
-   <span data-ttu-id="06e7c-172">연결 문자열에 `Locale Identifier=1036` 를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-172">Add `Locale Identifier=1036` to the connection string.</span></span> <span data-ttu-id="06e7c-173">파일을 저장하고 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-173">Save and close the file.</span></span>  
  
-   <span data-ttu-id="06e7c-174">Excel 열기 | **데이터**  |  **기존 연결**.</span><span class="sxs-lookup"><span data-stu-id="06e7c-174">Open Excel | **Data** | **Existing Connections**.</span></span> <span data-ttu-id="06e7c-175">목록을 이 컴퓨터에 있는 연결 파일로 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-175">Filter the list to just connections files on this computer.</span></span> <span data-ttu-id="06e7c-176">Adventure Works용 연결을 찾습니다. 이름을 주의 깊게 살펴보세요. 두 개 이상 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-176">Find the connection for Adventure Works (look at the name carefully; you might have more than one).</span></span> <span data-ttu-id="06e7c-177">연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-177">Open the connection.</span></span>  
  
     <span data-ttu-id="06e7c-178">Adventure Works 샘플 데이터베이스에 프랑스어 번역이 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-178">You should see the French translations from the Adventure Works sample database.</span></span>  
  
     <span data-ttu-id="06e7c-179">![프랑스어 번역이 있는 Excel 피벗 테이블](media/ssas-localetest-excel.png "프랑스어 번역이 있는 Excel 피벗 테이블")</span><span class="sxs-lookup"><span data-stu-id="06e7c-179">![Excel PivotTable with French translations](media/ssas-localetest-excel.png "Excel PivotTable with French translations")</span></span>  
  
 <span data-ttu-id="06e7c-180">후속 작업으로 SQL Server Profiler를 사용하여 로캘을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-180">As a follow up, you can use SQL Server Profiler to confirm the locale.</span></span> <span data-ttu-id="06e7c-181">`Session Initialize` 이벤트를 클릭한 다음 아래의 텍스트 영역에서 속성 목록을 보고 `<localeidentifier>1036</localeidentifier>`를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-181">Click a `Session Initialize` event and then look at the property list in the text area below to find `<localeidentifier>1036</localeidentifier>`.</span></span>  
  
 <span data-ttu-id="06e7c-182">Management Studio에서는 서버 연결에 있는 로캘 식별자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-182">In Management Studio, you can specify Locale Identifier on a server connection.</span></span>  
  
-   <span data-ttu-id="06e7c-183">개체 탐색기 | **연결**  |  **Analysis Services**  |  **옵션**에서 **추가 연결 매개 변수** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-183">In Object Explorer | **Connect** | **Analysis Services** | **Options**, click the **Additional Connection Parameters** tab.</span></span>  
  
-   <span data-ttu-id="06e7c-184">`Local Identifier=1036` 을 입력하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-184">Enter `Local Identifier=1036` and then click **Connect**.</span></span>  
  
-   <span data-ttu-id="06e7c-185">Adventure Works 데이터베이스에 대해 MDX 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-185">Execute an MDX query against the Adventure Works database.</span></span> <span data-ttu-id="06e7c-186">쿼리 결과는 프랑스어 번역이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-186">The query results should be the French translations.</span></span>  
  
     <span data-ttu-id="06e7c-187">![SSMS에서 프랑스어 번역이 있는 MDX 쿼리](media/ssas-localetest-ssms.png "SSMS에서 프랑스어 번역이 있는 MDX 쿼리")</span><span class="sxs-lookup"><span data-stu-id="06e7c-187">![MDX query with French translations in SSMS](media/ssas-localetest-ssms.png "MDX query with French translations in SSMS")</span></span>  
  
##  <a name="writing-mdx-queries-in-a-solution-containing-translations"></a><a name="bkmk_mdx"></a> <span data-ttu-id="06e7c-188">번역이 들어 있는 솔루션에서 MDX 쿼리 작성</span><span class="sxs-lookup"><span data-stu-id="06e7c-188">Writing MDX queries in a solution containing Translations</span></span>  
 <span data-ttu-id="06e7c-189">번역은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체의 이름에 대한 표시 정보를 제공합니다. 그러나 동일 개체의 식별자는 번역되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-189">Translations provide display information for the names of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects, but the identifiers for the same objects are not translated.</span></span> <span data-ttu-id="06e7c-190">가능하면 번역된 캡션 및 이름 대신 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 개체의 식별자 및 키를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="06e7c-190">Whenever possible, use the identifiers and keys for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects instead of the translated captions and names.</span></span> <span data-ttu-id="06e7c-191">예를 들어 여러 언어 간 이식성을 위해 MDX(Multidimensional Expressions) 문 및 스크립트에 대해 멤버 이름 대신 멤버 키를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-191">For example, use member keys instead of member names for Multidimensional Expressions (MDX) statements and scripts to ensure portability across multiple languages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06e7c-192">테이블 형식 개체 이름은 데이터 정렬에 관계없이 항상 대/소문자를 구분한다는 점에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="06e7c-192">Recall that tabular object names are always case-insensitive, regardless of collation.</span></span> <span data-ttu-id="06e7c-193">반면에 다차원 개체 이름은 데이터 정렬의 대/소문자 구분을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-193">Multidimensional object names, on the other hand, follow the case sensitivity of the collation.</span></span> <span data-ttu-id="06e7c-194">다차원 개체 이름만 대/소문자를 구분하므로 다차원 개체를 참조하는 모든 MDX 쿼리에 대/소문자가 올바로 사용되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-194">Since only multidimensional object names are case-sensitive make sure that all MDX queries referencing multidimensional objects are cased correctly.</span></span>  
  
##  <a name="writing-mdx-queries-containing-date-and-time-values"></a><a name="bkmk_datetime"></a> <span data-ttu-id="06e7c-195">날짜 및 시간 값이 들어 있는 MDX 쿼리 작성</span><span class="sxs-lookup"><span data-stu-id="06e7c-195">Writing MDX queries containing Date and Time Values</span></span>  
 <span data-ttu-id="06e7c-196">여러 언어 간에 날짜 및 시간 기반 MDX 쿼리의 이식성을 높이기 위한 제안 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-196">The following suggestions to make your date and time-based MDX queries more portable across different languages:</span></span>  
  
1.  <span data-ttu-id="06e7c-197">**비교 및 작업에 숫자 부분 사용**</span><span class="sxs-lookup"><span data-stu-id="06e7c-197">**Use numeric parts for comparisons and operations**</span></span>  
  
     <span data-ttu-id="06e7c-198">월 및 요일 비교 및 작업을 수행할 때 해당 문자열 대신 숫자 형식의 날짜 및 시간 부분을 사용합니다(예를 들어 MonthName 대신 MonthNumberofYear 사용).</span><span class="sxs-lookup"><span data-stu-id="06e7c-198">When you perform month and day-of-week comparisons and operations, use the numeric date and time parts instead of the string equivalents (for example, use MonthNumberofYear instead of MonthName).</span></span> <span data-ttu-id="06e7c-199">숫자 값은 언어 번역 간 차이의 영향을 가장 적게 받습니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-199">Numeric values are least affected by differences in language translations.</span></span>  
  
2.  <span data-ttu-id="06e7c-200">**결과 집합에 해당 문자열 사용**</span><span class="sxs-lookup"><span data-stu-id="06e7c-200">**Use string equivalents in a result set**</span></span>  
  
     <span data-ttu-id="06e7c-201">최종 사용자에게 표시되는 결과 집합을 만들 때 다국어 고객이 제공된 번역의 혜택을 받을 수 있도록 문자열(예: MonthName) 사용을 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="06e7c-201">When building result sets seen by end-users, consider using the string (such as MonthName) so that your multi-lingual audience can benefit from the translations you've provided.</span></span>  
  
3.  <span data-ttu-id="06e7c-202">**일반적인 날짜 및 시간 정보를 위한 ISO 날짜 형식 사용**</span><span class="sxs-lookup"><span data-stu-id="06e7c-202">**Use ISO date formats for universal date and time information**</span></span>  
  
     <span data-ttu-id="06e7c-203">한 [Analysis Services 전문가](http://geekswithblogs.net/darrengosbell/Default.aspx) 는 다음과 같이 추천합니다. "저는 SQL 또는 MDX 쿼리에 전달하는 날짜 문자열에 대해 항상 ISO 날짜 형식인 yyyy-mm-dd를 사용합니다. 이 형식은 명확하고 클라이언트나 서버의 국가별 설정과 관계없이 작동하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-203">One [Analysis Services expert](http://geekswithblogs.net/darrengosbell/Default.aspx) has this recommendation: "I always use the ISO date format yyyy-mm-dd for any date strings that I pass in to queries in SQL or MDX because it's unambiguous and will work regardless of the client or server's regional settings.</span></span> <span data-ttu-id="06e7c-204">모호한 날짜 형식을 구문 분석할 때 서버는 국가별 설정을 따라야 한다는 데 동의하겠지만 또한 선택할 수 있다면 선택에 따라 해석이 달라지지 않는 것이 좋다고 생각합니다."</span><span class="sxs-lookup"><span data-stu-id="06e7c-204">I would agree that the server should defer to its regional settings when parsing an ambiguous date format, but I also think that if you've got an option that is not open to interpretation that you are better choosing that anyway".</span></span>  
  
4.  `Use the Format function to enforce a specific format, regardless of regional language settings`  
  
     <span data-ttu-id="06e7c-205">포럼 게시물에서 가져온 다음의 MDX 쿼리는 형식을 사용하여 기본 국가별 설정에 관계없이 특정 형식으로 날짜를 반환하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="06e7c-205">The following MDX query, borrowed from a forum post, illustrates how to use Format to return dates in a specific format, irrespective of the underlying regional settings.</span></span>  
  
     <span data-ttu-id="06e7c-206">원래 게시물을 보려면 [SSAS 2012가 잘못된 날짜 생성(Network Steve의 포럼 게시물)](http://www.networksteve.com/forum/topic.php/SSAS_2012_generates_invalid_dates/?TopicId=40504&Posts=2) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="06e7c-206">See [SSAS 2012 generates invalid dates (forum post on Network Steve](http://www.networksteve.com/forum/topic.php/SSAS_2012_generates_invalid_dates/?TopicId=40504&Posts=2) for the original post.</span></span>  
  
    ```  
    WITH MEMBER [LinkTimeAdd11Date_Manual] as Format(dateadd("d",15,"2014-12-11"), "mm/dd/yyyy")  
    member [LinkTimeAdd15Date_Manual] as Format(dateadd("d",11,"2014-12-13"), "mm/dd/yyyy")  
    SELECT  
    { [LinkTimeAdd11Date_Manual]  
    ,[LinkTimeAdd15Date_Manual]  
    }  
    ON COLUMNS   
    FROM [Adventure Works]  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="06e7c-207">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06e7c-207">See Also</span></span>  
 <span data-ttu-id="06e7c-208">[다차원 Analysis Services에 대 한 세계화 시나리오](globalization-scenarios-for-analysis-services-multiidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="06e7c-208">[Globalization scenarios for Analysis Services Multidimensional](globalization-scenarios-for-analysis-services-multiidimensional.md) </span></span>  
 [<span data-ttu-id="06e7c-209">국가별 Transact-SQL 문 작성</span><span class="sxs-lookup"><span data-stu-id="06e7c-209">Write International Transact-SQL Statements</span></span>](../relational-databases/collations/write-international-transact-sql-statements.md)  
