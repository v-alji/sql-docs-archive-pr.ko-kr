---
title: 모델 필터 구문 및 예 (Analysis Services 데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filter syntax [data mining]
- filters [data mining]
- filters [Analysis Services]
ms.assetid: c729d9b3-8fda-405e-9497-52b2d7493eae
author: minewiskan
ms.author: owend
ms.openlocfilehash: f7ca200d179c0fe81b948793a4b4478f71502657
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728971"
---
# <a name="model-filter-syntax-and-examples-analysis-services---data-mining"></a><span data-ttu-id="bc111-102">모델 필터 구문 및 예(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="bc111-102">Model Filter Syntax and Examples (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="bc111-103">이 섹션에서는 샘플 식과 함께 모델 필터 구문에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-103">This section provides detailed information about the syntax for model filters, together with sample expressions.</span></span>  
  
 
  
##  <a name="filter-syntax"></a><a name="bkmk_Syntax"></a> <span data-ttu-id="bc111-104">Filter Syntax</span><span class="sxs-lookup"><span data-stu-id="bc111-104">Filter Syntax</span></span>  
 <span data-ttu-id="bc111-105">일반적으로 필터 식은 WHERE 절의 내용에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-105">Filter expressions generally are equivalent to the content of a WHERE clause.</span></span> <span data-ttu-id="bc111-106">논리 연산자 `AND`, `OR` 및 `NOT`을 사용하여 여러 조건을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-106">You can connect multiple conditions by using the logical operators `AND`, `OR`, and `NOT`.</span></span>  
  
 <span data-ttu-id="bc111-107">중첩 테이블에서는 `EXISTS` 및 `NOT EXISTS` 연산자도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-107">In nested tables, you can also use the `EXISTS` and `NOT EXISTS` operators.</span></span> <span data-ttu-id="bc111-108">`EXISTS` 조건은 하위 쿼리가 하나 이상의 행을 반환하는 경우 `true`로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-108">An `EXISTS` condition evaluates to `true` if the subquery returns at least one row.</span></span> <span data-ttu-id="bc111-109">이는 중첩 테이블에 특정 값을 포함하는 사례로 모델을 제한하려는 경우 유용합니다. 특정 제품을 한 번 이상 구매한 고객으로 모델을 제한하려는 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-109">This is useful in cases where you want to restrict the model to cases that contain a particular value in the nested table: for example, customers who have purchased an item at least once.</span></span>  
  
 <span data-ttu-id="bc111-110">`NOT EXISTS` 조건은 하위 쿼리에 지정된 조건이 없는 경우 `true`로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-110">A `NOT EXISTS` condition evaluates to `true` if the condition specified in the subquery does not exist.</span></span> <span data-ttu-id="bc111-111">특정 제품을 구매한 적이 없는 고객으로 모델을 제한하려는 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-111">An example is when you want to restrict the model to customers who have never purchased a particular item.</span></span>  
  
 <span data-ttu-id="bc111-112">일반 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-112">The general syntax is as follows:</span></span>  
  
```  
<filter>::=<predicate list>  | ( <predicate list> )  
<predicate list>::= <predicate> | [<logical_operator> <predicate list>]   
<logical_operator::= AND| OR  
<predicate>::= NOT <predicate>|( <predicate> ) <avPredicate> | <nestedTablePredicate> | ( <predicate> )   
<avPredicate>::= <columnName> <operator> <scalar> | <columnName> IS [NOT] NULL  
<operator>::= = | != | <> | > | >= | < | <=  
<nestedTablePredicate>::= EXISTS (<subquery>)  
<subquery>::=SELECT * FROM <columnName>[ WHERE  <predicate list> ]  
```  
  
 <span data-ttu-id="bc111-113">*필터가*</span><span class="sxs-lookup"><span data-stu-id="bc111-113">*filter*</span></span>  
 <span data-ttu-id="bc111-114">논리 연산자로 연결된 하나 이상의 조건자를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-114">Contains one or more predicates, connected by logical operators.</span></span>  
  
 <span data-ttu-id="bc111-115">*predicate list*</span><span class="sxs-lookup"><span data-stu-id="bc111-115">*predicate list*</span></span>  
 <span data-ttu-id="bc111-116">논리 연산자로 구분된 하나 이상의 올바른 필터 식입니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-116">One or more valid filter expressions, separated by logical operators.</span></span>  
  
 <span data-ttu-id="bc111-117">*columnName*</span><span class="sxs-lookup"><span data-stu-id="bc111-117">*columnName*</span></span>  
 <span data-ttu-id="bc111-118">마이닝 구조 열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-118">The name of a mining structure column.</span></span>  
  
 <span data-ttu-id="bc111-119">logical_operator</span><span class="sxs-lookup"><span data-stu-id="bc111-119">logical operator</span></span>  
 <span data-ttu-id="bc111-120">`AND`, `OR`, `NOT`</span><span class="sxs-lookup"><span data-stu-id="bc111-120">`AND`, `OR`, `NOT`</span></span>  
  
 <span data-ttu-id="bc111-121">*avPredicate*</span><span class="sxs-lookup"><span data-stu-id="bc111-121">*avPredicate*</span></span>  
 <span data-ttu-id="bc111-122">스칼라 마이닝 구조 열에만 적용할 수 있는 필터 식입니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-122">Filter expression that can be applied to scalar mining structure column only.</span></span> <span data-ttu-id="bc111-123">*avPredicate* 식은 모델 필터나 중첩 테이블 필터 모두에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-123">An *avPredicate* expression can be used in both model filters or nested table filters.</span></span>  
  
 <span data-ttu-id="bc111-124">다음 연산자를 사용하는 식은 연속 열에만 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-124">An expression that uses any of the following operators can only be applied to a continuous column.</span></span> <span data-ttu-id="bc111-125">:</span><span class="sxs-lookup"><span data-stu-id="bc111-125">:</span></span>  
  
-   <span data-ttu-id="bc111-126">**\<**(보다 작음)</span><span class="sxs-lookup"><span data-stu-id="bc111-126">**\<** (less than)</span></span>  
  
-   <span data-ttu-id="bc111-127">**>**(보다 큼)</span><span class="sxs-lookup"><span data-stu-id="bc111-127">**>** (greater than)</span></span>  
  
-   <span data-ttu-id="bc111-128">**>=**(크거나 같음)</span><span class="sxs-lookup"><span data-stu-id="bc111-128">**>=** (greater than or equal to)</span></span>  
  
-   <span data-ttu-id="bc111-129">**\<=**(작거나 같음)</span><span class="sxs-lookup"><span data-stu-id="bc111-129">**\<=** (less than or equal to)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc111-130">데이터 형식과 관계없이 이러한 연산자는 유형이 `Discrete`, `Discretized` 또는 `Key`인 열에 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-130">Regardless of the data type, these operators cannot be applied to a column that has the type `Discrete`, `Discretized`, or `Key`.</span></span>  
  
 <span data-ttu-id="bc111-131">다음 연산자를 사용하는 식은 연속 열, 불연속 열, 분할된 열 또는 키 열에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-131">An expression that uses any of the following operators can be applied to a continuous, discrete, discretized, or key column:</span></span>  
  
-   <span data-ttu-id="bc111-132">**=** 같거나</span><span class="sxs-lookup"><span data-stu-id="bc111-132">**=** (equals)</span></span>  
  
-   <span data-ttu-id="bc111-133">**! =** (같지 않음)</span><span class="sxs-lookup"><span data-stu-id="bc111-133">**!=** (not equal to)</span></span>  
  
-   <span data-ttu-id="bc111-134">**NULL**</span><span class="sxs-lookup"><span data-stu-id="bc111-134">**IS NULL**</span></span>  
  
 <span data-ttu-id="bc111-135">*avPredicate*인수가 불연속 열에 적용되는 경우 필터에 사용되는 값은 특정 버킷의 임의 값이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-135">If the argument, *avPredicate*, applies to a discretized column, the value used in the filter can be any value in a specific bucket.</span></span>  
  
 <span data-ttu-id="bc111-136">즉, 조건을 `AgeDisc = '25-35'`로 정의하지 않고 해당 구간에서 값을 컴퓨팅하여 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-136">In other words, you do not define the condition as `AgeDisc = '25-35'`, but instead compute and then use a value from that interval.</span></span>  
  
 <span data-ttu-id="bc111-137">예를 들어  `AgeDisc = 27`  은 27과 같은 구간(이 경우 25-35)에 있는 임의의 값을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-137">Example:  `AgeDisc = 27`  means any value in the same interval as 27, which in this case is 25-35.</span></span>  
  
 <span data-ttu-id="bc111-138">*nestedTablePredicate*</span><span class="sxs-lookup"><span data-stu-id="bc111-138">*nestedTablePredicate*</span></span>  
 <span data-ttu-id="bc111-139">중첩 테이블에 적용되는 필터 식입니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-139">Filter expression that applies to a nested table.</span></span> <span data-ttu-id="bc111-140">모델 필터에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-140">Can be used in model filters only.</span></span>  
  
 <span data-ttu-id="bc111-141">*nestedTablePredicate*의 하위 쿼리 인수는 테이블 마이닝 구조 열에만 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-141">The sub-query argument of the argument, *nestedTablePredicate*, can only apply to a table mining structure column</span></span>  
  
 <span data-ttu-id="bc111-142">하위 쿼리</span><span class="sxs-lookup"><span data-stu-id="bc111-142">subquery</span></span>  
 <span data-ttu-id="bc111-143">올바른 조건자 또는 조건자 목록 앞에 오는 SELECT 문입니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-143">A SELECT statement followed by a valid predicate or list of predicates.</span></span>  
  
 <span data-ttu-id="bc111-144">모든 조건자는 *avPredicates*에 설명된 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-144">All the predicates must be of the type described in *avPredicates*.</span></span> <span data-ttu-id="bc111-145">또한 조건자는 현재 중첩 테이블에 포함되어 있으며 *columnName*인수로 식별되는 열만 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-145">Furthermore, the predicates can refer only to columns that are included in the current nested table, identified by the argument, *columnName*.</span></span>  
  
### <a name="limitations-on-filter-syntax"></a><span data-ttu-id="bc111-146">필터 구문의 제한 사항</span><span class="sxs-lookup"><span data-stu-id="bc111-146">Limitations on Filter Syntax</span></span>  
 <span data-ttu-id="bc111-147">필터에는 다음 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-147">The following restrictions apply to filters:</span></span>  
  
-   <span data-ttu-id="bc111-148">필터는 간단한 조건자만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-148">A filter can contain only simple predicates.</span></span> <span data-ttu-id="bc111-149">여기에는 수치 연산자, 스칼라 및 열 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-149">These include mathematical operators, scalars, and column names.</span></span>  
  
-   <span data-ttu-id="bc111-150">사용자 정의 함수는 필터 구문에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-150">User-defined functions are not supported in the filter syntax.</span></span>  
  
-   <span data-ttu-id="bc111-151">더하기 기호나 빼기 기호 같이 부울이 아닌 연산자는 필터 구문에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-151">Non-Boolean operators, such as the plus or minus signs, are not supported in the filter syntax.</span></span>  
  
## <a name="examples-of-filters"></a><span data-ttu-id="bc111-152">필터 예</span><span class="sxs-lookup"><span data-stu-id="bc111-152">Examples of Filters</span></span>  
 <span data-ttu-id="bc111-153">다음 예에서는 마이닝 모델에 적용되는 필터의 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-153">The following examples demonstrate the use of filters applied to a mining model.</span></span> <span data-ttu-id="bc111-154">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 사용하여 **속성** 창 및 필터 대화 상자의 **식** 창에서 필터 식을 만드는 경우 WITH FILTER 키워드 뒤에 나타나는 문자열만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-154">If you create the filter expression by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Property** window and the **Expression** pane of the filter dialog box, you would see only the string that appears after the WITH FILTER keywords.</span></span> <span data-ttu-id="bc111-155">여기서는 열 유형 및 사용법을 더 쉽게 이해할 수 있도록 마이닝 구조의 정의를 포함했습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-155">Here, the definition of the mining structure is included to make it easier to understand the column type and usage.</span></span>  
  
###  <a name="example-1-typical-case-level-filtering"></a><a name="bkmk_Ex1"></a> <span data-ttu-id="bc111-156">예 1: 일반적인 사례 수준 필터링</span><span class="sxs-lookup"><span data-stu-id="bc111-156">Example 1: Typical Case-Level Filtering</span></span>  
 <span data-ttu-id="bc111-157">이 예에서는 직업이 건축가이고 나이가 31세 이상인 고객으로 모델에 사용되는 사례를 제한하는 간단한 필터를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-157">This example shows a simple filter that restricts the cases used in the model to customers whose occupation is architect and whose age is over 30.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_1  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT  
)  
WITH FILTER (Age > 30 AND Occupation='Architect')  
```  
  

  
###  <a name="example-2-case-level-filtering-using-nested-table-attributes"></a><a name="bkmk_Ex2"></a> <span data-ttu-id="bc111-158">예 2: 중첩 테이블 특성을 사용한 사례 수준 필터링</span><span class="sxs-lookup"><span data-stu-id="bc111-158">Example 2: Case-Level Filtering using Nested Table Attributes</span></span>  
 <span data-ttu-id="bc111-159">마이닝 구조에 중첩 테이블이 포함되어 있는 경우 중첩 테이블에서 값의 존재 여부를 필터링하거나 특정 값이 포함된 중첩 테이블 행을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-159">If your mining structure contains nested tables, you can either filter on the existence of a value in a nested table, or filter on nested table rows that contain a specific value.</span></span> <span data-ttu-id="bc111-160">이 예에서는 우유를 포함한 제품을 한 번 이상 구매한 31세 이상의 고객으로 모델에 사용되는 사례를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-160">This example restricts the cases used for the model to customers over the age of 30 who made at least one purchase that included milk.</span></span>  
  
 <span data-ttu-id="bc111-161">이 예에서 볼 수 있듯이 모델에 포함된 열만 필터에 사용할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-161">As this example shows, it is not necessary that the filter use only columns that are included in the model.</span></span> <span data-ttu-id="bc111-162">중첩 테이블 **Products** 는 마이닝 구조의 일부이지만 마이닝 모델에는 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-162">The nested table **Products** is part of the mining structure, but is not included in the mining model.</span></span> <span data-ttu-id="bc111-163">그럼에도 불구하고 중첩 테이블의 값 및 특성을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-163">However, you can still filter on values and attributes in the nested table.</span></span> <span data-ttu-id="bc111-164">이러한 사례에 대한 세부 정보를 보려면 드릴스루를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-164">To view the details of these cases, drillthrough must be enabled.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_2  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT  
)  
WITH DRILLTHROUGH,   
FILTER (Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk')  
)  
```  
  
 
  
###  <a name="example-3-case-level-filtering-on-multiple-nested-table-attributes"></a><a name="bkmk_Ex3"></a> <span data-ttu-id="bc111-165">예 3: 여러 중첩 테이블 특성을 사용한 사례 수준 필터링</span><span class="sxs-lookup"><span data-stu-id="bc111-165">Example 3: Case-Level Filtering on Multiple Nested Table Attributes</span></span>  
 <span data-ttu-id="bc111-166">이 예에서는 사례 테이블에 적용되는 조건, 중첩 테이블의 특성에 적용되는 조건 및 중첩 테이블 열 중 하나의 특정 값에 적용되는 조건이라는 세 부분으로 이루어진 필터를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-166">This example shows a three-part filter: a condition applies to the case table, another condition to an attribute in the nested table, and another condition on a specific value in one of the nested table columns.</span></span>  
  
 <span data-ttu-id="bc111-167">필터의 첫 번째 조건인 `Age > 30`은 사례 테이블의 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-167">The first condition in the filter, `Age > 30`, applies to a column in the case table.</span></span> <span data-ttu-id="bc111-168">나머지 조건은 중첩 테이블에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-168">The remaining conditions apply to the nested table.</span></span>  
  
 <span data-ttu-id="bc111-169">두 번째 조건인 `EXISTS (SELECT * FROM Products WHERE ProductName='Milk'`는 중첩 테이블에 우유를 포함한 한 번 이상의 구매가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-169">The second condition, `EXISTS (SELECT * FROM Products WHERE ProductName='Milk'`, checks for the presence of at least one purchase in the nested table that included milk.</span></span> <span data-ttu-id="bc111-170">세 번째 조건인 `Quantity>=2`는 고객이 한 번의 거래 과정에서 두 팩 이상의 우유를 구매했음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-170">The third condition, `Quantity>=2`, means that the customer must have purchased at least two units of milk in a single transaction.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_3  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
)  
)  
FILTER (Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk'  AND Quantity >= 2)   
)  
```  
  

  
###  <a name="example-4-case-level-filtering-on-absence-of-nested-table-attributes"></a><a name="bkmk_Ex4"></a> <span data-ttu-id="bc111-171">예 4: 중첩 테이블 특성의 부재를 사용한 사례 수준 필터링</span><span class="sxs-lookup"><span data-stu-id="bc111-171">Example 4: Case-Level Filtering On Absence of Nested Table Attributes</span></span>  
 <span data-ttu-id="bc111-172">이 예에서는 중첩 테이블에서 특성의 부재를 필터링하여 특정 제품을 구매하지 않은 고객으로 사례를 제한하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-172">This example shows how to limit cases to customer who did not purchase a specific item, by filtering on the absence of an attribute in the nested table.</span></span> <span data-ttu-id="bc111-173">이 예에서는 우유를 구입한 적이 없는 31세 이상의 고객을 사용하여 모델을 학습합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-173">In this example, the model is trained using customers over the age of 30 who have never bought milk.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_4  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName  
)  
)  
FILTER (Age > 30 AND NOT EXISTS (SELECT * FROM Products WHERE ProductName='Milk') )  
```  
  

  
###  <a name="example-5-filtering-on-multiple-nested-table-values"></a><a name="bkmk_Ex5"></a> <span data-ttu-id="bc111-174">예 5: 여러 중첩 테이블 값을 사용한 필터링</span><span class="sxs-lookup"><span data-stu-id="bc111-174">Example 5: Filtering on Multiple Nested Table Values</span></span>  
 <span data-ttu-id="bc111-175">이 예는 중첩 테이블 필터링을 보여 주기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-175">The purpose of the example is to show nested table filtering.</span></span> <span data-ttu-id="bc111-176">중첩 테이블 필터는 사례 필터 다음에 적용되며 중첩 테이블 행만 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-176">The nested table filter is applied after the case filter, and only restricts nested table rows.</span></span>  
  
 <span data-ttu-id="bc111-177">이 모델에서는 EXISTS를 지정하지 않았으므로 빈 중첩 테이블이 있는 여러 사례가 모델에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-177">This model could contain multiple cases with empty nested tables because EXISTS is not specified.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_5  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
) WITH FILTER(ProductName='Milk' OR ProductName='bottled water')  
)  
WITH DRILLTHROUGH  
```  
  

  
###  <a name="example-6-filtering-on-nested-table-attributes-and-exists"></a><a name="bkmk_Ex6"></a> <span data-ttu-id="bc111-178">예 6: 중첩 테이블 특성 및 EXISTS를 사용한 필터링</span><span class="sxs-lookup"><span data-stu-id="bc111-178">Example 6: Filtering on Nested Table Attributes and EXISTS</span></span>  
 <span data-ttu-id="bc111-179">이 예에서 중첩 테이블에 대한 필터는 우유 또는 생수를 포함하는 항목으로만 행을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-179">In this example, the filter on the nested table restricts the rows to those that contain either milk or bottled water.</span></span> <span data-ttu-id="bc111-180">그런 다음 `EXISTS` 문을 사용하여 모델의 사례를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-180">Then, the cases in the model are restricted by using an `EXISTS` statement.</span></span> <span data-ttu-id="bc111-181">이렇게 하면 중첩 테이블이 비어 있지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-181">This makes sure that the nested table is not empty.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_6  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
) WITH FILTER(ProductName='Milk' OR ProductName='bottled water')  
)  
FILTER (EXISTS (Products))  
```  
  

  
###  <a name="example-7-complex-filter-combinations"></a><a name="bkmk_Ex7"></a> <span data-ttu-id="bc111-182">예 7: 복잡한 필터 조합</span><span class="sxs-lookup"><span data-stu-id="bc111-182">Example 7: Complex Filter Combinations</span></span>  
 <span data-ttu-id="bc111-183">이 모델의 시나리오는 예 4의 시나리오와 비슷하지만 훨씬 더 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-183">The scenario for this model resembles that of Example 4, but is far more complex.</span></span> <span data-ttu-id="bc111-184">중첩 테이블 **ProductsOnSale**에는 필터 조건이 있습니다 .이는 `(OnSale)` **Onsale** 의 값이 `true` **ProductName**에 나열 된 제품에 대 한 값 이어야 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-184">The nested table, **ProductsOnSale**, has the filter condition `(OnSale)` meaning that the value of **OnSale** must be `true` for the product listed in **ProductName**.</span></span> <span data-ttu-id="bc111-185">여기서 **OnSale** 은 구조 열입니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-185">Here, **OnSale** is a structure column.</span></span>  
  
 <span data-ttu-id="bc111-186">**ProductsNotOnSale**에 대 한 필터의 두 번째 부분은이 구문을 반복 하지만 **onsale** 의 값이 인 제품에 대 한 필터입니다 `not true``(!OnSale)` .</span><span class="sxs-lookup"><span data-stu-id="bc111-186">The second part of the filter, for **ProductsNotOnSale**, repeats this syntax, but filters on products for which the value of **OnSale** is `not true``(!OnSale)`.</span></span>  
  
 <span data-ttu-id="bc111-187">마지막으로 조건을 조합하고 하나의 추가 제한 사항을 사례 테이블에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-187">Finally, the conditions are combined and one additional restriction is added to the case table.</span></span> <span data-ttu-id="bc111-188">그 결과 26세 이상의 모든 고객에 대해 **ProductsNotOnSale** 목록에 포함된 사례를 기반으로 **ProductsOnSale** 목록의 제품 구매를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-188">The result is to predict purchases of products in the **ProductsNotOnSale** list, based on the cases that are included in the **ProductsOnSale** list, for all customers over the age of 25.</span></span>  
  
 `ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_7`  
  
 `(`  
  
 `CustomerId,`  
  
 `Age,`  
  
 `Occupation,`  
  
 `MaritalStatus,`  
  
 `ProductsOnSale`  
  
 `(`  
  
 `ProductName KEY`  
  
 `) WITH FILTER(OnSale),`  
  
 `ProductsNotOnSale PREDICT ONLY`  
  
 `(`  
  
 `ProductName KEY`  
  
 `) WITH FILTER(!OnSale)`  
  
 `)`  
  
 `WITH DRILLTHROUGH,`  
  
 `FILTER (EXISTS (ProductsOnSale) AND EXISTS(ProductsNotOnSale) AND Age > 25)`  
  
  
  
###  <a name="example-8-filtering-on-dates"></a><a name="bkmk_Ex8"></a> <span data-ttu-id="bc111-189">예 8: 날짜로 필터링</span><span class="sxs-lookup"><span data-stu-id="bc111-189">Example 8: Filtering on Dates</span></span>  
 <span data-ttu-id="bc111-190">다른 데이터와 마찬가지로 날짜로 입력 열을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-190">You can filter input columns on dates, as you would any other data.</span></span> <span data-ttu-id="bc111-191">날짜/시간 형식의 열에 포함된 날짜는 연속 값입니다. 따라서 보다 큼(>) 또는 보다 작음(<)과 같은 연산자를 사용하여 날짜 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-191">Dates contained in a column of type date/time are continuous values; therefore, you can specify a date range by using operators such as greater than (>) or less than (<).</span></span> <span data-ttu-id="bc111-192">데이터 원본에서 날짜를 연속 데이터 형식이 아니라 불연속 또는 텍스트 값으로 나타낼 경우 날짜 범위를 필터링할 수 없고 개별 불연속 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-192">If your data source does not represent dates by a Continuous data type, but as discrete or text values, you cannot filter on a date range, but must specify individual discrete values.</span></span>  
  
 <span data-ttu-id="bc111-193">그러나 필터에 사용된 날짜 열이 또한 모델의 키 열인 경우 시계열 모델에서 날짜 열에 대한 필터를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-193">However, you cannot create a filter on the date column in a time series model if the date column used for the filter is also the key column for the model.</span></span> <span data-ttu-id="bc111-194">이는 시계열 모델 및 시퀀스 클러스터링 모델에서 날짜 열은 `KeyTime` 또는 `KeySequence` 형식으로 처리될 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-194">That is because, in time series models and sequence clustering models, the date column might be handled as type `KeyTime` or `KeySequence`.</span></span>  
  
 <span data-ttu-id="bc111-195">시계열 모델에서 연속 날짜를 필터링해야 하는 경우 마이닝 구조에서 열의 복사본을 만들고 새 열에서 모델을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-195">If you need to filter on continuous dates in a time series model, you can create a copy of the column in the mining structure, and filter the model on the new column.</span></span>  
  
 <span data-ttu-id="bc111-196">예를 들어 다음 식은 예측 모델에 추가된 `Continuous` 형식의 날짜 열에 대한 필터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-196">For example, the following expression represents a filter on a date column of type `Continuous` that has been added to the Forecasting model.</span></span>  
  
 `=[DateCopy] > '12:31:2003:00:00:00'`  
  
> [!NOTE]  
>  <span data-ttu-id="bc111-197">모델에 추가하는 모든 추가 열은 결과에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-197">Note that any extra columns that you add to the model might affect the results.</span></span> <span data-ttu-id="bc111-198">따라서 계열의 계산에 열을 사용하지 않으려면 열을 모델이 아니라 마이닝 구조에만 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-198">Therefore, if you do not want the column to be used in computation of the series, you should add the column only to the mining structure, and not to the model.</span></span> <span data-ttu-id="bc111-199">열에서 모델 플래그를 `PredictOnly` 또는 `Ignore`로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-199">You can also set the model flag on the column to `PredictOnly` or to `Ignore`.</span></span> <span data-ttu-id="bc111-200">자세한 내용은 [모델링 플래그&#40;데이터 마이닝&#41;](modeling-flags-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bc111-200">For more information, see [Modeling Flags &#40;Data Mining&#41;](modeling-flags-data-mining.md).</span></span>  
  
 <span data-ttu-id="bc111-201">다른 모델 유형의 경우 다른 열과 마찬가지로 입력 조건이나 필터 조건으로 날짜를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-201">For other model types, you can use dates as input criteria or filter criteria just like you would in any other column.</span></span> <span data-ttu-id="bc111-202">그러나 `Continuous` 데이터 형식에서 지원하지 않은 특정 수준의 세분성이 필요한 경우 필터링 및 분석에 사용할 단위를 추출하는 식을 사용하여 데이터 원본에서 파생 값을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-202">However, if you need to use a specific level of granularity that is not supported by a `Continuous` data type, you can create a derived value in the data source by using expressions to extract the unit to use in filtering and analysis.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="bc111-203">필터 조건으로 날짜를 지정하는 경우에는 현재 운영 체제의 날짜 형식에 관계없이 다음 형식을 사용해야 합니다. `mm/dd/yyyy`</span><span class="sxs-lookup"><span data-stu-id="bc111-203">When you specify a dates as filter criteria, you must use the following format, regardless of the date format for the current OS: `mm/dd/yyyy`.</span></span> <span data-ttu-id="bc111-204">다른 형식을 사용하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-204">Any other format results in an error.</span></span>  
  
 <span data-ttu-id="bc111-205">예를 들어 콜 센터 결과를 필터링하여 주말만 표시하려면 각 날짜의 평일 이름을 추출한 다음 해당 평일 이름 값을 입력에 사용하거나 필터링에서 불연속 값으로 사용하는 식을 데이터 원본 뷰에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-205">For example, if you want to filter your call center results to show only weekends, you can create an expression in the data source view that extracts the weekday name for each date, and then use that weekday name value for input or as a discrete value in filtering.</span></span> <span data-ttu-id="bc111-206">반복 값은 모델에 영향을 줄 수 있으므로 파생 값과 함께 날짜 열을 사용하는 대신에 열 중에서 하나만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc111-206">Just remember that repeating values can affect the model, so you should use only one of the columns, not the date column plus the derived value.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="bc111-207">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc111-207">See Also</span></span>  
 <span data-ttu-id="bc111-208">[마이닝 모델 &#40;Analysis Services 데이터 마이닝&#41;필터](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="bc111-208">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="bc111-209">테스트 및 유효성 검사&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="bc111-209">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  
