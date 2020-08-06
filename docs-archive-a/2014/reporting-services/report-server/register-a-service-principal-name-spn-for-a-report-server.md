---
title: 보고서 서버의 SPN(서비스 사용자 이름) 등록 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 502170f16aad66757e8f44419ccbac3017072449
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660898"
---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a><span data-ttu-id="b627f-102">보고서 서버의 SPN(서비스 사용자 이름) 등록</span><span class="sxs-lookup"><span data-stu-id="b627f-102">Register a Service Principal Name (SPN) for a Report Server</span></span>
  <span data-ttu-id="b627f-103">상호 인증에 Kerberos 프로토콜을 사용하는 네트워크에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 배포하는 경우 도메인 사용자 계정으로 실행되도록 보고서 서버 서비스 SPN(서비스 사용자 이름)을 구성하려면 보고서 서버 서비스에 대한 SPN을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-103">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a network that uses the Kerberos protocol for mutual authentication, you must create a Service Principal Name (SPN) for the Report Server service if you configure it to run as a domain user account.</span></span>  
  
## <a name="about-spns"></a><span data-ttu-id="b627f-104">SPN 정보</span><span class="sxs-lookup"><span data-stu-id="b627f-104">About SPNs</span></span>  
 <span data-ttu-id="b627f-105">SPN은 Kerberos 인증을 사용하는 네트워크에서 고유한 서비스 식별자로</span><span class="sxs-lookup"><span data-stu-id="b627f-105">An SPN is a unique identifier for a service on a network that uses Kerberos authentication.</span></span> <span data-ttu-id="b627f-106">서비스 클래스, 호스트 이름, 포트로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-106">It consists of a service class, a host name, and a port.</span></span> <span data-ttu-id="b627f-107">Kerberos 인증을 사용하는 네트워크에서 서버에 대한 SPN은 기본 제공 컴퓨터 계정(예: NetworkService 또는 LocalSystem) 또는 사용자 계정에서 등록되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-107">On a network that uses Kerberos authentication, an SPN for the server must be registered under either a built-in computer account (such as NetworkService or LocalSystem) or user account.</span></span> <span data-ttu-id="b627f-108">기본 제공 계정에 대해서는 SPN이 자동으로 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-108">SPNs are registered for built-in accounts automatically.</span></span> <span data-ttu-id="b627f-109">그러나 도메인 사용자 계정에서 서비스를 실행할 경우 사용할 계정에 대한 SPN을 수동으로 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-109">However, when you run a service under a domain user account, you must manually register the SPN for the account you want to use.</span></span>  
  
 <span data-ttu-id="b627f-110">SPN을 만들려면 **SetSPN** 명령줄 유틸리티를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-110">To create an SPN, you can use the **SetSPN** command line utility.</span></span> <span data-ttu-id="b627f-111">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="b627f-111">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="b627f-112">[Setspn](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) ( https://technet.microsoft.com/library/cc731241(WS.10).aspx) .</span><span class="sxs-lookup"><span data-stu-id="b627f-112">[Setspn](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (https://technet.microsoft.com/library/cc731241(WS.10).aspx).</span></span>  
  
-   <span data-ttu-id="b627f-113">[Spn (서비스 사용자 이름) SetSPN 구문 (Setspn.exe)](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) ( https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) .</span><span class="sxs-lookup"><span data-stu-id="b627f-113">[Service Principal Names (SPNs) SetSPN Syntax (Setspn.exe)](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx).</span></span>  
  
 <span data-ttu-id="b627f-114">도메인 컨트롤러에서 이 유틸리티를 실행하려면 도메인 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-114">You must be a domain administrator to run the utility on the domain controller.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b627f-115">구문</span><span class="sxs-lookup"><span data-stu-id="b627f-115">Syntax</span></span>  
 <span data-ttu-id="b627f-116">SetSPN 유틸리티를 사용하여 보고서 서버의 SPN을 만드는 명령 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-116">The command syntax for using SetSPN utility to create an SPN for the report server resembles the following:</span></span>  
  
```  
Setspn -s http/<computername>.<domainname>:<port> <domain-user-account>  
```  
  
 <span data-ttu-id="b627f-117">**SetSPN** 은 Windows Server에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-117">**SetSPN** is available with Windows Server.</span></span> <span data-ttu-id="b627f-118">`-s` 인수는 중복이 없는지 확인한 후 SPN을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-118">The `-s` argument adds a SPN after validating no duplicate exists.</span></span> <span data-ttu-id="b627f-119">**참고: -s** 는 Windows Server(Windows Server 2008부터)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-119">**NOTE:-s** is available in Windows Server starting with Windows Server 2008.</span></span>  
  
 <span data-ttu-id="b627f-120">`HTTP`는 서비스 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-120">`HTTP` is the service class.</span></span> <span data-ttu-id="b627f-121">보고서 서버 웹 서비스는 HTTP.SYS에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-121">The Report Server Web service runs in HTTP.SYS.</span></span> <span data-ttu-id="b627f-122">HTTP용 SPN을 만들면 HTTP.SYS에서 실행되는 같은 컴퓨터에 있는 모든 웹 애플리케이션(IIS에서 호스팅되는 애플리케이션 포함)에 도메인 사용자 계정을 기반으로 하는 티켓이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-122">A by-product of creating an SPN for HTTP is that all Web applications on the same computer that run in HTTP.SYS (including applications hosted in IIS) will be granted tickets based on the domain user account.</span></span> <span data-ttu-id="b627f-123">이러한 서비스가 다른 계정에서 실행되면 인증 요청이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-123">If those services run under a different account, the authentication requests will fail.</span></span> <span data-ttu-id="b627f-124">이 문제를 방지하려면 같은 계정에서 실행되도록 모든 HTTP 애플리케이션을 구성하거나 애플리케이션마다 호스트 헤더를 만든 다음 호스트 헤더별로 SPN을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="b627f-124">To avoid this problem, be sure to configure all HTTP applications to run under the same account, or consider creating host headers for each application and then creating separate SPNs for each host header.</span></span> <span data-ttu-id="b627f-125">호스트 헤더를 구성할 때는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성과 관계없이 DNS를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-125">When you configure host headers, DNS changes are required regardless of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration.</span></span>  
  
 <span data-ttu-id="b627f-126">, 및에 대해 지정 하는 값은 \<*computername*> \<*domainname*> \<*port*> 보고서 서버를 호스팅하는 컴퓨터의 고유 네트워크 주소를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-126">The values that you specify for \<*computername*>, \<*domainname*>, and \<*port*> identify the unique network address of the computer that hosts the report server.</span></span> <span data-ttu-id="b627f-127">이는 로컬 호스트 이름이거나 FQDN(정규화된 도메인 이름)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-127">This can be a local host name or a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="b627f-128">도메인이 하나 뿐이 고 포트 80를 사용 하는 경우 \<*domainname*> 명령줄에서 및를 생략할 수 있습니다 \<*port*> .</span><span class="sxs-lookup"><span data-stu-id="b627f-128">If you only have one domain and are using port 80, you can omit \<*domainname*> and \<*port*> from your command line.</span></span> <span data-ttu-id="b627f-129">\<*domain-user-account*>보고서 서버 서비스를 실행 하는 데 사용 되며 SPN을 등록 해야 하는 사용자 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-129">\<*domain-user-account*> is the user account under which the Report Server service runs and for which the SPN must be registered.</span></span>  
  
## <a name="register-an-spn-for-domain-user-account"></a><span data-ttu-id="b627f-130">도메인 사용자 계정에 대한 SPN 등록</span><span class="sxs-lookup"><span data-stu-id="b627f-130">Register an SPN for Domain User Account</span></span>  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a><span data-ttu-id="b627f-131">도메인 사용자로 실행 중인 보고서 서버 서비스에 대한 SPN을 등록하려면</span><span class="sxs-lookup"><span data-stu-id="b627f-131">To register an SPN for a Report Server service running as a domain user</span></span>  
  
1.  <span data-ttu-id="b627f-132">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 설치하고 도메인 사용자 계정으로 실행되도록 보고서 서버 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-132">Install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and configure the Report Server service to run as a domain user account.</span></span> <span data-ttu-id="b627f-133">다음 단계를 완료해야 보고서 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-133">Note that users will not be able to connect to the report server until you complete the following steps.</span></span>  
  
2.  <span data-ttu-id="b627f-134">도메인 관리자로 도메인 컨트롤러에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-134">Log on to the domain controller as domain administrator.</span></span>  
  
3.  <span data-ttu-id="b627f-135">명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-135">Open a Command Prompt window.</span></span>  
  
4.  <span data-ttu-id="b627f-136">다음 명령을 복사하되 자리 표시자 값은 사용자의 네트워크에 유효한 실제 값으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-136">Copy the following command, replacing placeholder values with actual values that are valid for your network:</span></span>  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name>:<port> <domain-user-account>  
    ```  
  
     <span data-ttu-id="b627f-137">예를 들면 다음과 같습니다. `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`</span><span class="sxs-lookup"><span data-stu-id="b627f-137">For example: `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`</span></span>  
  
5.  <span data-ttu-id="b627f-138">명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-138">Run the command.</span></span>  
  
6.  <span data-ttu-id="b627f-139">**RsReportServer.config** 파일을 열고 `<AuthenticationTypes>` 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-139">Open the **RsReportServer.config** file and locate the `<AuthenticationTypes>` section.</span></span>  
  
7.  <span data-ttu-id="b627f-140">`<RSWindowsNegotiate/>` 를 이 섹션의 첫 번째 항목으로 추가하여 NTLM을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="b627f-140">Add `<RSWindowsNegotiate/>` as the first entry in this section to enable NTLM.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b627f-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b627f-141">See Also</span></span>  
 <span data-ttu-id="b627f-142">[SSRS Configuration Manager &#40;서비스 계정 구성&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b627f-142">[Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="b627f-143">[보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b627f-143">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="b627f-144">Reporting Services 기본 모드 보고서 서버 관리</span><span class="sxs-lookup"><span data-stu-id="b627f-144">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
