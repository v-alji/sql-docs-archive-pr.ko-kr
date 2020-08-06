---
title: Analysis Services 배포 마법사 실행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, running
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6207e3e7981f52ca158f50515166d237e0524ea7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743544"
---
# <a name="running-the-analysis-services-deployment-wizard"></a><span data-ttu-id="67ecd-102">Analysis Services 배포 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="67ecd-102">Running the Analysis Services Deployment Wizard</span></span>
  <span data-ttu-id="67ecd-103">배포 마법사를 사용 하 여 프로젝트를 배포 하는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 다음과 같은 방법으로 마법사를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-103">When you use the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard to deploy a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you can run the wizard in the following ways:</span></span>  
  
-   <span data-ttu-id="67ecd-104">**대화형으로**[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 대화형으로 실행하면 사용자 입력에 따라 변경되는 입력 파일을 기반으로 XML 배포 스크립트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-104">**Interactively** When run interactively, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard generates an XML deployment script based on the input files, as modified interactively by user input.</span></span> <span data-ttu-id="67ecd-105">모든 사용자 수정 내용은 배포 스크립트에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-105">The wizard applies any user modifications only to the deployment script.</span></span> <span data-ttu-id="67ecd-106">마법사가 입력 파일을 수정하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-106">The wizard does not modify the input files.</span></span> <span data-ttu-id="67ecd-107">입력 파일에 대한 자세한 내용은 [배포 스크립트를 만드는 데 사용하는 입력 파일 이해](deployment-script-files-input-used-to-create-deployment-script.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67ecd-107">For more information about the input files, see [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md).</span></span>  
  
-   <span data-ttu-id="67ecd-108">**명령 프롬프트에서** 명령 프롬프트에서 실행 되는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사는 마법사를 실행 하는 데 사용 하는 스위치에 따라 XMLA (XML for Analysis) 배포 스크립트를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-108">**From the command prompt** When run at the command prompt, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard generates an XML for Analysis (XMLA) deployment script based upon the switches that you use to run the wizard.</span></span> <span data-ttu-id="67ecd-109">이 경우 마법사가 사용자 입력이 필요한 메시지를 표시하고 해당 입력 내용을 기반으로 입력 파일을 수정하거나 현재 입력 파일을 그대로 사용하여 자동 무인 배포를 실행하거나 나중에 사용할 수 있는 배포 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-109">The wizard may any one of the following: prompt you for user input and modify input files based on that input; run a silent, unattended deployment using the input files as is; or create a deployment script that you can use later.</span></span>  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a><span data-ttu-id="67ecd-110">대화형으로 Analysis Services 배포 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="67ecd-110">Running the Analysis Services Deployment Wizard Interactively</span></span>  
 <span data-ttu-id="67ecd-111">대화형으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 실행하면 마법사가 입력 파일의 값을 읽고 사용자에게 이 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-111">When you run interactively, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the values from the input files and presents this information to you.</span></span> <span data-ttu-id="67ecd-112">배포 대상, 구성 설정, 배포 옵션 및 연결 문자열 암호 등의 입력 값을 수정 하거나 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-112">You can modify these input values-such as deployment destination, configuration settings, deployment options, and connection string passwords-or leave them as is.</span></span> <span data-ttu-id="67ecd-113">사용자가 변경한 입력 값은 XMLA 배포 스크립트 생성 시 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-113">If you change any input values, the wizard uses these changes when generating the XMLA deployment script.</span></span> <span data-ttu-id="67ecd-114">그러나 마법사가 입력 파일의 값을 변경하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-114">However, the wizard does not make any changes to the values in the input file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67ecd-115">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사가 입력 값을 수정하게 하려면 명령 프롬프트에서 마법사를 실행하고 응답 파일 모드로 실행되도록 마법사를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-115">If you want to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard modify the input values, run the wizard at the command prompt and set the wizard to run in answer file mode.</span></span>  
  
 <span data-ttu-id="67ecd-116">입력 값을 검토한 다음 필요에 맞게 변경하면 XMLA 배포 스크립트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-116">After you review the input values and make any wanted changes, the wizard generates the XMLA deployment script.</span></span> <span data-ttu-id="67ecd-117">이 배포 스크립트를 대상 서버에서 바로 실행하거나 나중에 사용하도록 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-117">You can run this deployment script immediately on the destination server or save the script for later use.</span></span>  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a><span data-ttu-id="67ecd-118">대화형으로 Analysis Services 배포 마법사를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="67ecd-118">To run the Analysis Services Deployment Wizard interactively</span></span>  
  
-   <span data-ttu-id="67ecd-119">**시작**메뉴에서 **모든 프로그램**, **Microsoft SQL Server**, **Analysis Services**를 차례로 가리키고 **배포 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-119">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Analysis Services**, and then click **Deployment Wizard**.</span></span>  
  
     <span data-ttu-id="67ecd-120">또는</span><span class="sxs-lookup"><span data-stu-id="67ecd-120">-or-</span></span>  
  
-   <span data-ttu-id="67ecd-121">프로젝트의 **프로젝트 폴더에서** . n e t [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 파일을 두 번 클릭 합니다. *\<project name>*</span><span class="sxs-lookup"><span data-stu-id="67ecd-121">In the **Projects** folder of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, double-click the *\<project name>*.asdatabase file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="67ecd-122">Asdatabase 파일을 찾을 수 없는 경우 *\<project name>* 검색을 사용 하 여 \* asdatabase를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-122">If you cannot find the *\<project name>*.asdatabase file, try using Search and specify \*.asdatabase.</span></span>  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a><span data-ttu-id="67ecd-123">명령 프롬프트에서 Analysis Services 배포 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="67ecd-123">Running the Analysis Services Deployment Wizard at the Command Prompt</span></span>  
 <span data-ttu-id="67ecd-124">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 명령 프롬프트에서도 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-124">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard can also be run at the command prompt.</span></span> <span data-ttu-id="67ecd-125">명령 프롬프트에서 마법사를 실행하는 경우 .asdatabase 파일의 전체 경로를 제공하고 다음 모드 중 하나로 마법사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-125">When you run the wizard at the command prompt, you provide the full path to the .asdatabase file and  run the wizard in one of the following modes:</span></span>  
  
 <span data-ttu-id="67ecd-126">**응답 파일 모드**</span><span class="sxs-lookup"><span data-stu-id="67ecd-126">**Answer file mode**</span></span>  
 <span data-ttu-id="67ecd-127">응답 파일 모드에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]프로젝트를 작성할 때 기본적으로 생성된 입력 파일을 대화형으로 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-127">In answer file mode, the wizard lets you interactively modify the input files that were originally generated when the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project was built in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="67ecd-128">이렇게 수정한 입력 파일은 XMLA 배포 스크립트 생성 전에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-128">The wizard saves these modified input files before generating the XMLA deployment script.</span></span> <span data-ttu-id="67ecd-129">수정한 입력 파일은 다음에 마법사를 실행할 때 새 시작 지점이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-129">The modified input files become the new starting point the next time that the wizard is run.</span></span>  
  
 <span data-ttu-id="67ecd-130">응답 파일 모드에서 마법사를 실행 하려면 **/a** 스위치를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-130">To run the wizard in answer file mode, use the **/a** switch.</span></span>  
  
 <span data-ttu-id="67ecd-131">**자동 모드**</span><span class="sxs-lookup"><span data-stu-id="67ecd-131">**Silent mode**</span></span>  
 <span data-ttu-id="67ecd-132">자동 모드에서는 입력 파일에 있는 정보를 기반으로 자동 무인 배포가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-132">In silent mode, the wizard runs a silent, unattended deployment based on the information resident in the input files.</span></span>  
  
 <span data-ttu-id="67ecd-133">자동 모드에서 마법사를 실행 하려면 **/s** 스위치를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-133">To run the wizard in silent mode, use the **/s** switch.</span></span> <span data-ttu-id="67ecd-134">자동 모드로 마법사를 실행하는 경우 메시지가 콘솔이나 로그 파일(제공된 경우)에 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-134">When you run the wizard in silent mode, messages are output to the console or to a log file if one is provided.</span></span>  
  
 <span data-ttu-id="67ecd-135">**출력 모드**</span><span class="sxs-lookup"><span data-stu-id="67ecd-135">**Output mode**</span></span>  
 <span data-ttu-id="67ecd-136">출력 모드에서는 입력 파일을 기반으로 나중에 실행할 XMLA 배포 스크립트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-136">In output mode, the wizard generates an XMLA deployment script for later execution based on the input files.</span></span>  
  
 <span data-ttu-id="67ecd-137">출력 모드에서 마법사를 실행 하려면 **/o** 스위치를 사용 하 고 출력 파일 이름을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-137">To run the wizard in output mode, use the **/o** switch and provide an output file name.</span></span>  
  
 <span data-ttu-id="67ecd-138">이러한 명령줄 스위치에 대한 자세한 내용은 [배포 유틸리티를 사용하여 모델 솔루션 배포](deploy-model-solutions-with-the-deployment-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67ecd-138">For more information about these command line switches, see [Deploy Model Solutions with the Deployment Utility](deploy-model-solutions-with-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="67ecd-139">다음 절차에서는 명령 프롬프트에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 배포 마법사를 실행하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-139">The following procedure describes how to run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt.</span></span>  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a><span data-ttu-id="67ecd-140">명령 프롬프트에서 Analysis Services 배포 마법사를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="67ecd-140">To run the Analysis Services Deployment Wizard at the command prompt</span></span>  
  
1.  <span data-ttu-id="67ecd-141">명령 프롬프트를 열고 C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-141">Open a command prompt and navigate to the C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE folder.</span></span>  
  
2.  <span data-ttu-id="67ecd-142">**Microsoft.AnalysisServices.Deployment.exe** 를 입력하고 뒤에 마법사를 실행하려는 모드에 해당하는 스위치를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="67ecd-142">Type **Microsoft.AnalysisServices.Deployment.exe** followed by the switches that correspond to the mode in which you want to run the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ecd-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67ecd-143">See Also</span></span>  
 <span data-ttu-id="67ecd-144">[Analysis Services 배포 스크립트 이해](understanding-the-analysis-services-deployment-script.md) </span><span class="sxs-lookup"><span data-stu-id="67ecd-144">[Understanding the Analysis Services Deployment Script](understanding-the-analysis-services-deployment-script.md) </span></span>  
 [<span data-ttu-id="67ecd-145">배포 마법사를 사용하여 모델 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="67ecd-145">Deploy Model Solutions Using the Deployment Wizard</span></span>](deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
