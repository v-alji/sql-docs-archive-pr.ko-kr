---
title: 경로를 사용 하 여 구성 요소 연결 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], connections
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 05633e4c-1370-4b05-802b-f36b07dd71c8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e11955601406406abe48b53197e95c8224762fee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738620"
---
# <a name="connect-components-with-paths"></a><span data-ttu-id="1cea2-102">경로에 구성 요소 연결</span><span class="sxs-lookup"><span data-stu-id="1cea2-102">Connect Components with Paths</span></span>
  <span data-ttu-id="1cea2-103">**디자이너의** 데이터 흐름 [!INCLUDE[ssIS](../includes/ssis-md.md)] 탭의 디자인 화면에서 패키지의 데이터 흐름을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1cea2-103">You construct the data flow in a package on the design surface of the **Data Flow** tab in the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="1cea2-104">데이터 흐름에 데이터 흐름 구성 요소가 두 개 있으면 원본 또는 변환의 출력을 변환 또는 대상의 입력에 연결하여 두 구성 요소를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cea2-104">If a data flow contains two data flow components, you can connect them by connecting the output of a source or transformation to the input of a transformation or destination.</span></span> <span data-ttu-id="1cea2-105">두 데이터 흐름 구성 요소 간 연결선을 경로라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cea2-105">The connector between two data flow components is called a path.</span></span>

 <span data-ttu-id="1cea2-106">다음 다이어그램에서는 하나의 원본 구성 요소, 두 개의 변환, 하나의 대상 구성 요소 및 이를 연결하는 경로가 포함된 간단한 데이터 흐름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1cea2-106">The following diagram shows a simple data flow with a source component, two transformations, a destination component, and the paths that connect them.</span></span>

 <span data-ttu-id="1cea2-107">![데이터 흐름](media/mw-dts-08.gif "데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="1cea2-107">![Data flow](media/mw-dts-08.gif "Data flow")</span></span>

 <span data-ttu-id="1cea2-108">두 구성 요소를 연결한 다음에는 **데이터 흐름 경로 편집기**에서 경로를 통해 이동하는 데이터의 메타데이터와 경로의 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cea2-108">After two components are connected, you can view the metadata of the data that moves through the path and the properties of the path in **Data Flow Path Editor**.</span></span> <span data-ttu-id="1cea2-109">자세한 내용은 [Integration Services Paths](data-flow/integration-services-paths.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1cea2-109">For more information, see [Integration Services Paths](data-flow/integration-services-paths.md).</span></span>

 <span data-ttu-id="1cea2-110">경로에 데이터 뷰어를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cea2-110">You can also add data viewers to paths.</span></span> <span data-ttu-id="1cea2-111">데이터 뷰어를 사용하면 패키지가 실행될 때 데이터 흐름 구성 요소 간에 이동하는 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cea2-111">A data viewer makes it possible to view data moving between data flow components when the package is run.</span></span>

### <a name="to-connect-components-in-a-data-flow"></a><span data-ttu-id="1cea2-112">데이터 흐름에서 구성 요소를 연결하려면</span><span class="sxs-lookup"><span data-stu-id="1cea2-112">To connect components in a data flow</span></span>

-   [<span data-ttu-id="1cea2-113">데이터 흐름의 구성 요소 연결</span><span class="sxs-lookup"><span data-stu-id="1cea2-113">Connect Components in a Data Flow</span></span>](data-flow/connect-components-in-a-data-flow.md)

### <a name="to-set-path-properties"></a><span data-ttu-id="1cea2-114">경로 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="1cea2-114">To set path properties</span></span>

-   [<span data-ttu-id="1cea2-115">데이터 흐름 경로 편집기를 사용하여 경로의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="1cea2-115">Set the Properties of a Path by Using the Data Flow Path Editor</span></span>](../../2014/integration-services/set-the-properties-of-a-path-by-using-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a><span data-ttu-id="1cea2-116">경로 메타데이터를 보려면</span><span class="sxs-lookup"><span data-stu-id="1cea2-116">To view path metadata</span></span>

-   [<span data-ttu-id="1cea2-117">데이터 흐름 경로 편집기를 사용하여 경로 메타데이터 보기</span><span class="sxs-lookup"><span data-stu-id="1cea2-117">View Path Metadata in the Data Flow Path Editor</span></span>](../../2014/integration-services/view-path-metadata-in-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a><span data-ttu-id="1cea2-118">경로 메타데이터를 보려면</span><span class="sxs-lookup"><span data-stu-id="1cea2-118">To view path metadata</span></span>

-   [<span data-ttu-id="1cea2-119">데이터 흐름에 데이터 뷰어 추가</span><span class="sxs-lookup"><span data-stu-id="1cea2-119">Add a Data Viewer to a Data Flow</span></span>](../../2014/integration-services/add-a-data-viewer-to-a-data-flow.md)

## <a name="see-also"></a><span data-ttu-id="1cea2-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1cea2-120">See Also</span></span>
 <span data-ttu-id="1cea2-121">데이터 [흐름 태스크](control-flow/data-flow-task.md) 데이터 [흐름](data-flow/data-flow.md) [변환](data-flow/transformations/transform-data-with-transformations.md) 데이터의 변환 [오류 처리](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="1cea2-121">[Data Flow Task](control-flow/data-flow-task.md) [Data Flow](data-flow/data-flow.md) [Transform Data with Transformations](data-flow/transformations/transform-data-with-transformations.md) [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>


