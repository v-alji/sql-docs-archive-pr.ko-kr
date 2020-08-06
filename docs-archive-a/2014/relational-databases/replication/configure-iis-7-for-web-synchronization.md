---
title: 웹 동기화를 위한 IIS 7 구성 | Microsoft 문서
ms.custom: ''
ms.date: 09/12/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- IIS 7 server configuration [SQL Server replication]
- Web synchronization, IIS 7 servers
ms.assetid: c201fe2c-0a76-44e5-a233-05e14cd224a6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 65b5aa1ea0d314a9675b1c1b90b688d2990e6d24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661641"
---
# <a name="configure-iis-7-for-web-synchronization"></a><span data-ttu-id="ea163-102">웹 동기화를 위한 IIS 7 구성</span><span class="sxs-lookup"><span data-stu-id="ea163-102">Configure IIS 7 for Web Synchronization</span></span>
  <span data-ttu-id="ea163-103">이 항목의 절차에서는 병합 복제를 위한 웹 동기화에서 사용할 [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS(인터넷 정보 서비스) 버전 7 이상을 수동으로 구성하는 프로세스를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-103">The procedures in this topic will guide you through the process of manually configuring [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) version 7 and higher for use with Web synchronization for merge replication.</span></span> 
  
 <span data-ttu-id="ea163-104">IIS 7을 구성하는 단계는 웹 동기화를 사용하도록 설정하는 데 필요한 3가지 단계 중 첫 번째 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-104">Configuring IIS 7 is the first of three steps needed to enable Web synchronization.</span></span>  
  
 <span data-ttu-id="ea163-105">전체 구성 프로세스에 대한 개요는 [웹 동기화 구성](configure-web-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea163-105">For an overview of the entire configuration process, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ea163-106">애플리케이션에서 [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] 이상 버전을 사용해야 하며, 이전 버전의 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 가 IIS 서버에 설치되어 있으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-106">Make sure that your application uses only [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] or later versions, and that earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] are not installed on the IIS server.</span></span> <span data-ttu-id="ea163-107">이전 버전의 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]가 있으면 다음과 같은 오류가 발생할 수 있습니다. "웹 동기화 중 메시지 형식이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-107">Earlier versions of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] can cause errors, such as: "The format of a message during Web synchronization was invalid.</span></span> <span data-ttu-id="ea163-108">웹 서버에서 복제 구성 요소가 올바르게 구성되었는지 확인하십시오."</span><span class="sxs-lookup"><span data-stu-id="ea163-108">Ensure that replication components are properly configured at the Web server."</span></span>  
  
 <span data-ttu-id="ea163-109">웹 동기화를 사용하려면 다음 단계를 완료하여 IIS 7을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-109">To use Web synchronization, you must configure IIS 7 by completing the following steps.</span></span> <span data-ttu-id="ea163-110">이 항목에서는 각 단계를 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-110">Each step is described in detail in this topic.</span></span>  
  
1.  <span data-ttu-id="ea163-111">IIS를 실행하는 컴퓨터에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 수신기를 설치하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-111">Install and configure the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener on the computer that is running IIS.</span></span>  
  
2.  <span data-ttu-id="ea163-112">SSL(Secure Sockets Layer)을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-112">Configure Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="ea163-113">SSL은 IIS와 모든 구독자 간의 통신을 위해 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-113">SSL is required for communication between IIS and all subscribers.</span></span>  
  
3.  <span data-ttu-id="ea163-114">IIS 인증을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-114">Configure IIS authentication.</span></span>  
  
4.  <span data-ttu-id="ea163-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 수신기에 대한 계정을 구성하고 사용 권한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-115">Configure an account and set permissions for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener.</span></span>  
  
## <a name="installing-the-sql-server-replication-listener"></a><span data-ttu-id="ea163-116">SQL Server 복제 수신기 설치</span><span class="sxs-lookup"><span data-stu-id="ea163-116">Installing the SQL Server Replication Listener</span></span>  

<span data-ttu-id="ea163-117">웹 동기화는 IIS 버전 5.0부터 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-117">Web synchronization is supported on IIS, beginning with version 5.0.</span></span> <span data-ttu-id="ea163-118">IIS 버전 7.0 이상에서는 IIS 버전 5 및 6의 웹 동기화 구성 마법사를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-118">The Configure Web Synchronization Wizard of IIS version 5 and 6, is not available with IIS version 7.0 and higher.</span></span> <span data-ttu-id="ea163-119">**SQL Server 2012부터 IIS 서버의 웹 동기화 구성 요소를 사용하려면 복제와 함께 SQL Server를 설치해야 합니다. 무료 SQL Server Express Edition일 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="ea163-119">**Beginning with SQL Server 2012, to use the web sync component on IIS server, you should install SQL Server with replication. This can be the free SQL Server Express edition.**</span></span>
  
#### <a name="to-install-and-configure-the-sql-server-replication-listener"></a><span data-ttu-id="ea163-120">SQL Server 복제 수신기를 설치 및 구성하려면</span><span class="sxs-lookup"><span data-stu-id="ea163-120">To install and configure the SQL Server Replication Listener</span></span>  
  
1. <span data-ttu-id="ea163-121">IIS 컴퓨터에 SQL Server 복제를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-121">Install SQL Server replication on the IIS computer.</span></span>

2.  <span data-ttu-id="ea163-122">IIS를 실행하는 컴퓨터에 replisapi.dll에 대한 새 파일 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-122">Create a new file directory for replisapi.dll on the computer that is running IIS.</span></span> <span data-ttu-id="ea163-123">원하는 위치에 이 디렉터리를 만들 수 있지만 \<*drive*>:\Inetpub 디렉터리 아래에 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-123">You can create the directory wherever you want, but we recommend that you create the directory under the \<*drive*>:\Inetpub directory.</span></span> <span data-ttu-id="ea163-124">예를 들어 \<*drive*>:\Inetpub\SQLReplication\\ 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-124">For example, create the directory \<*drive*>:\Inetpub\SQLReplication\\.</span></span>  
  
3.  <span data-ttu-id="ea163-125">[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ 디렉터리에 있는 replisapi.dll을 1단계에서 만든 파일 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-125">Copy replisapi.dll from the directory [!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]com\ to the file directory that you created in step 1.</span></span>  
  
4.  <span data-ttu-id="ea163-126">replisapi.dll을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-126">Register replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="ea163-127">**시작**을 클릭한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-127">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="ea163-128">**열기** 상자에를 입력 한 `cmd` 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-128">In the **Open** box, enter `cmd`, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="ea163-129">1단계에서 만든 디렉터리에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-129">In the directory created in step 1, execute the following command:</span></span>  
  
         `regsvr32 replisapi.dll`  
  
5.  <span data-ttu-id="ea163-130">복제를 위한 새 웹 사이트를 만들거나 기존 사이트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-130">Create a new Web site for replication or use an existing site.</span></span> <span data-ttu-id="ea163-131">이 웹 사이트는 동기화를 수행하는 동안 복제 구성 요소에서 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-131">This Web site will be accessed by replication components during synchronization.</span></span> <span data-ttu-id="ea163-132">이 항목의 절차에서는 기본 웹 사이트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-132">Procedures in this topic will assume the Default Web Site.</span></span> <span data-ttu-id="ea163-133">웹 사이트를 만드는 방법은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea163-133">For more information about how to create Web sites, see the IIS documentation</span></span>  
  
6.  <span data-ttu-id="ea163-134">IIS에 가상 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-134">Create a virtual directory in IIS.</span></span> <span data-ttu-id="ea163-135">가상 디렉터리는 4단계에서 만든 웹 사이트 아래에 만들어야 하며 1단계에서 만든 디렉터리에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-135">The virtual directory should be created under the Web site that you created in step 4 and map it to the directory created in step 1.</span></span> <span data-ttu-id="ea163-136">이 디렉터리에 대한 사용 권한은 가능한 제한적으로 할당하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-136">Be as restrictive as possible when you assign permissions to this directory.</span></span> <span data-ttu-id="ea163-137">적어도 **읽기** 및 **실행** 권한을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-137">You must select at least **Read** and **Execute** permissions.</span></span>  
  
    1.  <span data-ttu-id="ea163-138">**IIS(인터넷 정보 서비스) 관리자**의 **연결** 창에서 **기본 웹 사이트**를 마우스 오른쪽 단추로 클릭한 다음 **가상 디렉터리 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-138">In **Internet Information Services (IIS) Manager**, in the **Connections** pane, right-click **Default Web Site**, and then select **Add Virtual Directory**.</span></span>  
  
    2.  <span data-ttu-id="ea163-139">**별칭**에를 입력 `SQLReplication` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-139">For **Alias**, enter `SQLReplication`.</span></span>  
  
    3.  <span data-ttu-id="ea163-140">**실제 경로**에서 **\<drive>:\Inetpub\SQLReplication\\** 을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-140">For **Physical Path**, enter **\<drive>:\Inetpub\SQLReplication\\**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="ea163-141">replisapi.dll이 실행될 수 있도록 IIS를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-141">Configure IIS to enable replisapi.dll to execute.</span></span>  
  
    1.  <span data-ttu-id="ea163-142">**IIS(인터넷 정보 서비스) 관리자**에서 **기본 웹 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-142">In **Internet Information Services (IIS) Manager**, click **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="ea163-143">가운데 창에서 **처리기 매핑**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-143">In the center pane, click **Handler Mappings**.</span></span>  
  
    3.  <span data-ttu-id="ea163-144">**동작** 창에서 **모듈 매핑 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-144">In the **Actions** pane, click **Add Module Mapping**.</span></span>  
  
    4.  <span data-ttu-id="ea163-145">**요청** 경로에를 입력 `replisapi.dll` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-145">For **Request** Path, enter `replisapi.dll`.</span></span>  
  
    5.  <span data-ttu-id="ea163-146">**모듈** 드롭다운 목록에서 **IsapiModule**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-146">From the **Module** drop-down list, select **IsapiModule**.</span></span>  
  
    6.  <span data-ttu-id="ea163-147">**실행 파일**에서 **\<drive>:\Inetpub\SQLReplication\replisapi.dll**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-147">For **Executable**, enter **\<drive>:\Inetpub\SQLReplication\replisapi.dll**.</span></span>  
  
    7.  <span data-ttu-id="ea163-148">**이름**에 `Replisapi`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-148">For **Name**, enter `Replisapi`.</span></span>  
  
    8.  <span data-ttu-id="ea163-149">**요청 제한** 단추를 클릭하고 **액세스** 탭을 클릭한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-149">Click the **Request Restrictions** button, click the **Access** tab, and then click **Execute**.</span></span>  
  
    9. <span data-ttu-id="ea163-150">**확인** 을 클릭하여 **요청 제한** 대화 상자를 닫은 다음 다시 **확인** 을 클릭하여 **모듈 매핑 추가** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-150">Click **OK** to close the **Request Restrictions** dialog box, and then click **OK** again to close the **Add Module Mapping** dialog box.</span></span> <span data-ttu-id="ea163-151">ISAPI 확장을 허용할지 묻는 메시지가 표시되면 **예** 를 클릭하여 확장을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-151">When you are prompted to allow the ISAPI extension, click **Yes** to add the extension.</span></span>  
  
    10. <span data-ttu-id="ea163-152">Replisapi.dll이 **사용** 처리기 매핑 아래에 나열되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-152">Verify that Replisapi.dll is listed under the **Enabled** handler mappings.</span></span> <span data-ttu-id="ea163-153">이 dll이 **사용 안 함** 목록에 있는 경우 Replisapi 항목을 마우스 오른쪽 단추로 클릭한 다음 **기능 사용 권한 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-153">If it is in the **Disabled** list, right-click the Replisapi entry and then click **Edit Feature Permissions**.</span></span> <span data-ttu-id="ea163-154">**실행** 상자를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-154">Check the **Execute** box, and then click **OK**.</span></span>  
  
## <a name="configuring-iis-authentication"></a><span data-ttu-id="ea163-155">IIS 인증 구성</span><span class="sxs-lookup"><span data-stu-id="ea163-155">Configuring IIS Authentication</span></span>  
 <span data-ttu-id="ea163-156">구독자 컴퓨터가 IIS에 연결한 다음 리소스 및 프로세스에 액세스하려면 먼저 IIS에서 해당 구독자를 인증해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-156">When subscriber computers connect to IIS, IIS must authenticate the subscribers before they can access resources and processes.</span></span> <span data-ttu-id="ea163-157">인증은 전체 웹 사이트나 사용자가 만든 가상 디렉터리에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-157">Authentication can be applied to the whole Web site or to the virtual directory that you created.</span></span>  
  
 <span data-ttu-id="ea163-158">기본 인증과 함께 SSL을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-158">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="ea163-159">SSL은 사용하는 인증 유형에 관계없이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-159">SSL is required, regardless of the type of authentication that is used.</span></span>  
  
 <span data-ttu-id="ea163-160">기본 인증과 함께 SSL을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-160">We recommend that you use Basic Authentication with SSL.</span></span> <span data-ttu-id="ea163-161">SSL은 사용하는 인증 유형에 관계없이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-161">SSL is required, regardless of the type of authentication that is used.</span></span>  
  
#### <a name="to-configure-iis-authentication"></a><span data-ttu-id="ea163-162">IIS 인증을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="ea163-162">To Configure IIS Authentication</span></span>  
  
1.  <span data-ttu-id="ea163-163">**IIS(인터넷 정보 서비스) 관리자**에서 **기본 웹 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-163">In **Internet Information Services (IIS) Manager**, click **Default Web Site**.</span></span>  
  
2.  <span data-ttu-id="ea163-164">중간 창에서 **인증**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-164">In the middle pane, double-click **Authentication**.</span></span>  
  
3.  <span data-ttu-id="ea163-165">익명 인증을 마우스 오른쪽 단추로 클릭한 다음 사용 안 함을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-165">Right-click Anonymous Authentication, and then choose Disable.</span></span>  
  
4.  <span data-ttu-id="ea163-166">기본 인증을 마우스 오른쪽 단추로 클릭한 다음 사용을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-166">Right-click Basic Authentication, and then choose Enable.</span></span>  
  
## <a name="configuring-secure-sockets-layer"></a><span data-ttu-id="ea163-167">SSL(Secure Sockets Layer) 구성</span><span class="sxs-lookup"><span data-stu-id="ea163-167">Configuring Secure Sockets Layer</span></span>  
 <span data-ttu-id="ea163-168">SSL을 구성하려면 IIS를 실행하는 컴퓨터에서 사용할 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-168">To configure SSL, specify a certificate to be used by the computer running IIS.</span></span> <span data-ttu-id="ea163-169">병합 복제를 위한 웹 동기화에서는 서버 인증서를 사용할 수 있지만 클라이언트 인증서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-169">Web synchronization for merge replication supports using server certificates, but not client certificates.</span></span> <span data-ttu-id="ea163-170">배포를 위해 IIS를 구성하려면 먼저 CA(인증 기관)에서 인증서를 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-170">To configure IIS for deployment, you must first obtain a certificate from a certification authority (CA).</span></span> <span data-ttu-id="ea163-171">인증서에 대한 자세한 내용은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea163-171">For more information about certificates, see the IIS documentation.</span></span>  
  
 <span data-ttu-id="ea163-172">인증서를 설치한 다음에는 웹 동기화에서 사용하는 웹 사이트와 인증서를 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-172">After you install the certificate, you must associate the certificate with the Web site that is used by Web synchronization.</span></span> <span data-ttu-id="ea163-173">개발 및 테스트용으로 자체 서명 인증서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-173">For development and testing, you can specify a self-signed certificate.</span></span> <span data-ttu-id="ea163-174">IIS 7은 인증서를 만들고 해당 인증서를 사용자의 컴퓨터에 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-174">IIS 7 can create a certificate for you and register it on your computer.</span></span>  
  
 <span data-ttu-id="ea163-175">프로덕션을 위해 배포하는 경우와 여기에서 설명하는 절차 사이의 차이점은 프로덕션 및 프로덕션 이전 테스팅에서는 자체 서명된 인증서 대신 CA에서 발급한 인증서를 사용한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-175">The difference between deploying for production and the procedures given here is that in production and pre-production testing, you would use a certificate issued by a CA instead of a self-signed certificate.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ea163-176">프로덕션 설치의 경우에는 자체 서명된 인증서를 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-176">A self-signed certificate is not recommended for a production installation.</span></span> <span data-ttu-id="ea163-177">자체 서명된 인증서는 안전하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-177">Self-signed certificates are not secure.</span></span> <span data-ttu-id="ea163-178">자체 서명된 인증서는 개발 및 테스트용으로만 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea163-178">Use self-signed certificates for development and testing only.</span></span>  
  
 <span data-ttu-id="ea163-179">SSL을 구성하려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea163-179">To configure SSL, you will perform the following steps:</span></span>  
  
1.  <span data-ttu-id="ea163-180">웹 사이트에서 SSL을 필요로 하고 클라이언트 인증서를 무시하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-180">Configure the Web site to require SSL and ignore client certificates.</span></span>  
  
2.  <span data-ttu-id="ea163-181">CA에서 인증서를 얻거나 자체 서명된 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-181">Obtain a certificate from a CA or create a self-signed certificate.</span></span>  
  
3.  <span data-ttu-id="ea163-182">인증서를 복제 웹 사이트에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-182">Bind the certificate to the replication Web site.</span></span>  
  
#### <a name="to-require-ssl-security-for-a-web-site"></a><span data-ttu-id="ea163-183">웹 사이트에 대해 SSL 보안을 요구하려면</span><span class="sxs-lookup"><span data-stu-id="ea163-183">To require SSL security for a Web site</span></span>  
  
1.  <span data-ttu-id="ea163-184">**IIS(인터넷 정보 서비스) 관리자**에서 로컬 서버 노드를 확장한 다음 **기본 웹 사이트** 또는 사용자의 웹 동기화 사이트(기본 웹 사이트와 다른 경우)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-184">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click the **Default Web Site** (or your Web synchronization site if it is different from the default Web site).</span></span>  
  
2.  <span data-ttu-id="ea163-185">중간 창에서 **SSL 설정**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-185">In the middle pane, double-click **SSL Settings**.</span></span>  
  
3.  <span data-ttu-id="ea163-186">**SSL 필요** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-186">Check the **Require SSL** option.</span></span> <span data-ttu-id="ea163-187">**클라이언트 인증서**아래에서 **무시** 단추가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-187">Under **Client certificates**, verify that the **Ignore** button is selected.</span></span>  
  
#### <a name="to-create-a-self-signed-certificate-for-testing"></a><span data-ttu-id="ea163-188">테스트를 위한 자체 서명된 인증서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="ea163-188">To create a self-signed certificate for testing</span></span>  
  
1.  <span data-ttu-id="ea163-189">**IIS(인터넷 정보 서비스) 관리자**에서 로컬 서버 노드를 클릭한 다음 가운데 창에서 **서버 인증서**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-189">In **Internet Information Services (IIS) Manager**, click the local server node, and then in the center pane, double-click on **Server Certificates**.</span></span>  
  
2.  <span data-ttu-id="ea163-190">**동작** 창에서 **자체 서명된 인증서 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-190">In the **Actions** pane, click **Create Self-Signed Certificate**.</span></span>  
  
3.  <span data-ttu-id="ea163-191">**자체 서명된 인증서 만들기** 대화 상자에서 인증서에 대한 이름을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-191">In the **Create Self-Signed Certificate** dialog box, enter a name for the certificate, and then click **OK**.</span></span>  
  
###### <a name="to-bind-a-certificate-to-a-web-site"></a><span data-ttu-id="ea163-192">인증서를 웹 사이트에 바인딩하려면</span><span class="sxs-lookup"><span data-stu-id="ea163-192">To bind a certificate to a Web site</span></span>  
  
1.  <span data-ttu-id="ea163-193">**연결** 창에서 **기본 웹 사이트** 또는 사용자의 웹 동기화 사이트(기본 웹 사이트와 다른 경우)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-193">In the **Connections** pane, click the **Default Web Site** (or your Web synchronization site, if it is different from the default Web site).</span></span>  
  
2.  <span data-ttu-id="ea163-194">**동작** 창에서 **바인딩**을 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-194">In the **Actions** pane, click **Bindings**, and then click **Add**.</span></span> <span data-ttu-id="ea163-195">**사이트 바인딩 추가** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-195">The **Add Site Binding** dialog box will appear.</span></span>  
  
3.  <span data-ttu-id="ea163-196">**유형** 드롭다운 목록에서 **https**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-196">From the **Type** drop-down list, select **https**.</span></span> <span data-ttu-id="ea163-197">**IP 주소** 및 **포트**에 대한 기본 설정은 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-197">Leave the default settings for **IP address** and **Port**.</span></span>  
  
4.  <span data-ttu-id="ea163-198">**SSL 인증서** 드롭다운 목록에서 "테스트를 위한 자체 서명된 인증서를 만들려면"에서 만든 인증서를 선택하고 **확인**을 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-198">From the **SSL certificate** drop-down list, select the certificate created in "To create a self-signed certificate for testing," click **OK**, and then click **Close**.</span></span>  
  
###### <a name="to-test-the-certificate"></a><span data-ttu-id="ea163-199">인증서를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="ea163-199">To test the certificate</span></span>  
  
1.  <span data-ttu-id="ea163-200">**ternet formation Services (IIS) Manager**에서 **기본 웹 사이트.**</span><span class="sxs-lookup"><span data-stu-id="ea163-200">In **Internet Information Services (IIS) Manager**, click **Default Web Site.**</span></span>  
  
2.  <span data-ttu-id="ea163-201">**동작** 창에서 **\*:443(https) 찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-201">From the **Actions** pane, click **Browse \*:443(https)**.</span></span>  
  
3.  <span data-ttu-id="ea163-202">Internet Explorer가 열리고 "이 웹 사이트의 보안 인증서에 문제가 있습니다."라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-202">Internet Explorer will open and display a message that "There is a problem with this website's security certificate."</span></span> <span data-ttu-id="ea163-203">이 경고에서는 연결된 인증서가 공인 CA에 의해 발급되지 않았으며 신뢰할 수 없을 수도 있음을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-203">This warning tells you that the associated certificate was not issued by a recognized CA and might not be trustworthy.</span></span> <span data-ttu-id="ea163-204">이는 예상되는 경고이므로 **이 웹 사이트를 계속 탐색합니다(권장하지 않음).** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-204">This is an expected warning, so click **Continue to this website (not recommended)**.</span></span>  
  
4.  <span data-ttu-id="ea163-205">**localhost에 연결**메시지가 표시되면 사용자 이름 및 암호를 입력하여 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-205">If you are prompted to **Connect to localhost**, enter a user name and password to proceed.</span></span> <span data-ttu-id="ea163-206">웹 사이트에 대한 기본 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-206">You should see the default page for the Web site.</span></span>  
  
## <a name="setting-permissions-for-the-sql-server-replication-listener"></a><span data-ttu-id="ea163-207">SQL Server 복제 수신기에 대한 사용 권한 설정</span><span class="sxs-lookup"><span data-stu-id="ea163-207">Setting Permissions for the SQL Server Replication Listener</span></span>  
 <span data-ttu-id="ea163-208">구독자 컴퓨터가 IIS를 실행하는 컴퓨터에 연결되면 IIS 구성 시 지정한 인증 유형을 사용하여 해당 구독자가 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-208">When a subscriber computer connects to the computer running IIS, the subscriber is authenticated by using the type of authentication specified when you configured IIS.</span></span> <span data-ttu-id="ea163-209">IIS에서는 구독자를 인증한 다음 해당 구독자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제를 호출할 수 있는 권한을 가지고 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-209">After IIS authenticates the subscriber, IIS checks whether the subscriber is authorized to invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="ea163-210">replisapi.dll에 대한 권한을 설정하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제를 호출할 수 있는 사용자를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-210">You control the users that can invoke [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication by setting permissions for replisapi.dll.</span></span> <span data-ttu-id="ea163-211">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제에 무단으로 액세스하지 못하도록 하려면 사용 권한을 적절하게 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-211">Properly configuring permissions is necessary to prevent unauthorized access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication.</span></span>  
  
 <span data-ttu-id="ea163-212">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제 수신기를 실행할 계정에 대해 최소 사용 권한을 구성하려면 다음 절차를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-212">To configure the minimum permissions for the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replication Listener runs, complete the following procedure.</span></span> <span data-ttu-id="ea163-213">다음 절차의 단계는 IIS 7.0을 실행하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server 2008에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-213">The steps in the following procedure apply to [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Server 2008 running IIS 7.0.</span></span>  
  
 <span data-ttu-id="ea163-214">다음 단계를 수행한 다음에는 PAL(게시 액세스 목록)에 필요한 로그인을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-214">In addition to performing the following steps, make sure that the required logins are in the publication access list (PAL).</span></span> <span data-ttu-id="ea163-215">PAL에 대한 자세한 내용은 [게시자 보안 설정](security/secure-the-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea163-215">For more information about the PAL, see [Secure the Publisher](security/secure-the-publisher.md).</span></span>  
  
 <span data-ttu-id="ea163-216">**중요** 이 섹션에서 만든 계정은 동기화하는 동안 게시자 및 배포자에 연결되는 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-216">**Important** The account created in this section is the account that will connect to the Publisher and Distributor during synchronization.</span></span> <span data-ttu-id="ea163-217">이 계정은 게시 및 배포 서버의 SQL 로그인 계정으로 추가되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-217">This account must be added as a SQL Login account on the distribution and publication server.</span></span>  
  
 <span data-ttu-id="ea163-218">SQL Server 복제 수신기에 대해 사용되는 계정은 병합 에이전트 보안 항목의 "게시자 또는 배포자에 연결" 섹션에 설명된 대로 사용 권한을 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-218">The account used for the SQL Server Replication Listener must have permissions as described in the Merge Agent Security topic, in the "Connect to the Publisher or Distributor" section.</span></span>  
  
 <span data-ttu-id="ea163-219">요약하면, 계정은 다음 조건을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-219">In summary, the account must:</span></span>  
  
-   <span data-ttu-id="ea163-220">PAL(게시 액세스 목록)의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-220">Be a member of the Publication Access List (PAL).</span></span>  
  
-   <span data-ttu-id="ea163-221">게시 데이터베이스의 사용자와 연결된 로그인에 매핑되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-221">Be mapped to a login associated with a user in the publication database.</span></span>  
  
-   <span data-ttu-id="ea163-222">배포 데이터베이스의 사용자와 연결된 로그인에 매핑되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-222">Be mapped to a login associated with a user in the distribution database.</span></span>  
  
-   <span data-ttu-id="ea163-223">스냅샷 공유에 대한 읽기 권한을 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-223">Have Read permissions on the snapshot share.</span></span>  
  
#### <a name="to-configure-the-account-and-permissions"></a><span data-ttu-id="ea163-224">계정 및 사용 권한을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="ea163-224">To configure the account and permissions</span></span>  
  
1.  <span data-ttu-id="ea163-225">IIS를 실행하는 컴퓨터에 로컬 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-225">Create a local account on the computer running IIS:</span></span>  
  
    1.  <span data-ttu-id="ea163-226">**서버 관리자**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-226">Open **Server Manager**.</span></span> <span data-ttu-id="ea163-227">시작 메뉴에서 **컴퓨터**를 마우스 오른쪽 단추로 클릭한 다음 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-227">From the Start menu, right-click **Computer**, and then click **Manage**.</span></span>  
  
    2.  <span data-ttu-id="ea163-228">**서버 관리자**에서 **구성**을 확장한 다음 **로컬 사용자 및 그룹**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-228">In **Server Manager**, expand **Configuration**, and then expand **Local Users and Groups**.</span></span>  
  
    3.  <span data-ttu-id="ea163-229">**사용자**를 마우스 오른쪽 단추로 클릭한 다음 **새 사용자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-229">Right-click **Users**, and then click **New User**.</span></span>  
  
    4.  <span data-ttu-id="ea163-230">사용자 이름과 강력한 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-230">Enter a user name and a strong password.</span></span> <span data-ttu-id="ea163-231">**다음 로그온할 때 반드시 암호 변경**의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-231">Clear **User must change password at next logon**.</span></span>  
  
    5.  <span data-ttu-id="ea163-232">**만들기**를 클릭한 다음 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-232">Click **Create**, and then click **Close**.</span></span>  
  
2.  <span data-ttu-id="ea163-233">IIS_IUSRS 그룹에 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-233">Add the account to the IIS_IUSRS group:</span></span>  
  
    1.  <span data-ttu-id="ea163-234">**서버 관리자**에서 **구성**을 확장하고 **로컬 사용자 및 그룹**을 확장한 다음 **그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-234">In **Server Manager**, expand **Configuration**, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
    2.  <span data-ttu-id="ea163-235">**IIS_IUSRS**를 마우스 오른쪽 단추로 클릭한 다음 **그룹에 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-235">Right-click **IIS_IUSRS**, and then click **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="ea163-236">**IIS_IUSRS 속성** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-236">In the **IIS_IUSRS Properties** dialog box, click **Add**.</span></span>  
  
    4.  <span data-ttu-id="ea163-237">**사용자, 컴퓨터 또는 그룹 선택** 대화 상자에 1단계에서 만든 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-237">In the **Select Users, Computers, or Groups** dialog box, add the account created in step 1.</span></span>  
  
    5.  <span data-ttu-id="ea163-238">**다음 위치에서** 에 도메인이 아닌 로컬 컴퓨터 이름이 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-238">Verify that **From this location** displays the name of the local computer (not a domain).</span></span> <span data-ttu-id="ea163-239">이 필드에 로컬 컴퓨터 이름이 표시되지 않는 경우 **위치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-239">If this field does not display the local computer name, click **Locations**.</span></span> <span data-ttu-id="ea163-240">**위치** 대화 상자에서 로컬 컴퓨터를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-240">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="ea163-241">**사용자 선택** 대화 상자 및 **IIS_IUSRS 속성** 대화 상자에서**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-241">In the **Select Users** dialog box and the **IIS_IUSRS Properties** dialog box, click**OK**.</span></span>  
  
3.  <span data-ttu-id="ea163-242">replisapi.dll을 포함하는 폴더에 최소 계정 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-242">Grant minimum account permissions on the folder that contains replisapi.dll:</span></span>  
  
    1.  <span data-ttu-id="ea163-243">Windows 탐색기에서 replisapi.dll에 대해 만든 폴더를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-243">In Windows Explorer, right-click the folder that you created for replisapi.dll, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="ea163-244">**보안** 탭에서 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-244">On the **Security** tab, click **Edit**.</span></span>  
  
    3.  <span data-ttu-id="ea163-245">**\<foldername>에 대한 권한** 대화 상자에서 **추가**를 클릭하여 1단계에서 만든 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-245">In the **Permissions for \<foldername>** dialog box, click **Add** to add the account that you created in step 1.</span></span>  
  
    4.  <span data-ttu-id="ea163-246">**다음 위치에서** 에 도메인이 아닌 로컬 컴퓨터 이름이 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-246">Verify that **From this location** displays the name of the local computer (not a domain).</span></span> <span data-ttu-id="ea163-247">이 필드에 로컬 컴퓨터 이름이 표시되지 않는 경우 **위치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-247">If this field does not display the local computer name, click **Locations**.</span></span> <span data-ttu-id="ea163-248">**위치** 대화 상자에서 로컬 컴퓨터를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-248">In the **Locations** dialog box, select the local computer, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="ea163-249">계정에는 **읽기**, **읽기 및 실행** 및 **폴더 내용 보기** 권한만 부여되었는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="ea163-249">Verify that the account is granted only **Read**, **Read & Execute**, and **List Folder Contents** permissions.</span></span>  
  
    6.  <span data-ttu-id="ea163-250">디렉터리에 대한 액세스가 필요 없는 사용자나 그룹을 선택하고 **제거**를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-250">Select any users or groups that do not require access to the directory, click **Remove**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="ea163-251">**인터넷 정보 서비스(IIS) 관리자**에서 애플리케이션 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-251">Create an application pool in **Internet Information Services (IIS) Manager**:</span></span>  
  
    1.  <span data-ttu-id="ea163-252">**IIS(인터넷 정보 서비스) 관리자**의 **연결** 창에서 로컬 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-252">In **Internet Information Services (IIS) Manager**, in the **Connections** pane, expand the local server node.</span></span>  
  
    2.  <span data-ttu-id="ea163-253">**애플리케이션 풀**을 마우스 오른쪽 단추로 클릭하고 **애플리케이션 풀 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-253">Right-click **Application Pools**, and then click **Add Application Pool**.</span></span>  
  
    3.  <span data-ttu-id="ea163-254">애플리케이션 풀의 이름을 입력하고 남아 있는 필드에 대한 기본값을 그대로 둔 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-254">Enter a name for the application pool, leave the default values for the remaining fields, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea163-255">동기화 클라이언트가 세 개 이상 동시에 실행되도록 하려면 웹 가든을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-255">If you anticipate having more than two concurrent synchronization clients, you might want to create a web garden.</span></span> <span data-ttu-id="ea163-256">자세한 내용은 [웹 동기화 구성](configure-web-synchronization.md)에서 "웹 가든 만들기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea163-256">For more information, see "Creating a Web Garden" in [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
5.  <span data-ttu-id="ea163-257">계정과 애플리케이션 풀을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-257">Associate the account with the application pool:</span></span>  
  
    1.  <span data-ttu-id="ea163-258">**IIS(인터넷 정보 서비스) 관리자**에서 로컬 서버 노드를 확장한 다음 **애플리케이션 풀**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-258">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click on **Application Pools**.</span></span>  
  
    2.  <span data-ttu-id="ea163-259">만든 애플리케이션 풀을 마우스 오른쪽 단추로 클릭한 다음 **애플리케이션 풀 기본값 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-259">Right-click the application pool that you created, and then click **Set Application Pool Defaults**.</span></span>  
  
    3.  <span data-ttu-id="ea163-260">**애플리케이션 풀 기본값** 대화 상자에서 **프로세스 모델** 섹션으로 스크롤한 다음 **ID** 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-260">In the **Application Pool Defaults** dialog box, scroll down to the **Process Model** section, and then click the **Identity** field.</span></span>  
  
    4.  <span data-ttu-id="ea163-261">**ID** 행의 오른쪽에서 줄임표 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-261">Click the ellipsis button on the right side of the **Identity** row.</span></span>  
  
    5.  <span data-ttu-id="ea163-262">**사용자 지정 계정** 라디오 단추를 클릭한 다음 **설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-262">Click the **Custom Account** radio button, and then click **Set**.</span></span>  
  
    6.  <span data-ttu-id="ea163-263">**사용자 이름** 및 **암호** 필드에 1단계에서 만든 계정과 암호를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-263">In the **User name** and **Password** fields, enter the account and password that were created in step 1, and then click **OK**.</span></span>  
  
    7.  <span data-ttu-id="ea163-264">**확인** 을 클릭하여 **애플리케이션 풀 ID** 대화 상자를 닫은 다음 다시 **확인** 을 클릭하여 **애플리케이션 풀 기본값**대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-264">Click **OK** to close the **Application Pool Identity** dialog box, and then click **OK** again to close the **Application Pool Defaults**dialog box.</span></span>  
  
6.  <span data-ttu-id="ea163-265">애플리케이션 풀을 복제 웹 사이트와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-265">Associate the application pool with the replication Web site:</span></span>  
  
    1.  <span data-ttu-id="ea163-266">**IIS(인터넷 정보 서비스) 관리자**에서 로컬 서버 노드를 확장한 다음 **기본 웹 사이트** 또는 사용자의 웹 동기화 사이트(기본 웹 사이트와 다른 경우)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-266">In **Internet Information Services (IIS) Manager**, expand the local server node, and then click on the **Default Web Site** (or your Web synchronization site if it is different from the default Web site).</span></span>  
  
    2.  <span data-ttu-id="ea163-267">**동작** 창의 **웹 사이트 관리**에서 **고급 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-267">In the **Actions** pane, under **Manage Web Site**, click **Advanced Settings**.</span></span>  
  
    3.  <span data-ttu-id="ea163-268">**고급 설정** 대화 상자에서 **애플리케이션 풀**의 오른쪽에 있는 줄임표 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-268">In the **Advanced Settings** dialog box, click on the ellipsis button to the right of **Application Pool**.</span></span>  
  
    4.  <span data-ttu-id="ea163-269">**애플리케이션 풀** 드롭다운 목록에서 4단계에서 만든 애플리케이션 풀을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-269">From the **Application pool** drop-down list, select the application pool you created in step 4, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="ea163-270">다시 **확인** 을 클릭하여 고급 설정을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-270">Click **OK** again to close Advanced Settings.</span></span>  
  
## <a name="testing-the-connection-to-replisapidll"></a><span data-ttu-id="ea163-271">replisapi.dll에 대한 연결 테스트</span><span class="sxs-lookup"><span data-stu-id="ea163-271">Testing the Connection to replisapi.dll</span></span>  
 <span data-ttu-id="ea163-272">진단 모드에서 웹 동기화를 실행하여 IIS를 실행하는 컴퓨터에 대한 연결을 테스트하고 SSL(Secure Sockets Layer) 인증서가 제대로 설치되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-272">Run Web synchronization in diagnostic mode to test the connection to the computer running IIS and to make sure that the Secure Sockets Layer (SSL) certificate is properly installed.</span></span> <span data-ttu-id="ea163-273">진단 모드에서 웹 동기화를 실행하려면 IIS가 실행되는 컴퓨터의 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-273">To run Web synchronization in diagnostic mode, you must be an administrator on the computer running IIS.</span></span>  
  
#### <a name="to-test-the-connection-to-replisapidll"></a><span data-ttu-id="ea163-274">replisapi.dll에 대한 연결을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="ea163-274">To test the connection to replisapi.dll</span></span>  
  
1.  <span data-ttu-id="ea163-275">구독자의 LAN(Local Area Network) 설정이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-275">Make sure that local area network (LAN) settings at the Subscriber are correct:</span></span>  
  
    1.  <span data-ttu-id="ea163-276">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer의 **도구** 메뉴에서 **인터넷 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-276">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, on the **Tools** menu, click **Internet Options**.</span></span>  
  
    2.  <span data-ttu-id="ea163-277">**연결** 탭에서 **LAN 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-277">On the **Connections** tab, click **LAN Settings**.</span></span>  
  
    3.  <span data-ttu-id="ea163-278">LAN에 프록시 서버가 사용되지 않는 경우 **자동으로 설정 검색** 및 **사용자 LAN에 프록시 서버 사용**의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-278">If a proxy server is not used on the LAN, clear **Automatically Detect Settings** and **Use a proxy server for your LAN**.</span></span>  
  
    4.  <span data-ttu-id="ea163-279">프록시 서버가 사용되는 경우 **사용자 LAN에 프록시 서버 사용** 및 **로컬 주소에 프록시 서버 사용 안 함**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-279">If a proxy server is used, click **Use a proxy server for your LAN** and **Bypass proxy server for local addresses**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="ea163-280">구독자에서는 Internet Explorer에서 replisapi.dll에 대한 주소에 `?diag` (예:</span><span class="sxs-lookup"><span data-stu-id="ea163-280">At the Subscriber, in Internet Explorer, connect to the server in diagnostic mode by appending `?diag` to the address for the replisapi.dll.</span></span> <span data-ttu-id="ea163-281">예: `https://server.domain.com/directory/replisapi.dll?diag`</span><span class="sxs-lookup"><span data-stu-id="ea163-281">For example: `https://server.domain.com/directory/replisapi.dll?diag`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea163-282">위 예에서 **server.domain.com** 은 IIS 관리자의 **서버 인증서** 섹션 아래에 나열된 정확한 **발급 대상** 이름으로 대체되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-282">In the example above, **server.domain.com** should be replaced with the exact **Issued To** name listed under the **Server Certificates** section in IIS Manager.</span></span>  
  
3.  <span data-ttu-id="ea163-283">IIS에 대해 지정한 인증서를 Windows 운영 체제에서 인식하지 못할 경우 **보안 경고** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-283">If the certificate that you specified for IIS is not recognized by the Windows operating system, the **Security Alert** dialog box appears.</span></span> <span data-ttu-id="ea163-284">이 경고는 인증서가 테스트 인증서이거나 Windows에서 인식할 수 없는 CA(인증 기관)에서 발급한 인증서이기 때문에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-284">This alert might occur because the certificate is a test certificate or the certificate was issued by a certification authority (CA) that Windows does not recognize.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea163-285">이 대화 상자가 나타나지 않으면 액세스하는 서버에 대한 인증서가 구독자의 인증서 저장소에 신뢰할 수 있는 인증서로 추가되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-285">If this dialog box does not appear, make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="ea163-286">인증서를 내보내는 방법은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea163-286">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
    1.  <span data-ttu-id="ea163-287">**보안 경고** 대화 상자에서 **인증서 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-287">In the **Security Alert** dialog box, click **View Certificate**.</span></span>  
  
    2.  <span data-ttu-id="ea163-288">**인증서** 대화 상자의 **일반** 탭에서 **인증서 설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-288">In the **Certificate** dialog box, on the **General** tab, click **Install Certificate**.</span></span>  
  
    3.  <span data-ttu-id="ea163-289">기본값을 적용한 후 인증서 가져오기 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-289">Complete the Certificate Import Wizard, accepting the defaults.</span></span>  
  
    4.  <span data-ttu-id="ea163-290">**보안 경고** 대화 상자에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-290">In the **Security Warning** dialog box, click **Yes**.</span></span>  
  
    5.  <span data-ttu-id="ea163-291">인증서 가져오기 마법사 확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-291">In the Certificate Import Wizard confirmation dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="ea163-292">**인증서** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-292">Close the **Certificate** dialog box.</span></span>  
  
    7.  <span data-ttu-id="ea163-293">**보안 경고** 대화 상자에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-293">In the **Security Alert** dialog box, click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea163-294">인증서는 사용자에 대해 설치되므로</span><span class="sxs-lookup"><span data-stu-id="ea163-294">Certificates are installed for users.</span></span> <span data-ttu-id="ea163-295">IIS와 동기화할 각 사용자에 대해 이 프로세스를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-295">This process must be performed for each user that will synchronize with IIS.</span></span>  
  
4.  <span data-ttu-id="ea163-296">**\<ServerName>에 연결** 대화 상자에서 병합 에이전트가 IIS에 연결하는 데 사용할 로그인 및 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-296">In the **Connect to \<ServerName>** dialog box, specify the login and password that the Merge Agent will use to connect to IIS.</span></span> <span data-ttu-id="ea163-297">이러한 자격 증명은 새 구독 마법사에서도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-297">These credentials will also be specified in the New Subscription Wizard.</span></span>  
  
5.  <span data-ttu-id="ea163-298">**SQL Websync 진단 정보**라는 Internet Explorer 창에서 페이지의 각 **상태** 열 값이 **SUCCESS**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-298">In the Internet Explorer window called **SQL Websync diagnostic information**, verify that the value in each **Status** column on the page is **SUCCESS**.</span></span>  
  
6.  <span data-ttu-id="ea163-299">구독자에 인증서가 올바르게 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-299">Make sure that the certificate is installed correctly on the Subscriber:</span></span>  
  
    1.  <span data-ttu-id="ea163-300">Internet Explorer를 닫았다가 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-300">Close and then reopen Internet Explorer.</span></span>  
  
    2.  <span data-ttu-id="ea163-301">진단 모드에서 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-301">Connect to the server in diagnostic mode.</span></span> <span data-ttu-id="ea163-302">인증서가 제대로 설치된 경우 **보안 경고** 대화 상자가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-302">If the certificate is installed properly, the **Security Alert** dialog box will not appear.</span></span> <span data-ttu-id="ea163-303">이 대화 상자가 나타나면 병합 에이전트가 IIS를 실행하는 컴퓨터에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-303">If the dialog box appears, the Merge Agent will fail when it tries to connect to the computer that is running IIS.</span></span> <span data-ttu-id="ea163-304">액세스하는 서버에 대한 인증서가 구독자의 인증서 저장소에 신뢰할 수 있는 인증서로 추가되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea163-304">You must make sure that the certificate for the server that you are accessing has been added to the certificate store at the Subscriber as a trusted certificate.</span></span> <span data-ttu-id="ea163-305">인증서를 내보내는 방법은 IIS 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea163-305">For more information about exporting certificates, see the IIS documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea163-306">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea163-306">See Also</span></span>  
 <span data-ttu-id="ea163-307">[병합 복제에 대한 웹 동기화](web-synchronization-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="ea163-307">[Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="ea163-308">웹 동기화 구성</span><span class="sxs-lookup"><span data-stu-id="ea163-308">Configure Web Synchronization</span></span>](configure-web-synchronization.md)  
  
  
