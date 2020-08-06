---
title: PowerShell Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/11/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
author: minewiskan
ms.author: owend
ms.openlocfilehash: 56af6f26c29e5c1ddb278b620b6f525c70bd1203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648192"
---
# <a name="analysis-services-powershell"></a><span data-ttu-id="5ffdb-102">Analysis Services PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ffdb-102">Analysis Services PowerShell</span></span>
  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]<span data-ttu-id="5ffdb-103">에는 Windows PowerShell을 사용하여 Analysis Services 개체를 탐색, 관리 및 쿼리할 수 있도록 Analysis Services PowerShell(SQLAS) 공급자 및 cmdlet이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-103">includes an Analysis Services PowerShell (SQLAS) provider and cmdlets so that you can use Windows PowerShell to navigate, administer, and query Analysis Services objects.</span></span>  
  
 <span data-ttu-id="5ffdb-104">Analysis Services PowerShell은 다음으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-104">Analysis Services PowerShell consists of the following:</span></span>  
  
-   <span data-ttu-id="5ffdb-105">AMO(Analysis Management Object) 계층을 탐색하는 데 사용되는 `SQLAS` 공급자</span><span class="sxs-lookup"><span data-stu-id="5ffdb-105">`SQLAS` provider used for navigating the Analysis Management Object (AMO) hierarchy.</span></span>  
  
-   <span data-ttu-id="5ffdb-106">MDX, DMX 또는 XMLA 스크립트를 실행하는 데 사용되는 `Invoke-ASCmd` cmdlet</span><span class="sxs-lookup"><span data-stu-id="5ffdb-106">`Invoke-ASCmd` cmdlet used for executing MDX, DMX, or XMLA script.</span></span>  
  
-   <span data-ttu-id="5ffdb-107">처리, 역할 관리, 파티션 관리, 백업 및 복원과 같은 일상적인 작업을 위한 태스크 관련 cmdlet</span><span class="sxs-lookup"><span data-stu-id="5ffdb-107">Task-specific cmdlets for routine operations, such as processing, role management, partition management, backup and restore.</span></span>  
  
## <a name="in-this-article"></a><span data-ttu-id="5ffdb-108">이 문서의 내용</span><span class="sxs-lookup"><span data-stu-id="5ffdb-108">In this article</span></span>  
 [<span data-ttu-id="5ffdb-109">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="5ffdb-109">Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="5ffdb-110">Analysis Services 지원 되는 버전 및 모드</span><span class="sxs-lookup"><span data-stu-id="5ffdb-110">Supported Versions and Modes of Analysis Services</span></span>](#bkmk_vers)  
  
 [<span data-ttu-id="5ffdb-111">인증 요구 사항 및 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="5ffdb-111">Authentication Requirements and Security Considerations</span></span>](#bkmk_auth)  
  
 [<span data-ttu-id="5ffdb-112">Analysis Services PowerShell 태스크</span><span class="sxs-lookup"><span data-stu-id="5ffdb-112">Analysis Services PowerShell Tasks</span></span>](#bkmk_tasks)  

<span data-ttu-id="5ffdb-113">구문 및 예제에 대 한 자세한 내용은 [Analysis Services PowerShell 참조](/sql/analysis-services/powershell/analysis-services-powershell-reference)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-113">For more information about syntax and examples, see [Analysis Services PowerShell Reference](/sql/analysis-services/powershell/analysis-services-powershell-reference).</span></span>

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="5ffdb-114">필수 조건</span><span class="sxs-lookup"><span data-stu-id="5ffdb-114">Prerequisites</span></span>  
 <span data-ttu-id="5ffdb-115">Windows PowerShell 2.0이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-115">Windows PowerShell 2.0 must be installed.</span></span> <span data-ttu-id="5ffdb-116">새 Windows 운영 체제 버전에서는 Windows PowerShell 2.0이 기본적으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-116">It is installed by default on newer versions of the Windows operating systems.</span></span> <span data-ttu-id="5ffdb-117">자세한 내용은 [Windows PowerShell 2.0 설치](https://msdn.microsoft.com/library/ff637750.aspx) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-117">For more information, see [Install Windows PowerShell 2.0](https://msdn.microsoft.com/library/ff637750.aspx)</span></span>

<!-- ff637750.aspx above is linked to by:  (https://go.microsoft.com/fwlink/?LinkId=227613). -->
  
 <span data-ttu-id="5ffdb-118">SQLPS(SQL Server PowerShell) 모듈 및 클라이언트 라이브러리를 포함하는 SQL Server 기능을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-118">You must install a SQL Server feature that includes the SQL Server PowerShell (SQLPS) module and client libraries.</span></span> <span data-ttu-id="5ffdb-119">PowerShell 기능과 클라이언트 라이브러리가 포함되어 있는 SQL Server Management Studio를 설치하면 이러한 기능이 자동으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-119">The easiest way to do this is by installing SQL Server Management Studio, which includes the PowerShell feature and client libraries automatically.</span></span> <span data-ttu-id="5ffdb-120">SQLPS(SQL Server PowerShell) 모듈에는 모든 SQL Server 기능에 대한 PowerShell 공급자 및 cmdlet이 포함되어 있습니다. 여기에는 Analysis Services 개체 계층 탐색에 사용되는 SQLAS 공급자 및 SQLASCmdlets 모듈도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-120">The SQL Server PowerShell (SQLPS) module contains the PowerShell providers and cmdlets for all SQL Server features, including the SQLASCmdlets module and SQLAS provider used for navigating the Analysis Services object hierarchy.</span></span>  
  
 <span data-ttu-id="5ffdb-121">공급자 및 cmdlet을 사용 하려면 먼저 **SQLPS** 모듈을 가져와야 합니다 `SQLAS` .</span><span class="sxs-lookup"><span data-stu-id="5ffdb-121">You must import the **SQLPS** module before you can use the `SQLAS` provider and cmdlets.</span></span> <span data-ttu-id="5ffdb-122">SQLAS 공급자는 공급자의 확장입니다 `SQLServer` .</span><span class="sxs-lookup"><span data-stu-id="5ffdb-122">The SQLAS provider is an extension of the `SQLServer` provider.</span></span> <span data-ttu-id="5ffdb-123">SQLPS 모듈은 여러 가지 방법으로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-123">There are several ways to import the SQLPS module.</span></span> <span data-ttu-id="5ffdb-124">자세한 내용은 [SQLPS 모듈 가져오기](../../2014/database-engine/import-the-sqlps-module.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-124">For more information, see [Import the SQLPS Module](../../2014/database-engine/import-the-sqlps-module.md).</span></span>  
  
 <span data-ttu-id="5ffdb-125">Analysis Services 인스턴스에 원격으로 액세스하려면 원격 관리 및 파일 공유를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-125">Remote access to an Analysis Services instance requires that you enable remote administration and file sharing.</span></span> <span data-ttu-id="5ffdb-126">자세한 내용은이 항목의 [원격 관리 사용](#bkmk_remote) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-126">For more information, see [Enable Remote Administration](#bkmk_remote) in this topic.</span></span>  
  
##  <a name="supported-versions-and-modes-of-analysis-services"></a><a name="bkmk_vers"></a> <span data-ttu-id="5ffdb-127">지원되는 Analysis Services 버전 및 모드</span><span class="sxs-lookup"><span data-stu-id="5ffdb-127">Supported Versions and Modes of Analysis Services</span></span>  
 <span data-ttu-id="5ffdb-128">현재 Analysis Services PowerShell은 Windows Server 2008 R2, Windows Server 2008 SP1 또는 Windows 7에서 실행되는 모든 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services 버전에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-128">Currently, Analysis Services PowerShell is supported on any edition of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services running on Windows Server 2008 R2, Windows Server 2008 SP1, or Windows 7.</span></span>  
  
 <span data-ttu-id="5ffdb-129">다음 표에서는 컨텍스트별로 Analysis Services PowerShell의 사용 가능 여부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-129">The following table shows the availability of Analysis Services PowerShell in different contexts.</span></span>  
  
|<span data-ttu-id="5ffdb-130">컨텍스트</span><span class="sxs-lookup"><span data-stu-id="5ffdb-130">Context</span></span>|<span data-ttu-id="5ffdb-131">PowerShell 기능 사용 가능 여부</span><span class="sxs-lookup"><span data-stu-id="5ffdb-131">PowerShell Feature Availability</span></span>|  
|-------------|-------------------------------------|  
|<span data-ttu-id="5ffdb-132">다차원 인스턴스 및 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5ffdb-132">Multidimensional instances and databases</span></span>|<span data-ttu-id="5ffdb-133">로컬 및 원격 관리에 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-133">Supported for local and remote administration.</span></span><br /><br /> <span data-ttu-id="5ffdb-134">병합 파티션에는 로컬 연결이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-134">Merge-partition requires a local connection.</span></span>|  
|<span data-ttu-id="5ffdb-135">테이블 형식 인스턴스 및 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5ffdb-135">Tabular instances and databases</span></span>|<span data-ttu-id="5ffdb-136">로컬 및 원격 관리에 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-136">Supported for local and remote administration.</span></span><br /><br /> <span data-ttu-id="5ffdb-137">자세한 내용은 [PowerShell을 사용 하 여 테이블 형식 모델 관리](https://go.microsoft.com/fwlink/?linkID=227685)에 대 한 8 월 2011 블로그를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-137">For more information, see an August 2011 blog about [Manage Tabular Models Using PowerShell](https://go.microsoft.com/fwlink/?linkID=227685).</span></span>|  
|<span data-ttu-id="5ffdb-138">SharePoint용 PowerPivot 인스턴스 및 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="5ffdb-138">PowerPivot for SharePoint instances and databases</span></span>|<span data-ttu-id="5ffdb-139">제한적으로 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-139">Limited support.</span></span> <span data-ttu-id="5ffdb-140">HTTP 연결 및 SQLAS 공급자를 사용하여 인스턴스 및 데이터베이스 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-140">You can use HTTP connections and the SQLAS provider to view instance and database information.</span></span><br /><br /> <span data-ttu-id="5ffdb-141">하지만 cmdlet은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-141">However, using the cmdlets is not supported.</span></span> <span data-ttu-id="5ffdb-142">Analysis Services PowerShell을 사용하여 메모리 내 PowerPivot 데이터베이스를 백업 또는 복원하거나, 역할을 추가 또는 제거하거나, 데이터를 처리하거나, 임의의 XMLA 스크립트를 실행해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-142">You must not use Analysis Services PowerShell to backup and restore in-memory PowerPivot database, nor should you add or remove roles, process data, or run arbitrary XMLA script.</span></span><br /><br /> <span data-ttu-id="5ffdb-143">SharePoint용 PowerPivot에는 구성 작업에 사용할 수 있는 기본 제공 PowerShell 지원 기능이 포함되어 있습니다. 이 기능은 별도로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-143">For configuration purposes, PowerPivot for SharePoint has built-in PowerShell support that is provided separately.</span></span> <span data-ttu-id="5ffdb-144">자세한 내용은 [SharePoint용 PowerPivot에 대 한 PowerShell 참조](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-144">For more information, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>|  
|<span data-ttu-id="5ffdb-145">로컬 큐브에 대한 네이티브 연결</span><span class="sxs-lookup"><span data-stu-id="5ffdb-145">Native connections to local cubes</span></span><br /><br /> <span data-ttu-id="5ffdb-146">"Data Source = c:\backup\test.cub"</span><span class="sxs-lookup"><span data-stu-id="5ffdb-146">"Data Source=c:\backup\test.cub"</span></span>|<span data-ttu-id="5ffdb-147">지원 안 됨</span><span class="sxs-lookup"><span data-stu-id="5ffdb-147">Not supported.</span></span>|  
|<span data-ttu-id="5ffdb-148">SharePoint의 BI 의미 체계 모델 연결 파일(.bism)에 대한 HTTP 연결</span><span class="sxs-lookup"><span data-stu-id="5ffdb-148">HTTP connections to BI semantic model (.bism) connection files in SharePoint</span></span><br /><br /> <span data-ttu-id="5ffdb-149">"Data Source = http://server/shared_docs/name.bism "</span><span class="sxs-lookup"><span data-stu-id="5ffdb-149">"Data Source=http://server/shared_docs/name.bism"</span></span>|<span data-ttu-id="5ffdb-150">지원 안 됨</span><span class="sxs-lookup"><span data-stu-id="5ffdb-150">Not supported.</span></span>|  
|<span data-ttu-id="5ffdb-151">PowerPivot 데이터베이스에 대한 포함된 연결</span><span class="sxs-lookup"><span data-stu-id="5ffdb-151">Embedded connections to PowerPivot databases</span></span><br /><br /> <span data-ttu-id="5ffdb-152">"Data Source = $Embedded $"</span><span class="sxs-lookup"><span data-stu-id="5ffdb-152">"Data Source=$Embedded$"</span></span>|<span data-ttu-id="5ffdb-153">지원 안 됨</span><span class="sxs-lookup"><span data-stu-id="5ffdb-153">Not supported.</span></span>|  
|<span data-ttu-id="5ffdb-154">Analysis Services 저장 프로시저의 로컬 서버 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="5ffdb-154">Local server context in Analysis Services stored procedures</span></span><br /><br /> <span data-ttu-id="5ffdb-155">"Data Source = \*"</span><span class="sxs-lookup"><span data-stu-id="5ffdb-155">"Data Source=\*"</span></span>|<span data-ttu-id="5ffdb-156">지원 안 됨</span><span class="sxs-lookup"><span data-stu-id="5ffdb-156">Not supported.</span></span>|  
  
##  <a name="authentication-requirements-and-security-considerations"></a><a name="bkmk_auth"></a><span data-ttu-id="5ffdb-157">인증 요구 사항 및 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="5ffdb-157">Authentication Requirements and Security Considerations</span></span>  
 <span data-ttu-id="5ffdb-158">Analysis Services에 연결하는 경우 Windows 사용자 ID를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-158">When connecting to Analysis Services, you must make the connection using a Windows user identity.</span></span> <span data-ttu-id="5ffdb-159">대부분 Windows 통합 보안을 사용하여 연결이 이루어지는데 이 경우 현재 사용자의 ID가 서버 작업이 수행되는 보안 컨텍스트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-159">For the most part, a connection is made using Windows integrated security, where the identity of the current user sets the security context under which server operations are performed.</span></span> <span data-ttu-id="5ffdb-160">하지만 Analysis Services에 대한 HTTP 액세스를 구성하면 추가 인증 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-160">However, additional authentication methods become available when you configure HTTP access to Analysis Services.</span></span> <span data-ttu-id="5ffdb-161">이 섹션에서는 연결 유형에 따라 사용할 수 있는 인증 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-161">This section explains how the type of connection determines which authentication options you can use.</span></span>  
  
 <span data-ttu-id="5ffdb-162">Analysis Services에 대한 연결은 네이티브 연결과 HTTP 연결 중 하나로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-162">Connections to Analysis Services are characterized as either native connections or HTTP connections.</span></span> <span data-ttu-id="5ffdb-163">네이티브 연결은 클라이언트 애플리케이션에서 서버로의 직접 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-163">A native connection is a direct connection from a client application to the server.</span></span> <span data-ttu-id="5ffdb-164">PowerShell 세션에서 PowerShell 클라이언트는 Analysis Services용 OLE DB 공급자를 사용하여 직접 Analysis Services 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-164">In a PowerShell session, the PowerShell client uses the OLE DB provider for Analysis Services to connect directly to an Analysis Services instance.</span></span> <span data-ttu-id="5ffdb-165">네이티브 연결은 언제나 Windows 통합 보안을 사용하여 이루어지며 여기서는 Analysis Services PowerShell이 현재 사용자로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-165">A native connection is always made using Windows integrated security, where Analysis Services PowerShell executes as the current user.</span></span> <span data-ttu-id="5ffdb-166">Analysis Services는 가장을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-166">Analysis Services does not support impersonation.</span></span> <span data-ttu-id="5ffdb-167">특정 사용자로 작업을 수행하려는 경우 해당 사용자로 PowerShell 세션을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-167">If you want to perform an operation as a specific user, you must start the PowerShell session as that user.</span></span>  
  
 <span data-ttu-id="5ffdb-168">HTTP 연결은 IIS를 통해 간접적으로 이루어지며 기본 인증 등의 추가 인증 옵션을 사용하여 Analysis Services 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-168">HTTP connections are made indirectly through IIS, allowing for additional authentication options, such as Basic authentication, to connect to an Analysis Services instance.</span></span> <span data-ttu-id="5ffdb-169">IIS는 가장을 지원하므로 IIS가 연결 시 가장에 사용할 자격 증명을 포함하는 연결 문자열을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-169">Because IIS supports impersonation, you can provide a connection string that includes credentials IIS will use to impersonate when making a connection.</span></span> <span data-ttu-id="5ffdb-170">자격 증명을 제공 하기 위해-Credential 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-170">To provide credentials, you can use the -Credential parameter.</span></span>  
  
 <span data-ttu-id="5ffdb-171">**PowerShell에서-Credential 매개 변수 사용**</span><span class="sxs-lookup"><span data-stu-id="5ffdb-171">**Using the -Credential Parameter in PowerShell**</span></span>  
  
 <span data-ttu-id="5ffdb-172">-Credential 매개 변수는 사용자 이름 및 암호를 지정 하는 PSCredential 개체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-172">The -Credential parameter takes a PSCredential object that specifies a user name and password.</span></span> <span data-ttu-id="5ffdb-173">Analysis Services PowerShell에서-Credential 매개 변수는 기존 연결의 컨텍스트 내에서 실행 되는 cmdlet이 아닌 Analysis Services에 대 한 연결 요청을 수행 하는 cmdlet에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-173">In Analysis Services PowerShell, the -Credential parameter is available for cmdlets that make a connection request to Analysis Services, as opposed to cmdlets that run within the context of an existing connection.</span></span> <span data-ttu-id="5ffdb-174">연결 요청을 수행하는 cmdlet에는 Invoke-ASCmd, Backup-ASDatabase, Restore-ASDatabase 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-174">Cmdlets that make a connection request include Invoke-ASCmd, Backup-ASDatabase, and Restore-ASDatabase.</span></span> <span data-ttu-id="5ffdb-175">이러한 cmdlet의 경우 다음 조건을 충족 한다고 가정 하 여-Credential 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-175">For these cmdlets, the -Credential parameter can be used, assuming the following criteria are met:</span></span>  
  
1.  <span data-ttu-id="5ffdb-176">서버가 HTTP 액세스를 사용하도록 구성된 경우, 즉 IIS가 연결을 처리하고, 사용자 이름 및 암호를 읽고, Analysis Services에 연결할 때 해당 사용자 ID를 가장하는 경우.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-176">The server is configured for HTTP access, which means that IIS handles the connection, reads the user name and password, and impersonates that user identity when connecting to Analysis Services.</span></span> <span data-ttu-id="5ffdb-177">자세한 내용은 [IIS&#40;인터넷 정보 서비스&#41; 8.0에서 Analysis Services에 대한 HTTP 액세스 구성](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-177">For more information, see [Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md).</span></span>  
  
2.  <span data-ttu-id="5ffdb-178">Analysis Services HTTP 액세스를 위해 생성된 IIS 가상 디렉터리가 기본 인증을 사용하도록 구성된 경우</span><span class="sxs-lookup"><span data-stu-id="5ffdb-178">The IIS virtual directory that was created for Analysis Services HTTP access is configured for Basic authentication.</span></span>  
  
3.  <span data-ttu-id="5ffdb-179">자격 증명 개체가 제공하는 사용자 이름 및 암호는 Windows 사용자 ID로 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-179">The user name and password provided by the credential object resolves to a Windows user identity.</span></span> <span data-ttu-id="5ffdb-180">Analysis Services는 이 ID를 현재 사용자로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-180">Analysis Services uses this identity as the current user.</span></span> <span data-ttu-id="5ffdb-181">사용자가 Windows 사용자가 아니거나 요청된 작업을 수행할 수 있는 권한이 없는 경우 해당 요청은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-181">If the user is not a Windows user, or lacks sufficient permissions to perform the requested operation, the request will fail.</span></span>  
  
 <span data-ttu-id="5ffdb-182">자격 증명 개체를 만들려면 Get-Credential cmdlet을 사용하여 작업자로부터 자격 증명을 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-182">To create a credential object, you can use the Get-Credential cmdlet to collect the credentials from the operator.</span></span> <span data-ttu-id="5ffdb-183">그런 다음 Analysis Services에 연결하는 명령에 이 자격 증명 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-183">You can then use the credential object on a command that connects to Analysis Services.</span></span> <span data-ttu-id="5ffdb-184">다음 예에서는 이러한 접근 방법 중 하나를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-184">The following example illustrates one approach.</span></span> <span data-ttu-id="5ffdb-185">이 예에서는 `SQLSERVER:\SQLAS\HTTP_DS` HTTP 액세스에 대해 구성 된 로컬 인스턴스 ()에 대 한 연결이 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-185">In this example, the connection is to a local instance (`SQLSERVER:\SQLAS\HTTP_DS`) configured for HTTP access.</span></span>  
  
```powershell
$cred = Get-Credential adventureworks\dbadmin  
Invoke-ASCmd -Inputfile:"c:\discoverconnections.xmla" -Credential:$cred  
```  
  
 <span data-ttu-id="5ffdb-186">기본 인증을 사용하는 경우 사용자 이름과 암호가 암호화된 연결을 통해 전송되도록 언제나 HTTPS와 SSL을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-186">When using Basic authentication, you should always use HTTPS with SSL so that username and passwords are sent over an encrypted connection.</span></span> <span data-ttu-id="5ffdb-187">자세한 내용은 [iis 7.0에서 SSL(Secure Sockets Layer) 구성](https://go.microsoft.com/fwlink/?linkID=184299) 및 [기본 인증 구성 (iis 7)](https://go.microsoft.com/fwlink/?LinkId=230776)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-187">For more information, see [Configure Secure Sockets Layer in IIS 7.0](https://go.microsoft.com/fwlink/?linkID=184299) and [Configure Basic Authentication (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=230776).</span></span>  
  
 <span data-ttu-id="5ffdb-188">PowerShell에서 제공하는 자격 증명, 쿼리 및 명령은 변경되지 않고 전송 계층으로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-188">Remember that credentials, queries, and commands that you provide in PowerShell are passed unchanged to the transport layer.</span></span> <span data-ttu-id="5ffdb-189">스크립트에 중요한 콘텐츠를 포함하면 악의적인 삽입 공격의 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-189">Including sensitive content in your scripts increases the risk of a malicious injection attack.</span></span>  
  
 <span data-ttu-id="5ffdb-190">**Microsoft.Secure.String 개체로 암호 제공**</span><span class="sxs-lookup"><span data-stu-id="5ffdb-190">**Providing a password as a Microsoft.Secure.String object**</span></span>  
  
 <span data-ttu-id="5ffdb-191">백업 및 복원과 같은 일부 작업은 명령에 암호를 제공할 때 활성화되는 암호화 옵션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-191">Some operations, such as backup and restore, support encryption options that are activated when you provide a password in the command.</span></span> <span data-ttu-id="5ffdb-192">암호를 제공하면 Analysis Services가 백업 파일을 암호화하거나 해독합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-192">Providing the password signals Analysis Services to encrypt or decrypt the backup file.</span></span> <span data-ttu-id="5ffdb-193">Analysis Services에서 이 암호는 보안 문자열 개체로 인스턴스화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-193">In Analysis Services, this password is instantiated as a secure string object.</span></span> <span data-ttu-id="5ffdb-194">다음 예에서는 런타임에 작업자로부터 암호를 수집하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-194">The following example provides an illustration of how to collect a password from the operator at run time.</span></span>  
  
```powershell
$pwd = read-host -AsSecureString -Prompt "Password"  
$pwd -is [System.IDisposable]  
```  
  
 <span data-ttu-id="5ffdb-195">이제 $pwd 변수를 암호 매개 변수로 전달하여 암호화된 데이터베이스 파일을 백업하거나 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-195">You can now backup or restore an encrypted database file, passing the $pwd variable to the password parameter.</span></span> <span data-ttu-id="5ffdb-196">이 그림을 다른 cmdlet과 결합 하는 전체 예제를 보려면 [Backup-asdatabase cmdlet](/powershell/module/sqlserver/backup-asdatabase) 및 [Restore-asdatabase cmdlet](/powershell/module/sqlserver/restore-asdatabase)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-196">To view a complete example that combines this illustration with other cmdlets, see [Backup-ASDatabase cmdlet](/powershell/module/sqlserver/backup-asdatabase) and [Restore-ASDatabase cmdlet](/powershell/module/sqlserver/restore-asdatabase).</span></span>
  
 <span data-ttu-id="5ffdb-197">후속 단계로 세션에서 암호 및 변수를 모두 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-197">As a follow up step, remove both the password and variable from the session.</span></span>  
  
```powershell
$pwd.Dispose()  
Remove-Variable -Name pwd  
```  
  
##  <a name="analysis-services-powershell-tasks"></a><a name="bkmk_tasks"></a><span data-ttu-id="5ffdb-198">PowerShell 작업 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="5ffdb-198">Analysis Services PowerShell Tasks</span></span>  
 <span data-ttu-id="5ffdb-199">Windows PowerShell 관리 셸 또는 Windows 명령 프롬프트에서 Analysis Services PowerShell을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-199">You can run Analysis Services PowerShell from the Windows PowerShell management shell or a Windows command prompt.</span></span> <span data-ttu-id="5ffdb-200">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 Analysis Services PowerShell을 실행할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-200">Running Analysis Services PowerShell from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] is not supported.</span></span>  
  
 <span data-ttu-id="5ffdb-201">이 섹션에서는 Analysis Services PowerShell을 사용할 때의 일반적인 태스크에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-201">This section describes common tasks for using Analysis Services PowerShell.</span></span>  
  
-   [<span data-ttu-id="5ffdb-202">Analysis Services 공급자 및 Cmdlet 로드</span><span class="sxs-lookup"><span data-stu-id="5ffdb-202">Load the Analysis Services Provider and Cmdlets</span></span>](#bkmk_load)  
  
-   [<span data-ttu-id="5ffdb-203">원격 관리 설정</span><span class="sxs-lookup"><span data-stu-id="5ffdb-203">Enable Remote Administration</span></span>](#bkmk_remote)  
  
-   [<span data-ttu-id="5ffdb-204">Analysis Services 개체에 연결</span><span class="sxs-lookup"><span data-stu-id="5ffdb-204">Connect to an Analysis Services Object</span></span>](#bkmk_connect)  
  
-   [<span data-ttu-id="5ffdb-205">서비스 관리</span><span class="sxs-lookup"><span data-stu-id="5ffdb-205">Administer the Service</span></span>](#bkmk_admin)  
  
-   [<span data-ttu-id="5ffdb-206">Analysis Services PowerShell에 대한 도움말 가져오기</span><span class="sxs-lookup"><span data-stu-id="5ffdb-206">Get Help for Analysis Services PowerShell</span></span>](#bkmk_help)  
  
###  <a name="load-the-analysis-services-provider-and-cmdlets"></a><a name="bkmk_load"></a><span data-ttu-id="5ffdb-207">Analysis Services 공급자 및 Cmdlet을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-207">Load the Analysis Services Provider and Cmdlets</span></span>  
 <span data-ttu-id="5ffdb-208">Analysis Services 공급자는 SQLPS 모듈을 가져오면 사용할 수 있는 SQL Server 루트 공급자의 확장 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-208">The Analysis Services provider is an extension of the SQL Server root provider that becomes available when you import the SQLPS module.</span></span> <span data-ttu-id="5ffdb-209">Analysis Services cmdlet은 동시에 로드됩니다. 공급자 없이 사용하려는 경우에는 독립적으로 로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-209">Analysis Services cmdlets are loaded simultaneously; you can also load them independently if you want to use them without the provider.</span></span>  
  
-   <span data-ttu-id="5ffdb-210">Import-module cmdlet을 실행하여 모든 Analysis Services PowerShell 기능이 포함된 SQLPS를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-210">Run the Import-module cmdlet to load SQLPS that includes all of the Analysis Services PowerShell functionality.</span></span> <span data-ttu-id="5ffdb-211">모듈을 가져올 수 없으면 모듈을 로드하는 동안에만 임시로 실행 정책을 "제한 없음"으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-211">If you cannot import the module, you can temporarily change the execution policy to unrestricted for the purpose of the loading the module.</span></span> <span data-ttu-id="5ffdb-212">자세한 내용은 [SQLPS 모듈 가져오기](../../2014/database-engine/import-the-sqlps-module.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-212">For more information, see [Import the SQLPS Module](../../2014/database-engine/import-the-sqlps-module.md).</span></span>  
  
    ```powershell
    Import-Module "sqlps"  
    ```  
  
     <span data-ttu-id="5ffdb-213">`import-module "sqlps" -disablenamechecking`을 사용하여 승인되지 않은 동사 이름에 대한 경고를 표시하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-213">Alternatively, use `import-module "sqlps" -disablenamechecking` to suppress the warning about unapproved verb names.</span></span>  
  
-   <span data-ttu-id="5ffdb-214">Analysis Services 공급자 또는 Invoke-ASCmd cmdlet 없이 태스크 관련 Analysis Services cmdlet만 로드하려면 독립적인 작업으로 SQLASCmdlets 모듈을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-214">To load just the task-specific Analysis Services cmdlets, without the Analysis Services provider or the Invoke-ASCmd cmdlet, you can load the SQLASCmdlets module as an independent operation.</span></span>  
  
    ```powershell
    Import-Module "sqlascmdlets"  
    ```  
  
###  <a name="enable-remote-administration"></a><a name="bkmk_remote"></a><span data-ttu-id="5ffdb-215">원격 관리 사용</span><span class="sxs-lookup"><span data-stu-id="5ffdb-215">Enable Remote Administration</span></span>  
 <span data-ttu-id="5ffdb-216">원격 Analysis Services 인스턴스에서 Analysis Services PowerShell을 사용하려면 먼저 원격 관리 및 파일 공유를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-216">Before you can use Analysis Services PowerShell with a remote Analysis Services instance, you must first enable remote administration and file sharing.</span></span> <span data-ttu-id="5ffdb-217">다음 오류는 방화벽 구성 문제를 나타냅니다. "RPC 서버를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-217">The following error indicates a firewall configuration issue: "The RPC server is unavailable.</span></span> <span data-ttu-id="5ffdb-218">(HRESULT: 0x800706BA에서 예외가 발생했습니다.)"</span><span class="sxs-lookup"><span data-stu-id="5ffdb-218">(Exception from HRESULT: 0x800706BA)".</span></span>  
  
1.  <span data-ttu-id="5ffdb-219">로컬 및 원격 컴퓨터 모두에 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] 버전의 클라이언트 및 서버 도구가 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-219">Verify that both local and remote computers have the [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] versions of the client and server tools.</span></span>  
  
2.  <span data-ttu-id="5ffdb-220">Analysis Services 인스턴스를 호스팅하는 원격 서버의 Windows 방화벽에서 TCP 포트 2383을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-220">On the remote server that is hosting an Analysis Services instance, open TCP port 2383 in Windows Firewall.</span></span> <span data-ttu-id="5ffdb-221">Analysis Services를 명명된 인스턴스로 설치했거나 사용자 지정 포트를 사용하는 경우 포트 번호가 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-221">If you installed Analysis Services as a named instance or are using a custom port, the port number will be different.</span></span> <span data-ttu-id="5ffdb-222">자세한 내용은 [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-222">For more information, see [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
3.  <span data-ttu-id="5ffdb-223">원격 서버에서 다음 서비스가 시작 됨: RPC (원격 프로시저 호출) 서비스, TCP/IP NetBIOS 도우미 서비스, WMI(Windows Management Instrumentation) (WMI) 서비스, Windows 원격 관리 (WS-MANAGEMENT) 서비스를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-223">On the remote server, verify that the followings services are started:  Remote Procedure Call (RPC) service, TCP/IP NetBIOS Helper service, Windows Management Instrumentation (WMI) service, Windows Remote Management (WS-Management) service.</span></span>  
  
4.  <span data-ttu-id="5ffdb-224">원격 서버에서 그룹 정책 개체 편집기 스냅인(gpedit.msc)을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-224">On the remote server, start the Group Policy Object Editor snap-in (gpedit.msc).</span></span>  
  
5.  <span data-ttu-id="5ffdb-225">컴퓨터 구성에서 관리 템플릿, 네트워크, 네트워크 구성 요소, Windows 방화벽을 차례로 연 다음 도메인 프로파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-225">Open Computer Configuration, open Administrative Templates, open Network, open Network Connections, open Windows Firewall, and then open Domain Profile.</span></span>  
  
6.  <span data-ttu-id="5ffdb-226">**Windows 방화벽: 인바운드 원격 관리 예외 허용**을 두 번 클릭 하 고 **사용**을 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-226">Double-click **Windows Firewall: Allow inbound remote administration exception**, select **Enabled**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="5ffdb-227">**Windows 방화벽: 인바운드 파일 및 프린터 공유 예외 허용**을 두 번 클릭 하 고 **사용**을 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-227">Double-click **Windows Firewall: Allow inbound file and printer sharing exception**, select **Enabled**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="5ffdb-228">클라이언트 도구가 있는 로컬 컴퓨터에서 다음 cmdlet을 사용 하 여 원격 관리를 확인 하 고 *원격 서버 이름* 자리 표시자에 대 한 실제 서버 이름을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-228">On the local computer that has the client tools, use the following cmdlets to verify remote administration, substituting the actual server name for the *remote-server-name* placeholder.</span></span> <span data-ttu-id="5ffdb-229">Analysis Services가 기본 인스턴스로 설치된 경우 인스턴스 이름은 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-229">Omit the instance name if Analysis Services is installed as the default instance.</span></span> <span data-ttu-id="5ffdb-230">이 명령은 SQLPS 모듈을 이미 가져온 경우에만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-230">You must have previously imported the SQLPS module in order for the command to work.</span></span>  
  
    ```
    PS SQLSERVER:\> cd sqlas
    PS SQLSERVER:\sqlas> cd <remote-server-name\instance-name>  
    PS SQLSERVER:\sqlas\<remote-server-name\instance-name> dir  
    ```  
  
 <span data-ttu-id="5ffdb-231">경우에 따라서는 추가 구성이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-231">In some cases, additional configuration might be necessary.</span></span> <span data-ttu-id="5ffdb-232">다른 컴퓨터에서 원격 서버에 대한 명령을 실행하려면 먼저 해당 원격 서버에 다음을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-232">You might need to type the following on the remote server before you can issue commands to it from another computer:</span></span>  
  
```powershell
Enable-PSRemoting  
```  
  
  
###  <a name="connect-to-an-analysis-services-object"></a><a name="bkmk_connect"></a><span data-ttu-id="5ffdb-233">Analysis Services 개체에 연결</span><span class="sxs-lookup"><span data-stu-id="5ffdb-233">Connect to an Analysis Services Object</span></span>  
 <span data-ttu-id="5ffdb-234">Analysis Services PowerShell 공급자는 Analysis Services 개체 계층 탐색을 지원하고 명령 실행 컨텍스트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-234">The Analysis Services PowerShell provider supports navigation of the Analysis Services object hierarchy and sets the context for running commands.</span></span> <span data-ttu-id="5ffdb-235">이 공급자는 SQLPS 모듈을 통해 사용할 수 있는 SQLSERVER 루트 공급자의 확장 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-235">The provider is an extension of the SQLSERVER root provider available through the SQLPS module.</span></span> <span data-ttu-id="5ffdb-236">SQLPS 모듈을 로드한 후 경로를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-236">After you load the SQLPS module, you can navigate the path.</span></span>  
  
 <span data-ttu-id="5ffdb-237">로컬 또는 원격 인스턴스에 연결할 수 있지만 merge-partition과 같은 일부 cmdlet은 로컬 인스턴스에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-237">You can connect to a local or remote instance, but some cmdlets only run on a local instance (namely, merge-partition).</span></span> <span data-ttu-id="5ffdb-238">네이티브 연결을 사용할 수도 있고, HTTP 액세스를 사용하도록 구성한 Analysis Services 서버에 대해서는 HTTP 연결을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-238">You can use a native connection or an HTTP connection for Analysis Services servers that you configured for HTTP access.</span></span> <span data-ttu-id="5ffdb-239">다음 그림에서는 네이티브 연결과 HTTP 연결의 탐색 경로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-239">The following illustrations show the navigation path for native and HTTP connections.</span></span> <span data-ttu-id="5ffdb-240">다음 그림에서는 네이티브 연결과 HTTP 연결의 탐색 경로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-240">The following illustrations show the navigation path for native and HTTP connections.</span></span>  
  
 <span data-ttu-id="5ffdb-241">**Analysis Services에 대한 네이티브 연결**</span><span class="sxs-lookup"><span data-stu-id="5ffdb-241">**Native Connections to Analysis Services**</span></span>  
  
 <span data-ttu-id="5ffdb-242">![Analysis Services에 대한 네이티브 연결](media/ssas-powershell-nativeconnection.gif "Analysis Services에 대한 네이티브 연결")</span><span class="sxs-lookup"><span data-stu-id="5ffdb-242">![Native connection to Analysis Services](media/ssas-powershell-nativeconnection.gif "Native connection to Analysis Services")</span></span>  
  
 <span data-ttu-id="5ffdb-243">다음 예에서는 네이티브 연결을 사용하여 개체 계층을 탐색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-243">The following example is a demonstration of how to use a native connection to navigate object hierarchy.</span></span> <span data-ttu-id="5ffdb-244">공급자에서 `dir`을 실행하여 인스턴스 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-244">From the provider, you can issue a `dir` to view instance information.</span></span> <span data-ttu-id="5ffdb-245">`cd`를 사용하여 해당 인스턴스의 개체를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-245">You can use `cd` to view objects of that instance.</span></span>  
  
```  
PS SQLSERVER:> cd sqlas  
PS SQLSERVER\sqlas:> dir  
PS SQLSERVER\sqlas:> cd localhost\default  
PS SQLSERVER\sqlas\localhost\default:> dir  
```  
  
 <span data-ttu-id="5ffdb-246">어셈블리, 데이터베이스, 역할 및 추적과 같은 컬렉션이 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-246">You should see the following collections: Assemblies, Databases, Roles, and Traces.</span></span> <span data-ttu-id="5ffdb-247">계속하여 `cd` 및 `dir`을 사용하여 각 컬렉션의 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-247">Continuing to use `cd` and `dir`, you can view the contents of each collection.</span></span>  
  
 <span data-ttu-id="5ffdb-248">**Analysis Services에 대한 HTTP 연결**</span><span class="sxs-lookup"><span data-stu-id="5ffdb-248">**HTTP Connections to Analysis Services**</span></span>  
  
 <span data-ttu-id="5ffdb-249">![Analysis Services에 대한 HTTP 연결](media/ssas-powershell-httpconnection.gif "Analysis Services에 대한 HTTP 연결")</span><span class="sxs-lookup"><span data-stu-id="5ffdb-249">![HTTP Connection to Analysis Services](media/ssas-powershell-httpconnection.gif "HTTP Connection to Analysis Services")</span></span>  
  
 <span data-ttu-id="5ffdb-250">HTTP 연결은이 항목의 지침을 사용 하 여 http 액세스를 사용 하도록 서버를 구성한 경우에 유용 합니다. [인터넷 정보 서비스 &#40;IIS&#41; 8.0에서 Analysis Services에 대 한 Http 액세스 구성](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)</span><span class="sxs-lookup"><span data-stu-id="5ffdb-250">HTTP connections are useful if you configured your server for HTTP access using the instructions in this topic: [Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)</span></span>  
  
 <span data-ttu-id="5ffdb-251">의 서버 URL을 가정 하면 http://localhost/olap/msmdpump.dll 연결이 다음과 같이 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-251">Assuming a server URL of http://localhost/olap/msmdpump.dll, a connection might look like the following:</span></span>  
  
```  
PS SQLSERVER\sqlas:> cd http_ds  
PS SQLSERVER\sqlas\http_ds:> $Url=Encode-SqlName "http://localhost/olap/msmdpump.dll"  
PS SQLSERVER\sqlas\http_ds:> cd $Url  
PS SQLSERVER\sqlas\http_ds\http%3A%2F%2Flocalhost%2olap%2msmdpump%2Edll:> dir  
```  
  
 <span data-ttu-id="5ffdb-252">어셈블리, 데이터베이스, 역할 및 추적과 같은 컬렉션이 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-252">You should see the following collections: Assemblies, Databases, Roles, and Traces.</span></span> <span data-ttu-id="5ffdb-253">이 컬렉션의 내용을 볼 수 없는 경우 OLAP 가상 디렉터리의 인증 설정을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-253">If you cannot view the contents of these collections, check the authentication settings on the OLAP virtual directory.</span></span> <span data-ttu-id="5ffdb-254">익명 액세스가 비활성화되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-254">Make sure that Anonymous Access is disabled.</span></span> <span data-ttu-id="5ffdb-255">Windows 인증을 사용하는 경우 Windows 사용자 계정에 Analysis Services 인스턴스에 대한 관리 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-255">If you are using Windows Authentication, be sure that your Windows user account has administrative permissions on the Analysis Services instance.</span></span>  
  
###  <a name="administer-the-service"></a><a name="bkmk_admin"></a><span data-ttu-id="5ffdb-256">서비스 관리</span><span class="sxs-lookup"><span data-stu-id="5ffdb-256">Administer the Service</span></span>  
 <span data-ttu-id="5ffdb-257">서비스가 실행되고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-257">Verify the service is running.</span></span> <span data-ttu-id="5ffdb-258">Analysis Services(MSSQLServerOLAPService) 및 데이터베이스 엔진을 비롯하여 SQL Server 서비스의 상태, 이름 및 표시 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-258">Returns status, name, and display name for SQL Server services, including Analysis Services (MSSQLServerOLAPService) and the Database Engine.</span></span>  
  
```powershell
Get-Service mssql*  
```  
  
 <span data-ttu-id="5ffdb-259">프로세스 ID, 핸들 수 및 메모리 사용을 비롯한 프로세스 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-259">Returns properties about a process, including process ID, handle count, and memory usage:</span></span>  
  
```powershell
Get-Process msmdsrv  
```  
  
 <span data-ttu-id="5ffdb-260">관리 셸에서 다음 cmdlet을 실행하면 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-260">Restarts the service when you issue the following cmdlet from the administrator shell:</span></span>  
  
```powershell
Restart-Service mssqlserverolapservice  
```  
  
###  <a name="get-help-for-analysis-services-powershell"></a><a name="bkmk_help"></a><span data-ttu-id="5ffdb-261">Analysis Services PowerShell에 대 한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="5ffdb-261">Get Help for Analysis Services PowerShell</span></span>  
 <span data-ttu-id="5ffdb-262">다음 cmdlet을 사용하여 cmdlet 사용 가능 여부를 확인하고 서비스, 프로세스 및 개체에 대한 추가 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-262">Use any of the following cmdlets to verify cmdlet availability and to get more information about services, processes, and objects.</span></span>  
  
1.  <span data-ttu-id="5ffdb-263">`Get-Help`는 예를 포함하여 Analysis Services cmdlet에 대한 기본 제공 도움말을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-263">`Get-Help` returns the built-in help for an Analysis Services cmdlet, including examples:</span></span>  
  
    ```powershell
    Get-Help invoke-ascmd -Examples  
    ```  
  
2.  <span data-ttu-id="5ffdb-264">`Get-Command`는 Analysis Services PowerShell cmdlet 11개의 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-264">`Get-Command` returns a list of the eleven Analysis Services PowerShell cmdlets:</span></span>  
  
    ```powershell
    Get-Command -module SQLASCmdlets  
    ```  
  
3.  <span data-ttu-id="5ffdb-265">`Get-Member`는 서비스 또는 프로세스의 속성 또는 메서드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-265">`Get-Member` returns properties or methods of a service or process.</span></span>  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Property  
    ```  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Method  
    ```  
  
    ```powershell
    Get-Process msmdsrv | Get-Member -Type Property  
    ```  
  
4.  <span data-ttu-id="5ffdb-266">`Get-Member`는 SQLAS 공급자를 통해 서버 인스턴스를 지정하여 개체의 속성 및 메서드(예: 서버 개체의 AMO 메서드)를 반환하는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-266">`Get-Member` can also be used to return properties or methods of an object (for example, AMO methods on the server object) using the SQLAS provider to specify the server instance.</span></span>  
  
    ```
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = New-Object Microsoft.AnalysisServices.Server  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = | Get-Member -Type Method  
    ```  
  
5.  <span data-ttu-id="5ffdb-267">`Get-PSdrive`는 현재 설치되어 있는 공급자 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-267">`Get-PSdrive` returns a list of the providers that are currently installed.</span></span> <span data-ttu-id="5ffdb-268">SQLPS 모듈을 가져온 경우 목록에 `SQLServer` 공급자가 표시됩니다. SQLAS는 SQLServer 공급자의 일부이므로 목록에 별도로 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ffdb-268">If you imported the SQLPS module, you will see the `SQLServer` provider in the list (SQLAS is part of the SQLServer provider and never appears separately in the list):</span></span>  
  
    ```powershell
    Get-PSDrive  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5ffdb-269">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ffdb-269">See Also</span></span>  
 <span data-ttu-id="5ffdb-270">[SQL Server PowerShell 설치](../database-engine/install-windows/install-sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="5ffdb-270">[Install SQL Server PowerShell](../database-engine/install-windows/install-sql-server-powershell.md) </span></span>  
 <span data-ttu-id="5ffdb-271">[PowerShell을 사용 하 여 테이블 형식 모델 관리 (블로그)](https://go.microsoft.com/fwlink/?linkID=227685) </span><span class="sxs-lookup"><span data-stu-id="5ffdb-271">[Manage Tabular Models Using PowerShell (blog)](https://go.microsoft.com/fwlink/?linkID=227685) </span></span>  
 [<span data-ttu-id="5ffdb-272">IIS&#40;인터넷 정보 서비스&#41; 8.0에서 Analysis Services에 대한 HTTP 액세스 구성</span><span class="sxs-lookup"><span data-stu-id="5ffdb-272">Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0</span></span>](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
