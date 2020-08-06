---
title: Foreach 루프 편집기 (변수 매핑 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd37c8c6c00f18d8b5493a058239cc880ecc1f5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743379"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a><span data-ttu-id="243d6-102">Foreach 루프 편집기(변수 매핑 페이지)</span><span class="sxs-lookup"><span data-stu-id="243d6-102">Foreach Loop Editor (Variable Mappings Page)</span></span>
  <span data-ttu-id="243d6-103">**Foreach 루프 편집기** 대화 상자의 **변수 매핑** 페이지를 사용하여 변수를 컬렉션 값에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-103">Use the **Variables Mappings** page of the **Foreach Loop Editor** dialog box to map variables to the collection value.</span></span> <span data-ttu-id="243d6-104">변수 값은 루프가 반복될 때마다 컬렉션 값으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-104">The value of the variable is updated with the collection values on each iteration of the loop.</span></span>  
  
 <span data-ttu-id="243d6-105">Integration Services 패키지의 Foreach 루프 컨테이너를 사용하는 방법은 [Foreach Loop Container](control-flow/foreach-loop-container.md) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="243d6-105">To learn about how to use the Foreach Loop container in an Integration Services package,  see [Foreach Loop Container](control-flow/foreach-loop-container.md) .</span></span> <span data-ttu-id="243d6-106">구성 방법에 대한 자세한 내용은 [Foreach 루프 컨테이너 구성](../../2014/integration-services/configure-a-foreach-loop-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="243d6-106">To learn about how to configure it, see [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="243d6-107">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 자습서인 간단한 ETL 패키지 만들기 자습서에는 Foreach 루프를 추가 및 구성하는 방법을 배울 수 있는 단원이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-107">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorial, Creating a Simple ETL Package Tutorial, includes a lesson that teaches you to add and configure a Foreach Loop.</span></span>  
  
## <a name="options"></a><span data-ttu-id="243d6-108">옵션</span><span class="sxs-lookup"><span data-stu-id="243d6-108">Options</span></span>  
 <span data-ttu-id="243d6-109">**변수**</span><span class="sxs-lookup"><span data-stu-id="243d6-109">**Variable**</span></span>  
 <span data-ttu-id="243d6-110">기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-110">Select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="243d6-111">변수를 매핑하면 새 행이 **변수** 목록에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-111">After you map a variable, a new row is automatically added to the **Variable** list.</span></span>  
  
 <span data-ttu-id="243d6-112">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="243d6-112">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="243d6-113">**Index**</span><span class="sxs-lookup"><span data-stu-id="243d6-113">**Index**</span></span>  
 <span data-ttu-id="243d6-114">Foreach Item 열거자를 사용하는 경우 컬렉션 값에서 변수에 매핑할 열의 인덱스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-114">If using the Foreach Item enumerator, specify the index of the column in the collection value to map to the variable.</span></span> <span data-ttu-id="243d6-115">다른 유형의 열거자를 사용하는 경우 인덱스는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-115">For other enumerator types, the index is read-only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="243d6-116">인덱스는 0부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-116">The index is 0-based.</span></span>  
  
 <span data-ttu-id="243d6-117">**관련 항목**: [Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)</span><span class="sxs-lookup"><span data-stu-id="243d6-117">**Related Topics**: [Loop through Excel Files and Tables by Using a Foreach Loop Container](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)</span></span>  
  
 <span data-ttu-id="243d6-118">**Delete**</span><span class="sxs-lookup"><span data-stu-id="243d6-118">**Delete**</span></span>  
 <span data-ttu-id="243d6-119">변수를 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="243d6-119">Select a variable, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="243d6-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="243d6-120">See Also</span></span>  
 <span data-ttu-id="243d6-121">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="243d6-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="243d6-122">[Foreach 루프 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="243d6-122">[Foreach Loop Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="243d6-123">[Foreach 루프 편집기 &#40;컬렉션 페이지&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md) </span><span class="sxs-lookup"><span data-stu-id="243d6-123">[Foreach Loop Editor &#40;Collection Page&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md) </span></span>  
 <span data-ttu-id="243d6-124">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="243d6-124">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="243d6-125">For 루프 컨테이너</span><span class="sxs-lookup"><span data-stu-id="243d6-125">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
