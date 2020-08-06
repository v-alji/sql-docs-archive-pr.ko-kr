---
title: FILESTREAM 사용 및 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], enabling
ms.assetid: 78737e19-c65b-48d9-8fa9-aa6f1e1bce73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f6c0e505bd32636d045519b36e439bc21c7079d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638857"
---
# <a name="enable-and-configure-filestream"></a><span data-ttu-id="e96c0-102">FILESTREAM 사용 및 구성</span><span class="sxs-lookup"><span data-stu-id="e96c0-102">Enable and Configure FILESTREAM</span></span>
  <span data-ttu-id="e96c0-103">FILESTREAM을 사용하려면 먼저 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]인스턴스에서 FILESTREAM을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-103">Before you can start to use FILESTREAM, you must enable FILESTREAM on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="e96c0-104">이 항목에서는 SQL Server 구성 관리자를 사용하여 FILESTREAM을 사용하도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-104">This topic describes how to enable FILESTREAM by using SQL Server Configuration Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e96c0-105">64비트 운영 체제에서 실행되는 32비트 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 FILESTREAM을 사용하도록 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-105">You cannot enable FILESTREAM on a 32-bit version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on a 64-bit operating system.</span></span>  
  
##  <a name="enabling-filestream"></a><a name="enabling"></a> <span data-ttu-id="e96c0-106">FILESTREAM 설정</span><span class="sxs-lookup"><span data-stu-id="e96c0-106">Enabling FILESTREAM</span></span>  
  
#### <a name="to-enable-and-change-filestream-settings"></a><span data-ttu-id="e96c0-107">FILESTREAM을 사용하도록 설정하고 해당 설정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="e96c0-107">To enable and change FILESTREAM settings</span></span>  
  
1.  <span data-ttu-id="e96c0-108">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="e96c0-109">서비스 목록에서 **SQL Server 서비스**를 마우스 오른쪽 단추로 클릭한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-109">In the list of services, right-click **SQL Server Services**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="e96c0-110">**SQL Server 구성 관리자** 스냅인에서 FILESTREAM을 사용할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-110">In the **SQL Server Configuration Manager** snap-in, locate the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you want to enable FILESTREAM.</span></span>  
  
4.  <span data-ttu-id="e96c0-111">해당 인스턴스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-111">Right-click the instance, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="e96c0-112">**SQL Server 속성** 대화 상자에서 **FILESTREAM** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-112">In the **SQL Server Properties** dialog box, click the **FILESTREAM** tab.</span></span>  
  
6.  <span data-ttu-id="e96c0-113">**Transact-SQL 액세스에 FILESTREAM 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-113">Select the **Enable FILESTREAM for Transact-SQL access** check box.</span></span>  
  
7.  <span data-ttu-id="e96c0-114">Windows에서 FILESTREAM 데이터를 읽고 쓰려는 경우 **파일 I/O 스트리밍 액세스에 FILESTREAM 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-114">If you want to read and write FILESTREAM data from Windows, click **Enable FILESTREAM for file I/O streaming access**.</span></span> <span data-ttu-id="e96c0-115">**Windows 공유 이름** 상자에 Windows 공유의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-115">Enter the name of the Windows share in the **Windows Share Name** box.</span></span>  
  
8.  <span data-ttu-id="e96c0-116">원격 클라이언트가 이 공유에 저장된 FILESTREAM 데이터에 액세스해야 하는 경우 **원격 클라이언트가 FILESTREAM 데이터에 대한 스트리밍 액세스를 가질 수 있도록 허용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-116">If remote clients must access the FILESTREAM data that is stored on this share, select **Allow remote clients to have streaming access to FILESTREAM data**.</span></span>  
  
9. <span data-ttu-id="e96c0-117">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-117">Click **Apply**.</span></span>  
  
10. <span data-ttu-id="e96c0-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 **새 쿼리** 를 클릭하여 쿼리 편집기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
11. <span data-ttu-id="e96c0-119">쿼리 편집기에서 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-119">In Query Editor, enter the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
    ```sql  
    EXEC sp_configure filestream_access_level, 2  
    RECONFIGURE  
    ```  
  
12. <span data-ttu-id="e96c0-120">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-120">Click **Execute**.</span></span>  
  
13. <span data-ttu-id="e96c0-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-121">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  

  
##  <a name="best-practices"></a><a name="best"></a> <span data-ttu-id="e96c0-122">최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="e96c0-122">Best Practices</span></span>  
  
###  <a name="physical-configuration-and-maintenance"></a><a name="config"></a><span data-ttu-id="e96c0-123">물리적 구성 및 유지 관리</span><span class="sxs-lookup"><span data-stu-id="e96c0-123">Physical Configuration and Maintenance</span></span>  
 <span data-ttu-id="e96c0-124">FILESTREAM 스토리지 볼륨을 설정할 때 다음 지침을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="e96c0-124">When you set up FILESTREAM storage volumes, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="e96c0-125">FILESTREAM 컴퓨터 시스템에서 약식 파일 이름을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-125">Turn off short file names on FILESTREAM computer systems.</span></span> <span data-ttu-id="e96c0-126">약식 파일 이름은 생성하는 데 시간이 많이 소요됩니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-126">Short file names take significantly longer to create.</span></span> <span data-ttu-id="e96c0-127">약식 파일 이름을 비활성화하려면 Windows **fsutil** 유틸리티를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-127">To disable short file names, use the Windows **fsutil** utility.</span></span>  
  
-   <span data-ttu-id="e96c0-128">정기적으로 FILESTREAM 컴퓨터 시스템 조각 모음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-128">Regularly defragment FILESTREAM computer systems.</span></span>  
  
-   <span data-ttu-id="e96c0-129">64KB NTFS 클러스터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-129">Use 64-KB NTFS clusters.</span></span> <span data-ttu-id="e96c0-130">압축된 볼륨은 4KB NTFS 클러스터로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-130">Compressed volumes must be set to 4-KB NTFS clusters.</span></span>  
  
-   <span data-ttu-id="e96c0-131">FILESTREAM 볼륨에서 인덱싱을 해제하고 **disablelastaccess** 설정합니다. **disablelastaccess**를 설정하려면 Windows **fsutil** 유틸리티를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-131">Disable indexing on FILESTREAM volumes and set **disablelastaccess** To set **disablelastaccess**, use the Windows **fsutil** utility.</span></span>  
  
-   <span data-ttu-id="e96c0-132">FILESTREAM 볼륨에 대한 바이러스 검사가 필요 없을 때는 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-132">Disable antivirus scanning of FILESTREAM volumes when it is not unnecessary.</span></span> <span data-ttu-id="e96c0-133">바이러스 검사가 필요한 경우, 잘못된 파일을 자동으로 삭제하는 정책을 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="e96c0-133">If antivirus scanning is necessary, avoid setting policies that will automatically delete offending files.</span></span>  
  
-   <span data-ttu-id="e96c0-134">애플리케이션에서 요구되는 내결함성 및 성능 RAID 수준을 설정하고 조절합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-134">Set up and tune the RAID level for fault tolerance and the performance that is required by an application.</span></span>  
  
||||||  
|-|-|-|-|-|  
|<span data-ttu-id="e96c0-135">RAID 수준</span><span class="sxs-lookup"><span data-stu-id="e96c0-135">RAID level</span></span>|<span data-ttu-id="e96c0-136">쓰기 성능</span><span class="sxs-lookup"><span data-stu-id="e96c0-136">Write performance</span></span>|<span data-ttu-id="e96c0-137">읽기 성능</span><span class="sxs-lookup"><span data-stu-id="e96c0-137">Read performance</span></span>|<span data-ttu-id="e96c0-138">내결함성</span><span class="sxs-lookup"><span data-stu-id="e96c0-138">Fault tolerance</span></span>|<span data-ttu-id="e96c0-139">설명</span><span class="sxs-lookup"><span data-stu-id="e96c0-139">Remarks</span></span>|  
|<span data-ttu-id="e96c0-140">RAID 5</span><span class="sxs-lookup"><span data-stu-id="e96c0-140">RAID 5</span></span>|<span data-ttu-id="e96c0-141">정상</span><span class="sxs-lookup"><span data-stu-id="e96c0-141">Normal</span></span>|<span data-ttu-id="e96c0-142">정상</span><span class="sxs-lookup"><span data-stu-id="e96c0-142">Normal</span></span>|<span data-ttu-id="e96c0-143">최고</span><span class="sxs-lookup"><span data-stu-id="e96c0-143">Excellent</span></span>|<span data-ttu-id="e96c0-144">성능은 하나의 디스크 또는 JBOD보다 우수하지만 RAID 0 또는 스트라이프를 사용하는 RAID 5보다 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-144">Performance is better than one disk or JBOD; and less than RAID 0 or RAID 5 with striping.</span></span>|  
|<span data-ttu-id="e96c0-145">RAID 0</span><span class="sxs-lookup"><span data-stu-id="e96c0-145">RAID 0</span></span>|<span data-ttu-id="e96c0-146">최고</span><span class="sxs-lookup"><span data-stu-id="e96c0-146">Excellent</span></span>|<span data-ttu-id="e96c0-147">최고</span><span class="sxs-lookup"><span data-stu-id="e96c0-147">Excellent</span></span>|<span data-ttu-id="e96c0-148">None</span><span class="sxs-lookup"><span data-stu-id="e96c0-148">None</span></span>||  
|<span data-ttu-id="e96c0-149">RAID 5 + 스트라이프</span><span class="sxs-lookup"><span data-stu-id="e96c0-149">RAID 5 + stripping</span></span>|<span data-ttu-id="e96c0-150">최고</span><span class="sxs-lookup"><span data-stu-id="e96c0-150">Excellent</span></span>|<span data-ttu-id="e96c0-151">최고</span><span class="sxs-lookup"><span data-stu-id="e96c0-151">Excellent</span></span>|<span data-ttu-id="e96c0-152">최고</span><span class="sxs-lookup"><span data-stu-id="e96c0-152">Excellent</span></span>|<span data-ttu-id="e96c0-153">가장 비용이 많이 드는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-153">Most expensive option.</span></span>|  
  

  
###  <a name="physical-database-design"></a><a name="database"></a><span data-ttu-id="e96c0-154">물리적 데이터베이스 디자인</span><span class="sxs-lookup"><span data-stu-id="e96c0-154">Physical Database Design</span></span>  
 <span data-ttu-id="e96c0-155">FILESTREAM 데이터베이스를 디자인할 때 다음 같은 지침을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="e96c0-155">When you design a FILESTREAM database, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="e96c0-156">FILESTREAM 열에는 해당 하는 ROWGUID 열이 수반 되어야 합니다 `uniqueidentifier` .</span><span class="sxs-lookup"><span data-stu-id="e96c0-156">FILESTREAM columns must be accompanied by a corresponding `uniqueidentifier`ROWGUID column.</span></span> <span data-ttu-id="e96c0-157">이러한 종류의 테이블에는 고유한 인덱스도 함께 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-157">These kinds of tables must also be accompanied by a unique index.</span></span> <span data-ttu-id="e96c0-158">일반적으로 이러한 인덱스는 클러스터형 인덱스가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-158">Typically this index is not a clustered index.</span></span> <span data-ttu-id="e96c0-159">데이터베이스 비즈니스 논리에 클러스터형 인덱스가 필요한 경우, 인덱스에 저장된 값이 임의의 값이 아니어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-159">If the databases business logic requires a clustered index, you have to make sure that the values stored in the index are not random.</span></span> <span data-ttu-id="e96c0-160">임의의 값인 경우에는 테이블에서 행이 추가되거나 제거될 때마다 인덱스가 다시 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-160">Random values will cause the index to be reordered every time that a row is added or removed from the table.</span></span>  
  
-   <span data-ttu-id="e96c0-161">성능상의 이유로 FILESTREAM 파일 그룹 및 컨테이너는 운영 체제, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그, tempdb 또는 페이징 파일 이외의 볼륨에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-161">For performance reasons, FILESTREAM filegroups and containers should reside on volumes other than the operating system, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log, tempdb, or paging file.</span></span>  
  
-   <span data-ttu-id="e96c0-162">공간 관리 및 정책은 FILESTREAM에서 직접적으로 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-162">Space management and policies are not directly supported by FILESTREAM.</span></span> <span data-ttu-id="e96c0-163">하지만 각 FILESTREAM 파일 그룹을 개별 볼륨에 지정하고 볼륨의 관리 기능을 사용하는 방법을 통해 간접적으로 공간을 관리하고 정책을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e96c0-163">However, you can manage space and apply policies indirectly by assigning each FILESTREAM filegroup to a separate volume and using the volume's management features.</span></span>  
  
  
