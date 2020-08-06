---
title: 데이터 흐름의 데이터 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- comparing data
- data types [Integration Services], data flow
- parsing [Integration Services]
- string comparisons
- data flow [Integration Services], data options
ms.assetid: 8a9d6186-eb52-48e3-997e-021f24d458a3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a073db65768c413b6cbe648c757ad75d80bd318e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741152"
---
# <a name="data-in-data-flows"></a><span data-ttu-id="6bdf4-102">데이터 흐름의 데이터</span><span class="sxs-lookup"><span data-stu-id="6bdf4-102">Data in Data Flows</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="6bdf4-103">에는 데이터 흐름에 사용되는 데이터 형식 집합이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-103">provides a set of data types that are used in data flows.</span></span>  
  
## <a name="data-type-conversion"></a><span data-ttu-id="6bdf4-104">데이터 형식 변환</span><span class="sxs-lookup"><span data-stu-id="6bdf4-104">Data Type Conversion</span></span>  
 <span data-ttu-id="6bdf4-105">데이터 흐름에 추가하는 원본은 원본 데이터를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-105">The source that you add to a data flow converts the source data to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types.</span></span> <span data-ttu-id="6bdf4-106">이후의 변환에서는 데이터를 다른 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식으로 변환할 수 있으며, 데이터가 로드되는 데이터 저장소 유형에 따라 대상에서 최종 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식을 대상 데이터 저장소에 필요한 데이터 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-106">Subsequent transformations may convert the data to different [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, and depending on the type of data store into which data is loaded, destinations may convert the final [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to the data type required by the destination data store.</span></span> <span data-ttu-id="6bdf4-107">자세한 내용은 [Integration Services Data Types](integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-107">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="6bdf4-108">데이터를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식으로 변환하기 위해 데이터 흐름 구성 요소는 해당 데이터를 구문 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-108">To convert the data to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type, a data flow component parses the data.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="6bdf4-109">에서는 빠른 구문 분석과 표준 구문 분석이라는 두 가지 유형의 구문 분석을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-109">provides two types of data parsing: fast parse and standard parse.</span></span> <span data-ttu-id="6bdf4-110">대부분의 데이터 흐름 구성 요소에서는 표준 구문 분석만 사용할 수 있지만, 플랫 파일 원본과 데이터 변환에서는 빠른 구문 분석이나 표준 구문 분석을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-110">Most data flow components can use only standard parsing; however, the Flat File source and the Data Conversion transformation can use either fast parse or standard parse.</span></span> <span data-ttu-id="6bdf4-111">자세한 내용은 [Parsing Data](parsing-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-111">For more information, see [Parsing Data](parsing-data.md).</span></span>  
  
## <a name="data-type-comparison"></a><span data-ttu-id="6bdf4-112">데이터 형식 압축</span><span class="sxs-lookup"><span data-stu-id="6bdf4-112">Data Type Comparison</span></span>  
 <span data-ttu-id="6bdf4-113">여러 변환에서는 데이터 값을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-113">Many transformations compare data values.</span></span> <span data-ttu-id="6bdf4-114">예를 들어 집계 변환은 일련의 데이터 행에서 값을 집계하기 위해 값을 비교하고, 정렬 변환에서는 값을 정렬하기 위해 비교하고, 조회 변환에서는 값을 별개의 참조 테이블에 있는 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-114">For example, the Aggregate transformation compares values for the purpose of aggregating values across a set of data rows, the Sort transformation compares values in order to sort them, and the Lookup transformation compares values against values in a separate reference table.</span></span> <span data-ttu-id="6bdf4-115">문자열의 비교 방법을 지정하기 위해 변환에는 대/소문자 구분 무시 여부, 일본어 텍스트에서의 가나 형식 취급 방법 및 문자열의 공백 문자 무시 여부와 같은 일련의 비교 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-115">To specify how strings should be compared, the transformation includes a set of comparison options such as whether to ignore case sensitivity, how to handle kana types in Japanese text, and whether to ignore white-space characters in the string.</span></span> <span data-ttu-id="6bdf4-116">자세한 내용은 [Comparing String Data](comparing-string-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-116">For more information, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="6bdf4-117">또한 식 계산기는 변수, 선행 제약 조건 및 변환에서 사용되는 식이 계산될 때 데이터 값을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-117">The expression evaluator also compares data values when it evaluates the expressions that variables, precedence constraints, and transformations use.</span></span>  
  
## <a name="data-flow-troubleshooting"></a><span data-ttu-id="6bdf4-118">데이터 흐름 문제 해결</span><span class="sxs-lookup"><span data-stu-id="6bdf4-118">Data Flow Troubleshooting</span></span>  
 <span data-ttu-id="6bdf4-119">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 카탈로그에 패키지를 배포한 후 실행 중에 데이터 흐름을 분석하여 성능을 검사하거나 다른 문제를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-119">Once you have deployed a package to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalog, you can analyze the data flow in the package during execution to check performance or look for other issues.</span></span> <span data-ttu-id="6bdf4-120">패키지 상태 및 기록을 볼 수 있는 표준 보고서를 사용할 수 있으며, 패키지 실행에 대한 세부 정보를 제공하는 데이터베이스 뷰를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-120">Standard reports are available that allow you to view package status and history, and you can query database views that provide detailed information about package execution.</span></span> <span data-ttu-id="6bdf4-121">실행 중에 데이터 탭을 동적으로 추가 및 제거하여 패키지의 특정 구성 요소를 대상으로 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-121">You also can dynamically add and remove data taps during execution to target specific components of your package.</span></span> <span data-ttu-id="6bdf4-122">자세한 내용은 [데이터 흐름 분석](data-flow.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bdf4-122">For more information, see [Analysis of Data Flow](data-flow.md).</span></span>  
  
  
