---
title: 파일 축소 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkfile.f1
helpviewer_keywords:
- shrinking files
- decreasing file size
- databases [SQL Server], shrinking
- reducing file size
- size [SQL Server], files
- file size [SQL Server]
ms.assetid: ce5c8798-c039-4ab2-81e7-90a8d688b893
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac69e4bd2db3ef7fe0815d235dd1de7d3396b302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728328"
---
# <a name="shrink-a-file"></a><span data-ttu-id="66285-102">파일 축소</span><span class="sxs-lookup"><span data-stu-id="66285-102">Shrink a File</span></span>
  <span data-ttu-id="66285-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터 또는 로그 파일을 축소하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-103">This topic describes how to shrink a data or log file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="66285-104">파일 끝에 있는 데이터 페이지를 파일 앞의 사용되지 않은 공간으로 이동하여 데이터 파일을 축소하면 공간이 복구됩니다.</span><span class="sxs-lookup"><span data-stu-id="66285-104">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="66285-105">파일 끝에 사용 가능한 공간을 충분히 확보한 다음 파일 끝에 있는 데이터 페이지를 할당 해제하고 파일 시스템에 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-105">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
 <span data-ttu-id="66285-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="66285-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="66285-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="66285-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="66285-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="66285-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="66285-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="66285-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="66285-110">보안</span><span class="sxs-lookup"><span data-stu-id="66285-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="66285-111">**데이터 또는 로그 파일을 축소하려면:**</span><span class="sxs-lookup"><span data-stu-id="66285-111">**To shrink a data or log file, using:**</span></span>  
  
     [<span data-ttu-id="66285-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="66285-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="66285-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="66285-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="66285-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="66285-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="66285-115">제한 사항</span><span class="sxs-lookup"><span data-stu-id="66285-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="66285-116">주 데이터 파일은 model 데이터베이스에 있는 주 파일의 크기보다 작게 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-116">The primary data file cannot be made smaller than the size of the primary file in the model database.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="66285-117">권장 사항</span><span class="sxs-lookup"><span data-stu-id="66285-117">Recommendations</span></span>  
  
-   <span data-ttu-id="66285-118">파일 축소를 위해 이동되는 데이터는 파일 내의 모든 사용 가능한 위치로 분산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-118">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="66285-119">이로 인해 인덱스 조각화가 발생하여 인덱스 범위를 검색하는 쿼리 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-119">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="66285-120">조각화를 방지하려면 축소 후 파일에 대한 인덱스를 다시 작성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-120">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="66285-121">보안</span><span class="sxs-lookup"><span data-stu-id="66285-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="66285-122">권한</span><span class="sxs-lookup"><span data-stu-id="66285-122">Permissions</span></span>  
 <span data-ttu-id="66285-123">**sysadmin** 고정 서버 역할의 멤버 또는 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-123">Requires membership in the **sysadmin** fixed server role or the **db_owner** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="66285-124">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="66285-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-shrink-a-data-or-log-file"></a><span data-ttu-id="66285-125">데이터 또는 로그 파일을 축소하려면</span><span class="sxs-lookup"><span data-stu-id="66285-125">To shrink a data or log file</span></span>  
  
1.  <span data-ttu-id="66285-126">개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-126">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="66285-127">**데이터베이스** 를 확장한 다음 축소할 데이터베이스를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-127">Expand **Databases** and then right-click the database that you want to shrink.</span></span>  
  
3.  <span data-ttu-id="66285-128">**태스크**, **축소**를 차례로 가리킨 다음 **파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-128">Point to **Tasks**, point to **Shrink**, and then click **Files**.</span></span>  
  
     <span data-ttu-id="66285-129">**Database**</span><span class="sxs-lookup"><span data-stu-id="66285-129">**Database**</span></span>  
     <span data-ttu-id="66285-130">선택한 데이터베이스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-130">Displays the name of the selected database.</span></span>  
  
     <span data-ttu-id="66285-131">**파일 유형**</span><span class="sxs-lookup"><span data-stu-id="66285-131">**File type**</span></span>  
     <span data-ttu-id="66285-132">파일의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-132">Select the file type for the file.</span></span> <span data-ttu-id="66285-133">**데이터** 와 **로그** 파일 중에 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-133">The available choices are **Data** and **Log** files.</span></span> <span data-ttu-id="66285-134">기본 설정은 **데이터**입니다.</span><span class="sxs-lookup"><span data-stu-id="66285-134">The default selection is **Data**.</span></span> <span data-ttu-id="66285-135">다른 파일 그룹 유형을 선택하면 변경 내용에 따라 다른 필드의 선택 내용도 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="66285-135">Selecting a different filegroup type changes the selections in the other fields accordingly.</span></span>  
  
     <span data-ttu-id="66285-136">**파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="66285-136">**Filegroup**</span></span>  
     <span data-ttu-id="66285-137">위의 **파일 유형** 에서 선택한 내용과 연관된 파일 그룹 목록에서 파일 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-137">Select a filegroup from the list of Filegroups associated with the selected **File type** above.</span></span> <span data-ttu-id="66285-138">다른 파일 그룹을 선택하면 변경 내용에 따라 다른 필드의 선택 내용도 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="66285-138">Selecting a different filegroup changes the selections in the other fields accordingly.</span></span>  
  
     <span data-ttu-id="66285-139">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="66285-139">**File name**</span></span>  
     <span data-ttu-id="66285-140">선택한 파일 그룹 및 파일 형식의 사용 가능한 파일 목록에서 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-140">Select a file from the list of available files of the selected filegroup and file type.</span></span>  
  
     <span data-ttu-id="66285-141">**위치**</span><span class="sxs-lookup"><span data-stu-id="66285-141">**Location**</span></span>  
     <span data-ttu-id="66285-142">현재 선택된 파일의 전체 경로를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-142">Displays the full path to the currently selected file.</span></span> <span data-ttu-id="66285-143">이 경로는 편집할 수 없지만 클립보드로 복사할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-143">The path is not editable, but it can be copied to the clipboard.</span></span>  
  
     <span data-ttu-id="66285-144">**현재 할당된 공간**</span><span class="sxs-lookup"><span data-stu-id="66285-144">**Currently allocated space**</span></span>  
     <span data-ttu-id="66285-145">데이터 파일의 경우 현재 할당된 공간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-145">For data files, displays the current allocated space.</span></span> <span data-ttu-id="66285-146">로그 파일의 경우 DBCC SQLPERF(LOGSPACE)의 출력에 따라 계산된 현재 할당된 공간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-146">For log files, displays the current allocated space computed from the output of DBCC SQLPERF(LOGSPACE).</span></span>  
  
     <span data-ttu-id="66285-147">**사용 가능한 공간**</span><span class="sxs-lookup"><span data-stu-id="66285-147">**Available free space**</span></span>  
     <span data-ttu-id="66285-148">데이터 파일의 경우 DBCC SHOWFILESTATS(파일 ID)의 출력에 따라 계산된 현재 사용 가능한 빈 공간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-148">For data files, displays the current available free space computed from the output of DBCC SHOWFILESTATS(fileid).</span></span> <span data-ttu-id="66285-149">로그 파일의 경우 DBCC SQLPERF(LOGSPACE)의 출력에 따라 계산된 현재 사용 가능한 빈 공간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-149">For log files, displays the current available free space computed from the output of DBCC SQLPERF(LOGSPACE).</span></span>  
  
     <span data-ttu-id="66285-150">**사용하지 않은 공간 해제**</span><span class="sxs-lookup"><span data-stu-id="66285-150">**Release unused space**</span></span>  
     <span data-ttu-id="66285-151">파일에서 사용되지 않는 공간을 운영 체제에 반환하고 마지막으로 할당된 익스텐트까지 파일을 축소하여 데이터를 이동하지 않고 파일 크기를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="66285-151">Cause any unused space in the files to be released to the operating system and shrink the file to the last allocated extent, reducing the file size without moving any data.</span></span> <span data-ttu-id="66285-152">할당되지 않은 페이지에 행을 다시 할당하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-152">No attempt is made to relocate rows to unallocated pages.</span></span>  
  
     <span data-ttu-id="66285-153">**사용하지 않은 공간을 해제하기 전에 페이지 다시 구성**</span><span class="sxs-lookup"><span data-stu-id="66285-153">**Reorganize pages before releasing unused space**</span></span>  
     <span data-ttu-id="66285-154">대상 파일 크기를 지정하는 DBCC SHRINKFILE을 실행한 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-154">Equivalent to executing DBCC SHRINKFILE specifying the target file size.</span></span> <span data-ttu-id="66285-155">이 옵션을 선택한 경우 사용자가 **파일을 다음 크기로 축소** 입력란에 대상 파일 크기를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-155">When this option is selected, the user must specify a target file size in the **Shrink file to** box.</span></span>  
  
     <span data-ttu-id="66285-156">**파일을 다음 크기로 축소**</span><span class="sxs-lookup"><span data-stu-id="66285-156">**Shrink file to**</span></span>  
     <span data-ttu-id="66285-157">축소 작업의 대상 파일 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-157">Specifies the target file size for the shrink operation.</span></span> <span data-ttu-id="66285-158">이 크기는 현재 할당된 공간의 크기보다 크고 파일에 할당된 총 익스텐트 수보다 적어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-158">The size cannot be less than the current allocated space or more than the total extents allocated to the file.</span></span> <span data-ttu-id="66285-159">최소값보다 작거나 최대값보다 큰 값을 입력한 경우 포커스를 이동하거나 도구 모음의 단추를 클릭하면 최소값 또는 최대값으로 되돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="66285-159">Entering a value beyond the minimum or the maximum will revert to the min or the max once the focus is changed or when any of the buttons on the toolbar are clicked.</span></span>  
  
     <span data-ttu-id="66285-160">**같은 파일 그룹의 다른 파일로 데이터를 마이그레이션하여 파일 비우기**</span><span class="sxs-lookup"><span data-stu-id="66285-160">**Empty file by migrating the data to other files in the same filegroup**</span></span>  
     <span data-ttu-id="66285-161">지정한 파일의 모든 데이터를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-161">Migrate all data from the specified file.</span></span> <span data-ttu-id="66285-162">이 옵션을 선택하면 ALTER DATABASE 문을 사용하여 해당 파일을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-162">This option allows the file to be dropped using the ALTER DATABASE statement.</span></span> <span data-ttu-id="66285-163">이 옵션은 EMPTYFILE 옵션을 사용하여 DBCC SHRINKFILE을 실행하는 것과 같은 기능을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-163">This option is equivalent to executing DBCC SHRINKFILE with the EMPTYFILE option.</span></span>  
  
4.  <span data-ttu-id="66285-164">파일 형식 및 파일 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-164">Select the file type and file name.</span></span>  
  
5.  <span data-ttu-id="66285-165">선택적으로 **사용하지 않은 공간 해제** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-165">Optionally, select the **Release unused space** check box.</span></span>  
  
     <span data-ttu-id="66285-166">이 옵션을 선택하면 파일에서 사용되지 않은 공간이 해제되어 운영 체제에서 사용할 수 있게 되며 파일이 마지막으로 할당된 범위로 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="66285-166">Selecting this option causes any unused space in the file to be released to the operating system and shrinks the file to the last allocated extent.</span></span> <span data-ttu-id="66285-167">이렇게 하면 데이터를 이동하지 않아도 파일 크기가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="66285-167">This reduces the file size without moving any data.</span></span>  
  
6.  <span data-ttu-id="66285-168">선택적으로 **사용하지 않은 공간을 해제하기 전에 파일을 다시 구성** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-168">Optionally, select the **Reorganize files before releasing unused space** check box.</span></span> <span data-ttu-id="66285-169">이 확인란을 선택하면 **파일을 다음 크기로 축소** 값을 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-169">If this is selected, the **Shrink file to** value must be specified.</span></span> <span data-ttu-id="66285-170">기본적으로 이 옵션은 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-170">By default, the option is cleared.</span></span>  
  
     <span data-ttu-id="66285-171">이 옵션을 선택하면 파일에서 사용되지 않은 공간이 해제되어 운영 체제에서 사용할 수 있게 되며 행의 위치를 할당되지 않은 페이지에 지정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-171">Selecting this option causes any unused space in the file to be released to the operating system and tries to relocate rows to unallocated pages.</span></span>  
  
7.  <span data-ttu-id="66285-172">선택적으로 데이터베이스를 축소한 후 데이터베이스 파일에 남겨둘 여유 공간의 최대 비율을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-172">Optionally, enter the maximum percentage of free space to be left in the database file after the database has been shrunk.</span></span> <span data-ttu-id="66285-173">허용되는 값은 0에서 99까지입니다.</span><span class="sxs-lookup"><span data-stu-id="66285-173">Permissible values are between 0 and 99.</span></span> <span data-ttu-id="66285-174">이 옵션은 **사용하지 않은 공간을 해제하기 전에 파일 다시 구성** 을 활성화한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-174">This option is only available when **Reorganize files before releasing unused space** is enabled.</span></span>  
  
8.  <span data-ttu-id="66285-175">선택적으로 **같은 파일 그룹의 다른 파일로 데이터를 마이그레이션하여 파일 비우기** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-175">Optionally, select the **Empty file by migrating the data to other files in the same filegroup** check box.</span></span>  
  
     <span data-ttu-id="66285-176">이 옵션을 선택하면 지정된 파일의 모든 데이터가 파일 그룹 내 다른 파일로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-176">Selecting this option moves all data from the specified file to other files in the filegroup.</span></span> <span data-ttu-id="66285-177">그런 다음 빈 파일을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66285-177">The empty file can then be deleted.</span></span> <span data-ttu-id="66285-178">이 옵션은 EMPTYFILE 옵션을 사용하여 DBCC SHRINKFILE을 실행하는 것과 같은 기능을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-178">This option is the same as executing DBCC SHRINKFILE with the EMPTYFILE option.</span></span>  
  
9. <span data-ttu-id="66285-179">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-179">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="66285-180">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="66285-180">Using Transact-SQL</span></span>  
  
#### <a name="to-shrink-a-data-or-log-file"></a><span data-ttu-id="66285-181">데이터 또는 로그 파일을 축소하려면</span><span class="sxs-lookup"><span data-stu-id="66285-181">To shrink a data or log file</span></span>  
  
1.  <span data-ttu-id="66285-182">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-182">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="66285-183">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-183">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="66285-184">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-184">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="66285-185">이 예에서는 [DBCC SHRINKFILE](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) 을 사용하여 `UserDB` 데이터베이스에 있는 `DataFile1` 이라는 데이터 파일의 크기를 7MB로 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="66285-185">This example uses [DBCC SHRINKFILE](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) to shrink the size of a data file named `DataFile1` in the `UserDB` database to 7 MB.</span></span>  
  
 [!code-sql[DBCC#DBCC_SHRINKFILE1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkfile1)]  
  
## <a name="see-also"></a><span data-ttu-id="66285-186">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66285-186">See Also</span></span>  
 <span data-ttu-id="66285-187">[DBCC SHRINKDATABASE&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="66285-187">[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) </span></span>  
 <span data-ttu-id="66285-188">[데이터베이스 축소](shrink-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="66285-188">[Shrink a Database](shrink-a-database.md) </span></span>  
 <span data-ttu-id="66285-189">[데이터베이스에서 데이터 또는 로그 파일 삭제](delete-data-or-log-files-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="66285-189">[Delete Data or Log Files from a Database](delete-data-or-log-files-from-a-database.md) </span></span>  
 <span data-ttu-id="66285-190">[sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="66285-190">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="66285-191">sys.database_files&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="66285-191">sys.database_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)  
  
  
