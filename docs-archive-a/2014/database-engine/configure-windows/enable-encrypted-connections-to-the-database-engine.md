---
title: 데이터베이스 엔진 (SQL Server 구성 관리자)에 대 한 암호화 된 연결 사용 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e1653df929e3f8bc67158a0685ce07b8ba65de6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741243"
---
# <a name="enable-encrypted-connections-to-the-database-engine-sql-server-configuration-manager"></a><span data-ttu-id="0a701-102">데이터베이스 엔진에 암호화 연결 사용(SQL Server 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="0a701-102">Enable Encrypted Connections to the Database Engine (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="0a701-103">이 항목에서는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 구성 관리자를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 대한 인증서를 지정하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 암호화된 연결을 사용하도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-103">This topic describes how to enable encrypted connections for an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] by specifying a certificate for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="0a701-104">서버 컴퓨터에 구축된 인증서가 있어야 하며 클라이언트 컴퓨터가 해당 인증서의 루트 인증 기관을 트러스트하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-104">The server computer must have a certificate provisioned, and the client machine must be set up to trust the certificate's root authority.</span></span> <span data-ttu-id="0a701-105">구축은 인증서를 Windows로 가져와서 설치하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-105">Provisioning is the process of installing a certificate by importing it into Windows.</span></span>  
  
 <span data-ttu-id="0a701-106">인증서는 **서버 인증**용으로 발행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-106">The certificate must be issued for **Server Authentication**.</span></span> <span data-ttu-id="0a701-107">인증서의 이름은 컴퓨터의 정규화된 도메인 이름(FQDN)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-107">The name of the certificate must be the fully qualified domain name (FQDN) of the computer.</span></span>  
  
 <span data-ttu-id="0a701-108">인증서는 사용자 컴퓨터에 로컬로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-108">Certificates are stored locally for the users on the computer.</span></span> <span data-ttu-id="0a701-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 사용할 인증서를 설치하려면 서비스가 LocalSystem, NetworkService 또는 LocalService로 실행되고 있어 관리자 계정을 사용할 수 없는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스와 같은 사용자 계정으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-109">To install a certificate for use by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager under the same user account as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service unless the service is running as LocalSystem, NetworkService, or LocalService, in which case you may use an administrative account.</span></span>  
  
 <span data-ttu-id="0a701-110">클라이언트가 서버에 사용되는 인증서의 소유권을 확인할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-110">The client must be able to verify the ownership of the certificate used by the server.</span></span> <span data-ttu-id="0a701-111">클라이언트에 서버 인증서를 서명한 인증 기관의 공개 키 인증서가 있으면 추가 구성은 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-111">If the client has the public key certificate of the certification authority that signed the server certificate, no further configuration is necessary.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="0a701-112">Windows에는 많은 인증 기관의 공개 키 인증서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-112">Windows includes the public key certificates of many certification authorities.</span></span> <span data-ttu-id="0a701-113">클라이언트에 퍼블릭 키 인증서가 없는 퍼블릭 또는 프라이빗 인증 기관에서 서버 인증서를 서명한 경우 서버 인증서를 서명한 인증 기관의 퍼블릭 키 인증서를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-113">If the server certificate was signed by a public or private certification authority for which the client does not have the public key certificate, you must install the public key certificate of the certification authority that signed the server certificate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a701-114">장애 조치(Failover) 클러스터에 암호화를 사용하려면 장애 조치 클러스터의 모든 노드에 있는 가상 서버의 정규화된 DNS 이름으로 서버 인증서를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-114">To use encryption with a failover cluster, you must install the server certificate with the fully qualified DNS name of the virtual server on all nodes in the failover cluster.</span></span> <span data-ttu-id="0a701-115">예를 들어 노드 이름이 test1. 인 두 노드 클러스터가 있는 경우 *\<your company>* 입니다. com 및 *\<your company>* test2. com에 virtsql 이라는 가상 서버가 있는 경우 virtsql에 대 한 인증서를 설치 해야 *\<your company>* 합니다. 두 노드의 com</span><span class="sxs-lookup"><span data-stu-id="0a701-115">For example, if you have a two-node cluster, with nodes named test1.*\<your company>*.com and test2.*\<your company>*.com, and you have a virtual server named virtsql, you need to install a certificate for virtsql.*\<your company>*.com on both nodes.</span></span> <span data-ttu-id="0a701-116">**ForceEncryption**옵션 값을 **예**로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-116">You can set the value of the **ForceEncryption**option to **Yes**.</span></span>  
  
 <span data-ttu-id="0a701-117">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="0a701-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0a701-118">**암호화된 연결을 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="0a701-118">**To enable encrypted connections:**</span></span>  
  
     [<span data-ttu-id="0a701-119">서버에 인증서를 구축(설치)</span><span class="sxs-lookup"><span data-stu-id="0a701-119">Provision (install) a certificate on the server</span></span>](#Provision)  
  
     [<span data-ttu-id="0a701-120">서버 인증서 내보내기</span><span class="sxs-lookup"><span data-stu-id="0a701-120">Export the server certificate</span></span>](#Export)  
  
     [<span data-ttu-id="0a701-121">암호화된 연결을 허용하도록 서버 구성</span><span class="sxs-lookup"><span data-stu-id="0a701-121">Configure the server to accept encrypted connections</span></span>](#ConfigureServerConnections)  
  
     [<span data-ttu-id="0a701-122">암호화 된 연결을 요청 하도록 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="0a701-122">Configure the client to request encrypted connections</span></span>](#ConfigureClientConnections)  
  
     [<span data-ttu-id="0a701-123">SQL Server Management Studio의 연결 암호화</span><span class="sxs-lookup"><span data-stu-id="0a701-123">Encrypt a connection from SQL Server Management Studio</span></span>](#EncryptConnection)  
  
##  <a name="SSMSProcedure"></a>  
  
###  <a name="to-provision-install-a-certificate-on-the-server"></a><a name="Provision"></a> <span data-ttu-id="0a701-124">서버에 인증서를 구축(설치)하려면</span><span class="sxs-lookup"><span data-stu-id="0a701-124">To provision (install) a certificate on the server</span></span>  
  
1.  <span data-ttu-id="0a701-125">**시작** 메뉴에서 **실행**을 클릭 하 고 **열기** 상자에를 입력 `MMC` 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-125">On the **Start** menu, click **Run**, and in the **Open** box, type `MMC` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="0a701-126">MMC 콘솔의 **파일** 메뉴에서 **스냅인 추가/제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-126">In the MMC console, on the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
3.  <span data-ttu-id="0a701-127">**스냅인 추가/제거** 대화 상자에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-127">In the **Add/Remove Snap-in** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="0a701-128">**독립 실행형 스냅인 추가** 대화 상자에서 **인증서**를 클릭하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-128">In the **Add Standalone Snap-in** dialog box, click **Certificates**, click **Add**.</span></span>  
  
5.  <span data-ttu-id="0a701-129">**인증서 스냅인** 대화 상자에서 **컴퓨터 계정**을 클릭한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-129">In the **Certificates snap-in** dialog box, click **Computer account**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="0a701-130">**독립 실행형 스냅인 추가** 대화 상자에서 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-130">In the **Add Standalone Snap-in** dialog box, click **Close.**</span></span>  
  
7.  <span data-ttu-id="0a701-131">**스냅인 추가/제거** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-131">In the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="0a701-132">**인증서** 스냅인에서 **인증서**, **개인**을 차례로 확장한 다음 **인증서**를 마우스 오른쪽 단추로 클릭하고 **모든 태스크**를 가리킨 다음 **가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-132">In the **Certificates** snap-in, expand **Certificates**, expand **Personal**, and then right-click **Certificates**, point to **All Tasks**, and then click **Import**.</span></span>  
  
9. <span data-ttu-id="0a701-133">**인증서 가져오기 마법사**를 완료하여 컴퓨터에 인증서를 추가하고 MMC 콘솔을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-133">Complete the **Certificate Import Wizard**, to add a certificate to the computer, and close the MMC console.</span></span> <span data-ttu-id="0a701-134">컴퓨터에 인증서를 추가하는 방법은 Windows 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a701-134">For more information about adding a certificate to a computer, see your Windows documentation.</span></span>  
  
###  <a name="to-export-the-server-certificate"></a><a name="Export"></a> <span data-ttu-id="0a701-135">서버 인증서를 내보내려면</span><span class="sxs-lookup"><span data-stu-id="0a701-135">To export the server certificate</span></span>  
  
1.  <span data-ttu-id="0a701-136">**인증서** 스냅인의 **인증서** / **개인** 폴더에서 인증서를 찾은 다음 **인증서**를 마우스 오른쪽 단추로 클릭하고 **모든 태스크**를 가리킨 다음 **내보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-136">From the **Certificates** snap-in, locate the certificate in the **Certificates** / **Personal** folder, right-click the **Certificate**, point to **All Tasks**, and then click **Export**.</span></span>  
  
2.  <span data-ttu-id="0a701-137">편리한 위치에 인증서 파일을 저장하여 **인증서 내보내기 마법사**를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-137">Complete the **Certificate Export Wizard**, storing the certificate file in a convenient location.</span></span>  
  
###  <a name="to-configure-the-server-to-accept-encrypted-connections"></a><a name="ConfigureServerConnections"></a> <span data-ttu-id="0a701-138">암호화된 연결을 허용하도록 서버를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="0a701-138">To configure the server to accept encrypted connections</span></span>  
  
1.  <span data-ttu-id="0a701-139">**SQL Server 구성 관리자**에서 **SQL Server 네트워크 구성**을 확장하고 _\<server instance>_ 에 대한 **프로토콜**을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-139">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, right-click **Protocols for** _\<server instance>_, and then select**Properties**.</span></span>  
  
2.  <span data-ttu-id="0a701-140">속성 **에 대 한 프로토콜** _\<instance name>_ **Properties** 대화 상자 **에서 인증서** 탭의 **인증서** 상자에 대 한 드롭다운에서 원하는 인증서를 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-140">In the **Protocols for**_\<instance name>_ **Properties** dialog box, on the **Certificate** tab, select the desired certificate from the drop down for the **Certificate** box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="0a701-141">**플래그** 탭의 **ForceEncryption** 상자에서 **예**를 선택한 다음 **확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-141">On the **Flags** tab, in the **ForceEncryption** box, select **Yes**, and then click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="0a701-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-142">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
###  <a name="to-configure-the-client-to-request-encrypted-connections"></a><a name="ConfigureClientConnections"></a> <span data-ttu-id="0a701-143">암호화된 연결을 요청하도록 클라이언트를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="0a701-143">To configure the client to request encrypted connections</span></span>  
  
1.  <span data-ttu-id="0a701-144">원래 인증서 또는 내보낸 인증서 파일을 클라이언트 컴퓨터로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-144">Copy either the original certificate or the exported certificate file to the client computer.</span></span>  
  
2.  <span data-ttu-id="0a701-145">클라이언트 컴퓨터에서 **인증서** 스냅인을 사용하여 루트 인증서 또는 내보낸 인증서 파일을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-145">On the client computer, use the **Certificates** snap-in to install either the root certificate or the exported certificate file.</span></span>  
  
3.  <span data-ttu-id="0a701-146">콘솔 창에서 **SQL Server Native Client 구성**을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-146">In the console pane, right-click **SQL Server Native Client Configuration**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0a701-147">**플래그** 페이지의 **프로토콜 암호화 강제 사용** 상자에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-147">On the **Flags** page, in the **Force protocol encryption** box, click **Yes**.</span></span>  
  
###  <a name="to-encrypt-a-connection-from-sql-server-management-studio"></a><a name="EncryptConnection"></a><span data-ttu-id="0a701-148">SQL Server Management Studio에서 연결을 암호화 하려면</span><span class="sxs-lookup"><span data-stu-id="0a701-148">To encrypt a connection from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="0a701-149">개체 탐색기 도구 모음에서 **연결**, **데이터베이스 엔진**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-149">On the Object Explorer toolbar, click **Connect**, and then click **Database Engine**.</span></span>  
  
2.  <span data-ttu-id="0a701-150">**서버에 연결** 대화 상자에서 연결 정보를 지정한 다음 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-150">In the **Connect to Server** dialog box, complete the connection information, and then click **Options**.</span></span>  
  
3.  <span data-ttu-id="0a701-151">**연결 속성** 탭에서 **연결 암호화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a701-151">On the **Connection Properties** tab, click **Encrypt connection**.</span></span>  
  
  
