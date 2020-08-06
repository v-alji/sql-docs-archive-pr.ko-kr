---
title: 원시 파일 원본 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Raw File
- raw data [Integration Services]
- Raw File source
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cbc5800c4fb2b90b74e66b6ff161118b2b550f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648458"
---
# <a name="raw-file-source"></a><span data-ttu-id="9b91e-102">원시 파일 원본</span><span class="sxs-lookup"><span data-stu-id="9b91e-102">Raw File Source</span></span>
  <span data-ttu-id="9b91e-103">원시 파일 원본은 파일에서 원시 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-103">The Raw File source reads raw data from a file.</span></span> <span data-ttu-id="9b91e-104">원본의 기본 데이터 표현을 사용하므로 데이터를 변환하거나 거의 구문 분석할 필요도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-104">Because the representation of the data is native to the source, the data requires no translation and almost no parsing.</span></span> <span data-ttu-id="9b91e-105">따라서 원시 파일 원본은 플랫 파일 및 OLE DB 원본과 같은 다른 원본보다 빨리 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-105">This means that the Raw File source can read data more quickly than other sources such as the Flat File and the OLE DB sources.</span></span>  
  
 <span data-ttu-id="9b91e-106">원시 파일 원본은 원시 파일 대상에서 이전에 기록한 원시 데이터를 검색하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-106">The Raw File source is used to retrieve raw data that was previously written by the Raw File destination.</span></span> <span data-ttu-id="9b91e-107">또한 원시 파일 원본이 열만 포함된 빈 원시 파일(메타데이터 전용 파일)을 가리키도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-107">You can also point the Raw File source to an empty raw file that contains only the columns (metadata-only file).</span></span> <span data-ttu-id="9b91e-108">패키지를 실행할 필요없이 원시 파일 대상을 사용하여 메타데이터 전용 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-108">You use the Raw File destination to generate the metadata-only file without having to run the package.</span></span> <span data-ttu-id="9b91e-109">자세한 내용은 [Raw File Destination](raw-file-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b91e-109">For more information, see [Raw File Destination](raw-file-destination.md).</span></span>  
  
 <span data-ttu-id="9b91e-110">원시 파일 서식에는 정렬 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-110">The raw file format contains sort information.</span></span> <span data-ttu-id="9b91e-111">원시 파일 대상에는 문자열 열을 위한 비교 플래그를 포함하여 모든 정렬 정보가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-111">The Raw File Destination saves all the sort information including the comparison flags for string columns.</span></span> <span data-ttu-id="9b91e-112">원시 파일 원본은 정렬 정보를 읽고 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-112">The Raw File source reads and honors the sort information.</span></span> <span data-ttu-id="9b91e-113">고급 편집기를 사용하면 파일의 정렬 플래그를 무시하도록 원시 파일 원본을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-113">You do have the option of configuring the Raw File Source to ignore the sort flags in the file, using the Advanced Editor.</span></span> <span data-ttu-id="9b91e-114">비교 플래그에 대한 자세한 내용은 [Comparing String Data](comparing-string-data.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b91e-114">For more information about comparison flags, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="9b91e-115">원시 파일 원본에서 읽을 파일 이름을 지정하여 원시 파일을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-115">You configure the Raw File by specifying the name of the name of the file that the Raw File source reads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9b91e-116">이 원본은 연결 관리자를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-116">This source does not use a connection manager.</span></span>  
  
 <span data-ttu-id="9b91e-117">이 원본에는 하나의 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-117">This source has one output.</span></span> <span data-ttu-id="9b91e-118">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-118">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-raw-file-source"></a><span data-ttu-id="9b91e-119">원시 파일 원본 구성</span><span class="sxs-lookup"><span data-stu-id="9b91e-119">Configuration of the Raw File Source</span></span>  
 <span data-ttu-id="9b91e-120">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-120">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="9b91e-121">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b91e-121">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="9b91e-122">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="9b91e-122">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9b91e-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="9b91e-123">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="9b91e-124">원시 파일 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="9b91e-124">Raw File Custom Properties</span></span>](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="9b91e-125">관련 작업</span><span class="sxs-lookup"><span data-stu-id="9b91e-125">Related Tasks</span></span>  
 <span data-ttu-id="9b91e-126">구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b91e-126">For information about how to set the properties of the component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="9b91e-127">관련 내용</span><span class="sxs-lookup"><span data-stu-id="9b91e-127">Related Content</span></span>  
  
-   <span data-ttu-id="9b91e-128">sqlservercentral.com의 블로그 항목 - [원시 파일의 놀라운 기능](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131)</span><span class="sxs-lookup"><span data-stu-id="9b91e-128">Blog entry, [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131), on sqlservercentral.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b91e-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b91e-129">See Also</span></span>  
 <span data-ttu-id="9b91e-130">[원시 파일 대상](raw-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="9b91e-130">[Raw File Destination](raw-file-destination.md) </span></span>  
 [<span data-ttu-id="9b91e-131">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="9b91e-131">Data Flow</span></span>](data-flow.md)  
  
  
