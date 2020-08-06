---
title: 계산 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2da86ae5c5652c8b2614cae4bbb721802700d973
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649710"
---
# <a name="calculations-ssas-tabular"></a><span data-ttu-id="56e96-102">계산(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="56e96-102">Calculations (SSAS Tabular)</span></span>
  <span data-ttu-id="56e96-103">데이터를 모델로 가져온 후에는 계산을 추가하여 해당 데이터를 집계, 필터링, 확장, 결합 및 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56e96-103">After you have imported data into your model, you can add calculations to aggregate, filter, extend, combine, and secure that data.</span></span> <span data-ttu-id="56e96-104">테이블 형식 모델에서는 사용자 지정 계산을 만들기 위한 수식 언어인 DAX(Data Analysis Expressions)가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56e96-104">Tabular models use Data Analysis Expressions (DAX), a formula language for creating custom calculations.</span></span> <span data-ttu-id="56e96-105">테이블 형식 모델에서 DAX 수식을 사용하여 만드는 계산은 *계산 열*, *측정값*및 *행 필터*에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="56e96-105">In tabular models, the calculations you create by using DAX formulas are used in *Calculated Columns*, *Measures*, and *Row Filters*.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56e96-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="56e96-106">In This Section</span></span>  
  
|<span data-ttu-id="56e96-107">항목</span><span class="sxs-lookup"><span data-stu-id="56e96-107">Topic</span></span>|<span data-ttu-id="56e96-108">Description</span><span class="sxs-lookup"><span data-stu-id="56e96-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="56e96-109">테이블 형식 모델의 DAX 이해&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="56e96-109">Understanding DAX in Tabular Models &#40;SSAS Tabular&#41;</span></span>](understanding-dax-in-tabular-models-ssas-tabular.md)|<span data-ttu-id="56e96-110">테이블 형식 모델에서 계산 열, 측정값 및 행 필터에 대한 계산을 만드는 데 사용되는 DAX(Data Analysis Expressions) 수식 언어에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="56e96-110">Describes the Data Analysis Expressions (DAX) formula language used to create calculations for calculated columns, measures, and row filters in tabular models.</span></span>|  
|[<span data-ttu-id="56e96-111">DirectQuery 모드에서의 수식 호환성</span><span class="sxs-lookup"><span data-stu-id="56e96-111">Formula Compatibility in DirectQuery Mode</span></span>](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md)|<span data-ttu-id="56e96-112">차이점을 설명하고, DirectQuery 모드에서 지원되지 않는 함수와 지원은 되지만 다른 결과를 반환할 수 있는 함수의 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56e96-112">Describes the differences, lists the functions that are not supported in DirectQuery mode, and lists the functions that are supported but could return different results.</span></span>|  
|[<span data-ttu-id="56e96-113">DAX&#41; 참조 &#40;데이터 분석 식</span><span class="sxs-lookup"><span data-stu-id="56e96-113">Data Analysis Expressions &#40;DAX&#41; Reference</span></span>](/dax/data-analysis-expressions-dax-reference)|<span data-ttu-id="56e96-114">이 섹션에서는 DAX 구문, 연산자 및 함수에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="56e96-114">This section provides detailed descriptions of DAX syntax, operators, and functions.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="56e96-115">이 섹션에서는 계산을 만드는 단계별 태스크는 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56e96-115">Step-by-step tasks for creating calculations are not provided in this section.</span></span> <span data-ttu-id="56e96-116">계산은 계산 열, 측정값 및 역할의 행 필터에 지정되기 때문에 DAX 수식을 만드는 장소에 대한 지침은 해당 기능과 관련된 태스크에서 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56e96-116">Because calculations are specified in calculated columns, measures, and row filters (in roles), instructions on where to create DAX formulas are provided in tasks related to those features.</span></span> <span data-ttu-id="56e96-117">자세한 내용은 [계산 열 만들기&#40;SSAS 테이블 형식&#41;](ssas-calculated-columns-create-a-calculated-column.md), [측정값 만들기 및 관리&#40;SSAS 테이블 형식&#41;](measures-ssas-tabular.md) 및 [역할 만들기 및 관리&#40;SSAS 테이블 형식&#41;](roles-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56e96-117">For more information, see [Create a Calculated Column &#40;SSAS Tabular&#41;](ssas-calculated-columns-create-a-calculated-column.md), [Create and Manage Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md), and [Create and Manage Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56e96-118">DAX를 사용하여 테이블 형식 모델을 쿼리할 수도 있지만 이 섹션에서는 DAX 수식을 사용하여 계산을 만드는 과정에 대해서만 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="56e96-118">While DAX can also be used to query a tabular model, topics in this section focus specifically on using DAX formulas to create calculations.</span></span>  
  
  
