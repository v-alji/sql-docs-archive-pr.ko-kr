---
title: 열 수정(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying data types
- column data types [SQL Server]
- data types [SQL Server], columns
ms.assetid: b67b95c5-61ef-4bd8-9a3e-1640eb7583ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: a73c25d91b742f1cc1f7edcc8a95cdf226b2683c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652027"
---
# <a name="modify-columns-database-engine"></a><span data-ttu-id="4f466-102">열 수정(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="4f466-102">Modify Columns (Database Engine)</span></span>
  <span data-ttu-id="4f466-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 열의 데이터 형식을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-103">You can modify the data type of a column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="4f466-104">이미 데이터가 포함되어 있는 열의 데이터 형식을 수정하면 기존 데이터를 새 형식으로 변환하는 과정에서 데이터를 완전히 잃을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-104">Modifying the data type of a column that already contains data can result in the permanent loss of data when the existing data is converted to the new type.</span></span> <span data-ttu-id="4f466-105">또한 수정된 열에 의존하고 있는 코드나 애플리케이션에 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-105">In addition, code and applications that depend on the modified column may fail.</span></span> <span data-ttu-id="4f466-106">여기에는 쿼리, 뷰, 저장 프로시저, 사용자 정의 함수, 클라이언트 애플리케이션 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-106">These include queries, views, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="4f466-107">이러한 문제는 연쇄적인 파급 효과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-107">Note that these failures will cascade.</span></span> <span data-ttu-id="4f466-108">예를 들어 수정된 열에 의존하는 사용자 정의 함수를 호출하는 저장 프로시저가 실패할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-108">For example, a stored procedure that calls a user-defined function that depends on the modified column may fail.</span></span> <span data-ttu-id="4f466-109">따라서 열을 변경할 때는 이러한 결과를 미리 신중하게 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-109">Carefully consider any changes you want to make to a column before making it.</span></span>  
  
 <span data-ttu-id="4f466-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4f466-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4f466-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4f466-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4f466-112">보안</span><span class="sxs-lookup"><span data-stu-id="4f466-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4f466-113">**열의 데이터 형식을 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="4f466-113">**To modify the data type of a column, using:**</span></span>  
  
     [<span data-ttu-id="4f466-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4f466-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4f466-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4f466-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4f466-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4f466-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4f466-117">보안</span><span class="sxs-lookup"><span data-stu-id="4f466-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4f466-118">권한</span><span class="sxs-lookup"><span data-stu-id="4f466-118">Permissions</span></span>  
 <span data-ttu-id="4f466-119">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-119">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4f466-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4f466-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-the-data-type-of-a-column"></a><span data-ttu-id="4f466-121">열의 데이터 형식을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="4f466-121">To modify the data type of a column</span></span>  
  
1.  <span data-ttu-id="4f466-122">**개체 탐색기**에서 소수 자릿수를 변경할 열이 포함된 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-122">In **Object Explorer**, right-click the table with columns for which you want to change the scale and click **Design**.</span></span>  
  
2.  <span data-ttu-id="4f466-123">데이터 형식을 수정하려는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-123">Select the column for which you want to modify the data type.</span></span>  
  
3.  <span data-ttu-id="4f466-124">**열 속성** 탭에서 **데이터 형식** 속성의 표 형태 셀을 클릭하고 드롭다운 목록에서 새 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-124">In the **Column Properties** tab, click the grid cell for the **Data Type** property and choose a new data type from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="4f466-125">**파일** 메뉴에서 _테이블 이름_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-125">On the **File** menu, click **Save**_table name_.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f466-126">열의 데이터 형식을 수정하면 선택한 데이터 형식에 대해 이미 다른 길이를 지정했더라도 테이블 디자이너에서 해당 형식의 기본 길이가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-126">When you modify the data type of a column, Table Designer applies the default length of the data type you selected, even if you have already specified another.</span></span> <span data-ttu-id="4f466-127">데이터 형식을 지정한 후에 항상 데이터 형식 길이를 원하는 값으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-127">Always set the data type length for to the desired value after specifying the data type.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="4f466-128">다른 테이블과 연관된 열의 데이터 형식을 수정하려고 시도하면 해당 변경 내용을 다른 테이블에도 적용할지 묻는 확인 메시지가 테이블 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-128">If you attempt to modify the data type of a column that relates to other tables, Table Designer asks you to confirm that the change should be made to the columns in the other tables as well.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4f466-129">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4f466-129">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-the-data-type-of-a-column"></a><span data-ttu-id="4f466-130">열의 데이터 형식을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="4f466-130">To modify the data type of a column</span></span>  
  
1.  <span data-ttu-id="4f466-131">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4f466-132">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4f466-133">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4f466-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    CREATE TABLE dbo.doc_exy (column_a INT ) ;  
    GO  
    INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
    GO  
    ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
    GO  
  
    ```  
  
 <span data-ttu-id="4f466-134">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4f466-134">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)</span></span>  
  
  
