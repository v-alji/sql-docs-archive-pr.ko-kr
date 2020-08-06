---
title: PowerPivot 구성 및 솔루션 배포 (SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6401fd92-f43b-450e-8298-12db644c25bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7eaea7f9c490fd320d6dbd0777519eeca218b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729960"
---
# <a name="configure-powerpivot-and-deploy-solutions-sharepoint-2013"></a><span data-ttu-id="0091d-102">Configure PowerPivot and Deploy Solutions (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="0091d-102">Configure PowerPivot and Deploy Solutions (SharePoint 2013)</span></span>
  <span data-ttu-id="0091d-103">이 항목에서는 PowerPivot 갤러리, 데이터 새로 고침 예약, 관리 대시보드 및 데이터 공급자를 포함하여 [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)]의 PowerPivot 기능에 대한 중간 계층 향상 배포 및 구성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-103">This topics describes the deployment and configuration of middle-tier enhancements to the PowerPivot features in [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] including PowerPivot Gallery, Schedule data refresh, Management Dashboard, and data providers.</span></span> <span data-ttu-id="0091d-104">**SharePoint 2013용 PowerPivot 구성** 도구를 실행하여 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-104">Run **PowerPivot for SharePoint 2013 Configuration** tool to complete the following:</span></span>  
  
-   <span data-ttu-id="0091d-105">SharePoint 솔루션 파일 배포</span><span class="sxs-lookup"><span data-stu-id="0091d-105">Deploy SharePoint solution files.</span></span>  
  
-   <span data-ttu-id="0091d-106">PowerPivot 서비스 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="0091d-106">Create a PowerPivot service application.</span></span>  
  
-   <span data-ttu-id="0091d-107">SharePoint 모드에서 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버를 사용하도록 Excel Services 애플리케이션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-107">Configure an Excel Services Application to use an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="0091d-108">백 엔드 서비스 및 SharePoint 모드에서 서버를 설치 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [SharePoint용 PowerPivot 2013 설치](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0091d-108">For information on backend services and installing a [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode, see [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>  
  
 <span data-ttu-id="0091d-109">SharePoint용 PowerPivot 2013 구성 도구를 설치 하는 방법에 대 한 자세한 내용은 [SharePoint 2013 &#40;SharePoint용 PowerPivot 추가 기능 설치 또는 제거](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) 를 참조 하십시오&#41;</span><span class="sxs-lookup"><span data-stu-id="0091d-109">For information on installing the PowerPivot for SharePoint 2013 Configuration tool, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)</span></span>  
  
 <span data-ttu-id="0091d-110">이 항목에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-110">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="0091d-111">SharePoint 2013용 PowerPivot 구성 실행</span><span class="sxs-lookup"><span data-stu-id="0091d-111">Run PowerPivot for SharePoint 2013 configuration</span></span>](#bkmk_run_configuration_tool)  
  
 [<span data-ttu-id="0091d-112">PowerPivot 구성 확인</span><span class="sxs-lookup"><span data-stu-id="0091d-112">Verify PowerPivot Configuration</span></span>](#bkmk_verify_powerpivot)  
  
 [<span data-ttu-id="0091d-113">문제 해결</span><span class="sxs-lookup"><span data-stu-id="0091d-113">Troubleshoot Issues</span></span>](#bkmk_troubleshoot_issues)  
  
##  <a name="run-powerpivot-for-sharepoint-2013-configuration"></a><a name="bkmk_run_configuration_tool"></a><span data-ttu-id="0091d-114">SharePoint용 PowerPivot 2013 구성 실행</span><span class="sxs-lookup"><span data-stu-id="0091d-114">Run PowerPivot for SharePoint 2013 configuration</span></span>  
 <span data-ttu-id="0091d-115">**참고:**[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 설치 마법사는 [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)]에 대한 두 가지 구성 도구를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-115">**Note:** The [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] setup wizard installs two different configuration tools for [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)].</span></span> <span data-ttu-id="0091d-116">구성 파일은 각각 SharePoint의 다른 버전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-116">They each support a different version of SharePoint.</span></span>  
  
|<span data-ttu-id="0091d-117">Name</span><span class="sxs-lookup"><span data-stu-id="0091d-117">Name</span></span>|<span data-ttu-id="0091d-118">Description</span><span class="sxs-lookup"><span data-stu-id="0091d-118">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="0091d-119">SharePoint 2013용 PowerPivot 구성</span><span class="sxs-lookup"><span data-stu-id="0091d-119">PowerPivot for SharePoint 2013 Configuration</span></span>|<span data-ttu-id="0091d-120">SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="0091d-120">SharePoint 2013</span></span>|  
|<span data-ttu-id="0091d-121">PowerPivot 구성 도구</span><span class="sxs-lookup"><span data-stu-id="0091d-121">PowerPivot Configuration Tool</span></span>|<span data-ttu-id="0091d-122">SharePoint 2010 SP1(서비스 팩 1)</span><span class="sxs-lookup"><span data-stu-id="0091d-122">SharePoint 2010 with SharePoint 2010 Service Pack 1 (SP1)</span></span>|  
  
 <span data-ttu-id="0091d-123">**참고:** 다음 단계를 완료하려면 팜 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-123">**Note:** To complete the following steps, you must be a farm administrator.</span></span> <span data-ttu-id="0091d-124">다음과 유사한 오류 메시지가 표시되는 경우</span><span class="sxs-lookup"><span data-stu-id="0091d-124">If you see an error message similar to the following:</span></span>  
  
-   <span data-ttu-id="0091d-125">"사용자가 팜 관리자가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-125">"The user is not a farm administrator.</span></span> <span data-ttu-id="0091d-126">유효성 검사 오류를 처리하고 다시 시도하십시오."</span><span class="sxs-lookup"><span data-stu-id="0091d-126">Please address the validation failures and try again."</span></span>  
  
 <span data-ttu-id="0091d-127">SharePoint를 설치한 계정으로 로그인하거나 설치 계정을 SharePoint 중앙 관리 사이트의 주 관리자로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-127">Either login as the account that installed SharePoint or configure the setup account as the primary administrator of the SharePoint Central Administration Site.</span></span>  
  
1.  <span data-ttu-id="0091d-128">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **구성 도구**및 **SharePoint 2013용 PowerPivot 구성**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-128">On the **Start** menu, click **All Programs**, and then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], click **Configuration Tools**, and then click **PowerPivot For SharePoint 2013 Configuration**.</span></span> <span data-ttu-id="0091d-129">도구는 SharePoint용 PowerPivot이 로컬 서버에 설치된 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-129">Toold is listed only when PowerPivot for SharePoint is installed on the local server.</span></span>  
  
2.  <span data-ttu-id="0091d-130">**SharePoint용 PowerPivot 구성 또는 복구** 를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-130">Click **Configure or Repair PowerPivot for SharePoint** and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="0091d-131">도구는 유효성 검사를 실행하여 PowerPivot의 현재 상태와 구성을 완료하는 데 필요한 단계를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-131">The tool runs validation to verify the current state of PowerPivot and what steps are required to complete configuration.</span></span> <span data-ttu-id="0091d-132">창을 전체 크기로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-132">Expand the window to full size.</span></span> <span data-ttu-id="0091d-133">창 아래쪽에 **유효성 검사**, **실행**및 **끝내기** 명령이 포함된 단추 모음이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-133">You should see a button bar at the bottom of the window that includes **Validate**, **Run**, and **Exit** commands.</span></span>  
  
4.  <span data-ttu-id="0091d-134">**매개 변수** 탭에서</span><span class="sxs-lookup"><span data-stu-id="0091d-134">On the **Parameters** tab:</span></span>  
  
    1.  <span data-ttu-id="0091d-135">**기본 계정 사용자 이름**: 기본 계정의 도메인 사용자 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-135">**Default Account UserName**: Enter a domain user account for the default account.</span></span> <span data-ttu-id="0091d-136">이 계정은 PowerPivot 서비스 애플리케이션 풀을 포함한 서비스를 프로비전하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-136">This account will be used to provision services, including the PowerPivot service application pool.</span></span> <span data-ttu-id="0091d-137">네트워크 서비스, 로컬 시스템 등의 기본 제공 계정을 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="0091d-137">Do not specify a built-in account such as Network Service or Local System.</span></span> <span data-ttu-id="0091d-138">이 도구는 기본 제공 계정을 지정하는 구성을 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-138">The tool blocks configurations that specify built-in accounts.</span></span>  
  
    2.  <span data-ttu-id="0091d-139">**데이터베이스 서버**: SharePoint 팜에 대해 지원되는 SQL Server 데이터베이스 엔진을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-139">**Database Server**: You can use SQL Server Database engine that is supported for the SharePoint farm.</span></span>  
  
    3.  <span data-ttu-id="0091d-140">**암호**: 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-140">**Passphrase**: Enter a passphrase.</span></span> <span data-ttu-id="0091d-141">새 SharePoint 팜을 만드는 경우 서버 또는 애플리케이션을 SharePoint 팜에 추가할 때마다 암호가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-141">If you are creating a new SharePoint farm, the passphrase is used whenever you add a server or application to the SharePoint farm.</span></span> <span data-ttu-id="0091d-142">팜이 이미 있는 경우 서버 애플리케이션을 팜에 추가할 수 있는 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-142">If the farm already exists, enter the passphrase that allows you to add a server application to the farm.</span></span>  
  
    4.  <span data-ttu-id="0091d-143">**Excel Services용 PowerPivot 서버**: [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint 모드 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-143">**PowerPivot Server for Excel Services**: Type the name of an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint mode server.</span></span> <span data-ttu-id="0091d-144">단일 서버 배포에서 이는 데이터베이스 서버와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-144">In a single-server deployment, it is the same as the database server.</span></span> `[ServerName]\powerpivot`  
  
    5.  <span data-ttu-id="0091d-145">왼쪽 창에서 **사이트 모음 만들기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-145">Click **Create Site Collection** in the left window.</span></span> <span data-ttu-id="0091d-146">이후 단계에서 참조할 수 있도록 **사이트 URL** 을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-146">Note **Site URL** so you can reference it in later steps.</span></span> <span data-ttu-id="0091d-147">SharePoint 서버가 아직 구성되지 않은 경우 구성 마법사가 웹 애플리케이션 및 사이트 모음 URL을 `http://[ServerName]`의 루트로 기본 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-147">If the SharePoint server is not already configured, then the configuration wizard defaults the web application, and site collection URLs to the root of `http://[ServerName]`.</span></span> <span data-ttu-id="0091d-148">기본값을 수정하려면 왼쪽 창에서 **기본 웹 애플리케이션 만들기** 및 **웹 애플리케이션 솔루션 배포**페이지를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="0091d-148">To modify the defaults review the following pages in the left window: **Create Default Web application** and **Deploy Web Application Solution**</span></span>  
  
5.  <span data-ttu-id="0091d-149">필요에 따라 각 동작을 완료하는 데 사용되는 나머지 입력 값을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-149">Optionally, review the remaining input values used to complete each action.</span></span> <span data-ttu-id="0091d-150">동작의 세부 정보를 보고 검토하려면 왼쪽 창에서 각 동작을 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="0091d-150">Click each action in the left window to see and review the details of the action.</span></span> <span data-ttu-id="0091d-151">각 항목에 대 한 자세한 내용은이 항목의 " [구성 또는 복구 SharePoint용 PowerPivot 2010 &#40;PowerPivot 구성&#41;도구](../../configure-repair-powerpivot-sharepoint-2010.md) 에서 서버를 구성 하는 데 사용 되는 입력 값" 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="0091d-151">For more information about each one, see the section "Input values used to configure the server in [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md) in this topic.</span></span>  
  
6.  <span data-ttu-id="0091d-152">선택적으로 지금 처리하지 않으려는 동작을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-152">Optionally, remove any actions that you do not want to process at this time.</span></span> <span data-ttu-id="0091d-153">예를 들어, Secure Store Service를 나중에 구성하려는 경우 **Secure Store Service 구성**을 클릭한 다음 **태스크 목록에 이 동작 포함**확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-153">For example, if you want to configure Secure Store Service later, click **Configure Secure Store Service**, and then clear the checkbox **Include this action in the task list**.</span></span>  
  
7.  <span data-ttu-id="0091d-154">**유효성 검사** 를 클릭하여 목록에서 동작을 처리할 수 있는 충분한 정보가 도구에 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-154">Click **Validate** to check whether the tool has sufficient information to process the actions in the list.</span></span> <span data-ttu-id="0091d-155">유효성 검사 오류가 표시되면 왼쪽 창에서 경고를 클릭하여 유효성 검사 오류에 대한 자세한 내용을 보세요.</span><span class="sxs-lookup"><span data-stu-id="0091d-155">If you see validation errors, click the warnings in the left pane to see details of the validation error.</span></span> <span data-ttu-id="0091d-156">유효성 검사 오류를 수정한 다음 **유효성 검사** 를 다시 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-156">Correct any validation errors and then click **Validate** again.</span></span>  
  
8.  <span data-ttu-id="0091d-157">**실행** 을 클릭하여 태스크 목록에 있는 모든 동작을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-157">Click **Run** to process all of the actions in the task list.</span></span> <span data-ttu-id="0091d-158">동작의 유효성을 검사한 후에 **실행** 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-158">Note that **Run** becomes available after you validate the actions.</span></span> <span data-ttu-id="0091d-159">**실행** 이 활성화되지 않으면 먼저 **유효성 검사** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-159">If **Run** is not enabled, click **Validate** first.</span></span>  
  
 <span data-ttu-id="0091d-160">자세한 내용은 [SharePoint용 PowerPivot 2010 &#40;PowerPivot 구성 도구 구성 또는 복구](../../configure-repair-powerpivot-sharepoint-2010.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="0091d-160">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)</span></span>  
  
##  <a name="verify-powerpivot-configuration"></a><a name="bkmk_verify_powerpivot"></a><span data-ttu-id="0091d-161">PowerPivot 구성 확인</span><span class="sxs-lookup"><span data-stu-id="0091d-161">Verify PowerPivot Configuration</span></span>  
 <span data-ttu-id="0091d-162">**서비스:**</span><span class="sxs-lookup"><span data-stu-id="0091d-162">**Services:**</span></span>  
  
1.  <span data-ttu-id="0091d-163">중앙 관리의 시스템 설정에서 **서버의 서비스 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-163">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="0091d-164">**SQL Server Analysis Services** 및 **SQL Server PowerPivot 시스템 서비스** 가 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-164">Verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** are started.</span></span>  
  
 <span data-ttu-id="0091d-165">**팜 기능:**</span><span class="sxs-lookup"><span data-stu-id="0091d-165">**Farm Feature:**</span></span>  
  
1.  <span data-ttu-id="0091d-166">중앙 관리의 시스템 설정에서 **팜 기능 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-166">In Central Administration, in System Settings, click **Manage farm features**.</span></span>  
  
2.  <span data-ttu-id="0091d-167">**PowerPivot 통합 기능** 이 **활성**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-167">Verify that **PowerPivot Integration Feature** is **Active**.</span></span>  
  
 <span data-ttu-id="0091d-168">**사이트 모음 기능:**</span><span class="sxs-lookup"><span data-stu-id="0091d-168">**Site Collection Feature:**</span></span>  
  
1.  <span data-ttu-id="0091d-169">구성 도구로 만든 사이트 URL로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-169">Browse to your site URL that was created by the Configuration tool.</span></span>  
  
     <span data-ttu-id="0091d-170">**설정**![SharePoint 설정](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 설정")을 클릭 한 다음 **사이트 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-170">Click **Settings**![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings"), and then click **Site Settings**.</span></span>  
  
     <span data-ttu-id="0091d-171">**사이트 모음 기능**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-171">Click **Site Collection Features**.</span></span>  
  
2.  <span data-ttu-id="0091d-172">**사이트 모음에 대한 PowerPivot 기능 통합** 이 **활성**상태인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-172">Verify that **PowerPivot Feature Integration for Site Collections** is **Active**.</span></span>  
  
 <span data-ttu-id="0091d-173">**PowerPivot 서비스 응용 프로그램:**</span><span class="sxs-lookup"><span data-stu-id="0091d-173">**PowerPivot Service Application:**</span></span>  
  
1.  <span data-ttu-id="0091d-174">중앙 관리의 **애플리케이션 관리**에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-174">In Central Administration, in the **Application Management**, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="0091d-175">서비스 애플리케이션 상태가 **시작**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-175">Verify the service application status is **started**.</span></span> <span data-ttu-id="0091d-176">기본 이름은 **기본 PowerPivot 서비스 응용 프로그램**입니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-176">The default name is **Default PowerPivot Service Application**.</span></span>  
  
     <span data-ttu-id="0091d-177">기본 서비스 애플리케이션의 이름을 클릭하여 서비스 애플리케이션에 대한 PowerPivot 관리 대시보드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-177">Click the name of the services application to open the PowerPivot Management Dashboard for the service application opens.</span></span> <span data-ttu-id="0091d-178">처음 사용하는 경우 대시보드는 로드하는 데 몇 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-178">On first use, the dashboard takes several minutes to load.</span></span>  
  
 <span data-ttu-id="0091d-179">자세한 내용은 [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0091d-179">For more information, see [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).</span></span>  
  
##  <a name="troubleshoot-issues"></a><a name="bkmk_troubleshoot_issues"></a><span data-ttu-id="0091d-180">문제 해결</span><span class="sxs-lookup"><span data-stu-id="0091d-180">Troubleshoot Issues</span></span>  
 <span data-ttu-id="0091d-181">문제 해결을 돕기 위해 진단 로깅이 활성화되어 있는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-181">To assist in troubleshooting issues, it is a good idea to verify the diagnostic logging is enabled.</span></span>  
  
1.  <span data-ttu-id="0091d-182">SharePoint 중앙 관리에서 **모니터링** 을 클릭하고 **사용 현황 및 상태 데이터 수집 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-182">In SharePoint Central Administration, click **Monitoring** and then click **Configure usage and health data collection**.</span></span>  
  
2.  <span data-ttu-id="0091d-183">**사용량 현황 데이터 수집 사용** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-183">Verify **Enable usage data collection** is selected.</span></span>  
  
3.  <span data-ttu-id="0091d-184">다음 이벤트가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-184">Verify the following events are selected:</span></span>  
  
    -   <span data-ttu-id="0091d-185">교육 원격 분석을 위한 사용 현황 필드 정의</span><span class="sxs-lookup"><span data-stu-id="0091d-185">Definition of usage fields for Education telemetry</span></span>  
  
    -   <span data-ttu-id="0091d-186">PowerPivot 연결</span><span class="sxs-lookup"><span data-stu-id="0091d-186">PowerPivot Connects</span></span>  
  
    -   <span data-ttu-id="0091d-187">PowerPivot 데이터 로드 사용</span><span class="sxs-lookup"><span data-stu-id="0091d-187">PowerPivot Load Data Usage</span></span>  
  
    -   <span data-ttu-id="0091d-188">PowerPivot 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="0091d-188">PowerPivot Query Usage</span></span>  
  
    -   <span data-ttu-id="0091d-189">PowerPivot 데이터 언로드 사용</span><span class="sxs-lookup"><span data-stu-id="0091d-189">PowerPivot Unload Data Usage</span></span>  
  
4.  <span data-ttu-id="0091d-190">**상태 데이터 수집 사용** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-190">Verify **Enable health data collection** is selected.</span></span>  
  
5.  <span data-ttu-id="0091d-191">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0091d-191">Click **OK**.</span></span>  
  
 <span data-ttu-id="0091d-192">데이터 새로 고침 문제를 해결 하는 방법에 대 한 자세한 내용은 [PowerPivot 데이터 새로 고침 문제 해결](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) (을 참조 https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) 하세요.</span><span class="sxs-lookup"><span data-stu-id="0091d-192">For more information on trouble shooting data refresh, see [Troubleshooting PowerPivot Data Refresh](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx).</span></span>  
  
 <span data-ttu-id="0091d-193">구성 도구에 대한 자세한 내용은 [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0091d-193">For more information on the configuration tool, see [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).</span></span>  
  
  
