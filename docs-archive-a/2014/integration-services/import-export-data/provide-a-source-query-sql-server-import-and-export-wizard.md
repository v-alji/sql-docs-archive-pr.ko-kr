---
title: 원본 쿼리 지정(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b21100f51c279e9ba764c8f82565af9d6e391ef3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652921"
---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a><span data-ttu-id="34680-102">원본 쿼리 지정(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="34680-102">Provide a Source Query (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="34680-103">**원본 쿼리 지정** 페이지를 사용하여 데이터 원본에서 대상으로 복사할 데이터를 생성하는 SQL 문을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34680-103">Use the **Provide a Source Query** page to type the SQL statement that will generate the data to copy from the data source to the destination.</span></span>  
  
 <span data-ttu-id="34680-104">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34680-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="34680-105">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 사용 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34680-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="34680-106">SQL Server 가져오기 및 내보내기 마법사의 목적은 원본에서 대상으로 데이터를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="34680-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="34680-107">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34680-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="34680-108">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34680-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="34680-109">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34680-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="34680-110">옵션</span><span class="sxs-lookup"><span data-stu-id="34680-110">Options</span></span>  
 <span data-ttu-id="34680-111">**SQL 문**</span><span class="sxs-lookup"><span data-stu-id="34680-111">**SQL statement**</span></span>  
 <span data-ttu-id="34680-112">원본 데이터베이스의 데이터에서 선택한 행을 검색할 쿼리 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="34680-112">Type a query statement to retrieve selected rows of data from the source database.</span></span> <span data-ttu-id="34680-113">예를 들어 다음 쿼리 문은 AdventureWorks 데이터베이스에서 커미션 비율이 1.5% 이상인 영업 사원에 대한 **SalesPersonID**, **SalesQuota**및 **SalesYTD** 를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="34680-113">For example, the following query statement retrieves the **SalesPersonID**, **SalesQuota**, and **SalesYTD** from the AdventureWorks database for sales persons whose commission percentage is more than 1.5 percent.</span></span>  
  
```  
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  
  
 <span data-ttu-id="34680-114">**Parse**</span><span class="sxs-lookup"><span data-stu-id="34680-114">**Parse**</span></span>  
 <span data-ttu-id="34680-115">**SQL 문** 입력란에 입력된 SQL 문의 구문을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="34680-115">Checks the syntax of the SQL statement in the **SQL statement** text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34680-116">이 문의 구문을 검사하는 데 필요한 시간이 제한 시간 값인 30초를 초과하면 구문 분석이 중지되고 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="34680-116">If the time that is required to check the syntax of the statement exceeds the time-out value of 30 seconds, parsing stops and generates an error.</span></span> <span data-ttu-id="34680-117">구문 분석이 성공할 때까지는 이 마법사 페이지를 지나서 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34680-117">You will not be able to move past this page of the wizard until parsing succeeds.</span></span> <span data-ttu-id="34680-118">한 가지 해결 방법은 쿼리를 기반으로 하는 데이터베이스 뷰를 만든 다음 쿼리 텍스트를 직접 입력하는 대신 마법사에서 이 뷰를 쿼리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="34680-118">One solution is to create a database view based on the query, and to query the view from the wizard, instead of entering the query text directly.</span></span>  
  
 <span data-ttu-id="34680-119">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="34680-119">**Browse**</span></span>  
 <span data-ttu-id="34680-120">**열기** 대화 상자를 사용하여 SQL 문이 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34680-120">Select a file containing a SQL statement by using the **Open** dialog box.</span></span> <span data-ttu-id="34680-121">파일을 선택하면 해당 파일의 텍스트가 **쿼리 문** 의 입력란으로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="34680-121">Selecting a file copies the text from the file into the **Query statement** text box.</span></span>  
  
  
