---
title: 스크립트 태스크 편집기에서 스크립트 태스크 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b75b4a030e6c5baa2e26c610b0e8216843c8cca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648445"
---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a><span data-ttu-id="0719d-102">스크립트 태스크 편집기에서 스크립트 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="0719d-102">Configuring the Script Task in the Script Task Editor</span></span>
  <span data-ttu-id="0719d-103">스크립트 태스크에서 사용자 지정 코드를 작성하려면 먼저 **스크립트 태스크 편집기**의 세 페이지에서 주 속성을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-103">Before you write custom code in the Script task, you configure its principal properties in the three pages of the **Script Task Editor**.</span></span> <span data-ttu-id="0719d-104">속성 창에서는 스크립트 태스크에 고유하지 않은 추가 태스크 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-104">You can configure additional task properties that are not unique to the Script task by using the Properties window.</span></span>

> [!NOTE]
>  <span data-ttu-id="0719d-105">스크립트가 미리 컴파일되었는지 여부를 지정할 수 있었던 이전 버전과는 달리 [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] 이상에서는 모든 스크립트가 미리 컴파일되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-105">Unlike earlier versions where you could indicate whether scripts were precompiled, all scripts are precompiled beginning in [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)].</span></span>

## <a name="general-page-of-the-script-task-editor"></a><span data-ttu-id="0719d-106">스크립트 태스크 편집기의 일반 페이지</span><span class="sxs-lookup"><span data-stu-id="0719d-106">General Page of the Script Task Editor</span></span>
 <span data-ttu-id="0719d-107">**스크립트 태스크 편집기**의 **일반** 페이지에서는 스크립트 태스크의 고유한 이름과 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-107">On the **General** page of the **Script Task Editor**, you assign a unique name and a description for the Script task.</span></span>

## <a name="script-page-of-the-script-task-editor"></a><span data-ttu-id="0719d-108">스크립트 태스크 편집기의 스크립트 페이지</span><span class="sxs-lookup"><span data-stu-id="0719d-108">Script Page of the Script Task Editor</span></span>
 <span data-ttu-id="0719d-109">**스크립트 태스크 편집기**의 **스크립트** 페이지에는 스크립트 태스크의 사용자 지정 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-109">The **Script** page of the **Script Task Editor** displays the custom properties of the Script task.</span></span>

### <a name="scriptlanguage-property"></a><span data-ttu-id="0719d-110">ScriptLanguage 속성</span><span class="sxs-lookup"><span data-stu-id="0719d-110">ScriptLanguage Property</span></span>
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="0719d-111">VSTA([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications)는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 프로그래밍 언어를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) supports the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# programming languages.</span></span> <span data-ttu-id="0719d-112">스크립트 태스크에서 스크립트를 만든 후에는 **ScriptLanguage** 속성의 값을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-112">After you create a script in the Script task, you cannot change value of the **ScriptLanguage** property.</span></span>

 <span data-ttu-id="0719d-113">스크립트 태스크 및 스크립트 구성 요소에 대한 기본 스크립트 언어를 설정하려면 **옵션** 대화 상자의 **일반** 페이지에 있는 **ScriptLanguage** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-113">To set the default script language for Script tasks and Script components, use the **ScriptLanguage** property on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="0719d-114">자세한 내용은 [General Page](../../general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0719d-114">For more information, see [General Page](../../general-page-of-integration-services-designers-options.md).</span></span>

### <a name="entrypoint-property"></a><span data-ttu-id="0719d-115">EntryPoint 속성</span><span class="sxs-lookup"><span data-stu-id="0719d-115">EntryPoint Property</span></span>
 <span data-ttu-id="0719d-116">`EntryPoint` 속성은 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 런타임이 VSTA 프로젝트의 `ScriptMain` 클래스에서 스크립트 태스크 코드에 대한 진입점으로 호출하는 메서드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-116">The `EntryPoint` property specifies the method on the `ScriptMain` class in the VSTA project that the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span> <span data-ttu-id="0719d-117">`ScriptMain`클래스는 스크립트 템플릿이 생성 하는 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-117">The `ScriptMain` class is the default class generated by the script templates.</span></span>

 <span data-ttu-id="0719d-118">VSTA 프로젝트에서 메서드 이름을 변경한 경우 `EntryPoint` 속성의 값을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-118">If you change the name of the method in the VSTA project, you must change the value of the `EntryPoint` property.</span></span>

### <a name="readonlyvariables-and-readwritevariables-properties"></a><span data-ttu-id="0719d-119">ReadOnlyVariables 및 ReadWriteVariables 속성</span><span class="sxs-lookup"><span data-stu-id="0719d-119">ReadOnlyVariables and ReadWriteVariables Properties</span></span>
 <span data-ttu-id="0719d-120">쉼표로 구분된 기존 변수 목록을 이러한 속성의 값으로 입력하여 스크립트 태스크 코드 내에서 해당 변수를 읽기 전용 또는 읽기/쓰기 권한으로 액세스할 수 있게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-120">You can enter comma-delimited lists of existing variables as the values of these properties to make the variables available for read-only or read/write access within the Script task code.</span></span> <span data-ttu-id="0719d-121">두 유형의 변수 모두 코드에서 `Dts` 개체의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-121">Variables of both types are accessed in code through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object.</span></span> <span data-ttu-id="0719d-122">자세한 내용은 [Using Variables in the Script Task](../../extending-packages-scripting/task/using-variables-in-the-script-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0719d-122">For more information, see [Using Variables in the Script Task](../../extending-packages-scripting/task/using-variables-in-the-script-task.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="0719d-123">변수 이름은 대소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-123">Variable names are case-sensitive.</span></span>

 <span data-ttu-id="0719d-124">변수를 선택하려면 속성 필드 옆의 줄임표( **...** ) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-124">To select the variables, click the ellipsis (**...**) button next to the property field.</span></span> <span data-ttu-id="0719d-125">자세한 내용은 [변수 선택 페이지](../../control-flow/select-variables-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0719d-125">For more information, see [Select Variables Page](../../control-flow/select-variables-page.md).</span></span>

### <a name="edit-script-button"></a><span data-ttu-id="0719d-126">스크립트 편집 단추</span><span class="sxs-lookup"><span data-stu-id="0719d-126">Edit Script Button</span></span>
 <span data-ttu-id="0719d-127">**스크립트 편집** 단추를 클릭하면 사용자 지정 스크립트를 작성할 수 있는 VSTA 개발 환경이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-127">The **Edit Script** button launches the VSTA development environment in which you write your custom script.</span></span> <span data-ttu-id="0719d-128">자세한 내용은 [스크립트 태스크 코딩 및 디버깅](coding-and-debugging-the-script-task.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0719d-128">For more information, see [Coding and Debugging the Script Task](coding-and-debugging-the-script-task.md).</span></span>

## <a name="expressions-page-of-the-script-task-editor"></a><span data-ttu-id="0719d-129">스크립트 태스크 편집기의 식 페이지</span><span class="sxs-lookup"><span data-stu-id="0719d-129">Expressions Page of the Script Task Editor</span></span>
 <span data-ttu-id="0719d-130">**스크립트 태스크 편집기**의 **식**에서 식을 사용하여 위에 나열된 스크립트 태스크의 속성과 그 밖의 여러 태스크 속성에 대한 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-130">On the **Expressions** page of the **Script Task Editor**, you can use expressions to provide values for the properties of the Script task listed above and for many other task properties.</span></span> <span data-ttu-id="0719d-131">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../../expressions/integration-services-ssis-expressions.md)가 될 때까지 워크플로를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="0719d-131">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>

<span data-ttu-id="0719d-132">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="0719d-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="0719d-133">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]의 최신 다운로드, 아티클, 예제 및 비디오와 커뮤니티의 정선된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하십시오.</span><span class="sxs-lookup"><span data-stu-id="0719d-133">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="0719d-134">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="0719d-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="0719d-135">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="0719d-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="0719d-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0719d-136">See Also</span></span>
 [<span data-ttu-id="0719d-137">스크립트 태스크 코딩 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="0719d-137">Coding and Debugging the Script Task</span></span>](coding-and-debugging-the-script-task.md)


