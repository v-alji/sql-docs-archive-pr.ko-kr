---
title: 변수 창 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.variables.f1
helpviewer_keywords:
- Variables Window dialog box
ms.assetid: f405e5ce-ef69-4c58-8c7d-a3d44dfe9ab0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffd6da67386291c14ebf588da9a1cf8f399214b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652894"
---
# <a name="variables-window"></a><span data-ttu-id="3b219-102">변수 창</span><span class="sxs-lookup"><span data-stu-id="3b219-102">Variables Window</span></span>
  <span data-ttu-id="3b219-103">**변수** 창을 사용하여 사용자 정의 변수를 생성 및 수정하고 시스템 변수를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-103">Use the **Variables** window to create and modify user-defined variables and view system variables.</span></span>  
  
 <span data-ttu-id="3b219-104">기본적으로는 **변수** 창은 **의 SSID 디자이너에 있는** 연결 관리자 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]영역 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-104">By default, the **Variables** window is located below the **Connection Managers** area in the SSIS Designer, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="3b219-105">**변수** 창이 표시되지 않는 경우 **SSIS** 메뉴에서 **변수**를 클릭하여 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-105">If you don't see the **Variables** window, click **Variables** on the **SSIS** menu to display the window.</span></span>  
  
 <span data-ttu-id="3b219-106">**옵션** 대화 상자의 **키보드** 페이지에서 필요에 따라 선택한 키 조합에 View.Variables 명령을 매핑하여 **변수** 창을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-106">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b219-107">`Name` 및 `Namespace` 속성 값은 Unicode Standard 2.0에 정의된 대로 영문자 또는 밑줄(_)로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-107">The values of the `Name` and `Namespace` properties must begin with an alphabetic character letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span> <span data-ttu-id="3b219-108">후속 문자는 Unicode Standard 2.0에 정의된 문자 또는 숫자이거나 밑줄(\_)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-108">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, or the underscore (\_).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3b219-109">옵션</span><span class="sxs-lookup"><span data-stu-id="3b219-109">Options</span></span>  
 <span data-ttu-id="3b219-110">**변수 추가**</span><span class="sxs-lookup"><span data-stu-id="3b219-110">**Add Variable**</span></span>  
 <span data-ttu-id="3b219-111">사용자 정의 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-111">Add a user-defined variable.</span></span>  
  
 <span data-ttu-id="3b219-112">**변수 이동**</span><span class="sxs-lookup"><span data-stu-id="3b219-112">**Move Variable**</span></span>  
 <span data-ttu-id="3b219-113">목록에서 변수를 클릭하고 **변수 이동** 을 클릭하여 변수 범위를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-113">Click a variable in the list, and then click **Move Variable** to change the variable scope.</span></span> <span data-ttu-id="3b219-114">**새 범위 선택** 대화 상자에서 변수 범위를 변경할 패키지나 패키지에 들어 있는 컨테이너, 태스크 또는 이벤트 처리기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-114">In the **Select New Scope** dialog box, select the package or a container, task, or event handler in the package, to change the variable scope.</span></span>  
  
 <span data-ttu-id="3b219-115">변수 범위에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md)영역 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-115">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="3b219-116">**변수 삭제**</span><span class="sxs-lookup"><span data-stu-id="3b219-116">**Delete Variable**</span></span>  
 <span data-ttu-id="3b219-117">목록에서 변수를 선택한 다음 **변수 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-117">Select a variable from the list, and then click **Delete Variable**.</span></span>  
  
 <span data-ttu-id="3b219-118">**표 옵션**</span><span class="sxs-lookup"><span data-stu-id="3b219-118">**Grid Options**</span></span>  
 <span data-ttu-id="3b219-119">열 선택을 변경하고 **변수** 창에 필터를 적용할 수 있는 **가변 눈금 옵션** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-119">Click to open the **Variable Grid Options** dialog box where you can change the column selection and apply filters to the **Variables** window.</span></span> <span data-ttu-id="3b219-120">자세한 내용은 [가변 눈금 옵션](../../2014/integration-services/variable-grid-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b219-120">For more information, see [Variable Grid Options](../../2014/integration-services/variable-grid-options.md).</span></span>  
  
 `Name`  
 <span data-ttu-id="3b219-121">변수 이름을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-121">View the variable name.</span></span> <span data-ttu-id="3b219-122">사용자 정의 변수의 이름을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-122">You can update the name for user-defined variables.</span></span>  
  
 <span data-ttu-id="3b219-123">**범위**</span><span class="sxs-lookup"><span data-stu-id="3b219-123">**Scope**</span></span>  
 <span data-ttu-id="3b219-124">변수의 범위를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-124">View the scope of the variable.</span></span> <span data-ttu-id="3b219-125">변수 범위는 전체 패키지 범위이거나 컨테이너 또는 태스크 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-125">A variable has either the scope of the entire package, or the scope of a container or task.</span></span> <span data-ttu-id="3b219-126">변수 범위가 충분해야 변수 값을 읽거나 설정하는 데 필요한 모든 다른 태스크 또는 구성 요소에 변수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-126">The scope of the variable must be sufficient so that the variable is visible to any other tasks or components that need to read or set its value.</span></span>  
  
 <span data-ttu-id="3b219-127">변수를 클릭하고 **변수** 창에서 **변수 이동** 을 클릭하여 범위를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-127">You can change the scope by clicking the variable and then clicking **Move Variable** in the **Variables** window.</span></span>  
  
 <span data-ttu-id="3b219-128">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="3b219-128">**Data Type**</span></span>  
 <span data-ttu-id="3b219-129">변수의 데이터 형식을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-129">View the data type of the variable.</span></span> <span data-ttu-id="3b219-130">사용자 정의 변수에 대한 목록에서 데이터 형식을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-130">You can select a data type from the list for user-defined variables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b219-131">변수에 식을 할당할 경우 데이터 형식을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-131">If you assign an expression to the variable, you cannot change the data type.</span></span>  
  
 <span data-ttu-id="3b219-132">**값**</span><span class="sxs-lookup"><span data-stu-id="3b219-132">**Value**</span></span>  
 <span data-ttu-id="3b219-133">변수 값을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-133">View the variable value.</span></span> <span data-ttu-id="3b219-134">사용자 정의 변수에 대한 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-134">You can update the value for user-defined variables.</span></span> <span data-ttu-id="3b219-135">이 값은 리터럴 또는 식일 수 있으며 값은 다중 행 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-135">This value can be a literal or an expression, and the value can be a multi-line string.</span></span> <span data-ttu-id="3b219-136">변수에 식을 할당하려면 **변수** 창의 **식** 열 옆에 있는 줄임표 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-136">To assign an expression to the variable, click the ellipse button that is next to the **Expression** column in the **Variables** window.</span></span>  
  
 `Namespace`  
 <span data-ttu-id="3b219-137">네임스페이스 이름을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-137">View the namespace name.</span></span> <span data-ttu-id="3b219-138">사용자 정의 변수는 처음에 **user** 네임 스페이스에 생성 되지만 필드에서 네임 스페이스 이름을 변경할 수 있습니다 `Namespace` .</span><span class="sxs-lookup"><span data-stu-id="3b219-138">User-defined variables are initially created in the **User** namespace, but you can change the namespace name in the `Namespace` field.</span></span> <span data-ttu-id="3b219-139">이 열을 표시하려면 **표 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-139">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="3b219-140">**Raise Change Event**</span><span class="sxs-lookup"><span data-stu-id="3b219-140">**Raise Change Event**</span></span>  
 <span data-ttu-id="3b219-141">값이 변경될 때 `OnVariableValueChanged` 이벤트를 발생시킬지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-141">Indicate whether to raise the `OnVariableValueChanged` event when a value changes.</span></span> <span data-ttu-id="3b219-142">사용자 정의 및 시스템 변수에 대한 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-142">You can update the value for user-defined and system variables.</span></span> <span data-ttu-id="3b219-143">기본적으로 **변수** 창에는 이 열이 나열되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-143">By default, the **Variables** window does not list this column.</span></span> <span data-ttu-id="3b219-144">이 열을 표시하려면 **표 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-144">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="3b219-145">**설명**</span><span class="sxs-lookup"><span data-stu-id="3b219-145">**Description**</span></span>  
 <span data-ttu-id="3b219-146">변수 설명을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-146">View the variable description.</span></span> <span data-ttu-id="3b219-147">사용자 정의 변수에 대한 설명을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-147">You can change the description for user-defined variables.</span></span> <span data-ttu-id="3b219-148">기본적으로 **변수** 창에는 이 열이 나열되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-148">By default, the **Variables** window does not list this column.</span></span> <span data-ttu-id="3b219-149">이 열을 표시하려면 **표 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-149">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="3b219-150">**식**</span><span class="sxs-lookup"><span data-stu-id="3b219-150">**Expression**</span></span>  
 <span data-ttu-id="3b219-151">변수에 할당된 식을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-151">View the expression assigned to the variable.</span></span> <span data-ttu-id="3b219-152">식을 할당하려면 줄임표 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-152">To assign an expression, click the ellipse button.</span></span>  
  
 <span data-ttu-id="3b219-153">변수에 식을 할당할 경우 해당 변수 옆에 특수 아이콘 표식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-153">If you assign an expression to a variable, a special icon marker displays next to the variable.</span></span> <span data-ttu-id="3b219-154">이 특수 아이콘 표식은 식이 설정되어 있는 연결 관리자 및 태스크 옆에도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b219-154">This special icon marker also displays next to connection managers and tasks that have expressions set on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b219-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b219-155">See Also</span></span>  
 <span data-ttu-id="3b219-156">[Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="3b219-156">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="3b219-157">[패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="3b219-157">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="3b219-158">[Integration Services &#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="3b219-158">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 [<span data-ttu-id="3b219-159">패키지 실행을 위한 덤프 파일 생성</span><span class="sxs-lookup"><span data-stu-id="3b219-159">Generating Dump Files for Package Execution</span></span>](troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
