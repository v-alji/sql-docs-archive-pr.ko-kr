---
title: 테이블의 데이터 읽기(자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- reading data in a table
ms.assetid: 532232c9-3d41-45cd-9150-de67a1cbfcf5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4bdaaeeddf8f35792c536624abfe6ff11b2dbd2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652475"
---
# <a name="reading-the-data-in-a-table-tutorial"></a><span data-ttu-id="2c709-102">테이블의 데이터 읽기(자습서)</span><span class="sxs-lookup"><span data-stu-id="2c709-102">Reading the Data in a Table (Tutorial)</span></span>
  <span data-ttu-id="2c709-103">SELECT 문을 사용하여 테이블의 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-103">Use the SELECT statement to read the data in a table.</span></span> <span data-ttu-id="2c709-104">SELECT 문은 가장 중요한 [!INCLUDE[tsql](../includes/tsql-md.md)] 문 중 하나이며 구문은 다양하게 변형되어 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-104">The SELECT statement is one of the most important [!INCLUDE[tsql](../includes/tsql-md.md)] statements, and there are many variations in the syntax.</span></span> <span data-ttu-id="2c709-105">이 자습서에서는 5개의 간단한 버전을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-105">For this tutorial, you will work with five simple versions.</span></span>  
  
### <a name="to-read-the-data-in-a-table"></a><span data-ttu-id="2c709-106">테이블의 데이터를 읽으려면</span><span class="sxs-lookup"><span data-stu-id="2c709-106">To read the data in a table</span></span>  
  
1.  <span data-ttu-id="2c709-107">다음 문을 입력하고 실행하여 `Products` 테이블의 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-107">Type and execute the following statements to read the data in the `Products` table.</span></span>  
  
    ```  
    -- The basic syntax for reading data from a single table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
    GO  
  
    ```  
  
2.  <span data-ttu-id="2c709-108">별표를 사용하여 테이블의 모든 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-108">You can use an asterisk to select all the columns in the table.</span></span> <span data-ttu-id="2c709-109">이 방법은 임시 쿼리에서 사용되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-109">This is often used in ad hoc queries.</span></span> <span data-ttu-id="2c709-110">나중에 새 열이 테이블에 추가되는 경우에도 문에서 예측된 열을 반환하도록 영구 코드로 열 목록을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-110">You should provide the column list in you permanent code so that the statement will return the predicted columns, even if a new column is added to the table later.</span></span>  
  
    ```  
    -- Returns all columns in the table  
    -- Does not use the optional schema, dbo  
    SELECT * FROM Products  
    GO  
  
    ```  
  
3.  <span data-ttu-id="2c709-111">반환하지 않으려는 열은 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-111">You can omit columns that you do not want to return.</span></span> <span data-ttu-id="2c709-112">열은 나열된 순서대로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-112">The columns will be returned in the order that they are listed.</span></span>  
  
    ```  
    -- Returns only two of the columns from the table  
    SELECT ProductName, Price  
        FROM dbo.Products  
    GO  
  
    ```  
  
4.  <span data-ttu-id="2c709-113">`WHERE` 절을 사용하여 사용자에게 반환되는 행을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-113">Use a `WHERE` clause to limit the rows that are returned to the user.</span></span>  
  
    ```  
    -- Returns only two of the records in the table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
        WHERE ProductID < 60  
    GO  
  
    ```  
  
5.  <span data-ttu-id="2c709-114">열이 반환되면 열의 값에 대한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-114">You can work with the values in the columns as they are returned.</span></span> <span data-ttu-id="2c709-115">다음 예는 `Price` 열에서 수치 연산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-115">The following example performs a mathematical operation on the `Price` column.</span></span> <span data-ttu-id="2c709-116">`AS` 키워드를 사용하여 이름을 제공하지 않은 경우 이 방법으로 변경된 열에는 이름이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c709-116">Columns that have been changed in this way will not have a name unless you provide one by using the `AS` keyword.</span></span>  
  
    ```  
    -- Returns ProductName and the Price including a 7% tax  
    -- Provides the name CustomerPays for the calculated column  
    SELECT ProductName, Price * 1.07 AS CustomerPays  
        FROM dbo.Products  
    GO  
    ```  
  
## <a name="functions-that-are-useful-in-a-select-statement"></a><span data-ttu-id="2c709-117">SELECT 문에 유용한 함수</span><span class="sxs-lookup"><span data-stu-id="2c709-117">Functions That Are Useful in a SELECT Statement</span></span>  
 <span data-ttu-id="2c709-118">SELECT 문에서 데이터 작업을 수행하는 데 사용할 수 있는 일부 함수에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2c709-118">For information about some functions that you can use to work with data in SELECT statements, see the following topics:</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="2c709-119">문자열 함수&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2c709-119">String Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/string-functions-transact-sql)|[<span data-ttu-id="2c709-120">날짜 및 시간 데이터 형식 및 함수 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2c709-120">Date and Time Data Types and Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|  
|[<span data-ttu-id="2c709-121">수치 연산 함수&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2c709-121">Mathematical Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)|[<span data-ttu-id="2c709-122">텍스트 및 이미지 함수&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2c709-122">Text and Image Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/text-and-image-functions-textptr-transact-sql)|  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2c709-123">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="2c709-123">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2c709-124">요약: 데이터베이스 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="2c709-124">Summary: Creating Database Objects</span></span>](lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="2c709-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c709-125">See Also</span></span>  
 [<span data-ttu-id="2c709-126">SELECT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2c709-126">SELECT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/select-transact-sql)  
  
  
