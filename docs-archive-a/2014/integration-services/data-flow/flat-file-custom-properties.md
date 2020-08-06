---
title: 플랫 파일 사용자 지정 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b906e9268bf3a74ffcf5661953397ad7a24b77a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742420"
---
# <a name="flat-file-custom-properties"></a><span data-ttu-id="39afb-102">플랫 파일 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="39afb-102">Flat File Custom Properties</span></span>
  <span data-ttu-id="39afb-103">**원본 사용자 지정 속성**</span><span class="sxs-lookup"><span data-stu-id="39afb-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="39afb-104">플랫 파일 원본에는 사용자 지정 속성과 모든 데이터 흐름 구성 요소에 공통된 속성이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-104">The Flat File source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="39afb-105">다음 표에서는 플랫 파일 원본의 사용자 지정 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-105">The following table describes the custom properties of the Flat File source.</span></span> <span data-ttu-id="39afb-106">모든 속성은 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="39afb-107">속성 이름</span><span class="sxs-lookup"><span data-stu-id="39afb-107">Property name</span></span>|<span data-ttu-id="39afb-108">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="39afb-108">Data Type</span></span>|<span data-ttu-id="39afb-109">Description</span><span class="sxs-lookup"><span data-stu-id="39afb-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="39afb-110">FileNameColumnName</span><span class="sxs-lookup"><span data-stu-id="39afb-110">FileNameColumnName</span></span>|<span data-ttu-id="39afb-111">String</span><span class="sxs-lookup"><span data-stu-id="39afb-111">String</span></span>|<span data-ttu-id="39afb-112">파일 이름이 포함된 출력 열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-112">The name of an output column that contains the file name.</span></span> <span data-ttu-id="39afb-113">이름이 지정되지 않은 경우 파일 이름이 포함된 출력 열이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-113">If no name is specified, no output column containing the file name will be generated.</span></span><br /><br /> <span data-ttu-id="39afb-114">참고: 이 속성은 **플랫 파일 원본 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-114">Note: This property is not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
|<span data-ttu-id="39afb-115">RetainNulls</span><span class="sxs-lookup"><span data-stu-id="39afb-115">RetainNulls</span></span>|<span data-ttu-id="39afb-116">부울</span><span class="sxs-lookup"><span data-stu-id="39afb-116">Boolean</span></span>|<span data-ttu-id="39afb-117">데이터 변환 파이프라인 엔진에서 데이터를 처리할 때 원본 파일의 Null 값을 Null 값으로 유지할지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-117">A value that specifies whether to retain Null values from the source file as Null values when the data is processed by the Data Transformation Pipeline engine.</span></span> <span data-ttu-id="39afb-118">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-118">The default value of this property is `False`.</span></span>|  
  
 <span data-ttu-id="39afb-119">플랫 파일 원본의 출력에는 사용자 지정 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-119">The output of the Flat File source has no custom properties.</span></span>  
  
 <span data-ttu-id="39afb-120">다음 표에서는 플랫 파일 원본 출력 열의 사용자 지정 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-120">The following table describes the custom properties of the output columns of the Flat File source.</span></span> <span data-ttu-id="39afb-121">모든 속성은 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-121">All properties are read/write.</span></span>  
  
|<span data-ttu-id="39afb-122">속성 이름</span><span class="sxs-lookup"><span data-stu-id="39afb-122">Property name</span></span>|<span data-ttu-id="39afb-123">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="39afb-123">Data Type</span></span>|<span data-ttu-id="39afb-124">Description</span><span class="sxs-lookup"><span data-stu-id="39afb-124">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="39afb-125">FastParse</span><span class="sxs-lookup"><span data-stu-id="39afb-125">FastParse</span></span>|<span data-ttu-id="39afb-126">부울</span><span class="sxs-lookup"><span data-stu-id="39afb-126">Boolean</span></span>|<span data-ttu-id="39afb-127">열이 DTS에서 제공하는 더 빠르지만 로캘을 구분하지 않는 빠른 구문 분석 루틴을 사용하는지, 아니면 로캘을 구분하는 표준 구문 분석 루틴을 사용하는지를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-127">A value that indicates whether the column uses the quicker, but locale-insensitive, fast parsing routines that DTS provides or the locale-sensitive standard parsing routines.</span></span> <span data-ttu-id="39afb-128">자세한 내용은 [Fast Parse](../fast-parse.md) 및 [Standard Parse](../standard-parse.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39afb-128">For more information, see [Fast Parse](../fast-parse.md) and [Standard Parse](../standard-parse.md).</span></span> <span data-ttu-id="39afb-129">이 속성의 기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-129">The default value of this property is `False`.</span></span><br /><br /> <span data-ttu-id="39afb-130">참고: 이 속성은 **플랫 파일 원본 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-130">Note: This property is not available in the **Flat File Source Editor**, but can be set by using the **Advanced Editor**.</span></span>|  
  
 <span data-ttu-id="39afb-131">자세한 내용은 [Flat File Source](flat-file-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39afb-131">For more information, see [Flat File Source](flat-file-source.md).</span></span>  
  
 <span data-ttu-id="39afb-132">**대상 사용자 지정 속성**</span><span class="sxs-lookup"><span data-stu-id="39afb-132">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="39afb-133">플랫 파일 대상에는 사용자 지정 속성과 모든 데이터 흐름 구성 요소에 공통된 속성이 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-133">The Flat File destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="39afb-134">다음 표에서는 플랫 파일 대상의 사용자 지정 속성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-134">The following table describes the custom properties of the Flat File destination.</span></span> <span data-ttu-id="39afb-135">모든 속성은 읽기/쓰기가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-135">All properties are read/write.</span></span>  
  
|<span data-ttu-id="39afb-136">속성 이름</span><span class="sxs-lookup"><span data-stu-id="39afb-136">Property name</span></span>|<span data-ttu-id="39afb-137">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="39afb-137">Data Type</span></span>|<span data-ttu-id="39afb-138">Description</span><span class="sxs-lookup"><span data-stu-id="39afb-138">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="39afb-139">헤더</span><span class="sxs-lookup"><span data-stu-id="39afb-139">Header</span></span>|<span data-ttu-id="39afb-140">String</span><span class="sxs-lookup"><span data-stu-id="39afb-140">String</span></span>|<span data-ttu-id="39afb-141">데이터를 쓰기 전에 파일에 삽입할 텍스트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-141">A block of text that is inserted in the file before any data is written.</span></span><br /><br /> <span data-ttu-id="39afb-142">이 속성의 값은 속성 식을 사용하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-142">The value of this property can be specified by using a property expression.</span></span>|  
|<span data-ttu-id="39afb-143">Overwrite</span><span class="sxs-lookup"><span data-stu-id="39afb-143">Overwrite</span></span>|<span data-ttu-id="39afb-144">부울</span><span class="sxs-lookup"><span data-stu-id="39afb-144">Boolean</span></span>|<span data-ttu-id="39afb-145">이름이 같은 기존 대상 파일을 덮어쓸지, 아니면 해당 파일에 추가할지를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-145">A value that specifies whether to overwrite or append to an existing destination file that has the same name.</span></span> <span data-ttu-id="39afb-146">이 속성의 기본값은 `True`입니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-146">The default value of this property is `True`.</span></span>|  
  
 <span data-ttu-id="39afb-147">플랫 파일 대상의 입력 및 입력 열에는 사용자 지정 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39afb-147">The input and the input columns of the Flat File destination have no custom properties.</span></span>  
  
 <span data-ttu-id="39afb-148">자세한 내용은 [Flat File Destination](flat-file-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39afb-148">For more information, see [Flat File Destination](flat-file-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39afb-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39afb-149">See Also</span></span>  
 [<span data-ttu-id="39afb-150">Common Properties</span><span class="sxs-lookup"><span data-stu-id="39afb-150">Common Properties</span></span>](../common-properties.md)  
  
  
