---
title: 스크립트 구성 요소를 사용하여 비동기 변환 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- asynchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: 0d814404-21e4-4a68-894c-96fa47ab25ae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 465c4a597b4a18d7bd956116cd5d7640a5393958
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651770"
---
# <a name="creating-an-asynchronous-transformation-with-the-script-component"></a><span data-ttu-id="9313e-102">스크립트 구성 요소를 사용하여 비동기 변환 만들기</span><span class="sxs-lookup"><span data-stu-id="9313e-102">Creating an Asynchronous Transformation with the Script Component</span></span>
  <span data-ttu-id="9313e-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 데이터 흐름에서 변환 구성 요소를 사용하여 데이터가 원본에서 대상으로 전달될 때 데이터를 수정하고 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-103">You use a transformation component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to modify and analyze data as it passes from source to destination.</span></span> <span data-ttu-id="9313e-104">동기 출력을 사용하는 변환에서는 각 입력 행이 이 구성 요소를 통해 전달될 때 이를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-104">A transformation with synchronous outputs processes each input row as it passes through the component.</span></span> <span data-ttu-id="9313e-105">비동기 출력을 사용하는 변환에서는 입력 행을 모두 받을 때까지 기다렸다가 처리를 완료하거나 입력 행을 모두 받기 전에 일부 행을 출력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-105">A transformation with asynchronous outputs may wait to complete its processing until the transformation has received all input rows, or the transformation may output certain rows before it has received all input rows.</span></span> <span data-ttu-id="9313e-106">이 항목에서는 비동기 변환에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-106">This topic discusses an asynchronous transformation.</span></span> <span data-ttu-id="9313e-107">처리에 동기 변환이 필요한 경우에는 [스크립트 구성 요소를 사용하여 동기 변환 만들기](../data-flow/transformations/script-component.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-107">If your processing requires a synchronous transformation, see [Creating a Synchronous Transformation with the Script Component](../data-flow/transformations/script-component.md).</span></span> <span data-ttu-id="9313e-108">동기 구성 요소와 비동기 구성 요소 간 차이에 대한 자세한 내용은 [동기 및 비동기 변환 이해](../understanding-synchronous-and-asynchronous-transformations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-108">For more information about the differences between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="9313e-109">스크립트 구성 요소에 대한 개요는 [스크립트 구성 요소를 사용하여 데이터 흐름 확장](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-109">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>

 <span data-ttu-id="9313e-110">스크립트 구성 요소 및 해당 구성 요소가 생성하는 인프라 코드를 사용하면 사용자 지정 데이터 흐름 구성 요소를 개발하는 과정이 간단해집니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-110">The Script component and the infrastructure code that it generates for you simplify the process of developing a custom data flow component.</span></span> <span data-ttu-id="9313e-111">하지만 스크립트 구성 요소의 작동 방식을 이해하려면 [사용자 지정 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) 섹션과 이 섹션의 [동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)을 통해 사용자 지정 데이터 흐름 구성 요소를 개발하는 데 필요한 단계를 파악하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-111">However, to understand how the Script component works, you may find it useful to read through the steps that you must follow in developing a custom data flow component in the [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) section, and especially [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>

## <a name="getting-started-with-an-asynchronous-transformation-component"></a><span data-ttu-id="9313e-112">비동기 변환 구성 요소 시작</span><span class="sxs-lookup"><span data-stu-id="9313e-112">Getting Started with an Asynchronous Transformation Component</span></span>
 <span data-ttu-id="9313e-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 데이터 흐름 탭에 스크립트 구성 요소를 추가하면 구성 요소를 원본, 변환 또는 대상으로 미리 구성하기 위한 **스크립트 구성 요소 유형 선택** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-113">When you add a Script component to the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box appears, prompting you to preconfigure the component as a source, transformation, or destination.</span></span> <span data-ttu-id="9313e-114">이 대화 상자에서 **변환**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-114">In this dialog box, select **Transformation**.</span></span>

## <a name="configuring-an-asynchronous-transformation-component-in-metadata-design-mode"></a><span data-ttu-id="9313e-115">메타데이터 디자인 모드에서 비동기 변환 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="9313e-115">Configuring an Asynchronous Transformation Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="9313e-116">변환 구성 요소를 만드는 옵션을 선택한 후에는 **스크립트 변환 편집기**를 사용하여 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-116">After you select the option to create a transformation component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="9313e-117">자세한 내용은 [스크립트 구성 요소 편집기에서 스크립트 구성 요소 구성](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-117">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="9313e-118">스크립트 구성 요소에서 사용할 스크립트 언어를 선택하려면 **스크립트 변환 편집기** 대화 상자의 **스크립트** 페이지에서 **ScriptLanguage** 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-118">To select the script language that the Script component will use, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor** dialog box.</span></span>

> [!NOTE]
>  <span data-ttu-id="9313e-119">스크립트 구성 요소에 대한 기본 스크립트 언어를 설정하려면 **옵션** 대화 상자의 **일반** 페이지에서 **스크립트 언어** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-119">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="9313e-120">자세한 내용은 [General Page](../general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-120">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="9313e-121">데이터 흐름 변환 구성 요소는 하나의 입력을 사용하며 하나 이상의 출력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-121">A data flow transformation component has one input and supports one or more outputs.</span></span> <span data-ttu-id="9313e-122">구성 요소의 입력과 출력을 구성하는 것은 사용자 지정 스크립트를 작성하기 전에 메타데이터 디자인 모드에서 **스크립트 변환 편집기**를 사용하여 완료해야 하는 단계 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-122">Configuring the input and outputs of your component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="configuring-input-columns"></a><span data-ttu-id="9313e-123">입력 열 구성</span><span class="sxs-lookup"><span data-stu-id="9313e-123">Configuring Input Columns</span></span>
 <span data-ttu-id="9313e-124">스크립트 구성 요소를 사용하여 만들어진 변환 구성 요소에서는 하나의 입력만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-124">A transformation component created by using the Script component has a single input.</span></span>

 <span data-ttu-id="9313e-125">**스크립트 변환 편집기**의 **입력 열** 페이지에 나타나는 열 목록에는 업스트림 데이터 흐름 구성 요소의 출력에서 가져온 사용 가능한 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-125">On the **Input Columns** page of the **Script Transformation Editor**, the columns list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="9313e-126">이 목록에서 변환하거나 전달할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-126">Select the columns that you want to transform or pass through.</span></span> <span data-ttu-id="9313e-127">현재 위치에서 변환할 모든 열은 읽기/쓰기로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-127">Mark any columns that you want to transform in place as Read/Write.</span></span>

 <span data-ttu-id="9313e-128">**스크립트 변환 편집기**의 **입력 열** 페이지에 대한 자세한 내용은 [스크립트 변환 편집기&#40;입력 열 페이지&#41;](../script-transformation-editor-input-columns-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-128">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

### <a name="configuring-inputs-outputs-and-output-columns"></a><span data-ttu-id="9313e-129">입력, 출력 및 출력 열 구성</span><span class="sxs-lookup"><span data-stu-id="9313e-129">Configuring Inputs, Outputs, and Output Columns</span></span>
 <span data-ttu-id="9313e-130">변환 구성 요소는 하나 이상의 출력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-130">A transformation component supports one or more outputs.</span></span>

 <span data-ttu-id="9313e-131">비동기 출력을 사용하는 변환에는 두 개의 출력이 있는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-131">Frequently a transformation with asynchronous outputs has two outputs.</span></span> <span data-ttu-id="9313e-132">예를 들어 특정 도시에 있는 주소의 수를 계산할 때 주소 데이터를 하나의 출력에 전달하고 집계 결과는 다른 출력으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-132">For example, when you count the number of addresses located in a specific city, you may want to pass the address data through to one output, while sending the result of the aggregation to another output.</span></span> <span data-ttu-id="9313e-133">집계 출력에는 새 출력 열도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-133">The aggregation output also requires a new output column.</span></span>

 <span data-ttu-id="9313e-134">**스크립트 변환 편집기**의 **입/출력** 페이지에서는 기본적으로 단일 출력이 만들어졌지만 출력 열은 만들어지지 않았음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-134">On the **Inputs and Outputs** page of the **Script Transformation Editor**, you see that a single output has been created by default, but no output columns have been created.</span></span> <span data-ttu-id="9313e-135">편집기의 이 페이지에서 다음과 같은 항목을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-135">On this page of the editor, you can configure the following items:</span></span>

-   <span data-ttu-id="9313e-136">집계 결과에 대한 출력과 같은 추가 출력을 하나 이상 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-136">You may want to create one or more additional outputs, such as an output for the result of an aggregation.</span></span> <span data-ttu-id="9313e-137">비동기 변환 구성 요소의 출력을 관리하려면 **출력 추가** 및 **출력 제거** 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-137">Use the **Add Output** and **Remove Output** buttons to manage the outputs of your asynchronous transformation component.</span></span> <span data-ttu-id="9313e-138">출력이 단순히 업스트림 구성 요소에서 데이터를 전달하거나 기존 행 및 열의 현재 위치에서 데이터를 변환하지 않음을 나타내려면 각 출력의 `SynchronousInputID` 속성을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-138">Set the `SynchronousInputID` property of each output to zero to indicate that the output does not simply pass through data from an upstream component or transform it in place in the existing rows and columns.</span></span> <span data-ttu-id="9313e-139">입력과 출력이 비동기적으로 이루어지게 하는 것은 이 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-139">It is this setting that makes the outputs asynchronous to the input.</span></span>

-   <span data-ttu-id="9313e-140">입력 및 출력에 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-140">You may want to assign a friendly name to the input and outputs.</span></span> <span data-ttu-id="9313e-141">스크립트 구성 요소에서는 이러한 이름을 사용하여 스크립트에서 입력 및 출력을 참조하는 데 사용할 형식화된 접근자 속성을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-141">The Script component uses these names to generate the typed accessor properties that you will use to refer to the input and outputs in your script.</span></span>

-   <span data-ttu-id="9313e-142">비동기 변환에서는 데이터 흐름에 열을 추가하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-142">Frequently an asynchronous transformation adds columns to the data flow.</span></span> <span data-ttu-id="9313e-143">출력의 `SynchronousInputID` 속성이 0으로 설정되어 출력이 단순히 업스트림 구성 요소에서 데이터를 전달하거나 기존 행 및 열의 현재 위치에서 데이터를 변환하지 않음을 나타내는 경우에는 출력에서 명시적으로 출력 열을 추가하고 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-143">When the `SynchronousInputID` property of an output is zero, indicating that the output does not simply pass through data from an upstream component or transform it in place in the existing rows and columns, you must add and configure output columns explicitly on the output.</span></span> <span data-ttu-id="9313e-144">출력 열의 이름은 해당 열이 매핑된 입력 열의 이름과 같지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-144">Output columns do not have to have the same names as the input columns to which they are mapped.</span></span>

-   <span data-ttu-id="9313e-145">추가 정보를 포함할 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-145">You may want to add more columns to contain additional information.</span></span> <span data-ttu-id="9313e-146">이 경우 추가 열에 데이터를 채우기 위한 코드를 직접 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-146">You must write your own code to fill the additional columns with data.</span></span> <span data-ttu-id="9313e-147">표준 오류 출력의 동작을 재현하는 방법에 대한 자세한 내용은 [스크립트 구성 요소의 오류 출력 시뮬레이션](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-147">For information about reproducing the behavior of a standard error output, see [Simulating an Error Output for the Script Component](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).</span></span>

 <span data-ttu-id="9313e-148">**스크립트 변환 편집기**의 **입/출력** 페이지에 대한 자세한 내용은 [스크립트 변환 편집기&#40;입/출력 페이지&#41;](../script-transformation-editor-inputs-and-outputs-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-148">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="9313e-149">변수 추가</span><span class="sxs-lookup"><span data-stu-id="9313e-149">Adding Variables</span></span>
 <span data-ttu-id="9313e-150">스크립트에 사용하려는 값을 포함하는 기존 변수가 있는 경우 **스크립트 변환 편집기**의 **스크립트** 페이지에서 ReadOnlyVariables 및 ReadWriteVariables 속성 필드에 해당 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-150">If there are any existing variables whose values you want to use in your script, you can add them in the ReadOnlyVariables and ReadWriteVariables property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="9313e-151">속성 필드에 여러 변수를 추가하는 경우 변수 이름을 쉼표로 구분하십시오.</span><span class="sxs-lookup"><span data-stu-id="9313e-151">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="9313e-152">및 속성 필드 옆의 줄임표 (**...**) 단추를 클릭 한 `ReadOnlyVariables` `ReadWriteVariables` 다음 **변수 선택** 대화 상자에서 변수를 선택 하 여 여러 개의 변수를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-152">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="9313e-153">스크립트 구성 요소에서 변수를 사용하는 방법에 대한 일반적인 내용은 [스크립트 구성 요소에서 변수 사용](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-153">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="9313e-154">**스크립트 변환 편집기**의 **스크립트** 페이지에 대한 자세한 내용은 [스크립트 변환 편집기&#40;스크립트 페이지&#41;](../script-transformation-editor-script-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-154">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-an-asynchronous-transformation-component-in-code-design-mode"></a><span data-ttu-id="9313e-155">코드 디자인 모드에서 비동기 변환 구성 요소 스크립팅</span><span class="sxs-lookup"><span data-stu-id="9313e-155">Scripting an Asynchronous Transformation Component in Code-Design Mode</span></span>
 <span data-ttu-id="9313e-156">구성 요소에 대한 메타데이터를 모두 구성한 후에는 사용자 지정 스크립트를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-156">After you have configured all the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="9313e-157">**스크립트 변환 편집기**의 **스크립트** 페이지에서 **스크립트 편집**을 클릭하여 사용자 지정 스크립트를 추가할 수 있는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications) IDE를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-157">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="9313e-158">사용하는 스크립트 언어는 **스크립트** 페이지에서 **ScriptLanguage** 속성에 대한 스크립트 언어로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 중에서 선택한 언어에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-158">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="9313e-159">스크립트 구성 요소를 사용하여 만든 모든 종류의 구성 요소에 적용되는 중요한 정보는 [스크립트 구성 요소 코딩 및 디버깅](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-159">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="9313e-160">자동 생성 코드 이해</span><span class="sxs-lookup"><span data-stu-id="9313e-160">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="9313e-161">변환 구성 요소를 만들고 구성한 후 VSTA IDE를 열면 편집 가능한 `ScriptMain` 클래스가 ProcessInputRow 및 CreateNewOutputRows 메서드에 대 한 스텁을 사용 하 여 코드 편집기에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-161">When you open the VSTA IDE after creating and configuring a transformation component, the editable `ScriptMain` class appears in the code editor with stubs for the ProcessInputRow and the CreateNewOutputRows methods.</span></span> <span data-ttu-id="9313e-162">이 ScriptMain 클래스에서 사용자 지정 코드를 작성해야 하며 ProcessInputRow는 변환 구성 요소에서 가장 중요한 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-162">The ScriptMain class is where you will write your custom code, and ProcessInputRow is the most important method in a transformation component.</span></span> <span data-ttu-id="9313e-163">`CreateNewOutputRows` 메서드는 원본 구성 요소에서 보다 일반적으로 사용되는데 이는 두 구성 요소가 모두 개별적인 출력 행을 만들어야 한다는 점에서 비동기 변환과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-163">The `CreateNewOutputRows` method is more typically used in a source component, which is like an asynchronous transformation in that both components must create their own output rows.</span></span>

 <span data-ttu-id="9313e-164">VSTA **프로젝트 탐색기** 창을 열면 스크립트 구성 요소가 읽기 전용 `BufferWrapper` 및 프로젝트 항목도 생성 한 것을 볼 수 있습니다 `ComponentWrapper` .</span><span class="sxs-lookup"><span data-stu-id="9313e-164">If you open the VSTA **Project Explorer** window, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="9313e-165">ScriptMain 클래스는 프로젝트 항목의 UserComponent 클래스에서 상속 `ComponentWrapper` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-165">The ScriptMain class inherits from the UserComponent class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="9313e-166">런타임에 데이터 흐름 엔진은 `UserComponent` <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> 부모 클래스의 메서드를 재정의 하는 클래스의 PrimeOutput 메서드를 호출 합니다 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> .</span><span class="sxs-lookup"><span data-stu-id="9313e-166">At run time, the data flow engine calls the PrimeOutput method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="9313e-167">PrimeOutput 메서드는 차례로 CreateNewOutputRows 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-167">The PrimeOutput method in turn calls the CreateNewOutputRows method.</span></span>

 <span data-ttu-id="9313e-168">다음으로, 데이터 흐름 엔진은 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 부모 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> 메서드를 재정의하는 UserComponent 클래스의 ProcessInput 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-168">Next, the data flow engine invokes the ProcessInput method in the UserComponent class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="9313e-169">그러면 ProcessInput 메서드는 입력 버퍼의 행을 반복하고 각 행에 대해 ProcessInputRow 메서드를 한 번씩 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-169">The ProcessInput method in turn loops through the rows in the input buffer and calls the ProcessInputRow method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="9313e-170">사용자 지정 코드 작성</span><span class="sxs-lookup"><span data-stu-id="9313e-170">Writing Your Custom Code</span></span>
 <span data-ttu-id="9313e-171">사용자 지정 비동기 변환 구성 요소 만들기를 마치려면 재정의된 ProcessInputRow 메서드를 사용하여 입력 버퍼의 각 행에 있는 데이터를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-171">To finish creating a custom asynchronous transformation component, you must use the overridden ProcessInputRow method to process the data in each row of the input buffer.</span></span> <span data-ttu-id="9313e-172">출력은 입력과 동기적으로 이루어지지 않으므로 데이터 행을 출력에 명시적으로 써야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-172">Because the outputs are not synchronous to the input, you must explicitly write rows of data to the outputs.</span></span>

 <span data-ttu-id="9313e-173">비동기 변환에서는 ProcessInputRow 또는 ProcessInput 메서드 내에서 AddRow 메서드를 사용하여 출력에 행을 적절하게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-173">In an asynchronous transformation, you can use the AddRow method to add rows to the output as appropriate from within the ProcessInputRow or ProcessInput methods.</span></span> <span data-ttu-id="9313e-174">CreateNewOutputRows 메서드를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-174">You do not have to use the CreateNewOutputRows method.</span></span> <span data-ttu-id="9313e-175">집계 결과와 같은 결과를 특정 출력에 한 행으로 작성하려는 경우 먼저 CreateNewOutputRows 메서드를 사용하여 출력 행을 만들고 나중에 모든 입력 행을 처리한 후에 해당 값을 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-175">If you are writing a single row of results, such as aggregation results, to a particular output, you can create the output row beforehand by using the CreateNewOutputRows method, and fill in its values later after processing all input rows.</span></span> <span data-ttu-id="9313e-176">그러나 스크립트 구성 요소에서는 입력 또는 출력에 현재 행만 사용할 수 있으므로 CreateNewOutputRows 메서드에서 여러 행을 만드는 것은 유용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-176">However it is not useful to create multiple rows in the CreateNewOutputRows method, because the Script component only lets you use the current row in an input or output.</span></span> <span data-ttu-id="9313e-177">CreateNewOutputRows 메서드는 처리할 입력 행이 없는 원본 구성 요소에서 보다 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-177">The CreateNewOutputRows method is more important in a source component where there are no input rows to process.</span></span>

 <span data-ttu-id="9313e-178">ProcessInput 메서드 자체를 재정의할 수도 있으므로 입력 버퍼를 반복하고 각 행에 대해 ProcessInputRow를 호출하기 전이나 그 후에 예비 또는 최종 처리를 추가로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-178">You may also want to override the ProcessInput method itself, so that you can do additional preliminary or final processing before or after you loop through the input buffer and call ProcessInputRow for each row.</span></span> <span data-ttu-id="9313e-179">예를 들어이 항목의 코드 예제 중 하나는 ProcessInput을 재정의 하 여 특정 도시의 주소 수를 계산 하 여 행을 반복 하 고,이 `.` 예에서는 모든 행이 처리 된 후에 두 번째 출력에 요약 값을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-179">For example, one of the code examples in this topic overrides ProcessInput to count the number of addresses in a specific city as ProcessInputRow loops through rows`.` The example writes the summary value to the second output after all rows have been processed.</span></span> <span data-ttu-id="9313e-180">PostExecute가 호출되면 출력 버퍼를 더 이상 사용할 수 없으므로 이 예에서는 ProcessInput에서 출력을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-180">The example completes the output in ProcessInput because the output buffers are no longer available when PostExecute is called.</span></span>

 <span data-ttu-id="9313e-181">요구 사항에 따라 ScriptMain 클래스에서 사용할 수 있는 PreExecute 및 PostExecute 메서드에서 스크립트를 작성하여 예비 또는 최종 처리를 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-181">Depending on your requirements, you may also want to write script in the PreExecute and PostExecute methods available in the ScriptMain class to perform any preliminary or final processing.</span></span>

> [!NOTE]
>  <span data-ttu-id="9313e-182">사용자 지정 데이터 흐름 구성 요소를 처음부터 새로 개발하려는 경우에는 나중에 출력 버퍼에 데이터 행을 추가할 수 있도록 PrimeOutput 메서드를 재정의하여 출력 버퍼에 대한 참조를 캐시하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-182">If you were developing a custom data flow component from scratch, it would be important to override the PrimeOutput method to cache references to the output buffers so that you could add rows of data to the buffers later.</span></span> <span data-ttu-id="9313e-183">스크립트 구성 요소에서는 `BufferWrapper` 프로젝트 항목에 각 출력 버퍼를 나타내는 자동 생성 클래스가 있으므로 이 작업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-183">In the Script component, this is not necessary because you have an automatically generated class representing each output buffer in the `BufferWrapper` project item.</span></span>

## <a name="example"></a><span data-ttu-id="9313e-184">예제</span><span class="sxs-lookup"><span data-stu-id="9313e-184">Example</span></span>
 <span data-ttu-id="9313e-185">이 예에서는 ScriptMain 클래스에서 비동기 변환 구성 요소를 만드는 데 필요한 사용자 지정 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-185">This example demonstrates the custom code that is required in the ScriptMain class to create an asynchronous transformation component.</span></span>

> [!NOTE]
>  <span data-ttu-id="9313e-186">이 예에서는 **AdventureWorks** 예제 데이터베이스의 **Person.Address** 테이블을 사용하고 이 테이블의 첫 번째 열과 네 번째 열, **intAddressID** 및 **nvarchar(30)City**를 데이터 흐름을 통해 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-186">These examples use the **Person.Address** table in the **AdventureWorks** sample database and pass its first and fourth columns, the **intAddressID** and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="9313e-187">이 섹션의 원본, 변환 및 대상 예제에는 동일한 데이터가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-187">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="9313e-188">각 예에 대해 필수 구성 요소 및 가정도 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-188">Additional prerequisites and assumptions are documented for each example.</span></span>

 <span data-ttu-id="9313e-189">이 예에서는 두 개의 출력을 사용하는 비동기 변환 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-189">This example demonstrates an asynchronous transformation component with two outputs.</span></span> <span data-ttu-id="9313e-190">이 변환에서는 **AddressID** 및 **City** 열을 한 출력에 전달하고 동시에 특정 도시에 있는 주소의 수를 계산한 다음 이 결과 값을 두 번째 출력에 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-190">This transformation passes through the **AddressID** and **City** columns to one output, while it counts the number of addresses located in a specific city (Redmond, Washington, U.S.A.), and then outputs the resulting value to a second output.</span></span>

 <span data-ttu-id="9313e-191">이 예제 코드를 실행하려면 다음과 같이 패키지와 구성 요소를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-191">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="9313e-192">데이터 흐름 디자이너 화면에 새 스크립트 구성 요소를 추가하고 이 구성 요소를 변환으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-192">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="9313e-193">디자이너에서 원본 또는 다른 변환의 출력을 새 변환 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-193">Connect the output of a source or of another transformation to the new transformation component in the designer.</span></span> <span data-ttu-id="9313e-194">이 출력은 **AdventureWorks** 샘플 데이터베이스에 있는 **Person.Address** 테이블의 데이터를 제공해야 하며, 이 데이터에는 적어도 **AddressID** 및 **City** 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-194">This output should provide data from the **Person.Address** table of the **AdventureWorks** sample database that contains at least the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="9313e-195">**스크립트 변환 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-195">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="9313e-196">**입력 열** 페이지에서 **AddressID** 및 **City** 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-196">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>

4.  <span data-ttu-id="9313e-197">**입/출력** 페이지에서 첫 번째 출력에 **AddressID** 및 **City** 출력 열을 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-197">On the **Inputs and Outputs** page, add and configure the **AddressID** and **City** output columns on the first output.</span></span> <span data-ttu-id="9313e-198">두 번째 출력을 추가하고 이 두 번째 출력에 요약 값에 대한 출력 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-198">Add a second output, and add an output column for the summary value on the second output.</span></span> <span data-ttu-id="9313e-199">이 예에서는 각 입력 행을 첫 번째 출력에 명시적으로 복사하므로 첫 번째 출력의 SynchronousInputID 속성은 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-199">Set the SynchronousInputID property of the first output to 0, because this example copies each input row explicitly to the first output.</span></span> <span data-ttu-id="9313e-200">새로 만든 출력의 SynchronousInputID 속성은 이미 0으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-200">The SynchronousInputID property of the newly-created output is already set to 0.</span></span>

5.  <span data-ttu-id="9313e-201">입력, 출력 및 새 출력 열의 이름을 보다 알기 쉬운 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-201">Rename the input, the outputs, and the new output column to give them more descriptive names.</span></span> <span data-ttu-id="9313e-202">이 예에서는 입력 이름으로 **MyAddressInput**을 사용하고, 출력 이름으로 **MyAddressOutput** 및 **MySummaryOutput**을 사용하며, 두 번째 출력의 출력 열 이름으로는 **MyRedmondCount**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-202">The example uses **MyAddressInput** as the name of the input, **MyAddressOutput** and **MySummaryOutput** for the outputs, and **MyRedmondCount** for the output column on the second output.</span></span>

6.  <span data-ttu-id="9313e-203">**스크립트** 페이지에서 **스크립트 편집**을 클릭하고 다음 스크립트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-203">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="9313e-204">그런 다음 스크립트 개발 환경 및 **스크립트 변환 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-204">Then close the script development environment and the **Script Transformation Editor**.</span></span>

7.  <span data-ttu-id="9313e-205">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상이나 [스크립트 구성 요소를 사용하여 대상 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)에서 보여 준 예제 대상 구성 요소와 같이 **AddressID** 및 **City** 열을 필요로 하는 대상 구성 요소를 첫 번째 출력에 대해 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-205">Create and configure a destination component for the first output that expects the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md), .</span></span> <span data-ttu-id="9313e-206">그런 다음 변환의 첫 번째 출력인 **MyAddressOutput**을 대상 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-206">Then connect the first output of the transformation, **MyAddressOutput**, to the destination component.</span></span> <span data-ttu-id="9313e-207">**AdventureWorks** 데이터베이스에서 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 실행하여 대상 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-207">You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the **AdventureWorks** database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

8.  <span data-ttu-id="9313e-208">두 번째 출력에 대한 다른 대상 구성 요소를 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-208">Create and configure another destination component for the second output.</span></span> <span data-ttu-id="9313e-209">그런 다음 변환의 두 번째 출력인 **MySummaryOutput**을 대상 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-209">Then connect the second output of the transformation, **MySummaryOutput**, to the destination component.</span></span> <span data-ttu-id="9313e-210">두 번째 출력은 단일 값이 있는 단일 행을 쓰므로 단일 열이 있는 새 파일에 연결하는 플랫 파일 연결 관리자를 사용하여 대상을 쉽게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-210">Because the second output writes a single row with a single value, you can easily configure a destination with a Flat File connection manager that connects to a new file that has a single column.</span></span> <span data-ttu-id="9313e-211">이 예에서 이 대상 열의 이름은 **MyRedmondCount**입니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-211">In the example, this destination column is named **MyRedmondCount**.</span></span>

9. <span data-ttu-id="9313e-212">예제를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9313e-212">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Private myRedmondAddressCount As Integer

    Public Overrides Sub CreateNewOutputRows()

        MySummaryOutputBuffer.AddRow()

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInput(ByVal Buffer As MyAddressInputBuffer)

        While Buffer.NextRow()
            MyAddressInput_ProcessInputRow(Buffer)
        End While

        If Buffer.EndOfRowset Then
            MyAddressOutputBuffer.SetEndOfRowset()
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount
            MySummaryOutputBuffer.SetEndOfRowset()
        End If

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        With MyAddressOutputBuffer
            .AddRow()
            .AddressID = Row.AddressID
            .City = Row.City
        End With

        If Row.City.ToUpper = "REDMOND" Then
            myRedmondAddressCount += 1
        End If

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

{
    private int myRedmondAddressCount;

    public override void CreateNewOutputRows()
    {

        MySummaryOutputBuffer.AddRow();

    }

    public override void MyAddressInput_ProcessInput(MyAddressInputBuffer Buffer)
    {

        while (Buffer.NextRow())
        {
            MyAddressInput_ProcessInputRow(Buffer);
        }

        if (Buffer.EndOfRowset())
        {
            MyAddressOutputBuffer.SetEndOfRowset();
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount;
            MySummaryOutputBuffer.SetEndOfRowset();
        }

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        {
            MyAddressOutputBuffer.AddRow();
            MyAddressOutputBuffer.AddressID = Row.AddressID;
            MyAddressOutputBuffer.City = Row.City;
        }

        if (Row.City.ToUpper() == "REDMOND")
        {
            myRedmondAddressCount += 1;
        }

    }

}

```

<span data-ttu-id="9313e-213">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="9313e-213">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9313e-214">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-214">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9313e-215">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-215">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9313e-216">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="9313e-216">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="9313e-217">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9313e-217">See Also</span></span>
 <span data-ttu-id="9313e-218">[동기 및 비동기 변환 이해](../understanding-synchronous-and-asynchronous-transformations.md) [스크립트 구성 요소를 사용 하 여 동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) [비동기 출력을 사용 하 여 사용자 지정 변환 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)</span><span class="sxs-lookup"><span data-stu-id="9313e-218">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) [Developing a Custom Transformation Component with Asynchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)</span></span>


