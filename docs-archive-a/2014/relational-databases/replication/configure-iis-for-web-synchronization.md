---
title: 웹 동기화를 위한 IIS 구성 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- IIS server configuration [SQL Server replication]
- websync.log
- Web synchronization, IIS servers
ms.assetid: d651186e-c9ca-4864-a444-2cd6943b8e35
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 523c4fc30151acd3ee4df21f2fdaa2187e702870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648942"
---
# <a name="configure-iis-for-web-synchronization"></a><span data-ttu-id="f89c2-102">웹 동기화를 위한 IIS 구성</span><span class="sxs-lookup"><span data-stu-id="f89c2-102">Configure IIS for Web Synchronization</span></span>
  <span data-ttu-id="f89c2-103">이 항목의 절차는 병합 복제를 위해 웹 동기화를 구성하는 두 번째 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-103">The procedures in this topic make up the second step in configuring Web synchronization for merge replication.</span></span> <span data-ttu-id="f89c2-104">게시를 웹 동기화용으로 설정한 다음 이 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-104">You perform this step after you enable a publication for Web synchronization.</span></span> <span data-ttu-id="f89c2-105">구성 프로세스에 대한 개요는 [웹 동기화 구성](configure-web-synchronization.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-105">For an overview of the configuration process, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span> <span data-ttu-id="f89c2-106">이 항목의 절차를 완료한 다음에는 구독이 웹 동기화를 사용하도록 구성하는 세 번째 단계를 이어서 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-106">After you complete the procedures in this topic, continue to the third step, configuring a subscription to use Web synchronization.</span></span> <span data-ttu-id="f89c2-107">세 번째 단계는 다음 항목에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-107">This third step is described in the following topics:</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="f89c2-108">: [방법: 구독에서 웹 동기화를 사용하도록 구성\(SQL Server Management Studio)\)](https://msdn.microsoft.com/library/ms345214.aspx)</span><span class="sxs-lookup"><span data-stu-id="f89c2-108">: [How to: Configure a Subscription to Use Web Synchronization \(SQL Server Management Studio\)](https://msdn.microsoft.com/library/ms345214.aspx)</span></span>  
  
-   <span data-ttu-id="f89c2-109">복제 [!INCLUDE[tsql](../../includes/tsql-md.md)] 프로그래밍: [방법:구독에서 웹 동기화를 사용하도록 구성(복제 Transact-SQL 프로그래밍)](https://msdn.microsoft.com/library/ms345206.aspx)</span><span class="sxs-lookup"><span data-stu-id="f89c2-109">Replication [!INCLUDE[tsql](../../includes/tsql-md.md)] programming: [How to: Configure a Subscription to Use Web Synchronization (Replication Transact-SQL Programming)](https://msdn.microsoft.com/library/ms345206.aspx)</span></span>  
  
-   <span data-ttu-id="f89c2-110">RMO: [방법: 구독에서 웹 동기화를 사용하도록 구성(RMO 프로그래밍)](https://msdn.microsoft.com/library/ms345207.aspx)</span><span class="sxs-lookup"><span data-stu-id="f89c2-110">RMO: [How to: Configure a Subscription to Use Web Synchronization (RMO Programming)](https://msdn.microsoft.com/library/ms345207.aspx)</span></span>  
  
 <span data-ttu-id="f89c2-111">웹 동기화는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인터넷 정보 서비스(IIS)를 실행하는 컴퓨터를 사용하여 끌어오기 구독을 병합 게시에 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-111">Web synchronization uses a computer that is running [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) to synchronize pull subscriptions to merge publications.</span></span> <span data-ttu-id="f89c2-112">IIS 버전 5.0, IIS 버전 6.0 및 IIS 버전 7.0이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-112">IIS version 5.0, IIS version 6.0, and IIS version 7.0 are supported.</span></span> <span data-ttu-id="f89c2-113">웹 동기화 구성 마법사는 IIS 버전 7.0에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-113">The Configure Web Synchronization Wizard is not supported on IIS version 7.0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f89c2-114">애플리케이션에서 [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] 이상 버전을 사용해야 하며, 이전 버전의 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 가 IIS 서버에 설치되어 있으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-114">Make sure that your application uses only [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] or later versions, and that earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] are not installed on the IIS server.</span></span> <span data-ttu-id="f89c2-115">이전 버전의 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 가 있으면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-115">Earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] can cause errors.</span></span> <span data-ttu-id="f89c2-116">여기에는 다음이 포함됩니다. "웹 동기화 중 메시지 형식이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-116">These include the following: "The format of a message during Web synchronization was invalid.</span></span> <span data-ttu-id="f89c2-117">웹 서버에서 복제 구성 요소가 올바르게 구성되었는지 확인하십시오."</span><span class="sxs-lookup"><span data-stu-id="f89c2-117">Ensure that replication components are properly configured at the Web server".</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="f89c2-118">WebSync 및 대체 스냅샷 폴더 위치를 동시에 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-118">Do not use both WebSync and alternate snapshot folder locations at the same time.</span></span>  
  
 <span data-ttu-id="f89c2-119">웹 동기화를 사용하려면 다음 단계를 완료하여 IIS를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-119">To use Web synchronization, you must configure IIS by completing the following steps.</span></span> <span data-ttu-id="f89c2-120">이 항목에서는 각 단계를 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-120">Each step is described in detail in this topic.</span></span>  
  
1.  <span data-ttu-id="f89c2-121">SSL(Secure Sockets Layer)을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-121">Configure Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="f89c2-122">SSL은 IIS와 모든 구독자 간의 통신을 위해 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-122">SSL is required for communication between IIS and all Subscribers.</span></span>  
  
2.  <span data-ttu-id="f89c2-123">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사를 사용 하 여 IIS를 실행 하는 컴퓨터에 연결 구성 요소를 설치 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-123">Install [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connectivity components on the computer that is running IIS by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span> <span data-ttu-id="f89c2-124">3단계에서 언급한 웹 동기화 구성 마법사를 사용하려면 IIS를 실행하는 컴퓨터에 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 도 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-124">If you plan to use the Configure Web Synchronization Wizard that is mentioned in step 3, you must also install [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] on the computer that is running IIS.</span></span>  
  
3.  <span data-ttu-id="f89c2-125">IIS를 실행하는 컴퓨터를 웹 동기화용으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-125">Configure the computer that is running IIS for Web synchronization.</span></span> <span data-ttu-id="f89c2-126">컴퓨터를 수동으로 구성할 수 있지만 웹 동기화 구성 마법사를</span><span class="sxs-lookup"><span data-stu-id="f89c2-126">You can configure the computer manually or use the Configure Web Synchronization Wizard.</span></span> <span data-ttu-id="f89c2-127">사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-127">We recommend that you use the wizard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f89c2-128">IIS를 실행하는 컴퓨터에서 64비트 버전의 Windows를 실행 중인 경우 다음 명령을 실행하여 서버가 ISAPI(Internet Server API) 애플리케이션을 실행하도록 적절하게 구성되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-128">If the computer that is running IIS is running on a 64-bit version of Windows, you must run following command to make sure that the server is properly configured to run Internet Server API (ISAPI) applications.</span></span> <span data-ttu-id="f89c2-129">자세한 내용은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-129">For more information, see the IIS documentation.</span></span>  
  
    ```  
    cscript %SystemDrive%\inetpub\AdminScripts\adsutil.vbs set w3svc/AppPools/Enable32bitAppOnWin64 1  
    ```  
  
4.  <span data-ttu-id="f89c2-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 수신기에 대해 적절한 권한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-130">Set the appropriate permissions for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener.</span></span>  
  
5.  <span data-ttu-id="f89c2-131">진단 모드에서 웹 동기화를 실행하여 IIS를 실행하는 컴퓨터에 대한 연결을 테스트하고 SSL 인증서가 제대로 설치되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-131">Run Web synchronization in diagnostic mode to test the connection to the computer that is running IIS and to make sure that the SSL certificate is properly installed.</span></span>  
  
## <a name="configuring-secure-sockets-layer"></a><span data-ttu-id="f89c2-132">SSL(Secure Sockets Layer) 구성</span><span class="sxs-lookup"><span data-stu-id="f89c2-132">Configuring Secure Sockets Layer</span></span>  
 <span data-ttu-id="f89c2-133">SSL을 구성하려면 IIS를 실행하는 컴퓨터에서 사용할 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-133">To configure SSL, specify a certificate for the computer that is running IIS to use.</span></span> <span data-ttu-id="f89c2-134">병합 복제를 위한 웹 동기화에서는 서버 인증서를 사용할 수 있지만 클라이언트 인증서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-134">Web synchronization for merge replication supports using server certificates but not client certificates.</span></span> <span data-ttu-id="f89c2-135">배포를 위해 IIS를 구성하려면 먼저 CA(인증 기관)에서 인증서를 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-135">To configure IIS for deployment, you must first obtain a certificate from a certification authority (CA).</span></span> <span data-ttu-id="f89c2-136">인증 기관은 사용자, 컴퓨터 또는 다른 인증 기관에 속하는 공용 암호화 키의 신뢰성을 수립 및 보증하는 주체입니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-136">A certificate authority is an entity that is responsible for establishing and vouching for the authenticity of public encryption keys that belong to users, computers, or other certification authorities.</span></span> <span data-ttu-id="f89c2-137">인증서에 대한 자세한 내용은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-137">For more information about certificates, see the IIS documentation.</span></span> <span data-ttu-id="f89c2-138">인증서를 설치한 다음에는 웹 동기화에서 사용하는 웹 사이트와 인증서를 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-138">After you install the certificate, you must associate the certificate with the Web site that is used by Web synchronization.</span></span>  
  
#### <a name="to-specify-a-certificate-for-deployment"></a><span data-ttu-id="f89c2-139">배포를 위한 인증서를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="f89c2-139">To specify a certificate for deployment</span></span>  
  
1.  <span data-ttu-id="f89c2-140">IIS를 실행하는 컴퓨터에 관리자로 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-140">Log on to the computer that is running IIS as an administrator.</span></span>  
  
2.  <span data-ttu-id="f89c2-141">**인터넷 정보 서비스(IIS) 관리자**를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-141">Start **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="f89c2-142">**시작**을 클릭한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-142">Click **Start**, and then click **Run**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-143">**열기** 상자에를 입력 한 `inetmgr` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-143">In the **Open** box, type `inetmgr`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f89c2-144">IIS 인증서 마법사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-144">Run the IIS Certificate Wizard:</span></span>  
  
    1.  <span data-ttu-id="f89c2-145">**인터넷 정보 서비스(IIS) 관리자**에서 **로컬 컴퓨터** 노드를 확장한 다음 **웹 사이트** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-145">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand the **Web Sites** folder.</span></span>  
  
    2.  <span data-ttu-id="f89c2-146">**기본 웹 사이트**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-146">Right-click **Default Web Site**, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-147">**기본 웹 사이트 속성** 대화 상자의 **디렉터리 보안** 탭에서 **서버 인증서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-147">In the **Default Web Site Properties** dialog box, on the **Directory Security** tab, click **Server Certificate**.</span></span>  
  
    4.  <span data-ttu-id="f89c2-148">웹 서버 인증서 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-148">Complete the Web Server Certificate Wizard.</span></span>  
  
4.  <span data-ttu-id="f89c2-149">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-149">Click **OK**.</span></span>  
  
 <span data-ttu-id="f89c2-150">CA에서 서버 인증서를 얻을 수 없는 경우에는 테스트용 인증서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-150">If you cannot obtain a server certificate from a CA, you can specify a certificate for testing.</span></span> <span data-ttu-id="f89c2-151">테스트를 위해 IIS 6.0을 구성하려면 SelfSSL 유틸리티를 사용하여 인증서를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-151">To configure IIS 6.0 for testing, install a certificate by using the SelfSSL utility.</span></span> <span data-ttu-id="f89c2-152">이 유틸리티는 IIS 6.0 Resource Kit에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-152">This utility is available in the IIS 6.0 Resource Kit.</span></span> <span data-ttu-id="f89c2-153">[Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=5135)에서 도구를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-153">You can download the tools from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=5135).</span></span> <span data-ttu-id="f89c2-154">IIS 5.0의 경우 [Microsoft 도움말 및 지원](https://go.microsoft.com/fwlink/?LinkId=46229)을 방문하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-154">For IIS 5.0, go to [Microsoft Help and Support](https://go.microsoft.com/fwlink/?LinkId=46229).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f89c2-155">웹 사이트에서 SSL을 사용하려면 먼저 인증서를 웹 사이트에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-155">A certificate must be associated with a Web site before that Web site can use SSL.</span></span> <span data-ttu-id="f89c2-156">SelfSSL에서는 인증서를 자동으로 기본 웹 사이트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-156">SelfSSL automatically associates the certificate with the default Web site.</span></span> <span data-ttu-id="f89c2-157">이미 인증서가 있거나 CA에서 나중에 인증서를 설치할 경우 해당 인증서를 웹 동기화에서 사용하는 웹 사이트에 명시적으로 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-157">If you already have a certificate or later install a certificate from a CA, you must explicitly associate that certificate with the Web site that is used by Web synchronization.</span></span> <span data-ttu-id="f89c2-158">구독 동기화에 사용되는 웹 사이트에는 인증서를 하나만 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-158">Make sure there is only one certificate associated with the Web site that is used to synchronize subscriptions.</span></span> <span data-ttu-id="f89c2-159">인증서를 여러 개 연결하는 경우 구독자는 사용 가능한 첫 번째 웹 사이트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-159">If there are multiple certificates, the Subscriber will use the first available Web site.</span></span>  
  
#### <a name="to-specify-a-certificate-for-testing-in-iis-60"></a><span data-ttu-id="f89c2-160">IIS 6.0에서 테스트를 위해 인증서를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="f89c2-160">To specify a certificate for testing in IIS 6.0</span></span>  
  
1.  <span data-ttu-id="f89c2-161">IIS를 실행하는 컴퓨터에 관리자로 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-161">Log on to the computer that is running IIS as an administrator.</span></span>  
  
2.  <span data-ttu-id="f89c2-162">SelfSSL을 다운로드하고 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-162">Download and install SelfSSL.</span></span> <span data-ttu-id="f89c2-163">응용 프로그램은 기본적으로 다음 위치에 설치 됩니다 \<*drive*> . Files\IIS resources\selfssl에</span><span class="sxs-lookup"><span data-stu-id="f89c2-163">By default, the application is installed to \<*drive*>:\Program Files\IIS Resources\SelfSSL.</span></span> <span data-ttu-id="f89c2-164">응용 프로그램 및 설명서 바로 가기는 \<*drive*> : \Documents and Settings\All Users\Start Menu\Programs\IIS resources\selfssl에에 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-164">Application and documentation shortcuts are copied to \<*drive*>:\Documents and Settings\All Users\Start Menu\Programs\IIS Resources\SelfSSL.</span></span>  
  
3.  <span data-ttu-id="f89c2-165">SelfSSL을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-165">Run SelfSSL:</span></span>  
  
    -   <span data-ttu-id="f89c2-166">모든 매개 변수에 대해 기본값으로 SelfSSL을 실행하려면 이 애플리케이션의 설치 디렉터리를 찾은 다음 SelfSSL.exe를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-166">To run SelfSSL with default values for all parameters, locate the installation directory for the application, and then double-click SelfSSL.exe.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f89c2-167">기본적으로 SelfSSL에서 설치한 인증서는 7일 동안 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-167">By default, the certificate that is installed by SelfSSL is valid for seven days.</span></span>  
  
    -   <span data-ttu-id="f89c2-168">하나 이상의 매개 변수에 대한 값을 지정하려면 **시작**, **실행**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-168">To specify values for one or more parameters: click **Start**, and then click **Run**.</span></span> <span data-ttu-id="f89c2-169">**열기** 상자에를 입력 한 `cmd` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-169">In the **Open** box, enter `cmd`, and then click **OK**.</span></span> <span data-ttu-id="f89c2-170">SelfSSL 설치 디렉터리를 찾고 `SelfSSL`을 입력한 다음 하나 이상의 매개 변수에 대해 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-170">Locate the SelfSSL installation directory, type `SelfSSL`, and then specify values for one or more parameters.</span></span> <span data-ttu-id="f89c2-171">매개 변수 목록을 보려면 `SelfSSL -?`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-171">For a list of parameters, type `SelfSSL -?`.</span></span>  
  
## <a name="installing-connectivity-components-and-sql-server-management-studio"></a><span data-ttu-id="f89c2-172">연결 구성 요소 및 SQL Server Management Studio 설치</span><span class="sxs-lookup"><span data-stu-id="f89c2-172">Installing Connectivity Components and SQL Server Management Studio</span></span>  
  
#### <a name="to-install-sql-server-connectivity-components-and-sql-server-management-studio"></a><span data-ttu-id="f89c2-173">SQL Server 연결 구성 요소 및 SQL Server Management Studio를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="f89c2-173">To install SQL Server connectivity components and SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="f89c2-174">IIS를 실행하는 컴퓨터에 관리자로 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-174">Log on as an administrator to the computer that is running IIS.</span></span>  
  
2.  <span data-ttu-id="f89c2-175">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 설치 디스크에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-175">From the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installation disk, start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span> <span data-ttu-id="f89c2-176">이 마법사를 사용 하는 방법에 대 한 자세한 내용은 설치 [마법사 &#40;설치&#41;에서 SQL Server 2014 설치 ](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f89c2-176">For more information about using this wizard, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
3.  <span data-ttu-id="f89c2-177">**기능 선택** 페이지에서 **클라이언트 도구 연결**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-177">On the **Feature Selection** page, select **Client Tools Connectivity**.</span></span>  
  
4.  <span data-ttu-id="f89c2-178">웹 동기화 구성 마법사를 사용하려면 **관리 도구 - 기본**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-178">If you plan to use the Configure Web Synchronization Wizard, select **Management Tools - Basic**.</span></span>  
  
5.  <span data-ttu-id="f89c2-179">마법사를 완료한 다음 컴퓨터를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-179">Complete the wizard, and then restart the computer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f89c2-180">추가 구성 요소를 설치할 수도 있지만 웹 동기화를 위해서는 연결 구성 요소만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-180">You can install additional components, but only the connectivity components are required for Web synchronization.</span></span>  
  
## <a name="configuring-the-computer-that-is-running-iis-by-using-the-configure-web-synchronization-wizard"></a><span data-ttu-id="f89c2-181">웹 동기화 구성 마법사를 사용하여 IIS를 실행하는 컴퓨터 구성</span><span class="sxs-lookup"><span data-stu-id="f89c2-181">Configuring the Computer That Is Running IIS by Using the Configure Web Synchronization Wizard</span></span>  
 <span data-ttu-id="f89c2-182">웹 동기화 구성 마법사를 사용하거나 수동으로 IIS 서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-182">Configure the IIS server by using the Configure Web Synchronization Wizard or manually.</span></span> <span data-ttu-id="f89c2-183">마법사를 사용하는 것이 좋지만 다음 섹션에서는 수동 구성 단계도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-183">We recommend using the wizard, but we also provide steps for manual configuration in the next section.</span></span> <span data-ttu-id="f89c2-184">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 에서 제공되는 웹 동기화 마법사는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]을 실행하는 게시자 또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]로 업그레이드된 게시자에서 만들어진 게시에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-184">The Web Synchronization Wizard that is available with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] can be used only for publications that were created on a Publisher that is running [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], or a Publisher that was upgraded to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="f89c2-185">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]의 게시에서는 이 마법사를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-185">The wizard cannot be used for publications on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="f89c2-186">이 마법사는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전 및 [!INCLUDE[ssEWnoversion](../../includes/ssewnoversion-md.md)] 3.0 이상 버전의 구독에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-186">The wizard can be used with subscriptions on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, and [!INCLUDE[ssEWnoversion](../../includes/ssewnoversion-md.md)] 3.0 and later versions.</span></span>  
  
 <span data-ttu-id="f89c2-187">구성의 특징은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-187">The configuration has the following characteristics:</span></span>  
  
-   <span data-ttu-id="f89c2-188">IIS에서 기본 웹 사이트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-188">Uses the default Web site in IIS.</span></span> <span data-ttu-id="f89c2-189">그러나 다른 웹 사이트를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-189">However, you can use another Web site.</span></span> <span data-ttu-id="f89c2-190">웹 사이트를 만드는 방법은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-190">For more information about how to create Web sites, see the IIS documentation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f89c2-191">사용자가 지정하는 웹 사이트를 통해 웹 동기화에서 사용하는 구성 요소에 액세스할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="f89c2-191">The Web site that you specify provides access to the components that are used by Web synchronization.</span></span> <span data-ttu-id="f89c2-192">이 웹 사이트를 통해 다른 데이터나 웹 페이지에 액세스하려면 별도의 구성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-192">The Web site does not provide access to other data or Web pages unless you configure the site to do so.</span></span>  
  
-   <span data-ttu-id="f89c2-193">가상 디렉터리 및 관련 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-193">Creates a virtual directory and its associated alias.</span></span> <span data-ttu-id="f89c2-194">별칭은 웹 동기화 구성 요소에 액세스할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-194">The alias is used when accessing the Web synchronization components.</span></span> <span data-ttu-id="f89c2-195">예를 들어 IIS 주소가 `https://*server.domain.com*`이고 'websync1'이라는 별칭을 지정하면 replisapi.dll 구성 요소에 액세스하기 위한 주소는 `https://*server.domain.com*/websync1/replisapi.dll` 이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-195">For example, if the IIS address is `https://*server.domain.com*` and you specify an alias of 'websync1', the address to access the replisapi.dll component is `https://*server.domain.com*/websync1/replisapi.dll`.</span></span>  
  
-   <span data-ttu-id="f89c2-196">기본 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-196">Uses Basic Authentication.</span></span> <span data-ttu-id="f89c2-197">기본 인증을 사용하면 Kerberos 위임 없이도 IIS와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자/배포자를 서로 다른 컴퓨터에서 실행(권장 구성)할 수 있으므로 기본 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-197">We recommend using Basic Authentication because Basic Authentication enables you to run IIS and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher/Distributor on separate computers (the recommended configuration) without requiring Kerberos delegation.</span></span> <span data-ttu-id="f89c2-198">기본 인증과 함께 SSL을 사용하면 로그인, 암호 및 모든 데이터가 전송 중에 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-198">Using SSL with Basic Authentication makes sure that logins, passwords, and all data are encrypted in transit.</span></span> <span data-ttu-id="f89c2-199">사용 되는 인증 유형에 관계 없이 SSL이 필요 합니다. 웹 동기화에 대 한 모범 사례에 대 한 자세한 내용은 [웹 동기화 구성](configure-web-synchronization.md)에서 "웹 동기화에 대 한 최상의 보안 방법" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f89c2-199">(SSL is required, regardless of the type of authentication that is used.) For more information about best practices for Web synchronization, see the section "Security Best Practices for Web Synchronization" in [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
#### <a name="to-configure-the-computer-that-is-running-iis-by-using-the-configure-web-synchronization-wizard"></a><span data-ttu-id="f89c2-200">웹 동기화 구성 마법사를 사용하여 IIS를 실행하는 컴퓨터를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f89c2-200">To configure the computer that is running IIS by using the Configure Web Synchronization Wizard</span></span>  
  
1.  <span data-ttu-id="f89c2-201">IIS를 실행하는 컴퓨터에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-201">On the computer that is running IIS, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="f89c2-202">게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-202">Connect to the Publisher, and then expand the server node.</span></span>  
  
3.  <span data-ttu-id="f89c2-203">**로컬 게시** 폴더를 확장하고 해당 게시를 마우스 오른쪽 단추로 클릭한 다음 **웹 동기화 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-203">Expand the **Local Publications** folder, right-click the publication, and then click **Configure Web Synchronization**.</span></span>  
  
4.  <span data-ttu-id="f89c2-204">웹 동기화 구성 마법사의 **구독자 유형** 페이지에서 **SQL Server**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-204">In the Configure Web Synchronization Wizard, on the **Subscriber Type** page, select **SQL Server**.</span></span>  
  
5.  <span data-ttu-id="f89c2-205">**웹 서버** 페이지에서 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-205">On the **Web Server** page:</span></span>  
  
    1.  <span data-ttu-id="f89c2-206">구독을 동기화할 IIS 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-206">Select the instance of IIS that will synchronize subscriptions.</span></span>  
  
    2.  <span data-ttu-id="f89c2-207">**새 가상 디렉터리 만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-207">Select **Create a new virtual directory**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-208">페이지의 아래 창에서 IIS 인스턴스를 확장하고 **웹 사이트**를 확장한 다음 **기본 웹 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-208">In the lower pane of the page, expand the instance of IIS, expand **Web Sites**, and then click **Default Web Site**.</span></span>  
  
6.  <span data-ttu-id="f89c2-209">**가상 디렉터리 정보** 페이지에서 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-209">On the **Virtual Directory Information** page:</span></span>  
  
    1.  <span data-ttu-id="f89c2-210">**별칭** 상자에 가상 디렉터리의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-210">In the **Alias** box, enter an alias for the virtual directory.</span></span>  
  
    2.  <span data-ttu-id="f89c2-211">**경로** 상자에 가상 디렉터리의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-211">In the **Path** box, enter a path of the virtual directory.</span></span> <span data-ttu-id="f89c2-212">예를 들어 `websync1` **별칭** 상자에를 입력 한 경우 `C:\Inetpub\wwwroot\websync1` **경로** 상자에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-212">For example, if you entered `websync1` in the **Alias** box, enter `C:\Inetpub\wwwroot\websync1` in the **Path** box.</span></span> <span data-ttu-id="f89c2-213">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-213">Click **Next**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-214">두 대화 상자에서 모두 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-214">On both dialog boxes, click **Yes**.</span></span> <span data-ttu-id="f89c2-215">새 폴더가 생성되고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ISAPI(Internet Server API) DLL이 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-215">This specifies that you want to create a new folder and that you want to copy the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Internet Server API (ISAPI) DLL.</span></span> <span data-ttu-id="f89c2-216">.</span><span class="sxs-lookup"><span data-stu-id="f89c2-216">.</span></span>  
  
7.  <span data-ttu-id="f89c2-217">**인증된 액세스** 페이지에서 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-217">On the **Authenticated Access** page:</span></span>  
  
    1.  <span data-ttu-id="f89c2-218">**Windows 통합 인증** 및 **Windows 도메인 서버의 다이제스트 인증** 의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-218">Make sure that **Integrated Windows authentication** and **Digest authentication for Windows domain servers** are cleared.</span></span>  
  
    2.  <span data-ttu-id="f89c2-219">**기본 인증**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-219">Select **Basic Authentication**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-220">**기본 도메인** 및 **영역** 상자에 IIS를 실행하는 컴퓨터의 도메인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-220">In the **Default Domain** and **Realm** boxes, enter the domain of the computer that is running IIS.</span></span>  
  
8.  <span data-ttu-id="f89c2-221">**디렉터리 액세스** 페이지에서 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-221">On the **Directory Access** page:</span></span>  
  
    1.  <span data-ttu-id="f89c2-222">**추가**를 클릭한 다음 **사용자 또는 그룹 선택** 대화 상자에서 구독자가 IIS 연결에 사용할 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-222">Click **Add**, and then in the **Select Users or Groups** dialog box, add the accounts under which Subscribers will make connections to IIS.</span></span> <span data-ttu-id="f89c2-223">이러한 계정은 새 구독 마법사의 **웹 서버 정보** 페이지에서 지정하거나 [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)*@internet_login* 매개 변수의 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-223">These are the accounts that you will specify on the **Web Server Information** page of the New Subscription Wizard or as the value for the [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)*@internet_login* parameter.</span></span>  
  
9. <span data-ttu-id="f89c2-224">**스냅샷 공유 액세스** 페이지에서 스냅샷 공유를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-224">On the **Snapshot Share Access** page, enter the snapshot share.</span></span> <span data-ttu-id="f89c2-225">구독자가 스냅샷 파일에 액세스할 수 있도록 이 공유에는 적절한 사용 권한이 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-225">The appropriate permissions are set on this share so that Subscribers can access the snapshot files.</span></span> <span data-ttu-id="f89c2-226">공유 사용 권한에 대한 자세한 내용은 [스냅샷 폴더 보안 설정](security/secure-the-snapshot-folder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f89c2-226">For more information about permissions for the share, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span>  
  
10. <span data-ttu-id="f89c2-227">**마법사 완료** 페이지에서 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-227">On the **Completing the Wizard** page, click **Finish**.</span></span>  
  
     <span data-ttu-id="f89c2-228">IIS를 실행하는 원격 컴퓨터를 구성하는 동안 네트워크 오류와 같은 오류가 발생하면 완료된 모든 동작이 롤백되고 남은 동작이 모두 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-228">If a failure occurs, such as a network error while trying to configure a remote computer that is running IIS, all completed actions are rolled back and all remaining actions are canceled.</span></span> <span data-ttu-id="f89c2-229">완료된 동작을 롤백할 수 없으면 마법사의 마지막 페이지에 나타나는 상태는 **성공** 으로 표시되고 완료된 동작은 커밋된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-229">If a completed action cannot be rolled back, the status in the final page of the wizard displays **Success** and the completed actions remain committed.</span></span>  
  
11. <span data-ttu-id="f89c2-230">IIS를 실행하는 컴퓨터에서 64비트 버전의 Windows를 실행 중인 경우 replisapi.dll을 해당 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-230">If the computer that is running IIS is running on a 64-bit version of Windows, replisapi.dll must be copied to the appropriate directory:</span></span>  
  
    1.  <span data-ttu-id="f89c2-231">**시작**을 클릭한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-231">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="f89c2-232">**열기** 상자에를 입력 한 `iisreset` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-232">In the **Open** box, enter `iisreset`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-233">IIS를 중지했다가 다시 시작한 다음 [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\replisapi에 있는 replisapi.dll을 6b단계에서 지정한 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-233">After IIS stops and restarts, copy replisapi.dll from [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]COM\replisapi to the directory that is specified in step 6b.</span></span>  
  
    3.  <span data-ttu-id="f89c2-234">**시작**을 클릭한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-234">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="f89c2-235">**열기** 상자에를 입력 한 `cmd` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-235">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="f89c2-236">6b단계에서 지정한 디렉터리에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-236">In the directory that you specified in step 6b, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
## <a name="manually-configuring-the-computer-that-is-running-iis"></a><span data-ttu-id="f89c2-237">IIS를 실행하는 컴퓨터를 수동으로 구성</span><span class="sxs-lookup"><span data-stu-id="f89c2-237">Manually Configuring the Computer That Is Running IIS</span></span>  
 <span data-ttu-id="f89c2-238">IIS를 실행하는 컴퓨터를 수동으로 구성하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 수신기를 설치하고 구성한 다음 IIS에 연결할 구독자에 대해 권한을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-238">To configure the computer that is running IIS manually, you must install and configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener, and then configure authorization for Subscribers that will connect to IIS.</span></span>  
  
#### <a name="to-install-and-configure-the-sql-server-replication-listener"></a><span data-ttu-id="f89c2-239">SQL Server 복제 수신기를 설치 및 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f89c2-239">To install and configure the SQL Server Replication Listener</span></span>  
  
1.  <span data-ttu-id="f89c2-240">IIS를 실행하는 컴퓨터에 replisapi.dll을 포함시킬 파일 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-240">Create a file directory on the computer that is running IIS to contain replisapi.dll.</span></span> <span data-ttu-id="f89c2-241">원하는 위치에 이 디렉터리를 만들 수 있지만 \<*drive*>:\Inetpub 디렉터리 아래에 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-241">You can create the directory wherever you want, but we recommend that you create the directory under the \<*drive*>:\Inetpub directory.</span></span> <span data-ttu-id="f89c2-242">예를 들어 \<*drive*>:\Inetpub\SQLReplication\\ 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-242">For example, create the directory \<*drive*>:\Inetpub\SQLReplication\\.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f89c2-243">이 디렉터리는 FAT 파일 시스템이 아닌 NTFS 파일 시스템 파티션에 만드는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-243">We strongly recommend that you create this directory on an NTFS file system partition instead of a FAT file system.</span></span> <span data-ttu-id="f89c2-244">NTFS 파일 시스템을 사용하면 NTFS 파일 시스템 권한을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제에 액세스할 수 있는 사용자를 정확하게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-244">When you use the NTFS file system, you can use NTFS file system permissions to control precisely the users that can access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
2.  <span data-ttu-id="f89c2-245">[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ 디렉터리에 있는 replisapi.dll을 1단계에서 만든 파일 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-245">Copy replisapi.dll from the directory [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ to the file directory that you created in step 1.</span></span>  
  
3.  <span data-ttu-id="f89c2-246">replisapi.dll을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-246">Register replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="f89c2-247">**시작**을 클릭한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-247">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="f89c2-248">**열기** 상자에를 입력 한 `cmd` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-248">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-249">1단계에서 만든 디렉터리에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-249">In the directory that you created in step 1, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
4.  <span data-ttu-id="f89c2-250">복제를 위한 새 웹 사이트를 만들거나 기존 사이트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-250">Create a new Web site for replication, or use an existing site.</span></span> <span data-ttu-id="f89c2-251">이 웹 사이트는 동기화를 수행하는 동안 복제 구성 요소에서 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-251">The Web site will be accessed by replication components during synchronization.</span></span> <span data-ttu-id="f89c2-252">웹 사이트를 만드는 방법은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-252">For more information about how to create Web sites, see the IIS documentation.</span></span>  
  
5.  <span data-ttu-id="f89c2-253">IIS에 가상 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-253">Create a virtual directory in IIS.</span></span> <span data-ttu-id="f89c2-254">가상 디렉터리는 4단계에서 만든 웹 사이트 아래에 만들어야 하며 1단계에서 만든 디렉터리에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-254">The virtual directory should be created under the Web site that was created in step 4, and should be mapped to the directory that was created in step 1.</span></span> <span data-ttu-id="f89c2-255">가상 디렉터리를 만드는 방법은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-255">For more information about how to create virtual directories, see the IIS documentation.</span></span> <span data-ttu-id="f89c2-256">이 디렉터리에 대한 사용 권한은 가능한 제한적으로 할당하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-256">We recommend that you be as restrictive as possible when you assign permissions to this directory.</span></span> <span data-ttu-id="f89c2-257">**읽기** 및 **실행** 권한은 선택해야 하지만 **스크립트 실행**, **쓰기**및 **찾아보기** 권한은 선택하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-257">You must select **Read** and **Execute** permissions, but you can clear **Run scripts**, **Write**, and **Browse** permissions.</span></span>  
  
6.  <span data-ttu-id="f89c2-258">replisapi.dll이 실행될 수 있도록 IIS를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-258">Configure IIS to enable replisapi.dll to execute.</span></span> <span data-ttu-id="f89c2-259">이전 버전의 IIS에서는 4단계에서 할당한 사용 권한만으로도 충분하지만 IIS 버전 6.0에서는 ISAPI(Internet Server API) 확장을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-259">The permissions that are assigned in step 4 are sufficient for earlier versions of IIS; however, IIS version 6.0 requires Internet Server API (ISAPI) extensions to be enabled.</span></span> <span data-ttu-id="f89c2-260">자세한 내용은 IIS 6.0 설명서의 "ISAPI 확장 구성" 및 "동적 콘텐트 사용 설정 및 해제"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-260">For more information, see "Configuring ISAPI Extensions" and "Enabling and Disabling Dynamic Content" in the IIS 6.0 documentation.</span></span>  
  
#### <a name="to-configure-iis-authentication"></a><span data-ttu-id="f89c2-261">IIS 인증을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f89c2-261">To configure IIS authentication</span></span>  
  
-   <span data-ttu-id="f89c2-262">구독자가 IIS에 연결한 다음 리소스 및 프로세스에 액세스하려면 먼저 IIS에서 해당 구독자를 인증해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-262">When Subscribers connect to IIS, IIS must authenticate the Subscribers before they can access resources and processes.</span></span> <span data-ttu-id="f89c2-263">IIS는 익명, 기본 및 통합의 3가지 인증 유형을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-263">IIS offers three types of authentication: Anonymous, Basic, and Integrated.</span></span> <span data-ttu-id="f89c2-264">인증은 전체 웹 사이트나 사용자가 만든 가상 디렉터리에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-264">Authentication can be applied to the whole Web site or to the virtual directory that you created.</span></span>  
  
     <span data-ttu-id="f89c2-265">기본 인증과 함께 SSL을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-265">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="f89c2-266">SSL은 사용하는 인증 유형에 관계없이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-266">SSL is required, regardless of the type of authentication that is used.</span></span> <span data-ttu-id="f89c2-267">인증을 구성하는 방법은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-267">For more information about how to configure authentication, see the IIS documentation.</span></span>  
  
## <a name="setting-permissions-for-the-sql-server-replication-listener"></a><span data-ttu-id="f89c2-268">SQL Server 복제 수신기에 대한 사용 권한 설정</span><span class="sxs-lookup"><span data-stu-id="f89c2-268">Setting Permissions for the SQL Server Replication Listener</span></span>  
 <span data-ttu-id="f89c2-269">구독자가 IIS를 실행하는 컴퓨터에 연결하면 IIS 구성 시 지정한 인증 유형을 사용하여 해당 구독자가 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-269">When a Subscriber connects to the computer that is running IIS, the Subscriber is authenticated by using the type of authentication that was specified when you configured IIS.</span></span> <span data-ttu-id="f89c2-270">IIS에서는 구독자를 인증한 다음 해당 구독자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제를 호출할 수 있는 권한이 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-270">After IIS authenticates the Subscriber, IIS checks whether the Subscriber is authorized to invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="f89c2-271">replisapi.dll에 대한 권한을 설정하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제를 호출할 수 있는 사용자를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-271">You control the users that can invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication by setting permissions for replisapi.dll.</span></span> <span data-ttu-id="f89c2-272">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제에 무단으로 액세스하지 못하도록 하려면 사용 권한을 적절하게 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-272">Properly configuring permissions is necessary to prevent unauthorized access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
 <span data-ttu-id="f89c2-273">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 수신기를 실행할 계정에 대해 최소 사용 권한을 구성하려면 다음 절차를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-273">To configure the minimum permissions for the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener runs, complete the following procedure.</span></span> <span data-ttu-id="f89c2-274">이 절차의 단계는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] IIS 6.0 실행에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-274">The steps in the procedure apply to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] running IIS 6.0.</span></span>  
  
 <span data-ttu-id="f89c2-275">다음 단계를 수행한 다음에는 PAL(게시 액세스 목록)에 필요한 로그인을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-275">In addition to performing the following steps, make sure that the required logins are in the publication access list (PAL).</span></span> <span data-ttu-id="f89c2-276">PAL에 대한 자세한 내용은 [게시자 보안 설정](security/secure-the-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f89c2-276">For more information about the PAL, see [Secure the Publisher](security/secure-the-publisher.md).</span></span>  
  
#### <a name="to-configure-the-account-and-permissions"></a><span data-ttu-id="f89c2-277">계정 및 사용 권한을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f89c2-277">To configure the account and permissions</span></span>  
  
1.  <span data-ttu-id="f89c2-278">IIS를 실행하는 컴퓨터에 로컬 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-278">Create a local account on the computer that is running IIS:</span></span>  
  
    1.  <span data-ttu-id="f89c2-279">**내 컴퓨터**를 마우스 오른쪽 단추로 클릭한 다음 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-279">Right-click **My Computer**, and then click **Manage**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-280">**컴퓨터 관리**에서 **로컬 사용자 및 그룹**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-280">In **Computer Management**, expand **Local Users and Groups**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-281">**사용자**를 마우스 오른쪽 단추로 클릭한 다음 **새 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-281">Right-click **Users**, and then click **New User**.</span></span>  
  
    4.  <span data-ttu-id="f89c2-282">사용자 이름과 강력한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-282">Enter a user name and a strong password.</span></span>  
  
    5.  <span data-ttu-id="f89c2-283">**만들기**를 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-283">Click **Create**, and then click **Close**.</span></span>  
  
2.  <span data-ttu-id="f89c2-284">IIS_WPG 그룹에 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-284">Add the account to the IIS_WPG group:</span></span>  
  
    1.  <span data-ttu-id="f89c2-285">**컴퓨터 관리**에서 **로컬 사용자 및 그룹**을 확장한 다음 **그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-285">In **Computer Management**, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-286">**IIS_WPG**를 마우스 오른쪽 단추로 클릭한 다음 **그룹에 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-286">Right-click **IIS_WPG**, and then click **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-287">**IIS_WPG 속성** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-287">In the **IIS_WPG Properties** dialog box, click **Add**.</span></span>  
  
    4.  <span data-ttu-id="f89c2-288">**사용자, 컴퓨터 또는 그룹 선택** 대화 상자에 1단계에서 만든 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-288">In the **Select Users, Computers, or Groups** dialog box, add the account created in step 1.</span></span>  
  
    5.  <span data-ttu-id="f89c2-289">**다음 위치에서** 필드에 도메인이 아닌 로컬 컴퓨터 이름이 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-289">Make sure that the name in the **From this location** field is the name of the local computer instead of a domain.</span></span> <span data-ttu-id="f89c2-290">로컬 컴퓨터 이름이 아닌 경우 **위치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-290">If the name is not a local computer, click **Locations**.</span></span> <span data-ttu-id="f89c2-291">**위치** 대화 상자에서 로컬 컴퓨터를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-291">In the **Locations** dialog box, elect the local computer, and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="f89c2-292">**사용자 선택** 대화 상자 및 **IIS_WPG 속성** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-292">In the **Select Users** dialog box and the **IIS_WPG Properties** dialog box, click **OK**.</span></span>  
  
3.  <span data-ttu-id="f89c2-293">계정에 대한 replisapi.dll을 포함하는 폴더에 최소 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-293">Grant the minimum permissions on the folder that contains replisapi.dll to the account :</span></span>  
  
    1.  <span data-ttu-id="f89c2-294">replisapi.dll에 대해 만든 폴더를 찾아서 마우스 오른쪽 단추로 클릭한 다음 **공유 및 보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-294">Locate the folder that you created for replisapi.dll, right-click the folder, and then click **Sharing and Security**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-295">**보안** 탭에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-295">On the **Security** tab, click **Add**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-296">**사용자, 컴퓨터 또는 그룹 선택** 대화 상자에 1단계에서 만든 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-296">In the **Select Users, Computers, or Groups** dialog box, add the account that you created in step 1.</span></span>  
  
    4.  <span data-ttu-id="f89c2-297">**다음 위치에서** 필드에 도메인이 아닌 로컬 컴퓨터 이름이 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-297">Make sure that the name in the **From this location** field is the name of the local computer instead of a domain.</span></span> <span data-ttu-id="f89c2-298">로컬 컴퓨터 이름이 아닌 경우 **위치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-298">If the name is not a local computer, click **Locations**.</span></span> <span data-ttu-id="f89c2-299">**위치** 대화 상자에서 로컬 컴퓨터를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-299">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="f89c2-300">계정에 **읽기**, **읽기 및 실행** 및 **폴더 내용 보기** 권한만 부여되었는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="f89c2-300">Make sure that the account is granted only **Read**, **Read & Execute**, and **List Folder Contents** permissions.</span></span>  
  
    6.  <span data-ttu-id="f89c2-301">디렉터리에 대한 액세스가 필요 없는 사용자나 그룹을 선택한 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-301">Select any users or groups that do not require access to the directory, and then click **Remove**.</span></span>  
  
    7.  <span data-ttu-id="f89c2-302">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-302">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="f89c2-303">**인터넷 정보 서비스(IIS) 관리자**에서 애플리케이션 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-303">Create an application pool in **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="f89c2-304">**시작**을 클릭한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-304">Click **Start**, and then click **Run**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-305">**열기** 상자에를 입력 한 `inetmgr` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-305">In the **Open** box, type `inetmgr`, and then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-306">**인터넷 정보 서비스(IIS) 관리자**에서 **로컬 컴퓨터** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-306">In **Internet Information Services (IIS) Manager**, expand the **local computer** node.</span></span>  
  
    4.  <span data-ttu-id="f89c2-307">**애플리케이션 풀**을 마우스 오른쪽 단추로 클릭하고 **새로 만들기** 를 가리킨 다음 **애플리케이션 풀**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-307">Right-click **Application Pools**, point to **New** and then click **Application Pool**.</span></span>  
  
    5.  <span data-ttu-id="f89c2-308">**애플리케이션 풀 ID** 필드에 풀 이름을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-308">Enter a name for the pool in the **Application pool ID** field, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="f89c2-309">계정과 애플리케이션 풀을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-309">Associate the account with the application pool:</span></span>  
  
    1.  <span data-ttu-id="f89c2-310">**인터넷 정보 서비스(IIS) 관리자**에서 **로컬 컴퓨터** 노드를 확장한 다음 **애플리케이션 풀**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-310">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand **Application Pools**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-311">만든 애플리케이션 풀을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-311">Right-click the application pool that you created, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-312">\*\* \<ApplicationPoolName> 속성\*\* 대화 상자의 **Id** 탭에서 **구성 가능**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-312">In the **\<ApplicationPoolName> Properties** dialog box, on the **Identity** tab, click **Configurable**.</span></span>  
  
    4.  <span data-ttu-id="f89c2-313">**사용자 이름** 및 **암호** 필드에 1단계에서 만든 계정과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-313">In the **User name** and **password** fields, enter the account and password that were created in step 1.</span></span>  
  
    5.  <span data-ttu-id="f89c2-314">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-314">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="f89c2-315">웹 동기화에 사용되는 가상 디렉터리와 애플리케이션 풀을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-315">Associate the application pool with the virtual directory that is used for Web synchronization:</span></span>  
  
    1.  <span data-ttu-id="f89c2-316">**인터넷 정보 서비스(IIS) 관리자**에서 **로컬 컴퓨터** 노드를 확장한 다음 **웹 사이트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-316">In **Internet Information Services (IIS) Manager**, expand the **local computer** node, and then expand **Web Sites**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-317">웹 동기화에 사용 중인 웹 사이트를 확장하고 웹 동기화를 위해 만든 가상 디렉터리를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-317">Expand the Web site that you are using for Web synchronization, right-click the virtual directory that you created for Web synchronization, and then click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-318">\*\* \<VirtualDirectoryName> 속성\*\* 대화 상자의 **가상 디렉터리** 탭에 있는 **응용 프로그램 풀** 드롭다운 목록에서 5 단계에서 만든 응용 프로그램 풀을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-318">On the **Virtual Directory** tab of the **\<VirtualDirectoryName> Properties** dialog box, from the **Application pool** drop-down list, select the application pool that was created in step 5.</span></span>  
  
    4.  <span data-ttu-id="f89c2-319">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-319">Click **OK**.</span></span>  
  
## <a name="testing-the-connection-to-replisapidll"></a><span data-ttu-id="f89c2-320">replisapi.dll에 대한 연결 테스트</span><span class="sxs-lookup"><span data-stu-id="f89c2-320">Testing the Connection to replisapi.dll</span></span>  
 <span data-ttu-id="f89c2-321">진단 모드에서 웹 동기화를 실행하여 IIS를 실행하는 컴퓨터에 대한 연결을 테스트하고 SSL(Secure Sockets Layer) 인증서가 제대로 설치되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-321">Run Web synchronization in diagnostic mode to test the connection to the computer that is running IIS and to make sure that the Secure Sockets Layer (SSL) certificate is properly installed.</span></span> <span data-ttu-id="f89c2-322">진단 모드에서 웹 동기화를 실행하려면 IIS가 실행되는 컴퓨터의 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-322">To run Web synchronization in diagnostic mode, you must be an administrator on the computer running IIS.</span></span>  
  
#### <a name="to-test-the-connection-to-replisapidll"></a><span data-ttu-id="f89c2-323">replisapi.dll에 대한 연결을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="f89c2-323">To test the connection to replisapi.dll</span></span>  
  
1.  <span data-ttu-id="f89c2-324">구독자의 LAN(Local Area Network) 설정이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-324">Make sure that local area network (LAN) settings at the Subscriber are correct:</span></span>  
  
    1.  <span data-ttu-id="f89c2-325">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer의 **도구** 메뉴에서 **인터넷 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-325">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, on the **Tools** menu, click **Internet Options**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-326">**연결** 탭에서 **LAN 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-326">On the **Connections** tab, click **LAN Settings**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-327">LAN에 프록시 서버가 사용되지 않는 경우 **자동으로 설정 검색** 및 **사용자 LAN에 프록시 서버 사용**의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-327">If a proxy server is not used on the LAN, clear **Automatically Detect Settings** and **Use a proxy server for your LAN**.</span></span>  
  
    4.  <span data-ttu-id="f89c2-328">프록시 서버가 사용되는 경우 **사용자 LAN에 프록시 서버 사용** 및 **로컬 주소에 프록시 서버 사용 안 함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-328">If a proxy server is used, select **Use a proxy server for your LAN** and **Bypass proxy server for local addresses**.</span></span>  
  
    5.  <span data-ttu-id="f89c2-329">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-329">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="f89c2-330">구독자에서는 Internet Explorer에서 replisapi.dll에 대한 주소에 `?diag` (예:</span><span class="sxs-lookup"><span data-stu-id="f89c2-330">At the Subscriber, in Internet Explorer, connect to the server in diagnostic mode by appending `?diag` to the address for the replisapi.dll.</span></span> <span data-ttu-id="f89c2-331">예: `https://server.domain.com/directory/replisapi.dll?diag`</span><span class="sxs-lookup"><span data-stu-id="f89c2-331">For example: `https://server.domain.com/directory/replisapi.dll?diag`.</span></span>  
  
3.  <span data-ttu-id="f89c2-332">IIS에 대해 지정한 인증서를 Windows 운영 체제에서 인식하지 못할 경우 **보안 경고** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-332">If the certificate that you specified for IIS is not recognized by the Windows operating system, the **Security Alert** dialog box appears.</span></span> <span data-ttu-id="f89c2-333">이 경고는 인증서가 테스트 인증서이거나 Windows에서 인식할 수 없는 CA(인증 기관)에서 발급한 인증서이기 때문에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-333">This alert might occur because the certificate is a test certificate or the certificate was issued by a certification authority (CA) that Windows does not recognize.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f89c2-334">이 대화 상자가 나타나지 않으면 액세스하는 서버에 대한 인증서가 구독자의 인증서 저장소에 신뢰할 수 있는 인증서로 추가되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-334">If this dialog box does not appear, make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="f89c2-335">인증서를 내보내는 방법은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-335">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
    1.  <span data-ttu-id="f89c2-336">**보안 경고** 대화 상자에서 **인증서 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-336">In the **Security Alert** dialog box, click **View Certificate**.</span></span>  
  
    2.  <span data-ttu-id="f89c2-337">**인증서** 대화 상자의 **일반** 탭에서 **인증서 설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-337">In the **Certificate** dialog box, on the **General** tab, click **Install Certificate**.</span></span>  
  
    3.  <span data-ttu-id="f89c2-338">기본값을 적용한 후 인증서 가져오기 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-338">Complete the Certificate Import Wizard, accepting the defaults.</span></span>  
  
    4.  <span data-ttu-id="f89c2-339">**보안 경고** 대화 상자에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-339">In the **Security Warning** dialog box, click **Yes**.</span></span>  
  
    5.  <span data-ttu-id="f89c2-340">인증서 가져오기 마법사 확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-340">In the Certificate Import Wizard confirmation dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="f89c2-341">**인증서** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-341">Close the **Certificate** dialog box.</span></span>  
  
    7.  <span data-ttu-id="f89c2-342">**보안 경고** 대화 상자에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-342">In the **Security Alert** dialog box, click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f89c2-343">인증서는 사용자에 대해 설치되므로</span><span class="sxs-lookup"><span data-stu-id="f89c2-343">Certificates are installed for users.</span></span> <span data-ttu-id="f89c2-344">IIS와 동기화할 각 사용자에 대해 이 프로세스를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-344">This process must be performed for each user that will synchronize with IIS.</span></span>  
  
4.  <span data-ttu-id="f89c2-345">**\<ServerName>에 연결** 대화 상자에서 병합 에이전트가 IIS에 연결하는 데 사용할 로그인 및 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-345">In the **Connect to \<ServerName>** dialog box, specify the login and password that the Merge Agent will use to connect to IIS.</span></span> <span data-ttu-id="f89c2-346">이러한 자격 증명은 새 구독 마법사에서도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-346">These credentials will also be specified in the New Subscription Wizard.</span></span>  
  
5.  <span data-ttu-id="f89c2-347">**SQL Websync 진단 정보**라는 Internet Explorer 창에서 페이지의 각 **상태** 열 값이 **SUCCESS**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-347">In the Internet Explorer window called **SQL Websync diagnostic information**, verify that the value in each **Status** column on the page is **SUCCESS**.</span></span>  
  
6.  <span data-ttu-id="f89c2-348">구독자에 인증서가 올바르게 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-348">Make sure that the certificate is installed correctly on the Subscriber:</span></span>  
  
    1.  <span data-ttu-id="f89c2-349">Internet Explorer를 닫았다가 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-349">Close and then reopen Internet Explorer.</span></span>  
  
    2.  <span data-ttu-id="f89c2-350">진단 모드에서 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-350">Connect to the server in diagnostic mode.</span></span> <span data-ttu-id="f89c2-351">인증서가 제대로 설치된 경우 **보안 경고** 대화 상자가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-351">If the certificate is installed properly, the **Security Alert** dialog box will not appear.</span></span> <span data-ttu-id="f89c2-352">이 대화 상자가 나타나면 병합 에이전트가 IIS를 실행하는 컴퓨터에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-352">If the dialog box appears, the Merge Agent will fail when it tries to connect to the computer that is running IIS.</span></span> <span data-ttu-id="f89c2-353">액세스하는 서버에 대한 인증서가 구독자의 인증서 저장소에 신뢰할 수 있는 인증서로 추가되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f89c2-353">You must make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="f89c2-354">인증서를 내보내는 방법은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f89c2-354">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89c2-355">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f89c2-355">See Also</span></span>  
 [<span data-ttu-id="f89c2-356">웹 동기화 구성</span><span class="sxs-lookup"><span data-stu-id="f89c2-356">Configure Web Synchronization</span></span>](configure-web-synchronization.md)  
  
  
