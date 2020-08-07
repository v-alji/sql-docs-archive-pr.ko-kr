---
title: 보고서 서버에서 Windows 인증 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [Reporting Services]
- Reporting Services, configuration
ms.assetid: 4de9c3dd-0ee7-49b3-88bb-209465ca9d86
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 879c036977f9a34528dbf38e42fa080e72617a14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731411"
---
# <a name="configure-windows-authentication-on-the-report-server"></a><span data-ttu-id="0a046-102">보고서 서버의 Windows 인증 구성</span><span class="sxs-lookup"><span data-stu-id="0a046-102">Configure Windows Authentication on the Report Server</span></span>
  <span data-ttu-id="0a046-103">기본적으로 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 Negotiate 또는 NTLM 인증을 지정하는 요청을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-103">By default, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] accepts requests that specify Negotiate or NTLM authentication.</span></span> <span data-ttu-id="0a046-104">배포에 이러한 보안 공급자를 사용하는 클라이언트 애플리케이션 및 브라우저가 포함된 경우 추가 구성 없이 기본값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-104">If your deployment includes client applications and browsers that use these security providers, you can use the default values without additional configuration.</span></span> <span data-ttu-id="0a046-105">Windows 통합 보안을 위해 다른 보안 공급자를 사용하거나(예: Kerberos를 직접 사용하려는 경우) 기본값을 수정하고 원래 설정을 복원하려는 경우 이 항목의 정보를 사용하여 보고서 서버에서 인증 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-105">If you want to use a different security provider for Windows integrated security (for example, if you want to use Kerberos directly), or if you modified the default values and want to restore the original settings, you can use the information in this topic to specify authentication settings on the report server.</span></span>  
  
 <span data-ttu-id="0a046-106">Windows 통합 보안을 사용하려면 보고서 서버에 액세스해야 하는 각 사용자가 유효한 Windows 로컬 또는 도메인 사용자 계정을 보유하고 있거나 Windows 로컬 또는 도메인 그룹 계정의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-106">To use Windows integrated security, each user who requires access to a report server must have a valid Windows local or domain user account or be a member of a Windows local or domain group account.</span></span> <span data-ttu-id="0a046-107">트러스트된 도메인에 한하여 다른 도메인의 계정을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-107">You can include accounts from other domains as long as those domains are trusted.</span></span> <span data-ttu-id="0a046-108">이 계정은 보고서 서버 컴퓨터에 액세스할 수 있어야 하며 이후에 특정 보고서 서버 작업에 액세스할 수 있도록 역할에 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-108">The accounts must have access to the report server computer, and must be subsequently assigned to roles in order to gain access to specific report server operations.</span></span>  
  
 <span data-ttu-id="0a046-109">다음의 추가 요구 사항도 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-109">The following additional requirements must also be met:</span></span>  
  
-   <span data-ttu-id="0a046-110">RSeportServer.config 파일에서 `AuthenticationType`을 `RSWindowsNegotiate`, `RSWindowsKerberos` 또는 `RSWindowsNTLM`으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-110">The RSeportServer.config files must have `AuthenticationType` set to `RSWindowsNegotiate`, `RSWindowsKerberos`, or `RSWindowsNTLM`.</span></span> <span data-ttu-id="0a046-111">기본적으로 보고서 서버 서비스 계정이 NetworkService 또는 LocalSystem인 경우 RSReportServer.config 파일에는 `RSWindowsNegotiate` 설정이 들어 있습니다. 그렇지 않으면 `RSWindowsNTLM` 설정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-111">By default, the RSReportServer.config file includes the `RSWindowsNegotiate` setting if the Report Server service account is either NetworkService or LocalSystem; otherwise, the `RSWindowsNTLM` setting is used.</span></span> <span data-ttu-id="0a046-112">Kerberos 인증만 사용하는 애플리케이션이 있는 경우 `RSWindowsKerberos`를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-112">You can add `RSWindowsKerberos` if you have applications that only use Kerberos authentication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0a046-113">`RSWindowsNegotiate`를 사용할 경우 보고서 서버 서비스가 도메인 사용자 계정으로 실행되도록 구성하고 해당 계정의 SPN(서비스 사용자 이름)을 등록하지 않으면 Kerberos 인증 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-113">Using `RSWindowsNegotiate` will result in a Kerberos authentication error if you configured the Report Server service to run under a domain user account and you did not register a Service Principal Name (SPN) for the account.</span></span> <span data-ttu-id="0a046-114">자세한 내용은 이 항목의 [보고서 서버에 연결할 때 Kerberos 인증 오류 해결](#proxyfirewallRSWindowsNegotiate) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a046-114">For more information, see [Resolving Kerberos Authentication Errors When Connecting to a report server](#proxyfirewallRSWindowsNegotiate) in this topic.</span></span>  
  
-   [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="0a046-115">에는 Windows 인증을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-115">must be configured for Windows Authentication.</span></span> <span data-ttu-id="0a046-116">기본적으로 보고서 서버 웹 서비스 및 보고서 관리자에 대 한 Web.config 파일에는 \<authentication mode="Windows"> 설정이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-116">By default, the Web.config files for the Report Server Web service and Report Manager include the \<authentication mode="Windows"> setting.</span></span> <span data-ttu-id="0a046-117">로 변경 하는 경우 \<authentication mode="Forms"> 에 대 한 Windows 인증이 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-117">If you change it to \<authentication mode="Forms">, the Windows Authentication for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] will fail.</span></span>  
  
-   <span data-ttu-id="0a046-118">보고서 서버 웹 서비스 및 보고서 관리자에 대 한 Web.config 파일에는가 있어야 합니다 \<identity impersonate= "true" /> .</span><span class="sxs-lookup"><span data-stu-id="0a046-118">The Web.config files for the Report Server Web service and Report Manager must have \<identity impersonate= "true" />.</span></span>  
  
-   <span data-ttu-id="0a046-119">클라이언트 애플리케이션 또는 브라우저에서 Windows 통합 보안을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-119">The client application or browser must support Windows integrated security.</span></span>  
  
 <span data-ttu-id="0a046-120">보고서 서버 인증 설정을 변경하려면 RSReportServer.config 파일에서 XML 요소 및 값을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-120">To change the report server authentication settings, edit the XML elements and values in the RSReportServer.config file.</span></span> <span data-ttu-id="0a046-121">이 항목의 예를 복사하고 붙여 넣어 특정 조합을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-121">You can copy and paste the examples in this topic to implement specific combinations.</span></span>  
  
 <span data-ttu-id="0a046-122">모든 클라이언트 및 서버 컴퓨터가 동일한 도메인 또는 트러스트된 도메인에 있고 회사 방화벽을 통해 인트라넷으로 액세스되도록 보고서 서버가 배포된 경우 기본 설정이 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-122">The default settings work best if all client and server computers are in the same domain or in a trusted domain and the report server is deployed for intranet access behind a corporate firewall.</span></span> <span data-ttu-id="0a046-123">Windows 자격 증명을 전달하려면 트러스트된 단일 도메인이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-123">Trusted and single domains are a requirement for passing Windows credentials.</span></span> <span data-ttu-id="0a046-124">서버에 대해 Kerberos 버전 5 프로토콜을 사용하는 경우 자격 증명을 두 번 이상 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-124">Credentials can be passed more than one time if you enable the Kerberos version 5 protocol for your servers.</span></span> <span data-ttu-id="0a046-125">그렇지 않으면 만료 전까지 자격 증명을 한 번만 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-125">Otherwise, credentials can be passed only one time before they expire.</span></span> <span data-ttu-id="0a046-126">여러 컴퓨터 연결에 대해 자격 증명을 구성하는 방법에 대한 자세한 내용은 [보고서 데이터 원본에 대한 자격 증명 및 연결 정보 지정](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a046-126">For more information about configuring credentials for multiple computer connections, see [Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
 <span data-ttu-id="0a046-127">다음은 기본 모드 보고서 서버에 대한 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-127">The following instructions are intended for a native mode report server.</span></span> <span data-ttu-id="0a046-128">보고서 서버가 SharePoint 통합 모드로 배포된 경우 Windows 통합 보안을 지정하는 기본 인증 설정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-128">If the report server is deployed in SharePoint integrated mode, you must use the default authentication settings that specify Windows integrated security.</span></span> <span data-ttu-id="0a046-129">보고서 서버는 기본 Windows 인증 확장 프로그램의 내부 기능을 사용하여 SharePoint 통합 모드의 보고서 서버를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-129">The report server uses internal features in the default Windows Authentication extension to support report servers in SharePoint integrated mode.</span></span>  
  
## <a name="extended-protection-for-authentication"></a><span data-ttu-id="0a046-130">인증에 대한 확장된 보호</span><span class="sxs-lookup"><span data-stu-id="0a046-130">Extended Protection for Authentication</span></span>  
 <span data-ttu-id="0a046-131">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]부터는 인증에 대한 확장된 보호가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-131">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], support for Extended Protection for Authentication is available.</span></span> <span data-ttu-id="0a046-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능은 채널 바인딩 및 서비스 바인딩을 사용해 인증 보호를 향상시킬 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-132">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature supports the use of channel binding and service binding to enhance protection of authentication.</span></span> <span data-ttu-id="0a046-133">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능은 확장된 보호를 지원하는 운영 체제에서 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-133">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features need to be used with an operating system that supports Extended Protection.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="0a046-134">구성은 RSReportServer.config 파일의 설정에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-134">configuration for extended protection is determined by settings in the RSReportServer.config file.</span></span> <span data-ttu-id="0a046-135">이 파일은 WMI API를 사용하거나 파일을 편집하여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-135">The file can be updated by either editing the file or using WMI APIs.</span></span> <span data-ttu-id="0a046-136">자세한 내용은 [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a046-136">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md).</span></span>  
  
### <a name="to-configure-a-report-server-to-use-windows-integrated-security"></a><span data-ttu-id="0a046-137">Windows 통합 보안을 사용하도록 보고서 서버를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="0a046-137">To configure a report server to use Windows integrated security</span></span>  
  
1.  <span data-ttu-id="0a046-138">텍스트 편집기에서 RSReportServer.config를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-138">Open RSReportServer.config in a text editor.</span></span>  
  
2.  <span data-ttu-id="0a046-139"><`Authentication`>를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-139">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="0a046-140">다음 중 필요에 가장 맞는 XML 구조를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-140">Copy one of the following XML structures that best fits your needs.</span></span> <span data-ttu-id="0a046-141">`RSWindowsNegotiate`, `RSWindowsNTLM` 및 `RSWindowsKerberos`를 순서에 상관없이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-141">You can specify `RSWindowsNegotiate`, `RSWindowsNTLM`, and `RSWindowsKerberos` in any order.</span></span> <span data-ttu-id="0a046-142">각 개별 요청이 아닌 연결을 인증하려는 경우 인증 지속성을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-142">You should enable authentication persistence if you want to authenticate the connection rather than each individual request.</span></span> <span data-ttu-id="0a046-143">인증 지속성을 사용하면 인증이 필요한 모든 요청이 연결 기간 동안 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-143">Under authentication persistence, all requests that require authentication will be allowed for the duration of the connection.</span></span>  
  
     <span data-ttu-id="0a046-144">보고서 서버 서비스 계정이 NetworkService 또는 LocalSystem인 경우 첫 번째 XML 구조가 기본 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-144">The first XML structure is the default configuration when the Report Server service account is either NetworkService or LocalSystem:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsNegotiate />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     <span data-ttu-id="0a046-145">보고서 서버 서비스 계정이 NetworkService 또는 LocalSystem이 아닌 경우 두 번째 XML 구조가 기본 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-145">The second XML structure is the default configuration when the Report Server service account is not NetworkService or LocalSystem:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    ```  
  
     \</Authentication>  
  
     <span data-ttu-id="0a046-146">세 번째 XML 구조는 Windows 통합 보안에서 사용되는 모든 보안 패키지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-146">The third XML structure specifies all of the security packages that are used in Windows integrated security:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsNegotiate />  
                 <RSWindowsKerberos />  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
    ```  
  
     <span data-ttu-id="0a046-147">네 번째 XML 구조는 Kerberos를 지원하지 않는 배포에 대해서만 또는 Kerberos 인증 오류를 해결하기 위해 NTLM을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-147">The fourth XML structure specifies NTLM only for deployments that do not support Kerberos or to work around Kerberos authentication errors:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
    ```  
  
4.  <span data-ttu-id="0a046-148"><>의 기존 항목 위에 붙여넣습니다 `Authentication` .</span><span class="sxs-lookup"><span data-stu-id="0a046-148">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="0a046-149">`Custom` 유형에서는 `RSWindows`을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-149">Note that you cannot use `Custom` with the `RSWindows` types.</span></span>  
  
5.  <span data-ttu-id="0a046-150">확장된 보호에 적합하게 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-150">Modify as appropriate the settings for extended protection.</span></span> <span data-ttu-id="0a046-151">확장된 보호는 기본적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-151">Extended protection is disabled by default.</span></span>  <span data-ttu-id="0a046-152">이러한 항목이 없는 경우 현재 컴퓨터에서 확장된 보호를 지원하는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 실행 중이지 않은 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-152">If these entries are not present, the current computer may not be running a version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] which supports extended protection.</span></span> <span data-ttu-id="0a046-153">자세한 내용은 [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a046-153">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span></span>  
  
    ```  
          <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>  
          <RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionScenario>  
    ```  
  
6.  <span data-ttu-id="0a046-154">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-154">Save the file.</span></span>  
  
7.  <span data-ttu-id="0a046-155">스케일 아웃 배포를 구성한 경우 배포의 다른 보고서 서버에 대해 이러한 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-155">If you configured a scale-out deployment, repeat these steps for other report servers in the deployment.</span></span>  
  
8.  <span data-ttu-id="0a046-156">보고서 서버를 다시 시작하여 현재 열려 있는 모든 세션을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-156">Restart the report server to clear any sessions that are currently open.</span></span>  
  
##  <a name="resolving-kerberos-authentication-errors-when-connecting-to-a-report-server"></a><a name="proxyfirewallRSWindowsNegotiate"></a><span data-ttu-id="0a046-157">보고서 서버에 연결할 때 Kerberos 인증 오류 해결</span><span class="sxs-lookup"><span data-stu-id="0a046-157">Resolving Kerberos Authentication Errors When Connecting to a Report Server</span></span>  
 <span data-ttu-id="0a046-158">Negotiate 또는 Kerberos 인증용으로 구성된 보고서 서버에서 Kerberos 인증 오류가 발생하면 보고서 서버에 대한 클라이언트 연결이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-158">On a report server that is configured for Negotiate or Kerberos authentication, a client connection to the report server will fail if there is a Kerberos authentication error.</span></span> <span data-ttu-id="0a046-159">Kerberos 인증 오류는 다음과 같은 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-159">Kerberos authentication errors are known to occur when:</span></span>  
  
-   <span data-ttu-id="0a046-160">보고서 서버 서비스가 Windows 도메인 사용자 계정으로 실행되는데 해당 계정의 SPN(서비스 사용자 이름)을 등록하지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="0a046-160">The Report Server service runs as a Windows domain user account and you did not register a Service Principal Name (SPN) for the account.</span></span>  
  
-   <span data-ttu-id="0a046-161">보고서 서버가 `RSWindowsNegotiate` 설정으로 구성된 경우</span><span class="sxs-lookup"><span data-stu-id="0a046-161">The report server is configured with the `RSWindowsNegotiate` setting.</span></span>  
  
-   <span data-ttu-id="0a046-162">브라우저가 보고서 서버에 보내는 요청의 인증 헤더에서 NTLM 대신 Kerberos를 선택하는 경우</span><span class="sxs-lookup"><span data-stu-id="0a046-162">The browser chooses Kerberos over NTLM in the authentication header in the request it sends to the report server.</span></span>  
  
 <span data-ttu-id="0a046-163">Kerberos 로깅을 사용하는 경우 오류를 감지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-163">You can detect the error if you enabled Kerberos logging.</span></span> <span data-ttu-id="0a046-164">자격 증명을 요청하는 메시지가 여러 번 표시된 다음 빈 브라우저 창이 표시되는 것도 오류의 다른 증상입니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-164">Another symptom of the error is that you are prompted for credentials multiple times and then see an empty browser window.</span></span>  
  
 <span data-ttu-id="0a046-165">`RSWindowsNegotiate`구성 파일에서 </>를 제거 하 고 연결을 다시 시도 하 여 Kerberos 인증 오류가 발생 하 고 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-165">You can confirm that you are encountering a Kerberos authentication error by removing < `RSWindowsNegotiate` /> from your configuration file and reattempting the connection.</span></span>  
  
 <span data-ttu-id="0a046-166">문제를 확인한 후에는 다음과 같은 방법으로 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-166">After you confirm the problem, you can address it in the following ways:</span></span>  
  
-   <span data-ttu-id="0a046-167">도메인 사용자 계정으로 실행되는 보고서 서버 서비스의 SPN을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-167">Register an SPN for the Report Server service under the domain user account.</span></span> <span data-ttu-id="0a046-168">자세한 내용은 [보고서 서버의 SPN&#40;서비스 사용자 이름&#41; 등록](../report-server/register-a-service-principal-name-spn-for-a-report-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a046-168">For more information, see [Register a Service Principal Name &#40;SPN&#41; for a Report Server](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).</span></span>  
  
-   <span data-ttu-id="0a046-169">서비스 계정이 네트워크 서비스와 같은 기본 제공 계정으로 실행되도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-169">Change the service account to run under a built-in account such as Network Service.</span></span> <span data-ttu-id="0a046-170">기본 제공 계정은 컴퓨터를 네트워크에 조인할 때 정의한 Host SPN에 HTTP SPN을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-170">Built-in accounts map HTTP SPN to the Host SPN, which is defined when you join a computer to your network.</span></span> <span data-ttu-id="0a046-171">자세한 내용은 [서비스 계정 구성&#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a046-171">For more information, see [Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).</span></span>  
  
-   <span data-ttu-id="0a046-172">NTLM을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-172">Use NTLM.</span></span> <span data-ttu-id="0a046-173">NTLM은 Kerberos 인증이 실패하는 경우에도 일반적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-173">NTLM will generally work in cases where Kerberos authentication fails.</span></span> <span data-ttu-id="0a046-174">NTLM을 사용하려면 RSReportServer.config 파일에서 `RSWindowsNegotiate`를 제거하고 `RSWindowsNTLM`만 지정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-174">To use NTLM, remove `RSWindowsNegotiate` from the RSReportServer.config file and verify that only `RSWindowsNTLM` is specified.</span></span> <span data-ttu-id="0a046-175">이 방법을 선택하는 경우 보고서 서버 서비스의 SPN을 정의하지 않아도 해당 서비스의 도메인 사용자 계정을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-175">If you choose this approach, you can continue to use a domain user account for the Report Server service even if you do not define an SPN for it.</span></span>  
  
#### <a name="logging-information"></a><span data-ttu-id="0a046-176">정보 로깅</span><span class="sxs-lookup"><span data-stu-id="0a046-176">Logging information</span></span>  
 <span data-ttu-id="0a046-177">다양한 로깅 정보 출처를 통해 Kerberos 관련 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-177">There are several sources of logging information that can help resolve Kerberos related issues.</span></span>  
  
##### <a name="user-account-control-attribute"></a><span data-ttu-id="0a046-178">UserAccountControl 특성</span><span class="sxs-lookup"><span data-stu-id="0a046-178">User-Account-Control Attribute</span></span>  
 <span data-ttu-id="0a046-179">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 계정이 Active Directory에서 충분한 특성 집합을 포함하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-179">Determine if the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account has the sufficient attribute set in Active Directory.</span></span> <span data-ttu-id="0a046-180">Reporting Services 서비스 추적 로그 파일을 검토하여 UserAccountControl 특성에 대해 기록되는 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-180">Review the reporting services service trace log file to find the value logged for the UserAccountControl attribute.</span></span> <span data-ttu-id="0a046-181">이 값은 10진수 형식으로 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-181">The value logged is in decimal form.</span></span> <span data-ttu-id="0a046-182">10진수 값을 16진수 형식으로 변환한 다음 UserAccountControl 특성에 대해 설명하는 MSDN 항목에서 해당 값을 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-182">You need to convert the decimal value to hexadecimal form and then find that value in the MSDN topic describing User-Account-Control Attribute.</span></span>  
  
-   <span data-ttu-id="0a046-183">Reporting Services 서비스 추적 로그 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-183">The reporting services service trace log entry will look similar to the following:</span></span>  
  
    ```  
    appdomainmanager!DefaultDomain!8f8!01/14/2010-14:42:28:: i INFO: The UserAccountControl value for the service account is 590336  
    ```  
  
-   <span data-ttu-id="0a046-184">10진수 값을 16진수 형식으로 변환하는 옵션 중 하나는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계산기를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-184">One option for converting the value Decimal value to hexadecimal form is to us the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Calculator.</span></span> <span data-ttu-id="0a046-185">Windows 계산기는 ‘Dec’ 옵션과 ‘Hex’ 옵션을 표시하는 여러 모드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-185">Windows Calculator supports several modes that show the 'Dec' option and 'Hex' options.</span></span> <span data-ttu-id="0a046-186">‘Dec’ 옵션을 선택하고 로그 파일에서 찾은 10진수 값을 붙여 넣거나 입력한 후에 ‘Hex’ 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-186">Select the 'Dec' option, paste or type in the decimal value you found in the log file and then select the 'Hex' option.</span></span>  
  
-   <span data-ttu-id="0a046-187">그런 다음 [User-Account-Control 특성](https://go.microsoft.com/fwlink/?LinkId=183366) 항목을 참조하여 서비스 계정의 특성을 파생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-187">Then refer to the topic [User-Account-Control Attribute](https://go.microsoft.com/fwlink/?LinkId=183366) to derive the attribute for the service account.</span></span>  
  
##### <a name="spns-configured-in-active-directory-for-the-reporting-services-service-account"></a><span data-ttu-id="0a046-188">Reporting Services 서비스 계정에 대해 Active Directory에서 구성된 SPN</span><span class="sxs-lookup"><span data-stu-id="0a046-188">SPNs Configured in Active Directory for the Reporting Services service account.</span></span>  
 <span data-ttu-id="0a046-189">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 추적 로그 파일에 SPN을 기록하려면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 확장된 보호 기능을 일시적으로 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-189">To log the SPNs in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service trace log file, you can enable the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Extended Protection feature temporarily.</span></span>  
  
-   <span data-ttu-id="0a046-190">다음을 설정하여 `rsreportserver.config` 구성 파일을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-190">Modify the configuration file `rsreportserver.config` by setting the following:</span></span>  
  
    ```  
    <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>   
    <RSWindowsExtendedProtectionScenario>Any</RSWindowsExtendedProtectionScenario>  
    ```  
  
-   <span data-ttu-id="0a046-191">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-191">Restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>

 <span data-ttu-id="0a046-192">확장된 보호를 계속 사용하지 않으려면 구성 값을 다시 기본값으로 설정하고 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 계정을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-192">If you do not want continue using Extended Protection, then set the configuration values back to defaults and restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service account.</span></span>  
  
```  
<RSWindowsExtendedProtectionLevel>Off</RSWindowsExtendedProtectionLevel>  
<RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionScenario>  
```  
  
 <span data-ttu-id="0a046-193">자세한 내용은 인증에 대한 확장된 보호를 참조 하세요 [Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="0a046-193">For more information see, [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span></span>  
  
#### <a name="how-the-browser-chooses-negotiated-kerberos-or-negotiated-ntlm"></a><span data-ttu-id="0a046-194">브라우저가 Negotiated Kerberos 또는 Negotiated NTLM을 선택하는 방법</span><span class="sxs-lookup"><span data-stu-id="0a046-194">How the Browser Chooses Negotiated Kerberos or Negotiated NTLM</span></span>  
 <span data-ttu-id="0a046-195">Internet Explorer를 사용하여 보고서 서버에 연결하는 경우 브라우저에서는 인증 헤더에 Negotiated Kerberos 또는 NTLM을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-195">When you use Internet Explorer to connect to the report server, it specifies either Negotiated Kerberos or NTLM on the authentication header.</span></span> <span data-ttu-id="0a046-196">NTLM은 다음과 같은 경우에 Kerberos 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-196">NTLM is used instead of Kerberos when:</span></span>  
  
-   <span data-ttu-id="0a046-197">요청을 로컬 보고서 서버로 보내는 경우</span><span class="sxs-lookup"><span data-stu-id="0a046-197">The request is sent to a local report server.</span></span>  
  
-   <span data-ttu-id="0a046-198">요청을 호스트 헤더 또는 서버 이름이 아닌 보고서 서버 컴퓨터의 IP 주소로 보내는 경우</span><span class="sxs-lookup"><span data-stu-id="0a046-198">The request is sent to an IP address of the report server computer rather than a host header or server name.</span></span>  
  
-   <span data-ttu-id="0a046-199">방화벽 소프트웨어가 Kerberos 인증에 사용되는 포트를 차단하는 경우</span><span class="sxs-lookup"><span data-stu-id="0a046-199">Firewall software blocks ports used for Kerberos authentication.</span></span>  
  
-   <span data-ttu-id="0a046-200">특정 서버의 운영 체제에서 Kerberos를 사용하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="0a046-200">The operating system of a particular server does not have Kerberos enabled.</span></span>  
  
-   <span data-ttu-id="0a046-201">최신 버전의 운영 체제에서 기본적으로 제공하는 Kerberos 인증 기능을 지원하지 않는 이전 버전의 Windows 클라이언트 및 서버 운영 체제가 도메인에 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="0a046-201">The domain includes older versions of Windows client and server operating systems that do not support the Kerberos authentication feature built into newer versions of the operating system.</span></span>  
  
 <span data-ttu-id="0a046-202">Internet Explorer는 URL, LAN 및 프록시 설정을 구성한 방법에 따라 Negotiated Kerberos 또는 NTLM을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-202">In addition, Internet Explorer might choose either Negotiated Kerberos or NTLM depending on how you configured URL, LAN, and proxy settings.</span></span>  
  
###### <a name="report-server-url"></a><span data-ttu-id="0a046-203">보고서 서버 URL</span><span class="sxs-lookup"><span data-stu-id="0a046-203">Report Server URL</span></span>  
 <span data-ttu-id="0a046-204">URL에 정규화된 도메인 이름이 포함된 경우 Internet Explorer는 NTLM을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-204">If the URL includes a fully qualified domain name, Internet Explorer selects NTLM.</span></span> <span data-ttu-id="0a046-205">URL에서 localhost를 지정하는 경우에도 Internet Explorer는 NTLM을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-205">If the URL specifies localhost, Internet Explorer selects NTLM.</span></span> <span data-ttu-id="0a046-206">URL에서 컴퓨터의 네트워크 이름을 지정하는 경우에는 Internet Explorer가 Negotiate를 선택합니다. 이 경우 보고서 서버 서비스 계정의 SPN이 있는지 여부에 따라 성공 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-206">If the URL specifies the network name of the computer, Internet Explorer selects Negotiate, which will succeed or fail depending on whether an SPN exists for the Report Server service account.</span></span>  
  
###### <a name="lan-and-proxy-settings-on-the-client"></a><span data-ttu-id="0a046-207">클라이언트에 대한 LAN 및 프록시 설정</span><span class="sxs-lookup"><span data-stu-id="0a046-207">LAN and Proxy Settings on the Client</span></span>  
 <span data-ttu-id="0a046-208">Internet Explorer에서 설정하는 LAN 및 프록시 설정에 따라 Kerberos 대신 NTLM이 선택되는지 여부가 결정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-208">LAN and proxy settings that you set in Internet Explorer can determine whether NTLM is chosen over Kerberos.</span></span> <span data-ttu-id="0a046-209">그러나 LAN 및 프록시 설정은 조직마다 다르므로 Kerberos 인증 오류에 영향을 주는 정확한 설정을 확인할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-209">However, because LAN and proxy settings vary across organizations, it is not possible to precisely determine the exact settings that contribute to Kerberos authentication errors.</span></span> <span data-ttu-id="0a046-210">예를 들어 사용자 조직에서 URL을 인트라넷 URL에서 인터넷 연결을 통해 확인되는 정규화된 도메인 이름 URL로 변환하는 프록시 설정을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-210">For example, your organization might enforce proxy settings that transform URLs from intranet URLs to fully-qualified domain name URLs that resolve over Internet connections.</span></span> <span data-ttu-id="0a046-211">URL 유형마다 서로 다른 인증 공급자를 사용하는 경우 실패할 것으로 예상한 일부 연결이 성공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-211">If different authentication providers are used for different types of URLs, you might find that some connections succeed when you would have expected them to fail.</span></span>  
  
 <span data-ttu-id="0a046-212">발생한 연결 오류가 인증 실패 때문인 것으로 판단되는 경우 다른 LAN 및 프록시 설정 조합을 시도하여 문제를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-212">If you encounter connection errors that you think are due to authentication failures, you can try different combinations of LAN and proxy settings to isolate the problem.</span></span> <span data-ttu-id="0a046-213">Internet Explorer에서 LAN 및 프록시 설정은 **인터넷 옵션** 의 **연결** 탭에서 **LAN 설정** 을 클릭하여 여는 **LAN 설정**대화 상자에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a046-213">In Internet Explorer, LAN and proxy settings are on the **Local Area Network (LAN) Settings** dialog box, which you open by clicking **LAN settings** on the **Connection** tab of **Internet Options**.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="0a046-214">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="0a046-214">External resources</span></span>  
  
-   <span data-ttu-id="0a046-215">Kerberos 및 보고서 서버에 대한 자세한 내용은 [Kerberos와 함께 SharePoint, Reporting Services 및 PerformancePoint Monitoring Server를 사용하여 비즈니스 인텔리전스 솔루션 배포(Deploying a Business Intelligence Solution Using SharePoint, Reporting Services, and PerformancePoint Monitoring Server with Kerberos)](https://go.microsoft.com/fwlink/?LinkID=177751)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a046-215">For additional information regarding Kerberos and report servers, see [Deploying a Business Intelligence Solution Using SharePoint, Reporting Services, and PerformancePoint Monitoring Server with Kerberos.](https://go.microsoft.com/fwlink/?LinkID=177751)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a046-216">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a046-216">See Also</span></span>  
 <span data-ttu-id="0a046-217">[보고서 서버 인증](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="0a046-217">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="0a046-218">[기본 모드 보고서 서버에 대한 사용 권한 부여](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="0a046-218">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="0a046-219">[Rsreportserver.config 구성 파일](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="0a046-219">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="0a046-220">[보고서 서버에서 기본 인증 구성](configure-basic-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="0a046-220">[Configure Basic Authentication on the Report Server](configure-basic-authentication-on-the-report-server.md) </span></span>  
 <span data-ttu-id="0a046-221">[보고서 서버에서 사용자 지정 또는 폼 인증 구성](configure-custom-or-forms-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="0a046-221">[Configure Custom or Forms Authentication on the Report Server](configure-custom-or-forms-authentication-on-the-report-server.md) </span></span>  
 [<span data-ttu-id="0a046-222">Reporting Services 인증에 대한 확장된 보호</span><span class="sxs-lookup"><span data-stu-id="0a046-222">Extended Protection for Authentication with Reporting Services</span></span>](extended-protection-for-authentication-with-reporting-services.md)  
  
  
