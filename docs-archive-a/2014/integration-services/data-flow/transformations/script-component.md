---
title: 스크립트 구성 요소 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponentdetails.f1
helpviewer_keywords:
- Script transformation
- scripts [Integration Services], transformations
- Script component [Integration Services], about Script component
- Script component [Integration Services]
ms.assetid: 131c2d0c-2e33-4785-94af-ada5c049821e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af8e500e399b0f69a7e34c9e2e01c74d83256107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743415"
---
# <a name="script-component"></a><span data-ttu-id="d7e3d-102">스크립트 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d7e3d-102">Script Component</span></span>
  <span data-ttu-id="d7e3d-103">스크립트 구성 요소는 스크립트를 호스팅하고 패키지에서 사용자 지정 스크립트 코드를 포함시키고 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-103">The Script component hosts script and enables a package to include and run custom script code.</span></span> <span data-ttu-id="d7e3d-104">패키지의 스크립트 구성 요소는 다음 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-104">You can use the Script component in packages for the following purposes:</span></span>  
  
-   <span data-ttu-id="d7e3d-105">데이터 흐름에서 여러 변환을 사용하는 대신 데이터에 여러 변환을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-105">Apply multiple transformations to data instead of using multiple transformations in the data flow.</span></span> <span data-ttu-id="d7e3d-106">예를 들어 스크립트로 두 열에 값을 추가하고 합계의 평균을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-106">For example, a script can add the values in two columns and then calculate the average of the sum.</span></span>  
  
-   <span data-ttu-id="d7e3d-107">기존 .NET 어셈블리에 있는 비즈니스 규칙에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-107">Access business rules in an existing .NET assembly.</span></span> <span data-ttu-id="d7e3d-108">예를 들어 스크립트로 `Income` 열에서 유효한 값 범위를 지정하는 비즈니스 규칙을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-108">For example, a script can apply a business rule that specifies the range of values that are valid in an `Income` column.</span></span>  
  
-   <span data-ttu-id="d7e3d-109">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 식 문법에서 제공되는 함수와 연산자 외에 사용자 지정 수식과 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-109">Use custom formulas and functions in addition to the functions and operators that the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] expression grammar provides.</span></span> <span data-ttu-id="d7e3d-110">예를 들어 LUHN 수식을 사용하는 신용 카드 번호의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-110">For example, validate credit card numbers that use the LUHN formula.</span></span>  
  
-   <span data-ttu-id="d7e3d-111">열 데이터의 유효성을 검사하고 잘못된 데이터가 포함된 레코드는 건너 뜁니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-111">Validate column data and skip records that contain invalid data.</span></span> <span data-ttu-id="d7e3d-112">예를 들어 스크립트로 적절한 우편 요금을 평가하여 금액이 너무 높거나 낮은 레코드를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-112">For example, a script can assess the reasonableness of a postage amount and skip records with extremely high or low amounts.</span></span>  
  
 <span data-ttu-id="d7e3d-113">스크립트 구성 요소를 사용하면 데이터 흐름에 사용자 지정 함수를 쉽고 빠르게 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-113">The Script component provides an easy and quick way to include custom functions in a data flow.</span></span> <span data-ttu-id="d7e3d-114">하지만 여러 패키지에서 스크립트 코드를 재사용하려는 경우에는 스크립트 구성 요소 대신 사용자 지정 구성 요소를 프로그래밍하는 방식을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-114">However, if you plan to reuse the script code in multiple packages, you should consider programming a custom component instead of using the Script component.</span></span> <span data-ttu-id="d7e3d-115">자세한 내용은 [사용자 지정 데이터 흐름 구성 요소 개발](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-115">For more information, see [Developing a Custom Data Flow Component](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7e3d-116">스크립트 구성 요소에 NULL인 열 값을 읽으려고 하는 스크립트가 포함되어 있는 경우 패키지를 실행할 때 스크립트 구성 요소가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-116">If the Script component contains a script that tries to read the value of a column that is NULL, the Script component fails when you run the package.</span></span> <span data-ttu-id="d7e3d-117">스크립트에서 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.IsNull%2A> 메서드를 사용하여 열 값을 읽기 전에 열이 NULL인지 여부를 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-117">We recommend that your script use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.IsNull%2A> method to determine whether the column is NULL before trying to read the column value.</span></span>  
  
 <span data-ttu-id="d7e3d-118">스크립트 구성 요소는 원본, 변환 또는 대상으로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-118">The Script component can be used as a source, a transformation, or a destination.</span></span> <span data-ttu-id="d7e3d-119">이 구성 요소는 하나의 입력과 여러 출력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-119">This component supports one input and multiple outputs.</span></span> <span data-ttu-id="d7e3d-120">구성 요소의 사용 방법에 따라 입력이나 출력 또는 모두를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-120">Depending on how the component is used, it supports either an input or outputs or both.</span></span> <span data-ttu-id="d7e3d-121">스크립트는 입력 또는 출력의 모든 행에 의해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-121">The script is invoked by every row in the input or output.</span></span>  
  
-   <span data-ttu-id="d7e3d-122">원본으로 사용되는 스크립트 구성 요소는 여러 출력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-122">If used as a source, the Script component supports multiple outputs.</span></span>  
  
-   <span data-ttu-id="d7e3d-123">변환으로 사용되는 스크립트 구성 요소는 하나의 입력과 여러 출력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-123">If used as a transformation, the Script component supports one input and multiple outputs.</span></span>  
  
-   <span data-ttu-id="d7e3d-124">대상으로 사용되는 스크립트 구성 요소는 하나의 입력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-124">If used as a destination, the Script component supports one input.</span></span>  
  
 <span data-ttu-id="d7e3d-125">스크립트 구성 요소는 오류 출력을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-125">The Script component does not support error outputs.</span></span>  
  
 <span data-ttu-id="d7e3d-126">스크립트 구성 요소를 패키지에 적합한 선택 항목으로 결정한 후에는 입력과 출력을 구성하고 구성 요소에서 사용하는 스크립트를 개발하며 구성 요소 자체를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-126">After you decide that the Script component is the appropriate choice for your package, you have to configure the inputs and outputs, develop the script that the component uses, and configure the component itself.</span></span>  
  
## <a name="understanding-the-script-component-modes"></a><span data-ttu-id="d7e3d-127">스크립트 구성 요소 모드 이해</span><span class="sxs-lookup"><span data-stu-id="d7e3d-127">Understanding the Script Component Modes</span></span>  
 <span data-ttu-id="d7e3d-128">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 스크립트 구성 요소에는 두 가지 모드인 메타데이터 디자인 모드와 코드 디자인 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-128">In the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the Script component has two modes: metadata-design mode and code-design mode.</span></span> <span data-ttu-id="d7e3d-129">메타데이터 디자인 모드에서는 스크립트 구성 요소 입력 및 출력을 추가하고 수정할 수 있지만 코드를 작성할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-129">In metadata-design mode, you can add and modify the Script component inputs and outputs, but you cannot write code.</span></span> <span data-ttu-id="d7e3d-130">따라서 입력과 출력이 구성된 다음에는 스크립트를 작성하기 위해 코드 디자인 모드로 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-130">After all the inputs and outputs are configured, you switch to code-design mode to write the script.</span></span> <span data-ttu-id="d7e3d-131">스크립트 구성 요소는 입력 및 출력의 메타데이터로부터 기본 코드를 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-131">The Script component automatically generates base code from the metadata of the inputs and outputs.</span></span> <span data-ttu-id="d7e3d-132">스크립트 구성 요소가 기본 코드를 생성한 다음 메타데이터를 변경하면 업데이트된 기본 코드가 사용자의 코드와 호환되지 않기 때문에 사용자의 코드가 더 이상 컴파일되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-132">If you change the metadata after the Script component generates the base code, your code may no longer compile because the updated base code may be incompatible with your code.</span></span>  
  
## <a name="writing-the-script-that-the-component-uses"></a><span data-ttu-id="d7e3d-133">구성 요소에서 사용하는 스크립트 작성</span><span class="sxs-lookup"><span data-stu-id="d7e3d-133">Writing the Script that the Component Uses</span></span>  
 <span data-ttu-id="d7e3d-134">스크립트 구성 요소는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications)를 스크립트 작성 환경으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-134">The Script component uses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the environment in which you write the scripts.</span></span> <span data-ttu-id="d7e3d-135">VSTA는 **스크립트 변환 편집기**를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-135">You access VSTA from the **Script Transformation Editor**.</span></span> <span data-ttu-id="d7e3d-136">자세한 내용은 [스크립트 변환 편집기&#40;스크립트 페이지&#41;](../../script-transformation-editor-script-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-136">For more information, see [Script Transformation Editor &#40;Script Page&#41;](../../script-transformation-editor-script-page.md).</span></span>  
  
 <span data-ttu-id="d7e3d-137">스크립트 구성 요소는 구성 요소 메타데이터를 나타내는 ScriptMain이라는 자동 생성된 클래스가 포함된 VSTA 프로젝트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-137">The Script component provides a VSTA project that includes an auto-generated class, named ScriptMain, that represents the component metadata.</span></span> <span data-ttu-id="d7e3d-138">예를 들어 스크립트 구성 요소가 3개의 출력이 있는 변환으로 사용되는 경우 ScriptMain에는 각 출력에 대한 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-138">For example, if the Script component is used as a transformation that has three outputs, ScriptMain includes a method for each output.</span></span> <span data-ttu-id="d7e3d-139">ScriptMain은 스크립트에 대한 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-139">ScriptMain is the entry point to the script.</span></span>  
  
 <span data-ttu-id="d7e3d-140">VSTA에는 색 구분 기능이 포함된 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 편집기, IntelliSense, 개체 브라우저 등 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 환경의 모든 표준 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-140">VSTA includes all the standard features of the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] environment, such as the color-coded [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] editor, IntelliSense, and Object Browser.</span></span> <span data-ttu-id="d7e3d-141">스크립트 구성 요소에서 사용하는 스크립트는 패키지 정의에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-141">The script that the Script component uses is stored in the package definition.</span></span> <span data-ttu-id="d7e3d-142">패키지를 디자인할 때 스크립트 코드는 임시로 프로젝트 파일에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-142">When you are designing the package, the script code is temporarily written to a project file.</span></span>  
  
 <span data-ttu-id="d7e3d-143">VSTA는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 및 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 프로그래밍 언어를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-143">VSTA supports the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic programming languages.</span></span>  
  
 <span data-ttu-id="d7e3d-144">스크립트 구성 요소를 프로그래밍하는 방법은 [스크립트 구성 요소를 사용하여 데이터 흐름 확장](script-component.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-144">For information about how to program the Script component, see [Extending the Data Flow with the Script Component](script-component.md).</span></span> <span data-ttu-id="d7e3d-145">스크립트 구성 요소를 원본, 변환 또는 대상으로 구성하는 방법에 대한 자세한 내용은 [Developing Specific Types of Script Components](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-145">For more specific information about how to configure the Script component as a source, transformation, or destination, see [Developing Specific Types of Script Components](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span> <span data-ttu-id="d7e3d-146">스크립트 구성 요소 사용 방법을 보여 주는 ODBC 대상 등의 추가 예는 [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-146">For additional examples such as an ODBC destination that demonstrate the use of the Script component, see [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7e3d-147">스크립트가 미리 컴파일되었는지 여부를 지정할 수 있었던 이전 버전과는 달리 모든 스크립트가 [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] 이상 버전에 미리 컴파일되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-147">Unlike earlier versions where you could indicate whether the scripts were precompiled, all scripts are precompiled in [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] and later versions.</span></span> <span data-ttu-id="d7e3d-148">스크립트가 미리 컴파일된 경우 런타임 시 언어 엔진이 로드되지 않으므로 패키지가 보다 신속하게 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-148">When a script is precompiled, the language engine is not loaded at run time and the package runs more quickly.</span></span> <span data-ttu-id="d7e3d-149">그러나 미리 컴파일된 이진 파일은 상당한 디스크 공간을 소비합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-149">However, precompiled binary files consume significant disk space.</span></span>  
  
## <a name="configuring-the-script-component"></a><span data-ttu-id="d7e3d-150">스크립트 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="d7e3d-150">Configuring the Script Component</span></span>  
 <span data-ttu-id="d7e3d-151">다음과 같은 방법으로 스크립트 구성 요소를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-151">You can configure the Script component in the following ways:</span></span>  
  
-   <span data-ttu-id="d7e3d-152">참조할 입력 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-152">Select the input columns to reference.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7e3d-153">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용할 경우 입력을 한 개만 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-153">You can configure only one input when you use the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
-   <span data-ttu-id="d7e3d-154">구성 요소에서 실행할 스크립트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-154">Provide the script that the component runs.</span></span>  
  
-   <span data-ttu-id="d7e3d-155">스크립트 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-155">Specify the script language.</span></span>  
  
-   <span data-ttu-id="d7e3d-156">쉼표로 구분된 읽기 전용 및 읽기/쓰기 변수 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-156">Provide comma-separated lists of read-only and read/write variables.</span></span>  
  
-   <span data-ttu-id="d7e3d-157">출력을 추가하고 스크립트가 할당할 출력 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-157">Add more outputs, and add output columns to which the script assigns.</span></span>  
  
 <span data-ttu-id="d7e3d-158">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-158">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
### <a name="configuring-the-script-component-in-the-designer"></a><span data-ttu-id="d7e3d-159">디자이너에서 스크립트 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="d7e3d-159">Configuring the Script Component in the Designer</span></span>  
 <span data-ttu-id="d7e3d-160">**스크립트 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-160">For more information about the properties that you can set in the **Script Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d7e3d-161">스크립트 변환 편집기&#40;입력 열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d7e3d-161">Script Transformation Editor &#40;Input Columns Page&#41;</span></span>](../../script-transformation-editor-input-columns-page.md)  
  
-   [<span data-ttu-id="d7e3d-162">스크립트 변환 편집기&#40;입/출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d7e3d-162">Script Transformation Editor &#40;Inputs and Outputs Page&#41;</span></span>](../../script-transformation-editor-inputs-and-outputs-page.md)  
  
-   [<span data-ttu-id="d7e3d-163">스크립트 변환 편집기&#40;스크립트 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d7e3d-163">Script Transformation Editor &#40;Script Page&#41;</span></span>](../../script-transformation-editor-script-page.md)  
  
-   [<span data-ttu-id="d7e3d-164">스크립트 변환 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d7e3d-164">Script Transformation Editor &#40;Connection Managers Page&#41;</span></span>](../../script-transformation-editor-connection-managers-page.md)  
  
 <span data-ttu-id="d7e3d-165">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-165">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="d7e3d-166">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="d7e3d-166">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
### <a name="configuring-the-script-component-programmatically"></a><span data-ttu-id="d7e3d-167">프로그래밍 방식으로 스크립트 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="d7e3d-167">Configuring the Script Component Programmatically</span></span>  
 <span data-ttu-id="d7e3d-168">**속성** 창을 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-168">For more information about the properties that you can set in the **Properties** window or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d7e3d-169">Common Properties</span><span class="sxs-lookup"><span data-stu-id="d7e3d-169">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="d7e3d-170">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="d7e3d-170">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="d7e3d-171">속성 설정 방법을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="d7e3d-171">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d7e3d-172">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="d7e3d-172">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="d7e3d-173">관련 내용</span><span class="sxs-lookup"><span data-stu-id="d7e3d-173">Related Content</span></span>  
 [<span data-ttu-id="d7e3d-174">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="d7e3d-174">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
 [<span data-ttu-id="d7e3d-175">스크립트 구성 요소를 사용하여 데이터 흐름 확장</span><span class="sxs-lookup"><span data-stu-id="d7e3d-175">Extending the Data Flow with the Script Component</span></span>](script-component.md)  
  
  
