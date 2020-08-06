---
title: 가변 눈금 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.variableoptionswindow.f1
helpviewer_keywords:
- Choose Variable Columns dialog box
ms.assetid: 7cccc230-3b20-4074-804f-3448d9616a83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b90e1a3c69e4eaf1f123603e0082ecb1eda4e893
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647734"
---
# <a name="variable-grid-options"></a><span data-ttu-id="cbe57-102">가변 눈금 옵션</span><span class="sxs-lookup"><span data-stu-id="cbe57-102">Variable Grid Options</span></span>
  <span data-ttu-id="cbe57-103">**가변 눈금 옵션** 대화 상자를 사용하여 **변수** 창에 표시될 열을 선택하고 변수 목록에 적용할 필터를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-103">Use the **Variable Grid Options** dialog box to select the columns that will display in the **Variables** window and to select the filters to apply to the list of variables.</span></span> <span data-ttu-id="cbe57-104">해당 변수 속성에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cbe57-104">For more information about the corresponding variable properties, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
## <a name="options-for-filter"></a><span data-ttu-id="cbe57-105">필터 옵션</span><span class="sxs-lookup"><span data-stu-id="cbe57-105">Options for Filter</span></span>  
 <span data-ttu-id="cbe57-106">**시스템 변수 표시**</span><span class="sxs-lookup"><span data-stu-id="cbe57-106">**Show system variables**</span></span>  
 <span data-ttu-id="cbe57-107">**변수** 창에 시스템 변수를 나열하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-107">Select to list system variables in the **Variables** window.</span></span> <span data-ttu-id="cbe57-108">시스템 변수는 미리 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-108">System variables are predefined.</span></span> <span data-ttu-id="cbe57-109">시스템 변수는 추가하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-109">You cannot add or delete system variables.</span></span> <span data-ttu-id="cbe57-110">**RaiseChangedEvent** 속성 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-110">You can modify the **RaiseChangedEvent** property setting.</span></span>  
  
 <span data-ttu-id="cbe57-111">이 목록은 색으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-111">This list is color coded.</span></span> <span data-ttu-id="cbe57-112">시스템 변수는 회색으로 표시되고 사용자 정의 변수는 검은색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-112">System variables are gray, and user-defined variables are black.</span></span>  
  
 <span data-ttu-id="cbe57-113">**모든 범위의 변수 표시**</span><span class="sxs-lookup"><span data-stu-id="cbe57-113">**Show variables of all scopes**</span></span>  
 <span data-ttu-id="cbe57-114">패키지의 범위 내에 있는 변수와 패키지의 컨테이너, 태스크 또는 이벤트 처리기의 범위 내에 있는 변수를 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-114">Select to show variables within the scope the package, and within the scope of containers, tasks, and event handlers in the package.</span></span> <span data-ttu-id="cbe57-115">패키지의 범위 내에 있는 변수와 선택된 컨테이너, 태스크 또는 이벤트 처리기의 범위 내에 있는 변수만 표시하려면 이 옵션의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-115">Clear this option to show only variables within the scope of the package and within the scope of a selected container, task, or event handler.</span></span>  
  
 <span data-ttu-id="cbe57-116">변수 범위에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md)영역 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-116">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
## <a name="options-for-columns"></a><span data-ttu-id="cbe57-117">열 옵션</span><span class="sxs-lookup"><span data-stu-id="cbe57-117">Options for Columns</span></span>  
 <span data-ttu-id="cbe57-118">**변수** 창에 표시할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe57-118">Select the columns that you want to appear in the **Variables** window.</span></span>  
  
-   <span data-ttu-id="cbe57-119">**범위**</span><span class="sxs-lookup"><span data-stu-id="cbe57-119">**Scope**</span></span>  
  
-   <span data-ttu-id="cbe57-120">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="cbe57-120">**Data type**</span></span>  
  
-   <span data-ttu-id="cbe57-121">**값**</span><span class="sxs-lookup"><span data-stu-id="cbe57-121">**Value**</span></span>  
  
-   <span data-ttu-id="cbe57-122">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="cbe57-122">**Namespace**</span></span>  
  
-   <span data-ttu-id="cbe57-123">**변수 값 변경 시 이벤트 발생**</span><span class="sxs-lookup"><span data-stu-id="cbe57-123">**Raise event when variable value changes**</span></span>  
  
-   <span data-ttu-id="cbe57-124">**설명**</span><span class="sxs-lookup"><span data-stu-id="cbe57-124">**Description**</span></span>  
  
-   <span data-ttu-id="cbe57-125">**식**</span><span class="sxs-lookup"><span data-stu-id="cbe57-125">**Expression**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe57-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cbe57-126">See Also</span></span>  
 <span data-ttu-id="cbe57-127">[변수 창](../../2014/integration-services/variables-window.md) </span><span class="sxs-lookup"><span data-stu-id="cbe57-127">[Variables Window](../../2014/integration-services/variables-window.md) </span></span>  
 <span data-ttu-id="cbe57-128">[Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="cbe57-128">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="cbe57-129">[패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="cbe57-129">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 [<span data-ttu-id="cbe57-130">Integration Services&#40;SSIS&#41; 이벤트 처리기</span><span class="sxs-lookup"><span data-stu-id="cbe57-130">Integration Services &#40;SSIS&#41; Event Handlers</span></span>](integration-services-ssis-event-handlers.md)  
  
  
