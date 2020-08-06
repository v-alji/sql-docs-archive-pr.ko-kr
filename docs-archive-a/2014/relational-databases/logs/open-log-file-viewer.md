---
title: 로그 파일 뷰어 열기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, opening
ms.assetid: a86b89cb-0432-4648-895a-05ecc5450e45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 269ff10275f7463a8a85249a2a0f06fe9bde364a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649530"
---
# <a name="open-log-file-viewer"></a><span data-ttu-id="8c26c-102">로그 파일 뷰어 열기</span><span class="sxs-lookup"><span data-stu-id="8c26c-102">Open Log File Viewer</span></span>
  <span data-ttu-id="8c26c-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 로그 파일 뷰어를 사용하여 다음 로그에 기록되는 오류 및 이벤트에 대한 정보에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-103">You can use Log File Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to access information about errors and events that are captured in the following logs:</span></span>  
  
-   <span data-ttu-id="8c26c-104">감사 컬렉션</span><span class="sxs-lookup"><span data-stu-id="8c26c-104">Audit Collection</span></span>  
  
-   <span data-ttu-id="8c26c-105">데이터 수집</span><span class="sxs-lookup"><span data-stu-id="8c26c-105">Data Collection</span></span>  
  
-   <span data-ttu-id="8c26c-106">데이터베이스 메일</span><span class="sxs-lookup"><span data-stu-id="8c26c-106">Database Mail</span></span>  
  
-   <span data-ttu-id="8c26c-107">작업 기록</span><span class="sxs-lookup"><span data-stu-id="8c26c-107">Job History</span></span>  
  
-   <span data-ttu-id="8c26c-108">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8c26c-108">SQL Server</span></span>  
  
-   <span data-ttu-id="8c26c-109">SQL Server 에이전트</span><span class="sxs-lookup"><span data-stu-id="8c26c-109">SQL Server Agent</span></span>  
  
-   <span data-ttu-id="8c26c-110">Windows 이벤트(이벤트 뷰어에서도 이러한 Windows 이벤트에 액세스할 수 있음)</span><span class="sxs-lookup"><span data-stu-id="8c26c-110">Windows events (These Windows events can also be accessed from Event Viewer.)</span></span>  
  
 <span data-ttu-id="8c26c-111">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]부터는 등록된 서버를 사용하여 로컬 또는 원격 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로그 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-111">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can use Registered Servers to view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from local or remote instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8c26c-112">등록된 서버를 사용하면 인스턴스가 온라인인지 오프라인인지 관계없이 로그 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-112">By using Registered Servers, you can view the log files when the instances are either online or offline.</span></span> <span data-ttu-id="8c26c-113">온라인 액세스에 대한 자세한 내용은 이 항목의 "등록된 서버에서 온라인 로그 파일을 보려면" 절차를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8c26c-113">For more information about online access, see the procedure "To view online log files from Registered Servers" later in this topic.</span></span> <span data-ttu-id="8c26c-114">오프라인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그 파일에 액세스하는 방법은 [오프라인 로그 파일 보기](view-offline-log-files.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c26c-114">For more information about how to access offline [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files, see [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
 <span data-ttu-id="8c26c-115">로그 파일 뷰어는 보려는 정보에 따라 여러 방법으로 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-115">You can open Log File Viewer in several ways, depending on the information that you want to view.</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8c26c-116">권한</span><span class="sxs-lookup"><span data-stu-id="8c26c-116">Permissions</span></span>  
 <span data-ttu-id="8c26c-117">온라인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 로그 파일에 액세스하려면 securityadmin 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-117">To access log files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are online, this requires membership in the securityadmin fixed server role.</span></span>  
  
 <span data-ttu-id="8c26c-118">오프라인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 로그 파일에 액세스하려면 **Root\Microsoft\SqlServer\ComputerManagement10** WMI 네임스페이스 및 로그 파일이 저장된 폴더 모두에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-118">To access log files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are offline, you must have read access to both the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace, and to the folder where the log files are stored.</span></span> <span data-ttu-id="8c26c-119">자세한 내용은 [오프라인 로그 파일 보기](view-offline-log-files.md)항목의 보안 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c26c-119">For more information, see the Security section of the topic [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
### <a name="security"></a><span data-ttu-id="8c26c-120">보안</span><span class="sxs-lookup"><span data-stu-id="8c26c-120">Security</span></span>  
 <span data-ttu-id="8c26c-121">securityadmin 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-121">Requires membership in the securityadmin fixed server role.</span></span>  
  
### <a name="view-log-files"></a><span data-ttu-id="8c26c-122">로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="8c26c-122">View Log Files</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-general-sql-server-activity"></a><span data-ttu-id="8c26c-123">일반적인 SQL Server 작업과 관련된 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="8c26c-123">To view logs that are related to general SQL Server activity</span></span>  
  
1.  <span data-ttu-id="8c26c-124">개체 탐색기에서 **관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-124">In Object Explorer, expand **Management**.</span></span>  
  
2.  <span data-ttu-id="8c26c-125">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-125">Do either of the following:</span></span>  
  
    -   <span data-ttu-id="8c26c-126">**SQL Server 로그**를 마우스 오른쪽 단추로 클릭하고 **보기**를 가리킨 다음 **SQL Server 로그** 또는 **SQL Server 및 Windows 로그**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-126">Right-click **SQL Server Logs**, point to **View**, and then click either **SQL Server Log** or **SQL Server and Windows Log**.</span></span>  
  
    -   <span data-ttu-id="8c26c-127">**SQL Server 로그**를 확장하고 로그 파일을 마우스 오른쪽 단추로 클릭한 다음 **SQL Server 로그 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-127">Expand **SQL Server Logs**, right-click any log file, and then click **View SQL Server Log**.</span></span> <span data-ttu-id="8c26c-128">로그 파일을 두 번 클릭해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-128">You can also double-click any log file.</span></span>  
  
     <span data-ttu-id="8c26c-129">로그에는 **데이터베이스 메일**, **SQL Server**, **SQL Server 에이전트**및 **Windows NT**가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-129">The logs include **Database Mail**, **SQL Server**, **SQL Server Agent**, and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-jobs"></a><span data-ttu-id="8c26c-130">작업과 관련된 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="8c26c-130">To view logs that are related to jobs</span></span>  
  
-   <span data-ttu-id="8c26c-131">개체 탐색기에서 **SQL Server 에이전트**를 확장하고 **작업**을 마우스 오른쪽 단추로 클릭한 다음 **기록 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-131">In Object Explorer, expand **SQL Server Agent**, right-click **Jobs**, and then click **View History**.</span></span>  
  
     <span data-ttu-id="8c26c-132">로그에는 **데이터베이스 메일**, **작업 기록**및 **SQL Server 에이전트**가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-132">The logs include **Database Mail**, **Job History**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-maintenance-plans"></a><span data-ttu-id="8c26c-133">유지 관리 계획과 관련된 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="8c26c-133">To view logs that are related to maintenance plans</span></span>  
  
-   <span data-ttu-id="8c26c-134">개체 탐색기에서 **관리**를 확장하고 **유지 관리 계획**을 마우스 오른쪽 단추로 클릭한 다음 **기록 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-134">In Object Explorer, expand **Management**, right-click **Maintenance Plans**, and then click **View History**.</span></span>  
  
     <span data-ttu-id="8c26c-135">로그에는 **데이터베이스 메일**, **작업 기록**, **유지 관리 계획**, **원격 유지 관리 계획**및 **SQL Server 에이전트**가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-135">The logs include **Database Mail**, **Job History**, **Maintenance Plans**, **Remote Maintenance Plans**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-data-collection"></a><span data-ttu-id="8c26c-136">데이터 컬렉션과 관련된 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="8c26c-136">To view logs that are related to Data Collection</span></span>  
  
-   <span data-ttu-id="8c26c-137">개체 탐색기에서 **관리**를 확장하고 **데이터 컬렉션**을 마우스 오른쪽 단추로 클릭한 다음 **로그 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-137">In Object Explorer, expand **Management**, right-click **Data Collection**, and then click **View Logs**.</span></span>  
  
     <span data-ttu-id="8c26c-138">로그에는 **데이터 컬렉션**, **작업 기록**및 **SQL Server 에이전트**가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-138">The logs include **Data Collection**, **Job History**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-database-mail"></a><span data-ttu-id="8c26c-139">데이터베이스 메일과 관련된 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="8c26c-139">To view logs that are related to Database Mail</span></span>  
  
-   <span data-ttu-id="8c26c-140">개체 탐색기에서 **관리**를 확장하고 **데이터베이스 메일**을 마우스 오른쪽 단추로 클릭한 다음 **데이터베이스 메일 로그 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-140">In Object Explorer, expand **Management**, right-click **Database Mail**, and then click **View Database Mail Log**.</span></span>  
  
     <span data-ttu-id="8c26c-141">로그에는 **데이터베이스 메일, 작업 기록**, **유지 관리 계획**, **원격 유지 관리 계획**, **SQL Server**, **SQL Server 에이전트**및 **Windows NT**가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-141">The logs include **Database Mail, Job History**, **Maintenance Plans**, **Remote Maintenance Plans**, **SQL Server**, **SQL Server Agent**, and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a><span data-ttu-id="8c26c-142">감사 컬렉션과 관련된 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="8c26c-142">To view logs that are related to audits collections</span></span>  
  
-   <span data-ttu-id="8c26c-143">개체 탐색기에서 **보안**, **감사**를 차례로 확장하고 감사를 마우스 오른쪽 단추로 클릭한 다음 **감사 로그 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-143">In Object Explorer, expand **Security**, expand **Audits**, right-click an audit, and then click **View Audit Logs**.</span></span>  
  
     <span data-ttu-id="8c26c-144">로그에는 **감사 컬렉션** 및 **Windows NT**가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-144">The logs include **Audit Collection** and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a><span data-ttu-id="8c26c-145">감사 컬렉션과 관련된 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="8c26c-145">To view logs that are related to audits collections</span></span>  
  
-   <span data-ttu-id="8c26c-146">개체 탐색기에서 **보안**, **감사**를 차례로 확장하고 감사를 마우스 오른쪽 단추로 클릭한 다음 **감사 로그 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-146">In Object Explorer, expand **Security**, expand **Audits**, right-click an audit, and then click **View Audit Logs**.</span></span>  
  
     <span data-ttu-id="8c26c-147">로그에는 **감사 컬렉션** 및 **Windows NT**가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c26c-147">The logs include **Audit Collection** and **Windows NT**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c26c-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c26c-148">See Also</span></span>  
 <span data-ttu-id="8c26c-149">[로그 파일 뷰어](log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="8c26c-149">[Log File Viewer](log-file-viewer.md) </span></span>  
 <span data-ttu-id="8c26c-150">[SQL Server Audit&#40;데이터베이스 엔진&#41;](../security/auditing/sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="8c26c-150">[SQL Server Audit &#40;Database Engine&#41;](../security/auditing/sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="8c26c-151">오프라인 로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="8c26c-151">View Offline Log Files</span></span>](view-offline-log-files.md)  
  
  
