---
title: Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], database mirroring
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: baf1a4b1-6790-4275-b261-490bca33bdb9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5558bc5684f2eb9053c935543db0c05d6225daf7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648571"
---
# <a name="create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql"></a><span data-ttu-id="f49ce-102">Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f49ce-102">Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="f49ce-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 Windows 인증을 사용하는 데이터베이스 미러링 엔드포인트를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-103">This topic describes how to create a database mirroring endpoint that uses Windows Authentication in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f49ce-104">데이터베이스 미러링 또는 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]을 지원하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 각 인스턴스에 데이터베이스 미러링 엔드포인트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-104">To support database mirroring or [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires a database mirroring endpoint.</span></span> <span data-ttu-id="f49ce-105">서버 인스턴스는 하나의 포트가 있는 데이터베이스 미러링 엔드포인트를 하나만 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-105">A server instance can have only one database mirroring endpoint, which has a single port.</span></span> <span data-ttu-id="f49ce-106">데이터베이스 미러링 엔드포인트는 엔드포인트가 생성될 때 로컬 시스템에서 사용 가능한 모든 포트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-106">A database mirroring endpoint can use any port that is available on the local system when the endpoint is created.</span></span> <span data-ttu-id="f49ce-107">서버 인스턴스의 모든 데이터베이스 미러링 세션이 이 포트에서 수신하고 데이터베이스 미러링에 대해 들어오는 모든 연결에 이 포트가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-107">All database mirroring sessions on a server instance listen on that port, and all incoming connections for database mirroring use that port.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f49ce-108">데이터베이스 미러링 엔드포인트가 있고 이미 사용 중인 경우 해당 엔드포인트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-108">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint.</span></span> <span data-ttu-id="f49ce-109">사용 중인 엔드포인트를 삭제하면 기존 세션이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-109">Dropping an in-use endpoint disrupts existing sessions.</span></span>  
  
 <span data-ttu-id="f49ce-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f49ce-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f49ce-111">**시작하기 전 주의 사항:**  [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="f49ce-111">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="f49ce-112">**데이터베이스 미러링 엔드포인트를 만들려면 다음을 사용합니다.**  [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="f49ce-112">**To create a database mirroring endpoint, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f49ce-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f49ce-113">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f49ce-114">보안</span><span class="sxs-lookup"><span data-stu-id="f49ce-114">Security</span></span>  
 <span data-ttu-id="f49ce-115">서버 인스턴스의 인증 및 암호화 방법은 시스템 관리자가 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-115">The authentication and encryption methods of the server instance are established by the system administrator.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f49ce-116">RC4 알고리즘은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-116">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="f49ce-117">AES를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-117">We recommend that you use AES.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f49ce-118">권한</span><span class="sxs-lookup"><span data-stu-id="f49ce-118">Permissions</span></span>  
 <span data-ttu-id="f49ce-119">CREATE ENDPOINT 권한 또는 sysadmin 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-119">Requires CREATE ENDPOINT permission, or membership in the sysadmin fixed server role.</span></span> <span data-ttu-id="f49ce-120">자세한 내용은 [GRANT 엔드포인트 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f49ce-120">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f49ce-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f49ce-121">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database-mirroring-endpoint-that-uses-windows-authentication"></a><span data-ttu-id="f49ce-122">Windows 인증을 사용하는 데이터베이스 미러링 엔드포인트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f49ce-122">To Create a Database Mirroring Endpoint That Uses Windows Authentication</span></span>  
  
1.  <span data-ttu-id="f49ce-123">데이터베이스 미러링 엔드포인트를 만들 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-123">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you want to create a database mirroring endpoint.</span></span>  
  
2.  <span data-ttu-id="f49ce-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f49ce-125">다음 문을 사용하여 데이터베이스 미러링 엔드포인트가 이미 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-125">Determine if a database mirroring endpoint already exists by using the following statement:</span></span>  
  
    ```sql
    SELECT name, role_desc, state_desc FROM sys.database_mirroring_endpoints;
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f49ce-126">서버 인스턴스에 대한 데이터베이스 미러링 엔드포인트가 이미 존재하는 경우 서버 인스턴스에서 설정한 다른 세션에 대한 엔드포인트를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="f49ce-126">If a database mirroring endpoint already exists for the server instance, use that endpoint for any other sessions you establish on the server instance.</span></span>  
  
4.  <span data-ttu-id="f49ce-127">Transact-SQL로 Windows 인증을 사용하는 엔드포인트를 만들려면 CREATE ENDPOINT 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-127">To use Transact-SQL to create an endpoint to use with Windows Authentication, use a CREATE ENDPOINT statement.</span></span> <span data-ttu-id="f49ce-128">이 문은 일반적으로 다음과 같은 형식으로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-128">The statement takes the following general form:</span></span>  
  
     <span data-ttu-id="f49ce-129">CREATE ENDPOINT *\<endpointName>*</span><span class="sxs-lookup"><span data-stu-id="f49ce-129">CREATE ENDPOINT *\<endpointName>*</span></span>  
  
     <span data-ttu-id="f49ce-130">STATE=STARTED</span><span class="sxs-lookup"><span data-stu-id="f49ce-130">STATE=STARTED</span></span>  
  
     <span data-ttu-id="f49ce-131">AS TCP ( LISTENER_PORT = *\<listenerPortList>* )</span><span class="sxs-lookup"><span data-stu-id="f49ce-131">AS TCP ( LISTENER_PORT = *\<listenerPortList>* )</span></span>  
  
     <span data-ttu-id="f49ce-132">FOR DATABASE_MIRRORING</span><span class="sxs-lookup"><span data-stu-id="f49ce-132">FOR DATABASE_MIRRORING</span></span>  
  
     <span data-ttu-id="f49ce-133">(</span><span class="sxs-lookup"><span data-stu-id="f49ce-133">(</span></span>  
  
     <span data-ttu-id="f49ce-134">[ AUTHENTICATION = **WINDOWS** [ *\<authorizationMethod>* ]</span><span class="sxs-lookup"><span data-stu-id="f49ce-134">[ AUTHENTICATION = **WINDOWS** [ *\<authorizationMethod>* ]</span></span>  
  
     <span data-ttu-id="f49ce-135">]</span><span class="sxs-lookup"><span data-stu-id="f49ce-135">]</span></span>  
  
     <span data-ttu-id="f49ce-136">[ [ **,** ] ENCRYPTION = **REQUIRED**</span><span class="sxs-lookup"><span data-stu-id="f49ce-136">[ [**,**] ENCRYPTION = **REQUIRED**</span></span>  
  
     <span data-ttu-id="f49ce-137">[ ALGORITHM { *\<algorithm>* } ]</span><span class="sxs-lookup"><span data-stu-id="f49ce-137">[ ALGORITHM { *\<algorithm>* } ]</span></span>  
  
     <span data-ttu-id="f49ce-138">]</span><span class="sxs-lookup"><span data-stu-id="f49ce-138">]</span></span>  
  
     <span data-ttu-id="f49ce-139">[ **,** ] ROLE = *\<role>*</span><span class="sxs-lookup"><span data-stu-id="f49ce-139">[**,**] ROLE = *\<role>*</span></span>  
  
     <span data-ttu-id="f49ce-140">)</span><span class="sxs-lookup"><span data-stu-id="f49ce-140">)</span></span>  
  
     <span data-ttu-id="f49ce-141">라는 설치 관리자 실행 파일에 포함됩니다. 여기서</span><span class="sxs-lookup"><span data-stu-id="f49ce-141">where</span></span>  
  
    -   <span data-ttu-id="f49ce-142">*\<endpointName>* 은 서버 인스턴스의 데이터베이스 미러링 엔드포인트에 대한 고유 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-142">*\<endpointName>* is a unique name for the database mirroring endpoint of the server instance.</span></span>  
  
    -   <span data-ttu-id="f49ce-143">STARTED는 엔드포인트가 시작되어 연결에 대한 수신을 시작하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-143">STARTED specifies that the endpoint is to be started and to begin listening for connections.</span></span> <span data-ttu-id="f49ce-144">데이터베이스 미러링 엔드포인트는 일반적으로 STARTED 상태로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-144">A database mirroring endpoint typically is created in the STARTED state.</span></span> <span data-ttu-id="f49ce-145">STOPPED 상태(기본값)나 DISABLED 상태로 세션을 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-145">Alternatively, you can start a session in a STOPPED state (the default) or DISABLED state.</span></span>  
  
    -   <span data-ttu-id="f49ce-146">*\<listenerPortList>* 는 서버에서 데이터베이스 미러링 메시지를 수신할 하나의 포트 번호(*nnnn*)입니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-146">*\<listenerPortList>* is a single port number (*nnnn*) on which you want the server to listen for database mirroring messages.</span></span> <span data-ttu-id="f49ce-147">TCP만 허용되기 때문에 다른 프로토콜을 지정하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-147">Only TCP is allowed; specifying any other protocol causes an error.</span></span>  
  
         <span data-ttu-id="f49ce-148">하나의 포트 번호는 컴퓨터 시스템당 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-148">A port number can be used only once per computer system.</span></span> <span data-ttu-id="f49ce-149">데이터베이스 미러링 엔드포인트는 엔드포인트가 생성될 때 로컬 시스템에서 사용 가능한 모든 포트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-149">A database mirroring endpoint can use any port that is available on the local system when the endpoint is created.</span></span> <span data-ttu-id="f49ce-150">시스템의 TCP 엔드포인트에서 현재 사용 중인 포트를 식별하려면 다음 Transact-SQL 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-150">To identify the ports currently being used by TCP endpoints on the system, use the following Transact-SQL statement:</span></span>  
  
        ```  
        SELECT name, port FROM sys.tcp_endpoints;  
        ```  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="f49ce-151">각 서버 인스턴스에는 하나의 고유 수신기 포트만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-151">Each server instance requires one and only one unique listener port.</span></span>  
  
    -   <span data-ttu-id="f49ce-152">엔드포인트에서 연결을 인증하는 데 NTLM이나 Kerberos만을 사용하려는 경우가 아니라면 Windows 인증에서 AUTHENTICATION 옵션은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-152">For Windows Authentication, the AUTHENTICATION option is optional, unless you want the endpoint to use only NTLM or Kerberos to authenticate connections.</span></span> <span data-ttu-id="f49ce-153">*\<authorizationMethod>* 는 연결 인증 방법을 NTLM, KERBEROS 또는 NEGOTIATE 중 하나로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-153">*\<authorizationMethod>* specifies the method used to authenticate connections as one of the following: NTLM, KERBEROS, or NEGOTIATE.</span></span> <span data-ttu-id="f49ce-154">기본값인 NEGOTIATE를 적용하면 엔드포인트가 Windows 협상 프로토콜을 사용하여 NTLM이나 Kerberos를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-154">The default, NEGOTIATE, causes the endpoint to use the Windows negotiation protocol to choose either NTLM or Kerberos.</span></span> <span data-ttu-id="f49ce-155">협상을 사용하면 반대쪽 엔드포인트의 인증 수준에 따라 인증을 사용하여 연결을 설정하거나 인증을 사용하지 않고 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-155">Negotiation enables connections with or without authentication, depending on the authentication level of the opposite endpoint.</span></span>  
  
    -   <span data-ttu-id="f49ce-156">ENCRYPTION은 기본적으로 REQUIRED로 설정되어 있으며</span><span class="sxs-lookup"><span data-stu-id="f49ce-156">ENCRYPTION is set to REQUIRED by default.</span></span> <span data-ttu-id="f49ce-157">이는 엔드포인트에 대한 모든 연결에 암호화를 사용해야 함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-157">This means that all connections to this endpoint must use encryption.</span></span> <span data-ttu-id="f49ce-158">그러나 다음과 같이 엔드포인트에 대해 암호화를 해제하거나 선택적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-158">However, you can disable encryption or make it optional on an endpoint.</span></span> <span data-ttu-id="f49ce-159">대체 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-159">The alternatives are as follows:</span></span>  
  
        |<span data-ttu-id="f49ce-160">값</span><span class="sxs-lookup"><span data-stu-id="f49ce-160">Value</span></span>|<span data-ttu-id="f49ce-161">정의</span><span class="sxs-lookup"><span data-stu-id="f49ce-161">Definition</span></span>|  
        |-----------|----------------|  
        |<span data-ttu-id="f49ce-162">DISABLED</span><span class="sxs-lookup"><span data-stu-id="f49ce-162">DISABLED</span></span>|<span data-ttu-id="f49ce-163">연결을 통해 전송되는 데이터를 암호화하지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-163">Specifies that data sent over a connection is not encrypted.</span></span>|  
        |<span data-ttu-id="f49ce-164">SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="f49ce-164">SUPPORTED</span></span>|<span data-ttu-id="f49ce-165">반대쪽 엔드포인트가 SUPPORTED나 REQUIRED로 지정된 경우에만 데이터를 암호화하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-165">Specifies that the data is encrypted only if the opposite endpoint specifies either SUPPORTED or REQUIRED.</span></span>|  
        |<span data-ttu-id="f49ce-166">REQUIRED</span><span class="sxs-lookup"><span data-stu-id="f49ce-166">REQUIRED</span></span>|<span data-ttu-id="f49ce-167">연결을 통해 전송되는 데이터를 반드시 암호화하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-167">Specifies that data sent over a connection must be encrypted.</span></span>|  
  
         <span data-ttu-id="f49ce-168">한 엔드포인트에 암호화가 필요한 경우 다른 엔드포인트의 ENCRYPTION은 SUPPORTED나 REQUIRED로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-168">If an endpoint requires encryption, the other endpoint must have ENCRYPTION set to either SUPPORTED or REQUIRED.</span></span>  
  
    -   <span data-ttu-id="f49ce-169">*\<algorithm>* 은 엔드포인트의 암호화 표준을 지정하는 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-169">*\<algorithm>* provides the option of specifying the encryption standards for the endpoint.</span></span> <span data-ttu-id="f49ce-170">*\<algorithm>* 값은 RC4, AES, AES RC4 또는 RC4 AES 중 하나이거나 이들 알고리즘의 조합일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-170">The value of *\<algorithm>* can be one following algorithms or combinations of algorithms: RC4, AES, AES RC4, or RC4 AES.</span></span>  
  
         <span data-ttu-id="f49ce-171">AES RC4는 엔드포인트가 AES 알고리즘에 우선 순위를 두어 암호화 알고리즘을 협상하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-171">AES RC4 specifies that this endpoint will negotiate for the encryption algorithm, giving preference to the AES algorithm.</span></span> <span data-ttu-id="f49ce-172">RC4 AES는 엔드포인트가 RC4 알고리즘에 우선 순위를 두어 암호화 알고리즘을 협상하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-172">RC4 AES specifies that this endpoint will negotiate for the encryption algorithm, giving preference to the RC4 algorithm.</span></span> <span data-ttu-id="f49ce-173">양쪽 엔드포인트가 두 알고리즘을 모두 지정하지만 순서가 다른 경우 연결을 수락하는 엔드포인트의 알고리즘이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-173">If both endpoints specify both algorithms but in different orders, the endpoint accepting the connection wins.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f49ce-174">RC4 알고리즘은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-174">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="f49ce-175">AES를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-175">We recommend that you use AES.</span></span>  
  
    -   <span data-ttu-id="f49ce-176">*\<role>* 은 서버가 수행할 수 있는 역할을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-176">*\<role>* defines the role or roles that the server can perform.</span></span> <span data-ttu-id="f49ce-177">ROLE은 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-177">Specifying ROLE is required.</span></span> <span data-ttu-id="f49ce-178">그러나 엔드포인트의 역할은 데이터베이스 미러링과만 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-178">However, the role of the endpoint is relevant only for database mirroring.</span></span> <span data-ttu-id="f49ce-179">[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]에 대해서는 엔드포인트의 역할이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-179">For [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], the role of the endpoint is ignored.</span></span>  
  
         <span data-ttu-id="f49ce-180">서버 인스턴스가 데이터베이스 미러링 세션에 따라 각기 다른 역할을 하도록 하려면 ROLE=ALL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-180">To allow a server instance to serve as one role for one database mirroring session and different role for another session, specify ROLE=ALL.</span></span> <span data-ttu-id="f49ce-181">서버 인스턴스가 파트너 또는 미러링 모니터 서버가 되도록 제한하려면 ROLE=PARTNER와 ROLE=WITNESS를 각각 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-181">To restrict a server instance to being either a partner or a witness, specify ROLE=PARTNER or ROLE=WITNESS, respectively.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="f49ce-182">다양 한 버전의에 대 한 데이터베이스 미러링 옵션에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f49ce-182">For more information about Database Mirroring options for different editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
     <span data-ttu-id="f49ce-183">CREATE ENDPOINT 구문에 대한 자세한 내용은 [CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)에서 Windows 인증을 사용하는 데이터베이스 미러링 엔드포인트를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-183">For a complete description of the CREATE ENDPOINT syntax, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f49ce-184">기존 엔드포인트를 변경하려면 [ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-184">To change an existing endpoint, use [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
###  <a name="example-creating-endpoints-to-support-for-database-mirroring-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f49ce-185">예제: 데이터베이스 미러링 지원을 위한 엔드포인트 만들기(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f49ce-185">Example: Creating Endpoints to Support for Database Mirroring (Transact-SQL)</span></span>  
 <span data-ttu-id="f49ce-186">다음 예에서는 세 대의 다른 컴퓨터 시스템에 있는 기본 서버 인스턴스에 대한 데이터베이스 미러링 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-186">The following example creates database mirroring endpoints for the default server instances on three separate computer systems:</span></span>  
  
|<span data-ttu-id="f49ce-187">서버 인스턴스의 역할</span><span class="sxs-lookup"><span data-stu-id="f49ce-187">Role of server instance</span></span>|<span data-ttu-id="f49ce-188">호스트 컴퓨터 이름</span><span class="sxs-lookup"><span data-stu-id="f49ce-188">Name of host computer</span></span>|  
|-----------------------------|---------------------------|  
|<span data-ttu-id="f49ce-189">파트너(처음에는 주 역할임)</span><span class="sxs-lookup"><span data-stu-id="f49ce-189">Partner (initially in the principal role)</span></span>|`SQLHOST01\.`|  
|<span data-ttu-id="f49ce-190">파트너(처음에는 미러 역할임)</span><span class="sxs-lookup"><span data-stu-id="f49ce-190">Partner (initially in the mirror role)</span></span>|`SQLHOST02\.`|  
|<span data-ttu-id="f49ce-191">미러링 모니터</span><span class="sxs-lookup"><span data-stu-id="f49ce-191">Witness</span></span>|`SQLHOST03\.`|  
  
 <span data-ttu-id="f49ce-192">이 예에서 세 엔드포인트는 모든 사용 가능한 포트 번호를 사용할 수 있지만 모두 포트 번호 7022를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-192">In this example, all three endpoints use port number 7022, though any available port number would work.</span></span> <span data-ttu-id="f49ce-193">세 엔드포인트에서 기본 유형인 Windows 인증을 사용하므로 AUTHENTICATION 옵션이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-193">The AUTHENTICATION option is unnecessary, because the endpoints use the default type, Windows Authentication.</span></span> <span data-ttu-id="f49ce-194">세 엔드포인트는 모두 Windows 인증의 기본 동작에 따라 연결 인증 방법을 협상하도록 되어 있으므로 ENCRYPTION 옵션도 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-194">The ENCRYPTION option is also unnecessary, because the endpoints are all intended to negotiate the authentication method for a connection, which is the default behavior for Windows Authentication.</span></span> <span data-ttu-id="f49ce-195">또한 세 엔드포인트에는 모두 기본 동작에 따라 암호화가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-195">Also, all of the endpoints require the encryption, which is the default behavior.</span></span>  
  
 <span data-ttu-id="f49ce-196">각 서버 인스턴스는 파트너나 미러링 모니터 서버로 역할이 제한되며 각 서버의 엔드포인트는 ROLE=PARTNER 또는 ROLE=WITNESS와 같이 해당 역할을 명시적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-196">Each server instance is limited to serving as either a partner or a witness, and the endpoint of each server expressly specifies which role (ROLE=PARTNER or ROLE=WITNESS).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f49ce-197">각 서버 인스턴스는 엔드포인트를 하나만 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f49ce-197">Each server instance can have only one endpoint.</span></span> <span data-ttu-id="f49ce-198">따라서 서버 인스턴스가 세션에 따라 파트너 역할을 하거나 미러링 모니터 서버 역할을 하도록 하려면 ROLE=ALL을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="f49ce-198">Therefore, if you want a server instance to be a partner in some sessions and the witness in others, specify ROLE=ALL.</span></span>  
  
```sql
--Endpoint for initial principal server instance, which  
--is the only server instance running on SQLHOST01.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for initial mirror server instance, which  
--is the only server instance running on SQLHOST02.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=PARTNER);  
GO  
--Endpoint for witness server instance, which  
--is the only server instance running on SQLHOST03.  
CREATE ENDPOINT endpoint_mirroring  
    STATE = STARTED  
    AS TCP ( LISTENER_PORT = 7022 )  
    FOR DATABASE_MIRRORING (ROLE=WITNESS);  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f49ce-199">관련 작업</span><span class="sxs-lookup"><span data-stu-id="f49ce-199">Related Tasks</span></span>  

### <a name="to-configure-a-database-mirroring-endpoint"></a><span data-ttu-id="f49ce-200">데이터베이스 미러링 엔드포인트를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f49ce-200">To Configure a Database Mirroring Endpoint</span></span>
  
-   [<span data-ttu-id="f49ce-201">AlwaysOn 가용성 그룹 &#40;SQL Server PowerShell에 대 한 데이터베이스 미러링 끝점을 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="f49ce-201">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](../availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="f49ce-202">데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f49ce-202">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="f49ce-203">데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f49ce-203">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="f49ce-204">데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f49ce-204">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="f49ce-205">서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;</span><span class="sxs-lookup"><span data-stu-id="f49ce-205">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="f49ce-206">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f49ce-206">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](../availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="f49ce-207">**데이터베이스 미러링 엔드포인트에 대한 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="f49ce-207">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="f49ce-208">sys.database_mirroring_endpoints&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f49ce-208">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="f49ce-209">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f49ce-209">See Also</span></span>  
 <span data-ttu-id="f49ce-210">[ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f49ce-210">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="f49ce-211">[암호화 알고리즘 선택](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="f49ce-211">[Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span></span>  
 <span data-ttu-id="f49ce-212">[CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f49ce-212">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="f49ce-213">[서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="f49ce-213">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="f49ce-214">[예: Windows 인증을 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="f49ce-214">[Example: Setting Up Database Mirroring Using Windows Authentication &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-windows-authentication-transact-sql.md) </span></span>  
 [<span data-ttu-id="f49ce-215">데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f49ce-215">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](the-database-mirroring-endpoint-sql-server.md)  
