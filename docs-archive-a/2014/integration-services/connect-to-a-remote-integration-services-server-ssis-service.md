---
title: 원격 Integration Services 서버에 연결 (SSIS 서비스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], remote instance
- Integration Services service, connecting
- Integration Services service, remote instance
- service [Integration Services], connecting
ms.assetid: 9487aff1-44d8-42c1-8176-bb9891d4632d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03c9c4f1c94e4599c2c14f407996431dabd493dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738596"
---
# <a name="connect-to-a-remote-integration-services-server-ssis-service"></a><span data-ttu-id="69473-102">원격 Integration Services 서버에 연결(SSIS 서비스)</span><span class="sxs-lookup"><span data-stu-id="69473-102">Connect to a Remote Integration Services Server (SSIS Service)</span></span>
    
> [!IMPORTANT] 
> <span data-ttu-id="69473-103">이 항목에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 관리하는 Windows 서비스인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="69473-104">는 이전 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]버전과의 호환성을 위한 서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="69473-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]부터는 Integration Services 서버의 패키지와 같은 개체를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="69473-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 나 다른 관리 애플리케이션에서 원격 서버의 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 인스턴스에 연결하려면 애플리케이션 사용자에게 서버에 대한 특정 권한 집합이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-106">Connecting to an instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a remote server, from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or another management application, requires a specific set of rights on the server for the users of the application.</span></span>  
  
> [!IMPORTANT] 
> <span data-ttu-id="69473-107">원격 서버에 저장된 패키지를 관리하는 경우 해당 원격 서버에 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스 인스턴스에 연결할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-107">To manage packages that are stored on a remote server, you do not have to connect to the instance of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on that remote server.</span></span> <span data-ttu-id="69473-108">대신 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 원격 서버에 저장된 패키지를 표시하도록 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 서비스에 대한 구성 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-108">Instead, edit the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service so that [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] displays the packages that are stored on the remote server.</span></span> <span data-ttu-id="69473-109">자세한 내용은 [Integration Services 서비스 구성&#40;SSIS 서비스&#41;](service/integration-services-service-ssis-service.md)버전과의 호환성을 위한 서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-109">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span>  
  
## <a name="connecting-to-integration-services-on-a-remote-server"></a><span data-ttu-id="69473-110">원격 서버의 Integration Services에 연결</span><span class="sxs-lookup"><span data-stu-id="69473-110">Connecting to Integration Services on a Remote Server</span></span>  
  
#### <a name="to-connect-to-integration-services-on-a-remote-server"></a><span data-ttu-id="69473-111">원격 서버의 Integration Services에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="69473-111">To connect to Integration Services on a Remote Server</span></span>  
  
1.  <span data-ttu-id="69473-112">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="69473-112">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="69473-113">**파일**, **개체 탐색기 연결** 을 차례로 선택하여 **서버에 연결** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-113">Select **File**, **Connect Object Explorer** to display the **Connect to Server** dialog box.</span></span>  
  
3.  <span data-ttu-id="69473-114">**서버 유형** 목록에서 **Integration Services** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-114">Select **Integration Services** in the **Server type** list.</span></span>  
  
4.  <span data-ttu-id="69473-115">**서버 이름** 텍스트 상자에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-115">Type the name of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server in the **Server name** text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="69473-116">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스는 인스턴스에 국한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-116">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is not instance-specific.</span></span> <span data-ttu-id="69473-117">Integration Services 서버가 실행 중인 컴퓨터의 이름을 사용하여 서비스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-117">You connect to the service by using the name of the computer on which the Integration Services service is running.</span></span>  
  
5.  <span data-ttu-id="69473-118">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-118">Click **Connect**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69473-119">**서버 찾아보기** 대화 상자에는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]의 원격 인스턴스가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-119">The **Browse for Servers** dialog box does not display remote instances of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="69473-120">또한 **옵션** 단추를 클릭하면 표시되는 **서버에 연결** 대화 상자의 **연결 옵션** 탭에서 사용할 수 있는 옵션은 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 연결에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-120">In addition, the options available on the **Connection Options** tab of the **Connect to Server** dialog box, which is displayed by clicking the **Options** button, are not applicable to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] connections.</span></span>  
  
## <a name="eliminating-the-access-is-denied-error"></a><span data-ttu-id="69473-121">"액세스가 거부되었습니다." 오류 제거</span><span class="sxs-lookup"><span data-stu-id="69473-121">Eliminating the "Access Is Denied" Error</span></span>  
 <span data-ttu-id="69473-122">충분한 권한이 없는 사용자가 원격 서버의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 인스턴스에 연결하려고 하면 "액세스가 거부되었습니다."라는 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="69473-122">When a user without sufficient rights attempts to connect to an instance of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a remote server, the server responds with an "Access is denied" error message.</span></span> <span data-ttu-id="69473-123">사용자에게 필요한 DCOM 권한을 부여하면 이 오류 메시지를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-123">You can avoid this error message by ensuring that users have the required DCOM permissions.</span></span>  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-server-2003-or-windows-xp"></a><span data-ttu-id="69473-124">Windows Server 2003 또는 Windows XP에서 원격 사용자의 권한을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="69473-124">To configure rights for remote users on Windows Server 2003 or Windows XP</span></span>  
  
1.  <span data-ttu-id="69473-125">사용자가 로컬 Administrators 그룹의 멤버가 아니면 분산 COM 사용자 그룹에 해당 사용자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-125">If the user is not a member of the local Administrators group, add the user to the Distributed COM Users group.</span></span> <span data-ttu-id="69473-126">이 작업은 **관리 도구** 메뉴에서 액세스할 수 있는 컴퓨터 관리 MMC 스냅인에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-126">You can do this in the Computer Management MMC snap-in accessed from the **Administrative Tools** menu.</span></span>  
  
2.  <span data-ttu-id="69473-127">제어판을 열고 **관리 도구** 를 두 번 클릭한 다음 **구성 요소 서비스** 를 두 번 클릭하여 구성 요소 서비스 MMC 스냅인을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-127">Open Control Panel, double-click **Administrative Tools,** and then double-click **Component Services** to start the Component Services MMC snap-in.</span></span>  
  
3.  <span data-ttu-id="69473-128">콘솔의 왼쪽 창에서 **구성 요소 서비스** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-128">Expand the **Component Services** node in the left pane of the console.</span></span> <span data-ttu-id="69473-129">**컴퓨터** 노드를 확장하고 **내 컴퓨터**를 확장한 다음 **DCOM 구성** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-129">Expand the **Computers** node, expand **My Computer**, and then click the **DCOM Config** node.</span></span>  
  
4.  <span data-ttu-id="69473-130">**DCOM 구성** 노드를 선택하고 구성할 수 있는 애플리케이션 목록에서 SQL Server Integration Services 11.0을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-130">Select the **DCOM Config** node, and then select SQL Server Integration Services 11.0 in the list of applications that can be configured.</span></span>  
  
5.  <span data-ttu-id="69473-131">SQL Server Integration Services 11.0을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-131">Right-click on SQL Server Integration Services 11.0 and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="69473-132">**SQL Server Integration Services 11.0 속성** 대화 상자에서 **보안** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-132">In the **SQL Server Integration Services 11.0 Properties** dialog box, select the **Security** tab.</span></span>  
  
7.  <span data-ttu-id="69473-133">**시작 및 활성화 권한**에서 **사용자 지정**을 선택하고 **편집** 을 클릭하여 **시작 권한** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="69473-133">Under **Launch and Activation Permissions**, select **Customize**, then click **Edit** to open the **Launch Permission** dialog box.</span></span>  
  
8.  <span data-ttu-id="69473-134">**시작 권한** 대화 상자에서 사용자를 추가하거나 삭제하고 적절한 사용자 및 그룹에 적절한 권한을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-134">In the **Launch Permission** dialog box, add or delete users, and assign the appropriate permissions to the appropriate users and groups.</span></span> <span data-ttu-id="69473-135">로컬 시작, 원격 시작, 로컬 활성화 및 원격 활성화 권한을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-135">The available permissions are Local Launch, Remote Launch, Local Activation, and Remote Activation.</span></span> <span data-ttu-id="69473-136">시작 권한은 서비스를 시작 및 중지할 수 있는 권한을 부여하거나 거부하고, 활성화 권한은 서비스에 연결할 수 있는 권한을 부여하거나 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-136">The Launch rights grant or deny permission to start and stop the service; the Activation rights grant or deny permission to connect to the service.</span></span>  
  
9. <span data-ttu-id="69473-137">확인을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-137">Click OK to close the dialog box.</span></span>  
  
10. <span data-ttu-id="69473-138">**액세스 권한**에서 7-8단계를 반복하여 적절한 사용자 및 그룹에 적절한 권한을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-138">Under **Access Permissions**, repeat steps 7 and 8 to assign the appropriate permissions to the appropriate users and groups.</span></span>  
  
11. <span data-ttu-id="69473-139">MMC 스냅인을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-139">Close the MMC snap-in.</span></span>  
  
12. <span data-ttu-id="69473-140">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-140">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-2000-with-the-latest-service-packs"></a><span data-ttu-id="69473-141">Windows 2000 최신 서비스 팩에서 원격 사용자의 권한을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="69473-141">To configure rights for remote users on Windows 2000 with the latest service packs</span></span>  
  
1.  <span data-ttu-id="69473-142">명령 프롬프트에서 **dcomcnfg.exe** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-142">Run **dcomcnfg.exe** at the command prompt.</span></span>  
  
2.  <span data-ttu-id="69473-143">**DCOM 구성 속성** 대화 상자의 **애플리케이션** 페이지에서 SQL Server Integration Services 11.0을 선택하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-143">On the **Applications** page of the **Distributed COM Configuration Properties** dialog box, select SQL Server Integration Services 11.0 and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="69473-144">**보안** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-144">Select the **Security** page.</span></span>  
  
4.  <span data-ttu-id="69473-145">두 개의 개별 대화 상자를 사용하여 **액세스 권한** 과 **시작 권한**을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-145">Use the two separate dialog boxes to configure **Access Permissions** and **Launch Permissions**.</span></span> <span data-ttu-id="69473-146">원격 액세스와 로컬 액세스는 구별할 수 없습니다. 액세스 권한에는 로컬 및 원격 액세스가 포함되고 시작 권한에는 로컬 및 원격 시작이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="69473-146">You cannot distinguish between remote and local access - Access permissions include local and remote access, and Launch permissions include local and remote launch.</span></span>  
  
5.  <span data-ttu-id="69473-147">대화 상자 및 **dcomcnfg.exe**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-147">Close the dialog boxes and **dcomcnfg.exe**.</span></span>  
  
6.  <span data-ttu-id="69473-148">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-148">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
## <a name="connecting-by-using-a-local-account"></a><span data-ttu-id="69473-149">로컬 계정을 사용하여 연결</span><span class="sxs-lookup"><span data-stu-id="69473-149">Connecting by using a Local Account</span></span>  
 <span data-ttu-id="69473-150">클라이언트 컴퓨터에서 로컬 Windows 계정으로 작업하는 경우 동일한 이름 및 암호와 적절한 권한이 있는 로컬 계정이 원격 컴퓨터에 있는 경우에만 원격 컴퓨터의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-150">If you are working in a local Windows account on a client computer, you can connect to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service on a remote computer only if a local account that has the same name and password and the appropriate rights exists on the remote computer.</span></span>  
  
## <a name="by-default-the-ssis-service-does-not-support-delegation"></a><span data-ttu-id="69473-151">기본적으로 위임이 지원되지 않는 SSIS 서비스</span><span class="sxs-lookup"><span data-stu-id="69473-151">By default the SSIS service does not support delegation</span></span>  
<span data-ttu-id="69473-152">기본적으로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스는 자격 증명 위임을 지원 하지 않거나 이중 홉이 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-152">By default the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service does not support the delegation of credentials, or what is sometimes referred to as a double hop.</span></span> <span data-ttu-id="69473-153">이 시나리오에서는 클라이언트 컴퓨터에서 작업 중이고 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스가 두 번째 컴퓨터에서 실행 중이며 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 는 세 번째 컴퓨터에서 실행 중이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-153">In this scenario, you are working on a client computer, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is running on a second computer, and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running on a third computer.</span></span> <span data-ttu-id="69473-154">먼저 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 가 클라이언트 컴퓨터에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스가 실행 중인 두 번째 컴퓨터로 자격 증명을 성공적으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-154">First, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] successfully passes your credentials from the client computer to the second computer on which the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is running.</span></span> <span data-ttu-id="69473-155">그러나 그런 다음 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스는 두 번째 컴퓨터에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가 실행 중인 세 번째 컴퓨터에 자격 증명을 위임할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69473-155">Then, however, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service cannot delegate your credentials from the second computer to the third computer on which [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running.</span></span>

<span data-ttu-id="69473-156">SQL Server 서비스 계정에 **모든 서비스에 대한 위임용으로 이 사용자 트러스트(Kerberos만)** 권한을 부여하여 자격 증명을 위임할 수 있으며 하위 프로세스로 Integration Services 서비스(ISServerExec.exe)가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="69473-156">You can enable delegation of credentials by granting the **Trust this user for delegation to any service (Kerberos Only)** right to the SQL Server service account, which launches the Integration Services service (ISServerExec.exe) as a child process.</span></span> <span data-ttu-id="69473-157">이 권한을 부여하기 전에 조직의 보안 요구 사항을 충족하는지 여부를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69473-157">Before you grant this right, consider whether it meets the security requirements of your organization.</span></span>

<span data-ttu-id="69473-158">자세한 내용은 [Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/)(SSIS 패키지로 도메인 간 Kerberos 및 위임 가져오기)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69473-158">For more info, see [Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="69473-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69473-159">See Also</span></span>  
 [<span data-ttu-id="69473-160">SSIS 서비스 액세스에 대한 Windows 방화벽 구성</span><span class="sxs-lookup"><span data-stu-id="69473-160">Configure a Windows Firewall for Access to the SSIS Service</span></span>](../../2014/integration-services/configure-a-windows-firewall-for-access-to-the-ssis-service.md)  
  
  
