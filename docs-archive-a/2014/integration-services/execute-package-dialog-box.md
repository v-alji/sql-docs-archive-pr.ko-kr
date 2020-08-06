---
title: 패키지 실행 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageexecute.f1
- sql12.ssis.ssms.executepackage.f1
ms.assetid: 4f7a806d-4867-4d1f-bc65-b00c1caee7b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b60381054c781cd59f0a9d434710663b72d616c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651795"
---
# <a name="execute-package-dialog-box"></a><span data-ttu-id="76517-102">Execute Package Dialog Box</span><span class="sxs-lookup"><span data-stu-id="76517-102">Execute Package Dialog Box</span></span>
  <span data-ttu-id="76517-103">**패키지 실행** 대화 상자를 사용하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 저장된 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76517-103">Use the **Execute Package** dialog box to run a package that is stored on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="76517-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지는 환경 변수에 값이 저장된 매개 변수를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76517-104">An [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package may contain parameters that values stored in environment variables.</span></span> <span data-ttu-id="76517-105">이러한 패키지를 실행하려면 먼저 환경 변수 값을 제공하는 데 사용할 환경을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-105">Before executing such a package, you must specify which environment will be used to provide the environment variable values.</span></span> <span data-ttu-id="76517-106">프로젝트에 여러 환경을 포함할 수는 있지만 실행할 때는 하나의 환경만 사용하여 환경 변수 값을 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76517-106">A project may contain multiple environments, but only one environment can be used for binding environment variable values at the time of execution.</span></span> <span data-ttu-id="76517-107">패키지에 사용되는 환경 변수가 없는 경우에는 환경이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76517-107">If no environment variables are used in the package, an environment is not required.</span></span>  
  
 <span data-ttu-id="76517-108">수행 작업</span><span class="sxs-lookup"><span data-stu-id="76517-108">What do you want to do?</span></span>  
  
-   [<span data-ttu-id="76517-109">패키지 실행 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="76517-109">Open the Execute Package dialog box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="76517-110">일반 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="76517-110">Set the Options on the General page</span></span>](#general)  
  
-   [<span data-ttu-id="76517-111">매개 변수 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="76517-111">Set the Options on the Parameters tab</span></span>](#parameters)  
  
-   [<span data-ttu-id="76517-112">연결 관리자 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="76517-112">Set the Options on the Connection Managers tab</span></span>](#connection)  
  
-   [<span data-ttu-id="76517-113">고급 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="76517-113">Set the Options on the Advanced tab</span></span>](#advanced)  
  
-   [<span data-ttu-id="76517-114">패키지 실행 대화 상자의 옵션 스크립팅</span><span class="sxs-lookup"><span data-stu-id="76517-114">Scripting the Options in the Execute Package Dialog Box</span></span>](#script)  
  
##  <a name="open-the-execute-package-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="76517-115">패키지 실행 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="76517-115">Open the Execute Package dialog box</span></span>  
  
1.  <span data-ttu-id="76517-116">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-116">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="76517-117">SSISDB 데이터베이스를 호스팅하는 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-117">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="76517-118">개체 탐색기에서 트리를 확장하여 **Integration Services 카탈로그** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-118">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="76517-119">**SSISDB** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-119">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="76517-120">실행할 패키지가 들어 있는 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-120">Expand the folder that contains the package you want to run.</span></span>  
  
5.  <span data-ttu-id="76517-121">패키지를 마우스 오른쪽 단추로 클릭하고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-121">Right-click the package, and then click **Execute**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="76517-122">일반 페이지에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="76517-122">Set the Options on the General page</span></span>  
 <span data-ttu-id="76517-123">**환경** 을 선택하여 패키지 실행 시 적용할 환경을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-123">Select **Environment** to specify the environment that is applied with the package is run.</span></span>  
  
##  <a name="set-the-options-on-the-parameters-tab"></a><a name="parameters"></a> <span data-ttu-id="76517-124">매개 변수 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="76517-124">Set the Options on the Parameters tab</span></span>  
 <span data-ttu-id="76517-125">**매개 변수** 탭에서 패키지 실행 시 사용되는 매개 변수 값을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-125">Use the **Parameters** tab to modify the parameter values that are used when the package runs.</span></span>  
  
##  <a name="set-the-options-on-the-connection-managers-tab"></a><a name="connection"></a> <span data-ttu-id="76517-126">연결 관리자 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="76517-126">Set the Options on the Connection Managers tab</span></span>  
 <span data-ttu-id="76517-127">연결 관리자 탭에서 패키지 연결 관리자 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-127">Use the Connection Managers tab to set the properties of the package connection manager(s).</span></span>  
  
##  <a name="set-the-options-on-the-advanced-tab"></a><a name="advanced"></a> <span data-ttu-id="76517-128">고급 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="76517-128">Set the Options on the Advanced tab</span></span>  
 <span data-ttu-id="76517-129">고급 탭에서 속성 및 기타 패키지 설정을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-129">Use the Advanced tab to manage properties and other package settings.</span></span>  
  
 <span data-ttu-id="76517-130">**추가**, **편집**, **제거**</span><span class="sxs-lookup"><span data-stu-id="76517-130">**Add**, **Edit**, **Remove**</span></span>  
 <span data-ttu-id="76517-131">속성을 추가, 편집 또는 제거하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-131">Click to add, edit, or remove a property.</span></span>  
  
 <span data-ttu-id="76517-132">**로깅 수준**</span><span class="sxs-lookup"><span data-stu-id="76517-132">**Logging level**</span></span>  
 <span data-ttu-id="76517-133">패키지 실행에 대한 로깅 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-133">Select the logging level for the package execution.</span></span> <span data-ttu-id="76517-134">자세한 내용은 [catalog.set_execution_parameter_value&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76517-134">For more information, see [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database).</span></span>  
  
 <span data-ttu-id="76517-135">**오류 덤프**</span><span class="sxs-lookup"><span data-stu-id="76517-135">**Dump on errors**</span></span>  
 <span data-ttu-id="76517-136">패키지 실행 시 오류가 발생할 경우 덤프 파일을 생성할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-136">Specify whether a dump file is created when errors occur during the package execution.</span></span> <span data-ttu-id="76517-137">자세한 내용은 [패키지 실행을 위한 덤프 파일 생성](troubleshooting/generating-dump-files-for-package-execution.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76517-137">For more information, see [Generating Dump Files for Package Execution](troubleshooting/generating-dump-files-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="76517-138">**32비트 런타임**</span><span class="sxs-lookup"><span data-stu-id="76517-138">**32-bit runtime**</span></span>  
 <span data-ttu-id="76517-139">패키지가 32비트 시스템에서 실행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-139">Specify that the package will execute on a 32-bit system.</span></span>  
  
##  <a name="scripting-the-options-in-the-execute-package-dialog-box"></a><a name="script"></a> <span data-ttu-id="76517-140">패키지 실행 대화 상자의 옵션 스크립팅</span><span class="sxs-lookup"><span data-stu-id="76517-140">Scripting the Options in the Execute Package Dialog Box</span></span>  
 <span data-ttu-id="76517-141">**패키지 실행** 대화 상자에 있는 동안 도구 모음의 **스크립트** 단추를 사용하여 [!INCLUDE[tsql](../includes/tsql-md.md)] 코드를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76517-141">While you are in the **Execute Package** dialog box, you can also use the **Script** button on the toolbar to write [!INCLUDE[tsql](../includes/tsql-md.md)] code for you.</span></span> <span data-ttu-id="76517-142">생성된 스크립트는 **패키지 실행** 대화 상자에서 선택한 것과 동일한 옵션으로 [catalog.start_execution&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) 저장 프로시저를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="76517-142">The generated script calls the stored procedures [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) with the same options that you have selected in the **Execute Package** dialog box.</span></span> <span data-ttu-id="76517-143">이 스크립트는 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]의 새 스크립트 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="76517-143">The script appears in a new script window in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
  
