---
title: 데이터베이스 스키마 이해 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Schema Generation Wizard, database schema
- database schema [Analysis Services]
- relational schema [Analysis Services], database schema
- subject area schema options [Analysis Services]
- staging area schema options [Analysis Services]
- denormalized schemas
ms.assetid: 51e411f9-ee3f-4b92-9833-c2bce8c6b752
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84f44db1b7abca1b8cad45cf5f46fcc0006bd92a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732092"
---
# <a name="understanding-the-database-schemas"></a><span data-ttu-id="b3d4e-102">데이터베이스 스키마 이해</span><span class="sxs-lookup"><span data-stu-id="b3d4e-102">Understanding the Database Schemas</span></span>
  <span data-ttu-id="b3d4e-103">스키마 생성 마법사는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 차원 및 측정값 그룹을 기반으로 주제 영역 데이터베이스에 대한 비정규 관계형 스키마를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-103">The Schema Generation Wizard generates a denormalized relational schema for the subject area database based on the dimensions and measure groups in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="b3d4e-104">마법사는 각 차원에 대해 차원 데이터를 저장할 관계형 테이블(차원 테이블)과 각 측정값 그룹에 대해 팩트 데이터를 저장할 관계형 테이블(팩트 테이블)을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-104">The wizard generates a relational table for each dimension to store dimension data, which is called a dimension table, and a relational table for each measure group to store fact data, which is called a fact table.</span></span> <span data-ttu-id="b3d4e-105">이러한 관계형 테이블을 생성할 때 연결된 차원, 연결된 측정값 및 서버 시간 차원은 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-105">The wizard ignores linked dimensions, linked measure groups, and server time dimensions when it generates these relational tables.</span></span>  
  
## <a name="validation"></a><span data-ttu-id="b3d4e-106">유효성 검사</span><span class="sxs-lookup"><span data-stu-id="b3d4e-106">Validation</span></span>  
 <span data-ttu-id="b3d4e-107">스키마 생성 마법사는 기본 관계형 스키마를 생성하기 전에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 큐브 및 차원의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-107">Before it begins to generate the underlying relational schema, the Schema Generation Wizard validates the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cubes and dimensions.</span></span> <span data-ttu-id="b3d4e-108">오류를 발견하면 작업을 중지하고 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 태스크 목록 창에 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-108">If the wizard detects errors, it stops and reports the errors to the Task List window in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="b3d4e-109">생성을 막는 오류의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-109">Examples of errors that prevent generation include the following:</span></span>  
  
-   <span data-ttu-id="b3d4e-110">키 특성이 두 개 이상인 차원</span><span class="sxs-lookup"><span data-stu-id="b3d4e-110">Dimensions that have more than one key attribute.</span></span>  
  
-   <span data-ttu-id="b3d4e-111">키 특성과 다른 데이터 형식의 부모 특성</span><span class="sxs-lookup"><span data-stu-id="b3d4e-111">Parent attributes that have different data types than the key attributes.</span></span>  
  
-   <span data-ttu-id="b3d4e-112">측정값이 없는 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="b3d4e-112">Measure groups that do not have measures.</span></span>  
  
-   <span data-ttu-id="b3d4e-113">중복 제거 차원 또는 잘못 구성된 측정값</span><span class="sxs-lookup"><span data-stu-id="b3d4e-113">Degenerate dimensions or measures that are improperly configured.</span></span>  
  
-   <span data-ttu-id="b3d4e-114">잘못 구성된 서로게이트 키. `ScdOriginalID` 특성 유형을 사용하는 여러 개의 특성 또는 정수 데이터 형식을 통해 열에 바인딩되지 않은 `ScdOriginalID`를 사용하는 특성이 여기에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-114">Surrogate keys that are improperly configured, such as multiple attributes using the `ScdOriginalID` attribute type or an attribute using the `ScdOriginalID` that is not bound to a column using the integer data type.</span></span>  
  
## <a name="dimension-tables"></a><span data-ttu-id="b3d4e-115">차원 테이블</span><span class="sxs-lookup"><span data-stu-id="b3d4e-115">Dimension Tables</span></span>  
 <span data-ttu-id="b3d4e-116">스키마 생성 마법사는 각 차원에 대해 주제 영역 데이터베이스에 포함할 차원 테이블을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-116">For each dimension, the Schema Generation Wizard generates a dimension table to be included in the subject area database.</span></span> <span data-ttu-id="b3d4e-117">차원 테이블의 구조는 차원 테이블의 기반이 되는 차원을 디자인할 때 선택한 사항에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-117">The structure of the dimension table depends on the choices made while designing the dimension on which it is based.</span></span>  
  
 <span data-ttu-id="b3d4e-118">열</span><span class="sxs-lookup"><span data-stu-id="b3d4e-118">Columns</span></span>  
 <span data-ttu-id="b3d4e-119">마법사는 차원 테이블의 기반이 되는 차원의 각 특성에 연결되는 바인딩(예: 각 특성의 `KeyColumns`, `NameColumn`, `ValueColumn`, `CustomRollupColumn`, `CustomRollupPropertiesColumn`, `UnaryOperatorColumn` 속성에 대한 바인딩) 각각에 대해 열을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-119">The wizard generates one column for the bindings associated to each attribute in the dimension on which the dimension table is based, such as the bindings for the `KeyColumns`, `NameColumn`, `ValueColumn`, `CustomRollupColumn`, `CustomRollupPropertiesColumn`, and `UnaryOperatorColumn` properties of each attribute.</span></span>  
  
 <span data-ttu-id="b3d4e-120">관계</span><span class="sxs-lookup"><span data-stu-id="b3d4e-120">Relationships</span></span>  
 <span data-ttu-id="b3d4e-121">마법사는 각 부모 특성에 대한 열과 차원 테이블의 기본 키 간에 관계를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-121">The wizard generates a relationship between the column for each parent attribute and the primary key of the dimension table.</span></span>  
  
 <span data-ttu-id="b3d4e-122">또한 큐브의 참조 차원으로 정의되는 각 추가 차원 테이블의 기본 키에 대한 관계를 생성합니다(해당되는 경우).</span><span class="sxs-lookup"><span data-stu-id="b3d4e-122">The wizard also generates a relationship to the primary key in each additional dimension table defined as a referenced dimension in the cube, if applicable.</span></span>  
  
 <span data-ttu-id="b3d4e-123">제약 조건</span><span class="sxs-lookup"><span data-stu-id="b3d4e-123">Constraints</span></span>  
 <span data-ttu-id="b3d4e-124">마법사는 기본적으로 차원의 키 특성을 기준으로 각 차원 테이블에 대해 기본 키 제약 조건을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-124">The wizard generates a primary key constraint, by default, for each dimension table based on the key attribute of the dimension.</span></span> <span data-ttu-id="b3d4e-125">기본 키 제약 조건이 생성되면 기본적으로 별도의 이름 열이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-125">If the primary key constraint is generated, a separate name column is generated by default.</span></span> <span data-ttu-id="b3d4e-126">데이터베이스에서 기본 키를 생성하지 않더라도 데이터 원본 뷰에는 논리적 기본 키가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-126">A logical primary key is created in the data source view even if you decide not to create the primary key in the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3d4e-127">차원 테이블의 기반이 되는 차원에서 키 특성을 두 개 이상 지정하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-127">An error occurs if more than one key attribute is specified in the dimension on which the dimension table is based.</span></span>  
  
 <span data-ttu-id="b3d4e-128">Translations</span><span class="sxs-lookup"><span data-stu-id="b3d4e-128">Translations</span></span>  
 <span data-ttu-id="b3d4e-129">마법사는 번역 열이 필요한 특성에 대해 번역된 값을 보관할 별도의 테이블을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-129">The wizard generates a separate table to hold the translated values for any attribute that requires a translation column.</span></span> <span data-ttu-id="b3d4e-130">또한 마법사는 필요한 각 언어에 대해 별도의 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-130">The wizard also creates a separate column for each of the required languages.</span></span>  
  
## <a name="fact-tables"></a><span data-ttu-id="b3d4e-131">팩트 테이블</span><span class="sxs-lookup"><span data-stu-id="b3d4e-131">Fact Tables</span></span>  
 <span data-ttu-id="b3d4e-132">스키마 생성 마법사는 큐브의 각 측정값 그룹에 대해 주제 영역 데이터베이스에 포함할 팩트 테이블을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-132">For each measure group in a cube, the Schema Generation Wizard generates a fact table to be included in the subject area database.</span></span> <span data-ttu-id="b3d4e-133">팩트 테이블의 구조는 팩트 테이블의 기반이 되는 측정값 그룹을 디자인할 때 선택한 사항 및 측정값 그룹과 포함된 차원 간에 설정된 관계에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-133">The structure of the fact table depends on the choices made while designing the measure group on which it is based, and the relationships established between the measure group and any included dimensions.</span></span>  
  
 <span data-ttu-id="b3d4e-134">열</span><span class="sxs-lookup"><span data-stu-id="b3d4e-134">Columns</span></span>  
 <span data-ttu-id="b3d4e-135">마법사는 `Count` 집계 함수를 사용하는 측정값을 제외하고 각 측정값에 대해 열을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-135">The wizard generates one column for each measure, except for measures that use the `Count` aggregation function.</span></span> <span data-ttu-id="b3d4e-136">이 함수를 사용하는 측정값에는 팩트 테이블에서 해당되는 열이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-136">Such measures do not require a corresponding column in the fact table.</span></span>  
  
 <span data-ttu-id="b3d4e-137">또한 마법사는 측정값 그룹에 있는 각 일반 차원 관계의 세분성 특성 열 각각에 대해 열을 생성하고, 테이블의 기반이 되는 측정값 그룹에 대한 팩트 차원 관계가 있는 차원의 각 특성에 연결된 바인딩에 대해 하나 이상의 열을 생성합니다(해당되는 경우).</span><span class="sxs-lookup"><span data-stu-id="b3d4e-137">The wizard also generates one column for each granularity attribute column of each regular dimension relationship on the measure group, and one or more columns for the bindings associated to each attribute of a dimension that has a fact dimension relationship to the measure group on which this table is based, if applicable.</span></span>  
  
 <span data-ttu-id="b3d4e-138">관계</span><span class="sxs-lookup"><span data-stu-id="b3d4e-138">Relationships</span></span>  
 <span data-ttu-id="b3d4e-139">마법사는 팩트 테이블의 각 일반 차원 관계에 대해 차원 테이블의 세분성 특성에 대한 관계를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-139">The wizard generates one relationship for each regular dimension relationship from the fact table to the dimension table's granularity attribute.</span></span> <span data-ttu-id="b3d4e-140">세분성이 차원 테이블의 키 특성을 기반으로 하는 경우에는 데이터베이스와 데이터 원본 뷰에서 관계가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-140">If the granularity is based on the key attribute of the dimension table, the relationship is created in the database and in the data source view.</span></span> <span data-ttu-id="b3d4e-141">세분성이 다른 특성을 기반으로 하는 경우에는 데이터 원본 뷰에서만 관계가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-141">If the granularity is based on another attribute, the relationship is created only in the data source view.</span></span>  
  
 <span data-ttu-id="b3d4e-142">마법사에서 인덱스를 생성 하도록 선택한 경우 이러한 각 관계 열에 대해 비클러스터형 인덱스가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-142">If you chose to generate indexes in the wizard, a nonclustered index is generated for each of these relationship columns.</span></span>  
  
 <span data-ttu-id="b3d4e-143">제약 조건</span><span class="sxs-lookup"><span data-stu-id="b3d4e-143">Constraints</span></span>  
 <span data-ttu-id="b3d4e-144">팩트 테이블에서는 기본 키가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-144">Primary keys are not generated on fact tables.</span></span>  
  
 <span data-ttu-id="b3d4e-145">참조 무결성을 강제 적용하는 경우에는 차원 테이블과 팩트 테이블 간에 참조 무결성 제약 조건이 생성됩니다(해당되는 경우).</span><span class="sxs-lookup"><span data-stu-id="b3d4e-145">If you chose to enforce referential integrity, referential integrity constraints are generated between dimension tables and fact tables where applicable.</span></span>  
  
 <span data-ttu-id="b3d4e-146">Translations</span><span class="sxs-lookup"><span data-stu-id="b3d4e-146">Translations</span></span>  
 <span data-ttu-id="b3d4e-147">마법사는 측정값 그룹에서 번역 열이 필요한 속성에 대해 번역된 값을 보관할 별도의 테이블을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-147">The wizard generates a separate table to hold the translated values for any property in the measure group that requires a translation column.</span></span> <span data-ttu-id="b3d4e-148">또한 마법사는 필요한 각 언어에 대해 별도의 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-148">The wizard also creates a separate column for each of the required languages.</span></span>  
  
## <a name="data-type-conversion-and-default-lengths"></a><span data-ttu-id="b3d4e-149">데이터 형식 변환 및 기본 길이</span><span class="sxs-lookup"><span data-stu-id="b3d4e-149">Data Type Conversion and Default Lengths</span></span>  
 <span data-ttu-id="b3d4e-150">스키마 생성 마법사는 데이터 형식을 사용 하는 열을 제외 하 고 모든 경우에 데이터 형식을 무시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `wchar` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-150">Schema Generation Wizard ignores data types in all cases except for columns that use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `wchar` data type.</span></span> <span data-ttu-id="b3d4e-151">`wchar` 데이터 크기는 `nvarchar` 데이터 형식으로 직접 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-151">The `wchar` data size translates directly to the `nvarchar` data type.</span></span> <span data-ttu-id="b3d4e-152">그러나 `wchar` 크기를 사용하는 지정된 열의 길이가 4000바이트를 초과하면 스키마 생성 마법사에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-152">However, if the specified length of a column using the `wchar` size is larger than 4000 bytes, the Schema Generation Wizard generates an error.</span></span>  
  
 <span data-ttu-id="b3d4e-153">특성에 대한 바인딩과 같은 데이터 항목에 대해 길이를 지정하지 않으면 해당 열에 다음 표의 기본 길이가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3d4e-153">If a data item, such as the binding for an attribute, has no specified length, the default length listed in the following table is used for the column.</span></span>  
  
|<span data-ttu-id="b3d4e-154">데이터 항목</span><span class="sxs-lookup"><span data-stu-id="b3d4e-154">Data item</span></span>|<span data-ttu-id="b3d4e-155">기본 길이(바이트)</span><span class="sxs-lookup"><span data-stu-id="b3d4e-155">Default length (bytes)</span></span>|  
|---------------|------------------------------|  
|<span data-ttu-id="b3d4e-156">KeyColumn</span><span class="sxs-lookup"><span data-stu-id="b3d4e-156">KeyColumn</span></span>|<span data-ttu-id="b3d4e-157">50</span><span class="sxs-lookup"><span data-stu-id="b3d4e-157">50</span></span>|  
|<span data-ttu-id="b3d4e-158">NameColumn</span><span class="sxs-lookup"><span data-stu-id="b3d4e-158">NameColumn</span></span>|<span data-ttu-id="b3d4e-159">50</span><span class="sxs-lookup"><span data-stu-id="b3d4e-159">50</span></span>|  
|<span data-ttu-id="b3d4e-160">CustomRollupColumn</span><span class="sxs-lookup"><span data-stu-id="b3d4e-160">CustomRollupColumn</span></span>|<span data-ttu-id="b3d4e-161">3000</span><span class="sxs-lookup"><span data-stu-id="b3d4e-161">3000</span></span>|  
|<span data-ttu-id="b3d4e-162">CustomRollupPropertiesColumn</span><span class="sxs-lookup"><span data-stu-id="b3d4e-162">CustomRollupPropertiesColumn</span></span>|<span data-ttu-id="b3d4e-163">500</span><span class="sxs-lookup"><span data-stu-id="b3d4e-163">500</span></span>|  
|<span data-ttu-id="b3d4e-164">UnaryOperatorColumn</span><span class="sxs-lookup"><span data-stu-id="b3d4e-164">UnaryOperatorColumn</span></span>|<span data-ttu-id="b3d4e-165">1</span><span class="sxs-lookup"><span data-stu-id="b3d4e-165">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3d4e-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3d4e-166">See Also</span></span>  
 <span data-ttu-id="b3d4e-167">[증분 생성 이해](understanding-incremental-generation.md) </span><span class="sxs-lookup"><span data-stu-id="b3d4e-167">[Understanding Incremental Generation](understanding-incremental-generation.md) </span></span>  
 [<span data-ttu-id="b3d4e-168">데이터 원본 뷰 및 데이터 원본에 대한 변경 내용 관리</span><span class="sxs-lookup"><span data-stu-id="b3d4e-168">Manage Changes to Data Source Views and Data Sources</span></span>](manage-changes-to-data-source-views-and-data-sources.md)  
  
  
