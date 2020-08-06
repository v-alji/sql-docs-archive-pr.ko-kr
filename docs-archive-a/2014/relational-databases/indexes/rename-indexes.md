---
title: 인덱스 이름 바꾸기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- renaming indexes
- index names [SQL Server]
- indexes [SQL Server], renaming
ms.assetid: d3d612a1-ea1b-4d99-85d2-0a2ad54f4b0e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 184d6e20f7857c5ea3535e77e21a0630ffc7b678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660555"
---
# <a name="rename-indexes"></a><span data-ttu-id="89673-102">인덱스 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="89673-102">Rename Indexes</span></span>
  <span data-ttu-id="89673-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 인덱스 이름을 바꾸는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-103">This topic describes how to rename an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="89673-104">인덱스 이름을 바꾸면 현재 인덱스 이름이 새 이름으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="89673-104">Renaming an index replaces the current index name with the new name that you provide.</span></span> <span data-ttu-id="89673-105">지정된 이름은 테이블 또는 뷰에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-105">The specified name must be unique within the table or view.</span></span> <span data-ttu-id="89673-106">예를 들어 **XPK_1**이라는 인덱스가 두 테이블에 있을 수는 있지만 동일한 테이블에 **XPK_1**이라는 인덱스가 두 개 있을 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89673-106">For example, two tables can have an index named **XPK_1**, but the same table cannot have two indexes named **XPK_1**.</span></span> <span data-ttu-id="89673-107">기존의 비활성 인덱스와 동일한 이름의 인덱스는 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89673-107">You cannot create an index with the same name as an existing disabled index.</span></span> <span data-ttu-id="89673-108">인덱스 이름을 바꾼다고 인덱스가 다시 작성되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="89673-108">Renaming an index does not cause the index to be rebuilt.</span></span>  
  
 <span data-ttu-id="89673-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="89673-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="89673-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="89673-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="89673-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="89673-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="89673-112">보안</span><span class="sxs-lookup"><span data-stu-id="89673-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="89673-113">**인덱스 이름을 바꾸려면:**</span><span class="sxs-lookup"><span data-stu-id="89673-113">**To rename an index, using:**</span></span>  
  
     [<span data-ttu-id="89673-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="89673-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="89673-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="89673-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="89673-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="89673-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="89673-117">제한 사항</span><span class="sxs-lookup"><span data-stu-id="89673-117">Limitations and Restrictions</span></span>  
 <span data-ttu-id="89673-118">테이블에서 PRIMARY KEY 또는 UNIQUE 제약 조건을 만들 때 제약 조건과 이름이 같은 인덱스가 테이블에 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="89673-118">When you create a PRIMARY KEY or UNIQUE constraint on a table, an index with the same name as the constraint is automatically created for the table.</span></span> <span data-ttu-id="89673-119">인덱스 이름은 테이블에서 고유해야 하므로 테이블에서 기존의 PRIMARY KEY 또는 UNIQUE 제약 조건과 같은 이름으로 인덱스를 만들거나 인덱스 이름을 같은 이름으로 바꿀 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89673-119">Because index names must be unique within the table, you cannot create or rename an index to have the same name as an existing PRIMARY KEY or UNIQUE constraint on the table.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="89673-120">보안</span><span class="sxs-lookup"><span data-stu-id="89673-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="89673-121">권한</span><span class="sxs-lookup"><span data-stu-id="89673-121">Permissions</span></span>  
 <span data-ttu-id="89673-122">인덱스에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-122">Requires ALTER permission on the index.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="89673-123">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="89673-123">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-an-index-by-using-the-table-designer"></a><span data-ttu-id="89673-124">테이블 디자이너를 사용하여 인덱스 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="89673-124">To rename an index by using the Table Designer</span></span>  
  
1.  <span data-ttu-id="89673-125">개체 탐색기에서 더하기 기호를 클릭하여 인덱스 이름을 바꿀 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-125">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rename an index.</span></span>  
  
2.  <span data-ttu-id="89673-126">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-126">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="89673-127">인덱스 이름을 바꿀 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-127">Right-click the table on which you want to rename an index and select **Design**.</span></span>  
  
4.  <span data-ttu-id="89673-128">**테이블 디자이너** 메뉴에서 **인덱스/키**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-128">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="89673-129">**선택한 기본/고유 키 또는 인덱스** 입력란에서 이름을 바꿀 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-129">Select the index you want to rename in the **Selected Primary/Unique Key or Index** text box.</span></span>  
  
6.  <span data-ttu-id="89673-130">표에서 **이름** 을 클릭하고 새 이름을 입력란에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-130">In the grid, click **Name** and type a new name into the text box.</span></span>  
  
7.  <span data-ttu-id="89673-131">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-131">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="89673-132">**파일** 메뉴에서 _table name_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-132">On the **File** menu, click **Save**_table_name_.</span></span>  
  
#### <a name="to-rename-an-index-by-using-object-explorer"></a><span data-ttu-id="89673-133">개체 탐색기를 사용하여 인덱스 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="89673-133">To rename an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="89673-134">개체 탐색기에서 더하기 기호를 클릭하여 인덱스 이름을 바꿀 테이블이 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-134">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to rename an index.</span></span>  
  
2.  <span data-ttu-id="89673-135">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-135">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="89673-136">더하기 기호를 클릭하여 인덱스 이름을 바꿀 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-136">Click the plus sign to expand the table on which you want to rename an index.</span></span>  
  
4.  <span data-ttu-id="89673-137">더하기 기호를 클릭하여 **인덱스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-137">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="89673-138">이름을 바꿀 인덱스를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-138">Right-click the index you want to rename and select **Rename**.</span></span>  
  
6.  <span data-ttu-id="89673-139">인덱스의 새 이름을 입력하고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="89673-139">Type the index's new name and press Enter.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="89673-140">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="89673-140">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-an-index"></a><span data-ttu-id="89673-141">인덱스 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="89673-141">To rename an index</span></span>  
  
1.  <span data-ttu-id="89673-142">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="89673-143">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="89673-144">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89673-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    --Renames the IX_ProductVendor_VendorID index on the Purchasing.ProductVendor table to IX_VendorID.   
  
    EXEC sp_rename N'Purchasing.ProductVendor.IX_ProductVendor_VendorID', N'IX_VendorID', N'INDEX';   
    GO  
    ```  
  
 <span data-ttu-id="89673-145">자세한 내용은 [sp_rename&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89673-145">For more information, see  [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
