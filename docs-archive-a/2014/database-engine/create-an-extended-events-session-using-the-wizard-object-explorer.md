---
title: 마법사를 사용 하 여 확장 이벤트 세션 만들기 (개체 탐색기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- Sql12.ssms.XeWizard.Summary.f1
- Sql12.ssms.XeWizard.SetSessionProperties.f1
- Sql12.ssms.XeWizard.CaptureAddFields.f1
- Sql12.ssms.XeWizard.SelectEvents.f1
- Sql12.ssms.XeWizard.SpecifySessionTargets.f1
- Sql12.ssms.XeWizard.Welcome.f1
- sql12.ssms.XeWizard.Welcome.f1
- Sql12.ssms.XeWizard.ChooseTemplate.f1
- Sql12.ssms.XeWizard.SetSessionEventFilters.f1
- Sql12.ssms.XeWizard.Results.f1
helpviewer_keywords:
- Sql11.ssms.XeWizard.CaptureAddFields.f1
- Sql11.ssms.XeWizard.SetSessionEventFilters.f1
- Sql11.ssms.XeWizard.SpecifySessionTargets.f1
- Sql11.ssms.XeWizard.Results.f1
- Sql11.ssms.XeWizard.ChooseTemplate.f1
- Sql11.ssms.XeWizard.SetSessionProperties.f1
- Sql11.ssms.XeWizard.Welcome.f1
- Sql11.ssms.XeWizard.Summary.f1
- Sql11.ssms.XeWizard.SelectEvents.f1
ms.assetid: 80c0456f-17c0-41d8-b2aa-502a2f3bb6de
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cdfc9141b0b99d5b06fc73044b8f4fae623922b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651251"
---
# <a name="create-an-extended-events-session-using-the-wizard-object-explorer"></a><span data-ttu-id="e1421-102">마법사를 사용하여 확장 이벤트 세션을 만들기(개체 탐색기)</span><span class="sxs-lookup"><span data-stu-id="e1421-102">Create an Extended Events Session Using the Wizard (Object Explorer)</span></span>
  <span data-ttu-id="e1421-103">서버의 이벤트를 손쉽게 선택하고 캡처할 수 있도록 확장 이벤트에는 확장 이벤트 세션을 만드는 단계를 안내해 주는 새 세션 마법사가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-103">To help you select and capture events on your server, Extended Events includes a New Session Wizard that guides you through the steps to create an Extended Events session.</span></span> <span data-ttu-id="e1421-104">새 세션 마법사에는 대부분의 확장 이벤트 기능이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-104">The New Session Wizard exposes most of the Extended Events functionality.</span></span> <span data-ttu-id="e1421-105">[새 세션 대화 상자](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md) 에서는 데이터를 캡처, 표시 및 분석하는 확장 이벤트 세션을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-105">The [New Session dialog](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md) also lets you define an Extended Events session that captures, displays, and analyzes your data.</span></span> <span data-ttu-id="e1421-106">새 세션 대화 상자에는 모든 확장 이벤트 기능이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-106">The New Session dialog exposes all Extended Events functionality.</span></span>  
  
### <a name="to-open-the-new-session-wizard"></a><span data-ttu-id="e1421-107">새 세션 마법사를 열려면</span><span class="sxs-lookup"><span data-stu-id="e1421-107">To open the New Session Wizard</span></span>  
  
1.  <span data-ttu-id="e1421-108">개체 탐색기에서 **관리** 노드를 확장하고 **확장 이벤트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-108">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="e1421-109">**세션**을 마우스 오른쪽 단추로 클릭하고 **새 세션 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-109">Right-click **Sessions**, and then click **New Session Wizard**.</span></span>  
  
### <a name="use-the-following-new-session-wizard-pages-to-create-an-event-session"></a><span data-ttu-id="e1421-110">새 세션 마법사 페이지를 사용하여 이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="e1421-110">Use the following New Session Wizard pages to create an event session</span></span>  
  
-   [<span data-ttu-id="e1421-111">소개</span><span class="sxs-lookup"><span data-stu-id="e1421-111">Introduction</span></span>](#BKMK_Welcome)  
  
-   [<span data-ttu-id="e1421-112">세션 속성 설정</span><span class="sxs-lookup"><span data-stu-id="e1421-112">Set Session Properties</span></span>](#BKMK_SetSessionProperties)  
  
-   [<span data-ttu-id="e1421-113">템플릿 선택</span><span class="sxs-lookup"><span data-stu-id="e1421-113">Choose Template</span></span>](#BKMK_ChooseTemplate)  
  
-   [<span data-ttu-id="e1421-114">캡처할 이벤트 선택</span><span class="sxs-lookup"><span data-stu-id="e1421-114">Select Events to Capture</span></span>](#BKMK_SelectEventsToCapture)  
  
-   [<span data-ttu-id="e1421-115">전역 필드 캡처</span><span class="sxs-lookup"><span data-stu-id="e1421-115">Capture Global Fields</span></span>](#BKMK_CaptureGlobalFields)  
  
-   [<span data-ttu-id="e1421-116">세션 이벤트 필터 설정</span><span class="sxs-lookup"><span data-stu-id="e1421-116">Set Session Event Filters</span></span>](#BKMK_SetSessionEventFilters)  
  
-   [<span data-ttu-id="e1421-117">세션 데이터 스토리지 지정</span><span class="sxs-lookup"><span data-stu-id="e1421-117">Specify Session Data Storage</span></span>](#BKMK_SpecifySessionDataOutput)  
  
-   [<span data-ttu-id="e1421-118">요약</span><span class="sxs-lookup"><span data-stu-id="e1421-118">Summary</span></span>](#BKMK_Summary)  
  
-   [<span data-ttu-id="e1421-119">이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="e1421-119">Create Event Session</span></span>](#BKMK_CreateEventSession)  
  
##  <a name="introduction"></a><a name="BKMK_Welcome"></a><span data-ttu-id="e1421-120">간략하게</span><span class="sxs-lookup"><span data-stu-id="e1421-120">Introduction</span></span>  
 <span data-ttu-id="e1421-121">**소개** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-121">On the **Introduction** page, do the following:</span></span>  
  
-   <span data-ttu-id="e1421-122">새 세션 마법사의 **소개** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-122">On the **Introduction** page of the New Session Wizard, click **Next**.</span></span>  
  
     <span data-ttu-id="e1421-123">마법사를 두 번 이상 사용하려는 경우 마법사를 시작할 때마다 소개가 나타나지 않도록 하려면 **이 페이지를 다시 표시 안 함** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-123">Select the **Do not show this page again** check box if you will be using the wizard more than once and do not want to read the introduction each time the wizard is launched.</span></span>  
  
##  <a name="set-session-properties"></a><a name="BKMK_SetSessionProperties"></a><span data-ttu-id="e1421-124">세션 속성 설정</span><span class="sxs-lookup"><span data-stu-id="e1421-124">Set Session Properties</span></span>  
 <span data-ttu-id="e1421-125">**세션 속성 설정** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-125">On the **Set Session Properties** page, do the following:</span></span>  
  
-   <span data-ttu-id="e1421-126">**세션 이름** 상자에 이벤트 세션에 대한 의미 있는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-126">In the **Session name** box, type a meaningful name for the event session.</span></span>  
  
     <span data-ttu-id="e1421-127">서버를 시작할 때 세션을 시작하려면 **서버 시작 시 이벤트 세션 시작** 확인란을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-127">If you want to start the session when you start the server, select the **Start the event session at server startup** check box, and then click **Next**.</span></span>  
  
##  <a name="choose-template"></a><a name="BKMK_ChooseTemplate"></a><span data-ttu-id="e1421-128">템플릿 선택</span><span class="sxs-lookup"><span data-stu-id="e1421-128">Choose Template</span></span>  
 <span data-ttu-id="e1421-129">**템플릿 선택** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-129">On the **Choose Template** page, do the following:</span></span>  
  
-   <span data-ttu-id="e1421-130">일반적인 문제를 위해 디자인된 미리 구성된 템플릿 집합에서 선택하려면 **다음 이벤트 세션 템플릿 사용** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-130">Select the **Use this event session template** option to select from a set of pre-configured templates designed for common problems.</span></span> <span data-ttu-id="e1421-131">드롭다운 목록에서 사용할 템플릿을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-131">Select the template you want to use from the drop-down list, and then click **Next**.</span></span>  
  
     <span data-ttu-id="e1421-132">또는</span><span class="sxs-lookup"><span data-stu-id="e1421-132">-OR-</span></span>  
  
-   <span data-ttu-id="e1421-133">미리 구성된 템플릿을 사용하지 않으려면 **템플릿 사용 안 함** 옵션을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-133">Select the **Do not use a template** option if you do not want to use any pre-configured template, and then click **Next**.</span></span>  
  
##  <a name="select-events-to-capture"></a><a name="BKMK_SelectEventsToCapture"></a><span data-ttu-id="e1421-134">캡처할 이벤트 선택</span><span class="sxs-lookup"><span data-stu-id="e1421-134">Select Events to Capture</span></span>  
 <span data-ttu-id="e1421-135">**캡처할 이벤트 선택** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-135">On the **Select Events to Capture** page, do the following:</span></span>  
  
1.  <span data-ttu-id="e1421-136">**이벤트 라이브러리**에서 캡처할 이벤트를 선택한 다음 오른쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-136">Select the events you want to capture from the **Event library**, and then click the right arrow.</span></span> <span data-ttu-id="e1421-137">이벤트 라이브러리에서 Shift 키 또는 Ctrl 키를 누른 상태로 각 이벤트를 클릭하여 여러 이벤트를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-137">You can select multiple events in the Event Library by using either Shift+Click or Ctrl+Click.</span></span>  
  
     <span data-ttu-id="e1421-138">드롭다운 목록 상자에서 캡처하려는 이벤트를 검색할 방법을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-138">You can select how you want to search for the events you want to capture from the drop-down list box.</span></span> <span data-ttu-id="e1421-139">예를 들어 이벤트 이름을 검색하거나 이벤트 이름과 설명을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-139">For example, you can search for event names or event names and their descriptions.</span></span> <span data-ttu-id="e1421-140">**이벤트 라이브러리** 상자에 검색할 텍스트를 입력하여 테이블의 단어를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-140">You can search for any word in the table by entering the text you want to search for in the **Event library** box.</span></span> <span data-ttu-id="e1421-141">예를 들어 **lock_acquired** 이벤트를 찾으려면 **lock**또는 **lock acquire**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-141">For example, if you want to find the **lock_acquired** event, you can enter **lock**, or **lock acquire**.</span></span>  
  
     <span data-ttu-id="e1421-142">선택한 이벤트는 **선택한 이벤트** 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-142">The events you select appear in the **Selected events** box.</span></span> <span data-ttu-id="e1421-143">**선택한 이벤트** 상자에서 이벤트를 제거하려면 왼쪽 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-143">To remove events from the **Selected events** box, click the left arrow.</span></span>  
  
2.  <span data-ttu-id="e1421-144">캡처할 이벤트를 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-144">After you select the events you want to capture, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1421-145">**디버그** 채널의 이벤트는 기본적으로 숨겨져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-145">Events from the **Debug** channel are hidden by default.</span></span> <span data-ttu-id="e1421-146">디버그 이벤트를 표시하려면 **채널** 드롭다운 목록에서 **디버그** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-146">To display debug events, select **Debug** from the **Channel** drop-down list.</span></span>  
  
##  <a name="capture-global-fields"></a><a name="BKMK_CaptureGlobalFields"></a><span data-ttu-id="e1421-147">전역 필드 캡처</span><span class="sxs-lookup"><span data-stu-id="e1421-147">Capture Global Fields</span></span>  
 <span data-ttu-id="e1421-148">동작이라고도 하는 전역 필드를 사용하여 선택한 이벤트에 대한 단일 동작 또는 여러 동작을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-148">You use global fields (also referred to as actions) to associate single or multiple actions for your selected events.</span></span> <span data-ttu-id="e1421-149">**템플릿 선택** 페이지에서 템플릿을 선택한 경우 템플릿에 정의된 모든 전역 필드가 이 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-149">If you selected a template on the **Choose Template** page, all of the global fields that are defined in the template are displayed on this page.</span></span>  
  
 <span data-ttu-id="e1421-150">**전역 필드 캡처** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-150">On the **Capture Global Fields** page, do the following:</span></span>  
  
-   <span data-ttu-id="e1421-151">이벤트 세션에 대해 캡처할 전역 필드를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-151">Select the global fields that you want to capture for the event session, and then click **Next**.</span></span>  
  
     <span data-ttu-id="e1421-152">전역 필드 옆의 확인란을 선택하거나 선택 취소하여 전역 필드를 제거 또는 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-152">You can remove or add global fields by selecting or clearing the check box next to the global field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1421-153">선택한 동작은 **이름** 별로 정렬되므로 관련 동작을 사전순으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-153">The selected actions are sorted by **Name** enabling you to view the associated actions in alphabetical order.</span></span> <span data-ttu-id="e1421-154">필드 이름 옆의 열 머리글을 클릭하여 설명이나 사용/사용 안 함 상태별로 정렬할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-154">You can sort by description or by the enable/disable status by clicking the column heading next to the field name.</span></span>  
  
##  <a name="set-session-event-filters"></a><a name="BKMK_SetSessionEventFilters"></a><span data-ttu-id="e1421-155">세션 이벤트 필터 설정</span><span class="sxs-lookup"><span data-stu-id="e1421-155">Set Session Event Filters</span></span>  
 <span data-ttu-id="e1421-156">조건자라고도 하는 필터를 적용하여 캡처할 이벤트를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-156">You can apply filters (also called predicates) to limit the events that you want to capture.</span></span> <span data-ttu-id="e1421-157">**세션 이벤트 필터 설정** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-157">On the **Set Session Event Filters** page, do the following:</span></span>  
  
1.  <span data-ttu-id="e1421-158">미리 구성된 템플릿을 사용하지 않는 경우 필터 조건을 만들고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-158">If you are not using a pre-configured template, create your filter criteria, and then click **Next**.</span></span>  
  
     <span data-ttu-id="e1421-159">미리 구성된 템플릿을 사용하는 경우 새 세션 마법사의 **템플릿의 필터(읽기 전용)** 섹션에 템플릿에서 이미 만들어진 필터가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-159">If you are using a pre-configured template, in the **Filters from template (read-only)** section, the New Session Wizard lists filters already created from the template.</span></span>  
  
2.  <span data-ttu-id="e1421-160">**추가 필터** 섹션에서 이벤트 세션에 대한 추가 필터를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-160">In the **Additional filters** section, you can configure additional filters for the event session.</span></span>  
  
     <span data-ttu-id="e1421-161">구성한 필터는 선택한 모든 이벤트에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-161">The filters you configure apply to all selected events.</span></span> <span data-ttu-id="e1421-162">새 세션 마법사에서는 각 이벤트에 대한 필터를 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-162">The New Session Wizard does not support configuring filters for each event.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1421-163">필터에 대한 그룹 절을 구성한 경우 결과를 저장하면 중복 괄호가 필터에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-163">When you configure a group clause for your filter, redundant parentheses are removed from the filter after the result is saved.</span></span> <span data-ttu-id="e1421-164">예를 들어 필터 그룹 **Clause 1** 및 **Clause 2**를 만든 경우 절 주위에 괄호가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-164">For example, if you create a filter grouping **Clause 1** and **Clause 2**, parentheses will appear around the clauses.</span></span> <span data-ttu-id="e1421-165">필터를 저장하면 중복 괄호가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-165">After you save the filter, the redundant parentheses are removed.</span></span> <span data-ttu-id="e1421-166">괄호가 제거되어도 필터 논리에는 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-166">The removal of the parentheses does not affect the filter logic.</span></span>  
  
##  <a name="specify-session-data-storage"></a><a name="BKMK_SpecifySessionDataOutput"></a><span data-ttu-id="e1421-167">세션 데이터 저장소 지정</span><span class="sxs-lookup"><span data-stu-id="e1421-167">Specify Session Data Storage</span></span>  
 <span data-ttu-id="e1421-168">**세션 데이터 스토리지 지정** 페이지를 사용하여 분석을 위해 데이터를 수집할 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-168">You use the **Specify Session Data Storage** page to specify how you want to collect your data for analysis.</span></span> <span data-ttu-id="e1421-169">SQL Server 확장 이벤트는 데이터 출력의 대상을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-169">SQL Server Extended Events uses targets for data output.</span></span> <span data-ttu-id="e1421-170">대상은 이벤트 데이터를 저장하고 파일에 쓰기 및 이벤트 데이터 집계 등의 동작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-170">Targets store event data and can perform actions such as writing to a file and aggregating event data.</span></span> <span data-ttu-id="e1421-171">분석을 위해 데이터를 수집할 방법을 결정하고 **세션 데이터 스토리지 지정** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-171">Decide how you want to collect your data for analysis, and on the **Specify Session Data Storage** page, do the following:</span></span>  
  
1.  <span data-ttu-id="e1421-172">큰 데이터 집합에 대한 기록 레코드를 만드는 경우 **나중에 분석할 수 있도록 데이터를 파일에 저장합니다.** 확인란을 선택하고 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-172">For large data sets and creating historical records, select the **Save data to a file for later analysis** check box, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="e1421-173">**서버의 파일 이름** 상자에 경로와 파일 이름을 입력하거나, **찾아보기** 를 클릭하여 데이터를 저장할 서버의 파일 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-173">In the **File name on server** box, enter the path and file name, or click **Browse** to specify the file directory on the server where you want to save the data.</span></span>  
  
    2.  <span data-ttu-id="e1421-174">**최대 파일 크기** 상자에서 파일 대상에 사용할 최대 파일 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-174">In the **Maximum file size** box, specify the maximum file size to be used for the file target.</span></span> <span data-ttu-id="e1421-175">최대 파일 크기를 지정하지 않으면 디스크가 가득 찰 때까지 파일 크기가 계속 커집니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-175">If you do not specify the maximum file size, the file will grow until the disk is full.</span></span> <span data-ttu-id="e1421-176">기본 파일 크기는 1GB입니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-176">The default file size is 1 gigabyte (GB).</span></span>  
  
    3.  <span data-ttu-id="e1421-177">파일 대상에 대해 파일 롤오버를 사용하도록 설정하려면 **파일 롤오버 사용** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-177">Select the **Enable file rollover** check box to enable file rollover for the file target.</span></span>  
  
    4.  <span data-ttu-id="e1421-178">**최대 파일 수** 상자에서 파일 시스템에 보관할 최대 파일 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-178">In the **Maximum number of files** box, specify the maximum number of files you want to retain in the file system.</span></span>  
  
2.  <span data-ttu-id="e1421-179">최근 데이터를 수집하려는 경우 **가장 최근 데이터만 사용합니다(ring_buffer 대상)** 확인란을 선택하고 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-179">For collecting recent data, select the **Work with only the most recent data (ring buffer target)** check box, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="e1421-180">**유지할 이벤트 수** 상자에서 보관할 이벤트 수를 입력하거나 위쪽 및 아래쪽 화살표를 사용하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-180">In the **Number of events to keep** box, enter or select the number of events you want to keep by using the up and down arrows.</span></span>  
  
    2.  <span data-ttu-id="e1421-181">**최대 버퍼 메모리 크기** 상자에서 사용할 버퍼 메모리의 최대 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-181">In the **Maximum buffer memory size** box, specify the maximum amount of buffer memory to use.</span></span> <span data-ttu-id="e1421-182">이 값에 도달하면 기존 이벤트가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-182">The existing events are dropped when this value is reached.</span></span>  
  
    3.  <span data-ttu-id="e1421-183">버퍼에 각 유형의 특정 이벤트 수를 보관하려면 **버퍼가 꽉 차면 유형당 지정한 개수의 이벤트 유지** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-183">If you want to keep a specific number of events of each type in the buffer, select the **Keep a specified number of events (per type) when the buffer is full** check box.</span></span>  
  
    4.  <span data-ttu-id="e1421-184">**유형당 유지할 이벤트 수** 상자에서 보관할 유형당 이벤트 수를 입력하거나 위쪽 및 아래쪽 화살표를 사용하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-184">In the **Number of events to keep (per type)** box, enter or select the number of events (per type) that you want to keep by using the up and down arrows.</span></span>  
  
##  <a name="summary"></a><a name="BKMK_Summary"></a> <span data-ttu-id="e1421-185">요약</span><span class="sxs-lookup"><span data-stu-id="e1421-185">Summary</span></span>  
 <span data-ttu-id="e1421-186">**요약** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-186">On the **Summary** page, do the following:</span></span>  
  
1.  <span data-ttu-id="e1421-187">선택한 내용이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-187">Make sure that your selections are correct.</span></span> <span data-ttu-id="e1421-188">이벤트 세션 노드를 확장하여 선택한 내용이 모두 이벤트 세션에 포함될지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-188">Expand the event session nodes to verify that all of your selections will be included in the event session.</span></span>  
  
2.  <span data-ttu-id="e1421-189">**스크립트** 를 클릭하여 세션 만들기 스크립트를 새 쿼리 편집기 창으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-189">Click **Script** to export the session creation script to a new Query Editor window.</span></span>  
  
3.  <span data-ttu-id="e1421-190">**마침** 을 클릭하여 이벤트 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-190">Click **Finish** to create the event session.</span></span>  
  
##  <a name="create-event-session"></a><a name="BKMK_CreateEventSession"></a><span data-ttu-id="e1421-191">이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="e1421-191">Create Event Session</span></span>  
 <span data-ttu-id="e1421-192">**이벤트 세션 만들기** 페이지에서 이벤트 세션을 성공적으로 만든 후 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-192">On the **Create Event Session** page, after your event session has been successfully created, do the following:</span></span>  
  
1.  <span data-ttu-id="e1421-193">마법사를 닫은 후 세션을 시작하려면 **세션을 만든 후 즉시 이벤트 세션 시작** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-193">Click **Start the event session immediately after session creation** to start the session after you close the wizard.</span></span> <span data-ttu-id="e1421-194">세션을 만든 후 즉시 이벤트 세션을 시작해야 라이브 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-194">You must start the event session immediately after you create the session to be able to watch live data.</span></span>  
  
2.  <span data-ttu-id="e1421-195">이벤트 세션의 라이브 데이트를 확인하려면 **캡처 시 화면에서 라이브 데이터 감시** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-195">Click **Watch live data on screen as it is captured** to view live data for your event session.</span></span> <span data-ttu-id="e1421-196">라이브 데이터는 세션이 만들어진 후 즉시 추적을 표시하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e1421-196">The live data will start displaying tracing immediately after the session is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1421-197">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1421-197">See Also</span></span>  
 [<span data-ttu-id="e1421-198">새 세션 대화 상자를 사용하여 확장 이벤트 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="e1421-198">Create an Extended Events Session Using the New Session Dialog</span></span>](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)  
  
  
