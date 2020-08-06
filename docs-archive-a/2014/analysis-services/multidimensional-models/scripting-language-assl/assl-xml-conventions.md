---
title: XML 규칙 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- whitespace [Analysis Services Scripting Language]
- trailing whitespace
- XSD data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- cardinality [Analysis Services Scripting Language]
- white space [Analysis Services Scripting Language]
- ASSL, XML conventions
- defaults [Analysis Services Scripting Language]
- leading whitespace
- Analysis Services Scripting Language, XML conventions
- XML [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
- inherited defaults [Analysis Services Scripting Language]
ms.assetid: bce4edad-4420-41ce-9672-8c00c5c0dec6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b70742b07fd6450b01cf205147a05f40c4b6121
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736970"
---
# <a name="assl-xml-conventions"></a><span data-ttu-id="bfbb1-102">ASSL XML 표기 규칙</span><span class="sxs-lookup"><span data-stu-id="bfbb1-102">ASSL XML Conventions</span></span>
  <span data-ttu-id="bfbb1-103">ASSL(Analysis Services Scripting Language)은 개체의 계층을 요소 유형의 집합으로 나타내며, 각 요소 유형은 포함할 수 있는 자식 요소를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-103">Analysis Services Scripting Language (ASSL) represents the hierarchy of objects as a set of element types, each of which defines the child elements they can contain.</span></span>  
  
 <span data-ttu-id="bfbb1-104">개체 계층을 나타내기 위해 ASSL에서는 다음과 같은 XML 표기 규칙을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-104">To represent the object hierarchy, ASSL uses the following XML conventions:</span></span>  
  
-   <span data-ttu-id="bfbb1-105">모든 개체 및 속성은 ' xml: lang ' 같은 표준 XML 특성을 제외 하 고 요소로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-105">All objects and properties are represented as elements, except for standard XML attributes such as 'xml:lang'.</span></span>  
  
-   <span data-ttu-id="bfbb1-106">요소 이름과 열거형 값은 모두 밑줄을 사용하지 않는 파스칼식 Microsoft .NET Framework 명명 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-106">Both element names and enumeration values follow the Microsoft .NET Framework naming convention of Pascal casing with no underscores.</span></span>  
  
-   <span data-ttu-id="bfbb1-107">모든 값의 대/소문자는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-107">The case of all values is preserved.</span></span> <span data-ttu-id="bfbb1-108">열거형의 값도 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-108">Values for enumerations are also case-sensitive.</span></span>  
  
 <span data-ttu-id="bfbb1-109">이 표기 규칙 목록 외에도 Analysis Services는 카디널리티, 상속, 공백, 데이터 형식 및 기본값에 관한 특정 표기 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-109">In addition to this list of conventions, Analysis Services also follows certain conventions regarding cardinality, inheritance, whitespace, data types, and default values.</span></span>  
  
## <a name="cardinality"></a><span data-ttu-id="bfbb1-110">카디널리티</span><span class="sxs-lookup"><span data-stu-id="bfbb1-110">Cardinality</span></span>  
 <span data-ttu-id="bfbb1-111">요소의 카디널리티가 1보다 큰 경우에는 XML 요소 컬렉션에서 이 요소를 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-111">When an element has a cardinality that is greater than 1, there is an XML element collection that encapsulates this element.</span></span> <span data-ttu-id="bfbb1-112">컬렉션 이름에는 컬렉션에 포함된 복수 형태의 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-112">The name of collection uses the plural form of the elements contained in the collection.</span></span> <span data-ttu-id="bfbb1-113">예를 들어, 다음 XML 조각은 `Dimensions` 요소 내의 `Database` 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-113">For example, the following XML fragment represents the `Dimensions` collection within a `Database` element:</span></span>  
  
 `<Database>`  
  
 `...`  
  
 `<Dimensions>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `</Dimensions>`  
  
 `</Database>`  
  
 ``  
  
 <span data-ttu-id="bfbb1-114">요소가 표시되는 순서는 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-114">The order in which elements appear is unimportant.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="bfbb1-115">상속</span><span class="sxs-lookup"><span data-stu-id="bfbb1-115">Inheritance</span></span>  
 <span data-ttu-id="bfbb1-116">겹치는 부분이 있으면서도 상당히 다른 속성 집합을 가지고 있는 서로 다른 개체가 있을 때 상속이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-116">Inheritance is used when there are distinct objects that have overlapping but significantly different sets of properties.</span></span> <span data-ttu-id="bfbb1-117">겹치면서도 서로 다른 개체의 예로는 가상 큐브, 연결된 큐브 및 일반 큐브가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-117">Examples of such overlapping but distinct objects are virtual cubes, linked cubes, and regular cubes.</span></span> <span data-ttu-id="bfbb1-118">Analysis Services에서는 겹치면서도 서로 다른 개체에 대해 XML 인스턴스 네임스페이스의 표준 `type` 특성을 사용하여 상속을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-118">For overlapping but distinct object, Analysis Services uses the standard `type` attribute from the XML Instance Namespace to indicate the inheritance.</span></span> <span data-ttu-id="bfbb1-119">예를 들어, 다음 XML 조각에서는 `type` 요소가 일반 큐브에서 상속되는지 또는 가상 큐브에서 상속되는지를 `Cube` 특성을 통해 식별하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-119">For example, the following XML fragment shows how the `type` attribute identifies whether a `Cube` element inherits from a regular cube or from a virtual cube:</span></span>  
  
 `<Cubes>`  
  
 `<Cube xsi:type="RegularCube">`  
  
 `<Name>Sales</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `<Cube xsi:type="VirtualCube">`  
  
 `<Name>SalesAndInventory</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `</Cubes>`  
  
 ``  
  
 <span data-ttu-id="bfbb1-120">여러 형식에 같은 이름의 속성이 있는 경우에는 일반적으로 상속을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-120">Inheritance is generally not used when multiple types have a property of the same name.</span></span> <span data-ttu-id="bfbb1-121">예를 들어, `Name` 및 `ID` 속성은 많은 요소에 나타나지만 이러한 속성은 추상 형식으로 승격되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-121">For example, the `Name` and `ID` properties appear on many elements, but these properties have not been promoted to an abstract type.</span></span>  
  
## <a name="whitespace"></a><span data-ttu-id="bfbb1-122">공백</span><span class="sxs-lookup"><span data-stu-id="bfbb1-122">Whitespace</span></span>  
 <span data-ttu-id="bfbb1-123">요소 값 안의 공백은 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-123">Whitespace within an element value is preserved.</span></span> <span data-ttu-id="bfbb1-124">그러나 선행 공백과 후행 공백은 항상 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-124">However, leading and trailing whitespace is always trimmed.</span></span> <span data-ttu-id="bfbb1-125">예를 들어, 다음 요소는 동일한 텍스트를 가지고 있지만 텍스트의 공백 수가 다르므로 서로 다른 값을 가진 것으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-125">For example, the following elements have the same text but differing amounts of whitespace within that text, and are therefore treated as if they have different values:</span></span>  
  
 `<Description>My text<Description>`  
  
 `<Description>My  text<Description>`  
  
 ``  
  
 <span data-ttu-id="bfbb1-126">그러나 다음 요소는 선행 및 후행 공백만 다르므로 같은 값을 가진 것으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-126">However, the following elements vary only in leading and trailing whitespace, and are therefore treated as if they have equivalent values:</span></span>  
  
 `<Description>My text<Description>`  
  
 `<Description>  My text  <Description>`  
  
 ``  
  
## <a name="data-types"></a><span data-ttu-id="bfbb1-127">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="bfbb1-127">Data Types</span></span>  
 <span data-ttu-id="bfbb1-128">Analysis Services는 다음과 같은 표준 XSD(XML 스키마 정의 언어) 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-128">Analysis Services uses the following standard XML Schema definition language (XSD) data types:</span></span>  
  
 `Int`  
 <span data-ttu-id="bfbb1-129">-231 ~ 231-1 범위의 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-129">An integer value in the range of -231 to 231 - 1.</span></span>  
  
 `Long`  
 <span data-ttu-id="bfbb1-130">-263-263-1 범위의 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-130">An integer value in range of -263 to 263 - 1.</span></span>  
  
 `String`  
 <span data-ttu-id="bfbb1-131">다음과 같은 전역 규칙을 따르는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-131">A string value that conforms to the following global rules:</span></span>  
  
-   <span data-ttu-id="bfbb1-132">제어 문자가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-132">Control characters are stripped out.</span></span>  
  
-   <span data-ttu-id="bfbb1-133">선행 공백과 후행 공백이 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-133">Leading and trailing white space is trimmed.</span></span>  
  
-   <span data-ttu-id="bfbb1-134">내부 공백이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-134">Internal white space is preserved.</span></span>  
  
 <span data-ttu-id="bfbb1-135">`Name` 및 `ID` 속성에는 문자열 요소의 유효한 문자에 대한 특별한 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-135">`Name` and `ID` properties have special limitations on valid characters in string elements.</span></span> <span data-ttu-id="bfbb1-136">및 규칙에 대 한 자세한 내용은 `Name` `ID` [개체 및 개체 특성](assl-objects-and-object-characteristics.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-136">For additional information about `Name` and `ID` conventions, see [ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md).</span></span>  
  
 `DateTime`  
 <span data-ttu-id="bfbb1-137">`DateTime`.NET Framework 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-137">A `DateTime` structure from the .NET Framework.</span></span> <span data-ttu-id="bfbb1-138">`DateTime` 값은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-138">A `DateTime` value cannot be NULL.</span></span> <span data-ttu-id="bfbb1-139">`DataTime` 데이터 형식에서 지원되는 가장 이른 날짜는 1601년 1월 1일이며 프로그래머는 이 날짜를 `DateTime.MinValue`로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-139">The lowest date supported by the `DataTime` data type is January 1, 1601, which is available to programmers as `DateTime.MinValue`.</span></span> <span data-ttu-id="bfbb1-140">지원되는 가장 낮은 날짜는 `DateTime` 값이 누락되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-140">The lowest supported date indicates that a `DateTime` value is missing.</span></span>  
  
 `Boolean`  
 <span data-ttu-id="bfbb1-141">{true, false} 또는 {0, 1}처럼 두 개의 값만 가지는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-141">An enumeration with only two values, such as {true, false} or {0, 1}.</span></span>  
  
## <a name="default-values"></a><span data-ttu-id="bfbb1-142">기본값</span><span class="sxs-lookup"><span data-stu-id="bfbb1-142">Default Values</span></span>  
 <span data-ttu-id="bfbb1-143">Analysis Services에서는 다음 표에 나열된 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-143">Analysis Services uses the defaults listed in the following table.</span></span>  
  
|<span data-ttu-id="bfbb1-144">XML 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="bfbb1-144">XML data type</span></span>|<span data-ttu-id="bfbb1-145">기본값</span><span class="sxs-lookup"><span data-stu-id="bfbb1-145">Default value</span></span>|  
|-------------------|-------------------|  
|`Boolean`|<span data-ttu-id="bfbb1-146">거짓</span><span class="sxs-lookup"><span data-stu-id="bfbb1-146">False</span></span>|  
|`String`|<span data-ttu-id="bfbb1-147">""(빈 문자열)</span><span class="sxs-lookup"><span data-stu-id="bfbb1-147">"" (empty string)</span></span>|  
|<span data-ttu-id="bfbb1-148">`Integer` 또는 `Long`</span><span class="sxs-lookup"><span data-stu-id="bfbb1-148">`Integer` or `Long`</span></span>|<span data-ttu-id="bfbb1-149">0(영)</span><span class="sxs-lookup"><span data-stu-id="bfbb1-149">0 (zero)</span></span>|  
|`Timestamp`|<span data-ttu-id="bfbb1-150">오전 12:00:00, 1/1/0001 (0 틱이 있는 .NET Framework에 해당 `System.DateTime` )</span><span class="sxs-lookup"><span data-stu-id="bfbb1-150">12:00:00 AM, 1/1/0001 (corresponding to a the .NET Frameworks `System.DateTime` with 0 ticks)</span></span>|  
  
 <span data-ttu-id="bfbb1-151">존재하기는 하지만 비어 있는 요소는 기본값이 아닌 Null 문자열 값을 갖는 것으로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-151">An element that is present but empty is interpreted as having a value of a null string, not the default value.</span></span>  
  
### <a name="inherited-defaults"></a><span data-ttu-id="bfbb1-152">상속된 기본값</span><span class="sxs-lookup"><span data-stu-id="bfbb1-152">Inherited Defaults</span></span>  
 <span data-ttu-id="bfbb1-153">개체에 지정된 일부 속성은 자식 또는 하위 항목 개체의 동일한 속성에 기본값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-153">Some properties that are specified on an object provide default values for the same property on child or descendant objects.</span></span> <span data-ttu-id="bfbb1-154">예를 들어, `Cube.StorageMode`는 `Partition.StorageMode`에 기본값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-154">For example, `Cube.StorageMode` provides the default value for `Partition.StorageMode`.</span></span> <span data-ttu-id="bfbb1-155">Analysis Services에서 상속된 기본값에 적용하는 규칙은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-155">The rules that Analysis Services applies for inherited default values are as follows:</span></span>  
  
-   <span data-ttu-id="bfbb1-156">XML에서 자식 개체의 속성이 Null이면 속성의 기본값은 상속된 값으로 기본 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-156">When the property for the child object is null in the XML, its value defaults to the inherited value.</span></span> <span data-ttu-id="bfbb1-157">그러나 서버의 값을 쿼리하는 경우 서버가 XML 요소의 null 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-157">However, if you query the value from the server, the server returns the null value of the XML element.</span></span>  
  
-   <span data-ttu-id="bfbb1-158">자식 개체의 속성이 자식 개체에 직접 설정되었는지 또는 상속되었는지 여부를 프로그래밍 방식으로 확인할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-158">It is not possible to determine programmatically whether the property of a child object has been set directly on the child object or inherited.</span></span>  
  
 <span data-ttu-id="bfbb1-159">일부 요소에는 요소가 누락되었을 때 적용되는 기본값이 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-159">Some elements have defined defaults that apply when the element is missing.</span></span> <span data-ttu-id="bfbb1-160">예를 들어, 다음 XML 조각에서 한 `Dimension` 요소에는 `Dimension` 요소가 있고 다른 `Visible` 요소에는 해당 요소가 없어도 두 `Dimension` 요소는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-160">For example, the `Dimension` elements in the following XML fragment are equivalent even though one `Dimension` element contains a `Visible` element, but the other `Dimension` element does not.</span></span>  
  
 `<Dimension>`  
  
 `<Name>Product</Name>`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `<Name>Product</ Name>`  
  
 `<Visible>true</Visible>`  
  
 `</Dimension>`  
  
 <span data-ttu-id="bfbb1-161">상속 된 기본값에 대 한 자세한 내용은 [개체 및 개체 특성](assl-objects-and-object-characteristics.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bfbb1-161">For more information on inherited defaults, see [ASSL Objects and Object Characteristics](assl-objects-and-object-characteristics.md).</span></span>  
  
  
