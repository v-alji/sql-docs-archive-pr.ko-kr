---
title: 테이블 만들기(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table creation [SQL Server], Visual Database Tools
ms.assetid: 6f7c6ac5-e6d3-4dca-831e-b28442ba535b
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8d84a4da6a10fbcbae311fe1bf738c03b85a4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661597"
---
# <a name="create-tables-database-engine"></a><span data-ttu-id="3b282-102">테이블 만들기(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="3b282-102">Create Tables (Database Engine)</span></span>
  <span data-ttu-id="3b282-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 새 테이블을 만들고, 테이블 이름을 지정하고, 이 테이블을 기존 데이터베이스에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-103">You can create a new table, name it, and add it to an existing database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>

> [!NOTE]
>  <span data-ttu-id="3b282-104">SQL Azure 데이터베이스에 연결되어 있는 경우 새 테이블 옵션을 사용하면 테이블 만들기 템플릿 스크립트가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-104">If you are connected to a SQL Azure database, the new table option launches a create table template script.</span></span> <span data-ttu-id="3b282-105">매개 변수를 편집한 다음 스크립트를 실행하여 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-105">Edit the parameters, then run the script to create a new table.</span></span> <span data-ttu-id="3b282-106">자세한 내용은 [SQL Azure 개요(SQL Azure Overview)](https://microsoft.sharepoint.com/sites/infopedia_g01/pages/cards/azure-sql-database.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b282-106">For more information, see [SQL Azure Overview](https://microsoft.sharepoint.com/sites/infopedia_g01/pages/cards/azure-sql-database.aspx).</span></span>

 <span data-ttu-id="3b282-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="3b282-107">**In This Topic**</span></span>

-   <span data-ttu-id="3b282-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="3b282-108">**Before you begin:**</span></span>

     [<span data-ttu-id="3b282-109">보안</span><span class="sxs-lookup"><span data-stu-id="3b282-109">Security</span></span>](#Security)

-   <span data-ttu-id="3b282-110">**테이블을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="3b282-110">**To create a table, using:**</span></span>

     [<span data-ttu-id="3b282-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3b282-111">SQL Server Management Studio</span></span>](#SSMSProcedure)

     [<span data-ttu-id="3b282-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3b282-112">Transact-SQL</span></span>](#TsqlProcedure)

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3b282-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3b282-113">Before You Begin</span></span>

###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3b282-114">보안</span><span class="sxs-lookup"><span data-stu-id="3b282-114">Security</span></span>

####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3b282-115">권한</span><span class="sxs-lookup"><span data-stu-id="3b282-115">Permissions</span></span>
 <span data-ttu-id="3b282-116">데이터베이스에는 CREATE TABLE 권한이 필요하고 테이블을 만들 구성표에는 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-116">Requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>

 <span data-ttu-id="3b282-117">CREATE TABLE 문에 있는 열을 CLR 사용자 정의 형식으로 정의하는 경우 해당 유형의 소유권이나 이에 대한 REFERENCES 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-117">If any columns in the CREATE TABLE statement are defined as a CLR user-defined type, either ownership of the type or REFERENCES permission on it is required.</span></span>

 <span data-ttu-id="3b282-118">CREATE TABLE 문의 열에 연관된 XML 스키마 컬렉션이 있는 경우 XML 스키마 컬렉션의 소유권이나 이에 대한 REFERENCES 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-118">If any columns in the CREATE TABLE statement have an XML schema collection associated with them, either ownership of the XML schema collection or REFERENCES permission on it is required.</span></span>

##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3b282-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="3b282-119">Using SQL Server Management Studio</span></span>

#### <a name="to-create-a-table-with-table-designer"></a><span data-ttu-id="3b282-120">테이블 디자이너로 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3b282-120">To create a table with Table Designer</span></span>

1.  <span data-ttu-id="3b282-121">**개체 탐색기**에서 수정할 데이터베이스를 포함하는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-121">In **Object Explorer**, connect to the instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] that contains the database to be modified.</span></span>

2.  <span data-ttu-id="3b282-122">**개체 탐색기**에서 **데이터베이스** 노드를 확장한 후 새 테이블을 포함할 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-122">In **Object Explorer**, expand the **Databases** node and then expand the database that will contain the new table.</span></span>

3.  <span data-ttu-id="3b282-123">개체 탐색기에서 데이터베이스의 **테이블** 노드를 마우스 오른쪽 단추로 클릭한 다음 **새 테이블**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-123">In Object Explorer, right-click the **Tables** node of your database and then click **New Table**.</span></span>

4.  <span data-ttu-id="3b282-124">다음 그림과 같이 각 열에 대해 열 이름을 입력하고, 데이터 형식을 선택하고, null 허용 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-124">Type column names, choose data types, and choose whether to allow nulls for each column as shown in the following illustration.</span></span>

     <span data-ttu-id="3b282-125">![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")</span><span class="sxs-lookup"><span data-stu-id="3b282-125">![AddColumnsinTableDesigner](../../database-engine/media/addcolumnsintabledesigner.gif "AddColumnsinTableDesigner")</span></span>

5.  <span data-ttu-id="3b282-126">ID 또는 계산 열 값 등 열의 더 많은 속성을 지정하려면 열을 클릭하고 열 속성 탭에서 적절한 속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-126">To specify more properties for a column, such as identity or computed column values, click the column and in the column properties tab, choose the appropriate properties.</span></span> <span data-ttu-id="3b282-127">열 속성에 대한 자세한 내용은 [테이블 열 속성&#40;SQL Server Management Studio&#41;](table-column-properties-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b282-127">For more information about column properties, see [Table Column Properties &#40;SQL Server Management Studio&#41;](table-column-properties-sql-server-management-studio.md).</span></span>

6.  <span data-ttu-id="3b282-128">열을 기본 키로 지정하려면 열을 마우스 오른쪽 단추로 클릭하고 **기본 키 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-128">To specify a column as a primary key, right-click the column and select **Set Primary Key**.</span></span> <span data-ttu-id="3b282-129">자세한 내용은 [Create Primary Keys](../tables/create-primary-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b282-129">For more information, see [Create Primary Keys](../tables/create-primary-keys.md).</span></span>

7.  <span data-ttu-id="3b282-130">외래 키 관계를 만들려면 제약 조건 또는 인덱스를 확인하고 테이블 디자이너 창에서 마우스 오른쪽 단추로 클릭하고 다음 그림과 같이 목록에서 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-130">To create foreign key relationships, check constraints, or indexes, right-click in the Table Designer pane and select an object from the list as shown in the following illustration.</span></span>

     <span data-ttu-id="3b282-131">![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")</span><span class="sxs-lookup"><span data-stu-id="3b282-131">![AddTableObjects](../../database-engine/media/addtableobjects.gif "AddTableObjects")</span></span>

     <span data-ttu-id="3b282-132">이러한 개체에 대한 자세한 내용은 [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md), [Create Check Constraints](../tables/create-check-constraints.md) 및 [Indexes](../indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b282-132">For more information about these objects, see [Create Foreign Key Relationships](../tables/create-foreign-key-relationships.md), [Create Check Constraints](../tables/create-check-constraints.md) and [Indexes](../indexes/indexes.md).</span></span>

8.  <span data-ttu-id="3b282-133">기본적으로 테이블은 **dbo** 스키마에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-133">By default, the table is contained in the **dbo** schema.</span></span> <span data-ttu-id="3b282-134">테이블에 다른 스키마를 지정하려면 다음 그림과 같이 테이블 디자이너 창에서 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-134">To specify a different schema for the table, right-click in the Table Designer pane and select **Properties** as shown in the following illustration.</span></span> <span data-ttu-id="3b282-135">**스키마** 드롭다운 목록에서 적절한 스키마를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-135">From the **Schema** drop-down list, select the appropriate schema.</span></span>

     <span data-ttu-id="3b282-136">![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")</span><span class="sxs-lookup"><span data-stu-id="3b282-136">![Specifyatableschema](../../database-engine/media/specifyatableschema.gif "Specifyatableschema")</span></span>

     <span data-ttu-id="3b282-137">스키마에 대한 자세한 내용은 [Create a Database Schema](../security/authentication-access/create-a-database-schema.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b282-137">For more information about schemas, see [Create a Database Schema](../security/authentication-access/create-a-database-schema.md).</span></span>

9. <span data-ttu-id="3b282-138">**파일** 메뉴에서 ‘테이블 이름’ **저장을 선택합니다.** \*\*</span><span class="sxs-lookup"><span data-stu-id="3b282-138">From the **File** menu, choose **Save** *table name*.</span></span>

10. <span data-ttu-id="3b282-139">**이름 선택** 대화 상자에서 테이블의 이름을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-139">In the **Choose Name** dialog box, type a name for the table and click **OK**.</span></span>

11. <span data-ttu-id="3b282-140">새 테이블을 보려면 **개체 탐색기**에서 **테이블** 노드를 확장하고 **F5** 를 눌러 개체 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-140">To view the new table, in **Object Explorer**, expand the **Tables** node and press **F5** to refresh the list of objects.</span></span> <span data-ttu-id="3b282-141">테이블 목록에 새 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-141">The new table is displayed in the list of tables.</span></span>

##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3b282-142">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="3b282-142">Using Transact-SQL</span></span>

#### <a name="to-create-a-table-in-the-query-editor"></a><span data-ttu-id="3b282-143">쿼리 편집기에서 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3b282-143">To create a table in the Query Editor</span></span>

1.  <span data-ttu-id="3b282-144">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-144">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>

2.  <span data-ttu-id="3b282-145">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-145">On the Standard bar, click **New Query**.</span></span>

3.  <span data-ttu-id="3b282-146">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b282-146">Copy and paste the following example into the query window and click **Execute**.</span></span>

    ```
    CREATE TABLE dbo.PurchaseOrderDetail
    (
        PurchaseOrderID int NOT NULL
        ,LineNumber smallint NOT NULL
        ,ProductID int NULL
        ,UnitPrice money NULL
        ,OrderQty smallint NULL
        ,ReceivedQty float NULL
        ,RejectedQty float NULL
        ,DueDate datetime NULL
    );
    ```

 <span data-ttu-id="3b282-147">더 많은 예제를 보려면 [CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b282-147">For more examples, see [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span>


