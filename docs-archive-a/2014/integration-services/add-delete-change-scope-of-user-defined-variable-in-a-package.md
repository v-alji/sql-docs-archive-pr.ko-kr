---
title: 패키지에서 사용자 정의 변수의 범위 추가, 삭제, 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], adding
ms.assetid: cbf40c7f-3c8a-48cd-aefa-8b37faf8b40e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a7e5980fc7f730c69ef886e4e80760cfbdc9e4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650249"
---
# <a name="add-delete-change-scope-of-user-defined-variable-in-a-package"></a><span data-ttu-id="c9268-102">패키지에서 사용자 정의 변수의 범위 추가, 삭제, 변경</span><span class="sxs-lookup"><span data-stu-id="c9268-102">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>
  <span data-ttu-id="c9268-103">다음 절차에서는 **변수** 창을 사용하여 패키지에서 사용자 정의 변수를 추가, 삭제 및 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-103">These procedures describe how to add, delete, and change the scope of a user-defined variable in a package by using the **Variables** window.</span></span>  
  
 <span data-ttu-id="c9268-104">변수 범위에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md)영역 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-104">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]<span data-ttu-id="c9268-105">는 런타임에 시스템 정보를 사용할 수 있도록 하고 패키지 및 이벤트 처리기와 같은 컨테이너에서 사용할 수 있는 시스템 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-105">also provides system variables that make system information available at run time and can be used in containers such as packages and event handlers.</span></span> <span data-ttu-id="c9268-106">시스템 변수는 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-106">You cannot delete system variables.</span></span>  
  
### <a name="to-add-a-variable"></a><span data-ttu-id="c9268-107">변수를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c9268-107">To add a variable</span></span>  
  
1.  <span data-ttu-id="c9268-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 작업하려는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package you want to work with.</span></span>  
  
2.  <span data-ttu-id="c9268-109">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-109">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c9268-110">다음 중 하나를 수행하여 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 변수 범위를 정의하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9268-110">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to define the scope of the variable, do one of the following:</span></span>  
  
    -   <span data-ttu-id="c9268-111">패키지 범위를 설정하려면 **제어 흐름** 탭의 디자인 화면에서 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-111">To set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
    -   <span data-ttu-id="c9268-112">이벤트 처리기의 범위를 설정하려면 **이벤트 처리기** 탭의 디자인 화면에서 실행 파일 및 이벤트 처리기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-112">To set the scope to an event handler, select an executable and an event handler on the design surface of the **Event Handler** tab.</span></span>  
  
    -   <span data-ttu-id="c9268-113">태스크 또는 컨테이너의 범위를 설정하려면 **제어 흐름** 탭 또는 **이벤트 처리기** 탭의 디자인 화면에서 태스크 또는 컨테이너를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-113">To set the scope to a task or container, on the design surface of the **Control Flow** tab or the **Event Handler** tab, click a task or container.</span></span>  
  
4.  <span data-ttu-id="c9268-114">**SSIS** 메뉴에서 **변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-114">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="c9268-115">**옵션** 대화 상자의 **키보드** 페이지에서 필요에 따라 선택한 키 조합에 View.Variables 명령을 매핑하여 **변수** 창을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-115">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
5.  <span data-ttu-id="c9268-116">**변수** 창에서 **변수 추가** 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-116">In the **Variables** window, click the **Add Variable** icon.</span></span> <span data-ttu-id="c9268-117">새 변수가 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-117">The new variable is added to the list.</span></span>  
  
6.  <span data-ttu-id="c9268-118">필요에 따라 **표 옵션** 아이콘을 클릭하고 **가변 눈금 옵션** 대화 상자에 표시할 추가 열을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-118">Optionally, click the **Grid Options** icon, select additional columns to show in the **Variables Grid Options** dialog box, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="c9268-119">필요에 따라 변수 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-119">Optionally, set the variable properties.</span></span> <span data-ttu-id="c9268-120">자세한 내용은 [사용자 정의 변수의 속성 설정](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-120">For more information, see [Set the Properties of a User-Defined Variable](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md).</span></span>  
  
8.  <span data-ttu-id="c9268-121">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-variable"></a><span data-ttu-id="c9268-122">변수를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="c9268-122">To delete a variable</span></span>  
  
1.  <span data-ttu-id="c9268-123">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="c9268-124">솔루션 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-124">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c9268-125">**SSIS** 메뉴에서 **변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-125">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="c9268-126">**옵션** 대화 상자의 **키보드** 페이지에서 필요에 따라 선택한 키 조합에 View.Variables 명령을 매핑하여 **변수** 창을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-126">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="c9268-127">삭제할 변수를 선택한 다음 **변수 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-127">Select the variable to delete, and then click **Delete Variable**.</span></span>  
  
     <span data-ttu-id="c9268-128">변수 창에 변수가 표시 되지 않는 경우 **표 옵션** 을 클릭 하 고 **모든 범위의 변수 표시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-128">If you don't see the variable in the Variables window, click **Grid Options** and then select **Show variables of all scopes**.</span></span>  
  
5.  <span data-ttu-id="c9268-129">**변수 삭제 확인** 대화 상자에서 **예** 를 클릭하여 삭제를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-129">If the **Confirm Deletion of Variables** dialog box opens, click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="c9268-130">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-130">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-change-the-scope-of-a-variable"></a><span data-ttu-id="c9268-131">변수의 범위를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="c9268-131">To change the scope of a variable</span></span>  
  
1.  <span data-ttu-id="c9268-132">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-132">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="c9268-133">솔루션 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-133">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c9268-134">**SSIS** 메뉴에서 **변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-134">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="c9268-135">**옵션** 대화 상자의 **키보드** 페이지에서 필요에 따라 선택한 키 조합에 View.Variables 명령을 매핑하여 **변수** 창을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-135">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="c9268-136">변수를 선택한 다음 **변수 이동**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-136">Select the variable and then click **Move Variable**.</span></span>  
  
     <span data-ttu-id="c9268-137">변수 창에 변수가 표시 되지 않는 경우 **표 옵션** 을 클릭 하 고 **모든 범위의 변수 표시**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-137">If you don't see the variable in the Variables window, click **Grid Options** and then select **Show variables of all scopes**.</span></span>  
  
5.  <span data-ttu-id="c9268-138">**새 범위 선택** 대화 상자에서 변수 범위를 변경할 패키지나 패키지에 들어 있는 컨테이너, 태스크 또는 이벤트 처리기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-138">In the **Select New Scope** dialog box, select the package or a container, task, or event handler in the package, to change the variable scope.</span></span>  
  
6.  <span data-ttu-id="c9268-139">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9268-139">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9268-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9268-140">See Also</span></span>  
 <span data-ttu-id="c9268-141">[Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="c9268-141">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="c9268-142">[패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="c9268-142">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="c9268-143">[사용자 정의 변수의 속성 설정](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md) </span><span class="sxs-lookup"><span data-stu-id="c9268-143">[Set the Properties of a User-Defined Variable](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md) </span></span>  
 [<span data-ttu-id="c9268-144">자식 패키지에서 변수 및 매개 변수의 값 사용</span><span class="sxs-lookup"><span data-stu-id="c9268-144">Use the Values of Variables and Parameters in a Child Package</span></span>](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
  
