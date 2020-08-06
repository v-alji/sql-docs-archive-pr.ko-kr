---
title: 데이터베이스 연결 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb11b5c257007872e92d3f0a7eadb3e46b4969cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742232"
---
# <a name="attach-a-database"></a><span data-ttu-id="ceb8c-102">데이터베이스 연결</span><span class="sxs-lookup"><span data-stu-id="ceb8c-102">Attach a Database</span></span>
  <span data-ttu-id="ceb8c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 데이터베이스를 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-103">This topic describes how to attach a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ceb8c-104">이 기능을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 복사, 이동 또는 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-104">You can use this feature to copy, move, or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="ceb8c-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ceb8c-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ceb8c-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ceb8c-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="ceb8c-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="ceb8c-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ceb8c-109">보안</span><span class="sxs-lookup"><span data-stu-id="ceb8c-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ceb8c-110">**데이터베이스를 연결하려면:**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-110">**To Attach a Database by using:**</span></span>  
  
     [<span data-ttu-id="ceb8c-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ceb8c-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ceb8c-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ceb8c-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="ceb8c-113">**후속 작업:**  [데이터베이스를 업그레이드한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="ceb8c-113">**Follow Up:**  [After Upgrading a Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ceb8c-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ceb8c-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ceb8c-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="ceb8c-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="ceb8c-116">먼저 데이터베이스를 분리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-116">The database must first be detached.</span></span> <span data-ttu-id="ceb8c-117">분리되지 않은 데이터베이스를 연결하려고 하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-117">Attempting to attach a database that has not been detached will return an error.</span></span> <span data-ttu-id="ceb8c-118">자세한 내용은 [데이터베이스 분리](detach-a-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-118">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
-   <span data-ttu-id="ceb8c-119">데이터베이스를 연결할 경우 모든 데이터 파일(MDF 및 LDF 파일)이 사용 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-119">When you attach a database, all data files (MDF and LDF files) must be available.</span></span> <span data-ttu-id="ceb8c-120">데이터베이스가 처음 생성되었을 때 또는 마지막으로 연결되었을 때와 경로가 다른 데이터 파일이 있으면 해당 파일의 현재 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-120">If any data file has a different path from when the database was first created or last attached, you must specify the current path of the file.</span></span>  
  
-   <span data-ttu-id="ceb8c-121">데이터베이스를 분리하는 경우 MDF 및 LDF 파일이 서로 다른 디렉터리에 있고 경로 중 하나에 \\\\?\GlobalRoot가 포함되어 있으면 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-121">When you attach a database, if MDF and LDF files are located in different directories and one of the paths includes \\\\?\GlobalRoot, the operation will fail.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ceb8c-122">권장 사항</span><span class="sxs-lookup"><span data-stu-id="ceb8c-122">Recommendations</span></span>  
<span data-ttu-id="ceb8c-123">`ALTER DATABASE`분리 및 연결을 사용 하는 대신 계획 된 재배치 절차를 사용 하 여 데이터베이스를 이동 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-123">We recommend that you move databases by using the `ALTER DATABASE` planned relocation procedure, instead of using detach and attach.</span></span> <span data-ttu-id="ceb8c-124">자세한 내용은 [Move User Databases](move-user-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-124">For more information, see [Move User Databases](move-user-databases.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ceb8c-125">보안</span><span class="sxs-lookup"><span data-stu-id="ceb8c-125">Security</span></span>  
<span data-ttu-id="ceb8c-126">파일 액세스 권한은 데이터베이스 분리, 연결 등의 여러 데이터베이스 작업 중에 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-126">File access permissions are set during a number of database operations, including detaching or attaching a database.</span></span> <span data-ttu-id="ceb8c-127">데이터베이스를 분리 및 연결할 때마다 설정되는 파일 사용 권한에 대한 자세한 내용은 [온라인 설명서에서](https://technet.microsoft.com/library/ms189128.aspx) 데이터 및 로그 파일 보안 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-127">For information about file permissions that are set whenever a database is detached and attached, see [Securing Data and Log Files](https://technet.microsoft.com/library/ms189128.aspx) in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online.</span></span>  
  
<span data-ttu-id="ceb8c-128">알 수 없거나 신뢰할 수 없는 출처의 데이터베이스는 연결 또는 복원하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-128">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="ceb8c-129">이러한 데이터베이스에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 실행하거나 스키마 또는 물리적 데이터베이스 구조를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-129">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="ceb8c-130">알 수 없거나 신뢰할 수 없는 소스의 데이터베이스를 사용하기 전에 비프로덕션 서버의 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 를 실행하여 데이터베이스에서 코드(예: 저장 프로시저 또는 다른 사용자 정의 코드)를 시험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-130">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span> <span data-ttu-id="ceb8c-131">데이터베이스 연결에 대한 자세한 내용 및 데이터베이스를 연결할 때 메타데이터에 대해 이루어지는 변경에 대한 자세한 내용은 [데이터베이스 분리 및 연결&#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-131">For more information about attaching databases and information about changes that are made to metadata when you attach a database, see [Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ceb8c-132">권한</span><span class="sxs-lookup"><span data-stu-id="ceb8c-132">Permissions</span></span>  
<span data-ttu-id="ceb8c-133">`CREATE DATABASE`, `CREATE ANY DATABASE` 또는 `ALTER ANY DATABASE` 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-133">Requires `CREATE DATABASE`, `CREATE ANY DATABASE`, or `ALTER ANY DATABASE` permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ceb8c-134">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ceb8c-134">Using SQL Server Management Studio</span></span>  
  
### <a name="to-attach-a-database"></a><span data-ttu-id="ceb8c-135">데이터베이스를 연결하려면</span><span class="sxs-lookup"><span data-stu-id="ceb8c-135">To Attach a Database</span></span>  
  
1.  <span data-ttu-id="ceb8c-136">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-136">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ceb8c-137">마우스 오른쪽 단추로 **데이터베이스** 를 클릭하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-137">Right-click **Databases** and click **Attach**.</span></span>  
  
3.  <span data-ttu-id="ceb8c-138">**데이터베이스 연결** 대화 상자에서 연결할 데이터베이스를 지정하려면 **추가**를 클릭하고 **데이터베이스 파일 찾기** 대화 상자에서 데이터베이스가 있는 디스크 드라이브를 선택한 다음 디렉터리 트리를 확장하여 데이터베이스의 .mdf 파일을 선택합니다. 파일의 경로를 예로 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-138">In the **Attach Databases** dialog box, to specify the database to be attached, click **Add**; and in the **Locate Database Files** dialog box, select the disk drive where the database resides and expand the directory tree to find and select the .mdf file of the database; for example:</span></span>  
  
     `C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    > <span data-ttu-id="ceb8c-139">이미 연결된 데이터베이스를 선택하려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-139">Trying to select a database that is already attached generates an error.</span></span>  
  
     <span data-ttu-id="ceb8c-140">**연결할 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-140">**Databases to attach**</span></span>  
     <span data-ttu-id="ceb8c-141">선택한 데이터베이스에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-141">Displays information about the selected databases.</span></span>  
  
     \<no column header>  
     <span data-ttu-id="ceb8c-142">연결 작업의 상태를 나타내는 아이콘을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-142">Displays an icon indicating the status of the attach operation.</span></span> <span data-ttu-id="ceb8c-143">가능한 아이콘은 아래의 **상태** 에 대한 설명에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-143">The possible icons are described in the **Status** description, below).</span></span>  
  
     <span data-ttu-id="ceb8c-144">**MDF 파일 위치**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-144">**MDF File Location**</span></span>  
     <span data-ttu-id="ceb8c-145">선택한 MDF 파일의 경로와 파일 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-145">Displays the path and file name of the selected MDF file.</span></span>  
  
     <span data-ttu-id="ceb8c-146">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-146">**Database Name**</span></span>  
     <span data-ttu-id="ceb8c-147">데이터베이스 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-147">Displays the name of the database.</span></span>  
  
     <span data-ttu-id="ceb8c-148">**다른 이름으로 연결**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-148">**Attach As**</span></span>  
     <span data-ttu-id="ceb8c-149">필요에 따라 연결할 데이터베이스의 이름을 다른 이름으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-149">Optionally, specifies a different name for the database to attach as.</span></span>  
  
     <span data-ttu-id="ceb8c-150">**소유자**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-150">**Owner**</span></span>  
     <span data-ttu-id="ceb8c-151">필요에 따라 다른 소유자를 선택할 수 있도록 가능한 데이터베이스 소유자의 드롭다운 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-151">Provides a drop-down list of possible database owners from which you can optionally select a different owner.</span></span>  
  
     <span data-ttu-id="ceb8c-152">**상태**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-152">**Status**</span></span>  
     <span data-ttu-id="ceb8c-153">다음 표에 설명된 내용과 같이 데이터베이스의 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-153">Displays the status of the database according to the following table.</span></span>  
  
    |<span data-ttu-id="ceb8c-154">아이콘</span><span class="sxs-lookup"><span data-stu-id="ceb8c-154">Icon</span></span>|<span data-ttu-id="ceb8c-155">상태 텍스트</span><span class="sxs-lookup"><span data-stu-id="ceb8c-155">Status text</span></span>|<span data-ttu-id="ceb8c-156">Description</span><span class="sxs-lookup"><span data-stu-id="ceb8c-156">Description</span></span>|  
    |----------|-----------------|-----------------|  
    |<span data-ttu-id="ceb8c-157">(아이콘 없음)</span><span class="sxs-lookup"><span data-stu-id="ceb8c-157">(No icon)</span></span>|<span data-ttu-id="ceb8c-158">(텍스트 없음)</span><span class="sxs-lookup"><span data-stu-id="ceb8c-158">(No text)</span></span>|<span data-ttu-id="ceb8c-159">연결 작업이 시작되지 않았거나 이 개체에 대해 보류 중입니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-159">Attach operation has not been started or may be pending for this object.</span></span> <span data-ttu-id="ceb8c-160">대화 상자가 열려 있는 경우에 표시되는 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-160">This is the default when the dialog is opened.</span></span>|  
    |<span data-ttu-id="ceb8c-161">녹색, 오른쪽 방향 삼각형</span><span class="sxs-lookup"><span data-stu-id="ceb8c-161">Green, right-pointing triangle</span></span>|<span data-ttu-id="ceb8c-162">진행 중</span><span class="sxs-lookup"><span data-stu-id="ceb8c-162">In progress</span></span>|<span data-ttu-id="ceb8c-163">연결 작업이 시작되었지만 아직 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-163">Attach operation has been started but it is not complete.</span></span>|  
    |<span data-ttu-id="ceb8c-164">녹색 확인 표시</span><span class="sxs-lookup"><span data-stu-id="ceb8c-164">Green check mark</span></span>|<span data-ttu-id="ceb8c-165">Success</span><span class="sxs-lookup"><span data-stu-id="ceb8c-165">Success</span></span>|<span data-ttu-id="ceb8c-166">개체가 성공적으로 연결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-166">The object has been attached successfully.</span></span>|  
    |<span data-ttu-id="ceb8c-167">흰색 십자 표시가 있는 빨강 원</span><span class="sxs-lookup"><span data-stu-id="ceb8c-167">Red circle containing a white cross</span></span>|<span data-ttu-id="ceb8c-168">Error</span><span class="sxs-lookup"><span data-stu-id="ceb8c-168">Error</span></span>|<span data-ttu-id="ceb8c-169">연결 작업을 수행하는 동안 오류가 발생하여 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-169">Attach operation encountered an error and did not complete successfully.</span></span>|  
    |<span data-ttu-id="ceb8c-170">오른쪽과 왼쪽에 두 개의 검정 사분면이 있고 위쪽과 아래쪽에 두 개의 흰색 사분면이 있는 원</span><span class="sxs-lookup"><span data-stu-id="ceb8c-170">Circle containing two black quadrants (on left and right) and two white quadrants (on top and bottom)</span></span>|<span data-ttu-id="ceb8c-171">중지됨</span><span class="sxs-lookup"><span data-stu-id="ceb8c-171">Stopped</span></span>|<span data-ttu-id="ceb8c-172">사용자가 작업을 중지하여 연결 작업이 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-172">Attach operation was not completed successfully because the user stopped the operation.</span></span>|  
    |<span data-ttu-id="ceb8c-173">시계 반대 방향을 가리키는 곡선 모양의 화살표가 있는 원</span><span class="sxs-lookup"><span data-stu-id="ceb8c-173">Circle containing a curved arrow pointing counter-clockwise</span></span>|<span data-ttu-id="ceb8c-174">롤백됨</span><span class="sxs-lookup"><span data-stu-id="ceb8c-174">Rolled Back</span></span>|<span data-ttu-id="ceb8c-175">연결 작업이 성공적으로 완료되었지만 다른 개체를 연결하는 동안 발생한 오류로 인해 롤백되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-175">Attach operation was successful but it has been rolled back due to an error during attachment of another object.</span></span>|  
  
     <span data-ttu-id="ceb8c-176">**메시지**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-176">**Message**</span></span>  
     <span data-ttu-id="ceb8c-177">빈 메시지 또는 "파일을 찾을 수 없습니다"라는 하이퍼링크를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-177">Displays either a blank message or a "File not found" hyperlink.</span></span>  
  
     <span data-ttu-id="ceb8c-178">**추가**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-178">**Add**</span></span>  
     <span data-ttu-id="ceb8c-179">필요한 기본 데이터베이스 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-179">Find the necessary main database files.</span></span> <span data-ttu-id="ceb8c-180">사용자가 .mdf 파일을 선택하면 **연결할 데이터베이스** 표의 각 필드에 적절한 정보가 자동으로 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-180">When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="ceb8c-181">**제거**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-181">**Remove**</span></span>  
     <span data-ttu-id="ceb8c-182">선택한 파일을 **연결할 데이터베이스** 표에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-182">Removes the selected file from the **Databases to attach** grid.</span></span>  
  
     <span data-ttu-id="ceb8c-183">**“** *<database_name>* **” 데이터베이스 정보**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-183">**"** *<database_name>* **" database details**</span></span>  
     <span data-ttu-id="ceb8c-184">연결할 파일의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-184">Displays the names of the files to be attached.</span></span> <span data-ttu-id="ceb8c-185">파일의 경로 이름을 확인하거나 변경하려면 **찾아보기** 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-185">To verify or change the pathname of a file, click the **Browse** button (**...**).</span></span>  
  
    > [!NOTE]  
    > <span data-ttu-id="ceb8c-186">파일이 없으면 **메시지** 열에 "찾을 수 없음"이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-186">If a file does not exist, the **Message** column displays "Not found."</span></span> <span data-ttu-id="ceb8c-187">로그 파일을 찾을 수 없는 경우 다른 디렉터리에 있거나 삭제된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-187">If a log file is not found, it exists in another directory or has been deleted.</span></span> <span data-ttu-id="ceb8c-188">올바른 위치를 가리키도록 **데이터베이스 정보** 표의 파일 경로를 업데이트하거나 표에서 로그 파일을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-188">You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid.</span></span> <span data-ttu-id="ceb8c-189">.ndf 데이터 파일을 찾을 수 없는 경우 올바른 위치를 가리키도록 표에서 해당 파일의 경로를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-189">If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.</span></span>  
  
     <span data-ttu-id="ceb8c-190">**원래 파일 이름**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-190">**Original File Name**</span></span>  
     <span data-ttu-id="ceb8c-191">데이터베이스에 속한 연결된 파일의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-191">Displays the name of the attached file belonging to the database.</span></span>  
  
     <span data-ttu-id="ceb8c-192">**파일 유형**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-192">**File Type**</span></span>  
     <span data-ttu-id="ceb8c-193">파일의 형식( **데이터** 또는 **로그**)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-193">Indicates the type of file, **Data** or **Log**.</span></span>  
  
     <span data-ttu-id="ceb8c-194">**현재 파일 경로**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-194">**Current File Path**</span></span>  
     <span data-ttu-id="ceb8c-195">선택한 데이터베이스 파일의 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-195">Displays the path to the selected database file.</span></span> <span data-ttu-id="ceb8c-196">이 경로는 직접 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-196">The path can be edited manually.</span></span>  
  
     <span data-ttu-id="ceb8c-197">**메시지**</span><span class="sxs-lookup"><span data-stu-id="ceb8c-197">**Message**</span></span>  
     <span data-ttu-id="ceb8c-198">빈 메시지 또는 "**파일을 찾을 수 없습니다**"라는 하이퍼링크를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-198">Displays either a blank message or a "**File not found**" hyperlink.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ceb8c-199">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ceb8c-199">Using Transact-SQL</span></span>  
  
### <a name="to-attach-a-database"></a><span data-ttu-id="ceb8c-200">데이터베이스를 연결하려면</span><span class="sxs-lookup"><span data-stu-id="ceb8c-200">To attach a database</span></span>  
  
1.  <span data-ttu-id="ceb8c-201">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-201">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ceb8c-202">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-202">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ceb8c-203">Close와 함께 [CREATE DATABASE](/sql/t-sql/statements/create-database-sql-server-transact-sql) 문을 사용 합니다 `FOR ATTACH` .</span><span class="sxs-lookup"><span data-stu-id="ceb8c-203">Use the [CREATE DATABASE](/sql/t-sql/statements/create-database-sql-server-transact-sql) statement with the `FOR ATTACH` close.</span></span>  
  
     <span data-ttu-id="ceb8c-204">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-204">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ceb8c-205">이 예에서는 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 데이터베이스의 파일을 연결하고 데이터베이스 이름을 `MyAdventureWorks`로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-205">This example attaches the files of the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database and renames the database to `MyAdventureWorks`.</span></span>  
  
    ```sql  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
    ```  
  
    > [!NOTE]  
    > <span data-ttu-id="ceb8c-206">또는 [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) 또는 [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) 저장 프로시저를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-206">Alternatively, you can use the [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) or [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) stored procedure.</span></span> <span data-ttu-id="ceb8c-207">그러나 이 프로시저는 이후 버전의 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-207">However, these procedures will be removed in a future version of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ceb8c-208">새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-208">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="ceb8c-209">CREATE DATABASE ...를 사용 하는 것이 좋습니다. 대신 FOR ATTACH.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-209">We recommend that you use CREATE DATABASE ... FOR ATTACH instead.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> <span data-ttu-id="ceb8c-210">후속 작업: SQL Server 데이터베이스를 업그레이드한 후</span><span class="sxs-lookup"><span data-stu-id="ceb8c-210">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="ceb8c-211">연결 방법을 사용 하 여 데이터베이스를 업그레이드 하면 데이터베이스를 바로 사용할 수 있으며 자동으로 업그레이드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-211">fter you upgrade a database by using the attach method, the database becomes available immediately and is automatically upgraded.</span></span> <span data-ttu-id="ceb8c-212">데이터베이스에 전체 텍스트 인덱스가 있는 경우 업그레이드 프로세스는 **전체 텍스트 업그레이드 옵션** 서버 속성의 설정에 따라 인덱스를 가져오거나, 다시 설정하거나, 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-212">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **Full-Text Upgrade Option** server property.</span></span> <span data-ttu-id="ceb8c-213">업그레이드 옵션이 **가져오기** 또는 **다시 작성**으로 설정되어 있는 경우 업그레이드하는 동안 전체 텍스트 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-213">If the upgrade option is set to **Import** or **Rebuild**, the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="ceb8c-214">인덱싱되는 데이터 양에 따라 가져오기 작업은 몇 시간씩 걸릴 수 있으며 다시 작성 작업은 10배 정도 더 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-214">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="ceb8c-215">업그레이드 옵션이 **가져오기**로 설정되어 있으면 전체 텍스트 카탈로그를 사용할 수 없는 경우 관련된 전체 텍스트 인덱스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-215">Note also that when the upgrade option is set to **Import**, if a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span>  
  
<span data-ttu-id="ceb8c-216">사용자 데이터베이스의 호환성 수준이 업그레이드 이전에 100 이상이면 업그레이드 후에도 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-216">If the compatibility level of a user database is 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="ceb8c-217">업그레이드 이전에 호환성 수준이 90이면 업그레이드된 데이터베이스에서는 호환성 수준이 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 지원되는 가장 낮은 호환성 수준인 100으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-217">If the compatibility level is 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="ceb8c-218">자세한 내용은 [ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ceb8c-218">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb8c-219">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ceb8c-219">See Also</span></span>  
 <span data-ttu-id="ceb8c-220">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ceb8c-220">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="ceb8c-221">데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="ceb8c-221">Detach a Database</span></span>](detach-a-database.md)  
  
  
