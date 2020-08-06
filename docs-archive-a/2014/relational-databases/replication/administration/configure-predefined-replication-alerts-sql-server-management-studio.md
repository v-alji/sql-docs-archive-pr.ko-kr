---
title: 미리 정의된 복제 경고 구성(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server replication]
- predefined replication alerts [SQL Server replication]
ms.assetid: c0414147-7ffe-4f9a-908c-71c1b5201584
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa78a08757cc7bbe809c5e3a1808c9632b76763a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741896"
---
# <a name="configure-predefined-replication-alerts-sql-server-management-studio"></a><span data-ttu-id="1bac0-102">미리 정의된 복제 경고 구성(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1bac0-102">Configure Predefined Replication Alerts (SQL Server Management Studio)</span></span>
  <span data-ttu-id="1bac0-103">복제는 다음과 같은 미리 정의된 경고를 제공합니다. 이러한 경고는 복제 이벤트에 응답하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-103">Replication offers the following predefined alerts, which can be configured to respond to replication events:</span></span>  
  
-   <span data-ttu-id="1bac0-104">**복제: 에이전트 성공**</span><span class="sxs-lookup"><span data-stu-id="1bac0-104">**Replication: agent success**</span></span>    
-   <span data-ttu-id="1bac0-105">**복제: 에이전트 실패**</span><span class="sxs-lookup"><span data-stu-id="1bac0-105">**Replication: agent failure**</span></span>    
-   <span data-ttu-id="1bac0-106">**복제: 에이전트 다시 시도**</span><span class="sxs-lookup"><span data-stu-id="1bac0-106">**Replication: agent retry**</span></span>    
-   <span data-ttu-id="1bac0-107">**복제: 만료된 구독 삭제**</span><span class="sxs-lookup"><span data-stu-id="1bac0-107">**Replication: expired subscription dropped**</span></span>    
-   <span data-ttu-id="1bac0-108">**복제: 유효성 검사 실패 후 구독이 다시 초기화되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="1bac0-108">**Replication: Subscription reinitialized after validation failure**</span></span>    
-   <span data-ttu-id="1bac0-109">**복제: 구독자가 데이터 유효성 검사에 실패했습니다.**</span><span class="sxs-lookup"><span data-stu-id="1bac0-109">**Replication: Subscriber has failed data validation**</span></span>    
-   <span data-ttu-id="1bac0-110">**복제: 구독자가 데이터 유효성 검사를 통과했습니다.**</span><span class="sxs-lookup"><span data-stu-id="1bac0-110">**Replication: Subscriber has passed data validation**</span></span>    
-   <span data-ttu-id="1bac0-111">**복제: 에이전트 사용자 지정 종료**</span><span class="sxs-lookup"><span data-stu-id="1bac0-111">**Replication: agent custom shutdown**</span></span>  
  
 <span data-ttu-id="1bac0-112">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]의 **경고** 폴더 또는 복제 모니터의 **경고** 탭에서 위와 같은 경고를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-112">Configure these alerts from the **Alerts** folder in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or the **Warnings** tab in Replication Monitor.</span></span> <span data-ttu-id="1bac0-113">이 탭에 액세스 하는 방법에 대 한 자세한 내용은 [정보 보기 및 복제 모니터를 사용 하 여 작업 수행](../monitor/view-information-and-perform-tasks-replication-monitor.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1bac0-113">For more information about accessing this tab, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="1bac0-114">복제 모니터는 이러한 경고 외에도 상태 및 성능과 관련된 일련의 경고를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-114">In addition to these alerts, Replication Monitor provides a set of warnings and alerts related to status and performance.</span></span> <span data-ttu-id="1bac0-115">자세한 내용은 [복제 모니터 경고 인프라에서 임계값 및 경고 설정](../monitor/set-thresholds-and-warnings-in-replication-monitor.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1bac0-115">For more information, see [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md) alerts infrastructure.</span></span> <span data-ttu-id="1bac0-116">자세한 내용은 [사용자 정의 이벤트 만들기](../../../ssms/agent/create-a-user-defined-event.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1bac0-116">For more information, see [Create a User-Defined Event](../../../ssms/agent/create-a-user-defined-event.md).</span></span>  
  
### <a name="to-configure-a-predefined-replication-alert-in-management-studio"></a><span data-ttu-id="1bac0-117">Management Studio에서 미리 정의된 복제 경고를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="1bac0-117">To configure a predefined replication alert in Management Studio</span></span>  
  
1.  <span data-ttu-id="1bac0-118">[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]에서 배포자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-118">Connect to the Distributor in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>    
2.  <span data-ttu-id="1bac0-119">**SQL Server 에이전트** 폴더를 확장한 다음 **경고** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-119">Expand the **SQL Server Agent** folder, and then expand the **Alerts** folder.</span></span>    
3.  <span data-ttu-id="1bac0-120">복제 경고를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-120">Right-click a replication alert, and then click **Properties**.</span></span>    
4.  <span data-ttu-id="1bac0-121">**\<AlertName> 경고 속성** 대화 상자에서 다음과 같은 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-121">Set options in the **\<AlertName> alert properties** dialog box:</span></span>    
    -   <span data-ttu-id="1bac0-122">**일반** 페이지에서 **사용**을 클릭하고 경고를 적용할 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-122">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>    
    -   <span data-ttu-id="1bac0-123">**응답** 페이지에서 전자 메일의 발송 여부 및/또는 작업의 실행 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-123">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
         <span data-ttu-id="1bac0-124">**복제: 구독자가 데이터 유효성 검사에 실패했습니다**라는 경고가 발생하면 복제가 이 경고에 대해 제공하는 응답 작업을 지정할 수 있습니다. **작업 실행**을 선택한 다음, 찾아보기 단추( **...** )를 클릭합니다. **작업 찾기** 대화 상자에서 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-124">If the alert is **Replication: Subscriber has failed data validation**, you can specify the response job that replication provides for this alert: Select **Execute job**, and then click the browse button (**...**). In the **Locate Job** dialog box, click **Browse**.</span></span> <span data-ttu-id="1bac0-125">**개체 찾아보기** 대화 상자에서 **데이터 유효성 검사에 실패한 구독 다시 초기화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-125">In the **Browse for Objects** dialog box, select **Reinitialize subscriptions having data validation failures**.</span></span> <span data-ttu-id="1bac0-126">열린 두 대화 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-126">Click **OK** in both open dialog boxes.</span></span> <span data-ttu-id="1bac0-127">실행 시 이 작업은 구독을 다시 초기화하는 저장 프로시저에 대한 RPC(원격 프로시저 호출)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-127">When the job executes, it uses a remote procedure call (RPC) to a stored procedure that reinitializes the subscription.</span></span> <span data-ttu-id="1bac0-128">게시자가 원격 배포자를 사용하는 경우 배포자에서 게시자로의 RPC를 설정할 수 있도록 게시자에서 원격 서버 로그인을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-128">If the Publisher uses a remote Distributor, you must define a remote server login at the Publisher, so that the RPC from the Distributor to the Publisher can be made.</span></span>   
    -   <span data-ttu-id="1bac0-129">**옵션** 페이지에서 응답 텍스트를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-129">On the **Options** page, customize the text of the response.</span></span>    
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-configure-an-alert-for-a-threshold-in-replication-monitor"></a><span data-ttu-id="1bac0-130">복제 모니터에서 임계값에 대한 경고를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="1bac0-130">To configure an alert for a threshold in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="1bac0-131">**경고** 탭에서 **경고 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-131">On the **Warnings** tab click **Configure Alerts**.</span></span>    
2.  <span data-ttu-id="1bac0-132">**복제 경고 구성** 대화 상자에서 경고를 선택한 다음 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-132">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>    
3.  <span data-ttu-id="1bac0-133">**\<AlertName> 경고 속성** 대화 상자에서 다음과 같은 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-133">Set options in the **\<AlertName> alert properties** dialog box:</span></span>    
    -   <span data-ttu-id="1bac0-134">**일반** 페이지에서 **사용**을 클릭하고 경고를 적용할 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-134">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>    
    -   <span data-ttu-id="1bac0-135">**응답** 페이지에서 전자 메일의 발송 여부 및/또는 작업의 실행 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-135">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>    
         <span data-ttu-id="1bac0-136">**복제: 구독자가 데이터 유효성 검사에 실패했습니다**라는 경고가 발생하면 복제가 이 경고에 대해 제공하는 응답 작업을 지정할 수 있습니다. **작업 실행**을 선택한 다음, 찾아보기 단추( **...** )를 클릭합니다. **작업 찾기** 대화 상자에서 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-136">If the alert is **Replication: Subscriber has failed data validation**, you can specify the response job that replication provides for this alert: Select **Execute job**, and then click the browse button (**...**). In the **Locate Job** dialog box, click **Browse**.</span></span> <span data-ttu-id="1bac0-137">**개체 찾아보기** 대화 상자에서 **데이터 유효성 검사에 실패한 구독 다시 초기화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-137">In the **Browse for Objects** dialog box, select **Reinitialize subscriptions having data validation failures**.</span></span> <span data-ttu-id="1bac0-138">열린 두 대화 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-138">Click **OK** in both open dialog boxes.</span></span> <span data-ttu-id="1bac0-139">실행 시 이 작업은 구독을 다시 초기화하는 저장 프로시저에 대한 RPC(원격 프로시저 호출)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-139">When the job executes, it uses a remote procedure call (RPC) to a stored procedure that reinitializes the subscription.</span></span> <span data-ttu-id="1bac0-140">게시자가 원격 배포자를 사용하는 경우 배포자에서 게시자로의 RPC를 설정할 수 있도록 게시자에서 원격 서버 로그인을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-140">If the Publisher uses a remote Distributor, you must define a remote server login at the Publisher, so that the RPC from the Distributor to the Publisher can be made.</span></span>   
    -   <span data-ttu-id="1bac0-141">**옵션** 페이지에서 응답 텍스트를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-141">On the **Options** page, customize the text of the response.</span></span>    
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]    
5.  <span data-ttu-id="1bac0-142">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1bac0-142">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bac0-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1bac0-143">See Also</span></span>  
 [<span data-ttu-id="1bac0-144">복제 에이전트 이벤트에 대한 경고 사용</span><span class="sxs-lookup"><span data-stu-id="1bac0-144">Use Alerts for Replication Agent Events</span></span>](../agents/use-alerts-for-replication-agent-events.md)  
  
  
