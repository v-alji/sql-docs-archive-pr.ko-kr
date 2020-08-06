---
title: 국가별 Transact-SQL 문 작성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1888d1045e43e0a9839fd76a21c51500af63539a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661154"
---
# <a name="write-international-transact-sql-statements"></a><span data-ttu-id="90381-102">국가별 Transact-SQL 문 작성</span><span class="sxs-lookup"><span data-stu-id="90381-102">Write International Transact-SQL Statements</span></span>
  <span data-ttu-id="90381-103">다음 지침에 따라 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하는 데이터베이스 및 데이터베이스 애플리케이션을 특정 언어에서 다른 언어로 이식하거나 여러 언어를 지원하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90381-103">Databases and database applications that use [!INCLUDE[tsql](../../includes/tsql-md.md)] statements will become more portable from one language to another, or will support multiple languages, if the following guidelines are followed:</span></span>  
  
-   <span data-ttu-id="90381-104">`char`, `varchar` 및 `text` 데이터 형식을 사용하는 경우 모두 `nchar`, `nvarchar` 및 `nvarchar(max)`로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="90381-104">Replace all uses of the `char`, `varchar`, and `text` data types with `nchar`, `nvarchar`, and `nvarchar(max)`.</span></span> <span data-ttu-id="90381-105">이렇게 하면 코드 페이지 변환 문제가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90381-105">By doing this, you do not have to consider code page conversion issues.</span></span> <span data-ttu-id="90381-106">자세한 내용은 [Collation and Unicode Support](collation-and-unicode-support.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90381-106">For more information, see [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="90381-107">월과 요일을 비교하고 연산하려면 문자열 이름 대신 숫자 형식의 날짜 부분을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="90381-107">When you perform month and day-of-week comparisons and operations, use the numeric date parts instead of the name strings.</span></span> <span data-ttu-id="90381-108">언어 설정이 다르면 월과 요일에 대해 각기 다른 이름이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="90381-108">Different language settings return different names for the months and weekdays.</span></span> <span data-ttu-id="90381-109">예를 들어 DATENAME(MONTH,GETDATE())은 언어가 영어(미국)로 설정되었을 경우 May를 반환하고 독일어로 설정되었을 경우 Mai를 반환하며 프랑스어로 설정되었을 경우에는 mai를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="90381-109">For example, DATENAME(MONTH,GETDATE()) returns May when the language is set to U.S. English, returns Mai when the language is set to German, and returns mai when the language is set to French.</span></span> <span data-ttu-id="90381-110">대신 이름이 아닌 해당 월의 숫자를 사용하는 DATEPART 함수 등을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="90381-110">Instead, use a function such as DATEPART that uses the number of the month instead of the name.</span></span> <span data-ttu-id="90381-111">날짜 이름이 숫자 표시보다 의미를 쉽게 알 수 있으므로 사용자에게 표시되는 결과 집합을 만들 때에는 DATEPART 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="90381-111">Use the DATEPART names when you build result sets to be displayed to a user, because the date names are frequently more meaningful than a numeric representation.</span></span> <span data-ttu-id="90381-112">그러나 특정 언어로 표시된 이름에 따라 달라지는 논리는 코딩하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="90381-112">However, do not code any logic that depends on the displayed names being from a specific language.</span></span>  
  
-   <span data-ttu-id="90381-113">INSERT 또는 UPDATE 문을 위한 입력이나 비교를 위해 날짜를 지정할 때 모든 언어 설정에서 동일하게 해석되는 상수를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="90381-113">When you specify dates in comparisons or for input to INSERT or UPDATE statements, use constants that are interpreted the same way for all language settings:</span></span>  
  
    -   <span data-ttu-id="90381-114">ADO, OLE DB 및 ODBC 애플리케이션은 다음과 같은 ODBC용 타임스탬프, 날짜 및 시간 이스케이프 절을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90381-114">ADO, OLE DB, and ODBC applications should use the ODBC timestamp, date, and time escape clauses of:</span></span>  
  
         <span data-ttu-id="90381-115">**{ts '** yyyy mm (yyyy) **-** _mm_ **-** _ddhh_**:**_mm_**:**_ss_[**.** _fff_] **'}** 예: **{ts '** 1998 **-** 09 **-** 24 10 **:** 02 **:** 20 **'}**</span><span class="sxs-lookup"><span data-stu-id="90381-115">**{ ts'** yyyy**-**_mm_**-**_ddhh_**:**_mm_**:**_ss_[**.**_fff_] **'}** such as: **{ ts'** 1998**-** 09**-** 24 10 **:** 02 **:** 20 **' }**</span></span>  
  
         <span data-ttu-id="90381-116">**{ d'** _yyyy_ **-** _mm_ **-** _dd_ **'}** 예: **{ d'** 1998**-** 09**-** 24 **'}**</span><span class="sxs-lookup"><span data-stu-id="90381-116">**{ d'** _yyyy_ **-** _mm_ **-** _dd_ **'}** such as: **{ d'** 1998**-** 09**-** 24 **'}**</span></span>  
  
         <span data-ttu-id="90381-117">**{t '** _hh_ **:** _mm_ **:** _ss_ **'}** (예: **{t '** 10:02:20 **'})**</span><span class="sxs-lookup"><span data-stu-id="90381-117">**{ t'** _hh_ **:** _mm_ **:** _ss_ **'}** such as: **{ t'** 10:02:20 **'}**</span></span>  
  
    -   <span data-ttu-id="90381-118">다른 API나 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트, 저장 프로시저, 트리거를 사용하는 애플리케이션에서는 분리되지 않은 숫자 문자열을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90381-118">Applications that use other APIs, or [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, stored procedures, and triggers, should use the unseparated numeric strings.</span></span> <span data-ttu-id="90381-119">예를 들어 19980924와 같은 *yyyymmdd* 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="90381-119">For example, *yyyymmdd* as 19980924.</span></span>  
  
    -   <span data-ttu-id="90381-120">다른 api 나 스크립트, 저장 프로시저 및 트리거를 사용 하는 응용 프로그램에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] `time` ,, `date` `smalldate` , `datetime` , **datetime2**및 `datetimeoffset` 데이터 형식과 문자열 데이터 형식 간의 모든 변환에 명시적 스타일 매개 변수와 함께 CONVERT 문을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90381-120">Applications that use other APIs, or [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, stored procedures, and triggers should use the CONVERT statement with an explicit style parameter for all conversions between the `time`, `date`, `smalldate`, `datetime`, **datetime2**, and `datetimeoffset` data types and character string data types.</span></span> <span data-ttu-id="90381-121">예를 들어 다음 문은 모든 언어 또는 날짜 형식 연결 설정에서 똑같이 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="90381-121">For example, the following statement is interpreted in the same way for all language or date format connection settings:</span></span>  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         <span data-ttu-id="90381-122">자세한 내용은 [CAST 및 CONVERT&#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90381-122">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
  
