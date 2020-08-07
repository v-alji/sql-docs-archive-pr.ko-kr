---
title: 내장 멤버 속성 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- intrinsic member properties [MDX]
ms.assetid: 84e6fe64-9b37-4e79-bedf-ae02e80bfce8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 268203d044734bb4e6a1d2acf6311ee7ef828a53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730963"
---
# <a name="intrinsic-member-properties-mdx"></a><span data-ttu-id="79e6b-102">기본 멤버 속성(MDX)</span><span class="sxs-lookup"><span data-stu-id="79e6b-102">Intrinsic Member Properties (MDX)</span></span>
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="79e6b-103">에서는 차원 멤버의 기본 속성을 표시합니다. 이러한 기본 속성을 쿼리에 포함하면 사용자 지정 애플리케이션에 사용할 추가 데이터 또는 메타데이터를 반환하거나 모델을 간편하게 검토 또는 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-103">exposes intrinsic properties on dimension members that you can include in a query to return additional data or metadata for use in a custom application, or to assist in model investigation or construction.</span></span> <span data-ttu-id="79e6b-104">SQL Server 클라이언트 도구를 사용하는 경우 SSMS(SQL Server Management Studio)에서 기본 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-104">If you are using the SQL Server client tools, you can view intrinsic properties in SQL Server Management Studio (SSMS).</span></span>  
  
 <span data-ttu-id="79e6b-105">기본 속성으로는 모든 멤버가 모든 수준에서 표시하는 `ID`, `KEY`, `KEYx` 및 `NAME`이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-105">Intrinsic properties include `ID`, `KEY`, `KEYx`, and `NAME`, which are properties exposed by every member, at any level.</span></span> <span data-ttu-id="79e6b-106">특히 `LEVEL_NUMBER` 또는 `PARENT_UNIQUE_NAME`과 같은 위치 정보를 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-106">You can also return positional information, such as `LEVEL_NUMBER` or `PARENT_UNIQUE_NAME`, among others.</span></span>  
  
 <span data-ttu-id="79e6b-107">쿼리 작성 방법 및 쿼리 실행에 사용하는 클라이언트 애플리케이션에 따라 결과 집합에 멤버 속성이 표시될 수도 있고 그렇지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-107">Depending on how you construct the query, and on the client application you are using to execute queries, member properties may or may not be visible in the result set.</span></span> <span data-ttu-id="79e6b-108">쿼리 테스트 또는 실행에 SQL Server Management Studio를 사용하는 경우 결과 집합에서 멤버를 두 번 클릭하여 각 멤버의 기본 속성 값이 표시된 멤버 속성 대화 상자를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-108">If you are using SQL Server Management Studio to test or run queries, you can double-click a member in the result set to open the Member Properties dialog box, showing the values for each intrinsic member property.</span></span>  
  
 <span data-ttu-id="79e6b-109">차원 멤버 속성을 사용하고 보는 방법에 대한 개요를 보려면 [SSMS에서 MDX 쿼리 창에서 SSAS 멤버 속성 보기](https://go.microsoft.com/fwlink/?LinkId=317362)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="79e6b-109">For an introduction to using and viewing dimension member properties, see [Viewing SSAS Member Properties within an MDX Query Window in SSMS](https://go.microsoft.com/fwlink/?LinkId=317362).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79e6b-110">1999 년 3 월 (2.6)에 설명 된 OLE DB 사양의 OLAP 섹션을 준수 하는 공급자는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 이 항목에 나열 된 기본 멤버 속성을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-110">As a provider that is compliant with the OLAP section of the OLE DB specification dated March 1999 (2.6), [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supports the intrinsic member properties listed in this topic.</span></span>  
>   
>  <span data-ttu-id="79e6b-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 이외의 공급자가 기본 멤버 속성을 추가로 지원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-111">Providers other than [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] may support additional intrinsic member properties.</span></span> <span data-ttu-id="79e6b-112">다른 공급자가 지원하는 기본 멤버 속성에 대한 자세한 내용은 해당 공급자가 제공하는 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="79e6b-112">For more information about the intrinsic member properties supported by other providers, refer to the documentation that comes with those providers.</span></span>  
  
## <a name="types-of-member-properties"></a><span data-ttu-id="79e6b-113">멤버 속성의 유형</span><span class="sxs-lookup"><span data-stu-id="79e6b-113">Types of Member Properties</span></span>  
 <span data-ttu-id="79e6b-114">에서 지 원하는 기본 멤버 속성은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 다음 두 가지 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-114">The intrinsic member properties supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] are of two types:</span></span>  
  
 <span data-ttu-id="79e6b-115">상황에 맞는 멤버 속성</span><span class="sxs-lookup"><span data-stu-id="79e6b-115">Context sensitive member properties</span></span>  
 <span data-ttu-id="79e6b-116">이 유형의 멤버 속성은 특정 계층 또는 수준의 컨텍스트에서 사용해야 하고 지정한 차원 또는 수준의 각 멤버에 대한 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-116">These member properties must be used in the context of a specific hierarchy or level, and supply values for each member of the specified dimension or level.</span></span>  
  
 <span data-ttu-id="79e6b-117">다음 예를 보면 `KEY` 속성의 경로가 포함되어 있습니다. `MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`</span><span class="sxs-lookup"><span data-stu-id="79e6b-117">Notice how the following example includes the path for the `KEY` property: `MEMBER [Measures].[Parent Member Key] AS [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")`.</span></span>  
  
 <span data-ttu-id="79e6b-118">상황에 맞지 않는 멤버 속성</span><span class="sxs-lookup"><span data-stu-id="79e6b-118">Non-context sensitive member properties</span></span>  
 <span data-ttu-id="79e6b-119">이 유형의 멤버 속성은 특정 차원 또는 수준의 컨텍스트에서 사용할 수 없고 한 축의 모든 멤버에 대한 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-119">These member properties cannot be used in the context of a specific dimension or level, and return values for all members on an axis.</span></span>  
  
 <span data-ttu-id="79e6b-120">상황에 맞지 않는 속성은 독립적이며 경로 정보를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-120">Context-insensitive properties standalone and do not include path information.</span></span> <span data-ttu-id="79e6b-121">다음 예에서는 `PARENT_UNIQUE_NAME`에 대해 차원이나 수준이 지정되어 있지 않습니다. `DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`</span><span class="sxs-lookup"><span data-stu-id="79e6b-121">Notice how there is no dimension or level specified for `PARENT_UNIQUE_NAME` in the following example: `DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS`</span></span>  
  
 <span data-ttu-id="79e6b-122">기본 멤버 속성이 상황에 맞든 맞지 않든 상관없이 다음의 사용 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-122">Regardless of whether the intrinsic member property is context sensitive or not, the following usage rules apply:</span></span>  
  
-   <span data-ttu-id="79e6b-123">축에 표시되는 차원 멤버와 관련된 기본 멤버 속성만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-123">You can specify only those intrinsic member properties that relate to dimension members that are projected on the axis.</span></span>  
  
-   <span data-ttu-id="79e6b-124">상황에 맞지 않는 기본 멤버 속성을 가진 같은 쿼리에서 상황에 맞는 멤버 속성에 대한 요청을 혼합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-124">You can mix requests for context sensitive member properties in the same query with non-context sensitive intrinsic member properties.</span></span>  
  
-   <span data-ttu-id="79e6b-125">`PROPERTIES` 키워드를 사용하여 속성에 대해 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-125">You use the `PROPERTIES` keyword to query for the properties.</span></span>  
  
 <span data-ttu-id="79e6b-126">다음 섹션에서는에서 사용할 수 있는 다양 한 상황에 맞는 기본 멤버 속성과 상황에 맞지 않는 기본 멤버 속성을 모두 설명 하 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 고 `PROPERTIES` 각 속성 형식에 키워드를 사용 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-126">The following sections describe both the various context sensitive and non-context sensitive intrinsic member properties available in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], and how to use the `PROPERTIES` keyword with each type of property.</span></span>  
  
## <a name="context-sensitive-member-properties"></a><span data-ttu-id="79e6b-127">상황에 맞는 멤버 속성</span><span class="sxs-lookup"><span data-stu-id="79e6b-127">Context Sensitive Member Properties</span></span>  
 <span data-ttu-id="79e6b-128">모든 차원 멤버와 수준 멤버는 상황에 맞는 기본 멤버 속성 목록을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-128">All dimension members and level members support a list of intrinsic member properties that are context sensitive.</span></span> <span data-ttu-id="79e6b-129">다음 표에서는 이러한 상황에 맞는 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-129">The following table lists these context-sensitive properties.</span></span>  
  
|<span data-ttu-id="79e6b-130">속성</span><span class="sxs-lookup"><span data-stu-id="79e6b-130">Property</span></span>|<span data-ttu-id="79e6b-131">설명</span><span class="sxs-lookup"><span data-stu-id="79e6b-131">Description</span></span>|  
|--------------|-----------------|  
|`ID`|<span data-ttu-id="79e6b-132">내부적으로 유지 관리되는 멤버 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-132">The internally maintained ID for the member.</span></span>|  
|`Key`|<span data-ttu-id="79e6b-133">원본 데이터 형식에서 멤버 키의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-133">The value of the member key in the original data type.</span></span> <span data-ttu-id="79e6b-134">MEMBER_KEY는 이전 버전과의 호환성을 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-134">MEMBER_KEY is for backward-compatibility.</span></span>  <span data-ttu-id="79e6b-135">비복합 키의 경우 MEMBER_KEY 값이 KEY0과 동일하고 복합 키의 경우 MEMBER_KEY 속성이 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-135">MEMBER_KEY has the same value as KEY0 for non-composite keys, and MEMBER_KEY property is null for composite keys.</span></span>|  
|`KEYx`|<span data-ttu-id="79e6b-136">멤버에 대한 키이며 x는 키의 서수 값(0부터 시작)입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-136">The key for the member, where x is the zero-based ordinal of the key.</span></span> <span data-ttu-id="79e6b-137">KEY0은 복합 키와 비복합 키에 모두 사용할 수 있지만 주로 복합 키에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-137">KEY0 is available for composite and non-composite keys, but primarily used for composite keys.</span></span><br /><br /> <span data-ttu-id="79e6b-138">KEY0, KEY1, KEY2 등이 모여 복합 키가 형성됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-138">For composite keys, KEY0, KEY1, KEY2, and so on, collectively form the composite key.</span></span> <span data-ttu-id="79e6b-139">쿼리에서 각 키를 사용하여 복합 키의 해당 부분을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-139">You can use each one independently in a query to return that portion of the composite key.</span></span> <span data-ttu-id="79e6b-140">예를 들어 KEY0을 지정하면 복합 키의 첫 번째 부분이 반환되고 KEY1을 지정하면 복합 키의 다음 부분이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-140">For example, specifying KEY0 returns the first part of the composite key, specifying KEY1 returns the next part of the composite key, and so on.</span></span><br /><br /> <span data-ttu-id="79e6b-141">복합 키가 아닌 경우 KEY0은 `Key`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-141">If the key is non-composite, then KEY0 is equivalent to `Key`.</span></span><br /><br /> <span data-ttu-id="79e6b-142">`KEYx`는 컨텍스트 내에서는 물론 컨텍스트 없이도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-142">Note that `KEYx` can be used in context as well as without context.</span></span> <span data-ttu-id="79e6b-143">이러한 이유로 이 키는 두 목록에 모두 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-143">For this reason, it appears in both lists.</span></span><br /><br /> <span data-ttu-id="79e6b-144">이 멤버 속성을 사용하는 방법에 대한 예는 [간단한 MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79e6b-144">For an example of how to use this member property, see [A Simple MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364).</span></span>|  
|`Name`|<span data-ttu-id="79e6b-145">멤버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-145">The name of the member.</span></span>|  
  
### <a name="properties-syntax-for-context-sensitive-properties"></a><span data-ttu-id="79e6b-146">상황에 맞는 속성에 대한 PROPERTIES 구문</span><span class="sxs-lookup"><span data-stu-id="79e6b-146">PROPERTIES Syntax for Context Sensitive Properties</span></span>  
 <span data-ttu-id="79e6b-147">특정 차원 또는 수준의 컨텍스트에서 이 멤버 속성을 사용하고 지정한 차원 또는 수준의 각 멤버에 대한 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-147">You use these member properties in the context of a specific dimension or level, and supply values for each member of the specified dimension or level.</span></span>  
  
 <span data-ttu-id="79e6b-148">차원 멤버 속성의 경우 속성 이름 앞에 해당 속성이 적용되는 차원 이름을 둡니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-148">For dimension member properties, you precede the name of the property with the name of the dimension to which the property applies.</span></span> <span data-ttu-id="79e6b-149">다음 예에서는 적합한 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-149">The following example shows the appropriate syntax:</span></span>  
  
 `DIMENSION PROPERTIES Dimension.Property_name`  
  
 <span data-ttu-id="79e6b-150">수준 멤버 속성의 경우 속성 이름 앞에 단순히 수준 이름만 두거나 추가 지정을 위해 차원 이름과 수준 이름을 앞에 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-150">For a level member property, you can precede the name of the property with just the level name or, for additional specification, both the dimension and level name.</span></span> <span data-ttu-id="79e6b-151">다음 예에서는 적합한 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-151">The following example shows the appropriate syntax:</span></span>  
  
 `DIMENSION PROPERTIES [Dimension.]Level.Property_name`  
  
 <span data-ttu-id="79e6b-152">이를 보여 주기 위해 `[Sales]` 차원에서 참조된 각 멤버의 이름을 모두 반환할 수도 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-152">To illustrate, you would like to return all the names of each referenced member in the `[Sales]` dimension.</span></span> <span data-ttu-id="79e6b-153">이러한 이름을 반환하려면 MDX 쿼리에 다음과 같은 문을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-153">To return these names, you would use the following statement in a Multidimensional Expressions (MDX) query:</span></span>  
  
 `DIMENSION PROPERTIES [Sales].Name`  
  
## <a name="non-context-sensitive-member-properties"></a><span data-ttu-id="79e6b-154">상황에 맞지 않는 멤버 속성</span><span class="sxs-lookup"><span data-stu-id="79e6b-154">Non-Context Sensitive Member Properties</span></span>  
 <span data-ttu-id="79e6b-155">모든 멤버가 컨텍스트에 상관없이 동일한 기본 멤버 속성 목록을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-155">All members support a list of intrinsic member properties that are the same regardless of context.</span></span> <span data-ttu-id="79e6b-156">이러한 속성들은 사용자에게 보다 나은 경험을 주기 위해 애플리케이션에서 사용할 수 있는 정보를 추가로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-156">These properties provide additional information that can be used by applications to enhance the user's experience.</span></span>  
  
 <span data-ttu-id="79e6b-157">다음 표에서는에서 지 원하는 상황에 맞지 않는 기본 속성을 보여 줍니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="79e6b-157">The following table lists the non-context sensitive intrinsic properties supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79e6b-158">MEMBERS 스키마 행 집합의 열은 다음 표에 나열된 기본 멤버 속성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-158">Columns in the MEMBERS schema rowset support the intrinsic member properties listed in the following table.</span></span> <span data-ttu-id="79e6b-159">스키마 행 집합에 대 한 자세한 내용은 `MEMBERS` [MDSCHEMA_MEMBERS 행 집합](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79e6b-159">For more information about the `MEMBERS` schema rowset, see [MDSCHEMA_MEMBERS Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-members-rowset).</span></span>  
  
|<span data-ttu-id="79e6b-160">속성</span><span class="sxs-lookup"><span data-stu-id="79e6b-160">Property</span></span>|<span data-ttu-id="79e6b-161">설명</span><span class="sxs-lookup"><span data-stu-id="79e6b-161">Description</span></span>|  
|--------------|-----------------|  
|`CATALOG_NAME`|<span data-ttu-id="79e6b-162">이 멤버가 속한 큐브 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-162">The name of the cube to which this member belongs.</span></span>|  
|`CHILDREN_CARDINALITY`|<span data-ttu-id="79e6b-163">멤버의 자식 수입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-163">The number of children that the member has.</span></span> <span data-ttu-id="79e6b-164">예상치일 수 있으므로 이 값을 정확한 수로 간주하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-164">This can be an estimate, so you should not rely on this to be the exact count.</span></span> <span data-ttu-id="79e6b-165">공급자는 가능한 한 최적의 예상치를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-165">Providers should return the best estimate possible.</span></span>|  
|`CUSTOM_ROLLUP`|<span data-ttu-id="79e6b-166">사용자 지정 멤버 식입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-166">The custom member expression.</span></span>|  
|`CUSTOM_ROLLUP_PROPERTIES`|<span data-ttu-id="79e6b-167">사용자 지정 멤버 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-167">The custom member properties.</span></span>|  
|`DESCRIPTION`|<span data-ttu-id="79e6b-168">사람이 읽을 수 있는 멤버 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-168">A human-readable description of the member.</span></span>|  
|`DIMENSION_UNIQUE_NAME`|<span data-ttu-id="79e6b-169">이 멤버가 속한 차원의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-169">The unique name of the dimension to which this member belongs.</span></span> <span data-ttu-id="79e6b-170">자격에 따라 고유한 이름을 생성하는 공급자의 경우 이 이름의 각 구성 요소는 구분 기호로 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-170">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`HIERARCHY_UNIQUE_NAME`|<span data-ttu-id="79e6b-171">계층의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-171">The unique name of the hierarchy.</span></span> <span data-ttu-id="79e6b-172">멤버가 둘 이상의 계층에 속한 경우 멤버가 속한 각 계층마다 하나의 행이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-172">If the member belongs to more than one hierarchy, there is one row for each hierarchy to which the member belongs.</span></span> <span data-ttu-id="79e6b-173">자격에 따라 고유한 이름을 생성하는 공급자의 경우 이 이름의 각 구성 요소는 구분 기호로 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-173">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`IS_DATAMEMBER`|<span data-ttu-id="79e6b-174">멤버가 데이터 멤버인지 여부를 나타내는 부울입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-174">A Boolean that indicates whether the member is a data member.</span></span>|  
|`IS_PLACEHOLDERMEMBER`|<span data-ttu-id="79e6b-175">멤버가 자리 표시자인지 여부를 나타내는 부울입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-175">A Boolean that indicates whether the member is a placeholder.</span></span>|  
|`KEYx`|<span data-ttu-id="79e6b-176">멤버에 대한 키이며 x는 키의 서수 값(0부터 시작)입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-176">The key for the member, where x is the zero-based ordinal of the key.</span></span> <span data-ttu-id="79e6b-177">KEY0은 복합 키와 비복합 키에 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-177">KEY0 is available for composite and non-composite keys.</span></span><br /><br /> <span data-ttu-id="79e6b-178">복합 키가 아닌 경우 KEY0은 `Key`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-178">If the key is non-composite, then KEY0 is equivalent to `Key`.</span></span><br /><br /> <span data-ttu-id="79e6b-179">KEY0, KEY1, KEY2 등이 모여 복합 키가 형성됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-179">For composite keys, KEY0, KEY1, KEY2, and so on, collectively form the composite key.</span></span> <span data-ttu-id="79e6b-180">쿼리에서 각 키를 참조하여 복합 키의 해당 부분을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-180">You can reference each one independently in a query to return that portion of the composite key.</span></span> <span data-ttu-id="79e6b-181">예를 들어 KEY0을 지정하면 복합 키의 첫 번째 부분이 반환되고 KEY1을 지정하면 복합 키의 다음 부분이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-181">For example, specifying KEY0 returns the first part of the composite key, specifying KEY1 returns the next part of the composite key, and so on.</span></span><br /><br /> <span data-ttu-id="79e6b-182">`KEYx`는 컨텍스트 내에서는 물론 컨텍스트 없이도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-182">Note that `KEYx` can be used in context as well as without context.</span></span> <span data-ttu-id="79e6b-183">이러한 이유로 이 키는 두 목록에 모두 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-183">For this reason, it appears in both lists.</span></span><br /><br /> <span data-ttu-id="79e6b-184">이 멤버 속성을 사용하는 방법에 대한 예는 [간단한 MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79e6b-184">For an example of how to use this member property, see [A Simple MDX Tidbit: Key0, Key1, Key2](https://go.microsoft.com/fwlink/?LinkId=317364).</span></span>|  
|<span data-ttu-id="79e6b-185">`LCID` *x*</span><span class="sxs-lookup"><span data-stu-id="79e6b-185">`LCID` *x*</span></span>|<span data-ttu-id="79e6b-186">로캘 ID 16진수 값으로 멤버 캡션을 변환한 값이며 *x* 는 로캘 ID 10진수 값(예: 영어-캐나다의 경우 LCID1009)입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-186">The translation of the member caption in the locale ID hexadecimal value, where *x* is the locale ID decimal value (for example, LCID1009 as English-Canada).</span></span> <span data-ttu-id="79e6b-187">데이터 원본에 바인딩된 캡션 열이 변환에 있는 경우에만 이 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-187">This is only available if the translation has the caption column bound to the data source.</span></span>|  
|`LEVEL_NUMBER`|<span data-ttu-id="79e6b-188">계층 루트에서 멤버까지의 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-188">The distance of the member from the root of the hierarchy.</span></span> <span data-ttu-id="79e6b-189">루트 수준은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-189">The root level is zero.</span></span>|  
|`LEVEL_UNIQUE_NAME`|<span data-ttu-id="79e6b-190">이 멤버가 속한 수준의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-190">The unique name of the level to which the member belongs.</span></span> <span data-ttu-id="79e6b-191">자격에 따라 고유한 이름을 생성하는 공급자의 경우 이 이름의 각 구성 요소는 구분 기호로 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-191">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`MEMBER_CAPTION`|<span data-ttu-id="79e6b-192">멤버에 연결된 레이블 또는 캡션입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-192">A label or caption associated with the member.</span></span> <span data-ttu-id="79e6b-193">캡션은 주로 표시용으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-193">The caption is primarily for display purposes.</span></span> <span data-ttu-id="79e6b-194">캡션이 없는 경우 쿼리는 `MEMBER_NAME`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-194">If a caption does not exist, the query returns `MEMBER_NAME`.</span></span>|  
|`MEMBER_KEY`|<span data-ttu-id="79e6b-195">원본 데이터 형식에서 멤버 키의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-195">The value of the member key in the original data type.</span></span> <span data-ttu-id="79e6b-196">MEMBER_KEY는 이전 버전과의 호환성을 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-196">MEMBER_KEY is for backward-compatibility.</span></span>  <span data-ttu-id="79e6b-197">비복합 키의 경우 MEMBER_KEY 값이 KEY0과 동일하고 복합 키의 경우 MEMBER_KEY 속성이 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-197">MEMBER_KEY has the same value as KEY0 for non-composite keys, and MEMBER_KEY property is null for composite keys.</span></span>|  
|`MEMBER_NAME`|<span data-ttu-id="79e6b-198">멤버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-198">The name of the member.</span></span>|  
|`MEMBER_TYPE`|<span data-ttu-id="79e6b-199">멤버의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-199">The type of the member.</span></span> <span data-ttu-id="79e6b-200">이 속성 값은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-200">This property can have one of the following values:</span></span> <br /><span data-ttu-id="79e6b-201">**MDMEMBER_TYPE_REGULAR**</span><span class="sxs-lookup"><span data-stu-id="79e6b-201">**MDMEMBER_TYPE_REGULAR**</span></span><br /><span data-ttu-id="79e6b-202">**MDMEMBER_TYPE_ALL**</span><span class="sxs-lookup"><span data-stu-id="79e6b-202">**MDMEMBER_TYPE_ALL**</span></span><br /><span data-ttu-id="79e6b-203">**MDMEMBER_TYPE_FORMULA**</span><span class="sxs-lookup"><span data-stu-id="79e6b-203">**MDMEMBER_TYPE_FORMULA**</span></span><br /><span data-ttu-id="79e6b-204">**MDMEMBER_TYPE_MEASURE**</span><span class="sxs-lookup"><span data-stu-id="79e6b-204">**MDMEMBER_TYPE_MEASURE**</span></span><br /><span data-ttu-id="79e6b-205">**MDMEMBER_TYPE_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="79e6b-205">**MDMEMBER_TYPE_UNKNOWN**</span></span><br /><br /> <br /><br /> <span data-ttu-id="79e6b-206">MDMEMBER_TYPE_FORMULA가 MDMEMBER_TYPE_MEASURE보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-206">MDMEMBER_TYPE_FORMULA takes precedence over MDMEMBER_TYPE_MEASURE.</span></span> <span data-ttu-id="79e6b-207">따라서 Measures 차원에 수식(계산) 멤버가 있는 경우 계산 멤버에 대한 `MEMBER_TYPE` 속성은 MDMEMBER_TYPE_FORMULA입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-207">Therefore, if there is a formula (calculated) member on the Measures dimension, the `MEMBER_TYPE` property for the calculated member is MDMEMBER_TYPE_FORMULA.</span></span>|  
|`MEMBER_UNIQUE_NAME`|<span data-ttu-id="79e6b-208">멤버의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-208">The unique name of the member.</span></span> <span data-ttu-id="79e6b-209">자격에 따라 고유한 이름을 생성하는 공급자의 경우 이 이름의 각 구성 요소는 구분 기호로 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-209">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`MEMBER_VALUE`|<span data-ttu-id="79e6b-210">원본 형식으로 된 멤버의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-210">The value of the member in the original type.</span></span>|  
|`PARENT_COUNT`|<span data-ttu-id="79e6b-211">이 멤버에 있는 부모 수입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-211">The number of parents that this member has.</span></span>|  
|`PARENT_LEVEL`|<span data-ttu-id="79e6b-212">계층 루트 수준에서 멤버 부모까지의 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-212">The distance of the member's parent from the root level of the hierarchy.</span></span> <span data-ttu-id="79e6b-213">루트 수준은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-213">The root level is zero.</span></span>|  
|`PARENT_UNIQUE_NAME`|<span data-ttu-id="79e6b-214">멤버 부모의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-214">The unique name of the member's parent.</span></span> <span data-ttu-id="79e6b-215">루트 수준의 모든 멤버에 대해서 `NULL`이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-215">`NULL` is returned for any members at the root level.</span></span> <span data-ttu-id="79e6b-216">자격에 따라 고유한 이름을 생성하는 공급자의 경우 이 이름의 각 구성 요소는 구분 기호로 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-216">For providers that generate unique names by qualification, each component of this name is delimited.</span></span>|  
|`SKIPPED_LEVELS`|<span data-ttu-id="79e6b-217">멤버의 건너뛴 수준 수입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-217">The number of skipped levels for the member.</span></span>|  
|`UNARY_OPERATOR`|<span data-ttu-id="79e6b-218">멤버에 대한 단항 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-218">The unary operator for the member.</span></span>|  
|`UNIQUE_NAME`|<span data-ttu-id="79e6b-219">멤버의 정규화된 이름으로, [dimension].[level].[key6.] 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-219">The fully-qualified name of the member, in this format: [dimension].[level].[key6.]</span></span>|  
  
### <a name="properties-syntax-for-non-context-sensitive-properties"></a><span data-ttu-id="79e6b-220">상황에 맞지 않는 속성에 대한 PROPERTIES 구문</span><span class="sxs-lookup"><span data-stu-id="79e6b-220">PROPERTIES Syntax for Non-Context Sensitive Properties</span></span>  
 <span data-ttu-id="79e6b-221">다음 구문을 사용하여 `PROPERTIES` 키워드를 사용하는 상황에 맞지 않는 기본 멤버 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-221">Use the following syntax to specify an intrinsic, non-context sensitive member property using the `PROPERTIES` keyword:</span></span>  
  
 `DIMENSION PROPERTIES Property`  
  
 <span data-ttu-id="79e6b-222">이 구문에서는 차원이나 수준별로 속성을 정규화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-222">Notice that this syntax does not allow the property to be qualified by a dimension or level.</span></span> <span data-ttu-id="79e6b-223">상황에 맞지 않는 기본 멤버 속성이 축의 모든 멤버에 적용되므로 속성을 정규화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-223">The property cannot be qualified because an intrinsic member property that is not context sensitive applies to all members of an axis.</span></span>  
  
 <span data-ttu-id="79e6b-224">예를 들어 `DESCRIPTION` 기본 멤버 속성을 지정하는 MDX 문의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-224">For example, an MDX statement that specifies the `DESCRIPTION` intrinsic member property would have the following syntax:</span></span>  
  
 `DIMENSION PROPERTIES DESCRIPTION`  
  
 <span data-ttu-id="79e6b-225">이 문은 축 차원의 각 멤버에 대한 설명을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-225">This statement returns the description of each member in the axis dimension.</span></span> <span data-ttu-id="79e6b-226">차원 또는 수준 *에서와* 같이 차원이 나 수준으로 속성을 정규화 하 려 한 경우이 `.DESCRIPTION` *Level* `.DESCRIPTION` 문은 유효성을 검사 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-226">If you tried to qualify the property with a dimension or level, as in *Dimension*`.DESCRIPTION` or *Level*`.DESCRIPTION`, the statement would not validate.</span></span>  
  
### <a name="example"></a><span data-ttu-id="79e6b-227">예제</span><span class="sxs-lookup"><span data-stu-id="79e6b-227">Example</span></span>  
 <span data-ttu-id="79e6b-228">다음 예에서는 기본 속성을 반환하는 MDX 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-228">The following examples show MDX queries that return intrinsic properties.</span></span>  
  
 <span data-ttu-id="79e6b-229">**예제 1: 쿼리에서 상황에 맞는 기본 속성 사용**</span><span class="sxs-lookup"><span data-stu-id="79e6b-229">**Example 1: Use context-sensitive intrinsic properties in query**</span></span>  
  
 <span data-ttu-id="79e6b-230">다음 예에서는 각 제품 범주의 부모 ID, 키 및 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-230">The following example returns parent ID, key, and name for each product category.</span></span> <span data-ttu-id="79e6b-231">속성이 측정값으로 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-231">Notice how the properties are exposed as measures.</span></span> <span data-ttu-id="79e6b-232">따라서 SSMS의 멤버 속성 대화 상자 대신 쿼리를 실행할 때 셀 집합에서 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-232">This lets you view the properties in a cellset when you run the query, rather than the Member Properties dialog in SSMS.</span></span> <span data-ttu-id="79e6b-233">다음과 같은 쿼리를 실행하여 이미 배포된 큐브에서 멤버 메타데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-233">You might run a query like this to retrieve member metadata from a cube that is already deployed.</span></span>  
  
```  
WITH  
MEMBER [Measures].[Parent Member ID] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("ID")  
MEMBER [Measures].[Parent Member Key] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("KEY")  
MEMBER [Measures].[Parent Member Name] AS  
 [Product].[Product Categories].CurrentMember.Parent.PROPERTIES("Name")  
SELECT  
 {[Measures].[Parent Member ID], [Measures].[Parent Member Key], [Measures].[Parent Member Name] } on COLUMNS,   
 [Product].[Product Categories].AllMembers on ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="79e6b-234">**예제 2: 상황에 맞지 않는 기본 속성**</span><span class="sxs-lookup"><span data-stu-id="79e6b-234">**Example 2: Non-context-sensitive intrinsic properties**</span></span>  
  
 <span data-ttu-id="79e6b-235">다음 예는 상황에 맞지 않는 기본 속성의 전체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-235">The following example is the full list of non-context-sensitive intrinsic properties.</span></span> <span data-ttu-id="79e6b-236">SSMS에서 쿼리를 실행한 후 개별 멤버를 클릭하여 멤버 속성 대화 상자에서 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-236">After running the query in SSMS, click individual members to view properties in the Member Properties dialog box.</span></span>  
  
```  
SELECT [Measures].[Sales Amount Quota] on COLUMNS,  
[Employee].[Employees].members  
DIMENSION PROPERTIES  
 CATALOG_NAME ,   
 CHILDREN_CARDINALITY ,  
 CUSTOM_ROLLUP ,   
 CUSTOM_ROLLUP_PROPERTIES ,   
 DESCRIPTION ,   
 DIMENSION_UNIQUE_NAME ,   
 HIERARCHY_UNIQUE_NAME ,  
 IS_DATAMEMBER ,   
 IS_PLACEHOLDERMEMBER ,   
 KEY0 ,  
 LCID ,  
 LEVEL_NUMBER ,  
 LEVEL_UNIQUE_NAME ,  
 MEMBER_CAPTION ,   
 MEMBER_KEY ,   
 MEMBER_NAME ,   
 MEMBER_TYPE ,  
 MEMBER_UNIQUE_NAME ,   
 MEMBER_VALUE ,   
 PARENT_COUNT ,   
 PARENT_LEVEL ,   
 PARENT_UNIQUE_NAME ,  
 SKIPPED_LEVELS ,   
 UNARY_OPERATOR ,   
 UNIQUE_NAME    
 ON ROWS  
FROM [Adventure Works]  
WHERE [Employee].[Employee Department].[Department].&[Sales]  
```  
  
 <span data-ttu-id="79e6b-237">**예제 3: 멤버 속성을 결과 집합에 데이터로 반환**</span><span class="sxs-lookup"><span data-stu-id="79e6b-237">**Example 3: Return member properties as data in a result set**</span></span>  
  
 <span data-ttu-id="79e6b-238">다음 예에서는 지정된 로캘에 대한 Adventure Works 큐브의 Product 차원에 있는 제품 카테고리 멤버의 번역된 캡션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="79e6b-238">The following example returns the translated caption for the product category member in the Product dimension in the Adventure Works cube for specified locales.</span></span>  
  
```  
WITH   
MEMBER Measures.CategoryCaption AS Product.Category.CurrentMember.MEMBER_CAPTION  
MEMBER Measures.SpanishCategoryCaption AS Product.Category.CurrentMember.Properties("LCID3082")  
MEMBER Measures.FrenchCategoryCaption AS Product.Category.CurrentMember.Properties("LCID1036")  
SELECT   
{ Measures.CategoryCaption, Measures.SpanishCategoryCaption, Measures.FrenchCategoryCaption } ON 0  
,[Product].[Category].MEMBERS ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="79e6b-239">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79e6b-239">See Also</span></span>  
 <span data-ttu-id="79e6b-240">[PeriodsToDate &#40;MDX&#41;](/sql/mdx/periodstodate-mdx) </span><span class="sxs-lookup"><span data-stu-id="79e6b-240">[PeriodsToDate &#40;MDX&#41;](/sql/mdx/periodstodate-mdx) </span></span>  
 <span data-ttu-id="79e6b-241">[MDX &#40;자식&#41;](/sql/mdx/children-mdx) </span><span class="sxs-lookup"><span data-stu-id="79e6b-241">[Children &#40;MDX&#41;](/sql/mdx/children-mdx) </span></span>  
 <span data-ttu-id="79e6b-242">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span><span class="sxs-lookup"><span data-stu-id="79e6b-242">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span></span>  
 <span data-ttu-id="79e6b-243">[MDX&#41; &#40;&#40;집합 수&#41;](/sql/mdx/count-set-mdx) </span><span class="sxs-lookup"><span data-stu-id="79e6b-243">[Count &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx) </span></span>  
 <span data-ttu-id="79e6b-244">[MDX &#40;필터&#41;](/sql/mdx/filter-mdx) </span><span class="sxs-lookup"><span data-stu-id="79e6b-244">[Filter &#40;MDX&#41;](/sql/mdx/filter-mdx) </span></span>  
 <span data-ttu-id="79e6b-245">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span><span class="sxs-lookup"><span data-stu-id="79e6b-245">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span></span>  
 <span data-ttu-id="79e6b-246">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span><span class="sxs-lookup"><span data-stu-id="79e6b-246">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span></span>  
 <span data-ttu-id="79e6b-247">[MDX &#40;속성&#41;](/sql/mdx/properties-mdx) </span><span class="sxs-lookup"><span data-stu-id="79e6b-247">[Properties &#40;MDX&#41;](/sql/mdx/properties-mdx) </span></span>  
 <span data-ttu-id="79e6b-248">[PrevMember &#40;MDX&#41;](/sql/mdx/prevmember-mdx) </span><span class="sxs-lookup"><span data-stu-id="79e6b-248">[PrevMember &#40;MDX&#41;](/sql/mdx/prevmember-mdx) </span></span>  
 <span data-ttu-id="79e6b-249">[MDX&#41;&#40;멤버 속성 사용](mdx-member-properties.md) </span><span class="sxs-lookup"><span data-stu-id="79e6b-249">[Using Member Properties &#40;MDX&#41;](mdx-member-properties.md) </span></span>  
 [<span data-ttu-id="79e6b-250">MDX 함수 참조&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="79e6b-250">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
