---
title: 사용자 정의 함수 이름 바꾸기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: c2695a5c-9cc5-4b18-8771-53027ca9a9af
author: rothja
ms.author: jroth
ms.openlocfilehash: ec923be64cf7819c4018ebda71a472f58b29cf8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661585"
---
# <a name="rename-user-defined-functions"></a><span data-ttu-id="a5712-102">사용자 정의 함수 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="a5712-102">Rename User-defined Functions</span></span>
  <span data-ttu-id="a5712-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 사용자 정의 함수의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-103">You can rename user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a5712-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="a5712-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a5712-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a5712-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a5712-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a5712-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a5712-107">보안</span><span class="sxs-lookup"><span data-stu-id="a5712-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a5712-108">**다음을 사용하여 사용자 정의 함수의 이름을 바꾸려면**</span><span class="sxs-lookup"><span data-stu-id="a5712-108">**To rename user-defined functions, using:**</span></span>  
  
     [<span data-ttu-id="a5712-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a5712-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a5712-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a5712-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a5712-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a5712-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a5712-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a5712-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a5712-113">함수 이름은 [식별자](../databases/database-identifiers.md)에 대한 규칙을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-113">Function names must comply with the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
-   <span data-ttu-id="a5712-114">사용자 정의 함수의 이름을 변경해도 **sys.sql_modules** 카탈로그 뷰의 정의 열에 있는 해당 개체 이름은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-114">Renaming a user-defined function will not change the name of the corresponding object name in the definition column of the **sys.sql_modules** catalog view.</span></span> <span data-ttu-id="a5712-115">따라서 이 개체 유형의 이름을 바꾸지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-115">Therefore, we recommend that you do not rename this object type.</span></span> <span data-ttu-id="a5712-116">대신 저장 프로시저를 삭제하고 새로운 이름으로 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-116">Instead, drop and re-create the stored procedure with its new name.</span></span>  
  
-   <span data-ttu-id="a5712-117">사용자 정의 함수의 이름 또는 정의를 변경할 때 개체에 해당 함수의 변경 내용이 적용되도록 업데이트하지 않으면 종속 개체가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-117">Changing the name or definition of a user-defined function can cause dependent objects to fail when the objects are not updated to reflect the changes that have been made to the function.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a5712-118">보안</span><span class="sxs-lookup"><span data-stu-id="a5712-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a5712-119">권한</span><span class="sxs-lookup"><span data-stu-id="a5712-119">Permissions</span></span>  
 <span data-ttu-id="a5712-120">함수를 삭제하려면 해당 함수가 속한 스키마에 대한 ALTER 권한이나 해당 함수에 대한 CONTROL 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-120">To drop the function, requires either ALTER permission on the schema to which the function belongs or CONTROL permission on the function.</span></span> <span data-ttu-id="a5712-121">함수를 다시 만들려면 데이터베이스에 대한 CREATE FUNCTION 권한과 함수가 생성되는 스키마에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-121">To re-create the function, requires CREATE FUNCTION permission in the database and ALTER permission on the schema in which the function is being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a5712-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a5712-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-user-defined-functions"></a><span data-ttu-id="a5712-123">사용자 정의 함수의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="a5712-123">To rename user-defined functions</span></span>  
  
1.  <span data-ttu-id="a5712-124">**개체 탐색기**에서 이름을 바꿀 함수가 포함된 데이터베이스 옆의 더하기 기호를 클릭한 다음</span><span class="sxs-lookup"><span data-stu-id="a5712-124">In **Object Explorer**, click the plus sign next to the database that contains the function you wish to rename and then</span></span>  
  
2.  <span data-ttu-id="a5712-125">**프로그래밍 기능** 폴더 옆의 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-125">Click the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="a5712-126">이름을 바꿀 함수가 포함된 폴더 옆의 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-126">Click the plus sign next to the folder that contains the function you wish to rename:</span></span>  
  
    -   <span data-ttu-id="a5712-127">테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="a5712-127">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="a5712-128">스칼라 반환 함수</span><span class="sxs-lookup"><span data-stu-id="a5712-128">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="a5712-129">Aggregate 함수</span><span class="sxs-lookup"><span data-stu-id="a5712-129">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="a5712-130">이름을 바꿀 함수를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-130">Right-click the function you wish to rename and select **Rename**.</span></span>  
  
5.  <span data-ttu-id="a5712-131">함수의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-131">Enter the function's new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a5712-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a5712-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="a5712-133">**사용자 정의 함수의 이름을 바꾸려면**</span><span class="sxs-lookup"><span data-stu-id="a5712-133">**To rename user-defined functions**</span></span>  
  
 <span data-ttu-id="a5712-134">이 작업은 Transact-SQL 문을 사용하여 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-134">This task cannot be performed using Transact-SQL statements.</span></span> <span data-ttu-id="a5712-135">Transact-SQL을 사용하여 사용자 정의 함수의 이름을 바꾸려면 먼저 기존 함수를 삭제하고 새로운 이름을 사용하여 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-135">To rename a user-defined function using Transact-SQL, you must first delete the existing function and then re-create it with the new name.</span></span> <span data-ttu-id="a5712-136">함수의 이전 이름을 사용하는 모든 코드 및 애플리케이션이 이제 새 이름을 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5712-136">Ensure that all code and applications that used the function's old name now use the new name.</span></span>  
  
 <span data-ttu-id="a5712-137">자세한 내용은 [CREATE FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) 및 [DROP FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5712-137">For more information, see [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) and [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5712-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5712-138">See Also</span></span>  
 <span data-ttu-id="a5712-139">[sys.sql_expression_dependencies&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5712-139">[sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) </span></span>  
 [<span data-ttu-id="a5712-140">사용자 정의 함수 보기</span><span class="sxs-lookup"><span data-stu-id="a5712-140">View User-defined Functions</span></span>](user-defined-functions.md)  
  
  
