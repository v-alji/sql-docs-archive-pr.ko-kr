---
title: 로그 파일 뷰어 F1 도움말 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.errorlog.f1
helpviewer_keywords:
- Log File Viewer
ms.assetid: 2243845c-4880-4aa0-9ee8-0a97a128996b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6eadb4baa4a47202b40a9cde1eca896022f31d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649537"
---
# <a name="log-file-viewer-f1-help"></a><span data-ttu-id="7745b-102">로그 파일 뷰어 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="7745b-102">Log File Viewer F1 Help</span></span>
  <span data-ttu-id="7745b-103">로그 파일 뷰어는 다양한 구성 요소의 로그 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-103">Log File Viewer displays log information from many different components.</span></span> <span data-ttu-id="7745b-104">로그 파일 뷰어를 연 다음 **로그 선택** 창을 사용하여 표시할 로그를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-104">When Log File Viewer is open, use the **Select logs** pane to select the logs you want to display.</span></span> <span data-ttu-id="7745b-105">각 로그는 해당 로그 유형에 적합한 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-105">Each log displays columns appropriate to that kind of log.</span></span>  
  
 <span data-ttu-id="7745b-106">사용 가능한 로그는 로그 파일 뷰어를 여는 방법에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-106">The logs that are available depend on how Log File Viewer is opened.</span></span> <span data-ttu-id="7745b-107">자세한 내용은 [로그 파일 뷰어 열기](open-log-file-viewer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7745b-107">For more information, see [Open Log File Viewer](open-log-file-viewer.md).</span></span>  
  
 <span data-ttu-id="7745b-108">감사 로그에 대해 표시되는 행 수는 **도구/옵션** 대화 상자의 **SQL Server 개체 탐색기/명령** 페이지에서 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-108">The number of rows that are displayed for audit logs can be configured on the **SQL Server Object Explorer/Commands** page of the **Tools/Options** dialog box.</span></span> <span data-ttu-id="7745b-109">감사 로그에 대해 표시되는 열에 대한 설명은 [sys.fn_get_audit_file&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7745b-109">For descriptions of the columns that are displayed for audit logs, see [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7745b-110">옵션</span><span class="sxs-lookup"><span data-stu-id="7745b-110">Options</span></span>  
 <span data-ttu-id="7745b-111">**로그 로드**</span><span class="sxs-lookup"><span data-stu-id="7745b-111">**Load Log**</span></span>  
 <span data-ttu-id="7745b-112">로드할 로그 파일을 지정할 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-112">Open a dialog box where you can specify a log file to load.</span></span>  
  
 <span data-ttu-id="7745b-113">**내보내기**</span><span class="sxs-lookup"><span data-stu-id="7745b-113">**Export**</span></span>  
 <span data-ttu-id="7745b-114">**로그 파일 요약** 표에 표시된 정보를 텍스트 파일로 내보낼 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-114">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
 <span data-ttu-id="7745b-115">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="7745b-115">**Refresh**</span></span>  
 <span data-ttu-id="7745b-116">선택한 로그의 뷰를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-116">Refresh the view of the selected logs.</span></span> <span data-ttu-id="7745b-117">**새로 고침** 단추를 누르면 필터 설정을 적용하는 동안 대상 서버에서 선택한 로그를 다시 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-117">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
 <span data-ttu-id="7745b-118">**Filter**</span><span class="sxs-lookup"><span data-stu-id="7745b-118">**Filter**</span></span>  
 <span data-ttu-id="7745b-119">**연결**, **날짜**또는 기타 **일반** 필터 조건과 같이 로그 파일 필터링에 사용되는 설정을 지정할 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-119">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
 <span data-ttu-id="7745b-120">**검색**</span><span class="sxs-lookup"><span data-stu-id="7745b-120">**Search**</span></span>  
 <span data-ttu-id="7745b-121">로그 파일에서 특정 텍스트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-121">Search the log file for specific text.</span></span> <span data-ttu-id="7745b-122">와일드카드 문자를 사용한 검색은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-122">Searching with wildcard characters is not supported.</span></span>  
  
 <span data-ttu-id="7745b-123">**중지**</span><span class="sxs-lookup"><span data-stu-id="7745b-123">**Stop**</span></span>  
 <span data-ttu-id="7745b-124">로그 파일 항목의 로드를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-124">Stops loading the log file entries.</span></span> <span data-ttu-id="7745b-125">예를 들어 원격 또는 오프라인 로그 파일을 로드하는 데 시간이 오래 걸리며 최근 항목만 보려는 경우 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-125">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
 <span data-ttu-id="7745b-126">**로그 파일 요약**</span><span class="sxs-lookup"><span data-stu-id="7745b-126">**Log file summary**</span></span>  
 <span data-ttu-id="7745b-127">이 정보 창에는 로그 파일 필터링에 대한 요약이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-127">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="7745b-128">파일을 필터링하지 않은 경우 **적용된 필터 없음**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-128">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="7745b-129">로그에 필터를 적용한 경우에는 **로그 항목 필터링 조건:** \<filter criteria>라는 텍스트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-129">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
 <span data-ttu-id="7745b-130">**선택한 행 정보**</span><span class="sxs-lookup"><span data-stu-id="7745b-130">**Selected row details**</span></span>  
 <span data-ttu-id="7745b-131">선택한 이벤트 행에 대한 추가 정보를 페이지 아래쪽에 표시하려면 해당 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-131">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="7745b-132">열을 표의 새 위치로 끌어서 다시 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-132">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="7745b-133">표 머리글의 열 구분선을 왼쪽이나 오른쪽으로 끌어 열의 크기를 조정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-133">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="7745b-134">열 내용에 맞게 열 너비를 자동 조정하려면 표 머리글의 열 구분선을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-134">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
 <span data-ttu-id="7745b-135">**인스턴스**</span><span class="sxs-lookup"><span data-stu-id="7745b-135">**Instance**</span></span>  
 <span data-ttu-id="7745b-136">이벤트가 발생한 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-136">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="7745b-137">이 이름은 *컴퓨터 이름*\\*인스턴스 이름*으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-137">This is displayed as *computer name*\\*instance name*.</span></span>  
  
## <a name="frequently-displayed-columns"></a><span data-ttu-id="7745b-138">일반적으로 표시되는 열</span><span class="sxs-lookup"><span data-stu-id="7745b-138">Frequently Displayed Columns</span></span>  
 <span data-ttu-id="7745b-139">**Date**</span><span class="sxs-lookup"><span data-stu-id="7745b-139">**Date**</span></span>  
 <span data-ttu-id="7745b-140">이벤트의 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-140">Displays the date of the event.</span></span>  
  
 <span data-ttu-id="7745b-141">**원본**</span><span class="sxs-lookup"><span data-stu-id="7745b-141">**Source**</span></span>  
 <span data-ttu-id="7745b-142">서비스의 이름(예: MSSQLSERVER)과 같이 이벤트가 생성된 원본 기능을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-142">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="7745b-143">이 열은 일부 로그 유형의 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-143">This does not appear for all log types.</span></span>  
  
 <span data-ttu-id="7745b-144">**메시지**</span><span class="sxs-lookup"><span data-stu-id="7745b-144">**Message**</span></span>  
 <span data-ttu-id="7745b-145">이벤트와 관련된 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-145">Displays any messages associated with the event.</span></span>  
  
 <span data-ttu-id="7745b-146">**로그 유형**</span><span class="sxs-lookup"><span data-stu-id="7745b-146">**Log Type**</span></span>  
 <span data-ttu-id="7745b-147">이벤트가 속한 로그의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-147">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="7745b-148">선택한 모든 로그가 로그 파일 요약 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-148">All selected logs appear in the log file summary window.</span></span>  
  
 <span data-ttu-id="7745b-149">**로그 원본**</span><span class="sxs-lookup"><span data-stu-id="7745b-149">**Log Source**</span></span>  
 <span data-ttu-id="7745b-150">이벤트가 캡처되는 원본 로그에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-150">Displays a description of the source log in which the event is captured.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="7745b-151">사용 권한</span><span class="sxs-lookup"><span data-stu-id="7745b-151">Permissions</span></span>  
 <span data-ttu-id="7745b-152">온라인 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 로그 파일에 액세스하려면 securityadmin 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-152">To access log files for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that are online, this requires membership in the securityadmin fixed server role.</span></span>  
  
 <span data-ttu-id="7745b-153">오프라인 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 로그 파일에 액세스하려면 **Root\Microsoft\SqlServer\ComputerManagement10** WMI 네임스페이스 및 로그 파일이 저장된 폴더 모두에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7745b-153">To access log files for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that are offline, you must have read access to both the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace, and to the folder where the log files are stored.</span></span> <span data-ttu-id="7745b-154">자세한 내용은 [오프라인 로그 파일 보기](view-offline-log-files.md)항목의 보안 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7745b-154">For more information, see the Security section of the topic [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7745b-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7745b-155">See Also</span></span>  
 <span data-ttu-id="7745b-156">[로그 파일 뷰어](log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="7745b-156">[Log File Viewer](log-file-viewer.md) </span></span>  
 <span data-ttu-id="7745b-157">[로그 파일 뷰어 열기](open-log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="7745b-157">[Open Log File Viewer](open-log-file-viewer.md) </span></span>  
 [<span data-ttu-id="7745b-158">오프라인 로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="7745b-158">View Offline Log Files</span></span>](view-offline-log-files.md)  
  
  
