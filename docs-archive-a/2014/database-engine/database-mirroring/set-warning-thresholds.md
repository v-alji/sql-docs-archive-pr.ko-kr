---
title: 경고 임계값 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.setwarningthreshold.f1
ms.assetid: 17f93147-e7d9-4092-b4c2-c11b38051171
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2d5fd9c0213d74f3a6b5d0d4cb2f11d3531d336d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733036"
---
# <a name="set-warning-thresholds"></a><span data-ttu-id="f1876-102">경고 임계값 설정</span><span class="sxs-lookup"><span data-stu-id="f1876-102">Set Warning Thresholds</span></span>
  <span data-ttu-id="f1876-103">이 대화 상자를 사용하여 **데이터베이스 미러링 모니터** 대화 상자의 탐색 트리에서 선택한 데이터베이스에 대한 하나 이상의 경고 임계값을 설정 및 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-103">Use this dialog box to enable and configure one or more warning thresholds for the database selected in the navigation tree of the **Database Mirroring Monitor** dialog box.</span></span>  
  
 <span data-ttu-id="f1876-104">이 대화 상자는 두 서버 인스턴스에 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-104">The dialog box tries to connect to both server instances.</span></span> <span data-ttu-id="f1876-105">이러한 연결은 비동기적으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-105">These connections are established asynchronously.</span></span> <span data-ttu-id="f1876-106">이 대화 상자에는 각 파트너의 연결 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-106">The dialog shows the connection status of each partner.</span></span> <span data-ttu-id="f1876-107">파트너가 연결되지 않은 경우 **연결**을 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-107">If the partner is not connected, you can click **Connect**.</span></span>  
  
 <span data-ttu-id="f1876-108">**SQL Server Management Studio를 사용하여 데이터베이스 미러링을 모니터링하려면**</span><span class="sxs-lookup"><span data-stu-id="f1876-108">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="f1876-109">데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f1876-109">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="f1876-110">옵션</span><span class="sxs-lookup"><span data-stu-id="f1876-110">Options</span></span>  
 <span data-ttu-id="f1876-111">*서버 인스턴스 및 서버 인스턴스의 연결 상태*</span><span class="sxs-lookup"><span data-stu-id="f1876-111">*Server instance and its connection status*</span></span>  
 <span data-ttu-id="f1876-112">시스템 INSTANCE_NAME 형식으로 된 파트너 서버 인스턴스의 이름 _SYSTEM_ **\\** _INSTANCE_NAME_입니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-112">Name of a partner server instance in the form _SYSTEM_**\\**_INSTANCE_NAME_.</span></span> <span data-ttu-id="f1876-113">기본 서버 인스턴스의 경우 시스템 이름만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-113">For a default server instance, only the system name is displayed.</span></span>  
  
 <span data-ttu-id="f1876-114">또한 이 필드는 모니터가 이 서버 인스턴스에 현재 연결되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-114">This field also indicates whether the monitor is currently connected to this server instance.</span></span> <span data-ttu-id="f1876-115">가능한 연결 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-115">The possible connection statuses are:</span></span>  
  
-   <span data-ttu-id="f1876-116">*server_instance_name\*\*\*에 연결되지 않음*\*</span><span class="sxs-lookup"><span data-stu-id="f1876-116">**Not connected to**  *server_instance_name*</span></span>  
  
-   <span data-ttu-id="f1876-117">*server_instance_name\*\*\*에 연결하는 중*\*</span><span class="sxs-lookup"><span data-stu-id="f1876-117">**Trying to connect to**  *server_instance_name*</span></span>  
  
-   <span data-ttu-id="f1876-118">*server_instance_name\*\*\*에 연결됨*\*</span><span class="sxs-lookup"><span data-stu-id="f1876-118">**Connected to**  *server_instance_name*</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f1876-119">**sysadmin** 고정 서버 역할의 멤버가 아닌 경우 이 상태는 *server_instance_name\*\*\*에 연결됨*\* **(제한된 사용 권한)** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-119">If you do are not a member of the **sysadmin** fixed server role, this status is **Connected to** *server_instance_name* **(Limited permissions)**.</span></span>  
  
 <span data-ttu-id="f1876-120">각 파트너 서버 인스턴스의 이름이 별도의 *서버 인스턴스 및 서버 인스턴스의 연결 상태* 필드에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-120">The name of each of the partner server instances is displayed in a separate *Server instance and its connection status* field.</span></span> <span data-ttu-id="f1876-121">모니터 실행이 시작되면 맨 위 필드에 주 서버가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-121">The top field lists the principal server when the monitor started running.</span></span>  
  
 <span data-ttu-id="f1876-122">**연결**/**취소**</span><span class="sxs-lookup"><span data-stu-id="f1876-122">**Connect**/**Cancel**</span></span>  
 <span data-ttu-id="f1876-123">**연결**/**취소** 단추는 각 *서버 인스턴스 및 서버 인스턴스의 연결 상태* 필드와 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-123">A **Connect**/**Cancel** button is associated with each *Server instance and its connection status* fields.</span></span> <span data-ttu-id="f1876-124">단추의 상태는 연결 상태에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-124">The state of the button depends on the connection status:</span></span>  
  
-   <span data-ttu-id="f1876-125">서버 인스턴스에 대한 연결이 없을 경우 단추 텍스트는 **연결**입니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-125">If there is no connection to the server instance, the button text is **Connect**.</span></span> <span data-ttu-id="f1876-126">서버 인스턴스에 연결하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-126">Click to connect to the server instance.</span></span>  
  
-   <span data-ttu-id="f1876-127">연결 시도가 진행 중이면 단추 텍스트는 **취소**입니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-127">When a connection attempt is in progress, the button text is **Cancel**.</span></span> <span data-ttu-id="f1876-128">연결 시도를 취소하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-128">Click to cancel the connection attempt.</span></span>  
  
-   <span data-ttu-id="f1876-129">서버가 연결된 경우 단추 텍스트는 **연결됨**이고 단추는 흐리게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-129">If the server is connected, the button text is **Connected**, and the button is dimmed.</span></span>  
  
 <span data-ttu-id="f1876-130">**임계값**</span><span class="sxs-lookup"><span data-stu-id="f1876-130">**Thresholds**</span></span>  
 <span data-ttu-id="f1876-131">**임계값** 표에는 두 서버 인스턴스에 대한 경고 설정이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-131">The **Thresholds** grid displays the warnings settings for the two server instances.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1876-132">서버 인스턴스가 연결되지 않은 경우 해당 열에는 빈 셀과 회색 배경이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-132">If a server instance is not connected, its columns are displayed with empty cells and a gray background.</span></span> <span data-ttu-id="f1876-133">연결이 열리면 해당 인스턴스의 내용이 표에 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-133">When the connection opens, the grid automatically displays the content from the instance.</span></span>  
  
 <span data-ttu-id="f1876-134">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-134">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="f1876-135">**경고**</span><span class="sxs-lookup"><span data-stu-id="f1876-135">**Warnings**</span></span>  
 <span data-ttu-id="f1876-136">지원되는 경고를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-136">Lists the supported warnings:</span></span>  
  
|<span data-ttu-id="f1876-137">Warning</span><span class="sxs-lookup"><span data-stu-id="f1876-137">Warning</span></span>|<span data-ttu-id="f1876-138">Description</span><span class="sxs-lookup"><span data-stu-id="f1876-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1876-139">**보내지 않은 로그가 임계값을 초과하는 경우 경고**</span><span class="sxs-lookup"><span data-stu-id="f1876-139">**Warn if the unsent log exceeds the threshold**</span></span>|<span data-ttu-id="f1876-140">임계값은 주 서버의 Send Queue에 있는 보내지 않은 로그의 크기(KB)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-140">The threshold indicates the number of kilobytes (KB) of the unsent log in the send queue on the principal.</span></span>|  
|<span data-ttu-id="f1876-141">**복원되지 않은 로그가 임계값을 초과하는 경우 경고**</span><span class="sxs-lookup"><span data-stu-id="f1876-141">**Warn if the unrestored log exceeds the threshold**</span></span>|<span data-ttu-id="f1876-142">임계값은 미러 서버 인스턴스에 있는 Redo Queue의 크기(KB)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-142">The threshold indicates the number of KB of the redo queue on the mirror server instance.</span></span>|  
|<span data-ttu-id="f1876-143">**보내지 않은 가장 오래된 트랜잭션 기간이 임계값을 초과하는 경우 경고**</span><span class="sxs-lookup"><span data-stu-id="f1876-143">**Warn if the age of the oldest unsent transaction exceeds the threshold**</span></span>|<span data-ttu-id="f1876-144">임계값은 Send Queue에서 미러 서버 인스턴스로 아직 보내지 않은 트랜잭션의 시간(분)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-144">The threshold indicates the number of minutes of transactions that have not yet been sent from the send queue to the mirror server instance.</span></span> <span data-ttu-id="f1876-145">이 값은 시간을 기준으로 발생 가능한 데이터 손실을 측정하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-145">This value helps measure the potential for data loss in terms of time.</span></span>|  
|<span data-ttu-id="f1876-146">**미러 커밋 오버헤드가 임계값을 초과하는 경우 경고**</span><span class="sxs-lookup"><span data-stu-id="f1876-146">**Warn if the mirror commit overhead exceeds the threshold**</span></span>|<span data-ttu-id="f1876-147">임계값은 트랜잭션당 지연 시간(밀리초)을 나타냅니다(보호 우선 모드에만 관련됨).</span><span class="sxs-lookup"><span data-stu-id="f1876-147">The threshold indicates the number of milliseconds of delay per transaction (relevant only in high-safety mode).</span></span> <span data-ttu-id="f1876-148">이 지연 시간은 주 서버 인스턴스에서 미리 서버 인스턴스가 트랜잭션 로그 레코드를 Redo Queue에 쓸 때까지 대기하는 동안 발생한 오버헤드 양입니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-148">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span>|  
  
 <span data-ttu-id="f1876-149">**'** *\<server instance>* **'에서 활성화됨**</span><span class="sxs-lookup"><span data-stu-id="f1876-149">**Enabled at '** *\<server instance>* **'**</span></span>  
 <span data-ttu-id="f1876-150">빈 확인란은 서버 인스턴스에서 경고가 현재 비활성화되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-150">A blank check box indicates that the warning is currently disabled on the server instance.</span></span> <span data-ttu-id="f1876-151">경고를 활성화하려면 해당 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-151">To enable a warning, click its check box.</span></span>  
  
 <span data-ttu-id="f1876-152">**'** *\<server instance>* **'에서의 임계값**</span><span class="sxs-lookup"><span data-stu-id="f1876-152">**Threshold at '** *\<server instance>* **'**</span></span>  
 <span data-ttu-id="f1876-153">경고가 활성화된 경우 이 열의 왼쪽에서 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-153">When a warning is enabled, set the threshold on the left side of this column.</span></span> <span data-ttu-id="f1876-154">상태 테이블을 업데이트할 때 지정된 임계값에 도달한 경우 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-154">An event occurs if the specified threshold has been reached when the status table is updated.</span></span> <span data-ttu-id="f1876-155">값을 구성한 후 임계값을 비활성화하면 해당 값은 이 필드에 남아 있으며 경고를 다시 활성화할 경우 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-155">If you disable a threshold after configuring a value, your value remains in this field and will be used if you re-enable the warning.</span></span>  
  
 <span data-ttu-id="f1876-156">경고가 활성화되지 않은 경우 이 필드는 비활성 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-156">When a warning is not enabled, this field is inactive.</span></span>  
  
 <span data-ttu-id="f1876-157">**확인**</span><span class="sxs-lookup"><span data-stu-id="f1876-157">**OK**</span></span>  
 <span data-ttu-id="f1876-158">**확인** 을 클릭하면 이 대화 상자가 닫히고 경고 임계값의 현재 지정된 값이 **경고** 탭 페이지의 **임계값**표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-158">Clicking **OK** closes this dialog box and displays the currently specified values of warning thresholds in the **Thresholds** grid on the **Warnings**tabbed page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1876-159">설명</span><span class="sxs-lookup"><span data-stu-id="f1876-159">Remarks</span></span>  
 <span data-ttu-id="f1876-160">임계값은 한 번에 한 파트너에만 적용할 수 있지만 데이터베이스가 장애 조치될 경우 경고가 유지되도록 두 파트너 모두에 지정된 이벤트에 대한 임계값을 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-160">A threshold is only applicable at one partner at a time, but we recommend that you set a threshold for a given event on both partners to ensure that the warning persists if the database fails over.</span></span> <span data-ttu-id="f1876-161">각 파트너에 적합한 임계값은 각 파트너 시스템의 성능 기능에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-161">The appropriate threshold for each partner depends on the performance capabilities of that partner's system.</span></span>  
  
 <span data-ttu-id="f1876-162">상태 테이블을 업데이트할 때 해당 값이 임계값보다 크거나 같을 경우에만 성능의 이벤트 로그에 이벤트가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-162">An event is written to the event log for a performance only if its value is at or above its threshold when the status table is being updated.</span></span> <span data-ttu-id="f1876-163">상태 업데이트 사이에 최대값이 일시적으로 임계값에 도달할 경우 해당 값은 누락됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1876-163">If a peak value reaches the threshold momentarily between status updates that peak is missed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1876-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f1876-164">See Also</span></span>  
 <span data-ttu-id="f1876-165">[데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="f1876-165">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="f1876-166">[데이터베이스 미러링 모니터링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f1876-166">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="f1876-167">데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f1876-167">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
