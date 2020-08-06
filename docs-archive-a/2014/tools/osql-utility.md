---
title: osql 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- operating systems [SQL Server], commands
- osql utility [SQL Server]
- stored procedures [SQL Server], command prompt
- scripts [SQL Server], command prompt
- RESET command
- GO command
- command prompt utilities [SQL Server], osql
- CTRL+C command
ms.assetid: cf530d9e-0609-4528-8975-ab8e08e40b9a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 95782afe0de8567781316e3478d04a090f968ed5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727616"
---
# <a name="osql-utility"></a><span data-ttu-id="98d39-102">osql 유틸리티</span><span class="sxs-lookup"><span data-stu-id="98d39-102">osql Utility</span></span>
  <span data-ttu-id="98d39-103">**osql** 유틸리티를 사용하여 [!INCLUDE[tsql](../includes/tsql-md.md)] 문, 시스템 프로시저 및 스크립트 파일을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-103">The **osql** utility allows you to enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements, system procedures, and script files.</span></span> <span data-ttu-id="98d39-104">이 유틸리티에서는 ODBC를 사용하여 서버와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-104">This utility uses ODBC to communicate with the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="98d39-105">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 이후 버전에서는 이 기능이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-105">This feature will be removed in a future version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="98d39-106">향후 개발 작업에서는 이 기능을 사용하지 않도록 하고 현재 이 기능을 사용하는 애플리케이션은 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="98d39-106">Avoid using this feature in new development work, and plan to modify applications that currently use the feature.</span></span> <span data-ttu-id="98d39-107">대신 **sqlcmd** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-107">Use **sqlcmd** instead.</span></span> <span data-ttu-id="98d39-108">자세한 내용은 [sqlcmd Utility](sqlcmd-utility.md)을(를) 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="98d39-108">For more information, see [sqlcmd Utility](sqlcmd-utility.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98d39-109">구문</span><span class="sxs-lookup"><span data-stu-id="98d39-109">Syntax</span></span>  
  
```  
  
      osql  
[-?] |  
[-L] |  
[  
  {  
     {-Ulogin_id [-Ppassword]} | -E }  
     [-Sserver_name[\instance_name]] [-Hwksta_name] [-ddb_name]  
     [-ltime_out] [-ttime_out] [-hheaders]  
     [-scol_separator] [-wcolumn_width] [-apacket_size]  
     [-e] [-I] [-D data_source_name]  
     [-ccmd_end] [-q "query"] [-Q"query"]  
     [-n] [-merror_level] [-r {0 | 1}]  
     [-iinput_file] [-ooutput_file] [-p]  
     [-b] [-u] [-R] [-O]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="98d39-110">인수</span><span class="sxs-lookup"><span data-stu-id="98d39-110">Arguments</span></span>  
 <span data-ttu-id="98d39-111">**-?**</span><span class="sxs-lookup"><span data-stu-id="98d39-111">**-?**</span></span>  
 <span data-ttu-id="98d39-112">**osql** 스위치의 구문 요약 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-112">Displays the syntax summary of **osql** switches.</span></span>  
  
 <span data-ttu-id="98d39-113">**-L**</span><span class="sxs-lookup"><span data-stu-id="98d39-113">**-L**</span></span>  
 <span data-ttu-id="98d39-114">로컬로 구성된 서버와 네트워크상에서 브로드캐스팅하는 서버의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-114">Lists the locally configured servers and the names of the servers broadcasting on the network.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98d39-115">네트워크에서 브로드캐스팅의 특성으로 인해 **osql** 은 모든 서버로부터 때맞춰 응답을 받지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-115">Due to the nature of broadcasting on networks, **osql** may not receive a timely response from all servers.</span></span> <span data-ttu-id="98d39-116">그러므로 반환되는 서버 목록은 이 옵션을 호출할 때마다 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-116">Therefore the list of servers returned may vary for each invocation of this option.</span></span>  
  
 <span data-ttu-id="98d39-117">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="98d39-117">**-U** _login_id_</span></span>  
 <span data-ttu-id="98d39-118">사용자 로그인 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-118">Is the user login ID.</span></span> <span data-ttu-id="98d39-119">로그인 ID는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-119">Login IDs are case-sensitive.</span></span>  
  
 <span data-ttu-id="98d39-120">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="98d39-120">**-P** _password_</span></span>  
 <span data-ttu-id="98d39-121">사용자가 지정하는 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-121">Is a user-specified password.</span></span> <span data-ttu-id="98d39-122">**-P** 옵션을 사용하지 않으면 **osql** 은 암호를 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-122">If the **-P** option is not used, **osql** prompts for a password.</span></span> <span data-ttu-id="98d39-123">암호를 입력하지 않고 명령 프롬프트의 마지막에 **-P** 옵션을 사용하면 **osql** 은 기본 암호인 NULL을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-123">If the **-P** option is used at the end of the command prompt without any password, **osql** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="98d39-124">빈 암호를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="98d39-124">Do not use a blank password.</span></span> <span data-ttu-id="98d39-125">강력한 암호를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="98d39-125">Use a strong password.</span></span> <span data-ttu-id="98d39-126">자세한 내용은 [Strong Passwords](../relational-databases/security/strong-passwords.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98d39-126">For more information, see [Strong Passwords](../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="98d39-127">암호는 대소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-127">Passwords are case-sensitive.</span></span>  
  
 <span data-ttu-id="98d39-128">OSQLPASSWORD 환경 변수를 사용하면 현재 세션에 대한 기본 암호를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-128">The OSQLPASSWORD environment variable allows you to set a default password for the current session.</span></span> <span data-ttu-id="98d39-129">따라서 배치 파일에 암호를 하드 코딩할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-129">Therefore, you do not have to hard code a password into batch files.</span></span>  
  
 <span data-ttu-id="98d39-130">**-P** 옵션으로 암호를 지정하지 않으면 **osql** 은 먼저 OSQLPASSWORD 변수를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-130">If you do not specify a password with the **-P** option, **osql** first checks for the OSQLPASSWORD variable.</span></span> <span data-ttu-id="98d39-131">값을 설정하지 않으면 **osql** 은 기본 암호인 NULL을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-131">If no value is set, **osql** uses the default password, NULL.</span></span> <span data-ttu-id="98d39-132">다음 예에서는 명령 프롬프트에서 OSQLPASSWORD 변수를 설정하고 **osql** 유틸리티에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-132">The following example sets the OSQLPASSWORD variable at a command prompt and then accesses the **osql** utility:</span></span>  
  
```  
C:\>SET OSQLPASSWORD=abracadabra  
C:\>osql   
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="98d39-133">암호를 마스킹하려면 **-U** 옵션과 함께 **-P** 옵션을 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="98d39-133">To mask your password, do not specify the **-P** option along with the **-U** option.</span></span> <span data-ttu-id="98d39-134">대신 **-U** 옵션 및 기타 스위치와 함께 **osql** 을 지정한 후 **-P**를 지정하지 말고 Enter 키를 누릅니다. 그러면 **osql** 이 암호를 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-134">Instead, after specifying **osql** along with the **-U** option and other switches (do not specify **-P**), press ENTER, and **osql** will prompt you for a password.</span></span> <span data-ttu-id="98d39-135">이 방법을 사용하면 암호 입력 시 암호가 마스킹됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-135">This method ensures that your password will be masked when it is entered.</span></span>  
  
 <span data-ttu-id="98d39-136">**-E**</span><span class="sxs-lookup"><span data-stu-id="98d39-136">**-E**</span></span>  
 <span data-ttu-id="98d39-137">암호를 요구하지 않고 트러스트된 연결을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-137">Uses a trusted connection instead of requesting a password.</span></span>  
  
 <span data-ttu-id="98d39-138">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="98d39-138">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="98d39-139">연결할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-139">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to.</span></span> <span data-ttu-id="98d39-140">해당 서버 컴퓨터에 있는 기본 *인스턴스에 연결하려면* server_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-140">Specify *server_name* to connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="98d39-141">_server_name_ **\\** 해당 서버에 있는 명명 된 인스턴스에 연결 하려면 server_name_instance_name_ 를 지정 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-141">Specify _server_name_**\\**_instance_name_ to connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="98d39-142">서버를 지정하지 않으면 **osql** 은 로컬 컴퓨터에 있는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 기본 인스턴스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-142">If no server is specified, **osql** connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="98d39-143">네트워크의 원격 컴퓨터에서 **osql** 을 실행할 때 이 옵션이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-143">This option is required when executing **osql** from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="98d39-144">**-H** _wksta_name_</span><span class="sxs-lookup"><span data-stu-id="98d39-144">**-H** _wksta_name_</span></span>  
 <span data-ttu-id="98d39-145">워크스테이션 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-145">Is a workstation name.</span></span> <span data-ttu-id="98d39-146">워크스테이션 이름은 **sysprocesses.hostname** 에 저장되고 **sp_who**에 의해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-146">The workstation name is stored in **sysprocesses.hostname** and is displayed by **sp_who**.</span></span> <span data-ttu-id="98d39-147">이 옵션을 지정하지 않으면 현재 컴퓨터 이름이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-147">If this option is not specified, the current computer name is assumed.</span></span>  
  
 <span data-ttu-id="98d39-148">**-d** _db_name_</span><span class="sxs-lookup"><span data-stu-id="98d39-148">**-d** _db_name_</span></span>  
 <span data-ttu-id="98d39-149">*osql* 을 시작할 때 USE **db_name**문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-149">Issues a USE *db_name* statement when **osql**is started.</span></span>  
  
 <span data-ttu-id="98d39-150">**-l** _time_out_</span><span class="sxs-lookup"><span data-stu-id="98d39-150">**-l** _time_out_</span></span>  
 <span data-ttu-id="98d39-151">**osql** 로그인 제한 시간(초)을 지정합니다. 기본 **osql** 로그인 제한 시간은 8초입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-151">Specifies the number of seconds before an **osql** login times out. The default time-out for login to **osql** is eight seconds.</span></span>  
  
 <span data-ttu-id="98d39-152">**-t** _time_out_</span><span class="sxs-lookup"><span data-stu-id="98d39-152">**-t** _time_out_</span></span>  
 <span data-ttu-id="98d39-153">명령 제한 시간(초)을 지정합니다. *time_out* 값을 지정하지 않으면 명령이 무기한 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-153">Specifies the number of seconds before a command times out. If a *time_out* value is not specified, commands do not time out.</span></span>  
  
 <span data-ttu-id="98d39-154">**-h** _headers_</span><span class="sxs-lookup"><span data-stu-id="98d39-154">**-h** _headers_</span></span>  
 <span data-ttu-id="98d39-155">열 머리글 사이에 출력할 행의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-155">Specifies the number of rows to print between column headings.</span></span> <span data-ttu-id="98d39-156">기본적으로 각 쿼리 결과 집합마다 머리글을 한 번 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-156">The default is to print headings one time for each set of query results.</span></span> <span data-ttu-id="98d39-157">머리글을 출력하지 않으려면 -1을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-157">Use -1 to specify that no headers will be printed.</span></span> <span data-ttu-id="98d39-158">-1을 사용하는 경우는 **-h -1**이 아니라 **-h-1**과 같이 매개 변수와 설정 사이에 공백이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-158">If -1 is used, there must be no space between the parameter and the setting (**-h-1**, not **-h -1**).</span></span>  
  
 <span data-ttu-id="98d39-159">**-s** _col_separator_</span><span class="sxs-lookup"><span data-stu-id="98d39-159">**-s** _col_separator_</span></span>  
 <span data-ttu-id="98d39-160">열 구분 기호 문자를 지정합니다. 기본값은 공백입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-160">Specifies the column-separator character, which is a blank space by default.</span></span> <span data-ttu-id="98d39-161">운영 체제에서 특별 한 의미를 갖는 문자 (예: |; &)를 사용 하려면 \< > 해당 문자를 큰따옴표 (")로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-161">To use characters that have special meaning to the operating system (for example, | ; & \< >), enclose the character in double quotation marks (").</span></span>  
  
 <span data-ttu-id="98d39-162">**-w** _column_width_</span><span class="sxs-lookup"><span data-stu-id="98d39-162">**-w** _column_width_</span></span>  
 <span data-ttu-id="98d39-163">출력에 사용할 화면의 너비를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-163">Allows the user to set the screen width for output.</span></span> <span data-ttu-id="98d39-164">기본값은 80자입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-164">The default is 80 characters.</span></span> <span data-ttu-id="98d39-165">출력 줄이 최대 화면 너비에 도달하면 여러 줄로 나뉘어집니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-165">When an output line has reached its maximum screen width, it is broken into multiple lines.</span></span>  
  
 <span data-ttu-id="98d39-166">**-a** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="98d39-166">**-a** _packet_size_</span></span>  
 <span data-ttu-id="98d39-167">다른 크기의 패킷을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-167">Allows you to request a different-sized packet.</span></span> <span data-ttu-id="98d39-168">유효한 *packet_size* 값은 512에서 65535까지입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-168">The valid values for *packet_size* are 512 through 65535.</span></span> <span data-ttu-id="98d39-169">기본값 **osql** 은 서버 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-169">The default value **osql** is the server default.</span></span> <span data-ttu-id="98d39-170">패킷 크기를 늘리면 GO 명령 사이에 SQL 문이 많은 크기가 큰 스크립트를 실행할 때 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-170">Increased packet size can enhance performance on larger script execution where the amount of SQL statements between GO commands is substantial.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="98d39-171">의 테스트 결과에 의하면 일반적으로 8192를 설정했을 때 대량 복사 작업이 가장 빨리 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-171">testing indicates that 8192 is typically the fastest setting for bulk copy operations.</span></span> <span data-ttu-id="98d39-172">더 큰 패킷 크기를 요청할 수 있지만 요청한 크기를 허용하지 않으면 **osql** 이 서버 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-172">A larger packet size can be requested, but **osql** defaults to the server default if the request cannot be granted.</span></span>  
  
 <span data-ttu-id="98d39-173">**-e**</span><span class="sxs-lookup"><span data-stu-id="98d39-173">**-e**</span></span>  
 <span data-ttu-id="98d39-174">입력을 에코합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-174">Echoes input.</span></span>  
  
 <span data-ttu-id="98d39-175">**-I**</span><span class="sxs-lookup"><span data-stu-id="98d39-175">**-I**</span></span>  
 <span data-ttu-id="98d39-176">QUOTED_IDENTIFIER 연결 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-176">Sets the QUOTED_IDENTIFIER connection option on.</span></span>  
  
 <span data-ttu-id="98d39-177">**-D** _data_source_name_</span><span class="sxs-lookup"><span data-stu-id="98d39-177">**-D** _data_source_name_</span></span>  
 <span data-ttu-id="98d39-178">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]용 ODBC 드라이버를 사용하여 정의한 ODBC 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-178">Connects to an ODBC data source that is defined using the ODBC driver for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="98d39-179">**osql** 연결은 데이터 원본에 지정한 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-179">The **osql** connection uses the options specified in the data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98d39-180">다른 드라이버에서 정의한 데이터 원본에서는 이 옵션이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-180">This option does not work with data sources defined for other drivers.</span></span>  
  
 <span data-ttu-id="98d39-181">**-c** _cmd_end_</span><span class="sxs-lookup"><span data-stu-id="98d39-181">**-c** _cmd_end_</span></span>  
 <span data-ttu-id="98d39-182">명령 종료 문자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-182">Specifies the command terminator.</span></span> <span data-ttu-id="98d39-183">기본적으로 줄에 GO만 단독으로 입력하면 명령이 종료되어 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-183">By default, commands are terminated and sent to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by entering GO on a line by itself.</span></span> <span data-ttu-id="98d39-184">명령 종료 문자를 다시 설정할 때는 앞에 백슬래시를 지정하는지 여부에 상관없이 [!INCLUDE[tsql](../includes/tsql-md.md)] 예약어 또는 운영 체제와 연관된 특별한 의미를 가진 문자를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="98d39-184">When you reset the command terminator, do not use [!INCLUDE[tsql](../includes/tsql-md.md)] reserved words or characters that have special meaning to the operating system, whether preceded by a backslash or not.</span></span>  
  
 <span data-ttu-id="98d39-185">**-q "** _query_ **"**</span><span class="sxs-lookup"><span data-stu-id="98d39-185">**-q "** _query_ **"**</span></span>  
 <span data-ttu-id="98d39-186">**osql** 이 시작될 때 쿼리를 실행하지만 쿼리가 완료되더라도 **osql** 을 끝내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-186">Executes a query when **osql** starts, but does not exit **osql** when the query completes.</span></span> <span data-ttu-id="98d39-187">쿼리 문에는 GO를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-187">(Note that the query statement should not include GO).</span></span> <span data-ttu-id="98d39-188">일괄 처리에서 쿼리를 실행하면 %변수 또는 환경 %변수%를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-188">If you issue a query from a batch file, use %variables, or environment %variables%.</span></span> <span data-ttu-id="98d39-189">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-189">For example:</span></span>  
  
```  
SET table=sys.objects  
osql -E -q "select name, object_id from %table%"  
```  
  
 <span data-ttu-id="98d39-190">쿼리는 큰따옴표로 묶고 쿼리 안에 포함되는 모든 것은 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-190">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span>  
  
 <span data-ttu-id="98d39-191">**-Q"** _query_ **"**</span><span class="sxs-lookup"><span data-stu-id="98d39-191">**-Q"** _query_ **"**</span></span>  
 <span data-ttu-id="98d39-192">쿼리를 실행하고 바로 **osql**을 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-192">Executes a query and immediately exits **osql**.</span></span> <span data-ttu-id="98d39-193">쿼리는 큰따옴표로 묶고 쿼리 안에 포함되는 모든 것은 작은따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-193">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span>  
  
 <span data-ttu-id="98d39-194">**-n**</span><span class="sxs-lookup"><span data-stu-id="98d39-194">**-n**</span></span>  
 <span data-ttu-id="98d39-195">입력 줄에서 번호 및 프롬프트 기호(>)를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-195">Removes numbering and the prompt symbol (>) from input lines.</span></span>  
  
 <span data-ttu-id="98d39-196">**-m** _error_level_</span><span class="sxs-lookup"><span data-stu-id="98d39-196">**-m** _error_level_</span></span>  
 <span data-ttu-id="98d39-197">오류 메시지 표시를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-197">Customizes the display of error messages.</span></span> <span data-ttu-id="98d39-198">지정한 심각도 이상의 오류에 대한 메시지 번호, 상태 및 오류 수준이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-198">The message number, state, and error level are displayed for errors of the specified severity level or higher.</span></span> <span data-ttu-id="98d39-199">지정한 수준보다 낮은 심각도의 오류에 대해서는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-199">Nothing is displayed for errors of levels lower than the specified level.</span></span> <span data-ttu-id="98d39-200">**-1** 을 사용하여 모든 머리글을 메시지(정보 메시지도 포함)와 함께 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-200">Use **-1** to specify that all headers are returned with messages, even informational messages.</span></span> <span data-ttu-id="98d39-201">**-1**을 사용하는 경우에는 **-m -1**이 아니라 **-m-1**과 같이 매개 변수와 설정 사이에 공백이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-201">If using **-1**, there must be no space between the parameter and the setting (**-m-1**, not **-m -1**).</span></span>  
  
 <span data-ttu-id="98d39-202">**-r** { **0**| **1**}</span><span class="sxs-lookup"><span data-stu-id="98d39-202">**-r** { **0**| **1**}</span></span>  
 <span data-ttu-id="98d39-203">메시지 출력을 화면으로 리디렉션합니다(**stderr**).</span><span class="sxs-lookup"><span data-stu-id="98d39-203">Redirects message output to the screen (**stderr**).</span></span> <span data-ttu-id="98d39-204">매개 변수를 지정하지 않거나 **0**을 지정하면 심각도가 11 이상인 오류 메시지만 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-204">If you do not specify a parameter, or if you specify **0**, only error messages with a severity level 11 or higher are redirected.</span></span> <span data-ttu-id="98d39-205">**1**을 지정하면 "print"를 포함하는 모든 메시지 출력이 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-205">If you specify **1**, all message output (including "print") is redirected.</span></span>  
  
 <span data-ttu-id="98d39-206">**-i** _input_file_</span><span class="sxs-lookup"><span data-stu-id="98d39-206">**-i** _input_file_</span></span>  
 <span data-ttu-id="98d39-207">SQL 문 또는 저장 프로시저의 일괄 처리가 포함된 파일을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-207">Identifies the file that contains a batch of SQL statements or stored procedures.</span></span> <span data-ttu-id="98d39-208">**\<** -i **대신 보다 작음(** ) 비교 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-208">The less than (**\<**) comparison operator can be used in place of **-i**.</span></span>  
  
 <span data-ttu-id="98d39-209">**-o** _output_file_</span><span class="sxs-lookup"><span data-stu-id="98d39-209">**-o** _output_file_</span></span>  
 <span data-ttu-id="98d39-210">**osql**에서 출력을 받는 파일을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-210">Identifies the file that receives output from **osql**.</span></span> <span data-ttu-id="98d39-211">**>** -o **대신 보다 큼(** ) 비교 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-211">The greater than (**>**) comparison operator can be used in place of **-o**.</span></span>  
  
 <span data-ttu-id="98d39-212">*input_file* 이 유니코드가 아니고 **-u** 가 지정되지 않은 경우 *output_file* 이 OEM 형식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-212">If *input_file* is not Unicode and **-u** is not specified, *output_file* is stored in OEM format.</span></span> <span data-ttu-id="98d39-213">*input_file* 이 유니코드이거나 **-u** 가 지정된 경우에는 *output_file* 이 유니코드 형식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-213">If *input_file* is Unicode or **-u** is specified, *output_file* is stored in Unicode format.</span></span>  
  
 <span data-ttu-id="98d39-214">**-p**</span><span class="sxs-lookup"><span data-stu-id="98d39-214">**-p**</span></span>  
 <span data-ttu-id="98d39-215">성능 통계를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-215">Prints performance statistics.</span></span>  
  
 <span data-ttu-id="98d39-216">**-b**</span><span class="sxs-lookup"><span data-stu-id="98d39-216">**-b**</span></span>  
 <span data-ttu-id="98d39-217">오류가 발생하면 **osql** 을 끝내고 DOS ERRORLEVEL 값을 반환하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-217">Specifies that **osql** exits and returns a DOS ERRORLEVEL value when an error occurs.</span></span> <span data-ttu-id="98d39-218">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 오류 메시지의 심각도가 11 이상이면 DOS ERRORLEVEL 변수에 1을 반환하고 아니면 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-218">The value returned to the DOS ERRORLEVEL variable is 1 when the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] error message has a severity of 11 or greater; otherwise, the value returned is 0.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="98d39-219">MS-DOS 배치 파일은 DOS ERRORLEVEL 값을 검사하여 오류를 적절하게 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-219">MS-DOS batch files can test the value of DOS ERRORLEVEL and handle the error appropriately.</span></span>  
  
 <span data-ttu-id="98d39-220">**-u**</span><span class="sxs-lookup"><span data-stu-id="98d39-220">**-u**</span></span>  
 <span data-ttu-id="98d39-221">*input_file* 형식에 관계없이 *output_file*이 유니코드 형식으로 저장되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-221">Specifies that *output_file* is stored in Unicode format, regardless of the format of the *input_file*.</span></span>  
  
 <span data-ttu-id="98d39-222">**-R**</span><span class="sxs-lookup"><span data-stu-id="98d39-222">**-R**</span></span>  
 <span data-ttu-id="98d39-223">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC 드라이버가 통화, 날짜 및 시간 데이터를 문자 데이터로 변환할 때 클라이언트 설정을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-223">Specifies that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC driver use client settings when converting currency, date, and time data to character data.</span></span>  
  
 <span data-ttu-id="98d39-224">**-O**</span><span class="sxs-lookup"><span data-stu-id="98d39-224">**-O**</span></span>  
 <span data-ttu-id="98d39-225">이전 버전의 **osql** 동작과 일치하도록 특정 **isql**기능을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-225">Specifies that certain **osql** features be deactivated to match the behavior of earlier versions of **isql**.</span></span> <span data-ttu-id="98d39-226">다음 기능이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-226">These features are deactivated:</span></span>  
  
-   <span data-ttu-id="98d39-227">EOF 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="98d39-227">EOF batch processing</span></span>  
  
-   <span data-ttu-id="98d39-228">콘솔 너비 자동 조정</span><span class="sxs-lookup"><span data-stu-id="98d39-228">Automatic console width scaling</span></span>  
  
-   <span data-ttu-id="98d39-229">와이드 메시지</span><span class="sxs-lookup"><span data-stu-id="98d39-229">Wide messages</span></span>  
  
 <span data-ttu-id="98d39-230">DOS ERRORLEVEL의 기본값을 -1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-230">It also sets the default DOS ERRORLEVEL value to -1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98d39-231">**osql**에서는 **-n** , **-O** 및 **-D**옵션이 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-231">The **-n**, **-O** and **-D** options are no longer supported by **osql**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98d39-232">설명</span><span class="sxs-lookup"><span data-stu-id="98d39-232">Remarks</span></span>  
 <span data-ttu-id="98d39-233">위에 나열된 대/소문자를 구분하는 옵션을 사용하여 **osql** 유틸리티를 운영 체제에서 직접 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-233">The **osql** utility is started directly from the operating system with the case-sensitive options listed here.</span></span> <span data-ttu-id="98d39-234">**osql**을 시작하면 osql이 SQL 문을 받아서 대화형으로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-234">After **osql**starts, it accepts SQL statements and sends them to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] interactively.</span></span> <span data-ttu-id="98d39-235">결과는 서식 지정되어 화면에 표시됩니다(**stdout**).</span><span class="sxs-lookup"><span data-stu-id="98d39-235">The results are formatted and displayed on the screen (**stdout**).</span></span> <span data-ttu-id="98d39-236">**osql**을 끝내려면 QUIT 또는 EXIT를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-236">Use QUIT or EXIT to exit from **osql**.</span></span>  
  
 <span data-ttu-id="98d39-237">**Osql**을 시작할 때 사용자 이름을 지정 하지 않으면에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 환경 변수를 확인 하 고이 변수를 사용 합니다 (예: **osqluser = ( *`user`* )** 또는 **osqlserver = ( *`server`* ))**.</span><span class="sxs-lookup"><span data-stu-id="98d39-237">If you do not specify a user name when you start **osql**, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] checks for the environment variables and uses those, for example, **osqluser=(*`user`*)** or **osqlserver=(*`server`*)**.</span></span> <span data-ttu-id="98d39-238">환경 변수를 설정하지 않으면 워크스테이션 사용자 이름이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-238">If no environment variables are set, the workstation user name is used.</span></span> <span data-ttu-id="98d39-239">서버를 지정하지 않으면 워크스테이션 이름이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-239">If you do not specify a server, the name of the workstation is used.</span></span>  
  
 <span data-ttu-id="98d39-240">**-U** 또는 **-P** 옵션을 사용하지 않으면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 인증 모드를 사용하여 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-240">If neither the **-U** or **-P** options are used, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] attempts to connect using [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication Mode.</span></span> <span data-ttu-id="98d39-241">인증은 [!INCLUDE[msCoName](../includes/msconame-md.md)] osql **을 실행하는 사용자의**Windows 계정에 기반합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-241">Authentication is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows account of the user running **osql**.</span></span>  
  
 <span data-ttu-id="98d39-242">**osql** 유틸리티는 ODBC API를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-242">The **osql** utility uses the ODBC API.</span></span> <span data-ttu-id="98d39-243">이 유틸리티는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ISO 연결 옵션의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC 드라이버 기본 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-243">The utility uses the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC driver default settings for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ISO connection options.</span></span> <span data-ttu-id="98d39-244">자세한 내용은 ANSI 옵션 효과를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="98d39-244">For more information, see Effects of ANSI Options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98d39-245">**osql** 유틸리티는 CLR 사용자 정의 데이터 형식을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-245">The **osql** utility does not support CLR user-defined data types.</span></span> <span data-ttu-id="98d39-246">이 데이터 형식을 처리하려면 **sqlcmd** 유틸리티를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-246">To process these data types, you must use the **sqlcmd** utility.</span></span> <span data-ttu-id="98d39-247">자세한 내용은 [sqlcmd Utility](sqlcmd-utility.md)을(를) 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="98d39-247">For more information, see [sqlcmd Utility](sqlcmd-utility.md).</span></span>  
  
## <a name="osql-commands"></a><span data-ttu-id="98d39-248">OSQL 명령</span><span class="sxs-lookup"><span data-stu-id="98d39-248">OSQL Commands</span></span>  
 <span data-ttu-id="98d39-249">[!INCLUDE[tsql](../includes/tsql-md.md)] osql **내에서**문 외에도 다음 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-249">In addition to [!INCLUDE[tsql](../includes/tsql-md.md)] statements within **osql**, these commands are also available.</span></span>  
  
|<span data-ttu-id="98d39-250">명령</span><span class="sxs-lookup"><span data-stu-id="98d39-250">Command</span></span>|<span data-ttu-id="98d39-251">Description</span><span class="sxs-lookup"><span data-stu-id="98d39-251">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98d39-252">이동</span><span class="sxs-lookup"><span data-stu-id="98d39-252">GO</span></span>|<span data-ttu-id="98d39-253">마지막 GO 이후에 입력한 모든 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-253">Executes all statements entered after the last GO.</span></span>|  
|<span data-ttu-id="98d39-254">RESET</span><span class="sxs-lookup"><span data-stu-id="98d39-254">RESET</span></span>|<span data-ttu-id="98d39-255">입력한 모든 문을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-255">Clears any statements you have entered.</span></span>|  
|<span data-ttu-id="98d39-256">QUIT 또는 EXIT( )</span><span class="sxs-lookup"><span data-stu-id="98d39-256">QUIT or EXIT( )</span></span>|<span data-ttu-id="98d39-257">**osql**을 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-257">Exits from **osql**.</span></span>|  
|<span data-ttu-id="98d39-258">CTRL+C</span><span class="sxs-lookup"><span data-stu-id="98d39-258">CTRL+C</span></span>|<span data-ttu-id="98d39-259">**osql**을 끝내지 않고 쿼리를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-259">Ends a query without exiting from **osql**.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="98d39-260">!!</span><span class="sxs-lookup"><span data-stu-id="98d39-260">The !!</span></span> <span data-ttu-id="98d39-261">및 ED 명령은 **osql**에서 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-261">and ED commands are no longer supported by **osql**.</span></span>  
  
 <span data-ttu-id="98d39-262">명령 종료 문자인 GO(기본 문자), RESET EXIT, QUIT 및 Ctrl+C는 **osql** 프롬프트 바로 뒤의 줄 시작 부분에 나올 때만 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-262">The command terminators GO (by default), RESET EXIT, QUIT, and CTRL+C, are recognized only if they appear at the beginning of a line, immediately following the **osql** prompt.</span></span>  
  
 <span data-ttu-id="98d39-263">GO는 일괄 처리의 끝을 알려 주고 캐시된 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 실행하도록 신호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-263">GO signals both the end of a batch and the execution of any cached [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="98d39-264">각 입력 줄의 끝에서 Enter 키를 누르면 **osql** 이 해당 줄의 문을 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-264">When you press ENTER at the end of each input line, **osql** caches the statements on that line.</span></span> <span data-ttu-id="98d39-265">GO를 입력한 다음 Enter 키를 누르면 현재 캐시된 모든 문을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 일괄 처리로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-265">When you press ENTER after typing GO, all of the currently cached statements are sent as a batch to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="98d39-266">현재 **osql** 유틸리티는 스크립트 끝에 GO가 있는 것으로 간주하므로 스크립트의 모든 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-266">The current **osql** utility works as if there is an implied GO at the end of any script executed, therefore all statements in the script execute.</span></span>  
  
 <span data-ttu-id="98d39-267">명령 종료 문자로 시작하는 줄을 입력하여 명령을 끝내십시오.</span><span class="sxs-lookup"><span data-stu-id="98d39-267">End a command by typing a line beginning with a command terminator.</span></span> <span data-ttu-id="98d39-268">명령 종료 문자 다음에 정수를 써서 명령 실행 횟수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-268">You can follow the command terminator with an integer to specify how many times the command should be run.</span></span> <span data-ttu-id="98d39-269">예를 들어 다음 명령을 100번 실행하려면 다음을 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="98d39-269">For example, to execute this command 100 times, type:</span></span>  
  
```  
SELECT x = 1  
GO 100  
```  
  
 <span data-ttu-id="98d39-270">결과는 실행이 끝날 때 한 번만 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-270">The results are printed once at the end of execution.</span></span> <span data-ttu-id="98d39-271">**osql** 을 사용하면 각 줄에서 최대 1,000자까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-271">**osql** does not accept more than 1,000 characters per line.</span></span> <span data-ttu-id="98d39-272">긴 문은 여러 줄로 나뉘어집니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-272">Large statements should be spread across multiple lines.</span></span>  
  
 <span data-ttu-id="98d39-273">Windows의 명령 재호출 기능을 사용하면 **osql** 문을 다시 호출하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-273">The command recall facilities of Windows can be used to recall and modify **osql** statements.</span></span> <span data-ttu-id="98d39-274">RESET을 입력하면 기존 쿼리 버퍼를 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-274">The existing query buffer can be cleared by typing RESET.</span></span>  
  
 <span data-ttu-id="98d39-275">**osql** 은 저장 프로시저를 실행할 때 일괄 처리의 각 결과 집합 사이에 빈 줄을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-275">When running stored procedures, **osql** prints a blank line between each set of results in a batch.</span></span> <span data-ttu-id="98d39-276">또한, 실행되는 문에 적용되지 않을 때는 "적용된 행 없음" 메시지가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-276">In addition, the "0 rows affected" message does not appear when it does not apply to the statement executed.</span></span>  
  
## <a name="using-osql-interactively"></a><span data-ttu-id="98d39-277">osql을 대화형으로 사용</span><span class="sxs-lookup"><span data-stu-id="98d39-277">Using osql Interactively</span></span>  
 <span data-ttu-id="98d39-278">**osql** 을 대화형으로 사용하려면 명령 프롬프트에서 **osql** 명령 및 옵션을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-278">To use **osql** interactively, type the **osql** command (and any of the options) at a command prompt.</span></span>  
  
 <span data-ttu-id="98d39-279">다음과 같은 명령을 입력하면 Stores.qry 파일과 같이 **osql** 실행 쿼리가 들어 있는 파일을 읽어올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-279">You can read in a file containing a query (such as Stores.qry) for execution by **osql** by typing a command similar to this:</span></span>  
  
```  
osql -E -i stores.qry  
```  
  
 <span data-ttu-id="98d39-280">다음과 같은 명령을 입력하면 쿼리가 들어 있는 Titles.qry 파일을 읽어 들이고 그 결과를 다른 파일에 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-280">You can read in a file containing a query (such as Titles.qry) and direct the results to another file by typing a command similar to this:</span></span>  
  
```  
osql -E -i titles.qry -o titles.res  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="98d39-281">가능하면 **-E**옵션(신뢰할 수 있는 연결)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-281">When possible, use the **-E**option (trusted connection).</span></span>  
  
 <span data-ttu-id="98d39-282">**Osql** 을 대화형으로 사용 하는 경우 **: r**_file_name_를 사용 하 여 운영 체제 파일을 명령 버퍼로 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-282">When using **osql** interactively, you can read an operating-system file into the command buffer with **:r**_file_name_.</span></span> <span data-ttu-id="98d39-283">그러면 *file_name* 의 SQL 스크립트가 직접 서버에 한 번의 일괄 처리로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-283">This sends the SQL script in *file_name* directly to the server as a single batch.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98d39-284">**osql**을 사용할 때 일괄 처리 구분 기호 GO가 SQL 스크립트 파일에 나타나면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에서 이를 구문 오류로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-284">When using **osql**, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] treats the batch separator GO, if it appears in a SQL script file, as a syntax error.</span></span>  
  
## <a name="inserting-comments"></a><span data-ttu-id="98d39-285">주석 삽입</span><span class="sxs-lookup"><span data-stu-id="98d39-285">Inserting Comments</span></span>  
 <span data-ttu-id="98d39-286">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] osql **을 사용하여**에 전송하는 Transact-SQL 문에 주석을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-286">You can include comments in a Transact-SQL statement submitted to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by **osql**.</span></span> <span data-ttu-id="98d39-287">허용되는 두 가지 주석 유형은 -- 및 /\*...\*/입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-287">Two types of commenting styles are allowed: -- and /\*...\*/.</span></span>  
  
## <a name="using-exit-to-return-results-in-osql"></a><span data-ttu-id="98d39-288">EXIT를 사용하여 osql의 결과 반환</span><span class="sxs-lookup"><span data-stu-id="98d39-288">Using EXIT to Return Results in osql</span></span>  
 <span data-ttu-id="98d39-289">SELECT 문의 결과를 **osql**의 반환 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-289">You can use the result of a SELECT statement as the return value from **osql**.</span></span> <span data-ttu-id="98d39-290">숫자일 경우 마지막 결과 행의 마지막 열은 4바이트 정수(long)로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-290">If it is numeric, the last column of the last result row is converted to a 4-byte integer (long).</span></span> <span data-ttu-id="98d39-291">MS-DOS는 하위 바이트를 부모 프로세스 또는 운영 체제 오류 수준에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-291">MS-DOS passes the low byte to the parent process or operating system error level.</span></span> <span data-ttu-id="98d39-292">Windows에서는 4바이트 정수 전체를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-292">Windows passes the entire 4-byte integer.</span></span> <span data-ttu-id="98d39-293">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-293">The syntax is:</span></span>  
  
```  
EXIT ( < query > )  
```  
  
 <span data-ttu-id="98d39-294">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-294">For example:</span></span>  
  
```  
EXIT(SELECT @@ROWCOUNT)  
```  
  
 <span data-ttu-id="98d39-295">EXIT 매개 변수를 배치 파일의 일부로 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-295">You can also include the EXIT parameter as part of a batch file.</span></span> <span data-ttu-id="98d39-296">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-296">For example:</span></span>  
  
```  
osql -E -Q "EXIT(SELECT COUNT(*) FROM '%1')"  
```  
  
 <span data-ttu-id="98d39-297">**osql** 유틸리티는 괄호 **()** 안에 입력된 모든 내용을 그대로 서버에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-297">The **osql** utility passes everything between the parentheses **()** to the server exactly as entered.</span></span> <span data-ttu-id="98d39-298">저장 시스템 프로시저가 설정을 선택하고 값을 반환하면 선택 내용만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-298">If a stored system procedure selects a set and returns a value, only the selection is returned.</span></span> <span data-ttu-id="98d39-299">EXIT **()** 문의 괄호 사이에 아무 것도 없으면 이 문 앞에 나오는 모든 문을 실행한 다음 값을 반환하지 않고 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-299">The EXIT **()** statement with nothing between the parentheses executes everything preceding it in the batch and then exits with no return value.</span></span>  
  
 <span data-ttu-id="98d39-300">다음과 같은 4개의 EXIT 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-300">There are four EXIT formats:</span></span>  
  
-   <span data-ttu-id="98d39-301">EXIT</span><span class="sxs-lookup"><span data-stu-id="98d39-301">EXIT</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98d39-302">일괄 처리를 실행하지 않고 즉시 종료하며 값을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-302">Does not execute the batch; quits immediately and returns no value.</span></span>  
  
-   <span data-ttu-id="98d39-303">EXIT **()**</span><span class="sxs-lookup"><span data-stu-id="98d39-303">EXIT **()**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98d39-304">일괄 처리를 실행한 다음 종료하며 값을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-304">Executes the batch, and then quits and returns no value.</span></span>  
  
-   <span data-ttu-id="98d39-305">EXIT **( *`query`* )**</span><span class="sxs-lookup"><span data-stu-id="98d39-305">EXIT **(*`query`*)**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98d39-306">쿼리를 포함한 일괄 처리를 실행하며 쿼리 결과를 반환한 다음 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-306">Executes the batch, including the query, and then quits after returning the results of the query.</span></span>  
  
-   <span data-ttu-id="98d39-307">상태가 127인 RAISERROR</span><span class="sxs-lookup"><span data-stu-id="98d39-307">RAISERROR with a state of 127</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98d39-308">**osql** 스크립트에 RAISERROR를 사용할 때 상태 127이 발생하면 **osql** 이 종료되고 메시지 ID가 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-308">If RAISERROR is used within an **osql** script and a state of 127 is raised, **osql** will quit and return the message ID back to the client.</span></span> <span data-ttu-id="98d39-309">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-309">For example:</span></span>  
  
```  
RAISERROR(50001, 10, 127)  
```  
  
 <span data-ttu-id="98d39-310">이 오류가 발생하면 **osql** 스크립트가 종료되고 메시지 ID 50001이 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-310">This error will cause the **osql** script to end and the message ID 50001 will be returned to the client.</span></span>  
  
 <span data-ttu-id="98d39-311">-1부터 -99까지의 반환 값은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 예약되어 있습니다. **osql** 에는 다음과 같은 값이 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-311">The return values -1 to -99 are reserved by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]; **osql** defines these values:</span></span>  
  
-   <span data-ttu-id="98d39-312">-100</span><span class="sxs-lookup"><span data-stu-id="98d39-312">-100</span></span>  
  
     <span data-ttu-id="98d39-313">반환 값을 선택하기 전에 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-313">Error encountered prior to selecting return value.</span></span>  
  
-   <span data-ttu-id="98d39-314">-101</span><span class="sxs-lookup"><span data-stu-id="98d39-314">-101</span></span>  
  
     <span data-ttu-id="98d39-315">반환 값을 선택할 때 행을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-315">No rows found when selecting return value.</span></span>  
  
-   <span data-ttu-id="98d39-316">-102</span><span class="sxs-lookup"><span data-stu-id="98d39-316">-102</span></span>  
  
     <span data-ttu-id="98d39-317">반환 값을 선택할 때 변환 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-317">Conversion error occurred when selecting return value.</span></span>  
  
## <a name="displaying-money-and-smallmoney-data-types"></a><span data-ttu-id="98d39-318">money 및 smallmoney 데이터 형식 표시</span><span class="sxs-lookup"><span data-stu-id="98d39-318">Displaying money and smallmoney Data Types</span></span>  
 <span data-ttu-id="98d39-319">**osql** 은 `money` 두 개의 소수 자릿수로 및 `smallmoney` 데이터 형식을 표시 하지만는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 내부적으로 네 개의 소수 자릿수로 값을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-319">**osql** displays the `money` and `smallmoney` data types with two decimal places although [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stores the value internally with four decimal places.</span></span> <span data-ttu-id="98d39-320">예를 들어, 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-320">Consider the example:</span></span>  
  
```  
SELECT CAST(CAST(10.3496 AS money) AS decimal(6, 4))  
GO  
```  
  
 <span data-ttu-id="98d39-321">이 문의 결과는 `10.3496`로 표시됩니다. 모든 소수 자릿수를 그대로 사용하여 값이 저장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="98d39-321">This statement produces a result of `10.3496`, which indicates that the value is stored with all decimal places intact.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d39-322">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98d39-322">See Also</span></span>  
 <span data-ttu-id="98d39-323">[설명&#40;MDX&#41;](/sql/mdx/comment-mdx) </span><span class="sxs-lookup"><span data-stu-id="98d39-323">[Comment &#40;MDX&#41;](/sql/mdx/comment-mdx) </span></span>  
 <span data-ttu-id="98d39-324">[-- &#40;설명&#41;&#40;MDX&#41;](/sql/mdx/comment-mdx) </span><span class="sxs-lookup"><span data-stu-id="98d39-324">[-- &#40;Comment&#41; &#40;MDX&#41;](/sql/mdx/comment-mdx) </span></span>  
 <span data-ttu-id="98d39-325">[CAST 및 CONVERT&#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="98d39-325">[CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql) </span></span>  
 [<span data-ttu-id="98d39-326">RAISERROR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="98d39-326">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
