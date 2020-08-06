---
title: 가용성 복제본 추가 또는 수정 시 끝점 URL 지정 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- endpoints [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], endpoint
- Endpoint URLs (HADR)
ms.assetid: d7520c13-a8ee-4ddc-9e9a-54cd3d27ef1c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da1eb2bacd4d5a2f7d0b2a623343f62b5e89597d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741299"
---
# <a name="specify-the-endpoint-url-when-adding-or-modifying-an-availability-replica-sql-server"></a><span data-ttu-id="8cd90-102">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8cd90-102">Specify the Endpoint URL When Adding or Modifying an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="8cd90-103">가용성 그룹에 대한 가용성 복제본을 호스팅하려면 서버 인스턴스에서 데이터베이스 미러링 엔드포인트를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-103">To host an availability replica for an availability group, a server instance must possess a database mirroring endpoint.</span></span> <span data-ttu-id="8cd90-104">서버 인스턴스는 이 엔드포인트를 사용하여 다른 서버 인스턴스에서 호스팅하는 가용성 복제본의 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 메시지를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-104">The server instance uses this endpoint to listen for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] messages from availability replicas hosted by other server instances.</span></span> <span data-ttu-id="8cd90-105">가용성 그룹에 대한 가용성 복제본을 정의하려면 복제본을 호스팅하는 서버 인스턴스의 엔드포인트 URL을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-105">To define an availability replica for an availability group, you must specify the endpoint URL of the server instance that will host the replica.</span></span> <span data-ttu-id="8cd90-106">*엔드포인트 URL*은 데이터베이스 미러링 엔드포인트의 전송 프로토콜인 TCP, 서버 인스턴스의 시스템 주소, 엔드포인트와 연결된 포트 번호를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-106">The *endpoint URL* identifies the transport protocol of the database mirroring endpoint-TCP, the system address of the server instance, and the port number associated with the endpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8cd90-107">"엔드포인트 URL"이라는 용어는 데이터베이스 미러링 사용자 인터페이스 및 설명서에서 사용하는 "서버 네트워크 주소"라는 용어와 동의어입니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-107">The term "endpoint URL" is synonymous with the term "server network address" used by the database mirroring user interface and documentation.</span></span>  
  
-   [<span data-ttu-id="8cd90-108">끝점 URL의 구문</span><span class="sxs-lookup"><span data-stu-id="8cd90-108">Syntax for an Endpoint URL</span></span>](#SyntaxOfURL)  
  
-   [<span data-ttu-id="8cd90-109">시스템의 정규화 된 도메인 이름 찾기</span><span class="sxs-lookup"><span data-stu-id="8cd90-109">Finding the Fully Qualified Domain Name of A System</span></span>](#Finding_FQDN)  
  
-   [<span data-ttu-id="8cd90-110">관련 작업</span><span class="sxs-lookup"><span data-stu-id="8cd90-110">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="8cd90-111">관련 내용</span><span class="sxs-lookup"><span data-stu-id="8cd90-111">Related Content</span></span>](#RelatedContent)  
  
##  <a name="syntax-for-an-endpoint-url"></a><a name="SyntaxOfURL"></a> <span data-ttu-id="8cd90-112">엔드포인트 URL의 구문</span><span class="sxs-lookup"><span data-stu-id="8cd90-112">Syntax for an Endpoint URL</span></span>  
 <span data-ttu-id="8cd90-113">엔드포인트 URL의 구문은 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-113">The syntax for an endpoint URL is of the form:</span></span>  
  
 <span data-ttu-id="8cd90-114">TCP<strong>://</strong> *\<system-address>* <strong>:</strong> *\<port>*</span><span class="sxs-lookup"><span data-stu-id="8cd90-114">TCP<strong>://</strong>*\<system-address>*<strong>:</strong>*\<port>*</span></span>  
  
 <span data-ttu-id="8cd90-115">라는 설치 관리자 실행 파일에 포함됩니다. 여기서</span><span class="sxs-lookup"><span data-stu-id="8cd90-115">where</span></span>  
  
-   <span data-ttu-id="8cd90-116">*\<system-address>* 는 대상 컴퓨터 시스템을 명확하게 식별하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-116">*\<system-address>* is a string that unambiguously identifies the target computer system.</span></span> <span data-ttu-id="8cd90-117">일반적으로 서버 주소는 시스템 이름(시스템이 같은 도메인에 있는 경우), 정규화된 도메인 이름 또는 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-117">Typically, the server address is a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address:</span></span>  
  
    -   <span data-ttu-id="8cd90-118">WSFC(Windows Server 장애 조치(failover) 클러스터링) 노드는 같은 도메인에 있으므로 컴퓨터 시스템의 이름(예: `SYSTEM46`)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-118">Because the nodes of Windows Server Failover Clustering (WSFC) cluster are the same domain, you can use the name of the computer system; for example, `SYSTEM46`.</span></span>  
  
    -   <span data-ttu-id="8cd90-119">IP 주소를 사용하려면 환경에서 고유한 주소여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-119">To use an IP address, it must be unique in your environment.</span></span> <span data-ttu-id="8cd90-120">정적인 경우에만 IP 주소를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-120">We recommend that you use an IP address only if it is static.</span></span> <span data-ttu-id="8cd90-121">IP 주소는 IP 버전 4(IPv4) 또는 IP 버전 6(IPv6)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-121">The IP address can be IP Version 4 (IPv4) or IP Version 6 (IPv6).</span></span> <span data-ttu-id="8cd90-122">IPv6 주소는 대괄호로 묶어야 합니다(예: **[** _<IPv6_address>_ **]** ).</span><span class="sxs-lookup"><span data-stu-id="8cd90-122">An IPv6 address must be enclosed within square brackets, for example: **[**_<IPv6_address>_**]**.</span></span>  
  
         <span data-ttu-id="8cd90-123">시스템의 IP 주소를 확인하려면 Windows 명령 프롬프트에서 **ipconfig** 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-123">To learn the IP address of a system, at the Windows command prompt, enter the **ipconfig** command.</span></span>  
  
    -   <span data-ttu-id="8cd90-124">정규화된 도메인 이름을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-124">The fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="8cd90-125">이 주소 문자열은 로컬로 정의되므로 위치에 따라 형식이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-125">This is a locally defined address string that takes different forms in different places.</span></span> <span data-ttu-id="8cd90-126">항상은 아니지만 정규화된 도메인 이름은 컴퓨터 이름과 마침표로 구분된 일련의 도메인 세그먼트를 다음 형식으로 포함하는 복합 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-126">Often, but not always, a fully qualified domain name is a compound name that includes the computer name and a series of period-separated domain segments of the form:</span></span>  
  
         <span data-ttu-id="8cd90-127">_computer_name_ **.**</span><span class="sxs-lookup"><span data-stu-id="8cd90-127">_computer_name_ **.**</span></span> <span data-ttu-id="8cd90-128">_domain_segment_[... **.** _domain_segment_]</span><span class="sxs-lookup"><span data-stu-id="8cd90-128">_domain_segment_[...**.**_domain_segment_]</span></span>  
  
         <span data-ttu-id="8cd90-129">여기에서 *computer_name*은 서버 인스턴스를 실행하는 컴퓨터의 네트워크 이름이고 *domain_segment*[... **.** _domain_segment_]는 서버의 나머지 도메인 정보입니다(예: `localinfo.corp.Adventure-Works.com`).</span><span class="sxs-lookup"><span data-stu-id="8cd90-129">where *computer_name i*s the network name of the computer running the server instance, and *domain_segment*[...**.**_domain_segment_] is the remaining domain information of the server; for example: `localinfo.corp.Adventure-Works.com`.</span></span>  
  
         <span data-ttu-id="8cd90-130">도메인 세그먼트의 내용과 개수는 회사 또는 조직 내에서 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-130">The content and number of domain segments are determined within the company or organization.</span></span> <span data-ttu-id="8cd90-131">자세한 내용은 이 항목의 뒷부분에 나오는 [정규화된 도메인 이름 찾기](#Finding_FQDN)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8cd90-131">For more information, see [Finding the Fully Qualified Domain Name](#Finding_FQDN), later in this topic.</span></span>  
  
-   <span data-ttu-id="8cd90-132">*\<port>* 는 파트너 서버 인스턴스의 미러링 엔드포인트에 사용되는 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-132">*\<port>* is the port number used by the mirroring endpoint of the partner server instance.</span></span>  
  
     <span data-ttu-id="8cd90-133">데이터베이스 미러링 엔드포인트는 컴퓨터 시스템에서 사용 가능한 모든 포트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-133">A database mirroring endpoint can use any available port on the computer system.</span></span> <span data-ttu-id="8cd90-134">각 포트 번호는 하나의 엔드포인트에만 연결되어야 하고 각 엔드포인트는 단일 서버 인스턴스와 연결되므로 같은 서버의 서로 다른 서버 인스턴스는 서로 다른 포트의 각 엔드포인트에서 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-134">Each port number must be associated with only one endpoint, and each endpoint is associated with a single server instance; thus, different server instances on the same server listen on different endpoints with different ports.</span></span> <span data-ttu-id="8cd90-135">따라서 가용성 복제본을 지정할 때 엔드포인트 URL에서 지정하는 포트는 항상 들어오는 메시지를 엔드포인트가 해당 포트와 연결된 서버 인스턴스로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-135">Therefore, the port you specify in the endpoint URL when you specify an availability replica will always direct incoming messages to the server instance whose endpoint is associated with that port.</span></span>  
  
     <span data-ttu-id="8cd90-136">엔드포인트 URL에서는 포트 번호를 통해서만 대상 컴퓨터에서 미러링 엔드포인트와 연결되는 서버 인스턴스가 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-136">IIn the endpoint URL, only the number of the port identifies the server instance that is associated with the mirroring endpoint on the target computer.</span></span> <span data-ttu-id="8cd90-137">다음 그림에서는 단일 컴퓨터에 있는 두 서버 인스턴스의 엔드포인트 URL을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-137">The following figure illustrates the endpoint URLs of two server instances on a single computer.</span></span> <span data-ttu-id="8cd90-138">기본 인스턴스는 포트 `7022` 를 사용하고 명명된 인스턴스는 포트 `7033`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-138">The default instance uses port `7022` and the named instance uses port `7033`.</span></span> <span data-ttu-id="8cd90-139">이러한 두 서버 인스턴스에 대한 엔드포인트 URL은 각각 `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` 및 `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`입니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-139">The endpoint URL for these two server instances are, respectively: `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` and `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`.</span></span> <span data-ttu-id="8cd90-140">주소에는 서버 인스턴스 이름이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-140">Note that the address does not contain the name of the server instance.</span></span>  
  
     <span data-ttu-id="8cd90-141">![기본 인스턴스의 서버 네트워크 주소](../../media/dbm-2-instances-ports-1-system.gif "기본 인스턴스의 서버 네트워크 주소")</span><span class="sxs-lookup"><span data-stu-id="8cd90-141">![Server network addresses of a default instance](../../media/dbm-2-instances-ports-1-system.gif "Server network addresses of a default instance")</span></span>  
  
     <span data-ttu-id="8cd90-142">서버 인스턴스의 데이터베이스 미러링 엔드포인트와 현재 연결된 포트를 식별하려면 다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-142">To identify the port currently associated with database mirroring endpoint of a server instance, use the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql
    SELECT type_desc, port FROM sys.TCP_endpoints  
    ```  
  
     <span data-ttu-id="8cd90-143">**type_desc** 값이 "DATABASE_MIRRORING"인 행을 찾아 해당 포트 번호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-143">Find the row whose **type_desc** value is "DATABASE_MIRRORING," and use the corresponding port number.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="8cd90-144">예제</span><span class="sxs-lookup"><span data-stu-id="8cd90-144">Examples</span></span>  
  
#### <a name="a-using-a-system-name"></a><span data-ttu-id="8cd90-145">A.</span><span class="sxs-lookup"><span data-stu-id="8cd90-145">A.</span></span> <span data-ttu-id="8cd90-146">시스템 이름 사용</span><span class="sxs-lookup"><span data-stu-id="8cd90-146">Using a system name</span></span>  
 <span data-ttu-id="8cd90-147">다음 엔드포인트 URL은 시스템 이름 `SYSTEM46` 및 포트 `7022`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-147">The following endpoint URL specifies a system name, `SYSTEM46`, and port `7022`.</span></span>  
  
 `TCP://SYSTEM46:7022`  
  
#### <a name="b-using-a-fully-qualified-domain-name"></a><span data-ttu-id="8cd90-148">B.</span><span class="sxs-lookup"><span data-stu-id="8cd90-148">B.</span></span> <span data-ttu-id="8cd90-149">정규화된 도메인 이름 사용</span><span class="sxs-lookup"><span data-stu-id="8cd90-149">Using a fully qualified domain name</span></span>  
 <span data-ttu-id="8cd90-150">다음 엔드포인트 URL은 정규화된 도메인 이름 `DBSERVER8.manufacturing.Adventure-Works.com` 및 포트 `7024`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-150">The following endpoint URL specifies a fully qualified domain name, `DBSERVER8.manufacturing.Adventure-Works.com`, and port `7024`.</span></span>  
  
 `TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024`  
  
#### <a name="c-using-ipv4"></a><span data-ttu-id="8cd90-151">C.</span><span class="sxs-lookup"><span data-stu-id="8cd90-151">C.</span></span> <span data-ttu-id="8cd90-152">IPv4 사용</span><span class="sxs-lookup"><span data-stu-id="8cd90-152">Using IPv4</span></span>  
 <span data-ttu-id="8cd90-153">다음 엔드포인트 URL은 IPv4 주소 `10.193.9.134` 및 포트 `7023`을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-153">The following endpoint URL specifies an IPv4 address, `10.193.9.134`, and port `7023`.</span></span>  
  
 `TCP://10.193.9.134:7023`  
  
#### <a name="d-using-ipv6"></a><span data-ttu-id="8cd90-154">D.</span><span class="sxs-lookup"><span data-stu-id="8cd90-154">D.</span></span> <span data-ttu-id="8cd90-155">IPv6 사용</span><span class="sxs-lookup"><span data-stu-id="8cd90-155">Using IPv6</span></span>  
 <span data-ttu-id="8cd90-156">다음 엔드포인트 URL에는 IPv6 주소 `2001:4898:23:1002:20f:1fff:feff:b3a3` 및 포트 `7022`가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-156">The following endpoint URL contains an IPv6 address, `2001:4898:23:1002:20f:1fff:feff:b3a3`, and port `7022`.</span></span>  
  
 `TCP://[2001:4898:23:1002:20f:1fff:feff:b3a3]:7022`  
  
##  <a name="finding-the-fully-qualified-domain-name-of-a-system"></a><a name="Finding_FQDN"></a> <span data-ttu-id="8cd90-157">시스템의 정규화된 도메인 이름 찾기</span><span class="sxs-lookup"><span data-stu-id="8cd90-157">Finding the Fully Qualified Domain Name of A System</span></span>  
 <span data-ttu-id="8cd90-158">시스템의 정규화된 도메인 이름을 찾으려면 해당 시스템의 Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-158">To find the fully qualified domain name of a system, at the Windows command prompt on that system, enter:</span></span>  
  
 <span data-ttu-id="8cd90-159">**IPCONFIG /ALL**</span><span class="sxs-lookup"><span data-stu-id="8cd90-159">**IPCONFIG /ALL**</span></span>  
  
 <span data-ttu-id="8cd90-160">정규화된 도메인 이름을 구성하려면 *<host_name>* 및 *<Primary_Dns_Suffix>* 의 값을 다음과 같이 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-160">To form the fully qualified domain name, concatenate the values of *<host_name>* and *<Primary_Dns_Suffix>* as follows:</span></span>  
  
 <span data-ttu-id="8cd90-161">_<host_name>_ **.**</span><span class="sxs-lookup"><span data-stu-id="8cd90-161">_<host_name>_ **.**</span></span> <span data-ttu-id="8cd90-162">_<Primary_Dns_Suffix>_</span><span class="sxs-lookup"><span data-stu-id="8cd90-162">_<Primary_Dns_Suffix>_</span></span>  
  
 <span data-ttu-id="8cd90-163">예를 들어 다음 IP 구성은</span><span class="sxs-lookup"><span data-stu-id="8cd90-163">For example, the IP configuration</span></span>  
  
 `Host Name  .  .  .  .  .  .  : MYSERVER`  
  
 `Primary Dns Suffix  .  .  .  : mydomain.Adventure-Works.com`  
  
 <span data-ttu-id="8cd90-164">다음 정규화된 도메인 이름과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd90-164">equates to the following fully qualified domain name:</span></span>  
  
 `MYSERVER.mydomain.Adventure-Works.com`  
  
> [!NOTE]  
>  <span data-ttu-id="8cd90-165">정규화된 도메인 이름에 대한 자세한 내용은 시스템 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="8cd90-165">If you need more information about a fully qualified domain name, see your system administrator.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="8cd90-166">관련 작업</span><span class="sxs-lookup"><span data-stu-id="8cd90-166">Related Tasks</span></span>  
 <span data-ttu-id="8cd90-167">**데이터베이스 미러링 엔드포인트를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="8cd90-167">**To Configure a Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="8cd90-168">AlwaysOn 가용성 그룹 &#40;SQL Server PowerShell에 대 한 데이터베이스 미러링 끝점을 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd90-168">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="8cd90-169">Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd90-169">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="8cd90-170">데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd90-170">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="8cd90-171">데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd90-171">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="8cd90-172">데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd90-172">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="8cd90-173">서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd90-173">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="8cd90-174">삭제&#41;SQL Server AlwaysOn 가용성 그룹 구성 &#40;문제 해결</span><span class="sxs-lookup"><span data-stu-id="8cd90-174">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
 <span data-ttu-id="8cd90-175">**데이터베이스 미러링 엔드포인트에 대한 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="8cd90-175">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="8cd90-176">sys.database_mirroring_endpoints&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd90-176">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 <span data-ttu-id="8cd90-177">**가용성 복제본을 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="8cd90-177">**To add an availability replica**</span></span>  
  
-   [<span data-ttu-id="8cd90-178">가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd90-178">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="8cd90-179">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd90-179">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="8cd90-180">관련 내용</span><span class="sxs-lookup"><span data-stu-id="8cd90-180">Related Content</span></span>  
  
-   [<span data-ttu-id="8cd90-181">고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="8cd90-181">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a><span data-ttu-id="8cd90-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8cd90-182">See Also</span></span>  
 <span data-ttu-id="8cd90-183">[가용성 그룹의 생성 및 구성&#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8cd90-183">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="8cd90-184">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8cd90-184">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="8cd90-185">CREATE ENDPOINT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8cd90-185">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
