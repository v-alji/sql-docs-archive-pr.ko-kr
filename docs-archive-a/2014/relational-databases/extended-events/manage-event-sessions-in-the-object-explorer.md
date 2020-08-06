---
title: 개체 탐색기에서 이벤트 세션 관리 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
ms.assetid: 16849e38-d3fb-414d-8dcb-797b5ffce6ee
author: rothja
ms.author: jroth
ms.openlocfilehash: 1aa33a97137f63348898e6b1fcb7b19b2d218573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646460"
---
# <a name="manage-event-sessions-in-the-object-explorer"></a><span data-ttu-id="286e5-102">개체 탐색기에서 이벤트 세션 관리</span><span class="sxs-lookup"><span data-stu-id="286e5-102">Manage Event Sessions in the Object Explorer</span></span>
  <span data-ttu-id="286e5-103">이 항목에서는 **개체 탐색기** 에서 수행할 수 있는 확장 이벤트에 영향을 주는 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-103">This topic discusses the actions you can take in **Object Explorer** that affect Extended Events:</span></span>  
  
-   <span data-ttu-id="286e5-104">확장 이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="286e5-104">Create an Extended Events Session</span></span>  
  
-   <span data-ttu-id="286e5-105">확장 이벤트 세션 시작 또는 중지</span><span class="sxs-lookup"><span data-stu-id="286e5-105">Starting or Stopping an Extended Events Session</span></span>  
  
-   <span data-ttu-id="286e5-106">확장 이벤트 세션 내보내기</span><span class="sxs-lookup"><span data-stu-id="286e5-106">Export an Extended Events Session</span></span>  
  
-   <span data-ttu-id="286e5-107">확장 이벤트 세션 템플릿 가져오기</span><span class="sxs-lookup"><span data-stu-id="286e5-107">Import an Extended Events Session Template</span></span>  
  
-   <span data-ttu-id="286e5-108">확장 이벤트 세션 편집</span><span class="sxs-lookup"><span data-stu-id="286e5-108">Edit an Extended Events Session</span></span>  
  
-   <span data-ttu-id="286e5-109">확장 이벤트 세션 삭제</span><span class="sxs-lookup"><span data-stu-id="286e5-109">Delete an Extended Events Session</span></span>  
  
## <a name="create-an-extended-events-session"></a><span data-ttu-id="286e5-110">확장 이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="286e5-110">Create an Extended Events Session</span></span>  
 <span data-ttu-id="286e5-111">확장 이벤트 세션을 만드는 방법은 [Create an Extended Events Session](../../database-engine/create-an-extended-events-session.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="286e5-111">For more information about creating an Extended Events session, see [Create an Extended Events Session](../../database-engine/create-an-extended-events-session.md).</span></span>  
  
## <a name="starting-or-stopping-an-extended-events-session"></a><span data-ttu-id="286e5-112">확장 이벤트 세션 시작 또는 중지</span><span class="sxs-lookup"><span data-stu-id="286e5-112">Starting or Stopping an Extended Events Session</span></span>  
 <span data-ttu-id="286e5-113">**Query Editor** `ALTER EVENT SESSION` 문을 사용 하거나 **개체 탐색기**의 **확장 이벤트** 노드를 사용 하 여 쿼리 편집기를 통해 확장 이벤트 세션을 시작 하거나 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-113">You can start or stop an Extended Events session through the **Query Editor** using the `ALTER EVENT SESSION` statement, or by using the **Extended Events** node of **Object Explorer**.</span></span>  
  
 <span data-ttu-id="286e5-114">이벤트 세션을 중지하면 해당 세션은 sys.dm_xe_sessions DMV(동적 관리 뷰)에서 더 이상 활성 세션으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-114">When you stop an event session, the session is no longer listed as an active session in the sys.dm_xe_sessions dynamic management view (DMV).</span></span> <span data-ttu-id="286e5-115">그러나 세션 정의는 그대로 유지되므로 세션을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-115">However, the session definition remains intact, and you can restart the session.</span></span> <span data-ttu-id="286e5-116">세션 정의를 완전히 제거하려면 세션을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-116">To completely remove a session definition, you must delete the session.</span></span>  
  
 <span data-ttu-id="286e5-117">확장 이벤트 세션을 시작하거나 중지하려면 ALTER ANY EVENT SESSION 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-117">To start or stop an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
 <span data-ttu-id="286e5-118">링 버퍼, 버킷팅, 이벤트 쌍 또는 동기 이벤트 카운터 대상 등의 메모리 내 대상을 사용하는 세션을 중지하면 해당 세션의 버퍼(sys.dm_xe_session_targets DMV의 target_data 열)에 저장된 모든 정보가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-118">When you stop a session that uses an in-memory target, such as the ring buffer, bucketing, event pairing, or synchronous event counter targets, all the information stored in the session's buffer (the target_data column of the sys.dm_xe_session_targets DMV) will be lost.</span></span> <span data-ttu-id="286e5-119">세션을 중지한 후 이벤트 데이터에 액세스하려면 세션을 중지하기 전에 데이터를 저장하거나 파일 대상을 사용하도록 세션을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-119">To access event data after you stop the session, you should either save the data before you stop the session, or configure the session to use the file target.</span></span>  
  
### <a name="start-or-stop-an-extended-events-session-using-query-editor"></a><span data-ttu-id="286e5-120">쿼리 편집기를 사용하여 확장 이벤트 세션 시작 또는 중지</span><span class="sxs-lookup"><span data-stu-id="286e5-120">Start or Stop an Extended Events Session Using Query Editor</span></span>  
 <span data-ttu-id="286e5-121">세션을 시작하려면 다음 문을 실행합니다. *session_name* 을 확장 이벤트 세션의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-121">To start a session, issue the following statements, replacing *session_name* with the name of the Extended Events session:</span></span>  
  
```  
ALTER EVENT SESSION [session_name]  
ON SERVER  
STATE = START  
```  
  
 <span data-ttu-id="286e5-122">세션을 중지하려면 다음 문을 실행합니다. *session_name* 을 확장 이벤트 세션의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-122">To stop a session, issue the following statements, replacing *session_name* with the name of the Extended Events session:</span></span>  
  
```  
ALTER EVENT SESSION [session_name]  
ON SERVER  
STATE = STOP  
```  
  
### <a name="start-or-stop-an-extended-events-session-in-object-explorer"></a><span data-ttu-id="286e5-123">개체 탐색기에서 확장 이벤트 세션 시작 또는 중지</span><span class="sxs-lookup"><span data-stu-id="286e5-123">Start or Stop an Extended Events Session in Object Explorer</span></span>  
 <span data-ttu-id="286e5-124">**개체 탐색기**에서 확장 이벤트 세션을 시작하거나 중지하려면 **관리**, **확장 이벤트**및 **세션** 노드를 차례로 확장한 다음 세션을 마우스 오른쪽 단추로 클릭하고 **세션 시작** 또는 **세션 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-124">To start or stop an Extended Events session in **Object Explorer**, expand the **Management**, **Extended Events**, and then **Sessions** nodes and right click on a session and then click **Start Session** or **Stop Session**.</span></span>  
  
## <a name="export-an-extended-events-session-template"></a><span data-ttu-id="286e5-125">확장 이벤트 세션 템플릿 내보내기</span><span class="sxs-lookup"><span data-stu-id="286e5-125">Export an Extended Events Session Template</span></span>  
 <span data-ttu-id="286e5-126">**개체 탐색기**를 사용하여 확장 이벤트 세션을 내보내고 이 세션을 .xml 템플릿 파일로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-126">You can export an Extended Events session using **Object Explorer**, and save it as an .xml template file.</span></span> <span data-ttu-id="286e5-127">예를 들어 세션을 내보낸 다음 **새 세션 마법사** 또는 **새 세션** 마법사를 사용하여 새 이벤트 세션에 템플릿을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-127">For example, you may want to export a session and then apply the template to a new event session using the **New Session Wizard** or the **New Session** wizard.</span></span>  
  
 <span data-ttu-id="286e5-128">세션을 내보내는 경우 NTFS 파일 시스템을 사용하는 위치에 템플릿 파일을 저장하고, 인증된 사용자만 해당 정보를 볼 수 있도록 액세스를 제한해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-128">When you export a session, make sure that you save the template file to a location that uses the NTFS file system, and that you restrict access to users who are authorized to view the information.</span></span>  
  
 <span data-ttu-id="286e5-129">**개체 탐색기**에서 확장 이벤트 세션을 내보내려면</span><span class="sxs-lookup"><span data-stu-id="286e5-129">To export an Extended Events session in **Object Explorer**:</span></span>  
  
1.  <span data-ttu-id="286e5-130">**관리**, **확장 이벤트**및 **세션** 노드를 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-130">Expand the **Management**, **Extended Events**, and then **Sessions** nodes</span></span>  
  
2.  <span data-ttu-id="286e5-131">내보낼 세션을 마우스 오른쪽 단추로 클릭하고 **세션 내보내기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-131">Right-click the session that you want to export, and select **Export Session**.</span></span>  
  
3.  <span data-ttu-id="286e5-132">**다른 이름으로 저장** 대화 상자에서 파일을 저장할 위치를 선택하고 **파일 이름** 상자에 파일 이름을 입력한 다음 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-132">In the **Save As** dialog box, select a location to save the file, type the file name in the **File name** box, and then click **Save**.</span></span>  
  
     <span data-ttu-id="286e5-133">파일을 기본 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 템플릿 위치에 저장하면 **새 세션 마법사** 및 **새 세션** 대화 상자의 미리 정의된 템플릿 드롭다운 목록에 해당 템플릿이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-133">If you save the file to the default [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] template location, the template will appear in the dropdown list of predefined templates when you use the **New Session Wizard** and **New Session** dialog.</span></span>  
  
## <a name="import-an-extended-events-session-template"></a><span data-ttu-id="286e5-134">확장 이벤트 세션 템플릿 가져오기</span><span class="sxs-lookup"><span data-stu-id="286e5-134">Import an Extended Events Session Template</span></span>  
 <span data-ttu-id="286e5-135">**개체 탐색기**를 사용하여 확장 이벤트 세션 템플릿을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-135">Using **Object Explorer**, you can import a template for an Extended Events session.</span></span> <span data-ttu-id="286e5-136">예를 들어 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 내보낸 템플릿을 사용하여 세션을 만들려는 경우 템플릿을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-136">For example, you may want to do this to create a session from a template that was exported from another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="286e5-137">확장 이벤트 세션을 가져오려면 `ALTER ANY EVENT SESSION` 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-137">To import an Extended Events session, you must have the necessary `ALTER ANY EVENT SESSION` permissions.</span></span>  
  
 <span data-ttu-id="286e5-138">템플릿 파일을 가져오기 전에 파일 원본을 신뢰할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-138">Before you import a template file, make sure that the file is from a trusted source.</span></span> <span data-ttu-id="286e5-139">NTFS 파일 시스템을 사용하며 인증된 사용자만 해당 정보를 볼 수 있도록 액세스가 제한된 위치에 템플릿 파일을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-139">Template files should be saved to a location that uses the NTFS file system and where access is restricted to users who are authorized to view the information.</span></span>  
  
 <span data-ttu-id="286e5-140">확장 이벤트 세션을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="286e5-140">To import an Extended Events session:</span></span>  
  
1.  <span data-ttu-id="286e5-141">**개체 탐색기**에서 **관리**및 **확장 이벤트** 노드를 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-141">In **Object Explorer**, expand the **Management**, and then **Extended Events** nodes.</span></span>  
  
2.  <span data-ttu-id="286e5-142">**세션** 을 마우스 오른쪽 단추로 클릭하고 **새 세션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-142">Right-click **Sessions** and select **New Session**.</span></span>  
  
3.  <span data-ttu-id="286e5-143">세션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-143">Specify a name for the session.</span></span>  
  
4.  <span data-ttu-id="286e5-144">**템플릿** 드롭다운 상자를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-144">Expand the **Template** drop down box.</span></span>  
  
5.  <span data-ttu-id="286e5-145">**\<File From ...>열기**를 클릭하고 가져올 세션(XML 파일)을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-145">Click **\<File From ...>Open** and browse for the session (XML file) you want to import.</span></span>  
  
 <span data-ttu-id="286e5-146">해당 세션이 **세션** 노드에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-146">The session appears under the **Sessions** node.</span></span> <span data-ttu-id="286e5-147">기본적으로 세션은 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-147">By default, the session is not started.</span></span>  
  
## <a name="edit-an-extended-events-session"></a><span data-ttu-id="286e5-148">확장 이벤트 세션 편집</span><span class="sxs-lookup"><span data-stu-id="286e5-148">Edit an Extended Events Session</span></span>  
 <span data-ttu-id="286e5-149">개체 탐색기에서 확장 이벤트 세션을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-149">You can edit an Extended Events session in Object Explorer.</span></span>  
  
 <span data-ttu-id="286e5-150">확장 이벤트 세션을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="286e5-150">To edit an Extended Events session:</span></span>  
  
1.  <span data-ttu-id="286e5-151">**개체 탐색기**에서 **관리**, **확장 이벤트**, **세션** 노드를 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-151">In **Object Explorer**, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="286e5-152">세션을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-152">Right-click a session and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="286e5-153">**페이지 선택** 섹션에서 편집할 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-153">In the **Select a page** section, select the page or pages you want to edit.</span></span>  
  
4.  <span data-ttu-id="286e5-154">이벤트 세션을 수정한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-154">After you finish revising the event session, click **OK**.</span></span>  
  
## <a name="script-an-event-session-definition-using-tsql"></a><span data-ttu-id="286e5-155">다음을 사용하여 확장 이벤트 세션 스크립팅: [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="286e5-155">Script an Event Session Definition Using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
 <span data-ttu-id="286e5-156">새 세션 마법사와 새 세션 대화 상자에는 확장 이벤트 세션을 정의하는, [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 생성하는 스크립트 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-156">Both the New Session Wizard and the New Session dialog have a Script option that generates the [!INCLUDE[tsql](../../includes/tsql-md.md)] that defines the Extended Events session.</span></span>  
  
 <span data-ttu-id="286e5-157">세션 이름을 마우스 오른쪽 단추로 클릭하고 [!INCLUDE[tsql](../../includes/tsql-md.md)] 세션 스크립팅 **을 선택한 다음**Create **를 선택하여 기존 확장 이벤트 세션의**에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-157">You can access the [!INCLUDE[tsql](../../includes/tsql-md.md)] for an existing Extended Events session by right clicking the session name, selecting **Script Session as**, and then selecting **Create to**.</span></span>  
  
## <a name="delete-an-extended-events-session"></a><span data-ttu-id="286e5-158">확장 이벤트 세션 삭제</span><span class="sxs-lookup"><span data-stu-id="286e5-158">Delete an Extended Events Session</span></span>  
 <span data-ttu-id="286e5-159">다음과 같은 방법으로 확장 이벤트 세션을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-159">You can delete an Extended Events session:</span></span>  
  
-   <span data-ttu-id="286e5-160">쿼리 편집기에서 `DROP EVENT SESSION` 사용</span><span class="sxs-lookup"><span data-stu-id="286e5-160">In Query Editor using `DROP EVENT SESSION`.</span></span>  
  
-   <span data-ttu-id="286e5-161">**개체 탐색기**에서</span><span class="sxs-lookup"><span data-stu-id="286e5-161">In **Object Explorer**.</span></span>  
  
 <span data-ttu-id="286e5-162">이벤트 세션을 삭제하면 모든 구성 정보도 제거되므로 해당 세션 정의가 더 이상 sys.server_event_sessions 카탈로그 뷰에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-162">When you delete an event session, all configuration information is removed and the session definition no longer appears in the sys.server_event_sessions catalog view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="286e5-163">system_health 및 AlwaysOn_health에 포함 되어 있으며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 삭제 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="286e5-163">system_health and AlwaysOn_health are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; do not delete them.</span></span> <span data-ttu-id="286e5-164">system_health는 기본적으로 사용됩니다. 자세한 내용은 [system_health 세션 사용](use-the-ssms-xe-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="286e5-164">system_health is enabled by default (for more information, see [Use the system_health Session](use-the-ssms-xe-profiler.md)).</span></span> <span data-ttu-id="286e5-165">AlwaysOn_health은 기본적으로 해제 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-165">AlwaysOn_health is off by default.</span></span> <span data-ttu-id="286e5-166">이러한 세션은 성능 문제를 진단하는 데 유용한 데이터를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-166">These sessions collect data that can be useful for diagnosing performance issues.</span></span>  
  
 <span data-ttu-id="286e5-167">확장 이벤트 세션을 삭제하려면 ALTER ANY EVENT SESSION 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-167">To delete an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
 <span data-ttu-id="286e5-168">**개체 탐색기**에서 확장 이벤트 세션을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="286e5-168">To delete an Extended Events session in **Object Explorer**:</span></span>  
  
1.  <span data-ttu-id="286e5-169">**관리**, **확장 이벤트**및 **세션** 노드를 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-169">Expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="286e5-170">세션을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-170">Right-click a session and select **Delete**.</span></span>  
  
3.  <span data-ttu-id="286e5-171">**개체 삭제** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-171">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="286e5-172">이벤트 세션을 수정한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-172">After you finish revising the event session, click **OK**.</span></span>  
  
 <span data-ttu-id="286e5-173">**쿼리 편집기**에서 확장 이벤트 세션을 삭제하려면 다음 문을 실행합니다. *session_name* 을 삭제할 확장 이벤트 세션의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="286e5-173">To delete an Extended Events session in the **Query Editor**, Issue the following statements, replacing *session_name* with the name of the Extended Events session that you want to delete:</span></span>  
  
```  
DROP EVENT SESSION [session_name]  
ON SERVER  
```  
  
  
