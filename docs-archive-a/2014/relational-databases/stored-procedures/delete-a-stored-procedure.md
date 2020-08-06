---
title: 저장 프로시저 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- removing stored procedures
- stored procedures [SQL Server], deleting
- deleting stored procedures
ms.assetid: 232dbf4d-392a-406f-af3a-579518cd8e46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 418e68d4bb7c6ba6632767a554aea72e85726840
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659865"
---
# <a name="delete-a-stored-procedure"></a><span data-ttu-id="3caf1-102">저장 프로시저 삭제</span><span class="sxs-lookup"><span data-stu-id="3caf1-102">Delete a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-delete-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a><span data-ttu-id="3caf1-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에 저장된 프로시저를 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-103">This topic describes how to delete a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="3caf1-104">**시작하기 전 주의 사항:**  [제한 사항](#Restrictions), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="3caf1-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="3caf1-105">**프로시저를 삭제하려면 다음을 사용합니다.**   [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="3caf1-105">**To delete a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3caf1-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3caf1-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3caf1-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="3caf1-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3caf1-108">프로시저를 삭제할 때 개체와 스크립트에 프로시저의 삭제가 적용되도록 업데이트하지 않으면 종속 개체와 스크립트가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-108">Deleting a procedure can cause dependent objects and scripts to fail when the objects and scripts are not updated to reflect the removal of the procedure.</span></span> <span data-ttu-id="3caf1-109">그러나 동일한 이름 및 매개 변수의 프로시저가 삭제된 프로시저를 대체하기 위해 생성된 경우 참조하는 다른 개체는 올바르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-109">However, if a new procedure of the same name and the same parameters is created to replace the one that was deleted, other objects that reference it will still process successfully.</span></span> <span data-ttu-id="3caf1-110">자세한 내용은 [저장 프로시저의 종속성 보기](view-the-dependencies-of-a-stored-procedure.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3caf1-110">For more information, see [View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3caf1-111">보안</span><span class="sxs-lookup"><span data-stu-id="3caf1-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3caf1-112">권한</span><span class="sxs-lookup"><span data-stu-id="3caf1-112">Permissions</span></span>  
 <span data-ttu-id="3caf1-113">프로시저가 속한 스키마에 대한 ALTER 권한 또는 프로시저에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-113">Requires ALTER permission on the schema to which the procedure belongs, or CONTROL permission on the procedure.</span></span>  
  
##  <a name="how-to-delete-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="3caf1-114">저장 프로시저를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="3caf1-114">How to Delete a Stored Procedure</span></span>  
 <span data-ttu-id="3caf1-115">다음 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-115">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="3caf1-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3caf1-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="3caf1-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3caf1-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3caf1-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="3caf1-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="3caf1-119">**개체 탐색기에서 프로시저를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="3caf1-119">**To delete a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="3caf1-120">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-120">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="3caf1-121">**데이터베이스**를 확장하고 해당 프로시저가 속한 데이터베이스를 확장한 다음 **프로그래밍 기능**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-121">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="3caf1-122">**저장 프로시저**를 확장하고 제거할 프로시저를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-122">Expand **Stored Procedures**, right-click the procedure to remove, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="3caf1-123">프로시저에 종속된 개체를 보려면 **종속성 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-123">To view objects that depend on the procedure, click **Show Dependencies**.</span></span>  
  
5.  <span data-ttu-id="3caf1-124">올바른 프로시저가 선택되었는지 확인하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-124">Confirm the correct procedure is selected, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="3caf1-125">모든 종속 개체와 스크립트에서 참조 프로시저를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-125">Remove references to the procedure from any dependent objects and scripts.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3caf1-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="3caf1-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="3caf1-127">**쿼리 편집기에서 프로시저를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="3caf1-127">**To delete a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="3caf1-128">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="3caf1-129">**데이터베이스**를 확장하고 프로시저가 속한 데이터베이스를 확장하거나 도구 모음의 사용 가능한 데이터베이스 목록에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-129">Expand **Databases**, expand the database in which the procedure belongs, or, from the tool bar, select the database from the list of available databases.</span></span>  
  
3.  <span data-ttu-id="3caf1-130">파일 메뉴에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-130">On the File menu, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="3caf1-131">현재 데이터베이스의 저장 프로시저 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-131">Obtain the name of stored procedure to remove in the current database.</span></span> <span data-ttu-id="3caf1-132">개체 탐색기에서 **프로그래밍 기능** 을 확장한 다음 **저장 프로시저**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-132">From Object Explorer, expand **Programmability** and then expand **Stored Procedures**.</span></span> <span data-ttu-id="3caf1-133">또는 쿼리 편집기에서 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-133">Alternatively, in the query editor, run the following statement.</span></span>  
  
    ```sql  
    SELECT name AS procedure_name   
        ,SCHEMA_NAME(schema_id) AS schema_name  
        ,type_desc  
        ,create_date  
        ,modify_date  
    FROM sys.procedures;  
    ```  
  
5.  <span data-ttu-id="3caf1-134">다음 예제를 쿼리 편집기에 복사하여 붙여 넣고 저장 프로시저 이름을 입력하여 현재 데이터베이스에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-134">Copy and paste the following example into the query editor and insert a stored procedure name to delete from the current database.</span></span>  
  
    ```sql  
    DROP PROCEDURE <stored procedure name>;  
    GO  
    ```  
  
6.  <span data-ttu-id="3caf1-135">모든 종속 개체와 스크립트에서 참조 프로시저를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf1-135">Remove references to the procedure from any dependent objects and scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3caf1-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3caf1-136">See Also</span></span>  
 <span data-ttu-id="3caf1-137">[저장 프로시저 만들기](create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3caf1-137">[Create a Stored Procedure](create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="3caf1-138">[저장 프로시저 수정](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3caf1-138">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="3caf1-139">[저장 프로시저 이름 바꾸기](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3caf1-139">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="3caf1-140">[저장 프로시저의 정의 보기](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3caf1-140">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="3caf1-141">[저장 프로시저의 종속성 보기](view-the-dependencies-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3caf1-141">[View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="3caf1-142">DROP PROCEDURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3caf1-142">DROP PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-procedure-transact-sql)  
  
  
