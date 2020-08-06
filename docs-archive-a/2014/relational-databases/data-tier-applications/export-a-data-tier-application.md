---
title: 데이터 계층 애플리케이션 내보내기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.exportdac.settings.f1
- sql12.swb. exportdac.settings.f1
- sql12.swb.exportdac.welcome.f1
- sql12.swb. exportdac.summary.f1
- sql12.swb.exportdac.progress.f1
- sql12.swb.exportdac.summary.f1
- sql12.swb.exportdac.results.f1
- sql12.swb. exportdac.results.f1
helpviewer_keywords:
- How to [DAC], export
- wizard [DAC], export
- export DAC
- data-tier application [SQL Server], export
ms.assetid: 61915bc5-0f5f-45ac-8cfe-3452bc185558
author: stevestein
ms.author: sstein
ms.openlocfilehash: d5e1bbfc5c38dee5e7f29598086d87b680880641
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659454"
---
# <a name="export-a-data-tier-application"></a><span data-ttu-id="2c59e-102">데이터 계층 애플리케이션 내보내기</span><span class="sxs-lookup"><span data-stu-id="2c59e-102">Export a Data-tier Application</span></span>
  <span data-ttu-id="2c59e-103">DAC(데이터 계층 애플리케이션) 또는 데이터베이스를 내보내면 데이터베이스의 개체 정의와 테이블에 포함된 모든 데이터를 포함하는 내보내기 파일이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-103">Exporting a deployed data-tier application (DAC) or database creates an export file that includes both the definitions of the objects in the database and all of the data contained in the tables.</span></span> <span data-ttu-id="2c59e-104">이 내보내기 파일을 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 다른 인스턴스 또는 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-104">The export file can then be imported to another instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="2c59e-105">내보내기-가져오기 작업을 결합하여 인스턴스 간에 DAC를 마이그레이션하거나 논리 백업을 만들거나 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에 배포된 데이터베이스의 온-프레미스 복사본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-105">The export-import operations can be combined to migrate a DAC between instances, to create a logical backup, or to create an on-premise copy of a database deployed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="2c59e-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="2c59e-106">Before You Begin</span></span>  
 <span data-ttu-id="2c59e-107">내보내기 프로세스에서는 DAC 내보내기 파일을 두 단계로 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-107">The export process builds a DAC export file in two stages.</span></span>  
  
1.  <span data-ttu-id="2c59e-108">내보내기를 수행하면 DAC 추출 시 DAC 패키지 파일에 DAC 정의가 작성되듯이 내보내기 파일(BACPAC 파일)에 DAC 정의가 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-108">The export builds a DAC definition in the export file - BACPAC file - in the same way a DAC extract builds a DAC definition in a DAC package file.</span></span> <span data-ttu-id="2c59e-109">내보낸 DAC 정의에는 현재 데이터베이스의 모든 개체가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-109">The exported DAC definition includes all of the objects in the current database.</span></span> <span data-ttu-id="2c59e-110">DAC에서 원래 배포된 데이터베이스에 대해 내보내기 프로세스를 실행할 때 배포 후에 데이터베이스를 직접 변경한 경우 내보낸 정의는 원본 DAC에 정의된 개체 집합이 아니라 데이터베이스의 개체 집합과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-110">If the export process is run against a database that was originally deployed from a DAC, and changes were made directly to the database after deployment, the exported definition matches the object set in the database, not what was defined in the original DAC.</span></span>  
  
2.  <span data-ttu-id="2c59e-111">보내기에서는 데이터베이스의 모든 테이블에서 데이터를 대량 복사한 다음 내보내기 파일에 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-111">The export bulk copies out the data from all of the tables in the database and incorporates the data into the export file.</span></span>  
  
 <span data-ttu-id="2c59e-112">내보내기 프로세스에서는 DAC 버전을 1.0.0.0으로 설정하고 내보내기 파일의 DAC 설명을 빈 문자열로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-112">The export process sets the DAC version to 1.0.0.0 and the DAC description in the export file to an empty string.</span></span> <span data-ttu-id="2c59e-113">데이터베이스가 DAC에서 배포된 경우에는 내보내기 파일의 DAC 정의에 원본 DAC에 지정된 것과 동일한 이름이 포함되고, 그렇지 않은 경우에는 DAC 이름이 데이터베이스 이름으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-113">If the database was deployed from a DAC, the DAC definition in the export file contains the name given to the original DAC, otherwise the DAC name is set to the database name.</span></span>  
  

###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="2c59e-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="2c59e-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="2c59e-115">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]또는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4(서비스 팩 4) 이상의 데이터베이스에서만 DAC 또는 데이터베이스를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-115">A DAC or database can only be exported from a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span>  
  
 <span data-ttu-id="2c59e-116">DAC 또는 포함된 사용자가 지원하지 않는 개체가 있는 데이터베이스를 내보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-116">You cannot export a database that has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="2c59e-117">DAC에서 지원되는 개체 유형에 대한 자세한 내용은 [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c59e-117">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2c59e-118">권한</span><span class="sxs-lookup"><span data-stu-id="2c59e-118">Permissions</span></span>  
 <span data-ttu-id="2c59e-119">DAC를 내보내려면 **sys.sql_expression_dependencies**에 대한 SELECT 권한뿐만 아니라 최소한 ALTER ANY LOGIN 및 데이터베이스 범위 VIEW DEFINITION 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-119">Exporting a DAC requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="2c59e-120">DAC를 내보내려면 securityadmin 고정 서버 역할의 멤버이면서 DAC를 내보내는 데이터베이스의 database_owner 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-120">Exporting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is exported.</span></span> <span data-ttu-id="2c59e-121">sysadmin 고정 서버 역할의 멤버 또는 기본 제공 SQL Server 시스템 관리자 계정인 **sa** 는 DAC를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-121">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also export a DAC.</span></span>  
  
##  <a name="using-the-export-data-tier-application-wizard"></a><a name="UsingDeployDACWizard"></a><span data-ttu-id="2c59e-122">데이터 계층 응용 프로그램 내보내기 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="2c59e-122">Using the Export Data-tier Application Wizard</span></span>  
 <span data-ttu-id="2c59e-123">**마법사를 사용하여 DAC를 내보내려면**</span><span class="sxs-lookup"><span data-stu-id="2c59e-123">**To Export a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="2c59e-124">온-프레미스 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-124">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], whether on-premise or in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
2.  <span data-ttu-id="2c59e-125">**개체 탐색기**에서 DAC를 내보내려는 인스턴스에 대한 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-125">In **Object Explorer**, expand the node for the instance from which you want to export the DAC.</span></span>  
  
3.  <span data-ttu-id="2c59e-126">데이터베이스 이름을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-126">Right-click the database name.</span></span>  
  
4.  <span data-ttu-id="2c59e-127">**태스크**를 클릭한 다음, **데이터 계층 애플리케이션 내보내기...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-127">Click **Tasks** and then select **Export Data-tier Application...**</span></span>  
  
5.  <span data-ttu-id="2c59e-128">마법사 대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-128">Complete the wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="2c59e-129">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-129">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="2c59e-130">내보내기 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-130">Export Settings Page</span></span>](#Export_settings)  
  
    -   [<span data-ttu-id="2c59e-131">유효성 검사 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-131">Validation Page</span></span>](#Validation)  
  
    -   [<span data-ttu-id="2c59e-132">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-132">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="2c59e-133">진행률 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-133">Progress Page</span></span>](#Progress)  
  
    -   [<span data-ttu-id="2c59e-134">결과 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-134">Results Page</span></span>](#Results)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="2c59e-135">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-135">Introduction Page</span></span>  
 <span data-ttu-id="2c59e-136">이 페이지에서는 데이터 계층 애플리케이션 내보내기 마법사의 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-136">This page describes the steps for the Export Data-tier Application Wizard.</span></span>  
  
 <span data-ttu-id="2c59e-137">**Options**</span><span class="sxs-lookup"><span data-stu-id="2c59e-137">**Options**</span></span>  
  
 <span data-ttu-id="2c59e-138">**이 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="2c59e-138">**Do not show this page again.**</span></span> <span data-ttu-id="2c59e-139">- 앞으로 소개 페이지가 표시되지 않도록 하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-139">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="2c59e-140">**다음** - **DAC 패키지 선택** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-140">**Next** - Proceeds to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="2c59e-141">**취소** -작업을 취소 하 고 마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-141">**Cancel** - Cancels the operation and closes the Wizard.</span></span>  
  
##  <a name="export-settings-page"></a><a name="Export_settings"></a><span data-ttu-id="2c59e-142">내보내기 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-142">Export Settings Page</span></span>  
 <span data-ttu-id="2c59e-143">이 페이지에서는 BACPAC 파일을 만들려는 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-143">Use this page to specify the location where you want the BACPAC file to be created.</span></span>  
  
-   <span data-ttu-id="2c59e-144">**로컬 디스크에 저장** - 로컬 컴퓨터의 디렉터리에 BACPAC 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-144">**Save to local disk** - Creates a BACPAC file in a directory on the local computer.</span></span> <span data-ttu-id="2c59e-145">**찾아보기...** 를 클릭하여 로컬 컴퓨터로 이동하거나 제공된 공간에 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-145">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span> <span data-ttu-id="2c59e-146">경로 이름에 파일 이름과 .bacpac 확장명을 모두 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-146">The path name must include a file name and the .bacpac extension.</span></span>  
  
-   <span data-ttu-id="2c59e-147">**Azure에 저장** - Azure 컨테이너에 BACPAC 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-147">**Save to Azure** - Creates a BACPAC file in an Azure container.</span></span> <span data-ttu-id="2c59e-148">이 옵션의 유효성을 검사하려면 Azure 컨테이너에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-148">You must connect to an Azure container in order to validate this option.</span></span> <span data-ttu-id="2c59e-149">또한 이 옵션을 사용하려면 임시 파일을 보관할 로컬 디렉터리를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-149">Note that this option also requires that you specify a local directory for the temporary file.</span></span> <span data-ttu-id="2c59e-150">지정된 위치에 임시 파일이 만들어지고 작업이 완료된 후에도 해당 위치에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-150">Note that the temporary file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
 <span data-ttu-id="2c59e-151">내보낼 테이블 하위 집합을 지정하려면 **고급** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-151">To specify a subset of tables to export, use the **Advanced** option.</span></span>  
  
##  <a name="validation-page"></a><a name="Validation"></a><span data-ttu-id="2c59e-152">유효성 검사 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-152">Validation Page</span></span>  
 <span data-ttu-id="2c59e-153">유효성 검사 페이지에서 작업을 차단한 문제를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-153">Use the validation page to review any issues that block the operation.</span></span> <span data-ttu-id="2c59e-154">계속하려면 차단 문제를 해결하고 **유효성 검사 다시 실행** 을 클릭하여 유효성 검사에 성공했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-154">To continue, resolve blocking issues and then click **Re-run Validation** to ensure that validation is successful.</span></span>  
  
 <span data-ttu-id="2c59e-155">계속하려면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-155">To continue, click **Next**.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="2c59e-156">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-156">Summary Page</span></span>  
 <span data-ttu-id="2c59e-157">이 페이지에서 작업에 대해 지정한 원본 및 대상 설정을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-157">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="2c59e-158">지정한 설정을 사용하여 내보내기 작업을 완료하려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-158">To complete the export operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="2c59e-159">내보내기 작업을 취소하고 마법사를 종료하려면 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-159">To cancel the export operation and exit the Wizard, click **Cancel**.</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="2c59e-160">진행률 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-160">Progress Page</span></span>  
 <span data-ttu-id="2c59e-161">이 페이지에는 작업 상태를 나타내는 진행률 표시줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-161">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="2c59e-162">자세한 상태를 보려면 **자세히 보기** 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-162">To view detailed status, click the **View details** option.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="2c59e-163">결과 페이지</span><span class="sxs-lookup"><span data-stu-id="2c59e-163">Results Page</span></span>  
 <span data-ttu-id="2c59e-164">이 페이지에서는 내보내기 작업의 성공 또는 실패를 보고하고 각 작업의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-164">This page reports the success or failure of the export operation, showing the results of each action.</span></span> <span data-ttu-id="2c59e-165">오류가 발생한 동작에는 모두 **결과** 열에 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-165">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="2c59e-166">링크를 클릭하면 해당 동작의 오류에 대한 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-166">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="2c59e-167">**마침** 을 클릭 하 여 마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-167">Click **Finish** to close the Wizard.</span></span>  
  
##  <a name="using-a-net-framework-application"></a><a name="NetApp"></a><span data-ttu-id="2c59e-168">.Net Framework 응용 프로그램 사용</span><span class="sxs-lookup"><span data-stu-id="2c59e-168">Using a .Net Framework Application</span></span>  
 <span data-ttu-id="2c59e-169">**.Net Framework 애플리케이션에서 Export() 메서드를 사용하여 DAC를 내보냅니다.**</span><span class="sxs-lookup"><span data-stu-id="2c59e-169">**To export a DAC using the Export() method in a .Net Framework application.**</span></span>  
  
 <span data-ttu-id="2c59e-170">코드 예제를 보려면 [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)에서 DAC 샘플 애플리케이션을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-170">To view a code example, download the DAC sample application on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)</span></span>  
  
1.  <span data-ttu-id="2c59e-171">SMO Server 개체를 만든 다음 내보낼 DAC를 포함하는 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-171">Create a SMO Server object and set it to the instance that contains the DAC to be exported.</span></span>  
  
2.  <span data-ttu-id="2c59e-172">`ServerConnection` 개체를 열고 동일한 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-172">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="2c59e-173">`Export` 형식의 `Microsoft.SqlServer.Management.Dac.DacStore` 메서드를 사용하여 DAC를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-173">Use the `Export` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to export the DAC.</span></span> <span data-ttu-id="2c59e-174">내보낼 DAC의 이름과 내보내기 파일을 배치할 폴더의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c59e-174">Specify the name of the DAC to be exported, and the path to the folder where the export file is to be placed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c59e-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c59e-175">See Also</span></span>  
 <span data-ttu-id="2c59e-176">[데이터 계층 애플리케이션](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="2c59e-176">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="2c59e-177">데이터베이스에서 DAC 추출</span><span class="sxs-lookup"><span data-stu-id="2c59e-177">Extract a DAC From a Database</span></span>](extract-a-dac-from-a-database.md)  
  
  
