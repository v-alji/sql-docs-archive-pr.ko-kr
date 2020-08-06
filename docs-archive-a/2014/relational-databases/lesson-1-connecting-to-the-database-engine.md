---
title: '1단원: 데이터베이스 엔진에 연결 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e8db82f0-50ed-4531-9209-940006ed34cb
author: rothja
ms.author: jroth
ms.openlocfilehash: 6cdc53bece6bfade5fb4a0ba7d97b7bd2e921d95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649546"
---
# <a name="lesson-1-connecting-to-the-database-engine"></a><span data-ttu-id="f303f-102">1단원: 데이터베이스 엔진에 연결</span><span class="sxs-lookup"><span data-stu-id="f303f-102">Lesson 1: Connecting to the Database Engine</span></span>
  <span data-ttu-id="f303f-103">[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]을 설치할 때 설치되는 도구는 버전 및 설치 선택 사항에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-103">When you install the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], the tools that are installed depend upon the edition and your setup choices.</span></span> <span data-ttu-id="f303f-104">이 단원에서는 주 도구를 검토하고 이러한 도구에 연결하는 방법을 보여 주며 보다 많은 사용자에게 권한을 부여하는 기본 기능을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-104">This lesson reviews the principal tools, and shows you how to connect and perform a basic function (authorizing more users).</span></span>  
  
  
  
##  <a name="tools-for-getting-started"></a><a name="tools"></a><span data-ttu-id="f303f-105">시작 도구</span><span class="sxs-lookup"><span data-stu-id="f303f-105">Tools For Getting Started</span></span>  
 <span data-ttu-id="f303f-106">[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 은 다양한 도구와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-106">The [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] ships with a variety of tools.</span></span> <span data-ttu-id="f303f-107">이 항목에서는 이 중 가장 필요한 도구를 설명하고 작업에 적합한 도구를 선택할 수 있도록 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-107">This topic describes the first tools you will need, and helps you select the right tool for the job.</span></span> <span data-ttu-id="f303f-108">모든 도구는 **시작** 메뉴에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-108">All tools can be accessed from the **Start** menu.</span></span> <span data-ttu-id="f303f-109">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]와 같은 일부 도구는 기본적으로 설치되지 않으며</span><span class="sxs-lookup"><span data-stu-id="f303f-109">Some tools, such as [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], are not installed by default.</span></span> <span data-ttu-id="f303f-110">설치하는 동안 클라이언트 구성 요소의 일부로 해당 도구를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-110">You must select the tools as part of the client components during setup.</span></span> <span data-ttu-id="f303f-111">아래에서 설명하는 도구에 대한 전체 설명을 보려면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서에서 검색하세요.</span><span class="sxs-lookup"><span data-stu-id="f303f-111">For a complete description of the tools described below, search for them in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span> [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] <span data-ttu-id="f303f-112">에는 이러한 도구의 일부만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-112">contains only a subset of the tools.</span></span>  
  
### <a name="basic-tools"></a><span data-ttu-id="f303f-113">기본 도구</span><span class="sxs-lookup"><span data-stu-id="f303f-113">Basic Tools</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="f303f-114">는 [!INCLUDE[ssDE](../includes/ssde-md.md)]을 관리하고 [!INCLUDE[tsql](../includes/tsql-md.md)] 코드를 기록하는 주 도구이며</span><span class="sxs-lookup"><span data-stu-id="f303f-114">is the principal tool for administering the [!INCLUDE[ssDE](../includes/ssde-md.md)] and writing [!INCLUDE[tsql](../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="f303f-115">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 셸에 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-115">It is hosted in the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell.</span></span> <span data-ttu-id="f303f-116">에는 포함 되어 있지 [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] 않지만 [Microsoft 다운로드 센터](https://go.microsoft.com/fwlink/?LinkId=144346)에서 별도로 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-116">It is not included in [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] but is available as a separate download from [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkId=144346).</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f303f-117">구성 관리자는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 및 클라이언트 도구 둘 다와 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-117">Configuration Manager installs with both [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the client tools.</span></span> <span data-ttu-id="f303f-118">이 관리자를 사용하면 서버 프로토콜을 설정하고, TCP 포트와 같은 프로토콜 옵션을 구성하고, 서버 서비스가 자동으로 시작되도록 구성하고, 클라이언트 컴퓨터에서 사용자가 선호하는 방법으로 연결을 설정하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-118">It lets you enable server protocols, configure protocol options such as TCP ports, configure server services to start automatically, and configure client computers to connect in your preferred manner.</span></span> <span data-ttu-id="f303f-119">이 도구는 더 많은 고급 연결 요소를 구성하지만 기능을 설정하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-119">This tool configures the more advanced connectivity elements but does not enable features.</span></span>  
  
### <a name="sample-database"></a><span data-ttu-id="f303f-120">예제 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="f303f-120">Sample Database</span></span>  
 <span data-ttu-id="f303f-121">예제 데이터베이스 및 예제는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]과 함께 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-121">The sample databases and samples are not included with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f303f-122">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서에 설명된 대부분의 예제에서는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 샘플 데이터베이스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-122">Most of the examples that are described in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online use the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
##### <a name="to-start-sql-server-management-studio"></a><span data-ttu-id="f303f-123">SQL Server Management Studio를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="f303f-123">To start SQL Server Management Studio</span></span>  
  
-   <span data-ttu-id="f303f-124">**시작** 메뉴에서 **모든 프로그램**,을 차례로 가리킨 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] 다음 **SQL Server Management Studio**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-124">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
##### <a name="to-start-sql-server-configuration-manager"></a><span data-ttu-id="f303f-125">SQL Server 구성 관리자를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="f303f-125">To start SQL Server Configuration Manager</span></span>  
  
-   <span data-ttu-id="f303f-126">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-126">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
##  <a name="connecting-with-management-studio"></a><a name="connect"></a><span data-ttu-id="f303f-127">Management Studio 연결</span><span class="sxs-lookup"><span data-stu-id="f303f-127">Connecting with Management Studio</span></span>  
 <span data-ttu-id="f303f-128">인스턴스 이름을 알고 있으며 컴퓨터의 Administrators 그룹 멤버로 연결하는 경우에는 동일한 컴퓨터에서 실행하는 도구의 [!INCLUDE[ssDE](../includes/ssde-md.md)]에 쉽게 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-128">It is easy to connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] from tools that are running on the same computer if you know the name of the instance, and if you are connecting as a member of the Administrators group on the computer.</span></span> <span data-ttu-id="f303f-129">다음 절차는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 호스팅하는 컴퓨터에서 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-129">The following procedures must be performed on the same computer that hosts [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
##### <a name="to-determine-the-name-of-the-instance-of-the-database-engine"></a><span data-ttu-id="f303f-130">데이터베이스 엔진 인스턴스의 이름을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="f303f-130">To determine the name of the instance of the Database Engine</span></span>  
  
1.  <span data-ttu-id="f303f-131">Administrators 그룹의 멤버로 Windows에 로그인한 다음 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-131">Log into Windows as a member of the Administrators group, and open [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f303f-132">[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]또는 이상에 연결 하는 [!INCLUDE[wiprlhlong](../includes/wiprlhlong-md.md)] 경우 [!INCLUDE[nextref_longhorn](../includes/nextref-longhorn-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 관리자 자격 증명을 사용 하 여 연결 하려면를 마우스 오른쪽 단추로 클릭 한 다음 **관리자 권한으로 실행** 을 클릭 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-132">If you are connecting to  [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] on [!INCLUDE[wiprlhlong](../includes/wiprlhlong-md.md)] or [!INCLUDE[nextref_longhorn](../includes/nextref-longhorn-md.md)] (or more recent), you may need to right-click [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] and then click **Run as Administrator** in order to connect using your Administrator credentials.</span></span> <span data-ttu-id="f303f-133">[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]부터는 설치 과정에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 대해 선택한 로그인이 추가되므로 관리자 자격 증명은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-133">Starting in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], setup adds selected logins to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], so your Administrator credentials are not necessary.</span></span>  
  
2.  <span data-ttu-id="f303f-134">**서버에 연결** 대화 상자에서 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-134">In the **Connect to Server** dialog box, click **Cancel**.</span></span>  
  
3.  <span data-ttu-id="f303f-135">등록된 서버가 표시되지 않으면 **보기** 메뉴에서 **등록된 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-135">If Registered Servers is not displayed, on the **View** menu, click **Registered Servers**.</span></span>  
  
4.  <span data-ttu-id="f303f-136">등록된 서버 도구 모음에서 **데이터베이스 엔진** 을 선택한 상태로 **데이터베이스 엔진**을 확장하고 **로컬 서버 그룹**을 마우스 오른쪽 단추로 클릭한 다음 **태스크**를 가리키고 **로컬 서버 등록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-136">With **Database Engine** selected on the Registered Servers toolbar, expand **Database Engine**, right-click **Local Server Groups**, point to **Tasks**, and then click **Register Local Servers**.</span></span> <span data-ttu-id="f303f-137">컴퓨터에 설치된 모든 [!INCLUDE[ssDE](../includes/ssde-md.md)] 인스턴스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-137">All instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] installed on the computer are displayed.</span></span> <span data-ttu-id="f303f-138">기본 인스턴스의 이름은 지정되지 않으며 컴퓨터 이름으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-138">The default instance is unnamed and is shown as the computer name.</span></span> <span data-ttu-id="f303f-139">명명된 인스턴스는 컴퓨터 이름 다음에 백슬래시(\\)가 오고 마지막으로 인스턴스 이름이 붙는 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-139">A named instance displays as the computer name followed by a backward slash (\\) and then the name of the instance.</span></span> <span data-ttu-id="f303f-140">[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]의 경우 설치하는 동안 이름을 변경하지 않은 한 인스턴스 이름이 *<computer_name>* \sqlexpress로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-140">For [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], the instance is named *<computer_name>* \sqlexpress unless the name was changed during setup.</span></span>  
  
##### <a name="to-verify-that-the-database-engine-is-running"></a><span data-ttu-id="f303f-141">데이터베이스 엔진이 실행 중인지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="f303f-141">To verify that the Database Engine is running</span></span>  
  
1.  <span data-ttu-id="f303f-142">등록된 서버에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스 이름 옆에 흰색 화살표가 포함된 녹색 원이 표시되는 경우 [!INCLUDE[ssDE](../includes/ssde-md.md)] 이 실행 중이므로 별도의 동작이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-142">In Registered Servers, if the name of your instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has a green dot with a white arrow next to the name, the [!INCLUDE[ssDE](../includes/ssde-md.md)] is running and no further action is necessary.</span></span>  
  
2.  <span data-ttu-id="f303f-143">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스 이름 옆에 흰색 사각형이 포함된 빨간색 원이 표시되는 경우 [!INCLUDE[ssDE](../includes/ssde-md.md)] 이 중지된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-143">If the name of your instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has a red dot with a white square next to the name, the [!INCLUDE[ssDE](../includes/ssde-md.md)] is stopped.</span></span> <span data-ttu-id="f303f-144">[!INCLUDE[ssDE](../includes/ssde-md.md)]의 이름을 마우스 오른쪽 단추로 클릭한 다음 **서비스 제어**, **시작**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-144">Right-click the name of the [!INCLUDE[ssDE](../includes/ssde-md.md)], click **Service Control**, and then click **Start**.</span></span> <span data-ttu-id="f303f-145">확인 대화 상자가 표시된 다음 [!INCLUDE[ssDE](../includes/ssde-md.md)] 이 시작되고 원이 흰색 화살표가 포함된 녹색으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-145">After a confirmation dialog box, the [!INCLUDE[ssDE](../includes/ssde-md.md)] should start and the circle should turn green with a white arrow.</span></span>  
  
##### <a name="to-connect-to-the-database-engine"></a><span data-ttu-id="f303f-146">데이터베이스 엔진에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="f303f-146">To connect to the Database Engine</span></span>  
  
1.  <span data-ttu-id="f303f-147">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]의 **파일** 메뉴에서 **개체 탐색기 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-147">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], on the **File** menu, click **Connect Object Explorer**.</span></span>  
  
     <span data-ttu-id="f303f-148">**서버에 연결** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-148">The **Connect to Server** dialog box opens.</span></span> <span data-ttu-id="f303f-149">**서버 유형** 상자에 마지막으로 사용한 구성 요소 유형이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-149">The **Server type** box displays the type of component that was last used.</span></span>  
  
2.  <span data-ttu-id="f303f-150">**데이터베이스 엔진**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-150">Select **Database Engine**.</span></span>  
  
3.  <span data-ttu-id="f303f-151">**서버 이름** 상자에 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-151">In the **Server name** box, type the name of the instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="f303f-152">기본 SQL Server 인스턴스의 경우 서버 이름은 컴퓨터 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-152">For the default instance of SQL Server, the server name is the computer name.</span></span> <span data-ttu-id="f303f-153">SQL Server 명명 된 인스턴스의 경우 서버 이름은 **<\SQLEXPRESS**와 같이 *<computer_name>\*\*\*\\*\*\* \* instance_name> ACCTG_SRVR입니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-153">For a named instance of SQL Server, the server name is the *<computer_name>***\\***<instance_name>,* such as **ACCTG_SRVR\SQLEXPRESS**.</span></span>  
  
4.  <span data-ttu-id="f303f-154">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-154">Click **Connect**.</span></span>  
  
##  <a name="authorizing-additional-connections"></a><a name="additional"></a><span data-ttu-id="f303f-155">추가 연결 권한 부여</span><span class="sxs-lookup"><span data-stu-id="f303f-155">Authorizing Additional Connections</span></span>  
 <span data-ttu-id="f303f-156">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 관리자로 연결한 다음 가장 먼저 수행해야 할 태스크 중 하나는 다른 사용자가 연결할 수 있도록 권한을 부여하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-156">Now that you have connected to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] as an administrator, one of your first tasks is to authorize other users to connect.</span></span> <span data-ttu-id="f303f-157">로그인을 만들고 이 로그인이 사용자로서 데이터베이스에 액세스할 수 있도록 권한을 부여하여 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-157">You do this by creating a login and authorizing that login to access a database as a user.</span></span> <span data-ttu-id="f303f-158">로그인은 Windows 자격 증명을 사용하는 Windows 인증 로그인이나 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 인증 정보를 저장하며 Windows 자격 증명과는 독립적인 SQL Server 인증 로그인 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-158">Logins can be either Windows Authentication logins, which use credentials from Windows, or SQL Server Authentication logins, which store the authentication information in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and are independent of your Windows credentials.</span></span> <span data-ttu-id="f303f-159">가능하면 Windows 인증을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f303f-159">Use Windows Authentication whenever possible.</span></span>  
  
##### <a name="create-a-windows-authentication-login"></a><span data-ttu-id="f303f-160">Windows 인증 로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="f303f-160">Create a Windows Authentication login</span></span>  
  
1.  <span data-ttu-id="f303f-161">이전 태스크에서는 [!INCLUDE[ssDE](../includes/ssde-md.md)] 를 사용하여 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]에 연결했습니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-161">In the previous task, you connected to the [!INCLUDE[ssDE](../includes/ssde-md.md)] using [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="f303f-162">개체 탐색기에서 서버 인스턴스, **보안**을 차례로 확장하고 **로그인**을 마우스 오른쪽 단추로 클릭한 다음 **새 로그인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-162">In Object Explorer, expand your server instance, expand **Security**, right-click **Logins**, and then click **New Login**.</span></span>  
  
     <span data-ttu-id="f303f-163">**로그인 - 신규** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-163">The **Login - New** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="f303f-164">**일반** 페이지의 **로그인 이름** 상자에 \* \<domain> \\ 로그인 \><\* 형식으로 Windows 로그인을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-164">On the **General** page, in the **Login name** box, type a Windows login in the format *\<domain>\\<login\>*.</span></span>  
  
3.  <span data-ttu-id="f303f-165">**기본 데이터베이스** 상자에서 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 를 선택합니다(사용 가능한 경우).</span><span class="sxs-lookup"><span data-stu-id="f303f-165">In the **Default database** box, select [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] if available.</span></span> <span data-ttu-id="f303f-166">사용할 수 없는 경우 **master**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-166">Otherwise select **master**.</span></span>  
  
4.  <span data-ttu-id="f303f-167">새 로그인을 관리자로 지정하려는 경우 **서버 역할** 페이지에서 **sysadmin**을 클릭하고, 지정하지 않는 경우 이 확인란을 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-167">On the **Server Roles** page, if the new login is to be an administrator, click **sysadmin**, otherwise leave this blank.</span></span>  
  
5.  <span data-ttu-id="f303f-168">**사용자 매핑** 페이지에서 **데이터베이스에 대한** 매핑 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 을 선택합니다(사용 가능한 경우).</span><span class="sxs-lookup"><span data-stu-id="f303f-168">On the **User Mapping** page, select **Map** for the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database if it is available.</span></span> <span data-ttu-id="f303f-169">사용할 수 없는 경우 **master**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-169">Otherwise select **master**.</span></span> <span data-ttu-id="f303f-170">**사용자** 상자가 해당 로그인으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-170">Note that the **User** box is populated with the login.</span></span> <span data-ttu-id="f303f-171">이 대화 상자를 닫으면 데이터베이스에 해당 사용자가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-171">When closed, the dialog box will create this user in the database.</span></span>  
  
6.  <span data-ttu-id="f303f-172">**기본 스키마** 상자에 **dbo** 를 입력하여 해당 로그인을 데이터베이스 소유자 스키마에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-172">In the **Default Schema** box, type **dbo** to map the login to the database owner schema.</span></span>  
  
7.  <span data-ttu-id="f303f-173">**보안 개체** 및 **상태** 상자의 기본 설정을 적용한 다음 **확인** 을 클릭하여 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-173">Accept the default settings for the **Securables** and **Status** boxes and click **OK** to create the login.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f303f-174">이 섹션의 내용은 초보자를 위한 기본 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-174">This is basic information to get you started.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f303f-175">에서는 강력한 보안 환경을 제공하며 보안은 데이터베이스 작업의 매우 중요한 한 측면입니다.</span><span class="sxs-lookup"><span data-stu-id="f303f-175">provides a rich security environment, and security is obviously an important aspect of database operations.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="f303f-176">다음 단원</span><span class="sxs-lookup"><span data-stu-id="f303f-176">Next Lesson</span></span>  
 [<span data-ttu-id="f303f-177">2단원: 다른 컴퓨터에서 연결</span><span class="sxs-lookup"><span data-stu-id="f303f-177">Lesson 2: Connecting from Another Computer</span></span>](lesson-2-connecting-from-another-computer.md)  
  
  