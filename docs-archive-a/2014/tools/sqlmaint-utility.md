---
title: sqlmaint 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- database maintenance plans [SQL Server]
- sqlmaint utility
- maintaining databases [SQL Server]
- backups [SQL Server], sqlmaint utility
- command prompt utilities [SQL Server], sqlmaint
- maintenance plans [SQL Server], command prompt
- backing up [SQL Server], sqlmaint utility
ms.assetid: 937a9932-4aed-464b-b97a-a5acfe6a50de
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80e60b75305ee91e8b62a201d9c86af301326789
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727535"
---
# <a name="sqlmaint-utility"></a><span data-ttu-id="614ba-102">sqlmaint 유틸리티</span><span class="sxs-lookup"><span data-stu-id="614ba-102">sqlmaint Utility</span></span>
  <span data-ttu-id="614ba-103">**sqlmaint** 유틸리티는 하나 이상의 데이터베이스에서 지정한 유지 관리 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-103">The**sqlmaint** utility performs a specified set of maintenance operations on one or more databases.</span></span> <span data-ttu-id="614ba-104">**sqlmaint** 를 사용하여 DBCC 검사를 실행하고 데이터베이스 및 트랜잭션 로그를 백업하고 통계를 업데이트하고 인덱스를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-104">Use **sqlmaint** to run DBCC checks, back up a database and its transaction log, update statistics, and rebuild indexes.</span></span> <span data-ttu-id="614ba-105">모든 데이터베이스 유지 관리 작업은 지정된 텍스트 파일, HTML 파일 또는 전자 메일 계정으로 보낼 수 있는 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-105">All database maintenance activities generate a report that can be sent to a designated text file, HTML file, or e-mail account.</span></span> <span data-ttu-id="614ba-106">**sqlmaint** 는 이전 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]로 만든 데이터베이스 유지 관리 계획을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-106">**sqlmaint** executes database maintenance plans created with previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="614ba-107">명령 프롬프트에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유지 관리 계획을 실행하려면 [dtexec 유틸리티](../integration-services/packages/dtexec-utility.md)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-107">To run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] maintenance plans from the command prompt, use the [dtexec Utility](../integration-services/packages/dtexec-utility.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../includes/ssnotedepnextavoid-md.md)] <span data-ttu-id="614ba-108">대신 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유지 관리 계획 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-108">Use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] maintenance plan feature instead.</span></span> <span data-ttu-id="614ba-109">유지 관리 계획에 대한 자세한 내용은 [유지 관리 계획](../relational-databases/maintenance-plans/maintenance-plans.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="614ba-109">For more information on maintenance plans, see [Maintenance Plans](../relational-databases/maintenance-plans/maintenance-plans.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="614ba-110">구문</span><span class="sxs-lookup"><span data-stu-id="614ba-110">Syntax</span></span>  
  
```  
  
      sqlmaint   
[-?] |  
[  
     [-Sserver_name[\instance_name]]  
     [-Ulogin_ID [-Ppassword]]  
     {  
          [-Ddatabase_name | -PlanNamename | -PlanIDguid ]  
          [-Rpttext_file]  
          [-Tooperator_name]  
          [-HtmlRpthtml_file [-DelHtmlRpt <time_period>] ]  
          [-RmUnusedSpacethreshold_percentfree_percent]  
          [-CkDB | -CkDBNoIdx]  
          [-CkAl | -CkAlNoIdx]  
          [-CkCat]  
          [-UpdOptiStatssample_percent]  
          [-RebldIdxfree_space]  
          [-SupportComputedColumn]  
          [-WriteHistory]  
          [  
               {-BkUpDB [backup_path] | -BkUpLog [backup_path] }  
               {-BkUpMedia  
                    {DISK [  
                           [-DelBkUps<time_period>]   
                           [-CrBkSubDir ]   
                           [-UseDefDir ]   
                          ]  
                     | TAPE   
                    }  
               }  
               [-BkUpOnlyIfClean]  
               [-VrfyBackup]  
          ]  
     }  
]  
<time_period> ::=  
number[minutes | hours | days | weeks | months]  
```  
  
## <a name="arguments"></a><span data-ttu-id="614ba-111">인수</span><span class="sxs-lookup"><span data-stu-id="614ba-111">Arguments</span></span>  
 <span data-ttu-id="614ba-112">매개 변수 및 해당 값은 공백으로 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-112">The parameters and their values must be separated by a space.</span></span> <span data-ttu-id="614ba-113">예를 들어 **-S** 와 *server_name*사이에 공백이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-113">For example, there must be a space between **-S** and *server_name*.</span></span>  
  
 <span data-ttu-id="614ba-114">**-?**</span><span class="sxs-lookup"><span data-stu-id="614ba-114">**-?**</span></span>  
 <span data-ttu-id="614ba-115">**sqlmaint** 에 대한 구문 다이어그램이 반환되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-115">Specifies that the syntax diagram for **sqlmaint** be returned.</span></span> <span data-ttu-id="614ba-116">이 매개 변수는 단독으로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-116">This parameter must be used alone.</span></span>  
  
 <span data-ttu-id="614ba-117">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="614ba-117">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="614ba-118">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 대상 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-118">Specifies the target instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="614ba-119">해당 서버 컴퓨터에 있는 기본 *인스턴스에 연결하려면* server_name [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-119">Specify *server_name* to connect to the default instance of [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on that server.</span></span> <span data-ttu-id="614ba-120">해당 서버에 있는 명명 된 인스턴스에 연결 하려면 *server_name **_\\_** instance_name* 를 지정 [!INCLUDE[ssDE](../includes/ssde-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-120">Specify *server_name\*\*_\\_*\* instance_name\* to connect to a named instance of [!INCLUDE[ssDE](../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="614ba-121">서버를 지정하지 않으면 **sqlmaint** 가 로컬 컴퓨터에 있는 [!INCLUDE[ssDE](../includes/ssde-md.md)] 의 기본 인스턴스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-121">If no server is specified, **sqlmaint** connects to the default instance of [!INCLUDE[ssDE](../includes/ssde-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="614ba-122">**-U** _login_ID_</span><span class="sxs-lookup"><span data-stu-id="614ba-122">**-U** _login_ID_</span></span>  
 <span data-ttu-id="614ba-123">서버에 연결할 때 사용할 로그인 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-123">Specifies the login ID to use when connecting to the server.</span></span> <span data-ttu-id="614ba-124">이 인수를 제공하지 않으면 **sqlmaint** 에서 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-124">If not supplied, **sqlmaint** attempts to use [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication.</span></span> <span data-ttu-id="614ba-125">*login_ID* 에 특수 문자가 포함된 경우 큰따옴표(")로 묶어야 합니다. 그렇지 않은 경우 큰따옴표는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-125">If *login_ID* contains special characters, it must be enclosed in double quotation marks ("); otherwise, the double quotation marks are optional.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="614ba-126">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="614ba-126">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="614ba-127">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="614ba-127">**-P** _password_</span></span>  
 <span data-ttu-id="614ba-128">로그인 ID의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-128">Specifies the password for the login ID.</span></span> <span data-ttu-id="614ba-129">**-U** 매개 변수도 제공한 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-129">Only valid if the **-U** parameter is also supplied.</span></span> <span data-ttu-id="614ba-130">*password* 에 특수 문자가 포함된 경우 큰따옴표(")로 묶어야 합니다. 그렇지 않은 경우 큰따옴표는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-130">If *password* contains special characters, it must be enclosed in double quotation marks; otherwise, the double quotation marks are optional.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="614ba-131">암호는 마스킹되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-131">The password is not masked.</span></span> <span data-ttu-id="614ba-132">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="614ba-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="614ba-133">**-D** _database_name_</span><span class="sxs-lookup"><span data-stu-id="614ba-133">**-D** _database_name_</span></span>  
 <span data-ttu-id="614ba-134">유지 관리 작업을 수행할 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-134">Specifies the name of the database in which to perform the maintenance operation.</span></span> <span data-ttu-id="614ba-135">*database_name* 에 특수 문자가 포함된 경우 큰따옴표(")로 묶어야 합니다. 그렇지 않은 경우 큰따옴표는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-135">If *database_name* contains special characters, it must be enclosed in double quotation marks; otherwise, the double quotation marks are optional.</span></span>  
  
 <span data-ttu-id="614ba-136">**-PlanName** _name_</span><span class="sxs-lookup"><span data-stu-id="614ba-136">**-PlanName** _name_</span></span>  
 <span data-ttu-id="614ba-137">데이터베이스 유지 관리 계획 마법사를 사용하여 정의한 데이터베이스 유지 관리 계획의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-137">Specifies the name of a database maintenance plan defined using the Database Maintenance Plan Wizard.</span></span> <span data-ttu-id="614ba-138">**sqlmaint** 가 계획에서 사용하는 유일한 정보는 계획에 있는 데이터베이스 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-138">The only information **sqlmaint** uses from the plan is the list of the databases in the plan.</span></span> <span data-ttu-id="614ba-139">다른 **sqlmaint** 매개 변수에서 지정한 모든 유지 관리 작업이 이 데이터베이스 목록에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-139">Any maintenance activities you specify in the other **sqlmaint** parameters are applied to this list of databases.</span></span>  
  
 <span data-ttu-id="614ba-140">**-PlanID** _guid_</span><span class="sxs-lookup"><span data-stu-id="614ba-140">**-PlanID** _guid_</span></span>  
 <span data-ttu-id="614ba-141">데이터베이스 유지 관리 계획 마법사를 사용하여 정의한 데이터베이스 유지 관리 계획의 GUID(Globally Unique Identifier)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-141">Specifies the globally unique identifier (GUID) of a database maintenance plan defined using the Database Maintenance Plan Wizard.</span></span> <span data-ttu-id="614ba-142">**sqlmaint** 가 계획에서 사용하는 유일한 정보는 계획에 있는 데이터베이스 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-142">The only information **sqlmaint** uses from the plan is the list of the databases in the plan.</span></span> <span data-ttu-id="614ba-143">다른 **sqlmaint** 매개 변수에서 지정한 모든 유지 관리 작업이 이 데이터베이스 목록에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-143">Any maintenance activities you specify in the other **sqlmaint** parameters are applied to this list of databases.</span></span> <span data-ttu-id="614ba-144">이 인수는 msdb.dbo.sysdbmaintplans의 plan_id 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-144">This must match a plan_id value in msdb.dbo.sysdbmaintplans.</span></span>  
  
 <span data-ttu-id="614ba-145">**-Rpt** _text_file_</span><span class="sxs-lookup"><span data-stu-id="614ba-145">**-Rpt** _text_file_</span></span>  
 <span data-ttu-id="614ba-146">보고서를 생성할 파일의 전체 경로와 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-146">Specifies the full path and name of the file into which the report is to be generated.</span></span> <span data-ttu-id="614ba-147">이 보고서는 화면에도 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-147">The report is also generated on the screen.</span></span> <span data-ttu-id="614ba-148">보고서에서는 파일 이름에 날짜를 추가하여 버전 정보를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-148">The report maintains version information by adding a date to the file name.</span></span> <span data-ttu-id="614ba-149">날짜는 _*yyyyMMddhhmm*형식으로 파일 이름 끝의 마침표 앞에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-149">The date is generated as follows: at the end of the file name but before the period, in the form _*yyyyMMddhhmm*.</span></span> <span data-ttu-id="614ba-150">*yyyy* = 연도, *MM* = 월, *dd* = 일, *hh* = 시, *mm* = 분입니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-150">*yyyy* = year, *MM* = month, *dd* = day, *hh* = hour, *mm* = minute.</span></span>  
  
 <span data-ttu-id="614ba-151">1996년 12월 1일 오전 10시 23분에</span><span class="sxs-lookup"><span data-stu-id="614ba-151">If you run the utility at 10:23 A.M.</span></span> <span data-ttu-id="614ba-152">유틸리티를 실행하는 경우 *text_file* 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-152">on December 1, 1996, and this is the *text_file* value:</span></span>  
  
```  
c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.rpt  
```  
  
 <span data-ttu-id="614ba-153">생성되는 파일 이름은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-153">The generated file name is:</span></span>  
  
```  
c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint_199612011023.rpt  
```  
  
 <span data-ttu-id="614ba-154">*sqlmaint* 에서 원격 서버에 액세스할 때 **text_file** 에는 전체 UNC(범용 명명 규칙) 파일 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-154">The full Universal Naming Convention (UNC) file name is required for *text_file* when **sqlmaint** accesses a remote server.</span></span>  
  
 <span data-ttu-id="614ba-155">**-** _Operator_name_</span><span class="sxs-lookup"><span data-stu-id="614ba-155">**-To** _operator_name_</span></span>  
 <span data-ttu-id="614ba-156">SQL 메일을 통해 생성된 보고서를 받는 운영자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-156">Specifies the operator to whom the generated report is sent through SQL Mail.</span></span>  
  
 <span data-ttu-id="614ba-157">**-HtmlRpt** _html_file_</span><span class="sxs-lookup"><span data-stu-id="614ba-157">**-HtmlRpt** _html_file_</span></span>  
 <span data-ttu-id="614ba-158">HTML 보고서를 생성할 파일의 전체 경로와 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-158">Specifies the full path and name of the file into which an HTML report is to be generated.</span></span> <span data-ttu-id="614ba-159">**sqlmaint** 에서는 *-Rpt* 매개 변수와 마찬가지로 _ **yyyyMMddhhmm** 형식의 문자열을 파일 이름에 더하여 파일 이름을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-159">**sqlmaint** generates the file name by appending a string of the format _*yyyyMMddhhmm* to the file name, just as it does for the **-Rpt** parameter.</span></span>  
  
 <span data-ttu-id="614ba-160">*sqlmaint* 에서 원격 서버에 액세스할 때 **html_file** 에는 전체 UNC 파일 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-160">The full UNC file name is required for *html_file* when **sqlmaint** accesses a remote server.</span></span>  
  
 <span data-ttu-id="614ba-161">**-DelHtmlRpt** \<*time_period*></span><span class="sxs-lookup"><span data-stu-id="614ba-161">**-DelHtmlRpt** \<*time_period*></span></span>  
 <span data-ttu-id="614ba-162">보고서 파일을 만든 후 시간 간격이 \<*time_period*>를 초과할 경우 보고서 디렉터리에 있는 HTML 보고서가 삭제되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-162">Specifies that any HTML report in the report directory be deleted if the time interval after the creation of the report file exceeds \<*time_period*>.</span></span> <span data-ttu-id="614ba-163">**-DelHtmlRpt**는 *html_file* 매개 변수에서 생성된 패턴과 이름이 맞는 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-163">**-DelHtmlRpt** looks for files whose name fits the pattern generated from the *html_file* parameter.</span></span> <span data-ttu-id="614ba-164">*html_file*이 c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.htm인 경우 **-DelHtmlRpt**는 **sqlmaint**에서 파일 이름이 C:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint\*.htm 패턴과 일치하고 지정된 \<*time_period*>보다 오래된 모든 파일을 삭제하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-164">If *html_file* is c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.htm, then **-DelHtmlRpt** causes **sqlmaint** to delete any files whose names match the pattern C:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint\*.htm and that are older than the specified \<*time_period*>.</span></span>  
  
 <span data-ttu-id="614ba-165">**-RmUnusedSpace** _threshold_percent free_percent_</span><span class="sxs-lookup"><span data-stu-id="614ba-165">**-RmUnusedSpace** _threshold_percent free_percent_</span></span>  
 <span data-ttu-id="614ba-166">**-D**에 지정된 데이터베이스에서 사용하지 않는 공간을 제거하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-166">Specifies that unused space be removed from the database specified in **-D**.</span></span> <span data-ttu-id="614ba-167">이 옵션은 자동으로 증가하도록 정의된 데이터베이스에서만 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-167">This option is only useful for databases that are defined to grow automatically.</span></span> <span data-ttu-id="614ba-168">*Threshold_percent* 는 데이터베이스 크기가 몇 MB에 도달하면 **sqlmaint** 가 사용하지 않는 데이터 공간을 제거할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-168">*Threshold_percent* specifies in megabytes the size that the database must reach before **sqlmaint** attempts to remove unused data space.</span></span> <span data-ttu-id="614ba-169">데이터베이스가 *threshold_percent*보다 작으면 동작이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-169">If the database is smaller than the *threshold_percent*, no action is taken.</span></span> <span data-ttu-id="614ba-170">*Free_percent* 는 사용하지 않는 공간 중 데이터베이스에 유지해야 할 공간을 최종 데이터베이스 크기의 백분율로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-170">*Free_percent* specifies how much unused space must remain in the database, specified as a percentage of the final size of the database.</span></span> <span data-ttu-id="614ba-171">예를 들어 200MB의 데이터베이스에 100MB 데이터가 포함된 경우 *free_percent* 에 10을 지정하면 최종 데이터베이스 크기는 110MB가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-171">For example, if a 200-MB database contains 100 MB of data, specifying 10 for *free_percent* results in the final database size being 110 MB.</span></span> <span data-ttu-id="614ba-172">데이터베이스가 *free_percent* 와 데이터베이스의 데이터 양을 더한 크기보다 작으면 데이터베이스가 확장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-172">Note that a database is not expanded if it is smaller than *free_percent* plus the amount of data in the database.</span></span> <span data-ttu-id="614ba-173">예를 들어 108MB의 데이터베이스에 100MB 데이터가 포함된 경우 *free_percent* 에 10을 지정하면 데이터베이스가 110MB로 확장되지 않고 108MB로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-173">For example, if a 108-MB database has 100 MB of data, specifying 10 for *free_percent* does not expand the database to 110 MB; it remains at 108 MB.</span></span>  
  
 <span data-ttu-id="614ba-174">**-CkDB** |  **-CkDBNoIdx**</span><span class="sxs-lookup"><span data-stu-id="614ba-174">**-CkDB** | **-CkDBNoIdx**</span></span>  
 <span data-ttu-id="614ba-175">**-D**에 지정된 데이터베이스에서 NOINDEX 옵션으로 DBCC CHECKDB 문 또는 DBCC CHECKDB 문을 실행하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-175">Specifies that a DBCC CHECKDB statement or a DBCC CHECKDB statement with the NOINDEX option be run in the database specified in **-D**.</span></span> <span data-ttu-id="614ba-176">자세한 내용은 DBCC CHECKDB를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="614ba-176">For more information, see DBCC CHECKDB.</span></span>  
  
 <span data-ttu-id="614ba-177">*sqlmaint* 를 실행할 때 데이터베이스가 사용 중인 경우 **text_file** 에 경고가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-177">A warning is written to *text_file* if the database is in use when **sqlmaint** runs.</span></span>  
  
 <span data-ttu-id="614ba-178">**-CkAl** |  **-CkAlNoIdx**</span><span class="sxs-lookup"><span data-stu-id="614ba-178">**-CkAl** | **-CkAlNoIdx**</span></span>  
 <span data-ttu-id="614ba-179">**-D**에 지정된 데이터베이스에서 NOINDEX 옵션으로 DBCC CHECKALLOC 문을 실행하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-179">Specifies that a DBCC CHECKALLOC statement with the NOINDEX option be run in the database specified in **-D**.</span></span> <span data-ttu-id="614ba-180">자세한 내용은 [DBCC CHECKALLOC&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="614ba-180">For more information, see [DBCC CHECKALLOC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql).</span></span>  
  
 <span data-ttu-id="614ba-181">**-CkCat**</span><span class="sxs-lookup"><span data-stu-id="614ba-181">**-CkCat**</span></span>  
 <span data-ttu-id="614ba-182">**-D**에 지정된 데이터베이스에서 DBCC CHECKCATALOG(Transact-SQL) 문을 실행하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-182">Specifies that a DBCC CHECKCATALOG (Transact-SQL) statement be run in the database specified in **-D**.</span></span> <span data-ttu-id="614ba-183">자세한 내용은 [DBCC CHECKCATALOG&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkcatalog-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="614ba-183">For more information, see [DBCC CHECKCATALOG &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkcatalog-transact-sql).</span></span>  
  
 <span data-ttu-id="614ba-184">**-UpdOptiStats** _sample_percent_</span><span class="sxs-lookup"><span data-stu-id="614ba-184">**-UpdOptiStats** _sample_percent_</span></span>  
 <span data-ttu-id="614ba-185">데이터베이스의 각 테이블에서 다음 문을 실행하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-185">Specifies that the following statement be run on each table in the database:</span></span>  
  
```  
UPDATE STATISTICS table WITH SAMPLE sample_percent PERCENT;  
```  
  
 <span data-ttu-id="614ba-186">테이블에 계산 열이 포함된 경우에는 **-UpdOptiStats** 를 사용할 때 **-SupportedComputedColumn**인수도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-186">If the tables contain computed columns, you must also specify the **-SupportedComputedColumn** argument when you use **-UpdOptiStats**.</span></span>  
  
 <span data-ttu-id="614ba-187">자세한 내용은 [UPDATE STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)로 만든 데이터베이스 유지 관리 계획을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-187">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
 <span data-ttu-id="614ba-188">**-RebldIdx** _free_space_</span><span class="sxs-lookup"><span data-stu-id="614ba-188">**-RebldIdx** _free_space_</span></span>  
 <span data-ttu-id="614ba-189">채우기 비율과 반대로 *free_space* 백분율 값을 사용하여 대상 데이터베이스에서 테이블의 인덱스를 다시 만들도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-189">Specifies that indexes on tables in the target database should be rebuilt by using the *free_space* percent value as the inverse of the fill factor.</span></span> <span data-ttu-id="614ba-190">예를 들어 *free_space* 백분율이 30인 경우 사용되는 채우기 비율은 70입니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-190">For example, if *free_space* percentage is 30, then the fill factor used is 70.</span></span> <span data-ttu-id="614ba-191">*free_space* 백분율 값으로 100을 지정하면 원래 채우기 비율 값으로 인덱스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-191">If a *free_space* percentage value of 100 is specified, then the indexes are rebuilt with the original fill factor value.</span></span>  
  
 <span data-ttu-id="614ba-192">인덱스가 계산 열에 있을 경우 **-RebldIdx** 를 사용할 때 **-SupportComputedColumn**인수도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-192">If the indexes are on computed columns, you must also specify the **-SupportComputedColumn** argument when you use **-RebldIdx**.</span></span>  
  
 <span data-ttu-id="614ba-193">**-RebldIdx**</span><span class="sxs-lookup"><span data-stu-id="614ba-193">**-SupportComputedColumn**</span></span>  
 <span data-ttu-id="614ba-194">계산 열에서 **sqlmaint** 를 사용하여 DBCC 유지 관리 명령을 실행하려면 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-194">Must be specified to run DBCC maintenance commands with **sqlmaint** on computed columns.</span></span>  
  
 <span data-ttu-id="614ba-195">**-WriteHistory**</span><span class="sxs-lookup"><span data-stu-id="614ba-195">**-WriteHistory**</span></span>  
 <span data-ttu-id="614ba-196">**sqlmaint**에서 수행되는 각 유지 관리 동작에 대한 항목을 msdb.dbo.sysdbmaintplan_history에 만들도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-196">Specifies that an entry be made in msdb.dbo.sysdbmaintplan_history for each maintenance action performed by **sqlmaint**.</span></span> <span data-ttu-id="614ba-197">**-PlanName** 또는 **-PlanID** 를 지정할 경우 sysdbmaintplan_history의 항목은 지정된 계획의 ID를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-197">If **-PlanName** or **-PlanID** is specified, the entries in sysdbmaintplan_history use the ID of the specified plan.</span></span> <span data-ttu-id="614ba-198">**-D** 를 지정할 경우 sysdbmaintplan_history의 항목은 계획 ID에 0을 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-198">If **-D** is specified, the entries in sysdbmaintplan_history are made with zeroes for the plan ID.</span></span>  
  
 <span data-ttu-id="614ba-199">**-BkUpDB** [ *backup_path*] |  **-BkUpLog** [ *backup_path* ]</span><span class="sxs-lookup"><span data-stu-id="614ba-199">**-BkUpDB** [ *backup_path*] |  **-BkUpLog** [ *backup_path* ]</span></span>  
 <span data-ttu-id="614ba-200">백업 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-200">Specifies a backup action.</span></span> <span data-ttu-id="614ba-201">**-BkUpDb** 는 전체 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-201">**-BkUpDb** backs up the entire database.</span></span> <span data-ttu-id="614ba-202">**-BkUpLog** 는 트랜잭션 로그만 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-202">**-BkUpLog** backs up only the transaction log.</span></span>  
  
 <span data-ttu-id="614ba-203">*backup_path* 는 백업 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-203">*backup_path* specifies the directory for the backup.</span></span> <span data-ttu-id="614ba-204">*-UseDefDir* 도 지정한 경우 **backup_path** 는 필요하지 않으며 둘 다 지정하는 경우에는 **-UseDefDir** 값이 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-204">*backup_path* is not needed if **-UseDefDir** is also specified, and is overridden by **-UseDefDir** if both are specified.</span></span> <span data-ttu-id="614ba-205">디렉터리나 \\\\.\TAPE0과 같은 테이프 디바이스 주소에 백업을 보관할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-205">The backup can be placed in a directory or a tape device address (for example, \\\\.\TAPE0).</span></span> <span data-ttu-id="614ba-206">데이터베이스 백업 파일 이름은 다음과 같이 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-206">The file name for a database backup is generated automatically as follows:</span></span>  
  
```  
dbname_db_yyyyMMddhhmm.BAK  
  
```  
  
 <span data-ttu-id="614ba-207">라는 설치 관리자 실행 파일에 포함됩니다. 여기서</span><span class="sxs-lookup"><span data-stu-id="614ba-207">where</span></span>  
  
-   <span data-ttu-id="614ba-208">*dbname* 은 백업하는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-208">*dbname* is the name of the database being backed up.</span></span>  
  
-   <span data-ttu-id="614ba-209">*yyyyMMddhhmm* 은 백업 작업의 시간이며 *yyyy* = 연도, *MM* = 월, *dd* = 일, *hh* = 시, 그리고 *mm* = 분을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-209">*yyyyMMddhhmm* is the time of the backup operation with *yyyy* = year, *MM* = month, *dd* = day, *hh* = hour, and *mm* = minute.</span></span>  
  
 <span data-ttu-id="614ba-210">트랜잭션 백업 파일 이름은 이와 비슷한 형식으로 자동 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-210">The file name for a transaction backup is generated automatically with a similar format:</span></span>  
  
```  
dbname_log_yyyymmddhhmm.BAK  
  
```  
  
 <span data-ttu-id="614ba-211">**-BkUpDB** 매개 변수를 사용하는 경우 **-BkUpMedia** 매개 변수를 사용하여 미디어도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-211">If you use the **-BkUpDB** parameter, you must also specify the media by using the **-BkUpMedia** parameter.</span></span>  
  
 <span data-ttu-id="614ba-212">**-BkUpMedia**</span><span class="sxs-lookup"><span data-stu-id="614ba-212">**-BkUpMedia**</span></span>  
 <span data-ttu-id="614ba-213">백업 미디어 유형을 DISK 또는 TAPE 중 하나로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-213">Specifies the media type of the backup, either DISK or TAPE.</span></span>  
  
 <span data-ttu-id="614ba-214">**DISK**</span><span class="sxs-lookup"><span data-stu-id="614ba-214">**DISK**</span></span>  
 <span data-ttu-id="614ba-215">백업 미디어로 디스크를 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-215">Specifies that the backup medium is disk.</span></span>  
  
 <span data-ttu-id="614ba-216">**-DelBkUps**\< *time_period* ></span><span class="sxs-lookup"><span data-stu-id="614ba-216">**-DelBkUps**\< *time_period* ></span></span>  
 <span data-ttu-id="614ba-217">디스크 백업의 경우 백업을 만든 후 시간 간격이 \<*time_period*>를 초과하면 백업 디렉터리에 있는 모든 백업 파일을 삭제하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-217">For disk backups, specifies that any backup file in the backup directory be deleted if the time interval after the creation of the backup exceeds the \<*time_period*>.</span></span>  
  
 <span data-ttu-id="614ba-218">**-CrBkSubDir**</span><span class="sxs-lookup"><span data-stu-id="614ba-218">**-CrBkSubDir**</span></span>  
 <span data-ttu-id="614ba-219">디스크 백업의 경우 *-UseDefDir*도 지정했으면 [ **backup_path** ] 디렉터리나 기본 백업 디렉터리에 하위 디렉터리를 만들도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-219">For disk backups, specifies that a subdirectory be created in the [*backup_path*] directory or in the default backup directory if **-UseDefDir** is also specified.</span></span> <span data-ttu-id="614ba-220">하위 디렉터리의 이름은 **-D**에 지정된 데이터베이스 이름을 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-220">The name of the subdirectory is generated from the database name specified in **-D**.</span></span> <span data-ttu-id="614ba-221">**-CrBkSubDir** 을 사용하면 *backup_path* 매개 변수를 변경할 필요 없이 다른 데이터베이스의 모든 백업을 별도의 하위 디렉터리에 쉽게 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-221">**-CrBkSubDir** offers an easy way to put all the backups for different databases into separate subdirectories without having to change the *backup_path* parameter.</span></span>  
  
 <span data-ttu-id="614ba-222">**backup_path**</span><span class="sxs-lookup"><span data-stu-id="614ba-222">**-UseDefDir**</span></span>  
 <span data-ttu-id="614ba-223">디스크 백업의 경우 기본 백업 디렉터리에 백업 파일을 만들도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-223">For disk backups, specifies that the backup file be created in the default backup directory.</span></span> <span data-ttu-id="614ba-224">둘 다 지정한 경우**UseDefDir** 이 *backup_path* 보다 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-224">**UseDefDir** overrides *backup_path* if both are specified.</span></span> <span data-ttu-id="614ba-225">기본 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 설정을 사용하는 경우 기본 백업 디렉터리는 C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\Backup입니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-225">With a default [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] setup, the default backup directory is C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\Backup.</span></span>  
  
 <span data-ttu-id="614ba-226">**TAPE**</span><span class="sxs-lookup"><span data-stu-id="614ba-226">**TAPE**</span></span>  
 <span data-ttu-id="614ba-227">백업 미디어로 테이프를 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-227">Specifies that the backup medium is tape.</span></span>  
  
 <span data-ttu-id="614ba-228">**-BkUpOnlyIfClean**</span><span class="sxs-lookup"><span data-stu-id="614ba-228">**-BkUpOnlyIfClean**</span></span>  
 <span data-ttu-id="614ba-229">지정된 **-Ck** 검사를 통해 데이터에 문제가 발견되지 않을 경우에만 백업이 수행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-229">Specifies that the backup occur only if any specified **-Ck** checks did not find problems with the data.</span></span> <span data-ttu-id="614ba-230">유지 관리 동작은 명령 프롬프트에 표시되는 것과 같은 순서로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-230">Maintenance actions run in the same sequence as they appear in the command prompt.</span></span> <span data-ttu-id="614ba-231">**-BkUpOnlyIfClean**을 지정할 계획인 경우 **-BkUpDB**-BkUpLog **매개 변수 전에 매개 변수**-CkDB **,** -CkDBNoIdx **,** -CkAl **,** -CkAlNoIdx **,** / **-CkTxtAl** 또는 **-CkCat**를 지정합니다. 이 매개 변수를 지정하지 않으면 검사 보고서 문제가 있는지 여부에 상관없이 백업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-231">Specify the parameters **-CkDB**, **-CkDBNoIdx**, **-CkAl**, **-CkAlNoIdx**, **-CkTxtAl**, or **-CkCat** before the **-BkUpDB**/**-BkUpLog** parameter(s) if you are also going to specify **-BkUpOnlyIfClean**, or the backup occurs whether or not the check reports problems.</span></span>  
  
 <span data-ttu-id="614ba-232">**-VrfyBackup**</span><span class="sxs-lookup"><span data-stu-id="614ba-232">**-VrfyBackup**</span></span>  
 <span data-ttu-id="614ba-233">백업이 완료되면 백업에서 RESTORE VERIFYONLY를 실행하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-233">Specifies that RESTORE VERIFYONLY be run on the backup when it completes.</span></span>  
  
 <span data-ttu-id="614ba-234">*number*[**minutes**| **hours**| **day**| **weeks**| **months**]</span><span class="sxs-lookup"><span data-stu-id="614ba-234">*number*[**minutes**| **hours**| **day**| **weeks**| **months**]</span></span>  
 <span data-ttu-id="614ba-235">보고서 또는 백업 파일을 삭제할 기준이 되는 시간 간격을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-235">Specifies the time interval used to determine if a report or backup file is old enough to be deleted.</span></span> <span data-ttu-id="614ba-236">*number* 는 정수와 시간 단위로 공백 없이 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-236">*number* is an integer followed (without a space) by a unit of time.</span></span> <span data-ttu-id="614ba-237">올바른 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-237">Valid examples:</span></span>  
  
-   <span data-ttu-id="614ba-238">**12weeks**</span><span class="sxs-lookup"><span data-stu-id="614ba-238">**12weeks**</span></span>  
  
-   <span data-ttu-id="614ba-239">**3months**</span><span class="sxs-lookup"><span data-stu-id="614ba-239">**3months**</span></span>  
  
-   <span data-ttu-id="614ba-240">**15days**</span><span class="sxs-lookup"><span data-stu-id="614ba-240">**15days**</span></span>  
  
 <span data-ttu-id="614ba-241">*number* 만 지정하면 기본적으로 날짜 부분에 **weeks**가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-241">If only *number* is specified, the default date part is **weeks**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="614ba-242">설명</span><span class="sxs-lookup"><span data-stu-id="614ba-242">Remarks</span></span>  
 <span data-ttu-id="614ba-243">**sqlmaint** 유틸리티는 하나 이상의 데이터베이스에서 유지 관리 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-243">The **sqlmaint** utility performs maintenance operations on one or more databases.</span></span> <span data-ttu-id="614ba-244">**-D** 를 지정할 경우 지정한 데이터베이스에서만 나머지 스위치에 지정된 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-244">If **-D** is specified, the operations specified in the remaining switches are performed only on the specified database.</span></span> <span data-ttu-id="614ba-245">**-PlanName** 또는 **-PlanID** 를 지정할 경우 **sqlmaint** 가 지정된 유지 관리 작업에서 정보를 검색하면 계획에 있는 데이터베이스 목록만 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-245">If **-PlanName** or **-PlanID** are specified, the only information **sqlmaint** retrieves from the specified maintenance plan is the list of databases in the plan.</span></span> <span data-ttu-id="614ba-246">나머지 **sqlmaint** 매개 변수에 지정된 모든 작업은 계획에서 가져온 목록의 각 데이터베이스에 대해 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-246">All operations specified in the remaining **sqlmaint** parameters are applied against each database in the list obtained from the plan.</span></span> <span data-ttu-id="614ba-247">**sqlmaint** 유틸리티는 계획 자체에 정의된 유지 관리 작업을 적용하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-247">The **sqlmaint** utility does not apply any of the maintenance activities defined in the plan itself.</span></span>  
  
 <span data-ttu-id="614ba-248">**sqlmaint** 유틸리티가 성공적으로 실행되면 0을 반환하고 실패하면 1을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-248">The **sqlmaint** utility returns 0 if it runs successfully or 1 if it fails.</span></span> <span data-ttu-id="614ba-249">실패는 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-249">Failure is reported:</span></span>  
  
-   <span data-ttu-id="614ba-250">유지 관리 동작이 실패할 경우</span><span class="sxs-lookup"><span data-stu-id="614ba-250">If any of the maintenance actions fail.</span></span>  
  
-   <span data-ttu-id="614ba-251">**-CkDB**, **-CkDBNoIdx**, **-CkAl**, **-CkAlNoIdx**, **-CkTxtAl**또는 **-CkCat** 검사에서 데이터 관련 문제를 발견합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-251">If **-CkDB**, **-CkDBNoIdx**, **-CkAl**, **-CkAlNoIdx**, **-CkTxtAl**, or **-CkCat** checks find problems with the data.</span></span>  
  
-   <span data-ttu-id="614ba-252">일반 오류가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="614ba-252">If a general failure is encountered.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="614ba-253">사용 권한</span><span class="sxs-lookup"><span data-stu-id="614ba-253">Permissions</span></span>  
 <span data-ttu-id="614ba-254">**sqlmaint** 유틸리티는 **에 대한** 읽기 및 실행 `sqlmaint.exe`권한이 있는 Windows 사용자라면 누구나 실행할 수 있습니다. 이 파일은 기본적으로 `x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER1\MSSQL\Binn` 폴더에 저장되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-254">The **sqlmaint** utility can be executed by any Windows user with **Read and Execute** permission on `sqlmaint.exe`, which by default is stored in the `x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER1\MSSQL\Binn` folder.</span></span> <span data-ttu-id="614ba-255">또한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -login_ID **로 지정된** 로그인에는 지정된 동작을 수행하는 데 필요한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-255">Additionally, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login specified with **-login_ID** must have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] permissions required to perform the specified action.</span></span> <span data-ttu-id="614ba-256">Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에 연결하는 경우 인증된 Windows 사용자에 매핑된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로그인에는 지정된 동작을 수행하는 데 필요한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-256">If the connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses Windows Authentication, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login mapped to the authenticated Windows user must have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] permissions required to perform the specified action.</span></span>  
  
 <span data-ttu-id="614ba-257">예를 들어 **-BkUpDB** 를 사용하려면 BACKUP 문을 실행할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-257">For example, using the **-BkUpDB** requires permission to execute the BACKUP statement.</span></span> <span data-ttu-id="614ba-258">또한 **-UpdOptiStats** 인수를 사용하려면 UPDATE STATISTICS 문을 실행할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-258">And using the **-UpdOptiStats** argument requires permission to execute the UPDATE STATISTICS statement.</span></span> <span data-ttu-id="614ba-259">자세한 내용은 온라인 설명서에서 해당 항목의 "사용 권한" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="614ba-259">For more information, see the "Permissions" sections of the corresponding topics in Books Online.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="614ba-260">예</span><span class="sxs-lookup"><span data-stu-id="614ba-260">Examples</span></span>  
  
### <a name="a-performing-dbcc-checks-on-a-database"></a><span data-ttu-id="614ba-261">A.</span><span class="sxs-lookup"><span data-stu-id="614ba-261">A.</span></span> <span data-ttu-id="614ba-262">데이터베이스에서 DBCC 검사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-262">Performing DBCC checks on a database</span></span>  
  
```  
sqlmaint -S MyServer -D AdventureWorks2012 -CkDB -CkAl -CkCat -Rpt C:\MyReports\AdvWks_chk.rpt  
```  
  
### <a name="b-updating-statistics-using-a-15-sample-in-all-databases-in-a-plan-also-shrink-any-of-the-database-that-have-reached-110-mb-to-having-only-10-free-space"></a><span data-ttu-id="614ba-263">B.</span><span class="sxs-lookup"><span data-stu-id="614ba-263">B.</span></span> <span data-ttu-id="614ba-264">계획의 모든 데이터베이스에서 15% 샘플을 사용하여 통계를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-264">Updating statistics using a 15% sample in all databases in a plan.</span></span> <span data-ttu-id="614ba-265">또한 110MB에 도달한 데이터베이스를 축소하여 빈 공간이 10%가 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-265">Also, shrink any of the database that have reached 110 MB to having only 10% free space</span></span>  
  
```  
sqlmaint -S MyServer -PlanName MyUserDBPlan -UpdOptiStats 15 -RmUnusedSpace 110 10  
```  
  
### <a name="c-backing-up-all-the-databases-in-a-plan-to-their-individual-subdirectories-in-the-default-xprogram-filesmicrosoft-sql-servermssql12mssqlservermssqlbackup-directory-also-delete-any-backups-older-than-2-weeks"></a><span data-ttu-id="614ba-266">C.</span><span class="sxs-lookup"><span data-stu-id="614ba-266">C.</span></span> <span data-ttu-id="614ba-267">계획의 모든 데이터베이스를 기본 x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup 디렉터리에 있는 개별 하위 디렉터리에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-267">Backing up all the databases in a plan to their individual subdirectories in the default x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup directory.</span></span> <span data-ttu-id="614ba-268">또한 2주가 지난 백업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="614ba-268">Also, delete any backups older than 2 weeks</span></span>  
  
```  
sqlmaint -S MyServer -PlanName MyUserDBPlan -BkUpDB -BkUpMedia DISK -UseDefDir -CrBkSubDir -DelBkUps 2weeks  
```  
  
### <a name="d-backing-up-a-database-to-the-default-xprogram-filesmicrosoft-sql-servermssql12mssqlservermssqlbackup-directory"></a><span data-ttu-id="614ba-269">D.</span><span class="sxs-lookup"><span data-stu-id="614ba-269">D.</span></span> <span data-ttu-id="614ba-270">기본 x:\Program Files\Microsoft SQL Server\MSSQL12.에 데이터베이스 백업 MSSQLSERVER\MSSQL\Backup 디렉터리. </span><span class="sxs-lookup"><span data-stu-id="614ba-270">Backing up a database to the default x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup directory.</span></span>\  
  
```  
sqlmaint -S MyServer -BkUpDB -BkUpMedia DISK -UseDefDir  
```  
  
## <a name="see-also"></a><span data-ttu-id="614ba-271">참고 항목</span><span class="sxs-lookup"><span data-stu-id="614ba-271">See Also</span></span>  
 <span data-ttu-id="614ba-272">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="614ba-272">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="614ba-273">UPDATE STATISTICS&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="614ba-273">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
