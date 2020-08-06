---
title: 단일 사용자 모드로 데이터베이스 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], database option
ms.assetid: fb5254eb-b635-4b39-8361-136fd36f2b1f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 16281b5fa7d4f6698bb6c498915bfa84779b3e14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728335"
---
# <a name="set-a-database-to-single-user-mode"></a><span data-ttu-id="4be51-102">단일 사용자 모드로 데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="4be51-102">Set a Database to Single-user Mode</span></span>
  <span data-ttu-id="4be51-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 사용자 정의 데이터베이스를 단일 사용자 모드로 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-103">This topic describes how to set a user-defined database to single-user mode in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4be51-104">단일 사용자 모드는 한 번에 하나의 사용자만 데이터베이스에 액세스할 수 있도록 지정하며 일반적으로 유지 관리 동작에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-104">Single-user mode specifies that only one user at a time can access the database and is generally used for maintenance actions.</span></span>  
  
 <span data-ttu-id="4be51-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="4be51-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4be51-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="4be51-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4be51-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4be51-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4be51-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4be51-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="4be51-109">보안</span><span class="sxs-lookup"><span data-stu-id="4be51-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4be51-110">**데이터베이스를 단일 사용자 모드로 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="4be51-110">**To set a database to single-user mode, using:**</span></span>  
  
     [<span data-ttu-id="4be51-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4be51-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4be51-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4be51-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4be51-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="4be51-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4be51-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4be51-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4be51-115">데이터베이스를 단일 사용자 모드로 설정할 때 다른 사용자가 데이터베이스에 연결되어 있으면 해당 데이터베이스 연결이 경고 없이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-115">If other users are connected to the database at the time that you set the database to single-user mode, their connections to the database will be closed without warning.</span></span>  
  
-   <span data-ttu-id="4be51-116">옵션을 설정한 사용자가 로그오프해도 데이터베이스는 단일 사용자 모드로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-116">The database remains in single-user mode even if the user that set the option logs off.</span></span> <span data-ttu-id="4be51-117">이때 다른 한 명의 사용자만 데이터베이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-117">At that point, a different user, but only one, can connect to the database.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="4be51-118">필수 조건</span><span class="sxs-lookup"><span data-stu-id="4be51-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="4be51-119">데이터베이스를 SINGLE_USER로 설정하기 전에 AUTO_UPDATE_STATISTICS_ASYNC 옵션이 OFF로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-119">Before you set the database to SINGLE_USER, verify that the AUTO_UPDATE_STATISTICS_ASYNC option is set to OFF.</span></span> <span data-ttu-id="4be51-120">이 옵션이 ON으로 설정되면 통계 업데이트에 사용되는 백그라운드 스레드가 데이터베이스에 대한 연결을 점유하므로 사용자는 단일 사용자 모드로 데이터베이스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-120">When this option is set to ON, the background thread that is used to update statistics takes a connection against the database, and you will be unable to access the database in single-user mode.</span></span> <span data-ttu-id="4be51-121">자세한 내용은 [ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4be51-121">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4be51-122">보안</span><span class="sxs-lookup"><span data-stu-id="4be51-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4be51-123">권한</span><span class="sxs-lookup"><span data-stu-id="4be51-123">Permissions</span></span>  
 <span data-ttu-id="4be51-124">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-124">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4be51-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="4be51-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-a-database-to-single-user-mode"></a><span data-ttu-id="4be51-126">데이터베이스를 단일 사용자 모드로 설정하려면</span><span class="sxs-lookup"><span data-stu-id="4be51-126">To set a database to single-user mode</span></span>  
  
1.  <span data-ttu-id="4be51-127">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-127">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="4be51-128">변경할 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-128">Right-click the database to change, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="4be51-129">**데이터베이스 속성** 대화 상자에서 **옵션** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-129">In the **Database Properties** dialog box, click the **Options** page.</span></span>  
  
4.  <span data-ttu-id="4be51-130">**액세스 제한** 옵션에서 **단일**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-130">From the **Restrict Access** option, select **Single**.</span></span>  
  
5.  <span data-ttu-id="4be51-131">다른 사용자가 데이터베이스에 연결되어 있으면 **열린 연결** 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-131">If other users are connected to the database, an **Open Connections** message will appear.</span></span> <span data-ttu-id="4be51-132">다른 모든 연결을 닫고 속성을 변경하려면 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-132">To change the property and close all other connections, click **Yes**.</span></span>  
  
 <span data-ttu-id="4be51-133">이 절차에 따라 데이터베이스를 다중 또는 제한됨 액세스로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-133">You can also set the database to Multiple or Restricted access by using this procedure.</span></span> <span data-ttu-id="4be51-134">액세스 제한 옵션에 대한 자세한 내용은 [데이터베이스 속성&#40;옵션 페이지&#41;](database-properties-options-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4be51-134">For more information about the Restrict Access options, see [Database Properties &#40;Options Page&#41;](database-properties-options-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4be51-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="4be51-135">Using Transact-SQL</span></span>  
  
#### <a name="to-set-a-database-to-single-user-mode"></a><span data-ttu-id="4be51-136">데이터베이스를 단일 사용자 모드로 설정하려면</span><span class="sxs-lookup"><span data-stu-id="4be51-136">To set a database to single-user mode</span></span>  
  
1.  <span data-ttu-id="4be51-137">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-137">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4be51-138">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4be51-139">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4be51-140">이 예에서는 데이터베이스를 `SINGLE_USER` 모드로 설정하여 배타적 액세스 권한을 확보한 다음</span><span class="sxs-lookup"><span data-stu-id="4be51-140">This example sets the database to `SINGLE_USER` mode to obtain exclusive access.</span></span> <span data-ttu-id="4be51-141">[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 데이터베이스의 상태를 `READ_ONLY` 로 설정한 후 데이터베이스 액세스를 모든 사용자에게 반환합니다. 종료 옵션 `WITH ROLLBACK IMMEDIATE` 는 첫 번째 `ALTER DATABASE` 문에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-141">The example then sets the state of the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to `READ_ONLY` and returns access to the database to all users.The termination option `WITH ROLLBACK IMMEDIATE` is specified in the first `ALTER DATABASE` statement.</span></span> <span data-ttu-id="4be51-142">완료되지 않은 트랜잭션은 모두 롤백되며 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 데이터베이스로의 다른 모든 연결은 즉시 끊어집니다.</span><span class="sxs-lookup"><span data-stu-id="4be51-142">This will cause all incomplete transactions to be rolled back and any other connections to the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to be immediately disconnected.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase8](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase8)]  
  
## <a name="see-also"></a><span data-ttu-id="4be51-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4be51-143">See Also</span></span>  
 [<span data-ttu-id="4be51-144">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4be51-144">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
