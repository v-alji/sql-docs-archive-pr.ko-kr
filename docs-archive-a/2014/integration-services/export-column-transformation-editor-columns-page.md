---
title: 열 내보내기 변환 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 404b404e2328228049ae46fb1c3089b0b4089f0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649118"
---
# <a name="export-column-transformation-editor-columns-page"></a><span data-ttu-id="587d5-102">열 내보내기 변환 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="587d5-102">Export Column Transformation Editor (Columns Page)</span></span>
  <span data-ttu-id="587d5-103">**열 내보내기 변환 편집기** 대화 상자의 **열** 페이지를 사용하여 데이터 흐름에서 파일로 추출할 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-103">Use the **Columns** page of the **Export Column Transformation Editor** dialog box to specify columns in the data flow to extract to files.</span></span> <span data-ttu-id="587d5-104">열 내보내기 변환 시 데이터를 파일에 추가할 것인지, 아니면 기존 파일을 덮어쓸 것인지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-104">You can specify whether the Export Column transformation appends data to a file or overwrites an existing file.</span></span>  
  
 <span data-ttu-id="587d5-105">열 내보내기 변환에 대한 자세한 내용은 [Export Column Transformation](data-flow/transformations/export-column-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="587d5-105">To learn more about the Export Column transformation, see [Export Column Transformation](data-flow/transformations/export-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="587d5-106">옵션</span><span class="sxs-lookup"><span data-stu-id="587d5-106">Options</span></span>  
 <span data-ttu-id="587d5-107">**추출 열**</span><span class="sxs-lookup"><span data-stu-id="587d5-107">**Extract Column**</span></span>  
 <span data-ttu-id="587d5-108">텍스트 또는 이미지 데이터를 포함하는 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-108">Select from the list of input columns that contain text or image data.</span></span> <span data-ttu-id="587d5-109">모든 행에 **추출 열** 과 **파일 경로 열**에 대한 정의가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-109">All rows should have definitions for **Extract Column** and **File Path Column**.</span></span>  
  
 <span data-ttu-id="587d5-110">**파일 경로 열**</span><span class="sxs-lookup"><span data-stu-id="587d5-110">**File Path Column**</span></span>  
 <span data-ttu-id="587d5-111">파일 경로 및 파일 이름을 포함하는 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-111">Select from the list of input columns that contain file paths and file names.</span></span> <span data-ttu-id="587d5-112">모든 행에 **추출 열** 과 **파일 경로 열**에 대한 정의가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-112">All rows should have definitions for **Extract Column** and **File Path Column**.</span></span>  
  
 <span data-ttu-id="587d5-113">**추가 허용**</span><span class="sxs-lookup"><span data-stu-id="587d5-113">**Allow Append**</span></span>  
 <span data-ttu-id="587d5-114">변환 시 데이터를 기존 파일에 추가할 것인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-114">Specify whether the transformation appends data to existing files.</span></span> <span data-ttu-id="587d5-115">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-115">The default is `false`.</span></span>  
  
 <span data-ttu-id="587d5-116">**강제 자름**</span><span class="sxs-lookup"><span data-stu-id="587d5-116">**Force Truncate**</span></span>  
 <span data-ttu-id="587d5-117">변환 시 데이터를 쓰기 전에 기존 파일의 내용을 삭제할 것인지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-117">Specify whether the transformation deletes the contents of existing files before writing data.</span></span> <span data-ttu-id="587d5-118">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-118">The default is `false`.</span></span>  
  
 <span data-ttu-id="587d5-119">**BOM 쓰기**</span><span class="sxs-lookup"><span data-stu-id="587d5-119">**Write BOM**</span></span>  
 <span data-ttu-id="587d5-120">BOM(바이트 순서 표시)을 파일에 쓸 것인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-120">Specify whether to write a byte-order mark (BOM) to the file.</span></span> <span data-ttu-id="587d5-121">데이터 형식이 `DT_NTEXT` 또는 DT_WSTR이고 기존 데이터 파일에 추가되지 않는 경우에만 BOM을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="587d5-121">A BOM is only written if the data has the `DT_NTEXT` or DT_WSTR data type and is not appended to an existing data file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="587d5-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="587d5-122">See Also</span></span>  
 <span data-ttu-id="587d5-123">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="587d5-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="587d5-124">열 내보내기 변환 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="587d5-124">Export Column Transformation Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
