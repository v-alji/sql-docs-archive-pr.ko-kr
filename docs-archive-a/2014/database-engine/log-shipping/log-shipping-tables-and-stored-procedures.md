---
title: 로그 전달 테이블 및 저장 프로시저 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary servers [SQL Server]
- monitor servers [SQL Server]
- log shipping [SQL Server], system tables
- log shipping [SQL Server], stored procedures
- primary servers [SQL Server]
ms.assetid: 03420810-4c38-4c0c-adf0-913eb044c50a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f10a6555ed3a0c27a72c3d097cc200f21d901274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729744"
---
# <a name="log-shipping-tables-and-stored-procedures"></a><span data-ttu-id="3988e-102">Log Shipping Tables and Stored Procedures</span><span class="sxs-lookup"><span data-stu-id="3988e-102">Log Shipping Tables and Stored Procedures</span></span>
  <span data-ttu-id="3988e-103">이 항목에서는 로그 전달 구성과 관련된 모든 테이블과 저장된 프로시저에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-103">This topic describes all of the tables and stored procedures associated with a log shipping configuration.</span></span> <span data-ttu-id="3988e-104">모든 로그 전달 테이블은 각 서버의 **msdb** 에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-104">All log shipping tables are stored in **msdb** on each server.</span></span> <span data-ttu-id="3988e-105">아래의 표에서는 로그 전달 구성에서 서버에 사용된 테이블 및 저장 프로시저를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-105">The tables below describe which tables and stored procedures are used on which servers in a log shipping configuration.</span></span>  
  
## <a name="primary-server-tables"></a><span data-ttu-id="3988e-106">주 서버 테이블</span><span class="sxs-lookup"><span data-stu-id="3988e-106">Primary Server Tables</span></span>  
  
|<span data-ttu-id="3988e-107">테이블</span><span class="sxs-lookup"><span data-stu-id="3988e-107">Table</span></span>|<span data-ttu-id="3988e-108">Description</span><span class="sxs-lookup"><span data-stu-id="3988e-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3988e-109">log_shipping_monitor_alert</span><span class="sxs-lookup"><span data-stu-id="3988e-109">log_shipping_monitor_alert</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|<span data-ttu-id="3988e-110">경고 작업 ID를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-110">Stores alert job ID.</span></span> <span data-ttu-id="3988e-111">이 테이블은 원격 모니터 서버가 구성되지 않았으면 주 서버에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-111">This table is only used on the primary server if a remote monitor server has not been configured.</span></span>|  
|[<span data-ttu-id="3988e-112">log_shipping_monitor_error_detail</span><span class="sxs-lookup"><span data-stu-id="3988e-112">log_shipping_monitor_error_detail</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|<span data-ttu-id="3988e-113">이 주 서버와 관련된 로그 전달 작업에 대한 오류 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-113">Stores error detail for log shipping jobs associated with this primary server.</span></span>|  
|[<span data-ttu-id="3988e-114">log_shipping_monitor_history_detail</span><span class="sxs-lookup"><span data-stu-id="3988e-114">log_shipping_monitor_history_detail</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|<span data-ttu-id="3988e-115">이 주 서버와 관련된 로그 전달 작업에 대한 기록 세부 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-115">Stores history detail for log shipping jobs associated with this primary server.</span></span>|  
|[<span data-ttu-id="3988e-116">log_shipping_monitor_primary</span><span class="sxs-lookup"><span data-stu-id="3988e-116">log_shipping_monitor_primary</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)|<span data-ttu-id="3988e-117">이 주 데이터베이스에 대한 하나의 모니터 레코드를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-117">Stores one monitor record for this primary database.</span></span>|  
|[<span data-ttu-id="3988e-118">log_shipping_primary_databases</span><span class="sxs-lookup"><span data-stu-id="3988e-118">log_shipping_primary_databases</span></span>](/sql/relational-databases/system-tables/log-shipping-primary-databases-transact-sql)|<span data-ttu-id="3988e-119">지정된 서버의 주 데이터베이스에 대한 구성 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-119">Contains configuration information for primary databases on a given server.</span></span> <span data-ttu-id="3988e-120">주 데이터베이스마다 한 행을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-120">Stores one row per primary database.</span></span>|  
|[<span data-ttu-id="3988e-121">log_shipping_primary_secondaries</span><span class="sxs-lookup"><span data-stu-id="3988e-121">log_shipping_primary_secondaries</span></span>](/sql/relational-databases/system-tables/log-shipping-primary-secondaries-transact-sql)|<span data-ttu-id="3988e-122">주 데이터베이스를 보조 데이터베이스로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-122">Maps primary databases to secondary databases.</span></span>|  
  
## <a name="primary-server-stored-procedures"></a><span data-ttu-id="3988e-123">주 서버 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="3988e-123">Primary Server Stored Procedures</span></span>  
  
|<span data-ttu-id="3988e-124">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="3988e-124">Stored Procedure</span></span>|<span data-ttu-id="3988e-125">Description</span><span class="sxs-lookup"><span data-stu-id="3988e-125">Description</span></span>|  
|----------------------|-----------------|  
|[<span data-ttu-id="3988e-126">sp_add_log_shipping_primary_database</span><span class="sxs-lookup"><span data-stu-id="3988e-126">sp_add_log_shipping_primary_database</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)|<span data-ttu-id="3988e-127">백업 작업, 로컬 모니터 레코드 및 원격 모니터 레코드를 포함하여 로그 전달 구성에 대한 주 데이터베이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-127">Sets up the primary database for a log shipping configuration, including the backup job, local monitor record, and remote monitor record.</span></span>|  
|[<span data-ttu-id="3988e-128">sp_add_log_shipping_primary_secondary</span><span class="sxs-lookup"><span data-stu-id="3988e-128">sp_add_log_shipping_primary_secondary</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql)|<span data-ttu-id="3988e-129">기존 주 데이터베이스에 보조 데이터베이스 이름을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-129">Adds a secondary database name to an existing primary database.</span></span>|  
|[<span data-ttu-id="3988e-130">sp_change_log_shipping_primary_database</span><span class="sxs-lookup"><span data-stu-id="3988e-130">sp_change_log_shipping_primary_database</span></span>](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql)|<span data-ttu-id="3988e-131">로컬 및 원격 모니터 레코드를 포함하여 주 데이터베이스 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-131">Changes primary database settings including local and remote monitor record.</span></span>|  
|[<span data-ttu-id="3988e-132">sp_cleanup_log_shipping_history</span><span class="sxs-lookup"><span data-stu-id="3988e-132">sp_cleanup_log_shipping_history</span></span>](/sql/relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql)|<span data-ttu-id="3988e-133">보존 기간을 기준으로 로컬과 모니터에서 기록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-133">Cleans up history locally and on the monitor based on retention period.</span></span>|  
|[<span data-ttu-id="3988e-134">sp_delete_log_shipping_primary_database</span><span class="sxs-lookup"><span data-stu-id="3988e-134">sp_delete_log_shipping_primary_database</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql)|<span data-ttu-id="3988e-135">로컬 및 원격 기록과 백업 작업을 포함하여 주 데이터베이스의 로그 전달을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-135">Removes log shipping of primary database including backup job as well as local and remote history.</span></span>|  
|[<span data-ttu-id="3988e-136">sp_delete_log_shipping_primary_secondary</span><span class="sxs-lookup"><span data-stu-id="3988e-136">sp_delete_log_shipping_primary_secondary</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql)|<span data-ttu-id="3988e-137">주 데이터베이스에서 보조 데이터베이스 이름을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-137">Removes a secondary database name from a primary database.</span></span>|  
|[<span data-ttu-id="3988e-138">sp_help_log_shipping_primary_database</span><span class="sxs-lookup"><span data-stu-id="3988e-138">sp_help_log_shipping_primary_database</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql)|<span data-ttu-id="3988e-139">주 데이터베이스 설정을 검색하고 **log_shipping_primary_databases** 및 **log_shipping_monitor_primary** 테이블의 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-139">Retrieves primary database settings and displays the values from the **log_shipping_primary_databases** and **log_shipping_monitor_primary** tables.</span></span>|  
|[<span data-ttu-id="3988e-140">sp_help_log_shipping_primary_secondary</span><span class="sxs-lookup"><span data-stu-id="3988e-140">sp_help_log_shipping_primary_secondary</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-secondary-transact-sql)|<span data-ttu-id="3988e-141">주 데이터베이스의 보조 데이터베이스 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-141">Retrieves secondary database names for a primary database.</span></span>|  
|[<span data-ttu-id="3988e-142">sp_refresh_log_shipping_monitor</span><span class="sxs-lookup"><span data-stu-id="3988e-142">sp_refresh_log_shipping_monitor</span></span>](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)|<span data-ttu-id="3988e-143">지정된 로그 전달 에이전트에 대한 최신 정보로 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-143">Refreshes the monitor with the latest information for the specified log shipping agent.</span></span>|  
  
## <a name="secondary-server-tables"></a><span data-ttu-id="3988e-144">보조 서버 테이블</span><span class="sxs-lookup"><span data-stu-id="3988e-144">Secondary Server Tables</span></span>  
  
|<span data-ttu-id="3988e-145">테이블</span><span class="sxs-lookup"><span data-stu-id="3988e-145">Table</span></span>|<span data-ttu-id="3988e-146">Description</span><span class="sxs-lookup"><span data-stu-id="3988e-146">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3988e-147">log_shipping_monitor_alert</span><span class="sxs-lookup"><span data-stu-id="3988e-147">log_shipping_monitor_alert</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|<span data-ttu-id="3988e-148">경고 작업 ID를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-148">Stores alert job ID.</span></span> <span data-ttu-id="3988e-149">이 테이블은 원격 모니터 서버가 구성되지 않았으면 보조 서버에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-149">This table is only used on the secondary server if a remote monitor server has not been configured.</span></span>|  
|[<span data-ttu-id="3988e-150">log_shipping_monitor_error_detail</span><span class="sxs-lookup"><span data-stu-id="3988e-150">log_shipping_monitor_error_detail</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|<span data-ttu-id="3988e-151">이 보조 서버와 관련된 로그 전달 작업에 대한 오류 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-151">Stores error detail for log shipping jobs associated with this secondary server.</span></span>|  
|[<span data-ttu-id="3988e-152">log_shipping_monitor_history_detail</span><span class="sxs-lookup"><span data-stu-id="3988e-152">log_shipping_monitor_history_detail</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|<span data-ttu-id="3988e-153">이 보조 서버와 관련된 로그 저장 작업에 대한 기록 세부 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-153">Stores history detail for log shipping jobs associated with this secondary server.</span></span>|  
|[<span data-ttu-id="3988e-154">log_shipping_monitor_secondary</span><span class="sxs-lookup"><span data-stu-id="3988e-154">log_shipping_monitor_secondary</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)|<span data-ttu-id="3988e-155">이 보조 서버와 관련된 보조 데이터베이스마다 하나의 모니터 레코드를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-155">Stores one monitor record per secondary database associated with this secondary server.</span></span>|  
|[<span data-ttu-id="3988e-156">log_shipping_secondary</span><span class="sxs-lookup"><span data-stu-id="3988e-156">log_shipping_secondary</span></span>](/sql/relational-databases/system-tables/log-shipping-secondary-transact-sql)|<span data-ttu-id="3988e-157">지정된 서버의 보조 데이터베이스에 대한 구성 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-157">Contains configuration information for the secondary databases on a given server.</span></span> <span data-ttu-id="3988e-158">보조 ID마다 한 행을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-158">Stores one row per secondary ID.</span></span>|  
|[<span data-ttu-id="3988e-159">log_shipping_secondary_databases</span><span class="sxs-lookup"><span data-stu-id="3988e-159">log_shipping_secondary_databases</span></span>](/sql/relational-databases/system-tables/log-shipping-secondary-databases-transact-sql)|<span data-ttu-id="3988e-160">지정된 보조 데이터베이스에 대한 구성 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-160">Stores configuration information for a given secondary database.</span></span> <span data-ttu-id="3988e-161">보조 데이터베이스마다 한 행을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-161">Stores one row per secondary database.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="3988e-162">지정된 주 데이터베이스에 대한 동일한 보조 서버의 보조 데이터베이스는 **log_shipping_secondary** 테이블의 설정을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-162">Secondary databases on the same secondary server for a given primary database share the settings in the **log_shipping_secondary** table.</span></span> <span data-ttu-id="3988e-163">하나의 보조 데이터베이스에 대한 공유 설정이 변경되면 모든 보조 데이터베이스에 대한 설정이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-163">If a shared setting is altered for one secondary database, the setting is altered for all of them.</span></span>  
  
## <a name="secondary-server-stored-procedures"></a><span data-ttu-id="3988e-164">보조 서버 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="3988e-164">Secondary Server Stored Procedures</span></span>  
  
|<span data-ttu-id="3988e-165">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="3988e-165">Stored Procedure</span></span>|<span data-ttu-id="3988e-166">Description</span><span class="sxs-lookup"><span data-stu-id="3988e-166">Description</span></span>|  
|----------------------|-----------------|  
|[<span data-ttu-id="3988e-167">sp_add_log_shipping_secondary_database</span><span class="sxs-lookup"><span data-stu-id="3988e-167">sp_add_log_shipping_secondary_database</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql)|<span data-ttu-id="3988e-168">로그 전달에 대한 보조 데이터베이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-168">Sets up a secondary database for log shipping.</span></span>|  
|[<span data-ttu-id="3988e-169">sp_add_log_shipping_secondary_primary</span><span class="sxs-lookup"><span data-stu-id="3988e-169">sp_add_log_shipping_secondary_primary</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql)|<span data-ttu-id="3988e-170">지정된 주 데이터베이스에 대한 보조 서버에서 주 정보를 설정하고, 로컬 및 원격 모니터 링크를 추가하며, 복사본을 만들고 작업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-170">Sets up the primary information, adds local and remote monitor links, and creates copy and restore jobs on the secondary server for the specified primary database.</span></span>|  
|[<span data-ttu-id="3988e-171">sp_change_log_shipping_secondary_database</span><span class="sxs-lookup"><span data-stu-id="3988e-171">sp_change_log_shipping_secondary_database</span></span>](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql)|<span data-ttu-id="3988e-172">로컬 및 원격 모니터 레코드를 포함하여 보조 데이터베이스 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-172">Changes secondary database settings including local and remote monitor records.</span></span>|  
|[<span data-ttu-id="3988e-173">sp_change_log_shipping_secondary_primary</span><span class="sxs-lookup"><span data-stu-id="3988e-173">sp_change_log_shipping_secondary_primary</span></span>](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-primary-transact-sql)|<span data-ttu-id="3988e-174">원본 및 대상 디렉터리와 파일 보존 기간 같은 보조 데이터베이스 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-174">Changes secondary database settings such as source and destination directory, and file retention period.</span></span>|  
|[<span data-ttu-id="3988e-175">sp_cleanup_log_shipping_history</span><span class="sxs-lookup"><span data-stu-id="3988e-175">sp_cleanup_log_shipping_history</span></span>](/sql/relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql)|<span data-ttu-id="3988e-176">보존 기간을 기준으로 로컬과 모니터에서 기록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-176">Cleans up history locally and on the monitor based on retention period.</span></span>|  
|[<span data-ttu-id="3988e-177">sp_delete_log_shipping_secondary_database</span><span class="sxs-lookup"><span data-stu-id="3988e-177">sp_delete_log_shipping_secondary_database</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql)|<span data-ttu-id="3988e-178">보조 데이터베이스, 로컬 기록 및 원격 기록을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-178">Removes a secondary database and the local history and remote history.</span></span>|  
|[<span data-ttu-id="3988e-179">sp_delete_log_shipping_secondary_primary</span><span class="sxs-lookup"><span data-stu-id="3988e-179">sp_delete_log_shipping_secondary_primary</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-primary-transact-sql)|<span data-ttu-id="3988e-180">보조 서버에서 지정한 주 서버에 대한 정보를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-180">Removes the information about the specified primary server from the secondary server.</span></span>|  
|[<span data-ttu-id="3988e-181">sp_help_log_shipping_secondary_database</span><span class="sxs-lookup"><span data-stu-id="3988e-181">sp_help_log_shipping_secondary_database</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql)|<span data-ttu-id="3988e-182">**log_shipping_secondary**, **log_shipping_secondary_databases**및 **log_shipping_monitor_secondary** 테이블에서 보조 데이터베이스 설정을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-182">Retrieves secondary database settings from the **log_shipping_secondary**, **log_shipping_secondary_databases**, and **log_shipping_monitor_secondary** tables.</span></span>|  
|[<span data-ttu-id="3988e-183">sp_help_log_shipping_secondary_primary</span><span class="sxs-lookup"><span data-stu-id="3988e-183">sp_help_log_shipping_secondary_primary</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-primary-transact-sql)|<span data-ttu-id="3988e-184">이 저장 프로시저는 보조 서버에서 지정된 주 데이터베이스의 설정을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-184">This stored procedure retrieves the settings for a given primary database on the secondary server.</span></span>|  
|[<span data-ttu-id="3988e-185">sp_refresh_log_shipping_monitor</span><span class="sxs-lookup"><span data-stu-id="3988e-185">sp_refresh_log_shipping_monitor</span></span>](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)|<span data-ttu-id="3988e-186">지정된 로그 전달 에이전트에 대한 최신 정보로 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-186">Refreshes the monitor with the latest information for the specified log shipping agent.</span></span>|  
  
## <a name="monitor-server-tables"></a><span data-ttu-id="3988e-187">모니터 서버 테이블</span><span class="sxs-lookup"><span data-stu-id="3988e-187">Monitor Server Tables</span></span>  
  
|<span data-ttu-id="3988e-188">테이블</span><span class="sxs-lookup"><span data-stu-id="3988e-188">Table</span></span>|<span data-ttu-id="3988e-189">Description</span><span class="sxs-lookup"><span data-stu-id="3988e-189">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3988e-190">log_shipping_monitor_alert</span><span class="sxs-lookup"><span data-stu-id="3988e-190">log_shipping_monitor_alert</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|<span data-ttu-id="3988e-191">경고 작업 ID를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-191">Stores alert job ID.</span></span>|  
|[<span data-ttu-id="3988e-192">log_shipping_monitor_error_detail</span><span class="sxs-lookup"><span data-stu-id="3988e-192">log_shipping_monitor_error_detail</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|<span data-ttu-id="3988e-193">로그 전달 작업에 대한 오류 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-193">Stores error detail for log shipping jobs.</span></span>|  
|[<span data-ttu-id="3988e-194">log_shipping_monitor_history_detail</span><span class="sxs-lookup"><span data-stu-id="3988e-194">log_shipping_monitor_history_detail</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|<span data-ttu-id="3988e-195">로그 전달 작업에 대한 기록 세부 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-195">Stores history detail for log shipping jobs.</span></span>|  
|[<span data-ttu-id="3988e-196">log_shipping_monitor_primary</span><span class="sxs-lookup"><span data-stu-id="3988e-196">log_shipping_monitor_primary</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)|<span data-ttu-id="3988e-197">이 모니터 서버와 관련된 주 데이터베이스마다 하나의 모니터 레코드를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-197">Stores one monitor record per primary database associated with this monitor server.</span></span>|  
|[<span data-ttu-id="3988e-198">log_shipping_monitor_secondary</span><span class="sxs-lookup"><span data-stu-id="3988e-198">log_shipping_monitor_secondary</span></span>](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)|<span data-ttu-id="3988e-199">이 모니터 서버와 관련된 보조 데이터베이스마다 하나의 모니터 레코드를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-199">Stores one monitor record per secondary database associated with this monitor server.</span></span>|  
  
## <a name="monitor-server-stored-procedures"></a><span data-ttu-id="3988e-200">모니터 서버 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="3988e-200">Monitor Server Stored Procedures</span></span>  
  
|<span data-ttu-id="3988e-201">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="3988e-201">Stored Procedure</span></span>|<span data-ttu-id="3988e-202">Description</span><span class="sxs-lookup"><span data-stu-id="3988e-202">Description</span></span>|  
|----------------------|-----------------|  
|[<span data-ttu-id="3988e-203">sp_add_log_shipping_alert_job</span><span class="sxs-lookup"><span data-stu-id="3988e-203">sp_add_log_shipping_alert_job</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql)|<span data-ttu-id="3988e-204">로그 전달 경고 작업이 아직 생성되지 않았으면 하나를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-204">Creates a log shipping alert job if one has not already been created.</span></span>|  
|[<span data-ttu-id="3988e-205">sp_delete_log_shipping_alert_job</span><span class="sxs-lookup"><span data-stu-id="3988e-205">sp_delete_log_shipping_alert_job</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-alert-job-transact-sql)|<span data-ttu-id="3988e-206">관련된 주 데이터베이스가 없으면 로그 전달 경고 작업을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-206">Removes a log shipping alert job if there are no associated primary databases.</span></span>|  
|[<span data-ttu-id="3988e-207">sp_help_log_shipping_alert_job</span><span class="sxs-lookup"><span data-stu-id="3988e-207">sp_help_log_shipping_alert_job</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-alert-job-transact-sql)|<span data-ttu-id="3988e-208">경고 작업의 작업 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-208">Returns the job ID of the alert job.</span></span>|  
|[<span data-ttu-id="3988e-209">sp_help_log_shipping_monitor_primary</span><span class="sxs-lookup"><span data-stu-id="3988e-209">sp_help_log_shipping_monitor_primary</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql)|<span data-ttu-id="3988e-210">**log_shipping_monitor_primary** 테이블에서 지정한 주 데이터베이스에 대한 모니터 레코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-210">Returns monitor records for the specified primary database from the **log_shipping_monitor_primary** table.</span></span>|  
|[<span data-ttu-id="3988e-211">sp_help_log_shipping_monitor_secondary</span><span class="sxs-lookup"><span data-stu-id="3988e-211">sp_help_log_shipping_monitor_secondary</span></span>](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql)|<span data-ttu-id="3988e-212">**log_shipping_monitor_secondary** 테이블에서 지정한 보조 데이터베이스에 대한 모니터 레코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3988e-212">Returns monitor records for the specified secondary database from the **log_shipping_monitor_secondary** table.</span></span>|  
  
  