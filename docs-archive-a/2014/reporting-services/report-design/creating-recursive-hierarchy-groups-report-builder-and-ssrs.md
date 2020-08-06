---
title: 재귀 계층 구조 그룹 생성(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: aeb99e725c5c61a6dc66c83e53afbc43b1224582
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649406"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a><span data-ttu-id="50946-102">재귀 계층 구조 그룹 생성(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="50946-102">Creating Recursive Hierarchy Groups (Report Builder and SSRS)</span></span>
  <span data-ttu-id="50946-103">부모와 자식 간의 관계가 데이터 집합의 필드로 표현 되는 재귀 데이터를 표시 하려면 자식 필드를 기반으로 데이터 영역 그룹 식을 설정 하 고 부모 필드를 기반으로 부모 속성을 설정 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50946-103">To display recursive data where the relationship between parent and child is represented by fields in the dataset, you can set the data region group expression based on the child field and set the Parent property based on the parent field.</span></span>  
  
 <span data-ttu-id="50946-104">계층적 데이터를 표시하는 것은 조직도의 직원과 같은 재귀 계층 구조 그룹에 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="50946-104">Displaying hierarchical data is a common use for recursive hierarchy groups, for example, employees in an organizational chart.</span></span> <span data-ttu-id="50946-105">데이터 세트에는 직원 및 관리자 목록이 포함되며 관리자 이름은 직원 목록에도 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="50946-105">The dataset includes a list of employees and the managers, where the manager names also appear in the list of employees.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a><span data-ttu-id="50946-106">재귀 계층 만들기</span><span class="sxs-lookup"><span data-stu-id="50946-106">Creating Recursive Hierarchies</span></span>  
 <span data-ttu-id="50946-107">테이블릭스 데이터 영역에서 재귀 계층 구조를 작성하려면 자식 데이터를 지정하는 필드로 그룹 식을 설정하고 부모 데이터를 지정하는 필드로 그룹의 Parent 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50946-107">To build a recursive hierarchy in a tablix data region, you must set the group expression to the field that specifies the child data and the Parent property of the group to the field that specifies the parent data.</span></span> <span data-ttu-id="50946-108">예를 들어 직원 ID 및 관리자 ID에 대한 필드를 포함하는 데이터 세트가 있으며 직원이 관리자에게 보고하는 경우 그룹 식을 직원 ID로 설정하고 Parent 속성을 관리자 ID로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50946-108">For example, for a dataset that includes fields for employee ID and manager ID where employees report to managers, set the group expression to employee ID and the Parent property to manager ID.</span></span>  
  
 <span data-ttu-id="50946-109">재귀 계층 구조로 정의된 그룹, 즉 Parent 속성을 사용하는 그룹에는 그룹 식이 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50946-109">A group that is defined as a recursive hierarchy (that is, a group that uses the Parent property) can have only one group expression.</span></span> <span data-ttu-id="50946-110">입력란 안쪽 여백에 `Level` 함수를 사용하여 계층에서의 수준을 기준으로 직원 이름을 들여쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50946-110">You can use the `Level` function in text box padding to indent employee names based on their level in the hierarchy.</span></span>  
  
 <span data-ttu-id="50946-111">자세한 내용은 [데이터 영역에서 그룹 추가 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) 및 [재귀 계층 구조 그룹 만들기&#40;보고서 작성기 및 SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50946-111">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) and  [Create a Recursive Hierarchy Group &#40;Report Builder and SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).</span></span>  
  
### <a name="aggregate-functions-that-support-recursion"></a><span data-ttu-id="50946-112">재귀를 지원하는 집계 함수</span><span class="sxs-lookup"><span data-stu-id="50946-112">Aggregate Functions that support Recursion</span></span>  
 <span data-ttu-id="50946-113">매개 변수 *Recursive* 를 허용하는 Reporting Services 집계 함수를 사용하여 재귀 계층 구조의 요약 데이터를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50946-113">You can use Reporting Services aggregate functions that accept the parameter *Recursive* to calculate summary data for a recursive hierarchy.</span></span> <span data-ttu-id="50946-114">다음 함수는 `Recursive` [Sum](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [Count](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [countrows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md)및 [VarP](report-builder-functions-varp-function.md)함수를 매개 변수로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="50946-114">The following functions accept `Recursive` as a parameter: [Sum](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [Count](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md), and [VarP](report-builder-functions-varp-function.md).</span></span> <span data-ttu-id="50946-115">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50946-115">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50946-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50946-116">See Also</span></span>  
 <span data-ttu-id="50946-117">[테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="50946-117">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="50946-118">[테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="50946-118">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="50946-119">[집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="50946-119">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="50946-120">[테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="50946-120">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="50946-121">[행렬&#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="50946-121">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="50946-122">[목록&#40;보고서 작성기 및 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="50946-122">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="50946-123">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="50946-123">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
