---
title: 사용자 정의 함수 실행 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
author: rothja
ms.author: jroth
ms.openlocfilehash: 4446f3b3a132488fdac6e859f30abaca40a193d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661588"
---
# <a name="execute-user-defined-functions"></a><span data-ttu-id="7cdb0-102">사용자 정의 함수 실행</span><span class="sxs-lookup"><span data-stu-id="7cdb0-102">Execute User-defined Functions</span></span>
  <span data-ttu-id="7cdb0-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 사용자 정의 함수를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-103">You can execute a user defined function in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7cdb0-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="7cdb0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7cdb0-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="7cdb0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7cdb0-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7cdb0-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7cdb0-107">보안</span><span class="sxs-lookup"><span data-stu-id="7cdb0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7cdb0-108">**사용자 정의 함수를 실행하려면:**</span><span class="sxs-lookup"><span data-stu-id="7cdb0-108">**To execute a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="7cdb0-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7cdb0-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7cdb0-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7cdb0-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7cdb0-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7cdb0-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="7cdb0-112">Transact-SQL에서 *value* 또는 @*parameter_name*=*value*를 사용하여 매개 변수를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-112">In Transact-SQL, parameters can be supplied either by using *value* or by using @*parameter_name*=*value.*</span></span> <span data-ttu-id="7cdb0-113">를 사용하여 제공할 수 있습니다. 매개 변수는 트랜잭션의 일부가 아니므로 나중에 롤백되는 트랜잭션에서 매개 변수가 변경된 경우 해당 매개 변수의 값은 이전 값으로 되돌아가지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-113">A parameter is not part of a transaction; therefore, if a parameter is changed in a transaction that is later rolled back, the value of the parameter does not revert to its previous value.</span></span> <span data-ttu-id="7cdb0-114">호출자에게 반환되는 값은 항상 모듈이 반환되는 시점의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-114">The value returned to the caller is always the value at the time the module returns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7cdb0-115">보안</span><span class="sxs-lookup"><span data-stu-id="7cdb0-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7cdb0-116">권한</span><span class="sxs-lookup"><span data-stu-id="7cdb0-116">Permissions</span></span>  
 <span data-ttu-id="7cdb0-117">EXECUTE 문을 실행하는 데에는 사용 권한이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-117">Permissions are not required to run the EXECUTE statement.</span></span> <span data-ttu-id="7cdb0-118">그러나 EXECUTE 문자열 내에서 참조되는 보안 개체에 대해서는 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-118">However, permissions are required on the securables that are referenced within the EXECUTE string.</span></span> <span data-ttu-id="7cdb0-119">예를 들어 문자열에 INSERT 문이 있는 경우 EXECUTE 문의 호출자에게는 대상 테이블에 대한 INSERT 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-119">For example, if the string contains an INSERT statement, the caller of the EXECUTE statement must have INSERT permission on the target table.</span></span> <span data-ttu-id="7cdb0-120">EXECUTE 문이 모듈 내에 포함된 경우에도 EXECUTE 문이 실행될 때는 사용 권한 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-120">Permissions are checked at the time EXECUTE statement is encountered, even if the EXECUTE statement is included within a module.</span></span> <span data-ttu-id="7cdb0-121">자세한 내용은 [EXECUTE &#40;transact-sql&#41;](/sql/t-sql/language-elements/execute-transact-sql) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-121">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7cdb0-122">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="7cdb0-122">Using Transact-SQL</span></span>  
  
#### <a name="to-execute-a-user-defined-function"></a><span data-ttu-id="7cdb0-123">사용자 정의 함수를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="7cdb0-123">To execute a user-defined function</span></span>  
  
1.  <span data-ttu-id="7cdb0-124">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7cdb0-125">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7cdb0-126">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Declares a variable and sets it to zero.  
    -- This variable is used to return the results of the function.  
    DECLARE @ret nvarchar(15)= NULL;   
  
    -- Executes the dbo.ufnGetSalesOrderStatusText function.  
    --The function requires a value for one parameter, @Status.   
    EXEC @ret = dbo.ufnGetSalesOrderStatusText @Status= 5;   
    --Returns the result in the message tab.  
    PRINT @ret;  
    ```  
  
 <span data-ttu-id="7cdb0-127">자세한 내용은 [EXECUTE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7cdb0-127">For more information, see [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
  
