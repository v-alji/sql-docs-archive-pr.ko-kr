---
title: DML 트리거 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], DML triggers
- deferred name resolution, DML triggers
- WITH ENCRYPTION clause
- IF UPDATE
- SET statement, DML triggers
- DML triggers, programming
- testing column changes
- results [SQL Server], DML triggers
ms.assetid: b2b52258-642b-462e-8e0f-18c09d2eccf4
author: rothja
ms.author: jroth
ms.openlocfilehash: f843513ba634bcb3479e373eb9ac978ab584588d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660403"
---
# <a name="create-dml-triggers"></a><span data-ttu-id="33060-102">DML 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="33060-102">Create DML Triggers</span></span>
  <span data-ttu-id="33060-103">이 항목에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 및 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] CREATE TRIGGER 문을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] DML 트리거를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-103">This topic describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] DML trigger by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER statement.</span></span>  
  
##  <a name="before-you-begin"></a><a name="Top"></a> <span data-ttu-id="33060-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="33060-104">Before You Begin</span></span>  
  
### <a name="limitations-and-restrictions"></a><span data-ttu-id="33060-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="33060-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="33060-106">DML 트리거 생성과 관련한 제한 사항 목록은 [CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="33060-106">For a list of limitations and restrictions related to creating DML triggers, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="33060-107">권한</span><span class="sxs-lookup"><span data-stu-id="33060-107">Permissions</span></span>  
 <span data-ttu-id="33060-108">트리거를 생성할 테이블 또는 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-108">Requires ALTER permission on the table or view on which the trigger is being created.</span></span>  
  
##  <a name="how-to-create-a-dml-trigger"></a><a name="Procedures"></a> <span data-ttu-id="33060-109">DML 트리거를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="33060-109">How to Create a DML Trigger</span></span>  
 <span data-ttu-id="33060-110">다음 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33060-110">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="33060-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="33060-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="33060-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="33060-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="33060-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="33060-113">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="33060-114">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-114">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="33060-115">**데이터베이스**, [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스, **테이블** 및 **Purchasing.PurchaseOrderHeader**테이블을 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-115">Expand **Databases**, expand the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, expand **Tables** and then expand the table **Purchasing.PurchaseOrderHeader**.</span></span>  
  
3.  <span data-ttu-id="33060-116">**트리거**를 마우스 오른쪽 단추로 클릭한 다음 **새 트리거**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-116">Right-click **Triggers**, and then select **New Trigger**.</span></span>  
  
4.  <span data-ttu-id="33060-117">**쿼리** 메뉴에서 **템플릿 매개 변수 값 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-117">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span> <span data-ttu-id="33060-118">또는 (Ctrl-Shift-M)을 눌러 **템플릿 매개 변수 값 지정** 대화 상자를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33060-118">Alternatively, you can press (Ctrl-Shift-M) to open the **Specify Values for Template Parameters** dialog box.</span></span>  
  
5.  <span data-ttu-id="33060-119">**템플릿 매개 변수 값 지정** 대화 상자에 표시된 매개 변수에 대해 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-119">In the **Specify Values for Template Parameters** dialog box, enter the following values for the parameters shown.</span></span>  
  
    |<span data-ttu-id="33060-120">매개 변수</span><span class="sxs-lookup"><span data-stu-id="33060-120">Parameter</span></span>|<span data-ttu-id="33060-121">값</span><span class="sxs-lookup"><span data-stu-id="33060-121">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="33060-122">작성자</span><span class="sxs-lookup"><span data-stu-id="33060-122">Author</span></span>|<span data-ttu-id="33060-123">*Your name*</span><span class="sxs-lookup"><span data-stu-id="33060-123">*Your name*</span></span>|  
    |<span data-ttu-id="33060-124">만든 날짜</span><span class="sxs-lookup"><span data-stu-id="33060-124">Create Date</span></span>|<span data-ttu-id="33060-125">*Today's date*</span><span class="sxs-lookup"><span data-stu-id="33060-125">*Today's date*</span></span>|  
    |<span data-ttu-id="33060-126">Description</span><span class="sxs-lookup"><span data-stu-id="33060-126">Description</span></span>|<span data-ttu-id="33060-127">공급업체의 새 PO를 삽입하기 전에 공급업체의 신용 등급을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-127">Checks the vendor credit rating before allowing a new purchase order with the vendor to be inserted.</span></span>|  
    |<span data-ttu-id="33060-128">Schema_Name</span><span class="sxs-lookup"><span data-stu-id="33060-128">Schema_Name</span></span>|<span data-ttu-id="33060-129">구매</span><span class="sxs-lookup"><span data-stu-id="33060-129">Purchasing</span></span>|  
    |<span data-ttu-id="33060-130">Trigger_Name</span><span class="sxs-lookup"><span data-stu-id="33060-130">Trigger_Name</span></span>|<span data-ttu-id="33060-131">NewPODetail2</span><span class="sxs-lookup"><span data-stu-id="33060-131">NewPODetail2</span></span>|  
    |<span data-ttu-id="33060-132">Table_Name</span><span class="sxs-lookup"><span data-stu-id="33060-132">Table_Name</span></span>|<span data-ttu-id="33060-133">PurchaseOrderDetail</span><span class="sxs-lookup"><span data-stu-id="33060-133">PurchaseOrderDetail</span></span>|  
    |<span data-ttu-id="33060-134">Data_Modification_Statement</span><span class="sxs-lookup"><span data-stu-id="33060-134">Data_Modification_Statement</span></span>|<span data-ttu-id="33060-135">목록에서 UPDATE 및 DELETE를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-135">Remove UPDATE and DELETE from the list.</span></span>|  
  
6.  <span data-ttu-id="33060-136">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-136">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="33060-137">**쿼리 편집기**에서 `-- Insert statements for trigger here` 주석을 다음 문으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="33060-137">In the **Query Editor**, replace the comment `-- Insert statements for trigger here` with the following statement:</span></span>  
  
    ```sql  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
  
8.  <span data-ttu-id="33060-138">구문이 올바른지 확인하려면 **쿼리** 메뉴에서 **구문 분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-138">To verify the syntax is valid, on the **Query** menu, click **Parse**.</span></span> <span data-ttu-id="33060-139">오류 메시지가 반환되면 필요에 따라 위의 정보와 문을 비교하여 수정하고 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-139">If an error message is returned, compare the statement with the information above and correct as needed and repeat this step.</span></span>  
  
9. <span data-ttu-id="33060-140">DML 트리거를 만들려면 **쿼리** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-140">To create the DML trigger, from the **Query** menu, click **Execute**.</span></span> <span data-ttu-id="33060-141">DML 트리거가 데이터베이스 개체로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="33060-141">The DML trigger is created as an object in the database.</span></span>  
  
10. <span data-ttu-id="33060-142">개체 탐색기에 나열된 DML 트리거를 보려면 **트리거** 를 마우스 오른쪽 단추로 클릭하고 **새로 고침**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-142">To see the DML trigger listed in Object Explorer, right-click **Triggers** and select **Refresh**.</span></span>  
  
 [<span data-ttu-id="33060-143">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="33060-143">Before You Begin</span></span>](#Top)  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="33060-144">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="33060-144">Using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="33060-145">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="33060-146">메뉴에서 **파일** 메뉴에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-146">From the **File** menu, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="33060-147">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33060-147">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="33060-148">이 예에서는 위와 동일한 저장된 DML 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="33060-148">This example creates the same stored DML trigger as above.</span></span>  
  
    ```sql
    -- Trigger valid for multirow and single row inserts  
    -- and optimal for single row inserts.  
    USE AdventureWorks2012;  
    GO  
    CREATE TRIGGER NewPODetail3  
    ON Purchasing.PurchaseOrderDetail  
    FOR INSERT AS  
    IF @@ROWCOUNT = 1  
    BEGIN  
       UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal + LineTotal  
       FROM inserted  
       WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
  
    END  
    ELSE  
    BEGIN  
          UPDATE Purchasing.PurchaseOrderHeader  
       SET SubTotal = SubTotal +   
          (SELECT SUM(LineTotal)  
          FROM inserted  
          WHERE PurchaseOrderHeader.PurchaseOrderID  
           = inserted.PurchaseOrderID)  
       WHERE PurchaseOrderHeader.PurchaseOrderID IN  
          (SELECT PurchaseOrderID FROM inserted)  
    END;  
    ```  
