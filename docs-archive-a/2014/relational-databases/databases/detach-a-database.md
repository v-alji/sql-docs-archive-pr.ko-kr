---
title: 데이터베이스 분리 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.detachdatabase.f1
helpviewer_keywords:
- database detaching [SQL Server]
- detaching databases [SQL Server]
ms.assetid: f63d4107-13e4-4bfe-922d-5e4f712e472d
author: stevestein
ms.author: sstein
ms.openlocfilehash: b8acc809b881012d18f78995bb8e521337fb02ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661135"
---
# <a name="detach-a-database"></a><span data-ttu-id="05443-102">데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="05443-102">Detach a Database</span></span>
  <span data-ttu-id="05443-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 데이터베이스를 분리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-103">This topic describes how to detach a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="05443-104">분리된 파일은 그대로 남아 있으며 FOR ATTACH 또는 FOR ATTACH_REBUILD_LOG 옵션과 함께 CREATE DATABASE를 사용하여 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05443-104">The detached files remain and can be reattached by using CREATE DATABASE with the FOR ATTACH or FOR ATTACH_REBUILD_LOG option.</span></span> <span data-ttu-id="05443-105">또한 파일을 다른 서버로 이동하거나 첨부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05443-105">The files can be moved to another server and attached there.</span></span>  
  
 <span data-ttu-id="05443-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="05443-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="05443-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="05443-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="05443-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="05443-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="05443-109">보안</span><span class="sxs-lookup"><span data-stu-id="05443-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="05443-110">**데이터베이스를 분리하려면:**</span><span class="sxs-lookup"><span data-stu-id="05443-110">**To detach a database, using:**</span></span>  
  
     [<span data-ttu-id="05443-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="05443-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="05443-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="05443-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="05443-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="05443-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="05443-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="05443-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="05443-115">제한 사항 목록은 [데이터베이스 분리 및 연결&#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)의 데이터베이스를 분리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-115">For a list of limitations and restrictions, see [Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="05443-116">보안</span><span class="sxs-lookup"><span data-stu-id="05443-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="05443-117">권한</span><span class="sxs-lookup"><span data-stu-id="05443-117">Permissions</span></span>  
 <span data-ttu-id="05443-118">db_owner 고정 데이터베이스 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-118">Requires membership in the db_owner fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="05443-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="05443-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-detach-a-database"></a><span data-ttu-id="05443-120">데이터베이스를 분리하려면</span><span class="sxs-lookup"><span data-stu-id="05443-120">To detach a database</span></span>  
  
1.  <span data-ttu-id="05443-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-121">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand the instance.</span></span>  
  
2.  <span data-ttu-id="05443-122">**데이터베이스**를 확장한 다음 분리할 사용자 데이터베이스 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-122">Expand **Databases**, and select the name of the user database you want to detach.</span></span>  
  
3.  <span data-ttu-id="05443-123">데이터베이스 이름을 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **분리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-123">Right-click the database name, point to **Tasks**, and then click **Detach**.</span></span> <span data-ttu-id="05443-124">**데이터베이스 분리** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="05443-124">The **Detach Database** dialog box appears.</span></span>  
  
     <span data-ttu-id="05443-125">**분리할 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="05443-125">**Databases to detach**</span></span>  
     <span data-ttu-id="05443-126">분리할 데이터베이스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-126">Lists the databases to detach.</span></span>  
  
     <span data-ttu-id="05443-127">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="05443-127">**Database Name**</span></span>  
     <span data-ttu-id="05443-128">분리할 데이터베이스 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-128">Displays the name of the database to be detached.</span></span>  
  
     <span data-ttu-id="05443-129">**연결 삭제**</span><span class="sxs-lookup"><span data-stu-id="05443-129">**Drop Connections**</span></span>  
     <span data-ttu-id="05443-130">지정한 데이터베이스에 대한 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="05443-130">Disconnect connections to the specified database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05443-131">활성 연결이 있는 데이터베이스는 분리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05443-131">You cannot detach a database with active connections.</span></span>  
  
     <span data-ttu-id="05443-132">**통계 업데이트**</span><span class="sxs-lookup"><span data-stu-id="05443-132">**Update Statistics**</span></span>  
     <span data-ttu-id="05443-133">기본적으로 분리 작업은 데이터베이스를 분리할 때 오래된 최적화 통계를 유지합니다. 기존의 최적화 통계를 업데이트하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-133">By default, the detach operation retains any out-of-date optimization statistics when detaching the database; to update the existing optimization statistics, click this check box.</span></span>  
  
     <span data-ttu-id="05443-134">**전체 텍스트 카탈로그 유지**</span><span class="sxs-lookup"><span data-stu-id="05443-134">**Keep Full-Text Catalogs**</span></span>  
     <span data-ttu-id="05443-135">기본적으로 분리 작업은 데이터베이스와 연결된 모든 전체 텍스트 카탈로그를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-135">By default, the detach operation keeps any full-text catalogs that are associated with the database.</span></span> <span data-ttu-id="05443-136">전체 텍스트 카탈로그를 제거하려면 **전체 텍스트 카탈로그 유지** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-136">To remove them, clear the **Keep Full-Text Catalogs** check box.</span></span> <span data-ttu-id="05443-137">이 옵션은 데이터베이스를 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 업그레이드하는 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="05443-137">This option appears only when you are upgrading a database from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="05443-138">**상태**</span><span class="sxs-lookup"><span data-stu-id="05443-138">**Status**</span></span>  
     <span data-ttu-id="05443-139">다음 상태 중 하나를 표시합니다. **준비** 또는 **준비 안 됨**을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-139">Displays one of the following states: **Ready** or **Not ready**.</span></span>  
  
     <span data-ttu-id="05443-140">**메시지**</span><span class="sxs-lookup"><span data-stu-id="05443-140">**Message**</span></span>  
     <span data-ttu-id="05443-141">다음과 같이 **메시지** 열에 데이터베이스에 대한 정보가 표시될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05443-141">The **Message** column may display information about the database, as follows:</span></span>  
  
    -   <span data-ttu-id="05443-142">데이터베이스가 복제와 관련된 경우 **상태** 는 **준비 안 됨** 이고 **메시지** 열에는 **데이터베이스 복제 완료**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="05443-142">When a database is involved with replication, the **Status** is **Not ready** and the **Message** column displays **Database replicated**.</span></span>  
  
    -   <span data-ttu-id="05443-143">데이터베이스에 하나 이상의 활성 연결이 있는 경우 **상태**는 **준비 안 됨**이고 **메시지** 열에는 _<number_of_active_connections>_ **활성 연결**이 표시됩니다. 예를 들어 **1 활성 연결**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="05443-143">When a database has one or more active connections, the **Status** is **Not ready** and the **Message** column displays _<number_of_active_connections>_**Active connection(s)** - for example: **1 Active connection(s)**.</span></span> <span data-ttu-id="05443-144">데이터베이스를 분리하려면 먼저 **연결 삭제**를 선택하여 모든 활성 연결을 끊어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-144">Before you can detach the database, you need to disconnect any active connections by selecting **Drop Connections**.</span></span>  
  
     <span data-ttu-id="05443-145">메시지에 대한 자세한 내용을 보려면 하이퍼링크로 연결된 텍스트를 클릭하여 작업 모니터를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="05443-145">To obtain more information about a message, click the hyperlinked text to open Activity Monitor.</span></span>  
  
4.  <span data-ttu-id="05443-146">데이터베이스를 분리할 준비가 되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-146">When you are ready to detach the database, click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05443-147">새로 분리된 데이터베이스는 뷰를 새로 고칠 때까지 개체 탐색기의 **데이터베이스** 노드에 계속 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="05443-147">The newly detached database will remain visible in the **Databases** node of Object Explorer until the view is refreshed.</span></span> <span data-ttu-id="05443-148">뷰는 언제든지 새로 고칠 수 있습니다. 개체 탐색기 창을 클릭하고 메뉴 모음에서 **보기**, **새로 고침**을 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-148">You can refresh the view at any time: Click in the Object Explorer pane, and from the menu bar select **View** and then **Refresh**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="05443-149">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="05443-149">Using Transact-SQL</span></span>  
  
#### <a name="to-detach-a-database"></a><span data-ttu-id="05443-150">데이터베이스를 분리하려면</span><span class="sxs-lookup"><span data-stu-id="05443-150">To detach a database</span></span>  
  
1.  <span data-ttu-id="05443-151">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-151">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="05443-152">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-152">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="05443-153">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-153">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="05443-154">이 예에서는 skipchecks가 true로 설정된 AdventureWorks2012 데이터베이스를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="05443-154">This example detaches the AdventureWorks2012 database with skipchecks set to true.</span></span>  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
## <a name="see-also"></a><span data-ttu-id="05443-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05443-155">See Also</span></span>  
 <span data-ttu-id="05443-156">[데이터베이스 분리 및 연결&#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="05443-156">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 [<span data-ttu-id="05443-157">sp_detach_db&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="05443-157">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
  
