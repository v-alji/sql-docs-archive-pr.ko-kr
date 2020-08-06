---
title: 뷰 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3e05724f7d6384d0407e915207ad60a1cdfb01b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646262"
---
# <a name="delete-views"></a><span data-ttu-id="6fb8e-102">뷰 삭제</span><span class="sxs-lookup"><span data-stu-id="6fb8e-102">Delete Views</span></span>
  <span data-ttu-id="6fb8e-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 다음을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 뷰를 삭제할 수 있습니다. [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb8e-103">You can delete (drop) views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6fb8e-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6fb8e-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6fb8e-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="6fb8e-105">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6fb8e-106">뷰를 삭제하면 해당 뷰의 정의 및 뷰에 대한 기타 정보가 시스템 카탈로그에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-106">When you drop a view, the definition of the view and other information about the view is deleted from the system catalog.</span></span> <span data-ttu-id="6fb8e-107">또한 해당 뷰에 대한 모든 권한도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-107">All permissions for the view are also deleted.</span></span>  
  
-   <span data-ttu-id="6fb8e-108">`DROP TABLE` 을 사용하여 삭제된 테이블의 모든 뷰는 `DROP VIEW`를 사용하여 명시적으로 삭제되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-108">Any view on a table that is dropped by using `DROP TABLE` must be dropped explicitly by using `DROP VIEW`.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6fb8e-109">보안</span><span class="sxs-lookup"><span data-stu-id="6fb8e-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6fb8e-110">권한</span><span class="sxs-lookup"><span data-stu-id="6fb8e-110">Permissions</span></span>  
 <span data-ttu-id="6fb8e-111">SCHEMA에 대한 ALTER 권한 또는 OBJECT에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-111">Requires ALTER permission on SCHEMA or CONTROL permission on OBJECT.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6fb8e-112">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6fb8e-112">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-view-from-a-database"></a><span data-ttu-id="6fb8e-113">데이터베이스에서 뷰를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6fb8e-113">To delete a view from a database</span></span>  
  
1.  <span data-ttu-id="6fb8e-114">**개체 탐색기**에서 삭제할 뷰가 포함된 데이터베이스를 확장한 다음 **뷰** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-114">In **Object Explorer**, expand the database that contains the view you want to delete, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="6fb8e-115">삭제할 뷰를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-115">Right-click the view you want to delete and click **Delete**.</span></span>  
  
3.  <span data-ttu-id="6fb8e-116">**개체 삭제** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-116">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6fb8e-117">**개체 삭제** 대화 상자에서 **종속성 표시** 를 클릭 하 여 _view_name_**종속성** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-117">Click **Show Dependencies** in the **Delete Object** dialog box to open the _view_name_**Dependencies** dialog box.</span></span> <span data-ttu-id="6fb8e-118">이 대화 상자에는 해당 뷰에 종속된 모든 개체와 해당 뷰가 종속된 모든 개체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-118">This will show all of the objects that depend on the view and all of the objects on which the view depends.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6fb8e-119">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="6fb8e-119">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-view-from-a-database"></a><span data-ttu-id="6fb8e-120">데이터베이스에서 뷰를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6fb8e-120">To delete a view from a database</span></span>  
  
1.  <span data-ttu-id="6fb8e-121">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6fb8e-122">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6fb8e-123">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6fb8e-124">다음 예에서는 지정된 뷰가 이미 존재하는 경우에만 해당 뷰를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-124">The example deletes the specified view only if the view already exists.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 <span data-ttu-id="6fb8e-125">자세한 내용은 [DROP VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6fb8e-125">For more information, see [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).</span></span>  
  
  
