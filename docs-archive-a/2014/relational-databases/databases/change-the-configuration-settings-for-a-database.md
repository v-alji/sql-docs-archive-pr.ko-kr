---
title: 데이터베이스 메일의 구성 설정 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database configuration [SQL Server]
- configuration options [SQL Server], databases
- modifying database configuration settings
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f9edecefae5154bb66a65e38724d9e77a94fdbb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742231"
---
# <a name="change-the-configuration-settings-for-a-database"></a><span data-ttu-id="6dde8-102">데이터베이스 메일의 구성 설정 변경</span><span class="sxs-lookup"><span data-stu-id="6dde8-102">Change the Configuration Settings for a Database</span></span>
  <span data-ttu-id="6dde8-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터베이스 수준 옵션을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-103">This topic describes how to change database-level options in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6dde8-104">데이터베이스 수준의 옵션은 각 데이터베이스의 고유한 옵션이므로 다른 데이터베이스에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-104">These options are unique to each database and do not affect other databases.</span></span>  
  
 <span data-ttu-id="6dde8-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="6dde8-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6dde8-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="6dde8-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6dde8-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="6dde8-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6dde8-108">보안</span><span class="sxs-lookup"><span data-stu-id="6dde8-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6dde8-109">**다음을 사용하여 데이터베이스의 옵션 설정을 변경합니다.**</span><span class="sxs-lookup"><span data-stu-id="6dde8-109">**To change the option settings for a database, using:**</span></span>  
  
     [<span data-ttu-id="6dde8-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6dde8-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6dde8-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6dde8-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6dde8-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6dde8-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6dde8-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="6dde8-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6dde8-114">시스템 관리자, 데이터베이스 소유자, **sysadmin** 및 **dbcreator** 고정 서버 역할과 **db_owner** 고정 데이터베이스 역할의 멤버만 이 옵션을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-114">Only the system administrator, database owner, members of the **sysadmin** and **dbcreator** fixed server roles and **db_owner** fixed database roles can modify these options.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6dde8-115">보안</span><span class="sxs-lookup"><span data-stu-id="6dde8-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6dde8-116">권한</span><span class="sxs-lookup"><span data-stu-id="6dde8-116">Permissions</span></span>  
 <span data-ttu-id="6dde8-117">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6dde8-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6dde8-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-option-settings-for-a-database"></a><span data-ttu-id="6dde8-119">데이터베이스의 옵션 설정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="6dde8-119">To change the option settings for a database</span></span>  
  
1.  <span data-ttu-id="6dde8-120">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결하고 서버와 **데이터베이스**를 차례로 확장한 다음 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-120">In Object Explorer, connect to a [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, expand the server, expand **Databases**, right-click a database, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6dde8-121">**데이터베이스 속성** 대화 상자에서 **옵션** 을 클릭하면 대부분의 구성 설정에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-121">In the **Database Properties** dialog box, click **Options** to access most of the configuration settings.</span></span> <span data-ttu-id="6dde8-122">파일 및 파일 그룹 구성, 미러링 및 로그 전달은 해당 페이지에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-122">File and filegroup configurations, mirroring and log shipping are on their respective pages.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6dde8-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="6dde8-123">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-option-settings-for-a-database"></a><span data-ttu-id="6dde8-124">데이터베이스의 옵션 설정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="6dde8-124">To change the option settings for a database</span></span>  
  
1.  <span data-ttu-id="6dde8-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6dde8-126">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6dde8-127">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-127">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6dde8-128">이 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스에 대해 복구 모델 및 데이터 페이지 확인 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6dde8-128">This example sets the recovery model and data page verification options for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase7)]  
  
 <span data-ttu-id="6dde8-129">더 많은 예제를 보려면 [ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6dde8-129">For more examples, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dde8-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6dde8-130">See Also</span></span>  
 <span data-ttu-id="6dde8-131">[ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span><span class="sxs-lookup"><span data-stu-id="6dde8-131">[ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span></span>  
 <span data-ttu-id="6dde8-132">[ALTER DATABASE 데이터베이스 미러링&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="6dde8-132">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="6dde8-133">[ALTER DATABASE SET HADR&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span><span class="sxs-lookup"><span data-stu-id="6dde8-133">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span></span>  
 <span data-ttu-id="6dde8-134">[데이터베이스 이름 바꾸기](rename-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="6dde8-134">[Rename a Database](rename-a-database.md) </span></span>  
 [<span data-ttu-id="6dde8-135">데이터베이스 축소</span><span class="sxs-lookup"><span data-stu-id="6dde8-135">Shrink a Database</span></span>](shrink-a-database.md)  
  
  
