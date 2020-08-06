---
title: 스크립트 변환 편집기 (입력 열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.inputcolumn.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: d6e4ce84-3335-48e6-82d3-1c359ed87f63
author: chugugrace
ms.author: chugu
ms.openlocfilehash: daffb52b62ad59ae4fe574d7fa27d4820b9cb5a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728464"
---
# <a name="script-transformation-editor-input-columns-page"></a><span data-ttu-id="0bb0d-102">스크립트 변환 편집기(입력 열 페이지)</span><span class="sxs-lookup"><span data-stu-id="0bb0d-102">Script Transformation Editor (Input Columns Page)</span></span>
  <span data-ttu-id="0bb0d-103">**스크립트 변환 편집기** 대화 상자의 **입력 열** 페이지를 사용하여 입력 열의 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-103">Use the **Input Columns** page of the **Script Transformation Editor** dialog box to set properties on input columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0bb0d-104">**입력 열** 페이지는 출력은 있지만 입력은 없는 원본 구성 요소에 대해서는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-104">The **Input Columns** page is not displayed for Source components, which have outputs but no inputs.</span></span>  
  
 <span data-ttu-id="0bb0d-105">스크립트 구성 요소에 대한 자세한 내용은 [Script Component](data-flow/transformations/script-component.md) 및 [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-105">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="0bb0d-106">스크립트 구성 요소 프로그래밍 방법은 [스크립트 구성 요소를 사용하여 데이터 흐름 확장](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-106">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0bb0d-107">옵션</span><span class="sxs-lookup"><span data-stu-id="0bb0d-107">Options</span></span>  
 <span data-ttu-id="0bb0d-108">**입력 이름**</span><span class="sxs-lookup"><span data-stu-id="0bb0d-108">**Input name**</span></span>  
 <span data-ttu-id="0bb0d-109">사용 가능한 입력 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-109">Select from the list of available inputs.</span></span>  
  
 <span data-ttu-id="0bb0d-110">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="0bb0d-110">**Available Input Columns**</span></span>  
 <span data-ttu-id="0bb0d-111">확인란을 사용하여 스크립트 변환에서 사용할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-111">Using the check boxes, specify the columns that the script transformation will use.</span></span>  
  
 <span data-ttu-id="0bb0d-112">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="0bb0d-112">**Input Column**</span></span>  
 <span data-ttu-id="0bb0d-113">각 행에 대해 사용 가능한 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-113">Select from the list of available input columns for each row.</span></span> <span data-ttu-id="0bb0d-114">선택 내용에 따라 **사용 가능한 입력 열**테이블의 확인란이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-114">Your selections are reflected in the check box selections in the **Available Input Columns**table.</span></span>  
  
 <span data-ttu-id="0bb0d-115">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="0bb0d-115">**Output Alias**</span></span>  
 <span data-ttu-id="0bb0d-116">각 출력 열의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-116">Type an alias for each output column.</span></span> <span data-ttu-id="0bb0d-117">기본값은 입력 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-117">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="0bb0d-118">**사용 유형**</span><span class="sxs-lookup"><span data-stu-id="0bb0d-118">**Usage Type**</span></span>  
 <span data-ttu-id="0bb0d-119">스크립트 변환에서 각 열을 `ReadOnly`로 처리할지, 아니면 `ReadWrite`로 처리할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0bb0d-119">Specify whether the Script Transformation will treat each column as `ReadOnly` or `ReadWrite`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb0d-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0bb0d-120">See Also</span></span>  
 <span data-ttu-id="0bb0d-121">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0bb0d-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="0bb0d-122">[스크립트 구성 요소 유형 선택](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="0bb0d-122">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="0bb0d-123">[스크립트 변환 편집기 &#40;입력 및 출력 페이지&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span><span class="sxs-lookup"><span data-stu-id="0bb0d-123">[Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md) </span></span>  
 <span data-ttu-id="0bb0d-124">[스크립트 변환 편집기 &#40;스크립트 페이지&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span><span class="sxs-lookup"><span data-stu-id="0bb0d-124">[Script Transformation Editor &#40;Script Page&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span></span>  
 <span data-ttu-id="0bb0d-125">[스크립트 변환 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="0bb0d-125">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="0bb0d-126">추가 스크립트 구성 요소 예</span><span class="sxs-lookup"><span data-stu-id="0bb0d-126">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
