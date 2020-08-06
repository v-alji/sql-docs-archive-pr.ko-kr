---
title: 플랫 파일 원본 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9b0249b2b17d50fdef4b5cf4aff70a1318614257
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647144"
---
# <a name="flat-file-source-editor-columns-page"></a><span data-ttu-id="fbfa5-102">플랫 파일 원본 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="fbfa5-102">Flat File Source Editor (Columns Page)</span></span>
  <span data-ttu-id="fbfa5-103">**플랫 파일 원본 편집기** 대화 상자의 **열** 노드를 사용하여 출력 열을 외부(원본) 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-103">Use the **Columns** node of the **Flat File Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fbfa5-104">플랫 파일 원본의 `FileNameColumnName` 속성과 `FastParse` 출력 열의 속성은 **플랫 파일 원본 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용 하 여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-104">The `FileNameColumnName` property of the Flat File source and the `FastParse` property of its output columns are not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="fbfa5-105">이러한 속성에 대한 자세한 내용은 [Flat File Custom Properties](data-flow/flat-file-custom-properties.md)의 플랫 파일 원본 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-105">For more information on these properties, see the Flat File Source section of [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).</span></span>  
  
 <span data-ttu-id="fbfa5-106">플랫 파일 원본에 대한 자세한 내용은 [Flat File Source](data-flow/flat-file-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-106">To learn more about the Flat File source, see [Flat File Source](data-flow/flat-file-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fbfa5-107">옵션</span><span class="sxs-lookup"><span data-stu-id="fbfa5-107">Options</span></span>  
 <span data-ttu-id="fbfa5-108">**사용 가능한 외부 열**</span><span class="sxs-lookup"><span data-stu-id="fbfa5-108">**Available External Columns**</span></span>  
 <span data-ttu-id="fbfa5-109">데이터 원본에서 사용 가능한 외부 열의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-109">View the list of available external columns in the data source.</span></span> <span data-ttu-id="fbfa5-110">이 테이블을 사용하여 열을 추가하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-110">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="fbfa5-111">**외부 열**</span><span class="sxs-lookup"><span data-stu-id="fbfa5-111">**External Column**</span></span>  
 <span data-ttu-id="fbfa5-112">태스크에서 읽는 순서대로 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-112">View external (source) columns in the order in which the task will read them.</span></span> <span data-ttu-id="fbfa5-113">이 순서는 먼저 테이블에서 선택된 열을 지운 다음 목록에서 다른 순서로 외부 열을 선택하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-113">You can change this order by first clearing the selected columns in the table, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="fbfa5-114">**출력 열**</span><span class="sxs-lookup"><span data-stu-id="fbfa5-114">**Output Column**</span></span>  
 <span data-ttu-id="fbfa5-115">각 출력 열에 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-115">Provide a unique name for each output column.</span></span> <span data-ttu-id="fbfa5-116">기본값은 선택한 외부(원본) 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-116">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="fbfa5-117">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbfa5-117">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbfa5-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fbfa5-118">See Also</span></span>  
 <span data-ttu-id="fbfa5-119">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fbfa5-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="fbfa5-120">[플랫 파일 원본 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="fbfa5-120">[Flat File Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="fbfa5-121">[플랫 파일 원본 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="fbfa5-121">[Flat File Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="fbfa5-122">플랫 파일 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="fbfa5-122">Flat File Connection Manager</span></span>](connection-manager/file-connection-manager.md)  
  
  
