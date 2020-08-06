---
title: 스크립트 태스크 편집기 (스크립트 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.script.f1
helpviewer_keywords:
- Script Task Editor
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4eec491cc689d7d5c616e0819075e1ee5159d4e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728475"
---
# <a name="script-task-editor-script-page"></a><span data-ttu-id="97089-102">스크립트 태스크 편집기(스크립트 페이지)</span><span class="sxs-lookup"><span data-stu-id="97089-102">Script Task Editor (Script Page)</span></span>
  <span data-ttu-id="97089-103">**스크립트 태스크 편집기** 대화 상자의 **스크립트** 페이지를 사용하여 스크립트 속성을 설정하고 스크립트에서 액세스할 수 있는 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97089-103">Use the **Script** page of the **Script Task Editor** dialog box to set script properties and specify variables that can be accessed by the script.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97089-104">[!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] 와 그 이후 버전에서는 모든 스크립트가 미리 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="97089-104">In [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] and later versions, all scripts are precompiled.</span></span> <span data-ttu-id="97089-105">그러나 이전 버전에서는 **PrecompileScriptIntoBinaryCode** 속성을 설정하여 스크립트가 미리 컴파일되었음을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97089-105">In earlier versions, you set a **PrecompileScriptIntoBinaryCode** property to specify that the script was precompiled.</span></span>  
  
 <span data-ttu-id="97089-106">스크립트 태스크에 대한 자세한 내용은 [Script Task](control-flow/script-task.md) 및 [스크립트 태스크 편집기에서 스크립트 태스크 구성](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="97089-106">To learn more about the Script task, see [Script Task](control-flow/script-task.md) and [Configuring the Script Task in the Script Task Editor](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md).</span></span> <span data-ttu-id="97089-107">스크립트 태스크 프로그래밍 방법은 [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="97089-107">To learn about programming the Script task, see [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="97089-108">옵션</span><span class="sxs-lookup"><span data-stu-id="97089-108">Options</span></span>  
 <span data-ttu-id="97089-109">**ScriptLanguage**</span><span class="sxs-lookup"><span data-stu-id="97089-109">**ScriptLanguage**</span></span>  
 <span data-ttu-id="97089-110">태스크에 대한 스크립트 언어를 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C# 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="97089-110">Select the scripting language for the task, either [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="97089-111">태스크에 대한 스크립트를 작성한 후에는 **ScriptLanguage** 속성의 값을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97089-111">After you have created a script for the task, you cannot change the value of the **ScriptLanguage** property.</span></span>  
  
 <span data-ttu-id="97089-112">스크립트 태스크에 대한 스크립트 언어를 설정하려면 **옵션** 대화 상자의 **일반** 페이지에서 **스크립트 언어** 옵션을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="97089-112">To set the default scripting language for the Script task, use the **Scripting language** option on **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="97089-113">자세한 내용은 [General Page](general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97089-113">For more information, see [General Page](general-page-of-integration-services-designers-options.md).</span></span>  
  
 <span data-ttu-id="97089-114">**EntryPoint**</span><span class="sxs-lookup"><span data-stu-id="97089-114">**EntryPoint**</span></span>  
 <span data-ttu-id="97089-115">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 런타임이 스크립트 태스크 코드에 대한 진입점으로 호출하는 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97089-115">Specify the method that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] runtime calls as the entry point into the code of the Script task.</span></span> <span data-ttu-id="97089-116">지정한 메서드는 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSTA (Tools for Applications) 프로젝트의 scriptmain 클래스에 있어야 합니다. scriptmain 클래스는 스크립트 템플릿에 의해 생성 된 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="97089-116">The specified method must be in the ScriptMain class of the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) project The ScriptMain class is the default class generated by the script templates.</span></span>  
  
 <span data-ttu-id="97089-117">VSTA 프로젝트에서 메서드 이름을 변경한 경우 **EntryPoint** 속성의 값을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97089-117">If you change the name of the method in the VSTA project, you must change the value of the **EntryPoint** property.</span></span>  
  
 <span data-ttu-id="97089-118">**ReadOnlyVariables**</span><span class="sxs-lookup"><span data-stu-id="97089-118">**ReadOnlyVariables**</span></span>  
 <span data-ttu-id="97089-119">스크립트에 사용할 수 있는 읽기 전용 변수 목록을 쉼표로 구분하여 입력하거나 줄임표 단추(**...**)를 클릭하고 **변수 선택** 대화 상자에서 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="97089-119">Type a comma-separated list of read-only variables that are available to the script, or click the ellipsis (**...**) button and select the variables in the **Select variables** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97089-120">변수 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="97089-120">Variable names are case sensitive.</span></span>  
  
 <span data-ttu-id="97089-121">**ReadWriteVariables**</span><span class="sxs-lookup"><span data-stu-id="97089-121">**ReadWriteVariables**</span></span>  
 <span data-ttu-id="97089-122">스크립트에 사용할 수 있는 읽기/쓰기 변수 목록을 쉼표로 구분하여 입력하거나 줄임표 단추(**...**)를 클릭하고 **변수 선택** 대화 상자에서 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="97089-122">Type a comma-separated list of read/write variables that are available to the script, or click the ellipsis (**...**) button and select the variables in the **Select variables** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97089-123">변수 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="97089-123">Variable names are case sensitive.</span></span>  
  
 <span data-ttu-id="97089-124">**스크립트 편집**</span><span class="sxs-lookup"><span data-stu-id="97089-124">**Edit Script**</span></span>  
 <span data-ttu-id="97089-125">스크립트를 작성하거나 수정할 수 있는 VSTA IDE가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="97089-125">Opens the VSTA IDE where you can create or modify the script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97089-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97089-126">See Also</span></span>  
 <span data-ttu-id="97089-127">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="97089-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="97089-128">[일반 페이지](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="97089-128">[General Page](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="97089-129">[스크립트 태스크 편집기 &#40;일반 페이지&#41;](../../2014/integration-services/script-task-editor-general-page.md) </span><span class="sxs-lookup"><span data-stu-id="97089-129">[Script Task Editor &#40;General Page&#41;](../../2014/integration-services/script-task-editor-general-page.md) </span></span>  
 <span data-ttu-id="97089-130">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="97089-130">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="97089-131">[스크립트 태스크 예제](extending-packages-scripting-task-examples/script-task-examples.md) </span><span class="sxs-lookup"><span data-stu-id="97089-131">[Script Task Examples](extending-packages-scripting-task-examples/script-task-examples.md) </span></span>  
 <span data-ttu-id="97089-132">[Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="97089-132">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="97089-133">패키지에서 사용자 정의 변수의 범위 추가, 삭제, 변경</span><span class="sxs-lookup"><span data-stu-id="97089-133">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
