---
title: SQL Server의 기존 인스턴스 제거(설치) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- removing instances of SQL Server
- uninstalling instances of SQL Server
- removing SQL Server
- instances of SQL Server, uninstalling
- uninstalling SQL Server
ms.assetid: 3c64b29d-61d7-4b86-961c-0de62261c6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 51d426a12a2f7f1b7bedbfb7770c4d9cb369f12b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650436"
---
# <a name="uninstall-an-existing-instance-of-sql-server-setup"></a><span data-ttu-id="0df15-102">SQL Server의 기존 인스턴스 제거(설치)</span><span class="sxs-lookup"><span data-stu-id="0df15-102">Uninstall an Existing Instance of SQL Server (Setup)</span></span>
  <span data-ttu-id="0df15-103">이 문서에서는 독립 실행형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-103">This article describes how to uninstall a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0df15-104">이 항목의 단계를 수행하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 설치할 수 있도록 시스템을 준비할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-104">By following the steps in this topic, you also prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0df15-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 제거하려면 서비스로 로그온할 수 있는 권한을 가진 로컬 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-105">To uninstall an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be a local administrator with permission to log on as a service.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0df15-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터를 제거하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램이 제공하는 노드 제거 기능을 사용하여 각 노드를 개별적으로 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-106">To uninstall a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, use the Remove Node functionality provided by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to remove each node individually.</span></span> <span data-ttu-id="0df15-107">자세한 내용은 [SQL Server 장애 조치 (Failover) 클러스터에서 노드 추가 또는 제거 &#40;설치](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="0df15-107">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span></span>  
  
 <span data-ttu-id="0df15-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 제거하기 전에 다음의 중요 정보를 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="0df15-108">Consider the following important information before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="0df15-109">필요한 최소한의 실제 메모리를 갖춘 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소를 제거하려면 먼저 페이지 파일 크기가 충분한지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-109">Before you remove [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components from a computer that has the minimum required amount of physical memory, make sure that the page file size is sufficient.</span></span> <span data-ttu-id="0df15-110">페이지 파일 크기는 실제 메모리의 두 배여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-110">The page file size must be equal to two times the amount of physical memory.</span></span> <span data-ttu-id="0df15-111">가상 메모리가 부족하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 완전히 제거되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-111">Insufficient virtual memory can cause an incomplete removal of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="0df15-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스가 여러 개인 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser는 마지막 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 인스턴스가 제거될 때 자동으로 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-112">If you have multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser uninstalls automatically when the last instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is uninstalled.</span></span>  
  
     <span data-ttu-id="0df15-113">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 모든 구성 요소를 제거하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 제어판 **의** 프로그램 및 기능 **에서**Browser 구성 요소를 수동으로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-113">If you want to uninstall all components of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must uninstall the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser component manually from **Programs and Features** in **Control Panel**.</span></span>  
  
### <a name="before-you-uninstall"></a><span data-ttu-id="0df15-114">제거하기 전에</span><span class="sxs-lookup"><span data-stu-id="0df15-114">Before You Uninstall</span></span>  
  
1.  <span data-ttu-id="0df15-115">**데이터를 백업합니다.**</span><span class="sxs-lookup"><span data-stu-id="0df15-115">**Back up your data.**</span></span> <span data-ttu-id="0df15-116">필수 단계는 아니지만 데이터베이스를 현재 상태대로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-116">Although this is not a required step, you might have databases that you want to save in their present state.</span></span> <span data-ttu-id="0df15-117">시스템 데이터베이스에 적용된 변경 사항을 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-117">You might also want to save changes that were made to the system databases.</span></span> <span data-ttu-id="0df15-118">두 경우 모두 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 제거하기 전에 데이터를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-118">If either situation is true, make sure that back up the data before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0df15-119">또는 모든 데이터 및 로그 파일의 사본을 MSSQL 폴더 이외의 폴더에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-119">Alternatively, save a copy of all the data and log files in a folder other than the MSSQL folder.</span></span> <span data-ttu-id="0df15-120">MSSQL 폴더는 제거 중에 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-120">The MSSQL folder is deleted during uninstallation.</span></span>  
  
     <span data-ttu-id="0df15-121">저장해야 하는 파일에는 다음 데이터베이스 파일이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-121">The files that you must save include the following database files:</span></span>  
  
    -   <span data-ttu-id="0df15-122">Master.mdf</span><span class="sxs-lookup"><span data-stu-id="0df15-122">Master.mdf</span></span>  
  
    -   <span data-ttu-id="0df15-123">Mastlog.ldf</span><span class="sxs-lookup"><span data-stu-id="0df15-123">Mastlog.ldf</span></span>  
  
    -   <span data-ttu-id="0df15-124">Model.mdf</span><span class="sxs-lookup"><span data-stu-id="0df15-124">Model.mdf</span></span>  
  
    -   <span data-ttu-id="0df15-125">Modellog.ldf</span><span class="sxs-lookup"><span data-stu-id="0df15-125">Modellog.ldf</span></span>  
  
    -   <span data-ttu-id="0df15-126">Msdbdata.mdf</span><span class="sxs-lookup"><span data-stu-id="0df15-126">Msdbdata.mdf</span></span>  
  
    -   <span data-ttu-id="0df15-127">Msdblog.ldf</span><span class="sxs-lookup"><span data-stu-id="0df15-127">Msdblog.ldf</span></span>  
  
    -   <span data-ttu-id="0df15-128">Mssqlsystemresource.mdf</span><span class="sxs-lookup"><span data-stu-id="0df15-128">Mssqlsystemresource.mdf</span></span>  
  
    -   <span data-ttu-id="0df15-129">Mssqlsustemresource.ldf</span><span class="sxs-lookup"><span data-stu-id="0df15-129">Mssqlsustemresource.ldf</span></span>  
  
    -   <span data-ttu-id="0df15-130">Tempdb.mdf</span><span class="sxs-lookup"><span data-stu-id="0df15-130">Tempdb.mdf</span></span>  
  
    -   <span data-ttu-id="0df15-131">Templog.ldf</span><span class="sxs-lookup"><span data-stu-id="0df15-131">Templog.ldf</span></span>  
  
    -   <span data-ttu-id="0df15-132">`ReportServer[$InstanceName]`( [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본값은 기본 데이터베이스입니다.)</span><span class="sxs-lookup"><span data-stu-id="0df15-132">`ReportServer[$InstanceName]` (Thisis the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] default database.)</span></span>  
  
    -   <span data-ttu-id="0df15-133">ReportServer[$InstanceName]TempDB( [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 임시 데이터베이스)</span><span class="sxs-lookup"><span data-stu-id="0df15-133">ReportServer[$InstanceName]TempDB (This is the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] default temporary database.)</span></span>  
  
2.  <span data-ttu-id="0df15-134">**로컬 보안 그룹을 삭제합니다.**</span><span class="sxs-lookup"><span data-stu-id="0df15-134">**Delete the local security groups.**</span></span> <span data-ttu-id="0df15-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 제거하기 전에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소에 대한 로컬 보안 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-135">Before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], delete the local security groups for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
3.  <span data-ttu-id="0df15-136">**서비스를**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **모두 중지합니다.**</span><span class="sxs-lookup"><span data-stu-id="0df15-136">**Stop all**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **services.**</span></span> <span data-ttu-id="0df15-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소를 제거하기 전에 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 중지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-137">We recommend that you stop all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services before you uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span> <span data-ttu-id="0df15-138">활성 연결로 인해 제거 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-138">Active connections can prevent successful uninstallation.</span></span>  
  
4.  <span data-ttu-id="0df15-139">**적합한 권한을 가진 계정을 사용합니다.**</span><span class="sxs-lookup"><span data-stu-id="0df15-139">**Use an account that has the appropriate permissions.**</span></span> <span data-ttu-id="0df15-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정 또는 동등한 권한을 가진 계정을 사용하여 서버에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-140">Log on to the server by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account or by using an account that has equivalent permissions.</span></span> <span data-ttu-id="0df15-141">예를 들어 로컬 Administrators 그룹의 멤버 계정을 사용하여 서버에 로그온할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-141">For example, you can log on to the server by using an account that is a member of the local Administrators group.</span></span>  
  
### <a name="to-uninstall-an-instance-of-ssnoversion"></a><span data-ttu-id="0df15-142">기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0df15-142">To Uninstall an Instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="0df15-143">제거 프로세스를 시작하려면 **제어판** , **프로그램 및 기능**으로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-143">To begin the uninstall process, go to **Control Panel** and then **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="0df15-144">마우스 오른쪽 단추 **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** 를 클릭 하 고 **제거**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-144">Right click **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** and select **Uninstall**.</span></span> <span data-ttu-id="0df15-145">**제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-145">Then click **Remove**.</span></span> <span data-ttu-id="0df15-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-146">This starts the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span>  
  
     <span data-ttu-id="0df15-147">컴퓨터 구성을 확인하기 위해 설치 지원 규칙이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-147">Setup Support Rules runs to verify your computer configuration.</span></span> <span data-ttu-id="0df15-148">계속하려면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-148">To continue, click **Next**.</span></span>  
  
3.  <span data-ttu-id="0df15-149">인스턴스 선택 페이지에서 드롭다운 상자를 사용하여 제거할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 지정하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 공유 기능 및 관리 도구만 제거하는 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-149">On the Select Instance page, use the drop-down box to specify an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to remove, or specify the option to remove only the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared features and management tools.</span></span> <span data-ttu-id="0df15-150">계속하려면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-150">To continue, click **Next**.</span></span>  
  
4.  <span data-ttu-id="0df15-151">기능 선택 페이지에서 지정한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 제거할 기능을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-151">On the Select Features page, specify the features to remove from the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="0df15-152">작업을 성공적으로 완료할 수 있는지 확인하기 위해 제거 규칙이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-152">Removal rules runs to verify that the operation can complete successfully.</span></span>  
  
5.  <span data-ttu-id="0df15-153">**제거 준비** 페이지에서 제거할 구성 요소 및 기능 목록을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-153">On the **Ready to Remove** page, review the list of components and features that will be uninstalled.</span></span> <span data-ttu-id="0df15-154">**제거** 를 클릭하여 제거를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-154">Click **Remove** to begin uninstalling</span></span>  
  
6.  <span data-ttu-id="0df15-155">마지막 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 제거한 직후에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로그램 및 기능 **의 프로그램 목록에**와 연결된 다른 프로그램이 계속 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-155">Immediately after you uninstall the last [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, the other programs associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will still be visible in the list of programs in **Programs and Features**.</span></span> <span data-ttu-id="0df15-156">그러나 **프로그램 및 기능**을 닫은 후 다음에 **프로그램 및 기능**을 열면 프로그램 목록이 새로 고쳐져서 실제로 설치된 프로그램만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-156">However, if you close **Programs and Features**, the next time you open **Programs and Features**, it will refresh the list of programs, to show only the ones that are actually still installed.</span></span>  
  
### <a name="if-the-uninstallation-fails"></a><span data-ttu-id="0df15-157">제거에 실패하는 경우</span><span class="sxs-lookup"><span data-stu-id="0df15-157">If the Uninstallation Fails</span></span>  
  
1.  <span data-ttu-id="0df15-158">제거 프로세스가 성공적으로 완료되지 않은 경우 제거 실패 원인이 된 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="0df15-158">If the uninstallation process does not complete successfully, attempt to fix the problem that caused the uninstallation to fail.</span></span> <span data-ttu-id="0df15-159">다음 문서는 제거 실패의 원인을 파악하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-159">The following articles can help you understand the cause of the failed uninstallation:</span></span>  
  
    -   [<span data-ttu-id="0df15-160">설치 로그 파일에서 SQL Server 2008 설치 문제를 확인하는 방법</span><span class="sxs-lookup"><span data-stu-id="0df15-160">How to identify SQL Server 2008 setup issues in the setup log files</span></span>](https://support.microsoft.com/kb/955396/en-us)  
  
    -   [<span data-ttu-id="0df15-161">SQL Server 설치 로그 파일 보기 및 읽기</span><span class="sxs-lookup"><span data-stu-id="0df15-161">View and Read SQL Server Setup Log Files</span></span>](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
2.  <span data-ttu-id="0df15-162">제거 실패 원인을 해결할 수 없는 경우 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 고객 지원 센터에 문의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-162">If you are unable to fix the cause of the uninstallation failure, you can contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Support.</span></span> <span data-ttu-id="0df15-163">중요 파일을 의도하지 않게 삭제한 경우와 같은 때는 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 다시 설치하기 전에 운영 체제를 다시 설치해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0df15-163">In some cases, such as unintentional deletion of important files, reinstalling the operating system may be required before reinstalling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df15-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0df15-164">See Also</span></span>  
 [<span data-ttu-id="0df15-165">SQL Server 설치 로그 파일 보기 및 읽기</span><span class="sxs-lookup"><span data-stu-id="0df15-165">View and Read SQL Server Setup Log Files</span></span>](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
