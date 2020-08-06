---
title: 원시 파일 사용자 지정 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7e81f7e1-fac0-4b57-b145-8f1b9e4720bf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7614c03fbf44f37597e586549e306d01c28b523d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648465"
---
# <a name="raw-file-custom-properties"></a><span data-ttu-id="eed80-102">원시 파일 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="eed80-102">Raw File Custom Properties</span></span>
  <span data-ttu-id="eed80-103">**원본 사용자 지정 속성**</span><span class="sxs-lookup"><span data-stu-id="eed80-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="eed80-104">원시 파일 원본에는 사용자 지정 속성과 모든 데이터 흐름 구성 요소에 공통된 속성이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-104">The Raw File source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="eed80-105">다음 표에서는 원시 파일 원본의 사용자 지정 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-105">The following table describes the custom properties of the Raw File source.</span></span> <span data-ttu-id="eed80-106">모든 속성은 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="eed80-107">속성 이름</span><span class="sxs-lookup"><span data-stu-id="eed80-107">Property name</span></span>|<span data-ttu-id="eed80-108">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="eed80-108">Data Type</span></span>|<span data-ttu-id="eed80-109">Description</span><span class="sxs-lookup"><span data-stu-id="eed80-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="eed80-110">AccessMode</span><span class="sxs-lookup"><span data-stu-id="eed80-110">AccessMode</span></span>|<span data-ttu-id="eed80-111">Integer(열거형)</span><span class="sxs-lookup"><span data-stu-id="eed80-111">Integer (enumeration)</span></span>|<span data-ttu-id="eed80-112">원시 데이터에 액세스하는 데 사용되는 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-112">The mode used to access the raw data.</span></span> <span data-ttu-id="eed80-113">가능한 값은 `File name`(0) 및 `File name from variable`(1)입니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-113">The possible values are `File name` (0) and `File name from variable` (1).</span></span> <span data-ttu-id="eed80-114">기본값은 `File name`(0)입니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-114">The default value is `File name` (0).</span></span>|  
|<span data-ttu-id="eed80-115">FileName</span><span class="sxs-lookup"><span data-stu-id="eed80-115">FileName</span></span>|<span data-ttu-id="eed80-116">String</span><span class="sxs-lookup"><span data-stu-id="eed80-116">String</span></span>|<span data-ttu-id="eed80-117">원본 파일의 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-117">The path and file name of the source file.</span></span>|  
  
 <span data-ttu-id="eed80-118">원시 파일 원본의 출력 및 출력 열에는 사용자 지정 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-118">The output and the output columns of the Raw File source have no custom properties.</span></span>  
  
 <span data-ttu-id="eed80-119">자세한 내용은 [Raw File Source](raw-file-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eed80-119">For more information, see [Raw File Source](raw-file-source.md).</span></span>  
  
 <span data-ttu-id="eed80-120">**대상 사용자 지정 속성**</span><span class="sxs-lookup"><span data-stu-id="eed80-120">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="eed80-121">원시 파일 대상에는 사용자 지정 속성과 모든 데이터 흐름 구성 요소에 공통된 속성이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-121">The Raw File destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="eed80-122">다음 표에서는 원시 파일 대상의 사용자 지정 속성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-122">The following table describes the custom properties of the Raw File destination.</span></span> <span data-ttu-id="eed80-123">모든 속성은 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-123">All properties are read/write.</span></span>  
  
|<span data-ttu-id="eed80-124">속성 이름</span><span class="sxs-lookup"><span data-stu-id="eed80-124">Property name</span></span>|<span data-ttu-id="eed80-125">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="eed80-125">Data Type</span></span>|<span data-ttu-id="eed80-126">Description</span><span class="sxs-lookup"><span data-stu-id="eed80-126">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="eed80-127">AccessMode</span><span class="sxs-lookup"><span data-stu-id="eed80-127">AccessMode</span></span>|<span data-ttu-id="eed80-128">Integer(열거형)</span><span class="sxs-lookup"><span data-stu-id="eed80-128">Integer (enumeration)</span></span>|<span data-ttu-id="eed80-129">FileName 속성에 파일 이름이 포함되어 있는지, 아니면 파일 이름이 포함된 변수의 이름이 포함되어 있는지를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-129">A value that specifies whether the FileName property contains a file name, or the name of a variable that contains a file name.</span></span> <span data-ttu-id="eed80-130">옵션으로는 `File name`(0) 및 `File name from variable`(1)이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-130">The options are `File name` (0) and `File name from variable` (1).</span></span>|  
|<span data-ttu-id="eed80-131">FileName</span><span class="sxs-lookup"><span data-stu-id="eed80-131">FileName</span></span>|<span data-ttu-id="eed80-132">String</span><span class="sxs-lookup"><span data-stu-id="eed80-132">String</span></span>|<span data-ttu-id="eed80-133">원시 파일 대상에서 쓰는 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-133">The name of the file to which the Raw File destination writes.</span></span>|  
|<span data-ttu-id="eed80-134">WriteOption</span><span class="sxs-lookup"><span data-stu-id="eed80-134">WriteOption</span></span>|<span data-ttu-id="eed80-135">Integer(열거형)</span><span class="sxs-lookup"><span data-stu-id="eed80-135">Integer (enumeration)</span></span>|<span data-ttu-id="eed80-136">원시 파일 대상에서 이름이 같은 기존 파일을 삭제하는지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-136">A value that specifies whether the Raw File destination deletes an existing file that has the same name.</span></span> <span data-ttu-id="eed80-137">옵션으로는 `Create Always`(0), `Create Once`(1), `Truncate and Append`(3) 및 `Append`(2)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-137">The options are `Create Always` (0), `Create Once` (1), `Truncate and Append` (3), and `Append` (2).</span></span> <span data-ttu-id="eed80-138">이 속성의 기본값은 `Create Always`(0)입니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-138">The default value of this property is `Create Always` (0).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="eed80-139">추가 작업을 수행하려면 추가된 데이터의 메타데이터가 파일에 이미 있는 데이터의 메타데이터와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-139">An append operation requires the metadata of the appended data to match the metadata of the data already present in the file.</span></span>  
  
 <span data-ttu-id="eed80-140">원시 파일 대상의 입력 및 입력 열에는 사용자 지정 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eed80-140">The input and the input columns of the Raw File destination have no custom properties.</span></span>  
  
 <span data-ttu-id="eed80-141">자세한 내용은 [Raw File Destination](raw-file-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eed80-141">For more information, see [Raw File Destination](raw-file-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed80-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eed80-142">See Also</span></span>  
 [<span data-ttu-id="eed80-143">Common Properties</span><span class="sxs-lookup"><span data-stu-id="eed80-143">Common Properties</span></span>](../common-properties.md)  
  
  
