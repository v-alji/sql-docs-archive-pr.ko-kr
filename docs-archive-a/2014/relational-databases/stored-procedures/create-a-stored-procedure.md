---
title: 저장 프로시저 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- new stored procedures
- stored procedures [SQL Server], creating
- creating stored procedures
ms.assetid: 76e8a6ba-1381-4620-b356-4311e1331ca7
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6781840e6a6c84773f40a6cd0557ccb79b676eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659866"
---
# <a name="create-a-stored-procedure"></a><span data-ttu-id="46510-102">저장 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="46510-102">Create a Stored Procedure</span></span>
  <span data-ttu-id="46510-103">이 항목에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 및 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] CREATE PROCEDURE 문을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-103">This topic describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE PROCEDURE statement.</span></span>  
  
##  <a name="Top"></a>   
-   <span data-ttu-id="46510-104">**시작하기 전 주의 사항:**  [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="46510-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="46510-105">**저장 프로시저를 만들려면 다음을 사용합니다.**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="46510-105">**To create a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="46510-106">권한</span><span class="sxs-lookup"><span data-stu-id="46510-106">Permissions</span></span>  
 <span data-ttu-id="46510-107">데이터베이스의 CREATE PROCEDURE 권한과 프로시저를 만들 스키마에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-107">Requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created.</span></span>  
  
##  <a name="how-to-create-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="46510-108">저장 프로시저를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="46510-108">How to Create a Stored Procedure</span></span>  
 <span data-ttu-id="46510-109">다음 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46510-109">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="46510-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="46510-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="46510-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="46510-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="46510-112">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="46510-112">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="46510-113">**개체 탐색기에서 프로시저를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="46510-113">**To create a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="46510-114">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-114">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="46510-115">**데이터베이스**를 확장하고 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 확장한 다음 **프로그래밍 기능**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-115">Expand **Databases**, expand the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="46510-116">**저장 프로시저**를 마우스 오른쪽 단추로 클릭한 다음 **새 저장 프로시저**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-116">Right-click **Stored Procedures**, and then click **New Stored Procedure**.</span></span>  
  
4.  <span data-ttu-id="46510-117">**쿼리** 메뉴에서 **템플릿 매개 변수 값 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-117">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
5.  <span data-ttu-id="46510-118">**템플릿 매개 변수 값 지정** 대화 상자에 표시된 매개 변수에 대해 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-118">In the **Specify Values for Template Parameters** dialog box, enter the following values for the parameters shown.</span></span>  
  
    |<span data-ttu-id="46510-119">매개 변수</span><span class="sxs-lookup"><span data-stu-id="46510-119">Parameter</span></span>|<span data-ttu-id="46510-120">값</span><span class="sxs-lookup"><span data-stu-id="46510-120">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="46510-121">작성자</span><span class="sxs-lookup"><span data-stu-id="46510-121">Author</span></span>|<span data-ttu-id="46510-122">*Your name*</span><span class="sxs-lookup"><span data-stu-id="46510-122">*Your name*</span></span>|  
    |<span data-ttu-id="46510-123">만든 날짜</span><span class="sxs-lookup"><span data-stu-id="46510-123">Create Date</span></span>|<span data-ttu-id="46510-124">*Today's date*</span><span class="sxs-lookup"><span data-stu-id="46510-124">*Today's date*</span></span>|  
    |<span data-ttu-id="46510-125">Description</span><span class="sxs-lookup"><span data-stu-id="46510-125">Description</span></span>|<span data-ttu-id="46510-126">Returns employee data</span><span class="sxs-lookup"><span data-stu-id="46510-126">Returns employee data.</span></span>|  
    |<span data-ttu-id="46510-127">Procedure_name</span><span class="sxs-lookup"><span data-stu-id="46510-127">Procedure_name</span></span>|<span data-ttu-id="46510-128">HumanResources.uspGetEmployeesTest</span><span class="sxs-lookup"><span data-stu-id="46510-128">HumanResources.uspGetEmployeesTest</span></span>|  
    |@Param1|@LastName|  
    |@Datatype_For_Param1|<span data-ttu-id="46510-129">`nvarchar`(50)</span><span class="sxs-lookup"><span data-stu-id="46510-129">`nvarchar`(50)</span></span>|  
    |<span data-ttu-id="46510-130">Default_Value_For_Param1</span><span class="sxs-lookup"><span data-stu-id="46510-130">Default_Value_For_Param1</span></span>|<span data-ttu-id="46510-131">NULL</span><span class="sxs-lookup"><span data-stu-id="46510-131">NULL</span></span>|  
    |@Param2|@FirstName|  
    |@Datatype_For_Param2|<span data-ttu-id="46510-132">`nvarchar`(50)</span><span class="sxs-lookup"><span data-stu-id="46510-132">`nvarchar`(50)</span></span>|  
    |<span data-ttu-id="46510-133">Default_Value_For_Param2</span><span class="sxs-lookup"><span data-stu-id="46510-133">Default_Value_For_Param2</span></span>|<span data-ttu-id="46510-134">NULL</span><span class="sxs-lookup"><span data-stu-id="46510-134">NULL</span></span>|  
  
6.  <span data-ttu-id="46510-135">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-135">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="46510-136">**쿼리 편집기**에서 SELECT 문을 다음 문으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="46510-136">In the **Query Editor**, replace the SELECT statement with the following statement:</span></span>  
  
    ```sql  
    SELECT FirstName, LastName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory  
    WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    ```  
  
8.  <span data-ttu-id="46510-137">구문을 테스트하려면 **쿼리** 메뉴에서 **구문 분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-137">To test the syntax, on the **Query** menu, click **Parse**.</span></span> <span data-ttu-id="46510-138">오류 메시지가 반환되면 필요에 따라 위의 정보와 문을 비교하여 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-138">If an error message is returned, compare the statements with the information above and correct as needed.</span></span>  
  
9. <span data-ttu-id="46510-139">프로시저를 만들려면 **쿼리** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-139">To create the procedure, from  the **Query** menu, click **Execute**.</span></span> <span data-ttu-id="46510-140">프로시저가 데이터베이스 개체로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="46510-140">The procedure is created as an object in the database.</span></span>  
  
10. <span data-ttu-id="46510-141">개체 탐색기에 나열된 프로시저를 보려면 **저장 프로시저** 를 마우스 오른쪽 단추로 클릭하고 **새로 고침**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-141">To see the procedure listed in Object Explorer, right-click **Stored Procedures** and select **Refresh**.</span></span>  
  
11. <span data-ttu-id="46510-142">프로시저를 실행하려면 개체 탐색기에서 저장 프로시저 이름 **HumanResources.uspGetEmployeesTest** 를 마우스 오른쪽 단추로 클릭하고 **저장 프로시저 실행**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-142">To run the procedure, in Object Explorer, right-click the stored procedure name **HumanResources.uspGetEmployeesTest** and select **Execute Stored Procedure**.</span></span>  
  
12. <span data-ttu-id="46510-143">**프로시저 실행** 창에서 @LastName 매개 변수의 값으로 Margheim을 입력하고 @FirstName 매개 변수의 값으로 Diane을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-143">In the **Execute Procedure** window, enter Margheim as the value for the parameter @LastName and enter the value Diane as the value for the parameter @FirstName.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="46510-144">모든 사용자 입력에 대해 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-144">Validate all user input.</span></span> <span data-ttu-id="46510-145">유효성 검사를 수행하기 전에는 사용자 입력을 연결하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="46510-145">Do not concatenate user input before you validate it.</span></span> <span data-ttu-id="46510-146">유효성 검사가 수행되지 않은 사용자 입력으로부터 생성된 명령은 실행하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="46510-146">Never execute a command constructed from unvalidated user input.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="46510-147">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="46510-147">Using Transact-SQL</span></span>  
 <span data-ttu-id="46510-148">**쿼리 편집기에서 프로시저를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="46510-148">**To create a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="46510-149">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-149">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="46510-150">메뉴에서 **파일** 메뉴에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-150">From the **File** menu, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="46510-151">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-151">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="46510-152">이 예에서는 다른 프로시저 이름을 사용하여 위와 같은 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46510-152">This example creates the same stored procedure as above using a different procedure name.</span></span>  
  
    ```sql
    USE AdventureWorks2012;  
    GO  
    CREATE PROCEDURE HumanResources.uspGetEmployeesTest2   
        @LastName nvarchar(50),   
        @FirstName nvarchar(50)   
    AS
  
        SET NOCOUNT ON;  
        SELECT FirstName, LastName, Department  
        FROM HumanResources.vEmployeeDepartmentHistory  
        WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    GO
    ```  
  
4.  <span data-ttu-id="46510-153">프로시저를 실행하려면 다음 예제를 새 쿼리 창에 복사하여 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46510-153">To run the procedure, copy and paste the following example into a new query window and click **Execute**.</span></span> <span data-ttu-id="46510-154">매개 변수 값을 지정하는 다른 메서드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="46510-154">Notice that different methods of specifying the parameter values are shown.</span></span>  
  
    ```sql
    EXECUTE HumanResources.uspGetEmployeesTest2 N'Ackerman', N'Pilar';  
    -- Or  
    EXEC HumanResources.uspGetEmployeesTest2 @LastName = N'Ackerman', @FirstName = N'Pilar';  
    GO  
    -- Or  
    EXECUTE HumanResources.uspGetEmployeesTest2 @FirstName = N'Pilar', @LastName = N'Ackerman';  
    GO
    ```  
  
## <a name="see-also"></a><span data-ttu-id="46510-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46510-155">See Also</span></span>  
 [<span data-ttu-id="46510-156">CREATE PROCEDURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="46510-156">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  