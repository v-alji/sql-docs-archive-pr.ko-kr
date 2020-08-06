---
title: 스크립트 구성 요소를 사용하여 동기 변환 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: aa1bee1a-ab06-44d8-9944-4bff03d73016
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34252f1caba4e2c1b3b99788d32527a33793b6ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651771"
---
# <a name="creating-a-synchronous-transformation-with-the-script-component"></a><span data-ttu-id="f35b2-102">스크립트 구성 요소를 사용하여 동기 변환 만들기</span><span class="sxs-lookup"><span data-stu-id="f35b2-102">Creating a Synchronous Transformation with the Script Component</span></span>
  <span data-ttu-id="f35b2-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 데이터 흐름에서 변환 구성 요소를 사용하여 데이터가 원본에서 대상으로 전달될 때 데이터를 수정하고 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-103">You use a transformation component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to modify and analyze data as it passes from source to destination.</span></span> <span data-ttu-id="f35b2-104">동기 출력을 사용하는 변환에서는 각 입력 행이 이 구성 요소를 통해 전달될 때 이를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-104">A transformation with synchronous outputs processes each input row as it passes through the component.</span></span> <span data-ttu-id="f35b2-105">그러나 비동기 출력을 사용하는 변환에서는 입력 행을 모두 받을 때까지 기다렸다가 처리를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-105">A transformation with asynchronous outputs waits until it has received all input rows to complete its processing.</span></span> <span data-ttu-id="f35b2-106">이 항목에서는 동기 변환에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-106">This topic discusses a synchronous transformation.</span></span> <span data-ttu-id="f35b2-107">비동기 변환에 대한 자세한 내용은 [스크립트 구성 요소를 사용하여 비동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-107">For information about asynchronous transformations, see [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span> <span data-ttu-id="f35b2-108">동기 구성 요소와 비동기 구성 요소 간의 차이점에 대한 자세한 내용은 [동기 및 비동기 변환 이해](../understanding-synchronous-and-asynchronous-transformations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-108">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="f35b2-109">스크립트 구성 요소에 대한 개요는 [스크립트 구성 요소를 사용하여 데이터 흐름 확장](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-109">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>

 <span data-ttu-id="f35b2-110">스크립트 구성 요소 및 해당 구성 요소가 생성하는 인프라 코드를 사용하면 사용자 지정 데이터 흐름 구성 요소를 개발하는 과정이 훨씬 간단해집니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-110">The Script component and the infrastructure code that it generates for you simplify significantly the process of developing a custom data flow component.</span></span> <span data-ttu-id="f35b2-111">하지만 스크립트 구성 요소의 작동 방식을 이해하려면 [사용자 지정 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) 섹션과 이 섹션의 [동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)에서 사용자 지정 데이터 흐름 구성 요소를 개발하는 데 필요한 단계를 파악하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-111">However, to understand how the Script component works, you may find it useful to read the steps that you must follow in developing a custom data flow component in the section on [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), and especially [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>

## <a name="getting-started-with-a-synchronous-transformation-component"></a><span data-ttu-id="f35b2-112">동기 변환 구성 요소 시작</span><span class="sxs-lookup"><span data-stu-id="f35b2-112">Getting Started with a Synchronous Transformation Component</span></span>
 <span data-ttu-id="f35b2-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 데이터 흐름 창에 스크립트 구성 요소를 추가하면 원본, 대상 또는 변환 구성 요소 유형을 선택하기 위한 **스크립트 구성 요소 유형 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-113">When you add a Script component to the Data Flow pane of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box opens and prompts you to select a Source, Destination, or Transformation component type.</span></span> <span data-ttu-id="f35b2-114">이 대화 상자에서 **변환**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-114">In this dialog box, select **Transformation**.</span></span>

## <a name="configuring-a-synchronous-transformation-component-in-metadata-design-mode"></a><span data-ttu-id="f35b2-115">메타데이터 디자인 모드에서 동기 변환 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="f35b2-115">Configuring a Synchronous Transformation Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="f35b2-116">변환 구성 요소를 만드는 옵션을 선택한 후에는 **스크립트 변환 편집기**를 사용하여 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-116">After you select the option to create a transformation component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="f35b2-117">자세한 내용은 [스크립트 구성 요소 편집기에서 스크립트 구성 요소 구성](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-117">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="f35b2-118">스크립트 구성 요소의 스크립트 언어를 설정하려면 **스크립트 변환 편집기**의 **스크립트** 페이지에서 **ScriptLanguage** 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-118">To set the script language for the Script component, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor**.</span></span>

> [!NOTE]
>  <span data-ttu-id="f35b2-119">스크립트 구성 요소에 대한 기본 스크립트 언어를 설정하려면 **옵션** 대화 상자의 **일반** 페이지에서 **스크립트 언어** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-119">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="f35b2-120">자세한 내용은 [General Page](../general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-120">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="f35b2-121">데이터 흐름 변환 구성 요소는 하나의 입력을 사용하며 하나 이상의 출력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-121">A data flow transformation component has one input, and supports one or more outputs.</span></span> <span data-ttu-id="f35b2-122">구성 요소의 입력과 출력을 구성하는 것은 사용자 지정 스크립트를 작성하기 전에 메타데이터 디자인 모드에서 **스크립트 변환 편집기**를 사용하여 완료해야 하는 단계 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-122">Configuring the input and outputs for the component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="configuring-input-columns"></a><span data-ttu-id="f35b2-123">입력 열 구성</span><span class="sxs-lookup"><span data-stu-id="f35b2-123">Configuring Input Columns</span></span>
 <span data-ttu-id="f35b2-124">변환 구성 요소에서는 하나의 입력을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-124">A transformation component has one input.</span></span>

 <span data-ttu-id="f35b2-125">**스크립트 변환 편집기**의 **입력 열** 페이지에 나타나는 열 목록에는 업스트림 데이터 흐름 구성 요소의 출력에서 가져온 사용 가능한 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-125">On the **Input Columns** page of the **Script Transformation Editor,** the column list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="f35b2-126">이 목록에서 변환하거나 전달할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-126">Select the columns that you want to transform or pass through.</span></span> <span data-ttu-id="f35b2-127">현재 위치에서 변환할 모든 열은 읽기/쓰기로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-127">Mark any columns that you want to transform in place as Read/Write.</span></span>

 <span data-ttu-id="f35b2-128">**스크립트 변환 편집기**의 **입력 열** 페이지에 대한 자세한 내용은 [스크립트 변환 편집기&#40;입력 열 페이지&#41;](../script-transformation-editor-input-columns-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-128">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

### <a name="configuring-inputs-outputs-and-output-columns"></a><span data-ttu-id="f35b2-129">입력, 출력 및 출력 열 구성</span><span class="sxs-lookup"><span data-stu-id="f35b2-129">Configuring Inputs, Outputs, and Output Columns</span></span>
 <span data-ttu-id="f35b2-130">변환 구성 요소는 하나 이상의 출력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-130">A transformation component supports one or more outputs.</span></span>

 <span data-ttu-id="f35b2-131">**스크립트 변환 편집기**의 **입/출력** 페이지에서는 단일 출력이 만들어져 있지만 해당 출력에 열은 없음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-131">On the **Inputs and Outputs** page of the **Script Transformation Editor**, you can see that a single output has been created, but the output has no columns.</span></span> <span data-ttu-id="f35b2-132">편집기의 이 페이지에서 다음과 같은 항목을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-132">On this page of the editor, you may need or want to configure the following items.</span></span>

-   <span data-ttu-id="f35b2-133">예기치 않은 값이 포함된 행에 대한 시뮬레이션된 오류 출력과 같은 추가 출력을 하나 이상 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-133">Create one or more additional outputs, such as a simulated error output for rows that contain unexpected values.</span></span> <span data-ttu-id="f35b2-134">동기 변환 구성 요소의 출력을 관리하려면 **출력 추가** 및 **출력 제거** 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-134">Use the **Add Output** and **Remove Output** buttons to manage the outputs of your synchronous transformation component.</span></span> <span data-ttu-id="f35b2-135">각 행을 한 출력 또는 다른 출력으로 리디렉션하도록 지정하지 않은 경우에는 모든 입력 행이 사용 가능한 모든 출력으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-135">All input rows are directed to all available outputs unless you indicate that you intend to redirect each row to one output or the other.</span></span> <span data-ttu-id="f35b2-136">출력의 `ExclusionGroup` 속성에 0이 아닌 정수 값을 지정하면 행을 리디렉션하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-136">You indicate that you intend to redirect rows by specifying a non-zero integer value for the `ExclusionGroup` property on the outputs.</span></span> <span data-ttu-id="f35b2-137">출력을 식별하기 위해 `ExclusionGroup`에 입력하는 특정 정수 값은 중요하지 않지만 지정한 출력 그룹에는 일관되게 동일한 정수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-137">The specific integer value entered in `ExclusionGroup` to identify the outputs is not significant, but you must use the same integer consistently for the specified group of outputs.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="f35b2-138">모든 행을 출력하지 않으려는 경우 단일 출력과 함께 0이 아닌 `ExclusionGroup` 속성 값을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-138">You can also use a non-zero `ExclusionGroup` property value with a single output when you do not want to output all rows.</span></span> <span data-ttu-id="f35b2-139">그러나 이 경우 출력으로 보낼 각 행에 대해 **DirectRowTo\<outputbuffer>** 메서드를 명시적으로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-139">However, in this case,  you must explicitly call the **DirectRowTo\<outputbuffer>** method for each row that you want to send to the output.</span></span>

-   <span data-ttu-id="f35b2-140">입력 및 출력에 보다 알기 쉬운 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-140">Assign a more descriptive name to the input and outputs.</span></span> <span data-ttu-id="f35b2-141">스크립트 구성 요소에서는 이러한 이름을 사용하여 스크립트에서 입력 및 출력을 참조하는 데 사용할 형식화된 접근자 속성을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-141">The Script component uses these names to generate the typed accessor properties that you will use to refer to the input and outputs in your script.</span></span>

-   <span data-ttu-id="f35b2-142">동기 변환의 경우 열을 현재 상태로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-142">Leave columns as is for synchronous transformations.</span></span> <span data-ttu-id="f35b2-143">일반적으로 동기 변환에서는 데이터 흐름에 열을 추가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-143">Typically a synchronous transformation does not add columns to the data flow.</span></span> <span data-ttu-id="f35b2-144">데이터는 버퍼의 현재 위치에서 수정되고 해당 버퍼는 데이터 흐름의 다음 구성 요소로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-144">Data is modified in place in the buffer, and the buffer is passed on to the next component in the data flow.</span></span> <span data-ttu-id="f35b2-145">이 경우 변환의 출력에서 출력 열을 명시적으로 추가하거나 구성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-145">If this is the case, you do not have to add and configure output columns explicitly on the transformation's outputs.</span></span> <span data-ttu-id="f35b2-146">출력은 편집기에서 명시적으로 정의된 열이 없는 상태로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-146">The outputs appear in the editor without any explicitly defined columns.</span></span>

-   <span data-ttu-id="f35b2-147">행 수준 오류에 대한 시뮬레이션된 오류 출력에 새 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-147">Add new columns to simulated error outputs for row-level errors.</span></span> <span data-ttu-id="f35b2-148">일반적으로 동일한 `ExclusionGroup`의 여러 출력에는 동일한 출력 열 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-148">Ordinarily multiple outputs in the same `ExclusionGroup` have the same set of output columns.</span></span> <span data-ttu-id="f35b2-149">그러나 시뮬레이션된 오류 출력을 만드는 경우 오류 정보를 포함할 다른 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-149">However, if you are creating a simulated error output, you may want to add more columns to contain error information.</span></span> <span data-ttu-id="f35b2-150">데이터 흐름 엔진에서 오류 행을 처리하는 방법은 [데이터 흐름 구성 요소에서 오류 출력 사용](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-150">For information about how the data flow engine processes error rows, see [Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md).</span></span> <span data-ttu-id="f35b2-151">스크립트 구성 요소에서는 개발자가 직접 코드를 작성하여 추가 열을 적절한 오류 정보로 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-151">Note that in the Script component you must write your own code to fill the additional columns with appropriate error information.</span></span> <span data-ttu-id="f35b2-152">자세한 내용은 [스크립트 구성 요소의 오류 출력 시뮬레이션](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-152">For more information, see [Simulating an Error Output for the Script Component](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).</span></span>

 <span data-ttu-id="f35b2-153">**스크립트 변환 편집기**의 **입/출력** 페이지에 대한 자세한 내용은 [스크립트 변환 편집기&#40;입/출력 페이지&#41;](../script-transformation-editor-inputs-and-outputs-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-153">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="f35b2-154">변수 추가</span><span class="sxs-lookup"><span data-stu-id="f35b2-154">Adding Variables</span></span>
 <span data-ttu-id="f35b2-155">스크립트에서 기존 변수를 사용 하려는 경우 스크립트 `ReadOnlyVariables` `ReadWriteVariables` **변환 편집기**의 **스크립트** 페이지에서 및 속성 필드에 해당 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-155">If you want to use existing variables in your script, you can add them in the `ReadOnlyVariables` and `ReadWriteVariables` property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="f35b2-156">속성 필드에 여러 변수를 추가하는 경우 변수 이름을 쉼표로 구분하십시오.</span><span class="sxs-lookup"><span data-stu-id="f35b2-156">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="f35b2-157">및 속성 필드 옆의 줄임표 (**...**) 단추를 클릭 한 `ReadOnlyVariables` `ReadWriteVariables` 다음 **변수 선택** 대화 상자에서 변수를 선택 하 여 여러 개의 변수를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-157">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="f35b2-158">스크립트 구성 요소에서 변수를 사용하는 방법에 대한 일반적인 내용은 [스크립트 구성 요소에서 변수 사용](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-158">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="f35b2-159">**스크립트 변환 편집기**의 **스크립트** 페이지에 대한 자세한 내용은 [스크립트 변환 편집기&#40;스크립트 페이지&#41;](../script-transformation-editor-script-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-159">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-a-synchronous-transformation-component-in-code-design-mode"></a><span data-ttu-id="f35b2-160">코드 디자인 모드에서 동기 변환 구성 요소 스크립팅</span><span class="sxs-lookup"><span data-stu-id="f35b2-160">Scripting a Synchronous Transformation Component in Code-Design Mode</span></span>
 <span data-ttu-id="f35b2-161">구성 요소에 대한 메타데이터를 구성한 후에는 사용자 지정 스크립트를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-161">After you have configured the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="f35b2-162">**스크립트 변환 편집기**의 **스크립트** 페이지에서 **스크립트 편집**을 클릭하여 사용자 지정 스크립트를 추가할 수 있는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications) IDE를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-162">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="f35b2-163">사용하는 스크립트 언어는 **스크립트** 페이지에서 **ScriptLanguage** 속성에 대한 스크립트 언어로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 중에서 선택한 언어에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-163">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="f35b2-164">스크립트 구성 요소를 사용하여 만든 모든 종류의 구성 요소에 적용되는 중요한 정보는 [스크립트 구성 요소 코딩 및 디버깅](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-164">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="f35b2-165">자동 생성 코드 이해</span><span class="sxs-lookup"><span data-stu-id="f35b2-165">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="f35b2-166">변환 구성 요소를 만들고 구성한 후 VSTA IDE를 열면 편집 가능한 `ScriptMain` 클래스가 `ProcessInputRow` 메서드에 대한 스텁과 함께 코드 편집기에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-166">When you open the VSTA IDE after you create and configuring a transformation component, the editable `ScriptMain` class appears in the code editor with a stub for the `ProcessInputRow` method.</span></span> <span data-ttu-id="f35b2-167">이 `ScriptMain` 클래스에서 사용자 지정 코드를 작성해야 하며 `ProcessInputRow`는 변환 구성 요소에서 가장 중요한 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-167">The `ScriptMain` class is where you will write your custom code, and `ProcessInputRow` is the most important method in a transformation component.</span></span>

 <span data-ttu-id="f35b2-168">VSTA에서 **프로젝트 탐색기** 창을 열면 스크립트 구성 요소가 읽기 전용 `BufferWrapper` 및 프로젝트 항목도 생성 한 것을 볼 수 있습니다 `ComponentWrapper` .</span><span class="sxs-lookup"><span data-stu-id="f35b2-168">If you open the **Project Explorer** window in VSTA, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="f35b2-169">`ScriptMain` 클래스는 `UserComponent` 프로젝트 항목의 `ComponentWrapper` 클래스에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-169">The `ScriptMain` class inherits from the `UserComponent` class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="f35b2-170">런타임에 데이터 흐름 엔진은 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> 부모 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 메서드를 재정의하는 `ProcessInput` 클래스의 `UserComponent` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-170">At run time, the data flow engine invokes the `ProcessInput` method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="f35b2-171">그러면 `ProcessInput` 메서드는 입력 버퍼의 행을 반복하고 각 행에 대해 `ProcessInputRow` 메서드를 한 번씩 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-171">The `ProcessInput` method in turn loops through the rows in the input buffer and calls the `ProcessInputRow` method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="f35b2-172">사용자 지정 코드 작성</span><span class="sxs-lookup"><span data-stu-id="f35b2-172">Writing Your Custom Code</span></span>
 <span data-ttu-id="f35b2-173">동기 출력을 사용하는 변환 구성 요소는 모든 데이터 흐름 구성 요소 중에서 작성하기가 가장 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-173">A transformation component with synchronous outputs is the simplest of all data flow components to write.</span></span> <span data-ttu-id="f35b2-174">예를 들어 이 항목의 뒷부분에 있는 단일 출력 예는 다음과 같은 사용자 지정 코드로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-174">For example, the single-output example shown later in this topic consists of the following custom code:</span></span>

```vb
Row.City = UCase(Row.City)
```

```csharp
Row.City = (Row.City).ToUpper();

```

 <span data-ttu-id="f35b2-175">사용자 지정 동기 변환 구성 요소 만들기를 마치려면 재정의된 `ProcessInputRow` 메서드를 사용하여 입력 버퍼의 각 행에 있는 데이터를 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-175">To finish creating a custom synchronous transformation component, you use the overridden `ProcessInputRow` method to transform the data in each row of the input buffer.</span></span> <span data-ttu-id="f35b2-176">데이터 흐름 엔진에서는 이 버퍼가 가득 차면 데이터 흐름의 다음 구성 요소로 버퍼를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-176">The data flow engine passes this buffer, when full, to the next component in the data flow.</span></span>

 <span data-ttu-id="f35b2-177">개발자의 요구 사항에 따라 `PreExecute` 클래스에서 사용할 수 있는 `PostExecute` 및 `ScriptMain` 메서드에서 스크립트를 작성하여 예비 또는 최종 처리를 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-177">Depending on your requirements, you may also want to write script in the `PreExecute` and `PostExecute` methods, available in the `ScriptMain` class, to perform preliminary or final processing.</span></span>

### <a name="working-with-multiple-outputs"></a><span data-ttu-id="f35b2-178">여러 출력 작업</span><span class="sxs-lookup"><span data-stu-id="f35b2-178">Working with Multiple Outputs</span></span>
 <span data-ttu-id="f35b2-179">입력 행을 둘 이상의 가능한 출력 중 하나로 전송하는 데 필요한 사용자 지정 코드는 앞에서 설명한 단일 출력을 사용하는 경우보다 그다지 많지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-179">Directing input rows to one of two or more possible outputs does not require much more custom code than the single-output scenario discussed earlier.</span></span> <span data-ttu-id="f35b2-180">예를 들어 이 항목의 뒷부분에 있는 두 개의 출력을 사용하는 예는 다음과 같은 사용자 지정 코드로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-180">For example, the two-output example shown later in this topic consists of the following custom code:</span></span>

```vb
Row.City = UCase(Row.City)
If Row.City = "REDMOND" Then
    Row.DirectRowToMyRedmondAddresses()
Else
    Row.DirectRowToMyOtherAddresses()
End If
```

```csharp
Row.City = (Row.City).ToUpper();

if (Row.City=="REDMOND")
{
    Row.DirectRowToMyRedmondAddresses();
}
else
{
    Row.DirectRowToMyOtherAddresses();
}
```

 <span data-ttu-id="f35b2-181">이 예에서 스크립트 구성 요소는 개발자가 구성한 출력의 이름을 따라 **DirectRowTo\<OutputBufferX>** 메서드를 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-181">In this example, the Script component generates the **DirectRowTo\<OutputBufferX>** methods for you, based on the names of the outputs that you configured.</span></span> <span data-ttu-id="f35b2-182">비슷한 코드를 사용하여 오류 출력을 시뮬레이션된 오류 출력으로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-182">You can use similar code to direct error rows to a simulated error output.</span></span>

## <a name="examples"></a><span data-ttu-id="f35b2-183">예</span><span class="sxs-lookup"><span data-stu-id="f35b2-183">Examples</span></span>
 <span data-ttu-id="f35b2-184">이 예에서는 `ScriptMain` 클래스에서 동기 변환 구성 요소를 만드는 데 필요한 사용자 지정 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-184">The examples here demonstrate the custom code that is required in the `ScriptMain` class to create a synchronous transformation component.</span></span>

> [!NOTE]
>  <span data-ttu-id="f35b2-185">이 예에서는 예제 데이터베이스의 **Person. Address** 테이블을 사용 `AdventureWorks` 하 여 데이터 흐름을 통해 첫 번째 및 네 번째 열인 **intaddressid** 와 **nvarchar (30) City** 열을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-185">These examples use the **Person.Address** table in the `AdventureWorks` sample database and pass its first and fourth columns, the **intAddressID** and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="f35b2-186">이 섹션의 원본, 변환 및 대상 예제에는 동일한 데이터가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-186">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="f35b2-187">각 예에 대해 필수 구성 요소 및 가정도 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-187">Additional prerequisites and assumptions are documented for each example.</span></span>

### <a name="single-output-synchronous-transformation-example"></a><span data-ttu-id="f35b2-188">단일 출력 동기 변환 예</span><span class="sxs-lookup"><span data-stu-id="f35b2-188">Single Output Synchronous Transformation Example</span></span>
 <span data-ttu-id="f35b2-189">이 예에서는 단일 출력을 사용하는 동기 변환 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-189">This example demonstrates a synchronous transformation component with a single output.</span></span> <span data-ttu-id="f35b2-190">이 변환에서는 **AddressID** 열을 전달하고 **City** 열을 대문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-190">This transformation passes through the **AddressID** column and converts the **City** column to uppercase.</span></span>

 <span data-ttu-id="f35b2-191">이 예제 코드를 실행하려면 다음과 같이 패키지와 구성 요소를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-191">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="f35b2-192">데이터 흐름 디자이너 화면에 새 스크립트 구성 요소를 추가하고 이 구성 요소를 변환으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-192">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="f35b2-193">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 원본 또는 다른 변환의 출력을 새 변환 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-193">Connect the output of a source or of another transformation to the new transformation component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="f35b2-194">이 출력은 **Person.Address** `AdventureWorks` **addressid** 및 **City** 열이 포함 된 예제 데이터베이스의 Person. Address 테이블에서 데이터를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-194">This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="f35b2-195">**스크립트 변환 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-195">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="f35b2-196">**입력 열** 페이지에서 **AddressID** 및 **City** 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-196">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span> <span data-ttu-id="f35b2-197">**City** 열을 읽기/쓰기로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-197">Mark the **City** column as Read/Write.</span></span>

4.  <span data-ttu-id="f35b2-198">**입/출력** 페이지에서 입력 및 출력의 이름을 **MyAddressInput** 및 **MyAddressOutput**과 같이 보다 알기 쉬운 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-198">On the **Inputs and Outputs** page, rename the input and output with more descriptive names, such as **MyAddressInput** and **MyAddressOutput**.</span></span> <span data-ttu-id="f35b2-199">출력의 `SynchronousInputID`는 입력의 `ID`에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-199">Notice that the `SynchronousInputID` of the output corresponds to the `ID` of the input.</span></span> <span data-ttu-id="f35b2-200">따라서 출력 열을 추가하고 구성하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-200">Therefore you do not have to add and configure output columns.</span></span>

5.  <span data-ttu-id="f35b2-201">**스크립트** 페이지에서 **스크립트 편집**을 클릭하고 다음 스크립트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-201">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="f35b2-202">그런 다음 스크립트 개발 환경 및 **스크립트 변환 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-202">Then close the script development environment and the **Script Transformation Editor**.</span></span>

6.  <span data-ttu-id="f35b2-203">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상이나 [스크립트 구성 요소를 사용하여 대상 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)에서 보여 준 예제 대상 구성 요소와 같이 **AddressID** 및 **City** 열을 필요로 하는 대상 구성 요소를 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-203">Create and configure a destination component that expects the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="f35b2-204">그런 다음 변환의 출력을 대상 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-204">Then connect the output of the transformation to the destination component.</span></span> <span data-ttu-id="f35b2-205">[!INCLUDE[tsql](../../includes/tsql-md.md)] 데이터베이스에서 다음 `AdventureWorks` 명령을 실행하여 대상 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-205">You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

7.  <span data-ttu-id="f35b2-206">예제를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-206">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        Row.City = UCase(Row.City)

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

{
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        Row.City = (Row.City).ToUpper();

    }

}
```

### <a name="two-output-synchronous-transformation-example"></a><span data-ttu-id="f35b2-207">두 개의 출력을 사용하는 동기 변환 예</span><span class="sxs-lookup"><span data-stu-id="f35b2-207">Two-Output Synchronous Transformation Example</span></span>
 <span data-ttu-id="f35b2-208">이 예에서는 두 개의 출력을 사용하는 동기 변환 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-208">This example demonstrates a synchronous transformation component with two outputs.</span></span> <span data-ttu-id="f35b2-209">이 변환에서는 **AddressID** 열을 전달하고 **City** 열을 대문자로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-209">This transformation passes through the **AddressID** column and converts the **City** column to uppercase.</span></span> <span data-ttu-id="f35b2-210">도시 이름이 Redmond이면 해당 행은 한 출력으로 전송되고 다른 모든 행은 다른 출력으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-210">If the city name is Redmond, it directs the row to one output; it directs all other rows to another output.</span></span>

 <span data-ttu-id="f35b2-211">이 예제 코드를 실행하려면 다음과 같이 패키지와 구성 요소를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-211">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="f35b2-212">데이터 흐름 디자이너 화면에 새 스크립트 구성 요소를 추가하고 이 구성 요소를 변환으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-212">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="f35b2-213">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 원본 또는 다른 변환의 출력을 새 변환 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-213">Connect the output of a source or of another transformation to the new transformation component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="f35b2-214">이 출력은 **Person.Address** `AdventureWorks` 적어도 **addressid** 및 **City** 열이 포함 된 예제 데이터베이스의 Person. Address 테이블에서 데이터를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-214">This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains at least the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="f35b2-215">**스크립트 변환 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-215">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="f35b2-216">**입력 열** 페이지에서 **AddressID** 및 **City** 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-216">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span> <span data-ttu-id="f35b2-217">**City** 열을 읽기/쓰기로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-217">Mark the **City** column as Read/Write.</span></span>

4.  <span data-ttu-id="f35b2-218">**입/출력** 페이지에서 두 번째 출력을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-218">On the **Inputs and Outputs** page, create a second output.</span></span> <span data-ttu-id="f35b2-219">새 출력을 추가한 후에는 해당 `SynchronousInputID`를 입력의 `ID`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-219">After you add the new output, make sure that you set its `SynchronousInputID` to the `ID` of the input.</span></span> <span data-ttu-id="f35b2-220">기본적으로 만들어진 첫 번째 출력에는 이 속성이 이미 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-220">This property is already set on the first output, which is created by default.</span></span> <span data-ttu-id="f35b2-221">상호 배타적인 두 개의 출력 간에 입력 행을 분리하려면 각 출력에 대해 `ExclusionGroup` 속성을 0이 아닌 동일한 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-221">For each output, set the `ExclusionGroup` property to the same non-zero value to indicate that you will split the input rows between two mutually exclusive outputs.</span></span> <span data-ttu-id="f35b2-222">출력에 출력 열을 추가할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-222">You do not have to add any output columns to the outputs.</span></span>

5.  <span data-ttu-id="f35b2-223">입력 및 출력 이름을 **MyAddressInput**, **MyRedmondAddresses** 및 **MyOtherAddresses**와 같이 보다 알기 쉬운 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-223">Rename the input and outputs with more descriptive names, such as **MyAddressInput**, **MyRedmondAddresses**, and **MyOtherAddresses**.</span></span>

6.  <span data-ttu-id="f35b2-224">**스크립트** 페이지에서 **스크립트 편집**을 클릭하고 다음 스크립트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-224">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="f35b2-225">그런 다음 스크립트 개발 환경 및 **스크립트 변환 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-225">Then close the script development environment and the **Script Transformation Editor**.</span></span>

7.  <span data-ttu-id="f35b2-226">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상, 플랫 파일 대상 또는 [스크립트 구성 요소를 사용하여 대상 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)에서 보여 준 예제 대상 구성 요소와 같이 **AddressID** 및 **City** 열을 필요로 하는 두 개의 대상 구성 요소를 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-226">Create and configure two destination components that expect the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, a Flat File destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="f35b2-227">그런 다음 변환의 각 출력을 대상 구성 요소 중 하나에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-227">Then connect each of the outputs of the transformation to one of the destination components.</span></span> <span data-ttu-id="f35b2-228">`AdventureWorks` 데이터베이스에서 다음과 같이 고유한 테이블 이름으로 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 실행하여 대상 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-228">You can create destination tables by running a [!INCLUDE[tsql](../../includes/tsql-md.md)] command similar to the following (with unique table names) in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2](
        [AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL
    ```

8.  <span data-ttu-id="f35b2-229">예제를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f35b2-229">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        Row.City = UCase(Row.City)

        If Row.City = "REDMOND" Then
            Row.DirectRowToMyRedmondAddresses()
        Else
            Row.DirectRowToMyOtherAddresses()
        End If

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        Row.City = (Row.City).ToUpper();

        if (Row.City == "REDMOND")
        {
            Row.DirectRowToMyRedmondAddresses();
        }
        else
        {
            Row.DirectRowToMyOtherAddresses();
        }

    }
}
```

<span data-ttu-id="f35b2-230">|![](./media/creating-a-synchronous-transformation-with-the-script-component/dts-16.gif)  **최신 상태 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="f35b2-230">|![](./media/creating-a-synchronous-transformation-with-the-script-component/dts-16.gif)  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f35b2-231">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/msconame-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-231">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/msconame-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f35b2-232">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-232">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f35b2-233">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="f35b2-233">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="f35b2-234">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f35b2-234">See Also</span></span>
 <span data-ttu-id="f35b2-235">[동기 및 비동기 변환 이해](../understanding-synchronous-and-asynchronous-transformations.md) [스크립트 구성 요소를 사용 하 여 비동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md) [동기 출력을 사용 하 여 사용자 지정 변환 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)</span><span class="sxs-lookup"><span data-stu-id="f35b2-235">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md) [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)</span></span>


