---
title: SQL Server 에이전트 오류 로그 보기(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- viewing SQL Server Agent error logs
- displaying SQL Server Agent error logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: de920425-fa44-469f-b83d-49e3f97e97f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: b88214a158a970a754c5f313bde3d53f2652ae73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734900"
---
# <a name="view-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="e878c-102">View SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e878c-102">View SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e878c-103">이 항목에서는  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에이전트 오류 로그를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-103">This topic describes how to view the  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e878c-104">로그 파일 뷰어는 다양한 구성 요소의 로그 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-104">Log File Viewer displays log information from many different components.</span></span> <span data-ttu-id="e878c-105">로그 파일 뷰어를 연 다음 **로그 선택** 창을 사용하여 표시할 로그를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-105">When Log File Viewer is open, use the **Select logs** pane to select the logs you want to display.</span></span> <span data-ttu-id="e878c-106">각 로그는 해당 로그 유형에 적합한 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-106">Each log displays columns appropriate to that kind of log.</span></span> <span data-ttu-id="e878c-107">사용 가능한 로그는 로그 파일 뷰어를 여는 방법에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-107">The logs that are available depend on how Log File Viewer is opened.</span></span>  
  
 <span data-ttu-id="e878c-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="e878c-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e878c-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="e878c-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e878c-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e878c-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e878c-111">보안</span><span class="sxs-lookup"><span data-stu-id="e878c-111">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="e878c-112">SQL Server Management Studio를 사용하여 SQL Server 에이전트 오류 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="e878c-112">To view the SQL Server Agent error log, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e878c-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e878c-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e878c-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e878c-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e878c-115">사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e878c-116">보안</span><span class="sxs-lookup"><span data-stu-id="e878c-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e878c-117">권한</span><span class="sxs-lookup"><span data-stu-id="e878c-117">Permissions</span></span>  
 <span data-ttu-id="e878c-118">해당 기능을 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **sysadmin** 고정 서버 역할 멤버인 계정의 자격 증명을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e878c-119">이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="e878c-120">서비스로 로그온(SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="e878c-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="e878c-121">프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="e878c-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="e878c-122">트래버스 검사 무시(SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="e878c-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="e878c-123">프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="e878c-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="e878c-124">에이전트 서비스 계정에 필요한 Windows 사용 권한에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 에이전트 서비스에 대 한 계정 선택](select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e878c-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e878c-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e878c-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-ssnoversion-agent-error-log"></a><span data-ttu-id="e878c-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="e878c-126">To view the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log</span></span>  
  
1.  <span data-ttu-id="e878c-127">**개체 탐색기**에서 더하기 기호를 클릭하여 보려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그가 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-127">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log that you want to view.</span></span>  
  
2.  <span data-ttu-id="e878c-128">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-128">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="e878c-129">더하기 기호를 클릭하여 **오류 로그** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-129">Click the plus sign to expand the **Error Logs** folder.</span></span>  
  
4.  <span data-ttu-id="e878c-130">보려는 오류 로그를 마우스 오른쪽 단추로 클릭하고 **에이전트 로그 보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-130">Right-click the error log you want to view and select **View Agent Log**.</span></span>  
  
     <span data-ttu-id="e878c-131">**로그 파일 뷰어-**_server_name_ 대화 상자에서 사용할 수 있는 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-131">The following options are available in the **Log File Viewer -**_server_name_ dialog box:</span></span>  
  
     <span data-ttu-id="e878c-132">**로그 로드**</span><span class="sxs-lookup"><span data-stu-id="e878c-132">**Load Log**</span></span>  
     <span data-ttu-id="e878c-133">로드할 로그 파일을 지정할 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-133">Open a dialog box where you can specify a log file to load.</span></span>  
  
     <span data-ttu-id="e878c-134">**내보내기**</span><span class="sxs-lookup"><span data-stu-id="e878c-134">**Export**</span></span>  
     <span data-ttu-id="e878c-135">**로그 파일 요약** 표에 표시된 정보를 텍스트 파일로 내보낼 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-135">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
     <span data-ttu-id="e878c-136">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="e878c-136">**Refresh**</span></span>  
     <span data-ttu-id="e878c-137">선택한 로그의 뷰를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-137">Refresh the view of the selected logs.</span></span> <span data-ttu-id="e878c-138">**새로 고침** 단추를 누르면 필터 설정을 적용하는 동안 대상 서버에서 선택한 로그를 다시 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-138">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
     <span data-ttu-id="e878c-139">**Filter**</span><span class="sxs-lookup"><span data-stu-id="e878c-139">**Filter**</span></span>  
     <span data-ttu-id="e878c-140">**연결**, **날짜**또는 기타 **일반** 필터 조건과 같이 로그 파일 필터링에 사용되는 설정을 지정할 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-140">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
     <span data-ttu-id="e878c-141">**검색**</span><span class="sxs-lookup"><span data-stu-id="e878c-141">**Search**</span></span>  
     <span data-ttu-id="e878c-142">로그 파일에서 특정 텍스트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-142">Search the log file for specific text.</span></span> <span data-ttu-id="e878c-143">와일드카드 문자를 사용한 검색은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-143">Searching with wildcard characters is not supported.</span></span>  
  
     <span data-ttu-id="e878c-144">**중지**</span><span class="sxs-lookup"><span data-stu-id="e878c-144">**Stop**</span></span>  
     <span data-ttu-id="e878c-145">로그 파일 항목의 로드를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-145">Stops loading the log file entries.</span></span> <span data-ttu-id="e878c-146">예를 들어 원격 또는 오프라인 로그 파일을 로드하는 데 시간이 오래 걸리며 최근 항목만 보려는 경우 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-146">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
     <span data-ttu-id="e878c-147">**로그 파일 요약**</span><span class="sxs-lookup"><span data-stu-id="e878c-147">**Log file summary**</span></span>  
     <span data-ttu-id="e878c-148">이 정보 창에는 로그 파일 필터링에 대한 요약이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-148">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="e878c-149">파일을 필터링하지 않은 경우 **적용된 필터 없음**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-149">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="e878c-150">로그에 필터를 적용한 경우에는 **로그 항목 필터링 조건:** \<filter criteria>라는 텍스트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-150">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
     <span data-ttu-id="e878c-151">**선택한 행 정보**</span><span class="sxs-lookup"><span data-stu-id="e878c-151">**Selected row details**</span></span>  
     <span data-ttu-id="e878c-152">선택한 이벤트 행에 대한 추가 정보를 페이지 아래쪽에 표시하려면 해당 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-152">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="e878c-153">열을 표의 새 위치로 끌어서 다시 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-153">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="e878c-154">표 머리글의 열 구분선을 왼쪽이나 오른쪽으로 끌어 열의 크기를 조정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-154">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="e878c-155">열 내용에 맞게 열 너비를 자동 조정하려면 표 머리글의 열 구분선을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-155">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
     <span data-ttu-id="e878c-156">**인스턴스**</span><span class="sxs-lookup"><span data-stu-id="e878c-156">**Instance**</span></span>  
     <span data-ttu-id="e878c-157">이벤트가 발생한 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-157">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="e878c-158">이 이름은 *컴퓨터 이름*\\*인스턴스 이름*으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-158">This is displayed as *computer name*\\*instance name*.</span></span>  
  
     <span data-ttu-id="e878c-159">**Date**</span><span class="sxs-lookup"><span data-stu-id="e878c-159">**Date**</span></span>  
     <span data-ttu-id="e878c-160">이벤트의 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-160">Displays the date of the event.</span></span>  
  
     <span data-ttu-id="e878c-161">**원본**</span><span class="sxs-lookup"><span data-stu-id="e878c-161">**Source**</span></span>  
     <span data-ttu-id="e878c-162">서비스의 이름(예: MSSQLSERVER)과 같이 이벤트가 생성된 원본 기능을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-162">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="e878c-163">이 열은 일부 로그 유형의 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-163">This does not appear for all log types.</span></span>  
  
     <span data-ttu-id="e878c-164">**메시지**</span><span class="sxs-lookup"><span data-stu-id="e878c-164">**Message**</span></span>  
     <span data-ttu-id="e878c-165">이벤트와 관련된 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-165">Displays any messages associated with the event.</span></span>  
  
     <span data-ttu-id="e878c-166">**로그 유형**</span><span class="sxs-lookup"><span data-stu-id="e878c-166">**Log Type**</span></span>  
     <span data-ttu-id="e878c-167">이벤트가 속한 로그의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-167">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="e878c-168">선택한 모든 로그가 로그 파일 요약 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-168">All selected logs appear in the log file summary window.</span></span>  
  
     <span data-ttu-id="e878c-169">**로그 원본**</span><span class="sxs-lookup"><span data-stu-id="e878c-169">**Log Source**</span></span>  
     <span data-ttu-id="e878c-170">이벤트가 캡처되는 원본 로그에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-170">Displays a description of the source log in which the event is captured.</span></span>  
  
5.  <span data-ttu-id="e878c-171">완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e878c-171">When finished, click **Close**.</span></span>  
  
  
