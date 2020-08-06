---
title: rsconfig 유틸리티(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- connections [Reporting Services], configuring
- rsconfig utility
- report servers [Reporting Services], connections
- command prompt utilities [Reporting Services]
- command prompt utilities [SQL Server], rsconfig
ms.assetid: 84e45a2f-3ca6-4c16-8259-c15ff49d72ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 499fa5529991b36e467567b4c7006845dfcd2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736000"
---
# <a name="rsconfig-utility-ssrs"></a><span data-ttu-id="5eeeb-102">rsconfig 유틸리티(SSRS)</span><span class="sxs-lookup"><span data-stu-id="5eeeb-102">rsconfig Utility (SSRS)</span></span>
  <span data-ttu-id="5eeeb-103">**rsconfig.exe** 유틸리티는 연결 및 계정 값을 암호화하여 RSReportServer.config 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-103">The **rsconfig.exe** utility encrypts and stores connection and account values in the RSReportServer.config file.</span></span> <span data-ttu-id="5eeeb-104">암호화되는 값에는 무인 보고서 처리에 사용되는 보고서 서버 데이터베이스 연결 정보 및 계정 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-104">Encrypted values include report server database connection information and account values used for unattended report processing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eeeb-105">구문</span><span class="sxs-lookup"><span data-stu-id="5eeeb-105">Syntax</span></span>  
  
```  
  
      rsconfig {-?}  
{-cconnection}  
{-eunattendedaccount}  
{-mcomputername}  
{-iinstancename}  
{-sservername}  
{-ddatabasename}  
{-aauthmethod}  
{-uusername}  
{-ppassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a><span data-ttu-id="5eeeb-106">인수</span><span class="sxs-lookup"><span data-stu-id="5eeeb-106">Arguments</span></span>  
  
|<span data-ttu-id="5eeeb-107">용어</span><span class="sxs-lookup"><span data-stu-id="5eeeb-107">Term</span></span>|<span data-ttu-id="5eeeb-108">선택/필수</span><span class="sxs-lookup"><span data-stu-id="5eeeb-108">Optional/Required</span></span>|<span data-ttu-id="5eeeb-109">정의</span><span class="sxs-lookup"><span data-stu-id="5eeeb-109">Definition</span></span>|  
|----------|------------------------|----------------|  
|<span data-ttu-id="5eeeb-110">**-?**</span><span class="sxs-lookup"><span data-stu-id="5eeeb-110">**-?**</span></span>|<span data-ttu-id="5eeeb-111">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="5eeeb-111">Optional.</span></span>|<span data-ttu-id="5eeeb-112">Rsconfig.exe 인수의 구문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-112">Displays the syntax of Rsconfig.exe arguments.</span></span>|  
|`-c`|<span data-ttu-id="5eeeb-113">`-e` 인수를 사용하지 않은 경우 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-113">Required if `-e` argument is not used.</span></span>|<span data-ttu-id="5eeeb-114">보고서 서버에서 보고서 서버 데이터베이스에 연결하는 데 사용되는 연결 문자열, 자격 증명 및 데이터 원본 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-114">Specifies the connection string, credentials, and data source values used to connect a report server to the report server database.</span></span><br /><br /> <span data-ttu-id="5eeeb-115">이 인수는 값을 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-115">This argument does not take a value.</span></span> <span data-ttu-id="5eeeb-116">그러나 모든 필수 연결 값을 제공하려면 이 인수와 함께 추가 인수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-116">However, additional arguments must be specified with it to provide all of the required connection values.</span></span><br /><br /> <span data-ttu-id="5eeeb-117">을 사용 하 여 지정할 수 있는 인수에는 `-c` `-m` , **-s**,,,,,, 및가 포함 됩니다 `-i` `-d` `-a` `-u` `-p` `-t` .</span><span class="sxs-lookup"><span data-stu-id="5eeeb-117">Arguments that you can specify with `-c` include `-m`, **-s**, `-i`,`-d`,`-a`,`-u`,`-p`, and`-t`.</span></span>|  
|`-e`|<span data-ttu-id="5eeeb-118">`-c` 인수를 사용하지 않은 경우 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-118">Required if `-c` argument is not used.</span></span>|<span data-ttu-id="5eeeb-119">무인 보고서 실행 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-119">Specifies the unattended report execution account.</span></span><br /><br /> <span data-ttu-id="5eeeb-120">이 인수는 값을 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-120">This argument does not take a value.</span></span> <span data-ttu-id="5eeeb-121">그러나 구성 파일에 암호화된 값을 지정하려면 명령줄에 추가 인수를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-121">However, you must include additional arguments on the command line to specify that values that are encrypted in the configuration file.</span></span><br /><br /> <span data-ttu-id="5eeeb-122">`-e`를 사용하여 지정할 수 있는 인수에는 `-u`, `-p` 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-122">Arguments that you can specify with `-e` include `-u` and `-p`.</span></span> <span data-ttu-id="5eeeb-123">`-t`도 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-123">You can also set `-t`.</span></span>|  
|<span data-ttu-id="5eeeb-124">`-m`  *컴퓨터*</span><span class="sxs-lookup"><span data-stu-id="5eeeb-124">`-m`  *computername*</span></span>|<span data-ttu-id="5eeeb-125">원격 보고서 서버 인스턴스를 구성하는 경우 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-125">Required if you are configuring a remote report server instance.</span></span>|<span data-ttu-id="5eeeb-126">보고서 서버를 호스팅하는 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-126">Specifies the name of the computer that is hosting the report server.</span></span> <span data-ttu-id="5eeeb-127">이 인수를 생략할 경우 기본값은 `localhost`입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-127">If this argument is omitted, the default is `localhost`.</span></span>|  
|<span data-ttu-id="5eeeb-128">**-s**  *servername*</span><span class="sxs-lookup"><span data-stu-id="5eeeb-128">**-s**  *servername*</span></span>|<span data-ttu-id="5eeeb-129">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-129">Required.</span></span>|<span data-ttu-id="5eeeb-130">보고서 서버 데이터베이스를 호스팅하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-130">Specifies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server database.</span></span>|  
|<span data-ttu-id="5eeeb-131">`-i`  *instancename*</span><span class="sxs-lookup"><span data-stu-id="5eeeb-131">`-i`  *instancename*</span></span>|<span data-ttu-id="5eeeb-132">명명된 인스턴스를 사용하는 경우 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-132">Required if you are using named instances.</span></span>|<span data-ttu-id="5eeeb-133">명명된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 사용하여 보고서 서버 데이터베이스를 호스팅하는 경우 이 값은 명명된 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-133">If you used a named [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host the report server database, this value specifies the named instance.</span></span>|  
|<span data-ttu-id="5eeeb-134">`-d`  *databasename*</span><span class="sxs-lookup"><span data-stu-id="5eeeb-134">`-d`  *databasename*</span></span>|<span data-ttu-id="5eeeb-135">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-135">Required.</span></span>|<span data-ttu-id="5eeeb-136">보고서 서버 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-136">Specifies the name of the report server database.</span></span>|  
|<span data-ttu-id="5eeeb-137">`-a`  *authmethod*</span><span class="sxs-lookup"><span data-stu-id="5eeeb-137">`-a`  *authmethod*</span></span>|<span data-ttu-id="5eeeb-138">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-138">Required.</span></span>|<span data-ttu-id="5eeeb-139">보고서 서버에서 보고서 서버 데이터베이스에 연결할 때 사용하는 인증 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-139">Specifies the authentication method that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="5eeeb-140">유효한 값은 `Windows` 또는 `SQL`입니다. 이 인수는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-140">Valid values are `Windows` or `SQL` (this argument is not case-sensitive).</span></span><br /><br /> <span data-ttu-id="5eeeb-141">`Windows`에서는 보고서 서버가 Windows 인증을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-141">`Windows` specifies that the report server use Windows Authentication.</span></span><br /><br /> <span data-ttu-id="5eeeb-142">`SQL`에서는 보고서 서버가 SQL Server 인증을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-142">`SQL` specifies that the report server use SQL Server Authentication.</span></span>|  
|<span data-ttu-id="5eeeb-143">`-u`  *[도메인 \\ ] 이름*</span><span class="sxs-lookup"><span data-stu-id="5eeeb-143">`-u`  *[domain\\]username*</span></span>|<span data-ttu-id="5eeeb-144">`-e`에는 필수 인수이고 `-c`에는 선택 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-144">Required with `-e` Optional with `-c`.</span></span>|<span data-ttu-id="5eeeb-145">보고서 서버 데이터베이스 연결 또는 무인 계정을 위한 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-145">Specifies a user account for the report server database connection or for the unattended account.</span></span><br /><br /> <span data-ttu-id="5eeeb-146">**rsconfig -e**의 경우 이 인수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-146">For **rsconfig -e**, this argument is required.</span></span> <span data-ttu-id="5eeeb-147">도메인 사용자 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-147">It must be a domain user account.</span></span><br /><br /> <span data-ttu-id="5eeeb-148">**Rsconfig** 및의 경우 `-a SQL` 이 인수는 로그인을 지정 해야 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5eeeb-148">For **rsconfig -c** and `-a SQL`, this argument must specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span><br /><br /> <span data-ttu-id="5eeeb-149">**Rsconfig** 및의 경우 `-a Windows` 이 인수는 도메인 사용자, 기본 제공 계정 또는 서비스 계정 자격 증명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-149">For **rsconfig -c** and `-a Windows`, this argument may specify a domain user, a built-in account, or service account credentials.</span></span> <span data-ttu-id="5eeeb-150">도메인 계정을 지정하는 경우 *domain* 및 *username* 을 *domain\username*형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-150">If you are specifying a domain account, specify *domain* and *username* in the format *domain\username*.</span></span> <span data-ttu-id="5eeeb-151">기본 제공 계정을 사용하는 경우 이 인수는 선택 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-151">If you are using a built-in account, this argument is optional.</span></span> <span data-ttu-id="5eeeb-152">서비스 계정 자격 증명을 사용하려면 이 인수를 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-152">If you want to use service account credentials, omit this argument.</span></span>|  
|<span data-ttu-id="5eeeb-153">`-p`  *암호*</span><span class="sxs-lookup"><span data-stu-id="5eeeb-153">`-p`  *password*</span></span>|<span data-ttu-id="5eeeb-154">`-u`를 지정하는 경우 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-154">Required if `-u` is specified.</span></span>|<span data-ttu-id="5eeeb-155">*username* 인수와 함께 사용할 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-155">Specifies the password to use with the *username* argument.</span></span> <span data-ttu-id="5eeeb-156">계정에 암호가 필요하지 않은 경우에는 이 인수를 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-156">You can set this argument to a blank value if the account does not require a password.</span></span> <span data-ttu-id="5eeeb-157">도메인 계정의 경우 이 값은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-157">This value is case-sensitive for domain accounts.</span></span>|  
|`-t`|<span data-ttu-id="5eeeb-158">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-158">Optional.</span></span>|<span data-ttu-id="5eeeb-159">추적 로그에 오류 메시지를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-159">Outputs error messages to the trace log.</span></span> <span data-ttu-id="5eeeb-160">이 인수는 값을 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-160">This argument does not take a value.</span></span> <span data-ttu-id="5eeeb-161">자세한 내용은 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-161">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>|  
  
## <a name="permissions"></a><span data-ttu-id="5eeeb-162">사용 권한</span><span class="sxs-lookup"><span data-stu-id="5eeeb-162">Permissions</span></span>  
 <span data-ttu-id="5eeeb-163">구성 중인 보고서 서버를 호스팅하는 컴퓨터에 로컬 관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-163">You must be a local administrator on the computer that hosts the report server you are configuring.</span></span>  
  
## <a name="file-location"></a><span data-ttu-id="5eeeb-164">파일 위치</span><span class="sxs-lookup"><span data-stu-id="5eeeb-164">File Location</span></span>  
 <span data-ttu-id="5eeeb-165">Rsconfig.exe는 **\Program Files\Microsoft SQL Server\110\Tools\Binn**에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-165">Rsconfig.exe is located in **\Program Files\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="5eeeb-166">파일 시스템의 모든 폴더에서 유틸리티를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-166">You can run the utility from any folder on your file system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5eeeb-167">설명</span><span class="sxs-lookup"><span data-stu-id="5eeeb-167">Remarks</span></span>  
 <span data-ttu-id="5eeeb-168">Rsconfig.exe는 다음 두 가지 목적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-168">Rsconfig.exe is used for two purposes:</span></span>  
  
-   <span data-ttu-id="5eeeb-169">보고서 서버에서 보고서 서버 데이터베이스에 연결하는 데 사용하는 연결 정보를 수정하려는 경우</span><span class="sxs-lookup"><span data-stu-id="5eeeb-169">To modify the connection information that a report server uses to connect to a report server database.</span></span>  
  
-   <span data-ttu-id="5eeeb-170">다른 자격 증명을 사용할 수 없을 때 보고서 서버에서 원격 데이터베이스 서버에 로그온하는 데 사용하는 특수 계정을 구성하려는 경우</span><span class="sxs-lookup"><span data-stu-id="5eeeb-170">To configure a special account that the report server uses to log on to a remote database server when other credentials are not available.</span></span>  
  
 <span data-ttu-id="5eeeb-171">**의 로컬 또는 원격 인스턴스에서** rsconfig [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]유틸리티를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-171">You can run the**rsconfig** utility on a local or remote instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="5eeeb-172">이미 설정된 값을 해독하고 보는 데 **rsconfig** 유틸리티를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-172">You cannot use the **rsconfig** utility to decrypt and view values that are already set.</span></span>  
  
 <span data-ttu-id="5eeeb-173">이 유틸리티를 실행하려면 구성 중인 컴퓨터에 WMI(Windows Management Instrumentation)가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-173">Before you can run this utility, Windows Management Instrumentation (WMI) must be installed on the computer that you are configuring.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5eeeb-174">예</span><span class="sxs-lookup"><span data-stu-id="5eeeb-174">Examples</span></span>  
 <span data-ttu-id="5eeeb-175">다음 예에서는 **rsconfig**를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-175">The following examples illustrate ways of using **rsconfig**.</span></span>  
  
#### <a name="specifying-a-domain-user-account"></a><span data-ttu-id="5eeeb-176">도메인 사용자 계정 지정</span><span class="sxs-lookup"><span data-stu-id="5eeeb-176">Specifying a Domain User Account</span></span>  
 <span data-ttu-id="5eeeb-177">이 예에서는 로컬 보고서 서버 데이터베이스에 연결할 때 도메인 사용자 계정을 사용하도록 보고서 서버를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-177">This example shows how to configure a report server to use a domain user account when connecting to a local report server database.</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows -u <MYDOMAIN\MYACCOUNT> -p <PASSWORD>  
```  
  
#### <a name="specifying-a-sql-server-database-user-account"></a><span data-ttu-id="5eeeb-178">SQL Server 데이터베이스 사용자 계정 지정</span><span class="sxs-lookup"><span data-stu-id="5eeeb-178">Specifying a SQL Server Database User Account</span></span>  
 <span data-ttu-id="5eeeb-179">이 예에서는 원격 보고서 서버 데이터베이스에 연결할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 사용하도록 보고서 서버를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-179">This example shows how to configure a report server to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to connect to a remote report server database.</span></span>  
  
```  
rsconfig -c -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -d reportserver -a SQL -u SA -p <SAPASSWORD>  
```  
  
#### <a name="specifying-a-built-in-account"></a><span data-ttu-id="5eeeb-180">기본 제공 계정 지정</span><span class="sxs-lookup"><span data-stu-id="5eeeb-180">Specifying a Built-in Account</span></span>  
 <span data-ttu-id="5eeeb-181">이 예에서는 로컬 보고서 서버 데이터베이스에 연결할 때 기본 제공 계정을 사용하도록 보고서 서버를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-181">This example shows how to configure a report server to use a built-in account when connecting to a local report server database.</span></span> <span data-ttu-id="5eeeb-182">`-u`는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-182">Notice that `-u` is not used.</span></span> <span data-ttu-id="5eeeb-183">지원 되는 기본 제공 계정 값의 예에는 로컬 시스템에 대 한 NT 권한 및 네트워크 서비스용 NT AUTHORITY\NETWORKSERVICE (전용)가 포함 됩니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5eeeb-183">Examples of supported built-in account values include NT AUTHORITY\SYSTEM for Local System and NT AUTHORITY\NETWORKSERVICE for Network Service ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] only).</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows "NT AUTHORITY\SYSTEM"  
```  
  
#### <a name="specifying-a-service-account"></a><span data-ttu-id="5eeeb-184">서비스 계정 지정</span><span class="sxs-lookup"><span data-stu-id="5eeeb-184">Specifying a Service Account</span></span>  
 <span data-ttu-id="5eeeb-185">이 예에서는 로컬 보고서 서버 데이터베이스에 연결할 때 보고서 서버 Windows 서비스 계정 및 웹 서비스 계정을 사용하도록 보고서 서버를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-185">This example shows how to configure a report server to use the Report Server Windows service account and Web service account when connecting to a local report server database.</span></span> <span data-ttu-id="5eeeb-186">`-u`는 사용되지 않으며 계정 정보를 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-186">Notice that `-u` is not used and that no account information is specified.</span></span> <span data-ttu-id="5eeeb-187">명령에서 계정 값을 제거하는 경우 **rsconfig** 유틸리티는 각 서비스를 실행하는 통합된 보안 및 서비스 계정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-187">When you eliminate account values from the command, the **rsconfig** utility uses integrated security and the service account that each service runs under.</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows  
```  
  
#### <a name="specifying-the-unattended-account-on-a-local-server"></a><span data-ttu-id="5eeeb-188">로컬 서버에서 무인 계정 지정</span><span class="sxs-lookup"><span data-stu-id="5eeeb-188">Specifying the Unattended Account on a Local Server</span></span>  
 <span data-ttu-id="5eeeb-189">이 예에서는 외부 데이터 원본으로 자격 증명을 전달하지 않는 보고서의 무인 보고서 실행에 사용되는 계정을 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-189">This example shows how to configure the account used for unattended report execution for reports that do not pass credentials to the external data source.</span></span> <span data-ttu-id="5eeeb-190">이 계정은 Windows 도메인 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-190">The account must be a Windows domain account.</span></span> <span data-ttu-id="5eeeb-191">사용자 이름 및 암호에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-191">You cannot specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for the user name and password.</span></span> <span data-ttu-id="5eeeb-192">이 계정은 로컬 보고서 서버 인스턴스에서 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-192">The account is configured on a local report server instance.</span></span> <span data-ttu-id="5eeeb-193">ReportingServices\LogFiles 폴더의 추적 로그에 오류 메시지가 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-193">Error messages are captured in the trace logs in the ReportingServices\LogFiles folder.</span></span>  
  
```  
rsconfig -e -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
#### <a name="specifying-the-unattended-account-on-a-remote-server"></a><span data-ttu-id="5eeeb-194">원격 서버에서 무인 계정 지정</span><span class="sxs-lookup"><span data-stu-id="5eeeb-194">Specifying the Unattended Account on a Remote Server</span></span>  
 <span data-ttu-id="5eeeb-195">이 예에서는 Rsconfig.exe와 같은 버전의 원격 보고서 서버 인스턴스에서 계정을 구성하는 방법을 보여 줍니다(예: 보고서 서버와 Rsconfig.exe가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 버전인 경우).</span><span class="sxs-lookup"><span data-stu-id="5eeeb-195">This example shows how to configure the account on a remote report server instance that is the same version as Rsconfig.exe (for example, the report server and Rsconfig.exe are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 version).</span></span> <span data-ttu-id="5eeeb-196">원격 서버의 추적 로그에 오류 메시지 정보가 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="5eeeb-196">Error message information is captured in the trace logs on the remote server.</span></span>  
  
```  
rsconfig -e -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
## <a name="see-also"></a><span data-ttu-id="5eeeb-197">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5eeeb-197">See Also</span></span>  
 <span data-ttu-id="5eeeb-198">[SSRS Configuration Manager &#40;보고서 서버 데이터베이스 연결 구성&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5eeeb-198">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="5eeeb-199">[SSRS Configuration Manager &#40;무인 실행 계정을 구성&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5eeeb-199">[Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="5eeeb-200">[Reporting Services 보고서 서버&#40;기본 모드&#41;](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="5eeeb-200">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="5eeeb-201">[암호화된 보고서 서버 데이터 저장&#40;SSRS 구성 관리자&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="5eeeb-201">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 <span data-ttu-id="5eeeb-202">[Reporting Services 구성 파일](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="5eeeb-202">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="5eeeb-203">[SSRS&#41;&#40;보고서 서버 명령 프롬프트 유틸리티](report-server-command-prompt-utilities-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5eeeb-203">[Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span></span>  
 [<span data-ttu-id="5eeeb-204">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="5eeeb-204">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
