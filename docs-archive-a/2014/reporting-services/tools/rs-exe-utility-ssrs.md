---
title: RS.exe 유틸리티(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- automatic report server tasks
- rs utility
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], automating tasks
- command prompt utilities [SQL Server], rs
- scripts [Reporting Services], command prompt
- deploying reports [Reporting Services]
ms.assetid: bd6f958f-cce6-4e79-8a0f-9475da2919ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bcf21a1bf2453d2bd1f0644e31ca46f3f94e6884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735992"
---
# <a name="rsexe-utility-ssrs"></a><span data-ttu-id="7fee8-102">RS.exe 유틸리티(SSRS)</span><span class="sxs-lookup"><span data-stu-id="7fee8-102">RS.exe Utility (SSRS)</span></span>
  <span data-ttu-id="7fee8-103">RS.exe 유틸리티에서는 입력 파일에 제공된 스크립트를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-103">The rs.exe utility processes script that you provide in an input file.</span></span> <span data-ttu-id="7fee8-104">이 유틸리티를 사용하여 보고서 서버 배포 및 관리 태스크를 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-104">Use this utility to automate report server deployment and administration tasks.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7fee8-105">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]부터는 **rs** 유틸리티가 SharePoint 통합 모드용으로 구성된 보고서 서버와 기본 모드에서 구성된 서버에 대해 모두 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-105">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], the **rs** utility is supported against report servers that are configured for SharePoint integrated mode as well as servers configured in native mode.</span></span> <span data-ttu-id="7fee8-106">이전 버전에서는 기본 모드 구성만 지원되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-106">Previous versions only supported native mode configurations.</span></span>  
  
 <span data-ttu-id="7fee8-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="7fee8-107">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="7fee8-108">파일 위치</span><span class="sxs-lookup"><span data-stu-id="7fee8-108">File Location</span></span>](#bkmk_filelocation)  
  
-   [<span data-ttu-id="7fee8-109">인수</span><span class="sxs-lookup"><span data-stu-id="7fee8-109">Arguments</span></span>](#bkmk_arguments)  
  
-   [<span data-ttu-id="7fee8-110">권한</span><span class="sxs-lookup"><span data-stu-id="7fee8-110">Permissions</span></span>](#bkmk_permissions)  
  
-   [<span data-ttu-id="7fee8-111">예</span><span class="sxs-lookup"><span data-stu-id="7fee8-111">Examples</span></span>](#bkmk_examples)  
  
## <a name="syntax"></a><span data-ttu-id="7fee8-112">구문</span><span class="sxs-lookup"><span data-stu-id="7fee8-112">Syntax</span></span>  
  
```  
  
      rs {-?}  
{-i input_file=}  
{-s serverURL}  
{-u username}  
{-p password}  
{-e endpoint}  
{-l time_out}  
{-b batchmode}  
{-v globalvars=}  
{-t trace}  
```  
  
##  <a name="file-location"></a><a name="bkmk_filelocation"></a> <span data-ttu-id="7fee8-113">파일 위치</span><span class="sxs-lookup"><span data-stu-id="7fee8-113">File Location</span></span>  
 <span data-ttu-id="7fee8-114">**RS.exe** 는 **\Program Files\Microsoft SQL Server\110\Tools\Binn**에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-114">**RS.exe** is located at **\Program Files\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="7fee8-115">파일 시스템의 모든 폴더에서 유틸리티를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-115">You can run the utility from any folder on your file system.</span></span>  
  
##  <a name="arguments"></a><a name="bkmk_arguments"></a> <span data-ttu-id="7fee8-116">인수</span><span class="sxs-lookup"><span data-stu-id="7fee8-116">Arguments</span></span>  
 <span data-ttu-id="7fee8-117">**-?**</span><span class="sxs-lookup"><span data-stu-id="7fee8-117">**-?**</span></span>  
 <span data-ttu-id="7fee8-118">(옵션) **rs** 인수의 구문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-118">(Optional) Displays the syntax of **rs** arguments.</span></span>  
  
 <span data-ttu-id="7fee8-119">`-i`*input_file*</span><span class="sxs-lookup"><span data-stu-id="7fee8-119">`-i` *input_file*</span></span>  
 <span data-ttu-id="7fee8-120">실행할 .rss 파일을 지정합니다(필수).</span><span class="sxs-lookup"><span data-stu-id="7fee8-120">(Required) Specifies the .rss file to execute.</span></span> <span data-ttu-id="7fee8-121">이 값은 .rss 파일의 상대 경로 또는 정규화된 경로여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-121">This value can be a relative or fully qualified path to the .rss file.</span></span>  
  
 <span data-ttu-id="7fee8-122">`-s`*serverURL*</span><span class="sxs-lookup"><span data-stu-id="7fee8-122">`-s` *serverURL*</span></span>  
 <span data-ttu-id="7fee8-123">파일을 실행할 웹 서버 이름 및 보고서 서버 가상 디렉터리를 지정합니다(필수).</span><span class="sxs-lookup"><span data-stu-id="7fee8-123">(Required) Specifies the Web server name and report server virtual directory name to execute the file against.</span></span> <span data-ttu-id="7fee8-124">보고서 서버 URL의 예는 `http://examplewebserver/reportserver`입니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-124">An example of a report server URL is `http://examplewebserver/reportserver`.</span></span> <span data-ttu-id="7fee8-125">서버 이름의 시작 부분에 붙는 접두사 http:// 또는 https://는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-125">The prefix http:// or https:// at the beginning of the server name is optional.</span></span> <span data-ttu-id="7fee8-126">이를 생략하면 보고서 서버 스크립트 호스트에서 https를 먼저 사용해 본 다음 작동하지 않는 경우 http를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-126">If you omit the prefix, the report server script host tries to use https first, and then uses http if https does not work.</span></span>  
  
 <span data-ttu-id="7fee8-127">`-u`[*도메인* \\ ] *사용자 이름*</span><span class="sxs-lookup"><span data-stu-id="7fee8-127">`-u` [*domain*\\]*username*</span></span>  
 <span data-ttu-id="7fee8-128">보고서 서버에 연결하는 데 사용되는 사용자 계정을 지정합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="7fee8-128">(Optional) Specifies a user account used to connect to the report server.</span></span> <span data-ttu-id="7fee8-129">`-u`와 `-p`를 생략하면 현재 Windows 사용자 계정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-129">If `-u` and `-p` are omitted, the current Windows user account is used.</span></span>  
  
 <span data-ttu-id="7fee8-130">`-p`*암호*</span><span class="sxs-lookup"><span data-stu-id="7fee8-130">`-p` *password*</span></span>  
 <span data-ttu-id="7fee8-131">`-u` 인수에 사용할 암호를 지정합니다(`-u`를 지정한 경우 필수).</span><span class="sxs-lookup"><span data-stu-id="7fee8-131">(Required if `-u` is specified) Specifies the password to use with the `-u` argument.</span></span> <span data-ttu-id="7fee8-132">이 값은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-132">This value is case-sensitive.</span></span>  
  
 `-e`  
 <span data-ttu-id="7fee8-133">스크립트가 실행되어야 하는 대상 SOAP 엔드포인트를 지정합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="7fee8-133">(Optional) Specifies the SOAP endpoint against which the script should run.</span></span> <span data-ttu-id="7fee8-134">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-134">Valid values are the following:</span></span>  
  
-   <span data-ttu-id="7fee8-135">Mgmt2010</span><span class="sxs-lookup"><span data-stu-id="7fee8-135">Mgmt2010</span></span>  
  
-   <span data-ttu-id="7fee8-136">Mgmt2006</span><span class="sxs-lookup"><span data-stu-id="7fee8-136">Mgmt2006</span></span>  
  
-   <span data-ttu-id="7fee8-137">Mgmt2005</span><span class="sxs-lookup"><span data-stu-id="7fee8-137">Mgmt2005</span></span>  
  
-   <span data-ttu-id="7fee8-138">Exec2005</span><span class="sxs-lookup"><span data-stu-id="7fee8-138">Exec2005</span></span>  
  
 <span data-ttu-id="7fee8-139">값이 지정되지 않은 경우 Mgmt2005가 엔드포인트로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-139">If a value is not specified, the Mgmt2005 endpoint is used.</span></span> <span data-ttu-id="7fee8-140">SOAP 엔드포인트에 대한 자세한 내용은 [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fee8-140">For more information about the SOAP endpoints, see [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md).</span></span>  
  
 <span data-ttu-id="7fee8-141">`-l`*time_out*</span><span class="sxs-lookup"><span data-stu-id="7fee8-141">`-l` *time_out*</span></span>  
 <span data-ttu-id="7fee8-142">필드 서버에 대 한 연결 제한 시간이 초과 되기 전 까지의 시간 (초)을 지정 합니다. 기본값은 60 초입니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-142">(Optional) Specifies the number of seconds that elapse before the connection to the server times out. The default is 60 seconds.</span></span> <span data-ttu-id="7fee8-143">시간 제한 값을 지정하지 않으면 이 기본값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-143">If you do not specify a time-out value, the default is used.</span></span> <span data-ttu-id="7fee8-144">값을 `0`으로 지정하면 연결 시간 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-144">A value of `0` specifies that the connection never times out.</span></span>  
  
 <span data-ttu-id="7fee8-145">**-b**</span><span class="sxs-lookup"><span data-stu-id="7fee8-145">**-b**</span></span>  
 <span data-ttu-id="7fee8-146">스크립트 파일의 명령이 일괄적으로 실행되도록 지정합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="7fee8-146">(Optional) Specifies that the commands in the script file run in a batch.</span></span> <span data-ttu-id="7fee8-147">실패하는 명령이 있으면 이 일괄 처리가 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-147">If any commands fail, the batch is rolled back.</span></span> <span data-ttu-id="7fee8-148">일부 명령은 일괄 처리 방식이 아닌 일반적인 방식으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-148">Some commands cannot be batched, and those run as usual.</span></span> <span data-ttu-id="7fee8-149">스크립트 내에서 발생되며 처리되지 않는 예외만 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-149">Only exceptions that are thrown and are not handled within the script result in a rollback.</span></span> <span data-ttu-id="7fee8-150">스크립트가 예외를 처리하고 `Main`에서 정상적으로 반환되는 경우 일괄 처리가 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-150">If the script handles an exception and returns normally from `Main`, the batch is committed.</span></span> <span data-ttu-id="7fee8-151">이 매개 변수를 생략하면 명령이 일괄 처리를 만들지 않고 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-151">If you omit this parameter, the commands run without creating a batch.</span></span> <span data-ttu-id="7fee8-152">자세한 내용은 [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fee8-152">For more information, see [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md).</span></span>  
  
 <span data-ttu-id="7fee8-153">`-v` *globalvar*</span><span class="sxs-lookup"><span data-stu-id="7fee8-153">`-v` *globalvar*</span></span>  
 <span data-ttu-id="7fee8-154">스크립트에서 사용되는 전역 변수를 지정합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="7fee8-154">(Optional) Specifies global variables that are used in the script.</span></span> <span data-ttu-id="7fee8-155">스크립트에서 전역 변수가 사용되는 경우에는 이 인수를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-155">If the script uses global variables, you must specify this argument.</span></span> <span data-ttu-id="7fee8-156">지정하는 값은 .rss 파일에 정의되는 전역 변수에 대해 유효해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-156">The value that you specify must be valid for global variable defined in the .rss file.</span></span> <span data-ttu-id="7fee8-157">각 **-v** 인수에 대해 하나의 전역 변수를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-157">You must specify one global variable for each **-v** argument.</span></span>  
  
 <span data-ttu-id="7fee8-158">`-v` 인수는 명령줄에서 지정되며 런타임에 스크립트에 정의된 전역 변수의 값을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-158">The `-v` argument is specified on the command line and is used to set the value for a global variable that is defined in your script at run time.</span></span> <span data-ttu-id="7fee8-159">예를 들어 스크립트에 *parentFolder*라는 변수가 포함되어 있다면 다음과 같이 명령줄에서 해당 폴더에 대한 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-159">For example, if your script contains a variable named *parentFolder*, you can specify a name for that folder on the command line:</span></span>  
  
 `rs.exe -i myScriptFile.rss -s http://myServer/reportserver -v parentFolder="Financial Reports"`  
  
 <span data-ttu-id="7fee8-160">전역 변수가 지정한 이름으로 생성된 다음 제공된 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-160">Global variables are created with the names given and set to the values supplied.</span></span> <span data-ttu-id="7fee8-161">예를 들어 **-v a =**" `1` " **-v b =**" `2` "는 값이 " `a` " 인 변수 `1` 및 값이 "" 인 변수 **b** 를 반환 `2` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-161">For example, **-v a=**"`1`" **-v b=**"`2`" results in a variable named `a` with a value of"`1`" and a variable **b** with a value of "`2`".</span></span>  
  
 <span data-ttu-id="7fee8-162">전역 변수는 스크립트의 모든 함수에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-162">Global variables are available to any function in the script.</span></span> <span data-ttu-id="7fee8-163">백슬래시와 따옴표 (\*\* \\ "\*\*)는 큰따옴표로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-163">A backslash and quotation mark (**\\"**) is interpreted as a double quotation mark.</span></span> <span data-ttu-id="7fee8-164">인용 부호는 문자열에 공백이 포함되어 있는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-164">The quotation marks are required only if the string contains a space.</span></span> <span data-ttu-id="7fee8-165">변수 이름은에 유효 해야 하며 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 알파벳 문자 또는 밑줄로 시작 하 고 알파벳 문자, 숫자 또는 밑줄이 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-165">Variable names must be valid for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]; they must start with alphabetical character or underscore and contain alphabetical characters, digits, or underscores.</span></span> <span data-ttu-id="7fee8-166">예약어는 변수 이름으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-166">Reserved words cannot be used as variable names.</span></span> <span data-ttu-id="7fee8-167">전역 변수 사용에 대한 자세한 내용은 [식의 기본 제공 컬렉션&#40;보고서 작성기 및 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fee8-167">For more information about using global variables, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
 <span data-ttu-id="7fee8-168">**-t**</span><span class="sxs-lookup"><span data-stu-id="7fee8-168">**-t**</span></span>  
 <span data-ttu-id="7fee8-169">추적 로그에 오류 메시지를 출력합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="7fee8-169">(Optional) Outputs error messages to the trace log.</span></span> <span data-ttu-id="7fee8-170">이 인수는 값을 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-170">This argument does not take a value.</span></span> <span data-ttu-id="7fee8-171">자세한 내용은 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fee8-171">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>  
  
##  <a name="permissions"></a><a name="bkmk_permissions"></a> <span data-ttu-id="7fee8-172">권한</span><span class="sxs-lookup"><span data-stu-id="7fee8-172">Permissions</span></span>  
 <span data-ttu-id="7fee8-173">이 도구를 사용하려면 스크립트를 실행하는 보고서 서버 인스턴스에 연결할 수 있는 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-173">To run the tool, you must have permission to connect to the report server instance you are running the script against.</span></span> <span data-ttu-id="7fee8-174">스크립트를 실행하여 로컬 컴퓨터나 원격 컴퓨터를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-174">You can run scripts to make changes to the local computer or a remote computer.</span></span> <span data-ttu-id="7fee8-175">원격 컴퓨터에 설치된 보고서 서버를 변경하려면 `-s` 인수에 원격 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-175">To make changes to a report server installed on a remote computer, specify the remote computer in the `-s` argument.</span></span>  
  
##  <a name="examples"></a><a name="bkmk_examples"></a> <span data-ttu-id="7fee8-176">예</span><span class="sxs-lookup"><span data-stu-id="7fee8-176">Examples</span></span>  
 <span data-ttu-id="7fee8-177">다음 예에서는 실행할 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET 스크립트 및 웹 서비스 메서드가 포함된 스크립트 파일을 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-177">The following example illustrates how to specify the script file that contains [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET script and Web service methods that you want to execute.</span></span>  
  
```  
rs -i c:\scriptfiles\script_copycontent.rss -s http://localhost/reportserver  
```  
  
 <span data-ttu-id="7fee8-178"> 자세한 예는 [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fee8-178">For a detailed example, see [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
 <span data-ttu-id="7fee8-179">추가 예제는 [Reporting Services 스크립트 파일 실행](run-a-reporting-services-script-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fee8-179">For additional examples, see [Run a Reporting Services Script File](run-a-reporting-services-script-file.md)</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fee8-180">설명</span><span class="sxs-lookup"><span data-stu-id="7fee8-180">Remarks</span></span>  
 <span data-ttu-id="7fee8-181">시스템 속성을 설정하고 보고서를 게시하는 등의 스크립트를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-181">You can define scripts to set system properties, publish reports, and so forth.</span></span> <span data-ttu-id="7fee8-182">생성된 스크립트에는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API의 모든 메서드가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-182">The scripts that you create can include any methods of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API.</span></span> <span data-ttu-id="7fee8-183">사용할 수 있는 메서드 및 속성에 대한 자세한 내용은 [Report Server Web Service](../report-server-web-service/report-server-web-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fee8-183">For more information about the methods and properties available to you, see [Report Server Web Service](../report-server-web-service/report-server-web-service.md).</span></span>  
  
 <span data-ttu-id="7fee8-184">이 스크립트는 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET 코드로 작성하여 파일 이름 확장명이 .rss인 유니코드 또는 UTF-8 텍스트 파일로 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-184">The script must be written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET code, and stored in a Unicode or UTF-8 text file with an .rss file name extension.</span></span> <span data-ttu-id="7fee8-185">**rs** 유틸리티를 사용하여 스크립트를 디버깅할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-185">You cannot debug scripts with the **rs** utility.</span></span> <span data-ttu-id="7fee8-186">스크립트를 디버깅 하려면에서 코드를 실행 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fee8-186">To debug a script, run the code within [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="7fee8-187"> 자세한 예는 [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fee8-187">For a detailed example, see [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fee8-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7fee8-188">See Also</span></span>  
 <span data-ttu-id="7fee8-189">[Reporting Services 스크립트 파일 실행](run-a-reporting-services-script-file.md) </span><span class="sxs-lookup"><span data-stu-id="7fee8-189">[Run a Reporting Services Script File](run-a-reporting-services-script-file.md) </span></span>  
 <span data-ttu-id="7fee8-190">[배포 및 관리 태스크 스크립팅](script-deployment-and-administrative-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="7fee8-190">[Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) </span></span>  
 <span data-ttu-id="7fee8-191">[rs.exe 유틸리티 및 웹 서비스를 사용한 스크립팅](script-with-the-rs-exe-utility-and-the-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="7fee8-191">[Script with the rs.exe Utility and the Web Service](script-with-the-rs-exe-utility-and-the-web-service.md) </span></span>  
 [<span data-ttu-id="7fee8-192">보고서 서버 명령 프롬프트 유틸리티&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7fee8-192">Report Server Command Prompt Utilities &#40;SSRS&#41;</span></span>](report-server-command-prompt-utilities-ssrs.md)  
  
  
