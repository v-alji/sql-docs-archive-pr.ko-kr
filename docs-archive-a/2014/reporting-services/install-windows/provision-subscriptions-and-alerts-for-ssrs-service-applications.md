---
title: SSRS 서비스 애플리케이션에 대한 구독 및 경고 프로비전 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Shared Service
- SharePoint Mode [Reporting Services]
- SharePoint Mode
- Reporting Services Service Application
- SSRS service application
ms.assetid: d0de3f1f-4887-47fb-bacf-46aaad74c4be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c09033b6a31295b8fbe42058cba9059f5d05629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742940"
---
# <a name="provision-subscriptions-and-alerts-for-ssrs-service-applications"></a><span data-ttu-id="fef14-102">SSRS 서비스 애플리케이션에 대한 구독 및 경고 프로비전</span><span class="sxs-lookup"><span data-stu-id="fef14-102">Provision Subscriptions and Alerts for SSRS Service Applications</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fef14-103">구독 및 데이터 경고에는 SQL Server 에이전트가 필요하며 SQL Server 에이전트에 대한 사용 권한 구성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-103">subscriptions and data alerts require SQL Server Agent and require the configuration of permissions for SQL Server Agent.</span></span> <span data-ttu-id="fef14-104">SQL Server 에이전트가 필요하고 SQL Server 에이전트 실행 확인을 나타내는 오류 메시지가 표시되는 경우 사용 권한을 업데이트하거나 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-104">If you see error messages that indicate SQL Server Agent is required and you have verified SQL Server Agent is running, then update or verify permissions.</span></span> <span data-ttu-id="fef14-105">이 항목의 범위는 SharePoint 모드의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 이며, 이 항목에서는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구독을 사용하여 SQL Server 에이전트의 사용 권한을 업데이트하는 세 가지 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-105">The scope of this topic is [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode and the topic describes three ways you can update the permissions of SQL Server Agent with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions.</span></span> <span data-ttu-id="fef14-106">이 항목의 단계에 사용하는 자격 증명에는 서비스 애플리케이션, msdb 및 master 데이터베이스의 개체를 위한 RSExecRole에 실행 권한을 부여하기에 충분한 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-106">The credentials you use for the steps in this topic need to have sufficient permissions to grant execute permissions to the RSExecRole for objects in the service application, msdb, and master databases.</span></span>

||
|-|
|<span data-ttu-id="fef14-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** Sharepoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="fef14-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="fef14-108">![서비스 애플리케이션 DB에 대한 SQL 에이전트 권한](../../../2014/sql-server/install/media/rs-provisionsqlagent.gif "서비스 애플리케이션 DB에 대한 SQL 에이전트 권한")</span><span class="sxs-lookup"><span data-stu-id="fef14-108">![SQL Agent permissions to Service Application DBs](../../../2014/sql-server/install/media/rs-provisionsqlagent.gif "SQL Agent permissions to Service Application DBs")</span></span>

||<span data-ttu-id="fef14-109">Description</span><span class="sxs-lookup"><span data-stu-id="fef14-109">Description</span></span>|
|------|-----------------|
|<span data-ttu-id="fef14-110">**1**</span><span class="sxs-lookup"><span data-stu-id="fef14-110">**1**</span></span>|<span data-ttu-id="fef14-111">Reporting Services 서비스 애플리케이션 데이터베이스를 호스팅하는 SQL Server 데이터베이스 엔진의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-111">The instance of SQL Server Database engine that is hosting the Reporting Services service application databases.</span></span>|
|<span data-ttu-id="fef14-112">**2**</span><span class="sxs-lookup"><span data-stu-id="fef14-112">**2**</span></span>|<span data-ttu-id="fef14-113">SQL 데이터베이스 엔진의 인스턴스에 대한 SQL Server 에이전트의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-113">The instance of SQL Server agent for the instance of the SQL database engine.</span></span>|
|<span data-ttu-id="fef14-114">**3**</span><span class="sxs-lookup"><span data-stu-id="fef14-114">**3**</span></span>|<span data-ttu-id="fef14-115">Reporting Services 서비스 애플리케이션 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-115">The Reporting Services service application databases.</span></span> <span data-ttu-id="fef14-116">이름은 서비스 애플리케이션을 만드는 데 사용된 정보를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-116">The names are based on the information used for creating the service application.</span></span> <span data-ttu-id="fef14-117">다음은 데이터베이스 이름의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-117">The following are example database names:</span></span><br /><br /> <span data-ttu-id="fef14-118">ReportingService_2fbae157295d49df86d0b85760c704b0</span><span class="sxs-lookup"><span data-stu-id="fef14-118">ReportingService_2fbae157295d49df86d0b85760c704b0</span></span><br /><br /> <span data-ttu-id="fef14-119">ReportingService_2fbae157295d49df86d0b85760c704b0_Alerting</span><span class="sxs-lookup"><span data-stu-id="fef14-119">ReportingService_2fbae157295d49df86d0b85760c704b0_Alerting</span></span><br /><br /> <span data-ttu-id="fef14-120">ReportingService_2fbae157295d49df86d0b85760c704b0TempDB</span><span class="sxs-lookup"><span data-stu-id="fef14-120">ReportingService_2fbae157295d49df86d0b85760c704b0TempDB</span></span>|
|<span data-ttu-id="fef14-121">**4**</span><span class="sxs-lookup"><span data-stu-id="fef14-121">**4**</span></span>|<span data-ttu-id="fef14-122">SQL Server 데이터베이스 엔진 인스턴스의 마스터 및 MSDB 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-122">The master and MSDB database of the instance of the SQL Server Database engine.</span></span>|

 <span data-ttu-id="fef14-123">다음 세 가지 방법 중 하나를 사용하여 사용 권한을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-123">Use one the following three methods to update the permissions:</span></span>

1.  <span data-ttu-id="fef14-124">**구독 및 경고 프로비전** 페이지에서 자격 증명을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-124">From the **Provisions and Subscriptions and Alerts** page, type credentials and click **ok**.</span></span>

2.  <span data-ttu-id="fef14-125">구독 및 경고 프로비전 페이지에서 **스크립트 다운로드** 단추를 클릭하여 사용 권한 구성에 사용될 수 있는 Transact-SQL 스크립트를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-125">From the Provisions and Subscriptions and Alerts page, click the **Download Script** button to download a transact SQL script that can be used to configure permissions.</span></span>

3.  <span data-ttu-id="fef14-126">PowerShell cmdlet을 실행하여 사용 권한 구성에 사용될 수 있는 Transact-SQL 스크립트를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-126">Run a PowerShell cmdlet to build a transact SQL script that can be used to configure permissions.</span></span>

### <a name="to-update-permissions-using-the-provision-page"></a><span data-ttu-id="fef14-127">프로비전 페이지를 사용하여 사용 권한을 업데이트하려면</span><span class="sxs-lookup"><span data-stu-id="fef14-127">To update permissions using the provision page</span></span>

1.  <span data-ttu-id="fef14-128">SharePoint 중앙 관리의 **애플리케이션 관리** 그룹에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-128">From SharePoint Central Administration, in the **Application Management** group click **Manage Service Applications**</span></span>

2.  <span data-ttu-id="fef14-129">목록에서 서비스 애플리케이션을 찾고 애플리케이션 이름을 클릭하거나 **유형** 열을 클릭하여 서비스 애플리케이션을 선택하고 SharePoint 리본에서 **관리** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-129">Find your service application in the list and click the name of the application or click the **Type** column to select the services application and click the **Manage** button in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="fef14-130">**Reporting Services 애플리케이션 관리** 페이지에서 **구독 및 경고 프로비전**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-130">On the **Manage Reporting Services Application** page, click **Provision Subscriptions and Alerts**.</span></span>

4.  <span data-ttu-id="fef14-131">SharePoint 관리자가 Master 데이터베이스 및 서비스 애플리케이션 데이터베이스에 대한 충분한 권한이 있을 경우 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-131">If the SharePoint administrator has enough privileges to the Master database and the service application databases, type those credentials.</span></span>

5.  <span data-ttu-id="fef14-132">**확인** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-132">Click the **OK** button.</span></span>

##  <a name="to-download-the-transact-sql-script"></a><a name="bkmk_download"></a> <span data-ttu-id="fef14-133">Transact-SQL 스크립트를 다운로드하려면</span><span class="sxs-lookup"><span data-stu-id="fef14-133">To download the Transact-SQL Script</span></span>

1.  <span data-ttu-id="fef14-134">SharePoint 중앙 관리의 **애플리케이션 관리** 그룹에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-134">From SharePoint Central Administration, in the **Application Management** group click **Manage Service Applications**</span></span>

2.  <span data-ttu-id="fef14-135">목록에서 서비스 애플리케이션을 찾고 애플리케이션 이름을 클릭하거나 **유형** 열을 클릭하여 서비스 애플리케이션을 선택하고 SharePoint 리본에서 **관리** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-135">Find your service application in the list and click the name of the application or click the **Type** column to select the services application and click the **Manage** button in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="fef14-136">**Reporting Services 애플리케이션 관리** 페이지에서 **구독 및 경고 프로비전**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-136">On the **Manage Reporting Services Application** page, click **Provision Subscriptions and Alerts**.</span></span>

4.  <span data-ttu-id="fef14-137">**상태 보기** 영역에서 SQL Server 에이전트가 실행되고 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="fef14-137">In the **View Status** area, verify SQL Server Agent is running.</span></span>

5.  <span data-ttu-id="fef14-138">**스크립트 다운로드** 를 클릭하여 SQL Server Management Studio에서 권한 부여를 위해 실행할 수 있는 Transact-SQL 스크립트를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-138">Click **Download Script** to download a transact SQL script you can run in SQL Server Management studio to grant permissions.</span></span> <span data-ttu-id="fef14-139">만들어진 스크립트 파일 이름에는 Reporting Services 서비스 애플리케이션의 이름이 포함됩니다(예: **[서비스 애플리케이션 이름]-GrantRights.sql**).</span><span class="sxs-lookup"><span data-stu-id="fef14-139">The script file name that is created will contain the name of your Reporting Services service application name, for example **[name of the service application]-GrantRights.sql**.</span></span>

### <a name="to-generate-the-transact-sql-statement-with-powershell"></a><span data-ttu-id="fef14-140">PowerShell을 사용하여 Transact-SQL 문을 만들려면</span><span class="sxs-lookup"><span data-stu-id="fef14-140">To generate the Transact-SQL statement with PowerShell</span></span>

1.  <span data-ttu-id="fef14-141">SharePoint 2010 관리 셸에서 Windows PowerShell cmdlet을 사용하여 Transact-SQL 스크립트를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-141">You can also use a Windows PowerShell cmdlet in the SharePoint 2010 Management Shell to create the Transact-SQL script.</span></span>

2.  <span data-ttu-id="fef14-142">**시작** 메뉴에서 **모든 프로그램**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-142">On the **Start** menu, click **All Programs**.</span></span>

3.  <span data-ttu-id="fef14-143">**Microsoft SharePoint 2010 제품** 을 확장하고 **Microsoft SharePoint 2010 관리 셸**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-143">Expand **Microsoft SharePoint 2010 Products** and click **SharePoint 2010 Management Shell**.</span></span>

4.  <span data-ttu-id="fef14-144">보고서 서버 데이터베이스, 애플리케이션 풀 계정 및 문 경로의 이름을 바꾸어 다음 PowerShell cmdlet을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-144">Update the following PowerShell cmdlet by replacing the name of the report server database, application pool account, and the path of the statement.</span></span>

     <span data-ttu-id="fef14-145">**cmdlet 구문:** `Get-SPRSDatabaseRightsScript -DatabaseName <ReportingServices database name> -UserName <app pool account> -IsWindowsUser | Out-File <path of statement>`</span><span class="sxs-lookup"><span data-stu-id="fef14-145">**Syntax of cmdlet:** `Get-SPRSDatabaseRightsScript -DatabaseName <ReportingServices database name> -UserName <app pool account> -IsWindowsUser | Out-File <path of statement>`</span></span>

     <span data-ttu-id="fef14-146">**샘플 cmdlet:** `Get-SPRSDatabaseRightsScript -DatabaseName ReportingService_46fd00359f894b828907b254e3f6257c -UserName "NT AUTHORITY\NETWORK SERVICE" -IsWindowsUser | Out-File c:\SQLServerAgentrights.sql`</span><span class="sxs-lookup"><span data-stu-id="fef14-146">**Sample cmdlet:** `Get-SPRSDatabaseRightsScript -DatabaseName ReportingService_46fd00359f894b828907b254e3f6257c -UserName "NT AUTHORITY\NETWORK SERVICE" -IsWindowsUser | Out-File c:\SQLServerAgentrights.sql`</span></span>

## <a name="using-the-transact-sql-script"></a><span data-ttu-id="fef14-147">Transact-SQL 스크립트 사용</span><span class="sxs-lookup"><span data-stu-id="fef14-147">Using the Transact-SQL Script</span></span>
 <span data-ttu-id="fef14-148">프로비전 페이지의 스크립트 다운로드 또는 PowerShell을 사용하여 만든 스크립트를 사용하는 경우 다음 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-148">The following procedures can be used with scripts download from the provisions page or scripts created using PowerShell.</span></span>

#### <a name="to-load-the-transact-sql-script-in-sql-server-management-studio"></a><span data-ttu-id="fef14-149">SQL Server Management Studio에서 Transact-SQL 스크립트를 로드하려면</span><span class="sxs-lookup"><span data-stu-id="fef14-149">To load the Transact-SQL script in SQL Server Management Studio</span></span>

1.  <span data-ttu-id="fef14-150">SQL Server Management Studio를 열려면 **시작** 메뉴에서 **Microsoft SQL Server 2012** 를 클릭하고 **Microsoft SQL Server Management Studio**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-150">To open SQL Server Management Studio, on the **Start** menu, click **Microsoft SQL Server 2012** and click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="fef14-151">**서버에 연결** 대화 상자에서 다음 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-151">In the **Connect to Server** dialog box set the following options:</span></span>

    -   <span data-ttu-id="fef14-152">**서버 유형** 목록에서 **데이터베이스 엔진**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-152">In the **Server type** list, select **Database Engine**</span></span>

    -   <span data-ttu-id="fef14-153">**서버 이름**에서 SQL Server 에이전트를 구성하려는 SQL Server 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-153">In **Server Name**, type the name of the SQL Server instance on which you want to configure SQL Server Agent.</span></span>

    -   <span data-ttu-id="fef14-154">인증 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-154">Select an authentication mode.</span></span>

    -   <span data-ttu-id="fef14-155">SQL Server 인증을 사용하여 연결하는 경우 로그인과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-155">If connecting using SQL Server Authentication, provide a login and password.</span></span>

3.  <span data-ttu-id="fef14-156">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-156">Click **Connect**.</span></span>

#### <a name="to-run-the-transact-sql-statement"></a><span data-ttu-id="fef14-157">Transact-SQL 문을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="fef14-157">To run the Transact-SQL statement</span></span>

1.  <span data-ttu-id="fef14-158">SQL Server Management Studio의 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-158">On the toolbar of SQL Server Management Studio, click **New Query**.</span></span>

2.  <span data-ttu-id="fef14-159">**파일** 메뉴에서 **열기**를 클릭한 다음 **파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-159">On the **File** menu, click **Open**, and then click **File**.</span></span>

3.  <span data-ttu-id="fef14-160">SharePoint 2010 관리 셸에서 생성한 Transact-SQL 문을 저장한 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-160">Navigate to the folder where you saved the Transact-SQL statement that you generated in SharePoint 2010 Management Shell.</span></span>

4.  <span data-ttu-id="fef14-161">파일을 클릭한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-161">Click the file and then click **Open**.</span></span>

     <span data-ttu-id="fef14-162">문은 쿼리 창에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-162">The statement is added to the query window.</span></span>

5.  <span data-ttu-id="fef14-163">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fef14-163">Click **Execute**.</span></span>


