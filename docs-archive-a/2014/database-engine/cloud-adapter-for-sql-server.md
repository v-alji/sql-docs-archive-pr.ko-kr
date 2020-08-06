---
title: SQL Server에 대 한 클라우드 어댑터 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cloud adapter
- Deploy to Azure
ms.assetid: 82ed0d0f-952d-4d49-aa36-3855a3ca9877
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d5716435bb1db494bdabeb45ed366c1783926989
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652360"
---
# <a name="cloud-adapter-for-sql-server"></a><span data-ttu-id="10001-102">SQL Server에 대한 클라우드 어댑터</span><span class="sxs-lookup"><span data-stu-id="10001-102">Cloud Adapter for SQL Server</span></span>
  <span data-ttu-id="10001-103">클라우드 어댑터 서비스는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AZURE VM에서 프로 비전의 일부로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10001-103">The Cloud Adapter service is created as part of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provisioning on an Azure VM.</span></span> <span data-ttu-id="10001-104">클라우드 어댑터 서비스는 첫 번째 실행 중에 자체 서명된 SSL 인증서를 생성한 다음 **로컬 시스템** 계정으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="10001-104">The Cloud Adapter service generates a self-signed SSL certificate as part of its first run, and then runs as a **Local System** account.</span></span> <span data-ttu-id="10001-105">이 서비스는 자체적으로 구성하는 데 사용되는 구성 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-105">It generates a configuration file that is used to configure itself.</span></span> <span data-ttu-id="10001-106">클라우드 어댑터는 기본 포트 11435에서 들어오는 TCP 연결을 허용하도록 Windows 방화벽 규칙도 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-106">The Cloud Adapter also creates a Windows Firewall rule to allow its incoming TCP connections at default port 11435.</span></span>  
  
 <span data-ttu-id="10001-107">클라우드 어댑터는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 온-프레미스 인스턴스에서 메시지를 수신하는 상태 비저장 동기 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="10001-107">The Cloud Adapter is a stateless, synchronous service that receives messages from the on-premise instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="10001-108">클라우드 어댑터 서비스가 중지되면 원격 액세스 클라우드 어댑터가 중지되고 SSL 인증서가 바인딩 해제되며 Windows 방화벽 규칙이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-108">When the Cloud Adapter service is stopped, it stops the remote access Cloud Adapter, unbinds the SSL certificate, and disables the Windows Firewall rule.</span></span>  
  
## <a name="cloud-adapter-requirements"></a><span data-ttu-id="10001-109">클라우드 어댑터 요구 사항</span><span class="sxs-lookup"><span data-stu-id="10001-109">Cloud Adapter Requirements</span></span>  
 <span data-ttu-id="10001-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 클라우드 어댑터를 설치, 사용 및 실행하려면 다음 요구 사항을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-110">Note the following requirements to install, enable, and run the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="10001-111">클라우드 어댑터는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="10001-111">Cloud Adapter is supported with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 and higher.</span></span> <span data-ttu-id="10001-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 대한 클라우드 어댑터를 사용하려면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012용 SQL Management Objects가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-112">On [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012, the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requires SQL Management Objects for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012.</span></span>  
  
-   <span data-ttu-id="10001-113">클라우드 어댑터 웹 서비스는 **로컬 시스템** 계정으로 실행되며 태스크를 실행하기 전에 클라이언트 자격 증명을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-113">Cloud Adapter web service runs as a **Local System** account and verifies client credentials before executing any task.</span></span> <span data-ttu-id="10001-114">클라이언트에서 제공 하는 자격 증명은 원격 컴퓨터에서 로컬 **관리자** 그룹의 멤버인 사용 계정에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-114">Credentials supplied by the client must belong to the use account that is a member of the local **Administrators** group on the remote machine.</span></span>  
  
-   <span data-ttu-id="10001-115">클라우드 어댑터는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-115">Cloud Adapter supports only [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
-   <span data-ttu-id="10001-116">클라우드 어댑터는 sa 계정이 아니라 VM 로컬 관리자 계정을 사용하여 로컬 컴퓨터에서 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-116">Cloud Adapter uses VM local administrator account to execute commands on the local machine, not an sa account.</span></span>  
  
-   <span data-ttu-id="10001-117">클라우드 어댑터는 TCP/IP를 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-117">Cloud Adapter listens on TCP/IP.</span></span> <span data-ttu-id="10001-118">기본 포트는 11435입니다.</span><span class="sxs-lookup"><span data-stu-id="10001-118">The default port is 11435.</span></span>  
  
-   <span data-ttu-id="10001-119">클라우드 어댑터는 Windows 방화벽 규칙을 만들고 수정할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-119">Cloud Adapter must have permissions to create and modify Windows Firewall rules.</span></span>  
  
## <a name="cloud-adapter-configuration-settings"></a><span data-ttu-id="10001-120">클라우드 어댑터 구성 설정</span><span class="sxs-lookup"><span data-stu-id="10001-120">Cloud Adapter Configuration Settings</span></span>  
 <span data-ttu-id="10001-121">다음 클라우드 어댑터 구성 세부 정보를 사용하여 클라우드 어댑터에 대한 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-121">Use the following Cloud Adapter configuration details to modify settings for a Cloud Adapter.</span></span>  
  
-   <span data-ttu-id="10001-122">**구성 파일의 기본 경로** -C:\PROGRAM Files\Microsoft SQL Server\120\Tools\CloudAdapter</span><span class="sxs-lookup"><span data-stu-id="10001-122">**Default path for the configuration file** - C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter</span></span>\  
  
-   <span data-ttu-id="10001-123">**구성 파일 매개 변수** -</span><span class="sxs-lookup"><span data-stu-id="10001-123">**Configuration file parameters** -</span></span>  
  
    -   \<configuration>  
  
        -   \<appSettings>  
  
            -   \<add key="WebServicePort" value="" />  
  
            -   \<add key="WebServiceCertificate" value="GUID" />  
  
            -   \<add key="ExposeExceptionDetails" value="true" />  
  
        -   \</appSettings>  
  
    -   \</configuration>  
  
-   <span data-ttu-id="10001-124">**인증서 세부 정보** -인증서의 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-124">**Certificate details** - The certificate has the following values:</span></span>  
  
    -   <span data-ttu-id="10001-125">주체-"CN = CloudAdapter \<VMName> , dc = SQL Server, dc = Microsoft"</span><span class="sxs-lookup"><span data-stu-id="10001-125">Subject - "CN=CloudAdapter\<VMName>, DC=SQL Server, DC=Microsoft"</span></span>  
  
    -   <span data-ttu-id="10001-126">인증서에는 서버 인증 EKU만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-126">The certificate should have only Server Authentication EKU enabled.</span></span>  
  
    -   <span data-ttu-id="10001-127">인증서 키 길이는 2048입니다.</span><span class="sxs-lookup"><span data-stu-id="10001-127">The certificate key length is 2048.</span></span>  
  
 <span data-ttu-id="10001-128">**구성 파일 값**:</span><span class="sxs-lookup"><span data-stu-id="10001-128">**Configuration file values**:</span></span>  
  
|<span data-ttu-id="10001-129">설정</span><span class="sxs-lookup"><span data-stu-id="10001-129">Setting</span></span>|<span data-ttu-id="10001-130">값</span><span class="sxs-lookup"><span data-stu-id="10001-130">Values</span></span>|<span data-ttu-id="10001-131">기본값</span><span class="sxs-lookup"><span data-stu-id="10001-131">Default</span></span>|<span data-ttu-id="10001-132">주석</span><span class="sxs-lookup"><span data-stu-id="10001-132">Comments</span></span>|  
|-------------|------------|-------------|--------------|  
|<span data-ttu-id="10001-133">WebServicePort</span><span class="sxs-lookup"><span data-stu-id="10001-133">WebServicePort</span></span>|<span data-ttu-id="10001-134">1-65535</span><span class="sxs-lookup"><span data-stu-id="10001-134">1-65535</span></span>|<span data-ttu-id="10001-135">11435</span><span class="sxs-lookup"><span data-stu-id="10001-135">11435</span></span>|<span data-ttu-id="10001-136">지정되지 않은 경우 11435를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-136">If not specified, use 11435.</span></span>|  
|<span data-ttu-id="10001-137">WebServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="10001-137">WebServiceCertificate</span></span>|<span data-ttu-id="10001-138">Thumbprint</span><span class="sxs-lookup"><span data-stu-id="10001-138">Thumbprint</span></span>|<span data-ttu-id="10001-139">Empty</span><span class="sxs-lookup"><span data-stu-id="10001-139">Empty</span></span>|<span data-ttu-id="10001-140">비어 있는 경우 새로운 자체 서명된 인증서가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="10001-140">If empty, a new self-signed certificate is generated.</span></span>|  
|<span data-ttu-id="10001-141">ExposeExceptionDetails</span><span class="sxs-lookup"><span data-stu-id="10001-141">ExposeExceptionDetails</span></span>|<span data-ttu-id="10001-142">True/False</span><span class="sxs-lookup"><span data-stu-id="10001-142">True/False</span></span>|<span data-ttu-id="10001-143">거짓</span><span class="sxs-lookup"><span data-stu-id="10001-143">False</span></span>||  
  
## <a name="cloud-adapter-troubleshooting"></a><span data-ttu-id="10001-144">클라우드 어댑터 문제 해결</span><span class="sxs-lookup"><span data-stu-id="10001-144">Cloud Adapter Troubleshooting</span></span>  
 <span data-ttu-id="10001-145">다음 정보를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 대한 클라우드 어댑터의 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-145">Use the following information to troubleshoot the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="10001-146">**오류 처리 및 로깅** -오류 및 상태 메시지는 응용 프로그램 이벤트 로그에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10001-146">**Error handling and logging** - Errors and status messages are written to the Application Event Log.</span></span>  
  
-   <span data-ttu-id="10001-147">**추적, 이벤트** -모든 이벤트는 응용 프로그램 이벤트 로그에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10001-147">**Tracing, Events** - All events are written to the Application Event Log.</span></span>  
  
-   <span data-ttu-id="10001-148">**Control, configuration** -: C:\PROGRAM Files\Microsoft SQL Server\120\Tools\CloudAdapter에 있는 구성 파일을 사용 \\ 합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-148">**Control, configuration** - Use the configuration file located in:  C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter\\.</span></span>  
  
|<span data-ttu-id="10001-149">오류</span><span class="sxs-lookup"><span data-stu-id="10001-149">Error</span></span>|<span data-ttu-id="10001-150">오류 ID</span><span class="sxs-lookup"><span data-stu-id="10001-150">Error ID</span></span>|<span data-ttu-id="10001-151">원인</span><span class="sxs-lookup"><span data-stu-id="10001-151">Cause</span></span>|<span data-ttu-id="10001-152">해결 방법</span><span class="sxs-lookup"><span data-stu-id="10001-152">Resolution</span></span>|  
|-----------|--------------|-----------|----------------|  
|<span data-ttu-id="10001-153">인증서를 인증서 저장소에 추가하는 동안 예외가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-153">There was an exception while adding the certificate to the certificate store.</span></span> <span data-ttu-id="10001-154">{예외 텍스트}.</span><span class="sxs-lookup"><span data-stu-id="10001-154">{Exception text}.</span></span>|<span data-ttu-id="10001-155">45560</span><span class="sxs-lookup"><span data-stu-id="10001-155">45560</span></span>|<span data-ttu-id="10001-156">컴퓨터 인증서 저장소 사용 권한</span><span class="sxs-lookup"><span data-stu-id="10001-156">Machine certificate store permissions</span></span>|<span data-ttu-id="10001-157">클라우드 어댑터 서비스가 인증서를 컴퓨터 인증서 저장소에 추가할 수 있는 권한이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="10001-157">Ensure that the Cloud Adapter service has permissions to add certificates to the machine certificate store.</span></span>|  
|<span data-ttu-id="10001-158">포트 {포트 번호} 및 인증서 {지문}에 대한 SSL 바인딩을 구성하려고 하는 동안 예외가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-158">There was an exception while trying to configure the SSL binding for port {Port number} and certificate {Thumbprint}.</span></span> <span data-ttu-id="10001-159">{예외}.</span><span class="sxs-lookup"><span data-stu-id="10001-159">{Exception}.</span></span>|<span data-ttu-id="10001-160">45561</span><span class="sxs-lookup"><span data-stu-id="10001-160">45561</span></span>|<span data-ttu-id="10001-161">다른 애플리케이션에서 포트를 이미 사용하고 있거나 인증서를 포트에 바인딩했습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-161">Another application has already used the port or bound a certificate to it.</span></span>|<span data-ttu-id="10001-162">구성 파일에서 기존 바인딩을 제거하거나 클라우드 어댑터 포트를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-162">Remove existing bindings or change Cloud Adapter port in the configuration file.</span></span>|  
|<span data-ttu-id="10001-163">인증서 저장소에서 SSL 인증서 [{지문}]를 찾지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-163">Failed to find SSL certificate [{Thumbprint}] in the certificate store.</span></span>|<span data-ttu-id="10001-164">45564</span><span class="sxs-lookup"><span data-stu-id="10001-164">45564</span></span>|<span data-ttu-id="10001-165">인증서 지문은 구성 파일에 있지만 서비스에 대한 개인 인증서 저장소에는 인증서가 들어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-165">Certificate thumbprint is in the configuration file, but personal certificate store for the service does not contain certificate.</span></span><br /><br /> <span data-ttu-id="10001-166">사용 권한 부족</span><span class="sxs-lookup"><span data-stu-id="10001-166">Insufficient permissions.</span></span>|<span data-ttu-id="10001-167">인증서가 서비스에 대한 개인 인증서 저장소에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-167">Make sure the certificate is in the personal certificate store for the service.</span></span><br /><br /> <span data-ttu-id="10001-168">서비스가 저장소에 대한 올바른 사용 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-168">Make sure the service has correct permissions for the store.</span></span>|  
|<span data-ttu-id="10001-169">웹 서비스를 시작하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-169">Failed to start the web service.</span></span> <span data-ttu-id="10001-170">{예외 텍스트}.</span><span class="sxs-lookup"><span data-stu-id="10001-170">{Exception text}.</span></span>|<span data-ttu-id="10001-171">45570</span><span class="sxs-lookup"><span data-stu-id="10001-171">45570</span></span>|<span data-ttu-id="10001-172">예외에서 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="10001-172">Described in the exception.</span></span>|<span data-ttu-id="10001-173">ExposeExceptionDetails를 사용하고 예외에서 확장된 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-173">Enable ExposeExceptionDetails and use extended information from the exception.</span></span>|  
|<span data-ttu-id="10001-174">[{Thumbprint}] 인증서가 만료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-174">Certificate [{Thumbprint}] has expired.</span></span>|<span data-ttu-id="10001-175">45565</span><span class="sxs-lookup"><span data-stu-id="10001-175">45565</span></span>|<span data-ttu-id="10001-176">구성 파일에서 만료된 인증서가 참조되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10001-176">Expired certificate referenced from the configuration file.</span></span>|<span data-ttu-id="10001-177">유효한 인증서를 추가하고 지문을 사용하여 구성 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-177">Add a valid certificate and update the configuration file with its thumbprint.</span></span>|  
|<span data-ttu-id="10001-178">웹 서비스 {0} 오류:</span><span class="sxs-lookup"><span data-stu-id="10001-178">Web service error: {0}.</span></span>|<span data-ttu-id="10001-179">45571</span><span class="sxs-lookup"><span data-stu-id="10001-179">45571</span></span>|<span data-ttu-id="10001-180">예외에서 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="10001-180">Described in the exception.</span></span>|<span data-ttu-id="10001-181">ExposeExceptionDetails를 사용하고 예외에서 확장된 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="10001-181">Enable ExposeExceptionDetails and use extended information from the exception.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10001-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10001-182">See Also</span></span>  
 [<span data-ttu-id="10001-183">Microsoft Azure 가상 머신에 SQL Server 데이터베이스 배포</span><span class="sxs-lookup"><span data-stu-id="10001-183">Deploy a SQL Server Database to a Microsoft Azure Virtual Machine</span></span>](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)  
  
  
