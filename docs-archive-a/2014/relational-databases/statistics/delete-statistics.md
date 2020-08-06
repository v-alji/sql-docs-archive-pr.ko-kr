---
title: 통계 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], deleting
- deleting statistics
ms.assetid: eccce0aa-591e-4a1d-bd10-373b022f8749
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 36b74d7e1465c0742cda4fef9f34fb4b3930719c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659884"
---
# <a name="delete-statistics"></a><span data-ttu-id="ab587-102">통계 삭제</span><span class="sxs-lookup"><span data-stu-id="ab587-102">Delete Statistics</span></span>
  <span data-ttu-id="ab587-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 다음을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 의 테이블 및 뷰에서 통계를 삭제할 수 있습니다. [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab587-103">You can delete (drop) statistics from tables and views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="ab587-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="ab587-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ab587-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="ab587-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ab587-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ab587-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ab587-107">보안</span><span class="sxs-lookup"><span data-stu-id="ab587-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ab587-108">**다음을 사용하여 테이블 또는 뷰에서 통계를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="ab587-108">**To drop statistics from a table or view, using:**</span></span>  
  
     [<span data-ttu-id="ab587-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab587-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ab587-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab587-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ab587-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ab587-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ab587-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ab587-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ab587-113">통계를 삭제할 때는 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="ab587-113">Be careful when you drop statistics.</span></span> <span data-ttu-id="ab587-114">통계를 삭제하면 쿼리 최적화 프로그램이 선택한 실행 계획에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-114">Doing so may affect the execution plan chosen by the query optimizer.</span></span>  
  
-   <span data-ttu-id="ab587-115">인덱스에 대한 통계는 DROP STATISTICS를 사용하여 삭제할 수 없으며</span><span class="sxs-lookup"><span data-stu-id="ab587-115">Statistics on indexes cannot be dropped by using DROP STATISTICS.</span></span> <span data-ttu-id="ab587-116">인덱스가 존재하는 한 통계도 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-116">Statistics remain as long as the index exists.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ab587-117">보안</span><span class="sxs-lookup"><span data-stu-id="ab587-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ab587-118">권한</span><span class="sxs-lookup"><span data-stu-id="ab587-118">Permissions</span></span>  
 <span data-ttu-id="ab587-119">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-119">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ab587-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ab587-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-drop-statistics-from-a-table-or-view"></a><span data-ttu-id="ab587-121">테이블 또는 뷰에서 통계를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="ab587-121">To drop statistics from a table or view</span></span>  
  
1.  <span data-ttu-id="ab587-122">**개체 탐색기**에서 더하기 기호를 클릭하여 통계를 삭제할 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-122">In **Object Explorer**, click the plus sign to expand the database in which you want to delete a statistic.</span></span>  
  
2.  <span data-ttu-id="ab587-123">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-123">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="ab587-124">더하기 기호를 클릭하여 통계를 삭제할 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-124">Click the plus sign to expand the table in which you want to delete a statistic.</span></span>  
  
4.  <span data-ttu-id="ab587-125">더하기 기호를 클릭하여 **통계** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-125">Click the plus sign to expand the **Statistics** folder.</span></span>  
  
5.  <span data-ttu-id="ab587-126">삭제할 통계 개체를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-126">Right-click the statistics object that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="ab587-127">**개체 삭제** 대화 상자에서 올바른 통계를 선택했는지 확인하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-127">In the **Delete Object** dialog box, ensure that the correct statistic has been selected and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ab587-128">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ab587-128">Using Transact-SQL</span></span>  
  
#### <a name="to-drop-statistics-from-a-table-or-view"></a><span data-ttu-id="ab587-129">테이블 또는 뷰에서 통계를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="ab587-129">To drop statistics from a table or view</span></span>  
  
1.  <span data-ttu-id="ab587-130">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ab587-131">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ab587-132">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ab587-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- First, create two statistics named VendorCredit and CustomerTotal  
    -- The first statistic uses a random 50% sample of information provided from the Name and CreditRating columns in the Purchasing.Vendor table.  
    CREATE STATISTICS VendorCredit  
        ON Purchasing.Vendor (Name, CreditRating)  
        WITH SAMPLE 50 PERCENT  
    -- The second statistic uses all of the information from the CustomerID and TotalDue columns in the Sales.SalesOrderHeader table  
    CREATE STATISTICS CustomerTotal  
        ON Sales.SalesOrderHeader (CustomerID, TotalDue)  
        WITH FULLSCAN;  
    GO  
    -- This next statement drops both of the statistics created above. Note that the naming convention is [table_name].[statistics_name].  
    DROP STATISTICS Purchasing.Vendor.VendorCredit, Sales.SalesOrderHeader.CustomerTotal;  
    GO  
    ```  
  
 <span data-ttu-id="ab587-133">자세한 내용은 [DROP STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab587-133">For more information, see [DROP STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-statistics-transact-sql).</span></span>  
  
  
