---
title: 열 내보내기 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exportcolumntrans.f1
helpviewer_keywords:
- exporting data
- append options [Integration Services]
- Export Column transformation [Integration Services]
- columns [Integration Services], exporting
- inserting data
- truncate options [Integration Services]
ms.assetid: 678d2dfc-e40c-4fbb-b2cc-42fffc44478a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7ed2bef02d75b72870514e2333d2fa58720fb60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647777"
---
# <a name="export-column-transformation"></a><span data-ttu-id="9e921-102">열 내보내기 변환</span><span class="sxs-lookup"><span data-stu-id="9e921-102">Export Column Transformation</span></span>
  <span data-ttu-id="9e921-103">열 내보내기 변환은 데이터 흐름에서 데이터를 읽어 파일에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-103">The Export Column transformation reads data in a data flow and inserts the data into a file.</span></span> <span data-ttu-id="9e921-104">예를 들어 데이터 흐름에 각 제품 사진과 같은 제품 정보가 포함되어 있으면 열 내보내기 변환을 사용하여 이미지를 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-104">For example, if the data flow contains product information, such as a picture of each product, you could use the Export Column transformation to save the images to files.</span></span>  
  
## <a name="append-and-truncate-options"></a><span data-ttu-id="9e921-105">추가 및 잘림 옵션</span><span class="sxs-lookup"><span data-stu-id="9e921-105">Append and Truncate Options</span></span>  
 <span data-ttu-id="9e921-106">다음 표에서는 추가 및 잘림 옵션 설정이 결과에 미치는 영향을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-106">The following table describes how the settings for the append and truncate options affect results.</span></span>  
  
|<span data-ttu-id="9e921-107">추가</span><span class="sxs-lookup"><span data-stu-id="9e921-107">Append</span></span>|<span data-ttu-id="9e921-108">Truncate</span><span class="sxs-lookup"><span data-stu-id="9e921-108">Truncate</span></span>|<span data-ttu-id="9e921-109">파일 존재 여부</span><span class="sxs-lookup"><span data-stu-id="9e921-109">File exists</span></span>|<span data-ttu-id="9e921-110">결과</span><span class="sxs-lookup"><span data-stu-id="9e921-110">Results</span></span>|  
|------------|--------------|-----------------|-------------|  
|<span data-ttu-id="9e921-111">False</span><span class="sxs-lookup"><span data-stu-id="9e921-111">False</span></span>|<span data-ttu-id="9e921-112">False</span><span class="sxs-lookup"><span data-stu-id="9e921-112">False</span></span>|<span data-ttu-id="9e921-113">예</span><span class="sxs-lookup"><span data-stu-id="9e921-113">No</span></span>|<span data-ttu-id="9e921-114">이 변환은 새 파일을 만들고 해당 파일에 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-114">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="9e921-115">True</span><span class="sxs-lookup"><span data-stu-id="9e921-115">True</span></span>|<span data-ttu-id="9e921-116">False</span><span class="sxs-lookup"><span data-stu-id="9e921-116">False</span></span>|<span data-ttu-id="9e921-117">예</span><span class="sxs-lookup"><span data-stu-id="9e921-117">No</span></span>|<span data-ttu-id="9e921-118">이 변환은 새 파일을 만들고 해당 파일에 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-118">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="9e921-119">False</span><span class="sxs-lookup"><span data-stu-id="9e921-119">False</span></span>|<span data-ttu-id="9e921-120">True</span><span class="sxs-lookup"><span data-stu-id="9e921-120">True</span></span>|<span data-ttu-id="9e921-121">예</span><span class="sxs-lookup"><span data-stu-id="9e921-121">No</span></span>|<span data-ttu-id="9e921-122">이 변환은 새 파일을 만들고 해당 파일에 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-122">The transformation creates a new file and writes the data to the file.</span></span>|  
|<span data-ttu-id="9e921-123">True</span><span class="sxs-lookup"><span data-stu-id="9e921-123">True</span></span>|<span data-ttu-id="9e921-124">True</span><span class="sxs-lookup"><span data-stu-id="9e921-124">True</span></span>|<span data-ttu-id="9e921-125">예</span><span class="sxs-lookup"><span data-stu-id="9e921-125">No</span></span>|<span data-ttu-id="9e921-126">이 변환은 디자인 타임 유효성 검사에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-126">The transformation fails design time validation.</span></span> <span data-ttu-id="9e921-127">두 속성을 모두 `true`로 설정하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-127">It is not valid to set both properties to `true`.</span></span>|  
|<span data-ttu-id="9e921-128">False</span><span class="sxs-lookup"><span data-stu-id="9e921-128">False</span></span>|<span data-ttu-id="9e921-129">False</span><span class="sxs-lookup"><span data-stu-id="9e921-129">False</span></span>|<span data-ttu-id="9e921-130">yes</span><span class="sxs-lookup"><span data-stu-id="9e921-130">Yes</span></span>|<span data-ttu-id="9e921-131">런타임 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-131">A run-time error occurs.</span></span> <span data-ttu-id="9e921-132">이 변환은 파일은 있지만 해당 파일에 쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-132">The file exists, but the transformation cannot write to it.</span></span>|  
|<span data-ttu-id="9e921-133">False</span><span class="sxs-lookup"><span data-stu-id="9e921-133">False</span></span>|<span data-ttu-id="9e921-134">True</span><span class="sxs-lookup"><span data-stu-id="9e921-134">True</span></span>|<span data-ttu-id="9e921-135">yes</span><span class="sxs-lookup"><span data-stu-id="9e921-135">Yes</span></span>|<span data-ttu-id="9e921-136">이 변환은 파일을 삭제하고 다시 만든 후 해당 파일에 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-136">The transformation deletes and re-creates the file and writes the data to the file.</span></span>|  
|<span data-ttu-id="9e921-137">True</span><span class="sxs-lookup"><span data-stu-id="9e921-137">True</span></span>|<span data-ttu-id="9e921-138">False</span><span class="sxs-lookup"><span data-stu-id="9e921-138">False</span></span>|<span data-ttu-id="9e921-139">yes</span><span class="sxs-lookup"><span data-stu-id="9e921-139">Yes</span></span>|<span data-ttu-id="9e921-140">이 변환은 파일을 열고 해당 파일의 끝에 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-140">The transformation opens the file and writes the data at the end of the file.</span></span>|  
|<span data-ttu-id="9e921-141">True</span><span class="sxs-lookup"><span data-stu-id="9e921-141">True</span></span>|<span data-ttu-id="9e921-142">True</span><span class="sxs-lookup"><span data-stu-id="9e921-142">True</span></span>|<span data-ttu-id="9e921-143">yes</span><span class="sxs-lookup"><span data-stu-id="9e921-143">Yes</span></span>|<span data-ttu-id="9e921-144">이 변환은 디자인 타임 유효성 검사에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-144">The transformation fails design time validation.</span></span> <span data-ttu-id="9e921-145">두 속성을 모두 `true`로 설정하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-145">It is not valid to set both properties to `true`.</span></span>|  
  
## <a name="configuration-of-the-export-column-transformation"></a><span data-ttu-id="9e921-146">열 내보내기 변환 구성</span><span class="sxs-lookup"><span data-stu-id="9e921-146">Configuration of the Export Column Transformation</span></span>  
 <span data-ttu-id="9e921-147">다음과 같은 방법으로 열 내보내기 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-147">You can configure the Export Column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="9e921-148">데이터를 쓸 파일 경로가 포함된 열과 데이터 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-148">Specify the data columns and the columns that contain the path of files to which to write the data.</span></span>  
  
-   <span data-ttu-id="9e921-149">데이터 삽입 작업에서 기존 파일을 추가하거나 잘라낼지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-149">Specify whether the data-insertion operation appends or truncates existing files.</span></span>  
  
-   <span data-ttu-id="9e921-150">파일에 BOM(바이트 순서 표시)을 쓸지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-150">Specify whether a byte-order mark (BOM) is written to the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9e921-151">기존 파일에 데이터를 추가하지 않으며 데이터 형식이 DT_NTEXT인 경우에만 BOM이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-151">A BOM is written only when the data is not appended to an existing file and the data has the DT_NTEXT data type.</span></span>  
  
 <span data-ttu-id="9e921-152">이 변환은 입력 열의 쌍을 사용합니다. 그 중 하나에는 파일 이름이 있고 다른 하나에는 데이터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-152">The transformation uses pairs of input columns: One column contains a file name, and the other column contains data.</span></span> <span data-ttu-id="9e921-153">데이터 집합의 각 행에서 서로 다른 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-153">Each row in the data set can specify a different file.</span></span> <span data-ttu-id="9e921-154">변환이 행을 처리하면 지정한 파일에 데이터가 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-154">As the transformation processes a row, the data is inserted into the specified file.</span></span> <span data-ttu-id="9e921-155">런타임 시 파일이 존재하지 않을 경우 이 변환은 새로 파일을 만든 후 데이터를 해당 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-155">At run time, the transformation creates the files, if they do not already exist, and then the transformation writes the data to the files.</span></span> <span data-ttu-id="9e921-156">기록될 데이터 형식은 DT_TEXT, DT_NTEXT 또는 DT_IMAGE여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-156">The data to be written must have a DT_TEXT, DT_NTEXT, or DT_IMAGE data type.</span></span> <span data-ttu-id="9e921-157">자세한 내용은 [Integration Services Data Types](../integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e921-157">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="9e921-158">이 변환에는 하나의 입력, 하나의 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-158">This transformation has one input, one output, and one error output.</span></span>  
  
 <span data-ttu-id="9e921-159">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-159">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="9e921-160">**열 내보내기 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [열 내보내기 변환 편집기&#40;열 페이지&#41;](../../export-column-transformation-editor-columns-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e921-160">For more information about the properties that you can set in the **Export Column Transformation Editor** dialog box, see [Export Column Transformation Editor &#40;Columns Page&#41;](../../export-column-transformation-editor-columns-page.md).</span></span>  
  
 <span data-ttu-id="9e921-161">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e921-161">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="9e921-162">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="9e921-162">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9e921-163">Common Properties</span><span class="sxs-lookup"><span data-stu-id="9e921-163">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="9e921-164">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="9e921-164">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="9e921-165">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e921-165">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
