---
title: 테이블에서 데이터 삽입 및 업데이트(자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- inserting and updating data
ms.assetid: 514dc87a-b829-43b5-8fc8-1a400a260284
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0646019f166e1c2cc126a4cc7d2ed8f27a7bd2f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652474"
---
# <a name="inserting-and-updating-data-in-a-table-tutorial"></a><span data-ttu-id="c961c-102">테이블에서 데이터 삽입 및 업데이트(자습서)</span><span class="sxs-lookup"><span data-stu-id="c961c-102">Inserting and Updating Data in a Table (Tutorial)</span></span>
  <span data-ttu-id="c961c-103">이제 **Products** 테이블을 만들었으므로 INSERT 문을 사용하여 테이블에 데이터를 삽입할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-103">Now that you have created the **Products** table, you are ready to insert data into the table by using the INSERT statement.</span></span> <span data-ttu-id="c961c-104">데이터가 삽입된 후 UPDATE 문을 사용하여 행 내용을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-104">After the data is inserted, you will change the content of a row by using an UPDATE statement.</span></span> <span data-ttu-id="c961c-105">UPDATE 문의 WHERE 절을 사용하여 업데이트를 단일 행으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-105">You will use the WHERE clause of the UPDATE statement to restrict the update to a single row.</span></span> <span data-ttu-id="c961c-106">4개의 문이 다음 데이터를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-106">The four statements will enter the following data.</span></span>  
  
|<span data-ttu-id="c961c-107">ProductID</span><span class="sxs-lookup"><span data-stu-id="c961c-107">ProductID</span></span>|<span data-ttu-id="c961c-108">ProductName</span><span class="sxs-lookup"><span data-stu-id="c961c-108">ProductName</span></span>|<span data-ttu-id="c961c-109">가격</span><span class="sxs-lookup"><span data-stu-id="c961c-109">Price</span></span>|<span data-ttu-id="c961c-110">ProductDescription</span><span class="sxs-lookup"><span data-stu-id="c961c-110">ProductDescription</span></span>|  
|---------------|-----------------|-----------|------------------------|  
|<span data-ttu-id="c961c-111">1</span><span class="sxs-lookup"><span data-stu-id="c961c-111">1</span></span>|<span data-ttu-id="c961c-112">Clamp</span><span class="sxs-lookup"><span data-stu-id="c961c-112">Clamp</span></span>|<span data-ttu-id="c961c-113">12.48</span><span class="sxs-lookup"><span data-stu-id="c961c-113">12.48</span></span>|<span data-ttu-id="c961c-114">Workbench clamp</span><span class="sxs-lookup"><span data-stu-id="c961c-114">Workbench clamp</span></span>|  
|<span data-ttu-id="c961c-115">50</span><span class="sxs-lookup"><span data-stu-id="c961c-115">50</span></span>|<span data-ttu-id="c961c-116">Screwdriver</span><span class="sxs-lookup"><span data-stu-id="c961c-116">Screwdriver</span></span>|<span data-ttu-id="c961c-117">3.17</span><span class="sxs-lookup"><span data-stu-id="c961c-117">3.17</span></span>|<span data-ttu-id="c961c-118">Flat head</span><span class="sxs-lookup"><span data-stu-id="c961c-118">Flat head</span></span>|  
|<span data-ttu-id="c961c-119">75</span><span class="sxs-lookup"><span data-stu-id="c961c-119">75</span></span>|<span data-ttu-id="c961c-120">Tire Bar</span><span class="sxs-lookup"><span data-stu-id="c961c-120">Tire Bar</span></span>||<span data-ttu-id="c961c-121">Tool for changing tires.</span><span class="sxs-lookup"><span data-stu-id="c961c-121">Tool for changing tires.</span></span>|  
|<span data-ttu-id="c961c-122">3000</span><span class="sxs-lookup"><span data-stu-id="c961c-122">3000</span></span>|<span data-ttu-id="c961c-123">3mm Bracket</span><span class="sxs-lookup"><span data-stu-id="c961c-123">3mm Bracket</span></span>|<span data-ttu-id="c961c-124">.52</span><span class="sxs-lookup"><span data-stu-id="c961c-124">.52</span></span>||  
  
 <span data-ttu-id="c961c-125">기본 구문은 INSERT, 테이블 이름, 열 목록, VALUES, 삽입할 값 목록을 차례로 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-125">The basic syntax is: INSERT, table name, column list, VALUES, and then a list of the values to be inserted.</span></span> <span data-ttu-id="c961c-126">줄의 맨 앞에 있는 두 개의 하이픈은 해당 줄이 주석이며 컴파일러에서 텍스트를 무시한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-126">The two hyphens in front of a line indicate that the line is a comment and the text will be ignored by the compiler.</span></span> <span data-ttu-id="c961c-127">이 경우에는 허용되는 구문 변형을 주석에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-127">In this case, the comment describes a permissible variation of the syntax.</span></span>  
  
### <a name="to-insert-data-into-a-table"></a><span data-ttu-id="c961c-128">데이터를 테이블에 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="c961c-128">To insert data into a table</span></span>  
  
1.  <span data-ttu-id="c961c-129">다음 문을 실행하여 이전 태스크에서 만든 `Products` 테이블에 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-129">Execute the following statement to insert a row into the `Products` table that was created in the previous task.</span></span> <span data-ttu-id="c961c-130">기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-130">This is the basic syntax.</span></span>  
  
    ```  
    -- Standard syntax  
    INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
        VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
    GO  
  
    ```  
  
2.  <span data-ttu-id="c961c-131">다음 문은 필드 목록(괄호로 묶인 부분) 및 값 목록에서 `ProductID` 및 `ProductName` 의 위치를 전환하여 매개 변수가 제공되는 순서를 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-131">The following statement shows how you can change the order in which the parameters are provided by switching the placement of the `ProductID` and `ProductName` in both the field list (in parentheses) and in the values list.</span></span>  
  
    ```  
    -- Changing the order of the columns  
    INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
        VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
    GO  
  
    ```  
  
3.  <span data-ttu-id="c961c-132">다음 문은 값이 올바른 순서로 나열되는 경우 열 이름이 선택 사항임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-132">The following statement demonstrates that the names of the columns are optional, as long as the values are listed in the correct order.</span></span> <span data-ttu-id="c961c-133">이 구문이 일반적이기는 하지만 다른 사람이 코드를 이해하기 어려울 수 있으므로 이 구문을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-133">This syntax is common but is not recommended because it might be harder for others to understand your code.</span></span> <span data-ttu-id="c961c-134">`NULL` 이 `Price` 열에 대해 지정되는데, 이 제품의 가격을 아직 알 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-134">`NULL` is specified for the `Price` column because the price for this product is not yet known.</span></span>  
  
    ```  
    -- Skipping the column list, but keeping the values in order  
    INSERT dbo.Products  
        VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
    GO  
  
    ```  
  
4.  <span data-ttu-id="c961c-135">기본 스키마에서 테이블을 액세스 및 변경하는 경우 스키마 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-135">The schema name is optional as long as you are accessing and changing a table in your default schema.</span></span> <span data-ttu-id="c961c-136">`ProductDescription` 열에서 Null 값을 허용하고 제공되는 값이 없으므로 `ProductDescription` 열 이름과 값을 문에서 완전히 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-136">Because the `ProductDescription` column allows null values and no value is being provided, the `ProductDescription` column name and value can be dropped from the statement completely.</span></span>  
  
    ```  
    -- Dropping the optional dbo and dropping the ProductDescription column  
    INSERT Products (ProductID, ProductName, Price)  
        VALUES (3000, '3mm Bracket', .52)  
    GO  
    ```  
  
### <a name="to-update-the-products-table"></a><span data-ttu-id="c961c-137">Products 테이블을 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="c961c-137">To update the products table</span></span>  
  
1.  <span data-ttu-id="c961c-138">다음 `UPDATE` 문을 입력하고 실행하여 두 번째 제품의 `ProductName` 을 `Screwdriver`에서 `Flat Head Screwdriver`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c961c-138">Type and execute the following `UPDATE` statement to change the `ProductName` of the second product from `Screwdriver`, to `Flat Head Screwdriver`.</span></span>  
  
    ```  
    UPDATE dbo.Products  
        SET ProductName = 'Flat Head Screwdriver'  
        WHERE ProductID = 50  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c961c-139">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="c961c-139">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c961c-140">테이블의 데이터 읽기&#40;자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="c961c-140">Reading the Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-4-reading-the-data-in-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="c961c-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c961c-141">See Also</span></span>  
 <span data-ttu-id="c961c-142">[INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c961c-142">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 [<span data-ttu-id="c961c-143">UPDATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c961c-143">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
