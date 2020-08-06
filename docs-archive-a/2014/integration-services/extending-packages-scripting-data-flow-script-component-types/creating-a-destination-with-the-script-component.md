---
title: 스크립트 구성 요소를 사용하여 대상 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], destination components
- destinations [Integration Services], components
- input columns [Integration Services]
ms.assetid: 214e22e8-7e7d-4876-b690-c138e5721b81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1245dde111b24d1c37e2c5550d236c97126ee725
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652955"
---
# <a name="creating-a-destination-with-the-script-component"></a><span data-ttu-id="18a3a-102">스크립트 구성 요소를 사용하여 대상 만들기</span><span class="sxs-lookup"><span data-stu-id="18a3a-102">Creating a Destination with the Script Component</span></span>
  <span data-ttu-id="18a3a-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 데이터 흐름에서 대상 구성 요소를 사용하여 업스트림 원본 및 변환에서 받은 데이터를 데이터 원본에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-103">You use a destination component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to save data received from upstream sources and transformations to a data source.</span></span> <span data-ttu-id="18a3a-104">일반적으로 대상 구성 요소는 기존 연결 관리자를 통해 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-104">Ordinarily the destination component connects to the data source through an existing connection manager.</span></span>

 <span data-ttu-id="18a3a-105">스크립트 구성 요소에 대 한 개요를 보려면 [스크립트 구성 요소를 사용 하 여 데이터 흐름 확장] (. /extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="18a3a-105">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span></span>

 <span data-ttu-id="18a3a-106">스크립트 구성 요소 및 해당 구성 요소가 생성하는 인프라 코드를 사용하면 사용자 지정 데이터 흐름 구성 요소를 개발하는 과정이 훨씬 간단해집니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-106">The Script component and the infrastructure code that it generates for you simplify significantly the process of developing a custom data flow component.</span></span> <span data-ttu-id="18a3a-107">그러나 스크립트 구성 요소의 작동 방식을 이해하려면 [사용자 지정 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) 섹션, 특히 [사용자 지정 대상 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)에서 사용자 지정 데이터 흐름 구성 요소를 개발하는 단계를 파악하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-107">However, to understand how the Script component works, you may find it useful to read through the steps for developing a custom data flow components in the [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) section, and especially [Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md).</span></span>

## <a name="getting-started-with-a-destination-component"></a><span data-ttu-id="18a3a-108">대상 구성 요소 시작</span><span class="sxs-lookup"><span data-stu-id="18a3a-108">Getting Started with a Destination Component</span></span>
 <span data-ttu-id="18a3a-109">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 [데이터 흐름] 탭에 스크립트 구성 요소를 추가하면, **스크립트 구성 요소 유형 선택** 대화 상자가 열려 **원본**, **대상** 또는 **변환** 스크립트를 선택하도록 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-109">When you add a Script component to the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box opens and prompts you to select a **Source**, **Destination**, or **Transformation** script.</span></span> <span data-ttu-id="18a3a-110">이 대화 상자에서 **대상**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-110">In this dialog box, select **Destination**.</span></span>

 <span data-ttu-id="18a3a-111">그런 다음 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 변환의 출력을 대상 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-111">Next, connect the output of a transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="18a3a-112">테스트를 위해 변환하지 않고 원본을 대상에 직접 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-112">For testing, you can connect a source directly to a destination without any transformations.</span></span>

## <a name="configuring-a-destination-component-in-metadata-design-mode"></a><span data-ttu-id="18a3a-113">메타데이터 디자인 모드에서 대상 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="18a3a-113">Configuring a Destination Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="18a3a-114">대상 구성 요소를 만드는 옵션을 선택한 후 **스크립트 변환 편집기**를 사용하여 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-114">After you select the option to create a destination component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="18a3a-115">자세한 내용은 [스크립트 구성 요소 편집기에서 스크립트 구성 요소 구성](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-115">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="18a3a-116">스크립트 대상에서 사용할 스크립트 언어를 선택하려면 **스크립트 변환 편집기** 대화 상자의 **스크립트** 페이지에서 **ScriptLanguage** 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-116">To select the script language that the Script destination will use, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor** dialog box.</span></span>

> [!NOTE]
>  <span data-ttu-id="18a3a-117">스크립트 구성 요소에 대한 기본 스크립트 언어를 설정하려면 **옵션** 대화 상자의 **일반** 페이지에서 **스크립트 언어** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-117">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="18a3a-118">자세한 내용은 [General Page](../general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-118">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="18a3a-119">데이터 흐름 대상 구성 요소에는 하나의 입력이 포함되며 출력은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-119">A data flow destination component has one input and no outputs.</span></span> <span data-ttu-id="18a3a-120">구성 요소에 대한 입력 구성은 사용자 지정 스크립트를 작성하기 전에 **스크립트 변환 편집기**를 사용하여 메타데이터 디자인 모드에서 완료해야 하는 단계 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-120">Configuring the input for the component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="adding-connection-managers"></a><span data-ttu-id="18a3a-121">연결 관리자 추가</span><span class="sxs-lookup"><span data-stu-id="18a3a-121">Adding Connection Managers</span></span>
 <span data-ttu-id="18a3a-122">일반적으로 대상 구성 요소는 기존 연결 관리자를 사용하여 데이터 흐름에서 받은 데이터를 저장할 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-122">Ordinarily a destination component uses an existing connection manager to connect to the data source to which it saves data from the data flow.</span></span> <span data-ttu-id="18a3a-123">**스크립트 변환 편집기**의 **연결 관리자** 페이지에서 **추가**를 클릭하여 적절한 연결 관리자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-123">On the **Connection Managers** page of the **Script Transformation Editor**, click **Add** to add the appropriate connection manager.</span></span>

 <span data-ttu-id="18a3a-124">그러나 연결 관리자는 단지 특정 유형의 데이터 원본에 연결하는 데 필요한 정보를 캡슐화하고 저장하는 편리한 단위일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-124">However, a connection manager is just a convenient unit that encapsulates and stores the information that is required to connect to a data source of a particular type.</span></span> <span data-ttu-id="18a3a-125">데이터를 로드하거나 저장하고 데이터 원본에 대한 연결을 열고 닫는 사용자 지정 코드는 사용자가 직접 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-125">You must write your own custom code to load or save your data, and possibly to open and close the connection to the data source.</span></span>

 <span data-ttu-id="18a3a-126">스크립트 구성 요소에서 연결 관리자를 사용하는 방법에 대한 일반적은 내용은 [스크립트 구성 요소에서 데이터 원본에 연결](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-126">For general information about how to use connection managers with the Script component, see [Connecting to Data Sources in the Script Component](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).</span></span>

 <span data-ttu-id="18a3a-127">**스크립트 변환 편집기**의 **연결 관리자** 페이지에 대한 자세한 내용은 [스크립트 변환 편집기&#40;연결 관리자 페이지&#41;](../script-transformation-editor-connection-managers-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-127">For more information about the **Connection Managers** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Connection Managers Page&#41;](../script-transformation-editor-connection-managers-page.md).</span></span>

### <a name="configuring-inputs-and-input-columns"></a><span data-ttu-id="18a3a-128">입력 및 입력 열 구성</span><span class="sxs-lookup"><span data-stu-id="18a3a-128">Configuring Inputs and Input Columns</span></span>
 <span data-ttu-id="18a3a-129">대상 구성 요소에는 하나의 입력이 포함되며 출력은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-129">A destination component has one input and no outputs.</span></span>

 <span data-ttu-id="18a3a-130">**스크립트 변환 편집기**의 **입력 열** 페이지에서 열 목록에는 데이터 흐름에 있는 업스트림 구성 요소의 출력에서 사용 가능한 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-130">On the **Input Columns** page of the **Script Transformation Editor**, the column list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="18a3a-131">이 목록에서 저장할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-131">Select the columns that you want to save.</span></span>

 <span data-ttu-id="18a3a-132">**스크립트 변환 편집기**의 **입력 열** 페이지에 대한 자세한 내용은 [스크립트 변환 편집기&#40;입력 열 페이지&#41;](../script-transformation-editor-input-columns-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-132">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

 <span data-ttu-id="18a3a-133">**스크립트 변환 편집기**의 **입/출력** 페이지에는 이름을 바꿀 수 있는 단일 입력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-133">The **Inputs and Outputs** page of the **Script Transformation Editor** shows a single input, which you can rename.</span></span> <span data-ttu-id="18a3a-134">스크립트에서는 자동 생성 코드에서 만들어진 접근자 속성을 사용하여 입력을 이름으로 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-134">You will refer to the input by its name in your script by using the accessor property created in the auto-generated code.</span></span>

 <span data-ttu-id="18a3a-135">**스크립트 변환 편집기**의 **입/출력** 페이지에 대한 자세한 내용은 [스크립트 변환 편집기&#40;입/출력 페이지&#41;](../script-transformation-editor-inputs-and-outputs-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-135">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="18a3a-136">변수 추가</span><span class="sxs-lookup"><span data-stu-id="18a3a-136">Adding Variables</span></span>
 <span data-ttu-id="18a3a-137">스크립트에서 기존 변수를 사용 하려는 경우 스크립트 `ReadOnlyVariables` `ReadWriteVariables` **변환 편집기**의 **스크립트** 페이지에서 및 속성 필드에 해당 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-137">If you want to use existing variables in your script, you can add them in the `ReadOnlyVariables` and `ReadWriteVariables` property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="18a3a-138">속성 필드에 여러 변수를 추가하는 경우 변수 이름을 쉼표로 구분하십시오.</span><span class="sxs-lookup"><span data-stu-id="18a3a-138">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="18a3a-139">및 속성 필드 옆의 줄임표 (**...**) 단추를 클릭 한 `ReadOnlyVariables` `ReadWriteVariables` 다음 **변수 선택** 대화 상자에서 변수를 선택 하 여 여러 개의 변수를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-139">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="18a3a-140">스크립트 구성 요소에서 변수를 사용하는 방법에 대한 일반적인 내용은 [스크립트 구성 요소에서 변수 사용](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-140">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="18a3a-141">**스크립트 변환 편집기**의 **스크립트** 페이지에 대한 자세한 내용은 [스크립트 변환 편집기&#40;스크립트 페이지&#41;](../script-transformation-editor-script-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-141">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-a-destination-component-in-code-design-mode"></a><span data-ttu-id="18a3a-142">코드 디자인 모드에서 대상 구성 요소 스크립팅</span><span class="sxs-lookup"><span data-stu-id="18a3a-142">Scripting a Destination Component in Code-Design Mode</span></span>
 <span data-ttu-id="18a3a-143">구성 요소에 대한 메타데이터를 구성한 후에는 사용자 지정 스크립트를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-143">After you have configured the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="18a3a-144">**스크립트 변환 편집기**의 **스크립트** 페이지에서 **스크립트 편집**을 클릭하여 사용자 지정 스크립트를 추가할 수 있는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications) IDE를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-144">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="18a3a-145">사용하는 스크립트 언어는 **스크립트** 페이지에서 **ScriptLanguage** 속성에 대한 스크립트 언어로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 중에서 선택한 언어에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-145">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="18a3a-146">스크립트 구성 요소를 사용하여 만든 모든 종류의 구성 요소에 적용되는 중요한 정보는 [스크립트 구성 요소 코딩 및 디버깅](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-146">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="18a3a-147">자동 생성 코드 이해</span><span class="sxs-lookup"><span data-stu-id="18a3a-147">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="18a3a-148">대상 구성 요소를 만들고 구성한 후 VSTA IDE를 열면 편집 가능한 `ScriptMain` 클래스가 `ProcessInputRow` 메서드에 대한 스텁과 함께 코드 편집기에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-148">When you open the VSTA IDE after you create and configuring a destination component, the editable `ScriptMain` class appears in the code editor with a stub for the `ProcessInputRow` method.</span></span> <span data-ttu-id="18a3a-149">이 `ScriptMain` 클래스에서 사용자 지정 코드를 작성해야 하며 `ProcessInputRow`는 대상 구성 요소에서 가장 중요한 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-149">The `ScriptMain` class is where you will write your custom code, and `ProcessInputRow` is the most important method in a destination component.</span></span>

 <span data-ttu-id="18a3a-150">VSTA에서 **프로젝트 탐색기** 창을 열면 스크립트 구성 요소가 읽기 전용 `BufferWrapper` 및 프로젝트 항목도 생성 한 것을 볼 수 있습니다 `ComponentWrapper` .</span><span class="sxs-lookup"><span data-stu-id="18a3a-150">If you open the **Project Explorer** window in VSTA, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="18a3a-151">`ScriptMain` 클래스는 `UserComponent` 프로젝트 항목의 `ComponentWrapper` 클래스에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-151">The `ScriptMain` class inherits from `UserComponent` class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="18a3a-152">런타임에 데이터 흐름 엔진은 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> 부모 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 메서드를 재정의하는 `ProcessInput` 클래스의 `UserComponent` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-152">At run time, the data flow engine invokes the `ProcessInput` method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="18a3a-153">그러면 `ProcessInput` 메서드는 입력 버퍼의 행을 반복하고 각 행에 대해 `ProcessInputRow` 메서드를 한 번씩 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-153">The `ProcessInput` method in turn loops through the rows in the input buffer and calls the `ProcessInputRow` method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="18a3a-154">사용자 지정 코드 작성</span><span class="sxs-lookup"><span data-stu-id="18a3a-154">Writing Your Custom Code</span></span>
 <span data-ttu-id="18a3a-155">사용자 지정 대상 구성 요소 만들기를 마치기 위해 `ScriptMain` 클래스에서 사용할 수 있는 다음 메서드에서 스크립트를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-155">To finish creating a custom destination component, you may want to write script in the following methods available in the `ScriptMain` class.</span></span>

1.  <span data-ttu-id="18a3a-156">`AcquireConnections` 메서드를 재정의하여 외부 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-156">Override the `AcquireConnections` method to connect to the external data source.</span></span> <span data-ttu-id="18a3a-157">연결 관리자에서 연결 개체나 필요한 연결 정보를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-157">Extract the connection object, or the required connection information, from the connection manager.</span></span>

2.  <span data-ttu-id="18a3a-158">`PreExecute` 메서드를 재정의하여 데이터를 저장하기 위한 준비를 합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-158">Override the `PreExecute` method to prepare to save the data.</span></span> <span data-ttu-id="18a3a-159">예를 들어 이 메서드에서 `SqlCommand`와 해당 매개 변수를 만들고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-159">For example, you may want to create and configure a `SqlCommand` and its parameters in this method.</span></span>

3.  <span data-ttu-id="18a3a-160">재정의된 `ProcessInputRow` 메서드를 사용하여 각 입력 행을 외부 데이터 원본에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-160">Use the overridden `ProcessInputRow` method to copy each input row to the external data source.</span></span> <span data-ttu-id="18a3a-161">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상의 경우 열 값을 `SqlCommand`의 매개 변수에 복사하고 각 행에 대해 이 명령을 한 번씩 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-161">For example, for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, you can copy the column values into the parameters of a `SqlCommand` and execute the command one time for each row.</span></span> <span data-ttu-id="18a3a-162">플랫 파일 대상의 경우 각 열의 값을 열 구분 기호로 구분하여 `StreamWriter`에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-162">For a flat file destination, you can write the values for each column to a `StreamWriter`, separating the values by the column delimiter.</span></span>

4.  <span data-ttu-id="18a3a-163">`PostExecute` 메서드를 재정의하여 필요할 경우 외부 데이터 원본과의 연결을 끊고 그 밖에 필요한 정리 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-163">Override the `PostExecute` method to disconnect from the external data source, if required, and to perform any other required cleanup.</span></span>

## <a name="examples"></a><span data-ttu-id="18a3a-164">예</span><span class="sxs-lookup"><span data-stu-id="18a3a-164">Examples</span></span>
 <span data-ttu-id="18a3a-165">다음 예에서는 `ScriptMain` 클래스에서 대상 구성 요소를 만드는 데 필요한 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-165">The examples that follow demonstrate code that is required in the `ScriptMain` class to create a destination component.</span></span>

> [!NOTE]
>  <span data-ttu-id="18a3a-166">이 예에서는 예제 데이터베이스의 **Person. Address** 테이블을 사용 `AdventureWorks` 하 여 데이터 흐름을 통해 첫 번째 및 네 번째 열인 **int \* addressid**\* 및 **nvarchar (30) City** 열을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-166">These examples use the **Person.Address** table in the `AdventureWorks` sample database and pass its first and fourth columns, the **int\*AddressID**\* and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="18a3a-167">이 섹션의 원본, 변환 및 대상 예제에는 동일한 데이터가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-167">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="18a3a-168">각 예에 대해 필수 구성 요소 및 가정도 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-168">Additional prerequisites and assumptions are documented for each example.</span></span>

### <a name="adonet-destination-example"></a><span data-ttu-id="18a3a-169">ADO.NET 대상 예</span><span class="sxs-lookup"><span data-stu-id="18a3a-169">ADO.NET Destination Example</span></span>
 <span data-ttu-id="18a3a-170">이 예제에서는 기존 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자를 사용하여 데이터 흐름의 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 저장하는 대상 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-170">This example demonstrates a destination component that uses an existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to save data from the data flow into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>

 <span data-ttu-id="18a3a-171">이 예제 코드를 실행하려면 다음과 같이 패키지와 구성 요소를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-171">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="18a3a-172">`SqlClient` 공급자를 사용하여 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 데이터베이스에 연결하는 `AdventureWorks` 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-172">Create an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the `SqlClient` provider to connect to the `AdventureWorks` database.</span></span>

2.  <span data-ttu-id="18a3a-173">`AdventureWorks` 데이터베이스에서 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 실행하여 대상 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-173">Create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

3.  <span data-ttu-id="18a3a-174">데이터 흐름 디자이너 화면에 새 스크립트 구성 요소를 추가하고 이 구성 요소를 대상으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-174">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>

4.  <span data-ttu-id="18a3a-175">업스트림 원본 또는 변환의 출력을 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 대상 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-175">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="18a3a-176">변환을 사용 하지 않고 소스를 대상에 직접 연결할 수 있습니다. 이 출력은 **Person.Address** `AdventureWorks` 적어도 **addressid** 및 **City** 열이 포함 된 예제 데이터베이스의 Person. Address 테이블에서 데이터를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-176">(You can connect a source directly to a destination without any transformations.) This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains at least the **AddressID** and **City** columns.</span></span>

5.  <span data-ttu-id="18a3a-177">**스크립트 변환 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-177">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="18a3a-178">**입력 열** 페이지에서 **AddressID** 및 **City** 입력 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-178">On the **Input Columns** page, select the **AddressID** and **City** input columns.</span></span>

6.  <span data-ttu-id="18a3a-179">**입/출력** 페이지에서 입력의 이름을 **MyAddressInput**과 같이 더 알기 쉬운 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-179">On the **Inputs and Outputs** page, rename the input with a more descriptive name such as **MyAddressInput**.</span></span>

7.  <span data-ttu-id="18a3a-180">**연결 관리자** 페이지에서 **MyADONETConnectionManager**와 같은 이름으로 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 연결 관리자를 추가하거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-180">On the **Connection Managers** page, add or create the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager with a name such as **MyADONETConnectionManager**.</span></span>

8.  <span data-ttu-id="18a3a-181">**스크립트** 페이지에서 **스크립트 편집**을 클릭하고 다음 스크립트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-181">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="18a3a-182">그런 다음 스크립트 개발 환경을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-182">Then close the script development environment.</span></span>

9. <span data-ttu-id="18a3a-183">**스크립트 변환 편집기**를 닫고 샘플을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-183">Close the **Script Transformation Editor** and run the sample.</span></span>

```vb
Imports System.Data.SqlClient
...
Public Class ScriptMain
    Inherits UserComponent

    Dim connMgr As IDTSConnectionManager100
    Dim sqlConn As SqlConnection
    Dim sqlCmd As SqlCommand
    Dim sqlParam As SqlParameter

    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

        connMgr = Me.Connections.MyADONETConnectionManager
        sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

    End Sub

    Public Overrides Sub PreExecute()

        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _
            "VALUES(@addressid, @city)", sqlConn)
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)
        sqlCmd.Parameters.Add(sqlParam)
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)
        sqlCmd.Parameters.Add(sqlParam)

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)
        With sqlCmd
            .Parameters("@addressid").Value = Row.AddressID
            .Parameters("@city").Value = Row.City
            .ExecuteNonQuery()
        End With
    End Sub

    Public Overrides Sub ReleaseConnections()

        connMgr.ReleaseConnection(sqlConn)

    End Sub

End Class
```

```csharp
using System.Data.SqlClient;
public class ScriptMain:
    UserComponent

{
    IDTSConnectionManager100 connMgr;
    SqlConnection sqlConn;
    SqlCommand sqlCmd;
    SqlParameter sqlParam;

    public override void AcquireConnections(object Transaction)
    {

        connMgr = this.Connections.MyADONETConnectionManager;
        sqlConn = (SqlConnection)connMgr.AcquireConnection(null);

    }

    public override void PreExecute()
    {

        sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " +
            "VALUES(@addressid, @city)", sqlConn);
        sqlParam = new SqlParameter("@addressid", SqlDbType.Int);
        sqlCmd.Parameters.Add(sqlParam);
        sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);
        sqlCmd.Parameters.Add(sqlParam);

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {
        {
            sqlCmd.Parameters["@addressid"].Value = Row.AddressID;
            sqlCmd.Parameters["@city"].Value = Row.City;
            sqlCmd.ExecuteNonQuery();
        }
    }

    public override void ReleaseConnections()
    {

        connMgr.ReleaseConnection(sqlConn);

    }

}
```

### <a name="flat-file-destination-example"></a><span data-ttu-id="18a3a-184">플랫 파일 대상의 예</span><span class="sxs-lookup"><span data-stu-id="18a3a-184">Flat File Destination Example</span></span>
 <span data-ttu-id="18a3a-185">이 예에서는 기존 플랫 파일 연결 관리자를 사용하여 데이터 흐름에서 받은 데이터를 플랫 파일에 저장하는 대상 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-185">This example demonstrates a destination component that uses an existing Flat File connection manager to save data from the data flow to a flat file.</span></span>

 <span data-ttu-id="18a3a-186">이 예제 코드를 실행하려면 다음과 같이 패키지와 구성 요소를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-186">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="18a3a-187">대상 파일에 연결하는 플랫 파일 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-187">Create a Flat File connection manager that connects to a destination file.</span></span> <span data-ttu-id="18a3a-188">대상 파일이 없는 경우에는 대상 구성 요소가 대상 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-188">The file does not have to exist; the destination component will create it.</span></span> <span data-ttu-id="18a3a-189">대상 파일을 **AddressID** 및 **City** 열이 포함되고 쉼표로 구분된 파일로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-189">Configure the destination file as a comma-delimited file that contains the **AddressID** and **City** columns.</span></span>

2.  <span data-ttu-id="18a3a-190">데이터 흐름 디자이너 화면에 새 스크립트 구성 요소를 추가하고 이 구성 요소를 대상으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-190">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>

3.  <span data-ttu-id="18a3a-191">업스트림 원본 또는 변환의 출력을 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 대상 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-191">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="18a3a-192">변환을 사용 하지 않고 소스를 대상에 직접 연결할 수 있습니다. 이 출력은 예제 데이터베이스의 **Person. Address** 테이블에서 데이터를 제공 해야 `AdventureWorks` 하며, 적어도 **addressid** 및 **City** 열을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-192">(You can connect a source directly to a destination without any transformations.) This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database, and should contain at least the **AddressID** and **City** columns.</span></span>

4.  <span data-ttu-id="18a3a-193">**스크립트 변환 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-193">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="18a3a-194">**입력 열** 페이지에서 **AddressID** 및 **City** 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-194">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>

5.  <span data-ttu-id="18a3a-195">**입/출력** 페이지에서 입력의 이름을 **MyAddressInput**과 같이 더 알기 쉬운 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-195">On the **Inputs and Outputs** page, rename the input with a more descriptive name, such as **MyAddressInput**.</span></span>

6.  <span data-ttu-id="18a3a-196">**연결 관리자** 페이지에서 **MyFlatFileDestConnectionManager**와 같이 알기 쉬운 이름으로 플랫 파일 연결 관리자를 추가하거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-196">On the **Connection Managers** page, add or create the Flat File connection manager with a descriptive name such as **MyFlatFileDestConnectionManager**.</span></span>

7.  <span data-ttu-id="18a3a-197">**스크립트** 페이지에서 **스크립트 편집**을 클릭하고 다음 스크립트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-197">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="18a3a-198">그런 다음 스크립트 개발 환경을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-198">Then close the script development environment.</span></span>

8.  <span data-ttu-id="18a3a-199">**스크립트 변환 편집기**를 닫고 샘플을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="18a3a-199">Close the **Script Transformation Editor** and run the sample.</span></span>

```vb
Imports System.IO
...
Public Class ScriptMain
    Inherits UserComponent

    Dim copiedAddressFile As String
    Private textWriter As StreamWriter
    Private columnDelimiter As String = ","

    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

        Dim connMgr As IDTSConnectionManager100 = _
            Me.Connections.MyFlatFileDestConnectionManager
        copiedAddressFile = CType(connMgr.AcquireConnection(Nothing), String)

    End Sub

    Public Overrides Sub PreExecute()

        textWriter = New StreamWriter(copiedAddressFile, False)

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        With textWriter
            If Not Row.AddressID_IsNull Then
                .Write(Row.AddressID)
            End If
            .Write(columnDelimiter)
            If Not Row.City_IsNull Then
                .Write(Row.City)
            End If
            .WriteLine()
        End With

    End Sub

    Public Overrides Sub PostExecute()

        textWriter.Close()

    End Sub

End Class
```

```csharp
using System.IO;
public class ScriptMain:
    UserComponent

{
    string copiedAddressFile;
    private StreamWriter textWriter;
    private string columnDelimiter = ",";

    public override void AcquireConnections(object Transaction)
    {

        IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileDestConnectionManager;
        copiedAddressFile = (string) connMgr.AcquireConnection(null);

    }

    public override void PreExecute()
    {

        textWriter = new StreamWriter(copiedAddressFile, false);

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        {
            if (!Row.AddressID_IsNull)
            {
                textWriter.Write(Row.AddressID);
            }
            textWriter.Write(columnDelimiter);
            if (!Row.City_IsNull)
            {
                textWriter.Write(Row.City);
            }
            textWriter.WriteLine();
        }

    }

    public override void PostExecute()
    {

        textWriter.Close();

    }

}
```

<span data-ttu-id="18a3a-200">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="18a3a-200">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="18a3a-201">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-201">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="18a3a-202">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-202">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="18a3a-203">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="18a3a-203">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="18a3a-204">참고 항목</span><span class="sxs-lookup"><span data-stu-id="18a3a-204">See Also</span></span>
 <span data-ttu-id="18a3a-205">[스크립트 구성 요소를 사용 하 여 원본 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) [사용자 지정 대상 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)</span><span class="sxs-lookup"><span data-stu-id="18a3a-205">[Creating a Source with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) [Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)</span></span>


