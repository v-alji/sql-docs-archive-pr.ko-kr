---
title: 스크립트 변환 편집기 (입/출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.columnproperties.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 9659d2d2-5d73-4470-9768-e07b77142fc9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16adf74a1cd8f0c778bc18eaff84437b8fc13603
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728460"
---
# <a name="script-transformation-editor-inputs-and-outputs-page"></a><span data-ttu-id="e6505-102">스크립트 변환 편집기(입/출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="e6505-102">Script Transformation Editor (Inputs and Outputs Page)</span></span>
  <span data-ttu-id="e6505-103">**스크립트 변환 편집기** 대화 상자의 **입/출력** 페이지를 사용하여 스크립트 변환에 대한 입력 및 출력을 추가, 제거 및 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6505-103">Use the **Inputs and Outputs** page of the **Script Transformation Editor** dialog box to add, remove, and configure inputs and outputs for the Script Transformation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6505-104">원본 구성 요소는 출력이 있고 입력이 없지만 대상 구성 요소는 입력이 있고 출력이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6505-104">Source components have outputs and no inputs, while destination components have inputs but no outputs.</span></span> <span data-ttu-id="e6505-105">변환은 입력과 출력이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6505-105">Transformations have both inputs and outputs.</span></span>  
  
 <span data-ttu-id="e6505-106">스크립트 구성 요소에 대한 자세한 내용은 [Script Component](data-flow/transformations/script-component.md) 및 [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e6505-106">To learn more about the Script component, see [Script Component](data-flow/transformations/script-component.md) and [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span> <span data-ttu-id="e6505-107">스크립트 구성 요소 프로그래밍 방법은 [스크립트 구성 요소를 사용하여 데이터 흐름 확장](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e6505-107">To learn about programming the Script component, see [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e6505-108">옵션</span><span class="sxs-lookup"><span data-stu-id="e6505-108">Options</span></span>  
 <span data-ttu-id="e6505-109">**Inputs and outputs**</span><span class="sxs-lookup"><span data-stu-id="e6505-109">**Inputs and outputs**</span></span>  
 <span data-ttu-id="e6505-110">왼쪽에서 입력 또는 출력을 선택하여 오른쪽에 있는 테이블에서 해당 속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e6505-110">Select an input or output on the left to view its properties in the table on the right.</span></span> <span data-ttu-id="e6505-111">편집할 수 있는 속성은 선택하는 입력 또는 출력에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e6505-111">Properties available for editing vary according to the selection.</span></span> <span data-ttu-id="e6505-112">표시된 속성 중 다수는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="e6505-112">Many of the properties displayed are read-only.</span></span> <span data-ttu-id="e6505-113">개별 속성에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e6505-113">For more information on the individual properties, see the following topics.</span></span>  
  
 [<span data-ttu-id="e6505-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="e6505-114">Common Properties</span></span>](../../2014/integration-services/common-properties.md)  
  
 [<span data-ttu-id="e6505-115">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="e6505-115">Transformation Custom Properties</span></span>](data-flow/transformations/transformation-custom-properties.md)  
  
 <span data-ttu-id="e6505-116">**출력 추가**</span><span class="sxs-lookup"><span data-stu-id="e6505-116">**Add Output**</span></span>  
 <span data-ttu-id="e6505-117">목록에 출력을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e6505-117">Add an additional output to the list.</span></span>  
  
 <span data-ttu-id="e6505-118">**열 추가**</span><span class="sxs-lookup"><span data-stu-id="e6505-118">**Add Column**</span></span>  
 <span data-ttu-id="e6505-119">새 출력 열을 추가할 폴더를 선택한 다음 **열 추가**를 클릭하여 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e6505-119">Select a folder in which to place the new output column, and then add the column by clicking **Add Column**.</span></span>  
  
 <span data-ttu-id="e6505-120">**출력 제거**</span><span class="sxs-lookup"><span data-stu-id="e6505-120">**Remove Output**</span></span>  
 <span data-ttu-id="e6505-121">출력을 선택한 다음 **출력 제거**를 클릭하여 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e6505-121">Select an output, and then remove it by clicking **Remove Output**.</span></span>  
  
 <span data-ttu-id="e6505-122">**열 제거**</span><span class="sxs-lookup"><span data-stu-id="e6505-122">**Remove Column**</span></span>  
 <span data-ttu-id="e6505-123">열을 선택한 다음 **열 제거**를 클릭하여 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e6505-123">Select a column, and then remove it by clicking **Remove Column**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6505-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6505-124">See Also</span></span>  
 <span data-ttu-id="e6505-125">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e6505-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e6505-126">[스크립트 구성 요소 유형 선택](../../2014/integration-services/select-script-component-type.md) </span><span class="sxs-lookup"><span data-stu-id="e6505-126">[Select Script Component Type](../../2014/integration-services/select-script-component-type.md) </span></span>  
 <span data-ttu-id="e6505-127">[스크립트 변환 편집기 &#40;입력 열 페이지&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e6505-127">[Script Transformation Editor &#40;Input Columns Page&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md) </span></span>  
 <span data-ttu-id="e6505-128">[스크립트 변환 편집기 &#40;스크립트 페이지&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span><span class="sxs-lookup"><span data-stu-id="e6505-128">[Script Transformation Editor &#40;Script Page&#41;](../../2014/integration-services/script-transformation-editor-script-page.md) </span></span>  
 <span data-ttu-id="e6505-129">[스크립트 변환 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span><span class="sxs-lookup"><span data-stu-id="e6505-129">[Script Transformation Editor &#40;Connection Managers Page&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md) </span></span>  
 [<span data-ttu-id="e6505-130">추가 스크립트 구성 요소 예</span><span class="sxs-lookup"><span data-stu-id="e6505-130">Additional Script Component Examples</span></span>](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
