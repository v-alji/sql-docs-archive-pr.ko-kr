---
title: 인덱스 다시 빌드 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reindex.f1
- reindex
helpviewer_keywords:
- Rebuild Index Task dialog box
ms.assetid: 33e2940b-139f-4563-b0cb-5683f08bd879
author: rothja
ms.author: jroth
ms.openlocfilehash: bc9d7c85a72c34cee1ef7af8cb4b4f25f918a3fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649515"
---
# <a name="rebuild-index-task-maintenance-plan"></a><span data-ttu-id="f3473-102">인덱스 다시 작성 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="f3473-102">Rebuild Index Task (Maintenance Plan)</span></span>
  <span data-ttu-id="f3473-103">**인덱스 다시 작성 태스크** 대화 상자를 사용하여 데이터베이스에 있는 테이블의 인덱스를 새 채우기 비율로 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-103">Use the **Rebuild Index Task** dialog to re-create the indexes on the tables in the database with a new fill factor.</span></span> <span data-ttu-id="f3473-104">채우기 비율은 향후 확장을 수용하기 위해 각 인덱스 페이지에 남겨 둘 빈 공간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-104">The fill factor determines the amount of empty space on each page in the index, to accommodate future expansion.</span></span> <span data-ttu-id="f3473-105">데이터를 테이블에 추가할 때는 채우기 비율이 유지되지 않으므로 사용 가능한 공간이 꽉 찹니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-105">As data is added to the table, the free space fills because the fill factor is not maintained.</span></span> <span data-ttu-id="f3473-106">데이터 및 인덱스 페이지를 다시 구성하면 사용 가능한 공간을 다시 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-106">Reorganizing data and index pages can re-establish the free space.</span></span>  
  
 <span data-ttu-id="f3473-107">**인덱스 다시 작성 태스크** 는 ALTER INDEX 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-107">The **Rebuild Index Task** uses the ALTER INDEX statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f3473-108">옵션</span><span class="sxs-lookup"><span data-stu-id="f3473-108">Options</span></span>  
 <span data-ttu-id="f3473-109">**연결**</span><span class="sxs-lookup"><span data-stu-id="f3473-109">**Connection**</span></span>  
 <span data-ttu-id="f3473-110">이 태스크를 수행할 때 사용할 서버 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-110">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="f3473-111">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="f3473-111">**New**</span></span>  
 <span data-ttu-id="f3473-112">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-112">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="f3473-113">아래에서는 **새 연결** 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-113">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="f3473-114">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="f3473-114">**Databases**</span></span>  
 <span data-ttu-id="f3473-115">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-115">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="f3473-116">**모든 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="f3473-116">**All databases**</span></span>  
  
     <span data-ttu-id="f3473-117">tempdb를 제외한 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-117">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="f3473-118">**모든 시스템 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="f3473-118">**All system databases**</span></span>  
  
     <span data-ttu-id="f3473-119">tempdb를 제외한 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-119">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="f3473-120">사용자가 만든 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-120">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="f3473-121">**모든 사용자 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="f3473-121">**All user databases**</span></span>  
  
     <span data-ttu-id="f3473-122">사용자가 만든 모든 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-122">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="f3473-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-123">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="f3473-124">**다음 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="f3473-124">**These specific databases**</span></span>  
  
     <span data-ttu-id="f3473-125">선택한 데이터베이스에 대해서만 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-125">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="f3473-126">이 옵션을 선택한 경우에는 목록에서 하나 이상의 데이터베이스를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-126">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f3473-127">유지 관리 계획은 호환성 수준 80 이상으로 설정된 데이터베이스에 대해서만 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-127">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="f3473-128">호환성 수준 70 이하로 설정된 데이터베이스는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-128">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="f3473-129">**Object**</span><span class="sxs-lookup"><span data-stu-id="f3473-129">**Object**</span></span>  
 <span data-ttu-id="f3473-130">테이블, 뷰 또는 둘 다를 표시하도록 **선택** 표를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-130">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="f3473-131">**선택**</span><span class="sxs-lookup"><span data-stu-id="f3473-131">**Selection**</span></span>  
 <span data-ttu-id="f3473-132">이 태스크의 영향을 받는 테이블 또는 인덱스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-132">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="f3473-133">개체 상자에서 **테이블 및 뷰** 를 선택한 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-133">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
 <span data-ttu-id="f3473-134">**사용 가능한 공간의 기본 크기로 페이지 다시 구성**</span><span class="sxs-lookup"><span data-stu-id="f3473-134">**Reorganize pages with the default amount of free space**</span></span>  
 <span data-ttu-id="f3473-135">데이터베이스 테이블의 인덱스를 삭제하고 인덱스를 만들 때 지정한 채우기 비율로 인덱스를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-135">Drop the indexes on the tables in the database and re-create them with the fill factor that was specified when the indexes were created.</span></span>  
  
 <span data-ttu-id="f3473-136">**페이지당 빈 공간 비율을 다음으로 변경**</span><span class="sxs-lookup"><span data-stu-id="f3473-136">**Change free space per page percentage to**</span></span>  
 <span data-ttu-id="f3473-137">데이터베이스 테이블의 인덱스를 삭제하고 자동으로 계산된 새 채우기 비율로 인덱스를 다시 만들기 때문에 인덱스 페이지에 대해 지정된 크기의 사용 가능한 공간이 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-137">Drop the indexes on the tables in the database and re-create them with a new, automatically calculated fill factor, thereby reserving the specified amount of free space on the index pages.</span></span> <span data-ttu-id="f3473-138">이 비율이 커질수록 인덱스 페이지에 대해 더 많은 사용 가능한 공간이 예약되고 인덱스가 더 커집니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-138">The higher the percentage, the more free space is reserved on the index pages, and the larger the index grows.</span></span> <span data-ttu-id="f3473-139">유효한 값은 0에서 100까지입니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-139">Valid values are from 0 through 100.</span></span>  
  
 <span data-ttu-id="f3473-140">**tempdb에 결과 정렬**</span><span class="sxs-lookup"><span data-stu-id="f3473-140">**Sort results in tempdb**</span></span>  
 <span data-ttu-id="f3473-141">인덱스를 `SORT_IN_TEMPDB` 만드는 동안 생성 된 중간 정렬 결과가 일시적으로 저장 되는 위치를 결정 하는 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-141">Use the `SORT_IN_TEMPDB`option, which determines where the intermediate sort results, generated during index creation, are temporarily stored.</span></span> <span data-ttu-id="f3473-142">정렬 작업이 필요하지 않거나 메모리에서 정렬을 수행할 수 있으면 `SORT_IN_TEMPDB`옵션이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-142">If a sort operation is not required, or if the sort can be performed in memory, the `SORT_IN_TEMPDB`option is ignored.</span></span>  
  
 <span data-ttu-id="f3473-143">**인덱스를 다시 만드는 동안 인덱스를 온라인으로 유지**</span><span class="sxs-lookup"><span data-stu-id="f3473-143">**Keep index online while reindexing**</span></span>  
 <span data-ttu-id="f3473-144">사용자가 인덱스 작업을 수행하는 동안 기본 테이블이나 클러스터형 인덱스 데이터 및 연관된 모든 비클러스터형 인덱스에 액세스할 수 있는 `ONLINE` 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-144">Use the `ONLINE` option which allows users to access the underlying table or clustered index data and any associated nonclustered indexes during index operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3473-145">온라인 인덱스 작업은 일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-145">Online index operations are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f3473-146">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f3473-146">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="f3473-147">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="f3473-147">**View T-SQL**</span></span>  
 <span data-ttu-id="f3473-148">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-148">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3473-149">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-149">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="f3473-150">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="f3473-150">New Connection Dialog Box</span></span>  
 <span data-ttu-id="f3473-151">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="f3473-151">**Connection name**</span></span>  
 <span data-ttu-id="f3473-152">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-152">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="f3473-153">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="f3473-153">**Select or enter a server name**</span></span>  
 <span data-ttu-id="f3473-154">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-154">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="f3473-155">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="f3473-155">**Refresh**</span></span>  
 <span data-ttu-id="f3473-156">사용할 수 있는 서버 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-156">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="f3473-157">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="f3473-157">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="f3473-158">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-158">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="f3473-159">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="f3473-159">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="f3473-160">Windows 인증을 사용하여 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-160">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="f3473-161">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="f3473-161">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="f3473-162">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-162">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="f3473-163">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-163">This option is not available.</span></span>  
  
 <span data-ttu-id="f3473-164">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="f3473-164">**User name**</span></span>  
 <span data-ttu-id="f3473-165">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-165">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="f3473-166">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-166">This option is not available.</span></span>  
  
 <span data-ttu-id="f3473-167">**암호**</span><span class="sxs-lookup"><span data-stu-id="f3473-167">**Password**</span></span>  
 <span data-ttu-id="f3473-168">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-168">Provide a password to use when authenticating.</span></span> <span data-ttu-id="f3473-169">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3473-169">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3473-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3473-170">See Also</span></span>  
 <span data-ttu-id="f3473-171">[ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f3473-171">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="f3473-172">[DBCC DBREINDEX&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f3473-172">[DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) </span></span>  
 <span data-ttu-id="f3473-173">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f3473-173">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="f3473-174">[인덱스에 대한 SORT_IN_TEMPDB 옵션](../indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="f3473-174">[SORT_IN_TEMPDB Option For Indexes](../indexes/indexes.md) </span></span>  
 <span data-ttu-id="f3473-175">[온라인 인덱스 작업에 대한 지침](../indexes/guidelines-for-online-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="f3473-175">[Guidelines for Online Index Operations](../indexes/guidelines-for-online-index-operations.md) </span></span>  
 <span data-ttu-id="f3473-176">[온라인 인덱스 작동 방식](../indexes/how-online-index-operations-work.md) </span><span class="sxs-lookup"><span data-stu-id="f3473-176">[How Online Index Operations Work](../indexes/how-online-index-operations-work.md) </span></span>  
 [<span data-ttu-id="f3473-177">온라인으로 인덱스 작업 수행</span><span class="sxs-lookup"><span data-stu-id="f3473-177">Perform Index Operations Online</span></span>](../indexes/perform-index-operations-online.md)  
  
  
