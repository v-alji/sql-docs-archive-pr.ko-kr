---
title: Windows PowerShell을 사용 하 여 PowerPivot 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4d83e53e-04f1-417d-9039-d9e81ae0483d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 83b42da3e676a291bb021c02ee52e9a810207397
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659666"
---
# <a name="powerpivot-configuration-using-windows-powershell"></a><span data-ttu-id="be0ca-102">Windows PowerShell을 사용하여 PowerPivot 구성</span><span class="sxs-lookup"><span data-stu-id="be0ca-102">PowerPivot Configuration using Windows PowerShell</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="be0ca-103">에는 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]의 설치를 구성하는 데 사용할 수 있는 Windows PowerShell cmdlet이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-103">includes Windows PowerShell cmdlets that you can use to configure an installation of [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].</span></span> <span data-ttu-id="be0ca-104">PowerShell을 사용하여 설치를 완전히 구성하려면 SharePoint cmdlet과 SharePoint용 PowerPivot cmdlet을 모두 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-104">To fully configure an installation with PowerShell requires the use of both SharePoint cmdlets and PowerPivot for SharePoint cmdlets.</span></span> <span data-ttu-id="be0ca-105">대부분의 구성은 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 도구 중 하나를 사용하여 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-105">A majority of configuration can be completed using one of the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] tools.</span></span> <span data-ttu-id="be0ca-106">도구에 대한 자세한 내용은 [PowerPivot Configuration Tools](power-pivot-configuration-tools.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="be0ca-106">For more information on the tools, see [PowerPivot Configuration Tools](power-pivot-configuration-tools.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="be0ca-107">SharePoint 2010 팜의 경우 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 데이터베이스 서버를 사용하는 SharePoint 팜이나 SharePoint용 PowerPivot을 구성하려면 먼저 SharePoint 2010 SP1을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-107">For a SharePoint 2010 farm, SharePoint 2010 SP1 must be installed before you can configure either PowerPivot for SharePoint, or a SharePoint farm that uses a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database server.</span></span> <span data-ttu-id="be0ca-108">서비스 팩을 아직 설치하지 않았으면 서버를 구성하기 전에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-108">If you have not yet installed the service pack, install it before you begin configuring the server.</span></span>  
  
## <a name="benefits-of-configuring-powerpivot-for-sharepoint-using-powershell"></a><span data-ttu-id="be0ca-109">PowerShell을 사용하여 SharePoint용 PowerPivot을 구성할 때의 이점</span><span class="sxs-lookup"><span data-stu-id="be0ca-109">Benefits of Configuring PowerPivot for SharePoint Using PowerShell</span></span>  
 <span data-ttu-id="be0ca-110">Windows PowerShell 스크립트(.ps1) 파일을 작성하여 구성 태스크를 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-110">You can build Windows PowerShell script (.ps1) files to automate configuration tasks.</span></span> <span data-ttu-id="be0ca-111">모든 서버에서 실행할 수 있는 스크립팅된 설치 및 구성 단계가 필요한 경우 이 방법을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-111">This approach is recommended if you require scripted installation and configuration steps that you can run on any server.</span></span> <span data-ttu-id="be0ca-112">하드웨어 오류가 발생할 경우 서버를 다시 작성하기 위한 재해 복구 계획의 일부로 이러한 스크립트가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-112">You might require such a script as part of a disaster recovery plan for rebuilding a server in the event of a hardware failure.</span></span>  
  
## <a name="view-a-list-of-the-powerpivot-cmdlets-on-a-server"></a><span data-ttu-id="be0ca-113">서버의 PowerPivot Cmdlet 목록 보기</span><span class="sxs-lookup"><span data-stu-id="be0ca-113">View a list of the PowerPivot Cmdlets on a Server</span></span>  
 <span data-ttu-id="be0ca-114">Cmdlet의 내용과 예제를 보려면 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] [SharePoint용 PowerPivot에 대 한 PowerShell 참조](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="be0ca-114">To see content and examples of the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] cmdlets, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>  
  
 <span data-ttu-id="be0ca-115">PowerShell을 사용하여 PowerPivot cmdlet의 목록을 보려면</span><span class="sxs-lookup"><span data-stu-id="be0ca-115">To use PowerShell to view a list of the PowerPivot cmdlets:</span></span>  
  
1.  <span data-ttu-id="be0ca-116">**관리자 권한으로 실행** 옵션을 사용하여 SharePoint 관리 셸을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-116">Open SharePoint Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="be0ca-117">다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-117">Enter the following command:</span></span>  
  
    ```powershell
    Get-Help *powerpivot*  
    ```  
  
     <span data-ttu-id="be0ca-118">cmdlet 이름에 PowerPivot이 포함된 cmdlet 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-118">You should see a list of cmdlets that include PowerPivot in the cmdlet name.</span></span> <span data-ttu-id="be0ca-119">예: `Get-PowerPivotServiceApplication`.</span><span class="sxs-lookup"><span data-stu-id="be0ca-119">For example `Get-PowerPivotServiceApplication`.</span></span> <span data-ttu-id="be0ca-120">사용 가능한 cmdlet 수는 사용 중인 Analysis Services의 버전에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-120">The number of cmdlets available depends on the version of Analysis Services you are using.</span></span>  
  
    -   <span data-ttu-id="be0ca-121">SharePoint 모드 및 SharePoint 2013에 대해 구성한 SQL Server 2012 SP1 Analysis Services 서버에서는 cmdlet을 10개까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-121">10 cmdlets with SQL Server 2012 SP1 Analysis Services server configured in SharePoint mode, and SharePoint 2013.</span></span> <span data-ttu-id="be0ca-122">2012 SP1 버전에서는 Analysis Server를 SharePoint 팜 외부에서 실행할 수 있고 더 적은 수의 Windows PowerShell cmdlet을 필요로 하는 새로운 아키텍처를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-122">The 2012 SP1 version utilizes a new architecture that allows the Analysis Server to run outside the SharePoint farm and requires fewer management Windows PowerShell cmdlets.</span></span>  
  
    -   <span data-ttu-id="be0ca-123">SharePoint 모드 및 SharePoint 2010에서 구성한 SQL Server 2012 Analysis Services 서버에서는 cmdlet을 17개까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-123">17 cmdlets with SQL Server 2012 Analysis Services server configured in SharePoint mode, and SharePoint 2010.</span></span>  
  
     <span data-ttu-id="be0ca-124">목록에 반환 되는 명령이 없거나 ""와 유사한 오류 메시지가 표시 되는 경우 `get-help could not find *powerpivot* in a help file in this session.` 서버에서 PowerPivot cmdlet을 사용 하도록 설정 하는 방법에 대 한 지침은이 항목의 다음 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="be0ca-124">If no commands are returned in the list or you see an error message similar to "`get-help could not find *powerpivot* in a help file in this session.`", see the next section in this topic for instructions on how to enable the PowerPivot cmdlets on the server.</span></span>  
  
     <span data-ttu-id="be0ca-125">모든 cmdlet에는 온라인 도움말이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-125">All cmdlets have online help.</span></span> <span data-ttu-id="be0ca-126">다음 예에서는 `New-PowerPivotServiceApplication` cmdlet에 대한 온라인 도움말을 보는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-126">The following example shows how to view the online help for the `New-PowerPivotServiceApplication` cmdlet:</span></span>  
  
    ```powershell
    Get-Help new-powerpivotserviceapplication -Full  
    ```  
  
     <span data-ttu-id="be0ca-127">예만 보려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-127">Alternatively, to view just the examples, use the following syntax:</span></span>  
  
    ```powershell
    Get-Help new-powerpivotserviceapplication -Example  
    ```  
  
## <a name="enable-powerpivot-cmdlets-on-a-server"></a><span data-ttu-id="be0ca-128">서버에서 PowerPivot Cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="be0ca-128">Enable PowerPivot Cmdlets on a Server</span></span>  
 <span data-ttu-id="be0ca-129">SharePoint용 PowerPivot을 설치하고 팜 솔루션을 배포한 후 PowerPivot cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-129">PowerPivot cmdlets are available after you install PowerPivot for SharePoint and deploy the farm solution.</span></span> <span data-ttu-id="be0ca-130">PowerPivot 구성 도구를 실행하면 솔루션이 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-130">The solutions are deployed when you ran the PowerPivot Configuration tool.</span></span> <span data-ttu-id="be0ca-131">Cmdlet을 사용하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-131">Follow these steps to enable the use of cmdlets:</span></span>  
  
1.  <span data-ttu-id="be0ca-132">**관리자 권한으로 실행** 옵션을 사용하여 SharePoint 관리 셸을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-132">Open SharePoint Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="be0ca-133">첫 번째 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-133">Run the first cmdlet:</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     <span data-ttu-id="be0ca-134">이 cmdlet을 실행하면 솔루션의 이름,  솔루션 ID  및 Deployed=False가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-134">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="be0ca-135">다음 단계에서는 솔루션을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-135">In the next step, you deploy the solution.</span></span>  
  
3.  <span data-ttu-id="be0ca-136">두 번째 cmdlet을 실행하여 솔루션을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-136">Run the second cmdlet to deploy the solution:</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
4.  <span data-ttu-id="be0ca-137">창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-137">Close the window.</span></span> <span data-ttu-id="be0ca-138">**관리자 권한으로 실행** 옵션을 사용하여 창을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="be0ca-138">Reopen it, again using the **Run as Administrator** option.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="be0ca-139">관련 내용</span><span class="sxs-lookup"><span data-stu-id="be0ca-139">Related Content</span></span>  
 [<span data-ttu-id="be0ca-140">중앙 관리에서 PowerPivot 서버 관리 및 구성</span><span class="sxs-lookup"><span data-stu-id="be0ca-140">PowerPivot Server Administration and Configuration in Central Administration</span></span>](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [<span data-ttu-id="be0ca-141">PowerPivot Configuration Tools</span><span class="sxs-lookup"><span data-stu-id="be0ca-141">PowerPivot Configuration Tools</span></span>](power-pivot-configuration-tools.md)  
  
 [<span data-ttu-id="be0ca-142">SharePoint용 PowerPivot에 대한 PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="be0ca-142">PowerShell Reference for PowerPivot for SharePoint</span></span>](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
