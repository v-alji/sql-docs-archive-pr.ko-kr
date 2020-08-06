---
title: SharePoint에 PowerPivot 솔루션 배포 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f202a2b7-34e0-43aa-90d5-c9a085a37c32
author: minewiskan
ms.author: owend
ms.openlocfilehash: 043647988598f932b70cc06e6bb5492d66864372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653009"
---
# <a name="deploy-powerpivot-solutions-to-sharepoint"></a><span data-ttu-id="46a27-102">SharePoint에 PowerPivot 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="46a27-102">Deploy PowerPivot Solutions to SharePoint</span></span>
  <span data-ttu-id="46a27-103">다음 지침을 사용하여 SharePoint Server 2010 환경에 PowerPivot 기능을 추가하는 두 개의 솔루션 패키지를 수동으로 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-103">Use the following instructions to manually deploy two solution packages that add PowerPivot features to a SharePoint Server 2010 environment.</span></span> <span data-ttu-id="46a27-104">솔루션 배포는 SharePoint 2010 서버에서 SharePoint용 PowerPivot을 구성하기 위한 필수 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-104">Deploying the solutions is a required step for configuring PowerPivot for SharePoint on a SharePoint 2010 server.</span></span> <span data-ttu-id="46a27-105">필수 단계의 전체 목록을 보려면 [중앙 관리의 PowerPivot 서버 관리 및 구성](power-pivot-server-administration-and-configuration-in-central-administration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46a27-105">To view the complete list of required steps, see [PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md).</span></span>  
  
 <span data-ttu-id="46a27-106">또는 PowerPivot 구성 도구를 사용하여 솔루션을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-106">Alternatively, you can use the PowerPivot Configuration Tool to deploy the solutions.</span></span> <span data-ttu-id="46a27-107">구성 도구를 사용하는 방법은 단일 서버 설치의 경우 더 쉽고 효율적인 방법이지만 친숙한 도구를 사용하고 싶거나 동시에 여러 기능을 구성하려는 경우 중앙 관리 및 Powershell을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-107">Using the configuration tool is easier and more efficient for a single server installation, but you might want to use Central Administration and PowerShell if you prefer using a familiar tool or if you are configuring multiple features at the same time.</span></span> <span data-ttu-id="46a27-108">구성 도구를 사용 하는 방법에 대 한 자세한 내용은 [PowerPivot 구성 도구](power-pivot-configuration-tools.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46a27-108">For more information about using the configuration tool, see [PowerPivot Configuration Tools](power-pivot-configuration-tools.md).</span></span>  
  
 <span data-ttu-id="46a27-109">솔루션을 배포하기 전에 먼저 SQL Server 2012 설치 미디어를 사용하여 SharePoint용 PowerPivot을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-109">Before deploying the solutions, you must first install PowerPivot for SharePoint using the SQL Server 2012 installation media.</span></span> <span data-ttu-id="46a27-110">SQL Server 설치 프로그램은 배포할 솔루션 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-110">SQL Server Setup installs the solution packages that you are about to deploy.</span></span>  
  
 <span data-ttu-id="46a27-111">이 항목에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-111">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="46a27-112">필수 구성 요소: 웹 응용 프로그램에서 클래식 모드 인증을 사용 하는지 확인</span><span class="sxs-lookup"><span data-stu-id="46a27-112">Prerequisite: Verify the Web Application uses Classic Mode Authentication</span></span>](#bkmk_classic)  
  
 [<span data-ttu-id="46a27-113">1단계: 팜 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="46a27-113">Step 1: Deploy the Farm Solution</span></span>](#bkmk_farm)  
  
 [<span data-ttu-id="46a27-114">2 단계: 중앙 관리에 PowerPivot 웹 응용 프로그램 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="46a27-114">Step 2: Deploy the PowerPivot Web Application Solution to Central Administration</span></span>](#deployCA)  
  
 [<span data-ttu-id="46a27-115">3 단계: 다른 웹 응용 프로그램에 PowerPivot 웹 응용 프로그램 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="46a27-115">Step 3: Deploy the PowerPivot Web Application Solution to Other Web Applications</span></span>](#deployUI)  
  
 [<span data-ttu-id="46a27-116">솔루션 다시 배포 또는 취소</span><span class="sxs-lookup"><span data-stu-id="46a27-116">Redeploy or retract the Solution</span></span>](#retract)  
  
 [<span data-ttu-id="46a27-117">PowerPivot 솔루션 정보</span><span class="sxs-lookup"><span data-stu-id="46a27-117">About the PowerPivot Solutions</span></span>](#intro)  
  
##  <a name="prerequisite-verify-the-web-application-uses-classic-mode-authentication"></a><a name="bkmk_classic"></a> <span data-ttu-id="46a27-118">사전 요구 사항: 웹 애플리케이션에서 클래식 모드 인증을 사용하는지 확인</span><span class="sxs-lookup"><span data-stu-id="46a27-118">Prerequisite: Verify the Web Application uses Classic Mode Authentication</span></span>  
 <span data-ttu-id="46a27-119">SharePoint용 PowerPivot은 Windows 클래식 모드 인증을 사용하는 웹 애플리케이션에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-119">PowerPivot for SharePoint is only supported for web applications that use Windows-classic mode authentication.</span></span> <span data-ttu-id="46a27-120">응용 프로그램이 클래식 모드를 사용 하는지 확인 하려면 **sharepoint 2010 관리 셸에서**다음 PowerShell cmdlet을 실행 하 고를 `http://<top-level site name>` sharepoint 사이트의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-120">To check whether the application uses Classic mode, run the following PowerShell cmdlet from the **SharePoint 2010 Management Shell**, replacing `http://<top-level site name>` with the name of your SharePoint site:</span></span>  
  
```powershell
Get-SPWebApplication http://<top-level site name> | Format-List UseClaimsAuthentication  
```  
  
 <span data-ttu-id="46a27-121">반환 값은 **false**여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-121">The return value should be **false**.</span></span> <span data-ttu-id="46a27-122">**True**이면이 웹 응용 프로그램을 사용 하 여 PowerPivot 데이터에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-122">If it is **true**, you cannot access PowerPivot data with this web application.</span></span>  
  
##  <a name="step-1-deploy-the-farm-solution"></a><a name="bkmk_farm"></a><span data-ttu-id="46a27-123">1 단계: 팜 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="46a27-123">Step 1: Deploy the Farm Solution</span></span>  
 <span data-ttu-id="46a27-124">이 섹션에서는 PowerShell을 사용하여 솔루션을 배포하는 방법을 보여 주지만 PowerPivot 구성 도구를 사용하여 이 태스크를 완료할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-124">This section shows you how to deploy solutions using PowerShell, but you can also use the PowerPivot Configuration Tool to complete this task.</span></span> <span data-ttu-id="46a27-125">자세한 내용은 [SharePoint용 PowerPivot 2010 &#40;PowerPivot 구성 도구&#41;구성 또는 복구 ](../configure-repair-powerpivot-sharepoint-2010.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46a27-125">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../configure-repair-powerpivot-sharepoint-2010.md).</span></span>  
  
 <span data-ttu-id="46a27-126">이 태스크는 SharePoint용 PowerPivot을 설치한 후 한 번만 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-126">This task only needs to be performed once, after you install PowerPivot for SharePoint.</span></span>  
  
1.  <span data-ttu-id="46a27-127">SharePoint용 PowerPivot가 설치 된 서버에서 **관리자 권한으로 실행** 옵션을 사용 하 여 SharePoint 2010 관리 셸을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-127">On a server that has an installation of PowerPivot for SharePoint, open a SharePoint 2010 Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="46a27-128">다음 cmdlet을 실행하여 팜 솔루션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-128">Run the following cmdlet to add the farm solution.</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     <span data-ttu-id="46a27-129">이 cmdlet을 실행하면 솔루션의 이름,  솔루션 ID  및 Deployed=False가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-129">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="46a27-130">다음 단계에서는 솔루션을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-130">In the next step, you will deploy the solution.</span></span>  
  
3.  <span data-ttu-id="46a27-131">다음 cmdlet을 실행하여 팜 솔루션을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-131">Run the next cmdlet to deploy the farm solution:</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
##  <a name="step-2-deploy-the-powerpivot-web-application-solution-to-central-administration"></a><a name="deployCA"></a><span data-ttu-id="46a27-132">2 단계: 중앙 관리에 PowerPivot 웹 응용 프로그램 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="46a27-132">Step 2: Deploy the PowerPivot Web Application Solution to Central Administration</span></span>  
 <span data-ttu-id="46a27-133">팜 솔루션을 배포한 후 중앙 관리에 웹 애플리케이션 솔루션을 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-133">After you deploy the farm solution, you must deploy the Web application solution to Central Administration.</span></span> <span data-ttu-id="46a27-134">이 단계에서는 중앙 관리에 PowerPivot 관리 대시보드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-134">This step adds the PowerPivot Management Dashboard to Central Administration.</span></span>  
  
1.  <span data-ttu-id="46a27-135">**관리자 권한으로 실행** 옵션을 사용하여 SharePoint  2010  관리 셸을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-135">Open a SharePoint 2010 Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="46a27-136">다음 cmdlet을 실행하여 중앙 관리에 대한 참조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-136">Run the following cmdlet to create a reference to Central Administration:</span></span>  
  
    ```powershell
    $centralAdmin = $(Get-SPWebApplication -IncludeCentralAdministration | Where { $_.IsAdministrationWebApplication -eq $TRUE})  
    ```  
  
3.  <span data-ttu-id="46a27-137">다음 cmdlet을 실행하여 팜 솔루션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-137">Run the following cmdlet to add the farm solution.</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotWebApp.wsp"  
    ```  
  
     <span data-ttu-id="46a27-138">이 cmdlet을 실행하면 솔루션의 이름,  솔루션 ID  및 Deployed=False가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-138">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="46a27-139">다음 단계에서는 솔루션을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-139">In the next step, you will deploy the solution.</span></span>  
  
4.  <span data-ttu-id="46a27-140">다음 cmdlet을 실행하여 중앙 관리에 웹 애플리케이션 솔루션을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-140">Run the next cmdlet to install the web application solution to Central Administration.</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotWebApp.wsp -GACDeployment -Force -WebApplication $centralAdmin  
    ```  
  
 <span data-ttu-id="46a27-141">이제 중앙 관리에 웹 애플리케이션 솔루션이 배포되었으므로 중앙 관리를 사용하여 모든 나머지 구성 단계를 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-141">Now that the web application solution is deployed to Central Administration, you can use Central Administration to complete all remaining configuration steps.</span></span>  
  
##  <a name="step-3-deploy-the-powerpivot-web-application-solution-to-other-web-applications"></a><a name="deployUI"></a><span data-ttu-id="46a27-142">3 단계: 다른 웹 응용 프로그램에 PowerPivot 웹 응용 프로그램 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="46a27-142">Step 3: Deploy the PowerPivot Web Application Solution to Other Web Applications</span></span>  
 <span data-ttu-id="46a27-143">앞에서는 Powerpivotwebapp.wsp를 중앙 관리로 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-143">In the previous task, you deployed Powerpivotwebapp.wsp to Central Administration.</span></span> <span data-ttu-id="46a27-144">이 섹션에서는 PowerPivot 데이터 액세스를 지원하는 각각의 기존 웹 애플리케이션에 powerpivotwebapp.wsp를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-144">In this section, you deploy the powerpivotwebapp.wsp on each existing web application that supports PowerPivot data access.</span></span> <span data-ttu-id="46a27-145">나중에 웹 애플리케이션을 더 많이 추가하는 경우 추가 웹 애플리케이션에 대해 이 단계를 반복해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-145">If you add more web applications later, be sure to repeat this step for those additional web applications.</span></span>  
  
1.  <span data-ttu-id="46a27-146">중앙 관리의 시스템 설정에서 **팜 솔루션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-146">In Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="46a27-147">**Powerpivotwebapp.wsp**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-147">Click **powerpivotwebapp.wsp**.</span></span>  
  
3.  <span data-ttu-id="46a27-148">**솔루션 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-148">Click **Deploy Solution**.</span></span>  
  
4.  <span data-ttu-id="46a27-149">**배포 대상**에서 PowerPivot 기능 지원을 추가할 SharePoint 웹 응용 프로그램을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-149">In **Deploy To?**, select the SharePoint web application for which you want to add PowerPivot feature support.</span></span>  
  
5.  <span data-ttu-id="46a27-150">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="46a27-151">PowerPivot 데이터 액세스를 지원할 다른 SharePoint 웹 애플리케이션에 대해서도 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-151">Repeat for other SharePoint web applications that will also support PowerPivot data access.</span></span>  
  
##  <a name="redeploy-or-retract-the-solution"></a><a name="retract"></a><span data-ttu-id="46a27-152">솔루션 다시 배포 또는 취소</span><span class="sxs-lookup"><span data-stu-id="46a27-152">Redeploy or retract the Solution</span></span>  
 <span data-ttu-id="46a27-153">SharePoint 중앙 관리에서 솔루션 취소 기능을 제공하기는 하지만 설치 또는 패치 배포 문제를 체계적으로 해결하는 경우가 아니면 powerpivotwebapp.wsp 파일을 취소할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-153">Although SharePoint Central Administration provides solution retraction, you do not need to retract the powerpivotwebapp.wsp file unless you are systematically troubleshooting an installation or patch deployment problem.</span></span>  
  
1.  <span data-ttu-id="46a27-154">SharePoint  2010  중앙 관리의 시스템 설정에서 **팜 솔루션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-154">In SharePoint 2010 Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="46a27-155">**Powerpivotwebapp.wsp**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-155">Click **Powerpivotwebapp.wsp**.</span></span>  
  
3.  <span data-ttu-id="46a27-156">**솔루션 취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-156">Click **Retract Solution**.</span></span>  
  
 <span data-ttu-id="46a27-157">팜 솔루션을 다시 추적 하는 서버 배포 문제가 발생 하는 경우 PowerPivot 구성 도구에서 **복구** 옵션을 실행 하 여 다시 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-157">If you encounter server deployment issues that you trace back to the farm solution, you can redeploy it by running the **Repair** option in the PowerPivot Configuration Tool.</span></span> <span data-ttu-id="46a27-158">사용자가 수행할 단계가 더 적으므로 도구를 통해 복구 작업을 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-158">Repair operations via the tool is preferred because it requires fewer steps on your part.</span></span> <span data-ttu-id="46a27-159">자세한 내용은 [SharePoint용 PowerPivot 2010 &#40;PowerPivot 구성 도구&#41;구성 또는 복구 ](../configure-repair-powerpivot-sharepoint-2010.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46a27-159">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../configure-repair-powerpivot-sharepoint-2010.md).</span></span>  
  
 <span data-ttu-id="46a27-160">모든 솔루션을 다시 배포하려는 경우에는 다음 순서로 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-160">If you still want to re-deploy all solutions, be sure to do so in this order:</span></span>  
  
1.  <span data-ttu-id="46a27-161">PowerPivot 웹 애플리케이션 솔루션을 사용하는 모든 SharePoint 웹 애플리케이션에서 PowerPivot 웹 애플리케이션 솔루션을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-161">Retract the PowerPivot Web application solution from all SharePoint web applications that use it.</span></span>  
  
2.  <span data-ttu-id="46a27-162">PowerPivot 팜 솔루션을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-162">Retract the PowerPivot farm solution.</span></span>  
  
3.  <span data-ttu-id="46a27-163">PowerPivot 팜 솔루션을 다시 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-163">Redeploy the PowerPivot farm solution.</span></span>  
  
4.  <span data-ttu-id="46a27-164">모든 SharePoint 웹 애플리케이션에 PowerPivot 웹 애플리케이션 솔루션을 다시 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-164">Redeploy the PowerPivot Web application solution to all SharePoint web applications.</span></span>  
  
##  <a name="about-the-powerpivot-solutions"></a><a name="intro"></a><span data-ttu-id="46a27-165">PowerPivot 솔루션 정보</span><span class="sxs-lookup"><span data-stu-id="46a27-165">About the PowerPivot Solutions</span></span>  
 <span data-ttu-id="46a27-166">SharePoint용 PowerPivot에서는 두 가지 솔루션 패키지를 사용하여 해당 애플리케이션 페이지 및 프로그램 파일을 팜과 개별 웹 애플리케이션에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-166">PowerPivot for SharePoint uses two solution packages to deploy its application pages and program files to the farm and to individual web applications.</span></span>  
  
-   <span data-ttu-id="46a27-167">팜 솔루션은 전역적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-167">The farm solution is global.</span></span> <span data-ttu-id="46a27-168">이 솔루션은 한 번 배포되고 나면 나중에 팜에 추가하는 모든 새 SharePoint용 PowerPivot 서버에서 자동으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-168">It is deployed once and then becomes automatically available to any new PowerPivot for SharePoint servers that you add to the farm later.</span></span>  
  
-   <span data-ttu-id="46a27-169">웹 애플리케이션 솔루션은 애플리케이션별로 적용되므로 중앙 관리 웹 애플리케이션을 비롯한 팜의 각 웹 애플리케이션에 배포되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-169">The web application solution is application-specific and must be deployed to each web application in the farm, including the Central Administration web application.</span></span>  
  
 <span data-ttu-id="46a27-170">각 솔루션은 다른 방식으로 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-170">Each solution is deployed differently.</span></span>  <span data-ttu-id="46a27-171">팜 솔루션은 첫 번째 SharePoint용 PowerPivot 인스턴스가 설치된 후 한 번 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-171">The farm solution is deployed once, after the first PowerPivot for SharePoint instance is installed.</span></span> <span data-ttu-id="46a27-172">팜 솔루션을 배포하려면 PowerPivot 구성 도구 또는 PowerShell cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-172">To deploy the farm solution, you use the PowerPivot Configuration Tool or PowerShell cmdlets.</span></span>  
  
 <span data-ttu-id="46a27-173">웹 애플리케이션 솔루션은 처음 중앙 관리에 배포된 다음 PowerPivot 데이터에 대한 요청을 지원하는 모든 추가 웹 애플리케이션에 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-173">The web application solution is initially deployed to Central Administration, followed by subsequent solution deployments to any additional web applications that will support requests for PowerPivot data.</span></span> <span data-ttu-id="46a27-174">중앙 관리에 웹 애플리케이션 솔루션을 배포하려면 PowerPivot 구성 도구 또는 PowerShell cmdlet을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-174">To deploy the web application solution to Central Administration, you must use the PowerPivot Configuration Tool or PowerShell cmdlet.</span></span> <span data-ttu-id="46a27-175">다른 모든 웹 애플리케이션의 경우 중앙 관리 또는 PowerShell을 사용하여 수동으로 웹 애플리케이션 솔루션을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-175">For all other web applications, you can deploy the web application solution manually using Central Administration or PowerShell.</span></span>  
  
|<span data-ttu-id="46a27-176">해결 방법</span><span class="sxs-lookup"><span data-stu-id="46a27-176">Solution</span></span>|<span data-ttu-id="46a27-177">Description</span><span class="sxs-lookup"><span data-stu-id="46a27-177">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="46a27-178">Powerpivotfarm.wsp</span><span class="sxs-lookup"><span data-stu-id="46a27-178">Powerpivotfarm.wsp</span></span>|<span data-ttu-id="46a27-179">Microsoft.AnalysisServices.SharePoint.Integration.dll을 전역 어셈블리에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-179">Adds Microsoft.AnalysisServices.SharePoint.Integration.dll to the global assembly.</span></span><br /><br /> <span data-ttu-id="46a27-180">Microsoft.AnalysisServices.ChannelTransport.dll을 전역 어셈블리에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-180">Adds Microsoft.AnalysisServices.ChannelTransport.dll to the global assembly.</span></span><br /><br /> <span data-ttu-id="46a27-181">기능 및 리소스 파일을 설치하고 내용 유형을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-181">Installs features and resources files, and registers content types.</span></span><br /><br /> <span data-ttu-id="46a27-182">PowerPivot 갤러리 및 데이터 피드 라이브러리용 라이브러리 템플릿을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-182">Adds library templates for PowerPivot Gallery and Data Feed libraries.</span></span><br /><br /> <span data-ttu-id="46a27-183">서비스 애플리케이션 구성, PowerPivot 관리 대시보드, 데이터 새로 고침, PowerPivot 갤러리를 위한 애플리케이션 페이지를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-183">Adds application pages for service application configuration, PowerPivot Management Dashboard, data refresh, and PowerPivot Gallery.</span></span>|  
|<span data-ttu-id="46a27-184">powerpivotwebapp.wsp</span><span class="sxs-lookup"><span data-stu-id="46a27-184">Powerpivotwebapp.wsp</span></span>|<span data-ttu-id="46a27-185">Microsoft.AnalysisServices.SharePoint.Integration.dll 리소스 파일을 웹 프런트 엔드의 웹 서버 확장 폴더에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-185">Adds Microsoft.AnalysisServices.SharePoint.Integration.dll resources files to the web server extensions folder on the Web front-end.</span></span><br /><br /> <span data-ttu-id="46a27-186">PowerPivot 웹 서비스를 웹 프런트 엔드에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-186">Adds PowerPivot Web service to the Web-front end.</span></span><br /><br /> <span data-ttu-id="46a27-187">PowerPivot 갤러리용 축소판 이미지 생성 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46a27-187">Adds thumbnail image generation for PowerPivot Gallery.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46a27-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46a27-188">See Also</span></span>  
 <span data-ttu-id="46a27-189">[업그레이드 SharePoint용 PowerPivot](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="46a27-189">[Upgrade PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="46a27-190">[중앙 관리에서 PowerPivot 서버 관리 및 구성](power-pivot-server-administration-and-configuration-in-central-administration.md) </span><span class="sxs-lookup"><span data-stu-id="46a27-190">[PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) </span></span>  
 [<span data-ttu-id="46a27-191">Windows PowerShell을 사용하여 PowerPivot 구성</span><span class="sxs-lookup"><span data-stu-id="46a27-191">PowerPivot Configuration using Windows PowerShell</span></span>](power-pivot-configuration-using-windows-powershell.md)  
