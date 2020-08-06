---
title: 오프라인 로그 파일 보기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, viewing offline logs
- offline log files
ms.assetid: 9223e474-f224-4907-a4f2-081e11db58f5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2afc1992b54c78f69bfae1fc152b41c20bcd4ea1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653363"
---
# <a name="view-offline-log-files"></a><span data-ttu-id="282ea-102">오프라인 로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="282ea-102">View Offline Log Files</span></span>
  <span data-ttu-id="282ea-103">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]부터는 대상 인스턴스가 오프라인이거나 시작할 수 없는 경우 로컬 또는 원격 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-103">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from a local or remote instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when the target instance is offline or cannot start.</span></span>  
  
 <span data-ttu-id="282ea-104">등록된 서버에서 오프라인 로그 파일에 액세스하거나 WMI 및 WQL(WMI Query Language) 쿼리를 통해 프로그래밍 방식으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-104">You can access the offline log files from Registered Servers, or programmatically through WMI and WQL (WMI Query Language) queries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="282ea-105">이 방법을 사용하여 온라인 상태인 인스턴스에 연결할 수도 있지만 몇 가지 이유로 인해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결을 통해서는 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-105">You can also use these methods to connect to an instance that is online, but for some reason, you cannot connect through a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="282ea-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="282ea-106">Before you Begin</span></span>  
 <span data-ttu-id="282ea-107">오프라인 로그 파일에 연결하려면 오프라인 로그 파일을 보는 데 사용하는 컴퓨터와 보려는 로그 파일이 있는 컴퓨터에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-107">To connect to offline log files, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be installed on the computer that you are using to view the offline log files, and on the computer where the log files that you want to view are located.</span></span> <span data-ttu-id="282ea-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 두 컴퓨터에 설치된 경우 각 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스 및 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 실행하는 인스턴스의 오프라인 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-108">If an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on both computers, you can view offline files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and for instances that are running earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on either computer.</span></span>  
  
 <span data-ttu-id="282ea-109">등록된 서버를 사용하는 경우 연결할 인스턴스는 **로컬 서버 그룹** 또는 **중앙 관리 서버**에 등록되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-109">If you are using Registered Servers, the instance that you want to connect to must be registered under **Local Server Groups** or under **Central Management Servers**.</span></span> <span data-ttu-id="282ea-110">인스턴스는 자체적으로 등록될 수도 있고 서버 그룹의 멤버로 등록될 수도 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 등록된 서버에 추가하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="282ea-110">(The instance can be registered on its own or be a member of a server group.) For more information about how to add an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to Registered Servers, see the following topics:</span></span>  
  
-   [<span data-ttu-id="282ea-111">서버 그룹 만들기 또는 편집&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="282ea-111">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="282ea-112">연결된 서버 등록&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="282ea-112">Register a Connected Server &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="282ea-113">중앙 관리 서버 및 서버 그룹 만들기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="282ea-113">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
 <span data-ttu-id="282ea-114">WMI 및 WQL 쿼리를 통해 프로그래밍 방식으로 오프라인 로그 파일을 보는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="282ea-114">For more information about how to view offline log files programmatically through WMI and WQL queries, see the following topics:</span></span>  
  
-   <span data-ttu-id="282ea-115">[SqlErrorLogEvent 클래스](../wmi-provider-configuration-classes/sqlerrorlogevent-class.md) (이 항목에서는 지정된 로그 파일에서 로깅된 이벤트의 값을 검색하는 방법을 보여 줍니다.)</span><span class="sxs-lookup"><span data-stu-id="282ea-115">[SqlErrorLogEvent Class](../wmi-provider-configuration-classes/sqlerrorlogevent-class.md) (This topic shows how to retrieve values for logged events in a specified log file.)</span></span>  
  
-   <span data-ttu-id="282ea-116">[SqlErrorLogFile 클래스](../wmi-provider-configuration-classes/sqlerrorlogfile-class.md) (이 항목에서는 지정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로그 파일에 대한 정보를 검색하는 방법을 보여 줍니다.)</span><span class="sxs-lookup"><span data-stu-id="282ea-116">[SqlErrorLogFile Class](../wmi-provider-configuration-classes/sqlerrorlogfile-class.md) (This topic shows how to retrieve information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files on a specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="282ea-117">권한</span><span class="sxs-lookup"><span data-stu-id="282ea-117">Permissions</span></span>  
 <span data-ttu-id="282ea-118">오프라인 로그 파일에 연결하려면 로컬 컴퓨터와 원격 컴퓨터 모두에서 다음과 같은 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-118">To connect to an offline log file, you must have the following permissions on both the local and remote computers:</span></span>  
  
-   <span data-ttu-id="282ea-119">**Root\Microsoft\SqlServer\ComputerManagement12** WMI 네임스페이스에 대한 읽기 권한.</span><span class="sxs-lookup"><span data-stu-id="282ea-119">Read access to the **Root\Microsoft\SqlServer\ComputerManagement12** WMI namespace.</span></span> <span data-ttu-id="282ea-120">기본적으로 모든 사용자는 계정 사용 권한으로 읽기 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-120">By default, everyone has read access through the Enable Account permission.</span></span> <span data-ttu-id="282ea-121">자세한 내용은 이 섹션 뒷부분의 "WMI 사용 권한을 확인하려면" 절차를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="282ea-121">For more information, see the "To verify WMI permissions" procedure later in this section.</span></span>  
  
-   <span data-ttu-id="282ea-122">오류 로그 파일을 포함하는 폴더에 대한 읽기 권한.</span><span class="sxs-lookup"><span data-stu-id="282ea-122">Read permission to the folder that contains the error log files.</span></span> <span data-ttu-id="282ea-123">기본적으로 오류 로그 파일은 다음 경로에 있습니다. 여기서 \<*Drive>\*는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 설치한 드라이브를 나타내고 \<*InstanceName*>은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-123">By default the error log files are located in the following path (where \<*Drive>\* represents the drive where you installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and \<*InstanceName*> is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):</span></span>  
  
     <span data-ttu-id="282ea-124">**\<Drive>: Files\Microsoft SQL Server\MSSQL12. \<InstanceName> \MSSQL\Log**</span><span class="sxs-lookup"><span data-stu-id="282ea-124">**\<Drive>:\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\Log**</span></span>  
  
 <span data-ttu-id="282ea-125">WMI 네임스페이스 보안 설정을 확인하려면 WMI 컨트롤 스냅인을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-125">To verify WMI namespace security settings, you can use the WMI Control snap-in.</span></span>  
  
#### <a name="to-verify-wmi-permissions"></a><span data-ttu-id="282ea-126">WMI 사용 권한을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="282ea-126">To verify WMI permissions</span></span>  
  
1.  <span data-ttu-id="282ea-127">WMI 컨트롤 스냅인을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-127">Open the WMI Control snap-in.</span></span> <span data-ttu-id="282ea-128">WMI 컨트롤 스냅인을 열려면 운영 체제에 따라 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-128">To do this, do either of the following, depending on the operating system:</span></span>  
  
    -   <span data-ttu-id="282ea-129">**시작**을 클릭하고 **검색 시작** 상자에 `wmimgmt.msc`를 입력한 다음 ENTER 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-129">Click **Start**, type `wmimgmt.msc` in the **Start Search** box, and then press ENTER.</span></span>  
  
    -   <span data-ttu-id="282ea-130">**시작**, **실행**을 차례로 클릭 하 `wmimgmt.msc` 고를 입력 한 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-130">Click **Start**, click **Run**, type `wmimgmt.msc`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="282ea-131">기본적으로 WMI 컨트롤 스냅인은 로컬 컴퓨터를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-131">By default, the WMI Control snap-in manages the local computer.</span></span>  
  
     <span data-ttu-id="282ea-132">원격 컴퓨터에 연결하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-132">If you want to connect to a remote computer, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="282ea-133">**WMI 컨트롤(로컬)** 을 마우스 오른쪽 단추로 클릭한 다음 **다른 컴퓨터에 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-133">Right-click **WMI Control (Local)**, and then click **Connect to another computer**.</span></span>  
  
    2.  <span data-ttu-id="282ea-134">**관리되는 컴퓨터 변경** 대화 상자에서 **다른 컴퓨터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-134">In the **Change managed computer** dialog box, click **Another computer**.</span></span>  
  
    3.  <span data-ttu-id="282ea-135">원격 컴퓨터 이름을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-135">Enter the remote computer name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="282ea-136">**Wmi 컨트롤 (로컬)** 또는 **Wmi 컨트롤 (***RemoteComputerName***)** 을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-136">Right-click **WMI Control (Local)** or **WMI Control (***RemoteComputerName***)**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="282ea-137">**WMI 컨트롤 속성** 대화 상자에서 **보안** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-137">In the **WMI Control Properties** dialog box, click the **Security** tab.</span></span>  
  
5.  <span data-ttu-id="282ea-138">네임스페이스 트리에서 다음 네임스페이스를 찾아서 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-138">In the namespace tree, locate and then click the following namespace:</span></span>  
  
     <span data-ttu-id="282ea-139">**Root\Microsoft\SqlServer\ComputerManagement10**</span><span class="sxs-lookup"><span data-stu-id="282ea-139">**Root\Microsoft\SqlServer\ComputerManagement10**</span></span>  
  
6.  <span data-ttu-id="282ea-140">**보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-140">Click **Security**.</span></span>  
  
7.  <span data-ttu-id="282ea-141">사용할 계정에 **계정 사용** 사용 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-141">Make sure that the account that will be used has the **Enable Account** permission.</span></span> <span data-ttu-id="282ea-142">이 사용 권한이 있으면 WMI 개체에 대한 읽기 액세스가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-142">This permission allows Read access to WMI objects.</span></span>  
  
### <a name="view-log-files"></a><span data-ttu-id="282ea-143">로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="282ea-143">View Log Files</span></span>  
 <span data-ttu-id="282ea-144">다음 절차에서는 등록된 서버를 통해 오프라인 로그 파일을 보는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-144">The following procedure shows how to view offline log files through Registered Servers.</span></span> <span data-ttu-id="282ea-145">이 절차에서는 다음과 같은 사항을 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-145">The procedure assumes the following:</span></span>  
  
 <span data-ttu-id="282ea-146">연결하려는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 이미 등록된 서버에 등록되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-146">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to connect to is already registered in Registered Servers.</span></span>  
  
##### <a name="to-view-log-files-for-instances-that-are-offline"></a><span data-ttu-id="282ea-147">오프라인 인스턴스의 로그 파일을 보려면</span><span class="sxs-lookup"><span data-stu-id="282ea-147">To view log files for instances that are offline</span></span>  
  
1.  <span data-ttu-id="282ea-148">로컬 인스턴스의 오프라인 로그 파일을 보려면 승격된 권한으로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-148">If you want to view offline log files on a local instance, make sure that you start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] with elevated permissions.</span></span> <span data-ttu-id="282ea-149">이렇게 하려면 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 시작할 때 **SQL Server Management Studio**를 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-149">To do this, when you start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click **SQL Server Management Studio**, and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="282ea-150">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **보기** 메뉴에서 **등록된 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-150">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
3.  <span data-ttu-id="282ea-151">콘솔 트리에서 오프라인 파일을 보려는 인스턴스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-151">In the console tree, locate the instance on which you want to view the offline files.</span></span>  
  
4.  <span data-ttu-id="282ea-152">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-152">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="282ea-153">인스턴스가 **로컬 서버 그룹**아래에 있으면 **로컬 서버 그룹**, 서버 그룹(인스턴스가 그룹의 멤버인 경우)을 차례로 확장하고 인스턴스를 마우스 오른쪽 단추로 클릭한 다음 **SQL Server 로그 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-153">If the instance is under **Local Server Groups**, expand **Local Server Groups**, expand the server group (if the instance is a member of a group), right-click the instance, and then click **View SQL Server Log**.</span></span>  
  
    -   <span data-ttu-id="282ea-154">인스턴스가 중앙 관리 서버 자체이면 **중앙 관리 서버**를 확장하고 인스턴스를 마우스 오른쪽 단추로 클릭하고 **중앙 관리 서버 동작**을 가리킨 다음 **SQL Server 로그 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-154">If the instance is the Central Management Server itself, expand **Central Management Servers**, right-click the instance, point to **Central Management Server Actions**, and then click **View SQL Server Log**.</span></span>  
  
    -   <span data-ttu-id="282ea-155">인스턴스가 **중앙 관리 서버**아래에 있으면 **중앙 관리 서버**, 해당 중앙 관리 서버를 차례로 확장하고 인스턴스를 마우스 오른쪽 단추로 클릭한 다음(또는 서버 그룹을 확장하고 인스턴스를 마우스 오른쪽 단추로 클릭한 다음) **SQL Server 로그 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-155">If the instance is under **Central Management Servers**, expand **Central Management Servers**, expand the Central Management Server, right-click the instance (or expand a server group and right-click the instance), and then click **View SQL Server Log**.</span></span>  
  
5.  <span data-ttu-id="282ea-156">로컬 인스턴스에 연결하는 경우 현재 사용자 자격 증명을 사용하여 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-156">If you are connecting to a local instance, the connection is made using the current user credentials.</span></span>  
  
     <span data-ttu-id="282ea-157">원격 인스턴스에 연결하는 경우 **로그 파일 뷰어 - 연결 계정** 대화 상자에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-157">If you are connecting to a remote instance, in the **Log File Viewer - Connect As** dialog box, do either of the following:</span></span>  
  
    -   <span data-ttu-id="282ea-158">현재 사용자로 연결하려면 **다른 사용자로 연결** 확인란의 선택을 지운 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-158">To connect as the current user, make sure that the **Connect as another user** check box is cleared, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="282ea-159">다른 사용자로 연결하려면 **다른 사용자로 연결** 확인란을 선택한 다음 **사용자 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-159">To connect as another user, select the **Connect as another user** check box, and then click **Set User**.</span></span> <span data-ttu-id="282ea-160">메시지가 표시되면 *domain_name*\\*user_name*형식의 사용자 이름이 포함된 사용자 자격 증명을 입력하고 **확인**을 클릭한 다음 다시 **확인** 을 클릭하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-160">When you are prompted, enter the user credentials (with the user name in the format *domain_name*\\*user_name*), click **OK**, and then click **OK** again to connect.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="282ea-161">로그 파일 로드 시간이 너무 긴 경우 로그 파일 뷰어 도구 모음에서 **중지** 를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="282ea-161">If the log files take too long to load, you can click **Stop** on the Log File Viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="282ea-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="282ea-162">See Also</span></span>  
 [<span data-ttu-id="282ea-163">로그 파일 뷰어</span><span class="sxs-lookup"><span data-stu-id="282ea-163">Log File Viewer</span></span>](log-file-viewer.md)  
  
  
