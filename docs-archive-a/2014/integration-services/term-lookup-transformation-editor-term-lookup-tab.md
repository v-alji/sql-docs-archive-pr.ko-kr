---
title: 용어 조회 변환 편집기 (용어 조회 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bb8c0bd0477d9883640cc3e4d3cb25c2a3a8b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660675"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a><span data-ttu-id="32564-102">용어 조회 변환 편집기(용어 조회 탭)</span><span class="sxs-lookup"><span data-stu-id="32564-102">Term Lookup Transformation Editor (Term Lookup Tab)</span></span>
  <span data-ttu-id="32564-103">**용어 조회 변환 편집기** 대화 상자의 **용어 조회** 탭을 사용하여 입력 열을 참조 테이블의 조회 열로 매핑하고 각 출력 열의 별칭을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32564-103">Use the **Term Lookup** tab of the **Term Lookup Transformation Editor** dialog box to map an input column to a lookup column in a reference table and to provide an alias for each output column.</span></span>  
  
 <span data-ttu-id="32564-104">용어 조회 변환에 대한 자세한 내용은 [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="32564-104">To learn more about the Term Lookup transformation, see [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="32564-105">옵션</span><span class="sxs-lookup"><span data-stu-id="32564-105">Options</span></span>  
 <span data-ttu-id="32564-106">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="32564-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="32564-107">확인란을 사용하여 변경되지 않은 출력 열로 전달할 입력 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="32564-107">Using the check boxes, select input columns to pass through to the output unchanged.</span></span> <span data-ttu-id="32564-108">입력 열을 **사용 가능한 참조 열** 목록으로 끌어서 참조 테이블의 조회 열로 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32564-108">Drag an input column to the **Available Reference Columns** list to map it to a lookup column in the reference table.</span></span> <span data-ttu-id="32564-109">입력 및 조회 열에 일치하는 지원 데이터 형식 DT_NTEXT 또는 DT_WSTR이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="32564-109">The input and lookup columns must have matching, supported data types, either DT_NTEXT or DT_WSTR.</span></span> <span data-ttu-id="32564-110">매핑 선을 선택하고 마우스 오른쪽 단추를 클릭하여 [관계 만들기](data-flow/transformations/create-relationships.md) 대화 상자에서 매핑을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="32564-110">Select a mapping line and right-click to edit the mappings in the [Create Relationships](data-flow/transformations/create-relationships.md) dialog box.</span></span>  
  
 <span data-ttu-id="32564-111">**사용 가능한 참조 열**</span><span class="sxs-lookup"><span data-stu-id="32564-111">**Available Reference Columns**</span></span>  
 <span data-ttu-id="32564-112">참조 테이블에서 사용 가능한 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="32564-112">View the available columns in the reference table.</span></span> <span data-ttu-id="32564-113">일치시킬 용어 목록이 포함된 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="32564-113">Choose the column that contains the list of terms to match.</span></span>  
  
 <span data-ttu-id="32564-114">**통과 열**</span><span class="sxs-lookup"><span data-stu-id="32564-114">**Pass-Through Column**</span></span>  
 <span data-ttu-id="32564-115">사용 가능한 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="32564-115">Select from the list of available input columns.</span></span> <span data-ttu-id="32564-116">선택 내용에 따라 **사용 가능한 입력 열** 테이블의 확인란이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="32564-116">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="32564-117">**출력 열 별칭**</span><span class="sxs-lookup"><span data-stu-id="32564-117">**Output Column Alias**</span></span>  
 <span data-ttu-id="32564-118">각 출력 열의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="32564-118">Type an alias for each output column.</span></span> <span data-ttu-id="32564-119">기본값은 열 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32564-119">The default is the name of the column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="32564-120">**오류 출력 구성**</span><span class="sxs-lookup"><span data-stu-id="32564-120">**Configure Error Output**</span></span>  
 <span data-ttu-id="32564-121">[오류 출력 구성](../../2014/integration-services/configure-error-output.md) 대화 상자를 사용하여 오류 발생의 원인이 되는 행에 대한 오류 처리 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32564-121">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32564-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32564-122">See Also</span></span>  
 <span data-ttu-id="32564-123">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="32564-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="32564-124">[용어 조회 변환 편집기 &#40;참조 테이블 탭&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="32564-124">[Term Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 <span data-ttu-id="32564-125">[용어 조회 변환 편집기 &#40;고급 탭&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="32564-125">[Term Lookup Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="32564-126">용어 추출 변환</span><span class="sxs-lookup"><span data-stu-id="32564-126">Term Extraction Transformation</span></span>](data-flow/transformations/term-extraction-transformation.md)  
  
  
