---
title: 데이터베이스 복사 마법사 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.cdw.transfermethod.f1
- sql12.swb.cdw.welcome.f1
- sql12.swb.cdw.packageconfiguration.f1
- sql12.swb.cdw.schedule.f1
- sql12.swb.cdw.destination.f1
- sql12.swb.cdw.complete.f1
- sql12.swb.cdw.destinationconfiguration.f1
- sql12.swb.cdw.selectdatabaseobjects.f1
- sql12.swb.cdw.databases.f1
- sql12.swb.cdw.source.f1
- sql12.swb.cdw.locationofsourcedbfiles.f1
helpviewer_keywords:
- Copy Database Wizard
- starting Copy Database Wizard
ms.assetid: 7a999fc7-0a26-4a0d-9eeb-db6fc794f3cb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0baaeef6cb196a67b2f615aa280b61b61fbc5119
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741083"
---
# <a name="use-the-copy-database-wizard"></a><span data-ttu-id="5e600-102">데이터베이스 복사 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="5e600-102">Use the Copy Database Wizard</span></span>
  <span data-ttu-id="5e600-103">데이터베이스 복사 마법사를 사용하면 서버를 중단하는 일 없이 데이터베이스 및 그 개체를 쉽게 다른 서버로 이동하거나 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-103">The Copy Database Wizard lets you move or copy databases and their objects easily from one server to another, with no server downtime.</span></span> <span data-ttu-id="5e600-104">데이터베이스를 이전 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-104">You can also upgrade databases from a previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="5e600-105">이 마법사를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-105">By using this wizard, you can do the following:</span></span>  
  
-   <span data-ttu-id="5e600-106">원본 서버 및 대상 서버 선택</span><span class="sxs-lookup"><span data-stu-id="5e600-106">Pick a source and destination server.</span></span>  
  
-   <span data-ttu-id="5e600-107">이동하거나 복사하거나 업그레이드할 데이터베이스 선택</span><span class="sxs-lookup"><span data-stu-id="5e600-107">Select databases to move, copy or upgrade.</span></span>  
  
-   <span data-ttu-id="5e600-108">데이터베이스의 파일 위치 지정</span><span class="sxs-lookup"><span data-stu-id="5e600-108">Specify the file location for the databases.</span></span>  
  
-   <span data-ttu-id="5e600-109">대상 서버에서 로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="5e600-109">Create logins on the destination server.</span></span>  
  
-   <span data-ttu-id="5e600-110">지원 개체, 작업, 사용자 정의 저장 프로시저 및 오류 메시지를 추가로 복사</span><span class="sxs-lookup"><span data-stu-id="5e600-110">Copy additional supporting objects, jobs, user-defined stored procedures, and error messages.</span></span>  
  
-   <span data-ttu-id="5e600-111">데이터베이스 이동 또는 복사 일정 예약</span><span class="sxs-lookup"><span data-stu-id="5e600-111">Schedule when to move or copy the databases.</span></span>  
  
 <span data-ttu-id="5e600-112">데이터베이스뿐만 아니라 관련 메타데이터(예: 복사된 데이터베이스에 필요한 **master** 데이터베이스의 로그인 및 개체)도 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-112">In addition to copying databases, you can copy associated metadata, for example, logins and objects from the **master** database that are required by a copied database.</span></span>  
  
 <span data-ttu-id="5e600-113">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="5e600-113">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5e600-114">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5e600-114">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5e600-115">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5e600-115">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5e600-116">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="5e600-116">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="5e600-117">권장 사항</span><span class="sxs-lookup"><span data-stu-id="5e600-117">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="5e600-118">보안</span><span class="sxs-lookup"><span data-stu-id="5e600-118">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5e600-119">**데이터베이스 복사 마법사 사용**</span><span class="sxs-lookup"><span data-stu-id="5e600-119">**Using the Copy Database Wizard to:**</span></span>  
  
     [<span data-ttu-id="5e600-120">데이터베이스 복사, 이동 또는 업그레이드</span><span class="sxs-lookup"><span data-stu-id="5e600-120">Copy, Move, or Upgrade Databases</span></span>](#Copy_Move)  
  
-   <span data-ttu-id="5e600-121">**업그레이드 후 후속 작업:**</span><span class="sxs-lookup"><span data-stu-id="5e600-121">**Follow up, after upgrade:**</span></span>  
  
     [<span data-ttu-id="5e600-122">SQL Server 데이터베이스를 업그레이드한 후</span><span class="sxs-lookup"><span data-stu-id="5e600-122">After Upgrading a SQL Server Database</span></span>](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5e600-123">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5e600-123">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5e600-124">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5e600-124">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5e600-125">Express Edition에서는 데이터베이스 복사 마법사를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-125">The Copy Database Wizard is not available in the Express edition.</span></span>  
  
-   <span data-ttu-id="5e600-126">다음 데이터베이스는 데이터베이스 복사 마법사를 사용하여 이동하거나 복사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-126">The Copy Database Wizard cannot be used to copy or move the following databases.</span></span>  
  
    -   <span data-ttu-id="5e600-127">시스템 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5e600-127">System databases</span></span>  
  
    -   <span data-ttu-id="5e600-128">복제용으로 표시된 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5e600-128">Databases marked for replication.</span></span>  
  
    -   <span data-ttu-id="5e600-129">액세스 불가, 로드 중, 오프라인, 복구 중으로 표시되거나 응급 모드인 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5e600-129">Databases marked Inaccessible, Loading, Offline, Recovering, Suspect, or in Emergency Mode.</span></span>  
  
-   <span data-ttu-id="5e600-130">데이터베이스를 업그레이드한 후에는 이전 버전으로 다운그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-130">After a database has been upgraded, it cannot be downgraded to a previous version.</span></span>  
  
-   <span data-ttu-id="5e600-131">**이동** 옵션을 선택하면 마법사가 데이터베이스를 이동한 후 자동으로 원본 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-131">If you select the **Move** option, the wizard deletes the source database automatically after moving the database.</span></span> <span data-ttu-id="5e600-132">**복사** 옵션을 선택하면 데이터베이스 복사 마법사에서 원본 데이터베이스를 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-132">The Copy Database Wizard does not delete a source database if you select the **Copy** option.</span></span>  
  
-   <span data-ttu-id="5e600-133">SMO( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects) 방법을 사용하여 전체 텍스트 카탈로그를 이동하는 경우 이동 후에 인덱스를 다시 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-133">If you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object method to move the full-text catalog, you must repopulate the index after the move.</span></span>  
  
-   <span data-ttu-id="5e600-134">분리/연결 방법은 데이터베이스를 분리하고 데이터베이스 파일(.mdf, .ndf, .ldf)을 이동하거나 복사한 다음 새 위치에서 데이터베이스를 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-134">The detach-and-attach method detaches the database, moves or copies the database .mdf, .ndf, .ldf files and reattaches the database in the new location.</span></span> <span data-ttu-id="5e600-135">분리/연결 방법의 경우 데이터 손실이나 불일치가 발생하지 않도록 하려면 활성 세션을 이동 또는 복사 중인 데이터베이스에 연결하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-135">For the detach-and-attach method, to avoid data loss or inconsistency, active sessions cannot be attached to the database being moved or copied.</span></span> <span data-ttu-id="5e600-136">활성 세션이 있는 경우 데이터베이스 복사 마법사가 이동 또는 복사 작업을 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-136">If any active sessions exist, the Copy Database Wizard does not execute the move or copy operation.</span></span> <span data-ttu-id="5e600-137">SMO( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects) 방법에서는 데이터베이스가 결코 오프라인 상태가 되지 않으므로 활성 세션이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-137">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object method, active sessions are allowed because the database is never taken offline.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="5e600-138">필수 조건</span><span class="sxs-lookup"><span data-stu-id="5e600-138">Prerequisites</span></span>  
 <span data-ttu-id="5e600-139">대상 서버에서 SQL Server 에이전트가 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-139">Ensure that SQL Server Agent is started on the destination server.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="5e600-140">권장 사항</span><span class="sxs-lookup"><span data-stu-id="5e600-140">Recommendations</span></span>  
  
-   <span data-ttu-id="5e600-141">업그레이드한 데이터베이스가 최적의 성능을 낼 수 있도록 업그레이드한 데이터베이스에 대해 sp_updatestats(통계 업데이트)를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e600-141">To ensure optimal performance of an upgraded database, run sp_updatestats (update statistics) against the upgraded database.</span></span>  
  
-   <span data-ttu-id="5e600-142">데이터베이스를 다른 서버 인스턴스로 복사하는 경우 사용자와 애플리케이션에 일관된 환경을 제공하려면 로그인, 작업 등 데이터베이스의 일부 또는 모든 메타데이터를 다른 서버 인스턴스에서 다시 만들어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-142">When you copy a database to another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="5e600-143">자세한 내용은 [다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e600-143">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5e600-144">보안</span><span class="sxs-lookup"><span data-stu-id="5e600-144">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5e600-145">권한</span><span class="sxs-lookup"><span data-stu-id="5e600-145">Permissions</span></span>  
 <span data-ttu-id="5e600-146">원본 서버와 대상 서버 모두에서 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-146">You must be a member of the **sysadmin** fixed server role on both the source and destination servers.</span></span>  
  
##  <a name="copy-move-or-upgrade-databases"></a><a name="Copy_Move"></a><span data-ttu-id="5e600-147">데이터베이스 복사, 이동 또는 업그레이드</span><span class="sxs-lookup"><span data-stu-id="5e600-147">Copy, Move or Upgrade Databases</span></span>  
  
1.  <span data-ttu-id="5e600-148">의 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 개체 탐색기에서 **데이터베이스**를 확장 하 고 데이터베이스를 마우스 오른쪽 단추로 클릭 한 다음 **태스크**를 가리키고 **데이터베이스 복사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-148">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in Object Explorer, expand **Databases**, right-click a database, point to **Tasks**, and then click **Copy Database**.</span></span>  
  
2.  <span data-ttu-id="5e600-149">**원본 서버 선택** 페이지에서 이동 또는 복사하려는 데이터베이스가 있는 서버를 지정하고 로그인 정보를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-149">From the **Select a Source Server** page, specify the server with the database to move or copy, and to enter login information.</span></span> <span data-ttu-id="5e600-150">인증 방법을 선택하고 로그인 정보를 입력한 후 **다음** 을 클릭하여 원본 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-150">After you select the authentication method and enter login information, click **Next** to establish the connection to the source server.</span></span> <span data-ttu-id="5e600-151">이 연결은 해당 세션 동안 열린 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-151">This connection remains open throughout the session.</span></span>  
  
     <span data-ttu-id="5e600-152">**원본 서버**</span><span class="sxs-lookup"><span data-stu-id="5e600-152">**Source server**</span></span>  
     <span data-ttu-id="5e600-153">이동 또는 복사 하려는 데이터베이스가 있는 서버의 이름을 선택 하거나 찾아보기 (...) 단추를 클릭 하 여 원하는 서버를 찾습니다 (**...**).</span><span class="sxs-lookup"><span data-stu-id="5e600-153">Select the name of the server on which the database or databases you want to move or copy are located, or click the browse (**...**) button to locate the server you want.</span></span> <span data-ttu-id="5e600-154">서버는 최소한 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-154">The server must be at least [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
     <span data-ttu-id="5e600-155">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="5e600-155">**Use Windows Authentication**</span></span>  
     <span data-ttu-id="5e600-156">사용자가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 사용자 계정을 통해 연결하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-156">Allow a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="5e600-157">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="5e600-157">**Use SQL Server Authentication**</span></span>  
     <span data-ttu-id="5e600-158">사용자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 사용자 이름 및 암호를 제공하여 연결하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-158">Allow a user to connect by providing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user name and password.</span></span>  
  
     <span data-ttu-id="5e600-159">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="5e600-159">**User name**</span></span>  
     <span data-ttu-id="5e600-160">연결에 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-160">Enter the user name to connect with.</span></span> <span data-ttu-id="5e600-161">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-161">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication .</span></span>  
  
     <span data-ttu-id="5e600-162">**암호**</span><span class="sxs-lookup"><span data-stu-id="5e600-162">**Password**</span></span>  
     <span data-ttu-id="5e600-163">로그인 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-163">Enter the password for the login.</span></span> <span data-ttu-id="5e600-164">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-164">This option is only available if you have selected to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="5e600-165">**다음**</span><span class="sxs-lookup"><span data-stu-id="5e600-165">**Next**</span></span>  
     <span data-ttu-id="5e600-166">서버에 연결하고 사용자의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-166">Connect to the server and validate the user.</span></span> <span data-ttu-id="5e600-167">이 프로세스는 사용자가 선택한 컴퓨터에서 **sysadmin** 고정 서버 역할의 멤버인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-167">This process checks whether the user is a member of the **sysadmin** fixed server role on the selected computer.</span></span>  
  
3.  <span data-ttu-id="5e600-168">**대상 서버 선택** 페이지에서 데이터베이스를 이동 또는 복사할 서버를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-168">From the **Select a Destination Server** page, specify the server where the database will be moved or copied.</span></span> <span data-ttu-id="5e600-169">원본 서버와 대상 서버를 동일한 서버 인스턴스로 설정하면 데이터베이스 복사본이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-169">If you set the source and destination servers to the same server instance, you will make a copy of a database.</span></span> <span data-ttu-id="5e600-170">이 경우 이 마법사에서 나중에 데이터베이스의 이름을 바꿔야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-170">In this case you must rename the database at a later point in the wizard.</span></span> <span data-ttu-id="5e600-171">원본 데이터베이스 이름은 대상 서버에 있는 이름과 충돌하지 않는 경우에만 복사되거나 이동된 데이터베이스에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-171">The source database name can be used for the copied or moved database only if name conflicts do not exist on the destination server.</span></span> <span data-ttu-id="5e600-172">이름 충돌이 있을 때는 먼저 대상 서버에서 수동으로 이 문제를 해결해야 원본 데이터베이스 이름을 대상 서버에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-172">If name conflicts exist, you must resolve them manually on the destination server before you can use the source database name there.</span></span>  
  
     <span data-ttu-id="5e600-173">**대상 서버**</span><span class="sxs-lookup"><span data-stu-id="5e600-173">**Destination server**</span></span>  
     <span data-ttu-id="5e600-174">데이터베이스 또는 데이터베이스를 이동 또는 복사할 서버의 이름을 선택 하거나 찾아보기 단추 (**...**)를 클릭 하 여 대상 서버를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-174">Select the name of the server to which the database or databases will be moved or copied, or click the browse (**...**) button to locate a destination server.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e600-175">클러스터형 서버인 대상을 사용할 수 있습니다. 그러나 데이터베이스 복사 마법사를 사용하면 클러스터형 대상 서버에서 공유 드라이브만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-175">You can use a destination that is a clustered server; the Copy Database Wizard will make sure you select only shared drives on a clustered destination server.</span></span>  
  
     <span data-ttu-id="5e600-176">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="5e600-176">**Use Windows Authentication**</span></span>  
     <span data-ttu-id="5e600-177">사용자가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 사용자 계정을 통해 연결하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-177">Allow a user to connect through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
     <span data-ttu-id="5e600-178">**SQL Server 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="5e600-178">**Use SQL Server Authentication**</span></span>  
     <span data-ttu-id="5e600-179">사용자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 사용자 이름 및 암호를 제공하여 연결하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-179">Allow a user to connect by providing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user name and password.</span></span>  
  
     <span data-ttu-id="5e600-180">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="5e600-180">**User name**</span></span>  
     <span data-ttu-id="5e600-181">연결에 사용할 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-181">Enter the user name to connect with.</span></span> <span data-ttu-id="5e600-182">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-182">This option is only available if you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="5e600-183">**암호**</span><span class="sxs-lookup"><span data-stu-id="5e600-183">**Password**</span></span>  
     <span data-ttu-id="5e600-184">로그인 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-184">Enter the password for the login.</span></span> <span data-ttu-id="5e600-185">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-185">This option is only available if you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="5e600-186">**다음**</span><span class="sxs-lookup"><span data-stu-id="5e600-186">**Next**</span></span>  
     <span data-ttu-id="5e600-187">서버에 연결하고 사용자의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-187">Connect to the server and validate the user.</span></span> <span data-ttu-id="5e600-188">이 프로세스는 사용자가 선택한 컴퓨터에서 위의 사용 권한을 가지고 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-188">This process checks whether the user has the permissions listed above on the selected computers.</span></span>  
  
4.  <span data-ttu-id="5e600-189">**전송 방법 선택** 페이지에서 전송 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-189">From the **Select a Transfer Method** page, select the transfer method.</span></span>  
  
     <span data-ttu-id="5e600-190">**분리/연결 방법을 사용합니다.**</span><span class="sxs-lookup"><span data-stu-id="5e600-190">**Use the detach and attach method**</span></span>  
     <span data-ttu-id="5e600-191">데이터베이스를 원본 서버에서 분리하고 데이터베이스 파일(.mdf, .ndf 및 .ldf)을 대상 서버로 복사하고 데이터베이스를 대상 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-191">Detach the database from the source server, copy the database files (.mdf, .ndf, and .ldf) to the destination server, and attach the database at the destination server.</span></span> <span data-ttu-id="5e600-192">이 방법은 원본 디스크를 읽고 대상 디스크에 쓰는 작업이 주된 작업이므로 속도가 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-192">This method is usually the faster method because the principal work is reading the source disk and writing the destination disk.</span></span> <span data-ttu-id="5e600-193">데이터베이스에서 개체를 만들거나 데이터베이스 스토리지 구조를 만드는 데는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 논리를 필요로 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-193">No [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logic is required to create objects within the database, or create data storage structures.</span></span> <span data-ttu-id="5e600-194">그러나 데이터베이스에 할당되었지만 사용되지 않는 공간이 많으면 속도가 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-194">This method can be slower, however, if the database contains a large amount of allocated but unused space.</span></span> <span data-ttu-id="5e600-195">예를 들어 100MB를 할당하여 만든 새 데이터베이스의 경우 5MB만 사용 중이고 나머지 공간은 비어 있어도 100MB 전체가 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-195">For instance, a new and practically empty database that is created allocating 100 MB, copies the entire 100 MB, even if only 5 MB is full.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e600-196">이 방법을 사용하면 전송 중에 사용자가 데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-196">This method makes the database unavailable to users during the transfer.</span></span>  
  
     <span data-ttu-id="5e600-197">**오류 발생 시 원본 데이터베이스 다시 연결**</span><span class="sxs-lookup"><span data-stu-id="5e600-197">**If a failure occurs, reattach the source database**</span></span>  
     <span data-ttu-id="5e600-198">데이터베이스를 복사하면 원본 데이터베이스 파일이 원본 서버에 항상 다시 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-198">When a database is copied, the original database files are always reattached to the source server.</span></span> <span data-ttu-id="5e600-199">데이터베이스 이동을 완료할 수 없는 경우 이 상자를 사용하여 원본 파일을 원본 데이터베이스에 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-199">Use this box to reattach original files to the source database if a database move cannot be completed.</span></span>  
  
     <span data-ttu-id="5e600-200">**SQL 관리 개체 방법을 사용합니다.**</span><span class="sxs-lookup"><span data-stu-id="5e600-200">**Use the SQL Management Object method**</span></span>  
     <span data-ttu-id="5e600-201">이 방법은 원본 데이터베이스에 있는 데이터베이스 개체의 정의를 읽어 대상 데이터베이스에 각 개체를 만든 다음,</span><span class="sxs-lookup"><span data-stu-id="5e600-201">This method reads the definition of each database object on the source database and creates each object in the destination database.</span></span> <span data-ttu-id="5e600-202">원본 테이블에서 대상 테이블로 데이터를 전송하여 인덱스와 메타데이터를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-202">Then it transfers the data from the source tables to the destination tables, recreating indexes and metadata.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e600-203">이 방법을 사용하면 데이터를 전송하는 동안에도 데이터베이스 사용자가 데이터베이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-203">Database users can continue to access the database during the transfer.</span></span>  
  
5.  <span data-ttu-id="5e600-204">**데이터베이스 선택** 페이지에서, 원본 서버에서 대상 서버로 이동 또는 복사할 데이터베이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-204">From the **Select Database** page, select the database or databases you want to move or copy from the source server to the destination server.</span></span> <span data-ttu-id="5e600-205">이 항목의 ' Begin Before ' 섹션에서 [제한 사항을](#Restrictions) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e600-205">See [Limitations and Restrictions](#Restrictions) in the 'Before You Begin' section of this topic.</span></span>  
  
     <span data-ttu-id="5e600-206">**이동**</span><span class="sxs-lookup"><span data-stu-id="5e600-206">**Move**</span></span>  
     <span data-ttu-id="5e600-207">데이터베이스를 대상 서버로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-207">Move the database to the destination server.</span></span>  
  
     <span data-ttu-id="5e600-208">**복사**</span><span class="sxs-lookup"><span data-stu-id="5e600-208">**Copy**</span></span>  
     <span data-ttu-id="5e600-209">데이터베이스를 대상 서버에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-209">Copy the database to the destination server.</span></span>  
  
     <span data-ttu-id="5e600-210">**원본**</span><span class="sxs-lookup"><span data-stu-id="5e600-210">**Source**</span></span>  
     <span data-ttu-id="5e600-211">원본 서버에 존재하는 데이터베이스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-211">Displays the databases that exist on the source server.</span></span>  
  
     <span data-ttu-id="5e600-212">**상태**</span><span class="sxs-lookup"><span data-stu-id="5e600-212">**Status**</span></span>  
     <span data-ttu-id="5e600-213">데이터베이스를 이동할 수 있는 경우 **확인을** 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-213">Displays **OK** if the database can be moved.</span></span> <span data-ttu-id="5e600-214">그렇지 않은 경우 데이터베이스를 이동하지 못하는 이유를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-214">Otherwise displays the reason why the database cannot be moved.</span></span>  
  
     <span data-ttu-id="5e600-215">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="5e600-215">**Refresh**</span></span>  
     <span data-ttu-id="5e600-216">데이터베이스 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-216">Refresh the list of databases.</span></span>  
  
     <span data-ttu-id="5e600-217">**다음**</span><span class="sxs-lookup"><span data-stu-id="5e600-217">**Next**</span></span>  
     <span data-ttu-id="5e600-218">확인 프로세스를 시작한 후, 다음 화면으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-218">Start the validation process, and then move to the next screen.</span></span>  
  
6.  <span data-ttu-id="5e600-219">**대상 데이터베이스 구성** 페이지에서 데이터베이스 이름을 변경하고(해당하는 경우) 데이터베이스 파일의 위치와 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-219">From the **Configure Destination Database** page, change the database name if appropriate and specify the location and names of the database files.</span></span> <span data-ttu-id="5e600-220">이 페이지는 이동하거나 복사하는 각 데이터베이스에 대해 한 번씩 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-220">This page appears once for each database being moved or copied.</span></span>  
  
7.  <span data-ttu-id="5e600-221">**데이터베이스 개체 선택** 페이지에서 이동 또는 복사 작업에 포함할 개체를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-221">From the **Select Database Objects** page, select the objects to include in the move or copy operation.</span></span> <span data-ttu-id="5e600-222">이 페이지는 원본 서버와 대상 서버가 다를 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-222">This page is only available when the source and destination are different servers.</span></span> <span data-ttu-id="5e600-223">개체를 포함하려면 **사용 가능한 관련 개체** 상자에서 개체 이름을 클릭한 다음 **>>** 단추를 클릭하여 **선택한 관련 개체** 상자로 개체를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-223">To include an object, click the object name in the **Available related objects** box, and then click the **>>** button to move the object to the **Selected related objects** box.</span></span> <span data-ttu-id="5e600-224">개체를 제외 하려면 **선택한 관련 개체** 상자에서 개체 이름을 클릭 한 다음 단추를 클릭 **<\<** 하 여 **사용 가능한 관련 개체** 상자로 개체를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-224">To exclude an object, click the object name in the **Selected related objects** box, and then click the **<\<** button to move the object to the **Available related objects** box.</span></span> <span data-ttu-id="5e600-225">기본적으로 선택한 각 유형의 모든 개체가 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-225">By default all objects of each selected type are transferred.</span></span> <span data-ttu-id="5e600-226">특정 유형의 개별 개체를 선택하려면 **선택한 관련 개체** 상자에서 해당 개체 유형 옆의 줄임표 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-226">To choose individual objects of any type, click the ellipsis button next to any object type in the **Selected related objects** box.</span></span> <span data-ttu-id="5e600-227">그러면 개별 개체를 선택할 수 있는 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-227">This opens a dialog box where you can select individual objects.</span></span>  
  
     <span data-ttu-id="5e600-228">**로그인(런타임 시 모든 로그인)**</span><span class="sxs-lookup"><span data-stu-id="5e600-228">**Logins (All logins at run time)**</span></span>  
     <span data-ttu-id="5e600-229">이동 또는 복사 작업에 로그인을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-229">Include logins in the move or copy operation.</span></span> <span data-ttu-id="5e600-230">기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-230">Selected by default.</span></span>  
  
     <span data-ttu-id="5e600-231">**master 데이터베이스의 저장 프로시저**</span><span class="sxs-lookup"><span data-stu-id="5e600-231">**Stored procedures from master database**</span></span>  
     <span data-ttu-id="5e600-232">**Master** 데이터베이스의 저장 프로시저를 이동 또는 복사 작업에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-232">Include stored procedures from the **master** database in the move or copy operation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e600-233">확장 저장 프로시저 및 이와 관련된 DLL은 자동으로 복사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-233">Extended stored procedures and their associated DLLs are not eligible for automated copy.</span></span>  
  
     <span data-ttu-id="5e600-234">**SQL Server 에이전트 작업**</span><span class="sxs-lookup"><span data-stu-id="5e600-234">**SQL Server Agent jobs**</span></span>  
     <span data-ttu-id="5e600-235">**Msdb** 데이터베이스의 작업을 이동 또는 복사 작업에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-235">Include jobs from the **msdb** database in the move or copy operation.</span></span>  
  
     <span data-ttu-id="5e600-236">**사용자 정의 오류 메시지**</span><span class="sxs-lookup"><span data-stu-id="5e600-236">**User-defined error messages**</span></span>  
     <span data-ttu-id="5e600-237">이동 또는 복사 작업에 사용자 정의 오류 메시지를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-237">Include user-defined error messages in the move or copy operation.</span></span>  
  
     <span data-ttu-id="5e600-238">**엔드포인트**</span><span class="sxs-lookup"><span data-stu-id="5e600-238">**Endpoints**</span></span>  
     <span data-ttu-id="5e600-239">원본 데이터베이스에 정의된 엔드포인트를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-239">Include endpoints defined in the source database.</span></span>  
  
     <span data-ttu-id="5e600-240">**전체 텍스트 카탈로그**</span><span class="sxs-lookup"><span data-stu-id="5e600-240">**Full-text catalog**</span></span>  
     <span data-ttu-id="5e600-241">원본 데이터베이스의 전체 텍스트 카탈로그를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-241">Include full-text catalogs from the source database.</span></span>  
  
     <span data-ttu-id="5e600-242">**SSIS 패키지**</span><span class="sxs-lookup"><span data-stu-id="5e600-242">**SSIS Package**</span></span>  
     <span data-ttu-id="5e600-243">원본 데이터베이스에 정의된 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-243">Include [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages defined in the source database.</span></span>  
  
     <span data-ttu-id="5e600-244">**설명**</span><span class="sxs-lookup"><span data-stu-id="5e600-244">**Description**</span></span>  
     <span data-ttu-id="5e600-245">개체에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-245">A description of the object.</span></span>  
  
8.  <span data-ttu-id="5e600-246">**원본 데이터베이스 파일 위치** 페이지에서 원본 서버의 데이터베이스 파일에 들어 있는 파일 시스템 공유를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-246">From the **Location of Source Database Files** page, specify a file system share that contains the database files on the source server.</span></span> <span data-ttu-id="5e600-247">이는 원본 및 대상 서버 인스턴스가 서로 다른 컴퓨터에 있는 경우 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-247">This is required if the source and destination server instances are on different computers.</span></span>  
  
     <span data-ttu-id="5e600-248">**Database**</span><span class="sxs-lookup"><span data-stu-id="5e600-248">**Database**</span></span>  
     <span data-ttu-id="5e600-249">이동 중인 각 데이터베이스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-249">Displays the name of each database being moved.</span></span>  
  
     <span data-ttu-id="5e600-250">**폴더 위치**</span><span class="sxs-lookup"><span data-stu-id="5e600-250">**Folder location**</span></span>  
     <span data-ttu-id="5e600-251">파일 시스템에 있는 원본 데이터베이스 파일의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-251">Specify the location of the source database files on the file system.</span></span>  
  
     <span data-ttu-id="5e600-252">예: C:\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\DATA</span><span class="sxs-lookup"><span data-stu-id="5e600-252">For example: C:\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\DATA</span></span>  
  
     <span data-ttu-id="5e600-253">**원본 서버의 파일 공유**</span><span class="sxs-lookup"><span data-stu-id="5e600-253">**File share on source server**</span></span>  
     <span data-ttu-id="5e600-254">원본 데이터베이스 파일의 위치를 파일 공유 경로로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-254">Specify the location of the source database files as a path of a file share.</span></span>  
  
     <span data-ttu-id="5e600-255">예: " \\ \\ *server_name*\c $ Files\Microsoft SQL Server\MSSQL110. MSSQLSERVER\MSSQL\Data</span><span class="sxs-lookup"><span data-stu-id="5e600-255">For example: "\\\\*server_name*\C$\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\Data</span></span>  
  
9. <span data-ttu-id="5e600-256">데이터베이스 복사 마법사는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 구성 **페이지에서 데이터베이스를 전송할** 패키지를 만들고 패키지를 사용자 지정합니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="5e600-256">The Copy Database Wizard creates a [!INCLUDE[ssIS](../../includes/ssis-md.md)] package to transfer the database From the **Configure the Package** page, customize the package if appropriate.</span></span>  
  
     <span data-ttu-id="5e600-257">**패키지 위치**</span><span class="sxs-lookup"><span data-stu-id="5e600-257">**Package location**</span></span>  
     <span data-ttu-id="5e600-258">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지를 쓸 위치를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-258">Displays where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package will be written.</span></span>  
  
     <span data-ttu-id="5e600-259">**패키지 이름**</span><span class="sxs-lookup"><span data-stu-id="5e600-259">**Package name**</span></span>  
     <span data-ttu-id="5e600-260">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-260">Enter a name for the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span>  
  
     <span data-ttu-id="5e600-261">**로깅 옵션**</span><span class="sxs-lookup"><span data-stu-id="5e600-261">**Logging options**</span></span>  
     <span data-ttu-id="5e600-262">로깅 정보를 Windows 이벤트 로그에 저장할지 또는 텍스트 파일에 저장할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-262">Select whether to store the logging information in the Windows event log, or in a text file.</span></span>  
  
     <span data-ttu-id="5e600-263">**오류 로그 파일 경로**</span><span class="sxs-lookup"><span data-stu-id="5e600-263">**Error log file path**</span></span>  
     <span data-ttu-id="5e600-264">로그 파일의 위치에 대한 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-264">Provide a path for the location of the log file.</span></span> <span data-ttu-id="5e600-265">이 옵션은 텍스트 파일 로깅 옵션을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-265">This option is only available if the text file logging option is selected.</span></span>  
  
10. <span data-ttu-id="5e600-266">**패키지 예약** 페이지에서 이동 또는 복사 작업을 시작할 시기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-266">From the **Schedule the Package** page, specify when you want the move or copy operation to start.</span></span> <span data-ttu-id="5e600-267">시스템 관리자가 아닌 경우 SSIS( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) 패키지 실행 하위 시스템에 대한 액세스 권한이 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에이전트 프록시 계정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-267">If you are not a system administrator, you must specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy account that has access to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) Package execution subsystem.</span></span>  
  
     <span data-ttu-id="5e600-268">**Run immediately**</span><span class="sxs-lookup"><span data-stu-id="5e600-268">**Run immediately**</span></span>  
     <span data-ttu-id="5e600-269">**다음**을 클릭 하 여 이동 또는 복사 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-269">Start the move or copy operation after you click **Next**.</span></span>  
  
     <span data-ttu-id="5e600-270">**일정**</span><span class="sxs-lookup"><span data-stu-id="5e600-270">**Schedule**</span></span>  
     <span data-ttu-id="5e600-271">나중에 이동 또는 복사 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-271">Start the move or copy operation later.</span></span> <span data-ttu-id="5e600-272">현재 설정된 일정은 설명란에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-272">The current schedule settings appear in the description box.</span></span> <span data-ttu-id="5e600-273">일정을 변경하려면 **변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-273">To change the schedule, click **Change**.</span></span>  
  
     <span data-ttu-id="5e600-274">**변경**</span><span class="sxs-lookup"><span data-stu-id="5e600-274">**Change**</span></span>  
     <span data-ttu-id="5e600-275">**새 작업 일정** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-275">Open the **New Job Schedule** dialog box.</span></span>  
  
     <span data-ttu-id="5e600-276">**Integration Services 프록시 계정**</span><span class="sxs-lookup"><span data-stu-id="5e600-276">**Integration Services proxy account**</span></span>  
     <span data-ttu-id="5e600-277">사용 가능한 프록시 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-277">Select an available proxy account.</span></span> <span data-ttu-id="5e600-278">전송을 예약하려면 **SQL Server Integration Services 패키지 실행** 하위 시스템에 대한 사용 권한으로 구성되어 사용자가 사용할 수 있는 프록시 계정이 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-278">To schedule the transfer, there must be at least one proxy account available to the user, configured with permission to the **SQL Server Integration Services package execution** subsystem.</span></span>  
  
     <span data-ttu-id="5e600-279">패키지 실행을 위한 프록시 계정을 만들려면 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 개체 탐색기에서 **SQL Server 에이전트**, **프록시**를 차례로 확장 하 고 **SSIS 패키지 실행**을 마우스 오른쪽 단추로 클릭 한 다음 **새 프록시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-279">To create a proxy account for [!INCLUDE[ssIS](../../includes/ssis-md.md)] package execution, in Object Explorer, expand **SQL Server Agent**, expand **Proxies**, right-click **SSIS Package Execution**, and then click **New Proxy**.</span></span>  
  
     <span data-ttu-id="5e600-280">**sysadmin** 고정 서버 역할의 멤버는 필요한 권한이 있는 **SQL Server 에이전트 서비스 계정**을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-280">Members of the **sysadmin** fixed server role can select the **SQL Server Agent Service Account**, which has the necessary permissions.</span></span>  
  
11. <span data-ttu-id="5e600-281">**마법사 완료** 페이지에서 선택한 옵션의 요약 내용을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-281">From the **Complete the Wizard** page, review the summary of the selected options.</span></span> <span data-ttu-id="5e600-282">옵션을 변경하려면 **뒤로** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-282">Click **Back** to change an option.</span></span> <span data-ttu-id="5e600-283">**마침** 을 클릭하여 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-283">Click **Finish** to create the database.</span></span> <span data-ttu-id="5e600-284">전송하는 동안 **작업을 수행하는 중** 페이지에서 **데이터베이스 복사 마법사**실행과 관련한 상태 정보를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-284">During the transfer, the **Performing operation** page monitors status information about the execution of the **Copy Database Wizard**.</span></span>  
  
     <span data-ttu-id="5e600-285">**동작**</span><span class="sxs-lookup"><span data-stu-id="5e600-285">**Action**</span></span>  
     <span data-ttu-id="5e600-286">수행 중인 동작을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-286">Lists each action being performed.</span></span>  
  
     <span data-ttu-id="5e600-287">**상태**</span><span class="sxs-lookup"><span data-stu-id="5e600-287">**Status**</span></span>  
     <span data-ttu-id="5e600-288">전반적으로 성공한 동작인지 아니면 실패한 동작인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-288">Indicates whether the action as a whole succeeded or failed.</span></span>  
  
     <span data-ttu-id="5e600-289">**Message**</span><span class="sxs-lookup"><span data-stu-id="5e600-289">**Message**</span></span>  
     <span data-ttu-id="5e600-290">각 단계에서 반환된 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-290">Provides any messages returned from each step.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> <span data-ttu-id="5e600-291">후속 작업: SQL Server 데이터베이스를 업그레이드한 후</span><span class="sxs-lookup"><span data-stu-id="5e600-291">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="5e600-292">데이터베이스 복사 마법사를 사용하여 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]버전으로 데이터베이스를 업그레이드하면 데이터베이스를 바로 사용할 수 있으며 데이터베이스가 자동으로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-292">After you use the Copy Database Wizard to upgrade a database from an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database becomes available immediately and is automatically upgraded.</span></span> <span data-ttu-id="5e600-293">데이터베이스에 전체 텍스트 인덱스가 있는 경우 업그레이드 프로세스는 **전체 텍스트 업그레이드 옵션** 서버 속성의 설정에 따라 인덱스를 가져오거나, 다시 설정하거나, 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-293">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **Full-Text Upgrade Option** server property.</span></span> <span data-ttu-id="5e600-294">업그레이드 옵션이 **가져오기** 또는 **다시 작성**으로 설정되어 있는 경우 업그레이드하는 동안 전체 텍스트 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-294">If the upgrade option is set to **Import** or **Rebuild**, the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="5e600-295">인덱싱되는 데이터 양에 따라 가져오기 작업은 몇 시간씩 걸릴 수 있으며 다시 작성 작업은 10배 정도 더 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-295">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="5e600-296">업그레이드 옵션이 **가져오기**로 설정되어 있으면 전체 텍스트 카탈로그를 사용할 수 없는 경우 관련된 전체 텍스트 인덱스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-296">Note also that when the upgrade option is set to **Import**, if a full-text catalog is not available, the associated full-text indexes are rebuilt.</span></span> <span data-ttu-id="5e600-297">**전체 텍스트 업그레이드 옵션** 속성 설정을 보거나 변경하는 방법은 [서버 인스턴스의 전체 텍스트 검색 관리 및 모니터링](../search/manage-and-monitor-full-text-search-for-a-server-instance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e600-297">For information about viewing or changing the setting of the **Full-Text Upgrade Option** property, see [Manage and Monitor Full-Text Search for a Server Instance](../search/manage-and-monitor-full-text-search-for-a-server-instance.md).</span></span>  
  
 <span data-ttu-id="5e600-298">사용자 데이터베이스의 호환성 수준이 업그레이드 이전에 100 이상이었다면 업그레이드 후에도 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-298">If the compatibility level of a user database was 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="5e600-299">업그레이드한 데이터베이스의 호환성 수준이 이전에 90이었다면 업그레이드 후에는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 지원되는 가장 낮은 호환성 수준인 100으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e600-299">If the compatibility level was 90 in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="5e600-300">자세한 내용은 [ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e600-300">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e600-301">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e600-301">See Also</span></span>  
 <span data-ttu-id="5e600-302">[분리 및 연결을 사용 하 여 데이터베이스 업그레이드 &#40;Transact-sql&#41;](upgrade-a-database-using-detach-and-attach-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="5e600-302">[Upgrade a Database Using Detach and Attach &#40;Transact-SQL&#41;](upgrade-a-database-using-detach-and-attach-transact-sql.md) </span></span>  
 [<span data-ttu-id="5e600-303">SQL Server 에이전트 프록시 만들기</span><span class="sxs-lookup"><span data-stu-id="5e600-303">Create a SQL Server Agent Proxy</span></span>](../../ssms/agent/create-a-sql-server-agent-proxy.md)  
  
  
