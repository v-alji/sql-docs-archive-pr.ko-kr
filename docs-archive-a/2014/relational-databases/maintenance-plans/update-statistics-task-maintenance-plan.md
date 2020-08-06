---
title: 통계 업데이트 태스크(유지 관리 계획) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.statistics.f1
helpviewer_keywords:
- Updates Statistics Task dialog box
ms.assetid: 22902fd0-eb39-4f18-af94-3fcb69d2a3a4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 486ef2da96785ed200900f497435117ef6437cb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661101"
---
# <a name="update-statistics-task-maintenance-plan"></a><span data-ttu-id="21305-102">통계 업데이트 태스크(유지 관리 계획)</span><span class="sxs-lookup"><span data-stu-id="21305-102">Update Statistics Task (Maintenance Plan)</span></span>
  <span data-ttu-id="21305-103">**통계 업데이트 태스크** 대화 상자를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 테이블 및 인덱스 데이터 정보를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21305-103">Use the **Update Statistics Task** dialog to update [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information about the data in the tables and indexes.</span></span> <span data-ttu-id="21305-104">데이터베이스의 사용자 테이블에 작성된 각 인덱스의 배포 통계를 다시 샘플링합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-104">This task resamples the distribution statistics of each index created on user tables in the database.</span></span> <span data-ttu-id="21305-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 사용하는 배포 통계는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 처리하는 동안 테이블 탐색을 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-105">The distribution statistics are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to optimize navigation through tables during the processing of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="21305-106">배포 통계를 자동으로 구축하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 각 인덱스에 대한 해당 테이블에서 데이터를 주기적으로 샘플링합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-106">To build the distribution statistics automatically, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically samples the data in the corresponding table for each index.</span></span> <span data-ttu-id="21305-107">샘플링하는 양은 테이블의 행 수와 데이터 수정 빈도를 기초로 정해집니다.</span><span class="sxs-lookup"><span data-stu-id="21305-107">This size of the sample is based on the number of rows in the table and the frequency of data modification.</span></span> <span data-ttu-id="21305-108">테이블에서 지정한 비율의 데이터를 사용하여 추가 샘플링을 수행하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-108">Use this option to perform an additional sampling using the specified percentage of data in the tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="21305-109">는 이 정보를 사용하여 보다 향상된 쿼리 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="21305-109">uses this information to create better query plans.</span></span>  
  
 <span data-ttu-id="21305-110">이 태스크는 UPDATE STATISTICS 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-110">This task executes the UPDATE STATISTICS statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="21305-111">옵션</span><span class="sxs-lookup"><span data-stu-id="21305-111">Options</span></span>  
 <span data-ttu-id="21305-112">**연결**</span><span class="sxs-lookup"><span data-stu-id="21305-112">**Connection**</span></span>  
 <span data-ttu-id="21305-113">이 태스크를 수행할 때 사용할 서버 연결을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-113">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="21305-114">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="21305-114">**New**</span></span>  
 <span data-ttu-id="21305-115">이 태스크를 수행할 때 사용할 새 서버 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="21305-115">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="21305-116">아래에서는 **새 연결** 대화 상자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-116">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="21305-117">**데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="21305-117">**Databases**</span></span>  
 <span data-ttu-id="21305-118">이 태스크의 영향을 받는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-118">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="21305-119">**모든 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="21305-119">**All databases**</span></span>  
  
     <span data-ttu-id="21305-120">tempdb를 제외한 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-120">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, except tempdb.</span></span>  
  
-   <span data-ttu-id="21305-121">**모든 시스템 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="21305-121">**All system databases**</span></span>  
  
     <span data-ttu-id="21305-122">tempdb를 제외한 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-122">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="21305-123">사용자가 만든 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21305-123">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="21305-124">**모든 사용자 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="21305-124">**All user databases**</span></span>  
  
     <span data-ttu-id="21305-125">사용자가 만든 모든 데이터베이스에 대해 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-125">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="21305-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터베이스에 대해서는 유지 관리 태스크가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21305-126">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="21305-127">**다음 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="21305-127">**These specific databases**</span></span>  
  
     <span data-ttu-id="21305-128">선택한 데이터베이스에 대해서만 유지 관리 태스크를 실행하는 유지 관리 계획을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-128">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="21305-129">이 옵션을 선택한 경우에는 목록에서 하나 이상의 데이터베이스를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-129">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="21305-130">**참고** 유지 관리 계획은 호환성 수준 80 이상으로 설정된 데이터베이스에 대해서만 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-130">**Note** Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="21305-131">호환성 수준 70 이하로 설정된 데이터베이스는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="21305-131">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="21305-132">**Object**</span><span class="sxs-lookup"><span data-stu-id="21305-132">**Object**</span></span>  
 <span data-ttu-id="21305-133">테이블, 뷰 또는 둘 다를 표시하도록 **선택** 표를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-133">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="21305-134">**선택**</span><span class="sxs-lookup"><span data-stu-id="21305-134">**Selection**</span></span>  
 <span data-ttu-id="21305-135">이 태스크의 영향을 받는 테이블 또는 인덱스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-135">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="21305-136">개체 상자에서 **테이블 및 뷰** 를 선택한 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21305-136">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
 <span data-ttu-id="21305-137">**모든 기존 통계**</span><span class="sxs-lookup"><span data-stu-id="21305-137">**All existing statistics**</span></span>  
 <span data-ttu-id="21305-138">열과 인덱스의 통계를 모두 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-138">Update statistics for both columns and indexes.</span></span>  
  
 <span data-ttu-id="21305-139">**열 통계만**</span><span class="sxs-lookup"><span data-stu-id="21305-139">**Column statistics only**</span></span>  
 <span data-ttu-id="21305-140">열 통계만 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-140">Only update column statistics.</span></span>  
  
 <span data-ttu-id="21305-141">**인덱스 통계만**</span><span class="sxs-lookup"><span data-stu-id="21305-141">**Index statistics only**</span></span>  
 <span data-ttu-id="21305-142">인덱스 통계만 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-142">Only update index statistics.</span></span>  
  
 <span data-ttu-id="21305-143">**검색 유형**</span><span class="sxs-lookup"><span data-stu-id="21305-143">**Scan type**</span></span>  
 <span data-ttu-id="21305-144">업데이트된 통계를 수집하는 데 사용되는 검색 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="21305-144">Type of scan used to gather updated statistics.</span></span>  
  
 <span data-ttu-id="21305-145">**전체 검색**</span><span class="sxs-lookup"><span data-stu-id="21305-145">**Full scan**</span></span>  
 <span data-ttu-id="21305-146">통계를 수집하기 위해 테이블이나 뷰의 모든 행을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="21305-146">Read all rows in the table or view to gather the statistics.</span></span>  
  
 <span data-ttu-id="21305-147">**샘플링 기준**</span><span class="sxs-lookup"><span data-stu-id="21305-147">**Sample by**</span></span>  
 <span data-ttu-id="21305-148">보다 큰 테이블이나 뷰에 대한 통계를 수집할 때 샘플링할 행의 수 또는 테이블이나 인덱싱된 뷰의 백분율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-148">Specify the percentage of the table or indexed view, or the number of rows to sample when collecting statistics for larger tables or views.</span></span>  
  
 <span data-ttu-id="21305-149">**T-SQL 보기**</span><span class="sxs-lookup"><span data-stu-id="21305-149">**View T-SQL**</span></span>  
 <span data-ttu-id="21305-150">선택한 옵션을 기반으로 서버에 대해 수행한 이 태스크의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-150">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="21305-151">영향을 받은 개체 수가 많은 경우에는 표시하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21305-151">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="21305-152">새 연결 대화 상자</span><span class="sxs-lookup"><span data-stu-id="21305-152">New Connection Dialog Box</span></span>  
 <span data-ttu-id="21305-153">**연결 이름**</span><span class="sxs-lookup"><span data-stu-id="21305-153">**Connection name**</span></span>  
 <span data-ttu-id="21305-154">새 연결의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-154">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="21305-155">**서버 이름 선택 또는 입력**</span><span class="sxs-lookup"><span data-stu-id="21305-155">**Select or enter a server name**</span></span>  
 <span data-ttu-id="21305-156">이 태스크를 수행할 때 연결할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-156">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="21305-157">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="21305-157">**Refresh**</span></span>  
 <span data-ttu-id="21305-158">사용할 수 있는 서버 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="21305-158">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="21305-159">**서버 로그온 정보 입력**</span><span class="sxs-lookup"><span data-stu-id="21305-159">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="21305-160">서버에 대한 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-160">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="21305-161">**Windows NT 통합 보안 사용**</span><span class="sxs-lookup"><span data-stu-id="21305-161">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="21305-162">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-162">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="21305-163">**특정 사용자 이름 및 암호 사용**</span><span class="sxs-lookup"><span data-stu-id="21305-163">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="21305-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-164">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="21305-165">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21305-165">This option is not available.</span></span>  
  
 <span data-ttu-id="21305-166">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="21305-166">**User name**</span></span>  
 <span data-ttu-id="21305-167">인증 시 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-167">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="21305-168">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21305-168">This option is not available.</span></span>  
  
 <span data-ttu-id="21305-169">**암호**</span><span class="sxs-lookup"><span data-stu-id="21305-169">**Password**</span></span>  
 <span data-ttu-id="21305-170">인증 시 사용할 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="21305-170">Provide a password to use when authenticating.</span></span> <span data-ttu-id="21305-171">이 옵션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="21305-171">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21305-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="21305-172">See Also</span></span>  
 [<span data-ttu-id="21305-173">UPDATE STATISTICS&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21305-173">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
