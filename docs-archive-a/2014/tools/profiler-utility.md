---
title: 프로파일러 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], profiler90 utility
- profiler90 utility
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: e91c30a9-0d29-4f84-bcb8-e8fb62afadda
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8df3e8557bb52839d17291bae0c5ba507d0a671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727611"
---
# <a name="profiler-utility"></a><span data-ttu-id="2fb6d-102">프로파일러 유틸리티</span><span class="sxs-lookup"><span data-stu-id="2fb6d-102">Profiler Utility</span></span>
  <span data-ttu-id="2fb6d-103">**profiler** 유틸리티는 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 도구를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-103">The **profiler** utility launches the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] tool.</span></span> <span data-ttu-id="2fb6d-104">이 항목에서 나중에 나열된 옵션 인수를 사용하여 애플리케이션 시작 방법을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-104">The optional arguments listed later in this topic allow you to control how the application starts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2fb6d-105">**profiler** 유틸리티는 추적 스크립팅을 위한 유틸리티가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-105">The **profiler** utility is not intended for scripting traces.</span></span> <span data-ttu-id="2fb6d-106">자세한 내용은 [SQL Server Profiler](sql-server-profiler/sql-server-profiler.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-106">For more information, see [SQL Server Profiler](sql-server-profiler/sql-server-profiler.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fb6d-107">구문</span><span class="sxs-lookup"><span data-stu-id="2fb6d-107">Syntax</span></span>  
  
```  
  
      profiler  
          [ /? ] |  
[  
{  
{ /U login_id [ /P password ] }  
| /E  
}  
{[ /S sql_server_name ] | [ /A analysis_services_server_name ] }  
[ /D database ]  
[ /T "template_name" ]  
[ /B { "trace_table_name" } ]  
{ [/F "filename" ] | [ /O "filename" ] }  
[ /L locale_ID ]  
[ /M "MM-DD-YY hh:mm:ss" ]  
[ /R ]  
[ /Z file_size ]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2fb6d-108">인수</span><span class="sxs-lookup"><span data-stu-id="2fb6d-108">Arguments</span></span>  
 <span data-ttu-id="2fb6d-109">**/?**</span><span class="sxs-lookup"><span data-stu-id="2fb6d-109">**/?**</span></span>  
 <span data-ttu-id="2fb6d-110">**profiler** 인수의 구문 요약 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-110">Displays the syntax summary of **profiler** arguments.</span></span>  
  
 <span data-ttu-id="2fb6d-111">**/U** *login_id*</span><span class="sxs-lookup"><span data-stu-id="2fb6d-111">**/U** *login_id*</span></span>  
 <span data-ttu-id="2fb6d-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 위한 사용자 로그인 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-112">Is the user login ID for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="2fb6d-113">로그인 ID는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-113">Login IDs are case sensitive.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]<span data-ttu-id="2fb6d-114">.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-114">.</span></span>  
  
 <span data-ttu-id="2fb6d-115">**/P** *password*</span><span class="sxs-lookup"><span data-stu-id="2fb6d-115">**/P** *password*</span></span>  
 <span data-ttu-id="2fb6d-116">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 위한 암호를 지정합니다. 사용자가 원하는 대로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-116">Specifies a user-specified password for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="2fb6d-117">**/E**</span><span class="sxs-lookup"><span data-stu-id="2fb6d-117">**/E**</span></span>  
 <span data-ttu-id="2fb6d-118">현재 사용자의 자격 증명으로 Windows 인증을 사용하는 연결을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-118">Specifies connecting with Windows Authentication with the current user's credentials.</span></span>  
  
 <span data-ttu-id="2fb6d-119">**/S**  *sql_server_name*</span><span class="sxs-lookup"><span data-stu-id="2fb6d-119">**/S**  *sql_server_name*</span></span>  
 <span data-ttu-id="2fb6d-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-120">Specifies an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2fb6d-121">프로파일러는 지정된 **/U** 및 **/P** 스위치 또는 **/E** 스위치에서 지정된 인증 정보를 사용하여 지정된 서버에 자동으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-121">Profiler will automatically connect to the specified server using the authentication information specified in the **/U** and **/P** switches or the **/E** switch.</span></span> <span data-ttu-id="2fb6d-122">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 명명된 인스턴스에 연결하려면 **/S** *sql_server_name*\\*instance_name*을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-122">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use **/S** *sql_server_name*\\*instance_name*.</span></span>  
  
 <span data-ttu-id="2fb6d-123">**/A**  *analysis_services_server_name*</span><span class="sxs-lookup"><span data-stu-id="2fb6d-123">**/A**  *analysis_services_server_name*</span></span>  
 <span data-ttu-id="2fb6d-124">Analysis Services 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-124">Specifies an instance of Analysis Services.</span></span> <span data-ttu-id="2fb6d-125">프로파일러는 지정된 **/U** 및 **/P** 스위치 또는 **/E** 스위치에서 지정된 인증 정보를 사용하여 지정된 서버에 자동으로 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-125">Profiler will automatically connect to the specified server using the authentication information specified in the **/U** and **/P** switches or the **/E** switch.</span></span> <span data-ttu-id="2fb6d-126">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 명명된 인스턴스에 연결하려면 **/A** *analysis_services_server_name\instance_name*을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-126">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] use **/A** *analysis_services_server_name\instance_name*.</span></span>  
  
 <span data-ttu-id="2fb6d-127">**/D** *database*</span><span class="sxs-lookup"><span data-stu-id="2fb6d-127">**/D** *database*</span></span>  
 <span data-ttu-id="2fb6d-128">연결에 사용할 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-128">Specifies the name of the database to be used with the connection.</span></span> <span data-ttu-id="2fb6d-129">데이터베이스를 지정하지 않으면 이 옵션은 지정된 사용자의 기본 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-129">This option will select the default database for the specified user if no database is specified.</span></span>  
  
 <span data-ttu-id="2fb6d-130">**/B "** *trace_table_name* **"**</span><span class="sxs-lookup"><span data-stu-id="2fb6d-130">**/B "** *trace_table_name* **"**</span></span>  
 <span data-ttu-id="2fb6d-131">프로파일러를 시작할 때 로드할 추적 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-131">Specifies a trace table to load when the profiler is launched.</span></span> <span data-ttu-id="2fb6d-132">데이터베이스, 사용자나 스키마 및 테이블을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-132">You must specify the database, the user or schema, and the table.</span></span>  
  
 <span data-ttu-id="2fb6d-133">**/T"** *template_name* **"**</span><span class="sxs-lookup"><span data-stu-id="2fb6d-133">**/T"** *template_name* **"**</span></span>  
 <span data-ttu-id="2fb6d-134">추적을 구성하기 위해 로드할 템플릿을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-134">Specifies the template that will be loaded to configure the trace.</span></span> <span data-ttu-id="2fb6d-135">템플릿 이름을 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-135">The template name must be in quotes.</span></span> <span data-ttu-id="2fb6d-136">또한 템플릿 이름은 시스템 템플릿 디렉터리나 사용자 템플릿 디렉터리에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-136">The template name must be in either the system template directory or the user template directory.</span></span> <span data-ttu-id="2fb6d-137">두 디렉터리에 이름이 같은 템플릿 두 개가 있을 경우 시스템 디렉터리의 템플릿이 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-137">If two templates with the same name exist in both directories, the template from the system directory will be loaded.</span></span> <span data-ttu-id="2fb6d-138">지정한 이름의 템플릿이 없을 경우 표준 템플릿이 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-138">If no template with the specified name exists, the standard template will be loaded.</span></span> <span data-ttu-id="2fb6d-139">*template_name*에 템플릿의 파일 확장명(.tdf)을 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-139">Note that the file extension for the template (.tdf) should not be specified as part of the *template_name*.</span></span> <span data-ttu-id="2fb6d-140">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-140">For example:</span></span>  
  
```  
/T "standard"  
```  
  
 <span data-ttu-id="2fb6d-141">**/F"** *filename* **"**</span><span class="sxs-lookup"><span data-stu-id="2fb6d-141">**/F"** *filename* **"**</span></span>  
 <span data-ttu-id="2fb6d-142">프로파일러를 시작할 때 로드할 추적 파일의 경로와 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-142">Specifies the path and filename of a trace file to load when profiler is launched.</span></span> <span data-ttu-id="2fb6d-143">전체 경로 및 파일 이름은 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-143">The entire path and filename must be in quotes.</span></span> <span data-ttu-id="2fb6d-144">이 옵션은 **/O**와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-144">This option cannot be used with **/O**.</span></span>  
  
 <span data-ttu-id="2fb6d-145">**/O "** *filename*  **"**</span><span class="sxs-lookup"><span data-stu-id="2fb6d-145">**/O "** *filename*  **"**</span></span>  
 <span data-ttu-id="2fb6d-146">추적 결과를 기록할 파일의 경로와 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-146">Specifies the path and filename of a file to which trace results should be written.</span></span> <span data-ttu-id="2fb6d-147">전체 경로 및 파일 이름은 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-147">The entire path and filename must be in quotes.</span></span> <span data-ttu-id="2fb6d-148">이 옵션은 **/F**와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-148">This option cannot be used with **/F.**</span></span>  
  
 <span data-ttu-id="2fb6d-149">**/L** *locale_ID*</span><span class="sxs-lookup"><span data-stu-id="2fb6d-149">**/L** *locale_ID*</span></span>  
 <span data-ttu-id="2fb6d-150">사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-150">Not available.</span></span>  
  
 <span data-ttu-id="2fb6d-151">**/M "** *MM-DD-YY hh:mm:ss* **"**</span><span class="sxs-lookup"><span data-stu-id="2fb6d-151">**/M "** *MM-DD-YY hh:mm:ss* **"**</span></span>  
 <span data-ttu-id="2fb6d-152">추적을 중지할 날짜와 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-152">Specifies the date and time for the trace to stop.</span></span> <span data-ttu-id="2fb6d-153">중지 시간을 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-153">The stop time must be in quotes.</span></span> <span data-ttu-id="2fb6d-154">아래 표의 매개 변수에 따라 중지 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-154">Specify the stop time according to the parameters in the table below:</span></span>  
  
|<span data-ttu-id="2fb6d-155">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2fb6d-155">Parameter</span></span>|<span data-ttu-id="2fb6d-156">정의</span><span class="sxs-lookup"><span data-stu-id="2fb6d-156">Definition</span></span>|  
|---------------|----------------|  
|<span data-ttu-id="2fb6d-157">MM</span><span class="sxs-lookup"><span data-stu-id="2fb6d-157">MM</span></span>|<span data-ttu-id="2fb6d-158">두 자릿수 월</span><span class="sxs-lookup"><span data-stu-id="2fb6d-158">Two-digit month</span></span>|  
|<span data-ttu-id="2fb6d-159">DD</span><span class="sxs-lookup"><span data-stu-id="2fb6d-159">DD</span></span>|<span data-ttu-id="2fb6d-160">두 자릿수 일</span><span class="sxs-lookup"><span data-stu-id="2fb6d-160">Two-digit day</span></span>|  
|<span data-ttu-id="2fb6d-161">YY</span><span class="sxs-lookup"><span data-stu-id="2fb6d-161">YY</span></span>|<span data-ttu-id="2fb6d-162">두 자릿수 연도</span><span class="sxs-lookup"><span data-stu-id="2fb6d-162">Two-digit year</span></span>|  
|<span data-ttu-id="2fb6d-163">hh</span><span class="sxs-lookup"><span data-stu-id="2fb6d-163">hh</span></span>|<span data-ttu-id="2fb6d-164">24시간제의 두 자릿수 시간</span><span class="sxs-lookup"><span data-stu-id="2fb6d-164">Two-digit hour on a 24-hour clock</span></span>|  
|<span data-ttu-id="2fb6d-165">MM</span><span class="sxs-lookup"><span data-stu-id="2fb6d-165">mm</span></span>|<span data-ttu-id="2fb6d-166">두 자릿수 분</span><span class="sxs-lookup"><span data-stu-id="2fb6d-166">Two-digit minute</span></span>|  
|<span data-ttu-id="2fb6d-167">ss</span><span class="sxs-lookup"><span data-stu-id="2fb6d-167">ss</span></span>|<span data-ttu-id="2fb6d-168">두 자릿수 초</span><span class="sxs-lookup"><span data-stu-id="2fb6d-168">Two-digit second</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="2fb6d-169">**에서** 날짜 및 시간 값 표시에 국가별 설정 사용 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]옵션이 설정되어 있는 경우 "MM-DD-YY hh:mm:ss" 형식만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-169">The "MM-DD-YY hh:mm:ss" format can only be used if the **Use regional settings to display date and time values** option is enabled in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="2fb6d-170">이 옵션이 설정되어 있지 않은 경우 "YYYY-MM-DD hh:mm:ss" 날짜 및 시간 형식을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-170">If this option is not enabled, you must use the "YYYY-MM-DD hh:mm:ss" date and time format.</span></span>  
  
 <span data-ttu-id="2fb6d-171">**/R**</span><span class="sxs-lookup"><span data-stu-id="2fb6d-171">**/R**</span></span>  
 <span data-ttu-id="2fb6d-172">추적 파일 롤오버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-172">Enables trace file rollover.</span></span>  
  
 <span data-ttu-id="2fb6d-173">**/Z**  *file_size*</span><span class="sxs-lookup"><span data-stu-id="2fb6d-173">**/Z**  *file_size*</span></span>  
 <span data-ttu-id="2fb6d-174">추적 파일 크기(MB)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-174">Specifies the size of the trace file in megabytes (MB).</span></span> <span data-ttu-id="2fb6d-175">기본 크기는 5MB입니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-175">The default size is 5 MB.</span></span> <span data-ttu-id="2fb6d-176">롤오버를 사용하는 경우 모든 롤오버 파일이 이 인수에서 지정한 값으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-176">If rollover is enabled, all rollover files will be limited to the value specified in this argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fb6d-177">설명</span><span class="sxs-lookup"><span data-stu-id="2fb6d-177">Remarks</span></span>  
 <span data-ttu-id="2fb6d-178">특정 템플릿을 사용하여 추적을 시작하려면 **/S** 와 **/T** 옵션을 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-178">To start a trace with a specific template, use the **/S** and **/T** options together.</span></span> <span data-ttu-id="2fb6d-179">예를 들어 MyServer\MyInstance에 있는 Standard 템플릿을 사용하여 추적을 시작하려면 명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2fb6d-179">For example, to start a trace using the Standard template on MyServer\MyInstance, enter the following at the command prompt:</span></span>  
  
```  
profiler /S MyServer\MyInstance /T "Standard"  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fb6d-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2fb6d-180">See Also</span></span>  
 [<span data-ttu-id="2fb6d-181">명령 프롬프트 유틸리티 참조&#40;데이터베이스 엔진#41;</span><span class="sxs-lookup"><span data-stu-id="2fb6d-181">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](command-prompt-utility-reference-database-engine.md)  
  
  
