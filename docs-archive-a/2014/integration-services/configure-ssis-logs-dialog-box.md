---
title: SSIS 로그 구성 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.configuredtslogs.loggingdetails.f1
- sql12.dts.designer.configuredtslogs.providersandlogs.f1
- sql12.dts.designer.configuredtslogs.containers.f1
helpviewer_keywords:
- Configure SSIS Logs dialog box
ms.assetid: 4b980275-cd9a-4943-8c36-727d51f9a484
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 252b45765fb784790bcca0fb86e2e56e7e7baddc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649629"
---
# <a name="configure-ssis-logs-dialog-box"></a><span data-ttu-id="4758c-102">SSIS 로그 구성 대화 상자</span><span class="sxs-lookup"><span data-stu-id="4758c-102">Configure SSIS Logs Dialog Box</span></span>
  <span data-ttu-id="4758c-103">**SSIS 로그 구성** 대화 상자를 사용하여 패키지에 대한 로깅 옵션을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-103">Use the **Configure SSIS Logs** dialog box to define logging options for a package.</span></span>  
  
 <span data-ttu-id="4758c-104">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="4758c-104">**What do you want to do?**</span></span>  
  
1.  [<span data-ttu-id="4758c-105">SSIS 로그 구성 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="4758c-105">Open the Configure SSIS Logs Dialog Box</span></span>](#open_dialog)  
  
2.  [<span data-ttu-id="4758c-106">컨테이너 창의 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="4758c-106">Configure the Options in the Containers Pane</span></span>](#container)  
  
3.  [<span data-ttu-id="4758c-107">공급자 및 로그 탭의 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="4758c-107">Configure the Options on the Providers and Logs Tab</span></span>](#provider)  
  
4.  [<span data-ttu-id="4758c-108">자세히 탭의 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="4758c-108">Configure the Options on the Details Tab</span></span>](#detail)  
  
##  <a name="open-the-configure-ssis-logs-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="4758c-109">SSIS 로그 구성 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="4758c-109">Open the Configure SSIS Logs Dialog Box</span></span>  
 <span data-ttu-id="4758c-110">**SSIS 로그 구성 대화 상자를 열려면**</span><span class="sxs-lookup"><span data-stu-id="4758c-110">**To open the Configure SSIS Logs dialog box**</span></span>  
  
-   <span data-ttu-id="4758c-111">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너의 **SSIS** 메뉴에서 **로깅** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-111">In the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click **Logging** on the **SSIS** menu.</span></span>  
  
##  <a name="configure-the-options-in-the-containers-pane"></a><a name="container"></a> <span data-ttu-id="4758c-112">컨테이너 창의 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="4758c-112">Configure the Options in the Containers Pane</span></span>  
 <span data-ttu-id="4758c-113">**SSIS 로그 구성** 대화 상자의 **컨테이너** 창을 사용하여 패키지 및 해당 컨테이너에 대해 로깅을 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-113">Use the **Containers** pane of the **Configure SSIS Logs** dialog box to enable the package and its containers for logging.</span></span>  
  
### <a name="options"></a><span data-ttu-id="4758c-114">옵션</span><span class="sxs-lookup"><span data-stu-id="4758c-114">Options</span></span>  
 <span data-ttu-id="4758c-115">**컨테이너**</span><span class="sxs-lookup"><span data-stu-id="4758c-115">**Containers**</span></span>  
 <span data-ttu-id="4758c-116">패키지 및 해당 컨테이너에 대해 로깅을 활성화하려면 계층 뷰의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-116">Select the check boxes in the hierarchical view to enable the package and its containers for logging:</span></span>  
  
-   <span data-ttu-id="4758c-117">확인란의 선택을 취소하면 해당 컨테이너에 대해 로깅이 활성화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-117">If cleared, the container is not enabled for logging.</span></span> <span data-ttu-id="4758c-118">로깅을 활성화하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-118">Select to enable logging.</span></span>  
  
-   <span data-ttu-id="4758c-119">확인란이 흐리게 표시된 경우에는 해당 컨테이너에서 부모의 로깅 옵션을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-119">If dimmed, the container uses the logging options of its parent.</span></span> <span data-ttu-id="4758c-120">패키지에 대해서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-120">This option is not available for the package.</span></span>  
  
-   <span data-ttu-id="4758c-121">확인란을 선택하면 컨테이너에서 자체 로깅 옵션을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-121">If checked, the container defines its own logging options.</span></span>  
  
 <span data-ttu-id="4758c-122">컨테이너가 흐리게 표시되어 있는 경우 해당 컨테이너에 대해 로깅 옵션을 설정하려면 확인란을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-122">If a container is dimmed and you want to set logging options on the container, click its check box twice.</span></span> <span data-ttu-id="4758c-123">첫 번째 클릭은 확인란의 선택을 취소하고 두 번째 클릭은 확인란을 선택하여 사용할 로그 공급자 및 기록할 정보를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-123">The first click clears the check box, and the second click selects it, enabling you to choose the log providers to use and select the information to log.</span></span>  
  
##  <a name="configure-the-options-on-the-providers-and-logs-tab"></a><a name="provider"></a> <span data-ttu-id="4758c-124">공급자 및 로그 탭의 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="4758c-124">Configure the Options on the Providers and Logs Tab</span></span>  
 <span data-ttu-id="4758c-125">**SSIS 로그 구성** 대화 상자의 **공급자 및 로그** 탭을 사용하여 런타임 이벤트를 캡처하기 위한 로그를 생성 및 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-125">Use the **Providers and Logs** tab of the **Configure SSIS Logs** dialog box to create and configure logs for capturing run-time events.</span></span>  
  
### <a name="options"></a><span data-ttu-id="4758c-126">옵션</span><span class="sxs-lookup"><span data-stu-id="4758c-126">Options</span></span>  
 <span data-ttu-id="4758c-127">**공급자 유형**</span><span class="sxs-lookup"><span data-stu-id="4758c-127">**Provider type**</span></span>  
 <span data-ttu-id="4758c-128">목록에서 로그 공급자 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-128">Select a type of log provider from the list.</span></span>  
  
 <span data-ttu-id="4758c-129">**추가**</span><span class="sxs-lookup"><span data-stu-id="4758c-129">**Add**</span></span>  
 <span data-ttu-id="4758c-130">지정한 유형의 로그를 패키지의 로그 공급자 모음에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-130">Add a log of the specified type to the collection of log providers of the package.</span></span>  
  
 <span data-ttu-id="4758c-131">**이름**</span><span class="sxs-lookup"><span data-stu-id="4758c-131">**Name**</span></span>  
 <span data-ttu-id="4758c-132">**SSIS 로그 구성** 대화 상자의 **컨테이너** 창에서 선택한 컨테이너 또는 태스크에 대한 로그를 확인란을 사용하여 설정하거나 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-132">Enable or disable logs for containers or tasks selected in the **Containers** pane of the **Configure SSIS Logs** dialog box, by using the check boxes.</span></span> <span data-ttu-id="4758c-133">이름 필드는 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-133">The name field is editable.</span></span> <span data-ttu-id="4758c-134">공급자의 기본 이름을 사용하거나 설명이 포함된 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-134">Use the default name for the provider, or type a unique descriptive name.</span></span>  
  
 <span data-ttu-id="4758c-135">**설명**</span><span class="sxs-lookup"><span data-stu-id="4758c-135">**Description**</span></span>  
 <span data-ttu-id="4758c-136">설명 필드는 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-136">The description field is editable.</span></span> <span data-ttu-id="4758c-137">클릭한 다음 로그의 기본 설명을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-137">Click and then modify the default description of the log.</span></span>  
  
 <span data-ttu-id="4758c-138">**Configuration**</span><span class="sxs-lookup"><span data-stu-id="4758c-138">**Configuration**</span></span>  
 <span data-ttu-id="4758c-139">목록에서 기존 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-139">Select an existing connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span> <span data-ttu-id="4758c-140">로그 공급자의 유형에 따라 OLE DB 연결 관리자 또는 파일 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-140">Depending on the type of log provider, you can configure an OLE DB connection manager or a File connection manager.</span></span> <span data-ttu-id="4758c-141">[!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 이벤트 로그의 로그 공급자에는 연결이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-141">The log provider for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Event Log requires no connection.</span></span>  
  
 <span data-ttu-id="4758c-142">관련 항목: [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md) , [File Connection Manager](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="4758c-142">Related Topics: [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md) manager, [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
 <span data-ttu-id="4758c-143">**Delete**</span><span class="sxs-lookup"><span data-stu-id="4758c-143">**Delete**</span></span>  
 <span data-ttu-id="4758c-144">로그 공급자를 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-144">Select a log provider and then click **Delete**.</span></span>  
  
##  <a name="configure-the-options-on-the-details-tab"></a><a name="detail"></a> <span data-ttu-id="4758c-145">자세히 탭의 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="4758c-145">Configure the Options on the Details Tab</span></span>  
 <span data-ttu-id="4758c-146">**SSIS 로그 구성** 대화 상자의 **자세히** 탭을 사용하여 로깅에 사용할 이벤트와 로깅할 세부 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-146">Use the **Details** tab of the **Configure SSIS Logs** dialog box to specify the events to enable for logging and the information details to log.</span></span> <span data-ttu-id="4758c-147">선택한 정보는 패키지의 모든 로그 공급자에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-147">The information that you select applies to all the log providers in the package.</span></span> <span data-ttu-id="4758c-148">예를 들어 일부 정보는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 쓰고 다른 정보는 텍스트 파일에 쓰는 것은 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-148">For example, you cannot write some information to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and different information to a text file.</span></span>  
  
### <a name="options"></a><span data-ttu-id="4758c-149">옵션</span><span class="sxs-lookup"><span data-stu-id="4758c-149">Options</span></span>  
 <span data-ttu-id="4758c-150">**이벤트**</span><span class="sxs-lookup"><span data-stu-id="4758c-150">**Events**</span></span>  
 <span data-ttu-id="4758c-151">로깅할 이벤트를 설정 또는 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-151">Enable or disable events for logging.</span></span>  
  
 <span data-ttu-id="4758c-152">**설명**</span><span class="sxs-lookup"><span data-stu-id="4758c-152">**Description**</span></span>  
 <span data-ttu-id="4758c-153">이벤트에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-153">View a description of the event.</span></span>  
  
 <span data-ttu-id="4758c-154">**고급**</span><span class="sxs-lookup"><span data-stu-id="4758c-154">**Advanced**</span></span>  
 <span data-ttu-id="4758c-155">로깅할 이벤트를 선택하거나 선택을 취소하고, 각 이벤트에 대해 로깅할 정보를 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-155">Select or clear events to log, and select or clear information to log for each event.</span></span> <span data-ttu-id="4758c-156">이벤트 목록을 제외한 모든 로깅 세부 정보를 숨기려면 **기본** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-156">Click **Basic** to hide all logging details, except the list of events.</span></span> <span data-ttu-id="4758c-157">다음은 로깅에 사용할 수 있는 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-157">The following information is available for logging:</span></span>  
  
|<span data-ttu-id="4758c-158">값</span><span class="sxs-lookup"><span data-stu-id="4758c-158">Value</span></span>|<span data-ttu-id="4758c-159">Description</span><span class="sxs-lookup"><span data-stu-id="4758c-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4758c-160">**컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="4758c-160">**Computer**</span></span>|<span data-ttu-id="4758c-161">로깅된 이벤트가 발생한 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-161">The name of the computer on which the logged event occurred.</span></span>|  
|<span data-ttu-id="4758c-162">**연산자**</span><span class="sxs-lookup"><span data-stu-id="4758c-162">**Operator**</span></span>|<span data-ttu-id="4758c-163">패키지를 시작한 사람의 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-163">The user name of the person who started the package.</span></span>|  
|<span data-ttu-id="4758c-164">**SourceName**</span><span class="sxs-lookup"><span data-stu-id="4758c-164">**SourceName**</span></span>|<span data-ttu-id="4758c-165">로깅된 이벤트가 발생한 패키지, 컨테이너 및 태스크의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-165">The name of the package, container, or task in which the logged event occurred.</span></span>|  
|<span data-ttu-id="4758c-166">**SourceID**</span><span class="sxs-lookup"><span data-stu-id="4758c-166">**SourceID**</span></span>|<span data-ttu-id="4758c-167">로깅된 이벤트가 발생한 패키지, 컨테이너 또는 태스크의 GUID(Global Unique Identifier)입니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-167">The global unique identifier (GUID) of the package, container, or task in which the logged event occurred.</span></span>|  
|<span data-ttu-id="4758c-168">**ExecutionID**</span><span class="sxs-lookup"><span data-stu-id="4758c-168">**ExecutionID**</span></span>|<span data-ttu-id="4758c-169">패키지 실행 인스턴스의 GUID(Global Unique Identifier)입니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-169">The global unique identifier of the package execution instance.</span></span>|  
|<span data-ttu-id="4758c-170">**MessageText**</span><span class="sxs-lookup"><span data-stu-id="4758c-170">**MessageText**</span></span>|<span data-ttu-id="4758c-171">로그 항목과 연결된 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-171">A message associated with the log entry.</span></span>|  
|<span data-ttu-id="4758c-172">**DataBytes**</span><span class="sxs-lookup"><span data-stu-id="4758c-172">**DataBytes**</span></span>|<span data-ttu-id="4758c-173">다음에 사용하도록 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-173">Reserved for future use.</span></span>|  
  
 <span data-ttu-id="4758c-174">**기본**</span><span class="sxs-lookup"><span data-stu-id="4758c-174">**Basic**</span></span>  
 <span data-ttu-id="4758c-175">로깅할 이벤트를 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-175">Select or clear events to log.</span></span> <span data-ttu-id="4758c-176">이 옵션은 이벤트 목록을 제외한 로깅 세부 정보를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-176">This option hides logging details except the list of events.</span></span> <span data-ttu-id="4758c-177">이벤트를 선택한 경우 해당 이벤트에 대한 모든 로깅 세부 정보가 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-177">If you select an event, all logging details are selected for the event by default.</span></span> <span data-ttu-id="4758c-178">로깅 세부 정보를 모두 표시하려면 **고급** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-178">Click **Advanced** to show all logging details.</span></span>  
  
 <span data-ttu-id="4758c-179">**로드**</span><span class="sxs-lookup"><span data-stu-id="4758c-179">**Load**</span></span>  
 <span data-ttu-id="4758c-180">로깅 옵션을 설정하기 위한 템플릿으로 사용할 기존 XML 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-180">Specify an existing XML file to use as a template for setting logging options.</span></span>  
  
 <span data-ttu-id="4758c-181">**저장**</span><span class="sxs-lookup"><span data-stu-id="4758c-181">**Save**</span></span>  
 <span data-ttu-id="4758c-182">구성 세부 정보를 XML 파일에 템플릿으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4758c-182">Save configuration details as a template to an XML file.</span></span>  
  
  
