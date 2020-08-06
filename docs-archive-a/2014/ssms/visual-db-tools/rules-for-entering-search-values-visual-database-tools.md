---
title: 검색 값 입력 규칙(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- time [SQL Server], searches
- date searches
- dates [SQL Server], searches
- embedding apostrophes [SQL Server]
- logical value searches [SQL Server]
- case-sensitive search matches
- search criteria [SQL Server], rules
- text value searches [SQL Server]
- numeric value searches [SQL Server]
ms.assetid: 3c8134b7-83f4-41b4-99c8-e3949a685ff5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 907bcac93863bc5660993e910b37e25e25a129b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646795"
---
# <a name="rules-for-entering-search-values-visual-database-tools"></a><span data-ttu-id="4bb71-102">검색 값 입력 규칙(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4bb71-102">Rules for Entering Search Values (Visual Database Tools)</span></span>
  <span data-ttu-id="4bb71-103">이 항목에서는 다음과 같은 리터럴 형식 값을 검색 조건으로 입력할 때 적용되는 규칙을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-103">This topic discusses the conventions you must use when entering the following types of literal values for a search condition:</span></span>  
  
-   <span data-ttu-id="4bb71-104">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="4bb71-104">Text values</span></span>  
  
-   <span data-ttu-id="4bb71-105">숫자 값</span><span class="sxs-lookup"><span data-stu-id="4bb71-105">Numeric values</span></span>  
  
-   <span data-ttu-id="4bb71-106">날짜</span><span class="sxs-lookup"><span data-stu-id="4bb71-106">Dates</span></span>  
  
-   <span data-ttu-id="4bb71-107">논리 값</span><span class="sxs-lookup"><span data-stu-id="4bb71-107">Logical values</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bb71-108">이 항목의 정보는 표준 SQL-92 규칙에서 발췌한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-108">The information in this topic is derived from the rules for standard SQL-92.</span></span> <span data-ttu-id="4bb71-109">그러나 데이터베이스마다 자체의 고유한 방식으로 SQL을 구현할 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="4bb71-109">However, each database can implement SQL in its own way.</span></span> <span data-ttu-id="4bb71-110">여기에서 설명하는 지침이 모든 경우에 적용되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-110">Therefore, the guidelines provided here might not apply in every case.</span></span> <span data-ttu-id="4bb71-111">특정 데이터베이스에 대하여 검색 값을 입력하는 방법에 대한 내용은 사용하고 있는 데이터베이스의 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4bb71-111">If you have questions about how to enter search values for a particular database, refer to the documentation for the database that you are using.</span></span>  
  
## <a name="searching-on-text-values"></a><span data-ttu-id="4bb71-112">텍스트 값 검색</span><span class="sxs-lookup"><span data-stu-id="4bb71-112">Searching on Text Values</span></span>  
 <span data-ttu-id="4bb71-113">다음 지침은 검색 조건에 텍스트 값을 입력할 때 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-113">The following guidelines apply when you enter text values in search conditions:</span></span>  
  
-   <span data-ttu-id="4bb71-114">**인용 부호** 성에 대한 다음 예와 같이 텍스트 값을 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-114">**Quotation marks** Enclose text values in single quotation marks, as in this example for a last name:</span></span>  
  
    ```  
    'Smith'  
    ```  
  
     <span data-ttu-id="4bb71-115">[조건 창](visual-database-tools.md)에 검색 조건을 입력할 때 텍스트 값을 입력하기만 하면 쿼리 및 뷰 디자이너가 자동으로 이 값을 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-115">If you are entering a search condition in the [Criteria Pane](visual-database-tools.md), you can simply type the text value and the Query and View Designer will automatically put single quotation marks around it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4bb71-116">일부 데이터베이스의 경우 작은따옴표 안의 용어는 리터럴 값으로 해석되지만 큰따옴표 안의 용어는 열 또는 테이블 참조 같은 데이터베이스 개체로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-116">In some databases, terms in single quotation marks are interpreted as literal values, whereas terms in double quotation marks are interpreted as database objects such as column or table references.</span></span> <span data-ttu-id="4bb71-117">따라서 쿼리 및 뷰 디자이너에서 큰따옴표 안의 용어를 허용할 수 있다 하더라도 예상하는 것과 다르게 해석될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-117">Therefore, even though the Query and View Designer can accept terms in double quotation marks, it might interpret them differently than you expect.</span></span>  
  
-   <span data-ttu-id="4bb71-118">**아포스트로피 포함** 검색하는 데이터에 작은따옴표(아포스트로피)가 포함되어 있으면 작은따옴표를 두 개 입력하여 작은따옴표가 구분 기호가 아니라 리터럴 값으로 해석되도록 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-118">**Embedding apostrophes** If the data you are searching for contains a single quotation mark (an apostrophe), you can enter two single quotation marks to indicate that you mean the single quotation mark as a literal value and not a delimiter.</span></span> <span data-ttu-id="4bb71-119">예를 들어, 다음 조건은 "Swann’s Way" 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-119">For example, the following condition searches for the value "Swann's Way:"</span></span>  
  
    ```  
    ='Swann''s Way'  
    ```  
  
-   <span data-ttu-id="4bb71-120">**길이 제한** 긴 문자열을 입력할 때 데이터베이스에 대한 SQL 문의 최대 길이를 초과하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-120">**Length limits** Do not exceed the maximum length of the SQL statement for your database when entering long strings.</span></span>  
  
-   <span data-ttu-id="4bb71-121">**대/소문자 구분** 사용하고 있는 데이터베이스의 대/소문자 구분 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-121">**Case sensitivity** Follow the case sensitivity rules for the database you are using.</span></span> <span data-ttu-id="4bb71-122">사용하는 데이터베이스에 따라 텍스트를 검색할 때 대/소문자를 구분할 것인지 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-122">The database you are using determines whether text searches are case sensitive.</span></span> <span data-ttu-id="4bb71-123">예를 들어 일부 데이터베이스는 "=" 연산자를 대/소문자가 정확하게 일치하는 항목으로 해석하지만 다른 데이터베이스는 대/소문자를 무시하고 일치하는 항목으로 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-123">For example, some databases interpret the operator "=" to mean an exact case-sensitive match, but others will allow matches on any combination of uppercase and lowercase characters.</span></span>  
  
     <span data-ttu-id="4bb71-124">데이터베이스가 대/소문자를 구분하는 검색을 사용하는지 여부를 잘 모르겠는 경우에는 다음 예와 같이 검색 조건에 UPPER 함수 또는 LOWER 함수를 사용하여 검색 데이터의 대/소문자를 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-124">If you are unsure about whether the database uses a case-sensitive search, you can use the UPPER or LOWER functions in the search condition to convert the case of the search data, as illustrated in the following example:</span></span>  
  
    ```  
    WHERE UPPER(lname) = 'SMITH'  
    ```  
  
## <a name="searching-on-numeric-values"></a><span data-ttu-id="4bb71-125">숫자 값 검색</span><span class="sxs-lookup"><span data-stu-id="4bb71-125">Searching on Numeric Values</span></span>  
 <span data-ttu-id="4bb71-126">다음 지침은 검색 조건에 숫자 값을 입력할 때 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-126">The following guidelines apply when you enter numeric values in search conditions:</span></span>  
  
-   <span data-ttu-id="4bb71-127">**인용 부호** 숫자는 인용 부호로 묶지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-127">**Quotation marks** Do not enclose numbers in quotation marks.</span></span>  
  
-   <span data-ttu-id="4bb71-128">**숫자가 아닌 문자** Windows 제어판의 **국가별 설정** 대화 상자에 정의된 소수 구분 기호와 음수 기호(-) 외에는 숫자가 아닌 문자를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-128">**Non-numeric characters** Do not include non-numeric characters except the decimal separator (as defined in the **Regional Settings** dialog box of Windows Control Panel) and negative sign (-).</span></span> <span data-ttu-id="4bb71-129">자릿수 구분 기호(예: 천 단위 구분 쉼표) 또는 통화 기호를 넣지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="4bb71-129">Do not include digit grouping symbols (such as a comma between thousands) or currency symbols.</span></span>  
  
-   <span data-ttu-id="4bb71-130">**소수점** 정수를 입력하는 경우 검색할 숫자의 입력 값이 정수 또는 실수인지에 따라 소수점을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-130">**Decimal marks** If you are entering whole numbers, you can include a decimal mark, whether the value you are searching for is an integer or a real number.</span></span>  
  
-   <span data-ttu-id="4bb71-131">**지수 표기법** 매우 큰 수 또는 매우 작은 수를 다음 예에서와 같이 지수 표기법으로 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-131">**Scientific notation** You can enter very large or very small numbers using scientific notation, as in this example:</span></span>  
  
    ```  
    > 1.23456e-9  
    ```  
  
## <a name="searching-on-dates"></a><span data-ttu-id="4bb71-132">날짜 검색</span><span class="sxs-lookup"><span data-stu-id="4bb71-132">Searching on Dates</span></span>  
 <span data-ttu-id="4bb71-133">날짜를 입력하는 형식은 사용하는 데이터베이스와 쿼리 및 뷰 디자이너에서 날짜가 입력되는 대상 창에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-133">The format you use to enter dates depends on the database you are using and in what pane of the Query and View Designer you are entering the date.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4bb71-134">데이터 원본에 사용되는 형식을 알지 못하는 경우에는 일반적으로 사용하는 임의의 형식으로 날짜를 조건 창의 필터 열에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-134">If you don't know which format your data source uses, type a date into the filter column of the Criteria pane in any format familiar to you.</span></span> <span data-ttu-id="4bb71-135">이렇게 입력한 항목은 대부분 적절한 형식으로 디자이너에서 자동 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-135">The designer will convert most of such entries into the appropriate format.</span></span>  
  
 <span data-ttu-id="4bb71-136">다음과 같은 날짜 형식을 쿼리 및 뷰 디자이너에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-136">The Query and View Designer can work with the following date formats:</span></span>  
  
-   <span data-ttu-id="4bb71-137">**로캘 관련** **Windows 국가별 설정 속성** 대화 상자에 지정된 날짜 형식</span><span class="sxs-lookup"><span data-stu-id="4bb71-137">**Locale-specific** The format specified for dates in the **Windows Regional Settings Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="4bb71-138">**데이터베이스 관련** 해당 데이터베이스에서 인식하는 모든 형식</span><span class="sxs-lookup"><span data-stu-id="4bb71-138">**Database-specific** Any format understood by the database.</span></span>  
  
-   <span data-ttu-id="4bb71-139">**ANSI 표준 날짜** 다음 예와 같이 중괄호, 날짜를 나타내는 'd' 및 날짜 문자열을 사용하는 형식</span><span class="sxs-lookup"><span data-stu-id="4bb71-139">**ANSI standard date** A format that uses braces, the marker 'd' to designate the date, and a date string, as in the following example:</span></span>  
  
    ```  
    { d '1990-12-31' }  
    ```  
  
-   <span data-ttu-id="4bb71-140">**ANSI 표준 datetime** ANSI 표준 날짜와 비슷하지만 1990년 12월 31일에 대한 다음 예와 같이 'd' 대신 'ts'를 사용하고 24시간제를 사용하여 시, 분, 초를 날짜에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-140">**ANSI standard datetime** Similar to ANSI-standard date, but uses 'ts' instead of 'd' and adds hours, minutes, and seconds to the date (using a 24-hour clock), as in this example for December 31, 1990:</span></span>  
  
    ```  
    { ts '1990-12-31 00:00:00' }  
    ```  
  
     <span data-ttu-id="4bb71-141">일반적으로 ANSI 표준 날짜 형식은 실제 날짜 데이터 형식을 사용하여 날짜를 나타내는 데이터베이스에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-141">In general, the ANSI standard date format is used with databases that represent dates using a true date data type.</span></span> <span data-ttu-id="4bb71-142">이와 달리 datetime 형식은 datetime 데이터 형식을 지원하는 데이터베이스에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-142">In contrast, the datetime format is used with databases that support a datetime data type.</span></span>  
  
 <span data-ttu-id="4bb71-143">다음 표에는 쿼리 및 뷰 디자이너의 각 창에서 사용할 수 있는 날짜 형식이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-143">The following table summarizes the date format that you can use in different panes of the Query and View Designer.</span></span>  
  
|<span data-ttu-id="4bb71-144">**창**</span><span class="sxs-lookup"><span data-stu-id="4bb71-144">**Pane**</span></span>|<span data-ttu-id="4bb71-145">**날짜 형식**</span><span class="sxs-lookup"><span data-stu-id="4bb71-145">**Date format**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="4bb71-146">조건</span><span class="sxs-lookup"><span data-stu-id="4bb71-146">Criteria</span></span>|<span data-ttu-id="4bb71-147">로캘 관련 데이터베이스 관련 ANSI 표준</span><span class="sxs-lookup"><span data-stu-id="4bb71-147">Locale-specific Database-specific ANSI standard</span></span><br /><br /> <span data-ttu-id="4bb71-148">[조건 창](visual-database-tools.md) 에 입력한 날짜는 SQL 창에서 데이터베이스 호환 형식으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-148">Dates entered in the [Criteria Pane](visual-database-tools.md) are converted to a database-compatible format in the SQL pane.</span></span>|  
|<span data-ttu-id="4bb71-149">SQL</span><span class="sxs-lookup"><span data-stu-id="4bb71-149">SQL</span></span>|<span data-ttu-id="4bb71-150">데이터베이스 관련 ANSI 표준</span><span class="sxs-lookup"><span data-stu-id="4bb71-150">Database-specific ANSI standard</span></span>|  
|<span data-ttu-id="4bb71-151">결과</span><span class="sxs-lookup"><span data-stu-id="4bb71-151">Results</span></span>|<span data-ttu-id="4bb71-152">로캘 관련</span><span class="sxs-lookup"><span data-stu-id="4bb71-152">Locale-specific</span></span>|  
  
## <a name="searching-on-logical-values"></a><span data-ttu-id="4bb71-153">논리 값 검색</span><span class="sxs-lookup"><span data-stu-id="4bb71-153">Searching on Logical Values</span></span>  
 <span data-ttu-id="4bb71-154">논리 데이터의 형식은 데이터베이스마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-154">The format of logical data varies from database to database.</span></span> <span data-ttu-id="4bb71-155">대부분의 경우 False 값은 0으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-155">Very frequently, a value of False is stored as zero (0).</span></span> <span data-ttu-id="4bb71-156">True 값은 대개 1로 저장되지만 -1이 되는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-156">A value of True is most frequently stored as 1 and occasionally as -1.</span></span> <span data-ttu-id="4bb71-157">다음 지침은 검색 조건에 논리 값을 입력할 때 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-157">The following guidelines apply when you enter logical values in search conditions:</span></span>  
  
-   <span data-ttu-id="4bb71-158">False 값을 검색하려면 다음 예와 같이 0을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="4bb71-158">To search for a value of False, use a zero, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract = 0  
    ```  
  
-   <span data-ttu-id="4bb71-159">True 값을 검색할 때 사용할 형식을 모르면 다음 예에서와 같이 1을 사용하여 시도해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="4bb71-159">If you are not sure what format to use when searching for a True value, try using 1, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract = 1  
    ```  
  
-   <span data-ttu-id="4bb71-160">또는 다음과 같이 0이 아닌 값을 검색하여 검색 범위를 넓힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb71-160">Alternatively, you can broaden the scope of the search by searching for any non-zero value, as in the following example:</span></span>  
  
    ```  
    SELECT * FROM authors  
    WHERE contract <> 0  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4bb71-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4bb71-161">See Also</span></span>  
 [<span data-ttu-id="4bb71-162">검색 조건 지정&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="4bb71-162">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
