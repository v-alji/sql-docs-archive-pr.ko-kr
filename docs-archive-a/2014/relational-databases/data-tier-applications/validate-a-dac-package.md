---
title: DAC 패키지 유효성 검사 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], validate
- data-tier application [SQL Server], compare
- validate DAC
- compare DACs
- data-tier application [SQL Server], view
- view DAC
ms.assetid: 726ffcc2-9221-424a-8477-99e3f85f03bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 078c7bfeef2ff8636243f4853c03de252c7b9289
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660632"
---
# <a name="validate-a-dac-package"></a><span data-ttu-id="4476b-102">DAC 패키지 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="4476b-102">Validate a DAC Package</span></span>
  <span data-ttu-id="4476b-103">DAC 패키지를 프로덕션 환경에 배포하기 전에 내용을 검토하고 기존 DAC를 업그레이드하기 전에 업그레이드 동작의 유효성을 검사하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-103">It is a good practice to review the contents of a DAC package before deploying it in production, and to validate the upgrade actions before upgrading an existing DAC.</span></span> <span data-ttu-id="4476b-104">사용자의 조직에서 개발되지 않은 패키지를 배포하는 경우에는 더욱 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-104">This is especially true when deploying packages that were not developed in your organization.</span></span>  
  
1.  <span data-ttu-id="4476b-105">**시작하기 전 주의 사항:**  [필수 구성 요소](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="4476b-105">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
2.  <span data-ttu-id="4476b-106">**DAC를 업그레이드하려면 다음을 사용합니다.**  [DAC 내용 보기](#ViewDACContents), [데이터베이스 변경 내용 보기](#ViewDBChanges), [업그레이드 동작 보기](#ViewUpgradeActions), [DAC 비교](#CompareDACs)</span><span class="sxs-lookup"><span data-stu-id="4476b-106">**To upgrade a DAC, using:**  [View the Contents of a DAC](#ViewDACContents), [View Database Changes](#ViewDBChanges), [View Upgrade Actions](#ViewUpgradeActions), [Compare DACs](#CompareDACs)</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="4476b-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="4476b-107">Prerequisites</span></span>  
 <span data-ttu-id="4476b-108">출처를 알 수 없거나 신뢰할 수 없는 DAC 패키지는 배포하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-108">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="4476b-109">이러한 DAC에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 실행하거나 스키마를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-109">Such DACs could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema.</span></span> <span data-ttu-id="4476b-110">출처를 알 수 없거나 신뢰할 수 없는 DAC를 사용하기 전에 격리된 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 테스트 인스턴스에 이를 배포하고, 해당 데이터베이스에 대해 [DBCC CHECKDB&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)를 실행하며, 저장 프로시저 또는 다른 사용자 정의 코드 같은 데이터베이스의 코드도 검사하세요.</span><span class="sxs-lookup"><span data-stu-id="4476b-110">Before you use a DAC from an unknown or untrusted source, deploy it on an isolated test instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], run [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database, and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="view-the-contents-of-a-dac"></a><a name="ViewDACContents"></a> <span data-ttu-id="4476b-111">DAC 내용 보기</span><span class="sxs-lookup"><span data-stu-id="4476b-111">View the Contents of a DAC</span></span>  
 <span data-ttu-id="4476b-112">데이터 계층 애플리케이션(DAC) 패키지의 내용을 볼 수 있는 두 가지 메커니즘이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-112">There are two mechanisms for viewing the contents of a data-tier application (DAC) package.</span></span> <span data-ttu-id="4476b-113">SQL Server Developer Tools의 DAC 프로젝트로 DAC 패키지를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-113">You can import the DAC package to a DAC project in SQL Server Developer Tools.</span></span> <span data-ttu-id="4476b-114">두 번째는 패키지 내용을 폴더에 압축을 푸는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-114">You can unpack the contents of the package to a folder.</span></span>  
  
 <span data-ttu-id="4476b-115">**SQL Server Developer Tools에서 DAC 보기**</span><span class="sxs-lookup"><span data-stu-id="4476b-115">**View a DAC in SQL Server Developer Tools**</span></span>  
  
1.  <span data-ttu-id="4476b-116">**파일** 메뉴를 열고 **새로 만들기**를 선택한 다음, **프로젝트...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-116">Open the **File** menu, select **New**, and then select **Project...**.</span></span>  
  
2.  <span data-ttu-id="4476b-117">**SQL Server** 프로젝트 템플릿을 선택하고 **이름**, **위치**및 **솔루션 이름**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-117">Select the **SQL Server** project template, and specify a **Name**, **Location**, and **Solution name**.</span></span>  
  
3.  <span data-ttu-id="4476b-118">**솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-118">In **Solution Explorer**, right click the project node and select **Properties...**.</span></span>  
  
4.  <span data-ttu-id="4476b-119">**프로젝트 설정** 탭의 **출력 유형** 섹션에서 **데이터 계층 애플리케이션(.dacpac 파일)** 확인란을 선택한 다음 속성 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-119">On the **Project Settings** tab, in the **Output Types** section, select the **Data-tier Application (.dacpac File)** check box, and then close the properties dialog.</span></span>  
  
5.  <span data-ttu-id="4476b-120">**솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **데이터 계층 애플리케이션 가져오기...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-120">In **Solution Explorer**, right click the project node and select **Import Data-tier Application...**.</span></span>  
  
6.  <span data-ttu-id="4476b-121">**솔루션 탐색기** 를 사용하여 서버 선택 정책과 배포 이전 및 배포 이후 스크립트와 같은 DAC의 모든 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-121">Use **Solution Explorer** to open all of the files in the DAC, such as the server selection policy and the pre- and post-deployment scripts.</span></span>  
  
7.  <span data-ttu-id="4476b-122">**스키마 뷰** 를 사용하여 스키마 내의 모든 개체를 검토할 수 있으며, 특히 함수나 저장 프로시저와 같은 개체 내의 코드를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-122">Use the **Schema View** to review all of the objects in the schema, particularly reviewing the code in objects such as functions or stored procedures.</span></span>  
  
 <span data-ttu-id="4476b-123">**폴더에서 DAC 보기**</span><span class="sxs-lookup"><span data-stu-id="4476b-123">**View a DAC in a Folder**</span></span>  
  
-   <span data-ttu-id="4476b-124">[Unpack a DAC Package](unpack-a-dac-package.md)의 지침에 따라 폴더에 DAC 패키지의 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-124">Unpack the DAC package into a folder by following the instructions in [Unpack a DAC Package](unpack-a-dac-package.md).</span></span>  
  
-   <span data-ttu-id="4476b-125">[!INCLUDE[tsql](../../includes/tsql-md.md)] 의 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 쿼리 편집기에서 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]스크립트를 열어서 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-125">View the contents of the [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts by opening them in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="4476b-126">메모장 같은 도구에서 텍스트 파일의 내용 보기</span><span class="sxs-lookup"><span data-stu-id="4476b-126">View the contents of the text files in tools such as notepad.</span></span>  
  
##  <a name="view-database-changes"></a><a name="ViewDBChanges"></a> <span data-ttu-id="4476b-127">데이터베이스 변경 내용 보기</span><span class="sxs-lookup"><span data-stu-id="4476b-127">View Database Changes</span></span>  
 <span data-ttu-id="4476b-128">현재 버전의 DAC를 프로덕션 환경에 배포한 이후에 연결된 데이터베이스를 직접 변경하여 새 버전의 DAC에 정의된 스키마와 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-128">After the current version of a DAC was deployed to production, changes may have been made directly to the associated database that might conflict with the schema defined in a new version of the DAC.</span></span> <span data-ttu-id="4476b-129">따라서 새 버전의 DAC로 업그레이드하기 전에 데이터베이스가 그런 식으로 변경되었는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="4476b-129">Before upgrading to a new version of the DAC, check to see if such changes have been made to the database.</span></span>  
  
 <span data-ttu-id="4476b-130">**마법사를 사용하여 데이터베이스 변경 내용 보기**</span><span class="sxs-lookup"><span data-stu-id="4476b-130">**View Database Changes by Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="4476b-131">새 버전의 DAC를 포함하는 DAC 패키지와 현재 배포된 DAC를 지정하여 **데이터 계층 애플리케이션 업그레이드** 마법사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-131">Run the **Upgrade Data-tier Application** wizard, specifying the currently deployed DAC and the DAC package containing the new version of the DAC.</span></span>  
  
2.  <span data-ttu-id="4476b-132">**변경 내용 검색** 페이지에서 데이터베이스에 대한 변경 내용 보고서를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-132">On the **Detect Change** page, review the report of the changes that have been made to the database.</span></span>  
  
3.  <span data-ttu-id="4476b-133">업그레이드를 중단하려면 **취소** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-133">Select **Cancel** if you do not want to continue with the upgrade.</span></span>  
  
4.  <span data-ttu-id="4476b-134">마법사 사용에 대한 자세한 내용은 [데이터 계층 애플리케이션 업그레이드](upgrade-a-data-tier-application.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4476b-134">For more information on using the wizard, see [Upgrade a Data-tier Application](upgrade-a-data-tier-application.md).</span></span>  
  
### <a name="view-database-changes-by-using-powershell"></a><span data-ttu-id="4476b-135">PowerShell을 사용하여 데이터베이스 변경 내용 보기</span><span class="sxs-lookup"><span data-stu-id="4476b-135">View Database Changes by Using PowerShell</span></span>
  
1.  <span data-ttu-id="4476b-136">SMO Server 개체를 만든 다음 보려는 DAC를 포함하는 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-136">Create a SMO Server object and set it to the instance that contains the DAC to be viewed.</span></span>  
  
2.  <span data-ttu-id="4476b-137">`ServerConnection` 개체를 열고 동일한 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-137">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="4476b-138">DAC 이름을 변수로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-138">Specify the DAC name in a variable.</span></span>  
  
4.  <span data-ttu-id="4476b-139">`GetDatabaseChanges()` 메서드를 사용하여 `ChangeResults` 개체를 검색하고 개체를 텍스트 파일에 파이핑하여 새 개체, 삭제된 개체 및 변경된 개체에 대한 간단한 보고서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-139">Use the `GetDatabaseChanges()` method to retrieve a `ChangeResults` object, and pipe the object to a text file to generate a simple report of new, deleted, and changed objects.</span></span>  
  
### <a name="view-database-changes-example-powershell"></a><span data-ttu-id="4476b-140">데이터베이스 변경 내용 보기 예(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="4476b-140">View Database Changes Example (PowerShell)</span></span>
  
 <span data-ttu-id="4476b-141">다음 예에서는 MyApplicaiton이라는 배포된 DAC에 대한 데이터베이스 변경 내용을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-141">The following example reports any database changes that have been made in a deployed DAC named MyApplicaiton.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the change list and save to file.  
$dacChanges = $dacstore.GetDatabaseChanges($dacName) | Out-File -Filepath C:\DACScripts\MyApplicationChanges.txt  
```  
  
##  <a name="view-upgrade-actions"></a><a name="ViewUpgradeActions"></a><span data-ttu-id="4476b-142">업그레이드 동작 보기</span><span class="sxs-lookup"><span data-stu-id="4476b-142">View Upgrade Actions</span></span>  
 <span data-ttu-id="4476b-143">새 버전의 DAC 패키지를 사용하여 이전 DAC 패키지에서 배포된 DAC를 업그레이드하기 전에 업그레이드 동안 실행할 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 포함된 보고서를 생성한 다음 문을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-143">Before using a new version of a DAC package to upgrade a DAC that was deployed from an earlier DAC package, you can generate a report that contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that will be run during the upgrade, and then review the statements.</span></span>  
  
 <span data-ttu-id="4476b-144">**마법사를 사용하여 업그레이드 동작 보고**</span><span class="sxs-lookup"><span data-stu-id="4476b-144">**Report Upgrade Actions by Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="4476b-145">새 버전의 DAC를 포함하는 DAC 패키지와 현재 배포된 DAC를 지정하여 **데이터 계층 애플리케이션 업그레이드** 마법사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-145">Run the **Upgrade Data-tier Application** wizard, specifying the currently deployed DAC and the DAC package containing the new version of the DAC.</span></span>  
  
2.  <span data-ttu-id="4476b-146">**요약** 페이지에서 업그레이드 동작 보고서를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-146">On the **Summary** page, review the report of the upgrade actions.</span></span>  
  
3.  <span data-ttu-id="4476b-147">업그레이드를 중단하려면 **취소** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-147">Select **Cancel** if you do not want to continue with the upgrade.</span></span>  
  
4.  <span data-ttu-id="4476b-148">마법사 사용에 대한 자세한 내용은 [데이터 계층 애플리케이션 업그레이드](upgrade-a-data-tier-application.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4476b-148">For more information on using the wizard, see [Upgrade a Data-tier Application](upgrade-a-data-tier-application.md).</span></span>  
  
 <span data-ttu-id="4476b-149">**PowerShell을 사용하여 업그레이드 동작 보고**</span><span class="sxs-lookup"><span data-stu-id="4476b-149">**Report Upgrade Actions by Using PowerShell**</span></span>  
  
1.  <span data-ttu-id="4476b-150">SMO Server 개체를 만든 다음 배포된 DAC를 포함하는 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-150">Create a SMO Server object and set it to the instance that contains the deployed DAC.</span></span>  
  
2.  <span data-ttu-id="4476b-151">`ServerConnection` 개체를 열고 동일한 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-151">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="4476b-152">`System.IO.File`을 사용하여 DAC 패키지 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-152">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="4476b-153">DAC 이름을 변수로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-153">Specify the DAC name in a variable.</span></span>  
  
5.  <span data-ttu-id="4476b-154">`GetIncrementalUpgradeScript()` 메서드를 사용하여 업그레이드를 실행할 Transact-SQL 문 목록을 가져온 다음 목록을 텍스트 파일에 파이핑합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-154">Use the `GetIncrementalUpgradeScript()` method to get a list of the Transact-SQL statements an upgrade would run, and pipe the list to a text file.</span></span>  
  
6.  <span data-ttu-id="4476b-155">DAC 패키지 파일을 읽는 데 사용되는 파일 스트림을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-155">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="view-upgrade-actions-example-powershell"></a><span data-ttu-id="4476b-156">업그레이드 동작 보기 예(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="4476b-156">View Upgrade Actions Example (PowerShell)</span></span>
  
 <span data-ttu-id="4476b-157">다음 예에서는 MyApplicaiton이라는 DAC를 MyApplicationVNext.dacpac 파일에 정의된 스키마로 업그레이드하기 위해 실행하는 Transact-SQL 문에 대해 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-157">The following example reports the Transact-SQL statements that would be run to upgrading a DAC named MyApplicaiton to the schema defined in a MyApplicationVNext.dacpac file.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplicationVNext.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the upgrade script and save to file.  
$dacstore.GetIncrementalUpgradeScript($dacName, $dacType) | Out-File -Filepath C:\DACScripts\MyApplicationUpgrade.sql  
  
## Close the filestream to the new DAC package.  
$fileStream.Close()  
```  
  
##  <a name="compare-dacs"></a><a name="CompareDACs"></a><span data-ttu-id="4476b-158">Dac 비교</span><span class="sxs-lookup"><span data-stu-id="4476b-158">Compare DACs</span></span>  
 <span data-ttu-id="4476b-159">DAC를 업그레이드하기 전에 데이터베이스와 인스턴스 수준 개체에서 현재와 새 DAC의 차이를 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-159">Before upgrading a DAC, it is a good practice to review the differences in the database and instance-level objects between the current and new DACs.</span></span> <span data-ttu-id="4476b-160">현재 DAC의 패키지 복사본이 없는 경우에는 현재 데이터베이스에서 패키지를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-160">If you do not have a copy of the package for the current DAC, you can extract a package from the current database.</span></span>  
  
 <span data-ttu-id="4476b-161">두 DAC 프로젝트를 SQL Server Developer Tools의 DAC 프로젝트로 가져오면 스키마 비교 도구를 사용하여 두 DAC 간의 차이점을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-161">If you import both DAC packages into DAC projects in SQL Server Developer Tools, you can use the Schema Compare tool to analyze the differences between the two DACs.</span></span>  
  
 <span data-ttu-id="4476b-162">또는 별도의 폴더에 DAC의 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-162">Alternatively, unpack the DACs into separate folders.</span></span> <span data-ttu-id="4476b-163">그런 다음 WinDiff 유틸리티와 같은 비교 도구를 사용하여 차이를 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4476b-163">You can then use a difference tool, such as the WinDiff utility, to analyze the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4476b-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4476b-164">See Also</span></span>  
 <span data-ttu-id="4476b-165">[데이터 계층 애플리케이션](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="4476b-165">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="4476b-166">[데이터 계층 응용 프로그램 배포](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="4476b-166">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="4476b-167">데이터 계층 응용 프로그램 업그레이드</span><span class="sxs-lookup"><span data-stu-id="4476b-167">Upgrade a Data-tier Application</span></span>](upgrade-a-data-tier-application.md)  
