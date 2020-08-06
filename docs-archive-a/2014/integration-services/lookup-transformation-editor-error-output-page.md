---
title: 조회 변환 편집기 (오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.erroroutput.f1
ms.assetid: 15d53bb0-8be1-46fb-b459-04a397e75fac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9cd78f40a0072f7f0c5c923cdd51431873402f3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651097"
---
# <a name="lookup-transformation-editor-error-output-page"></a><span data-ttu-id="ce648-102">조회 변환 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="ce648-102">Lookup Transformation Editor (Error Output Page)</span></span>
  <span data-ttu-id="ce648-103">**조회 변환 편집기** 대화 상자의 **오류 출력** 페이지를 사용하여 오류 처리 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-103">Use the **Error Output** page of the **Lookup Transformation Editor** dialog box to specify error handling options.</span></span>  
  
 <span data-ttu-id="ce648-104">조회 변환에 대한 자세한 내용은 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce648-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ce648-105">옵션</span><span class="sxs-lookup"><span data-stu-id="ce648-105">Options</span></span>  
 <span data-ttu-id="ce648-106">**입/출력**</span><span class="sxs-lookup"><span data-stu-id="ce648-106">**Input/Output**</span></span>  
 <span data-ttu-id="ce648-107">입력 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-107">View the name of the input.</span></span>  
  
 <span data-ttu-id="ce648-108">**열**</span><span class="sxs-lookup"><span data-stu-id="ce648-108">**Column**</span></span>  
 <span data-ttu-id="ce648-109">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-109">Not used.</span></span>  
  
 <span data-ttu-id="ce648-110">**오류**</span><span class="sxs-lookup"><span data-stu-id="ce648-110">**Error**</span></span>  
 <span data-ttu-id="ce648-111">참조 데이터 세트에서 일치하는 항목이 없는 행을 처리할 때 발생하는 오류 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-111">Specify what type of error should occur when handling rows without matching entries in the reference dataset:</span></span>  
  
-   <span data-ttu-id="ce648-112">오류를 무시하고 행을 출력으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-112">Ignore the failure and direct the rows to an output.</span></span>  
  
-   <span data-ttu-id="ce648-113">행을 오류 출력으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-113">Redirect the rows to an error output.</span></span>  
  
-   <span data-ttu-id="ce648-114">구성 요소가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-114">Fail the component.</span></span>  
  
 <span data-ttu-id="ce648-115">**일치하는 항목이 없는 행 처리 방법 지정** 목록에서 **일치하는 항목이 없는 출력으로 행 리디렉션** 을 선택하는 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-115">This option is not available when you select **Redirect rows to no match output** in the **Specify how to handle rows with no matching entries** list.</span></span> <span data-ttu-id="ce648-116">이 목록은 **조회 변환 편집기** 대화 상자의 **일반** 페이지에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-116">This list is on the **General** page of the **Lookup Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="ce648-117">**관련 항목:** [데이터 오류 처리](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="ce648-117">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="ce648-118">**잘림**</span><span class="sxs-lookup"><span data-stu-id="ce648-118">**Truncation**</span></span>  
 <span data-ttu-id="ce648-119">데이터 잘림이 발생할 경우 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-119">Specify what should happen when data truncation occurs:</span></span>  
  
-   <span data-ttu-id="ce648-120">오류를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-120">Ignore the failure.</span></span>  
  
-   <span data-ttu-id="ce648-121">행을 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-121">Redirect the row.</span></span>  
  
-   <span data-ttu-id="ce648-122">구성 요소가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-122">Fail the component.</span></span>  
  
 <span data-ttu-id="ce648-123">**설명**</span><span class="sxs-lookup"><span data-stu-id="ce648-123">**Description**</span></span>  
 <span data-ttu-id="ce648-124">작업에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-124">View the description of the operation.</span></span>  
  
 <span data-ttu-id="ce648-125">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="ce648-125">**Set selected cells to this value**</span></span>  
 <span data-ttu-id="ce648-126">오류나 잘림 발생 시 선택한 모든 셀에 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-126">Specify what should happen to all the selected cells when an error or truncation occurs:</span></span>  
  
-   <span data-ttu-id="ce648-127">오류를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-127">Ignore the failure.</span></span>  
  
-   <span data-ttu-id="ce648-128">행을 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-128">Redirect the row.</span></span>  
  
-   <span data-ttu-id="ce648-129">구성 요소가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-129">Fail the component.</span></span>  
  
 <span data-ttu-id="ce648-130">**적용**</span><span class="sxs-lookup"><span data-stu-id="ce648-130">**Apply**</span></span>  
 <span data-ttu-id="ce648-131">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce648-131">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce648-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce648-132">See Also</span></span>  
 [<span data-ttu-id="ce648-133">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="ce648-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
