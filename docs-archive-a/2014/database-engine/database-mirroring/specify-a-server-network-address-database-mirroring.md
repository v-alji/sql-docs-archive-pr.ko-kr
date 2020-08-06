---
title: 서버 네트워크 주소 지정(데이터베이스 미러링) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], database mirroring
- server network addresses [SQL Server]
ms.assetid: a64d4b6b-9016-4f1e-a310-b1df181dd0c6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5c7db7ee6d321229205248059ce09a86f1da101f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651877"
---
# <a name="specify-a-server-network-address-database-mirroring"></a><span data-ttu-id="68462-102">서버 네트워크 주소 지정(데이터베이스 미러링)</span><span class="sxs-lookup"><span data-stu-id="68462-102">Specify a Server Network Address (Database Mirroring)</span></span>
  <span data-ttu-id="68462-103">데이터베이스 미러링 세션을 설정하려면 각 서버 인스턴스에 대한 서버 네트워크 주소가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-103">Setting up a database mirroring session requires a server network address for each of the server instances.</span></span> <span data-ttu-id="68462-104">서버 인스턴스의 서버 네트워크 주소는 시스템 주소와 인스턴스가 수신하는 포트 번호를 제공하여 인스턴스를 명확하게 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-104">The server network address of a server instance must unambiguously identify the instance by providing a system address and the number of the port on which the instance is listening.</span></span>  
  
 <span data-ttu-id="68462-105">서버 인스턴스에 데이터베이스 미러링 엔드포인트가 있어야만 서버 네트워크 주소에 포트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68462-105">Before you can specify a port in a server network address, the database mirroring endpoint must exist on the server instance.</span></span> <span data-ttu-id="68462-106">자세한 내용은 [Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68462-106">For more information, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
  
  
##  <a name="syntax-for-a-server-network-address"></a><a name="Syntax"></a> <span data-ttu-id="68462-107">서버 네트워크 주소 구문</span><span class="sxs-lookup"><span data-stu-id="68462-107">Syntax for a Server Network Address</span></span>  
 <span data-ttu-id="68462-108">서버 네트워크 주소 구문은 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-108">The syntax for a server network address is of the form:</span></span>  
  
 <span data-ttu-id="68462-109">TCP:<strong>//</strong> *\<system-address>* <strong> :<strong>*\<port>*</span><span class="sxs-lookup"><span data-stu-id="68462-109">TCP<strong>://</strong>*\<system-address>*<strong>:<strong>*\<port>*</span></span> 
  
 <span data-ttu-id="68462-110">라는 설치 관리자 실행 파일에 포함됩니다. 여기서</span><span class="sxs-lookup"><span data-stu-id="68462-110">where</span></span>  
  
-   <span data-ttu-id="68462-111">*\<system-address>* 는 대상 컴퓨터 시스템을 명확하게 식별하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="68462-111">*\<system-address>* is a string that unambiguously identifies the destination computer system.</span></span> <span data-ttu-id="68462-112">일반적으로 서버 주소는 시스템 이름(시스템이 같은 도메인에 있는 경우), 정규화된 도메인 이름 또는 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="68462-112">Typically, the server address is a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address:</span></span>  
  
    -   <span data-ttu-id="68462-113">시스템이 같은 도메인에 있는 경우 `SYSTEM46`과 같이 컴퓨터 시스템의 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68462-113">If the systems are the same domain, you can use the name of the computer system; for example, `SYSTEM46`.</span></span>  
  
    -   <span data-ttu-id="68462-114">IP 주소를 사용하려면 환경에서 고유한 주소여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-114">To use an IP address, it must be unique in your environment.</span></span> <span data-ttu-id="68462-115">정적인 경우에만 IP 주소를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="68462-115">We recommend that you use an IP address only if it is static.</span></span> <span data-ttu-id="68462-116">IP 주소는 IP 버전 4(IPv4) 또는 IP 버전 6(IPv6)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68462-116">The IP address can be IP Version 4 (IPv4) or IP Version 6 (IPv6).</span></span> <span data-ttu-id="68462-117">IPv6 주소는 대괄호로 묶어야 합니다(예: **[** _<IPv6_address>_ **]** ).</span><span class="sxs-lookup"><span data-stu-id="68462-117">An IPv6 address must be enclosed within square brackets, for example: **[**_<IPv6_address>_**]**.</span></span>  
  
         <span data-ttu-id="68462-118">시스템의 IP 주소를 확인하려면 Windows 명령 프롬프트에서 **ipconfig** 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-118">To learn the IP address of a system, at the Windows command prompt, enter the **ipconfig** command.</span></span>  
  
    -   <span data-ttu-id="68462-119">정규화된 도메인 이름을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="68462-119">The fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="68462-120">이 주소 문자열은 로컬로 정의되므로 위치에 따라 형식이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="68462-120">This is a locally defined address string that different forms in different places.</span></span> <span data-ttu-id="68462-121">항상은 아니지만 정규화된 도메인 이름은 컴퓨터 이름과 마침표로 구분된 일련의 도메인 세그먼트를 다음 형식으로 포함하는 복합 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="68462-121">Often, but not always, a fully qualified domain name is a compound name that includes the computer name and a series of period-separated domain segments of the form:</span></span>  
  
         <span data-ttu-id="68462-122">_computer_name_ **.**</span><span class="sxs-lookup"><span data-stu-id="68462-122">_computer_name_ **.**</span></span> <span data-ttu-id="68462-123">_domain_segment_[... **.** _domain_segment_]</span><span class="sxs-lookup"><span data-stu-id="68462-123">_domain_segment_[...**.**_domain_segment_]</span></span>  
  
         <span data-ttu-id="68462-124">여기에서 *computer_name*은 서버 인스턴스를 실행하는 컴퓨터의 네트워크 이름이고 *domain_segment*[... **.** _domain_segment_]는 서버의 나머지 도메인 정보입니다(예: `localinfo.corp.Adventure-Works.com`).</span><span class="sxs-lookup"><span data-stu-id="68462-124">where *computer_name i*s the network name of the computer running the server instance, and *domain_segment*[...**.**_domain_segment_] is the remaining domain information of the server; for example: `localinfo.corp.Adventure-Works.com`.</span></span>  
  
         <span data-ttu-id="68462-125">도메인 세그먼트의 내용과 개수는 회사 또는 조직 내에서 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="68462-125">The content and number of domain segments are determined within the company or organization.</span></span> <span data-ttu-id="68462-126">서버의 정규화된 도메인 이름을 모르는 경우 시스템 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="68462-126">If you do not know the fully qualified domain name for your server, see your system administrator.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="68462-127">정규화된 도메인 이름을 찾는 방법은 이 항목의 뒷부분에 나오는 "정규화된 도메인 이름 찾기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68462-127">For information about how to find a fully qualified domain name, see "Finding the Fully Qualified Domain Name," later in this topic.</span></span>  
  
-   <span data-ttu-id="68462-128">*\<port>* 는 파트너 서버 인스턴스의 미러링 엔드포인트에 사용되는 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="68462-128">*\<port>* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="68462-129">엔드포인트 지정에 대한 자세한 내용은 [Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="68462-129">For information about specifying an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
     <span data-ttu-id="68462-130">데이터베이스 미러링 엔드포인트는 컴퓨터 시스템에서 사용 가능한 모든 포트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68462-130">A database mirroring endpoint can use any available port on the computer system.</span></span> <span data-ttu-id="68462-131">컴퓨터 시스템의 각 포트 번호는 하나의 엔드포인트에만 연결되어야 하고 각 엔드포인트는 단일 서버 인스턴스와 연결되므로 같은 서버의 서로 다른 서버 인스턴스는 서로 다른 포트의 각 엔드포인트에서 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-131">Each port number on a computer system must be associated with only one endpoint, and each endpoint is associated with a single server instance; thus, different server instances on the same server listen on different endpoints with different ports.</span></span> <span data-ttu-id="68462-132">따라서 데이터베이스 미러링 세션을 설정할 때 서버 네트워크 주소에 지정하는 포트는 항상 엔드포인트가 해당 포트와 연결된 서버 인스턴스로 세션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-132">Therefore, the port you specify in the server network address when you set up a database mirroring session will always direct the session to the server instance whose endpoint is associated with that port.</span></span>  
  
     <span data-ttu-id="68462-133">서버 인스턴스의 서버 네트워크 주소에서 미러링 엔드포인트와 연결된 포트 번호만이 해당 인스턴스를 컴퓨터의 다른 인스턴스와 구분해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="68462-133">In the server network address of a server instance, only the number of the port associated with its mirroring endpoint distinguishes that instance from any other instances on the computer.</span></span> <span data-ttu-id="68462-134">다음 그림에서는 단일 컴퓨터에 있는 두 서버 인스턴스의 서버 네트워크 주소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="68462-134">The following figure illustrates the server network addresses of two server instances on a single computer.</span></span> <span data-ttu-id="68462-135">기본 인스턴스는 포트 `7022` 를 사용하고 명명된 인스턴스는 포트 `7033`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-135">The default instance uses port `7022` and the named instance uses port `7033`.</span></span> <span data-ttu-id="68462-136">이러한 두 서버 인스턴스에 대한 서버 네트워크 주소는 `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` 및 `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`입니다.</span><span class="sxs-lookup"><span data-stu-id="68462-136">The server network address for these two server instances are, respectively: `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7022` and `TCP://MYSYSTEM.Adventure-works.MyDomain.com:7033`.</span></span> <span data-ttu-id="68462-137">주소에는 서버 인스턴스 이름이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68462-137">Note that the address does not contain the name of the server instance.</span></span>  
  
     <span data-ttu-id="68462-138">![기본 인스턴스의 서버 네트워크 주소](../media/dbm-2-instances-ports-1-system.gif "기본 인스턴스의 서버 네트워크 주소")</span><span class="sxs-lookup"><span data-stu-id="68462-138">![Server network addresses of a default instance](../media/dbm-2-instances-ports-1-system.gif "Server network addresses of a default instance")</span></span>  
  
     <span data-ttu-id="68462-139">서버 인스턴스의 데이터베이스 미러링 엔드포인트와 현재 연결된 포트를 식별하려면 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-139">To identify the port currently associated with database mirroring endpoint of a server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT type_desc, port FROM sys.tcp_endpoints  
    ```  
  
     <span data-ttu-id="68462-140">**type_desc** 값이 "DATABASE_MIRRORING"인 행을 찾아 해당 포트 번호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-140">Find the row whose **type_desc** value is "DATABASE_MIRRORING," and use the corresponding port number.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="68462-141">예제</span><span class="sxs-lookup"><span data-stu-id="68462-141">Examples</span></span>  
  
#### <a name="a-using-a-system-name"></a><span data-ttu-id="68462-142">A.</span><span class="sxs-lookup"><span data-stu-id="68462-142">A.</span></span> <span data-ttu-id="68462-143">시스템 이름 사용</span><span class="sxs-lookup"><span data-stu-id="68462-143">Using a system name</span></span>  
 <span data-ttu-id="68462-144">다음 서버 네트워크 주소는 시스템 이름 `SYSTEM46`및 포트 `7022`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-144">The following server network address specifies a system name, `SYSTEM46`, and port `7022`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://SYSTEM46:7022';  
```  
  
#### <a name="b-using-a-fully-qualified-domain-name"></a><span data-ttu-id="68462-145">B.</span><span class="sxs-lookup"><span data-stu-id="68462-145">B.</span></span> <span data-ttu-id="68462-146">정규화된 도메인 이름 사용</span><span class="sxs-lookup"><span data-stu-id="68462-146">Using a fully qualified domain name</span></span>  
 <span data-ttu-id="68462-147">다음 서버 네트워크 주소는 정규화된 도메인 이름 `DBSERVER8.manufacturing.Adventure-Works.com`및 포트 `7024`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-147">The following server network address specifies a fully qualified domain name, `DBSERVER8.manufacturing.Adventure-Works.com`, and port `7024`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://DBSERVER8.manufacturing.Adventure-Works.com:7024';  
```  
  
#### <a name="c-using-ipv4"></a><span data-ttu-id="68462-148">C.</span><span class="sxs-lookup"><span data-stu-id="68462-148">C.</span></span> <span data-ttu-id="68462-149">IPv4 사용</span><span class="sxs-lookup"><span data-stu-id="68462-149">Using IPv4</span></span>  
 <span data-ttu-id="68462-150">다음 서버 네트워크 주소는 IPv4 주소 `10.193.9.134`및 포트 `7023`을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-150">The following server network address specifies an IPv4 address, `10.193.9.134`, and port `7023`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://10.193.9.134:7023';  
```  
  
#### <a name="d-using-ipv6"></a><span data-ttu-id="68462-151">D.</span><span class="sxs-lookup"><span data-stu-id="68462-151">D.</span></span> <span data-ttu-id="68462-152">IPv6 사용</span><span class="sxs-lookup"><span data-stu-id="68462-152">Using IPv6</span></span>  
 <span data-ttu-id="68462-153">다음 서버 네트워크 주소에는 IPv6 주소 `2001:4898:23:1002:20f:1fff:feff:b3a3`및 포트 `7022`가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68462-153">The following server network address contains an IPv6 address, `2001:4898:23:1002:20f:1fff:feff:b3a3`, and port `7022`.</span></span>  
  
```  
ALTER DATABASE AdventureWorks SET PARTNER ='tcp://[2001:4898:23:1002:20f:1fff:feff:b3a3]:7022';  
```  
  
## <a name="finding-the-fully-qualified-domain-name"></a><span data-ttu-id="68462-154">정규화된 도메인 이름 찾기</span><span class="sxs-lookup"><span data-stu-id="68462-154">Finding the Fully Qualified Domain Name</span></span>  
 <span data-ttu-id="68462-155">시스템의 정규화된 도메인 이름을 찾으려면 해당 시스템의 Windows 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-155">To find the fully qualified domain name of a system, at the Windows command prompt on that system, enter:</span></span>  
  
 <span data-ttu-id="68462-156">**IPCONFIG /ALL**</span><span class="sxs-lookup"><span data-stu-id="68462-156">**IPCONFIG /ALL**</span></span>  
  
 <span data-ttu-id="68462-157">정규화된 도메인 이름을 구성하려면 *<host_name>* 및 *<Primary_Dns_Suffix>* 의 값을 다음과 같이 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68462-157">To form the fully qualified domain name, concatenate the values of *<host_name>* and *<Primary_Dns_Suffix>* as follows:</span></span>  
  
 <span data-ttu-id="68462-158">_<host_name>_ **.**</span><span class="sxs-lookup"><span data-stu-id="68462-158">_<host_name>_ **.**</span></span> <span data-ttu-id="68462-159">_<Primary_Dns_Suffix>_</span><span class="sxs-lookup"><span data-stu-id="68462-159">_<Primary_Dns_Suffix>_</span></span>  
  
 <span data-ttu-id="68462-160">예를 들어 다음 IP 구성은</span><span class="sxs-lookup"><span data-stu-id="68462-160">For example, the IP configuration</span></span>  
  
 `Host Name  .  .  .  .  .  .  : MYSERVER`  
  
 `Primary Dns Suffix  .  .  .  : mydomain.Adventure-Works.com`  
  
 <span data-ttu-id="68462-161">다음 정규화된 도메인 이름과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="68462-161">equates to the following fully qualified domain name:</span></span>  
  
 `MYSERVER.mydomain.Adventure-Works.com`  
  
##  <a name="examples"></a><a name="Examples"></a> <span data-ttu-id="68462-162">예</span><span class="sxs-lookup"><span data-stu-id="68462-162">Examples</span></span>  
 <span data-ttu-id="68462-163">다음 예에서는 다른 도메인에 있는 `REMOTESYSTEM3` 이라는 컴퓨터 시스템의 서버 인스턴스에 대한 서버 네트워크 주소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="68462-163">The following example shows the server network address for a server instance on a computer system named `REMOTESYSTEM3` in another domain.</span></span> <span data-ttu-id="68462-164">도메인 정보는 `NORTHWEST.ADVENTURE-WORKS.COM`이고 데이터베이스 미러링 엔드포인트의 포트는 `7025`입니다.</span><span class="sxs-lookup"><span data-stu-id="68462-164">The domain information is `NORTHWEST.ADVENTURE-WORKS.COM`, and the port of the database mirroring endpoint is `7025`.</span></span> <span data-ttu-id="68462-165">이러한 예제 구성 요소가 지정되면 서버 네트워크 주소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="68462-165">Given these example components, the server network address is.</span></span>  
  
 `TCP://REMOTESYSTEM3.NORTHWEST.ADVENTURE-WORKS.COM:7025`  
  
 <span data-ttu-id="68462-166">다음 예에서는 `DBSERVER1`이라는 컴퓨터 시스템의 서버 인스턴스에 대한 서버 네트워크 주소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="68462-166">The following example shows the server network address for a server instance on a computer system named `DBSERVER1`.</span></span> <span data-ttu-id="68462-167">이 시스템은 로컬 도메인에 있으며 해당 시스템 이름으로 명확하게 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="68462-167">This system is in the local domain and is unambiguously identified by its system name.</span></span> <span data-ttu-id="68462-168">데이터베이스 미러링 엔드포인트의 포트는 `7022`입니다.</span><span class="sxs-lookup"><span data-stu-id="68462-168">The port of the database mirroring endpoint is `7022`.</span></span>  
  
 `TCP://DBSERVER1:7022`  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="68462-169">관련 작업</span><span class="sxs-lookup"><span data-stu-id="68462-169">Related Tasks</span></span>  
  
-   [<span data-ttu-id="68462-170">Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="68462-170">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="68462-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68462-171">See Also</span></span>  
 <span data-ttu-id="68462-172">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="68462-172">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="68462-173">데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="68462-173">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
  
  
