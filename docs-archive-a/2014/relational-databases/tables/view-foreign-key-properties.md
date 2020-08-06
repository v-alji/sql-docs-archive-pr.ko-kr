---
title: 외래 키 속성 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], attributes
- displaying foreign keys attributes
- viewing foreign keys attributes
ms.assetid: b0e57cb7-9b26-4b96-b76a-1f59f5f498c5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5860a0cf26b983d75bab86862ee1e5fdd7737712
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646833"
---
# <a name="view-foreign-key-properties"></a><span data-ttu-id="46eae-102">외래 키 속성 보기</span><span class="sxs-lookup"><span data-stu-id="46eae-102">View Foreign Key Properties</span></span>
  <span data-ttu-id="46eae-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 관계의 외래 키 특성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46eae-103">You can view the foreign key attributes of a relationship in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="46eae-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="46eae-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="46eae-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="46eae-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="46eae-106">보안</span><span class="sxs-lookup"><span data-stu-id="46eae-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="46eae-107">**특정 테이블의 외래 키 특성을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="46eae-107">**To view the foreign key attributes of a specific table, using:**</span></span>  
  
     [<span data-ttu-id="46eae-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="46eae-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="46eae-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="46eae-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="46eae-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="46eae-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="46eae-111">보안</span><span class="sxs-lookup"><span data-stu-id="46eae-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="46eae-112">권한</span><span class="sxs-lookup"><span data-stu-id="46eae-112">Permissions</span></span>  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] <span data-ttu-id="46eae-113">자세한 내용은 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46eae-113">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="46eae-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="46eae-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a><span data-ttu-id="46eae-115">특정 테이블의 관계에 대한 외래 키 특성을 보려면</span><span class="sxs-lookup"><span data-stu-id="46eae-115">To view the foreign key attributes of a relationship in a specific table</span></span>  
  
1.  <span data-ttu-id="46eae-116">보려는 외래 키가 포함된 테이블에 대한 테이블 디자이너를 열고 테이블 디자이너를 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **관계** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46eae-116">Open the Table Designer for the table containing the foreign key you want to view, right-click in the Table Designer, and choose **Relationships** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="46eae-117">**외래 키 관계** 대화 상자에서 표시하려는 속성이 포함된 관계를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46eae-117">In the **Foreign Key Relationships** dialog box, select the relationship with properties you want to view.</span></span>  
  
 <span data-ttu-id="46eae-118">외래 키 열이 기본 키에 연결되어 있으면 기본 키 열이 **테이블 디자이너** 의 행 선택기에서 기본 키 기호로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="46eae-118">If the foreign key columns are related to a primary key, the primary key columns are identified in **Table Designer** by a primary key symbol in the row selector.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="46eae-119">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="46eae-119">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a><span data-ttu-id="46eae-120">특정 테이블의 관계에 대한 외래 키 특성을 보려면</span><span class="sxs-lookup"><span data-stu-id="46eae-120">To view the foreign key attributes of a relationship in a specific table</span></span>  
  
1.  <span data-ttu-id="46eae-121">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="46eae-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="46eae-122">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46eae-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="46eae-123">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46eae-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="46eae-124">이 예에서는 예제 데이터베이스에 있는 `HumanResources.Employee` 테이블의 모든 외래 키와 해당 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="46eae-124">The example returns all foreign keys and their properties for the table `HumanResources.Employee` in the sample database.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT   
        f.name AS foreign_key_name  
       ,OBJECT_NAME(f.parent_object_id) AS table_name  
       ,COL_NAME(fc.parent_object_id, fc.parent_column_id) AS constraint_column_name  
       ,OBJECT_NAME (f.referenced_object_id) AS referenced_object  
       ,COL_NAME(fc.referenced_object_id, fc.referenced_column_id) AS referenced_column_name  
       ,is_disabled  
       ,delete_referential_action_desc  
       ,update_referential_action_desc  
    FROM sys.foreign_keys AS f  
    INNER JOIN sys.foreign_key_columns AS fc   
       ON f.object_id = fc.constraint_object_id   
    WHERE f.parent_object_id = OBJECT_ID('HumanResources.Employee');  
    ```  
  
 <span data-ttu-id="46eae-125">자세한 내용은 [sys.foreign_keys&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-keys-transact-sql) 및 [sys.foreign_key_columns&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46eae-125">For more information, see [sys.foreign_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-keys-transact-sql) and [sys.foreign_key_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
