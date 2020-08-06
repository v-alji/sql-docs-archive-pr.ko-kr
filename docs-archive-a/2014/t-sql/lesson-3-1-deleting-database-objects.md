---
title: 데이터베이스 개체 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6bd69935dbfac020c4c75bb391e7932009fd4197
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646794"
---
# <a name="deleting-database-objects"></a><span data-ttu-id="abf06-102">데이터베이스 개체 삭제</span><span class="sxs-lookup"><span data-stu-id="abf06-102">Deleting Database Objects</span></span>
  <span data-ttu-id="abf06-103">이 자습서의 모든 추적 내용을 제거하려면 데이터베이스를 삭제하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-103">To remove all traces of this tutorial, you could just delete the database.</span></span> <span data-ttu-id="abf06-104">그러나 이 항목에서는 자습서에서 수행한 모든 동작을 되돌리는 단계를 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-104">However, in this topic, you will go through the steps to reverse every action you took doing the tutorial.</span></span>  
  
### <a name="removing-permissions-and-objects"></a><span data-ttu-id="abf06-105">사용 권한 및 개체 제거</span><span class="sxs-lookup"><span data-stu-id="abf06-105">Removing permissions and objects</span></span>  
  
1.  <span data-ttu-id="abf06-106">개체를 삭제하기 전에 사용자가 올바른 데이터베이스에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-106">Before you delete objects, make sure you are in the correct database:</span></span>  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  <span data-ttu-id="abf06-107">`REVOKE` 문을 사용하여 저장 프로시저에 대한 `Mary` 의 실행 권한을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-107">Use the `REVOKE` statement to remove execute permission for `Mary` on the stored procedure:</span></span>  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  <span data-ttu-id="abf06-108">`DROP` 문을 사용하여 `Mary` 가 `TestData` 데이터베이스에 액세스할 수 있는 권한을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-108">Use the `DROP` statement to remove permission for `Mary` to access the `TestData` database:</span></span>  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  <span data-ttu-id="abf06-109">`DROP` 문을 사용하여 `Mary` 가 이 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]인스턴스에 액세스할 수 있는 권한을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-109">Use the `DROP` statement to remove permission for `Mary` to access this instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]:</span></span>  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  <span data-ttu-id="abf06-110">`DROP` 문을 사용하여 `pr_Names`저장 프로시저를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-110">Use the `DROP` statement to remove the store procedure `pr_Names`:</span></span>  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  <span data-ttu-id="abf06-111">`DROP` 문을 사용하여 `vw_Names`뷰를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-111">Use the `DROP` statement to remove the view `vw_Names`:</span></span>  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  <span data-ttu-id="abf06-112">`DELETE` 문을 사용하여 `Products` 테이블에서 모든 행을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-112">Use the `DELETE` statement to remove all rows from the `Products` table:</span></span>  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  <span data-ttu-id="abf06-113">`DROP` 문을 사용하여 `Products` 테이블을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-113">Use the `DROP` statement to remove the `Products` table:</span></span>  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. <span data-ttu-id="abf06-114">사용자가 `TestData` 데이터베이스에 있는 동안에는 이 데이터베이스를 제거할 수 없습니다. 따라서 먼저 컨텍스트를 다른 데이터베이스로 전환한 다음 `DROP` 문을 사용하여 `TestData` 데이터베이스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-114">You cannot remove the `TestData` database while you are in the database; therefore, first switch context to another database, and then use the `DROP` statement to remove the `TestData` database:</span></span>  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
 <span data-ttu-id="abf06-115">이것으로 [!INCLUDE[tsql](../includes/tsql-md.md)] 문 작성 자습서를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-115">This concludes the Writing [!INCLUDE[tsql](../includes/tsql-md.md)] Statements tutorial.</span></span> <span data-ttu-id="abf06-116">이 자습서는 간략한 개요이므로 사용된 문에 대한 모든 옵션을 설명하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-116">Remember, this tutorial is a brief overview and it does not describe all the options to the statements that are used.</span></span> <span data-ttu-id="abf06-117">효율적인 데이터베이스 구조를 디자인 및 작성하고 데이터에 대한 보안 액세스를 구성하려면 이 자습서의 예제 데이터베이스보다 복잡한 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="abf06-117">Designing and creating an efficient database structure and configuring secure access to the data requires a more complex database than that shown in this tutorial.</span></span>  
  
## <a name="return-to-sql-server-tools-portal"></a><span data-ttu-id="abf06-118">SQL Server 도구 포털로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="abf06-118">Return to SQL Server Tools Portal</span></span>  
 [<span data-ttu-id="abf06-119">자습서: Transact-SQL 문 작성</span><span class="sxs-lookup"><span data-stu-id="abf06-119">Tutorial: Writing Transact-SQL Statements</span></span>](tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a><span data-ttu-id="abf06-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="abf06-120">See Also</span></span>  
 <span data-ttu-id="abf06-121">[REVOKE&#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="abf06-121">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span></span>  
 <span data-ttu-id="abf06-122">[DROP USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="abf06-122">[DROP USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-user-transact-sql) </span></span>  
 <span data-ttu-id="abf06-123">[DROP LOGIN &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="abf06-123">[DROP LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-login-transact-sql) </span></span>  
 <span data-ttu-id="abf06-124">[DROP PROCEDURE &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="abf06-124">[DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span></span>  
 <span data-ttu-id="abf06-125">[DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="abf06-125">[DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql) </span></span>  
 <span data-ttu-id="abf06-126">[DELETE&#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="abf06-126">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span></span>  
 <span data-ttu-id="abf06-127">[DROP TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="abf06-127">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span></span>  
 [<span data-ttu-id="abf06-128">DROP DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="abf06-128">DROP DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)  
  
  
