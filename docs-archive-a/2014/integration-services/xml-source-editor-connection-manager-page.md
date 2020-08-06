---
title: XML 원본 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.connectionmanager.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e40ca6ef2d8fbcd10b756a2ce15f33730c367d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660672"
---
# <a name="xml-source-editor-connection-manager-page"></a><span data-ttu-id="a745d-102">XML 원본 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="a745d-102">XML Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="a745d-103">**XML 원본 편집기** 의 **연결 관리자** 페이지를 사용하여 XML 데이터를 변환할 XML 파일 및 XSD를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-103">Use the **Connection Manager** page of the **XML Source Editor** to specify an XML file and the XSD that transforms the XML data.</span></span>  
  
 <span data-ttu-id="a745d-104">XML 원본에 대한 자세한 내용은 [XML Source](data-flow/xml-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a745d-104">For more information about the XML source, see [XML Source](data-flow/xml-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="a745d-105">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="a745d-105">Static Options</span></span>  
 <span data-ttu-id="a745d-106">**데이터 액세스 모드**</span><span class="sxs-lookup"><span data-stu-id="a745d-106">**Data access mode**</span></span>  
 <span data-ttu-id="a745d-107">원본에서 데이터를 선택하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-107">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="a745d-108">값</span><span class="sxs-lookup"><span data-stu-id="a745d-108">Value</span></span>|<span data-ttu-id="a745d-109">Description</span><span class="sxs-lookup"><span data-stu-id="a745d-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a745d-110">XML 파일 위치</span><span class="sxs-lookup"><span data-stu-id="a745d-110">XML file location</span></span>|<span data-ttu-id="a745d-111">XML 파일에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-111">Retrieve data from an XML file.</span></span>|  
|<span data-ttu-id="a745d-112">변수를 사용한 XML 파일</span><span class="sxs-lookup"><span data-stu-id="a745d-112">XML file from variable</span></span>|<span data-ttu-id="a745d-113">변수에 XML 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-113">Specify the XML file name in a variable.</span></span><br /><br /> <span data-ttu-id="a745d-114">**관련 정보**: [패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="a745d-114">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="a745d-115">변수를 사용한 XML 데이터</span><span class="sxs-lookup"><span data-stu-id="a745d-115">XML data from variable</span></span>|<span data-ttu-id="a745d-116">변수에서 XML 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-116">Retrieve XML data from a variable.</span></span>|  
  
 <span data-ttu-id="a745d-117">**인라인 스키마 사용**</span><span class="sxs-lookup"><span data-stu-id="a745d-117">**Use inline schema**</span></span>  
 <span data-ttu-id="a745d-118">XML 원본 데이터에 구조 및 데이터를 정의하고 유효성을 검사하는 XSD 스키마를 포함할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-118">Specify whether the XML source data itself contains the XSD schema that defines and validates its structure and data.</span></span>  
  
 <span data-ttu-id="a745d-119">**XSD 위치**</span><span class="sxs-lookup"><span data-stu-id="a745d-119">**XSD location**</span></span>  
 <span data-ttu-id="a745d-120">XSD 스키마 파일의 경로 및 파일 이름을 입력하거나 **찾아보기**를 클릭하여 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-120">Type the path and file name of the XSD schema file, or locate the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="a745d-121">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="a745d-121">**Browse**</span></span>  
 <span data-ttu-id="a745d-122">**열기** 대화 상자를 사용하여 XSD 스키마 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-122">Use the **Open** dialog box to locate the XSD schema file.</span></span>  
  
 <span data-ttu-id="a745d-123">**XSD 생성**</span><span class="sxs-lookup"><span data-stu-id="a745d-123">**Generate XSD**</span></span>  
 <span data-ttu-id="a745d-124">**다른 이름으로 저장** 대화 상자를 사용하여 자동 생성된 XSD 스키마 파일의 위치를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-124">Use the **Save As** dialog box to select a location for the auto-generated XSD schema file.</span></span> <span data-ttu-id="a745d-125">편집기에서는 XML 데이터의 구조를 통해 스키마를 유추합니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-125">The editor infers the schema from the structure of the XML data.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="a745d-126">데이터 액세스 모드 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="a745d-126">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--xml-file-location"></a><span data-ttu-id="a745d-127">데이터 액세스 모드 = XML 파일 위치</span><span class="sxs-lookup"><span data-stu-id="a745d-127">Data access mode = XML file location</span></span>  
 <span data-ttu-id="a745d-128">**XML 위치**</span><span class="sxs-lookup"><span data-stu-id="a745d-128">**XML location**</span></span>  
 <span data-ttu-id="a745d-129">XML 데이터 파일의 경로 및 파일 이름을 입력하거나 **찾아보기**를 클릭하여 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-129">Type the path and file name of the XML data file, or locate the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="a745d-130">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="a745d-130">**Browse**</span></span>  
 <span data-ttu-id="a745d-131">**열기** 대화 상자를 사용하여 XML 데이터 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-131">Use the **Open** dialog box to locate the XML data file.</span></span>  
  
### <a name="data-access-mode--xml-file-from-variable"></a><span data-ttu-id="a745d-132">데이터 액세스 모드 = 변수를 사용한 XML 파일</span><span class="sxs-lookup"><span data-stu-id="a745d-132">Data access mode = XML file from variable</span></span>  
 <span data-ttu-id="a745d-133">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="a745d-133">**Variable name**</span></span>  
 <span data-ttu-id="a745d-134">XML 파일의 경로 및 파일 이름을 포함하는 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-134">Select the variable that contains the path and file name of the XML file.</span></span>  
  
### <a name="data-access-mode--xml-data-from-variable"></a><span data-ttu-id="a745d-135">데이터 액세스 모드 = 변수를 사용한 XML 데이터</span><span class="sxs-lookup"><span data-stu-id="a745d-135">Data access mode = XML data from variable</span></span>  
 <span data-ttu-id="a745d-136">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="a745d-136">**Variable name**</span></span>  
 <span data-ttu-id="a745d-137">XML 데이터를 포함하는 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a745d-137">Select the variable that contains the XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a745d-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a745d-138">See Also</span></span>  
 <span data-ttu-id="a745d-139">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a745d-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a745d-140">[XML 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/xml-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="a745d-140">[XML Source Editor &#40;Columns Page&#41;](../../2014/integration-services/xml-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="a745d-141">[XML 원본 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="a745d-141">[XML Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="a745d-142">XML 원본을 사용하여 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="a745d-142">Extract Data by Using the XML Source</span></span>](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
