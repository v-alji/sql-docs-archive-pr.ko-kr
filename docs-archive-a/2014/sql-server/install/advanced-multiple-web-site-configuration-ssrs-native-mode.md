---
title: 고급 다중 웹 사이트 구성 (SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.advancedmultiplewebsiteconfig.F1
ms.assetid: af4ede43-2225-45b5-ae7e-9202411551ba
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 65061eae928227f16b1088a0fb5448b19093cb1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650535"
---
# <a name="advanced-multiple-web-site-configuration-ssrs-native-mode"></a><span data-ttu-id="4234f-102">고급 다중 웹 사이트 구성(SSRS 암호 모드)</span><span class="sxs-lookup"><span data-stu-id="4234f-102">Advanced Multiple Web Site Configuration (SSRS Native Mode)</span></span>
  <span data-ttu-id="4234f-103">이 대화 상자에서는 보고서 서버 또는 보고서 관리자에 액세스할 때 사용되는 URL을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-103">Use this dialog box to create and manage the URLs used to access a report server or Report Manager.</span></span> <span data-ttu-id="4234f-104">**고급 다중 웹 사이트 구성** 대화 상자는 호스트 헤더 이름을 포함하는 사용자 지정 URL, 추가 URL을 만들거나 IP 주소를 IPv4 또는 IPv6 형식으로 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-104">The **Advanced Multiple Web Site Configuration** dialog box is used to create additional URLs, custom URLs that include a host header name, or specify an IP address in the IPv4 or IPv6 format.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="4234f-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="4234f-106">여러 가지 방법으로 보고서 서버에 액세스하도록 구성하려는 경우 URL을 여러 개 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-106">Creating multiple URLs is useful if you want to configure different ways to access a report server.</span></span> <span data-ttu-id="4234f-107">예를 들어 일반적으로 인트라넷 및 익스트라넷 연결을 통해 보고서 서버에 액세스하려면 각 유형의 연결마다 다른 URL을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-107">For example, report server access over intranet and extranet connection typically requires that you have different URLs for each type of connection.</span></span>  
  
 <span data-ttu-id="4234f-108">**고급 다중 웹 사이트 구성** 대화 상자를 열려면 **구성 관리자의** 웹 서비스 URL **또는** 보고서 관리자 URL **페이지에서** 고급 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-108">To open the **Advanced Multiple Web Site Configuration** dialog box, click **Advanced** on the **Web Service URL** or the **Report Manager URL** page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="4234f-109">**고급 다중 웹 사이트 구성** 대화 상자가 열리면 **추가** 또는 **편집** 을 클릭하여 새 URL을 정의하거나 기존 URL을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-109">After the **Advanced Multiple Web Site Configuration** dialog box is open, you can click **Add** or **Edit** to define new URLs or modify or delete existing URLs.</span></span>  
  
 <span data-ttu-id="4234f-110">**확인**을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-110">Click **OK** to save your changes.</span></span> <span data-ttu-id="4234f-111">URL을 추가하거나 제거한 후 **확인**을 클릭하지 않고 대화 상자를 닫으면 변경 내용이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-111">If you add or remove URLs, but then close the dialog box without first clicking **OK**, your changes will be lost.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4234f-112">옵션</span><span class="sxs-lookup"><span data-stu-id="4234f-112">Options</span></span>  
 <span data-ttu-id="4234f-113">**IP 주소**</span><span class="sxs-lookup"><span data-stu-id="4234f-113">**IP Address**</span></span>  
 <span data-ttu-id="4234f-114">TCP/IP 네트워크의 보고서 서버 컴퓨터를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-114">Identifies the report server computer on a TCP/IP network.</span></span> <span data-ttu-id="4234f-115">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-115">Valid values include:</span></span>  
  
-   <span data-ttu-id="4234f-116">**모두 할당됨** - 컴퓨터에 할당된 모든 IP 주소를 보고서 서버 애플리케이션을 가리키는 URL에 사용할 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-116">**All Assigned** specifies that any of the IP addresses that are assigned to the computer can be used in a URL that points to a report server application.</span></span> <span data-ttu-id="4234f-117">또한 이 값은 도메인 이름 서버에서 확인할 수 있는 호스트 이름(예: 컴퓨터 이름)부터 컴퓨터에 할당된 IP 주소까지 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-117">This value also encompasses friendly host names (such as computer names) that can be resolved by a domain name server to an IP address that is assigned to the computer.</span></span> <span data-ttu-id="4234f-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL에 대한 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-118">This is the default value for a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL.</span></span>  
  
-   <span data-ttu-id="4234f-119">**모두 할당되지 않음** - IP 주소 또는 호스트 이름과 정확하게 일치하지 않는 모든 요청을 보고서 서버에서 받아들이도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-119">**All Unassigned** specifies that the report server will accept any request that does not have an exact match for the IP address or host name.</span></span> <span data-ttu-id="4234f-120">다른 웹 애플리케이션에서 이미 이 값을 사용하고 있는 경우에는 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="4234f-120">Do not use this value if another Web application is already using it.</span></span> <span data-ttu-id="4234f-121">그럴 경우 다른 애플리케이션의 서비스가 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-121">If you do so, you will disrupt service for the other application.</span></span>  
  
-   <span data-ttu-id="4234f-122">**127.0.0.1** - localhost 액세스에 사용되며</span><span class="sxs-lookup"><span data-stu-id="4234f-122">**127.0.0.1** is used to access to localhost.</span></span> <span data-ttu-id="4234f-123">보고서 서버 컴퓨터에 대한 로컬 관리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-123">It supports local administration on the report server computer.</span></span> <span data-ttu-id="4234f-124">이 값만 선택할 경우 보고서 서버 컴퓨터에 로컬로 로그온한 사용자만 애플리케이션에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-124">If you select only this value, only users who are logged on locally to the report server computer will have access the application.</span></span>  
  
-   <span data-ttu-id="4234f-125">*Nnn.nnn.nnn.nnn* - 컴퓨터에 설치된 네트워크 어댑터 카드의 IPv4 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-125">*Nnn.nnn.nnn.nnn* is the IPv4 address of a network adapter card on your computer.</span></span> <span data-ttu-id="4234f-126">네트워크에서 IPv6 주소를 사용 하는 경우 IP 주소는 \<header> :*nnnn: nnnn: nnnn: nnnn*형식과 비슷한 8 4 바이트 필드의 128 비트 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-126">If your network uses IPv6 addressing, the IP address will be a 128-bit value of 8 4-byte fields similar to the following format: \<header>:*nnnn:nnnn:nnnn:nnnn*.</span></span>  
  
     <span data-ttu-id="4234f-127">카드가 여러 개인 경우 카드 하나당 한 개의 IP 주소가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-127">If you have multiple cards, you will see an IP address for each one.</span></span> <span data-ttu-id="4234f-128">IP 주소를 한 개만 선택할 경우 해당 IP 주소와 도메인 이름 서버가 이 IP 주소에 매핑한 호스트 이름만 애플리케이션에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-128">If you select only this value, it will limit application access to the just the IP address (and any host name that a domain name server maps to that address).</span></span> <span data-ttu-id="4234f-129">localhost를 사용하여 보고서 서버에 액세스할 수 없으며, 보고서 서버 컴퓨터에 설치된 다른 네트워크 어댑터 카드의 IP 주소를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-129">You cannot use localhost to access a report server, and you cannot use the IP addresses of other network adapter cards that are installed on the report server computer.</span></span>  
  
 <span data-ttu-id="4234f-130">**포트**</span><span class="sxs-lookup"><span data-stu-id="4234f-130">**Port**</span></span>  
 <span data-ttu-id="4234f-131">보고서 서버에서 요청을 모니터링하는 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-131">Specifies the port that report server monitors for requests.</span></span> <span data-ttu-id="4234f-132">기본 포트는 포트 80입니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-132">Port 80 is the default port.</span></span> <span data-ttu-id="4234f-133">포트 80을 사용할 경우 URL에 포트 번호를 포함시킬 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-133">If you use port 80, you do not have to include it in the URL.</span></span> <span data-ttu-id="4234f-134">다른 포트 번호를 사용 하는 경우 URL에 항상 포함 해야 합니다 (예:) http://localhost:8181/reports) .</span><span class="sxs-lookup"><span data-stu-id="4234f-134">If you use any other port number, you must always include it in the URL (for example, http://localhost:8181/reports).</span></span>  
  
 <span data-ttu-id="4234f-135">**호스트 헤더**</span><span class="sxs-lookup"><span data-stu-id="4234f-135">**Host Header**</span></span>  
 <span data-ttu-id="4234f-136">컴퓨터로 확인되는 도메인 이름 서버에 호스트 헤더가 이미 정의되어 있는 경우 보고서 서버 액세스용으로 구성되는 호스트 헤더를 URL에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-136">If you already have a host header defined on a domain name server that resolves to your computer, you can specify that host header in a URL that you configure for report server access.</span></span>  
  
 <span data-ttu-id="4234f-137">호스트 헤더란 여러 웹 사이트에서 단일 IP 주소와 포트를 공유할 수 있도록 하는 고유한 이름으로,</span><span class="sxs-lookup"><span data-stu-id="4234f-137">A host header is a unique name that allows multiple Web sites to share a single IP address and port.</span></span> <span data-ttu-id="4234f-138">IP 주소와 포트 번호에 비해 기억하기 쉬울 뿐 아니라 입력하기도 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-138">Host header names are easier to remember and type than IP address and port numbers.</span></span> <span data-ttu-id="4234f-139">호스트 헤더 이름의 예로는 www.adventure-works.com 을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-139">An example of a host header name might be www.adventure-works.com.</span></span>  
  
 <span data-ttu-id="4234f-140">**SSL 포트**</span><span class="sxs-lookup"><span data-stu-id="4234f-140">**SSL Port**</span></span>  
 <span data-ttu-id="4234f-141">SSL 연결용 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-141">Specifies the port for SSL connections.</span></span> <span data-ttu-id="4234f-142">SSL용 기본 포트는 443입니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-142">The default port for SSL is 443.</span></span>  
  
 <span data-ttu-id="4234f-143">**SSL 인증서**</span><span class="sxs-lookup"><span data-stu-id="4234f-143">**SSL Certificate**</span></span>  
 <span data-ttu-id="4234f-144">이 컴퓨터에 설치된 SSL 인증서의 인증서 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-144">Specifies the certificate name of an SSL certificate that you installed on this computer.</span></span> <span data-ttu-id="4234f-145">인증서가 와일드카드에 매핑될 경우 이 인증서를 보고서 서버 연결에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-145">If the certificate maps to a wildcard, you can use it for a report server connection.</span></span>  
  
 <span data-ttu-id="4234f-146">인증서가 등록되어 있는 정규화된 컴퓨터 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-146">Specifies the fully qualified computer name for which the certificate is registered.</span></span> <span data-ttu-id="4234f-147">지정하는 이름은 인증서가 등록된 이름과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-147">The name that you specify must be identical to the name for which the certificate is registered.</span></span>  
  
 <span data-ttu-id="4234f-148">이 옵션을 사용하려면 인증서가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-148">You must have a certificate installed to use this option.</span></span> <span data-ttu-id="4234f-149">RSReportServer.config 파일에서 UrlRoot 구성 설정도 수정하여 인증서가 등록되어 있는 컴퓨터의 정규화된 이름을 지정하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-149">You must also modify the UrlRoot configuration setting in the RSReportServer.config file so that it specifies the fully qualified name of the computer for which the certificate is registered.</span></span> <span data-ttu-id="4234f-150">자세한 내용은 [온라인 설명서의](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) 기본 모드 보고서 서버에서 SSL 연결 구성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4234f-150">For more information, see [Configure SSL Connections on a Native Mode Report Server](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="4234f-151">**발급 대상**</span><span class="sxs-lookup"><span data-stu-id="4234f-151">**Issued To**</span></span>  
 <span data-ttu-id="4234f-152">인증서를 만든 컴퓨터의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-152">Shows the name of the computer for which the certificate was created.</span></span>  
  
 <span data-ttu-id="4234f-153">**추가**</span><span class="sxs-lookup"><span data-stu-id="4234f-153">**Add**</span></span>  
 <span data-ttu-id="4234f-154">추가 URL을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-154">Define an additional URL.</span></span>  
  
 <span data-ttu-id="4234f-155">**편집**</span><span class="sxs-lookup"><span data-stu-id="4234f-155">**Edit**</span></span>  
 <span data-ttu-id="4234f-156">URL 구문의 특정 부분을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-156">Modify any part of the URL syntax.</span></span>  
  
 <span data-ttu-id="4234f-157">**제거**</span><span class="sxs-lookup"><span data-stu-id="4234f-157">**Remove**</span></span>  
 <span data-ttu-id="4234f-158">목록에서 URL 항목을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="4234f-158">Clear a URL entry from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4234f-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4234f-159">See Also</span></span>  
 <span data-ttu-id="4234f-160">[Reporting Services 구성 관리자&#40;기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="4234f-160">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="4234f-161">[SSRS Configuration Manager &#40;URL 구성&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="4234f-161">[Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="4234f-162">보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="4234f-162">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
