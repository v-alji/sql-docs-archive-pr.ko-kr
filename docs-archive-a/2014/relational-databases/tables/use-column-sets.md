---
title: 열 집합 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- sparse columns, column sets
- column sets
ms.assetid: a4f9de95-dc8f-4ad8-b957-137e32bfa500
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9cb496137c3986b78a55862e434c153d354a42ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660975"
---
# <a name="use-column-sets"></a><span data-ttu-id="f3741-102">열 집합 사용</span><span class="sxs-lookup"><span data-stu-id="f3741-102">Use Column Sets</span></span>
  <span data-ttu-id="f3741-103">스파스 열을 사용하는 테이블에서는 테이블의 모든 스파스 열을 반환하는 열 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-103">Tables that use sparse columns can designate a column set to return all sparse columns in the table.</span></span> <span data-ttu-id="f3741-104">열 집합은 구조화된 출력으로 테이블의 모든 스파스 열을 결합하는 형식화되지 않은 XML 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-104">A column set is an untyped XML representation that combines all the sparse columns of a table into a structured output.</span></span> <span data-ttu-id="f3741-105">열 집합은 열 집합이 테이블에 물리적으로 저장되지 않는다는 점에서 계산 열과 유사하며,</span><span class="sxs-lookup"><span data-stu-id="f3741-105">A column set is like a calculated column in that the column set is not physically stored in the table.</span></span> <span data-ttu-id="f3741-106">직접 업데이트할 수 있다는 점에서 계산 열과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-106">A column set differs from a calculated column in that the column set is directly updatable.</span></span>  
  
 <span data-ttu-id="f3741-107">테이블의 열 수가 많고 이러한 열을 개별적으로 작업하는 것이 복잡한 경우 열 집합을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-107">You should consider using column sets when the number of columns in a table is large, and operating on them individually is cumbersome.</span></span> <span data-ttu-id="f3741-108">애플리케이션에서 열이 많은 테이블의 열 집합을 사용하여 데이터를 선택하고 삽입하는 경우 성능이 약간 향상될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-108">Applications might see some performance improvement when they select and insert data by using column sets on tables that have lots of columns.</span></span> <span data-ttu-id="f3741-109">그러나 테이블의 열에 많은 인덱스가 정의되어 있는 경우 열 집합의 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-109">However, the performance of column sets can be reduced when many indexes are defined on the columns in the table.</span></span> <span data-ttu-id="f3741-110">왜냐하면 실행 계획에 필요한 메모리 양이 늘어나기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-110">This is because the amount of memory that is required for an execution plan increases.</span></span>  
  
 <span data-ttu-id="f3741-111">열 집합을 정의하려면 [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) 또는 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 문에 *<column_set_name>* FOR ALL_SPARSE_COLUMNS 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-111">To define a column set, use the *<column_set_name>* FOR ALL_SPARSE_COLUMNS keywords in the[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) or [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) statements.</span></span>  
  
## <a name="guidelines-for-using-column-sets"></a><span data-ttu-id="f3741-112">열 집합 사용 지침</span><span class="sxs-lookup"><span data-stu-id="f3741-112">Guidelines for Using Column Sets</span></span>  
 <span data-ttu-id="f3741-113">열 집합을 사용하는 경우 다음 지침을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-113">When you use column sets, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="f3741-114">스파스 열 및 열 집합을 동일한 문의 일부로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-114">Sparse columns and a column set can be added as part of the same statement.</span></span>  
  
-   <span data-ttu-id="f3741-115">열 집합은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-115">The column set cannot be changed.</span></span> <span data-ttu-id="f3741-116">열 집합을 변경하려면 열 집합을 삭제한 다음 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-116">To change a column set, you must delete and re-create the column set.</span></span>  
  
-   <span data-ttu-id="f3741-117">테이블에 스파스 열이 이미 포함되어 있는 경우 해당 테이블에 열 집합을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-117">A column set cannot be added to a table if that table already contains sparse columns.</span></span>  
  
-   <span data-ttu-id="f3741-118">스파스 열을 포함하지 않는 테이블에 열 집합을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-118">A column set can be added to a table that does not include any sparse columns.</span></span> <span data-ttu-id="f3741-119">스파스 열이 나중에 테이블에 추가되면 열 집합에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-119">If sparse columns are later added to the table, they will appear in the column set.</span></span>  
  
-   <span data-ttu-id="f3741-120">테이블당 열 집합 하나만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-120">Only one column set is allowed per table.</span></span>  
  
-   <span data-ttu-id="f3741-121">열 집합은 선택 사항이며 스파스 열을 사용하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-121">A column set is optional and is not required to use sparse columns.</span></span>  
  
-   <span data-ttu-id="f3741-122">열 집합에 제약 조건 또는 기본값을 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-122">Constraints or default values cannot be defined on a column set.</span></span>  
  
-   <span data-ttu-id="f3741-123">계산 열은 열 집합 열을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-123">Computed columns cannot contain column set columns.</span></span>  
  
-   <span data-ttu-id="f3741-124">열 집합을 포함하는 테이블에서는 분산 쿼리가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-124">Distributed queries are not supported on tables that contain column sets.</span></span>  
  
-   <span data-ttu-id="f3741-125">복제는 열 집합을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-125">Replication does not support column sets.</span></span>  
  
-   <span data-ttu-id="f3741-126">변경 데이터 캡처에서 열 집합을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-126">Change data capture does not support column sets.</span></span>  
  
-   <span data-ttu-id="f3741-127">열 집합은 어떠한 인덱스 종류의 일부도 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-127">A column set cannot be part of any kind of index.</span></span> <span data-ttu-id="f3741-128">여기에는 XML 인덱스, 전체 텍스트 인덱스 및 인덱싱된 뷰가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-128">This includes XML indexes, full-text indexes, and indexed views.</span></span> <span data-ttu-id="f3741-129">열 집합은 인덱스의 포괄 열로 추가될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-129">A column set cannot be added as an included column in any index.</span></span>  
  
-   <span data-ttu-id="f3741-130">열 집합은 필터링된 인덱스 또는 필터링된 통계의 필터 식에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-130">A column set cannot be used in the filter expression of a filtered index or filtered statistics.</span></span>  
  
-   <span data-ttu-id="f3741-131">뷰에 열 집합이 포함되어 있으면 열 집합이 뷰에서 XML 열로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-131">When a view includes a column set, the column set appears in the view as an XML column.</span></span>  
  
-   <span data-ttu-id="f3741-132">열 집합은 인덱싱된 뷰 정의에 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-132">A column set cannot be included in an indexed view definition.</span></span>  
  
-   <span data-ttu-id="f3741-133">열 집합을 포함하는 테이블이 있는 분할 뷰가 이름별로 스파스 열을 지정하면 해당 분할 뷰를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-133">Partitioned views that include tables that contain column sets are updatable when the partitioned view specifies the sparse columns by name.</span></span> <span data-ttu-id="f3741-134">분할 뷰가 열 집합을 참조하면 해당 분할 뷰를 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-134">A partitioned view is not updatable when it references the column set.</span></span>  
  
-   <span data-ttu-id="f3741-135">열 집합을 참조하는 쿼리 알림은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-135">Query notifications that refer to column sets are not permitted.</span></span>  
  
-   <span data-ttu-id="f3741-136">XML 데이터의 크기 제한이 2GB입니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-136">XML data has a size limit of 2 GB.</span></span> <span data-ttu-id="f3741-137">행에서 Null이 아닌 모든 스파스 열의 결합된 데이터가 이 제한을 초과하면 쿼리 또는 DML 작업에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-137">If the combined data of all the nonnull sparse columns in a row exceeds this limit, the query or DML operation will produce an error.</span></span>  
  
-   <span data-ttu-id="f3741-138">COLUMNS_UPDATED 함수에서 반환되는 데이터에 대한 자세한 내용은 [스파스 열 사용](use-sparse-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3741-138">For information about the data that is returned by the COLUMNS_UPDATED function, see [Use Sparse Columns](use-sparse-columns.md).</span></span>  
  
## <a name="guidelines-for-selecting-data-from-a-column-set"></a><span data-ttu-id="f3741-139">열 집합 데이터 선택 지침</span><span class="sxs-lookup"><span data-stu-id="f3741-139">Guidelines for Selecting Data from a Column Set</span></span>  
 <span data-ttu-id="f3741-140">열 집합에서 데이터를 선택하는 경우 다음 지침을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-140">Consider the following guidelines for selecting data from a column set:</span></span>  
  
-   <span data-ttu-id="f3741-141">이론적으로 열 집합은 기본 관계형 열 집합을 단일 XML 표현으로 집계하는 업데이트 가능 XML 계산 열 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-141">Conceptually, a column set is a type of updatable, computed XML column that aggregates a set of underlying relational columns into a single XML representation.</span></span> <span data-ttu-id="f3741-142">열 집합은 ALL_SPARSE_COLUMNS 속성만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-142">The column set only supports the ALL_SPARSE_COLUMNS property.</span></span> <span data-ttu-id="f3741-143">이 속성은 특정 행에 대해 모든 스파스 열의 Null이 아닌 값을 모두 집계하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-143">This property is used to aggregate all nonnull values from all sparse columns for a particular row.</span></span>  
  
-   <span data-ttu-id="f3741-144">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 테이블 편집기에서 열 집합은 편집할 수 있는 XML 필드로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-144">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] table editor, column sets are displayed as an editable XML field.</span></span> <span data-ttu-id="f3741-145">열 집합을 다음 형식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-145">Define column sets in the format:</span></span>  
  
    ```  
    <column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...  
    ```  
  
     <span data-ttu-id="f3741-146">열 집합 값의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-146">Examples of column set values are as follows:</span></span>  
  
    -   `<sparseProp1>10</sparseProp1><sparseProp3>20</sparseProp3>`  
  
    -   `<DocTitle>Bicycle Parts List</DocTitle><Region>West</Region>`  
  
-   <span data-ttu-id="f3741-147">Null 값을 포함하는 스파스 열은 열 집합에 대한 XML 표현에서 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-147">Sparse columns that contain null values are omitted from the XML representation for the column set.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="f3741-148">열 집합을 추가하면 SELECT \* 쿼리 동작이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-148">Adding a column set changes the behavior of SELECT \* queries.</span></span> <span data-ttu-id="f3741-149">쿼리는 열 집합을 XML 열로 반환하며 개별 스파스 열을 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-149">The query will return the column set as an XML column and not return the individual sparse columns.</span></span> <span data-ttu-id="f3741-150">스키마 디자이너 및 소프트웨어 개발자는 기존 애플리케이션에서 오류가 발생하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-150">Schema designers and software developers must be careful not to break existing applications.</span></span>  
  
## <a name="inserting-or-modifying-data-in-a-column-set"></a><span data-ttu-id="f3741-151">열 집합에서 데이터 삽입 또는 수정</span><span class="sxs-lookup"><span data-stu-id="f3741-151">Inserting or Modifying Data in a Column Set</span></span>  
 <span data-ttu-id="f3741-152">개별 열 이름을 사용하거나 열 집합의 XML 형식을 통해 열 집합의 이름을 참조하고 열 집합의 값을 지정하여 스파스 열의 데이터 조작 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-152">Data manipulation of a sparse column can be performed by using the name of the individual columns, or by referencing the name of the column set and specifying the values of the column set by using the XML format of the column set.</span></span> <span data-ttu-id="f3741-153">스파스 열은 XML 열에서 어떤 순서로도 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-153">Sparse columns can appear in any order in the XML column.</span></span>  
  
 <span data-ttu-id="f3741-154">XML 열 집합을 사용하여 스파스 열 값을 삽입하거나 업데이트하는 경우 기본 스파스 열에 삽입된 값은 `xml` 데이터 형식에서 암시적으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-154">When sparse column values are inserted or updated by using the XML column set, the values that are inserted into the underlying sparse columns are implicitly converted from the `xml` data type.</span></span> <span data-ttu-id="f3741-155">숫자 열의 경우 XML 숫자 열에 있는 빈 값이 빈 문자열로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-155">In the case of numeric columns, a blank value in the XML for the numeric column converts to an empty string.</span></span> <span data-ttu-id="f3741-156">이로 인해 다음 예에서처럼 0이 숫자 열에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-156">This causes a zero to be inserted into the numeric column as shown in the following example.</span></span>  
  
```  
CREATE TABLE t (i int SPARSE, cs xml column_set FOR ALL_SPARSE_COLUMNS);  
GO  
INSERT t(cs) VALUES ('<i/>');  
GO  
SELECT i FROM t;  
GO  
```  
  
 <span data-ttu-id="f3741-157">이 예에서는 열 `i`에 값이 지정되지 않았지만 값 `0` 이 삽입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-157">In this example, no value was specified for the column `i`, but the value `0` was inserted.</span></span>  
  
## <a name="using-the-sql_variant-data-type"></a><span data-ttu-id="f3741-158">sql_variant 데이터 형식 사용</span><span class="sxs-lookup"><span data-stu-id="f3741-158">Using the sql_variant Data Type</span></span>  
 <span data-ttu-id="f3741-159">`sql_variant` 데이터 형식은 `int`, `char` 및 `date`와 같은 여러 다른 데이터 형식을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-159">The `sql_variant` date type can store multiple different data types, such as `int`, `char`, and `date`.</span></span> <span data-ttu-id="f3741-160">열 집합은 `sql_variant` 값에 연결된 소수 자릿수, 전체 자릿수 및 로캘 정보와 같은 데이터 형식 정보를 생성된 XML 열에서 특성으로 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-160">Column sets output the data type information such as scale, precision, and locale information that is associated with a `sql_variant` value as attributes in the generated XML column.</span></span> <span data-ttu-id="f3741-161">사용자 지정하여 생성된 XML 문에 있는 이러한 특성을 열 집합의 삽입 또는 업데이트 작업에 대한 입력으로 제공하려는 경우에는 이 특성 중 일부가 필요하여 이러한 일부 특성에 기본값이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-161">If you try to provide these attributes in a custom-generated XML statement as an input for an insert or update operation on a column set, some of these attributes are required and some of them are assigned a default value.</span></span> <span data-ttu-id="f3741-162">다음 표에서는 데이터 형식과 값이 제공되지 않은 경우 서버에서 생성하는 기본값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-162">The following table lists the data types and the default values that the server generates when the value is not provided.</span></span>  
  
|<span data-ttu-id="f3741-163">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="f3741-163">Data type</span></span>|<span data-ttu-id="f3741-164">localeID\*</span><span class="sxs-lookup"><span data-stu-id="f3741-164">localeID\*</span></span>|<span data-ttu-id="f3741-165">sqlCompareOptions</span><span class="sxs-lookup"><span data-stu-id="f3741-165">sqlCompareOptions</span></span>|<span data-ttu-id="f3741-166">sqlCollationVersion</span><span class="sxs-lookup"><span data-stu-id="f3741-166">sqlCollationVersion</span></span>|<span data-ttu-id="f3741-167">SqlSortId</span><span class="sxs-lookup"><span data-stu-id="f3741-167">SqlSortId</span></span>|<span data-ttu-id="f3741-168">최대 길이</span><span class="sxs-lookup"><span data-stu-id="f3741-168">Maximum length</span></span>|<span data-ttu-id="f3741-169">자릿수</span><span class="sxs-lookup"><span data-stu-id="f3741-169">Precision</span></span>|<span data-ttu-id="f3741-170">확장</span><span class="sxs-lookup"><span data-stu-id="f3741-170">Scale</span></span>|  
|---------------|----------------|-----------------------|-------------------------|---------------|--------------------|---------------|-----------|  
|<span data-ttu-id="f3741-171">`char`, `varchar`, `binary`</span><span class="sxs-lookup"><span data-stu-id="f3741-171">`char`, `varchar`, `binary`</span></span>|<span data-ttu-id="f3741-172">-1</span><span class="sxs-lookup"><span data-stu-id="f3741-172">-1</span></span>|<span data-ttu-id="f3741-173">'기본값'</span><span class="sxs-lookup"><span data-stu-id="f3741-173">'Default'</span></span>|<span data-ttu-id="f3741-174">0</span><span class="sxs-lookup"><span data-stu-id="f3741-174">0</span></span>|<span data-ttu-id="f3741-175">0</span><span class="sxs-lookup"><span data-stu-id="f3741-175">0</span></span>|<span data-ttu-id="f3741-176">8000</span><span class="sxs-lookup"><span data-stu-id="f3741-176">8000</span></span>|<span data-ttu-id="f3741-177">해당 사항 없음\*\*</span><span class="sxs-lookup"><span data-stu-id="f3741-177">Not applicable\*\*</span></span>|<span data-ttu-id="f3741-178">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-178">Not applicable</span></span>|  
|`nvarchar`|<span data-ttu-id="f3741-179">-1</span><span class="sxs-lookup"><span data-stu-id="f3741-179">-1</span></span>|<span data-ttu-id="f3741-180">'기본값'</span><span class="sxs-lookup"><span data-stu-id="f3741-180">'Default'</span></span>|<span data-ttu-id="f3741-181">0</span><span class="sxs-lookup"><span data-stu-id="f3741-181">0</span></span>|<span data-ttu-id="f3741-182">0</span><span class="sxs-lookup"><span data-stu-id="f3741-182">0</span></span>|<span data-ttu-id="f3741-183">4000</span><span class="sxs-lookup"><span data-stu-id="f3741-183">4000</span></span>|<span data-ttu-id="f3741-184">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-184">Not applicable</span></span>|<span data-ttu-id="f3741-185">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-185">Not applicable</span></span>|  
|<span data-ttu-id="f3741-186">`decimal`, `float`, `real`</span><span class="sxs-lookup"><span data-stu-id="f3741-186">`decimal`, `float`, `real`</span></span>|<span data-ttu-id="f3741-187">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-187">Not applicable</span></span>|<span data-ttu-id="f3741-188">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-188">Not applicable</span></span>|<span data-ttu-id="f3741-189">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-189">Not applicable</span></span>|<span data-ttu-id="f3741-190">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-190">Not applicable</span></span>|<span data-ttu-id="f3741-191">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-191">Not applicable</span></span>|<span data-ttu-id="f3741-192">18</span><span class="sxs-lookup"><span data-stu-id="f3741-192">18</span></span>|<span data-ttu-id="f3741-193">0</span><span class="sxs-lookup"><span data-stu-id="f3741-193">0</span></span>|  
|<span data-ttu-id="f3741-194">`integer`, `bigint`, `tinyint`, `smallint`</span><span class="sxs-lookup"><span data-stu-id="f3741-194">`integer`, `bigint`, `tinyint`, `smallint`</span></span>|<span data-ttu-id="f3741-195">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-195">Not applicable</span></span>|<span data-ttu-id="f3741-196">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-196">Not applicable</span></span>|<span data-ttu-id="f3741-197">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-197">Not applicable</span></span>|<span data-ttu-id="f3741-198">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-198">Not applicable</span></span>|<span data-ttu-id="f3741-199">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-199">Not applicable</span></span>|<span data-ttu-id="f3741-200">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-200">Not applicable</span></span>|<span data-ttu-id="f3741-201">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-201">Not applicable</span></span>|  
|`datetime2`|<span data-ttu-id="f3741-202">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-202">Not applicable</span></span>|<span data-ttu-id="f3741-203">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-203">Not applicable</span></span>|<span data-ttu-id="f3741-204">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-204">Not applicable</span></span>|<span data-ttu-id="f3741-205">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-205">Not applicable</span></span>|<span data-ttu-id="f3741-206">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-206">Not applicable</span></span>|<span data-ttu-id="f3741-207">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-207">Not applicable</span></span>|<span data-ttu-id="f3741-208">7</span><span class="sxs-lookup"><span data-stu-id="f3741-208">7</span></span>|  
|`datetime offset`|<span data-ttu-id="f3741-209">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-209">Not applicable</span></span>|<span data-ttu-id="f3741-210">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-210">Not applicable</span></span>|<span data-ttu-id="f3741-211">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-211">Not applicable</span></span>|<span data-ttu-id="f3741-212">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-212">Not applicable</span></span>|<span data-ttu-id="f3741-213">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-213">Not applicable</span></span>|<span data-ttu-id="f3741-214">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-214">Not applicable</span></span>|<span data-ttu-id="f3741-215">7</span><span class="sxs-lookup"><span data-stu-id="f3741-215">7</span></span>|  
|<span data-ttu-id="f3741-216">`datetime`, `date`, `smalldatetime`</span><span class="sxs-lookup"><span data-stu-id="f3741-216">`datetime`, `date`, `smalldatetime`</span></span>|<span data-ttu-id="f3741-217">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-217">Not applicable</span></span>|<span data-ttu-id="f3741-218">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-218">Not applicable</span></span>|<span data-ttu-id="f3741-219">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-219">Not applicable</span></span>|<span data-ttu-id="f3741-220">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-220">Not applicable</span></span>|<span data-ttu-id="f3741-221">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-221">Not applicable</span></span>|<span data-ttu-id="f3741-222">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-222">Not applicable</span></span>|<span data-ttu-id="f3741-223">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-223">Not applicable</span></span>|  
|<span data-ttu-id="f3741-224">`money`, `smallmoney`</span><span class="sxs-lookup"><span data-stu-id="f3741-224">`money`, `smallmoney`</span></span>|<span data-ttu-id="f3741-225">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-225">Not applicable</span></span>|<span data-ttu-id="f3741-226">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-226">Not applicable</span></span>|<span data-ttu-id="f3741-227">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-227">Not applicable</span></span>|<span data-ttu-id="f3741-228">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-228">Not applicable</span></span>|<span data-ttu-id="f3741-229">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-229">Not applicable</span></span>|<span data-ttu-id="f3741-230">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-230">Not applicable</span></span>|<span data-ttu-id="f3741-231">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-231">Not applicable</span></span>|  
|`time`|<span data-ttu-id="f3741-232">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-232">Not applicable</span></span>|<span data-ttu-id="f3741-233">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-233">Not applicable</span></span>|<span data-ttu-id="f3741-234">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-234">Not applicable</span></span>|<span data-ttu-id="f3741-235">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-235">Not applicable</span></span>|<span data-ttu-id="f3741-236">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-236">Not applicable</span></span>|<span data-ttu-id="f3741-237">해당 없음</span><span class="sxs-lookup"><span data-stu-id="f3741-237">Not applicable</span></span>|<span data-ttu-id="f3741-238">7</span><span class="sxs-lookup"><span data-stu-id="f3741-238">7</span></span>|  
  
 <span data-ttu-id="f3741-239">\*  localeID -1은 기본 로캘을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-239">\*  localeID -1 means the default locale.</span></span> <span data-ttu-id="f3741-240">영어 로캘은 1033입니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-240">The English locale is 1033.</span></span>  
  
 <span data-ttu-id="f3741-241">\*\*  해당 사항 없음 = 열 집합에서 선택 작업을 수행하는 동안 이 특성에 대해 값이 출력되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-241">\*\*  Not applicable = No values are output for these attributes during a select operation on the column set.</span></span> <span data-ttu-id="f3741-242">삽입 또는 업데이트 작업에서 열 집합에 대해 제공된 XML 표현의 호출자에 의해 이 특성에 대한 값이 지정된 경우 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-242">Generates an error when a value is specified for this attribute by the caller in the XML representation provided for a column set in an insert or update operation.</span></span>  
  
## <a name="security"></a><span data-ttu-id="f3741-243">보안</span><span class="sxs-lookup"><span data-stu-id="f3741-243">Security</span></span>  
 <span data-ttu-id="f3741-244">열 집합에 대한 보안 모델은 테이블과 열 사이에 존재하는 보안 모델과 유사하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-244">The security model for a column set works similar to the security model that exists between table and columns.</span></span> <span data-ttu-id="f3741-245">열 집합은 미니 테이블로 시각화할 수 있으며 선택 작업은 이 미니 테이블에 대한 SELECT \* 작업과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-245">Column sets can be visualized as a minitable and a select operation is like a SELECT \* operation on this minitable.</span></span> <span data-ttu-id="f3741-246">그러나 스파스 열에 대한 열 집합 간 관계는 엄격히 말해 컨테이너가 아닌 그룹화 관계입니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-246">But, the relationship between column set to sparse columns is a grouping relationship instead of strictly a container.</span></span> <span data-ttu-id="f3741-247">보안 모델은 열 집합 열의 보안을 검사하고 기본 스파스 열의 DENY 작업을 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-247">The security model checks the security on the column set column, and honors the DENY operations on the underlying sparse columns.</span></span> <span data-ttu-id="f3741-248">보안 모델에는 다음과 같은 추가 특징이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-248">Additional characteristics of the security model are as follows:</span></span>  
  
-   <span data-ttu-id="f3741-249">보안 권한은 테이블에 있는 다른 모든 열과 유사하게 열 집합 열에서 부여되고 취소될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-249">Security permissions can be granted and revoked from the column set column, similar to any other column in the table.</span></span>  
  
-   <span data-ttu-id="f3741-250">열 집합 열에 대한 SELECT, INSERT, UPDATE, DELETE 및 REFERENCES 권한의 GRANT 또는 REVOKE가 해당 집합의 기본 멤버 열로 전파되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-250">A GRANT or REVOKE of SELECT, INSERT, UPDATE, DELETE, and REFERENCES permission on a column set column does not propagate to the underlying member columns of that set.</span></span> <span data-ttu-id="f3741-251">이는 열 집합 열을 사용하는 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-251">It applies only to the usage of the column set column.</span></span> <span data-ttu-id="f3741-252">열 집합에 대한 DENY 권한은 테이블의 기본 스파스 열로 전파되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-252">DENY permission on a column set does propagate to the underlying sparse columns of the table.</span></span>  
  
-   <span data-ttu-id="f3741-253">열 집합 열에 대해 SELECT, INSERT, UPDATE 및 DELETE 문을 실행하려면 사용자가 열 집합 열에 해당하는 권한은 물론 테이블의 모든 스파스 열에 해당하는 권한을 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-253">Executing SELECT, INSERT, UPDATE, and DELETE statements on the column set column require that the user has corresponding permissions on the column set column, and also the corresponding permission on all the sparse columns in the table.</span></span> <span data-ttu-id="f3741-254">열 집합은 테이블의 모든 스파스 열을 나타내므로 사용자가 변경하지 않으려는 스파스 열을 포함한 모든 스파스 열에 대한 권한을 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-254">Because the column set represents all the sparse columns in the table, you must have permission on all the sparse columns, and this includes sparse columns that you might not be changing.</span></span>  
  
-   <span data-ttu-id="f3741-255">스파스 열 또는 열 집합에 대해 REVOKE 문을 실행하면 보안이 기본값인 해당 부모 개체의 보안으로 되돌려집니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-255">Executing a REVOKE statement on a sparse column or column set defaults the security to their parent object.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f3741-256">예</span><span class="sxs-lookup"><span data-stu-id="f3741-256">Examples</span></span>  
 <span data-ttu-id="f3741-257">다음 예의 Document 테이블에는 `DocID` 및 `Title`열의 공통 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-257">In the following examples, a document table contains the common set of columns `DocID` and `Title`.</span></span> <span data-ttu-id="f3741-258">Production 그룹은 모든 생산 문서에 대한 `ProductionSpecification` 및 `ProductionLocation` 열을 원하며,</span><span class="sxs-lookup"><span data-stu-id="f3741-258">The Production group wants a `ProductionSpecification` and `ProductionLocation` column for all production documents.</span></span> <span data-ttu-id="f3741-259">Marketing 그룹은 마케팅 문서에 대한 `MarketingSurveyGroup` 열을 원합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-259">The Marketing group wants a `MarketingSurveyGroup` column for marketing documents.</span></span>  
  
### <a name="a-creating-a-table-that-has-a-column-set"></a><span data-ttu-id="f3741-260">A.</span><span class="sxs-lookup"><span data-stu-id="f3741-260">A.</span></span> <span data-ttu-id="f3741-261">열 집합을 포함하는 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="f3741-261">Creating a table that has a column set</span></span>  
 <span data-ttu-id="f3741-262">다음 예에서는 스파스 열을 사용하고 열 집합 `SpecialPurposeColumns`를 포함하는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-262">The following example creates the table that uses sparse columns and includes the column set `SpecialPurposeColumns`.</span></span> <span data-ttu-id="f3741-263">이 예에서는 테이블에 두 개의 행을 삽입한 다음 테이블에서 데이터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-263">The example inserts two rows into the table, and then selects data from the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3741-264">이 테이블에는 테이블을 보다 잘 표시하고 읽을 수 있도록 열이 5개만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-264">This table has only five columns to make it easier to display and read.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE DocumentStoreWithColumnSet  
    (DocID int PRIMARY KEY,  
     Title varchar(200) NOT NULL,  
     ProductionSpecification varchar(20) SPARSE NULL,  
     ProductionLocation smallint SPARSE NULL,  
     MarketingSurveyGroup varchar(20) SPARSE NULL,  
     MarketingProgramID int SPARSE NULL,  
     SpecialPurposeColumns XML COLUMN_SET FOR ALL_SPARSE_COLUMNS);  
GO  
```  
  
### <a name="b-inserting-data-to-a-table-by-using-the-names-of-the-sparse-columns"></a><span data-ttu-id="f3741-265">B.</span><span class="sxs-lookup"><span data-stu-id="f3741-265">B.</span></span> <span data-ttu-id="f3741-266">스파스 열 이름을 사용하여 테이블에 데이터 삽입</span><span class="sxs-lookup"><span data-stu-id="f3741-266">Inserting data to a table by using the names of the sparse columns</span></span>  
 <span data-ttu-id="f3741-267">다음 예에서는 예 1에서 만든 테이블에 두 개의 행을 삽입합니다. 이 예에서는 스파스 열 이름을 사용하고 열 집합을 참조하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-267">The following examples insert two rows into the table that is created in example A. The examples use the names of the sparse columns and do not reference the column set.</span></span>  
  
```  
INSERT DocumentStoreWithColumnSet (DocID, Title, ProductionSpecification, ProductionLocation)  
VALUES (1, 'Tire Spec 1', 'AXZZ217', 27);  
GO  
  
INSERT DocumentStoreWithColumnSet (DocID, Title, MarketingSurveyGroup)  
VALUES (2, 'Survey 2142', 'Men 25 - 35');  
GO  
```  
  
### <a name="c-inserting-data-to-a-table-by-using-the-name-of-the-column-set"></a><span data-ttu-id="f3741-268">C.</span><span class="sxs-lookup"><span data-stu-id="f3741-268">C.</span></span> <span data-ttu-id="f3741-269">열 집합 이름을 사용하여 테이블에 데이터 삽입</span><span class="sxs-lookup"><span data-stu-id="f3741-269">Inserting data to a table by using the name of the column set</span></span>  
 <span data-ttu-id="f3741-270">다음 예에서는 예 1에서 만든 테이블에 세 번째 행을 삽입합니다. 이 예에서는 스파스 열 이름이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-270">The following example inserts a third row into the table that is created in example A. This time the names of the sparse columns are not used.</span></span> <span data-ttu-id="f3741-271">대신 열 집합 이름이 사용되고 삽입 작업으로 인해 XML 형식의 스파스 열 4개 중 2개에 대한 값이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-271">Instead, the name of the column set is used, and the insert provides the values for two of the four sparse columns in XML format.</span></span>  
  
```  
INSERT DocumentStoreWithColumnSet (DocID, Title, SpecialPurposeColumns)  
VALUES (3, 'Tire Spec 2', '<ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>');  
GO  
```  
  
### <a name="d-observing-the-results-of-a-column-set-when-select--is-used"></a><span data-ttu-id="f3741-272">D.</span><span class="sxs-lookup"><span data-stu-id="f3741-272">D.</span></span> <span data-ttu-id="f3741-273">SELECT \*가 사용되는 경우의 열 집합 결과 관찰</span><span class="sxs-lookup"><span data-stu-id="f3741-273">Observing the results of a column set when SELECT \* is used</span></span>  
 <span data-ttu-id="f3741-274">다음 예에서는 열 집합을 포함하는 테이블의 모든 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-274">The following example selects all the columns from the table that contains a column set.</span></span> <span data-ttu-id="f3741-275">이 예에서는 스파스 열의 조합 값과 함께 XML 열을 반환하며</span><span class="sxs-lookup"><span data-stu-id="f3741-275">It returns an XML column with the combined values of the sparse columns.</span></span> <span data-ttu-id="f3741-276">스파스 열을 개별적으로 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-276">It does not return the sparse columns individually.</span></span>  
  
```  
SELECT DocID, Title, SpecialPurposeColumns FROM DocumentStoreWithColumnSet ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        SpecialPurposeColumns`  
  
 `1      Tire Spec 1  <ProductionSpecification>AXZZ217</ProductionSpecification><ProductionLocation>27</ProductionLocation>`  
  
 `2      Survey 2142  <MarketingSurveyGroup>Men 25 - 35</MarketingSurveyGroup>`  
  
 `3      Tire Spec 2  <ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>`  
  
### <a name="e-observing-the-results-of-selecting-the-column-set-by-name"></a><span data-ttu-id="f3741-277">E.</span><span class="sxs-lookup"><span data-stu-id="f3741-277">E.</span></span> <span data-ttu-id="f3741-278">이름별로 열 집합을 선택한 결과 관찰</span><span class="sxs-lookup"><span data-stu-id="f3741-278">Observing the results of selecting the column set by name</span></span>  
 <span data-ttu-id="f3741-279">Production 부서는 마케팅 데이터에 관심이 없으므로 이 예에서는 `WHERE` 절을 추가하여 출력을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-279">Because the Production department is not interested in the marketing data, this example adds a `WHERE` clause to restrict the output.</span></span> <span data-ttu-id="f3741-280">이 예에서는 열 집합 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-280">The example uses the name of the column set.</span></span>  
  
```  
SELECT DocID, Title, SpecialPurposeColumns  
FROM DocumentStoreWithColumnSet  
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        SpecialPurposeColumns`  
  
 `1     Tire Spec 1  <ProductionSpecification>AXZZ217</ProductionSpecification><ProductionLocation>27</ProductionLocation>`  
  
 `3     Tire Spec 2  <ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>`  
  
### <a name="f-observing-the-results-of-selecting-sparse-columns-by-name"></a><span data-ttu-id="f3741-281">F.</span><span class="sxs-lookup"><span data-stu-id="f3741-281">F.</span></span> <span data-ttu-id="f3741-282">이름별로 스파스 열을 선택한 결과 관찰</span><span class="sxs-lookup"><span data-stu-id="f3741-282">Observing the results of selecting sparse columns by name</span></span>  
 <span data-ttu-id="f3741-283">테이블에 열 집합이 포함되어 있으면 다음 예에서처럼 개별 열 이름을 사용하여 테이블을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-283">When a table contains a column set, you can still query the table by using the individual column names as shown in the following example.</span></span>  
  
```  
SELECT DocID, Title, ProductionSpecification, ProductionLocation   
FROM DocumentStoreWithColumnSet  
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        ProductionSpecification ProductionLocation`  
  
 `1     Tire Spec 1  AXZZ217                 27`  
  
 `3     Tire Spec 2  AXW9R411                38`  
  
### <a name="g-updating-a-table-by-using-a-column-set"></a><span data-ttu-id="f3741-284">G.</span><span class="sxs-lookup"><span data-stu-id="f3741-284">G.</span></span> <span data-ttu-id="f3741-285">열 집합을 사용하여 테이블 업데이트</span><span class="sxs-lookup"><span data-stu-id="f3741-285">Updating a table by using a column set</span></span>  
 <span data-ttu-id="f3741-286">다음 예에서는 해당 행에서 사용하는 스파스 열 모두에 대해 세 번째 레코드를 새 값으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-286">The following example updates the third record with new values for both sparse columns that are used by that row.</span></span>  
  
```  
UPDATE DocumentStoreWithColumnSet  
SET SpecialPurposeColumns = '<ProductionSpecification>ZZ285W</ProductionSpecification><ProductionLocation>38</ProductionLocation>'  
WHERE DocID = 3 ;  
GO  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f3741-287">열 집합을 사용하는 UPDATE 문은 테이블의 모든 스파스 열을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-287">An UPDATE statement that uses a column set updates all the sparse columns in the table.</span></span> <span data-ttu-id="f3741-288">참조되지 않는 스파스 열은 NULL로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-288">Sparse columns that are not referenced are updated to NULL.</span></span>  
  
 <span data-ttu-id="f3741-289">다음 예에서는 세 번째 레코드를 업데이트하지만 채워진 두 열 중 하나의 값만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-289">The following example updates the third record, but only specifies the value of one of the two populated columns.</span></span> <span data-ttu-id="f3741-290">세 번째 열 `ProductionLocation` 은 `UPDATE` 문에 포함되지 않으며 NULL로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3741-290">The second column `ProductionLocation` is not included in the `UPDATE` statement and is updated to NULL.</span></span>  
  
```  
UPDATE DocumentStoreWithColumnSet  
SET SpecialPurposeColumns = '<ProductionSpecification>ZZ285W</ProductionSpecification>'  
WHERE DocID = 3 ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3741-291">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3741-291">See Also</span></span>  
 [<span data-ttu-id="f3741-292">스파스 열 사용</span><span class="sxs-lookup"><span data-stu-id="f3741-292">Use Sparse Columns</span></span>](use-sparse-columns.md)  
  
  
