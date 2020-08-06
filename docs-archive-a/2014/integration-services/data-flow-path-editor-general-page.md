---
title: 데이터 흐름 경로 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.patheditor.general.f1
helpviewer_keywords:
- Data Flow Path Editor dialog box
ms.assetid: 72a9ff1d-3748-41d1-a9b2-63f4a77bba24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71eca61b1454e2e8cb811bbe450f584191ae77b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729707"
---
# <a name="data-flow-path-editor-general-page"></a><span data-ttu-id="5b8d4-102">데이터 흐름 경로 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="5b8d4-102">Data Flow Path Editor (General Page)</span></span>
  <span data-ttu-id="5b8d4-103">**데이터 흐름 경로 편집기** 대화 상자를 사용하여 경로 속성을 설정하고, 열 메타데이터를 보고, 경로에 연결된 데이터 뷰어를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-103">Use the **Data Flow Path Editor** dialog box to set path properties, view column metadata, and manage the data viewers attached to the path.</span></span>  
  
 <span data-ttu-id="5b8d4-104">**데이터 흐름 경로 편집기** 대화 상자의 **일반** 노드를 사용하여 경로의 이름을 지정하고 경로를 설명할 수 있을 뿐만 아니라 경로 주석 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-104">Use the **General** node of the **Data Flow Path Editor** dialog box to name and describe the path, and to specify the options for path annotation.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5b8d4-105">옵션</span><span class="sxs-lookup"><span data-stu-id="5b8d4-105">Options</span></span>  
 <span data-ttu-id="5b8d4-106">**이름**</span><span class="sxs-lookup"><span data-stu-id="5b8d4-106">**Name**</span></span>  
 <span data-ttu-id="5b8d4-107">경로에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-107">Provide a unique name for the path.</span></span>  
  
 <span data-ttu-id="5b8d4-108">**ID**</span><span class="sxs-lookup"><span data-stu-id="5b8d4-108">**ID**</span></span>  
 <span data-ttu-id="5b8d4-109">경로의 계보 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-109">The lineage identifier of the path.</span></span> <span data-ttu-id="5b8d4-110">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-110">This property is read-only.</span></span>  
  
 <span data-ttu-id="5b8d4-111">**IdentificationString**</span><span class="sxs-lookup"><span data-stu-id="5b8d4-111">**IdentificationString**</span></span>  
 <span data-ttu-id="5b8d4-112">경로를 식별하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-112">The string that identifies the path.</span></span> <span data-ttu-id="5b8d4-113">위에서 입력한 이름으로 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-113">Automatically generated from the name entered above.</span></span>  
  
 <span data-ttu-id="5b8d4-114">**설명**</span><span class="sxs-lookup"><span data-stu-id="5b8d4-114">**Description**</span></span>  
 <span data-ttu-id="5b8d4-115">경로에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-115">Describe the path.</span></span>  
  
 <span data-ttu-id="5b8d4-116">**PathAnnotation**</span><span class="sxs-lookup"><span data-stu-id="5b8d4-116">**PathAnnotation**</span></span>  
 <span data-ttu-id="5b8d4-117">사용할 주석의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-117">Specify the type of annotation to use.</span></span> <span data-ttu-id="5b8d4-118">주석을 사용하지 않으려면 **Never** 를 선택하고, 요청 시 주석을 사용하려면 **AsNeeded** 를 선택하고, **SourceName** 옵션의 값을 사용하여 자동으로 주석을 달려면 **SourceName** 을 선택하고, **Name** 속성의 값을 사용하여 자동으로 주석을 달려면 **PathName** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-118">Choose **Never** to disable annotations, **AsNeeded** to enable annotation on demand, **SourceName** to automatically annotate using the value of the **SourceName** option, and **PathName** to automatically annotate using the value of the **Name** property.</span></span>  
  
 <span data-ttu-id="5b8d4-119">**DestinationName**</span><span class="sxs-lookup"><span data-stu-id="5b8d4-119">**DestinationName**</span></span>  
 <span data-ttu-id="5b8d4-120">경로의 끝인 입력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-120">Displays the input that is the end of the path.</span></span>  
  
 <span data-ttu-id="5b8d4-121">**SourceName**</span><span class="sxs-lookup"><span data-stu-id="5b8d4-121">**SourceName**</span></span>  
 <span data-ttu-id="5b8d4-122">경로의 시작인 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5b8d4-122">Displays the output that is the start of the path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b8d4-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b8d4-123">See Also</span></span>  
 <span data-ttu-id="5b8d4-124">[데이터 흐름 경로 편집기 &#40;메타 데이터 페이지&#41;](../../2014/integration-services/data-flow-path-editor-metadata-page.md) </span><span class="sxs-lookup"><span data-stu-id="5b8d4-124">[Data Flow Path Editor &#40;Metadata Page&#41;](../../2014/integration-services/data-flow-path-editor-metadata-page.md) </span></span>  
 <span data-ttu-id="5b8d4-125">[데이터 흐름 경로 편집기 &#40;데이터 뷰어 페이지&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span><span class="sxs-lookup"><span data-stu-id="5b8d4-125">[Data Flow Path Editor &#40;Data Viewers Page&#41;](../../2014/integration-services/data-flow-path-editor-data-viewers-page.md) </span></span>  
 <span data-ttu-id="5b8d4-126">[데이터 흐름](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="5b8d4-126">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="5b8d4-127">패키지에서 주석 사용</span><span class="sxs-lookup"><span data-stu-id="5b8d4-127">Use Annotations in Packages</span></span>](use-annotations-in-packages.md)  
  
  
