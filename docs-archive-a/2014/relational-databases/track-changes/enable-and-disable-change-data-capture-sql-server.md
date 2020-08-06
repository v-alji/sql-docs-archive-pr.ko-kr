---
title: 변경 데이터 캡처 설정 및 해제(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- change data capture [SQL Server], enabling databases
- change data capture [SQL Server], disabling databases
- change data capture [SQL Server], disabling tables
ms.assetid: b741894f-d267-4b10-adfe-cbc14aa6caeb
author: rothja
ms.author: jroth
ms.openlocfilehash: df0a2fd4a2c6ffb2de58d6b52360d1730d0fa7df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650859"
---
# <a name="enable-and-disable-change-data-capture-sql-server"></a><span data-ttu-id="f6185-102">변경 데이터 캡처 설정 및 해제(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f6185-102">Enable and Disable Change Data Capture (SQL Server)</span></span>
  <span data-ttu-id="f6185-103">이 항목에서는 데이터베이스 및 테이블에서 변경 데이터 캡처를 사용하거나 사용하지 않도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-103">This topic describes how to enable and disable change data capture for a database and a table.</span></span>  
  
## <a name="enable-change-data-capture-for-a-database"></a><span data-ttu-id="f6185-104">데이터베이스에 변경 데이터 캡처 설정</span><span class="sxs-lookup"><span data-stu-id="f6185-104">Enable Change Data Capture for a Database</span></span>  
 <span data-ttu-id="f6185-105">개별 테이블에서 캡처 인스턴스를 만들려면 먼저 `sysadmin` 고정 서버 역할의 멤버가 데이터베이스에 변경 데이터 캡처를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-105">Before a capture instance can be created for individual tables, a member of the `sysadmin` fixed server role must first enable the database for change data capture.</span></span> <span data-ttu-id="f6185-106">이 작업은 데이터베이스 컨텍스트에서 [sys.sp_cdc_enable_db&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) 저장 프로시저를 실행하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-106">This is done by running the stored procedure [sys.sp_cdc_enable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) in the database context.</span></span> <span data-ttu-id="f6185-107">데이터베이스에 이 기능이 이미 설정되었는지 확인하려면 `is_cdc_enabled` 카탈로그 뷰의 `sys.databases` 열을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-107">To determine if a database is already enabled, query the `is_cdc_enabled` column in the `sys.databases` catalog view.</span></span>  
  
 <span data-ttu-id="f6185-108">데이터베이스에 변경 데이터 캡처가 설정되면 데이터베이스에 `cdc` 스키마, `cdc` 사용자, 메타데이터 테이블 및 다른 시스템 개체가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-108">When a database is enabled for change data capture, the `cdc` schema, `cdc` user, metadata tables, and other system objects are created for the database.</span></span> <span data-ttu-id="f6185-109">`cdc` 스키마에는 변경 데이터 캡처 메타데이터 테이블이 포함되며 원본 테이블에 변경 데이터 캡처가 설정된 후에는 변경 데이터에 대한 리포지토리 역할을 수행하는 개별 변경 테이블이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-109">The `cdc` schema contains the change data capture metadata tables and, after source tables are enabled for change data capture, the individual change tables serve as a repository for change data.</span></span> <span data-ttu-id="f6185-110">변경 데이터를 쿼리하는 데 사용되는 관련 시스템 함수도 `cdc` 스키마에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-110">The `cdc` schema also contains associated system functions used to query for change data.</span></span>  
  
 <span data-ttu-id="f6185-111">변경 데이터 캡처를 사용하려면 `cdc` 스키마와 `cdc` 사용자를 배타적으로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-111">Change data capture requires exclusive use of the `cdc` schema and `cdc` user.</span></span> <span data-ttu-id="f6185-112">*cdc* 라는 스키마 또는 데이터베이스 사용자가 데이터베이스에 현재 있는 경우 해당 스키마 및/또는 사용자가 삭제되거나 이름이 바뀔 때까지 데이터베이스에 변경 데이터 캡처를 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-112">If either a schema or a database user named *cdc* currently exists in a database, the database cannot be enabled for change data capture until the schema and or user are dropped or renamed.</span></span>  
  
 <span data-ttu-id="f6185-113">데이터베이스에서 이 기능을 사용하도록 설정하는 예는 데이터베이스의 변경 데이터 캡처 설정 템플릿을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6185-113">See the Enable Database for Change Data Capture template for an example of enabling a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f6185-114">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 이 템플릿을 찾으려면 **보기**로 이동하고 **템플릿 탐색기**를 클릭한 다음 **SQL Server 템플릿**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-114">To locate the templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], go to **View**, click **Template Explorer**, and then select **SQL Server Templates**.</span></span> <span data-ttu-id="f6185-115">**변경 데이터 캡처** 는 하위 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-115">**Change Data Capture** is a sub-folder.</span></span> <span data-ttu-id="f6185-116">이 폴더 아래에는 이 항목에서 참조하는 모든 템플릿이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-116">Under this folder, you will find all the templates referenced in this topic.</span></span> <span data-ttu-id="f6185-117">또한 **도구 모음에 있는** 템플릿 탐색기 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 아이콘을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-117">There is also a **Template Explorer** icon on the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar.</span></span>  
  
```sql  
-- ====  
-- Enable Database for CDC template   
-- ====  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_db  
GO  
```  
  
## <a name="disable-change-data-capture-for-a-database"></a><span data-ttu-id="f6185-118">데이터베이스의 변경 데이터 캡처 해제</span><span class="sxs-lookup"><span data-stu-id="f6185-118">Disable Change Data Capture for a Database</span></span>  
 <span data-ttu-id="f6185-119">`sysadmin`고정 서버 역할의 멤버는 데이터베이스 컨텍스트에서 [transact-sql&#41;&#40;sp_cdc_disable_db](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) 저장 프로시저를 실행 하 여 데이터베이스에 대 한 변경 데이터 캡처를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-119">A member of the `sysadmin` fixed server role can run the stored procedure [sys.sp_cdc_disable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) in the database context to disable change data capture for a database.</span></span> <span data-ttu-id="f6185-120">개별 테이블에서 먼저 이 기능을 해제한 후 데이터베이스에서 이 기능을 해제할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-120">It is not necessary to disable individual tables before you disable the database.</span></span> <span data-ttu-id="f6185-121">데이터베이스에서 이 기능을 해제하면 `cdc` 사용자 및 스키마와 변경 데이터 캡처 작업을 포함하는 모든 연결된 변경 데이터 캡처 메타데이터가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-121">Disabling the database removes all associated change data capture metadata, including the `cdc` user and schema and the change data capture jobs.</span></span> <span data-ttu-id="f6185-122">하지만 변경 데이터 캡처로 생성된 모든 제어 역할은 자동으로 제거되지 않으며 명시적으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-122">However, any gating roles created by change data capture will not be removed automatically and must be explicitly deleted.</span></span> <span data-ttu-id="f6185-123">데이터베이스에 이 기능이 설정되었는지 확인하려면 sys.databases 카탈로그 뷰의 `is_cdc_enabled` 열을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-123">To determine if a database is enabled, query the `is_cdc_enabled` column in the sys.databases catalog view.</span></span>  
  
 <span data-ttu-id="f6185-124">변경 데이터 캡처가 설정된 데이터베이스를 삭제하면 변경 데이터 캡처 작업이 자동으로 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-124">If a change data capture enabled database is dropped, change data capture jobs are automatically removed.</span></span>  
  
 <span data-ttu-id="f6185-125">데이터베이스에서 이 기능을 사용하지 않도록 설정하는 예는 데이터베이스의 변경 데이터 캡처 해제 템플릿을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6185-125">See the Disable Database for Change Data Capture template for an example of disabling a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f6185-126">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 이 템플릿을 찾으려면 **보기**로 이동하고 **템플릿 탐색기**를 클릭한 다음 **SQL Server 템플릿**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-126">To locate the templates in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], go to **View**, click **Template Explorer**, and then click **SQL Server Templates**.</span></span> <span data-ttu-id="f6185-127">**변경 데이터 캡처** 하위 폴더에는 이 항목에서 참조되는 모든 템플릿이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-127">**Change Data Capture** is a sub-folder where you will find all the templates that are referenced in this topic.</span></span> <span data-ttu-id="f6185-128">또한 **도구 모음에 있는** 템플릿 탐색기 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 아이콘을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-128">There is also a **Template Explorer** icon on the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar.</span></span>  
  
```sql  
-- =======  
-- Disable Database for Change Data Capture template   
-- =======  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_db  
GO  
```  
  
## <a name="enable-change-data-capture-for-a-table"></a><span data-ttu-id="f6185-129">테이블의 변경 데이터 캡처 설정</span><span class="sxs-lookup"><span data-stu-id="f6185-129">Enable Change Data Capture for a Table</span></span>  
 <span data-ttu-id="f6185-130">데이터베이스에 변경 데이터 캡처를 설정한 후에는 `db_owner` 고정 데이터베이스 역할의 멤버가 `sys.sp_cdc_enable_table` 저장 프로시저를 사용하여 개별 원본 테이블에 캡처 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-130">After a database has been enabled for change data capture, members of the `db_owner` fixed database role can create a capture instance for individual source tables by using the stored procedure `sys.sp_cdc_enable_table`.</span></span> <span data-ttu-id="f6185-131">원본 테이블에 변경 데이터 캡처가 이미 설정되었는지 확인하려면 `sys.tables` 카탈로그 뷰의 is_tracked_by_cdc 열을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-131">To determine whether a source table has already been enabled for change data capture, examine the is_tracked_by_cdc column in the `sys.tables` catalog view.</span></span>  
  
 <span data-ttu-id="f6185-132">캡처 인스턴스를 만들 때에는 다음과 같은 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-132">The following options can be specified when creating a capture instance:</span></span>  
  
 <span data-ttu-id="f6185-133">`Columns in the source table to be captured`.</span><span class="sxs-lookup"><span data-stu-id="f6185-133">`Columns in the source table to be captured`.</span></span>  
  
 <span data-ttu-id="f6185-134">기본적으로 원본 테이블의 모든 열은 캡처된 열로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-134">By default, all of the columns in the source table are identified as captured columns.</span></span> <span data-ttu-id="f6185-135">개인 정보 보호 또는 성능상의 이유로 열의 하위 집합만 추적 해야 하는 경우 매개 변수를 사용 하 여 *@captured_column_list* 열의 하위 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-135">If only a subset of columns need to be tracked, such as for privacy or performance reasons, use the *@captured_column_list* parameter to specify the subset of columns.</span></span>  
  
 `A filegroup to contain the change table.`  
  
 <span data-ttu-id="f6185-136">기본적으로 변경 테이블은 데이터베이스의 기본 파일 그룹에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-136">By default, the change table is located in the default filegroup of the database.</span></span> <span data-ttu-id="f6185-137">개별 변경 테이블의 배치를 제어 하려는 데이터베이스 소유자는 매개 변수를 사용 *@filegroup_name* 하 여 캡처 인스턴스와 연결 된 변경 테이블에 대해 특정 파일 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-137">Database owners who want to control the placement of individual change tables can use the *@filegroup_name* parameter to specify a particular filegroup for the change table associated with the capture instance.</span></span> <span data-ttu-id="f6185-138">명명된 파일 그룹은 이미 존재해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-138">The named filegroup must already exist.</span></span> <span data-ttu-id="f6185-139">일반적으로 변경 테이블은 원본 테이블과 별도의 파일 그룹에 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-139">Generally, it is recommended that change tables be placed in a filegroup separate from source tables.</span></span> <span data-ttu-id="f6185-140">`Enable a Table Specifying Filegroup Option`매개 변수를 사용 하는 방법을 보여 주는 예제는 템플릿을 참조 하십시오 *@filegroup_name* .</span><span class="sxs-lookup"><span data-stu-id="f6185-140">See the `Enable a Table Specifying Filegroup Option` template for an example showing use of the *@filegroup_name* parameter.</span></span>  
  
```sql  
-- =========  
-- Enable a Table Specifying Filegroup Option Template  
-- =========  
USE MyDB  
GO  
  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@filegroup_name = N'MyDB_CT',  
@supports_net_changes = 1  
GO  
```  
  
 `A role for controlling access to a change table.`  
  
 <span data-ttu-id="f6185-141">명명된 역할의 목적은 변경 데이터에 대한 액세스를 제어하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-141">The purpose of the named role is to control access to the change data.</span></span> <span data-ttu-id="f6185-142">지정된 역할은 기존의 고정 서버 역할 또는 데이터베이스 역할일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-142">The specified role can be an existing fixed server role or a database role.</span></span> <span data-ttu-id="f6185-143">지정된 역할이 아직 없는 경우 해당 이름의 데이터베이스 역할이 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-143">If the specified role does not already exist, a database role of that name is created automatically.</span></span> <span data-ttu-id="f6185-144">`sysadmin` 또는 `db_owner` 역할의 멤버는 변경 테이블의 데이터에 대한 모든 액세스 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-144">Members of either the `sysadmin` or `db_owner` role have full access to the data in the change tables.</span></span> <span data-ttu-id="f6185-145">다른 모든 사용자에게는 원본 테이블의 모든 캡처된 열에 대한 SELECT 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-145">All other users must have SELECT permission on all the captured columns of the source table.</span></span> <span data-ttu-id="f6185-146">또한 역할이 지정되면 `sysadmin` 또는 `db_owner` 역할의 멤버가 아닌 사용자도 지정한 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-146">In addition, when a role is specified, users who are not members of either the `sysadmin` or `db_owner` role must also be members of the specified role.</span></span>  
  
 <span data-ttu-id="f6185-147">제어 역할을 사용 하지 않으려면 매개 변수를 명시적으로 *@role_name* NULL로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-147">If you do not want to use a gating role, explicitly set the *@role_name* parameter to NULL.</span></span> <span data-ttu-id="f6185-148">제어 역할이 없는 테이블을 설정하는 예는 `Enable a Table Without Using a Gating Role` 템플릿을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6185-148">See the `Enable a Table Without Using a Gating Role` template for an example of enabling a table without a gating role.</span></span>  
  
```sql  
-- =========  
-- Enable a Table Without Using a Gating Role template   
-- =========  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = NULL,  
@supports_net_changes = 1  
GO  
  
```  
  
 `A function to query for net changes.`  
  
 <span data-ttu-id="f6185-149">캡처 인스턴스에는 항상 정의된 간격 내에서 발생한 모든 변경 테이블 항목을 반환하는 데 사용되는 테이블 반환 함수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-149">A capture instance will always include a table valued function for returning all change table entries that occurred within a defined interval.</span></span> <span data-ttu-id="f6185-150">이 함수 이름은 "cdc.fn_cdc_get_all_changes_"에 캡처 인스턴스 이름을 추가하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-150">This function is named by appending the capture instance name to "cdc.fn_cdc_get_all_changes_".</span></span> <span data-ttu-id="f6185-151">자세한 내용은 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6185-151">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="f6185-152">매개 변수가 *@supports_net_changes* 1로 설정 된 경우 캡처 인스턴스에 대 한 순 변경 함수도 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-152">If the parameter *@supports_net_changes* is set to 1, a net changes function is also generated for the capture instance.</span></span> <span data-ttu-id="f6185-153">이 함수는 호출에 지정된 간격 내에 변경된 각 개별 행에 대해 하나의 변경만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-153">This function returns only one change for each distinct row changed in the interval specified in the call.</span></span> <span data-ttu-id="f6185-154">자세한 내용은 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62;&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6185-154">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="f6185-155">순 변경 쿼리를 지원하기 위해 원본 테이블에는 행을 고유하게 식별하는 기본 키 또는 고유 인덱스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-155">To support net changes queries, the source table must have a primary key or unique index to uniquely identify rows.</span></span> <span data-ttu-id="f6185-156">고유 인덱스를 사용 하는 경우 매개 변수를 사용 하 여 인덱스 이름을 지정 해야 합니다 *@index_name* .</span><span class="sxs-lookup"><span data-stu-id="f6185-156">If a unique index is used, the name of the index must be specified using the *@index_name* parameter.</span></span> <span data-ttu-id="f6185-157">기본 키 또는 고유 인덱스에 정의된 열은 캡처할 원본 열 목록에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-157">The columns defined in the primary key or unique index must be included in the list of source columns to be captured.</span></span>  
  
 <span data-ttu-id="f6185-158">두 쿼리 함수로 캡처 인스턴스를 생성하는 방법을 보여 주는 예는 `Enable a Table for All and Net Changes Queries` 템플릿을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6185-158">See the `Enable a Table for All and Net Changes Queries` template for an example demonstrating the creation of a capture instance with both query functions.</span></span>  
  
```sql  
-- =============  
-- Enable a Table for All and Net Changes Queries template   
-- =============  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@supports_net_changes = 1  
GO  
```  
  
> [!NOTE]
>  <span data-ttu-id="f6185-159">기존 기본 키가 있는 테이블에 변경 데이터 캡처가 설정 되어 있고 *@index_name* 매개 변수를 사용 하 여 대체 고유 인덱스를 식별 하지 않는 경우 변경 데이터 캡처 기능에서 기본 키를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-159">If change data capture is enabled on a table with an existing primary key, and the *@index_name* parameter is not used to identify an alternative unique index, the change data capture feature will use the primary key.</span></span> <span data-ttu-id="f6185-160">기본 키에 대한 후속 변경 내용을 허용하려면 먼저 테이블의 변경 데이터 캡처를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-160">Subsequent changes to the primary key will not be allowed without first disabling change data capture for the table.</span></span> <span data-ttu-id="f6185-161">이는 변경 데이터 캡처를 구성할 때 순 변경 쿼리에 대한 지원을 요청했는지 여부와 관계없이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-161">This is true regardless of whether support for net changes queries was requested when change data capture was configured.</span></span> <span data-ttu-id="f6185-162">테이블에 변경 데이터 캡처를 설정할 당시 기본 키가 없는 경우에는 기본 키에 대한 후속 추가 사항이 변경 데이터 캡처에 의해 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-162">If there is no primary key on a table at the time it is enabled for change data capture, the subsequent addition of a primary key is ignored by change data capture.</span></span> <span data-ttu-id="f6185-163">변경 데이터 캡처는 테이블에 이 기능이 설정된 이후에 생성되는 기본 키를 사용하지 않으므로 키와 키 열을 제한 없이 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-163">Because change data capture will not use a primary key that is created after the table was enabled, the key and key columns can be removed without restrictions.</span></span>  
  
## <a name="disable-change-data-capture-for-a-table"></a><span data-ttu-id="f6185-164">테이블의 변경 데이터 캡처 해제</span><span class="sxs-lookup"><span data-stu-id="f6185-164">Disable Change Data Capture for a Table</span></span>  
 <span data-ttu-id="f6185-165">`db_owner` 고정 데이터베이스 역할의 멤버는 `sys.sp_cdc_disable_table` 저장 프로시저를 사용하여 개별 원본 테이블의 캡처 인스턴스를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-165">Members of the `db_owner` fixed database role can remove a capture instance for individual source tables by using the stored procedure `sys.sp_cdc_disable_table`.</span></span> <span data-ttu-id="f6185-166">원본 테이블에 현재 변경 데이터 캡처가 설정되었는지 확인하려면 `is_tracked_by_cdc` 카탈로그 뷰의 `sys.tables` 열을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-166">To determine whether a source table is currently enabled for change data capture, examine the `is_tracked_by_cdc` column in the `sys.tables` catalog view.</span></span> <span data-ttu-id="f6185-167">해제를 수행한 후 데이터베이스에 변경 데이터 캡처 기능이 설정된 테이블이 없으면 변경 데이터 캡처 작업도 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-167">If there are no tables enabled for the database after the disabling takes place, the change data capture jobs are also removed.</span></span>  
  
 <span data-ttu-id="f6185-168">변경 데이터 캡처가 설정된 테이블을 삭제하면 이 테이블과 연결된 변경 데이터 캡처 메타데이터도 자동으로 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6185-168">If a change data capture-enabled table is dropped, change data capture metadata that is associated with the table is automatically removed.</span></span>  
  
 <span data-ttu-id="f6185-169">테이블에서 이 기능을 사용하지 않도록 설정하는 예는 테이블의 캡처 인스턴스 해제 템플릿을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6185-169">See the Disable a Capture Instance for a Table template for an example of disabling a table.</span></span>  
  
```sql  
-- =====  
-- Disable a Capture Instance for a Table template   
-- =====  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@capture_instance = N'dbo_MyTable'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6185-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6185-170">See Also</span></span>  
 <span data-ttu-id="f6185-171">[데이터 변경 내용 추적&#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f6185-171">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="f6185-172">[변경 데이터 캡처 정보&#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f6185-172">[About Change Data Capture &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md) </span></span>  
 <span data-ttu-id="f6185-173">[변경 데이터 작업&#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f6185-173">[Work with Change Data &#40;SQL Server&#41;](work-with-change-data-sql-server.md) </span></span>  
 [<span data-ttu-id="f6185-174">변경 데이터 캡처 관리 및 모니터링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f6185-174">Administer and Monitor Change Data Capture &#40;SQL Server&#41;</span></span>](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
