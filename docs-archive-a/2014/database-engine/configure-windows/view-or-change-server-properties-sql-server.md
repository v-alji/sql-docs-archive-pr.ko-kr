---
title: 서버 속성 보기 또는 변경(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- viewing server properties
- server properties [SQL Server]
- displaying server properties
- servers [SQL Server], viewing
ms.assetid: 55f3ac04-5626-4ad2-96bd-a1f1b079659d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 415d4e2d1aaa3166ae4df2dea53b34e064544e06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729791"
---
# <a name="view-or-change-server-properties-sql-server"></a><span data-ttu-id="34b16-102">서버 속성 보기 또는 변경(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="34b16-102">View or Change Server Properties (SQL Server)</span></span>
  <span data-ttu-id="34b16-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]인스턴스의 속성을 보거나 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-103">This topic describes how to view or change the properties of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Configuration Manager.</span></span>  
  
 <span data-ttu-id="34b16-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="34b16-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="34b16-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="34b16-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="34b16-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="34b16-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="34b16-107">보안</span><span class="sxs-lookup"><span data-stu-id="34b16-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="34b16-108">**서버 속성을 보거나 변경하려면:**</span><span class="sxs-lookup"><span data-stu-id="34b16-108">**To view or change server properties, using:**</span></span>  
  
     [<span data-ttu-id="34b16-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="34b16-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="34b16-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="34b16-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="34b16-111">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="34b16-111">SQL Server Configuration Manager</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="34b16-112">**후속 작업:**  [서버 속성을 변경한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="34b16-112">**Follow Up:**  [After you change server properties](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="34b16-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="34b16-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="34b16-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="34b16-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="34b16-115">sp_configure를 사용할 때는 구성 옵션을 설정한 뒤에 RECONFIGURE 또는 RECONFIGURE WITH OVERRIDE를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-115">When using sp_configure, you must run either RECONFIGURE or RECONFIGURE WITH OVERRIDE after setting a configuration option.</span></span> <span data-ttu-id="34b16-116">RECONFIGURE WITH OVERRIDE 문은 각별한 주의가 필요한 구성 옵션에 주로 사용되지만</span><span class="sxs-lookup"><span data-stu-id="34b16-116">The RECONFIGURE WITH OVERRIDE statement is usually reserved for configuration options that should be used with extreme caution.</span></span> <span data-ttu-id="34b16-117">모든 구성 옵션에 사용할 수 있으며 RECONFIGURE 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-117">However, RECONFIGURE WITH OVERRIDE works for all configuration options, and you can use it in place of RECONFIGURE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34b16-118">RECONFIGURE는 트랜잭션 내에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-118">RECONFIGURE executes within a transaction.</span></span> <span data-ttu-id="34b16-119">다시 구성 작업 중 하나가 실패하면 다시 구성 작업이 하나도 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-119">If any of the reconfigure operations fail, none of the reconfigure operations will take effect.</span></span>  
  
-   <span data-ttu-id="34b16-120">일부 속성 페이지는 WMI(Windows Management Instrumentation)를 통해 얻은 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-120">Some property pages present information obtained via Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="34b16-121">이러한 페이지를 표시하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 실행 중인 컴퓨터에 WMI가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-121">To display those pages, WMI must be installed on the computer running [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="34b16-122">보안</span><span class="sxs-lookup"><span data-stu-id="34b16-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="34b16-123">권한</span><span class="sxs-lookup"><span data-stu-id="34b16-123">Permissions</span></span>  
 <span data-ttu-id="34b16-124">자세한 내용은 [서버 수준 역할](../../relational-databases/security/authentication-access/server-level-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34b16-124">For more information, see [Server-Level Roles](../../relational-databases/security/authentication-access/server-level-roles.md).</span></span>  
  
 <span data-ttu-id="34b16-125">매개 변수 없이 또는 첫 번째 매개 변수만 사용 하 여에 대 한 실행 권한은 `sp_configure` 기본적으로 모든 사용자에 게 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-125">Execute permissions on `sp_configure` with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="34b16-126">`sp_configure`구성 옵션을 변경 하거나 RECONFIGURE 문을 실행 하는 두 매개 변수를 사용 하 여 실행 하려면 사용자에 게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-126">To execute `sp_configure` with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="34b16-127">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-127">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="34b16-128">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="34b16-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-server-properties"></a><span data-ttu-id="34b16-129">서버 속성을 보거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="34b16-129">To view or change server properties</span></span>  
  
1.  <span data-ttu-id="34b16-130">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-130">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="34b16-131">**서버 속성** 대화 상자에서 해당 페이지에 대한 서버 정보를 보거나 변경할 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-131">In the **Server Properties** dialog box, click a page to view or change server information about that page.</span></span> <span data-ttu-id="34b16-132">일부 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-132">Some properties are read-only.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="34b16-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="34b16-133">Using Transact-SQL</span></span>  
  
#### <a name="to-view-server-properties-by-using-the-serverproperty-built-in-function"></a><span data-ttu-id="34b16-134">SERVERPROPERTY 기본 제공 함수를 사용하여 서버 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="34b16-134">To view server properties by using the SERVERPROPERTY built-in function</span></span>  
  
1.  <span data-ttu-id="34b16-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="34b16-136">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="34b16-137">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="34b16-138">이 예제에서는 [문에](/sql/t-sql/functions/serverproperty-transact-sql) SERVERPROPERTY `SELECT` 기본 제공 함수를 사용하여 현재 서버에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-138">This example uses the [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) built-in function in a `SELECT` statement to return information about the current server.</span></span> <span data-ttu-id="34b16-139">이 시나리오는 한 Windows 기반 서버에 여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 설치되어 있고 클라이언트가 현재 연결에서 사용되는 인스턴스에 대한 또 다른 연결을 열어야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-139">This scenario is useful when there are multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on a Windows-based server, and the client must open another connection to the same instance that is used by the current connection.</span></span>  
  
    ```sql  
    SELECT CONVERT( sysname, SERVERPROPERTY('servername'));  
    GO  
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysservers-catalog-view"></a><span data-ttu-id="34b16-140">sys.servers 카탈로그 뷰를 사용하여 서버 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="34b16-140">To view server properties by using the sys.servers catalog view</span></span>  
  
1.  <span data-ttu-id="34b16-141">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="34b16-142">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="34b16-143">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="34b16-144">이 예제에서는 [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) 카탈로그 뷰를 쿼리하여 현재 서버의 이름(`name`)과 ID(`server_id`) 및 연결된 서버에 연결하기 위한 OLE DB 공급자의 이름(`provider`)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-144">This example queries the [sys.servers](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql) catalog view to return the name (`name`) and ID (`server_id`) of the current server, and the name of the OLE DB provider (`provider`) for connecting to a linked server.</span></span>  
  
    ```sql  
    USE AdventureWorks2012;   
    GO  
    SELECT name, server_id, provider  
    FROM sys.servers ;   
    GO
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysconfigurations-catalog-view"></a><span data-ttu-id="34b16-145">sys.configurations 카탈로그 뷰를 사용하여 서버 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="34b16-145">To view server properties by using the sys.configurations catalog view</span></span>  
  
1.  <span data-ttu-id="34b16-146">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-146">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="34b16-147">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-147">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="34b16-148">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-148">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="34b16-149">이 예에서는 [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) 카탈로그 뷰를 쿼리하여 현재 서버의 각 서버 구성 옵션에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-149">This example queries the [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view to return information about each server configuration option on the current server.</span></span> <span data-ttu-id="34b16-150">이 예에서는 옵션의 이름(`name`)과 설명(`description`) 및 옵션이 고급 옵션인지 여부(`is_advanced`)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-150">The example returns the name (`name`) and description (`description`) of the option and whether the option is an advanced option (`is_advanced`).</span></span>  
  
    ```sql
    USE AdventureWorks2012;
    GO  
    SELECT name, description, is_advanced  
    FROM sys.configurations ;
    GO
    ```  
  
#### <a name="to-change-a-server-property-by-using-sp_configure"></a><span data-ttu-id="34b16-151">sp_configure를 사용하여 서버 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="34b16-151">To change a server property by using sp_configure</span></span>  
  
1.  <span data-ttu-id="34b16-152">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="34b16-153">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="34b16-154">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-154">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="34b16-155">이 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 서버 속성을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-155">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to change a server property.</span></span> <span data-ttu-id="34b16-156">이 예에서는 `fill factor` 옵션의 값을 `100`으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-156">The example changes the value of the `fill factor` option to `100`.</span></span> <span data-ttu-id="34b16-157">변경 내용을 적용하려면 서버를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-157">The server must be restarted before the change can take effect.</span></span>  
  
```sql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="34b16-158">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-158">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="34b16-159">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="34b16-159">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="34b16-160">일부 서버 속성은 SQL Server 구성 관리자를 사용하여 보거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-160">Some server properties can be viewed or changed by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="34b16-161">예를 들어 SQL Server 인스턴스의 버전 및 에디션을 보거나 오류 로그 파일이 저장된 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-161">For example, you can view the version and edition of the instance of SQL Server, or change the location where error log files are stored.</span></span> <span data-ttu-id="34b16-162">[서버 관련 동적 관리 뷰 및 함수](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)를 쿼리하여 이러한 속성을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-162">These properties can also be viewed by querying the [Server-Related Dynamic Management Views and Functions](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql).</span></span>  
  
#### <a name="to-view-or-change-server-properties"></a><span data-ttu-id="34b16-163">서버 속성을 보거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="34b16-163">To view or change server properties</span></span>  
  
1.  <span data-ttu-id="34b16-164">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-164">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="34b16-165">**SQL Server 구성 관리자**에서 **SQL Server 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-165">In **SQL Server Configuration Manager**, click **SQL Server Services**.</span></span>  
  
3.  <span data-ttu-id="34b16-166">세부 정보 창에서 **SQL Server(\<***instancename***>)** 를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-166">In the details pane, right-click **SQL Server (\<***instancename***>)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="34b16-167">**SQL Server(\<***instancename***>) 속성 대화** 상자의 **서비스** 탭 또는 **고급** 탭에서 서버 속성을 변경한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-167">In the **SQL Server (\<***instancename***>) Properties** dialog box, change the server properties on the **Service** tab or the **Advanced** tab, and then click **OK**.</span></span>  
  
##  <a name="follow-up-after-you-change-server-properties"></a><a name="FollowUp"></a><span data-ttu-id="34b16-168">후속 작업: 서버 속성을 변경한 후</span><span class="sxs-lookup"><span data-stu-id="34b16-168">Follow Up: After you change server properties</span></span>  
 <span data-ttu-id="34b16-169">일부 속성의 경우 변경 내용을 적용하려면 서버를 다시 시작해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b16-169">For some properties, the server might have to be restarted before the change can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b16-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34b16-170">See Also</span></span>  
 <span data-ttu-id="34b16-171">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="34b16-171">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="34b16-172">[SET 문&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34b16-172">[SET Statements &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql) </span></span>  
 <span data-ttu-id="34b16-173">[SERVERPROPERTY&#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34b16-173">[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql) </span></span>  
 <span data-ttu-id="34b16-174">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34b16-174">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="34b16-175">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34b16-175">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="34b16-176">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34b16-176">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="34b16-177">[WMI를 구성하여 SQL Server 도구에 서버 상태 표시](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md) </span><span class="sxs-lookup"><span data-stu-id="34b16-177">[Configure WMI to Show Server Status in SQL Server Tools](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md) </span></span>  
 <span data-ttu-id="34b16-178">[SQL Server 구성 관리자](../../relational-databases/sql-server-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="34b16-178">[SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md) </span></span>  
 <span data-ttu-id="34b16-179">[구성 함수&#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="34b16-179">[Configuration Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/configuration-functions-transact-sql) </span></span>  
 [<span data-ttu-id="34b16-180">서버 관련 동적 관리 뷰 및 함수&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="34b16-180">Server-Related Dynamic Management Views and Functions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql)  
