---
title: 데이터베이스 축소 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.shrink.f1
- Shrink Database Task
- Shrink Database(s) Task
helpviewer_keywords:
- Shrink Database Task dialog box
ms.assetid: a9874cac-cded-4145-9c38-8aafd267dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b8ee6060a4ee6ca3272434cf3d9115638a675e62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731564"
---
# <a name="shrink-database-task-maintenance-plan"></a><span data-ttu-id="07034-102">데이터베이스 축소 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="07034-102">Shrink Database Task (Maintenance Plan)</span></span>
  <span data-ttu-id="07034-103">**데이터베이스 축소 태스크** 대화 상자를 사용하여 선택한 데이터베이스의 크기를 줄이는 작업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-103">Use the **Shrink Database Task** dialog to create a task that attempts to reduce the size of the selected databases.</span></span> <span data-ttu-id="07034-104">아래 옵션을 사용하면 데이터베이스를 축소한 후 사용되지 않는 상태로 데이터베이스에 유지할 공간의 양을 결정할 수 있습니다. 이 비율이 커질수록 데이터베이스를 축소할 수 있는 비율이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="07034-104">Use the options below to determine the amount of unused space to remain in the database after the database is shrunk (the larger the percentage, the less the database can shrink).</span></span> <span data-ttu-id="07034-105">이 값은 데이터베이스에 있는 실제 데이터의 비율에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="07034-105">The value is based on the percentage of the actual data in the database.</span></span> <span data-ttu-id="07034-106">예를 들어 60MB의 데이터와 40MB의 사용 가능한 공간이 있는 100MB의 데이터베이스에서 사용 가능한 공간의 비율을 50%로 설정하면 60MB의 50%는 30MB이기 때문에 데이터 공간은 60MB가 되고 사용 가능한 공간은 30MB가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07034-106">For example, a 100-MB database containing 60 MB of data and 40 MB of free space, with a free space percentage of 50 percent, would result in 60 MB of data and 30 MB of free space (because 50 percent of 60 MB is 30 MB).</span></span> <span data-ttu-id="07034-107">데이터베이스에서 남는 공간만 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="07034-107">Only excess space in the database is eliminated.</span></span> <span data-ttu-id="07034-108">유효한 값은 0에서 100까지입니다.</span><span class="sxs-lookup"><span data-stu-id="07034-108">Valid values are from 0 through 100.</span></span>  
  
 <span data-ttu-id="07034-109">파일 끝에 있는 데이터 페이지를 파일 앞의 사용되지 않은 공간으로 이동하여 데이터 파일을 축소하면 공간이 복구됩니다.</span><span class="sxs-lookup"><span data-stu-id="07034-109">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="07034-110">파일 끝에 사용 가능한 공간을 충분히 확보한 다음 파일 끝에 있는 데이터 페이지를 할당 해제하고 파일 시스템에 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-110">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="07034-111">파일 축소를 위해 이동되는 데이터는 파일 내의 모든 사용 가능한 위치로 분산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-111">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="07034-112">이로 인해 인덱스 조각화가 발생하여 인덱스 범위를 검색하는 쿼리 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-112">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="07034-113">조각화를 방지하려면 축소 후 파일에 대한 인덱스를 다시 작성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-113">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
 <span data-ttu-id="07034-114">이 태스크는 DBCC SHRINKDATABASE 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-114">This task executes the DBCC SHRINKDATABASE statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="07034-115">옵션</span><span class="sxs-lookup"><span data-stu-id="07034-115">Options</span></span>  
 <span data-ttu-id="07034-116">**연결**</span><span class="sxs-lookup"><span data-stu-id="07034-116">**Connection**</span></span>  
 <span data-ttu-id="07034-117">이 태스크를 수행할 때 사용할 서버 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-117">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="07034-118">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="07034-118">**New**</span></span>  
 <span data-ttu-id="07034-119">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="07034-119">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="07034-120">아래에서는 **새 연결** 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-120">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="07034-121">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="07034-121">**Databases**</span></span>  
 <span data-ttu-id="07034-122">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-122">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="07034-123">**모든 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="07034-123">**All databases**</span></span>  
  
     <span data-ttu-id="07034-124">tempdb를 제외한 모든 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-124">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="07034-125">**모든 시스템 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="07034-125">**All system databases**</span></span>  
  
     <span data-ttu-id="07034-126">tempdb를 제외한 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-126">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="07034-127">사용자가 만든 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-127">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="07034-128">**모든 사용자 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="07034-128">**All user databases**</span></span>  
  
     <span data-ttu-id="07034-129">사용자가 만든 모든 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-129">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="07034-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-130">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="07034-131">**다음 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="07034-131">**These databases**</span></span>  
  
     <span data-ttu-id="07034-132">선택한 데이터베이스에 대해서만 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-132">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="07034-133">이 옵션을 선택한 경우에는 목록에서 하나 이상의 데이터베이스를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-133">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="07034-134">유지 관리 계획은 호환성 수준 80 이상으로 설정된 데이터베이스에 대해서만 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-134">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="07034-135">호환성 수준 70 이하로 설정된 데이터베이스는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-135">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="07034-136">**데이터베이스 크기가 다음을 초과하면 축소**</span><span class="sxs-lookup"><span data-stu-id="07034-136">**Shrink database when it grows beyond**</span></span>  
 <span data-ttu-id="07034-137">데이터베이스 축소 태스크를 시작하는 기준이 되는 크기(MB)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-137">Specify the size in megabytes that causes the task to execute.</span></span>  
  
 <span data-ttu-id="07034-138">**축소 후 데이터 공간 유지 비율**</span><span class="sxs-lookup"><span data-stu-id="07034-138">**Amount of free space to remain after shrink**</span></span>  
 <span data-ttu-id="07034-139">데이터베이스 파일의 사용 가능한 공간이 이 크기에 도달하면 축소를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-139">Stop shrinking when free space in database files reaches this size.</span></span>  
  
 <span data-ttu-id="07034-140">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="07034-140">**View T-SQL**</span></span>  
 <span data-ttu-id="07034-141">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-141">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07034-142">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-142">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="07034-143">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="07034-143">New Connection Dialog Box</span></span>  
 <span data-ttu-id="07034-144">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="07034-144">**Connection name**</span></span>  
 <span data-ttu-id="07034-145">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-145">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="07034-146">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="07034-146">**Select or enter a server name**</span></span>  
 <span data-ttu-id="07034-147">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-147">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="07034-148">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="07034-148">**Refresh**</span></span>  
 <span data-ttu-id="07034-149">사용할 수 있는 서버 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="07034-149">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="07034-150">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="07034-150">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="07034-151">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-151">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="07034-152">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="07034-152">**Use Windows NT Integrated security**</span></span>  
 <span data-ttu-id="07034-153">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-153">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="07034-154">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="07034-154">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="07034-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-155">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="07034-156">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-156">This option is not available.</span></span>  
  
 <span data-ttu-id="07034-157">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="07034-157">**User name**</span></span>  
 <span data-ttu-id="07034-158">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-158">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="07034-159">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-159">This option is not available.</span></span>  
  
 <span data-ttu-id="07034-160">**암호**</span><span class="sxs-lookup"><span data-stu-id="07034-160">**Password**</span></span>  
 <span data-ttu-id="07034-161">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="07034-161">Provide a password to use when authenticating.</span></span> <span data-ttu-id="07034-162">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07034-162">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07034-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07034-163">See Also</span></span>  
 [<span data-ttu-id="07034-164">DBCC SHRINKDATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07034-164">DBCC SHRINKDATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)  
  
  
