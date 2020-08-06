---
title: Integration Services 경로 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- paths [Integration Services], about paths
- data flow [Integration Services], paths
- paths [Integration Services]
- destinations [Integration Services], paths
- sources [Integration Services], paths
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c52bbd06974311a7fc94b3058309399d70df0034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731955"
---
# <a name="integration-services-paths"></a><span data-ttu-id="4239c-102">Integration Services 경로</span><span class="sxs-lookup"><span data-stu-id="4239c-102">Integration Services Paths</span></span>
  <span data-ttu-id="4239c-103">경로는 하나의 데이터 흐름 구성 요소의 출력을 다른 구성 요소의 입력에 연결함으로써 데이터 흐름의 두 구성 요소를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-103">A path connects two components in a data flow by connecting the output of one data flow component to the input of another component.</span></span> <span data-ttu-id="4239c-104">경로에는 원본과 대상이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-104">A path has a source and a destination.</span></span> <span data-ttu-id="4239c-105">예를 들어 경로가 OLE DB 원본과 정렬 변환을 연결하는 경우 OLE DB 원본은 경로의 원본이며, 정렬 변환은 경로의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-105">For example, if a path connects an OLE DB source and a Sort transformation, the OLE DB source is the source of the path, and the Sort transformation is the destination of the path.</span></span> <span data-ttu-id="4239c-106">원본은 경로가 시작되는 구성 요소이며, 대상은 경로가 끝나는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-106">The source is the component where the path starts, and the destination is the component where the path ends.</span></span>  
  
 <span data-ttu-id="4239c-107">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 패키지를 실행하는 경우에는 데이터 뷰어를 경로에 연결하여 데이터 흐름의 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-107">If you run a package in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can view the data in a data flow by attaching data viewers to a path.</span></span> <span data-ttu-id="4239c-108">표에 데이터를 표시하도록 데이터 뷰어를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-108">A data viewer can be configured to display data in a grid.</span></span> <span data-ttu-id="4239c-109">데이터 뷰어는 유용한 디버깅 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-109">A data viewer is a useful debugging tool.</span></span> <span data-ttu-id="4239c-110">자세한 내용은 [Debugging Data Flow](../troubleshooting/debugging-data-flow.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4239c-110">For more information, see [Debugging Data Flow](../troubleshooting/debugging-data-flow.md).</span></span>  
  
## <a name="configuration-of-the-path"></a><span data-ttu-id="4239c-111">경로 구성</span><span class="sxs-lookup"><span data-stu-id="4239c-111">Configuration of the Path</span></span>  
 <span data-ttu-id="4239c-112">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너는 경로 속성을 설정하고, 경로를 통과하는 데이터 열의 메타데이터를 보고, 데이터 뷰어를 구성할 수 있는 **데이터 흐름 경로 편집기** 대화 상자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-112">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides the **Data Flow Path Editor** dialog box for setting path properties, viewing the metadata of the data columns that pass through the path, and configuring data viewers.</span></span>  
  
 <span data-ttu-id="4239c-113">구성 가능한 경로 속성에는 경로의 이름, 설명 및 주석이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-113">The configurable path properties include the name, description, and annotation of the path.</span></span> <span data-ttu-id="4239c-114">또한 경로를 프로그래밍 방식으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-114">You can also configure paths programmatically.</span></span> <span data-ttu-id="4239c-115">자세한 내용은 [프로그래밍 방식으로 데이터 흐름 구성 요소 연결](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4239c-115">For more information, see [Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
 <span data-ttu-id="4239c-116">경로 주석에는 **디자이너의** 데이터 흐름 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 탭에서 디자인 화면에 표시된 경로 원본의 이름 또는 경로 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-116">A path annotation displays the name of the path source or the path name on the design surface of the **Data Flow** tab in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="4239c-117">경로 주석은 데이터 흐름, 제어 흐름 및 이벤트 처리기에 추가할 수 있는 주석과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-117">Path annotations are similar to the annotations you can add to data flows, control flows, and event handlers.</span></span> <span data-ttu-id="4239c-118">단지 경로 주석은 경로에 연결되며, 다른 주석은 **디자이너의**데이터 흐름 **,** 제어 흐름 **및**이벤트 처리기 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 테이블에 표시된다는 점만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-118">The only difference is that a path annotation is attached to a path, whereas other annotations appear on the **Data Flow**, **Control Flow**, and **Event Handle**r tabs of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="4239c-119">메타데이터에는 이전 구성 요소의 출력에 있는 각 열의 이름, 데이터 형식, 전체 자릿수, 소수 자릿수, 길이, 코드 페이지 및 원본 구성 요소가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-119">The metadata shows the name, data type, precision, scale, length, code page, and source component of each column in the output of the previous component.</span></span> <span data-ttu-id="4239c-120">원본 구성 요소는 해당 열을 만든 데이터 흐름 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-120">The source component is the data flow component that created the column.</span></span> <span data-ttu-id="4239c-121">이러한 구성 요소는 데이터 흐름에서 첫 번째 구성 요소일 수도 있으며, 아닐 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-121">This may or may not be the first component in the data flow.</span></span> <span data-ttu-id="4239c-122">예를 들어 UNION ALL 및 정렬 변환은 해당 열을 만들며, 이는 출력 열에 대한 원본이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-122">For example, the Union All and Sort transformations create their own columns, and they are the sources of their output columns.</span></span> <span data-ttu-id="4239c-123">반대로 열 복사 변환은 열을 변경하지 않은 상태로 전달하거나 입력 열을 복사하여 새 열을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-123">In contrast, a Copy Column transformation can pass through columns without changing them or can create new columns by copying input columns.</span></span> <span data-ttu-id="4239c-124">열 복사 변환은 새로운 열에 대해서만 원본 구성 요소가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-124">The Copy Column transformation is the source component only of the new columns.</span></span>  
  
 <span data-ttu-id="4239c-125">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4239c-125">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="4239c-126">**데이터 흐름 경로 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="4239c-126">For more information about the properties that you can set in the **Data Flow Path Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4239c-127">데이터 흐름 경로 편집기 &#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="4239c-127">Data Flow Path Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="4239c-128">데이터 흐름 경로 편집기 &#40;메타 데이터 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="4239c-128">Data Flow Path Editor &#40;Metadata Page&#41;</span></span>](../data-flow-path-editor-metadata-page.md)  
  
-   [<span data-ttu-id="4239c-129">데이터 흐름 경로 편집기 &#40;데이터 뷰어 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="4239c-129">Data Flow Path Editor &#40;Data Viewers Page&#41;</span></span>](../data-flow-path-editor-data-viewers-page.md)  
  
 <span data-ttu-id="4239c-130">프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용은 [Path Properties](../path-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4239c-130">For more information about the properties that you can set programmatically, see [Path Properties](../path-properties.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="4239c-131">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4239c-131">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4239c-132">데이터 흐름 경로 편집기를 사용하여 경로 메타데이터 보기</span><span class="sxs-lookup"><span data-stu-id="4239c-132">View Path Metadata in the Data Flow Path Editor</span></span>](../view-path-metadata-in-the-data-flow-path-editor.md)  
  
-   [<span data-ttu-id="4239c-133">데이터 흐름의 구성 요소 연결</span><span class="sxs-lookup"><span data-stu-id="4239c-133">Connect Components in a Data Flow</span></span>](connect-components-in-a-data-flow.md)  
  
## <a name="see-also"></a><span data-ttu-id="4239c-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4239c-134">See Also</span></span>  
 [<span data-ttu-id="4239c-135">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="4239c-135">Data Flow</span></span>](data-flow.md)  
  
  
