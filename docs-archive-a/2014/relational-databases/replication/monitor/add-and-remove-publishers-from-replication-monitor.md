---
title: 복제 모니터에서 게시자 추가 및 제거 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, adding and removing Publishers
ms.assetid: fa36c4b4-bfa5-494e-92e3-07a02d7332c3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 16c2876b55541e347e4e638132f36ad33932abb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741840"
---
# <a name="add-and-remove-publishers-from-replication-monitor"></a><span data-ttu-id="0c05d-102">복제 모니터에서 게시자 추가 및 제거</span><span class="sxs-lookup"><span data-stu-id="0c05d-102">Add and Remove Publishers from Replication Monitor</span></span>
  <span data-ttu-id="0c05d-103">복제 모니터를 실행하는 서버가 게시자인 경우 자동으로 모니터에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-103">The server from which you launch Replication Monitor is automatically added to the monitor if it is a Publisher.</span></span> <span data-ttu-id="0c05d-104">**게시자 추가** 대화 상자를 통해 게시자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-104">Additional Publishers can be added through the **Add Publisher** dialog box.</span></span> <span data-ttu-id="0c05d-105">게시자를 추가하면 게시자는 모니터의 왼쪽 창에 있는 그룹에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-105">After adding a Publisher, it is displayed in a group in the left pane of the monitor.</span></span> <span data-ttu-id="0c05d-106">**내 게시자** 그룹이 기본적으로 포함되지만 새 그룹을 만들어 하나 이상의 복제 토폴로지를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-106">The **My Publishers** group is included by default, but you can create new groups to manage one or more replication topologies.</span></span> <span data-ttu-id="0c05d-107">복제 모니터를 시작하는 방법은 [복제 모니터 시작](start-the-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0c05d-107">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
### <a name="to-add-a-sql-server-publisher"></a><span data-ttu-id="0c05d-108">SQL Server 게시자를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="0c05d-108">To add a SQL Server Publisher</span></span>  
  
1.  <span data-ttu-id="0c05d-109">왼쪽 창에서 **복제 모니터** 노드 또는 게시자 그룹 노드를 마우스 오른쪽 단추로 클릭한 다음 **게시자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-109">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="0c05d-110">**게시자 추가** 대화 상자에서 **추가**를 클릭한 다음 **SQL Server 게시자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-110">In the **Add Publisher** dialog box, click **Add**, and then click **Add SQL Server Publisher**.</span></span>  
  
3.  <span data-ttu-id="0c05d-111">**서버에 연결** 대화 상자에서 게시자의 이름을 입력한 다음 인증 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-111">In the **Connect to Server** dialog box, enter the name of the Publisher, and then select the authentication type.</span></span> <span data-ttu-id="0c05d-112">**SQL Server 인증**을 선택한 경우 로그인 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-112">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="0c05d-113">지정한 자격 증명은 나중에 이 서버에 연결할 때 사용하기 위해 복제 모니터에 의해 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-113">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="0c05d-114">지정한 Windows 계정 또는 SQL Server 로그인은 **sysadmin** 고정 서버 역할의 멤버이거나 배포 데이터베이스에 있는 **replmonitor** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-114">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="0c05d-115">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-115">Click **Connect**.</span></span> <span data-ttu-id="0c05d-116">게시자가 원격 배포자를 사용할 경우 **서버에 연결** 대화 상자에 배포자로 연결하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-116">If the Publisher uses a remote Distributor, you will be prompted to connect to the Distributor in the **Connect to Server** dialog box.</span></span> <span data-ttu-id="0c05d-117">지정한 자격 증명은 나중에 이 서버에 연결할 때 사용하기 위해 복제 모니터에 의해 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-117">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="0c05d-118">지정한 Windows 계정 또는 SQL Server 로그인은 **sysadmin** 고정 서버 역할의 멤버이거나 배포 데이터베이스에 있는 **replmonitor** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-118">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
5.  <span data-ttu-id="0c05d-119">게시자 또는 배포자의 이름이 **다음 게시자의 모니터링 시작** 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-119">The name of the Publisher and Distributor are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span>  
  
6.  <span data-ttu-id="0c05d-120">게시자에 대해 새로 고침 및 연결 옵션을 지정하려면 표에서 게시자를 선택한 다음 필요에 맞게 옵션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-120">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="0c05d-121">새로 고침 옵션에 대한 자세한 내용은 [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0c05d-121">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="0c05d-122">복제 모니터에서 게시자가 표시되는 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-122">Select the group under which the Publisher should be displayed in Replication Monitor.</span></span> <span data-ttu-id="0c05d-123">새 그룹을 만들려면 **새 그룹**을 클릭한 다음 그룹 이름을 입력합니다. **이 게시자를 다음 그룹에 표시** 목록에서 해당 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-123">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-add-an-oracle-publisher"></a><span data-ttu-id="0c05d-124">Oracle 게시자를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="0c05d-124">To add an Oracle Publisher</span></span>  
  
1.  <span data-ttu-id="0c05d-125">왼쪽 창에서 **복제 모니터** 노드 또는 게시자 그룹 노드를 마우스 오른쪽 단추로 클릭한 다음 **게시자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-125">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="0c05d-126">**게시자 추가** 대화 상자에서 **추가**를 클릭한 다음 **Oracle 게시자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-126">In the **Add Publisher** dialog box, click **Add**, and then click **Add Oracle Publisher**.</span></span>  
  
3.  <span data-ttu-id="0c05d-127">**서버에 연결** 대화 상자에서 Oracle 게시자와 연결된 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자의 이름을 입력하고 인증 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-127">In the **Connect to Server** dialog box, enter the name of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor associated with the Oracle Publisher, and then select the authentication type.</span></span> <span data-ttu-id="0c05d-128">**SQL Server 인증**을 선택한 경우 로그인 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-128">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="0c05d-129">지정한 자격 증명은 나중에 이 서버에 연결할 때 사용하기 위해 복제 모니터에 의해 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-129">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="0c05d-130">지정한 Windows 계정 또는 SQL Server 로그인은 **sysadmin** 고정 서버 역할의 멤버이거나 배포 데이터베이스에 있는 **replmonitor** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-130">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="0c05d-131">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-131">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="0c05d-132">게시자 또는 배포자의 이름이 **다음 게시자의 모니터링 시작** 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-132">The name of the Publisher and Distributor are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span>  
  
6.  <span data-ttu-id="0c05d-133">게시자에 대해 새로 고침 및 연결 옵션을 지정하려면 표에서 게시자를 선택한 다음 필요에 맞게 옵션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-133">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="0c05d-134">새로 고침 옵션에 대한 자세한 내용은 [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0c05d-134">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="0c05d-135">복제 모니터에서 게시자가 표시되는 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-135">Select the group under which the Publisher should be displayed in Replication Monitor.</span></span> <span data-ttu-id="0c05d-136">새 그룹을 만들려면 **새 그룹**을 클릭한 다음 그룹 이름을 입력합니다. **이 게시자를 다음 그룹에 표시** 목록에서 해당 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-136">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-add-one-or-more-publishers-that-use-the-same-distributor"></a><span data-ttu-id="0c05d-137">같은 배포자를 사용하는 하나 이상의 게시자를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="0c05d-137">To add one or more Publishers that use the same Distributor</span></span>  
  
1.  <span data-ttu-id="0c05d-138">왼쪽 창에서 **복제 모니터** 노드 또는 게시자 그룹 노드를 마우스 오른쪽 단추로 클릭한 다음 **게시자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-138">Right-click the **Replication Monitor** node or a Publisher group node in the left pane, and then click **Add Publisher**.</span></span>  
  
2.  <span data-ttu-id="0c05d-139">**게시자 추가** 대화 상자에서 **추가**를 클릭한 다음 **배포자를 지정한 후 해당 게시자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-139">In the **Add Publisher** dialog box, click **Add**, and then click **Specify a Distributor and Add Its Publishers**.</span></span>  
  
3.  <span data-ttu-id="0c05d-140">**서버에 연결** 대화 상자에서 배포자의 이름을 입력한 다음 인증 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-140">In the **Connect to Server** dialog box, enter the name of the Distributor, and then select the authentication type.</span></span> <span data-ttu-id="0c05d-141">**SQL Server 인증**을 선택한 경우 로그인 및 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-141">If you select **SQL Server Authentication**, enter a login and password.</span></span> <span data-ttu-id="0c05d-142">지정한 자격 증명은 나중에 이 서버에 연결할 때 사용하기 위해 복제 모니터에 의해 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-142">The credentials you specify are saved by Replication Monitor to use when connecting to this server in the future.</span></span> <span data-ttu-id="0c05d-143">지정한 Windows 계정 또는 SQL Server 로그인은 **sysadmin** 고정 서버 역할의 멤버이거나 배포 데이터베이스에 있는 **replmonitor** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-143">The Windows account or SQL Server login specified must be a member of the **sysadmin** fixed server role or a member of the **replmonitor** fixed database role in the distribution database.</span></span>  
  
4.  <span data-ttu-id="0c05d-144">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-144">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="0c05d-145">배포자와 각 게시자의 이름이 **다음 게시자의 모니터링 시작** 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-145">The name of the Distributor and each Publisher are displayed in the **Start monitoring the following Publisher(s)** grid.</span></span> <span data-ttu-id="0c05d-146">게시자가 복제 모니터에 이미 추가된 경우에는 표에 게시자가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-146">If a Publisher has already been added to Replication Monitor, it does not appear in the grid.</span></span>  
  
6.  <span data-ttu-id="0c05d-147">게시자에 대해 새로 고침 및 연결 옵션을 지정하려면 표에서 게시자를 선택한 다음 필요에 맞게 옵션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-147">To specify refresh and connection options for the Publisher, select the Publisher in the grid, and modify options as necessary.</span></span> <span data-ttu-id="0c05d-148">새로 고침 옵션에 대한 자세한 내용은 [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0c05d-148">For more information about refresh options, see [Caching, Refresh, and Replication Monitor Performance](caching-refresh-and-replication-monitor-performance.md).</span></span>  
  
7.  <span data-ttu-id="0c05d-149">복제 모니터에서 게시자가 표시되는 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-149">Select the group under which Publishers should be displayed in Replication Monitor.</span></span> <span data-ttu-id="0c05d-150">새 그룹을 만들려면 **새 그룹**을 클릭한 다음 그룹 이름을 입력합니다. **이 게시자를 다음 그룹에 표시** 목록에서 해당 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-150">To create a new group, click **New Group**, and then enter a group name; select the group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-modify-settings-for-the-publisher-and-publisher-groups"></a><span data-ttu-id="0c05d-151">게시자 및 게시자 그룹에 대한 설정을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="0c05d-151">To modify settings for the Publisher and Publisher Groups</span></span>  
  
1.  <span data-ttu-id="0c05d-152">왼쪽 창에서 게시자를 마우스 오른쪽 단추로 클릭한 다음 **게시자 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-152">Right-click a Publisher in the left pane, and then click **Publisher Settings**.</span></span>  
  
2.  <span data-ttu-id="0c05d-153">**게시자 설정** 대화 상자에서 변경을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-153">Make any changes in the **Publisher Settings** dialog box:</span></span>  
  
    -   <span data-ttu-id="0c05d-154">복제 모니터가 서버에 연결할 때 사용하는 자격 증명을 변경하려면 **게시자 연결** 또는 **배포자 연결**을 클릭한 다음 **서버에 연결** 입력란에 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-154">To change the credentials that Replication Monitor uses to connect to a server, click **Publisher Connection** or **Distributor Connection**, and then enter credentials in the **Connect to Server** dialog box.</span></span>  
  
    -   <span data-ttu-id="0c05d-155">한 그룹에서 다른 그룹으로 게시자를 이동하려면 **다음 게시자의 모니터링 시작** 표에서 게시자를 선택한 다음 **이 게시자를 다음 그룹에 표시** 목록에서 새 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-155">To move a Publisher from one group to another, select the Publisher in the **Start monitoring the following Publisher(s)** grid, and then select the new group in the **Show this Publisher(s) in the following group** list.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-remove-a-publisher-from-replication-monitor"></a><span data-ttu-id="0c05d-156">복제 모니터에서 게시자를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="0c05d-156">To remove a Publisher from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="0c05d-157">왼쪽 창에서 게시자를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-157">Right-click a Publisher in the left pane.</span></span>  
  
2.  <span data-ttu-id="0c05d-158">**제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-158">Click **Remove**.</span></span>  
  
### <a name="to-add-a-publisher-group-to-replication-monitor"></a><span data-ttu-id="0c05d-159">게시자 그룹을 복제 모니터에 추가하려면</span><span class="sxs-lookup"><span data-stu-id="0c05d-159">To add a Publisher group to Replication Monitor</span></span>  
  
1.  <span data-ttu-id="0c05d-160">게시자 그룹은 게시자를 추가하거나 게시자에 대한 설정을 수정하는 경우에만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-160">Publisher groups can be created only when adding a Publisher or modifying settings for a Publisher.</span></span> <span data-ttu-id="0c05d-161">자세한 내용은 게시자 추가 방법을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0c05d-161">See the how to procedures on adding a Publisher for more information.</span></span>  
  
### <a name="to-remove-a-publisher-group-from-replication-monitor"></a><span data-ttu-id="0c05d-162">복제 모니터에서 게시자 그룹을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="0c05d-162">To remove a Publisher group from Replication Monitor</span></span>  
  
1.  <span data-ttu-id="0c05d-163">모든 게시자를 다른 그룹으로 이동하거나 복제 모니터에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-163">Move all Publishers to a different group or remove them from Replication Monitor.</span></span> <span data-ttu-id="0c05d-164">자세한 내용은 이 항목의 앞부분에 나오는 절차를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0c05d-164">For more information, see previous procedures in this topic.</span></span>  
  
2.  <span data-ttu-id="0c05d-165">게시자 그룹을 마우스 오른쪽 단추로 클릭한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c05d-165">Right-click the Publisher group, and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c05d-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0c05d-166">See Also</span></span>  
 <span data-ttu-id="0c05d-167">[배포 구성](../configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="0c05d-167">[Configure Distribution](../configure-distribution.md) </span></span>  
 [<span data-ttu-id="0c05d-168">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="0c05d-168">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
