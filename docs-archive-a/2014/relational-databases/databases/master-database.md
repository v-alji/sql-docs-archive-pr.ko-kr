---
title: master 데이터베이스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], about
- master database [SQL Server]
ms.assetid: 660e909f-61eb-406b-bbce-8864dd629ba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac38453237ed6816c32ed974e8141c57c93ceb44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742167"
---
# <a name="master-database"></a><span data-ttu-id="9b1e7-102">master 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="9b1e7-102">master Database</span></span>
  <span data-ttu-id="9b1e7-103">**master** 데이터베이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템에 대한 모든 시스템 수준 정보를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-103">The **master** database records all the system-level information for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system.</span></span> <span data-ttu-id="9b1e7-104">이 정보에는 로그온 계정, 엔드포인트, 연결된 서버 및 시스템 구성 설정 등 인스턴스 차원의 메타데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-104">This includes instance-wide metadata such as logon accounts, endpoints, linked servers, and system configuration settings.</span></span> <span data-ttu-id="9b1e7-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 시스템 개체가 **master** 데이터베이스에 저장되지 않고 [리소스 데이터베이스](resource-database.md)에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-105">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], system objects are no longer stored in the **master** database; instead, they are stored in the [Resource database](resource-database.md).</span></span> <span data-ttu-id="9b1e7-106">**master** 는 다른 모든 데이터베이스의 존재 여부와 해당 데이터베이스 파일의 위치를 기록하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대한 초기화 정보를 기록하는 데이터베이스이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-106">Also, **master** is the database that records the existence of all other databases and the location of those database files and records the initialization information for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9b1e7-107">따라서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] master **데이터베이스를 사용할 수 없는 경우에는** 를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-107">Therefore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot start if the **master** database is unavailable.</span></span>  
  
## <a name="physical-properties-of-master"></a><span data-ttu-id="9b1e7-108">master의 물리적 속성</span><span class="sxs-lookup"><span data-stu-id="9b1e7-108">Physical Properties of master</span></span>  
 <span data-ttu-id="9b1e7-109">다음 표에서는 **master** 데이터와 로그 파일의 초기 구성 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-109">The following table lists the initial configuration values of the **master** data and log files.</span></span> <span data-ttu-id="9b1e7-110">이러한 파일의 크기는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에 따라 조금씩 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-110">The sizes of these files may vary slightly for different editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="9b1e7-111">파일</span><span class="sxs-lookup"><span data-stu-id="9b1e7-111">File</span></span>|<span data-ttu-id="9b1e7-112">논리적 이름</span><span class="sxs-lookup"><span data-stu-id="9b1e7-112">Logical name</span></span>|<span data-ttu-id="9b1e7-113">물리적 이름</span><span class="sxs-lookup"><span data-stu-id="9b1e7-113">Physical name</span></span>|<span data-ttu-id="9b1e7-114">파일 증가</span><span class="sxs-lookup"><span data-stu-id="9b1e7-114">File growth</span></span>|  
|----------|------------------|-------------------|-----------------|  
|<span data-ttu-id="9b1e7-115">주 데이터</span><span class="sxs-lookup"><span data-stu-id="9b1e7-115">Primary data</span></span>|<span data-ttu-id="9b1e7-116">master</span><span class="sxs-lookup"><span data-stu-id="9b1e7-116">master</span></span>|<span data-ttu-id="9b1e7-117">master.mdf</span><span class="sxs-lookup"><span data-stu-id="9b1e7-117">master.mdf</span></span>|<span data-ttu-id="9b1e7-118">디스크가 꽉 찰 때까지 10%씩 자동 증가</span><span class="sxs-lookup"><span data-stu-id="9b1e7-118">Autogrow by 10 percent until the disk is full.</span></span>|  
|<span data-ttu-id="9b1e7-119">로그</span><span class="sxs-lookup"><span data-stu-id="9b1e7-119">Log</span></span>|<span data-ttu-id="9b1e7-120">mastlog</span><span class="sxs-lookup"><span data-stu-id="9b1e7-120">mastlog</span></span>|<span data-ttu-id="9b1e7-121">mastlog.ldf</span><span class="sxs-lookup"><span data-stu-id="9b1e7-121">mastlog.ldf</span></span>|<span data-ttu-id="9b1e7-122">최대 2TB까지 10%씩 자동 증가</span><span class="sxs-lookup"><span data-stu-id="9b1e7-122">Autogrow by 10 percent to a maximum of 2 terabytes.</span></span>|  
  
 <span data-ttu-id="9b1e7-123">**master** 데이터 및 로그 파일의 이동 방법은 [시스템 데이터베이스 이동](system-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-123">For information about how to move the **master** data and log files, see [Move System Databases](system-databases.md).</span></span>  
  
### <a name="database-options"></a><span data-ttu-id="9b1e7-124">데이터베이스 옵션</span><span class="sxs-lookup"><span data-stu-id="9b1e7-124">Database Options</span></span>  
 <span data-ttu-id="9b1e7-125">다음 표에서는 **master** 데이터베이스의 각 옵션에 대한 기본값과 수정 가능 여부를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-125">The following table lists the default value for each database option in the **master** database and whether the option can be modified.</span></span> <span data-ttu-id="9b1e7-126">이러한 옵션의 현재 설정을 보려면 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 카탈로그 뷰를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-126">To view the current settings for these options, use the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
|<span data-ttu-id="9b1e7-127">데이터베이스 옵션</span><span class="sxs-lookup"><span data-stu-id="9b1e7-127">Database option</span></span>|<span data-ttu-id="9b1e7-128">기본값</span><span class="sxs-lookup"><span data-stu-id="9b1e7-128">Default value</span></span>|<span data-ttu-id="9b1e7-129">수정 가능</span><span class="sxs-lookup"><span data-stu-id="9b1e7-129">Can be modified</span></span>|  
|---------------------|-------------------|---------------------|  
|<span data-ttu-id="9b1e7-130">ALLOW_SNAPSHOT_ISOLATION</span><span class="sxs-lookup"><span data-stu-id="9b1e7-130">ALLOW_SNAPSHOT_ISOLATION</span></span>|<span data-ttu-id="9b1e7-131">켜기</span><span class="sxs-lookup"><span data-stu-id="9b1e7-131">ON</span></span>|<span data-ttu-id="9b1e7-132">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-132">No</span></span>|  
|<span data-ttu-id="9b1e7-133">ANSI_NULL_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9b1e7-133">ANSI_NULL_DEFAULT</span></span>|<span data-ttu-id="9b1e7-134">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-134">OFF</span></span>|<span data-ttu-id="9b1e7-135">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-135">Yes</span></span>|  
|<span data-ttu-id="9b1e7-136">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="9b1e7-136">ANSI_NULLS</span></span>|<span data-ttu-id="9b1e7-137">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-137">OFF</span></span>|<span data-ttu-id="9b1e7-138">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-138">Yes</span></span>|  
|<span data-ttu-id="9b1e7-139">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="9b1e7-139">ANSI_PADDING</span></span>|<span data-ttu-id="9b1e7-140">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-140">OFF</span></span>|<span data-ttu-id="9b1e7-141">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-141">Yes</span></span>|  
|<span data-ttu-id="9b1e7-142">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="9b1e7-142">ANSI_WARNINGS</span></span>|<span data-ttu-id="9b1e7-143">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-143">OFF</span></span>|<span data-ttu-id="9b1e7-144">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-144">Yes</span></span>|  
|<span data-ttu-id="9b1e7-145">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="9b1e7-145">ARITHABORT</span></span>|<span data-ttu-id="9b1e7-146">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-146">OFF</span></span>|<span data-ttu-id="9b1e7-147">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-147">Yes</span></span>|  
|<span data-ttu-id="9b1e7-148">AUTO_CLOSE</span><span class="sxs-lookup"><span data-stu-id="9b1e7-148">AUTO_CLOSE</span></span>|<span data-ttu-id="9b1e7-149">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-149">OFF</span></span>|<span data-ttu-id="9b1e7-150">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-150">No</span></span>|  
|<span data-ttu-id="9b1e7-151">AUTO_CREATE_STATISTICS</span><span class="sxs-lookup"><span data-stu-id="9b1e7-151">AUTO_CREATE_STATISTICS</span></span>|<span data-ttu-id="9b1e7-152">켜기</span><span class="sxs-lookup"><span data-stu-id="9b1e7-152">ON</span></span>|<span data-ttu-id="9b1e7-153">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-153">Yes</span></span>|  
|<span data-ttu-id="9b1e7-154">AUTO_SHRINK</span><span class="sxs-lookup"><span data-stu-id="9b1e7-154">AUTO_SHRINK</span></span>|<span data-ttu-id="9b1e7-155">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-155">OFF</span></span>|<span data-ttu-id="9b1e7-156">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-156">No</span></span>|  
|<span data-ttu-id="9b1e7-157">AUTO_UPDATE_STATISTICS</span><span class="sxs-lookup"><span data-stu-id="9b1e7-157">AUTO_UPDATE_STATISTICS</span></span>|<span data-ttu-id="9b1e7-158">켜기</span><span class="sxs-lookup"><span data-stu-id="9b1e7-158">ON</span></span>|<span data-ttu-id="9b1e7-159">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-159">Yes</span></span>|  
|<span data-ttu-id="9b1e7-160">AUTO_UPDATE_STATISTICS_ASYNC</span><span class="sxs-lookup"><span data-stu-id="9b1e7-160">AUTO_UPDATE_STATISTICS_ASYNC</span></span>|<span data-ttu-id="9b1e7-161">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-161">OFF</span></span>|<span data-ttu-id="9b1e7-162">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-162">Yes</span></span>|  
|<span data-ttu-id="9b1e7-163">CHANGE_TRACKING</span><span class="sxs-lookup"><span data-stu-id="9b1e7-163">CHANGE_TRACKING</span></span>|<span data-ttu-id="9b1e7-164">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-164">OFF</span></span>|<span data-ttu-id="9b1e7-165">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-165">No</span></span>|  
|<span data-ttu-id="9b1e7-166">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="9b1e7-166">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="9b1e7-167">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-167">OFF</span></span>|<span data-ttu-id="9b1e7-168">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-168">Yes</span></span>|  
|<span data-ttu-id="9b1e7-169">CURSOR_CLOSE_ON_COMMIT</span><span class="sxs-lookup"><span data-stu-id="9b1e7-169">CURSOR_CLOSE_ON_COMMIT</span></span>|<span data-ttu-id="9b1e7-170">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-170">OFF</span></span>|<span data-ttu-id="9b1e7-171">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-171">Yes</span></span>|  
|<span data-ttu-id="9b1e7-172">CURSOR_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="9b1e7-172">CURSOR_DEFAULT</span></span>|<span data-ttu-id="9b1e7-173">GLOBAL</span><span class="sxs-lookup"><span data-stu-id="9b1e7-173">GLOBAL</span></span>|<span data-ttu-id="9b1e7-174">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-174">Yes</span></span>|  
|<span data-ttu-id="9b1e7-175">데이터베이스 가용성 옵션</span><span class="sxs-lookup"><span data-stu-id="9b1e7-175">Database Availability Options</span></span>|<span data-ttu-id="9b1e7-176">ONLINE</span><span class="sxs-lookup"><span data-stu-id="9b1e7-176">ONLINE</span></span><br /><br /> <span data-ttu-id="9b1e7-177">MULTI_USER</span><span class="sxs-lookup"><span data-stu-id="9b1e7-177">MULTI_USER</span></span><br /><br /> <span data-ttu-id="9b1e7-178">READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="9b1e7-178">READ_WRITE</span></span>|<span data-ttu-id="9b1e7-179">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-179">No</span></span><br /><br /> <span data-ttu-id="9b1e7-180">아니요</span><span class="sxs-lookup"><span data-stu-id="9b1e7-180">No</span></span><br /><br /> <span data-ttu-id="9b1e7-181">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-181">No</span></span>|  
|<span data-ttu-id="9b1e7-182">DATE_CORRELATION_OPTIMIZATION</span><span class="sxs-lookup"><span data-stu-id="9b1e7-182">DATE_CORRELATION_OPTIMIZATION</span></span>|<span data-ttu-id="9b1e7-183">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-183">OFF</span></span>|<span data-ttu-id="9b1e7-184">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-184">Yes</span></span>|  
|<span data-ttu-id="9b1e7-185">DB_CHAINING</span><span class="sxs-lookup"><span data-stu-id="9b1e7-185">DB_CHAINING</span></span>|<span data-ttu-id="9b1e7-186">켜기</span><span class="sxs-lookup"><span data-stu-id="9b1e7-186">ON</span></span>|<span data-ttu-id="9b1e7-187">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-187">No</span></span>|  
|<span data-ttu-id="9b1e7-188">ENCRYPTION</span><span class="sxs-lookup"><span data-stu-id="9b1e7-188">ENCRYPTION</span></span>|<span data-ttu-id="9b1e7-189">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-189">OFF</span></span>|<span data-ttu-id="9b1e7-190">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-190">No</span></span>|  
|<span data-ttu-id="9b1e7-191">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="9b1e7-191">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="9b1e7-192">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-192">OFF</span></span>|<span data-ttu-id="9b1e7-193">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-193">Yes</span></span>|  
|<span data-ttu-id="9b1e7-194">PAGE_VERIFY</span><span class="sxs-lookup"><span data-stu-id="9b1e7-194">PAGE_VERIFY</span></span>|<span data-ttu-id="9b1e7-195">CHECKSUM</span><span class="sxs-lookup"><span data-stu-id="9b1e7-195">CHECKSUM</span></span>|<span data-ttu-id="9b1e7-196">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-196">Yes</span></span>|  
|<span data-ttu-id="9b1e7-197">PARAMETERIZATION</span><span class="sxs-lookup"><span data-stu-id="9b1e7-197">PARAMETERIZATION</span></span>|<span data-ttu-id="9b1e7-198">SIMPLE</span><span class="sxs-lookup"><span data-stu-id="9b1e7-198">SIMPLE</span></span>|<span data-ttu-id="9b1e7-199">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-199">Yes</span></span>|  
|<span data-ttu-id="9b1e7-200">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="9b1e7-200">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="9b1e7-201">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-201">OFF</span></span>|<span data-ttu-id="9b1e7-202">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-202">Yes</span></span>|  
|<span data-ttu-id="9b1e7-203">READ_COMMITTED_SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="9b1e7-203">READ_COMMITTED_SNAPSHOT</span></span>|<span data-ttu-id="9b1e7-204">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-204">OFF</span></span>|<span data-ttu-id="9b1e7-205">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-205">No</span></span>|  
|<span data-ttu-id="9b1e7-206">RECOVERY</span><span class="sxs-lookup"><span data-stu-id="9b1e7-206">RECOVERY</span></span>|<span data-ttu-id="9b1e7-207">SIMPLE</span><span class="sxs-lookup"><span data-stu-id="9b1e7-207">SIMPLE</span></span>|<span data-ttu-id="9b1e7-208">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-208">Yes</span></span>|  
|<span data-ttu-id="9b1e7-209">RECURSIVE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="9b1e7-209">RECURSIVE_TRIGGERS</span></span>|<span data-ttu-id="9b1e7-210">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-210">OFF</span></span>|<span data-ttu-id="9b1e7-211">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-211">Yes</span></span>|  
|<span data-ttu-id="9b1e7-212">Service Broker 옵션</span><span class="sxs-lookup"><span data-stu-id="9b1e7-212">Service Broker Options</span></span>|<span data-ttu-id="9b1e7-213">DISABLE_BROKER</span><span class="sxs-lookup"><span data-stu-id="9b1e7-213">DISABLE_BROKER</span></span>|<span data-ttu-id="9b1e7-214">아니요</span><span class="sxs-lookup"><span data-stu-id="9b1e7-214">No</span></span>|  
|<span data-ttu-id="9b1e7-215">TRUSTWORTHY</span><span class="sxs-lookup"><span data-stu-id="9b1e7-215">TRUSTWORTHY</span></span>|<span data-ttu-id="9b1e7-216">OFF</span><span class="sxs-lookup"><span data-stu-id="9b1e7-216">OFF</span></span>|<span data-ttu-id="9b1e7-217">예</span><span class="sxs-lookup"><span data-stu-id="9b1e7-217">Yes</span></span>|  
  
 <span data-ttu-id="9b1e7-218">이러한 데이터베이스 옵션에 대한 자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-218">For a description of these database options, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="9b1e7-219">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9b1e7-219">Restrictions</span></span>  
 <span data-ttu-id="9b1e7-220">**master** 데이터베이스에서는 다음 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-220">The following operations cannot be performed on the **master** database:</span></span>  
  
-   <span data-ttu-id="9b1e7-221">파일이나 파일 그룹 추가</span><span class="sxs-lookup"><span data-stu-id="9b1e7-221">Adding files or filegroups.</span></span>  
  
-   <span data-ttu-id="9b1e7-222">데이터 정렬 변경.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-222">Changing collation.</span></span> <span data-ttu-id="9b1e7-223">기본 데이터 정렬은 서버 데이터 정렬입니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-223">The default collation is the server collation.</span></span>  
  
-   <span data-ttu-id="9b1e7-224">데이터베이스 소유자 변경.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-224">Changing the database owner.</span></span> <span data-ttu-id="9b1e7-225">**master** 는 **sa**가 소유합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-225">**master** is owned by **sa**.</span></span>  
  
-   <span data-ttu-id="9b1e7-226">전체 텍스트 카탈로그 또는 전체 텍스트 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="9b1e7-226">Creating a full-text catalog or full-text index.</span></span>  
  
-   <span data-ttu-id="9b1e7-227">데이터베이스의 시스템 테이블에 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="9b1e7-227">Creating triggers on system tables in the database.</span></span>  
  
-   <span data-ttu-id="9b1e7-228">데이터베이스 삭제</span><span class="sxs-lookup"><span data-stu-id="9b1e7-228">Dropping the database.</span></span>  
  
-   <span data-ttu-id="9b1e7-229">데이터베이스에서 **게스트** 사용자를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-229">Dropping the **guest** user from the database.</span></span>  
  
-   <span data-ttu-id="9b1e7-230">변경 데이터 캡처 설정</span><span class="sxs-lookup"><span data-stu-id="9b1e7-230">Enabling change data capture.</span></span>  
  
-   <span data-ttu-id="9b1e7-231">데이터베이스 미러링 참여</span><span class="sxs-lookup"><span data-stu-id="9b1e7-231">Participating in database mirroring.</span></span>  
  
-   <span data-ttu-id="9b1e7-232">주 파일 그룹, 주 데이터 파일 또는 로그 파일 제거</span><span class="sxs-lookup"><span data-stu-id="9b1e7-232">Removing the primary filegroup, primary data file, or log file.</span></span>  
  
-   <span data-ttu-id="9b1e7-233">데이터베이스 또는 주 파일 그룹 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="9b1e7-233">Renaming the database or primary filegroup.</span></span>  
  
-   <span data-ttu-id="9b1e7-234">데이터베이스를 OFFLINE으로 설정</span><span class="sxs-lookup"><span data-stu-id="9b1e7-234">Setting the database to OFFLINE.</span></span>  
  
-   <span data-ttu-id="9b1e7-235">데이터베이스나 주 파일 그룹을 READ_ONLY로 설정</span><span class="sxs-lookup"><span data-stu-id="9b1e7-235">Setting the database or primary filegroup to READ_ONLY.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="9b1e7-236">권장 사항</span><span class="sxs-lookup"><span data-stu-id="9b1e7-236">Recommendations</span></span>  
 <span data-ttu-id="9b1e7-237">다음은 **master** 데이터베이스로 작업을 수행할 때 고려해야 할 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-237">When you work with the **master** database, consider the following recommendations:</span></span>  
  
-   <span data-ttu-id="9b1e7-238">언제든지 사용할 수 있도록 **master** 데이터베이스의 최신 백업을 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-238">Always have a current backup of the **master** database available.</span></span>  
  
-   <span data-ttu-id="9b1e7-239">다음 작업을 수행한 후에는 가능한 빨리 **master** 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-239">Back up the **master** database as soon as possible after the following operations:</span></span>  
  
    -   <span data-ttu-id="9b1e7-240">데이터베이스 만들기, 수정 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="9b1e7-240">Creating, modifying, or dropping any database</span></span>  
  
    -   <span data-ttu-id="9b1e7-241">서버 또는 데이터베이스 구성 값 변경</span><span class="sxs-lookup"><span data-stu-id="9b1e7-241">Changing server or database configuration values</span></span>  
  
    -   <span data-ttu-id="9b1e7-242">로그온 계정 수정 또는 추가</span><span class="sxs-lookup"><span data-stu-id="9b1e7-242">Modifying or adding logon accounts</span></span>  
  
-   <span data-ttu-id="9b1e7-243">**master**에는 사용자 개체를 만들지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-243">Do not create user objects in **master**.</span></span> <span data-ttu-id="9b1e7-244">사용자 개체를 만든 경우에는 **master** 를 더 자주 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-244">If you do, **master** must be backed up more frequently.</span></span>  
  
-   <span data-ttu-id="9b1e7-245">**master** 데이터베이스의 TRUSTWORTHY 옵션을 ON으로 설정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-245">Do not set the TRUSTWORTHY option to ON for the **master** database.</span></span>  
  
## <a name="what-to-do-if-master-becomes-unusable"></a><span data-ttu-id="9b1e7-246">master를 사용할 수 없게 된 경우 수행할 작업</span><span class="sxs-lookup"><span data-stu-id="9b1e7-246">What to Do If master Becomes Unusable</span></span>  
 <span data-ttu-id="9b1e7-247">**master** 를 사용할 수 없게 된 경우 다음 방법 중 하나로 데이터베이스를 사용 가능한 상태로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-247">If **master** becomes unusable, you can return the database to a usable state in either of the following ways:</span></span>  
  
-   <span data-ttu-id="9b1e7-248">현재 데이터베이스 백업에서 **master** 를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-248">Restore **master** from a current database backup.</span></span>  
  
     <span data-ttu-id="9b1e7-249">서버 인스턴스를 시작할 수 있으면 전체 데이터베이스 백업에서 **master** 를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-249">If you can start the server instance, you should be able to restore **master** from a full database backup.</span></span> <span data-ttu-id="9b1e7-250">자세한 내용은 [master 데이터베이스 복원&#40;Transact-SQL&#41;](../backup-restore/restore-the-master-database-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-250">For more information, see [Restore the master Database &#40;Transact-SQL&#41;](../backup-restore/restore-the-master-database-transact-sql.md).</span></span>  
  
-   <span data-ttu-id="9b1e7-251">**master** 를 완전히 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-251">Rebuild **master** completely.</span></span>  
  
     <span data-ttu-id="9b1e7-252">**master** 에 발생한 심각한 손상으로 인해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 시작할 수 없는 경우에는 **master**를 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-252">If severe damage to **master** prevents you from starting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must rebuild **master**.</span></span> <span data-ttu-id="9b1e7-253">자세한 내용은 [시스템 데이터베이스 다시 작성](rebuild-system-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-253">For more information, see [Rebuild System Databases](rebuild-system-databases.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9b1e7-254">**master** 를 다시 작성하면 모든 시스템 데이터베이스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b1e7-254">Rebuilding **master** rebuilds all of the system databases.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="9b1e7-255">관련 내용</span><span class="sxs-lookup"><span data-stu-id="9b1e7-255">Related Content</span></span>  
 [<span data-ttu-id="9b1e7-256">시스템 데이터베이스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="9b1e7-256">Rebuild System Databases</span></span>](rebuild-system-databases.md)  
  
 [<span data-ttu-id="9b1e7-257">시스템 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="9b1e7-257">System Databases</span></span>](system-databases.md)  
  
 [<span data-ttu-id="9b1e7-258">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9b1e7-258">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [<span data-ttu-id="9b1e7-259">sys.master_files&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9b1e7-259">sys.master_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [<span data-ttu-id="9b1e7-260">데이터베이스 파일 이동</span><span class="sxs-lookup"><span data-stu-id="9b1e7-260">Move Database Files</span></span>](move-database-files.md)  
  
  
