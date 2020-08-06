---
title: 명령 프롬프트에서 PowerPivot 설치 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7f1f2b28-c9f5-49ad-934b-02f2fa6b9328
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 54f30142cdc2e39b3ec565d4f965fdad675405e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660292"
---
# <a name="install-powerpivot-from-the-command-prompt"></a><span data-ttu-id="13b75-102">명령 프롬프트에서 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="13b75-102">Install PowerPivot from the Command Prompt</span></span>
  <span data-ttu-id="13b75-103">명령줄에서 설치 프로그램을 실행하여 SQL Server SharePoint용 PowerPivot를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-103">You can run Setup from the command line to install SQL Server PowerPivot for SharePoint.</span></span> <span data-ttu-id="13b75-104">명령에 `/ROLE` 매개 변수를 포함하고 `/FEATURES` 매개 변수는 제외해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-104">You must include the `/ROLE` parameter in your command and exclude the `/FEATURES` parameter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="13b75-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="13b75-105">Prerequisites</span></span>  
 <span data-ttu-id="13b75-106">SharePoint Server 2010 Enterprise Edition SP1(서비스 팩 1)이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-106">SharePoint Server 2010 enterprise edition with Service Pack 1 (SP1) must be installed.</span></span>  
  
 <span data-ttu-id="13b75-107">Analysis Services를 프로비전하기 위해 도메인 계정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-107">You must use domain accounts to provision Analysis Services.</span></span>  
  
 <span data-ttu-id="13b75-108">컴퓨터가 SharePoint 팜과 동일한 도메인에 가입되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-108">The computer must be joined to the same domain as the SharePoint farm.</span></span>  
  
##  <a name="role-based-installation-options"></a><a name="Commands"></a><span data-ttu-id="13b75-109">/ROLE 기반 설치 옵션</span><span class="sxs-lookup"><span data-stu-id="13b75-109">/ROLE based installation options</span></span>  
 <span data-ttu-id="13b75-110">SharePoint용 PowerPivot 배포의 경우 `/ROLE` 매개 변수가 `/FEATURES` 매개 변수를 대신하여 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-110">For PowerPivot for SharePoint deployments, the `/ROLE` parameter is used in place of the `/FEATURES` parameter.</span></span> <span data-ttu-id="13b75-111">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-111">Valid values include:</span></span>  
  
-   `SPI_AS_ExistingFarm`  
  
-   `SPI_AS_NewFarm`  
  
 <span data-ttu-id="13b75-112">이 두 역할은 모두 SharePoint용 PowerPivot이 SharePoint 팜에서 실행될 수 있도록 하는 애플리케이션, 구성 및 배포 파일을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-112">Both roles install application, configuration, and deployment files that enable a PowerPivot for SharePoint to run in a SharePoint farm.</span></span> <span data-ttu-id="13b75-113">두 역할 중 하나를 지정하면 설치 프로그램이 SharePoint 통합에 필요한 하드웨어 및 소프트웨어 요구 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-113">Specifying either role will cause Setup to check for hardware and software requirements necessary for SharePoint integration.</span></span>  
  
 <span data-ttu-id="13b75-114">기존 팜 옵션은 SharePoint 팜이 이미 설치되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-114">The existing farm option assumes that a SharePoint farm is already in place.</span></span> <span data-ttu-id="13b75-115">새 팜 옵션은 새 팜을 만든다고 가정 합니다. 이는 데이터베이스 엔진 인스턴스를 팜의 데이터베이스 서버로 사용할 수 있도록 명령줄 구문에 데이터베이스 엔진 인스턴스를 추가할 수 있도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-115">The new farm option assumes that you will create a new farm; it supports the addition of a Database Engine instance in the command line syntax so that you can use the Database Engine instance as the farm's database server.</span></span>  
  
 <span data-ttu-id="13b75-116">이전 릴리스와 달리 모든 서버 구성 태스크는 설치 후 태스크로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-116">In contrast with the previous releases, all server configuration tasks are performed as post-installation tasks.</span></span> <span data-ttu-id="13b75-117">설치 및 구성 단계를 자동화하는 경우 PowerShell을 사용하여 서버를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-117">If you are automating installation and configuration steps, you can use PowerShell to configure the server.</span></span> <span data-ttu-id="13b75-118">자세한 내용은 [Windows PowerShell을 사용한 PowerPivot 구성](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="13b75-118">For more information, see [PowerPivot Configuration using Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell).</span></span>  
  
## <a name="example-commands"></a><span data-ttu-id="13b75-119">예제 명령</span><span class="sxs-lookup"><span data-stu-id="13b75-119">Example Commands</span></span>  
 <span data-ttu-id="13b75-120">다음 예제는 각 옵션의 사용법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-120">The following examples illustrate the usage of each option.</span></span> <span data-ttu-id="13b75-121">예제 1은 `SPI_AS_ExistingFarm` 을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-121">Example 1 shows `SPI_AS_ExistingFarm`.</span></span>  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 <span data-ttu-id="13b75-122">예제 2는 `SPI_AS_NewFarm`을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-122">Example 2 shows `SPI_AS_NewFarm`.</span></span> <span data-ttu-id="13b75-123">데이터베이스 엔진을 프로비전하기 위한 매개 변수가 포함되어 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-123">Notice that it includes parameters for provisioning the Database Engine.</span></span>  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_NewFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/SQLSVCACCOUNT=<DomainName\UserName> /SQLSVCPASSWORD=<StrongPassword> /SQLSYSADMINACCOUNTS=<DomainName\UserName> /AGTSVCACCOUNT=<DomainName\UserName> /AGTSVCPASSWORD=<StrongPassword> /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
##  <a name="modifying-the-command-syntax"></a><a name="Join"></a><span data-ttu-id="13b75-124">명령 구문 수정</span><span class="sxs-lookup"><span data-stu-id="13b75-124">Modifying the command syntax</span></span>  
 <span data-ttu-id="13b75-125">다음 단계를 사용하여 예제 명령 구문을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-125">Use the following steps to modify the example command syntax.</span></span>  
  
1.  <span data-ttu-id="13b75-126">다음 명령을 메모장에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-126">Copy the following command into Notepad:</span></span>  
  
    ```cmd
    Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
    ```  
  
     <span data-ttu-id="13b75-127">`/q` 매개 변수가 설치 프로그램을 자동 모드에서 실행하며 사용자 인터페이스를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-127">The `/q` parameter runs Setup in quiet mode, which suppresses the user interface.</span></span>  
  
     <span data-ttu-id="13b75-128">`/IAcceptSQLServerLicenseTerms`는 무인 설치에 대해 `/q` 또는 `/qs` 매개 변수를 지정하는 경우 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-128">The `/IAcceptSQLServerLicenseTerms` is required when the `/q` or `/qs` parameter is specified for un-attended installations.</span></span>  
  
     <span data-ttu-id="13b75-129">`/action` 매개 변수는 설치를 수행하도록 설치 프로그램에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-129">The `/action` parameter instructs Setup to perform an installation.</span></span>  
  
     <span data-ttu-id="13b75-130">`/role` 매개 변수를 지정하면 SharePoint용 PowerPivot에 필요한 Analysis Services 프로그램 및 구성 파일이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-130">The `/role` parameter instructs Setup to install the Analysis Services program and configuration files required for PowerPivot for SharePoint.</span></span> <span data-ttu-id="13b75-131">이 역할 역시 기존 팜 연결 정보를 검색 및 사용하여 SharePoint 구성 데이터베이스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-131">This role also detects and uses the existing farm connectivity information to access the SharePoint configuration database.</span></span> <span data-ttu-id="13b75-132">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-132">This parameter is required.</span></span> <span data-ttu-id="13b75-133">설치할 구성 요소를 지정하려면 `/features` 매개 변수 대신 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-133">Use it instead of the `/features` parameter to specify the components to install.</span></span>  
  
     <span data-ttu-id="13b75-134">`/instancename` 매개 변수는 명명된 인스턴스로 'PowerPivot'을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-134">The `/instancename` parameter specifies 'PowerPivot' as a named instance.</span></span> <span data-ttu-id="13b75-135">이 값은 하드 코딩되어 변경할 수 없으며,</span><span class="sxs-lookup"><span data-stu-id="13b75-135">This value is hard-coded and cannot be changed.</span></span> <span data-ttu-id="13b75-136">교육용으로 명령에 지정되므로 서비스 설치 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-136">It is specified in the command for educational purposes so that you know how the service is installed.</span></span>  
  
     <span data-ttu-id="13b75-137">`/indicateprogress` 매개 변수를 사용하면 명령 프롬프트 창에서 진행률을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-137">The `/indicateprogress` parameter allows you to monitor progress in the command prompt window.</span></span>  
  
2.  <span data-ttu-id="13b75-138">`PID` 매개 변수는 명령에서 생략되므로 Evaluation 버전이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-138">The `PID` parameter is omitted from the command, which causes the Evaluation edition to be installed.</span></span> <span data-ttu-id="13b75-139">Enterprise 버전을 설치하려면 설치 명령에 PID를 추가하고 올바른 제품 키를 제공하십시오.</span><span class="sxs-lookup"><span data-stu-id="13b75-139">If you want to install the Enterprise edition, add the PID to your Setup command and provide a valid product key.</span></span>  
  
    ```  
    /PID=<product key for an Enterprise installation>  
    ```  
  
3.  <span data-ttu-id="13b75-140">및에 대 한 자리 표시자를 \<domain\username> \<StrongPassword> 유효한 사용자 계정 및 암호로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-140">Replace the placeholders for \<domain\username> and \<StrongPassword>with valid user accounts and passwords.</span></span>  
  
     <span data-ttu-id="13b75-141">`/assvaccount`및 **/assvcpassword** 매개 변수는 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 응용 프로그램 서버에서 인스턴스를 구성 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-141">The `/assvaccount` and **/assvcpassword** parameters are used to configure the [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance on the application server.</span></span> <span data-ttu-id="13b75-142">이들 자리 표시자는 올바른 계정 정보로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-142">Replace these placeholders with valid account information.</span></span>  
  
     <span data-ttu-id="13b75-143">**/Assysadminaccounts** 매개 변수는 SQL Server 설치 프로그램을 실행 하는 사용자의 id로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-143">The **/assysadminaccounts** parameter must be set to the identity of the user who is running SQL Server Setup.</span></span> <span data-ttu-id="13b75-144">시스템 관리자는 한 명 이상 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-144">You must specify at least one system administrator.</span></span> <span data-ttu-id="13b75-145">SQL Server 설치 프로그램은 기본 제공 관리자 그룹 멤버에 대해 자동 sysadmin 권한을 더 이상 부여하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-145">Note that SQL Server Setup no long grants automatic sysadmin permissions to members of the built-in Administrators group.</span></span>  
  
4.  <span data-ttu-id="13b75-146">줄 바꿈을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-146">Remove line breaks.</span></span>  
  
5.  <span data-ttu-id="13b75-147">전체 명령을 선택한 다음 편집 메뉴에서 **복사** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-147">Select the entire command and then click **Copy** on the Edit menu.</span></span>  
  
6.  <span data-ttu-id="13b75-148">관리자 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-148">Open an administrator command prompt.</span></span> <span data-ttu-id="13b75-149">이렇게 하려면 **시작**을 클릭 하 고 명령 프롬프트를 마우스 오른쪽 단추로 클릭 한 다음 **관리자 권한으로 실행**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-149">To do this, click **Start**, right-click the command prompt, and select **Run as administrator**.</span></span>  
  
7.  <span data-ttu-id="13b75-150">SQL Server 설치 미디어가 포함된 드라이브 또는 공유 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-150">Navigate to the drive or shared folder that contains the SQL Server installation media.</span></span>  
  
8.  <span data-ttu-id="13b75-151">수정한 명령을 명령줄에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-151">Paste the revised command into the command line.</span></span> <span data-ttu-id="13b75-152">이렇게 하려면 명령 프롬프트 창의 왼쪽 위 모서리에 있는 아이콘을 클릭 하 고 **편집**을 가리킨 다음 **붙여넣기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-152">To do this, click the icon in the top left corner of the command prompt window, point to **Edit**, and then click **Paste**.</span></span>  
  
9. <span data-ttu-id="13b75-153">**Enter** 키를 눌러 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-153">Press **Enter** to run the command.</span></span> <span data-ttu-id="13b75-154">설치가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-154">Wait for setup to complete.</span></span> <span data-ttu-id="13b75-155">명령 프롬프트 창에서 설치 진행률을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-155">You can monitor Setup's progress in the command prompt window.</span></span>  
  
10. <span data-ttu-id="13b75-156">설치를 확인하려면 \Program Files\SQL Server\120\Setup Bootstrap\Log의 summary.txt 파일을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="13b75-156">To verify installation, check the summary.txt file at \Program Files\SQL Server\120\Setup Bootstrap\Log.</span></span> <span data-ttu-id="13b75-157">서버가 오류 없이 설치된 경우 최종 결과는 "통과"여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-157">Final result should say "Passed" if the server installed without errors.</span></span>  
  
11. <span data-ttu-id="13b75-158">서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-158">Configure the server.</span></span> <span data-ttu-id="13b75-159">최소한 솔루션을 배포하고 서비스 애플리케이션을 만들고 각 사이트 모음에 대해 기능을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13b75-159">At a minimum, you must deploy solutions, create a service application, and enable the feature for each site collection.</span></span> <span data-ttu-id="13b75-160">자세한 내용은 [Configure Or Repair SharePoint용 PowerPivot 2010 &#40;Powerpivot 구성 도구&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md) 또는 [중앙 관리에서 powerpivot 서버 관리 및 구성](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="13b75-160">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md) or [PowerPivot Server Administration and Configuration in Central Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13b75-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13b75-161">See Also</span></span>  
 <span data-ttu-id="13b75-162">[PowerPivot 서비스 계정 구성](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts) </span><span class="sxs-lookup"><span data-stu-id="13b75-162">[Configure PowerPivot Service Accounts](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts) </span></span>  
 [<span data-ttu-id="13b75-163">SharePoint 2010용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="13b75-163">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
