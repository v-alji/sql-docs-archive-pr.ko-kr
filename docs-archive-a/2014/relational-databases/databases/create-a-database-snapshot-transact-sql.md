---
title: 데이터베이스 스냅샷 만들기(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], creating
ms.assetid: 187fbba3-c555-4030-9bdf-0f01994c5230
author: stevestein
ms.author: sstein
ms.openlocfilehash: bae68c2d507e1dd3809e76a9d842b765d72234e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742224"
---
# <a name="create-a-database-snapshot-transact-sql"></a><span data-ttu-id="fb669-102">Create a Database Snapshot (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fb669-102">Create a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="fb669-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 스냅샷은 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용해서만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-103">The only way to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshot is to use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="fb669-104">는 데이터베이스 스냅샷 만들기를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-104">does not support the creation of database snapshots.</span></span>  
  
-   <span data-ttu-id="fb669-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="fb669-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fb669-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="fb669-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="fb669-107">보안</span><span class="sxs-lookup"><span data-stu-id="fb669-107">Security</span></span>](#Security)  
  
     [<span data-ttu-id="fb669-108">최선의 구현 방법: 데이터베이스 스냅샷 명명</span><span class="sxs-lookup"><span data-stu-id="fb669-108">Best Practice: Naming Database Snapshots</span></span>](#Naming)  
  
-   <span data-ttu-id="fb669-109">**데이터베이스 스냅숏을 만들려면: transact-sql을 사용 합니다.**[Transact-SQL](#TsqlProcedure)  </span><span class="sxs-lookup"><span data-stu-id="fb669-109">**To create a database snapshot, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fb669-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fb669-110">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="fb669-111">필수 조건</span><span class="sxs-lookup"><span data-stu-id="fb669-111">Prerequisites</span></span>  
 <span data-ttu-id="fb669-112">복구 모델을 사용할 수 있는 원본 데이터베이스는 다음 사전 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-112">The source database, which can use any recovery model, must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="fb669-113">서버 인스턴스는 데이터베이스 스냅샷을 지원하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-113">The server instance must be running an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports database snapshot.</span></span> <span data-ttu-id="fb669-114">의 데이터베이스 스냅숏 지원에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fb669-114">For information about support for database snapshots in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="fb669-115">데이터베이스 미러링 세션의 미러 데이터베이스가 아닌 경우 원본 데이터베이스는 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-115">The source database must be online, unless the database is a mirror database within a database mirroring session.</span></span>  
  
-   <span data-ttu-id="fb669-116">미러 데이터베이스에서 데이터베이스 스냅샷을 만들려면 데이터베이스가 동기화된[미러링 상태](../../database-engine/database-mirroring/mirroring-states-sql-server.md)여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-116">To create a database snapshot on a mirror database, the database must be in the synchronized[mirroring state](../../database-engine/database-mirroring/mirroring-states-sql-server.md).</span></span>  
  
-   <span data-ttu-id="fb669-117">원본 데이터베이스는 확장 가능한 공유 데이터베이스로 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-117">The source database cannot be configured as a scalable shared database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fb669-118">다른 주요 고려 사항에 대한 자세한 내용은 [데이터베이스 스냅샷&#40;SQL Server&#41;](database-snapshots-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb669-118">For information about other significant considerations, see [Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="fb669-119">권장 사항</span><span class="sxs-lookup"><span data-stu-id="fb669-119">Recommendations</span></span>  
 <span data-ttu-id="fb669-120">이 섹션에서는 다음과 같은 최상의 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-120">This section discusses the following best practices:</span></span>  
  
-   [<span data-ttu-id="fb669-121">최선의 구현 방법: 데이터베이스 스냅샷 명명</span><span class="sxs-lookup"><span data-stu-id="fb669-121">Best Practice: Naming Database Snapshots</span></span>](#Naming)  
  
-   [<span data-ttu-id="fb669-122">최선의 구현 방법: 데이터베이스 스냅샷 수 제한</span><span class="sxs-lookup"><span data-stu-id="fb669-122">Best Practice: Limiting the Number of Database Snapshots</span></span>](#Limiting_Number)  
  
-   [<span data-ttu-id="fb669-123">최선의 구현 방법: 데이터베이스 스냅샷에 대한 클라이언트 연결</span><span class="sxs-lookup"><span data-stu-id="fb669-123">Best Practice: Client Connections to a Database Snapshot</span></span>](#Client_Connections)  
  
####  <a name="best-practice-naming-database-snapshots"></a><a name="Naming"></a> <span data-ttu-id="fb669-124">최선의 구현 방법: 데이터베이스 스냅샷 명명</span><span class="sxs-lookup"><span data-stu-id="fb669-124">Best Practice: Naming Database Snapshots</span></span>  
 <span data-ttu-id="fb669-125">스냅샷의 이름은 중요하므로 스냅샷을 만들기 전에 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-125">Before creating snapshots, it is important to consider how to name them.</span></span> <span data-ttu-id="fb669-126">각 데이터베이스 스냅샷에는 고유한 데이터베이스 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-126">Each database snapshot requires a unique database name.</span></span> <span data-ttu-id="fb669-127">쉬운 관리를 위해 데이터베이스를 식별하는 다음과 같은 정보를 스냅샷 이름에 첨가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-127">For administrative ease, the name of a snapshot can incorporate information that identifies the database, such as:</span></span>  
  
-   <span data-ttu-id="fb669-128">원본 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-128">The name of the source database.</span></span>  
  
-   <span data-ttu-id="fb669-129">스냅샷 이름임을 나타내는 부분</span><span class="sxs-lookup"><span data-stu-id="fb669-129">An indication that the new name is for a snapshot.</span></span>  
  
-   <span data-ttu-id="fb669-130">스냅샷을 만든 날짜 및 시간, 시퀀스 번호, 자정 이후의 시간 등 지정된 데이터베이스에 대한 스냅샷 순서를 구분하기 위한 정보</span><span class="sxs-lookup"><span data-stu-id="fb669-130">The creation date and time of the snapshot, a sequence number, or some other information, such as time of day, to distinguish sequential snapshots on a given database.</span></span>  
  
 <span data-ttu-id="fb669-131">예를 들어 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에 대한 일련의 스냅샷을 만든다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-131">For example, consider a series of snapshots for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="fb669-132">24시간 표기법을 기준으로 오전 6시와 오후 6시 사이에 6시간 간격으로</span><span class="sxs-lookup"><span data-stu-id="fb669-132">Three daily snapshots are created at 6-hour intervals between 6 A.M.</span></span> <span data-ttu-id="fb669-133">세 개의 일일 스냅숏을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-133">and 6 P.M., based on a 24-hour clock.</span></span> <span data-ttu-id="fb669-134">각 일일 스냅샷은 삭제 전 24시간 동안 보존되며 이후에 같은 이름의 새 스냅샷으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-134">Each daily snapshot is kept for 24 hours before being dropped and replaced by a new snapshot of the same name.</span></span> <span data-ttu-id="fb669-135">각 스냅샷 이름은 날짜가 아닌 시간만 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-135">Note that each snapshot name indicates the hour, but not the day:</span></span>  
  
```  
AdventureWorks_snapshot_0600  
AdventureWorks_snapshot_1200  
AdventureWorks_snapshot_1800  
```  
  
 <span data-ttu-id="fb669-136">이러한 일일 스냅샷을 만드는 시간이 일정하지 않을 경우 보다 덜 정확한 명명 규칙을 사용하는 것이 좋습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-136">Alternatively, if the creation time of these daily snapshots varies from day to day, a less precise naming convention might be preferable, for example:</span></span>  
  
```  
AdventureWorks_snapshot_morning  
AdventureWorks_snapshot_noon  
AdventureWorks_snapshot_evening  
```  
  
####  <a name="best-practice-limiting-the-number-of-database-snapshots"></a><a name="Limiting_Number"></a> <span data-ttu-id="fb669-137">최선의 구현 방법: 데이터베이스 스냅샷 수 제한</span><span class="sxs-lookup"><span data-stu-id="fb669-137">Best Practice: Limiting the Number of Database Snapshots</span></span>  
 <span data-ttu-id="fb669-138">원본 데이터베이스의 순차적 스냅샷을 캡처하기 위해 일정 기간 동안 일련의 스냅샷을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-138">Creating a series of snapshots over time captures sequential snapshots of the source database.</span></span> <span data-ttu-id="fb669-139">각 스냅샷은 명시적으로 삭제할 때까지 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-139">Each snapshot persists until it is explicitly dropped.</span></span> <span data-ttu-id="fb669-140">원본 페이지를 업데이트함에 따라 각 스냅샷의 크기도 증가하므로 새 스냅샷을 만든 후에는 디스크 공간 유지를 위해 기존의 스냅샷을 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-140">Because each snapshot will continue to grow as original pages are updated, you may want to conserve disk space by deleting an older snapshot after creating a new snapshot.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb669-141">데이터베이스 스냅샷으로 되돌리기 위해서는 해당 데이터베이스의 다른 스냅샷을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-141">If you want to revert to a database snapshot, you need to delete any other snapshots from that database.</span></span>  
  
####  <a name="best-practice-client-connections-to-a-database-snapshot"></a><a name="Client_Connections"></a> <span data-ttu-id="fb669-142">최선의 구현 방법: 데이터베이스 스냅샷에 대한 클라이언트 연결</span><span class="sxs-lookup"><span data-stu-id="fb669-142">Best Practice: Client Connections to a Database Snapshot</span></span>  
 <span data-ttu-id="fb669-143">클라이언트가 데이터베이스 스냅샷을 사용하려면 그 위치를 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-143">To use a database snapshot, clients need to know where to find it.</span></span> <span data-ttu-id="fb669-144">사용자가 데이터베이스 스냅샷을 읽는 동안 다른 스냅샷이 생성되거나 삭제될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-144">Users can read from one database snapshot while another is being created or deleted.</span></span> <span data-ttu-id="fb669-145">따라서 기존의 스냅샷을 새 스냅샷으로 대체하면 클라이언트를 새 스냅샷으로 리디렉션해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-145">However, when you substitute a new snapshot for an existing one, you need to redirect clients to the new snapshot.</span></span> <span data-ttu-id="fb669-146">사용자는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 이용해 수동으로 데이터베이스 스냅샷에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-146">Users can manually connect to a database snapshot by means of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="fb669-147">하지만 프로덕션 환경을 지원하려면 보고 및 작성 클라이언트를 자동으로 데이터베이스의 최신 데이터베이스 스냅샷으로 리디렉션하는 프로그래밍 솔루션을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-147">However, to support a production environment, you should create a programmatic solution that transparently directs report-writing clients to the latest database snapshot of the database.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fb669-148">보안</span><span class="sxs-lookup"><span data-stu-id="fb669-148">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fb669-149">권한</span><span class="sxs-lookup"><span data-stu-id="fb669-149">Permissions</span></span>  
 <span data-ttu-id="fb669-150">데이터베이스를 만들 수 있는 모든 사용자는 데이터베이스 스냅샷을 만들 수 있습니다. 그러나 미러 데이터베이스의 스냅샷을 만들려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-150">Any user who can create a database can create a database snapshot; however, to create a snapshot of a mirror database, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="how-to-create-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fb669-151">데이터베이스 스냅샷을 만드는 방법(Transact-SQL 사용)</span><span class="sxs-lookup"><span data-stu-id="fb669-151">How to Create a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="fb669-152">**데이터베이스 스냅샷을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="fb669-152">**To create a database snapshot**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb669-153">이 프로시저의 예는 이 섹션의 뒷부분에 나오는 [예제(Transact-SQL)](#TsqlExample)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb669-153">For an example of this procedure, see [Examples (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="fb669-154">원본 데이터베이스의 현재 크기를 기준으로 데이터베이스 스냅샷을 저장할 수 있는 충분한 디스크 공간이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-154">Based on the current size of the source database, ensure that you have sufficient disk space to hold the database snapshot.</span></span> <span data-ttu-id="fb669-155">데이터베이스 스냅샷의 최대 크기는 스냅샷을 생성할 때의 원본 데이터베이스 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-155">The maximum size of a database snapshot is the size of the source database at snapshot creation.</span></span> <span data-ttu-id="fb669-156">자세한 내용은 [데이터베이스 스냅샷 스파스 파일의 크기 보기&#40;Transact-SQL&#41;](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb669-156">For more information, see [View the Size of the Sparse File of a Database Snapshot &#40;Transact-SQL&#41;](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="fb669-157">AS SNAPSHOT OF 절을 사용하여 파일에서 CREATE DATABASE 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-157">Issue a CREATE DATABASE statement on the files using the AS SNAPSHOT OF clause.</span></span> <span data-ttu-id="fb669-158">스냅샷을 만들려면 원본 데이터베이스를 구성하는 모든 데이터베이스 파일의 논리적 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-158">Creating a snapshot requires specifying the logical name of every database file of the source database.</span></span> <span data-ttu-id="fb669-159">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-159">The syntax is as follows:</span></span>  
  
     <span data-ttu-id="fb669-160">CREATE DATABASE *database_snapshot_name*</span><span class="sxs-lookup"><span data-stu-id="fb669-160">CREATE DATABASE *database_snapshot_name*</span></span>  
  
     <span data-ttu-id="fb669-161">켜기</span><span class="sxs-lookup"><span data-stu-id="fb669-161">ON</span></span>  
  
     <span data-ttu-id="fb669-162">(</span><span class="sxs-lookup"><span data-stu-id="fb669-162">(</span></span>  
  
     <span data-ttu-id="fb669-163">NAME =*logical_file_name*,</span><span class="sxs-lookup"><span data-stu-id="fb669-163">NAME =*logical_file_name*,</span></span>  
  
     <span data-ttu-id="fb669-164">FILENAME ='*os_file_name*'</span><span class="sxs-lookup"><span data-stu-id="fb669-164">FILENAME ='*os_file_name*'</span></span>  
  
     <span data-ttu-id="fb669-165">) [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="fb669-165">) [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="fb669-166">AS SNAPSHOT OF *source_database_name*</span><span class="sxs-lookup"><span data-stu-id="fb669-166">AS SNAPSHOT OF *source_database_name*</span></span>  
  
     <span data-ttu-id="fb669-167">[;]</span><span class="sxs-lookup"><span data-stu-id="fb669-167">[;]</span></span>  
  
     <span data-ttu-id="fb669-168">여기서 *source_\*\*database_name*은 원본 데이터베이스이고, *logical_file_name*은 SQL Server에서 파일을 참조할 때 사용되는 논리적 이름이고, *os_file_name*은 운영 체제에서 파일을 만드는 데 사용되는 경로 및 파일 이름이고, *database_snapshot_name*은 데이터베이스를 되돌릴 스냅샷의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-168">Where *source_\*\*database_name* is the source database, *logical_file_name i*s the logical name used in SQL Server when referencing the file, *os_file_name* is the path and file name used by the operating system when you create the file, and *database_snapshot_name* is the name of the snapshot to which you want to revert the database.</span></span> <span data-ttu-id="fb669-169">이 구문에 대한 자세한 내용은 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)을 사용해서만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-169">For a full description of this syntax, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fb669-170">데이터베이스 스냅샷을 만들 때 로그 파일, 오프라인 파일, 복원 파일 및 존재하지 않는 파일은 CREATE DATABASE 문에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-170">When you create a database snapshot, log files, offline files, restoring files, and defunct files are not allowed in the CREATE DATABASE statement.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="fb669-171">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fb669-171">Examples (Transact-SQL)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb669-172">이 예에서 사용된 `.ss` 확장명은 임의로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-172">The `.ss` extension used in the examples is arbitrary.</span></span>  
  
 <span data-ttu-id="fb669-173">이 섹션에는 다음 예제가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-173">This section contains the following examples:</span></span>  
  
-   <span data-ttu-id="fb669-174">A.</span><span class="sxs-lookup"><span data-stu-id="fb669-174">A.</span></span> [<span data-ttu-id="fb669-175">AdventureWorks 데이터베이스에 대한 스냅샷 만들기</span><span class="sxs-lookup"><span data-stu-id="fb669-175">Creating a snapshot on the AdventureWorks database</span></span>](#Creating_on_AW)  
  
-   <span data-ttu-id="fb669-176">B.</span><span class="sxs-lookup"><span data-stu-id="fb669-176">B.</span></span> [<span data-ttu-id="fb669-177">Sales 데이터베이스에 대한 스냅샷 만들기</span><span class="sxs-lookup"><span data-stu-id="fb669-177">Creating a snapshot on the Sales database</span></span>](#Creating_on_Sales)  
  
####  <a name="a-creating-a-snapshot-on-the-adventureworks-database"></a><a name="Creating_on_AW"></a> <span data-ttu-id="fb669-178">1.</span><span class="sxs-lookup"><span data-stu-id="fb669-178">A.</span></span> <span data-ttu-id="fb669-179">AdventureWorks 데이터베이스에 대한 스냅샷 만들기</span><span class="sxs-lookup"><span data-stu-id="fb669-179">Creating a snapshot on the AdventureWorks database</span></span>  
 <span data-ttu-id="fb669-180">이 예에서는 `AdventureWorks` 데이터베이스에 대한 데이터베이스 스냅샷을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-180">This example creates a database snapshot on the `AdventureWorks` database.</span></span> <span data-ttu-id="fb669-181">스냅샷 이름 `AdventureWorks_dbss_1800` 및 스파스 파일의 파일 이름 `AdventureWorks_data_1800.ss`는 생성 시간이 오후 6시(18:00시)임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-181">The snapshot name, `AdventureWorks_dbss_1800`, and the file name of its sparse file, `AdventureWorks_data_1800.ss`, indicate the creation time, 6 P.M (1800 hours).</span></span>  
  
```  
CREATE DATABASE AdventureWorks_dbss1800 ON  
( NAME = AdventureWorks_Data, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data\AdventureWorks_data_1800.ss' )  
AS SNAPSHOT OF AdventureWorks;  
GO  
```  
  
####  <a name="b-creating-a-snapshot-on-the-sales-database"></a><a name="Creating_on_Sales"></a> <span data-ttu-id="fb669-182">2.</span><span class="sxs-lookup"><span data-stu-id="fb669-182">B.</span></span> <span data-ttu-id="fb669-183">Sales 데이터베이스에 대한 스냅샷 만들기</span><span class="sxs-lookup"><span data-stu-id="fb669-183">Creating a snapshot on the Sales database</span></span>  
 <span data-ttu-id="fb669-184">이 예에서는 `sales_snapshot1200`데이터베이스에 대한 데이터베이스 스냅샷 `Sales` 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-184">This example creates a database snapshot, `sales_snapshot1200`, on the `Sales` database.</span></span> <span data-ttu-id="fb669-185">이 데이터베이스는 [CREATE database &#40;SQL Server transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)의 예제 인 "파일 그룹이 있는 데이터베이스 만들기"에서 생성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fb669-185">This database was created in the example, "Creating a database that has filegroups," in [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
```  
--Creating sales_snapshot1200 as snapshot of the  
--Sales database:  
CREATE DATABASE sales_snapshot1200 ON  
( NAME = SPri1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SPri1dat_1200.ss'),  
( NAME = SPri2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SPri2dt_1200.ss'),  
( NAME = SGrp1Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\mssql\data\SG1Fi1dt_1200.ss'),  
( NAME = SGrp1Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG1Fi2dt_1200.ss'),  
( NAME = SGrp2Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG2Fi1dt_1200.ss'),  
( NAME = SGrp2Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG2Fi2dt_1200.ss')  
AS SNAPSHOT OF Sales;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="fb669-186">관련 작업</span><span class="sxs-lookup"><span data-stu-id="fb669-186">Related Tasks</span></span>  
  
-   [<span data-ttu-id="fb669-187">데이터베이스 스냅샷 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb669-187">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="fb669-188">데이터베이스를 데이터베이스 스냅샷으로 되돌리기</span><span class="sxs-lookup"><span data-stu-id="fb669-188">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="fb669-189">데이터베이스 스냅샷 삭제&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fb669-189">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="fb669-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb669-190">See Also</span></span>  
 <span data-ttu-id="fb669-191">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fb669-191">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="fb669-192">데이터베이스 스냅샷&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fb669-192">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
