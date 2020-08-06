---
title: 드릴스루를 사용 하 여 원본 데이터 검색 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5601a3ddfa7075ed53330e12c260af88648db990
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651353"
---
# <a name="using-drillthrough-to-retrieve-source-data-mdx"></a><span data-ttu-id="17a1c-102">DRILLTHROUGH를 사용하여 원본 데이터 검색(MDX)</span><span class="sxs-lookup"><span data-stu-id="17a1c-102">Using DRILLTHROUGH to Retrieve Source Data (MDX)</span></span>
  <span data-ttu-id="17a1c-103">MDX(Multidimensional Expressions)는 [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough)문을 사용하여 큐브 셀의 원본 데이터에서 행 집합을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-103">Multidimensional Expressions (MDX) uses the [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough)statement to retrieve a rowset from the source data for a cube cell.</span></span>  
  
 <span data-ttu-id="17a1c-104">큐브에서 `DRILLTHROUGH` 문을 실행하려면 해당 큐브에 대한 드릴스루 동작을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-104">In order to run a `DRILLTHROUGH` statement on a cube, a drillthrough action must be defined for that cube.</span></span> <span data-ttu-id="17a1c-105">드릴스루 동작을 정의하려면 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 큐브 디자이너에서 **동작** 창의 도구 모음에서 **새 드릴스루 동작**을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="17a1c-105">To define a drillthrough action, in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], in Cube Designer, on the **Actions** pane, on the toolbar, click **New Drillthrough Action**.</span></span> <span data-ttu-id="17a1c-106">새 드릴스루 동작에서 동작 이름, 대상, 조건 및 `DRILLTHROUGH` 문이 반환하는 열을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="17a1c-106">In the new drillthrough action, specify the action name, target, condition, and the columns that are returned by a `DRILLTHROUGH` statement.</span></span>  
  
## <a name="drillthrough-statement-syntax"></a><span data-ttu-id="17a1c-107">DRILLTHROUGH 문 구문</span><span class="sxs-lookup"><span data-stu-id="17a1c-107">DRILLTHROUGH Statement Syntax</span></span>  
 <span data-ttu-id="17a1c-108">`DRILLTHROUGH` 문의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-108">The `DRILLTHROUGH` statement uses the following syntax:</span></span>  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 <span data-ttu-id="17a1c-109">`SELECT` 절은 검색할 원본 데이터를 포함하는 큐브를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-109">The `SELECT` clause identifies the cube cell that contains the source data to be retrieved.</span></span> <span data-ttu-id="17a1c-110">이 `SELECT` 절은 `SELECT` 절에서 각 축에 한 개의 멤버만 지정할 수 있다는 점 이외에는 통상적인 MDX `SELECT` 문과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-110">This `SELECT` clause is the same to an ordinary MDX `SELECT` statement, except that in the `SELECT` clause only one member can be specified on each axis.</span></span> <span data-ttu-id="17a1c-111">한 개의 축에 멤버를 두 개 이상 지정하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-111">If more than one member is specified on an axis, an error occurs.</span></span>  
  
 <span data-ttu-id="17a1c-112">`<Max_Rows>` 구문은 반환된 각 행 집합의 최대 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-112">The `<Max_Rows>` syntax specifies the maximum number of the rows in each returned rowset.</span></span> <span data-ttu-id="17a1c-113">데이터 원본에 연결하는 데 사용되는 OLE DB 공급자가 `DBPROP_MAXROWS`를 지원하지 않으면 `<Max_Rows>` 설정은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-113">If the OLE DB provider that is used to connect to the data source does not support `DBPROP_MAXROWS`, the `<Max_Rows>` setting is ignored.</span></span>  
  
 <span data-ttu-id="17a1c-114">`<First_Rowset>` 구문은 행 집합이 먼저 반환되는 파티션을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-114">The `<First_Rowset>` syntax identifies the partition whose rowset is returned first.</span></span>  
  
 <span data-ttu-id="17a1c-115">`<Return_Columns>` 구문은 반환할 기본 데이터베이스 열을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-115">The `<Return_Columns>` syntax identifies the underlying database columns to be returned.</span></span>  
  
## <a name="drillthrough-statement-example"></a><span data-ttu-id="17a1c-116">DRILLTHROUGH 문 예</span><span class="sxs-lookup"><span data-stu-id="17a1c-116">DRILLTHROUGH Statement Example</span></span>  
 <span data-ttu-id="17a1c-117">다음 예에서는 `DRILLTHROUGH` 문의 사용 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-117">The following example demonstrates the use of the `DRILLTHROUGH` statement.</span></span> <span data-ttu-id="17a1c-118">이 예에서 DRILLTHROUGH 문은 상점 차원(slicer 축)을 따라 Store, Product 및 Time 차원 리프를 쿼리한 다음 부서 측정값 그룹, 부서 ID 및 직원의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="17a1c-118">In this example, the DRILLTHROUGH statement queries the leaves of the Store, Product, and Time dimensions along the Stores dimension (the slicer axis), and then returns the department measure group, department ID, and employee's first name.</span></span>  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a><span data-ttu-id="17a1c-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17a1c-119">See Also</span></span>  
 [<span data-ttu-id="17a1c-120">데이터 조작&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="17a1c-120">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
  
