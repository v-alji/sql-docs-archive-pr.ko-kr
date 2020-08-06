---
title: 자동으로 시작 되도록 SQL Server 인스턴스 설정 (SQL Server 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2fc21bd881c1588da47710c6d8437e31d3df2ab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738752"
---
# <a name="set-an-instance-of-sql-server-to-start-automatically-sql-server-configuration-manager"></a><span data-ttu-id="e2ca8-102">SQL Server 인스턴스를 자동으로 시작하도록 설정(SQL Server 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="e2ca8-102">Set an Instance of SQL Server to Start Automatically (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="e2ca8-103">이 항목에서는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 인스턴스가 자동으로 시작되도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-103">This topic describes how to set an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to start automatically in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="e2ca8-104">설치 시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 일반적으로 자동으로 시작되도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-104">During setup, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is normally configured to start automatically.</span></span> <span data-ttu-id="e2ca8-105">이렇게 구성되지 않은 경우 언제든지 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-105">If this was not done, you can change that setting at any time.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e2ca8-106">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="e2ca8-106">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a><span data-ttu-id="e2ca8-107">SQL Server 인스턴스를 자동으로 시작하도록 설정하려면</span><span class="sxs-lookup"><span data-stu-id="e2ca8-107">To set an instance of SQL Server to start automatically</span></span>  
  
1.  <span data-ttu-id="e2ca8-108">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2ca8-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자는 독립 실행형 프로그램이 아니라 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console 프로그램용 스냅인이므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자는 최신 버전의 Windows에서 애플리케이션으로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-109">Because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager does not appear as an application in newer versions of Windows.</span></span>  
    >   
    >  -   <span data-ttu-id="e2ca8-110">**Windows 10**:</span><span class="sxs-lookup"><span data-stu-id="e2ca8-110">**Windows 10**:</span></span>  
    >          <span data-ttu-id="e2ca8-111">Configuration Manager를 열려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **시작 페이지**에서 sqlservermanager12.msc (의 경우)를 입력 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-111">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, on the **Start Page**, type SQLServerManager12.msc (for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]).</span></span> <span data-ttu-id="e2ca8-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 경우 12를 더 작은 수로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-112">For previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replace 12 with a smaller number.</span></span> <span data-ttu-id="e2ca8-113">SQLServerManager12.msc를 클릭하면 구성 관리자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-113">Clicking SQLServerManager12.msc opens the Configuration Manager.</span></span> <span data-ttu-id="e2ca8-114">Configuration Manager를 시작 페이지나 작업 표시줄에 고정 하려면 Sqlservermanager12.msc를 마우스 오른쪽 단추로 클릭 한 다음 **파일 위치 열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-114">To pin the Configuration Manager to the Start Page or Task Bar, right-click SQLServerManager12.msc, and then click **Open file location**.</span></span> <span data-ttu-id="e2ca8-115">Windows 파일 탐색기에서 Sqlservermanager12.msc를 마우스 오른쪽 단추로 클릭 한 다음 **시작 화면에 고정** 또는 **작업 표시줄에 고정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-115">In the Windows File Explorer, right-click SQLServerManager12.msc, and then click **Pin to Start** or **Pin to taskbar**.</span></span>  
    > -   <span data-ttu-id="e2ca8-116">**Windows 8**:</span><span class="sxs-lookup"><span data-stu-id="e2ca8-116">**Windows 8**:</span></span>  
    >          <span data-ttu-id="e2ca8-117">Configuration Manager를 열려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **검색** 참의 **앱**아래에 \*\*SQLServerManager \<version> \*\* 를 입력 한 `SQLServerManager12.msc` 다음 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-117">To open [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager\<version>.msc** such as `SQLServerManager12.msc`, and then press **Enter**.</span></span>  
  
2.  <span data-ttu-id="e2ca8-118">**SQL Server 구성 관리자**에서 **서비스**를 확장한 다음 **SQL Server**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-118">In **SQL Server Configuration Manager**, expand **Services**, and then click **SQL Server**.</span></span>  
  
3.  <span data-ttu-id="e2ca8-119">세부 정보 창에서 자동으로 시작할 인스턴스의 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-119">In the details pane, right-click the name of the instance you want to start automatically, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e2ca8-120">**SQL Server \<***instancename***> 속성** 대화 상자에서 **시작 모드**를 **자동**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-120">In the **SQL Server \<***instancename***> Properties** dialog box, set **Start Mode** to **Automatic**.</span></span>  
  
5.  <span data-ttu-id="e2ca8-121">**확인**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e2ca8-121">Click **OK**, and then close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ca8-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2ca8-122">See Also</span></span>  
 <span data-ttu-id="e2ca8-123">[SQL Server 인스턴스의 자동 시작 방지&#40;SQL Server 구성 관리자&#41;](scm-services-prevent-automatic-startup-of-an-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e2ca8-123">[Prevent Automatic Startup of an Instance of SQL Server &#40;SQL Server Configuration Manager&#41;](scm-services-prevent-automatic-startup-of-an-instance.md) </span></span>  
 <span data-ttu-id="e2ca8-124">[다른 컴퓨터에 연결&#40;SQL Server 구성 관리자&#41;](scm-services-connect-to-another-computer.md) </span><span class="sxs-lookup"><span data-stu-id="e2ca8-124">[Connect to Another Computer &#40;SQL Server Configuration Manager&#41;](scm-services-connect-to-another-computer.md) </span></span>  
 [<span data-ttu-id="e2ca8-125">WMI를 구성하여 SQL Server 도구에 서버 상태 표시</span><span class="sxs-lookup"><span data-stu-id="e2ca8-125">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
