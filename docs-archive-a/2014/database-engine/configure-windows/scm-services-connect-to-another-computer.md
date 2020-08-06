---
title: 다른 컴퓨터에 연결(SQL Server 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], other computers
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3d478cebc1ca36ccb8f87b0355b7c8fe0a928cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661354"
---
# <a name="connect-to-another-computer-sql-server-configuration-manager"></a><span data-ttu-id="bb80d-102">다른 컴퓨터에 연결(SQL Server 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="bb80d-102">Connect to Another Computer (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="bb80d-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 다른 컴퓨터에 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-103">This topic describes how to connect to another computer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="bb80d-104">첫 번째 절차에 따라 Windows 컴퓨터 관리 MMC( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console)를 열고 해당 컴퓨터에 연결한 다음 서비스 및 애플리케이션 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-104">Follow the first procedure to open the Windows Computer Management [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (mmc), connect to the computer, and expand the Services and Applications tree.</span></span> <span data-ttu-id="bb80d-105">두 번째 절차에 따라 원격 컴퓨터의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자에 대한 링크가 있는 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-105">Follow the second procedure to create a file with a link to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on a remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb80d-106">일부 작업은 원격으로 연결할 때 구성 관리를 통해 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-106">Some actions cannot be performed by Configuration Manager when connecting remotely.</span></span>  
  
 <span data-ttu-id="bb80d-107">다른 컴퓨터의 서비스를 시작, 중지, 일시 중지 또는 재개하기 위해 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 서버에 연결하고 해당 서버 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 마우스 오른쪽 단추로 클릭한 다음 원하는 동작을 클릭할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-107">To start, stop, pause, or resume services on another computer, you can also connect to the server with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the server or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and then click the desired action.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-connect-to-another-computer-with-windows-computer-management"></a><span data-ttu-id="bb80d-108">Windows 컴퓨터 관리에서 다른 컴퓨터에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="bb80d-108">To connect to another computer with Windows Computer Management</span></span>  
  
1.  <span data-ttu-id="bb80d-109">**시작** 메뉴에서 **내 컴퓨터**를 마우스 오른쪽 단추로 클릭 한 다음 관리를 클릭 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="bb80d-109">On the **Start** menu, right-click **My Computer**, and then click **Manage.**</span></span>  
  
2.  <span data-ttu-id="bb80d-110">**컴퓨터 관리**에서 **컴퓨터 관리(로컬)** 를 마우스 오른쪽 단추로 클릭하고 **다른 컴퓨터로 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-110">In **Computer Management**, right-click **Computer Management (Local)**, and then click **Connect to another computer**.</span></span>  
  
3.  <span data-ttu-id="bb80d-111">**컴퓨터 선택** 대화 상자의 **다른 컴퓨터** 입력란에 관리할 컴퓨터의 이름을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-111">In the **Select Computer** dialog box, in the **Another computer** text box, type the name of the computer you want to manage, and then click **OK**.</span></span>  
  
     <span data-ttu-id="bb80d-112">원격 컴퓨터에서 실행 중인 서비스가 컴퓨터 관리에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-112">Computer Management displays the services running on the remote computer.</span></span> <span data-ttu-id="bb80d-113">최상위 노드가 **컴퓨터 관리** \<*remotecomputer*>로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-113">The top-level node changes to **Computer Management** \<*remotecomputer*>.</span></span>  
  
4.  <span data-ttu-id="bb80d-114">콘솔 트리에서 **서비스 및 애플리케이션**을 확장한 다음 **SQL Server 구성 관리자** 를 확장하여 원격 컴퓨터의 서비스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-114">In the console tree, expand **Services and Applications**, and then expand **SQL Server Configuration Manager** to manage the remote computer's services.</span></span>  
  
#### <a name="to-save-a-link-to-sql-server-configuration-manager-for-another-computer"></a><span data-ttu-id="bb80d-115">다른 컴퓨터의 SQL Server 구성 관리자에 대한 링크를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="bb80d-115">To save a link to SQL Server Configuration Manager for another computer</span></span>  
  
1.  <span data-ttu-id="bb80d-116">**시작** 메뉴에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-116">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="bb80d-117">**열기** 상자에를 입력 `mmc -a` 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 작성자 모드에서 관리 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-117">In the **Open** box, type `mmc -a` to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console in author mode.</span></span>  
  
3.  <span data-ttu-id="bb80d-118">**파일** 메뉴에서 **스냅인 추가/제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-118">On the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
4.  <span data-ttu-id="bb80d-119">**스냅인 추가/제거** 창에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-119">In the **Add/Remove Snap-in** window, click **Add**.</span></span>  
  
5.  <span data-ttu-id="bb80d-120">**독립 실행형 스냅인 추가** 창에서 **컴퓨터 관리** 를 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-120">In the **Add Standalone Snap-in** window, click **Computer Management** and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="bb80d-121">**컴퓨터 관리** 창에서 **다른 컴퓨터**를 클릭하고 관리할 원격 컴퓨터의 이름을 입력한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-121">In the **Computer Management** window, click **Another computer**, type the name of the remote computer you wish to manage, and then click **Finish**.</span></span>  
  
7.  <span data-ttu-id="bb80d-122">**독립 실행형 스냅인 추가** 창에서 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-122">In the **Add Standalone Snap-in** window, click **Close**.</span></span>  
  
8.  <span data-ttu-id="bb80d-123">**스냅인 추가/제거** 창에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-123">In the **Add/Remove Snap-in** window, click **OK**.</span></span>  
  
9. <span data-ttu-id="bb80d-124">**컴퓨터 관리 ( ***\<computer name>*** )** 및 **서비스 및 응용 프로그램**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-124">Expand **Computer Management (***\<computer name>***)**, and **Services and Applications**.</span></span>  
  
10. <span data-ttu-id="bb80d-125">**SQL Server 구성 관리자**를 마우스 오른쪽 단추로 클릭한 다음 **여기에서 창 새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-125">Right-click **SQL Server Configuration Manager**, and then click **New Window from here**.</span></span>  
  
11. <span data-ttu-id="bb80d-126">**창** 메뉴에서 **콘솔 루트**를 클릭하여 첫 번째 창으로 전환한 다음, 창을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-126">On the **Window** menu, click **Console Root**, to switch back to the first window, and delete the window.</span></span>  
  
12. <span data-ttu-id="bb80d-127">**파일** 메뉴에서 다른 이름 **으로 저장**을 클릭 하 고 파일 확장명을 가진 적절 한 이름을 사용 하 여 원하는 폴더에 파일을 저장 합니다 `.msc` .</span><span class="sxs-lookup"><span data-stu-id="bb80d-127">On the **File** menu, click **Save As**, and save the file in the desired folder, with an appropriate name with the `.msc` file extension.</span></span> <span data-ttu-id="bb80d-128">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-128">Close the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.</span></span>  
  
13. <span data-ttu-id="bb80d-129">대상 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 열려면 파일을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-129">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on the target computer, double-click the file.</span></span> <span data-ttu-id="bb80d-130">필요한 경우 파일에 대한 링크를 바탕 화면이나 **시작** 메뉴에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-130">If desired, save a link to the file on the desktop or in the **Start** menu.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="bb80d-131">원격 컴퓨터의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하는 경우 컴퓨터 이름이 명확하지 않아 실수로 다른 컴퓨터를 중지하거나 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-131">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager on a remote computer, the computer name is not obvious and it is possible to mistakenly stop or configure the wrong computer.</span></span> <span data-ttu-id="bb80d-132">**서비스** 탭에서 **호스트 이름** 상자를 선택하여 서비스를 수정하기 전에 컴퓨터 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bb80d-132">On the **Service** tab, check the **Host Name** box to confirm the computer name before modifying a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb80d-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb80d-133">See Also</span></span>  
 [<span data-ttu-id="bb80d-134">WMI를 구성하여 SQL Server 도구에 서버 상태 표시</span><span class="sxs-lookup"><span data-stu-id="bb80d-134">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
