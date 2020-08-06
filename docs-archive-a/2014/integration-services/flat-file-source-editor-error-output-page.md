---
title: 플랫 파일 원본 편집기 (오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.errorhandling.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: c50500e7-0c74-42a0-865f-301f03feffab
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 096de22c65d605fc1beea06cbb6ad5909788b408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647142"
---
# <a name="flat-file-source-editor-error-output-page"></a><span data-ttu-id="8b42b-102">플랫 파일 원본 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="8b42b-102">Flat File Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="8b42b-103">**플랫 파일 원본 편집기** 대화 상자의 **오류 출력** 페이지를 사용하여 오류 처리 옵션을 선택하고 오류 출력 열의 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b42b-103">Use the **Error Output** page of the **Flat File Source Editor** dialog box to select error-handling options and to set properties on error output columns.\</span></span>  
  
 <span data-ttu-id="8b42b-104">플랫 파일 원본에 대한 자세한 내용은 [Flat File Source](data-flow/flat-file-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b42b-104">To learn more about the Flat File source, see [Flat File Source](data-flow/flat-file-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8b42b-105">옵션</span><span class="sxs-lookup"><span data-stu-id="8b42b-105">Options</span></span>  
 <span data-ttu-id="8b42b-106">**입/출력**</span><span class="sxs-lookup"><span data-stu-id="8b42b-106">**Input/Output**</span></span>  
 <span data-ttu-id="8b42b-107">데이터 원본의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8b42b-107">View the name of the data source.</span></span>  
  
 <span data-ttu-id="8b42b-108">**열**</span><span class="sxs-lookup"><span data-stu-id="8b42b-108">**Column**</span></span>  
 <span data-ttu-id="8b42b-109">**플랫 파일 원본 편집기** 대화 상자의 **연결 관리자**페이지에서 선택한 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8b42b-109">View the external (source) columns that you selected on the **Connection Manager** page of the **Flat File Source Editor**dialog box.</span></span>  
  
 <span data-ttu-id="8b42b-110">**오류**</span><span class="sxs-lookup"><span data-stu-id="8b42b-110">**Error**</span></span>  
 <span data-ttu-id="8b42b-111">오류가 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b42b-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="8b42b-112">**관련 항목:** [데이터 오류 처리](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="8b42b-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="8b42b-113">**잘림**</span><span class="sxs-lookup"><span data-stu-id="8b42b-113">**Truncation**</span></span>  
 <span data-ttu-id="8b42b-114">잘림이 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b42b-114">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="8b42b-115">**설명**</span><span class="sxs-lookup"><span data-stu-id="8b42b-115">**Description**</span></span>  
 <span data-ttu-id="8b42b-116">오류에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8b42b-116">View the description of the error.</span></span>  
  
 <span data-ttu-id="8b42b-117">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="8b42b-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="8b42b-118">오류나 잘림 발생 시 선택한 모든 셀에 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b42b-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="8b42b-119">**적용**</span><span class="sxs-lookup"><span data-stu-id="8b42b-119">**Apply**</span></span>  
 <span data-ttu-id="8b42b-120">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b42b-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b42b-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8b42b-121">See Also</span></span>  
 <span data-ttu-id="8b42b-122">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8b42b-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="8b42b-123">[플랫 파일 원본 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="8b42b-123">[Flat File Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="8b42b-124">[플랫 파일 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="8b42b-124">[Flat File Source Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="8b42b-125">플랫 파일 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="8b42b-125">Flat File Connection Manager</span></span>](connection-manager/file-connection-manager.md)  
  
  
