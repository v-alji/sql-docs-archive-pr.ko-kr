---
title: SSIS 서비스에 대 한 액세스를 위해 Windows 방화벽 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], firewalls
- Windows Firewall [Integration Services]
- unauthorized access [Integration Services]
- Integration Services service, firewalls
- firewall systems [Integration Services]
- SQL Server Integration Services, firewalls
- SSIS, firewalls
ms.assetid: 39975cf2-c351-4205-8c39-27a0fadfb010
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d18b061ce16c88c50bbc08874efec455c28e15a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661258"
---
# <a name="configure-a-windows-firewall-for-access-to-the-ssis-service"></a><span data-ttu-id="e4f4f-102">SSIS 서비스 액세스에 대한 Windows 방화벽 구성</span><span class="sxs-lookup"><span data-stu-id="e4f4f-102">Configure a Windows Firewall for Access to the SSIS Service</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="e4f4f-103">이 항목에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 관리하는 Windows 서비스인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="e4f4f-104">는 이전 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]버전과의 호환성을 위한 서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="e4f4f-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]부터는 Integration Services 서버의 패키지와 같은 개체를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="e4f4f-106">Windows 방화벽 시스템을 사용하면 네트워크 연결을 통해 이루어지는 컴퓨터 리소스에 대한 무단 액세스를 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-106">The windowsfirewall system helps prevent unauthorized access to computer resources over a network connection.</span></span> <span data-ttu-id="e4f4f-107">이 방화벽을 통해 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에 액세스하려면 액세스 가능하도록 방화벽을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-107">To access [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] through this firewall, you have to configure the firewall to enable access.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e4f4f-108">원격 서버에 저장된 패키지를 관리하는 경우 해당 원격 서버에 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스 인스턴스에 연결할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-108">To manage packages that are stored on a remote server, you do not have to connect to the instance of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on that remote server.</span></span> <span data-ttu-id="e4f4f-109">대신 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 원격 서버에 저장된 패키지를 표시하도록 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 서비스에 대한 구성 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-109">Instead, edit the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service so that [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] displays the packages that are stored on the remote server.</span></span> <span data-ttu-id="e4f4f-110">자세한 내용은 [Integration Services 서비스 구성&#40;SSIS 서비스&#41;](configuring-the-integration-services-service-ssis-service.md)버전과의 호환성을 위한 서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-110">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](configuring-the-integration-services-service-ssis-service.md).</span></span>  
  
 <span data-ttu-id="e4f4f-111">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에는 DCOM 프로토콜이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-111">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service uses the DCOM protocol.</span></span> <span data-ttu-id="e4f4f-112">방화벽을 통해 DCOM 프로토콜이 작동 하는 방법에 대 한 자세한 내용은 "[방화벽과 함께 분산 COM 사용](https://manualzz.com/doc/19762578/using-distributed-com-with-firewalls-by-michael-nelson-in...)" 문서를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-112">For more information about how the DCOM protocol works through firewalls, see the article, "[Using Distributed COM with Firewalls](https://manualzz.com/doc/19762578/using-distributed-com-with-firewalls-by-michael-nelson-in...)".</span></span>  
  
 <span data-ttu-id="e4f4f-113">사용할 수 있는 방화벽 시스템은 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-113">There are many firewall systems available.</span></span> <span data-ttu-id="e4f4f-114">Windows 방화벽 이외의 다른 방화벽을 사용하는 경우 사용 중인 시스템별 정보를 보려면 해당 방화벽 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-114">If you are running a firewall other than windowsfirewall, see your firewall documentation for information that is specific to the system you are using.</span></span>  
  
 <span data-ttu-id="e4f4f-115">방화벽에서 애플리케이션 수준의 필터링이 지원되는 경우 Windows에서 제공하는 사용자 인터페이스를 사용하여 프로그램 및 서비스와 같이 방화벽을 통해 허용되는 예외를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-115">If the firewall supports application-level filtering, you can use the user interface that Windows provides to specify the exceptions that are allowed through the firewall, such as programs and services.</span></span> <span data-ttu-id="e4f4f-116">그렇지 않으면 제한된 TCP 포트 집합을 사용하도록 DCOM을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-116">Otherwise, you have to configure DCOM to use a limited set of TCP ports.</span></span> <span data-ttu-id="e4f4f-117">이전에 제공된 Microsoft 웹 사이트 링크에는 사용할 TCP 포트 지정 방법에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-117">The Microsoft website link previously provided includes information about how to specify the TCP ports to use.</span></span>  
  
 <span data-ttu-id="e4f4f-118">Integration Services 서비스에는 포트 135가 사용되며 이 포트는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-118">The Integration Services service uses port 135, and the port cannot be changed.</span></span> <span data-ttu-id="e4f4f-119">SCM(서비스 제어 관리자)에 액세스하려면 TCP 포트 135를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-119">You have to open TCP port 135 for access to the service control manager (SCM).</span></span> <span data-ttu-id="e4f4f-120">SCM은 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스 시작 및 중지와 실행 중인 서비스에 대한 제어 요청 전송과 같은 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-120">SCM performs tasks such as starting and stopping [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] services and transmitting control requests to the running service.</span></span>  
  
 <span data-ttu-id="e4f4f-121">다음 섹션의 정보는 Windows 방화벽에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-121">The information in the following section is specific to windowsfirewall.</span></span> <span data-ttu-id="e4f4f-122">명령 프롬프트에서 명령을 실행하거나 Windows 방화벽 대화 상자에서 속성을 설정하여 Windows 방화벽 시스템을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-122">You can configure the windowsfirewall system by running a command at the command prompt, or by setting properties in the windowsfirewall dialog box.</span></span>  
  
 <span data-ttu-id="e4f4f-123">기본 Windows 방화벽 설정 방법과 데이터베이스 엔진, Analysis Services, Reporting Services 및 Integration Services에 영향을 주는 TCP 포트에 대한 설명은 [SQL Server 액세스를 허용하도록 Windows 방화벽 구성](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-123">For more information about the default windowsfirewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="configuring-a-windowsfirewall"></a><span data-ttu-id="e4f4f-124">Windows 방화벽 구성</span><span class="sxs-lookup"><span data-stu-id="e4f4f-124">Configuring a windowsfirewall</span></span>  
 <span data-ttu-id="e4f4f-125">다음 명령을 사용하면 TCP 포트 135를 열고, 예외 목록에 MsDtsSrvr.exe를 추가하고, 방화벽에 대한 차단 해제 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-125">You can use the following commands to open TCP port 135, add MsDtsSrvr.exe to the exception list, and specify the scope of unblocking for the firewall.</span></span>  
  
#### <a name="to-configure-a-windowsfirewall-using-the-command-prompt-window"></a><span data-ttu-id="e4f4f-126">명령 프롬프트 창을 사용하여 Windows 방화벽을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="e4f4f-126">To configure a windowsfirewall using the Command Prompt window</span></span>  
  
1.  <span data-ttu-id="e4f4f-127">`netsh firewall add portopening protocol=TCP port=135 name="RPC (TCP/135)" mode=ENABLE scope=SUBNET` 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-127">Run the command: `netsh firewall add portopening protocol=TCP port=135 name="RPC (TCP/135)" mode=ENABLE scope=SUBNET`</span></span>  
  
2.  <span data-ttu-id="e4f4f-128">`netsh firewall add allowedprogram program="%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.exe" name="SSIS Service" scope=SUBNET` 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-128">Run the command: `netsh firewall add allowedprogram program="%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.exe" name="SSIS Service" scope=SUBNET`</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e4f4f-129">모든 컴퓨터와 인터넷상의 컴퓨터에 대해서도 방화벽을 열려면 scope=SUBNET을 scope=ALL로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-129">To open the firewall for all computers, and also for computers on the Internet, replace scope=SUBNET with scope=ALL.</span></span>  
  
 <span data-ttu-id="e4f4f-130">다음 절차에서는 Windows 사용자 인터페이스를 사용하여 TCP 포트 135를 열고, 예외 목록에 MsDtsSrvr.exe를 추가하고, 방화벽에 대한 차단 해제 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-130">The following procedure describes how to use the Windows user interface to open TCP port 135, add MsDtsSrvr.exe to the exception list, and specify the scope of unblocking for the firewall.</span></span>  
  
#### <a name="to-configure-a-firewall-using-the-windowsfirewall-dialog-box"></a><span data-ttu-id="e4f4f-131">Windows 방화벽 대화 상자를 사용하여 방화벽을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="e4f4f-131">To configure a firewall using the windowsfirewall dialog box</span></span>  
  
1.  <span data-ttu-id="e4f4f-132">제어판에서 **Windows 방화벽**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-132">In the Control Panel, double-click **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="e4f4f-133">**Windows 방화벽** 대화 상자에서 **예외** 탭을 클릭한 다음 **프로그램 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-133">In the **Windows Firewall** dialog box, click the **Exceptions** tab and then click **Add Program.**</span></span>  
  
3.  <span data-ttu-id="e4f4f-134">**프로그램 추가** 대화 상자에서 **찾아보기**를 클릭하고 Program Files\Microsoft SQL Server\100\DTS\Binn 폴더로 이동한 다음 MsDtsSrvr.exe를 클릭하고 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-134">In the **Add a Program** dialog box, **click Browse**, navigate to the Program Files\Microsoft SQL Server\100\DTS\Binn folder, click MsDtsSrvr.exe, and then click **Open**.</span></span> <span data-ttu-id="e4f4f-135">**확인** 을 클릭하여 **프로그램 추가** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-135">Click **OK** to close the **Add a Program** dialog box.</span></span>  
  
4.  <span data-ttu-id="e4f4f-136">**예외** 탭에서 **포트 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-136">On the **Exceptions** tab, click **Add Port.**</span></span>  
  
5.  <span data-ttu-id="e4f4f-137">**포트 추가** 대화 상자의 **이름** 상자에 **RPC(TCP/135)** 나 다른 설명이 포함된 이름을 입력하고 **포트 번호** 상자에 **135** 를 입력한 다음 **TCP**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-137">In the **Add a Port** dialog box, type **RPC(TCP/135)** or another descriptive name in the **Nam**e box, type **135** in the **Port Number** box, and then select **TCP**.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e4f4f-138">서비스는 항상 포트 135를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-138">service always uses port 135.</span></span> <span data-ttu-id="e4f4f-139">다른 포트를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-139">You cannot specify a different port.</span></span>  
  
6.  <span data-ttu-id="e4f4f-140">**포트 추가** 대화 상자에서는 선택적으로 **범위 변경** 을 클릭하여 기본 범위를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-140">In the **Add a Port** dialog box, you can optionally click **Change Scope** to modify the default scope.</span></span>  
  
7.  <span data-ttu-id="e4f4f-141">**범위 변경** 대화 상자에서 **내 네트워크(서브넷 전용)** 을 선택하거나 사용자 지정 목록을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-141">In the **Change Scope** dialog box, select **My network (subnet only)** or type a custom list, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="e4f4f-142">**확인** 을 클릭하여 **포트 추가**대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-142">To close the **Add a Port** dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="e4f4f-143">**Windows 방화벽** 대화 상자를 닫으려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-143">To close the **Windows Firewall** dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e4f4f-144">Windows 방화벽을 구성하려면 이 절차에서 제어판의 **Windows 방화벽** 항목을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-144">To configure the windowsfirewall, this procedure uses the **Windows Firewall** item in Control Panel.</span></span> <span data-ttu-id="e4f4f-145">**Windows 방화벽** 항목은 현재 네트워크 위치 프로필에 대한 방화벽만 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-145">The **Windows Firewall** item only configures the firewall for the current network location profile.</span></span> <span data-ttu-id="e4f4f-146">그러나 **netsh** 명령줄 도구 또는 고급 보안이 설정된 Windows 방화벽 MMC( [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console) 스냅인을 사용하여 Windows 방화벽을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-146">However, you can also configure the windowsfirewall by using the **netsh** command line tool or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (MMC) snap-in named windowsfirewall with Advanced Security.</span></span> <span data-ttu-id="e4f4f-147">이러한 도구에 대한 자세한 내용은 [SQL Server 액세스를 허용하도록 Windows 방화벽 구성](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4f4f-147">For more information about these tools, see [Configure the Windows Firewall to Allow SQL Server Access](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f4f-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4f4f-148">See Also</span></span>  
 <span data-ttu-id="e4f4f-149">[Integration Services Service &#40;SSIS 서비스&#41;구성](service/integration-services-service-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="e4f4f-149">[Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md) </span></span>  
 [<span data-ttu-id="e4f4f-150">Integration Services 서비스&#40;SSIS 서비스&#41;</span><span class="sxs-lookup"><span data-stu-id="e4f4f-150">Integration Services Service &#40;SSIS Service&#41;</span></span>](service/integration-services-service-ssis-service.md)  
  
  
