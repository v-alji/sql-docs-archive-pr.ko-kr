---
title: 데이터 변환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 57b1f70c070cdf81dc0bc899ed365d048db26cc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646568"
---
# <a name="data-conversion-transformation"></a><span data-ttu-id="0822c-102">데이터 변환</span><span class="sxs-lookup"><span data-stu-id="0822c-102">Data Conversion Transformation</span></span>
  <span data-ttu-id="0822c-103">데이터 변환은 입력 열의 데이터를 다른 데이터 형식으로 변환한 다음 새 출력 열에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-103">The Data Conversion transformation converts the data in an input column to a different data type and then copies it to a new output column.</span></span> <span data-ttu-id="0822c-104">예를 들어 패키지는 여러 개의 원본에서 데이터를 추출한 다음 이 변환을 사용하여 대상 데이터 저장소에 필요한 데이터 형식으로 열을 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-104">For example, a package can extract data from multiple sources, and then use this transformation to convert columns to the data type required by the destination data store.</span></span> <span data-ttu-id="0822c-105">단일 입력 열에 여러 개의 변환을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-105">You can apply multiple conversions to a single input column.</span></span>  
  
 <span data-ttu-id="0822c-106">이 변환을 사용하면 패키지가 다음 유형의 데이터 변환을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-106">Using this transformation, a package can perform the following types of data conversions:</span></span>  
  
-   <span data-ttu-id="0822c-107">데이터 형식을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-107">Change the data type.</span></span> <span data-ttu-id="0822c-108">자세한 내용은 [Integration Services Data Types](../integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0822c-108">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0822c-109">데이터를 날짜 또는 datetime 데이터 형식으로 변환하는 경우 출력 열의 날짜는 로캘 기본 설정에서 다른 형식을 지정해도 ISO 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-109">If you are converting data to a date or a datetime data type, the date in the output column is in the ISO format, although the locale preference may specify a different format.</span></span>  
  
-   <span data-ttu-id="0822c-110">문자열 데이터의 열 길이와 숫자 데이터의 전체 자릿수 및 소수 자릿수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-110">Set the column length of string data and the precision and scale on numeric data.</span></span> <span data-ttu-id="0822c-111">자세한 내용은 [전체 자릿수, 소수 자릿수 및 길이&#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0822c-111">For more information, see [Precision, Scale, and Length &#40;Transact-SQL&#41;](/sql/t-sql/data-types/precision-scale-and-length-transact-sql).</span></span>  
  
-   <span data-ttu-id="0822c-112">코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-112">Specify a code page.</span></span> <span data-ttu-id="0822c-113">자세한 내용은 [Comparing String Data](../comparing-string-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0822c-113">For more information, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0822c-114">문자열 데이터 형식의 열을 다른 문자열 데이터 형식의 열로 복사하는 경우 두 열이 동일한 코드 페이지를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-114">When copying between columns with a string data type, the two columns must use the same code page.</span></span>  
  
 <span data-ttu-id="0822c-115">문자열 데이터의 출력 열 길이가 해당 입력 열의 길이보다 짧으면 출력 데이터가 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-115">If the length of an output column of string data is shorter than the length of its corresponding input column, the output data is truncated.</span></span> <span data-ttu-id="0822c-116">자세한 내용은 [데이터 오류 처리](../error-handling-in-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0822c-116">For more information, see [Error Handling in Data](../error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="0822c-117">이 변환에는 하나의 입력, 하나의 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-117">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0822c-118">관련 작업</span><span class="sxs-lookup"><span data-stu-id="0822c-118">Related Tasks</span></span>  
 <span data-ttu-id="0822c-119">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0822c-119">You can set properties through the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span> <span data-ttu-id="0822c-120">SSIS 디자이너에서 데이터 변환을 사용하는 방법은 [데이터 변환을 사용하여 데이터를 다른 데이터 형식으로 변환](data-conversion-transformation.md) 및 [데이터 변환 편집기](../../data-conversion-transformation-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0822c-120">For information about using the Data Conversion Transformation in the SSIS Designer, see [Convert Data to a Different Data Type by Using the Data Conversion Transformation](data-conversion-transformation.md) and [Data Conversion Transformation Editor](../../data-conversion-transformation-editor.md).</span></span> <span data-ttu-id="0822c-121">이 변환의 속성을 프로그래밍 방식으로 설정하는 방법은 [공용 속성](../../common-properties.md) 및 [변환 사용자 지정 속성](transformation-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0822c-121">For information about setting properties of this transformation programmatically, see [Common Properties](../../common-properties.md) and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="0822c-122">관련 내용</span><span class="sxs-lookup"><span data-stu-id="0822c-122">Related Content</span></span>  
 <span data-ttu-id="0822c-123">blogs.msdn.com의 블로그 항목 - [SSIS 2008의 데이터 형식 변환 기술 간 성능 비교](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035)</span><span class="sxs-lookup"><span data-stu-id="0822c-123">Blog entry, [Performance Comparison between Data Type Conversion Techniques in SSIS 2008](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0822c-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0822c-124">See Also</span></span>  
 <span data-ttu-id="0822c-125">[빠른 구문 분석](../../fast-parse.md) </span><span class="sxs-lookup"><span data-stu-id="0822c-125">[Fast Parse](../../fast-parse.md) </span></span>  
 <span data-ttu-id="0822c-126">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="0822c-126">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="0822c-127">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="0822c-127">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
