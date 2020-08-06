---
title: C2WTS (Windows 토큰 서비스에 대 한 클레임) 및 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/25/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cf2e245dfae17556bdb906c134ba0d53898a8631
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650506"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a><span data-ttu-id="8d6af-102">C2WTS(Windows 토큰 서비스에 대한 클레임) 및 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="8d6af-102">Claims to Windows Token Service (C2WTS) and Reporting Services</span></span>
  <span data-ttu-id="8d6af-103">The SharePoint Claims to Windows Token Service (c2WTS) is required with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드에 SharePoint C2WTS(Windows 토큰 서비스에 대한 클레임)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-103">The SharePoint Claims to Windows Token Service (c2WTS) is required with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode if you want to use windows authentication for Data Sources that are outside the SharePoint farm.</span></span> <span data-ttu-id="8d6af-104">특히 사용자가 Windows 인증을 사용하여 데이터 원본에 액세스할 경우라도 WFE(웹 프런트 엔드)와 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 공유 서비스 간의 통신은 항상 클레임 인증으로 수행되기 때문에 SharePoint C2WTS가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-104">This is true even if the user accesses the data sources with Windows Authentication because the communication between the web front-end (WFE) and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service will always be Claims authentication.</span></span>  
  
 <span data-ttu-id="8d6af-105">데이터 원본이 공유 서비스와 동일한 컴퓨터에 있더라도 c2WTS가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-105">c2WTS is needed even if your data source(s) are on the same computer as the shared service.</span></span> <span data-ttu-id="8d6af-106">하지만 이 경우에는 제한된 위임이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-106">However in this scenario, constrained delegation is not needed.</span></span>  
  
 <span data-ttu-id="8d6af-107">c2WTS에서 만들어진 토큰은 제한된 위임(특정 서비스로 제한됨)과 "모든 인증 프로토콜 사용" 구성 옵션에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-107">The tokens created by c2WTS will only work with constrained delegation (constrains to specific services) and the configuration option "using any authentication protocol".</span></span> <span data-ttu-id="8d6af-108">앞에서 설명한 것처럼 데이터 원본이 공유 서비스와 동일한 컴퓨터에 있으면 제한된 위임이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-108">As noted earlier, if your data sources are on the same computer as the shared service, then constrained delegation is not needed.</span></span>  
  
 <span data-ttu-id="8d6af-109">사용자 환경에서 Kerberos 제한된 위임을 사용하는 경우 SharePoint Server 서비스와 외부 데이터 원본이 동일한 Windows 도메인에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-109">If your environment will use Kerberos constrained delegation, then the SharePoint Server service and external data sources need to reside in the same Windows domain.</span></span> <span data-ttu-id="8d6af-110">c2WTS(Windows 토큰 서비스에 대한 클레임)를 사용하는 서비스는 c2WTS에서 Kerberos 프로토콜 전환을 사용하여 클레임을 Windows 자격 증명으로 변환할 수 있도록 Kerberos **제한된** 위임을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-110">Any service that relies on the Claims to Windows token service (c2WTS) must use Kerberos **constrained** delegation to allow c2WTS to use Kerberos protocol transition to translate claims into Windows credentials.</span></span> <span data-ttu-id="8d6af-111">이러한 요구 사항은 모든 SharePoint 공유 서비스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-111">These requirements are true for all SharePoint Shared Services.</span></span> <span data-ttu-id="8d6af-112">자세한 내용은 [Microsoft SharePoint 2010 제품에 대 한 Kerberos 인증 개요 ( https://technet.microsoft.com/library/gg502594.aspx) ](https://technet.microsoft.com/library/gg502594.aspx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d6af-112">For more information, see [Overview of Kerberos authentication for Microsoft SharePoint 2010 Products  (https://technet.microsoft.com/library/gg502594.aspx)](https://technet.microsoft.com/library/gg502594.aspx).</span></span>  
  
 <span data-ttu-id="8d6af-113">이 항목에 절차가 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-113">The procedure is summarized in this topic.</span></span>  
  
||  
|-|  
|<span data-ttu-id="8d6af-114">**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="8d6af-114">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="8d6af-115">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8d6af-115">Prerequisites</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d6af-116">참고: 일부 구성 단계는 특정 팜 토폴로지에 따라 변경될 수 있으며 작동하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-116">Note: Some of the configuration steps may change, or may not work in certain farm topologies.</span></span> <span data-ttu-id="8d6af-117">예를 들어 단일 서버 설치에는 Windows Identity Foundation c2WTS 서비스가 지원되지 않으므로 이 팜 구성에서는 Windows 토큰 위임에 대한 클레임 시나리오가 가능하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-117">For instance, a single server install does not support the Windows Identity Foundation c2WTS services so claims to windows token delegation scenarios are not possible with this farm configuration.</span></span>  
  
### <a name="basic-steps-needed-to-configure-c2wts"></a><span data-ttu-id="8d6af-118">c2WTS를 구성하기 위해 필요한 기본 단계</span><span class="sxs-lookup"><span data-stu-id="8d6af-118">Basic steps needed to configure c2WTS</span></span>  
  
1.  <span data-ttu-id="8d6af-119">c2WTS 서비스 계정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-119">Configure the c2WTS service account.</span></span> <span data-ttu-id="8d6af-120">c2WTS를 실행하는 각 애플리케이션 서버의 로컬 관리자 그룹에 서비스 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-120">Add the service account to the local Administrators group on each application server running c2WTS.</span></span> <span data-ttu-id="8d6af-121">또한 계정에 다음과 같은 로컬 보안 정책 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-121">In addition, verify that the account has the following local security policy rights:</span></span>  
  
    -   <span data-ttu-id="8d6af-122">운영 체제의 일부로 작동</span><span class="sxs-lookup"><span data-stu-id="8d6af-122">Act as part of the operating system</span></span>  
  
    -   <span data-ttu-id="8d6af-123">인증 후 클라이언트 가장</span><span class="sxs-lookup"><span data-stu-id="8d6af-123">Impersonate a client after authentication</span></span>  
  
    -   <span data-ttu-id="8d6af-124">서비스로 로그온</span><span class="sxs-lookup"><span data-stu-id="8d6af-124">Log on as a service</span></span>  
  
     <span data-ttu-id="8d6af-125">C2WTS에서 사용되는 계정은 프로토콜 전환을 포함하는 제한된 위임에 맞게 구성되어야 하며 통신해야 하는 서비스(예:SQL Server 엔진, SQL Server Analysis Services)에 대한 위임 권한이 필요합니다. 위임을 구성할 때는 Active Directory 사용자 및 컴퓨터 스냅인을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-125">The account you use for c2WTS also needs to be configured for Constrained Delegation with Protocol Transitioning and needs permissions to delegate to the Services it is required to communicate with (i.e. SQL Server Engine, SQL Server Analysis Services).To configure delegation you can use the Active Directory Users and Computer snap-in.</span></span>  
  
    1.  <span data-ttu-id="8d6af-126">각 서비스 계정을 마우스 오른쪽 단추로 클릭하고 속성 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-126">Right-click each service account and open the properties dialog.</span></span> <span data-ttu-id="8d6af-127">대화 상자에서 **위임** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-127">In the dialog click the **Delegation** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8d6af-128">참고: 개체에 SPN이 할당된 경우에만 위임 탭이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-128">Note: the delegation tab is only visible if the object has an SPN assigned to it.</span></span> <span data-ttu-id="8d6af-129">c2WTS에는 c2WTS 계정에 대 한 SPN이 필요 하지 않지만 SPN이 없으면 **위임** 탭이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-129">c2WTS does not require an SPN on the c2WTS Account, however, without an SPN, the **Delegation** tab will not be visible.</span></span> <span data-ttu-id="8d6af-130">제한된 위임을 구성하는 다른 방법으로는 **ADSIEdit**와 같은 유틸리티를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-130">An alternative way to configure constrained delegation is to use a utility such as **ADSIEdit**.</span></span>  
  
    2.  <span data-ttu-id="8d6af-131">위임 탭에 대한 키 구성 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-131">Key configuration options on the delegation tab are the following:</span></span>  
  
        -   <span data-ttu-id="8d6af-132">"지정한 서비스에 대 한 위임용 으로만이 사용자 트러스트"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-132">Select "Trust this user for delegation to specified services only"</span></span>  
  
        -   <span data-ttu-id="8d6af-133">"모든 인증 프로토콜 사용" 선택</span><span class="sxs-lookup"><span data-stu-id="8d6af-133">Select "Use any authentication protocol"</span></span>  
  
         <span data-ttu-id="8d6af-134">자세한 내용은 [SharePoint 2010 및 SQL Server 2008 R2 제품에 대 한 kerberos 인증 구성](https://docs.microsoft.com/archive/blogs/tothesharepoint/white-paper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products) 백서에서 "컴퓨터 및 서비스 계정에 대 한 kerberos 제한 된 위임 구성" 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8d6af-134">For more information, see the "configure Kerberos constrained delegation for computers and service accounts" section of the following white paper, [Configuring Kerberos authentication for SharePoint 2010 and SQL Server 2008 R2 products](https://docs.microsoft.com/archive/blogs/tothesharepoint/white-paper-configuring-kerberos-authentication-for-sharepoint-2010-and-sql-server-2008-r2-products)</span></span>  
  
2.  <span data-ttu-id="8d6af-135">C2WTS ' AllowedCallers ' 구성</span><span class="sxs-lookup"><span data-stu-id="8d6af-135">Configure c2WTS 'AllowedCallers'</span></span>  
  
     <span data-ttu-id="8d6af-136">c2WTS에는 **c2wtshost.exe.config**구성 파일에 명시적으로 나열 된 ' 호출자 ' id가 필요 합니다. c2WTS는이 작업을 수행 하도록 구성 되지 않은 한 시스템의 모든 인증 된 사용자 로부터의 요청을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-136">c2WTS requires the 'callers' identities explicitly listed in the configuration file, **c2wtshost.exe.config**. c2WTS does not accept requests from all authenticated users in the system unless it is configured to do so.</span></span> <span data-ttu-id="8d6af-137">이 경우 ‘caller’는 WSS_WPG Windows 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-137">In this case the 'caller' is the WSS_WPG Windows group.</span></span> <span data-ttu-id="8d6af-138">c2wtshost.exe.confi 파일은 다음 위치에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-138">The c2wtshost.exe.confi file is saved in the following location:</span></span>  
  
     <span data-ttu-id="8d6af-139">**Files\Windows Id Foundation\v3.5\c2wtshost.exe.config**</span><span class="sxs-lookup"><span data-stu-id="8d6af-139">**\Program Files\Windows Identity Foundation\v3.5\c2wtshost.exe.config**</span></span>  
  
     <span data-ttu-id="8d6af-140">다음은 구성 파일의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-140">The following is an example of the configuration file:</span></span>  
  
    ```  
    <configuration>  
      <windowsTokenService>  
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->  
        <allowedCallers>  
          <clear/>  
          <add value="WSS_WPG" />  
        </allowedCallers>  
      </windowsTokenService>  
    </configuration>  
    ```  
  
3.  <span data-ttu-id="8d6af-141">운영 체제의 C2WTS 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-141">Start the operating system c2WTS service:</span></span>  
  
    1.  <span data-ttu-id="8d6af-142">이전 단계에서 구성한 서비스 계정을 사용하도록 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-142">Configure the service to use the service account you configured in the previous step.</span></span>  
  
    2.  <span data-ttu-id="8d6af-143">시작 유형을 "**자동**"으로 변경 하 고 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-143">Change the Startup type to "**Automatic**" and start the service.</span></span>  
  
4.  <span data-ttu-id="8d6af-144">SharePoint ' Windows 토큰 서비스에 대 한 클레임 ' 시작: **서버의 서비스 관리** 페이지에서 Sharepoint 중앙 관리를 통해 Windows 토큰 서비스에 대 한 클레임을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-144">Start the SharePoint 'Claims to Windows Token Service': Start the Claims to Windows Token Service through SharePoint Central Administration on the **Manage Services on Server** page.</span></span> <span data-ttu-id="8d6af-145">서비스는 동작을 수행하는 서버에서 시작되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-145">The service should be started on the server that will be performing the action.</span></span> <span data-ttu-id="8d6af-146">예를 들어 WFE인 서버와 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 공유 서비스가 실행되는 애플리케이션 서버인 다른 서버가 있는 경우 애플리케이션 서버에서만 c2WTS를 시작하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-146">For example if you have a server that is a WFE and another server that is an Application Server that has the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service running, you only need to start c2WTS on the Application Server.</span></span> <span data-ttu-id="8d6af-147">WFE에는 c2WTS가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6af-147">c2WTS is not needed on the WFE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6af-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d6af-148">See Also</span></span>  
 <span data-ttu-id="8d6af-149">[C2WTS (Windows 토큰 서비스에 대 한 클레임) 개요 (https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx) </span><span class="sxs-lookup"><span data-stu-id="8d6af-149">[Claims to Windows Token Service (c2WTS) Overview (https://msdn.microsoft.com/library/ee517278.aspx)](https://msdn.microsoft.com/library/ee517278.aspx) </span></span>  
 [<span data-ttu-id="8d6af-150">Microsoft SharePoint 2010 제품에 대 한 Kerberos 인증 개요 (https://technet.microsoft.com/library/gg502594.aspx)</span><span class="sxs-lookup"><span data-stu-id="8d6af-150">Overview of Kerberos authentication for Microsoft SharePoint 2010 Products (https://technet.microsoft.com/library/gg502594.aspx)</span></span>](https://technet.microsoft.com/library/gg502594.aspx)  
  
