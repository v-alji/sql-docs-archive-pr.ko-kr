---
title: CHECK 제약 조건 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- CHECK constraints, deleting
- constraints [SQL Server], deleting
- constraints [SQL Server], check
- deleting constraints
ms.assetid: 5f86c1a6-f5fa-4e77-a892-f6ae96fc0ab3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28a7f72993cbf2ed0a8cc76534380090ef0d0a55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650873"
---
# <a name="delete-check-constraints"></a><span data-ttu-id="2b8b1-102">CHECK 제약 조건 삭제</span><span class="sxs-lookup"><span data-stu-id="2b8b1-102">Delete Check Constraints</span></span>
  <span data-ttu-id="2b8b1-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 CHECK 제약 조건을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-103">You can delete a check constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2b8b1-104">CHECK 제약 조건을 삭제하면 제약 조건 식에 포함된 하나 이상의 열에 입력할 수 있는 데이터 값에 대한 제한 사항이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-104">Deleting check constraints removes the limitations on data values that are accepted in the column or columns included in the constraint expression.</span></span>  
  
 <span data-ttu-id="2b8b1-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="2b8b1-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2b8b1-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="2b8b1-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2b8b1-107">보안</span><span class="sxs-lookup"><span data-stu-id="2b8b1-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2b8b1-108">**CHECK 제약 조건을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="2b8b1-108">**To delete a check constraint, using:**</span></span>  
  
     [<span data-ttu-id="2b8b1-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2b8b1-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2b8b1-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2b8b1-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2b8b1-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="2b8b1-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2b8b1-112">보안</span><span class="sxs-lookup"><span data-stu-id="2b8b1-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2b8b1-113">권한</span><span class="sxs-lookup"><span data-stu-id="2b8b1-113">Permissions</span></span>  
 <span data-ttu-id="2b8b1-114">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2b8b1-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="2b8b1-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-check-constraint"></a><span data-ttu-id="2b8b1-116">CHECK 제약 조건을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="2b8b1-116">To delete a check constraint</span></span>  
  
1.  <span data-ttu-id="2b8b1-117">**개체 탐색기**에서 CHECK 제약 조건이 있는 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-117">In **Object Explorer**, expand the table with the check constraint.</span></span>  
  
2.  <span data-ttu-id="2b8b1-118">**제약 조건**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-118">Expand  **Constraints**.</span></span>  
  
3.  <span data-ttu-id="2b8b1-119">제약 조건을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-119">Right-click the constraint and click **Delete**.</span></span>  
  
4.  <span data-ttu-id="2b8b1-120">**개체 삭제** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-120">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2b8b1-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="2b8b1-121">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-check-constraint"></a><span data-ttu-id="2b8b1-122">CHECK 제약 조건을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="2b8b1-122">To delete a check constraint</span></span>  
  
1.  <span data-ttu-id="2b8b1-123">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2b8b1-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2b8b1-125">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT CHK_ColumnD_DocExc;  
    GO  
    ```  
  
 <span data-ttu-id="2b8b1-126">자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b8b1-126">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
  
