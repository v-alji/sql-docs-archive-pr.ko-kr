---
title: 열 속성(일반 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.columnproperties.general.f1
ms.assetid: a745890b-994e-4c23-8028-5c83751e60c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29a82df217eef719b4f0efffb3fc0c24b36a27aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661611"
---
# <a name="column-properties-general-page"></a><span data-ttu-id="066f4-102">열 속성(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="066f4-102">Column Properties (General Page)</span></span>
  <span data-ttu-id="066f4-103">이 페이지를 사용하여 선택한 열의 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-103">Use this page to view properties for the selected column.</span></span>  
  
 <span data-ttu-id="066f4-104">이 페이지의 정보는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-104">Information on this page is read-only.</span></span> <span data-ttu-id="066f4-105">열을 수정하려면 **열 속성** 대화 상자를 닫고, 개체 탐색기에서 테이블과 열을 확장하고, 열을 마우스 오른쪽 단추로 클릭한 다음 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-105">To modify the column, close the **Column Properties** dialog box, expand the table and columns in Object Explorer, right-click the column, and then click **Design**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="066f4-106">옵션</span><span class="sxs-lookup"><span data-stu-id="066f4-106">Options</span></span>  
 <span data-ttu-id="066f4-107">**이름**</span><span class="sxs-lookup"><span data-stu-id="066f4-107">**Name**</span></span>  
 <span data-ttu-id="066f4-108">열 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-108">The name of the column.</span></span>  
  
 <span data-ttu-id="066f4-109">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="066f4-109">**Data Type**</span></span>  
 <span data-ttu-id="066f4-110">열에서 보유할 수 있는 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-110">The type of data that the column can hold.</span></span> <span data-ttu-id="066f4-111">데이터 형식이 사용자 정의 데이터 형식인 경우 해당 형식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-111">If the data type is a user-defined data type, the user-defined data type is displayed.</span></span> <span data-ttu-id="066f4-112">사용자 정의 데이터 형식이 아닌 경우에는 시스템 데이터 형식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-112">If the data type is not a user-defined data type, then the system data type is displayed.</span></span> <span data-ttu-id="066f4-113">자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="066f4-113">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="066f4-114">**시스템 유형**</span><span class="sxs-lookup"><span data-stu-id="066f4-114">**System Type**</span></span>  
 <span data-ttu-id="066f4-115">열에서 보유할 수 있는 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-115">The type of data that the column can hold.</span></span> <span data-ttu-id="066f4-116">데이터 형식이 시스템 데이터 형식인 경우 해당 형식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-116">If the data type is a system data type, then the system data type is displayed.</span></span> <span data-ttu-id="066f4-117">사용자 정의 데이터 형식인 경우에는 해당 사용자 정의 데이터 형식을 구성하는 시스템 데이터 형식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-117">If the data type is a user-defined data type, the system data type that makes up the user-defined data type is displayed.</span></span>  
  
 <span data-ttu-id="066f4-118">**기본 키**</span><span class="sxs-lookup"><span data-stu-id="066f4-118">**Primary Key**</span></span>  
 <span data-ttu-id="066f4-119">열이 기본 키인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-119">Indicates whether the column is a primary key.</span></span> <span data-ttu-id="066f4-120">가능한 값은 **True**및 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-120">Possible values are **True**and **False**.</span></span>  
  
 <span data-ttu-id="066f4-121">**Null 허용**</span><span class="sxs-lookup"><span data-stu-id="066f4-121">**Allow Nulls**</span></span>  
 <span data-ttu-id="066f4-122">열에 Null 값을 사용할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-122">Indicates whether the column accepts null values.</span></span> <span data-ttu-id="066f4-123">가능한 값은 **True** 및 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-123">Possible values are **True** and **False**.</span></span>  
  
 <span data-ttu-id="066f4-124">**계산 여부**</span><span class="sxs-lookup"><span data-stu-id="066f4-124">**Is Computed**</span></span>  
 <span data-ttu-id="066f4-125">열 값이 계산 식의 결과 값인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-125">Indicates whether the column value is the result of a computed expression.</span></span>  
  
 <span data-ttu-id="066f4-126">**계산된 텍스트**</span><span class="sxs-lookup"><span data-stu-id="066f4-126">**Computed text**</span></span>  
 <span data-ttu-id="066f4-127">열 텍스트 컴퓨팅에 사용된 문을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-127">Indicates the statement used to compute the column text.</span></span> <span data-ttu-id="066f4-128">자세한 내용은 [Specify Computed Columns in a Table](specify-computed-columns-in-a-table.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="066f4-128">For more information, [Specify Computed Columns in a Table](specify-computed-columns-in-a-table.md).</span></span>  
  
 <span data-ttu-id="066f4-129">**ID**</span><span class="sxs-lookup"><span data-stu-id="066f4-129">**Identity**</span></span>  
 <span data-ttu-id="066f4-130">테이블에 대한 ID 열인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-130">Indicates whether the column is the identity column for the table.</span></span> <span data-ttu-id="066f4-131">가능한 값은 **True** 및 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-131">Possible values are **True** and **False**.</span></span>  
  
 <span data-ttu-id="066f4-132">**ID 초기값**</span><span class="sxs-lookup"><span data-stu-id="066f4-132">**Identity Seed**</span></span>  
 <span data-ttu-id="066f4-133">ID 열의 초기 행 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-133">Indicates the initial row value for an identity column.</span></span>  
  
 <span data-ttu-id="066f4-134">**ID 증가값**</span><span class="sxs-lookup"><span data-stu-id="066f4-134">**Identity Increment**</span></span>  
 <span data-ttu-id="066f4-135">**ID 증분** 속성은 새로 삽입되는 행의 ID 값을 생성할 때 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 기존의 가장 큰 행 ID 값에 더하는 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-135">The **Identity Increment** property specifies the value [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adds to the greatest existing row identity value as it generates an identity value for a row being inserted.</span></span>  
  
 <span data-ttu-id="066f4-136">**기본 바인딩**</span><span class="sxs-lookup"><span data-stu-id="066f4-136">**Default Binding**</span></span>  
 <span data-ttu-id="066f4-137">열에 바인딩된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] default bound to the column.</span></span> <span data-ttu-id="066f4-138">기본값이 바인딩되지 않은 경우에 이 옵션은 공백입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-138">This option is blank if no default is bound.</span></span>  
  
 <span data-ttu-id="066f4-139">**기본 스키마**</span><span class="sxs-lookup"><span data-stu-id="066f4-139">**Default Schema**</span></span>  
 <span data-ttu-id="066f4-140">참조된 열에 바인딩된 기본값을 소유하는 데이터베이스 스키마를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-140">Identifies the database schema owning the default bound to the referenced column.</span></span> <span data-ttu-id="066f4-141">기본값이 바인딩되지 않은 경우에 이 옵션은 공백입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-141">This option is blank if no default is bound.</span></span>  
  
 <span data-ttu-id="066f4-142">**규칙**</span><span class="sxs-lookup"><span data-stu-id="066f4-142">**Rule**</span></span>  
 <span data-ttu-id="066f4-143">열에 바인딩된 데이터 무결성 제약 조건을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-143">Identifies the data integrity constraint that is bound to the column.</span></span> <span data-ttu-id="066f4-144">규칙이 바인딩되지 않은 경우에 이 옵션은 공백입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-144">This option is blank if no rule is bound.</span></span>  
  
 <span data-ttu-id="066f4-145">**규칙 스키마**</span><span class="sxs-lookup"><span data-stu-id="066f4-145">**Rule Schema**</span></span>  
 <span data-ttu-id="066f4-146">참조된 열에 바인딩된 규칙을 소유하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 스키마를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-146">Displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database schema that owns the rule bound to the referenced column.</span></span> <span data-ttu-id="066f4-147">규칙이 바인딩되지 않은 경우에 이 옵션은 공백입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-147">This option is blank if no rule is bound.</span></span>  
  
 <span data-ttu-id="066f4-148">**길이**</span><span class="sxs-lookup"><span data-stu-id="066f4-148">**Length**</span></span>  
 <span data-ttu-id="066f4-149">열에 허용되는 최대 문자 또는 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-149">Indicates the maximum number of characters or bytes accepted by the column.</span></span>  
  
 <span data-ttu-id="066f4-150">**데이터 정렬**</span><span class="sxs-lookup"><span data-stu-id="066f4-150">**Collation**</span></span>  
 <span data-ttu-id="066f4-151">열에 지정되어 있는 데이터 정렬을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-151">Displays the current collation for the column.</span></span> <span data-ttu-id="066f4-152">이 옵션이 공백인 경우 개체의 데이터 정렬 속성이 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-152">If blank, the collation property is inherited from the object.</span></span>  
  
 <span data-ttu-id="066f4-153">**전체 자릿수**</span><span class="sxs-lookup"><span data-stu-id="066f4-153">**Numeric Precision**</span></span>  
 <span data-ttu-id="066f4-154">고정 전체 자릿수의 숫자 데이터 형식에서 최대 자릿수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-154">Indicates the maximum number of digits in a fixed-precision, numeric data type.</span></span>  
  
 <span data-ttu-id="066f4-155">**소수 자릿수**</span><span class="sxs-lookup"><span data-stu-id="066f4-155">**Numeric Scale**</span></span>  
 <span data-ttu-id="066f4-156">고정 전체 자릿수의 숫자 데이터 형식에서 소수점 이하 자릿수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-156">Indicates the number of digits to the right of the decimal point in a fixed-precision, numeric data type.</span></span>  
  
 <span data-ttu-id="066f4-157">**XML 스키마 네임스페이스**</span><span class="sxs-lookup"><span data-stu-id="066f4-157">**XML Schema Namespace**</span></span>  
 <span data-ttu-id="066f4-158">XSD(XML 스키마 정의) 언어 유효성 검사를 통해 XML 열의 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-158">Defines the type of the XML column by way of XML Schema Definition (XSD) Language validation.</span></span>  
  
 <span data-ttu-id="066f4-159">**XML 스키마 네임스페이스 스키마**</span><span class="sxs-lookup"><span data-stu-id="066f4-159">**XML Schema Namespace schema**</span></span>  
 <span data-ttu-id="066f4-160">XML 스키마 네임스페이스를 소유하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-160">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schema that owns the XML Schema Namespace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="066f4-161">스키마는 일반적인 용어지만 몇 가지 다른 의미를 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-161">There are several common but different meanings of the word schema.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="066f4-162">에서 스키마는 데이터베이스 개체를 구성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-162">uses schema to organize database objects.</span></span> <span data-ttu-id="066f4-163">소유권과 비슷한 개념이라 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-163">It is similar to ownership.</span></span> <span data-ttu-id="066f4-164">XML에서는 XML 정보 구성을 일련의 네임스페이스로 정의하는 데 스키마가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-164">XML uses the schema to define the organization of XML information into a series of namespaces.</span></span> <span data-ttu-id="066f4-165">즉, 스키마를 통해 관련된 XML 코드가 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-165">It is a way to group related XML code together.</span></span>  
  
 <span data-ttu-id="066f4-166">**스파스 여부**</span><span class="sxs-lookup"><span data-stu-id="066f4-166">**Is Sparse**</span></span>  
 <span data-ttu-id="066f4-167">열이 스파스 열인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-167">Indicates whether the column is a sparse column.</span></span> <span data-ttu-id="066f4-168">가능한 값은 **True** 및 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-168">Possible values are **True** and **False**.</span></span> <span data-ttu-id="066f4-169">자세한 내용은 [스파스 열 사용](use-sparse-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="066f4-169">For more information, see [Use Sparse Columns](use-sparse-columns.md).</span></span>  
  
 <span data-ttu-id="066f4-170">**열 집합 여부**</span><span class="sxs-lookup"><span data-stu-id="066f4-170">**Is Column Set**</span></span>  
 <span data-ttu-id="066f4-171">열이 열 집합인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-171">Indicates whether the column is a column set.</span></span> <span data-ttu-id="066f4-172">가능한 값은 **True** 및 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-172">Possible values are **True** and **False**.</span></span> <span data-ttu-id="066f4-173">자세한 내용은 [열 집합 사용](use-column-sets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="066f4-173">For more information, see [Use Column Sets](use-column-sets.md).</span></span>  
  
 <span data-ttu-id="066f4-174">**ANSI 패딩 상태**</span><span class="sxs-lookup"><span data-stu-id="066f4-174">**ANSI Padding Status**</span></span>  
 <span data-ttu-id="066f4-175">ANSI 패딩의 설정 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-175">Indicates whether ANSI padding is on or off.</span></span> <span data-ttu-id="066f4-176">자세한 내용은 [SET ANSI_PADDING&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="066f4-176">For more information, see [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).</span></span>  
  
 <span data-ttu-id="066f4-177">**전체 텍스트**</span><span class="sxs-lookup"><span data-stu-id="066f4-177">**Full Text**</span></span>  
 <span data-ttu-id="066f4-178">열이 전체 텍스트 쿼리에 참여하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-178">Displays whether the column participates in full-text queries.</span></span>  
  
 <span data-ttu-id="066f4-179">**통계 의미 체계**</span><span class="sxs-lookup"><span data-stu-id="066f4-179">**Statistical Semantics**</span></span>  
 <span data-ttu-id="066f4-180">열에 대해 통계 의미 체계 검색을 사용하도록 설정할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-180">Indicates whether statistical semantic search is enabled for the column.</span></span> <span data-ttu-id="066f4-181">자세한 내용은 [의미 체계 검색&#40;SQL Server&#41;](../search/semantic-search-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="066f4-181">For more information, see [Semantic Search &#40;SQL Server&#41;](../search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="066f4-182">**복제용 아님**</span><span class="sxs-lookup"><span data-stu-id="066f4-182">**Not For Replication**</span></span>  
 <span data-ttu-id="066f4-183">열을 복제할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-183">Indicates whether the column is available for replication.</span></span> <span data-ttu-id="066f4-184">가능한 값은 **True** 및 **False**입니다.</span><span class="sxs-lookup"><span data-stu-id="066f4-184">Possible values are **True** and **False**.</span></span>  
  
  
