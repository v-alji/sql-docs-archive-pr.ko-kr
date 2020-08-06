---
title: Excel 대상 편집기 (오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldestadapter.erroroutput.f1
helpviewer_keywords:
- Excel Destination Editor
ms.assetid: 72ae01cc-1774-4a36-9674-a0f2b2bf8c42
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bee679f563105cade3053a13eb122f6d482a7d86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651796"
---
# <a name="excel-destination-editor-error-output-page"></a><span data-ttu-id="81ca9-102">Excel 대상 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="81ca9-102">Excel Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="81ca9-103">**Excel 대상 편집기** 대화 상자의 **고급** 페이지를 사용하여 오류 처리 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ca9-103">Use the **Advanced** page of the **Excel Destination Editor** dialog box to specify options for error handling.</span></span>  
  
 <span data-ttu-id="81ca9-104">Excel 대상에 대한 자세한 내용은 [Excel Destination](data-flow/excel-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="81ca9-104">To learn more about the Excel destination, see [Excel Destination](data-flow/excel-destination.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="81ca9-105">옵션</span><span class="sxs-lookup"><span data-stu-id="81ca9-105">Options</span></span>  
 <span data-ttu-id="81ca9-106">**입력 또는 출력**</span><span class="sxs-lookup"><span data-stu-id="81ca9-106">**Input or Output**</span></span>  
 <span data-ttu-id="81ca9-107">데이터 원본의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ca9-107">View the name of the data source.</span></span>  
  
 <span data-ttu-id="81ca9-108">**열**</span><span class="sxs-lookup"><span data-stu-id="81ca9-108">**Column**</span></span>  
 <span data-ttu-id="81ca9-109">**Excel 원본 편집기** 대화 상자의 **연결 관리자**노드에서 선택한 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ca9-109">View the external (source) columns that you selected in the **Connection Manager** node of the **Excel Source Editor**dialog box.</span></span>  
  
 <span data-ttu-id="81ca9-110">**오류**</span><span class="sxs-lookup"><span data-stu-id="81ca9-110">**Error**</span></span>  
 <span data-ttu-id="81ca9-111">오류가 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ca9-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="81ca9-112">**관련 항목:** [데이터 오류 처리](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="81ca9-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="81ca9-113">**잘림**</span><span class="sxs-lookup"><span data-stu-id="81ca9-113">**Truncation**</span></span>  
 <span data-ttu-id="81ca9-114">잘림이 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ca9-114">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="81ca9-115">**설명**</span><span class="sxs-lookup"><span data-stu-id="81ca9-115">**Description**</span></span>  
 <span data-ttu-id="81ca9-116">오류에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81ca9-116">View the description of the error.</span></span>  
  
 <span data-ttu-id="81ca9-117">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="81ca9-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="81ca9-118">오류나 잘림 발생 시 선택한 모든 셀에 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81ca9-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="81ca9-119">**적용**</span><span class="sxs-lookup"><span data-stu-id="81ca9-119">**Apply**</span></span>  
 <span data-ttu-id="81ca9-120">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="81ca9-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ca9-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81ca9-121">See Also</span></span>  
 <span data-ttu-id="81ca9-122">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="81ca9-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="81ca9-123">[Excel 대상 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/excel-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="81ca9-123">[Excel Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/excel-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="81ca9-124">[Excel 대상 편집기 &#40;매핑 페이지&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="81ca9-124">[Excel Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="81ca9-125">Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑</span><span class="sxs-lookup"><span data-stu-id="81ca9-125">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
