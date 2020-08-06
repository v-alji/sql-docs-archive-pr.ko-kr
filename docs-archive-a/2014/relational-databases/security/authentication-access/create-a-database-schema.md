---
title: 데이터베이스 스키마 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.schemas.general.f1
helpviewer_keywords:
- creating schemas with Management Studio
- CREATE SCHEMA [Management Studio]
- database schemas
- schemas [SQL Server], creating
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3ac0c00768db6501c7d786c35758c1a9d75a5a7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730388"
---
# <a name="create-a-database-schema"></a><span data-ttu-id="845d4-102">데이터베이스 스키마 만들기</span><span class="sxs-lookup"><span data-stu-id="845d4-102">Create a Database Schema</span></span>
  <span data-ttu-id="845d4-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 스키마를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-103">This topic describes how to create a schema in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="845d4-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="845d4-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="845d4-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="845d4-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="845d4-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="845d4-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="845d4-107">보안</span><span class="sxs-lookup"><span data-stu-id="845d4-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="845d4-108">**다음을 사용하여 스키마를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="845d4-108">**To create a schema, using:**</span></span>  
  
     [<span data-ttu-id="845d4-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="845d4-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="845d4-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="845d4-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="845d4-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="845d4-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="845d4-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="845d4-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="845d4-113">새 스키마는 데이터베이스 수준 보안 주체인 데이터베이스 사용자, 데이터베이스 역할 또는 애플리케이션 역할 중 하나가 소유합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-113">The new schema is owned by one of the following database-level principals: database user, database role, or application role.</span></span> <span data-ttu-id="845d4-114">스키마 내에서 만든 개체는 스키마 소유자가 소유하며 **sys.objects** 의 **principal_id**가 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-114">Objects created within a schema are owned by the owner of the schema, and have a NULL **principal_id** in **sys.objects**.</span></span> <span data-ttu-id="845d4-115">스키마 포함 개체의 소유권을 모든 데이터베이스 수준 보안 주체에게 이전할 수 있지만 스키마 소유자는 항상 스키마 내의 개체에 대한 CONTROL 권한을 갖고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-115">Ownership of schema-contained objects can be transferred to any database-level principal, but the schema owner always retains CONTROL permission on objects within the schema.</span></span>  
  
-   <span data-ttu-id="845d4-116">데이터베이스 개체를 만들 때 개체 소유자로 유효한 도메인 보안 주체(사용자 또는 그룹)를 지정하면 도메인 보안 주체는 데이터베이스에 스키마로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-116">When creating a database object, if you specify a valid domain principal (user or group) as the object owner, the domain principal will be added to the database as a schema.</span></span> <span data-ttu-id="845d4-117">새 스키마는 도메인 보안 주체가 소유하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-117">The new schema will be owned by that domain principal.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="845d4-118">보안</span><span class="sxs-lookup"><span data-stu-id="845d4-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="845d4-119">권한</span><span class="sxs-lookup"><span data-stu-id="845d4-119">Permissions</span></span>  
  
-   <span data-ttu-id="845d4-120">데이터베이스에 대한 CREATE SCHEMA 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-120">Requires CREATE SCHEMA permission on the database.</span></span>  
  
-   <span data-ttu-id="845d4-121">다른 사용자를 생성되는 스키마의 소유자로 지정하려면 호출자에게 해당 사용자에 대한 IMPERSONATE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-121">To specify another user as the owner of the schema being created, the caller must have IMPERSONATE permission on that user.</span></span> <span data-ttu-id="845d4-122">데이터베이스 역할을 소유자로 지정하는 경우 호출자에게 해당 역할의 멤버 자격이나 해당 역할에 대한 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-122">If a database role is specified as the owner, the caller must have one of the following: membership in the role or ALTER permission on the role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="845d4-123">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="845d4-123">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-schema"></a><span data-ttu-id="845d4-124">스키마를 만들려면</span><span class="sxs-lookup"><span data-stu-id="845d4-124">To create a schema</span></span>  
  
1.  <span data-ttu-id="845d4-125">개체 탐색기에서 **데이터베이스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-125">In Object Explorer, expand the **Databases** folder.</span></span>  
  
2.  <span data-ttu-id="845d4-126">새 데이터베이스 스키마를 만들 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-126">Expand the database in which to create the new database schema.</span></span>  
  
3.  <span data-ttu-id="845d4-127">**보안** 폴더를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **스키마**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-127">Right-click the **Security** folder, point to **New**, and select **Schema**.</span></span>  
  
4.  <span data-ttu-id="845d4-128">**스키마 - 신규** 대화 상자의 **일반** 페이지에서 **스키마 이름** 상자에 새 스키마의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-128">In the **Schema - New** dialog box, on the **General** page, enter a name for the new schema in the **Schema name** box.</span></span>  
  
5.  <span data-ttu-id="845d4-129">**스키마 소유자** 상자에 해당 스키마를 소유할 데이터베이스 사용자 또는 역할의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-129">In the **Schema owner** box, enter the name of a database user or role to own the schema.</span></span> <span data-ttu-id="845d4-130">또는 **검색** 을 클릭하여 **역할 및 사용자 검색** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-130">Alternately, click **Search** to open the **Search Roles and Users** dialog box.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="845d4-131">추가 옵션</span><span class="sxs-lookup"><span data-stu-id="845d4-131">Additional Options</span></span>  
 <span data-ttu-id="845d4-132">**스키마 - 신규** 대화 상자에는 또한 **사용 권한** 및 **확장 속성**의 두 가지 추가 페이지의 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-132">The **Schema- New** dialog box also offers options on two additional pages: **Permissions** and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="845d4-133">**사용 권한** 페이지에는 사용 가능한 모든 보안 개체와 이러한 보안 개체에서 로그인에 부여할 수 있는 권한이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-133">The **Permissions** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="845d4-134">**확장 속성** 페이지에서는 데이터베이스 사용자에 사용자 지정 속성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-134">The **Extended properties** page allows you to add custom properties to database users.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="845d4-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="845d4-135">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-schema"></a><span data-ttu-id="845d4-136">스키마를 만들려면</span><span class="sxs-lookup"><span data-stu-id="845d4-136">To create a schema</span></span>  
  
1.  <span data-ttu-id="845d4-137">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="845d4-138">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="845d4-139">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="845d4-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the schema Sprockets owned by Annik that contains table NineProngs.   
    -- The statement grants SELECT to Mandar and denies SELECT to Prasanna.  
  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
  
 <span data-ttu-id="845d4-140">자세한 내용은 [CREATE SCHEMA&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-schema-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="845d4-140">For more information, see [CREATE SCHEMA &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-schema-transact-sql).</span></span>  
  
  
