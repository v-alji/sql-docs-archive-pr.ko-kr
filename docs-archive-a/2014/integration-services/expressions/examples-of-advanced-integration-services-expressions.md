---
title: 고급 Integration Services 식의 예 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- operators [Integration Services]
- expressions [Integration Services], examples
- examples [Integration Services]
ms.assetid: c7794ba3-0de5-466b-ae8a-9ddd27360049
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb1e8dc6f9bffd22c917414f80f6ba9f257b25b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650213"
---
# <a name="examples-of-advanced-integration-services-expressions"></a><span data-ttu-id="a1caf-102">고급 Integration Services 식의 예</span><span class="sxs-lookup"><span data-stu-id="a1caf-102">Examples of Advanced Integration Services Expressions</span></span>
  <span data-ttu-id="a1caf-103">이 섹션에서는 여러 개의 연산자와 함수가 결합된 고급 식의 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-103">This section provides examples of advanced expressions that combine multiple operators and functions.</span></span> <span data-ttu-id="a1caf-104">선행 제약 조건이나 조건부 분할 변환에 사용된 식은 부울로 계산되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-104">If an expression is used in a precedence constraint or the Conditional Split transformation, it must evaluate to a Boolean.</span></span> <span data-ttu-id="a1caf-105">그러나 속성 식, 변수, 파생 열 변환 또는 For 루프 컨테이너에 사용된 식에는 이 제한이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-105">That restriction, however, does not apply to expressions used in property expressions, variables, the Derived Column transformation, or the For Loop container.</span></span>  
  
 <span data-ttu-id="a1caf-106">다음 예에서는 **AdventureWorks** 및 [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-106">The following examples use the **AdventureWorks** and the [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="a1caf-107">각 예에서 사용되는 테이블이 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-107">Each example identifies the tables it uses.</span></span>  
  
## <a name="boolean-expressions"></a><span data-ttu-id="a1caf-108">부울 식</span><span class="sxs-lookup"><span data-stu-id="a1caf-108">Boolean Expressions</span></span>  
  
-   <span data-ttu-id="a1caf-109">이 예에서는 **Product** 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-109">This example uses the **Product** table.</span></span> <span data-ttu-id="a1caf-110">이 식은 **SellStartDate** 열의 월 부분을 계산하고 월이 6월 이후이면 TRUE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-110">The expression evaluates the month entry in the **SellStartDate** column and returns TRUE if the month is June or later.</span></span>  
  
    ```  
    DATEPART("mm",SellStartDate) > 6  
    ```  
  
-   <span data-ttu-id="a1caf-111">이 예에서는 **Product** 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-111">This example uses the **Product** table.</span></span> <span data-ttu-id="a1caf-112">이 식은 **ListPrice** 열을 **StandardCost** 열로 나눈 값을 반올림한 결과를 계산하고 결과가 1.5보다 크면 TRUE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-112">The expression evaluates the rounded result of dividing the **ListPrice** column by the **StandardCost** column, and returns TRUE if the result is greater than 1.5.</span></span>  
  
    ```  
    ROUND(ListPrice / StandardCost,2) > 1.50  
    ```  
  
-   <span data-ttu-id="a1caf-113">이 예에서는 **Product** 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-113">This example uses the **Product** table.</span></span> <span data-ttu-id="a1caf-114">이 식은 3개 연산이 모두 TRUE이면 TRUE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-114">The expression returns TRUE if all three operations evaluate to TRUE.</span></span> <span data-ttu-id="a1caf-115">**Size** 열과 **BikeSize** 변수의 데이터 형식이 호환되지 않으면 두 번째 예에 표시된 것처럼 식에 명시적 캐스트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-115">If the **Size** column and the **BikeSize** variable have incompatible data types, the expression requires an explicit cast as shown the second example.</span></span> <span data-ttu-id="a1caf-116">DT_WSTR로의 캐스트는 문자열 길이를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-116">The cast to DT_WSTR includes the length of the string.</span></span>  
  
    ```  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE && Size != @BikeSize  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE  && Size != (DT_WSTR,10)@BikeSize  
    ```  
  
-   <span data-ttu-id="a1caf-117">이 예에서는 **CurrencyRate** 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-117">This example uses the **CurrencyRate** table.</span></span> <span data-ttu-id="a1caf-118">이 식은 테이블과 변수의 값을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-118">The expression compares values in tables and variables.</span></span> <span data-ttu-id="a1caf-119">**FromCurrencyCode** 또는 **ToCurrencyCode** 열의 항목이 변수 값과 같고 **AverageRate** 값이 **EndOfDayRate**값보다 크면 TRUE가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-119">It returns TRUE if entries in the **FromCurrencyCode** or **ToCurrencyCode** columns are equal to variable values and if the value in **AverageRate** is greater that the value in **EndOfDayRate**.</span></span>  
  
    ```  
    (FromCurrencyCode == @FromCur || ToCurrencyCode == @ToCur) && AverageRate > EndOfDayRate  
    ```  
  
-   <span data-ttu-id="a1caf-120">이 예에서는 **Currency** 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-120">This example uses the **Currency** table.</span></span> <span data-ttu-id="a1caf-121">이 식은 **Name** 열이 a 또는 A가 아니면 TRUE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-121">The expression returns TRUE if the first character in the **Name** column is not a or A.</span></span>  
  
    ```  
    SUBSTRING(UPPER(Name),1,1) != "A"  
    ```  
  
     <span data-ttu-id="a1caf-122">다음 식은 동일한 결과를 제공하지만 한 문자만 대문자로 변환되기 때문에 훨씬 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-122">The following expression provides the same results, but it is more efficient because only one character is converted to uppercase.</span></span>  
  
    ```  
    UPPER(SUBSTRING(Name,1,1)) != "A"  
    ```  
  
## <a name="non-boolean-expressions"></a><span data-ttu-id="a1caf-123">부울이 아닌 식</span><span class="sxs-lookup"><span data-stu-id="a1caf-123">Non-Boolean Expressions</span></span>  
 <span data-ttu-id="a1caf-124">부울이 아닌 식은 파생 열 변환, 속성 식 및 For 루프 컨테이너에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-124">Non-Boolean expressions are used in the Derived Column transformation, property expressions, and the For Loop container.</span></span>  
  
-   <span data-ttu-id="a1caf-125">이 예에서는 **Contact** 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-125">This example uses the **Contact** table.</span></span> <span data-ttu-id="a1caf-126">이 식은 **FirstName**, **MiddleName**및 **LastName** 열에서 선행 및 후행 공백을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-126">The expression removes leading and trailing spaces from the **FirstName**, **MiddleName**, and **LastName** columns.</span></span> <span data-ttu-id="a1caf-127">**MiddleName** 열이 Null이 아니면 첫 문자를 추출하여 중간 이니셜과 **FirstName** 및 **LastName**열의 값을 연결하고 값 사이에 공백을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-127">It extracts the first letter of the **MiddleName** column if it is not null, concatenates the middle initial and the values in **FirstName** and **LastName**, and inserts appropriate spaces between values.</span></span>  
  
    ```  
    TRIM(FirstName) + " " + (!ISNULL(MiddleName) ? SUBSTRING(MiddleName,1,1) + " " : "") + TRIM(LastName)  
    ```  
  
-   <span data-ttu-id="a1caf-128">이 예에서는 **Contact** 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-128">This example uses the **Contact** table.</span></span> <span data-ttu-id="a1caf-129">이 식은 **Salutation** 열의 항목 유효성을 검사하고</span><span class="sxs-lookup"><span data-stu-id="a1caf-129">The expression validates entries in the **Salutation** column.</span></span> <span data-ttu-id="a1caf-130">**Salutation** 항목이나 빈 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-130">It returns a **Salutation** entry or an empty string.</span></span>  
  
    ```  
    (Salutation == "Sr." || Salutation == "Ms." || Salutation == "Sra." || Salutation == "Mr.") ? Salutation : ""  
    ```  
  
-   <span data-ttu-id="a1caf-131">이 예에서는 **Product** 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-131">This example uses the **Product** table.</span></span> <span data-ttu-id="a1caf-132">이 식은 **Color** 열의 첫 문자를 대문자로 변환하고 나머지 문자를 소문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-132">The expression converts the first character in the **Color** column to uppercase and converts remaining characters to lowercase.</span></span>  
  
    ```  
    UPPER(SUBSTRING(Color,1,1)) + LOWER(SUBSTRING(Color,2,15))  
    ```  
  
-   <span data-ttu-id="a1caf-133">이 예에서는 **Product** 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-133">This example uses the **Product** table.</span></span> <span data-ttu-id="a1caf-134">이 식은 제품이 판매된 월 수를 계산하며 **SellStartDate** 또는 **SellEndDate** 열에 NULL이 포함된 경우 "알 수 없음" 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-134">The expression calculates the number of months a product has been sold and returns the string "Unknown" if either the **SellStartDate** or the **SellEndDate** column contains NULL.</span></span>  
  
    ```  
    !(ISNULL(SellStartDate)) && !(ISNULL(SellEndDate)) ? (DT_WSTR,2)DATEDIFF("mm",SellStartDate,SellEndDate) : "Unknown"  
    ```  
  
-   <span data-ttu-id="a1caf-135">이 예에서는 **Product** 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-135">This example uses the **Product** table.</span></span> <span data-ttu-id="a1caf-136">이 식은 **StandardCost** 열의 표시를 계산하고 결과를 전체 두 자릿수로 반올림합니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-136">The expression calculates the markup on the **StandardCost** column and rounds the result to a precision of two.</span></span> <span data-ttu-id="a1caf-137">결과는 백분율로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1caf-137">The result is presented as a percentage.</span></span>  
  
    ```  
    ROUND(ListPrice / StandardCost,2) * 100  
    ```  
  
## <a name="related-tasks"></a><span data-ttu-id="a1caf-138">관련 작업</span><span class="sxs-lookup"><span data-stu-id="a1caf-138">Related Tasks</span></span>  
 [<span data-ttu-id="a1caf-139">데이터 흐름 구성 요소에서 식 사용</span><span class="sxs-lookup"><span data-stu-id="a1caf-139">Use an Expression in a Data Flow Component</span></span>](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="a1caf-140">관련 내용</span><span class="sxs-lookup"><span data-stu-id="a1caf-140">Related Content</span></span>  
 <span data-ttu-id="a1caf-141">pragmaticworks.com의 기술 문서 - [SSIS 식 치트 시트](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)</span><span class="sxs-lookup"><span data-stu-id="a1caf-141">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
  
