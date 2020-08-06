---
title: Excel 원본 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsourceadapter.columns.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 50024686-a18d-4824-b20e-c84123f89d0b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0713d8d3d0c1f56bf322684a924a286e8b81af55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651793"
---
# <a name="excel-source-editor-columns-page"></a><span data-ttu-id="4b70f-102">Excel 원본 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="4b70f-102">Excel Source Editor (Columns Page)</span></span>
  <span data-ttu-id="4b70f-103">**Excel 원본 편집기** 대화 상자의 **열** 페이지를 사용하여 출력 열을 각 외부(원본) 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b70f-103">Use the **Columns** page of the **Excel Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="4b70f-104">Excel 원본에 대한 자세한 내용은 [Excel Source](data-flow/excel-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b70f-104">To learn more about the Excel source, see [Excel Source](data-flow/excel-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4b70f-105">옵션</span><span class="sxs-lookup"><span data-stu-id="4b70f-105">Options</span></span>  
 <span data-ttu-id="4b70f-106">**사용 가능한 외부 열**</span><span class="sxs-lookup"><span data-stu-id="4b70f-106">**Available External Columns**</span></span>  
 <span data-ttu-id="4b70f-107">데이터 원본에서 사용 가능한 외부 열의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4b70f-107">View the list of available external columns in the data source.</span></span> <span data-ttu-id="4b70f-108">이 테이블을 사용하여 열을 추가하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b70f-108">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="4b70f-109">**외부 열**</span><span class="sxs-lookup"><span data-stu-id="4b70f-109">**External Column**</span></span>  
 <span data-ttu-id="4b70f-110">태스크에서 읽는 순서대로 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4b70f-110">View external (source) columns in the order in which the task will read them.</span></span> <span data-ttu-id="4b70f-111">이 순서는 먼저 위에 설명된 테이블에서 선택된 열을 지운 다음 목록에서 다른 순서로 외부 열을 선택하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b70f-111">You can change this order by first clearing the selected columns in the table discussed above, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="4b70f-112">**출력 열**</span><span class="sxs-lookup"><span data-stu-id="4b70f-112">**Output Column**</span></span>  
 <span data-ttu-id="4b70f-113">각 출력 열에 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b70f-113">Provide a unique name for each output column.</span></span> <span data-ttu-id="4b70f-114">기본값은 선택한 외부(원본) 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b70f-114">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="4b70f-115">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b70f-115">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b70f-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b70f-116">See Also</span></span>  
 <span data-ttu-id="4b70f-117">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4b70f-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="4b70f-118">[Excel 원본 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="4b70f-118">[Excel Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="4b70f-119">[Excel 원본 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="4b70f-119">[Excel Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="4b70f-120">[Excel 연결 관리자](connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="4b70f-120">[Excel Connection Manager](connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="4b70f-121">Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑</span><span class="sxs-lookup"><span data-stu-id="4b70f-121">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
