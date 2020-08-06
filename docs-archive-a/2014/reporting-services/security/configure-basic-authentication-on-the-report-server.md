---
title: 보고서 서버의 기본 인증 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- Basic authentication
ms.assetid: 8faf2938-b71b-4e61-a172-46da2209ff55
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07f860a67e02c3eb29c5af4f480d3817c55c507f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648263"
---
# <a name="configure-basic-authentication-on-the-report-server"></a><span data-ttu-id="892a7-102">보고서 서버에서 기본 인증 구성</span><span class="sxs-lookup"><span data-stu-id="892a7-102">Configure Basic Authentication on the Report Server</span></span>
  <span data-ttu-id="892a7-103">기본적으로 Reporting Services는 Negotiate 및 NTLM 인증을 지정하는 요청을 수락합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-103">By default, Reporting Services accepts requests that specify Negotiate and NTLM authentication.</span></span> <span data-ttu-id="892a7-104">현재 배포에 기본 인증을 사용하는 클라이언트 애플리케이션 또는 브라우저가 포함된 경우 지원되는 유형 목록에 기본 인증을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-104">If your deployment includes client applications or browsers that use Basic authentication, you must add Basic authentication to the list of supported types.</span></span> <span data-ttu-id="892a7-105">또한 보고서 작성기를 사용하려면 보고서 작성기 파일에 대한 익명 액세스를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-105">In addition, if you want to use Report Builder, you must enable Anonymous access to the Report Builder files.</span></span>  
  
 <span data-ttu-id="892a7-106">보고서 서버에 기본 인증을 구성하려면 RSReportServer.config 파일의 XML 요소 및 값을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-106">To configure Basic authentication on the report server, you edit XML elements and values in the RSReportServer.config file.</span></span> <span data-ttu-id="892a7-107">이 항목의 예를 복사하고 붙여넣어 기본값을 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-107">You can copy and paste the examples in this topic to replace the default values.</span></span>  
  
 <span data-ttu-id="892a7-108">기본 인증을 설정하기 전에 보안 인프라에서 기본 인증을 지원하는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="892a7-108">Before you enable Basic authentication, verify that your security infrastructure supports it.</span></span> <span data-ttu-id="892a7-109">기본 인증에서 보고서 서버 웹 서비스는 로컬 보안 기관에 자격 증명을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-109">Under Basic authentication, the Report Server Web service will pass credentials to the local security authority.</span></span> <span data-ttu-id="892a7-110">자격 증명이 로컬 사용자 계정을 지정하는 경우 사용자는 보고서 서버 컴퓨터의 로컬 보안 기관에 의해 인증되며 로컬 리소스에 대해 유효한 보안 토큰을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-110">If the credentials specify a local user account, the user is authenticated by the local security authority on the report server computer and the user will get a security token that is valid for local resources.</span></span> <span data-ttu-id="892a7-111">도메인 사용자 계정에 대한 자격 증명은 도메인 컨트롤러로 전달되어 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-111">Credentials for domain user accounts are forwarded to and authenticated by a domain controller.</span></span> <span data-ttu-id="892a7-112">인증 후 발급되는 티켓은 네트워크 리소스에 대해 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-112">The resulting ticket is valid for network resources.</span></span>  
  
 <span data-ttu-id="892a7-113">자격 증명이 네트워크의 도메인 컨트롤러로 전송되는 동안 도청될 위험을 완화하려면 SSL(Secure Sockets Layer)과 같은 채널 암호화가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-113">Channel encryption, such as Secure Sockets Layer (SSL), is required if you want to mitigate the risk of having credentials intercepted while in transit to a domain controller in your network.</span></span> <span data-ttu-id="892a7-114">기본 인증은 자체적으로 사용자 이름을 일반 텍스트로, 암호는 Base-64 인코딩으로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-114">By itself, Basic authentication transmits the user name in clear text and the password in base-64 encoding.</span></span> <span data-ttu-id="892a7-115">채널 암호화를 추가하면 패킷을 읽기가 불가능하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-115">Adding channel encryption makes the packet unreadable.</span></span> <span data-ttu-id="892a7-116">자세한 내용은 [기본 모드 보고서 서버에서 SSL 연결 구성](configure-ssl-connections-on-a-native-mode-report-server.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="892a7-116">For more information, see [Configure SSL Connections on a Native Mode Report Server](configure-ssl-connections-on-a-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="892a7-117">기본 인증을 설정한 다음에는 보고서에 데이터를 제공하는 외부 데이터 원본에 대한 연결 속성을 설정할 때 사용자가 **Windows 통합 보안** 옵션을 선택할 수 없다는 점을 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="892a7-117">After you enable Basic authentication, be aware that users cannot select the **Windows integrated security** option when setting connection properties to an external data source that provides data to a report.</span></span> <span data-ttu-id="892a7-118">이 옵션은 데이터 원본 속성 페이지에서 회색으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-118">The option will be grayed out in the data source property pages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="892a7-119">다음은 기본 모드 보고서 서버에 대한 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-119">The following instructions are intended for a native mode report server.</span></span> <span data-ttu-id="892a7-120">보고서 서버가 SharePoint 통합 모드로 배포된 경우 Windows 통합 보안을 지정하는 기본 인증 설정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-120">If the report server is deployed in SharePoint integrated mode, you must use the default authentication settings that specify Windows integrated security.</span></span> <span data-ttu-id="892a7-121">보고서 서버는 기본 Windows 인증 확장 프로그램의 내부 기능을 사용하여 SharePoint 통합 모드의 보고서 서버를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-121">The report server uses internal features in the default Windows Authentication extension to support report server in SharePoint integrated mode.</span></span>  
  
### <a name="to-configure-a-report-server-to-use-basic-authentication"></a><span data-ttu-id="892a7-122">기본 인증을 사용하도록 보고서 서버를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="892a7-122">To configure a report server to use Basic authentication</span></span>  
  
1.  <span data-ttu-id="892a7-123">텍스트 편집기에서 RSReportServer.config를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-123">Open RSReportServer.config in a text editor.</span></span>  
  
     <span data-ttu-id="892a7-124">파일은: Files\Microsoft SQL Server\MSRS12.에 있습니다 \* \<drive> .\* MSSQLSERVER\Reporting Services\reportserver</span><span class="sxs-lookup"><span data-stu-id="892a7-124">The file is located at *\<drive>:* \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer.</span></span>  
  
2.  <span data-ttu-id="892a7-125"><`Authentication`>를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-125">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="892a7-126">다음 중 필요에 가장 맞는 XML 구조를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-126">Copy one of the following XML structures that best fits your needs.</span></span> <span data-ttu-id="892a7-127">첫 번째 XML 구조는 다음 섹션에 설명되어 있는 모든 요소를 지정하기 위한 자리 표시자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-127">The first XML structure provides placeholders for specifying all of the elements, which are described in the next section:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsBasic>  
                       <LogonMethod>3</LogonMethod>  
                       <Realm></Realm>  
                       <DefaultDomain></DefaultDomain>  
                 </RSWindowsBasic>  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     <span data-ttu-id="892a7-128">기본값을 사용하는 경우 최소 요소 구조를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-128">If you are using default values, you can copy the minimum element structure:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsBasic/>  
          </AuthenticationTypes>  
    ```  
  
4.  <span data-ttu-id="892a7-129"><>의 기존 항목 위에 붙여넣습니다 `Authentication` .</span><span class="sxs-lookup"><span data-stu-id="892a7-129">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="892a7-130">여러 인증 유형을 사용하는 경우 `RSWindowsBasic` 요소만 추가하고 `RSWindowsNegotiate`, `RSWindowsNTLM` 또는 `RSWindowsKerberos`에 대한 요소는 삭제하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="892a7-130">If you are using multiple authentication types, add just the `RSWindowsBasic` element but do not delete the entries for `RSWindowsNegotiate`, `RSWindowsNTLM`, or `RSWindowsKerberos`.</span></span>  
  
     <span data-ttu-id="892a7-131">Safari 브라우저를 지원하려는 경우에는 여러 인증 유형을 사용하도록 보고서 서버를 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-131">To support the Safari browser, you cannot configure the report server to use multiple authentication types.</span></span> <span data-ttu-id="892a7-132">`RSWindowsBasic`만 지정하고 다른 항목은 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-132">You must specify only `RSWindowsBasic` and delete the other entries.</span></span>  
  
     <span data-ttu-id="892a7-133">`Custom`은 다른 인증 유형과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-133">Note that you cannot use `Custom` with other authentication types.</span></span>  
  
5.  <span data-ttu-id="892a7-134"><> 또는 <>에 대 한 빈 값 `Realm` `DefaultDomain` 을 사용자 환경에 유효한 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-134">Replace empty values for <`Realm`> or <`DefaultDomain`> with values that are valid for your environment.</span></span>  
  
6.  <span data-ttu-id="892a7-135">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-135">Save the file.</span></span>  
  
7.  <span data-ttu-id="892a7-136">스케일 아웃 배포를 구성한 경우 배포의 다른 보고서 서버에 대해 이러한 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-136">If you configured a scale-out deployment, repeat these steps for other report servers in the deployment.</span></span>  
  
8.  <span data-ttu-id="892a7-137">보고서 서버를 다시 시작하여 현재 열려 있는 모든 세션을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-137">Restart the report server to clear any sessions that are currently open.</span></span>  
  
## <a name="rswindowsbasic-reference"></a><span data-ttu-id="892a7-138">RSWindowsBasic 참조</span><span class="sxs-lookup"><span data-stu-id="892a7-138">RSWindowsBasic Reference</span></span>  
 <span data-ttu-id="892a7-139">기본 인증을 구성할 때 다음 요소를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-139">The following elements can be specified when configuring Basic authentication.</span></span>  
  
|<span data-ttu-id="892a7-140">요소</span><span class="sxs-lookup"><span data-stu-id="892a7-140">Element</span></span>|<span data-ttu-id="892a7-141">필수</span><span class="sxs-lookup"><span data-stu-id="892a7-141">Required</span></span>|<span data-ttu-id="892a7-142">유효한 값</span><span class="sxs-lookup"><span data-stu-id="892a7-142">Valid Values</span></span>|  
|-------------|--------------|------------------|  
|<span data-ttu-id="892a7-143">LogonMethod</span><span class="sxs-lookup"><span data-stu-id="892a7-143">LogonMethod</span></span>|<span data-ttu-id="892a7-144">예</span><span class="sxs-lookup"><span data-stu-id="892a7-144">Yes</span></span><br /><br /> <span data-ttu-id="892a7-145">값을 지정하지 않으면 3이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-145">If you do not specify a value, 3 will be used.</span></span>|<span data-ttu-id="892a7-146">`2` = 일반 텍스트 암호를 인증하는 고성능 서버를 위한 네트워크 로그온입니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-146">`2` = Network logon, intended for high performance servers to authenticate plain text passwords.</span></span><br /><br /> <span data-ttu-id="892a7-147">`3` = 각 HTTP 요청과 함께 전송되는 인증 패키지에 로그온 자격 증명을 유지하여 서버가 네트워크의 다른 서버에 연결할 때 사용자를 가장할 수 있도록 하는 일반 텍스트 로그온입니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-147">`3` = Cleartext logon, which preserves logon credentials in the authentication package that is sent with each HTTP request, allowing the server to impersonate the user when connecting to other servers in the network.</span></span> <span data-ttu-id="892a7-148">(기본값)</span><span class="sxs-lookup"><span data-stu-id="892a7-148">(Default)</span></span><br /><br /> <span data-ttu-id="892a7-149">참고: 값 0(대화형 로그온) 및 1(일괄 처리 로그온)은 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-149">Note: Values 0 (for interactive logon) and 1 (for batch logon) are not supported in [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)].</span></span>|  
|<span data-ttu-id="892a7-150">Realm</span><span class="sxs-lookup"><span data-stu-id="892a7-150">Realm</span></span>|<span data-ttu-id="892a7-151">옵션</span><span class="sxs-lookup"><span data-stu-id="892a7-151">Optional</span></span>|<span data-ttu-id="892a7-152">조직의 보호된 리소스에 대한 액세스를 제어하는 데 사용되는 권한 부여 및 인증 기능이 포함된 리소스 파티션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-152">Specifies a resource partition that includes authorization and authentication features used to control access to protected resources in your organization.</span></span>|  
|<span data-ttu-id="892a7-153">DefaultDomain</span><span class="sxs-lookup"><span data-stu-id="892a7-153">DefaultDomain</span></span>|<span data-ttu-id="892a7-154">옵션</span><span class="sxs-lookup"><span data-stu-id="892a7-154">Optional</span></span>|<span data-ttu-id="892a7-155">사용자를 인증할 때 서버가 사용하는 도메인을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-155">Specifies the domain used by the server to authenticate the user.</span></span> <span data-ttu-id="892a7-156">이 값은 선택 사항이지만 생략하면 보고서 서버가 컴퓨터 이름을 도메인으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-156">This value is optional, but if you omit it the report server will use the computer name as the domain.</span></span> <span data-ttu-id="892a7-157">컴퓨터가 도메인 멤버인 경우 해당 도메인이 기본 도메인입니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-157">If the computer is a member of domain, that domain is the default domain.</span></span> <span data-ttu-id="892a7-158">도메인 컨트롤러에 보고서 서버를 설치한 경우에는 컴퓨터에서 제어되는 도메인이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-158">If you installed the report server on a domain controller, the domain used is the one controlled by the computer.</span></span>|  
  
## <a name="enabling-anonymous-access-to-report-builder-application-files"></a><span data-ttu-id="892a7-159">보고서 작성기 애플리케이션 파일에 대한 익명 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="892a7-159">Enabling Anonymous Access to Report Builder Application Files</span></span>  
 <span data-ttu-id="892a7-160">보고서 작성기는 ClickOnce 기술을 사용하여 해당 애플리케이션 파일을 클라이언트 컴퓨터로 다운로드하고 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-160">Report Builder uses ClickOnce technology to download and install application files on the client computer.</span></span> <span data-ttu-id="892a7-161">클라이언트 컴퓨터에서 시작된 ClickOnce 애플리케이션 실행 프로그램은 보고서 서버 컴퓨터의 추가 애플리케이션 파일을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-161">When it starts on the client computer, the ClickOnce application launcher will make a request for additional application files on the report server computer.</span></span> <span data-ttu-id="892a7-162">보고서 서버가 기본 인증용으로 구성된 경우 ClickOnce 애플리케이션 실행 프로그램은 기본 인증을 지원하지 않으므로 인증 검사에 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-162">If the report server is configured for Basic authentication, the ClickOnce application launcher will fail the authentication check because it does not support Basic authentication.</span></span>  
  
 <span data-ttu-id="892a7-163">이 문제를 해결하려면 보고서 작성기 프로그램 파일에 대한 익명 액세스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-163">To work around this issue, you can configure Anonymous access to the Report Builder program files.</span></span> <span data-ttu-id="892a7-164">이렇게 하면 ClickOnce가 파일을 검색할 때 인증 검사를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-164">Doing so allows ClickOnce to bypass the authentication check when retrieving its files.</span></span> <span data-ttu-id="892a7-165">익명 액세스를 사용하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-165">Enable Anonymous access by doing the following:</span></span>  
  
-   <span data-ttu-id="892a7-166">보고서 서버가 기본 인증용으로 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-166">Verify that the report server is configured for Basic authentication.</span></span>  
  
-   <span data-ttu-id="892a7-167">ReportBuilder 아래에 bin 폴더를 만들고 4개의 어셈블리를 이 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-167">Create a bin folder under ReportBuilder and copy four assemblies to the folder.</span></span>  
  
-   <span data-ttu-id="892a7-168">RSReportServer.config에 `IsReportBuilderAnonymousAccessEnabled` 요소를 추가하고 `True`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-168">Add the `IsReportBuilderAnonymousAccessEnabled` element to the RSReportServer.config and set it to `True`.</span></span> <span data-ttu-id="892a7-169">파일을 저장하면 보고서 서버가 보고서 작성기에 대한 새 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-169">After you save the file, the report server creates a new endpoint to Report Builder.</span></span> <span data-ttu-id="892a7-170">이 엔드포인트는 프로그램 파일에 액세스하기 위해 내부적으로 사용되며 코드에서 사용할 수 있는 프로그래밍 인터페이스는 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-170">The endpoint is used internally to access program files and does not have a programmatic interface that you can use in code.</span></span> <span data-ttu-id="892a7-171">별도의 엔드포인트를 통해 보고서 작성기는 보고서 서버 서비스 프로세스 경계 내에 자체 애플리케이션 도메인을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-171">Having a separate endpoint allows Report Builder to run in its own application domain within the Report Server service process boundary.</span></span>  
  
-   <span data-ttu-id="892a7-172">필요에 따라 최소 권한 계정을 지정하여 보고서 서버와 다른 보안 컨텍스트에서 요청을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-172">Optionally, you can specify a least-privilege account to process requests under a security context that is different from the report server.</span></span> <span data-ttu-id="892a7-173">이 계정은 보고서 서버의 보고서 작성기 파일에 액세스하기 위한 익명 계정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-173">This account becomes the anonymous account for accessing Report Builder files on a report server.</span></span> <span data-ttu-id="892a7-174">이 계정은 ASP.NET 작업자 프로세스에 있는 스레드의 ID를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-174">The account sets the identity of the thread in the ASP.NET worker process.</span></span> <span data-ttu-id="892a7-175">이 스레드에서 실행되는 요청은 인증 검사 없이 보고서 서버로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-175">Requests that run in that thread are passed to the report server without an authentication check.</span></span> <span data-ttu-id="892a7-176">이 계정은 \<machine> 익명 액세스 및 가장이 사용 되는 경우 ASP.NET worker 프로세스에 대 한 보안 컨텍스트를 설정 하는 데 사용 되는 인터넷 정보 서비스 (IIS)의 IUSR_ 계정에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-176">This account is equivalent to the IUSR_\<machine> account in Internet Information Services (IIS), which is used to set the security context for ASP.NET worker processes when Anonymous access and impersonation are enabled.</span></span> <span data-ttu-id="892a7-177">계정을 지정하려면 보고서 작성기 Web.config 파일에 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-177">To specify the account, you add it to a Report Builder Web.config file.</span></span>  
  
 <span data-ttu-id="892a7-178">보고서 작성기 프로그램 파일에 대한 익명 액세스를 사용하려면 보고서 서버를 기본 인증용으로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-178">The report server must be configured for Basic authentication if you want to enable Anonymous access to the Report Builder program files.</span></span> <span data-ttu-id="892a7-179">보고서 서버가 기본 인증으로 구성되지 않은 경우 익명 액세스를 허용하려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-179">If the report server is not configured for Basic authentication, you will get an error when you attempt to enable Anonymous access.</span></span>  
  
 <span data-ttu-id="892a7-180">인증 문제 및 보고서 작성기에 대한 자세한 내용은 [보고서 작성기 액세스 구성](../report-server/configure-report-builder-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="892a7-180">For more information about authentication issues and Report Builder, see [Configure Report Builder Access](../report-server/configure-report-builder-access.md).</span></span>  
  
#### <a name="to-configure-report-builder-access-on-a-report-server-configured-for-basic-authentication"></a><span data-ttu-id="892a7-181">기본 인증용으로 구성된 보고서 서버에서 보고서 작성기 액세스를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="892a7-181">To configure Report Builder access on a report server configured for Basic authentication</span></span>  
  
1.  <span data-ttu-id="892a7-182">RSReportServer.config 파일의 인증 설정을 검사하여 보고서 서버가 기본 인증용으로 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-182">Verify the report server is configured for Basic authentication by checking the authentication settings in the RSReportServer.config file.</span></span>  
  
2.  <span data-ttu-id="892a7-183">ReportBuilder 폴더 아래에 bin 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-183">Create a BIN folder under the ReportBuilder folder.</span></span> <span data-ttu-id="892a7-184">기본적으로 이 폴더의 위치는 \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\ReportBuilder입니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-184">By default, this folder is located at \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\ReportBuilder.</span></span>  
  
3.  <span data-ttu-id="892a7-185">ReportServer\Bin 폴더에서 다음 4개의 어셈블리를 ReportBuilder\BIN 폴더로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-185">Copy the following assemblies from the ReportServer\Bin folder to the ReportBuilder\BIN folder:</span></span>  
  
     <span data-ttu-id="892a7-186">Microsoft.ReportingServices.Diagnostics.dll</span><span class="sxs-lookup"><span data-stu-id="892a7-186">Microsoft.ReportingServices.Diagnostics.dll</span></span>  
  
     <span data-ttu-id="892a7-187">Microsoft.ReportingServices.Interfaces.dll</span><span class="sxs-lookup"><span data-stu-id="892a7-187">Microsoft.ReportingServices.Interfaces.dll</span></span>  
  
     <span data-ttu-id="892a7-188">ReportingServicesAppDomainManager.dll</span><span class="sxs-lookup"><span data-stu-id="892a7-188">ReportingServicesAppDomainManager.dll</span></span>  
  
     <span data-ttu-id="892a7-189">RSHttpRuntime.dll</span><span class="sxs-lookup"><span data-stu-id="892a7-189">RSHttpRuntime.dll</span></span>  
  
4.  <span data-ttu-id="892a7-190">필요에 따라 익명 계정에서 보고서 작성기 요청을 처리하기 위한 Web.config 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-190">Optionally, create a Web.config file to process Report Builder requests under an Anonymous account:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
    <system.web>  
    <authentication mode="Windows" />    
    <identity impersonate="true " userName="username" password="password"/>  
    </system.web>  
    </configuration>  
    ```  
  
     <span data-ttu-id="892a7-191">Web.config 파일을 포함하는 경우 인증 모드가 `Windows`로 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-191">Authentication mode must be set to `Windows` if you include a Web.config file.</span></span>  
  
     <span data-ttu-id="892a7-192">`Identity impersonate`은 `True` 또는 `False`가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-192">`Identity impersonate` can be `True` or `False`.</span></span>  
  
    -   <span data-ttu-id="892a7-193">ASP.NET에서 보안 토큰을 읽지 않도록 하려면 `False`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-193">Set it to `False` if you do not want ASP.NET to read the security token.</span></span> <span data-ttu-id="892a7-194">요청은 보고서 서버 서비스의 보안 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-194">The request will run in the security context of the Report Server service.</span></span>  
  
    -   <span data-ttu-id="892a7-195">ASP.NET이 호스트 계층에서 보안 토큰을 읽도록 하려면 `True`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-195">Set it to `True` if you want ASP.NET to read the security token from the host layer.</span></span> <span data-ttu-id="892a7-196">`True`로 설정하는 경우 `userName` 및 `password`도 지정하여 익명 계정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-196">If you set it to `True`, you must also specify `userName` and `password` to designate an Anonymous account.</span></span> <span data-ttu-id="892a7-197">지정하는 자격 증명은 요청이 실행되는 보안 컨텍스트를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-197">The credentials you specify will determine the security context under which the request is issued.</span></span>  
  
5.  <span data-ttu-id="892a7-198">Web.config 파일을 ReportBuilder\bin 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-198">Save the Web.config file to the ReportBuilder\bin folder.</span></span>  
  
6.  <span data-ttu-id="892a7-199">RSReportServer.config 파일을 열어 Services 섹션에서 `IsReportManagerEnabled`를 찾은 후 그 아래에 다음 설정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-199">Open RSReportServer.config file, in the Services section, find `IsReportManagerEnabled` and add the following setting below it:</span></span>  
  
    ```  
    <IsReportBuilderAnonymousAccessEnabled>True</IsReportBuilderAnonymousAccessEnabled>  
    ```  
  
7.  <span data-ttu-id="892a7-200">RSReportServer.config를 저장하고 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-200">Save RSReportServer.config and close the file.</span></span>  
  
8.  <span data-ttu-id="892a7-201">보고서 서버를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="892a7-201">Restart the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="892a7-202">참고 항목</span><span class="sxs-lookup"><span data-stu-id="892a7-202">See Also</span></span>  
 <span data-ttu-id="892a7-203">[보고서 서버 애플리케이션의 애플리케이션 도메인](../report-server/application-domains-for-report-server-applications.md) </span><span class="sxs-lookup"><span data-stu-id="892a7-203">[Application Domains for Report Server Applications](../report-server/application-domains-for-report-server-applications.md) </span></span>  
 [<span data-ttu-id="892a7-204">Reporting Services 보안 및 보호</span><span class="sxs-lookup"><span data-stu-id="892a7-204">Reporting Services Security and Protection</span></span>](reporting-services-security-and-protection.md)  
  
  
