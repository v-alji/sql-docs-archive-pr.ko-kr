---
title: sqlcmd 유틸리티 | Microsoft 문서
ms.custom: ''
ms.date: 11/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- sqlcmd commands
- ED command
- sqlcmd utility
- command prompt utilities [SQL Server], sqlcmd
- '!! command'
- stored procedures [SQL Server], command prompt
- system stored procedures [SQL Server], command prompt
- sqlcmd utility, about sqlcmd utility
- scripts [SQL Server], command prompt
- RESET command
- GO command
ms.assetid: e1728707-5215-4c04-8320-e36f161b834a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fbe5a3dcefb2218543e015dad71acfe79aea8e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739016"
---
# <a name="sqlcmd-utility"></a><span data-ttu-id="db831-102">sqlcmd 유틸리티</span><span class="sxs-lookup"><span data-stu-id="db831-102">sqlcmd Utility</span></span>
  <span data-ttu-id="db831-103">`sqlcmd`유틸리티를 사용 하면 [!INCLUDE[tsql](../includes/tsql-md.md)] 명령 프롬프트, SQLCMD 모드의 **쿼리 편집기** , Windows 스크립트 파일 또는 에이전트 작업의 운영 체제 (Cmd.exe) 작업 단계에서 문, 시스템 프로시저 및 스크립트 파일을 입력할 수 있습니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="db831-103">The `sqlcmd` utility lets you enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt, in **Query Editor** in SQLCMD mode, in a Windows script file or in an operating system (Cmd.exe) job step of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="db831-104">이 유틸리티는 ODBC를 사용하여 [!INCLUDE[tsql](../includes/tsql-md.md)] 일괄 처리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-104">This utility uses ODBC to execute [!INCLUDE[tsql](../includes/tsql-md.md)] batches.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="db831-105">는 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] **쿼리 편집기**의 일반 및 SQLCMD 모드에서 실행 하기 위해 SqlClient를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-105">uses the [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]SqlClient for execution in regular and SQLCMD mode in **Query Editor**.</span></span> <span data-ttu-id="db831-106">명령줄에서 `sqlcmd`를 실행할 경우 `sqlcmd`는 ODBC 드라이버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-106">When `sqlcmd` is run from the command line, `sqlcmd` uses the ODBC driver.</span></span> <span data-ttu-id="db831-107">서로 다른 기본 옵션이 적용될 수 있으므로 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] SQLCMD 모드 및 `sqlcmd` 유틸리티에서 동일한 쿼리를 실행할 때 다른 동작이 수행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-107">Because different default options may apply, you might see different behavior when you execute the same query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] in SQLCMD Mode and in the `sqlcmd` utility.</span></span>  
  
 <span data-ttu-id="db831-108">현재는 `sqlcmd`를 실행할 때 명령줄 옵션과 값 사이에 공백을 넣을 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-108">Currently, `sqlcmd` does not require a space between the command line option and the value.</span></span> <span data-ttu-id="db831-109">하지만 후속 릴리스에서는 명령줄 옵션과 값 사이에 공백을 넣어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-109">However, in a future release, a space may be required between the command line option and the value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db831-110">구문</span><span class="sxs-lookup"><span data-stu-id="db831-110">Syntax</span></span>  
  
```  
  
   sqlcmd  
   -a  
   packet_size  
   -A (dedicated administrator connection)  
-b (terminate batch job if there is an error)  
-cbatch_terminator-C (trust the server certificate)  
-ddb_name-e (echo input)  
-E (use trusted connection)  
-fcodepage | i:codepage[,o:codepage] | o:codepage[,i:codepage]  
-hrows_per_header-Hworkstation_name-iinput_file-I (enable quoted identifiers)  
-k[1 | 2] (remove or replace control characters)  
-Kapplication_intent-llogin_timeout-L[c] (list servers, optional clean output)  
-merror_level-Mmultisubnet_failover-N (encrypt connection)  
-ooutput_file-p[1] (print statistics, optional colon format)  
-Ppassword-q "cmdline query"-Q "cmdline query" (and exit)  
-r[0 | 1] (msgs to stderr)  
-R (use client regional settings)  
-scol_separator-S [protocol:]server[\instance_name][,port]  
-tquery_timeout-u (unicode output file)  
-Ulogin_id-vvar = "value"-Verror_severity_level-wcolumn_width-W (remove trailing spaces)  
-x (disable variable substitution)  
-X[1] (disable commands, startup script, environment variables and optional exit)  
-yvariable_length_type_display_width-Yfixed_length_type_display_width-znew_password -Znew_password (and exit)  
  
-? (usage)  
```  
  
## <a name="command-line-options"></a><span data-ttu-id="db831-111">명령줄 옵션</span><span class="sxs-lookup"><span data-stu-id="db831-111">Command-line Options</span></span>  
 <span data-ttu-id="db831-112">**로그인 관련 옵션**</span><span class="sxs-lookup"><span data-stu-id="db831-112">**Login-Related Options**</span></span>  
  <span data-ttu-id="db831-113">**-A**</span><span class="sxs-lookup"><span data-stu-id="db831-113">**-A**</span></span>  
 <span data-ttu-id="db831-114">DAC(관리자 전용 연결)를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-114">Logs in to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with a Dedicated Administrator Connection (DAC).</span></span> <span data-ttu-id="db831-115">이 연결 유형은 서버 문제를 해결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-115">This kind of connection is used to troubleshoot a server.</span></span> <span data-ttu-id="db831-116">이 연결은 DAC를 지원하는 서버 컴퓨터에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-116">This will only work with server computers that support DAC.</span></span> <span data-ttu-id="db831-117">DAC를 사용할 수 없는 경우 `sqlcmd`는 오류 메시지를 생성하고 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-117">If DAC is not available, `sqlcmd` generates an error message and then exits.</span></span> <span data-ttu-id="db831-118">DAC에 대한 자세한 내용은 [데이터베이스 관리자를 위한 진단 연결](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db831-118">For more information about DAC, see [Diagnostic Connection for Database Administrators](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span>  
  
 <span data-ttu-id="db831-119">**-C**</span><span class="sxs-lookup"><span data-stu-id="db831-119">**-C**</span></span>  
 <span data-ttu-id="db831-120">이 스위치는 클라이언트에서 유효성 검사 없이 암시적으로 서버 인증서를 신뢰하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-120">This switch is used by the client to configure it to implicitly trust the server certificate without validation.</span></span> <span data-ttu-id="db831-121">이 옵션은 ADO.NET 옵션 `TRUSTSERVERCERTIFICATE = true`와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-121">This option is equivalent to the ADO.NET option `TRUSTSERVERCERTIFICATE = true`.</span></span>  
  
 <span data-ttu-id="db831-122">**-d** _db_name_</span><span class="sxs-lookup"><span data-stu-id="db831-122">**-d** _db_name_</span></span>  
 <span data-ttu-id="db831-123">를 `USE` 시작할 때 *db_name* 문을 실행 `sqlcmd` 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-123">Issues a `USE` *db_name* statement when you start `sqlcmd`.</span></span> <span data-ttu-id="db831-124">이 옵션은 `sqlcmd` 스크립팅 변수 SQLCMDDBNAME을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-124">This option sets the `sqlcmd` scripting variable SQLCMDDBNAME.</span></span> <span data-ttu-id="db831-125">이 변수는 초기 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-125">This specifies the initial database.</span></span> <span data-ttu-id="db831-126">기본값은 사용자 로그인의 기본 데이터베이스 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-126">The default is your login's default-database property.</span></span> <span data-ttu-id="db831-127">데이터베이스가 없을 경우 오류 메시지가 생성되고 `sqlcmd`가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-127">If the database does not exist, an error message is generated and `sqlcmd` exits.</span></span>  
  
 <span data-ttu-id="db831-128">**-l** _login_timeout_</span><span class="sxs-lookup"><span data-stu-id="db831-128">**-l** _login_timeout_</span></span>  
 <span data-ttu-id="db831-129">서버에 연결을 시도할 때 ODBC 드라이버에 대한 `sqlcmd` 로그인 제한 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-129">Specifies the number of seconds before a `sqlcmd` login to the ODBC driver times out when you try to connect to a server.</span></span> <span data-ttu-id="db831-130">이 옵션은 `sqlcmd` 스크립팅 변수 SQLCMDLOGINTIMEOUT을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-130">This option sets the `sqlcmd` scripting variable SQLCMDLOGINTIMEOUT.</span></span> <span data-ttu-id="db831-131">기본 `sqlcmd` 로그인 제한 시간은 8초입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-131">The default time-out for login to `sqlcmd` is eight seconds.</span></span> <span data-ttu-id="db831-132">로그인 제한 시간은 0에서 65534 사이의 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-132">The login time-out must be a number between 0 and 65534.</span></span> <span data-ttu-id="db831-133">입력한 값이 숫자가 아니거나 이 범위에 속하지 않을 경우 `sqlcmd`는 오류 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-133">If the value supplied is not numeric or does not fall into that range, `sqlcmd` generates an error message.</span></span> <span data-ttu-id="db831-134">값을 0으로 설정하면 제한 시간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-134">A value of 0 specifies time-out to be infinite.</span></span>  
  
 <span data-ttu-id="db831-135">**-E**</span><span class="sxs-lookup"><span data-stu-id="db831-135">**-E**</span></span>  
 <span data-ttu-id="db831-136">사용자 이름과 암호를 사용하는 대신 트러스트된 연결을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-136">Uses a trusted connection instead of using a user name and password to log on to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="db831-137">-E를 지정하지 않으면 `sqlcmd`는 기본적으로 트러스트된 연결 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-137">By default, without -E specified, `sqlcmd` uses the trusted connection option.</span></span>  
  
 <span data-ttu-id="db831-138">**-E** 옵션은 SQLCMDPASSWORD 등의 가능한 사용자 이름 및 암호 환경 변수 설정을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-138">The **-E** option ignores possible user name and password environment variable settings such as SQLCMDPASSWORD.</span></span> <span data-ttu-id="db831-139">**-E** 옵션과 함께 **-U** 옵션 또는 **-P** 옵션을 사용하면 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-139">If the **-E** option is used together with the **-U** option or the **-P** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="db831-140">**-H** _workstation_name_</span><span class="sxs-lookup"><span data-stu-id="db831-140">**-H** _workstation_name_</span></span>  
 <span data-ttu-id="db831-141">워크스테이션 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-141">A workstation name.</span></span> <span data-ttu-id="db831-142">이 옵션은 `sqlcmd` 스크립팅 변수 SQLCMDWORKSTATION을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-142">This option sets the `sqlcmd` scripting variable SQLCMDWORKSTATION.</span></span> <span data-ttu-id="db831-143">워크스테이션 이름은 **sys.processes** 카탈로그 뷰의 **hostname** 열에 나열되며 **sp_who** 저장 프로시저를 사용하여 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-143">The workstation name is listed in the **hostname** column of the **sys.processes** catalog view and can be returned using the stored procedure **sp_who**.</span></span> <span data-ttu-id="db831-144">이 옵션을 지정하지 않으면 기본적으로 현재 컴퓨터 이름이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-144">If this option is not specified, the default is the current computer name.</span></span> <span data-ttu-id="db831-145">이 이름을 사용하여 다른 `sqlcmd` 세션을 식별할 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="db831-145">This name can be used to identify different `sqlcmd` sessions.</span></span>  
  
 <span data-ttu-id="db831-146">**-K** _application_intent_</span><span class="sxs-lookup"><span data-stu-id="db831-146">**-K** _application_intent_</span></span>  
 <span data-ttu-id="db831-147">서버에 연결할 때 애플리케이션 작업 유형을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-147">Declares the application workload type when connecting to a server.</span></span> <span data-ttu-id="db831-148">현재 **ReadOnly**값만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-148">The only currently supported value is **ReadOnly**.</span></span> <span data-ttu-id="db831-149">**-K**를 지정하지 않으면 sqlcmd 유틸리티가 AlwaysOn 가용성 그룹에 있는 보조 복제본에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-149">If **-K** is not specified, the sqlcmd utility will not support connectivity to a secondary replica in an AlwaysOn availability group.</span></span> <span data-ttu-id="db831-150">자세한 내용은 [활성 보조: 읽기 가능한 보조 복제본](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db831-150">For more information, see [Active Secondaries: Readable Secondary Replicas](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="db831-151">`-M`*multisubnet_failover*</span><span class="sxs-lookup"><span data-stu-id="db831-151">`-M` *multisubnet_failover*</span></span>  
 <span data-ttu-id="db831-152">`-M` 가용성 그룹 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터 인스턴스의 가용성 그룹 수신기에 연결할 때는 항상 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="db831-152">Always specify `-M` when connecting to the availability group listener of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] availability group or a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Failover Cluster Instance.</span></span> <span data-ttu-id="db831-153">`-M`은 현재 활성 상태인 서버를 빠르게 검색하여 연결할 수 있도록 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-153">`-M` provides for faster detection of and connection to the (currently) active server.</span></span> <span data-ttu-id="db831-154">`-M`이 지정되지 않은 경우 `-M`이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-154">If `-M` is not specified, `-M` is off.</span></span> <span data-ttu-id="db831-155">에 대 한 자세한 내용은 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] [가용성 그룹 수신기, 클라이언트 연결 및 응용 프로그램 장애 조치 (failover) &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md), [가용성 그룹 만들기 및 구성 &#40;SQL Server ](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)&#41;, [장애 조치 (failover) 클러스터링 및 AlwaysOn 가용성 그룹 ](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)&#40;SQL Server 및 [활성 보조: 읽기 가능한 보조 복제본](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db831-155">For more information about [!INCLUDE[ssHADR](../includes/sshadr-md.md)], see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md), [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md), and [Active Secondaries: Readable Secondary Replicas](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) .</span></span>  
  
 <span data-ttu-id="db831-156">**-N**</span><span class="sxs-lookup"><span data-stu-id="db831-156">**-N**</span></span>  
 <span data-ttu-id="db831-157">이 스위치는 클라이언트에서 암호화된 연결을 요청하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-157">This switch is used by the client to request an encrypted connection.</span></span>  
  
 <span data-ttu-id="db831-158">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="db831-158">**-P** _password_</span></span>  
 <span data-ttu-id="db831-159">사용자가 지정하는 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-159">Is a user-specified password.</span></span> <span data-ttu-id="db831-160">암호는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-160">Passwords are case sensitive.</span></span> <span data-ttu-id="db831-161">-U 옵션을 사용 하 고 **-P** 옵션을 사용 하지 않고 SQLCMDPASSWORD 환경 변수를 설정 하지 않은 경우에서 사용자에 게 `sqlcmd` 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-161">If the -U option is used and the **-P** option is not used, and the SQLCMDPASSWORD environment variable has not been set, `sqlcmd` prompts the user for a password.</span></span> <span data-ttu-id="db831-162">암호 없이 명령 프롬프트의 끝에 **-P** 옵션을 사용 하면 `sqlcmd` 기본 암호 (NULL)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-162">If the **-P** option is used at the end of the command prompt without a password `sqlcmd` uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="db831-163">빈 암호를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="db831-163">Do not use a blank password.</span></span> <span data-ttu-id="db831-164">강력한 암호를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="db831-164">Use a strong password.</span></span> <span data-ttu-id="db831-165">자세한 내용은 [Strong Passwords](../relational-databases/security/strong-passwords.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db831-165">For more information, see [Strong Passwords](../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="db831-166">암호 프롬프트는 다음과 같이 콘솔에 출력되어 표시됩니다. `Password:`</span><span class="sxs-lookup"><span data-stu-id="db831-166">The password prompt is displayed by printing the password prompt to the console, as follows: `Password:`</span></span>  
  
 <span data-ttu-id="db831-167">사용자 입력은 숨겨지므로</span><span class="sxs-lookup"><span data-stu-id="db831-167">User input is hidden.</span></span> <span data-ttu-id="db831-168">아무 것도 표시되지 않고 커서가 해당 위치에 그대로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-168">This means that nothing is displayed and the cursor stays in position.</span></span>  
  
 <span data-ttu-id="db831-169">SQLCMDPASSWORD 환경 변수를 사용하면 현재 세션에 대한 기본 암호를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-169">The SQLCMDPASSWORD environment variable lets you set a default password for the current session.</span></span> <span data-ttu-id="db831-170">그러므로 암호를 배치 파일로 하드 코딩할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-170">Therefore, passwords do not have to be hard-coded into batch files.</span></span>  
  
 <span data-ttu-id="db831-171">다음 예에서는 먼저 명령 프롬프트에서 SQLCMDPASSWORD 변수를 설정하고 `sqlcmd` 유틸리티에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-171">The following example first sets the SQLCMDPASSWORD variable at the command prompt and then accesses the `sqlcmd` utility.</span></span> <span data-ttu-id="db831-172">명령 프롬프트에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-172">At the command prompt, type:</span></span>  
  
 `SET SQLCMDPASSWORD= p@a$$w0rd`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="db831-173">컴퓨터 모니터에서 누구나 암호를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-173">The password will be visible to anyone who can see your computer monitor.</span></span>  
  
 <span data-ttu-id="db831-174">명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-174">At the following command prompt, type:</span></span>  
  
 `sqlcmd`  
  
 <span data-ttu-id="db831-175">사용자 이름 및 암호 조합이 잘못된 경우 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-175">If the user name and password combination is incorrect, an error message is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-176">OSQLPASSWORD 환경 변수는 이전 버전과의 호환성을 위해 유지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-176">The OSQLPASSWORD environment variable has been kept for backward compatibility.</span></span> <span data-ttu-id="db831-177">SQLCMDPASSWORD 환경 변수는 OSQLPASSWORD 환경 변수 보다 우선 적용 됩니다. 즉 `sqlcmd` , 및 **osql** 은 간섭 없이 서로 옆에 사용할 수 있으며 이전 스크립트는 계속 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-177">The SQLCMDPASSWORD environment variable takes precedence over the OSQLPASSWORD environment variable; this means that `sqlcmd` and **osql** can be used next to each other without interference and that old scripts will continue to work.</span></span>  
  
 <span data-ttu-id="db831-178">**-P** 옵션과 함께 **-E** 옵션을 사용하면 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-178">If the **-P** option is used with the **-E** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="db831-179">**-P** 옵션 다음에 둘 이상의 인수를 지정하면 오류 메시지가 생성되고 프로그램이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-179">If the **-P** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="db831-180">**-S** [*protocol*:]*server*[ **\\** _instance_name_] [**,**_port_]</span><span class="sxs-lookup"><span data-stu-id="db831-180">**-S** [*protocol*:]*server*[**\\**_instance_name_][**,**_port_]</span></span>  
 <span data-ttu-id="db831-181">연결할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-181">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to which to connect.</span></span> <span data-ttu-id="db831-182">`sqlcmd` 스크립팅 변수 SQLCMDSERVER를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-182">It sets the `sqlcmd` scripting variable SQLCMDSERVER.</span></span>  
  
 <span data-ttu-id="db831-183">해당 서버 컴퓨터에 있는 기본 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결하려면 *server_name*을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-183">Specify *server_name* to connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server computer.</span></span> <span data-ttu-id="db831-184">*server_name* **\\** 해당 서버 컴퓨터에 있는 명명 된 인스턴스에 연결 하려면 server_name [ _instance_name_ ]를 지정 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-184">Specify *server_name* [ **\\**_instance_name_ ] to connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server computer.</span></span> <span data-ttu-id="db831-185">서버 컴퓨터를 지정하지 않으면 `sqlcmd`가 로컬 컴퓨터에 있는 기본 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-185">If no server computer is specified, `sqlcmd` connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="db831-186">네트워크의 원격 컴퓨터에서 `sqlcmd`를 실행할 경우에는 이 옵션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-186">This option is required when you execute `sqlcmd` from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="db831-187">*프로토콜* 은 `tcp` (tcp/ip), `lpc` (공유 메모리) 또는 `np` (명명 된 파이프) 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-187">*protocol* can be `tcp` (TCP/IP), `lpc` (shared memory), or `np` (named pipes).</span></span>  
  
 <span data-ttu-id="db831-188">를 시작할 때 [instance_name] *server_name* 지정 하지 않으면 **\\** _instance_name_ `sqlcmd` 에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] SQLCMDSERVER 환경 변수를 확인 하 고 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-188">If you do not specify a *server_name* [ **\\**_instance_name_ ] when you start `sqlcmd`, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] checks for and uses the SQLCMDSERVER environment variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-189">OSQLSERVER 환경 변수는 이전 버전과의 호환성을 위해 유지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-189">The OSQLSERVER environment variable has been kept for backward compatibility.</span></span> <span data-ttu-id="db831-190">SQLCMDSERVER 환경 변수는 OSQLSERVER 환경 변수 보다 우선 적용 됩니다. 즉 `sqlcmd` , 및 **osql** 은 간섭 없이 서로 옆에 사용할 수 있으며 이전 스크립트는 계속 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-190">The SQLCMDSERVER environment variable takes precedence over the OSQLSERVER environment variable; this means that `sqlcmd` and **osql** can be used next to each other without interference and that old scripts will continue to work.</span></span>  
  
 <span data-ttu-id="db831-191">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="db831-191">**-U** _login_id_</span></span>  
 <span data-ttu-id="db831-192">사용자 로그인 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-192">Is the user login ID.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-193">OSQLUSER 환경 변수는 이전 버전과의 호환성을 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-193">The OSQLUSER environment variable is available for backward compatibility.</span></span> <span data-ttu-id="db831-194">SQLCMDUSER 환경 변수는 OSQLUSER 환경 변수보다 우선적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-194">The SQLCMDUSER environment variable takes precedence over the OSQLUSER environment variable.</span></span> <span data-ttu-id="db831-195">즉 `sqlcmd` , 및 **osql** 은 간섭 없이 서로 옆에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-195">This means that `sqlcmd` and **osql** can be used next to each other without interference.</span></span> <span data-ttu-id="db831-196">이전 **osql** 스크립트도 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-196">It also means that existing **osql** scripts will continue to work.</span></span>  
  
 <span data-ttu-id="db831-197">**-U** 옵션과 **-P** 옵션을 모두 지정 하지 않으면에서 `sqlcmd` Windows 인증 모드를 사용 하 여 연결을 시도 [!INCLUDE[msCoName](../includes/msconame-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-197">If neither the **-U** option nor the **-P** option is specified, `sqlcmd` tries to connect by using [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication mode.</span></span> <span data-ttu-id="db831-198">`sqlcmd`를 실행하는 사용자의 Windows 계정을 기반으로 인증이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-198">Authentication is based on the Windows account of the user who is running `sqlcmd`.</span></span>  
  
 <span data-ttu-id="db831-199">이 항목의 뒷부분에 설명되어 있는 **-E** 옵션과 함께 **-U** 옵션을 사용하면 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-199">If the **-U** option is used with the **-E** option (described later in this topic), an error message is generated.</span></span> <span data-ttu-id="db831-200">**–U** 옵션 다음에 둘 이상의 인수를 지정하면 오류 메시지가 생성되고 프로그램이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-200">If the **-U** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="db831-201">**-z** _new_password_</span><span class="sxs-lookup"><span data-stu-id="db831-201">**-z** _new_password_</span></span>  
 <span data-ttu-id="db831-202">암호를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-202">Change password:</span></span>  
  
 `sqlcmd -U someuser -P s0mep@ssword -z a_new_p@a$$w0rd`  
  
 <span data-ttu-id="db831-203">**-Z** _new_password_</span><span class="sxs-lookup"><span data-stu-id="db831-203">**-Z** _new_password_</span></span>  
 <span data-ttu-id="db831-204">암호 변경 후 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-204">Change password and exit:</span></span>  
  
 `sqlcmd -U someuser -P s0mep@ssword -Z a_new_p@a$$w0rd`  
  
 <span data-ttu-id="db831-205">**입/출력 옵션**</span><span class="sxs-lookup"><span data-stu-id="db831-205">**Input/Output Options**</span></span>  
  <span data-ttu-id="db831-206">**-f** _codepage_ | **i:** _codepage_[ **,o:** _codepage_] | **o:** _codepage_[ **,i:** _codepage_]</span><span class="sxs-lookup"><span data-stu-id="db831-206">**-f** _codepage_ | **i:**_codepage_[**,o:**_codepage_] | **o:**_codepage_[**,i:**_codepage_]</span></span>  
 <span data-ttu-id="db831-207">입력 및 출력 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-207">Specifies the input and output code pages.</span></span> <span data-ttu-id="db831-208">코드 페이지 번호는 설치된 Windows 코드 페이지를 지정하는 숫자 값입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-208">The codepage number is a numeric value that specifies an installed Windows code page.</span></span>  
  
 <span data-ttu-id="db831-209">코드 페이지 변환 규칙은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-209">Code-page conversion rules:</span></span>  
  
-   <span data-ttu-id="db831-210">변환이 필요 없는 유니코드 파일이 입력 파일로 사용된 경우가 아니라면 `sqlcmd`는 지정된 코드 페이지가 없는 경우 입력 파일과 출력 파일에 현재 코드 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-210">If no code pages are specified, `sqlcmd` will use the current code page for both input and output files, unless the input file is a Unicode file, in which case no conversion is required.</span></span>  
  
-   <span data-ttu-id="db831-211">`sqlcmd`는 Big-Endian 및 Little-Endian 유니코드 입력 파일을 모두 자동으로 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-211">`sqlcmd` automatically recognizes both big-endian and little-endian Unicode input files.</span></span> <span data-ttu-id="db831-212">**-u** 옵션이 지정된 경우 출력은 항상 Little-Endian 유니코드가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-212">If the **-u** option has been specified, the output will always be little-endian Unicode.</span></span>  
  
-   <span data-ttu-id="db831-213">지정된 출력 파일이 없는 경우 출력 코드 페이지는 콘솔 코드 페이지가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-213">If no output file is specified, the output code page will be the console code page.</span></span> <span data-ttu-id="db831-214">이 경우 출력이 콘솔에 올바르게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-214">This enables the output to be displayed correctly on the console.</span></span>  
  
-   <span data-ttu-id="db831-215">여러 입력 파일이 있는 경우 동일한 코드 페이지를 사용하는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-215">Multiple input files are assumed to be of the same code page.</span></span> <span data-ttu-id="db831-216">유니코드 및 비유니코드 입력 파일을 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-216">Unicode and non-Unicode input files can be mixed.</span></span>  
  
 <span data-ttu-id="db831-217">명령 프롬프트에서 `chcp`를 입력하여 Cmd.exe의 코드 페이지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-217">Enter `chcp` at the command prompt to verify the code page of Cmd.exe.</span></span>  
  
 <span data-ttu-id="db831-218">**-i** _input_file_[**,**_input_file2_...]</span><span class="sxs-lookup"><span data-stu-id="db831-218">**-i** _input_file_[**,**_input_file2_...]</span></span>  
 <span data-ttu-id="db831-219">SQL 문 또는 저장 프로시저의 일괄 처리가 포함된 파일을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="db831-219">Identifies the file that contains a batch of SQL statements or stored procedures.</span></span> <span data-ttu-id="db831-220">순서대로 읽고 처리할 파일을 여러 개 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-220">Multiple files may be specified that will be read and processed in order.</span></span> <span data-ttu-id="db831-221">파일 이름 사이에 공백을 넣지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="db831-221">Do not use any spaces between file names.</span></span> <span data-ttu-id="db831-222">먼저 `sqlcmd`는 지정한 모든 파일이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-222">`sqlcmd` will first check to see whether all the specified files exist.</span></span> <span data-ttu-id="db831-223">하나 이상의 파일이 없을 경우 `sqlcmd`가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-223">If one or more files do not exist, `sqlcmd` will exit.</span></span> <span data-ttu-id="db831-224">-i 옵션과 -Q/-q 옵션은 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-224">The -i and the -Q/-q options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="db831-225">경로 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-225">Path examples:</span></span>  
  
 <span data-ttu-id="db831-226">**-i** C: \\ 파일 이름<\></span><span class="sxs-lookup"><span data-stu-id="db831-226">**-i** C:\\<filename\></span></span>  
  
 <span data-ttu-id="db831-227">**-i** \\ \\<Server \> \\<$>\\<파일 이름 공유\></span><span class="sxs-lookup"><span data-stu-id="db831-227">**-i** \\\\<Server\>\\<Share$>\\<filename\></span></span>  
  
 <span data-ttu-id="db831-228">**-i** "C:\Some 폴더 \\<파일 이름 \> "</span><span class="sxs-lookup"><span data-stu-id="db831-228">**-i** "C:\Some Folder\\<file name\>"</span></span>  
  
 <span data-ttu-id="db831-229">공백이 포함된 파일 경로는 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-229">File paths that contain spaces must be enclosed in quotation marks.</span></span>  
  
 <span data-ttu-id="db831-230">이 옵션은 두 번 이상 사용할 수 있습니다. **-i**_input_file_ **-i**_input_file._</span><span class="sxs-lookup"><span data-stu-id="db831-230">This option may be used more than once: **-i**_input_file_ **-I**_I input_file._</span></span>  
  
 <span data-ttu-id="db831-231">**-o** _output_file_</span><span class="sxs-lookup"><span data-stu-id="db831-231">**-o** _output_file_</span></span>  
 <span data-ttu-id="db831-232">`sqlcmd`에서 출력을 받는 파일을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="db831-232">Identifies the file that receives output from `sqlcmd`.</span></span>  
  
 <span data-ttu-id="db831-233">**-u** 를 지정하면 *output_file* 이 유니코드 형식으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-233">If **-u** is specified, the *output_file* is stored in Unicode format.</span></span> <span data-ttu-id="db831-234">파일 이름이 잘못된 경우 오류 메시지가 생성되고 `sqlcmd`가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-234">If the file name is not valid, an error message is generated, and `sqlcmd` exits.</span></span> <span data-ttu-id="db831-235">`sqlcmd`는 여러 `sqlcmd` 프로세스를 같은 파일에 동시에 쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-235">`sqlcmd` does not support concurrent writing of multiple `sqlcmd` processes to the same file.</span></span> <span data-ttu-id="db831-236">이 경우 파일 출력이 손상되거나 제대로 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-236">The file output will be corrupted or incorrect.</span></span> <span data-ttu-id="db831-237">파일 형식에 대한 자세한 내용은 **-f** 스위치를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db831-237">See the **-f** switch for more information about file formats.</span></span> <span data-ttu-id="db831-238">이 파일은 존재하지 않는 경우 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="db831-238">This file will be created if it does not exist.</span></span> <span data-ttu-id="db831-239">이전 `sqlcmd` 세션에서와 이름이 같은 파일은 덮어쓰여집니다.</span><span class="sxs-lookup"><span data-stu-id="db831-239">A file of the same name from a prior `sqlcmd` session will be overwritten.</span></span> <span data-ttu-id="db831-240">여기에 지정된 파일은 **stdout** 파일이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="db831-240">The file specified here is not the **stdout** file.</span></span> <span data-ttu-id="db831-241">**Stdout** 파일이 지정 된 경우에는이 파일이 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-241">If a **stdout** file is specified this file will not be used.</span></span>  
  
 <span data-ttu-id="db831-242">경로 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-242">Path examples:</span></span>  
  
 <span data-ttu-id="db831-243">**-o** C: \\< 파일 이름></span><span class="sxs-lookup"><span data-stu-id="db831-243">**-o** C:\\< filename></span></span>  
  
 <span data-ttu-id="db831-244">**-o** \\ \\<Server \> \\<$>\\<파일 이름 공유\></span><span class="sxs-lookup"><span data-stu-id="db831-244">**-o** \\\\<Server\>\\<Share$>\\<filename\></span></span>  
  
 <span data-ttu-id="db831-245">**-o "** C:\Some 폴더 \\<파일 이름 \> "</span><span class="sxs-lookup"><span data-stu-id="db831-245">**-o "** C:\Some Folder\\<file name\>"</span></span>  
  
 <span data-ttu-id="db831-246">공백이 포함된 파일 경로는 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-246">File paths that contain spaces must be enclosed in quotation marks.</span></span>  
  
 <span data-ttu-id="db831-247">**-r**[**0** | **1**]</span><span class="sxs-lookup"><span data-stu-id="db831-247">**-r**[**0** | **1**]</span></span>  
 <span data-ttu-id="db831-248">오류 메시지 출력을 화면으로 리디렉션합니다(**stderr**).</span><span class="sxs-lookup"><span data-stu-id="db831-248">Redirects the error message output to the screen (**stderr**).</span></span> <span data-ttu-id="db831-249">매개 변수를 지정하지 않거나 **0**을 지정하면 심각도가 11 이상인 오류 메시지만 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-249">If you do not specify a parameter or if you specify **0**, only error messages that have a severity level of 11 or higher are redirected.</span></span> <span data-ttu-id="db831-250">**1**을 지정하면 PRINT를 포함하는 모든 오류 메시지 출력이 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-250">If you specify **1**, all error message output including PRINT is redirected.</span></span> <span data-ttu-id="db831-251">-o를 사용할 경우 아무 효과도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-251">Has no effect if you use -o.</span></span> <span data-ttu-id="db831-252">기본적으로 메시지는 **stdout**으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-252">By default, messages are sent to **stdout**.</span></span>  
  
 <span data-ttu-id="db831-253">**-R**</span><span class="sxs-lookup"><span data-stu-id="db831-253">**-R**</span></span>  
 <span data-ttu-id="db831-254">`sqlcmd`에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 클라이언트의 로캘을 기반으로에서 검색 한 숫자, 통화, 날짜 및 시간 열을 지역화 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-254">Causes `sqlcmd` to localize numeric, currency, date, and time columns retrieved from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] based on the client's locale.</span></span> <span data-ttu-id="db831-255">기본적으로 이러한 열은 서버의 국가별 설정을 사용하여 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-255">By default, these columns are displayed using the server's regional settings.</span></span>  
  
 <span data-ttu-id="db831-256">**-u**</span><span class="sxs-lookup"><span data-stu-id="db831-256">**-u**</span></span>  
 <span data-ttu-id="db831-257">*input_file* 형식에 관계없이 *output_file*이 유니코드 형식으로 저장되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-257">Specifies that *output_file* is stored in Unicode format, regardless of the format of *input_file*.</span></span>  
  
 <span data-ttu-id="db831-258">**쿼리 실행 옵션**</span><span class="sxs-lookup"><span data-stu-id="db831-258">**Query Execution Options**</span></span>  
  <span data-ttu-id="db831-259">**-e**</span><span class="sxs-lookup"><span data-stu-id="db831-259">**-e**</span></span>  
 <span data-ttu-id="db831-260">표준 출력 디바이스에 입력 스크립트를 기록합니다(**stdout**).</span><span class="sxs-lookup"><span data-stu-id="db831-260">Writes input scripts to the standard output device (**stdout**).</span></span>  
  
 <span data-ttu-id="db831-261">**-I**</span><span class="sxs-lookup"><span data-stu-id="db831-261">**-I**</span></span>  
 <span data-ttu-id="db831-262">SET QUOTED_IDENTIFIER 연결 옵션을 ON으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-262">Sets the SET QUOTED_IDENTIFIER connection option to ON.</span></span> <span data-ttu-id="db831-263">기본적으로 OFF로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-263">By default, it is set to OFF.</span></span> <span data-ttu-id="db831-264">자세한 내용은 [SET QUOTED_IDENTIFIER&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db831-264">For more information, see [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).</span></span>  
  
 <span data-ttu-id="db831-265">**-q"** _cmdline query_ **"**</span><span class="sxs-lookup"><span data-stu-id="db831-265">**-q"** _cmdline query_ **"**</span></span>  
 <span data-ttu-id="db831-266">`sqlcmd`가 시작될 때 쿼리를 실행하지만 쿼리 실행이 완료되더라도 `sqlcmd`를 종료하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-266">Executes a query when `sqlcmd` starts, but does not exit `sqlcmd` when the query has finished running.</span></span> <span data-ttu-id="db831-267">세미콜론으로 구분된 여러 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-267">Multiple-semicolon-delimited queries can be executed.</span></span> <span data-ttu-id="db831-268">다음 예와 같이 쿼리를 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-268">Use quotation marks around the query, as shown in the following example.</span></span>  
  
 <span data-ttu-id="db831-269">명령 프롬프트에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-269">At the command prompt, type:</span></span>  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="db831-270">쿼리에 GO 종결자를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="db831-270">Do not use the GO terminator in the query.</span></span>  
  
 <span data-ttu-id="db831-271">이 옵션과 함께 `-b`를 지정하면 `sqlcmd`에 오류가 발생하여 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-271">If `-b` is specified together with this option, `sqlcmd` exits on error.</span></span> <span data-ttu-id="db831-272">`-b`에 대해서는 이 항목의 뒷부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-272">`-b` is described later in this topic.</span></span>  
  
 <span data-ttu-id="db831-273">**-Q "** _명령줄 query_ **"**</span><span class="sxs-lookup"><span data-stu-id="db831-273">**-Q"** _cmdline query_ **"**</span></span>  
 <span data-ttu-id="db831-274">`sqlcmd`가 시작될 때 쿼리를 실행한 다음 바로 `sqlcmd`를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-274">Executes a query when `sqlcmd` starts and then immediately exits `sqlcmd`.</span></span> <span data-ttu-id="db831-275">세미콜론으로 구분된 여러 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-275">Multiple-semicolon-delimited queries can be executed.</span></span>  
  
 <span data-ttu-id="db831-276">다음 예와 같이 쿼리를 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-276">Use quotation marks around the query, as shown in the following example.</span></span>  
  
 <span data-ttu-id="db831-277">명령 프롬프트에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-277">At the command prompt, type:</span></span>  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="db831-278">쿼리에 GO 종결자를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="db831-278">Do not use the GO terminator in the query.</span></span>  
  
 <span data-ttu-id="db831-279">이 옵션과 함께 `-b`를 지정하면 `sqlcmd`에 오류가 발생하여 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-279">If `-b` is specified together with this option, `sqlcmd` exits on error.</span></span> <span data-ttu-id="db831-280">`-b`에 대해서는 이 항목의 뒷부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-280">`-b` is described later in this topic.</span></span>  
  
 <span data-ttu-id="db831-281">**-t** _query_timeout_</span><span class="sxs-lookup"><span data-stu-id="db831-281">**-t** _query_timeout_</span></span>  
 <span data-ttu-id="db831-282">명령 또는 SQL 문 제한 시간 (초)을 지정 합니다. 이 옵션은 `sqlcmd` 스크립팅 변수 SQLCMDSTATTIMEOUT을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-282">Specifies the number of seconds before a command (or SQL statement) times out. This option sets the `sqlcmd` scripting variable SQLCMDSTATTIMEOUT.</span></span> <span data-ttu-id="db831-283">*time_out* 값을 지정하지 않으면 명령이 무기한 실행됩니다. *query\*\*time_out*은 1에서 65534 사이의 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-283">If a *time_out* value is not specified, the command does not time out. The *query\*\*time_out* must be a number between 1 and 65534.</span></span> <span data-ttu-id="db831-284">입력한 값이 숫자가 아니거나 이 범위에 속하지 않을 경우 `sqlcmd`는 오류 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-284">If the value supplied is not numeric or does not fall into that range, `sqlcmd` generates an error message.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-285">실제 제한 시간 값은 지정한 *time_out* 값과 몇 초 정도 차이가 날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-285">The actual time out value may vary from the specified *time_out* value by several seconds.</span></span>  
  
 <span data-ttu-id="db831-286">**-vvar =** _value_[ **var =** _value_...]</span><span class="sxs-lookup"><span data-stu-id="db831-286">**-vvar =** _value_[ **var =** _value_...]</span></span>  
 <span data-ttu-id="db831-287">`sqlcmd`스크립트에서 사용할 수 있는 스크립팅 변수를 만듭니다 `sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="db831-287">Creates a `sqlcmd`scripting variable that can be used in a `sqlcmd` script.</span></span> <span data-ttu-id="db831-288">공백이 포함된 값은 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-288">Enclose the value in quotation marks if the value contains spaces.</span></span> <span data-ttu-id="db831-289">여러 **_var_** = **" *`values`* "** 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-289">You can specify multiple **_var_**=**"*`values`*"** values.</span></span> <span data-ttu-id="db831-290">지정한 값에 오류가 있을 경우 `sqlcmd`는 오류 메시지를 생성하고 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-290">If there are errors in any of the values specified, `sqlcmd` generates an error message and then exits.</span></span>  
  
 `sqlcmd -v MyVar1=something MyVar2="some thing"`  
  
 `sqlcmd -v MyVar1=something -v MyVar2="some thing"`  
  
 <span data-ttu-id="db831-291">**-x**</span><span class="sxs-lookup"><span data-stu-id="db831-291">**-x**</span></span>  
 <span data-ttu-id="db831-292">`sqlcmd`에서 스크립팅 변수를 무시하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-292">Causes `sqlcmd` to ignore scripting variables.</span></span> <span data-ttu-id="db831-293">이는 $(*variable_name*) 등의 일반 변수와 형식이 같은 문자열이 포함되어 있을 수 있는 INSERT 문이 스크립트에 많이 포함된 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-293">This is useful when a script contains many INSERT statements that may contain strings that have the same format as regular variables, such as $(*variable_name*).</span></span>  
  
 <span data-ttu-id="db831-294">**형식 지정 옵션**</span><span class="sxs-lookup"><span data-stu-id="db831-294">**Formatting Options**</span></span>  
  <span data-ttu-id="db831-295">**-h** _headers_</span><span class="sxs-lookup"><span data-stu-id="db831-295">**-h** _headers_</span></span>  
 <span data-ttu-id="db831-296">열 머리글 사이에 출력할 행의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-296">Specifies the number of rows to print between the column headings.</span></span> <span data-ttu-id="db831-297">기본적으로 각 쿼리 결과 집합마다 머리글을 한 번 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-297">The default is to print headings one time for each set of query results.</span></span> <span data-ttu-id="db831-298">이 옵션은 `sqlcmd` 스크립팅 변수 SQLCMDHEADERS를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-298">This option sets the `sqlcmd` scripting variable SQLCMDHEADERS.</span></span> <span data-ttu-id="db831-299">머리글을 출력하지 않으려면 **-1** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-299">Use **-1** to specify that headers must not be printed.</span></span> <span data-ttu-id="db831-300">잘못된 값을 지정할 경우 `sqlcmd`는 오류 메시지를 생성하고 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-300">Any value that is not valid causes `sqlcmd` to generate an error message and then exit.</span></span>  
  
 <span data-ttu-id="db831-301">**-k** [**1** | **2**]</span><span class="sxs-lookup"><span data-stu-id="db831-301">**-k** [**1** | **2**]</span></span>  
 <span data-ttu-id="db831-302">출력에서 탭이나 줄 바꿈 문자와 같은 모든 제어 문자를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-302">Removes all control characters, such as tabs and new line characters from the output.</span></span> <span data-ttu-id="db831-303">데이터를 반환할 때 열 서식은 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-303">This preserves column formatting when data is returned.</span></span> <span data-ttu-id="db831-304">1을 지정하면 제어 문자가 단일 공백으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="db831-304">If 1 is specified, the control characters are replaced by a single space.</span></span> <span data-ttu-id="db831-305">2를 지정하면 연속된 제어 문자가 단일 공백으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="db831-305">If 2 is specified, consecutive control characters are replaced by a single space.</span></span> <span data-ttu-id="db831-306">**-k** 는 **-k1**과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-306">**-k** is the same as **-k1**.</span></span>  
  
 <span data-ttu-id="db831-307">**-s** _col_separator_</span><span class="sxs-lookup"><span data-stu-id="db831-307">**-s** _col_separator_</span></span>  
 <span data-ttu-id="db831-308">열 구분 기호 문자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-308">Specifies the column-separator character.</span></span> <span data-ttu-id="db831-309">기본값은 공백입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-309">The default is a blank space.</span></span> <span data-ttu-id="db831-310">이 옵션은 `sqlcmd` 스크립팅 변수 SQLCMDCOLSEP를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-310">This option sets the `sqlcmd` scripting variable SQLCMDCOLSEP.</span></span> <span data-ttu-id="db831-311">앰퍼샌드(&)나 세미콜론(;)과 같이 운영 체제에서 특별한 의미를 갖는 문자를 사용하려면 해당 문자를 따옴표(")로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-311">To use characters that have special meaning to the operating system such as the ampersand (&), or semicolon (;), enclose the character in quotation marks (").</span></span> <span data-ttu-id="db831-312">열 구분 기호로 임의의 8비트 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-312">The column separator can be any 8-bit character.</span></span>  
  
 <span data-ttu-id="db831-313">**-w** _column_width_</span><span class="sxs-lookup"><span data-stu-id="db831-313">**-w** _column_width_</span></span>  
 <span data-ttu-id="db831-314">출력할 화면 너비를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-314">Specifies the screen width for output.</span></span> <span data-ttu-id="db831-315">이 옵션은 `sqlcmd` 스크립팅 변수 SQLCMDCOLWIDTH를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-315">This option sets the `sqlcmd` scripting variable SQLCMDCOLWIDTH.</span></span> <span data-ttu-id="db831-316">열 너비는 8보다 크고 65536보다 작은 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-316">The column width must be a number greater than 8 and less than 65536.</span></span> <span data-ttu-id="db831-317">지정한 열 너비가 이 범위에 속하지 않을 경우 `sqlcmd`는 오류 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-317">If the specified column width does not fall into that range, `sqlcmd` generates and error message.</span></span> <span data-ttu-id="db831-318">기본 너비는 80자입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-318">The default width is 80 characters.</span></span> <span data-ttu-id="db831-319">출력 줄이 지정한 열 너비를 초과하면 다음 줄로 넘어갑니다.</span><span class="sxs-lookup"><span data-stu-id="db831-319">When an output line exceeds the specified column width, it wraps on to the next line.</span></span>  
  
 <span data-ttu-id="db831-320">**-W**</span><span class="sxs-lookup"><span data-stu-id="db831-320">**-W**</span></span>  
 <span data-ttu-id="db831-321">이 옵션은 열에서 후행 공백을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-321">This option removes trailing spaces from a column.</span></span> <span data-ttu-id="db831-322">다른 애플리케이션으로 내보낼 데이터를 준비하는 경우 **-s** 옵션과 함께 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-322">Use this option together with the **-s** option when preparing data that is to be exported to another application.</span></span> <span data-ttu-id="db831-323">**-y** 또는 **-Y** 옵션과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-323">Cannot be used with the **-y** or **-Y** options.</span></span>  
  
 <span data-ttu-id="db831-324">**-y** _variable_length_type_display_width_</span><span class="sxs-lookup"><span data-stu-id="db831-324">**-y** _variable_length_type_display_width_</span></span>  
 <span data-ttu-id="db831-325">`sqlcmd` 스크립팅 변수 SQLCMDMAXVARTYPEWIDTH를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-325">Sets the `sqlcmd` scripting variable SQLCMDMAXVARTYPEWIDTH.</span></span> <span data-ttu-id="db831-326">기본값은 256입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-326">The default is 256.</span></span> <span data-ttu-id="db831-327">다음과 같은 큰 가변 길이 데이터 형식에 대해 반환되는 문자 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-327">It limits the number of characters that are returned for the large variable length data types:</span></span>  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `xml`  
  
-   `UDT (user-defined data types)`  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
> [!NOTE]  
>  <span data-ttu-id="db831-328">UDT는 구현에 따라 길이가 고정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-328">UDTs can be of fixed length depending on the implementation.</span></span> <span data-ttu-id="db831-329">길이가 고정된 UDT의 길이가 *display_width*보다 짧으면 반환되는 UDT 값은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-329">If this length of a fixed length UDT is shorter that *display_width*, the value of the UDT returned is not affected.</span></span> <span data-ttu-id="db831-330">그러나 길이가 *display_width*보다 길면 출력이 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="db831-330">However, if the length is longer than *display_width*, the output is truncated.</span></span>  
  
 
> [!IMPORTANT]  
>  <span data-ttu-id="db831-331">**-y 0** 옵션은 반환되는 데이터 크기에 따라 서버와 네트워크 모두에서 심각한 성능 문제를 일으킬 수 있으므로 사용 시 매우 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-331">Use the **-y 0** option with extreme caution because it may cause serious performance issues on both the server and the network, depending on the size of data returned.</span></span>  
  
 <span data-ttu-id="db831-332">**-Y** _fixed_length_type_display_width_</span><span class="sxs-lookup"><span data-stu-id="db831-332">**-Y** _fixed_length_type_display_width_</span></span>  
 <span data-ttu-id="db831-333">`sqlcmd` 스크립팅 변수 SQLCMDMAXFIXEDTYPEWIDTH를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-333">Sets the `sqlcmd` scripting variable SQLCMDMAXFIXEDTYPEWIDTH.</span></span> <span data-ttu-id="db831-334">기본값은 0(무제한)입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-334">The default is 0 (unlimited).</span></span> <span data-ttu-id="db831-335">다음 데이터 형식에 대해 반환되는 문자 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-335">Limits the number of characters that are returned for the following data types:</span></span>  
  
-   <span data-ttu-id="db831-336">`char(`*n* `)` , 여기서 1<= n<= 8000</span><span class="sxs-lookup"><span data-stu-id="db831-336">`char(` *n* `)`, where 1<=n<=8000</span></span>  
  
-   <span data-ttu-id="db831-337">`nchar(n`*n* `)` , 여기서 1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="db831-337">`nchar(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   <span data-ttu-id="db831-338">`varchar(n`*n* `)` , 여기서 1<= n<= 8000</span><span class="sxs-lookup"><span data-stu-id="db831-338">`varchar(n` *n* `)`, where 1<=n<=8000</span></span>  
  
-   <span data-ttu-id="db831-339">`nvarchar(n`*n* `)` , 여기서 1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="db831-339">`nvarchar(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   <span data-ttu-id="db831-340">`varbinary(n`*n* `)` , 여기서 1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="db831-340">`varbinary(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   `variant`  
  
 <span data-ttu-id="db831-341">**오류 보고 옵션**</span><span class="sxs-lookup"><span data-stu-id="db831-341">**Error Reporting Options**</span></span>  
  `-b`  
 <span data-ttu-id="db831-342">오류가 발생하면 `sqlcmd`를 끝내고 DOS ERRORLEVEL 값을 반환하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-342">Specifies that `sqlcmd` exits and returns a DOS ERRORLEVEL value when an error occurs.</span></span> <span data-ttu-id="db831-343">**오류 메시지의 심각도가 10보다 큰 경우 DOS ERRORLEVEL 변수로** 1 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 이 반환되며 심각도가 10보다 작거나 같은 경우 **0**이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-343">The value that is returned to the DOS ERRORLEVEL variable is **1** when the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] error message has a severity level greater than 10; otherwise, the value returned is **0**.</span></span> <span data-ttu-id="db831-344">`-V` 외에도 `-b` 옵션을 설정한 경우 심각도가 `-V`를 사용하여 설정한 값보다 작으면 `sqlcmd`는 오류를 보고하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-344">If the `-V` option has been set in addition to `-b`, `sqlcmd` will not report an error if the severity level is lower than the values set using `-V`.</span></span> <span data-ttu-id="db831-345">명령 프롬프트 배치 파일은 ERRORLEVEL 값을 테스트하고 그에 따라 적절히 오류를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-345">Command prompt batch files can test the value of ERRORLEVEL and handle the error appropriately.</span></span> <span data-ttu-id="db831-346">`sqlcmd`는 심각도가 10(정보 메시지)인 오류는 보고하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-346">`sqlcmd` does not report errors for severity level 10 (informational messages).</span></span>  
  
 <span data-ttu-id="db831-347">`sqlcmd` 스크립트에 잘못된 설명 또는 구문 오류가 포함되었거나 스크립팅 변수가 없을 경우 반환되는 ERRORLEVEL은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-347">If the `sqlcmd` script contains an incorrect comment, syntax error, or is missing a scripting variable, ERRORLEVEL returned is 1.</span></span>  
  
 <span data-ttu-id="db831-348">**-m** _error_level_</span><span class="sxs-lookup"><span data-stu-id="db831-348">**-m** _error_level_</span></span>  
 <span data-ttu-id="db831-349">**stdout**에 보낼 오류 메시지를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-349">Controls which error messages are sent to **stdout**.</span></span> <span data-ttu-id="db831-350">심각도가 이 수준보다 크거나 같은 메시지는 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="db831-350">Messages that have a severity level greater than or equal to this level are sent.</span></span> <span data-ttu-id="db831-351">이 값을 **1**로 설정하면 정보 메시지를 포함한 모든 메시지가 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="db831-351">When this value is set to **-1**, all messages including informational messages, are sent.</span></span> <span data-ttu-id="db831-352">**-m** 과 **-1**사이에는 공백이 있으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-352">Spaces are not allowed between the **-m** and **-1**.</span></span> <span data-ttu-id="db831-353">예를 들어 **-m-1** 은 유효하고 **-m-1** 은 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-353">For example, **-m-1** is valid, and **-m-1** is not.</span></span>  
  
 <span data-ttu-id="db831-354">이 옵션은 `sqlcmd` 스크립팅 변수 SQLCMDERRORLEVEL도 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-354">This option also sets the `sqlcmd` scripting variable SQLCMDERRORLEVEL.</span></span> <span data-ttu-id="db831-355">이 변수의 기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-355">This variable has a default of 0.</span></span>  
  
 <span data-ttu-id="db831-356">`-V`*error_severity_level*</span><span class="sxs-lookup"><span data-stu-id="db831-356">`-V` *error_severity_level*</span></span>  
 <span data-ttu-id="db831-357">ERRORLEVEL 변수를 설정하는 데 사용되는 심각도를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-357">Controls the severity level that is used to set the ERRORLEVEL variable.</span></span> <span data-ttu-id="db831-358">심각도가 이 값보다 크거나 같은 오류 메시지는 ERRORLEVEL을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-358">Error messages that have severity levels greater than or equal to this value set ERRORLEVEL.</span></span> <span data-ttu-id="db831-359">0보다 작은 값은 0으로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-359">Values that are less than 0 are reported as 0.</span></span> <span data-ttu-id="db831-360">배치 파일 및 CMD 파일은 ERRORLEVEL 변수의 값을 테스트하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-360">Batch and CMD files can be used to test the value of the ERRORLEVEL variable.</span></span>  
  
 <span data-ttu-id="db831-361">**기타 옵션**</span><span class="sxs-lookup"><span data-stu-id="db831-361">**Miscellaneous Options**</span></span>  
  <span data-ttu-id="db831-362">**-a** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="db831-362">**-a** _packet_size_</span></span>  
 <span data-ttu-id="db831-363">다른 크기의 패킷을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-363">Requests a packet of a different size.</span></span> <span data-ttu-id="db831-364">이 옵션은 `sqlcmd` 스크립팅 변수 SQLCMDPACKETSIZE를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-364">This option sets the `sqlcmd` scripting variable SQLCMDPACKETSIZE.</span></span> <span data-ttu-id="db831-365">*packet_size* 는 512에서 32767 사이의 값이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-365">*packet_size* must be a value between 512 and 32767.</span></span> <span data-ttu-id="db831-366">기본값은 4096입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-366">The default = 4096.</span></span> <span data-ttu-id="db831-367">GO 명령 사이에 SQL 문 수가 많은 스크립트를 실행할 때는 패킷 크기가 클수록 성능이 더 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-367">A larger packet size can enhance performance for execution of scripts that have lots of SQL statements between GO commands.</span></span> <span data-ttu-id="db831-368">더 큰 패킷 크기를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-368">You can request a larger packet size.</span></span> <span data-ttu-id="db831-369">그러나 요청이 거부되면 `sqlcmd`는 서버 기본값을 패킷 크기로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-369">However, if the request is denied, `sqlcmd` uses the server default for packet size.</span></span>  
  
 <span data-ttu-id="db831-370">**-c** _batch_terminator_</span><span class="sxs-lookup"><span data-stu-id="db831-370">**-c** _batch_terminator_</span></span>  
 <span data-ttu-id="db831-371">일괄 처리 종결자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-371">Specifies the batch terminator.</span></span> <span data-ttu-id="db831-372">기본적으로 줄에 "GO"만 단독으로 입력하면 명령이 종료되어 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="db831-372">By default, commands are terminated and sent to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by typing the word "GO" on a line by itself.</span></span> <span data-ttu-id="db831-373">일괄 처리 종결자를 다시 설정할 때는 앞에 백슬래시가 있더라도 [!INCLUDE[tsql](../includes/tsql-md.md)] 예약 키워드 또는 운영 체제와 연관된 특별한 의미를 가진 문자를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="db831-373">When you reset the batch terminator, do not use [!INCLUDE[tsql](../includes/tsql-md.md)] reserved keywords or characters that have special meaning to the operating system, even if they are preceded by a backslash.</span></span>  
  
 <span data-ttu-id="db831-374">**-L**[**c**]</span><span class="sxs-lookup"><span data-stu-id="db831-374">**-L**[**c**]</span></span>  
 <span data-ttu-id="db831-375">로컬로 구성된 서버 컴퓨터와 네트워크상에서 브로드캐스팅하는 서버 컴퓨터의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-375">Lists the locally configured server computers, and the names of the server computers that are broadcasting on the network.</span></span> <span data-ttu-id="db831-376">이 매개 변수는 다른 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-376">This parameter cannot be used in combination with other parameters.</span></span> <span data-ttu-id="db831-377">표시할 수 있는 최대 서버 컴퓨터 수는 3000대입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-377">The maximum number of server computers that can be listed is 3000.</span></span> <span data-ttu-id="db831-378">버퍼 크기 때문에 서버 목록이 잘린 경우 경고 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-378">If the server list is truncated because of the size of the buffer a warning message is displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-379">네트워크에서 브로드캐스팅의 특성으로 인해 `sqlcmd`는 모든 서버로부터 시기 적절한 응답을 받지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-379">Because of the nature of broadcasting on networks, `sqlcmd` may not receive a timely response from all servers.</span></span> <span data-ttu-id="db831-380">그러므로 반환되는 서버 목록은 이 옵션을 호출할 때마다 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-380">Therefore, the list of servers returned may vary for each invocation of this option.</span></span>  
  
 <span data-ttu-id="db831-381">선택적 매개 변수 **c** 를 지정 하면 서버: 머리글 없이 출력이 나타나고 각 서버 줄이 선행 공백 없이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-381">If the optional parameter **c** is specified, the output appears without the Servers: header line and each server line is listed without leading spaces.</span></span> <span data-ttu-id="db831-382">이를 정리된 출력이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-382">This is referred to as clean output.</span></span> <span data-ttu-id="db831-383">정리된 출력은 스크립트 언어의 처리 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="db831-383">Clean output improves the processing performance of scripting languages.</span></span>  
  
 <span data-ttu-id="db831-384">**-p**[**1**]</span><span class="sxs-lookup"><span data-stu-id="db831-384">**-p**[**1**]</span></span>  
 <span data-ttu-id="db831-385">모든 결과 집합에 대한 성능 통계를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-385">Prints performance statistics for every result set.</span></span> <span data-ttu-id="db831-386">다음은 성능 통계 형식의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-386">The following is an example of the format for performance statistics:</span></span>  
  
 `Network packet size (bytes): n`  
  
 `x xact[s]:`  
  
 `Clock Time (ms.): total       t1  avg       t2 (t3 xacts per sec.)`  
  
 <span data-ttu-id="db831-387">위치:</span><span class="sxs-lookup"><span data-stu-id="db831-387">Where:</span></span>  
  
 <span data-ttu-id="db831-388">`x` = [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 처리되는 트랜잭션 수</span><span class="sxs-lookup"><span data-stu-id="db831-388">`x` = Number of transactions that are processed by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="db831-389">`t1` = 모든 트랜잭션의 총 시간</span><span class="sxs-lookup"><span data-stu-id="db831-389">`t1` = Total time for all transactions.</span></span>  
  
 <span data-ttu-id="db831-390">`t2` = 단일 트랜잭션의 평균 시간</span><span class="sxs-lookup"><span data-stu-id="db831-390">`t2` = Average time for a single transaction.</span></span>  
  
 <span data-ttu-id="db831-391">`t3` = 초당 평균 트랜잭션 수</span><span class="sxs-lookup"><span data-stu-id="db831-391">`t3` = Average number of transactions per second.</span></span>  
  
 <span data-ttu-id="db831-392">모든 시간은 밀리초 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-392">All times are in milliseconds.</span></span>  
  
 <span data-ttu-id="db831-393">선택적 매개 변수 **1** 을 지정할 경우 통계의 출력 형식은 콜론으로 구분된 형식입니다. 이 형식은 스프레드시트로 쉽게 가져오거나 스크립트를 통해 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-393">If the optional parameter **1** is specified, the output format of the statistics is in colon-separated format that can be imported easily into a spreadsheet or processed by a script.</span></span>  
  
 <span data-ttu-id="db831-394">선택적 매개 변수 값이 **1**이 아닌 경우 오류가 생성 되 고가 종료 됩니다 `sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="db831-394">If the optional parameter is any value other than **1**, an error is generated and `sqlcmd` exits.</span></span>  
  
 <span data-ttu-id="db831-395">`-X`[**1**]</span><span class="sxs-lookup"><span data-stu-id="db831-395">`-X`[**1**]</span></span>  
 <span data-ttu-id="db831-396">배치 파일에서 `sqlcmd`를 실행할 때 시스템 보안을 손상시킬 수 있는 명령을 사용할 수 없게 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-396">Disables commands that might compromise system security when `sqlcmd` is executed from a batch file.</span></span> <span data-ttu-id="db831-397">사용할 수 없게 설정된 명령은 여전히 인식되지만 `sqlcmd`는 경고 메시지를 표시하고 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-397">The disabled commands are still recognized; `sqlcmd` issues a warning message and continues.</span></span> <span data-ttu-id="db831-398">선택적 매개 변수 **1** 을 지정 하면에서 `sqlcmd` 오류 메시지를 생성 하 고 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-398">If the optional parameter **1** is specified, `sqlcmd` generates an error message and then exits.</span></span> <span data-ttu-id="db831-399">`-X` 옵션을 사용하면 다음 명령이 사용할 수 없게 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-399">The following commands are disabled when the `-X` option is used:</span></span>  
  
-   <span data-ttu-id="db831-400">**ED**</span><span class="sxs-lookup"><span data-stu-id="db831-400">**ED**</span></span>  
  
-   <span data-ttu-id="db831-401">**!!**</span><span class="sxs-lookup"><span data-stu-id="db831-401">**!!**</span></span> <span data-ttu-id="db831-402">_command_</span><span class="sxs-lookup"><span data-stu-id="db831-402">_command_</span></span>  
  
 <span data-ttu-id="db831-403">`-X` 옵션을 지정하면 환경 변수가 `sqlcmd`에 전달되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-403">If the `-X` option is specified, it prevents environment variables from being passed on to `sqlcmd`.</span></span> <span data-ttu-id="db831-404">또한 SQLCMDINI 스크립팅 변수를 사용하여 지정한 시작 스크립트가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-404">It also prevents the startup script specified by using the SQLCMDINI scripting variable from being executed.</span></span> <span data-ttu-id="db831-405">스크립팅 변수에 대 한 자세한 내용은 `sqlcmd` [스크립팅 변수와 함께 sqlcmd 사용](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db831-405">For more information about `sqlcmd` scripting variables, see [Use sqlcmd with Scripting Variables](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).</span></span>  
  
 <span data-ttu-id="db831-406">**-?**</span><span class="sxs-lookup"><span data-stu-id="db831-406">**-?**</span></span>  
 <span data-ttu-id="db831-407">`sqlcmd` 옵션의 구문 요약 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-407">Displays the syntax summary of `sqlcmd` options.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db831-408">설명</span><span class="sxs-lookup"><span data-stu-id="db831-408">Remarks</span></span>  
 <span data-ttu-id="db831-409">옵션은 구문 섹션에 표시된 순서대로 사용하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-409">Options do not have to be used in the order shown in the syntax section.</span></span>  
  
 <span data-ttu-id="db831-410">여러 결과가 반환된 경우 `sqlcmd`는 일괄 처리의 각 결과 집합 사이에 빈 줄을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-410">When multiple results are returned, `sqlcmd` prints a blank line between each result set in a batch.</span></span> <span data-ttu-id="db831-411">또한 \<x> 실행 된 문에 적용 되지 않으면 "영향을 받은 행" 메시지가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-411">In addition, the "\<x> rows affected" message does not appear when it does not apply to the statement executed.</span></span>  
  
 <span data-ttu-id="db831-412">`sqlcmd`대화형으로 사용 하려면 `sqlcmd` 이 항목의 앞부분에서 설명한 하나 이상의 옵션을 사용 하 여 명령 프롬프트에을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-412">To use `sqlcmd` interactively, type `sqlcmd` at the command prompt with any one or more of the options described earlier in this topic.</span></span> <span data-ttu-id="db831-413">자세한 내용은 [sqlcmd 유틸리티 사용](../relational-databases/scripting/sqlcmd-use-the-utility.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db831-413">For more information, see [Use the sqlcmd Utility](../relational-databases/scripting/sqlcmd-use-the-utility.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-414">**-L**, **-Q**, **-Z** 또는 **-i** 옵션을 선택 하면 `sqlcmd` 실행 후 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-414">The options **-L**, **-Q**, **-Z** or **-i** cause `sqlcmd` to exit after execution.</span></span>  
  
 <span data-ttu-id="db831-415">명령 환경(Cmd.exe)에서 모든 인수 및 확장 변수를 포함한 `sqlcmd` 명령줄의 총 길이는 운영 체제에서 Cmd.exe에 대해 지정한 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-415">The total length of the `sqlcmd` command line in the command environment (Cmd.exe), including all arguments and expanded variables, is that which is determined by the operating system for Cmd.exe.</span></span>  
  
## <a name="variable-precedence-low-to-high"></a><span data-ttu-id="db831-416">변수 우선 순위(낮은 순위에서 높은 순위)</span><span class="sxs-lookup"><span data-stu-id="db831-416">Variable Precedence (Low to High)</span></span>  
  
1.  <span data-ttu-id="db831-417">시스템 수준 환경 변수</span><span class="sxs-lookup"><span data-stu-id="db831-417">System-level environmental variables.</span></span>  
  
2.  <span data-ttu-id="db831-418">사용자 수준 환경 변수</span><span class="sxs-lookup"><span data-stu-id="db831-418">User-level environmental variables</span></span>  
  
3.  <span data-ttu-id="db831-419">실행 하기 전에 명령 프롬프트에서 설정한 명령 셸 (**set** X = Y) `sqlcmd` 입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-419">Command shell (**SET** X=Y) set at command prompt before running `sqlcmd`.</span></span>  
  
4.  <span data-ttu-id="db831-420">**sqlcmd-v** X=Y</span><span class="sxs-lookup"><span data-stu-id="db831-420">**sqlcmd-v** X=Y</span></span>  
  
5.  <span data-ttu-id="db831-421">**:Setvar** X Y</span><span class="sxs-lookup"><span data-stu-id="db831-421">**:Setvar** X Y</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-422">환경 변수를 보려면 **제어판**에서 **시스템**을 연 다음 **고급** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-422">To view the environmental variables, in **Control Panel**, open **System**, and then click the **Advanced** tab.</span></span>  
  
## <a name="sqlcmd-scripting-variables"></a><span data-ttu-id="db831-423">sqlcmd 스크립팅 변수</span><span class="sxs-lookup"><span data-stu-id="db831-423">sqlcmd Scripting Variables</span></span>  
  
|<span data-ttu-id="db831-424">변수</span><span class="sxs-lookup"><span data-stu-id="db831-424">Variable</span></span>|<span data-ttu-id="db831-425">관련 스위치</span><span class="sxs-lookup"><span data-stu-id="db831-425">Related switch</span></span>|<span data-ttu-id="db831-426">R/W</span><span class="sxs-lookup"><span data-stu-id="db831-426">R/W</span></span>|<span data-ttu-id="db831-427">기본값</span><span class="sxs-lookup"><span data-stu-id="db831-427">Default</span></span>|  
|--------------|--------------------|----------|-------------|  
|<span data-ttu-id="db831-428">SQLCMDUSER</span><span class="sxs-lookup"><span data-stu-id="db831-428">SQLCMDUSER</span></span>|<span data-ttu-id="db831-429">-U</span><span class="sxs-lookup"><span data-stu-id="db831-429">-U</span></span>|<span data-ttu-id="db831-430">R</span><span class="sxs-lookup"><span data-stu-id="db831-430">R</span></span>|<span data-ttu-id="db831-431">""</span><span class="sxs-lookup"><span data-stu-id="db831-431">""</span></span>|  
|<span data-ttu-id="db831-432">SQLCMDPASSWORD</span><span class="sxs-lookup"><span data-stu-id="db831-432">SQLCMDPASSWORD</span></span>|<span data-ttu-id="db831-433">-P</span><span class="sxs-lookup"><span data-stu-id="db831-433">-P</span></span>|--|<span data-ttu-id="db831-434">""</span><span class="sxs-lookup"><span data-stu-id="db831-434">""</span></span>|  
|<span data-ttu-id="db831-435">SQLCMDSERVER</span><span class="sxs-lookup"><span data-stu-id="db831-435">SQLCMDSERVER</span></span>|<span data-ttu-id="db831-436">-S</span><span class="sxs-lookup"><span data-stu-id="db831-436">-S</span></span>|<span data-ttu-id="db831-437">R</span><span class="sxs-lookup"><span data-stu-id="db831-437">R</span></span>|<span data-ttu-id="db831-438">"DefaultLocalInstance"</span><span class="sxs-lookup"><span data-stu-id="db831-438">"DefaultLocalInstance"</span></span>|  
|<span data-ttu-id="db831-439">SQLCMDWORKSTATION</span><span class="sxs-lookup"><span data-stu-id="db831-439">SQLCMDWORKSTATION</span></span>|<span data-ttu-id="db831-440">-H</span><span class="sxs-lookup"><span data-stu-id="db831-440">-H</span></span>|<span data-ttu-id="db831-441">R</span><span class="sxs-lookup"><span data-stu-id="db831-441">R</span></span>|<span data-ttu-id="db831-442">"ComputerName"</span><span class="sxs-lookup"><span data-stu-id="db831-442">"ComputerName"</span></span>|  
|<span data-ttu-id="db831-443">SQLCMDDBNAME</span><span class="sxs-lookup"><span data-stu-id="db831-443">SQLCMDDBNAME</span></span>|<span data-ttu-id="db831-444">-d</span><span class="sxs-lookup"><span data-stu-id="db831-444">-d</span></span>|<span data-ttu-id="db831-445">R</span><span class="sxs-lookup"><span data-stu-id="db831-445">R</span></span>|<span data-ttu-id="db831-446">""</span><span class="sxs-lookup"><span data-stu-id="db831-446">""</span></span>|  
|<span data-ttu-id="db831-447">SQLCMDLOGINTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db831-447">SQLCMDLOGINTIMEOUT</span></span>|<span data-ttu-id="db831-448">-l</span><span class="sxs-lookup"><span data-stu-id="db831-448">-l</span></span>|<span data-ttu-id="db831-449">R/W</span><span class="sxs-lookup"><span data-stu-id="db831-449">R/W</span></span>|<span data-ttu-id="db831-450">"8"(초)</span><span class="sxs-lookup"><span data-stu-id="db831-450">"8" (seconds)</span></span>|  
|<span data-ttu-id="db831-451">SQLCMDSTATTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db831-451">SQLCMDSTATTIMEOUT</span></span>|<span data-ttu-id="db831-452">-t</span><span class="sxs-lookup"><span data-stu-id="db831-452">-t</span></span>|<span data-ttu-id="db831-453">R/W</span><span class="sxs-lookup"><span data-stu-id="db831-453">R/W</span></span>|<span data-ttu-id="db831-454">"0" = 무기한 대기</span><span class="sxs-lookup"><span data-stu-id="db831-454">"0" = wait indefinitely</span></span>|  
|<span data-ttu-id="db831-455">SQLCMDHEADERS</span><span class="sxs-lookup"><span data-stu-id="db831-455">SQLCMDHEADERS</span></span>|<span data-ttu-id="db831-456">-H</span><span class="sxs-lookup"><span data-stu-id="db831-456">-h</span></span>|<span data-ttu-id="db831-457">R/W</span><span class="sxs-lookup"><span data-stu-id="db831-457">R/W</span></span>|<span data-ttu-id="db831-458">"0"</span><span class="sxs-lookup"><span data-stu-id="db831-458">"0"</span></span>|  
|<span data-ttu-id="db831-459">SQLCMDCOLSEP</span><span class="sxs-lookup"><span data-stu-id="db831-459">SQLCMDCOLSEP</span></span>|<span data-ttu-id="db831-460">-S</span><span class="sxs-lookup"><span data-stu-id="db831-460">-s</span></span>|<span data-ttu-id="db831-461">R/W</span><span class="sxs-lookup"><span data-stu-id="db831-461">R/W</span></span>|<span data-ttu-id="db831-462">" "</span><span class="sxs-lookup"><span data-stu-id="db831-462">" "</span></span>|  
|<span data-ttu-id="db831-463">SQLCMDCOLWIDTH</span><span class="sxs-lookup"><span data-stu-id="db831-463">SQLCMDCOLWIDTH</span></span>|<span data-ttu-id="db831-464">-w</span><span class="sxs-lookup"><span data-stu-id="db831-464">-w</span></span>|<span data-ttu-id="db831-465">R/W</span><span class="sxs-lookup"><span data-stu-id="db831-465">R/W</span></span>|<span data-ttu-id="db831-466">"0"</span><span class="sxs-lookup"><span data-stu-id="db831-466">"0"</span></span>|  
|<span data-ttu-id="db831-467">SQLCMDPACKETSIZE</span><span class="sxs-lookup"><span data-stu-id="db831-467">SQLCMDPACKETSIZE</span></span>|<span data-ttu-id="db831-468">지정하지 않을 경우</span><span class="sxs-lookup"><span data-stu-id="db831-468">-a</span></span>|<span data-ttu-id="db831-469">R</span><span class="sxs-lookup"><span data-stu-id="db831-469">R</span></span>|<span data-ttu-id="db831-470">"4096"</span><span class="sxs-lookup"><span data-stu-id="db831-470">"4096"</span></span>|  
|<span data-ttu-id="db831-471">SQLCMDERRORLEVEL</span><span class="sxs-lookup"><span data-stu-id="db831-471">SQLCMDERRORLEVEL</span></span>|<span data-ttu-id="db831-472">-M</span><span class="sxs-lookup"><span data-stu-id="db831-472">-m</span></span>|<span data-ttu-id="db831-473">R/W</span><span class="sxs-lookup"><span data-stu-id="db831-473">R/W</span></span>|<span data-ttu-id="db831-474">0</span><span class="sxs-lookup"><span data-stu-id="db831-474">0</span></span>|  
|<span data-ttu-id="db831-475">SQLCMDMAXVARTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="db831-475">SQLCMDMAXVARTYPEWIDTH</span></span>|<span data-ttu-id="db831-476">-y</span><span class="sxs-lookup"><span data-stu-id="db831-476">-y</span></span>|<span data-ttu-id="db831-477">R/W</span><span class="sxs-lookup"><span data-stu-id="db831-477">R/W</span></span>|<span data-ttu-id="db831-478">"256"</span><span class="sxs-lookup"><span data-stu-id="db831-478">"256"</span></span>|  
|<span data-ttu-id="db831-479">SQLCMDMAXFIXEDTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="db831-479">SQLCMDMAXFIXEDTYPEWIDTH</span></span>|<span data-ttu-id="db831-480">-y</span><span class="sxs-lookup"><span data-stu-id="db831-480">-Y</span></span>|<span data-ttu-id="db831-481">R/W</span><span class="sxs-lookup"><span data-stu-id="db831-481">R/W</span></span>|<span data-ttu-id="db831-482">"0" = 제한 없음</span><span class="sxs-lookup"><span data-stu-id="db831-482">"0" = unlimited</span></span>|  
|<span data-ttu-id="db831-483">SQLCMDEDITOR</span><span class="sxs-lookup"><span data-stu-id="db831-483">SQLCMDEDITOR</span></span>||<span data-ttu-id="db831-484">R/W</span><span class="sxs-lookup"><span data-stu-id="db831-484">R/W</span></span>|<span data-ttu-id="db831-485">"edit.com"</span><span class="sxs-lookup"><span data-stu-id="db831-485">"edit.com"</span></span>|  
|<span data-ttu-id="db831-486">SQLCMDINI</span><span class="sxs-lookup"><span data-stu-id="db831-486">SQLCMDINI</span></span>||<span data-ttu-id="db831-487">R</span><span class="sxs-lookup"><span data-stu-id="db831-487">R</span></span>|<span data-ttu-id="db831-488">""</span><span class="sxs-lookup"><span data-stu-id="db831-488">""</span></span>|  
  
 <span data-ttu-id="db831-489">SQLCMDUSER, SQLCMDPASSWORD 및 SQLCMDSERVER는 **:Connect**가</span><span class="sxs-lookup"><span data-stu-id="db831-489">SQLCMDUSER, SQLCMDPASSWORD and SQLCMDSERVER are set when **:Connect**</span></span>  
  
 <span data-ttu-id="db831-490">사용될 경우 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-490">is used.</span></span>  
  
 <span data-ttu-id="db831-491">R은 값이 프로그램 초기화 시 한 번만 설정될 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="db831-491">R indicates the value can only be set one time during program initialization.</span></span>  
  
 <span data-ttu-id="db831-492">R/W는 값이 **setvar** 명령을 사용하여 수정될 수 있으며 후속 명령이 새 값의 영향을 받을 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="db831-492">R/W indicates that the value can be modified by using the **setvar** command and subsequent commands will be influenced by the new value.</span></span>  
  
## <a name="sqlcmd-commands"></a><span data-ttu-id="db831-493">sqlcmd 명령</span><span class="sxs-lookup"><span data-stu-id="db831-493">sqlcmd Commands</span></span>  
 <span data-ttu-id="db831-494">`sqlcmd`에서 [!INCLUDE[tsql](../includes/tsql-md.md)] 문 외에도 다음 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-494">In addition to [!INCLUDE[tsql](../includes/tsql-md.md)] statements within `sqlcmd`, the following commands are also available:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db831-495">**GO** [*count*]</span><span class="sxs-lookup"><span data-stu-id="db831-495">**GO** [*count*]</span></span>|<span data-ttu-id="db831-496">**:List**</span><span class="sxs-lookup"><span data-stu-id="db831-496">**:List**</span></span>|  
|<span data-ttu-id="db831-497">[ **:** ] **RESET**</span><span class="sxs-lookup"><span data-stu-id="db831-497">[**:**] **RESET**</span></span>|<span data-ttu-id="db831-498">**:Error**</span><span class="sxs-lookup"><span data-stu-id="db831-498">**:Error**</span></span>|  
|<span data-ttu-id="db831-499">[ **:** ] **ED**</span><span class="sxs-lookup"><span data-stu-id="db831-499">[**:**] **ED**</span></span>|<span data-ttu-id="db831-500">**:Out**</span><span class="sxs-lookup"><span data-stu-id="db831-500">**:Out**</span></span>|  
|<span data-ttu-id="db831-501">[**:**] **!!**</span><span class="sxs-lookup"><span data-stu-id="db831-501">[**:**] **!!**</span></span>|<span data-ttu-id="db831-502">**:Perftrace**</span><span class="sxs-lookup"><span data-stu-id="db831-502">**:Perftrace**</span></span>|  
|<span data-ttu-id="db831-503">[ **:** ] **QUIT**</span><span class="sxs-lookup"><span data-stu-id="db831-503">[**:**] **QUIT**</span></span>|<span data-ttu-id="db831-504">**:Connect**</span><span class="sxs-lookup"><span data-stu-id="db831-504">**:Connect**</span></span>|  
|<span data-ttu-id="db831-505">[ **:** ] **EXIT**</span><span class="sxs-lookup"><span data-stu-id="db831-505">[**:**] **EXIT**</span></span>|<span data-ttu-id="db831-506">**:On Error**</span><span class="sxs-lookup"><span data-stu-id="db831-506">**:On Error**</span></span>|  
|<span data-ttu-id="db831-507">**:r**</span><span class="sxs-lookup"><span data-stu-id="db831-507">**:r**</span></span>|<span data-ttu-id="db831-508">**:Help**</span><span class="sxs-lookup"><span data-stu-id="db831-508">**:Help**</span></span>|  
|<span data-ttu-id="db831-509">**:ServerList**</span><span class="sxs-lookup"><span data-stu-id="db831-509">**:ServerList**</span></span>|<span data-ttu-id="db831-510">**:XML** [**ON** &#124; **OFF**]</span><span class="sxs-lookup"><span data-stu-id="db831-510">**:XML** [**ON** &#124; **OFF**]</span></span>|  
|<span data-ttu-id="db831-511">**:Setvar**</span><span class="sxs-lookup"><span data-stu-id="db831-511">**:Setvar**</span></span>|<span data-ttu-id="db831-512">**:Listvar**</span><span class="sxs-lookup"><span data-stu-id="db831-512">**:Listvar**</span></span>|  
  
 <span data-ttu-id="db831-513">`sqlcmd` 명령을 사용할 때는 다음 사항에 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="db831-513">Be aware of the following when you use `sqlcmd` commands:</span></span>  
  
-   <span data-ttu-id="db831-514">GO를 제외하고 모든 `sqlcmd` 명령에는 접두사로 콜론(:)을 붙여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-514">All `sqlcmd` commands, except GO, must be prefixed by a colon (:).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="db831-515">**osql** 스크립트와의 호환성을 유지하기 위해 일부 명령은 콜론 없이도 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-515">To maintain backward compatibility with existing **osql** scripts, some of the commands will be recognized without the colon.</span></span> <span data-ttu-id="db831-516">이러한 명령은 [**:**]으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-516">This is indicated by the [**:**].</span></span>  
  
-   <span data-ttu-id="db831-517">`sqlcmd` 명령은 줄 시작 부분에 나타난 경우에만 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-517">`sqlcmd` commands are recognized only if they appear at the start of a line.</span></span>  
  
-   <span data-ttu-id="db831-518">모든 `sqlcmd` 명령은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-518">All `sqlcmd` commands are case insensitive.</span></span>  
  
-   <span data-ttu-id="db831-519">각 명령을 별도의 줄에 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-519">Each command must be on a separate line.</span></span> <span data-ttu-id="db831-520">명령 다음에 [!INCLUDE[tsql](../includes/tsql-md.md)] 문이나 다른 명령을 입력할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-520">A command cannot be followed by a [!INCLUDE[tsql](../includes/tsql-md.md)] statement or another command.</span></span>  
  
-   <span data-ttu-id="db831-521">명령은 즉시 실행되며</span><span class="sxs-lookup"><span data-stu-id="db831-521">Commands are executed immediately.</span></span> <span data-ttu-id="db831-522">[!INCLUDE[tsql](../includes/tsql-md.md)] 문처럼 실행 버퍼에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-522">They are not put in the execution buffer as [!INCLUDE[tsql](../includes/tsql-md.md)] statements are.</span></span>  
  
 <span data-ttu-id="db831-523">**명령 편집**</span><span class="sxs-lookup"><span data-stu-id="db831-523">**Editing Commands**</span></span>  
  <span data-ttu-id="db831-524">[ **:** ] **ED**</span><span class="sxs-lookup"><span data-stu-id="db831-524">[**:**] **ED**</span></span>  
 <span data-ttu-id="db831-525">텍스트 편집기를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-525">Starts the text editor.</span></span> <span data-ttu-id="db831-526">이 편집기를 사용하여 현재 [!INCLUDE[tsql](../includes/tsql-md.md)] 일괄 처리를 편집하거나 마지막으로 실행된 일괄 처리를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-526">This editor can be used to edit the current [!INCLUDE[tsql](../includes/tsql-md.md)] batch, or the last executed batch.</span></span> <span data-ttu-id="db831-527">마지막으로 실행된 일괄 처리를 편집하려면 마지막 일괄 처리 실행을 마친 후 즉시 **ED** 명령을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-527">To edit the last executed batch, the **ED** command must be typed immediately after the last batch has completed execution.</span></span>  
  
 <span data-ttu-id="db831-528">텍스트 편집기는 SQLCMDEDITOR 환경 변수에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-528">The text editor is defined by the SQLCMDEDITOR environment variable.</span></span> <span data-ttu-id="db831-529">기본 편집기는 'Edit'입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-529">The default editor is 'Edit'.</span></span> <span data-ttu-id="db831-530">편집기를 변경하려면 SQLCMDEDITOR 환경 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-530">To change the editor, set the SQLCMDEDITOR environment variable.</span></span> <span data-ttu-id="db831-531">예를 들어 편집기를 [!INCLUDE[msCoName](../includes/msconame-md.md)] 메모장으로 설정하려면 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-531">For example, to set the editor to [!INCLUDE[msCoName](../includes/msconame-md.md)] Notepad, at the command prompt, type:</span></span>  
  
 `SET SQLCMDEDITOR=notepad`  
  
 <span data-ttu-id="db831-532">[ **:** ] **RESET**</span><span class="sxs-lookup"><span data-stu-id="db831-532">[**:**] **RESET**</span></span>  
 <span data-ttu-id="db831-533">문 캐시를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="db831-533">Clears the statement cache.</span></span>  
  
 <span data-ttu-id="db831-534">**:List**</span><span class="sxs-lookup"><span data-stu-id="db831-534">**:List**</span></span>  
 <span data-ttu-id="db831-535">문 캐시 내용을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-535">Prints the content of the statement cache.</span></span>  
  
 <span data-ttu-id="db831-536">**변수**</span><span class="sxs-lookup"><span data-stu-id="db831-536">**Variables**</span></span>  
  <span data-ttu-id="db831-537">**: Setvar** \<**var**> [ **"*`value`*"** ]</span><span class="sxs-lookup"><span data-stu-id="db831-537">**:Setvar** \<**var**> [ **"*`value`*"** ]</span></span>  
 <span data-ttu-id="db831-538">`sqlcmd` 스크립팅 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-538">Defines `sqlcmd` scripting variables.</span></span> <span data-ttu-id="db831-539">스크립팅 변수의 형식은 다음과 같습니다. `$(VARNAME)`.</span><span class="sxs-lookup"><span data-stu-id="db831-539">Scripting variables have the following format: `$(VARNAME)`.</span></span>  
  
 <span data-ttu-id="db831-540">변수 이름은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-540">Variable names are case insensitive.</span></span>  
  
 <span data-ttu-id="db831-541">스크립팅 변수는 다음과 같은 방법으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-541">Scripting variables can be set in the following ways:</span></span>  
  
-   <span data-ttu-id="db831-542">명령줄 옵션을 사용하여 암시적으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-542">Implicitly using a command-line option.</span></span> <span data-ttu-id="db831-543">예를 들어 **-l** 옵션은 SQLCMDLOGINTIMEOUT 변수를 설정 합니다 `sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="db831-543">For example, the **-l** option sets the SQLCMDLOGINTIMEOUT `sqlcmd` variable.</span></span>  
  
-   <span data-ttu-id="db831-544">**:Setvar** 명령을 사용하여 명시적으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-544">Explicitly by using the **:Setvar** command.</span></span>  
  
-   <span data-ttu-id="db831-545">`sqlcmd`를 실행하기 전에 환경 변수를 정의하여 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-545">By defining an environment variable before you run `sqlcmd`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-546">`-X` 옵션은 환경 변수가 `sqlcmd`에 전달되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-546">The `-X` option prevents environment variables from being passed on to `sqlcmd`.</span></span>  
  
 <span data-ttu-id="db831-547">**:Setvar** 명령을 사용하여 정의한 변수와 환경 변수의 이름이 같을 경우 **:Setvar** 명령을 사용하여 정의한 변수가 우선적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-547">If a variable defined by using **:Setvar** and an environment variable have the same name, the variable defined by using **:Setvar** takes precedence.</span></span>  
  
 <span data-ttu-id="db831-548">변수 이름에는 공백 문자를 포함해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-548">Variable names must not contain blank space characters.</span></span>  
  
 <span data-ttu-id="db831-549">변수 이름은 $(var) 등의 변수 식과 다른 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-549">Variable names cannot have the same form as a variable expression, such as $(var).</span></span>  
  
 <span data-ttu-id="db831-550">스크립팅 변수의 문자열 값에 공백이 포함된 경우 값을 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-550">If the string value of the scripting variable contains blank spaces, enclose the value in quotation marks.</span></span> <span data-ttu-id="db831-551">스크립팅 변수 값을 지정하지 않으면 스크립팅 변수가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-551">If a value for a scripting variable is not specified, the scripting variable is dropped.</span></span>  
  
 <span data-ttu-id="db831-552">**:Listvar**</span><span class="sxs-lookup"><span data-stu-id="db831-552">**:Listvar**</span></span>  
 <span data-ttu-id="db831-553">현재 설정되어 있는 스크립팅 변수의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-553">Displays a list of the scripting variables that are currently set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-554">로 설정 된 스크립팅 변수와 `sqlcmd` **: Setvar** 명령을 사용 하 여 설정한 스크립팅 변수만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-554">Only scripting variables that are set by `sqlcmd`, and those that are set using the **:Setvar** command will be displayed.</span></span>  
  
 <span data-ttu-id="db831-555">**출력 명령**</span><span class="sxs-lookup"><span data-stu-id="db831-555">**Output Commands**</span></span>  
  <span data-ttu-id="db831-556">**:Error** </span><span class="sxs-lookup"><span data-stu-id="db831-556">**:Error** </span></span>  
 <span data-ttu-id="db831-557">**_\<_** _filename_  **_>|_ STDERR | STDOUT**</span><span class="sxs-lookup"><span data-stu-id="db831-557">**_\<_** _filename_  **_>|_ STDERR|STDOUT**</span></span>  
 <span data-ttu-id="db831-558">*file name*에 지정된 파일, **stderr** 또는 **stdout**으로 모든 오류 출력을 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-558">Redirect all error output to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="db831-559">스크립트에서 **Error** 명령이 여러 번 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-559">The **Error** command can appear multiple times in a script.</span></span> <span data-ttu-id="db831-560">기본적으로 오류 출력은 **stderr**로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-560">By default, error output is sent to **stderr**.</span></span>  
  
 <span data-ttu-id="db831-561">*file name*</span><span class="sxs-lookup"><span data-stu-id="db831-561">*file name*</span></span>  
 <span data-ttu-id="db831-562">출력을 받을 파일을 만들고 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db831-562">Creates and opens a file that will receive the output.</span></span> <span data-ttu-id="db831-563">이 파일이 이미 있을 경우 0바이트로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="db831-563">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="db831-564">권한이나 기타 이유로 인해 이 파일을 사용할 수 없을 경우 출력이 전환되지 않으며 마지막으로 지정한 대상이나 기본 대상으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-564">If the file is not available because of permissions or other reasons, the output will not be switched and will be sent to the last specified or default destination.</span></span>  
  
 <span data-ttu-id="db831-565">**STDERR**</span><span class="sxs-lookup"><span data-stu-id="db831-565">**STDERR**</span></span>  
 <span data-ttu-id="db831-566">오류 출력을 **stderr** 스트림으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-566">Switches error output to the **stderr** stream.</span></span> <span data-ttu-id="db831-567">스트림을 리디렉션할 경우 리디렉션된 스트림 대상이 오류 출력을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-567">If this has been redirected, the target to which the stream has been redirected will receive the error output.</span></span>  
  
 <span data-ttu-id="db831-568">**STDOUT**</span><span class="sxs-lookup"><span data-stu-id="db831-568">**STDOUT**</span></span>  
 <span data-ttu-id="db831-569">오류 출력을 **stdout** 스트림으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-569">Switches error output to the **stdout** stream.</span></span> <span data-ttu-id="db831-570">스트림을 리디렉션할 경우 리디렉션된 스트림 대상이 오류 출력을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-570">If this has been redirected, the target to which the stream has been redirected will receive the error output.</span></span>  
  
 <span data-ttu-id="db831-571">\*\*: Out \<** _filename_ **> \*\* |  **STDERR** |  **STDOUT**</span><span class="sxs-lookup"><span data-stu-id="db831-571">**:Out \<** _filename_ **>**| **STDERR**| **STDOUT**</span></span>  
 <span data-ttu-id="db831-572">쿼리 결과를 만들어 *file name*에 지정된 파일, **stderr** 또는 **stdout**으로 모두 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-572">Creates and redirects all query results to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="db831-573">기본적으로 출력은 **stdout**으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-573">By default, output is sent to **stdout**.</span></span> <span data-ttu-id="db831-574">이 파일이 이미 있을 경우 0바이트로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="db831-574">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="db831-575">스크립트에서 **Out** 명령이 여러 번 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-575">The **Out** command can appear multiple times in a script.</span></span>  
  
 <span data-ttu-id="db831-576">\*\*:P erftrace \<** _filename_ **> \*\* |  **STDERR** |  **STDOUT**</span><span class="sxs-lookup"><span data-stu-id="db831-576">**:Perftrace \<** _filename_ **>**| **STDERR**| **STDOUT**</span></span>  
 <span data-ttu-id="db831-577">성능 추적 정보를 만들어 *file name*에 지정된 파일, **stderr** 또는 **stdout**으로 모두 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-577">Creates and redirects all performance trace information to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="db831-578">기본적으로 성능 추적 출력은 **stdout**으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-578">By default performance trace output is sent to **stdout**.</span></span> <span data-ttu-id="db831-579">이 파일이 이미 있을 경우 0바이트로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="db831-579">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="db831-580">스크립트에서 **Perftrace** 명령이 여러 번 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-580">The **Perftrace** command can appear multiple times in a script.</span></span>  
  
 <span data-ttu-id="db831-581">**실행 제어 명령**</span><span class="sxs-lookup"><span data-stu-id="db831-581">**Execution Control Commands**</span></span>  
  <span data-ttu-id="db831-582">**: On Error**[ `exit`  |  `ignore` ]</span><span class="sxs-lookup"><span data-stu-id="db831-582">**:On Error**[ `exit` | `ignore`]</span></span>  
 <span data-ttu-id="db831-583">스크립트나 일괄 처리를 실행하는 동안 오류가 발생할 때 수행할 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-583">Sets the action to be performed when an error occurs during script or batch execution.</span></span>  
  
 <span data-ttu-id="db831-584">`exit` 옵션을 사용하면 해당 오류 값이 표시되고 `sqlcmd`가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-584">When the `exit` option is used, `sqlcmd` exits with the appropriate error value.</span></span>  
  
 <span data-ttu-id="db831-585">`ignore` 옵션을 사용하면 `sqlcmd`는 오류를 무시하고 일괄 처리 또는 스크립트를 계속 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-585">When the `ignore` option is used, `sqlcmd` ignores the error and continues executing the batch or script.</span></span> <span data-ttu-id="db831-586">기본적으로 오류 메시지가 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-586">By default, an error message will be printed.</span></span>  
  
 <span data-ttu-id="db831-587">[ **:** ] **QUIT**</span><span class="sxs-lookup"><span data-stu-id="db831-587">[**:**] **QUIT**</span></span>  
 <span data-ttu-id="db831-588">`sqlcmd`를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="db831-588">Causes `sqlcmd` to exit.</span></span>  
  
 <span data-ttu-id="db831-589">[**:**] **EXIT**[ **( *`statement`* )** ]</span><span class="sxs-lookup"><span data-stu-id="db831-589">[**:**] **EXIT**[ **(*`statement`*)** ]</span></span>  
 <span data-ttu-id="db831-590">`sqlcmd`의 반환 값에 SELECT 문의 결과를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-590">Lets you use the result of a SELECT statement as the return value from `sqlcmd`.</span></span> <span data-ttu-id="db831-591">숫자일 경우 마지막 결과 행의 첫째 열은 4바이트 정수(long)로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-591">If numeric, the first column of the last result row is converted to a 4-byte integer (long).</span></span> <span data-ttu-id="db831-592">MS-DOS는 하위 바이트를 부모 프로세스 또는 운영 체제 오류 수준에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-592">MS-DOS passes the low byte to the parent process or operating system error level.</span></span> <span data-ttu-id="db831-593">Windows 200x에서는 4바이트 정수 전체를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-593">Windows 200x passes the whole 4-byte integer.</span></span> <span data-ttu-id="db831-594">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-594">The syntax is:</span></span>  
  
 `:EXIT(query)`  
  
 <span data-ttu-id="db831-595">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-595">For example:</span></span>  
  
 `:EXIT(SELECT @@ROWCOUNT)`  
  
 <span data-ttu-id="db831-596">**EXIT** 매개 변수를 배치 파일의 일부로 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-596">You can also include the **EXIT** parameter as part of a batch file.</span></span> <span data-ttu-id="db831-597">예를 들어 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-597">For example, at the command prompt, type:</span></span>  
  
 `sqlcmd -Q "EXIT(SELECT COUNT(*) FROM '%1')"`  
  
 <span data-ttu-id="db831-598">`sqlcmd`유틸리티는 괄호 **()** 사이에 있는 모든 항목을 서버로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="db831-598">The `sqlcmd` utility sends everything between the parentheses **()** to the server.</span></span> <span data-ttu-id="db831-599">시스템의 저장 프로시저가 설정을 선택하고 값을 반환하면 선택 내용만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-599">If a system stored procedure selects a set and returns a value, only the selection is returned.</span></span> <span data-ttu-id="db831-600">괄호 사이에 아무것도 없는 EXIT **()** 문은 일괄 처리에서 이 문 앞에 나오는 모든 문을 실행한 후에 반환 값 없이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-600">The EXIT **()** statement with nothing between the parentheses executes everything before it in the batch and then exits without a return value.</span></span>  
  
 <span data-ttu-id="db831-601">잘못된 쿼리를 지정하면 `sqlcmd`는 값을 반환하지 않고 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-601">When an incorrect query is specified, `sqlcmd` will exit without a return value.</span></span>  
  
 <span data-ttu-id="db831-602">다음은 EXIT 형식의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-602">Here is a list of EXIT formats:</span></span>  
  
-   <span data-ttu-id="db831-603">:EXIT</span><span class="sxs-lookup"><span data-stu-id="db831-603">:EXIT</span></span>  
  
 <span data-ttu-id="db831-604">일괄 처리를 실행하지 않고 즉시 종료하며 값을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-604">Does not execute the batch, and then quits immediately and returns no value.</span></span>  
  
-   <span data-ttu-id="db831-605">:EXIT( )</span><span class="sxs-lookup"><span data-stu-id="db831-605">:EXIT( )</span></span>  
  
 <span data-ttu-id="db831-606">일괄 처리를 실행한 다음 종료하며 값을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-606">Executes the batch, and then quits and returns no value.</span></span>  
  
-   <span data-ttu-id="db831-607">:EXIT(query)</span><span class="sxs-lookup"><span data-stu-id="db831-607">:EXIT(query)</span></span>  
  
 <span data-ttu-id="db831-608">쿼리를 포함하는 일괄 처리를 실행하며 쿼리 결과를 반환한 다음 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-608">Executes the batch that includes the query, and then quits after it returns the results of the query.</span></span>  
  
 <span data-ttu-id="db831-609">`sqlcmd` 스크립트에 RAISERROR를 사용할 때 상태 127이 발생하면 `sqlcmd`가 종료되고 메시지 ID가 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-609">If RAISERROR is used within a `sqlcmd` script and a state of 127 is raised, `sqlcmd` will quit and return the message ID back to the client.</span></span> <span data-ttu-id="db831-610">예:</span><span class="sxs-lookup"><span data-stu-id="db831-610">For example:</span></span>  
  
 `RAISERROR(50001, 10, 127)`  
  
 <span data-ttu-id="db831-611">이 오류가 발생하면 `sqlcmd` 스크립트가 종료되고 메시지 ID 50001이 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-611">This error will cause the `sqlcmd` script to end and return the message ID 50001 to the client.</span></span>  
  
 <span data-ttu-id="db831-612">1부터 -99까지의 반환 값은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 예약되어 있으므로 `sqlcmd`는 다음과 같은 추가 반환 값을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-612">The return values -1 to -99 are reserved by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]; `sqlcmd` defines the following additional return values:</span></span>  
  
|<span data-ttu-id="db831-613">반환 값</span><span class="sxs-lookup"><span data-stu-id="db831-613">Return Values</span></span>|<span data-ttu-id="db831-614">Description</span><span class="sxs-lookup"><span data-stu-id="db831-614">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="db831-615">-100</span><span class="sxs-lookup"><span data-stu-id="db831-615">-100</span></span>|<span data-ttu-id="db831-616">반환 값을 선택하기 전에 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-616">Error encountered prior to selecting return value.</span></span>|  
|<span data-ttu-id="db831-617">-101</span><span class="sxs-lookup"><span data-stu-id="db831-617">-101</span></span>|<span data-ttu-id="db831-618">반환 값을 선택할 때 행을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-618">No rows found when selecting return value.</span></span>|  
|<span data-ttu-id="db831-619">-102</span><span class="sxs-lookup"><span data-stu-id="db831-619">-102</span></span>|<span data-ttu-id="db831-620">반환 값을 선택할 때 변환 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-620">Conversion error occurred when selecting return value.</span></span>|  
  
 <span data-ttu-id="db831-621">**GO** [*count*]</span><span class="sxs-lookup"><span data-stu-id="db831-621">**GO** [*count*]</span></span>  
 <span data-ttu-id="db831-622">GO는 일괄 처리의 끝을 알려 주고 캐시된 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 실행하도록 신호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="db831-622">GO signals both the end of a batch and the execution of any cached [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="db831-623">*count*값을 지정하면 캐시된 문이 *count* 에 지정한 횟수만큼 단일 일괄 처리로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-623">When specifying a value for *count*, the cached statements will be executed *count* times, as a single batch.</span></span>  
  
 <span data-ttu-id="db831-624">**기타 명령**</span><span class="sxs-lookup"><span data-stu-id="db831-624">**Miscellaneous Commands**</span></span>  
  <span data-ttu-id="db831-625">**: r\<** _filename_ **>**</span><span class="sxs-lookup"><span data-stu-id="db831-625">**:r \<** _filename_ **>**</span></span>  
 <span data-ttu-id="db831-626">에 [!INCLUDE[tsql](../includes/tsql-md.md)] `sqlcmd` 지정 된 파일에서 추가 문과 명령을 문 캐시로 구문 분석 **<*`filename`*>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-626">Parses additional [!INCLUDE[tsql](../includes/tsql-md.md)] statements and `sqlcmd` commands from the file specified by **<*`filename`*>** into the statement cache.</span></span>  
  
 <span data-ttu-id="db831-627">파일에 [!INCLUDE[tsql](../includes/tsql-md.md)] 문이 포함되어 있고 뒤에 **GO**가 오지 않을 경우 **:r** 뒤에 오는 줄에 **GO**를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-627">If the file contains [!INCLUDE[tsql](../includes/tsql-md.md)] statements that are not followed by **GO**, you must enter **GO** on the line that follows **:r**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-628">**\<** _filename_ **>** 는가 실행 된 시작 디렉터리를 기준으로 읽습니다 `sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="db831-628">**\<** _filename_ **>** is read relative to the startup directory in which `sqlcmd` was run.</span></span>  
  
 <span data-ttu-id="db831-629">일괄 처리 종결자가 나타난 후 이 파일이 읽혀지고 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-629">The file will be read and executed after a batch terminator is encountered.</span></span> <span data-ttu-id="db831-630">여러 **:r** 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-630">You can issue multiple **:r** commands.</span></span> <span data-ttu-id="db831-631">이 파일에는 모든 유형의 `sqlcmd` 명령이 포함될 수 있으며</span><span class="sxs-lookup"><span data-stu-id="db831-631">The file may include any `sqlcmd` command.</span></span> <span data-ttu-id="db831-632">그 예로 일괄 처리 종결자 **GO**를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-632">This includes the batch terminator **GO**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-633">대화형 모드에서 표시되는 줄 수는 **:r** 명령이 나타날 때마다 1씩 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-633">The line count that is displayed in interactive mode will be increased by one for every **:r** command encountered.</span></span> <span data-ttu-id="db831-634">**:r** 명령은 목록 명령의 출력에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="db831-634">The **:r** command will appear in the output of the list command.</span></span>  
  
 <span data-ttu-id="db831-635">**:Serverlist**</span><span class="sxs-lookup"><span data-stu-id="db831-635">**:Serverlist**</span></span>  
 <span data-ttu-id="db831-636">로컬로 구성된 서버와 네트워크상에서 브로드캐스팅하는 서버의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-636">Lists the locally configured servers and the names of the servers broadcasting on the network.</span></span>  
  
 <span data-ttu-id="db831-637">**: Connect** _server_name_[ **\\** _instance_name_] [-l *timeout*] [-U *user_name* [-P *password*]]</span><span class="sxs-lookup"><span data-stu-id="db831-637">**:Connect** _server_name_[**\\**_instance_name_] [-l *timeout*] [-U *user_name* [-P *password*]]</span></span>  
 <span data-ttu-id="db831-638">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-638">Connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="db831-639">또한 현재 연결을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-639">Also closes the current connection.</span></span>  
  
 <span data-ttu-id="db831-640">제한 시간 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-640">Time-out options:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db831-641">0</span><span class="sxs-lookup"><span data-stu-id="db831-641">0</span></span>|<span data-ttu-id="db831-642">무기한 대기</span><span class="sxs-lookup"><span data-stu-id="db831-642">wait forever</span></span>|  
|<span data-ttu-id="db831-643">n>0</span><span class="sxs-lookup"><span data-stu-id="db831-643">n>0</span></span>|<span data-ttu-id="db831-644">n초 동안 대기</span><span class="sxs-lookup"><span data-stu-id="db831-644">wait for n seconds</span></span>|  
  
 <span data-ttu-id="db831-645">SQLCMDSERVER 스크립팅 변수는 현재 활성 연결을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-645">The SQLCMDSERVER scripting variable will reflect the current active connection.</span></span>  
  
 <span data-ttu-id="db831-646">*timeout* 을 지정하지 않으면 기본적으로 SQLCMDLOGINTIMEOUT 변수 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-646">If *timeout* is not specified, the value of the SQLCMDLOGINTIMEOUT variable is the default.</span></span>  
  
 <span data-ttu-id="db831-647">옵션이나 환경 변수로 *user_name* 만 지정하면 사용자에게 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-647">If only *user_name* is specified (either as an option, or as an environment variable), the user will be prompted to enter a password.</span></span> <span data-ttu-id="db831-648">이는 SQLCMDUSER 또는 SQLCMDPASSWORD 환경 변수를 설정한 경우 해당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-648">This is not true if the SQLCMDUSER or SQLCMDPASSWORD environment variables have been set.</span></span> <span data-ttu-id="db831-649">옵션이나 환경 변수를 지정하지 않을 경우 로그인하는 데 Windows 인증 모드가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-649">If neither options nor environment variables are provided, Windows Authentication mode is used to login.</span></span> <span data-ttu-id="db831-650">예를 들어 통합 보안을 사용하여 `instance1`[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 인스턴스인 `myserver`에 연결하려면 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-650">For example to connect to an instance, `instance1`, of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], `myserver`, by using integrated security you would use the following:</span></span>  
  
 `:connect myserver\instance1`  
  
 <span data-ttu-id="db831-651">스크립팅 변수를 사용하여 `myserver` 의 기본 인스턴스에 연결하려면 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-651">To connect to the default instance of `myserver` using scripting variables, you would use the following:</span></span>  
  
 `:setvar myusername test`  
  
 `:setvar myservername myserver`  
  
 `:connect $(myservername) $(myusername)`  
  
 <span data-ttu-id="db831-652">[**:**] **!!**\< *command*></span><span class="sxs-lookup"><span data-stu-id="db831-652">[**:**] **!!**\< *command*></span></span>  
 <span data-ttu-id="db831-653">운영 체제 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-653">Executes operating system commands.</span></span> <span data-ttu-id="db831-654">운영 체제 명령을 실행하려면 느낌표 두 개( **!!** )로 줄을 시작하고 운영 체제 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-654">To execute an operating system command, start a line with two exclamation marks (**!!**) followed by the operating system command.</span></span> <span data-ttu-id="db831-655">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-655">For example:</span></span>  
  
 `:!! Dir`  
  
> [!NOTE]  
>  <span data-ttu-id="db831-656">`sqlcmd`를 실행 중인 컴퓨터에서 명령이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-656">The command is executed on the computer on which `sqlcmd` is running.</span></span>  
  
 <span data-ttu-id="db831-657">**:XML** [**ON** | **OFF**]</span><span class="sxs-lookup"><span data-stu-id="db831-657">**:XML** [**ON** | **OFF**]</span></span>  
 <span data-ttu-id="db831-658">자세한 내용은 이 항목의 뒷부분에 나오는 "XML 출력 형식"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="db831-658">For more information, see "XML Output Format," later in this topic</span></span>  
  
 <span data-ttu-id="db831-659">**:Help**</span><span class="sxs-lookup"><span data-stu-id="db831-659">**:Help**</span></span>  
 <span data-ttu-id="db831-660">`sqlcmd` 명령과 각 명령에 대한 간단한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-660">Lists `sqlcmd` commands together with a short description of each command.</span></span>  
  
### <a name="sqlcmd-file-names"></a><span data-ttu-id="db831-661">sqlcmd 파일 이름</span><span class="sxs-lookup"><span data-stu-id="db831-661">sqlcmd File Names</span></span>  
 <span data-ttu-id="db831-662">`sqlcmd`입력 파일은 **-i** 옵션 또는 **: r** 명령을 사용 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-662">`sqlcmd` input files can be specified with the **-i** option or the **:r** command.</span></span> <span data-ttu-id="db831-663">출력 파일은 **-o** 옵션 또는 **:Error**, **:Out** 및 **:Perftrace** 명령을 사용하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-663">Output files can be specified with the **-o** option or the **:Error**, **:Out** and **:Perftrace** commands.</span></span> <span data-ttu-id="db831-664">다음은 이러한 파일 작업에 대한 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-664">The following are some guidelines for working with these files:</span></span>  
  
-   <span data-ttu-id="db831-665">**: Error**, **: Out** 및 **:P erftrace** 는 별도를 사용 해야 합니다 **<*`filename`*>** .</span><span class="sxs-lookup"><span data-stu-id="db831-665">**:Error**, **:Out** and **:Perftrace** should use separate **<*`filename`*>**.</span></span> <span data-ttu-id="db831-666">동일한를 **<*`filename`*>** 사용 하는 경우 명령의 입력이 혼합 되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-666">If the same **<*`filename`*>** is used, inputs from the commands may be intermixed.</span></span>  
  
-   <span data-ttu-id="db831-667">원격 서버에 있는 입력 파일을 로컬 컴퓨터에 있는 `sqlcmd`에서 호출할 경우 이 파일에 :out c:\OutputFile.txt와 같은 드라이브 파일 경로가 포함되어 있으면</span><span class="sxs-lookup"><span data-stu-id="db831-667">If an input file that is located on a remote server is called from `sqlcmd` on a local computer and the file contains a drive file path such as :out c:\OutputFile.txt.</span></span> <span data-ttu-id="db831-668">출력 파일이 원격 서버가 아닌 로컬 컴퓨터에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-668">The output file will be created on the local computer and not on the remote server.</span></span>  
  
-   <span data-ttu-id="db831-669">유효한 파일 경로에는 C: \\ **<*`filename`*>** , \\ \\<Server \> \\<Share $>\\ **<*`filename`*>** 및 "c:\ccfolder \\ **<*`file name`*>** "가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-669">Valid file paths include: C:\\**<*`filename`*>**, \\\\<Server\>\\<Share$>\\**<*`filename`*>** and "C:\Some Folder\\**<*`file name`*>**".</span></span> <span data-ttu-id="db831-670">경로에 공백이 있을 경우 따옴표를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-670">If there is a space in the path, use quotation marks.</span></span>  
  
-   <span data-ttu-id="db831-671">각각의 새 `sqlcmd` 세션은 이름이 같은 기존 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="db831-671">Each new `sqlcmd` session will overwrite existing files that have the same names.</span></span>  
  
### <a name="informational-messages"></a><span data-ttu-id="db831-672">정보 메시지</span><span class="sxs-lookup"><span data-stu-id="db831-672">Informational Messages</span></span>  
 <span data-ttu-id="db831-673">`sqlcmd`는 서버에서 보낸 모든 정보 메시지를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-673">`sqlcmd` prints any informational message that are sent by the server.</span></span> <span data-ttu-id="db831-674">다음 예에서는 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 실행한 후 정보 메시지가 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-674">In the following example, after the [!INCLUDE[tsql](../includes/tsql-md.md)] statements are executed, an informational message is printed.</span></span>  
  
 <span data-ttu-id="db831-675">명령 프롬프트에 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-675">At the command prompt, type the following:</span></span>  
  
 `sqlcmd`  
  
 `At the sqlcmd prompt type:`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 <span data-ttu-id="db831-676">Enter 키를 누르면 다음 정보 메시지가 출력됩니다. "Changed database context to 'AdventureWorks2012'."</span><span class="sxs-lookup"><span data-stu-id="db831-676">When you press ENTER, the following informational message is printed: "Changed database context to 'AdventureWorks2012'."</span></span>  
  
### <a name="output-format-from-transact-sql-queries"></a><span data-ttu-id="db831-677">Transact-SQL 쿼리의 출력 형식</span><span class="sxs-lookup"><span data-stu-id="db831-677">Output Format from Transact-SQL Queries</span></span>  
 <span data-ttu-id="db831-678">먼저 `sqlcmd`는 SELECT 목록에서 지정한 열 이름이 포함된 열 머리글을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-678">`sqlcmd` first prints a column header that contains the column names specified in the select list.</span></span> <span data-ttu-id="db831-679">열 이름은 SQLCMDCOLSEP 문자로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-679">The column names are separated by using the SQLCMDCOLSEP character.</span></span> <span data-ttu-id="db831-680">기본적으로 구분 문자는 공백입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-680">By default, this is a space.</span></span> <span data-ttu-id="db831-681">열 이름이 열 너비보다 짧은 경우 출력은 다음 열까지 공백으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="db831-681">If the column name is shorter than the column width, the output is padded with spaces up to the next column.</span></span>  
  
 <span data-ttu-id="db831-682">이 줄 다음에는 대시 문자로 이루어진 구분선이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-682">This line will be followed by a separator line that is a series of dash characters.</span></span> <span data-ttu-id="db831-683">다음은 출력의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-683">The following output shows an example.</span></span>  
  
 <span data-ttu-id="db831-684">`sqlcmd`를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-684">Start `sqlcmd`.</span></span> <span data-ttu-id="db831-685">`sqlcmd` 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-685">At the `sqlcmd` command prompt, type the following:</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `SELECT TOP (2) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 <span data-ttu-id="db831-686">Enter 키를 누르면 다음 결과 집합이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-686">When you press ENTER, the following result set is returned.</span></span>  
  
 `BusinessEntityID FirstName    LastName`  
  
 `---------------- ------------ ----------`  
  
 `285              Syed         Abbas`  
  
 `293              Catherine    Abel`  
  
 `(2 row(s) affected)`  
  
 <span data-ttu-id="db831-687">`BusinessEntityID` 열의 너비는 4자이지만 보다 긴 열 이름을 포함할 수 있도록 확장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-687">Although the `BusinessEntityID` column is only 4 characters wide, it has been expanded to accommodate the longer column name.</span></span> <span data-ttu-id="db831-688">기본적으로 출력은 80자에서 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="db831-688">By default, output is terminated at 80 characters.</span></span> <span data-ttu-id="db831-689">그러나 **-w** 옵션을 사용하거나 SQLCMDCOLWIDTH 스크립팅 변수를 설정하여 이 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-689">This can be changed by using the **-w** option, or by setting the SQLCMDCOLWIDTH scripting variable.</span></span>  
  
### <a name="xml-output-format"></a><span data-ttu-id="db831-690">XML 출력 형식</span><span class="sxs-lookup"><span data-stu-id="db831-690">XML Output Format</span></span>  
 <span data-ttu-id="db831-691">FOR XML 절의 결과로 나오는 XML 출력은 연속 스트림에서 형식이 지정되지 않은 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="db831-691">XML output that is the result of a FOR XML clause is output, unformatted, in a continuous stream.</span></span>  
  
 <span data-ttu-id="db831-692">XML 출력을 원하는 경우에는 `:XML ON`명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-692">When you expect XML output, use the following command: `:XML ON`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-693">`sqlcmd`는 일반 형식으로 오류 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-693">`sqlcmd` returns error messages in the usual format.</span></span> <span data-ttu-id="db831-694">오류 메시지는 XML 형식으로 XML 텍스트 스트림에도 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-694">Notice that the error messages are also output in the XML text stream in XML format.</span></span> <span data-ttu-id="db831-695">`:XML ON`을 사용할 경우 `sqlcmd`에서는 정보 메시지를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-695">By using `:XML ON`, `sqlcmd` does not display informational messages.</span></span>  
  
 <span data-ttu-id="db831-696">XML 모드를 해제하려면 `:XML OFF`명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-696">To set the XML mode off, use the following command: `:XML OFF`.</span></span>  
  
 <span data-ttu-id="db831-697">XML OFF 명령은 `sqlcmd`를 다시 행 기반 출력으로 전환하기 때문에 GO 명령이 나타난 다음에 XML OFF 명령을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-697">The GO command should not appear before the XML OFF command is issued because the XML OFF command switches `sqlcmd` back to row-oriented output.</span></span>  
  
 <span data-ttu-id="db831-698">스트리밍된 XML 데이터와 행 집합 데이터를 혼합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-698">XML (streamed) data and rowset data cannot be mixed.</span></span> <span data-ttu-id="db831-699">XML 스트림을 출력하는 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 실행하기 전에 XML ON 명령을 실행하지 않은 경우 출력이 잘못됩니다.</span><span class="sxs-lookup"><span data-stu-id="db831-699">If the XML ON command has not been issued before a [!INCLUDE[tsql](../includes/tsql-md.md)] statement that outputs XML streams is executed, the output will be garbled.</span></span> <span data-ttu-id="db831-700">XML ON 명령을 실행한 경우 일반 행 집합을 출력하는 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-700">If the XML ON command has been issued, you cannot execute [!INCLUDE[tsql](../includes/tsql-md.md)] statements that output regular row sets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db831-701">**:XML** 명령은 SET STATISTICS XML 문을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db831-701">The **:XML** command does not support the SET STATISTICS XML statement.</span></span>  
  
## <a name="sqlcmd-best-practices"></a><span data-ttu-id="db831-702">sqlcmd를 위한 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="db831-702">sqlcmd Best Practices</span></span>  
 <span data-ttu-id="db831-703">보안 및 효율성을 극대화하려면 다음 방법을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="db831-703">Use the following practices to help maximize security and efficiency.</span></span>  
  
-   <span data-ttu-id="db831-704">통합 보안을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-704">Use integrated security.</span></span>  
  
-   <span data-ttu-id="db831-705">자동화된 환경에서 `-X`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-705">Use `-X` in automated environments.</span></span>  
  
-   <span data-ttu-id="db831-706">적절한 NTFS 파일 시스템 권한을 사용하여 입력 및 출력 파일을 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-706">Secure input and output files by using appropriate NTFS file system permissions.</span></span>  
  
-   <span data-ttu-id="db831-707">성능을 향상시키려면 여러 세션 대신 한 번의 `sqlcmd` 세션에서 가능한 한 많은 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-707">To increase performance, do as much in one `sqlcmd` session as you can, instead of in a series of sessions.</span></span>  
  
-   <span data-ttu-id="db831-708">일괄 처리 또는 쿼리를 실행하는 데 걸리는 예상 시간보다 높은 제한 시간 값을 일괄 처리 또는 쿼리 실행에 대해 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db831-708">Set time-out values for batch or query execution higher than you expect it will take to execute the batch or query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db831-709">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db831-709">See Also</span></span>  
 <span data-ttu-id="db831-710">[sqlcmd 유틸리티 시작](../relational-databases/scripting/sqlcmd-start-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="db831-710">[Start the sqlcmd Utility](../relational-databases/scripting/sqlcmd-start-the-utility.md) </span></span>  
 <span data-ttu-id="db831-711">[sqlcmd를 사용하여 Transact-SQL 스크립트 파일 실행](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md) </span><span class="sxs-lookup"><span data-stu-id="db831-711">[Run Transact-SQL Script Files Using sqlcmd](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md) </span></span>  
 <span data-ttu-id="db831-712">[sqlcmd 유틸리티 사용](../relational-databases/scripting/sqlcmd-use-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="db831-712">[Use the sqlcmd Utility](../relational-databases/scripting/sqlcmd-use-the-utility.md) </span></span>  
 <span data-ttu-id="db831-713">[스크립팅 변수와 함께 sqlcmd 사용](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="db831-713">[Use sqlcmd with Scripting Variables](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md) </span></span>  
 <span data-ttu-id="db831-714">[sqlcmd를 사용하여 데이터베이스 엔진에 연결](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="db831-714">[Connect to the Database Engine With sqlcmd](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="db831-715">[쿼리 편집기로 SQLCMD 스크립트 편집](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md) </span><span class="sxs-lookup"><span data-stu-id="db831-715">[Edit SQLCMD Scripts with Query Editor](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md) </span></span>  
 <span data-ttu-id="db831-716">[작업 단계 관리](../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="db831-716">[Manage Job Steps](../ssms/agent/manage-job-steps.md) </span></span>  
 [<span data-ttu-id="db831-717">CmdExec 작업 단계 만들기</span><span class="sxs-lookup"><span data-stu-id="db831-717">Create a CmdExec Job Step</span></span>](../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
