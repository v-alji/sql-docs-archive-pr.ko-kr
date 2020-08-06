---
title: 열 내보내기 변환 편집기 (오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.errorhandling.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: 260be463-01a9-460c-9c98-e5265cb2b1e9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04a9c277bb4aaa28933d443bd12e6c2b39ed844e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743391"
---
# <a name="export-column-transformation-editor-error-output-page"></a><span data-ttu-id="b0c12-102">열 내보내기 변환 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="b0c12-102">Export Column Transformation Editor (Error Output Page)</span></span>
  <span data-ttu-id="b0c12-103">**열 내보내기 변환 편집기** 대화 상자의 **오류 출력** 페이지를 사용하여 오류 처리 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0c12-103">Use the **Error Output** page of the **Export Column Transformation Editor** dialog box to specify how to handle errors.</span></span>  
  
 <span data-ttu-id="b0c12-104">열 내보내기 변환에 대한 자세한 내용은 [Export Column Transformation](data-flow/transformations/export-column-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b0c12-104">To learn more about the Export Column transformation, see [Export Column Transformation](data-flow/transformations/export-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b0c12-105">옵션</span><span class="sxs-lookup"><span data-stu-id="b0c12-105">Options</span></span>  
 <span data-ttu-id="b0c12-106">**입/출력**</span><span class="sxs-lookup"><span data-stu-id="b0c12-106">**Input/Output**</span></span>  
 <span data-ttu-id="b0c12-107">출력의 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b0c12-107">View the name of the output.</span></span> <span data-ttu-id="b0c12-108">이름을 클릭하여 열을 포함할 뷰를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0c12-108">Click the name to expand the view to include columns.</span></span>  
  
 <span data-ttu-id="b0c12-109">**열**</span><span class="sxs-lookup"><span data-stu-id="b0c12-109">**Column**</span></span>  
 <span data-ttu-id="b0c12-110">**열 내보내기 변환 편집기** 대화 상자의 **열** 페이지에서 선택한 출력 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b0c12-110">View the output columns that you selected on the **Columns** page of the **Export Column Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="b0c12-111">**오류**</span><span class="sxs-lookup"><span data-stu-id="b0c12-111">**Error**</span></span>  
 <span data-ttu-id="b0c12-112">오류가 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0c12-112">Specify what you want to happen if an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="b0c12-113">**잘림**</span><span class="sxs-lookup"><span data-stu-id="b0c12-113">**Truncation**</span></span>  
 <span data-ttu-id="b0c12-114">잘림이 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0c12-114">Specify what you want to happen if a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="b0c12-115">**설명**</span><span class="sxs-lookup"><span data-stu-id="b0c12-115">**Description**</span></span>  
 <span data-ttu-id="b0c12-116">작업에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b0c12-116">View the description of the operation.</span></span>  
  
 <span data-ttu-id="b0c12-117">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="b0c12-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="b0c12-118">오류나 잘림 발생 시 선택한 모든 셀에 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0c12-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="b0c12-119">**적용**</span><span class="sxs-lookup"><span data-stu-id="b0c12-119">**Apply**</span></span>  
 <span data-ttu-id="b0c12-120">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b0c12-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c12-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0c12-121">See Also</span></span>  
 <span data-ttu-id="b0c12-122">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b0c12-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="b0c12-123">열 내보내기 변환 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b0c12-123">Export Column Transformation Editor &#40;Columns Page&#41;</span></span>](../../2014/integration-services/export-column-transformation-editor-columns-page.md)  
  
  
