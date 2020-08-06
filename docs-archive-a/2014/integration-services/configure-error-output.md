---
title: 오류 출력 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.configureerroroutput.f1
ms.assetid: 5f8da390-fab5-44f8-b268-d8fa313ce4b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: de1a5908c6075438599f4108e9780f5591b042c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652274"
---
# <a name="configure-error-output"></a><span data-ttu-id="3b39f-102">오류 출력 구성</span><span class="sxs-lookup"><span data-stu-id="3b39f-102">Configure Error Output</span></span>
  <span data-ttu-id="3b39f-103">**오류 출력 구성** 대화 상자를 사용하여 오류 출력을 지원하는 데이터 흐름 변환에 대한 오류 처리 옵션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b39f-103">Use the **Configure Error Output** dialog box to configure error handling options for data flow transformations that support an error output.</span></span>  
  
 <span data-ttu-id="3b39f-104">오류 출력 작업 방법에 대한 자세한 내용은 [데이터 오류 처리](data-flow/error-handling-in-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b39f-104">To learn more about working with error outputs, see [Error Handling in Data](data-flow/error-handling-in-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3b39f-105">옵션</span><span class="sxs-lookup"><span data-stu-id="3b39f-105">Options</span></span>  
 <span data-ttu-id="3b39f-106">**입력 또는 출력**</span><span class="sxs-lookup"><span data-stu-id="3b39f-106">**Input or Output**</span></span>  
 <span data-ttu-id="3b39f-107">출력의 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3b39f-107">View the name of the output.</span></span>  
  
 <span data-ttu-id="3b39f-108">**열**</span><span class="sxs-lookup"><span data-stu-id="3b39f-108">**Column**</span></span>  
 <span data-ttu-id="3b39f-109">변환 편집기 대화 상자에서 선택한 출력 열을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b39f-109">View the output columns that you selected in the transformation editor dialog box.</span></span>  
  
 <span data-ttu-id="3b39f-110">**오류**</span><span class="sxs-lookup"><span data-stu-id="3b39f-110">**Error**</span></span>  
 <span data-ttu-id="3b39f-111">해당 사항이 있을 경우 오류 발생 시 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b39f-111">If applicable, specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="3b39f-112">**관련 항목:** [데이터 오류 처리](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="3b39f-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="3b39f-113">**잘림**</span><span class="sxs-lookup"><span data-stu-id="3b39f-113">**Truncation**</span></span>  
 <span data-ttu-id="3b39f-114">해당 사항이 있을 경우 잘림 발생 시 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b39f-114">If applicable, specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="3b39f-115">**관련 항목:** [데이터 오류 처리](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="3b39f-115">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="3b39f-116">**설명**</span><span class="sxs-lookup"><span data-stu-id="3b39f-116">**Description**</span></span>  
 <span data-ttu-id="3b39f-117">작업에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b39f-117">View the description of the operation.</span></span>  
  
 <span data-ttu-id="3b39f-118">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="3b39f-118">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="3b39f-119">오류나 잘림 발생 시 선택한 모든 셀에 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b39f-119">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="3b39f-120">**적용**</span><span class="sxs-lookup"><span data-stu-id="3b39f-120">**Apply**</span></span>  
 <span data-ttu-id="3b39f-121">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3b39f-121">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b39f-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b39f-122">See Also</span></span>  
 [<span data-ttu-id="3b39f-123">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="3b39f-123">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
