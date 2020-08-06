---
title: 자식 패키지에서 변수 및 매개 변수의 값 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- configurations [Integration Services]
- packages [Integration Services], configurations
- variables [Integration Services], adding
ms.assetid: 9b939edb-4e17-48e5-8428-855beb10049c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 28561db91e5e924d8b25f9c7be7a4a51c6c315ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652900"
---
# <a name="use-the-values-of-variables-and-parameters-in-a-child-package"></a><span data-ttu-id="8ba1d-102">자식 패키지에서 변수 및 매개 변수의 값 사용</span><span class="sxs-lookup"><span data-stu-id="8ba1d-102">Use the Values of Variables and Parameters in a Child Package</span></span>
  <span data-ttu-id="8ba1d-103">이 절차에서는 부모 변수 구성 유형을 사용하는 패키지 구성을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-103">This procedure describes how to create a package configuration that uses the parent variable configuration type.</span></span> <span data-ttu-id="8ba1d-104">이 구성 유형을 사용하여 부모 패키지에서 실행되는 자식 패키지가 부모 변수에 액세스하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-104">This configuration type enables a child package that is run from a parent package to access a variable in the parent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ba1d-105">또한 부모 패키지 변수나 매개 변수 또는 프로젝트 매개 변수를 자식 패키지 매개 변수에 매핑하도록 패키지 실행 태스크를 구성하여 값을 자식 패키지에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-105">You can also pass values to a child package by configuring the Execute Package Task to map parent package variables or parameters, or project parameters, to child package parameters.</span></span> <span data-ttu-id="8ba1d-106">자세한 내용은 [Execute Package Task](control-flow/execute-package-task.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-106">For more information, see [Execute Package Task](control-flow/execute-package-task.md).</span></span>  
  
 <span data-ttu-id="8ba1d-107">자식 패키지에 패키지 구성을 만들기 전에 부모 패키지에 변수를 만들 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-107">It is not necessary to create the variable in the parent package before you create the package configuration in the child package.</span></span> <span data-ttu-id="8ba1d-108">부모 패키지에는 언제든지 변수를 추가할 수 있습니다. 단, 패키지 구성에 정확한 부모 변수의 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-108">You can add the variable to the parent package at any time, but you must use the exact name of the parent variable in the package configuration.</span></span> <span data-ttu-id="8ba1d-109">그러나 부모 변수 구성을 만들려면 이 부모 변수 구성을 통해 업데이트할 수 있는 자식 패키지에 기존 변수가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-109">However, before you can create a parent variable configuration, there must be an existing variable in the child package that the configuration can update.</span></span> <span data-ttu-id="8ba1d-110">변수 추가 및 구성에 대한 자세한 내용은 [패키지에서 사용자 정의 변수의 범위 추가, 삭제, 변경](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-110">For more information about adding and configuring variables, see [Add, Delete, Change Scope of User-Defined Variable in a Package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).</span></span>  
  
 <span data-ttu-id="8ba1d-111">부모 변수 구성에 사용되는 부모 패키지의 변수 범위는 패키지 실행 태스크, 태스크가 있는 컨테이너 또는 패키지로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-111">The scope of the variable in the parent package that is used in a parent variable configuration can be set to the Execute Package task, to the container that has the task, or to the package.</span></span> <span data-ttu-id="8ba1d-112">이름이 같은 여러 개의 변수가 패키지에 정의된 경우 패키지 실행 태스크 범위에 가장 가까운 변수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-112">If multiple variables with the same name are defined in a package, the variable that is closest in scope to the Execute Package task is used.</span></span> <span data-ttu-id="8ba1d-113">패키지 실행 태스크에 가장 가까운 범위는 작업 자체입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-113">The closest scope to the Execute Package task is the task itself.</span></span>  
  
### <a name="to-add-a-variable-to-a-parent-package"></a><span data-ttu-id="8ba1d-114">부모 패키지에 변수를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="8ba1d-114">To add a variable to a parent package</span></span>  
  
1.  <span data-ttu-id="8ba1d-115">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 자식 패키지에 전달할 변수를 추가할 패키지가 포함된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to which you want to add a variable to pass to a child package.</span></span>  
  
2.  <span data-ttu-id="8ba1d-116">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="8ba1d-117">다음 중 하나를 수행하여 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 변수 범위를 정의하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-117">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to define the scope of the variable, do one of the following:</span></span>  
  
    -   <span data-ttu-id="8ba1d-118">패키지 범위를 설정하려면 **제어 흐름** 탭의 디자인 화면에서 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-118">To set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
    -   <span data-ttu-id="8ba1d-119">범위를 패키지 실행 태스크의 부모 컨테이너로 설정하려면 컨테이너를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-119">To set the scope to a parent container of the Execute Package task, click the container.</span></span>  
  
    -   <span data-ttu-id="8ba1d-120">패키지 실행 태스크의 범위를 설정하려면 태스크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-120">To set the scope to the Execute Package task, click the task.</span></span>  
  
4.  <span data-ttu-id="8ba1d-121">변수를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-121">Add and configure a variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ba1d-122">변수가 저장하는 데이터와 호환 가능한 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-122">Select a data type that is compatible with the data that the variable will store.</span></span>  
  
5.  <span data-ttu-id="8ba1d-123">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-add-a-variable-to-a-child-package"></a><span data-ttu-id="8ba1d-124">자식 패키지에 변수를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="8ba1d-124">To add a variable to a child package</span></span>  
  
1.  <span data-ttu-id="8ba1d-125">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 부모 변수 구성을 추가할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-125">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to which you want to add a parent variable configuration.</span></span>  
  
2.  <span data-ttu-id="8ba1d-126">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-126">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="8ba1d-127">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 패키지 범위를 설정하려면 **제어 흐름** 탭의 디자인 화면에서 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-127">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="8ba1d-128">변수를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-128">Add and configure a variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ba1d-129">변수가 저장하는 데이터와 호환 가능한 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-129">Select a data type that is compatible with the data that the variable will store.</span></span>  
  
5.  <span data-ttu-id="8ba1d-130">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-130">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-add-a-parent-package-configuration-to-a-child-package"></a><span data-ttu-id="8ba1d-131">부모 패키지 구성을 자식 패키지에 추가하려면</span><span class="sxs-lookup"><span data-stu-id="8ba1d-131">To add a parent package configuration to a child package</span></span>  
  
1.  <span data-ttu-id="8ba1d-132">자식 패키지가 열려 있지 않은 경우에는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 자식 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-132">If it is not already open, open the child package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="8ba1d-133">**제어 흐름** 탭의 디자인 화면에서 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-133">Click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
3.  <span data-ttu-id="8ba1d-134">**SSIS** 메뉴에서 **패키지 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-134">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="8ba1d-135">**패키지 구성 도우미** 대화 상자에서 **패키지 구성 설정**을 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-135">In the **Package Configuration Organizer** dialog box, select **Enable package configuration**, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="8ba1d-136">패키지 구성 마법사 시작 페이지에서 다음을 클릭 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="8ba1d-136">On the welcome page of the Package Configuration Wizard, click **Next.**</span></span>  
  
6.  <span data-ttu-id="8ba1d-137">구성 유형 선택 페이지의 **구성 유형** 목록에서 **부모 패키지 변수** 를 선택하고 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-137">On the Select Configuration Type page, in the **Configuration type** list, select **Parent package variable** and do one of the following:</span></span>  
  
    -   <span data-ttu-id="8ba1d-138">**구성 설정을 직접 지정**을 선택하고 **부모 변수** 상자에 구성에서 사용할 부모 패키지의 변수 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-138">Select **Specify configuration settings directly**, and then in the **Parent variable** box, provide the name of the variable in the parent package to use in the configuration.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="8ba1d-139">변수 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-139">Variable names are case sensitive.</span></span>  
  
    -   <span data-ttu-id="8ba1d-140">**구성 위치가 환경 변수에 저장됨** 을 선택한 다음 **환경 변수 목록**에서 변수 이름이 포함된 환경 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-140">Select or **Configuration location is stored in an environment variable,** and then in the **Environment variable list**, select the environmentvariable that contains the name of the variable.</span></span>  
  
7.  <span data-ttu-id="8ba1d-141">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-141">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="8ba1d-142">대상 속성 선택 페이지에서 **변수** 노드, 구성할 변수의 **속성** 노드를 차례로 확장한 다음 구성에서 설정할 속성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-142">On the Select Target Property page, expand the **Variable** node, and expand the **Properties** node of the variable to configure, and then click the property to be set by the configuration.</span></span>  
  
9. <span data-ttu-id="8ba1d-143">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-143">Click **Next**.</span></span>  
  
10. <span data-ttu-id="8ba1d-144">마법사 완료 페이지에서 필요에 따라 기본 구성 이름을 수정하고 구성 정보를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-144">On the Completing the Wizard page, optionally, modify the default name of the configuration and review the configuration information.</span></span>  
  
11. <span data-ttu-id="8ba1d-145">**마침** 을 클릭하여 마법사를 완료하고 **패키지 구성 도우미** 대화 상자로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-145">Click **Finish** to complete the wizard and return to the **Package Configuration Organizer** dialog box.</span></span>  
  
12. <span data-ttu-id="8ba1d-146">**패키지 구성 도우미** 대화 상자의 **구성** 상자에 새 구성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-146">In the **Package Configuration Organizer** dialog box, the **Configuration** box lists the new configuration.</span></span>  
  
13. <span data-ttu-id="8ba1d-147">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba1d-147">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba1d-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ba1d-148">See Also</span></span>  
 <span data-ttu-id="8ba1d-149">[패키지 구성](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="8ba1d-149">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="8ba1d-150">[패키지 구성 만들기](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="8ba1d-150">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 <span data-ttu-id="8ba1d-151">[Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="8ba1d-151">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="8ba1d-152">패키지에서 변수 사용</span><span class="sxs-lookup"><span data-stu-id="8ba1d-152">Use Variables in Packages</span></span>](../../2014/integration-services/use-variables-in-packages.md)  
  
  
