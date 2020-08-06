---
title: 열 가져오기 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.importcolumntrans.f1
helpviewer_keywords:
- Import Column transformation [Integration Services]
- columns [Integration Services], importing
- importing data, SSIS packages
- inserting data
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4330438614cce7892e74dc9a1dcbb6680b72972
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659567"
---
# <a name="import-column-transformation"></a><span data-ttu-id="37808-102">열 가져오기 변환</span><span class="sxs-lookup"><span data-stu-id="37808-102">Import Column Transformation</span></span>
  <span data-ttu-id="37808-103">열 가져오기 변환은 파일에서 데이터를 읽어 데이터 흐름의 열에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="37808-103">The Import Column transformation reads data from files and adds the data to columns in a data flow.</span></span> <span data-ttu-id="37808-104">이 변환을 사용하면 패키지가 별도의 파일에 저장된 텍스트와 이미지를 데이터 흐름에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37808-104">Using this transformation, a package can add text and images stored in separate files to a data flow.</span></span> <span data-ttu-id="37808-105">예를 들어 제품 정보를 저장하는 테이블에 데이터를 로드하는 데이터 흐름은 파일에서 각 제품에 대한 고객 평가를 가져와서 데이터 흐름에 추가하는 열 가져오기 변환을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37808-105">For example, a data flow that loads data into a table that stores product information can include the Import Column transformation to import customer reviews of each product from files and add the reviews to the data flow.</span></span>  
  
 <span data-ttu-id="37808-106">다음과 같은 방법으로 열 가져오기 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37808-106">You can configure the Import Column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="37808-107">변환에서 데이터를 추가할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37808-107">Specify the columns to which the transformation adds data.</span></span>  
  
-   <span data-ttu-id="37808-108">변환에 BOM(바이트 순서 표시)이 필요한지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="37808-108">Specify whether the transformation expects a byte-order mark (BOM).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="37808-109">BOM은 데이터가 DT_NTEXT 데이터 형식인 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="37808-109">A BOM is only expected if the data has the DT_NTEXT data type.</span></span>  
  
 <span data-ttu-id="37808-110">변환 입력의 열에는 데이터가 저장된 파일 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="37808-110">A column in the transformation input contains the names of files that hold the data.</span></span> <span data-ttu-id="37808-111">데이터 세트의 각 행에서 서로 다른 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37808-111">Each row in the dataset can specify a different file.</span></span> <span data-ttu-id="37808-112">열 가져오기 변환은 행을 처리할 때 파일 이름을 읽고 파일 시스템에서 해당 파일을 연 다음 파일 내용을 출력 열에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="37808-112">When the Import Column transformation processes a row, it reads the file name, opens the corresponding file in the file system, and loads the file content into an output column.</span></span> <span data-ttu-id="37808-113">출력 열의 데이터 형식은 DT_TEXT, DT_NTEXT 또는 DT_IMAGE여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37808-113">The data type of the output column must be DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span> <span data-ttu-id="37808-114">자세한 내용은 [Integration Services Data Types](../integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37808-114">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="37808-115">이 변환에는 하나의 입력, 하나의 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37808-115">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="configuration-of-the-import-column-transformation"></a><span data-ttu-id="37808-116">열 가져오기 변환 구성</span><span class="sxs-lookup"><span data-stu-id="37808-116">Configuration of the Import Column Transformation</span></span>  
 <span data-ttu-id="37808-117">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37808-117">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="37808-118">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="37808-118">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="37808-119">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="37808-119">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="37808-120">Common Properties</span><span class="sxs-lookup"><span data-stu-id="37808-120">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="37808-121">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="37808-121">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="37808-122">관련 작업</span><span class="sxs-lookup"><span data-stu-id="37808-122">Related Tasks</span></span>  
 <span data-ttu-id="37808-123">이 구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37808-123">For information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37808-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37808-124">See Also</span></span>  
 <span data-ttu-id="37808-125">[열 내보내기 변환](export-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="37808-125">[Export Column Transformation](export-column-transformation.md) </span></span>  
 <span data-ttu-id="37808-126">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="37808-126">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="37808-127">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="37808-127">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
