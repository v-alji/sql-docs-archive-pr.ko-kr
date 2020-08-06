---
title: XML 원본 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.columns.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: 5162c400-b2fc-4711-af0f-609132fbaaad
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0b9433b7a2c4f08f9e0c70d568f8fc037ceb7c6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736502"
---
# <a name="xml-source-editor-columns-page"></a><span data-ttu-id="f8c29-102">XML 원본 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="f8c29-102">XML Source Editor (Columns Page)</span></span>
  <span data-ttu-id="f8c29-103">**XML 원본 편집기** 대화 상자의 **열** 노드를 사용하여 출력 열을 외부(원본) 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8c29-103">Use the **Columns** node of the **XML Source Editor** dialog box to map an output column to an external (source) column.</span></span>  
  
 <span data-ttu-id="f8c29-104">XML 원본에 대한 자세한 내용은 [XML Source](data-flow/xml-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f8c29-104">For more information about the XML source, see [XML Source](data-flow/xml-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f8c29-105">옵션</span><span class="sxs-lookup"><span data-stu-id="f8c29-105">Options</span></span>  
 <span data-ttu-id="f8c29-106">**사용 가능한 외부 열**</span><span class="sxs-lookup"><span data-stu-id="f8c29-106">**Available External Columns**</span></span>  
 <span data-ttu-id="f8c29-107">데이터 원본에서 사용 가능한 외부 열의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c29-107">View the list of available external columns in the data source.</span></span> <span data-ttu-id="f8c29-108">이 테이블을 사용하여 열을 추가하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8c29-108">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="f8c29-109">**외부 열**</span><span class="sxs-lookup"><span data-stu-id="f8c29-109">**External Column**</span></span>  
 <span data-ttu-id="f8c29-110">태스크에서 읽는 순서대로 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c29-110">View external (source) columns in the order in which the task will read them.</span></span> <span data-ttu-id="f8c29-111">이 순서는 먼저 편집기에 표시된 테이블에서 선택한 열을 지운 다음 목록에서 다른 순서로 외부 열을 선택하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8c29-111">You can change this order by first clearing the selected columns in the table displayed in the editor, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="f8c29-112">**출력 열**</span><span class="sxs-lookup"><span data-stu-id="f8c29-112">**Output Column**</span></span>  
 <span data-ttu-id="f8c29-113">각 출력 열에 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8c29-113">Provide a unique name for each output column.</span></span> <span data-ttu-id="f8c29-114">기본값은 선택한 외부(원본) 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8c29-114">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="f8c29-115">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8c29-115">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c29-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8c29-116">See Also</span></span>  
 <span data-ttu-id="f8c29-117">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f8c29-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f8c29-118">[연결 관리자 페이지 &#40;XML 원본 편집기&#41;](../../2014/integration-services/xml-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="f8c29-118">[XML Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/xml-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="f8c29-119">[XML 원본 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="f8c29-119">[XML Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="f8c29-120">XML 원본을 사용하여 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="f8c29-120">Extract Data by Using the XML Source</span></span>](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
