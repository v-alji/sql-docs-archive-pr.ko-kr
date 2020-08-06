---
title: UNIQUE 제약 조건 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- UNIQUE constraints [SQL Server], deleting
- constraints [SQL Server], deleting
- deleting constraints
- constraints [SQL Server], unique
ms.assetid: 71e563fc-f5d7-4c2e-a42f-f0695a831f32
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2fe2264aed4eb2f292a6bd1e4e565cebe2a833f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652697"
---
# <a name="delete-unique-constraints"></a><span data-ttu-id="42b4e-102">UNIQUE 제약 조건 삭제</span><span class="sxs-lookup"><span data-stu-id="42b4e-102">Delete Unique Constraints</span></span>
  <span data-ttu-id="42b4e-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 UNIQUE 제약 조건을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-103">You can delete a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="42b4e-104">UNIQUE 제약 조건을 삭제하면 제약 조건 식에 포함된 열 또는 열 조합에 입력한 값의 고유성 요구 사항이 제거되고 해당 고유 인덱스가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-104">Deleting a unique constraint removes the requirement for uniqueness for values entered in the column or combination of columns included in the constraint expression and deletes the corresponding unique index.</span></span>  
  
 <span data-ttu-id="42b4e-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="42b4e-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="42b4e-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="42b4e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="42b4e-107">보안</span><span class="sxs-lookup"><span data-stu-id="42b4e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="42b4e-108">**UNIQUE 제약 조건을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="42b4e-108">**To delete a unique constraint, using:**</span></span>  
  
     [<span data-ttu-id="42b4e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="42b4e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="42b4e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42b4e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="42b4e-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="42b4e-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="42b4e-112">보안</span><span class="sxs-lookup"><span data-stu-id="42b4e-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="42b4e-113">권한</span><span class="sxs-lookup"><span data-stu-id="42b4e-113">Permissions</span></span>  
 <span data-ttu-id="42b4e-114">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="42b4e-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="42b4e-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-unique-constraint-using-object-explorer"></a><span data-ttu-id="42b4e-116">개체 탐색기를 사용하여 UNIQUE 제약 조건을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="42b4e-116">To delete a unique constraint using Object Explorer</span></span>  
  
1.  <span data-ttu-id="42b4e-117">개체 탐색기에서 UNIQUE 제약 조건이 포함된 테이블을 확장한 후 **제약 조건**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-117">In Object Explorer, expand the table that contains the unique constraint and then expand **Constraints**.</span></span>  
  
2.  <span data-ttu-id="42b4e-118">키를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-118">Right-click the key and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="42b4e-119">**개체 삭제** 대화 상자에서 올바른 키가 지정되었는지 확인하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-119">In the **Delete Object** dialog box, verify the correct key is specified and click **OK**.</span></span>  
  
#### <a name="to-delete-a-unique-constraint-using-table-designer"></a><span data-ttu-id="42b4e-120">테이블 디자이너를 사용하여 UNIQUE 제약 조건을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="42b4e-120">To delete a unique constraint using Table Designer</span></span>  
  
1.  <span data-ttu-id="42b4e-121">**개체 탐색기**에서 UNIQUE 제약 조건이 있는 테이블을 마우스 오른쪽 단추로 클릭한 다음 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-121">In **Object Explorer**, right-click the table with the unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="42b4e-122">**테이블 디자이너** 메뉴에서 **인덱스/키**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-122">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
3.  <span data-ttu-id="42b4e-123">**인덱스/키** 대화 상자의 **선택한 기본/고유 키 및 인덱스** 목록에서 고유 키를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-123">In the **Indexes/Keys** dialog box, select the unique key in the **Selected Primary/Unique Key and Index** list.</span></span>  
  
4.  <span data-ttu-id="42b4e-124">**삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-124">Click **Delete**.</span></span>  
  
5.  <span data-ttu-id="42b4e-125">**파일** 메뉴에서 ‘테이블 이름’ **저장**을 클릭합니다. </span><span class="sxs-lookup"><span data-stu-id="42b4e-125">On the **File** menu, click **Save** _table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="42b4e-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="42b4e-126">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-unique-constraint"></a><span data-ttu-id="42b4e-127">UNIQUE 제약 조건을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="42b4e-127">To delete a unique constraint</span></span>  
  
1.  <span data-ttu-id="42b4e-128">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="42b4e-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="42b4e-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42b4e-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Return the name of unique constraint.  
    SELECT name  
    FROM sys.objects  
    WHERE type = 'UQ' AND OBJECT_NAME(parent_object_id) = N' DocExc';  
    GO  
    -- Delete the unique constraint.  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT UNQ_ColumnB_DocExc;  
    GO  
    ```  
  
 <span data-ttu-id="42b4e-131">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 및 [sys.objects&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42b4e-131">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) and [sys.objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
