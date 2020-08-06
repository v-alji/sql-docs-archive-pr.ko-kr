---
title: 테이블에 열 추가(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- adding columns
ms.assetid: abeb8d52-d562-4e29-9e1e-2923ae874859
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7e9294de10be0df9ef470c75d0934e9f8787b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650877"
---
# <a name="add-columns-to-a-table-database-engine"></a><span data-ttu-id="cf65a-102">테이블에 열 추가(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="cf65a-102">Add Columns to a Table (Database Engine)</span></span>
  <span data-ttu-id="cf65a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 테이블에 새 열을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-103">This topic describes how to add new columns to a table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="cf65a-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="cf65a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cf65a-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="cf65a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cf65a-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="cf65a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="cf65a-107">보안</span><span class="sxs-lookup"><span data-stu-id="cf65a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cf65a-108">**열을 삽입하려면**</span><span class="sxs-lookup"><span data-stu-id="cf65a-108">**To insert columns, using:**</span></span>  
  
     [<span data-ttu-id="cf65a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cf65a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cf65a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cf65a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cf65a-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="cf65a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cf65a-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="cf65a-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="cf65a-113">ALTER TABLE 문을 사용하여 테이블에 열을 추가하면 해당 열이 자동으로 테이블 끝에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-113">Using the ALTER TABLE statement to add columns to a table automatically adds those columns to the end of the table.</span></span> <span data-ttu-id="cf65a-114">테이블에서 특정 순서로 열을 지정하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-114">If you want the columns in a specific order in the table, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="cf65a-115">하지만 이러한 방식은 데이터베이스 설계상 최선의 방법이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-115">However, note that this is not a database design best practice.</span></span> <span data-ttu-id="cf65a-116">가장 좋은 방법은 애플리케이션 및 쿼리 수준에서 반환된 열에서 순서를 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-116">Best practice is to specify the order in which the columns are returned at the application and query level.</span></span> <span data-ttu-id="cf65a-117">SELECT \*를 사용해도 테이블에 정의된 순서에 따라 모든 열이 순서대로 반환된다고 가정해서는 안됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-117">You should not rely on the use of SELECT \* to return all columns in an expected order based on the order in which they are defined in the table.</span></span> <span data-ttu-id="cf65a-118">항상 열을 표시하려는 순서에 따라 쿼리 및 애플리케이션에서 이름으로 열을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="cf65a-118">Always specify the columns by name in your queries and applications in the order in which you would like them to appear.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cf65a-119">보안</span><span class="sxs-lookup"><span data-stu-id="cf65a-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cf65a-120">권한</span><span class="sxs-lookup"><span data-stu-id="cf65a-120">Permissions</span></span>  
 <span data-ttu-id="cf65a-121">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cf65a-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="cf65a-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-insert-columns-into-a-table-with-table-designer"></a><span data-ttu-id="cf65a-123">테이블 디자이너에서 테이블에 열을 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="cf65a-123">To insert columns into a table with Table Designer</span></span>  
  
1.  <span data-ttu-id="cf65a-124">**개체 탐색기**에서 열을 추가할 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-124">In **Object Explorer**, right-click the table to which you want to add columns and choose **Design**.</span></span>  
  
2.  <span data-ttu-id="cf65a-125">**열 이름** 열에서 첫 번째 빈 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-125">Click in the first blank cell in the **Column Name** column.</span></span>  
  
3.  <span data-ttu-id="cf65a-126">셀에 열 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-126">Type the column name in the cell.</span></span> <span data-ttu-id="cf65a-127">열 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-127">The column name is a required value.</span></span>  
  
4.  <span data-ttu-id="cf65a-128">Tab 키를 눌러 **데이터 형식** 셀로 이동한 다음 드롭다운에서 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-128">Press the TAB key to go to the **Data Type** cell and select a data type from the dropdown.</span></span> <span data-ttu-id="cf65a-129">데이터 형식도 반드시 지정해야 하며, 사용자가 이 값을 선택하지 않으면 기본값이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-129">This too is a required value, and will be assigned the default value if you don't choose one.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cf65a-130">**데이터베이스 도구** 아래의 **옵션**대화 상자에서 기본값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-130">You can change the default value in the **Options** dialog box under **Database Tools**.</span></span>  
  
5.  <span data-ttu-id="cf65a-131">**열 속성** 탭에서 다른 열 속성을 계속 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-131">Continue to define any other column properties in the **Column Properties** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cf65a-132"> 새 열을 만들면 열 속성에 기본값이 자동으로 추가됩니다. 이러한 값은 **열 속성** 탭에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-132">The default values for your column properties are added when you create a new column, but you can change them in the **Column Properties** tab.</span></span>  
  
6.  <span data-ttu-id="cf65a-133">열을 모두 추가했으면 **파일** 메뉴에서 ‘테이블 이름’ **저장**을 선택합니다.__</span><span class="sxs-lookup"><span data-stu-id="cf65a-133">When you are finished adding columns, from the **File** menu, choose **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cf65a-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="cf65a-134">Using Transact-SQL</span></span>  
  
#### <a name="to-insert-columns-into-a-table"></a><span data-ttu-id="cf65a-135">테이블에 열을 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="cf65a-135">To insert columns into a table</span></span>  
  
1.  <span data-ttu-id="cf65a-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf65a-137">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cf65a-138">다음 예에서는 `dbo.doc_exa`테이블에 두 개의 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-138">The following example adds two columns to the table `dbo.doc_exa`.</span></span> <span data-ttu-id="cf65a-139">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf65a-139">Copy and paste the following example into the query window and click **Execute**</span></span>  
  
```  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL, column_c INT NULL ;  
```  
  
##  <a name="for-more-information-see-alter-table-40transact-sql41"></a><a name="FollowUp"></a><span data-ttu-id="cf65a-140">자세한 내용은 [ALTER TABLE &#40;transact-sql](/sql/t-sql/statements/alter-table-transact-sql) 을 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="cf65a-140">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)</span></span>  
  
  
