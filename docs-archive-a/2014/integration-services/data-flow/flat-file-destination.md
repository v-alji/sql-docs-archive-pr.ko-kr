---
title: 플랫 파일 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfiledest.f1
helpviewer_keywords:
- flat files
- Flat File destination
- text file writing [Integration Services]
- destinations [Integration Services], Flat File
ms.assetid: e0d6e356-8db4-48aa-ba66-029397f98f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a961b7528b13a4eaa3297343e91f1deaf2fa3226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742419"
---
# <a name="flat-file-destination"></a><span data-ttu-id="1322f-102">플랫 파일 대상</span><span class="sxs-lookup"><span data-stu-id="1322f-102">Flat File Destination</span></span>
  <span data-ttu-id="1322f-103">플랫 파일 대상은 데이터를 텍스트 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-103">The Flat File destination writes data to a text file.</span></span> <span data-ttu-id="1322f-104">텍스트 파일은 구분 기호로 분리된 형식, 고정 폭 형식, 행 구분 기호가 있는 고정 폭 형식 또는 왼쪽 정렬 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-104">The text file can be in delimited, fixed width, fixed width with row delimiter, or ragged right format.</span></span>  
  
 <span data-ttu-id="1322f-105">다음과 같은 방법으로 플랫 파일 대상을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-105">You can configure the Flat File destination in the following ways:</span></span>  
  
-   <span data-ttu-id="1322f-106">데이터를 쓰기 전에 삽입할 텍스트 블록을 파일에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-106">Provide a block of text that is inserted in the file before any data is written.</span></span> <span data-ttu-id="1322f-107">텍스트는 열 제목과 같은 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-107">The text can provide information such as column headings.</span></span>  
  
-   <span data-ttu-id="1322f-108">같은 이름의 대상 파일에 데이터를 덮어쓸지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-108">Specify whether to overwrite a data in a destination file that has the same name.</span></span>  
  
 <span data-ttu-id="1322f-109">이 대상은 플랫 파일 연결 관리자를 사용하여 텍스트 파일에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-109">This destination uses a Flat File connection manager to access the text file.</span></span> <span data-ttu-id="1322f-110">플랫 파일 대상에서 사용되는 플랫 파일 연결 관리자에 속성을 설정하여 플랫 파일 대상에서 텍스트 파일을 기록하고 형식을 지정하는 방식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-110">By setting properties on the Flat File connection manager that the Flat File destination uses, you can specify how the Flat File destination formats and writes the text file.</span></span> <span data-ttu-id="1322f-111">플랫 파일 연결 관리자를 구성할 때 파일 및 파일의 각 열에 대한 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-111">When you configure the Flat File connection manager, you specify information about the file and about each column in the file.</span></span> <span data-ttu-id="1322f-112">예를 들어 파일의 열과 행을 구분하는 문자와 각 열의 데이터 형식 및 길이를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-112">For example, you specify the characters that delimit columns and rows in the file, and you specify the data type and the length of each column.</span></span> <span data-ttu-id="1322f-113">자세한 내용은 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1322f-113">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="1322f-114">플랫 파일 대상에는 Header 사용자 지정 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-114">The Flat File destination includes the Header custom property.</span></span> <span data-ttu-id="1322f-115">이 속성은 패키지가 로드되면 속성 식을 사용하여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-115">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="1322f-116">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../expressions/integration-services-ssis-expressions.md), [패키지에서 속성 식 사용](../expressions/use-property-expressions-in-packages.md) 및 [플랫 파일 사용자 지정 속성](flat-file-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1322f-116">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [Flat File Custom Properties](flat-file-custom-properties.md).</span></span>  
  
 <span data-ttu-id="1322f-117">이 대상은 하나의 출력을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-117">This destination has one output.</span></span> <span data-ttu-id="1322f-118">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-118">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-flat-file-destination"></a><span data-ttu-id="1322f-119">플랫 파일 대상 구성</span><span class="sxs-lookup"><span data-stu-id="1322f-119">Configuration of the Flat File Destination</span></span>  
 <span data-ttu-id="1322f-120">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-120">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="1322f-121">**플랫 파일 원본 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="1322f-121">For more information about the properties that you can set in the **Flat File Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="1322f-122">플랫 파일 대상 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1322f-122">Flat File Destination Editor &#40;Connection Manager Page&#41;</span></span>](../flat-file-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="1322f-123">플랫 파일 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1322f-123">Flat File Destination Editor &#40;Mappings Page&#41;</span></span>](../flat-file-destination-editor-mappings-page.md)  
  
 <span data-ttu-id="1322f-124">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1322f-124">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="1322f-125">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="1322f-125">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="1322f-126">Common Properties</span><span class="sxs-lookup"><span data-stu-id="1322f-126">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="1322f-127">플랫 파일 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="1322f-127">Flat File Custom Properties</span></span>](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="1322f-128">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1322f-128">Related Tasks</span></span>  
 <span data-ttu-id="1322f-129">데이터 흐름 구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1322f-129">For information about how to set the properties of a data flow component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1322f-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1322f-130">See Also</span></span>  
 <span data-ttu-id="1322f-131">[플랫 파일 원본](flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="1322f-131">[Flat File Source](flat-file-source.md) </span></span>  
 [<span data-ttu-id="1322f-132">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="1322f-132">Data Flow</span></span>](data-flow.md)  
  
  
