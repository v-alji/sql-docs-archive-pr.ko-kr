---
title: 주체 대체 이름을 사용 하도록 Reporting Services 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ce458f9f-4b4f-4a58-aa75-9a90dda1e622
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0312d2d1fff8f854eb2ffb8d0dad2563212ee23b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739538"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a><span data-ttu-id="004ac-102">주체 대체 이름을 사용하도록 Reporting Services 구성</span><span class="sxs-lookup"><span data-stu-id="004ac-102">Configure Reporting Services to Use a Subject Alternative Name</span></span>
  <span data-ttu-id="004ac-103">이 항목에서는 rsreportserver.config 파일을 수정하고 Netsh.exe 도구를 사용하여 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)를 구성하고 SAN(주체 대체 이름)을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-103">This topic explains how to configure [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) to use a subject alternative name (SAN) by modifying the rsreportserver.config file and using the Netsh.exe tool.</span></span>

||
|-|
|<span data-ttu-id="004ac-104">**[!INCLUDE[applies](../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 기본 모드</span><span class="sxs-lookup"><span data-stu-id="004ac-104">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Native mode</span></span>|

 <span data-ttu-id="004ac-105">이 지침은 보고 서비스 URL과 웹 서비스 URL에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-105">The instructions apply to the Reporting Service URL as well as a Web Service URL.</span></span>

 <span data-ttu-id="004ac-106">SAN을 사용하려면 서버에 SSL 인증서를 등록 및 서명하고 프라이빗 키를 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-106">To use a SAN, the SSL certificate must be registered on the server, signed, and have the private key.</span></span> <span data-ttu-id="004ac-107">자체 서명된 인증서를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-107">You cannot use a self-signed certificate</span></span>

 <span data-ttu-id="004ac-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 의 URL은 SSL 인증서를 사용하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-108">URLs in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] can be configured to use an SSL certificate.</span></span> <span data-ttu-id="004ac-109">인증서에는 일반적으로 SSL(Secure Sockets Layer) 세션에 대해 하나의 URL만 허용하는 주체 이름만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-109">A certificate normally has just a subject name, which allows only one URL for an SSL (Secure Sockets Layer) session.</span></span> <span data-ttu-id="004ac-110">SAN은 SSL 서비스에서 여러 URL을 수신하고 여러 URL에 대해 유효하도록 허용하며 다른 애플리케이션과 SSL 포트를 공유하도록 허용하는 인증서의 추가 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-110">The SAN is an additional field in the certificate that allows an SSL service to listen and be valid for many URLs, and to share the SSL port with other applications.</span></span> <span data-ttu-id="004ac-111">SAN은 www.s2.com과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-111">The SAN looks something like the following: www.s2.com.</span></span>

 <span data-ttu-id="004ac-112">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]의 SSL 설정에 대한 자세한 내용은 [기본 모드 보고서 서버에서 SSL 연결 구성](security/configure-ssl-connections-on-a-native-mode-report-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="004ac-112">For more information about SSL settings for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Configure SSL Connections on a Native Mode Report Server](security/configure-ssl-connections-on-a-native-mode-report-server.md).</span></span>

### <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a><span data-ttu-id="004ac-113">웹 서비스 URL에 대해 주체 대체 이름을 사용하도록 SSRS 구성</span><span class="sxs-lookup"><span data-stu-id="004ac-113">Configure SSRS to use a subject alternative name for Web Service URL</span></span>

1.  <span data-ttu-id="004ac-114">Reporting Services 구성 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-114">Start Reporting Services Configuration Manager.</span></span>

     <span data-ttu-id="004ac-115">자세한 내용은 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="004ac-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>

2.  <span data-ttu-id="004ac-116">**웹 서비스 URL** 페이지에서 SSL 포트 및 SSL 인증서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-116">On the **Web Service URL** page, select an SSL port and SSL Certificate.</span></span>

     <span data-ttu-id="004ac-117">![Reporting Services 구성 관리자](media/reportingservices-configurationmanager.png "Reporting Services 구성 관리자")</span><span class="sxs-lookup"><span data-stu-id="004ac-117">![Reporting Services Configuration Manager](media/reportingservices-configurationmanager.png "Reporting Services Configuration Manager")</span></span>

     <span data-ttu-id="004ac-118">구성 관리자가 포트에 대해 SSL 인증서를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-118">The configuration manager registers the SSL certificate for the port.</span></span>

3.  <span data-ttu-id="004ac-119">rsreportserver.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-119">Open the rsreportserver.config file.</span></span>

     <span data-ttu-id="004ac-120">SSRS 기본 모드의 경우 파일은 기본적으로 다음 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-120">For SSRS Native mode, the file is located by default in the following folder.</span></span>

    ```
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer
    ```

4.  <span data-ttu-id="004ac-121">보고서 서버 웹 서비스 애플리케이션의 URL 섹션을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-121">Copy the URL section for the Report Server Web Service application.</span></span>

     <span data-ttu-id="004ac-122">예를 들어 다음은 원래 URL 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-122">For example, the following is the original URL section.</span></span>

    ```
        <URL>
         <UrlString>https://localhost:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>

    ```

     <span data-ttu-id="004ac-123">다음은 수정된 URL 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-123">The following is the modified URL section.</span></span>

    ```
    <URL>
         <UrlString>https://www.s1.com:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>
        <URL>
         <UrlString>https://www.s2.com:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>

    ```

5.  <span data-ttu-id="004ac-124">rsreportserver.config 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-124">Save the rsreportserver.config file.</span></span>

6.  <span data-ttu-id="004ac-125">관리자로 명령 프롬프트를 시작하고 Netsh.exe 도구를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-125">Start a command prompt as an administrator, and run the Netsh.exe tool.</span></span>

    ```
    C:\windows\system32\netsh
    ```

7.  <span data-ttu-id="004ac-126">다음을 입력하여 http 컨텍스트로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-126">Switch to the http context by typing the following.</span></span>

    ```
    Netsh>http
    ```

8.  <span data-ttu-id="004ac-127">다음을 입력하여 기존 urlacls를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-127">Show the existing urlacls by typing the following.</span></span>

    ```
    Netsh http>show urlacl
    ```

     <span data-ttu-id="004ac-128">다음과 같은 항목이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-128">An entry such as the following appears.</span></span>

    ```
    Reserved URL            : https:// www.s1.com:443/ReportServer/
        User: NT SERVICE\ReportServer
            Listen: Yes
            Delegate: No
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)
    ```

     <span data-ttu-id="004ac-129">urlacl은 예약된 URL의 DACL(임의 액세스 제어 목록)입니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-129">An urlacl is a DACL (Discretionary Access Control List) for a reserved URL.</span></span>

9. <span data-ttu-id="004ac-130">다음을 입력하여 기존 항목으로 같은 사용자와 SDDL을 사용하여 주체 대체 이름에 대해 새 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-130">Create a new entry for the subject alternative name, with the same user and SDDL as the existing entry, by typing the following.</span></span>

    ```
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer  
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)

    ```

10. <span data-ttu-id="004ac-131">Reporting Services 구성 관리자의 **보고서 서버 상태** 페이지에서 **중지** 를 클릭한 다음 **시작** 을 클릭하여 보고서 서버를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="004ac-131">On the **Report Server Status** page of the Reporting Services Configuration Manager, Click **Stop** and then click **Start** to restart the report server.</span></span>

## <a name="see-also"></a><span data-ttu-id="004ac-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="004ac-132">See Also</span></span>
 <span data-ttu-id="004ac-133">[Rsreportserver.config 구성 파일](report-server/rsreportserver-config-configuration-file.md) [Reporting Services 구성 관리자 &#40;기본 모드로](../sql-server/install/reporting-services-configuration-manager-native-mode.md) [Reporting Services 구성 파일을 수정](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)&#41;&#40;RSreportserver.config [보고서 서버 url&#41;SSRS &#40;구성](install-windows/configure-report-server-urls-ssrs-configuration-manager.md) 합니다 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="004ac-133">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)</span></span>


