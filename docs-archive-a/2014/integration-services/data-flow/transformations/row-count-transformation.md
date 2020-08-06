---
title: 행 개수 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b0940d608aeaa96b7ec43fa4486944ce0f887e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743412"
---
# <a name="row-count-transformation"></a><span data-ttu-id="57de1-102">행 개수 변환</span><span class="sxs-lookup"><span data-stu-id="57de1-102">Row Count Transformation</span></span>
  <span data-ttu-id="57de1-103">행 개수 변환은 행이 데이터 흐름을 통과할 때 행 수를 세어 최종 개수를 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="57de1-103">The Row Count transformation counts rows as they pass through a data flow and stores the final count in a variable.</span></span>  
  
 <span data-ttu-id="57de1-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 패키지는 행 개수를 사용하여 스크립트, 식 및 속성 식에 사용된 변수를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57de1-104">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package can use row counts to update the variables used in scripts, expressions, and property expressions.</span></span> <span data-ttu-id="57de1-105">(예를 들어 행 개수가 저장되는 변수는 행 개수가 포함되도록 전자 메일 메시지의 메시지 텍스트를 업데이트할 수 있습니다.) 행 개수 변환에 사용되는 변수는 이미 존재해야 하며 행 개수 변환이 포함된 데이터 흐름이 속해 있는 데이터 흐름 태스크의 범위 내에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57de1-105">(For example, the variable that stores the row count can update the message text in an e-mail message to include the number of rows.) The variable that the Row Count transformation uses must already exist, and it must be in the scope of the Data Flow task to which the data flow with the Row Count transformation belongs.</span></span>  
  
 <span data-ttu-id="57de1-106">변환에서는 마지막 행이 변환을 통과한 후에만 변수에 행 개수 값을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="57de1-106">The transformation stores the row count value in the variable only after the last row has passed through the transformation.</span></span> <span data-ttu-id="57de1-107">따라서 변수 값은 행 개수 변환이 포함된 데이터 흐름에서 업데이트된 값을 사용할 수 있도록 적시에 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57de1-107">Therefore, the value of the variable is not updated in time to use the updated value in the data flow that contains the Row Count transformation.</span></span> <span data-ttu-id="57de1-108">업데이트된 변수는 별도의 데이터 흐름에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57de1-108">You can use the updated variable in a separate data flow.</span></span>  
  
 <span data-ttu-id="57de1-109">이 변환은 하나의 입력과 하나의 출력을 가지며</span><span class="sxs-lookup"><span data-stu-id="57de1-109">This transformation has one input and one output.</span></span> <span data-ttu-id="57de1-110">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57de1-110">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-row-count-transformation"></a><span data-ttu-id="57de1-111">행 개수 변환 구성</span><span class="sxs-lookup"><span data-stu-id="57de1-111">Configuration of the Row Count Transformation</span></span>  
 <span data-ttu-id="57de1-112">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57de1-112">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="57de1-113">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="57de1-113">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="57de1-114">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="57de1-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="57de1-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="57de1-115">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="57de1-116">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="57de1-116">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="57de1-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="57de1-117">Related Tasks</span></span>  
 <span data-ttu-id="57de1-118">이 구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="57de1-118">For information about how to set the properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57de1-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57de1-119">See Also</span></span>  
 <span data-ttu-id="57de1-120">[Integration Services&#40;SSIS&#41; 변수](../../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="57de1-120">[Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="57de1-121">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="57de1-121">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="57de1-122">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="57de1-122">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
