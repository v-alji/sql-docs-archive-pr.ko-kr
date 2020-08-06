---
title: Kerberos 연결의 서비스 사용자 이름 등록 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SPNs
- network connections [SQL Server], SPNs
- registering SPNs
- Server Principal Names
- SPNs [SQL Server]
ms.assetid: e38d5ce4-e538-4ab9-be67-7046e0d9504e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4db1e8b86fca057acbce29491be9c2be91f0748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659644"
---
# <a name="register-a-service-principal-name-for-kerberos-connections"></a><span data-ttu-id="6f946-102">Kerberos 연결의 서비스 사용자 이름 등록</span><span class="sxs-lookup"><span data-stu-id="6f946-102">Register a Service Principal Name for Kerberos Connections</span></span>
  <span data-ttu-id="6f946-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 Kerberos 인증을 사용하려면 다음 조건 중 하나에 해당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-103">To use Kerberos authentication with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires both the following conditions to be true:</span></span>  
  
-   <span data-ttu-id="6f946-104">클라이언트 및 서버 컴퓨터는 동일한 Windows 도메인이나 트러스트된 도메인의 일부여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-104">The client and server computers must be part of the same Windows domain, or in trusted domains.</span></span>  
  
-   <span data-ttu-id="6f946-105">SPN(서비스 사용자 이름)은 Windows 도메인에서 키 배포 센터 역할을 가정하는 Active Directory에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-105">A Service Principal Name (SPN) must be registered with Active Directory, which assumes the role of the Key Distribution Center in a Windows domain.</span></span> <span data-ttu-id="6f946-106">SPN은 등록된 후에, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 서비스를 시작하는 Windows 계정에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-106">The SPN, after it is registered, maps to the Windows account that started the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance service.</span></span> <span data-ttu-id="6f946-107">SPN 등록이 수행되지 않았거나 실패하면 Windows 보안 계층이 SPN과 연결된 계층을 결정할 수 없고 Kerberos 인증이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-107">If the SPN registration has not been performed or fails, the Windows security layer cannot determine the account associated with the SPN, and Kerberos authentication will not be used.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f946-108">서버가 SPN을 자동으로 등록할 수 없으면 SPN을 수동으로 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-108">If the server cannot automatically register the SPN, the SPN must be registered manually.</span></span> <span data-ttu-id="6f946-109">[수동 SPN 등록](#Manual)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f946-109">See [Manual SPN Registration](#Manual).</span></span>  
  
 <span data-ttu-id="6f946-110">sys.dm_exec_connections 동적 관리 뷰를 쿼리하여 연결에 Kerberos가 사용되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-110">You can verify that a connection is using Kerberos by querying the sys.dm_exec_connections dynamic management view.</span></span> <span data-ttu-id="6f946-111">다음 쿼리를 실행하고, Kerberos를 사용할 수 있을 경우 "KERBEROS"가 되는 auth_scheme 열의 값을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f946-111">Run the following query and check the value of the auth_scheme column, which will be "KERBEROS" if Kerberos is enabled.</span></span>  
  
```  
SELECT auth_scheme FROM sys.dm_exec_connections WHERE session_id = @@spid ;  
```  
  
> [!TIP]  
>  <span data-ttu-id="6f946-112">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]용 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos 구성 관리자**는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]과의 Kerberos 관련 연결 문제를 해결하는 진단 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-112">**[!INCLUDE[msCoName](../../includes/msconame-md.md)] Kerberos Configuration Manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** is a diagnostic tool that helps troubleshoot Kerberos related connectivity issues with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6f946-113">자세한 내용은 [SQL Server용 Microsoft Kerberos 구성 관리자](https://www.microsoft.com/download/details.aspx?id=39046)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f946-113">For more information, see [Microsoft Kerberos Configuration Manager for SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).</span></span>  
  
##  <a name="the-role-of-the-spn-in-authentication"></a><a name="Role"></a> <span data-ttu-id="6f946-114">인증에서 SPN의 역할</span><span class="sxs-lookup"><span data-stu-id="6f946-114">The Role of the SPN in Authentication</span></span>  
 <span data-ttu-id="6f946-115">애플리케이션에서 연결을 열고 Windows 인증을 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 컴퓨터 이름, 인스턴스 이름 및 필요에 따라 SPN을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-115">When an application opens a connection and uses Windows Authentication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client passes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer name, instance name and, optionally, an SPN.</span></span> <span data-ttu-id="6f946-116">연결이 SPN을 전달하면 변경 사항 없이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-116">If the connection passes an SPN it is used without any changes.</span></span>  
  
 <span data-ttu-id="6f946-117">연결이 SPN을 전달하지 않으면 기본 SPN이 사용된 프로토콜, 서버 이름 및 인스턴스 이름에 따라 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-117">If the connection does not pass an SPN, a default SPN is constructed based on the protocol used, server name, and the instance name.</span></span>  
  
 <span data-ttu-id="6f946-118">위의 두 시나리오에서 SPN은 키 배포 센터에 전달되어 연결 인증을 위한 보안 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-118">In both of the preceding scenarios, the SPN is sent to the Key Distribution Center to obtain a security token for authenticating the connection.</span></span> <span data-ttu-id="6f946-119">보안 토큰을 가져올 수 없으면 인증이 NTLM을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-119">If a security token cannot be obtained, authentication uses NTLM.</span></span>  
  
 <span data-ttu-id="6f946-120">SPN(서비스 사용자 이름)은 클라이언트가 서비스 인스턴스를 고유하게 식별하는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-120">A service principal name (SPN) is the name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="6f946-121">Kerberos 인증 서비스에서는 서비스를 인증하는 데 SPN을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-121">The Kerberos authentication service can use an SPN to authenticate a service.</span></span> <span data-ttu-id="6f946-122">클라이언트는 서비스에 연결할 때 서비스의 인스턴스를 찾고 해당 인스턴스에 대한 SPN을 작성한 다음 서비스에 연결하고 인증을 위해 서비스에 대한 SPN을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-122">When a client wants to connect to a service, it locates an instance of the service, composes an SPN for that instance, connects to the service, and presents the SPN for the service to authenticate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f946-123">이 항목에 설명된 정보는 클러스터링을 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-123">The information that is provided in this topic also applies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurations that use clustering.</span></span>  
  
 <span data-ttu-id="6f946-124">Windows 인증은 사용자를 SQL Server에 인증하는 데 사용하는 기본 인증 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-124">Windows Authentication is the preferred method for users to authenticate to SQL Server.</span></span> <span data-ttu-id="6f946-125">Windows 인증을 사용하는 클라이언트는 NTLM이나 Kerberos를 사용하여 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-125">Clients that use Windows Authentication are authenticated by either using NTLM or Kerberos.</span></span> <span data-ttu-id="6f946-126">Active Directory 환경에서는 항상 Kerberos 인증이 먼저 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-126">In an Active Directory environment, Kerberos authentication is always attempted first.</span></span> <span data-ttu-id="6f946-127">명명된 파이프를 사용하는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 클라이언트에는 Kerberos 인증을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-127">Kerberos authentication is not available for [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] clients using named pipes.</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6f946-128">권한</span><span class="sxs-lookup"><span data-stu-id="6f946-128">Permissions</span></span>  
 <span data-ttu-id="6f946-129">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 서비스를 시작하면 서비스가 SPN(서비스 사용자 이름)을 등록하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-129">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service starts, it attempts to register the Service Principal Name (SPN).</span></span> <span data-ttu-id="6f946-130">SQL Server를 시작하는 계정에 Active Directory Domain Services에 SPN을 등록할 권한이 없으면 이 호출이 실패하고 애플리케이션 이벤트 로그와 SQL Server 오류 로그에 경고 메시지가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-130">If the account starting SQL Server doesn't have permission to register a SPN in Active Directory Domain Services, this call will fail and a warning message will be logged in the Application event log as well as the SQL Server error log.</span></span> <span data-ttu-id="6f946-131">SPN을 등록하려면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 로컬 시스템(권장되지 않음) 또는 NETWORK SERVICE와 같은 기본 제공 계정이나 도메인 관리자 계정과 같은 SPN 등록 권한이 있는 계정으로 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-131">To register the SPN, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be running under a built-in account, such as Local System (not recommended), or NETWORK SERVICE, or an account that has permission to register an SPN, such as a domain administrator account.</span></span> <span data-ttu-id="6f946-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가  [!INCLUDE[win7](../../includes/win7-md.md)] 또는  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 운영 체제에서 실행 중인 경우 가상 계정이나 MSA(관리 서비스 계정)를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-132">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running on the  [!INCLUDE[win7](../../includes/win7-md.md)] or  [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] operating system, you can run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a virtual account or a managed service account (MSA).</span></span> <span data-ttu-id="6f946-133">가상 계정 및 MSA 모두 SPN을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-133">Both virtual accounts and MSA's can register an SPN.</span></span> <span data-ttu-id="6f946-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 이러한 계정 중 하나로 실행되고 있지 않으면 시작할 때 SPN이 등록되지 않으므로 도메인 관리자가 SPN을 수동으로 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-134">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running under one of these accounts, the SPN is not registered at startup and the domain administrator must register the SPN manually.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f946-135">Windows 도메인이 적어도 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Windows Server 2008 R2 기능 수준 이상에서 실행되도록 구성된 경우 관리 서비스 계정에는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 서비스의 SPN을 등록하는 데 필요한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-135">When the Windows domain is configured to run at less than the [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Windows Server 2008 R2 functional level, then the Managed Service Account will not have the necessary permissions to register the SPNs for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span> <span data-ttu-id="6f946-136">Kerberos 인증이 필요한 경우 도메인 관리자는 관리 서비스 계정에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SPN을 수동으로 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-136">If Kerberos authentication is required, the Domain Administrator should manually register the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SPNs on the Managed Service Account.</span></span>  
  
 <span data-ttu-id="6f946-137">기술 자료 문서 [SQL Server에서 Kerberos 인증을 사용하는 방법](https://support.microsoft.com/kb/319723)에는 도메인 관리자가 아닌 계정에 SPN 읽기/쓰기 권한을 부여하는 방법이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-137">The KB article, [How to use Kerberos authentication in SQL Server](https://support.microsoft.com/kb/319723), contains information about how to grant read or write permission to an SPN for an account that is not a Domain Administrator.</span></span>  
  
 <span data-ttu-id="6f946-138">추가 정보는 [SQL Server 2008에서 Kerberos 제한된 위임을 구현하는 방법(How to Implement Kerberos Constrained Delegation with SQL Server 2008)](https://technet.microsoft.com/library/ee191523.aspx)에서 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-138">Additional information is available at [How to Implement Kerberos Constrained Delegation with SQL Server 2008](https://technet.microsoft.com/library/ee191523.aspx)</span></span>  
  
##  <a name="spn-formats"></a><a name="Formats"></a> <span data-ttu-id="6f946-139">SPN 형식</span><span class="sxs-lookup"><span data-stu-id="6f946-139">SPN Formats</span></span>  
 <span data-ttu-id="6f946-140">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]부터 SPN 형식이 TCP/IP, 명명된 파이프 및 공유 메모리에서 Kerberos 인증을 지원하도록 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-140">Beginning with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SPN format is changed in order to support Kerberos authentication on TCP/IP, named pipes, and shared memory.</span></span> <span data-ttu-id="6f946-141">명명된 인스턴스 및 기본 인스턴스에 대해 지원되는 SPN 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-141">The supported SPN formats for named and default instances are as follows.</span></span>  
  
 <span data-ttu-id="6f946-142">**명명된 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="6f946-142">**Named instance**</span></span>  
  
-   <span data-ttu-id="6f946-143">*MSSQLSvc/FQDN*:[_port_**|**_instancename_], 여기서:</span><span class="sxs-lookup"><span data-stu-id="6f946-143">*MSSQLSvc/FQDN*:[_port_**|**_instancename_], where:</span></span>  
  
    -   <span data-ttu-id="6f946-144">*MSSQLSvc* 는 등록할 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-144">*MSSQLSvc* is the service that is being registered.</span></span>  
  
    -   <span data-ttu-id="6f946-145">*FQDN* 은 서버의 정규화 된 도메인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-145">*FQDN* is the fully qualified domain name of the server.</span></span>  
  
    -   <span data-ttu-id="6f946-146">*port* 는 TCP 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-146">*port* is the TCP port number.</span></span>  
  
    -   <span data-ttu-id="6f946-147">*instancename* 은 인스턴스의 이름입니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6f946-147">*instancename* is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="6f946-148">**기본 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="6f946-148">**Default instance**</span></span>  
  
-   <span data-ttu-id="6f946-149">*MSSQLSvc/fqdn*:_port_ **|** _MSSQLSvc/fqdn_, 여기서:</span><span class="sxs-lookup"><span data-stu-id="6f946-149">*MSSQLSvc/FQDN*:_port_**|**_MSSQLSvc/FQDN_, where:</span></span>  
  
    -   <span data-ttu-id="6f946-150">*MSSQLSvc* 는 등록할 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-150">*MSSQLSvc* is the service that is being registered.</span></span>  
  
    -   <span data-ttu-id="6f946-151">*FQDN* 은 서버의 정규화 된 도메인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-151">*FQDN* is the fully qualified domain name of the server.</span></span>  
  
    -   <span data-ttu-id="6f946-152">*port* 는 TCP 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-152">*port* is the TCP port number.</span></span>  
  
 <span data-ttu-id="6f946-153">새로운 SPN 형식에는 포트 번호가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-153">The new SPN format does not require a port number.</span></span> <span data-ttu-id="6f946-154">따라서 포트 번호를 사용하지 않는 다중 포트 서버 또는 프로토콜이 Kerberos 인증을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-154">This means that a multiple-port server or a protocol that does not use port numbers can use Kerberos authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f946-155">SPN에 TCP 포트가 포함되는 TCP/IP 연결의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 Kerberos 인증을 사용하여 연결하는 사용자를 위해 TCP 프로토콜을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-155">In the case of a TCP/IP connection, where the TCP port is included in the SPN, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must enable the TCP protocol for a user to connect by using Kerberos authentication.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6f946-156">MSSQLSvc/*fqdn: 포트*</span><span class="sxs-lookup"><span data-stu-id="6f946-156">MSSQLSvc/*fqdn:port*</span></span>|<span data-ttu-id="6f946-157">TCP가 사용될 때 공급자가 생성하는 기본 SPN입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-157">The provider-generated, default SPN when TCP is used.</span></span> <span data-ttu-id="6f946-158">*port* 는 TCP 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-158">*port* is a TCP port number.</span></span>|  
|<span data-ttu-id="6f946-159">MSSQLSvc/*fqdn*</span><span class="sxs-lookup"><span data-stu-id="6f946-159">MSSQLSvc/*fqdn*</span></span>|<span data-ttu-id="6f946-160">TCP 이외의 프로토콜이 사용될 때 기본 인스턴스에 대해 공급자가 생성하는 기본 SPN입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-160">The provider-generated, default SPN for a default instance when a protocol other than TCP is used.</span></span> <span data-ttu-id="6f946-161">*fqdn* 은 정규화 된 도메인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-161">*fqdn* is a fully-qualified domain name.</span></span>|  
|<span data-ttu-id="6f946-162">MSSQLSvc/*fqdn: InstanceName*</span><span class="sxs-lookup"><span data-stu-id="6f946-162">MSSQLSvc/*fqdn:InstanceName*</span></span>|<span data-ttu-id="6f946-163">TCP 이외의 프로토콜이 사용될 때 명명된 인스턴스에 대해 공급자가 생성하는 기본 SPN입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-163">The provider-generated, default SPN for a named instance when a protocol other than TCP is used.</span></span> <span data-ttu-id="6f946-164">*InstanceName* 은 인스턴스의 이름입니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6f946-164">*InstanceName* is the name of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
  
##  <a name="automatic-spn-registration"></a><a name="Auto"></a> <span data-ttu-id="6f946-165">SPN 자동 등록</span><span class="sxs-lookup"><span data-stu-id="6f946-165">Automatic SPN Registration</span></span>  
 <span data-ttu-id="6f946-166">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스가 시작되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스에 대한 SPN을 등록하려고 하고,</span><span class="sxs-lookup"><span data-stu-id="6f946-166">When an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] starts, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to register the SPN for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="6f946-167">인스턴스가 중지되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 SPN의 등록을 취소하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-167">When the instance is stopped, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tries to unregister the SPN.</span></span> <span data-ttu-id="6f946-168">TCP/IP 연결에서 SPN은 *MSSQLSvc/\<FQDN>* : *\<tcpport>* 형식으로 등록됩니다. 명명된 인스턴스와 기본 인스턴스는 모두 *MSSQLSvc*로 등록되며 *\<tcpport>* 값으로 인스턴스를 구문합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-168">For a TCP/IP connection the SPN is registered in the format *MSSQLSvc/\<FQDN>*:*\<tcpport>*.Both named instances and the default instance are registered as *MSSQLSvc*, relying on the *\<tcpport>* value to differentiate the instances.</span></span>  
  
 <span data-ttu-id="6f946-169">Kerberos를 지 원하는 다른 연결의 경우 SPN은 명명 된 인스턴스의 경우 *MSSQLSvc \<FQDN> /*: 형식으로 등록 됩니다 *\<instancename>* .</span><span class="sxs-lookup"><span data-stu-id="6f946-169">For other connections that support Kerberos the SPN is registered in the format *MSSQLSvc/\<FQDN>*:*\<instancename>* for a named instance.</span></span> <span data-ttu-id="6f946-170">기본 인스턴스는 *MSSQLSvc/\<FQDN>* 형식으로 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-170">The format for registering the default instance is *MSSQLSvc/\<FQDN>*.</span></span>  
  
 <span data-ttu-id="6f946-171">서비스 계정에 이러한 동작을 수행하는 데 필요한 권한이 없는 경우에는 수동으로 SPN을 등록하거나 등록 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-171">Manual intervention might be required to register or unregister the SPN if the service account lacks the permissions that are required for these actions.</span></span>  
  
##  <a name="manual-spn-registration"></a><a name="Manual"></a> <span data-ttu-id="6f946-172">수동 SPN 등록</span><span class="sxs-lookup"><span data-stu-id="6f946-172">Manual SPN Registration</span></span>  
 <span data-ttu-id="6f946-173">SPN을 수동으로 등록하려면 관리자가 Microsoft [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 지원 도구와 함께 제공되는 Setspn.exe 도구를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-173">To register the SPN manually, the administrator must use the Setspn.exe tool that is provided with the Microsoft [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] Support Tools.</span></span> <span data-ttu-id="6f946-174">자세한 내용은 [Windows Server 2003 서비스 팩 1 지원 도구](https://support.microsoft.com/kb/892777) 기술 자료 문서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f946-174">For more information, see the [Windows Server 2003 Service Pack 1 Support Tools](https://support.microsoft.com/kb/892777) KB article.</span></span>  
  
 <span data-ttu-id="6f946-175">Setspn.exe는 SPN 디렉터리 속성을 읽고 수정하고 삭제하는 데 사용할 수 있는 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-175">Setspn.exe is a command line tool that enables you to read, modify, and delete the Service Principal Names (SPN) directory property.</span></span> <span data-ttu-id="6f946-176">또한 이 도구를 통해 현재 SPN을 보고 계정의 기본 SPN을 다시 설정하고 보조 SPN을 추가 또는 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-176">This tool also enables you to view the current SPNs, reset the account's default SPNs, and add or delete supplemental SPNs.</span></span>  
  
 <span data-ttu-id="6f946-177">다음 예에서는 TCP/IP 연결에 대한 SPN을 수동으로 등록하는 데 사용되는 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-177">The following example illustrates the syntax used to register manually register an SPN for a TCP/IP connection.</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:1433 accountname  
```  
  
 <span data-ttu-id="6f946-178">**참고** SPN이 이미 있는 경우에는 해당 SPN을 삭제한 후 다시 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-178">**Note** If an SPN already exists, it must be deleted before it can be reregistered.</span></span> <span data-ttu-id="6f946-179">이 작업을 수행하려면 `setspn` 명령을 `-D` 스위치와 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-179">You do this by using the `setspn` command together with the `-D` switch.</span></span> <span data-ttu-id="6f946-180">다음 예에서는 새로운 인스턴스 기반 SPN을 수동으로 등록하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-180">The following examples illustrate how to manually register a new instance-based SPN.</span></span> <span data-ttu-id="6f946-181">기본 인스턴스의 경우에는 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-181">For a default instance, use:</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com accountname  
```  
  
 <span data-ttu-id="6f946-182">명명된 인스턴스의 경우에는 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-182">For a named instance, use:</span></span>  
  
```  
setspn -A MSSQLSvc/myhost.redmond.microsoft.com:instancename accountname  
```  
  
##  <a name="client-connections"></a><a name="Client"></a> <span data-ttu-id="6f946-183">클라이언트 연결</span><span class="sxs-lookup"><span data-stu-id="6f946-183">Client Connections</span></span>  
 <span data-ttu-id="6f946-184">사용자 지정 SPN은 클라이언트 드라이버에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-184">User-specified SPNs are supported in client drivers.</span></span> <span data-ttu-id="6f946-185">하지만 SPN이 제공되지 않은 경우 클라이언트 연결 유형을 기준으로 SPN이 자동 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-185">However, if an SPN is not provided, it will be generated automatically based on the type of a client connection.</span></span> <span data-ttu-id="6f946-186">TCP 연결의 경우 명명된 인스턴스와 기본 인스턴스 모두에 대해 *MSSQLSvc*/*FQDN*:[*port*] 형식의 SPN이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-186">For a TCP connection, an SPN in the format *MSSQLSvc*/*FQDN*:[*port*] is used for both the named and default instances.</span></span>  
  
 <span data-ttu-id="6f946-187">명명 된 파이프 및 공유 메모리 연결의 경우 *MSSQLSvc* / *fqdn*:*instancename* 형식의 SPN이 명명 된 인스턴스에 사용 되며 *MSSQLSvc* / *fqdn* 이 기본 인스턴스에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-187">For named pipes and shared memory connections, an SPN in the format *MSSQLSvc*/*FQDN*:*instancename* is used for a named instance and *MSSQLSvc*/*FQDN* is used for the default instance.</span></span>  
  
 <span data-ttu-id="6f946-188">**서비스 계정을 SPN으로 사용**</span><span class="sxs-lookup"><span data-stu-id="6f946-188">**Using a service account as an SPN**</span></span>  
  
 <span data-ttu-id="6f946-189">서비스 계정을 SPN으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-189">Service accounts can be used as an SPN.</span></span> <span data-ttu-id="6f946-190">서비스 계정은 Kerberos 인증에 대한 연결 특성을 통해 지정되며 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-190">They are specified through the connection attribute for the Kerberos authentication and take the following formats:</span></span>  
  
-   <span data-ttu-id="6f946-191">**username@domain**도메인 사용자 계정에 대 한 도메인 \**\** 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="6f946-191">**username@domain** or **domain\username** for a domain user account</span></span>  
  
-   <span data-ttu-id="6f946-192">**machine$@domain** 또는 **host\FQDN**(로컬 시스템 또는 NETWORK SERVICES와 같은 컴퓨터 도메인 계정의 경우)</span><span class="sxs-lookup"><span data-stu-id="6f946-192">**machine$@domain** or **host\FQDN** for a computer domain account such as Local System or NETWORK SERVICES.</span></span>  
  
 <span data-ttu-id="6f946-193">연결 인증 방법을 확인하려면 다음 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-193">To determine the authentication method of a connection, execute the following query.</span></span>  
  
```sql  
SELECT net_transport, auth_scheme   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
```  
  
##  <a name="authentication-defaults"></a><a name="Defaults"></a> <span data-ttu-id="6f946-194">인증 기본값</span><span class="sxs-lookup"><span data-stu-id="6f946-194">Authentication Defaults</span></span>  
 <span data-ttu-id="6f946-195">다음 표에서는 SPN 등록 시나리오에 따라 다르게 사용되는 인증 기본값에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-195">The following table describes the authentication defaults that are used based on SPN registration scenarios.</span></span>  
  
|<span data-ttu-id="6f946-196">시나리오</span><span class="sxs-lookup"><span data-stu-id="6f946-196">Scenario</span></span>|<span data-ttu-id="6f946-197">인증 방법</span><span class="sxs-lookup"><span data-stu-id="6f946-197">Authentication method</span></span>|  
|--------------|---------------------------|  
|<span data-ttu-id="6f946-198">SPN이 올바른 도메인 계정, 가상 계정, MSA 또는 기본 제공 계정에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-198">The SPN maps to the correct domain account, virtual account, MSA, or built-in account.</span></span> <span data-ttu-id="6f946-199">예를 들어 로컬 시스템 또는 NETWORK SERVICE에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-199">For example, Local System or NETWORK SERVICE.</span></span><br /><br /> <span data-ttu-id="6f946-200">참고: 올바른 것은 등록 된 SPN에 의해 매핑되는 계정이 SQL Server 서비스가 실행 되 고 있는 계정 임을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-200">Note: Correct means that the account mapped by the registered SPN is the account that the SQL Server service is running under.</span></span>|<span data-ttu-id="6f946-201">로컬 연결은 NTLM을 사용하고, 원격 연결은 Kerberos를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-201">Local connections use NTLM, remote connections use Kerberos.</span></span>|  
|<span data-ttu-id="6f946-202">SPN이 올바른 도메인 계정, 가상 계정, MSA 또는 기본 제공 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-202">The SPN is the correct domain account, virtual account, MSA, or built-in account.</span></span><br /><br /> <span data-ttu-id="6f946-203">참고: 올바른 것은 등록 된 SPN에 의해 매핑되는 계정이 SQL Server 서비스가 실행 되 고 있는 계정 임을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-203">Note: Correct means that the account mapped by the registered SPN is the account that the SQL Server service is running under.</span></span>|<span data-ttu-id="6f946-204">로컬 연결은 NTLM을 사용하고, 원격 연결은 Kerberos를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-204">Local connections use NTLM, remote connections use Kerberos.</span></span>|  
|<span data-ttu-id="6f946-205">SPN이 잘못된 도메인 계정, 가상 계정, MSA 또는 기본 제공 계정에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-205">The SPN maps to an incorrect domain account, virtual account, MSA, or built-in account</span></span>|<span data-ttu-id="6f946-206">인증에 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-206">Authentication fails.</span></span>|  
|<span data-ttu-id="6f946-207">SPN 조회에 실패했거나 SPN이 올바른 도메인 계정, 가상 계정, MSA 또는 기본 제공 계정에 매핑되지 않거나 SPN이 올바른 도메인 계정, 가상 계정, MSA 또는 기본 제공 계정이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-207">The SPN lookup fails or does not map to a correct domain account, virtual account, MSA, or built-in account, or is not a correct domain account, virtual account, MSA, or built-in account.</span></span>|<span data-ttu-id="6f946-208">로컬 및 원격 연결이 NTLM을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-208">Local and remote connections use NTLM.</span></span>|  
  
##  <a name="comments"></a><a name="Comments"></a> <span data-ttu-id="6f946-209">설명</span><span class="sxs-lookup"><span data-stu-id="6f946-209">Comments</span></span>  
 <span data-ttu-id="6f946-210">DAC(관리자 전용 연결)는 인스턴스 이름 기반 SPN을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-210">The Dedicated Administrator Connection (DAC) uses an instance name based SPN.</span></span> <span data-ttu-id="6f946-211">해당 SPN이 성공적으로 등록되었으면 DAC에 Kerberos 인증을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-211">Kerberos authentication can be used with a DAC if that SPN is registered successfully.</span></span> <span data-ttu-id="6f946-212">또는 사용자가 계정 이름을 SPN으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-212">As an alternative a user can specify the account name as an SPN.</span></span>  
  
 <span data-ttu-id="6f946-213">시작 시 SPN 등록에 실패하면 해당 내용이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에 기록되고 시작이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-213">If SPN registration fails during startup, this failure is recorded in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, and startup continues.</span></span>  
  
 <span data-ttu-id="6f946-214">종료 시 SPN 등록 취소에 실패하면 해당 내용이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에 기록되고 종료가 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f946-214">If SPN de-registration fails during shutdown, this failure is recorded in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, and shutdown continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f946-215">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f946-215">See Also</span></span>  
 <span data-ttu-id="6f946-216">[클라이언트 연결의 SPN&#40;서비스 사용자 이름&#41; 지원](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) </span><span class="sxs-lookup"><span data-stu-id="6f946-216">[Service Principal Name &#40;SPN&#41; Support in Client Connections](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) </span></span>  
 <span data-ttu-id="6f946-217">[클라이언트 연결의 SPN&#40;서비스 사용자 이름&#41;&#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="6f946-217">[Service Principal Names &#40;SPNs&#41; in Client Connections &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md) </span></span>  
 <span data-ttu-id="6f946-218">[클라이언트 연결의 SPN&#40;서비스 사용자 이름&#41;&#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="6f946-218">[Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) </span></span>  
 <span data-ttu-id="6f946-219">[SQL Server Native Client 기능](../../relational-databases/native-client/features/sql-server-native-client-features.md) </span><span class="sxs-lookup"><span data-stu-id="6f946-219">[SQL Server Native Client Features](../../relational-databases/native-client/features/sql-server-native-client-features.md) </span></span>  
 [<span data-ttu-id="6f946-220">Reporting Services 환경의 Kerberos 인증 문제 관리(영문)</span><span class="sxs-lookup"><span data-stu-id="6f946-220">Manage Kerberos Authentication Issues in a Reporting Services Environment</span></span>](https://technet.microsoft.com/library/ff679930.aspx)  
  
  
