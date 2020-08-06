---
title: 스크립트 변환 편집기 (스크립트 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df89bddd0a2f12e1d0efe0db74f4e10aadd772eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651078"
---
# <a name="script-transformation-editor-script-page"></a><span data-ttu-id="15a66-102">스크립트 변환 편집기(스크립트 페이지)</span><span class="sxs-lookup"><span data-stu-id="15a66-102">Script Transformation Editor (Script Page)</span></span>
  <span data-ttu-id="15a66-103">**스크립트 변환 편집기** 대화 상자의 **스크립트** 탭을 사용하여 스크립트 및 관련 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-103">Use the **Script** tab of the **Script Transformation Editor** dialog box to specify a script and related properties.</span></span>  
  
 <span data-ttu-id="15a66-104">스크립트 구성 요소에 대한 자세한 내용은 [Script Component](data-flow/transformations/script-component.md) 및 [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="15a66-104">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="15a66-105">스크립트 구성 요소 프로그래밍 방법은 [스크립트 구성 요소를 사용하여 데이터 흐름 확장](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="15a66-105">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="15a66-106">옵션</span><span class="sxs-lookup"><span data-stu-id="15a66-106">Options</span></span>  
 <span data-ttu-id="15a66-107">**속성**</span><span class="sxs-lookup"><span data-stu-id="15a66-107">**Properties**</span></span>  
 <span data-ttu-id="15a66-108">스크립트 변환 속성을 보고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-108">View and modify the properties of the Script transformation.</span></span> <span data-ttu-id="15a66-109">표시된 속성 중 다수는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-109">Many of the properties displayed are read-only.</span></span> <span data-ttu-id="15a66-110">다음 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-110">You can modify the following properties:</span></span>  
  
|<span data-ttu-id="15a66-111">값</span><span class="sxs-lookup"><span data-stu-id="15a66-111">Value</span></span>|<span data-ttu-id="15a66-112">Description</span><span class="sxs-lookup"><span data-stu-id="15a66-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15a66-113">**설명**</span><span class="sxs-lookup"><span data-stu-id="15a66-113">**Description**</span></span>|<span data-ttu-id="15a66-114">스크립트 변환의 목적을 기준으로 스크립트 변환을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-114">Describe the script transformation in terms of its purpose.</span></span>|  
|<span data-ttu-id="15a66-115">**LocaleID**</span><span class="sxs-lookup"><span data-stu-id="15a66-115">**LocaleID**</span></span>|<span data-ttu-id="15a66-116">정렬과 날짜 및 시간 변환에 사용할 지역별 정보를 제공하는 로캘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-116">Specify the locale to provide region-specific information for ordering, and for date and time conversion.</span></span>|  
|<span data-ttu-id="15a66-117">**이름**</span><span class="sxs-lookup"><span data-stu-id="15a66-117">**Name**</span></span>|<span data-ttu-id="15a66-118">구성 요소에 대한 설명이 포함된 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-118">Type a descriptive name for the component.</span></span>|  
|<span data-ttu-id="15a66-119">**ValidateExternalMetadata**</span><span class="sxs-lookup"><span data-stu-id="15a66-119">**ValidateExternalMetadata**</span></span>|<span data-ttu-id="15a66-120">스크립트 변환이 디자인 타임에서 외부 데이터 원본에 대해 열 메타데이터의 유효성을 검사할 것인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-120">Indicate whether the Script transformation validates column metadata against external data sources at design time.</span></span> <span data-ttu-id="15a66-121">값 `false`는 실행 시간까지 유효성 검사를 지연합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-121">A value of `false` delays validation until the time of execution.</span></span>|  
|<span data-ttu-id="15a66-122">**ReadOnlyVariables**</span><span class="sxs-lookup"><span data-stu-id="15a66-122">**ReadOnlyVariables**</span></span>|<span data-ttu-id="15a66-123">스크립트 변환을 통해 읽기 전용으로 액세스할 변수 목록을 쉼표로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-123">Type a comma-separated list of variables for read-only access by the Script transformation.</span></span><br /><br /> <span data-ttu-id="15a66-124">참고: 변수 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-124">Note: Variable names are case-sensitive.</span></span>|  
|<span data-ttu-id="15a66-125">**ReadWriteVariables**</span><span class="sxs-lookup"><span data-stu-id="15a66-125">**ReadWriteVariables**</span></span>|<span data-ttu-id="15a66-126">스크립트 변환을 통해 읽기/쓰기로 액세스할 변수 목록을 쉼표로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-126">Type a comma-separated list of variables for read/write access by the Script transformation.</span></span><br /><br /> <span data-ttu-id="15a66-127">참고: 변수 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-127">Note: Variable names are case-sensitive.</span></span>|  
|<span data-ttu-id="15a66-128">**ScriptLanguage**</span><span class="sxs-lookup"><span data-stu-id="15a66-128">**ScriptLanguage**</span></span>|<span data-ttu-id="15a66-129">스크립트 구성 요소에 사용될 스크립트 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-129">Select the script language to be used by the Script component.</span></span><br /><br /> <span data-ttu-id="15a66-130">스크립트 구성 요소 및 스크립트 태스크에 대한 기본 스크립트 언어를 설정하려면 **옵션** 대화 상자의 **일반** 페이지에서 **스크립트 언어** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-130">To set the default script language for Script components and Script tasks, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="15a66-131">자세한 내용은 [General Page](general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15a66-131">For more information, see [General Page](general-page-of-integration-services-designers-options.md).</span></span>|  
|<span data-ttu-id="15a66-132">**UserComponentTypeName**</span><span class="sxs-lookup"><span data-stu-id="15a66-132">**UserComponentTypeName**</span></span>|<span data-ttu-id="15a66-133">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인프라를 지원하는 `Microsoft.SqlServer.TxScript` 어셈블리 및 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> 클래스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-133">Specifies the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> class and the `Microsoft.SqlServer.TxScript` assembly that support the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] infrastructure.</span></span>|  
  
 <span data-ttu-id="15a66-134">**스크립트 편집**</span><span class="sxs-lookup"><span data-stu-id="15a66-134">**Edit Script**</span></span>  
 <span data-ttu-id="15a66-135">VSTA([!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications)를 사용하여 스크립트를 작성하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15a66-135">Use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) to create or modify a script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a66-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15a66-136">See Also</span></span>  
 <span data-ttu-id="15a66-137">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="15a66-137">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="15a66-138">[스크립트 구성 요소 유형 선택](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="15a66-138">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="15a66-139">[스크립트 변환 편집기 &#40;입력 열 페이지&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="15a66-139">[Script Transformation Editor &#40;Input Columns Page&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span></span>  
 <span data-ttu-id="15a66-140">[스크립트 변환 편집기 &#40;입력 및 출력 페이지&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span><span class="sxs-lookup"><span data-stu-id="15a66-140">[Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span></span>  
 <span data-ttu-id="15a66-141">[스크립트 변환 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="15a66-141">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="15a66-142">추가 스크립트 구성 요소 예</span><span class="sxs-lookup"><span data-stu-id="15a66-142">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
