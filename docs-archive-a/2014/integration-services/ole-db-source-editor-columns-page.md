---
title: OLE DB 원본 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.columns.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: bfbb0ae1-7759-4d45-8865-31df36ae5b34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 575a5a02198606d2412ff187750963ccb171e338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647754"
---
# <a name="ole-db-source-editor-columns-page"></a><span data-ttu-id="b10ef-102">OLE DB 원본 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="b10ef-102">OLE DB Source Editor (Columns Page)</span></span>
  <span data-ttu-id="b10ef-103">**OLE DB 원본 편집기** 대화 상자의 **열** 페이지를 사용하여 출력 열을 각 외부(원본) 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b10ef-103">Use the **Columns** page of the **OLE DB Source Editor** dialog box to map an output column to each external (source) column.</span></span>  
  
 <span data-ttu-id="b10ef-104">OLE DB 원본에 대한 자세한 내용은 [OLE DB Source](data-flow/ole-db-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b10ef-104">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b10ef-105">옵션</span><span class="sxs-lookup"><span data-stu-id="b10ef-105">Options</span></span>  
 <span data-ttu-id="b10ef-106">**사용 가능한 외부 열**</span><span class="sxs-lookup"><span data-stu-id="b10ef-106">**Available External Columns**</span></span>  
 <span data-ttu-id="b10ef-107">데이터 원본에서 사용 가능한 외부 열의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b10ef-107">View the list of available external columns in the data source.</span></span> <span data-ttu-id="b10ef-108">이 테이블을 사용하여 열을 추가하거나 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b10ef-108">You cannot use this table to add or delete columns.</span></span>  
  
 <span data-ttu-id="b10ef-109">**외부 열**</span><span class="sxs-lookup"><span data-stu-id="b10ef-109">**External Column**</span></span>  
 <span data-ttu-id="b10ef-110">이 원본의 데이터를 사용하는 구성 요소를 구성할 때 표시되는 순서로 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b10ef-110">View external (source) columns in the order in which you will see them when configuring components that consume data from this source.</span></span> <span data-ttu-id="b10ef-111">이 순서는 먼저 테이블에서 선택된 열을 지운 다음 목록에서 다른 순서로 외부 열을 선택하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b10ef-111">You can change this order by first clearing the selected columns in the table, and then selecting external columns from the list in a different order.</span></span>  
  
 <span data-ttu-id="b10ef-112">**출력 열**</span><span class="sxs-lookup"><span data-stu-id="b10ef-112">**Output Column**</span></span>  
 <span data-ttu-id="b10ef-113">각 출력 열에 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b10ef-113">Provide a unique name for each output column.</span></span> <span data-ttu-id="b10ef-114">기본값은 선택한 외부(원본) 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b10ef-114">The default is the name of the selected external (source) column; however, you can choose any unique, descriptive name.</span></span> <span data-ttu-id="b10ef-115">제공한 이름은 SSIS 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b10ef-115">The name provided will be displayed within the SSIS Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10ef-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b10ef-116">See Also</span></span>  
 <span data-ttu-id="b10ef-117">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b10ef-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b10ef-118">[OLE DB 원본 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="b10ef-118">[OLE DB Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="b10ef-119">[원본 편집기 &#40;오류 출력 페이지를 OLE DB&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="b10ef-119">[OLE DB Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="b10ef-120">[OLE DB 소스를 사용 하 여 데이터 추출](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="b10ef-120">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="b10ef-121">OLE DB 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="b10ef-121">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
