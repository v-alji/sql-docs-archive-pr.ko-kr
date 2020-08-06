---
title: CSDLBI 개념 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 2fbdf621-a94d-4a55-a088-3d56d65016ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 16c6597171eef10da67ad497e4303b3716298e6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649232"
---
# <a name="csdlbi-concepts"></a><span data-ttu-id="8ef5f-102">CSDLBI 개념</span><span class="sxs-lookup"><span data-stu-id="8ef5f-102">CSDLBI Concepts</span></span>
  <span data-ttu-id="8ef5f-103">CSDLBI(BI 포함 개념 스키마 정의 언어) 주석은 엔터티 데이터 프레임워크를 기반으로 하며, 별도의 데이터 집합을 프로그래밍 방식으로 액세스, 쿼리 또는 내보낼 수 있도록 하여 데이터를 나타내기 위한 추상화입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-103">Conceptual Schema Definition Language with BI annotations (CSDLBI) is based on the Entity Data Framework, which is an abstraction for representing data in a way that enables disparate data sets to be programmatically accessed, queried, or exported.</span></span> <span data-ttu-id="8ef5f-104">CSDLBI는 풍부한 데이터 기반 보고 및 애플리케이션을 지원하기 때문에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 사용하여 만든 데이터 모델을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-104">CSDLBI is used to represent data models created using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] because it supports rich, data-driven reporting and applications.</span></span>  
  
 <span data-ttu-id="8ef5f-105">이 단원에서는 CSDLBI 표현이 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 모델(테이블 형식 및 다차원)에 매핑되는 방법을 설명하고 각 모델 유형의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-105">This section explains how the CSDLBI representation maps to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data models (both tabular and multidimensional), along with examples of each model type.</span></span>  
  
 <span data-ttu-id="8ef5f-106">이러한 개념을 설명하는 데 사용하는 예는 Codeplex에서 제공하는 AdventureWorks 예제 데이터베이스를 통해 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-106">Examples used to illustrate these concepts are taken from the AdventureWorks sample database, available on Codeplex.</span></span> <span data-ttu-id="8ef5f-107">예제에 대 한 자세한 내용은 [SQL Server에 대 한 놀이 Works 샘플](https://go.microsoft.com/fwlink/?linkID=220093)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-107">For more information about the samples, see [Adventure Works Samples for SQL Server](https://go.microsoft.com/fwlink/?linkID=220093).</span></span>  
  
## <a name="structure-of-a-tabular-model-in-csdlbi"></a><span data-ttu-id="8ef5f-108">CSDLBI의 테이블 형식 모델 구조</span><span class="sxs-lookup"><span data-stu-id="8ef5f-108">Structure of a Tabular Model in CSDLBI</span></span>  
 <span data-ttu-id="8ef5f-109">보고서 모델과 해당 데이터를 설명하는 CSDLBI 문서는 xsd 문으로 시작하여 모델에 대한 정의로 이어집니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-109">A CSDLBI document that describes a report model and its data begins with the xsd statement, followed by the definition of a model.</span></span>  
  
 <span data-ttu-id="8ef5f-110">모델은 다음과 같은 주요 엔터티, 연결 및 속성이 포함된 네임스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-110">The model is a namespace, which contains the following major entities, associations, and properties:</span></span>  
  
-   <span data-ttu-id="8ef5f-111">`EntityContainer`는 모델의 테이블을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-111">The `EntityContainer` lists the tables in the model.</span></span>  
  
-   <span data-ttu-id="8ef5f-112">각 테이블은 `EntityContainer`를 사용하여 `EntitySet`로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-112">Each table is listed with the `EntityContainer` as an `EntitySet`.</span></span>  
  
-   <span data-ttu-id="8ef5f-113">두 테이블 사이의 각 관계는 관계 끝점과 관계 역할을 정의하는 `AssociationSet`로 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-113">Each relationship between two tables is described as an `AssociationSet` that defines the relationship end points and the relationship roles.</span></span>  
  
-   <span data-ttu-id="8ef5f-114">BISM이 테이블 및 해당 열에 대해 추가 세부 정보(정렬 및 표시용 속성 포함)를 제공하도록 `EntityType` 요소가 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-114">The `EntityType` element is extended for BISM to provide additional detail about the tables and the columns in them, including properties for sorting and display purposes.</span></span>  
  
-   <span data-ttu-id="8ef5f-115">`Measure` 요소는 모델에 사용할 수 있는 계산을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-115">The `Measure` element defines calculations that can be used in the model.</span></span> <span data-ttu-id="8ef5f-116">새 `KPI` 요소를 사용하면 특수 표시 특성 집합을 추가하여 측정값을 KPI로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-116">A measure can be turned into a KPI by adding a set of special display attributes, using the new `KPI` Element.</span></span>  
  
-   <span data-ttu-id="8ef5f-117">별도의 큐브 뷰 표현은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-117">There is no separate representation of perspectives.</span></span> <span data-ttu-id="8ef5f-118">큐브 뷰에 포함되지 않은 열과 테이블은 CSDL로 표시되지만 `Hidden` 특성을 사용하여 플래그가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-118">Columns and tables that are not included in a perspective are present in the CSDL but flagged with the `Hidden` attribute.</span></span>  
  
### <a name="entities-entitysets-and-entitytypes"></a><span data-ttu-id="8ef5f-119">Entities, EntitySets 및 EntityTypes</span><span class="sxs-lookup"><span data-stu-id="8ef5f-119">Entities, EntitySets, and EntityTypes</span></span>  
 <span data-ttu-id="8ef5f-120">엔터티 데이터 프레임워크에서 엔터티의 개념은 데이터 모델의 열과 테이블을 나타내도록 확장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-120">The notion of an entity in the Entity Data Framework is extended to represent columns and tables from the data model.</span></span> <span data-ttu-id="8ef5f-121">다음 발췌 구문에서는 테이블이 세 개만 포함된 단순한 모델의 `EntitySet` 요소 목록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-121">The following excerpt shows the list of `EntitySet` elements in a simple model containing only three tables.</span></span>  
  
```  
<EntityContainer Name="SimpleModel">  
<EntitySet Name="DimCustomer"EntityType="SimpleModel.DimCustomer">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimDate" EntityType="SimpleModel.DimDate">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimGeography" EntityType="SimpleModel.DimGeography">  
     <bi:EntitySet />  
   </EntitySet> />  
  
```  
  
 <span data-ttu-id="8ef5f-122">`EntitySet`에는 테이블의 열이나 데이터에 대한 정보가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-122">The `EntitySet` does not contain information about columns or data in the table.</span></span> <span data-ttu-id="8ef5f-123">열과 해당 속성에 대한 자세한 설명은 EntityType 요소에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-123">The detailed description of the columns and their properties is provided in the EntityType element.</span></span>  
  
 <span data-ttu-id="8ef5f-124">각 엔터티(테이블)에 대한 `EntitySet` 요소에는 키 열, 열의 데이터 형식과 길이, Null 허용 여부, 정렬 동작 등을 정의하는 속성 모음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-124">The `EntitySet` element for each entity (table) includes a collection of properties that define the key column, the data type and length of the column, nullability, sorting behavior, and so forth.</span></span> <span data-ttu-id="8ef5f-125">예를 들어 다음 CSDL 발췌 구문에서는 Customer 테이블에 있는 세 개의 열을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-125">For example, the following CSDL excerpt describes three columns in the Customer table.</span></span> <span data-ttu-id="8ef5f-126">첫 번째 열은 모델에 내부적으로 사용되며 숨겨진 특수한 열입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-126">The first column is a special hidden column used internally by the model.</span></span>  
  
```  
<EntityType Name="Customer">  
  <Key>  
     <PropertyRef Name="RowNumber" />  
  </Key>  
    <Property Name="RowNumber" Type="Int64" Nullable="false">  
     <bi:Property Hidden="true" Contents="RowNumber"  
       Stability="RowNumber" />  
    </Property>  
    <Property Name="CustomerKey" Type="Int64" Nullable="false">  
      <bi:Property />  
    </Property>  
     <Property Name="FirstName" Type="String" MaxLength="Max" FixedLength="false">  
       <bi:Property />  
      </Property>  
  
```  
  
 <span data-ttu-id="8ef5f-127">생성되는 CSDLBI 문서 크기를 제한하기 위해 엔터티에 두 번 이상 나타나는 속성이 기존 속성에 대한 참조에 의해 지정되므로 `EntityType`에 대해 속성이 한 번만 나열되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-127">To limit the size of the CSDLBI document that is generated, properties that appear more than once in an entity are specified by a reference to an existing property, so that the property need be listed only once for the `EntityType`.</span></span> <span data-ttu-id="8ef5f-128">클라이언트 애플리케이션은 `EntityType`과 일치하는 `OriginEntityType`을 찾아 속성의 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-128">The client application can get the value of the property by finding the `EntityType` that matches the `OriginEntityType`.</span></span>  
  
### <a name="relationships"></a><span data-ttu-id="8ef5f-129">관계</span><span class="sxs-lookup"><span data-stu-id="8ef5f-129">Relationships</span></span>  
 <span data-ttu-id="8ef5f-130">엔터티 데이터 프레임 워크에서 관계는 엔터티 간의 *연결* 로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-130">In the Entity Data Framework, relationships are defined as *associations* between entities.</span></span>  
  
 <span data-ttu-id="8ef5f-131">연결에는 항상 테이블의 필드나 열을 각각 가리키는 두 개의 끝이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-131">Associations always have exactly two ends, each pointing to a field or column in a table.</span></span> <span data-ttu-id="8ef5f-132">따라서 관계의 끝점이 다를 경우 두 테이블 사이의 관계가 여러 가지일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-132">Therefore, multiple relationships are possible between two tables, if the relationships have different end points.</span></span> <span data-ttu-id="8ef5f-133">역할 이름이 연결의 끝점에 지정되고, 데이터 모델의 컨텍스트에서 연결이 사용되는 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-133">A role name is assigned to the end points of the association, and indicates how the association is used in the context of the data model.</span></span> <span data-ttu-id="8ef5f-134">역할 이름의 예는 Orders 테이블의 고객 ID와 관련 된 고객 ID에 적용 되는 경우 **ShipTo**수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-134">An example of a role name might be **ShipTo**, when applied to a customer ID that is related to the customer ID in an Orders table.</span></span>  
  
 <span data-ttu-id="8ef5f-135">모델의 CSDLBI 표현에는 연결의 *복합성* 을 기준으로 엔터티가 서로 매핑되는 방법을 결정 하는 연결 특성도 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-135">The CSDLBI representation of the model also contains attributes on the association that determine how the entities are mapped to each other in terms of the *multiplicity* of the association.</span></span> <span data-ttu-id="8ef5f-136">복합성은 테이블 간 관계 끝점의 특성이나 열이 관계의 한 편에 있는지 아니면 여러 편에 있는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-136">Multiplicity indicates whether the attribute or column at the end point of a relationship between tables is on the one side of a relationship, or on the many side.</span></span> <span data-ttu-id="8ef5f-137">일 대 일 관계에 대한 별도의 값은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-137">There is no separate value for one-to-one relationships.</span></span> <span data-ttu-id="8ef5f-138">CSDLBI 주석은 복합성 0(엔터티가 어디에도 연결되지 않음)이나 0..1(일 대 일 관계 또는 일 대 다 관계)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-138">CSDLBI annotations support multiplicity of 0 (meaning the entity is not associated with anything) or 0..1, which means either a one-one relationship or a one-to-many relationship.</span></span>  
  
 <span data-ttu-id="8ef5f-139">다음 예제에서는 DateAlternateKey 열에서 조인된 Date 테이블과 ProductInventory 테이블 간 관계에 대한 CSDLBI 출력을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-139">The following sample represents the CSDLBI output for a relationship between the tables, Date and ProductInventory, where the two tables are joined on the column DateAlternateKey.</span></span> <span data-ttu-id="8ef5f-140">기본적으로 `AssociationSet`의 이름은 관계에 포함된 열의 정규화된 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-140">Notice that, by default, the name of the `AssociationSet` is the fully qualified name of the columns that are involved in the relationship.</span></span> <span data-ttu-id="8ef5f-141">그러나 모델을 설계할 때 다른 이름 형식을 사용하도록 이 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-141">However, you can change this behavior when you design the model, to use a different naming format.</span></span>  
  
```  
<AssociationSet Name="ProductInventory_Date_DateKey" Association="Model.ProductInventory_Date_DateKey">  
              <End EntitySet="ProductInventory" />  
              <End EntitySet="Date" />  
              <bi:AssociationSet />  
            </AssociationSet>  
  
```  
  
### <a name="visualization-and-navigation-properties"></a><span data-ttu-id="8ef5f-142">시각화 및 탐색 속성</span><span class="sxs-lookup"><span data-stu-id="8ef5f-142">Visualization and Navigation Properties</span></span>  
 <span data-ttu-id="8ef5f-143">CSDLBI 주석의 중요한 부분은 보고 계층에서 프레젠테이션을 정의하고 엔터티 간의 관계를 탐색하기 위한 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-143">An important part of the CSDLBI annotations are the properties for defining presentation in the reporting layer, and for navigating the relationships among entities.</span></span> <span data-ttu-id="8ef5f-144">대개 데이터 모델을 만들 때는 클라이언트 애플리케이션이 표시 순서와 그 밖의 세부 정보를 지정한다고 간주하므로 데이터 순서 지정 및 그룹화 방법 제어나 기본값 지정을 중요하게 여기지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-144">Typically, when you are creating a data model, you do not consider it important to control how the data is ordered or grouped, or what the default value might be, on the assumption that the client application will specify ordering and other details of presentation.</span></span> <span data-ttu-id="8ef5f-145">그러나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 테이블 형식 모델은 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 보고 클라이언트와의 통합을 위해 디자인되었으며 보고서 디자인 화면에서 데이터 모델의 엔터티를 표시하도록 지원하는 속성과 특성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-145">However, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular models are designed for integration with the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reporting client, and includes properties and attributes that support presentation of entities from the data model in the report design surface.</span></span>  
  
 <span data-ttu-id="8ef5f-146">시각화를 위한 확장에는 숫자 데이터와 함께 사용할 기본 집계를 지정하거나, 텍스트 필드가 이미지 URL을 가리키도록 지시하거나, 현재 필드를 정렬하는 데 사용되는 필드를 지정하기 위한 특성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-146">Extensions for visualization include attributes for specifying the default aggregation to use with numerical data, for indicating that a text field points to a URL of an image, or specifying the field used to sort the current field.</span></span>  
  
### <a name="name-properties-and-naming-conventions"></a><span data-ttu-id="8ef5f-147">이름 속성 및 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="8ef5f-147">Name Properties and Naming Conventions</span></span>  
 <span data-ttu-id="8ef5f-148">CSDLBI 스키마는 키로 사용할 수 있는 고유 이름과 식별자를 각 엔터티에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-148">The CSDLBI schema provides that each entity has a unique name and an identifier that can be used as a key.</span></span> <span data-ttu-id="8ef5f-149">또한 일부 엔터티는 표시용으로 사용되는 캡션과 엔터티가 사용되는 위치에 따라 달라지는 컨텍스트 이름을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-149">In addition, some entities can have captions used for display purposes, and contextual names that change depending on where the entity is used.</span></span>  
  
 <span data-ttu-id="8ef5f-150">`Documentation` 요소는 보고서 디자이너가 엔터티를 설명할 기회를 제공하여 비즈니스 사용자가 데이터의 의미를 이해하도록 돕습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-150">The `Documentation` element provides the opportunity for report designers to furnish a description of the entity, to help business users understand the meaning of the data.</span></span> <span data-ttu-id="8ef5f-151">일부 엔터티는 애플리케이션이나 클라이언트에서 사용할 추가 메타데이터를 제공하는 `Annotation` 특성을 한 개 이상 허용하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-151">Some entities also allow one or more `Annotation` attributes, which provide extra metadata for consumption by the application or by clients.</span></span>  
  
 <span data-ttu-id="8ef5f-152">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 도구로 모델을 생성하는 경우 개체를 위해 만든 이름은 개체 이름 지정과 이름의 고유성을 위해 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-152">When you generate a model the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tools, the names that are created for objects follow the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] conventions for object naming and name uniqueness.</span></span> <span data-ttu-id="8ef5f-153">그러나 CSDLBI는 C# 식별자에 대한 명명 규칙을 준수해야 하는 EDF(엔터티 데이터 프레임워크)를 기반으로 하기 때문에 서버에서 모델의 CSDLBI 출력을 만들 때 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 스키마에서 사용하는 이름을 가져와서 EDF 요구 사항에 맞는 새 개체 이름을 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-153">However, because CSDLBI is based on the Entity Data Framework (EDF), which requires that names adhere to conventions for C# identifiers, when the server creates the CSDLBI output for a model, the server takes the names used within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] schema and automatically creates new object names that comply with EDF requirements.</span></span> <span data-ttu-id="8ef5f-154">다음 표에서는 새 이름을 생성하기 위한 작업에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-154">The following table describes the operations by which the new names are generated.</span></span>  
  
|<span data-ttu-id="8ef5f-155">규칙</span><span class="sxs-lookup"><span data-stu-id="8ef5f-155">Rule</span></span>|<span data-ttu-id="8ef5f-156">작업</span><span class="sxs-lookup"><span data-stu-id="8ef5f-156">Action</span></span>|  
|----------|------------|  
|<span data-ttu-id="8ef5f-157">금지된 문자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-157">No forbidden characters</span></span>|<span data-ttu-id="8ef5f-158">금지된 문자는 밑줄로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-158">Forbidden characters are replaced by underscore.</span></span>|  
|<span data-ttu-id="8ef5f-159">이름은 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-159">Names must be unique</span></span>|<span data-ttu-id="8ef5f-160">두 문자열이 같으면 밑줄과 숫자를 추가하여 문자열 하나를 고유하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-160">If two strings are the same, one is made unique by appending underscore plus a number</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="8ef5f-161">캡션과 한정자는 번역되며 둘 중 하나는 지정한 언어로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-161">Captions and qualifiers both have translations, and for a given language, one or the other might be present.</span></span> <span data-ttu-id="8ef5f-162">즉, 한정자와 이름 또는 한정자와 캡션이 연결된 경우 문자열이 서로 다른 두 언어로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-162">This means that in cases where a qualifier and name or qualifier and caption are concatenated, the strings could be in two different languages.</span></span>  
  
## <a name="additions-to-support-multidimensional-models"></a><span data-ttu-id="8ef5f-163">다차원 모델을 지원하기 위한 추가 기능</span><span class="sxs-lookup"><span data-stu-id="8ef5f-163">Additions to Support Multidimensional Models</span></span>  
 <span data-ttu-id="8ef5f-164">CSDLBI 주석 버전 1.0은 테이블 형식의 모델만 지원했습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-164">Version 1.0 of the CSDLBI annotations supported only tabular models.</span></span> <span data-ttu-id="8ef5f-165">버전 1.1에서는 기존 BI 개발 도구를 사용하여 만든 다차원 모델(OLAP 큐브)에 대한 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-165">In version 1.1, support was added for multidimensional models (OLAP cubes) created using traditional BI development tools.</span></span> <span data-ttu-id="8ef5f-166">따라서 다차원 모델에 대한 XML 요청을 실행하여 보고에 사용할 모델의 CSDLBI 정의를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-166">Therefore, you can now issue an XML request to a multidimensional model and receive a CSDLBI definition of the model, for use in reporting.</span></span>  
  
 <span data-ttu-id="8ef5f-167">**큐브:** SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 테이블 형식 데이터베이스에는 모드를 하나만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-167">**Cubes:** A SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tabular database can contain only one mode.</span></span> <span data-ttu-id="8ef5f-168">반면에 각 다차원 데이터베이스에는 여러 개의 큐브가 포함될 수 있으며 각 데이터베이스는 기본 큐브와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-168">In contrast, each multidimensional database can contain multiple cubes, each database being associated with a default cube.</span></span> <span data-ttu-id="8ef5f-169">따라서 다차원 서버에 대해 XML 요청을 실행할 때는 큐브를 지정해야 하며, 그러지 않으면 기본 큐브에 대한 XML이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-169">Therefore, when issuing an XML request against a multidimensional server, it is necessary to specify the cube; otherwise, the XML for the default cube will be returned.</span></span>  
  
 <span data-ttu-id="8ef5f-170">그 점을 제외하면 큐브 표현은 테이블 형식의 모델 데이터베이스와 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-170">The representation of a cube is otherwise very much like that of a tabular model database.</span></span> <span data-ttu-id="8ef5f-171">큐브 이름과 큐브는 테이블 형식 데이터베이스와 데이터베이스 ID에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-171">The cube name and cube correspond to the tabular database name and database identifier.</span></span>  
  
 <span data-ttu-id="8ef5f-172">**차원:** 차원은 CSDLBI에서 열 및 속성이 있는 엔터티 (테이블)로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-172">**Dimensions:** A dimension is represented in CSDLBI as an entity (table) with columns and properties.</span></span> <span data-ttu-id="8ef5f-173">큐브 뷰에 포함되지 않았더라도 모델에는 포함되어 있는 차원은 CSDL 출력에 `Hidden`으로 표시되어 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-173">Note that even if not included in a perspective, a dimension that is included in the model will be represented in the CSDL output, marked as `Hidden`.</span></span>  
  
 <span data-ttu-id="8ef5f-174">**큐브 뷰:** 클라이언트는 개별 큐브 뷰에 대해 CSDL을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-174">**Perspectives:** A client can request CSDL for individual perspectives.</span></span> <span data-ttu-id="8ef5f-175">자세한 내용은 [DISCOVER_CSDL_METADATA 행 집합](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-175">For more information, see [DISCOVER_CSDL_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset).</span></span>  
  
 <span data-ttu-id="8ef5f-176">**계층:** 계층은 CSDLBI에서 수준 집합으로 지원 되 고 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-176">**Hierarchies:** Hierarchies are supported and represented in CSDLBI as a set of levels.</span></span>  
  
 <span data-ttu-id="8ef5f-177">**멤버:** 기본 멤버에 대 한 지원이 추가 되었으며 기본값은 CSDLBI 출력에 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-177">**Members:** Support for the default member has been added and default values are automatically added to the CSDLBI output.</span></span>  
  
 <span data-ttu-id="8ef5f-178">**계산 멤버:** 다차원 모델은 단일 실제 멤버가 있는 **모든** 자식에 대해 계산 멤버를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-178">**Calculated Members:** Multidimensional models support calculated members for child of **All** with a single real member.</span></span>  
  
 <span data-ttu-id="8ef5f-179">**차원 특성:** CSDLBI output에서 차원 특성은 지원 되며 집계할 수 없는 것으로 자동으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-179">**Dimension attributes:** In CSDLBI output, dimension attributes are supported and automatically marked as non-aggregatable.</span></span>  
  
 <span data-ttu-id="8ef5f-180">**Kpi:** Kpi가 CSDLBI 버전 1.1에서 지원 되었지만 표현이 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-180">**KPIs:** KPIs were supported in CSDLBI version 1.1, but the representation has changed.</span></span> <span data-ttu-id="8ef5f-181">예전에는 KPI가 측정값의 속성이었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-181">Before, a KPI was a property of a measure.</span></span> <span data-ttu-id="8ef5f-182">버전 1.1에서는 KPI 요소를 측정값에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-182">In version 1.1, the KPI element can be added to a measure</span></span>  
  
 <span data-ttu-id="8ef5f-183">**새 속성:** DirectQuery 모델을 지원 하기 위해 추가 특성이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-183">**New properties:** Additional attributes were added to support DirectQuery models.</span></span>  
  
 <span data-ttu-id="8ef5f-184">**제한 사항:** 셀 보안은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ef5f-184">**Limitations:** Cell security is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef5f-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ef5f-185">See Also</span></span>  
 [<span data-ttu-id="8ef5f-186">비즈니스 인텔리전스에 대한 CSDL 주석&#40;CSDLBI&#41;</span><span class="sxs-lookup"><span data-stu-id="8ef5f-186">CSDL Annotations for Business Intelligence &#40;CSDLBI&#41;</span></span>](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
  
