---
title: 플랫 파일 원본 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Flat File
- text file reading [Integration Services]
- flat files
- Flat File source
ms.assetid: 4a64f7f3-f25d-4db0-93b3-a29496030e58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b1ca0f38c457256b3f2ed2ddb81bfbd0dc06b6c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742416"
---
# <a name="flat-file-source"></a><span data-ttu-id="6f6cb-102">플랫 파일 원본</span><span class="sxs-lookup"><span data-stu-id="6f6cb-102">Flat File Source</span></span>
  <span data-ttu-id="6f6cb-103">플랫 파일 원본은 텍스트 파일에서 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-103">The Flat File source reads data from a text file.</span></span> <span data-ttu-id="6f6cb-104">텍스트 파일은 구분 기호로 분리됨, 고정 폭 또는 혼합 형식 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-104">The text file can be in delimited, fixed width, or mixed format.</span></span>  
  
-   <span data-ttu-id="6f6cb-105">구분 기호로 분리된 형식은 열 및 행 구분 기호를 사용하여 열과 행을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-105">Delimited format uses column and row delimiters to define columns and rows.</span></span>  
  
-   <span data-ttu-id="6f6cb-106">고정 폭 형식은 너비를 사용하여 열과 행을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-106">Fixed width format uses width to define columns and rows.</span></span> <span data-ttu-id="6f6cb-107">이 형식에는 최대 너비까지 필드를 패딩하는 문자도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-107">This format also includes a character for padding fields to their maximum width.</span></span>  
  
-   <span data-ttu-id="6f6cb-108">왼쪽 정렬 형식은 너비를 사용하여 모든 열을 정의하지만 마지막 열은 행 구분 기호로 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-108">Ragged right format uses width to define all columns, except for the last column, which is delimited by the row delimiter.</span></span>  
  
 <span data-ttu-id="6f6cb-109">다음과 같은 방법으로 플랫 파일 원본을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-109">You can configure the Flat File source in the following ways:</span></span>  
  
-   <span data-ttu-id="6f6cb-110">플랫 파일 원본이 데이터를 추출할 텍스트 파일 이름이 포함된 열을 변환 출력에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-110">Add a column to the transformation output that contains the name of the text file from which the Flat File source extracts data.</span></span>  
  
-   <span data-ttu-id="6f6cb-111">플랫 파일 원본이 길이가 0인 열의 문자열을 Null 값으로 해석할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-111">Specify whether the Flat File source interprets zero-length strings in columns as null values.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6f6cb-112">플랫 파일 원본이 사용하는 플랫 파일 연결 관리자에서 구분 기호로 분리된 형식을 사용하여 길이가 0인 문자열을 Null로 해석하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-112">The Flat File connection manager that the Flat File source uses must be configured to use a delimited format to interpret zero-length strings as nulls.</span></span> <span data-ttu-id="6f6cb-113">연결 관리자가 고정 폭 또는 왼쪽 정렬 형식을 사용하는 경우 공백으로 구성된 데이터를 Null 값으로 해석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-113">If the connection manager uses the fixed width or ragged right formats, data that consists of spaces cannot be interpreted as null values.</span></span>  
  
 <span data-ttu-id="6f6cb-114">플랫 파일 원본 출력의 출력 열에는 FastParse 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-114">The output columns in the output of the Flat File source include the FastParse property.</span></span> <span data-ttu-id="6f6cb-115">FastParse는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 제공하는 더 빠르지만 로캘을 구분하지 않는 빠른 구문 분석 루틴을 사용할지 또는 로캘을 구분하는 표준 구문 분석 루틴을 사용할지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-115">FastParse indicates whether the column uses the quicker, but locale-insensitive, fast parsing routines that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides or the locale-sensitive standard parsing routines.</span></span> <span data-ttu-id="6f6cb-116">자세한 내용은 [Fast Parse](../fast-parse.md) 및 [Standard Parse](../standard-parse.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-116">For more information, see [Fast Parse](../fast-parse.md) and [Standard Parse](../standard-parse.md).</span></span>  
  
 <span data-ttu-id="6f6cb-117">또한 출력 열에는 UseBinaryFormat 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-117">Output columns also include the UseBinaryFormat property.</span></span> <span data-ttu-id="6f6cb-118">이 속성을 사용하여 압축된 10진수 형식이 있는 데이터와 같은 이진 데이터에 대한 지원을 파일에서 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-118">You use this property to implement support for binary data, such as data with the packed decimal format, in files.</span></span> <span data-ttu-id="6f6cb-119">기본적으로 UseBinaryFormat은로 설정 됩니다 `false` .</span><span class="sxs-lookup"><span data-stu-id="6f6cb-119">By default UseBinaryFormat is set to `false`.</span></span> <span data-ttu-id="6f6cb-120">이진 형식을 사용 하려면 UseBinaryFormat을로 설정 하 `true` 고 출력 열의 데이터 형식을로 설정 `DT_BYTES` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-120">If you want to use a binary format, set UseBinaryFormat to `true` and the data type on the output column to `DT_BYTES`.</span></span> <span data-ttu-id="6f6cb-121">이렇게 설정할 경우 플랫 파일 원본은 데이터 변환을 건너뛰고 데이터를 있는 그대로 출력 열에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-121">When you do this, the Flat File source skips the data conversion and passes the data to the output column as is.</span></span> <span data-ttu-id="6f6cb-122">그런 다음 파생 열 또는 데이터 변환과 같은 변환을 사용하여 `DT_BYTES` 데이터를 다른 데이터 형식에 캐스팅하거나 스크립트 변환에서 사용자 지정 스크립트를 작성하여 데이터를 해석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-122">You can then use a transformation such as the Derived Column or Data Conversion to cast the `DT_BYTES` data to a different data type, or you can write custom script in a Script transformation to interpret the data.</span></span> <span data-ttu-id="6f6cb-123">또한 사용자 지정 데이터 흐름 구성 요소를 작성하여 데이터를 해석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-123">You can also write a custom data flow component to interpret the data.</span></span> <span data-ttu-id="6f6cb-124">캐스팅할 수 있는 데이터 형식에 대 한 자세한 내용은 `DT_BYTES` [CAST &#40;SSIS Expression&#41;](../expressions/cast-ssis-expression.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-124">For more information about which data types you can cast `DT_BYTES` to, see [Cast &#40;SSIS Expression&#41;](../expressions/cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="6f6cb-125">이 원본은 플랫 파일 연결 관리자를 사용하여 텍스트 파일에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-125">This source uses a Flat File connection manager to access the text file.</span></span> <span data-ttu-id="6f6cb-126">플랫 파일 연결 관리자의 속성을 설정하여 파일과 해당 파일의 각 열에 대한 정보를 제공하고 플랫 파일에서 텍스트 파일의 데이터를 처리하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-126">By setting properties on the Flat File connection manager, you can provide information about the file and each column in it, and specify how the Flat File source should handle the data in the text file.</span></span> <span data-ttu-id="6f6cb-127">예를 들어 파일의 열과 행을 구분하는 문자와 각 열의 데이터 형식 및 길이를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-127">For example, you can specify the characters that delimit columns and rows in the file, and the data type and the length of each column.</span></span> <span data-ttu-id="6f6cb-128">자세한 내용은 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-128">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="6f6cb-129">이 원본에는 출력 한 개와 오류 출력 한 개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-129">This source has one output and one error output.</span></span>  
  
## <a name="configuration-of-the-flat-file-source"></a><span data-ttu-id="6f6cb-130">플랫 파일 원본 구성</span><span class="sxs-lookup"><span data-stu-id="6f6cb-130">Configuration of the Flat File Source</span></span>  
 <span data-ttu-id="6f6cb-131">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="6f6cb-132">**플랫 파일 원본 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-132">For more information about the properties that you can set in the **Flat File Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="6f6cb-133">플랫 파일 원본 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="6f6cb-133">Flat File Source Editor &#40;Connection Manager Page&#41;</span></span>](../flat-file-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="6f6cb-134">플랫 파일 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="6f6cb-134">Flat File Source Editor &#40;Columns Page&#41;</span></span>](../flat-file-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="6f6cb-135">플랫 파일 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="6f6cb-135">Flat File Source Editor &#40;Error Output Page&#41;</span></span>](../flat-file-source-editor-error-output-page.md)  
  
 <span data-ttu-id="6f6cb-136">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-136">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="6f6cb-137">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-137">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="6f6cb-138">Common Properties</span><span class="sxs-lookup"><span data-stu-id="6f6cb-138">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="6f6cb-139">플랫 파일 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="6f6cb-139">Flat File Custom Properties</span></span>](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="6f6cb-140">관련 작업</span><span class="sxs-lookup"><span data-stu-id="6f6cb-140">Related Tasks</span></span>  
 <span data-ttu-id="6f6cb-141">데이터 흐름 구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cb-141">For details about how to set properties of a data flow component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6cb-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f6cb-142">See Also</span></span>  
 <span data-ttu-id="6f6cb-143">[플랫 파일 대상](flat-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="6f6cb-143">[Flat File Destination](flat-file-destination.md) </span></span>  
 [<span data-ttu-id="6f6cb-144">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="6f6cb-144">Data Flow</span></span>](data-flow.md)  
  
  
