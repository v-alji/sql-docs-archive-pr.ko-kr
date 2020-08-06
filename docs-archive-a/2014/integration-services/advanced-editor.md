---
title: 고급 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.advancededitor.columnmappings.f1
- sql12.dts.designer.advancededitor.inputcolumns.f1
- sql12.dts.designer.advancededitor.columnproperties.f1
- sql12.dts.designer.advancededitor.componentproperties.f1
- sql12.dts.designer.advancededitor.connections.f1
ms.assetid: 5ad0ac71-fa8b-4c26-bd42-e6ef00c87571
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f4897f2589acdeb93efecbdf9aacde07d21ca42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648530"
---
# <a name="advanced-editor"></a><span data-ttu-id="5905a-102">고급 편집기</span><span class="sxs-lookup"><span data-stu-id="5905a-102">Advanced Editor</span></span>
  <span data-ttu-id="5905a-103">**고급 편집기** 대화 상자를 사용하여 선택한 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체의 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-103">Use the **Advanced Editor** dialog box to configure to configure properties for the selected [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="5905a-104">**고급 편집기** 는 구성 가능한 속성이 있는 대부분의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-104">The **Advanced Editor** is available for most [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects that have configurable properties.</span></span> <span data-ttu-id="5905a-105">이 편집기는 사용자 지정 사용자 인터페이스를 노출하지 않는 개체에 사용할 수 있는 유일한 편집기입니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-105">It is the only editor available for those objects that do not expose a custom user interface.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="5905a-106">데이터 흐름 개체에는 구성 요소 수준, 입/출력 수준 및 입/출력 열 수준에서 설정할 수 있는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-106">data flow objects have properties that can be set at the component level, the input and output level, and the input and output column level.</span></span> <span data-ttu-id="5905a-107">**고급 편집기** 는 선택한 개체의 모든 공용 속성과 사용자 지정 속성을 열거하고 해당될 경우 다음 5개 탭 중에서 최대 4개 탭에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-107">The **Advanced Editor** enumerates all the common and custom properties of the selected object and displays them on up to four of the following five tabs as applicable:</span></span>  
  
-   <span data-ttu-id="5905a-108">**연결 관리자** - 이 탭을 사용하여 연결 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-108">**Connection Managers** -- use this tab to set connection properties</span></span>  
  
-   <span data-ttu-id="5905a-109">**구성 요소 속성** - 이 탭을 사용하여 구성 요소 수준의 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-109">**Component Properties** -- use this tab to set component-level properties</span></span>  
  
-   <span data-ttu-id="5905a-110">**열 매핑** - 이 탭을 사용하여 사용 가능한 열을 출력 열로 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-110">**Column Mappings** -- use this tab to map available columns as output columns</span></span>  
  
-   <span data-ttu-id="5905a-111">**입력 열** - 이 탭을 사용하여 입력 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-111">**Input Columns** -- use this tab to select input columns</span></span>  
  
-   <span data-ttu-id="5905a-112">**입/출력 속성** - 이 탭을 사용하여 입력 및 출력 속성을 설정하고, 출력을 추가 및 제거하고, 입력 및 출력 열을 선택하거나 제거하고, 입력 및 출력에 대한 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-112">**Input and Output Properties** -- use this tab to set input and output properties; and to add and remove outputs, select or remove columns for inputs and outputs, and set properties for inputs and outputs</span></span>  
  
 <span data-ttu-id="5905a-113">구성 요소에 따라 다른 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5905a-113">The properties displayed vary by component.</span></span> <span data-ttu-id="5905a-114">**고급 편집기**에 표시될 수 있는 속성에 대한 자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5905a-114">For more information on the properties that may be displayed in the **Advanced Editor**, see the following topics:</span></span>  
  
-   [<span data-ttu-id="5905a-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="5905a-115">Common Properties</span></span>](../../2014/integration-services/common-properties.md)  
  
-   [<span data-ttu-id="5905a-116">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="5905a-116">Transformation Custom Properties</span></span>](data-flow/transformations/transformation-custom-properties.md)  
  
-   [<span data-ttu-id="5905a-117">경로 속성</span><span class="sxs-lookup"><span data-stu-id="5905a-117">Path Properties</span></span>](../../2014/integration-services/path-properties.md)  
  
 <span data-ttu-id="5905a-118">편집하는 특정 구성 요소에 대한 자세한 내용은 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 및 개념 설명서의 데이터 흐름 요소 섹션에서 구성 요소 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5905a-118">For more information about the specific component that you are editing, see the description of the component in the Data Flow Elements section of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Objects and Concepts documentation:</span></span>  
  
-   [<span data-ttu-id="5905a-119">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="5905a-119">Integration Services Transformations</span></span>](data-flow/transformations/integration-services-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="5905a-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5905a-120">See Also</span></span>  
 [<span data-ttu-id="5905a-121">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="5905a-121">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
