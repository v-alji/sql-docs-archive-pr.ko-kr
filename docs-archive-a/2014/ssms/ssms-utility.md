---
title: Ssms 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], opening
- command prompt utilities [SQL Server], sqlwb
- sqlwb utility
- Management Studio command line
- opening SQL Server Management Studio
ms.assetid: aafda520-9e2a-4e1e-b936-1b165f1684e8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0cfc9469e49e6ce3839d02a61477b8957fbc13e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660279"
---
# <a name="ssms-utility"></a><span data-ttu-id="db263-102">Ssms 유틸리티</span><span class="sxs-lookup"><span data-stu-id="db263-102">Ssms Utility</span></span>
  <span data-ttu-id="db263-103">**Ssms**유틸리티는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db263-103">The **Ssms**utility opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="db263-104">**Ssms** 를 지정하면 서버 연결도 설정되며 쿼리, 스크립트, 파일, 프로젝트 및 솔루션이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="db263-104">If specified, **Ssms** also establishes a connection to a server, and opens queries, scripts, files, projects, and solutions.</span></span>  
  
 <span data-ttu-id="db263-105">쿼리, 프로젝트 또는 솔루션이 포함된 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db263-105">You can specify files that contain queries, projects, or solutions.</span></span> <span data-ttu-id="db263-106">연결 정보를 제공했고 파일 형식이 해당 서버 유형에 연결된 경우 쿼리가 포함된 파일은 서버에 자동으로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="db263-106">Files that contain queries are automatically connected to a server if connection information is provided and the file type is associated with that type of server.</span></span> <span data-ttu-id="db263-107">예를 들어 .sql 파일은 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 SQL 쿼리 편집기 창을 열고 .mdx 파일은 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 MDX 쿼리 편집기 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db263-107">For instance, .sql files will open a SQL Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and .mdx files will open an MDX Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="db263-108">**에서** SQL Server 솔루션 및 프로젝트 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="db263-108">**SQL Server Solutions and Projects** will open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db263-109">**Ssms** 유틸리티는 쿼리를 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db263-109">The **Ssms** utility does not run queries.</span></span> <span data-ttu-id="db263-110">명령줄에서 쿼리를 실행하려면 **sqlcmd** 유틸리티를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-110">To run queries from the command line, use the **sqlcmd** utility.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db263-111">구문</span><span class="sxs-lookup"><span data-stu-id="db263-111">Syntax</span></span>  
  
```  
  
      Ssms  
    [scriptfile] [projectfile] [solutionfile]  
    [-Sservername] [-ddatabasename] [-Uusername] [-Ppassword]   
    [-E] [-nosplash] [-log[filename]?] [-?]  
```  
  
## <a name="arguments"></a><span data-ttu-id="db263-112">인수</span><span class="sxs-lookup"><span data-stu-id="db263-112">Arguments</span></span>  
 <span data-ttu-id="db263-113">*scriptfile*</span><span class="sxs-lookup"><span data-stu-id="db263-113">*scriptfile*</span></span>  
 <span data-ttu-id="db263-114">열려는 스크립트 파일을 하나 이상 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-114">Specifies one or more script files to open.</span></span> <span data-ttu-id="db263-115">매개 변수에 파일의 전체 경로가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-115">The parameter must contain the full path to the files.</span></span>  
  
 <span data-ttu-id="db263-116">*projectfile*</span><span class="sxs-lookup"><span data-stu-id="db263-116">*projectfile*</span></span>  
 <span data-ttu-id="db263-117">열려는 스크립트 프로젝트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-117">Specifies a script project to open.</span></span> <span data-ttu-id="db263-118">매개 변수에 스크립트 프로젝트 파일의 전체 경로가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-118">The parameter must contain the full path to the script project file.</span></span>  
  
 <span data-ttu-id="db263-119">*solutionfile*</span><span class="sxs-lookup"><span data-stu-id="db263-119">*solutionfile*</span></span>  
 <span data-ttu-id="db263-120">열려는 솔루션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-120">Specifies a solution to open.</span></span> <span data-ttu-id="db263-121">매개 변수에 솔루션 파일의 전체 경로가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-121">The parameter must contain the full path to the solution file.</span></span>  
  
 <span data-ttu-id="db263-122">[**-S** _서버 이름_]</span><span class="sxs-lookup"><span data-stu-id="db263-122">[**-S** _servername_]</span></span>  
 <span data-ttu-id="db263-123">서버 이름</span><span class="sxs-lookup"><span data-stu-id="db263-123">Server name</span></span>  
  
 <span data-ttu-id="db263-124">[**-d** _databasename_]</span><span class="sxs-lookup"><span data-stu-id="db263-124">[**-d** _databasename_]</span></span>  
 <span data-ttu-id="db263-125">데이터베이스 이름</span><span class="sxs-lookup"><span data-stu-id="db263-125">Database name</span></span>  
  
 <span data-ttu-id="db263-126">[**-U** _username_]</span><span class="sxs-lookup"><span data-stu-id="db263-126">[**-U** _username_]</span></span>  
 <span data-ttu-id="db263-127">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 연결할 때 사용하는 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="db263-127">User name when connecting with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication</span></span>  
  
 <span data-ttu-id="db263-128">[**-P** _암호_]</span><span class="sxs-lookup"><span data-stu-id="db263-128">[**-P** _password_]</span></span>  
 <span data-ttu-id="db263-129">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 연결할 때 사용하는 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="db263-129">Password when connecting with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication</span></span>  
  
 <span data-ttu-id="db263-130">[**-E**]</span><span class="sxs-lookup"><span data-stu-id="db263-130">[**-E**]</span></span>  
 <span data-ttu-id="db263-131">Windows 인증을 사용하여 연결</span><span class="sxs-lookup"><span data-stu-id="db263-131">Connect using Windows Authentication</span></span>  
  
 <span data-ttu-id="db263-132">[**-nosplash**]</span><span class="sxs-lookup"><span data-stu-id="db263-132">[**-nosplash**]</span></span>  
 <span data-ttu-id="db263-133">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 여는 동안 시작 화면을 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db263-133">Prevents [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from displaying the splash screen graphic while opening.</span></span> <span data-ttu-id="db263-134">대역폭이 제한된 연결에서 터미널 서비스를 사용하여 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 실행하는 컴퓨터에 연결할 때 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-134">Use this option when connecting to the computer running [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] by means of Terminal Services over a connection with a limited bandwidth.</span></span> <span data-ttu-id="db263-135">이 인수는 대/소문자를 구분하지 않으며 다른 인수 앞이나 뒤에 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db263-135">This argument is not case-sensitive and may appear before or after other arguments</span></span>  
  
 <span data-ttu-id="db263-136">[**-log**_[filename]?_]</span><span class="sxs-lookup"><span data-stu-id="db263-136">[**-log**_[filename]?_]</span></span>  
 <span data-ttu-id="db263-137">문제 해결을 위해 지정된 파일에 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 작업을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-137">Logs [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] activity to the specified file for troubleshooting</span></span>  
  
 <span data-ttu-id="db263-138">[**-?**]</span><span class="sxs-lookup"><span data-stu-id="db263-138">[**-?**]</span></span>  
 <span data-ttu-id="db263-139">명령줄 도움말을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-139">Displays command line help</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db263-140">설명</span><span class="sxs-lookup"><span data-stu-id="db263-140">Remarks</span></span>  
 <span data-ttu-id="db263-141">모든 스위치는 선택 사항이며 쉼표로 구분되는 파일을 제외하고 공백으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-141">All of the switches are optional and separated by a space except files which are separated by commas.</span></span> <span data-ttu-id="db263-142">스위치를 지정하지 않으면 **Ssms** 가 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 도구 **메뉴의** 옵션 **설정에 지정된 대로** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db263-142">If you do not specify any switches, **Ssms** opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] as specified in the **Options** settings on the **Tools** menu.</span></span> <span data-ttu-id="db263-143">예를 들어 **환경/일반** 페이지에서 **시작 시** 옵션으로 **새 쿼리 창 열기**를 지정할 경우 **Ssms** 는 빈 쿼리 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db263-143">For example, if the **Environment/General** page **At startup** option specifies **Open new query window**, **Ssms** will open with a blank Query Editor.</span></span>  
  
 <span data-ttu-id="db263-144">**-Log** 스위치는 명령줄 끝에 다른 모든 스위치 뒤에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db263-144">The **-log** switch must appear at the end of the command line, after all other switches.</span></span> <span data-ttu-id="db263-145">파일 이름 인수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="db263-145">The filename argument is optional.</span></span> <span data-ttu-id="db263-146">파일 이름을 지정하는 경우 해당 파일이 없으면 파일이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="db263-146">If a filename is specified, and the file does not exist, the file is created.</span></span> <span data-ttu-id="db263-147">쓰기 권한 부족 등의 이유로 파일을 만들 수 없는 경우 로그는 대신 지역화되지 않은 APPDATA 위치에 작성됩니다(아래 참조).</span><span class="sxs-lookup"><span data-stu-id="db263-147">If the file cannot be created - for example, due to insufficient write access, the log is written to the nonlocalized APPDATA location instead (See below).</span></span> <span data-ttu-id="db263-148">파일 이름 인수를 지정하지 않으면 현재 사용자의 지역화되지 않은 애플리케이션 데이터 폴더에 파일이 두 개 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="db263-148">If the filename argument is not specified, two files are written to the current user's nonlocalized application data folder.</span></span> <span data-ttu-id="db263-149">SQL Server에 대한 지역화되지 않은 애플리케이션 데이터 폴더는 APPDATA 환경 변수에서 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db263-149">The nonlocalized application data folder for SQL Server can be found from the APPDATA environment variable.</span></span> <span data-ttu-id="db263-150">예를 들어 SQL Server 2012의 경우 폴더는 \<system drive> \Users \\<username \> \AppData\Roaming\Microsoft\AppEnv\10.0 \\ 입니다.</span><span class="sxs-lookup"><span data-stu-id="db263-150">For example, for SQL Server 2012, the folder is \<system drive>:\Users\\<username\>\AppData\Roaming\Microsoft\AppEnv\10.0\\.</span></span> <span data-ttu-id="db263-151">기본적으로 두 파일의 이름은 ActivityLog.xml과 ActivityLog.xsl입니다.</span><span class="sxs-lookup"><span data-stu-id="db263-151">The two files are, by default, named ActivityLog.xml and ActivityLog.xsl.</span></span> <span data-ttu-id="db263-152">ActivityLog.xml에는 작업 로그 데이터가 포함되고 ActivityLog.xsl은 XML 파일을 더 편리하게 볼 수 있는 방법을 제공하는 XML 스타일 시트입니다.</span><span class="sxs-lookup"><span data-stu-id="db263-152">The former contains the activity log data and the latter is an XML style sheet which provides a more convenient way to view the XML file.</span></span> <span data-ttu-id="db263-153">다음 단계를 사용 하 여 Internet Explorer와 같은 기본 XML 뷰어에서 로그 파일을 확인 합니다. 시작, 실행을 차례로 클릭 한 다음 제공 된 필드에 " \<system drive> : \Users \\<username\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml"를 입력 하 \> 고 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="db263-153">Use the following steps to view the log file in your default XML viewer, like Internet Explorer:  Click Start, then click Run...", then type "\<system drive>:\Users\\<username\>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml" into the field provided, and then press Enter.</span></span>  
  
 <span data-ttu-id="db263-154">연결 정보를 제공했고 파일 형식이 해당 서버 유형에 연결된 경우 쿼리가 포함된 파일을 서버에 연결할 것인지 묻는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="db263-154">Files that contain queries will prompt to be connected to a server if connection information is provided and the file type is associated with that type of server.</span></span> <span data-ttu-id="db263-155">예를 들어 .sql 파일은 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 SQL 쿼리 편집기 창을 열고 .mdx 파일은 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 MDX 쿼리 편집기 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db263-155">For instance, .sql files will open a SQL Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and .mdx files will open an MDX Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="db263-156">**에서** SQL Server 솔루션 및 프로젝트 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="db263-156">**SQL Server Solutions and Projects** will open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="db263-157">다음 표에서는 서버 유형과 연결된 파일 확장명을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db263-157">The following table maps server types to file extensions.</span></span>  
  
|<span data-ttu-id="db263-158">서버 유형</span><span class="sxs-lookup"><span data-stu-id="db263-158">Server type</span></span>|<span data-ttu-id="db263-159">내선 번호</span><span class="sxs-lookup"><span data-stu-id="db263-159">Extension</span></span>|  
|-----------------|---------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|<span data-ttu-id="db263-160">.sql</span><span class="sxs-lookup"><span data-stu-id="db263-160">.sql</span></span>|  
|<span data-ttu-id="db263-161">SQL Server Analysis Services</span><span class="sxs-lookup"><span data-stu-id="db263-161">SQL Server Analysis Services</span></span>|<span data-ttu-id="db263-162">.mdx</span><span class="sxs-lookup"><span data-stu-id="db263-162">.mdx</span></span><br /><br /> <span data-ttu-id="db263-163">.xmla</span><span class="sxs-lookup"><span data-stu-id="db263-163">.xmla</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="db263-164">예</span><span class="sxs-lookup"><span data-stu-id="db263-164">Examples</span></span>  
 <span data-ttu-id="db263-165">다음 스크립트는 명령 프롬프트에서 기본 설정으로 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db263-165">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt with the default settings:</span></span>  
  
```  
Ssms  
  
```  
  
 <span data-ttu-id="db263-166">다음 스크립트는 명령 프롬프트에서 Windows 인증을 사용하여 시작 화면을 표시하지 않고 코드 편집기를 서버 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 로 설정한 상태로 `ACCTG and the database AdventureWorks2012,` 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db263-166">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, with Windows Authentication, with the Code Editor set to the server `ACCTG and the database AdventureWorks2012,` without showing the splash screen:</span></span>  
  
```  
Ssms -E -S ACCTG -d AdventureWorks2012 -nosplash  
  
```  
  
 <span data-ttu-id="db263-167">다음 스크립트는 명령 프롬프트에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 열고 MonthEndQuery 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db263-167">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the MonthEndQuery script.</span></span>  
  
```  
Ssms "C:\Documents and Settings\username\My Documents\SQL Server Management Studio Projects\FinanceScripts\FinanceScripts\MonthEndQuery.sql"  
  
```  
  
 <span data-ttu-id="db263-168">다음 스크립트는 명령 프롬프트에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 열고 `developer`라는 컴퓨터에서 NewReportsProject 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db263-168">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the NewReportsProject project on the computer named `developer`:</span></span>  
  
```  
Ssms "\\developer\fin\ReportProj\ReportProj\NewReportProj.ssmssqlproj"  
  
```  
  
 <span data-ttu-id="db263-169">다음 스크립트는 명령 프롬프트에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 를 열고 MonthlyReports 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db263-169">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the MonthlyReports solution:</span></span>  
  
```  
Ssms "C:\solutionsfolder\ReportProj\MonthlyReports.ssmssln"  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="db263-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db263-170">See Also</span></span>  
 [<span data-ttu-id="db263-171">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="db263-171">Use SQL Server Management Studio</span></span>](../database-engine/use-sql-server-management-studio.md)  
  
  
