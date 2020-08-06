---
title: 사용자 정의 형식 코딩 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- validation [CLR integration]
- UDTs [CLR integration], coding
- UserDefined serialization format [CLR integration]
- Point UDT
- Parse method
- null values [CLR integration]
- ToString method
- ValidatePoint method
- attributes [CLR integration]
- coding user-defined types [CLR integration]
- Read method
- Write method
- nullability [CLR integration]
- user-defined types [CLR integration], coding
- Currency UDT
- validating UDT values
- exposing UDT properties [CLR integration]
ms.assetid: 1e5b43b3-4971-45ee-a591-3f535e2ac722
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e88c4d8162e5c7c921f5c5062f5b3c23df40a2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647714"
---
# <a name="coding-user-defined-types"></a><span data-ttu-id="332b9-102">사용자 정의 형식 코딩</span><span class="sxs-lookup"><span data-stu-id="332b9-102">Coding User-Defined Types</span></span>
  <span data-ttu-id="332b9-103">UDT(사용자 정의 형식) 정의를 코딩하는 경우 UDT를 클래스 또는 구조로 구현할지 여부와 선택한 형식 및 직렬화 옵션에 따라 다양한 기능을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-103">When coding your user-defined type (UDT) definition, you must implement various features, depending on whether you are implementing the UDT as a class or a structure, as well as on the format and serialization options you have chosen.</span></span>  
  
 <span data-ttu-id="332b9-104">이 섹션의 예에서는 `Point` UDT를 `struct`(Visual Basic의 경우 `Structure`)로 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-104">The example in this section illustrates implementing a `Point` UDT as a `struct` (or `Structure` in Visual Basic).</span></span> <span data-ttu-id="332b9-105">`Point` UDT는 속성 프로시저로 구현된 X 및 Y 좌표로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-105">The `Point` UDT consists of X and Y coordinates implemented as property procedures.</span></span>  
  
 <span data-ttu-id="332b9-106">UDT를 정의하는 경우 다음 네임스페이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-106">The following namespaces are required when defining a UDT:</span></span>  
  
```vb  
Imports System  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
```  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
```  
  
 <span data-ttu-id="332b9-107">`Microsoft.SqlServer.Server` 네임스페이스에는 UDT의 다양한 특성에 필요한 개체가 포함되어 있고, `System.Data.SqlTypes` 네임스페이스에는 어셈블리에서 사용할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본 데이터 형식을 나타내는 클래스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-107">The `Microsoft.SqlServer.Server` namespace contains the objects required for various attributes of your UDT, and the `System.Data.SqlTypes` namespace contains the classes that represent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types available to the assembly.</span></span> <span data-ttu-id="332b9-108">물론 어셈블리가 올바르게 작동하는 데 필요한 추가 네임스페이스가 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-108">There may of course be additional namespaces that your assembly requires in order to function correctly.</span></span> <span data-ttu-id="332b9-109">또한 `Point` UDT는 문자열 작업에 `System.Text` 네임스페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-109">The `Point` UDT also uses the `System.Text` namespace for working with strings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="332b9-110">`/clr:pure`를 사용하여 컴파일된 UDT 등의 Visual C++ 개체는 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-110">Visual C++ database objects, such as UDTs, compiled with `/clr:pure` are not supported for execution.</span></span>  
  
## <a name="specifying-attributes"></a><span data-ttu-id="332b9-111">특성 지정</span><span class="sxs-lookup"><span data-stu-id="332b9-111">Specifying Attributes</span></span>  
 <span data-ttu-id="332b9-112">특성은 직렬화를 사용하여 UDT의 스토리지 표현을 생성하고 UDT를 값으로 클라이언트에 전송하는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-112">Attributes determine how serialization is used to construct the storage representation of UDTs and to transmit UDTs by value to the client.</span></span>  
  
 <span data-ttu-id="332b9-113">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-113">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` is required.</span></span> <span data-ttu-id="332b9-114">`Serializable` 특성은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-114">The `Serializable` attribute is optional.</span></span> <span data-ttu-id="332b9-115">`Microsoft.SqlServer.Server.SqlFacetAttribute`를 지정하여 UDT의 반환 형식에 대한 정보를 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-115">You can also specify the `Microsoft.SqlServer.Server.SqlFacetAttribute` to provide information about the return type of a UDT.</span></span> <span data-ttu-id="332b9-116">자세한 내용은 [CLR 루틴용 사용자 지정 특성](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="332b9-116">For more information, see [Custom Attributes for CLR Routines](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).</span></span>  
  
### <a name="point-udt-attributes"></a><span data-ttu-id="332b9-117">Point UDT 특성</span><span class="sxs-lookup"><span data-stu-id="332b9-117">Point UDT Attributes</span></span>  
 <span data-ttu-id="332b9-118">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`는 `Point` UDT의 스토리지 형식을 `Native`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-118">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` sets the storage format for the `Point` UDT to `Native`.</span></span> <span data-ttu-id="332b9-119">`IsByteOrdered`는 `true`로 설정되며, 이 경우 비교 결과는 SQL Server에서 동일한 비교가 관리 코드에서 수행된 결과와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-119">`IsByteOrdered` is set to `true`, which guarantees that the results of comparisons are the same in SQL Server as if the same comparison had taken place in managed code.</span></span> <span data-ttu-id="332b9-120">UDT는 UDT에서 Null을 인식하도록 하는 `System.Data.SqlTypes.INullable` 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-120">The UDT implements the `System.Data.SqlTypes.INullable` interface to make the UDT null aware.</span></span>  
  
 <span data-ttu-id="332b9-121">다음 코드 조각에서는 `Point` UDT의 특성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-121">The following code fragment shows the attributes for the `Point` UDT.</span></span>  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True)> _  
  Public Structure Point  
    Implements INullable  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true)]  
public struct Point : INullable  
{  
```  
  
## <a name="implementing-nullability"></a><span data-ttu-id="332b9-122">Null 허용 여부 구현</span><span class="sxs-lookup"><span data-stu-id="332b9-122">Implementing Nullability</span></span>  
 <span data-ttu-id="332b9-123">어셈블리의 특성을 올바르게 지정하는 것 외에도 UDT는 Null 허용 여부를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-123">In addition to specifying the attributes for your assemblies correctly, your UDT must also support nullability.</span></span> <span data-ttu-id="332b9-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 로드된 UDT는 Null을 인식하지만 UDT에서 Null 값을 인식하려면 `System.Data.SqlTypes.INullable` 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-124">UDTs loaded into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are null-aware, but in order for the UDT to recognize a null value, the UDT must implement the `System.Data.SqlTypes.INullable` interface.</span></span>  
  
 <span data-ttu-id="332b9-125">CLR 코드 내에서 값이 Null인지 여부를 결정하는 데 필요한 `IsNull` 속성을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-125">You must create a property named `IsNull`, which is needed to determine whether a value is null from within CLR code.</span></span> <span data-ttu-id="332b9-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 UDT의 Null 인스턴스를 찾으면 일반적인 Null 처리 메서드를 사용하여 UDT가 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-126">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finds a null instance of a UDT, the UDT is persisted using normal null-handling methods.</span></span> <span data-ttu-id="332b9-127">서버는 필요하지 않은 경우 UDT 직렬화 또는 역직렬화하는 데 시간을 낭비하지 않으며 Null UDT를 저장하는 공간을 낭비하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-127">The server does not waste time serializing or deserializing the UDT if it does not have to, and it does not waste space to store a null UDT.</span></span> <span data-ttu-id="332b9-128">이 Null 검사는 CLR에서 UDT를 가져올 때마다 수행되므로 [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL 구문을 사용한 Null UDT 검사가 항상 작동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-128">This check for nulls is performed every time a UDT is brought over from the CLR, which means that using the [!INCLUDE[tsql](../../includes/tsql-md.md)] IS NULL construct to check for null UDTs should always work.</span></span> <span data-ttu-id="332b9-129">또한 서버는 `IsNull` 속성을 사용하여 인스턴스가 Null인지 여부를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-129">The `IsNull` property is also used by the server to test whether an instance is null.</span></span> <span data-ttu-id="332b9-130">서버에서 UDT가 Null임을 확인하면 기본 Null 처리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-130">Once the server determines that the UDT is null, it can use its native null handling.</span></span>  
  
 <span data-ttu-id="332b9-131">`get()`의 `IsNull` 메서드는 어떤 방식으로든 특별하게 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-131">The `get()` method of `IsNull` is not special-cased in any way.</span></span> <span data-ttu-id="332b9-132">`Point` 변수 `@p`가 `Null`이면 기본적으로 `@p.IsNull`은 "1"이 아니라 "NULL"이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-132">If a `Point` variable `@p` is `Null`, then `@p.IsNull` will, by default, evaluate to "NULL", not "1".</span></span> <span data-ttu-id="332b9-133">이는 `SqlMethod(OnNullCall)` 메서드의 `IsNull get()` 특성이 기본적으로 false로 설정되어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-133">This is because the `SqlMethod(OnNullCall)` attribute of the `IsNull get()` method defaults to false.</span></span> <span data-ttu-id="332b9-134">개체가 `Null`이므로 속성이 요청될 때 개체가 역직렬화되지 않고 메서드가 호출되지 않으며 기본값 "NULL"이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-134">Because the object is `Null`, when the property is requested the object is not deserialized, the method is not called, and a default value of "NULL" is returned.</span></span>  
  
### <a name="example"></a><span data-ttu-id="332b9-135">예제</span><span class="sxs-lookup"><span data-stu-id="332b9-135">Example</span></span>  
 <span data-ttu-id="332b9-136">다음 예에서 `is_Null` 변수는 프라이빗이며 UDT 인스턴스에 대해 Null 상태를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-136">In the following example, the `is_Null` variable is private and holds the state of null for the instance of the UDT.</span></span> <span data-ttu-id="332b9-137">코드에서 `is_Null`에 적합한 값을 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-137">Your code must maintain an appropriate value for `is_Null`.</span></span> <span data-ttu-id="332b9-138">또한 UDT의 Null 값 인스턴스를 반환하는 `Null`이라는 정적 속성이 UDT에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-138">The UDT must also have a static property named `Null` that returns a null value instance of the UDT.</span></span> <span data-ttu-id="332b9-139">이렇게 하면 인스턴스가 데이터베이스에서 실제로 Null인 경우 UDT에서 Null 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-139">This allows the UDT to return a null value if the instance is indeed null in the database.</span></span>  
  
```vb  
Private is_Null As Boolean  
  
Public ReadOnly Property IsNull() As Boolean _  
   Implements INullable.IsNull  
    Get  
        Return (is_Null)  
    End Get  
End Property  
  
Public Shared ReadOnly Property Null() As Point  
    Get  
        Dim pt As New Point  
        pt.is_Null = True  
        Return (pt)  
    End Get  
End Property  
```  
  
```csharp  
private bool is_Null;  
  
public bool IsNull  
{  
    get  
    {  
        return (is_Null);  
    }  
}  
  
public static Point Null  
{  
    get  
    {  
        Point pt = new Point();  
        pt.is_Null = true;  
        return pt;  
    }  
}  
```  
  
### <a name="is-null-vs-isnull"></a><span data-ttu-id="332b9-140">IS NULL 및 IsNull 비교</span><span class="sxs-lookup"><span data-stu-id="332b9-140">IS NULL vs. IsNull</span></span>  
 <span data-ttu-id="332b9-141">Points(id int, location Point) 스키마 및 다음 쿼리가 포함된 테이블을 살펴 보십시오. 여기서 `Point`는 CLR UDT입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-141">Consider a table that contains the schema Points(id int, location Point), where `Point` is a CLR UDT, and the following queries:</span></span>  
  
```  
--Query 1  
SELECT ID  
FROM Points  
WHERE NOT (location IS NULL) -- Or, WHERE location IS NOT NULL;  
```  
  
```  
--Query 2:  
SELECT ID  
FROM Points  
WHERE location.IsNull = 0;  
```  
  
 <span data-ttu-id="332b9-142">두 쿼리에서 모두 위치가 `Null`이 아닌 점의 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-142">Both queries return the IDs of points with non-`Null` locations.</span></span> <span data-ttu-id="332b9-143">쿼리 1에서는 일반적인 Null 처리가 사용되며 UDT의 역직렬화가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-143">In Query 1, normal null-handling is used, and there no deserialization of UDTs is required.</span></span> <span data-ttu-id="332b9-144">반면, 쿼리 2에서는 `Null`이 아닌 각 개체와 호출을 CLR로 역직렬화하여 `IsNull` 속성 값을 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-144">Query 2, on the other hand, has to deserialize each non-`Null` object and call into the CLR to obtain the value of the `IsNull` property.</span></span> <span data-ttu-id="332b9-145">`IS NULL`을 사용하면 성능이 향상되는 것이 확실하며 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드에서 UDT의 `IsNull` 속성을 읽을 이유가 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-145">Clearly, using `IS NULL` will exhibit better performance and there should never be a reason to read the `IsNull` property of a UDT from [!INCLUDE[tsql](../../includes/tsql-md.md)] code.</span></span>  
  
 <span data-ttu-id="332b9-146">그러면 `IsNull` 속성은 어떤 용도로 사용됩니까?</span><span class="sxs-lookup"><span data-stu-id="332b9-146">So, what is the use of the `IsNull` property?</span></span> <span data-ttu-id="332b9-147">첫째, CLR 코드 내에서 값이 `Null`인지 여부를 결정하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-147">First, it is needed to determine whether a value is `Null` from within CLR code.</span></span> <span data-ttu-id="332b9-148">둘째, 서버에서 인스턴스가 `Null`인지 여부를 테스트할 수 있어야 하므로 이 속성은 서버에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-148">Second, the server needs a way to test whether an instance is `Null`, so this property is used by the server.</span></span> <span data-ttu-id="332b9-149">서버에서 `Null`임을 확인하면 기본 Null 처리를 사용하여 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-149">After it determines it is `Null`, then it can use its native null handling to handle it.</span></span>  
  
## <a name="implementing-the-parse-method"></a><span data-ttu-id="332b9-150">Parse 메서드 구현</span><span class="sxs-lookup"><span data-stu-id="332b9-150">Implementing the Parse Method</span></span>  
 <span data-ttu-id="332b9-151">`Parse` 및 `ToString` 메서드를 사용하면 UDT의 문자열 표현으로 변환하거나 그 반대로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-151">The `Parse` and `ToString` methods allow for conversions to and from string representations of the UDT.</span></span> <span data-ttu-id="332b9-152">`Parse` 메서드는 문자열을 UDT로 변환할 수 있게 하며,</span><span class="sxs-lookup"><span data-stu-id="332b9-152">The `Parse` method allows a string to be converted into a UDT.</span></span> <span data-ttu-id="332b9-153">`static`(Visual Basic의 경우 `Shared`)으로 선언되고 `System.Data.SqlTypes.SqlString` 유형의 매개 변수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-153">It must be declared as `static` (or `Shared` in Visual Basic), and take a parameter of type `System.Data.SqlTypes.SqlString`.</span></span>  
  
 <span data-ttu-id="332b9-154">다음 코드 예제에서는 `Parse` UDT에 대해 X 및 Y 좌표를 구분하는 `Point` 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-154">The following code implements the `Parse` method for the `Point` UDT, which separates out the X and Y coordinates.</span></span> <span data-ttu-id="332b9-155">`Parse` 메서드는 `System.Data.SqlTypes.SqlString` 유형의 인수 하나를 사용하며, X 및 Y 값이 쉼표로 구분된 문자열로 제공된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-155">The `Parse` method has a single argument of type `System.Data.SqlTypes.SqlString`, and assumes that X and Y values are supplied as a comma-delimited string.</span></span> <span data-ttu-id="332b9-156">`Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall` 특성을 `false`로 설정하면 Point의 Null 인스턴스에서 `Parse` 메서드를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-156">Setting the `Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall` attribute to `false` prevents the `Parse` method from being called from a null instance of Point.</span></span>  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
    return pt;  
}  
```  
  
## <a name="implementing-the-tostring-method"></a><span data-ttu-id="332b9-157">ToString 메서드 구현</span><span class="sxs-lookup"><span data-stu-id="332b9-157">Implementing the ToString Method</span></span>  
 <span data-ttu-id="332b9-158">`ToString` 메서드는 `Point` UDT를 문자열 값으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-158">The `ToString` method converts the `Point` UDT to a string value.</span></span> <span data-ttu-id="332b9-159">이 경우 `Point` 유형의 Null 인스턴스에 대해 "NULL" 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-159">In this case, the string "NULL" is returned for a Null instance of the `Point` type.</span></span> <span data-ttu-id="332b9-160">`ToString` 메서드는 `Parse` 메서드와 반대로 `System.Text.StringBuilder`를 사용하여 X 및 Y 좌표 값으로 구성된, 쉼표로 구분된 `System.String`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-160">The `ToString` method reverses the `Parse` method by using a `System.Text.StringBuilder` to return a comma-delimited `System.String` consisting of the X and Y coordinate values.</span></span> <span data-ttu-id="332b9-161">**InvokeIfReceiverIsNull** 기본값은 false 이므로의 null 인스턴스에 대 한 검사는 `Point` 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-161">Because **InvokeIfReceiverIsNull** defaults to false, the check for a null instance of `Point` is unnecessary.</span></span>  
  
```vb  
Private _x As Int32  
Private _y As Int32  
  
Public Overrides Function ToString() As String  
    If Me.IsNull Then  
        Return "NULL"  
    Else  
        Dim builder As StringBuilder = New StringBuilder  
        builder.Append(_x)  
        builder.Append(",")  
        builder.Append(_y)  
        Return builder.ToString  
    End If  
End Function  
```  
  
```csharp  
private Int32 _x;  
private Int32 _y;  
  
public override string ToString()  
{  
    if (this.IsNull)  
        return "NULL";  
    else  
    {  
        StringBuilder builder = new StringBuilder();  
        builder.Append(_x);  
        builder.Append(",");  
        builder.Append(_y);  
        return builder.ToString();  
    }  
}  
```  
  
## <a name="exposing-udt-properties"></a><span data-ttu-id="332b9-162">UDT 속성 노출</span><span class="sxs-lookup"><span data-stu-id="332b9-162">Exposing UDT Properties</span></span>  
 <span data-ttu-id="332b9-163">`Point` UDT는 `System.Int32` 유형의 공용 읽기/쓰기 속성으로 구현된 X 및 Y 좌표를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-163">The `Point` UDT exposes X and Y coordinates that are implemented as public read-write properties of type `System.Int32`.</span></span>  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _x = Value  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _y = Value  
    End Set  
End Property  
```  
  
```csharp  
public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    set   
    {  
        _x = value;  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        _y = value;  
    }  
}  
```  
  
## <a name="validating-udt-values"></a><span data-ttu-id="332b9-164">UDT 값 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="332b9-164">Validating UDT Values</span></span>  
 <span data-ttu-id="332b9-165">UDT 데이터를 사용할 때 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]은 자동으로 이진 값을 UDT 값으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-165">When working with UDT data, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] automatically converts binary values to UDT values.</span></span> <span data-ttu-id="332b9-166">이 변환 프로세스에는 값이 유형의 직렬화 형식에 적합하고 값을 올바르게 역직렬화할 수 있는지 확인하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-166">This conversion process involves checking that values are appropriate for the serialization format of the type and ensuring that the value can be deserialized correctly.</span></span> <span data-ttu-id="332b9-167">이렇게 하면 값을 다시 이진 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-167">This ensures that the value can be converted back to binary form.</span></span> <span data-ttu-id="332b9-168">또한 바이트 정렬 UDT의 경우 결과 이진 값이 원래 이진 값과 일치하여</span><span class="sxs-lookup"><span data-stu-id="332b9-168">In the case of byte-ordered UDTs, this also ensures that the resulting binary value matches the original binary value.</span></span> <span data-ttu-id="332b9-169">잘못된 값이 데이터베이스에 저장되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-169">This prevents invalid values from being persisted in the database.</span></span> <span data-ttu-id="332b9-170">경우에 따라 이 검사 수준이 부적절할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-170">In some cases, this level of checking may be inadequate.</span></span> <span data-ttu-id="332b9-171">UDT 값이 예상 도메인이나 범위에 있어야 하는 경우 추가 유효성 검사가 필요할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-171">Additional validation may be required when UDT values are required to be in an expected domain or range.</span></span> <span data-ttu-id="332b9-172">예를 들어 날짜를 구현하는 UDT의 경우 일 값이 유효한 값의 특정 범위 내에 있는 양수여야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-172">For example, a UDT that implements a date might require the day value to be a positive number that falls within a certain range of valid values.</span></span>  
  
 <span data-ttu-id="332b9-173">`Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName`의  `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 속성을 사용하면 데이터가 UDT에 할당되거나 UDT로 변환될 때 서버에서 실행하는 유효성 검사 메서드의 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-173">The `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName` property of the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` allows you to supply the name of a validation method that the server runs when data is assigned to a UDT or converted to a UDT.</span></span> <span data-ttu-id="332b9-174">`ValidationMethodName`은 bcp 유틸리티, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, 분산 쿼리 및 TDS(Tabular Data Stream) RPC(원격 프로시저 호출) 작업을 실행하는 동안에도 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-174">`ValidationMethodName` is also called during the running of the bcp utility, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, distributed query, and tabular data stream (TDS) remote procedure call (RPC) operations.</span></span> <span data-ttu-id="332b9-175">`ValidationMethodName`의 기본값은 유효성 검사 메서드가 없음을 나타내는 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-175">The default value for `ValidationMethodName` is null, indicating that there is no validation method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="332b9-176">예제</span><span class="sxs-lookup"><span data-stu-id="332b9-176">Example</span></span>  
 <span data-ttu-id="332b9-177">다음 코드 조각에서는 `Point`의 `ValidationMethodName`을 지정하는 `ValidatePoint` 클래스 선언을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-177">The following code fragment shows the declaration for the `Point` class, which specifies a `ValidationMethodName` of `ValidatePoint`.</span></span>  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True, _  
  ValidationMethodName:="ValidatePoint")> _  
  Public Structure Point  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true,   
  ValidationMethodName = "ValidatePoint")]  
public struct Point : INullable  
{  
```  
  
 <span data-ttu-id="332b9-178">유효성 검사 메서드가 지정된 경우 해당 메서드에 다음 코드 조각과 유사한 서명이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-178">If a validation method is specified, it must have a signature that looks like the following code fragment.</span></span>  
  
```vb  
Private Function ValidationFunction() As Boolean  
    If (validation logic here) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidationFunction()  
{  
    if (validation logic here)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
 <span data-ttu-id="332b9-179">유효성 검사 메서드는 모든 범위를 가질 수 있으며 값이 유효한 경우 `true`, 그렇지 않으면 `false`을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-179">The validation method can have any scope and should return `true` if the value is valid, and `false` otherwise.</span></span> <span data-ttu-id="332b9-180">메서드에서 `false`를 반환하고 예외를 throw하면 값이 잘못된 것으로 처리되고 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-180">If the method returns `false` or throws an exception, the value is treated as not valid and an error is raised.</span></span>  
  
 <span data-ttu-id="332b9-181">아래 코드 예제에서는 값이 0보다 큰 X 및 Y 좌표만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-181">In the example below, the code allows only values of zero or greater the X and Y coordinates.</span></span>  
  
```vb  
Private Function ValidatePoint() As Boolean  
    If (_x >= 0) And (_y >= 0) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidatePoint()  
{  
    if ((_x >= 0) && (_y >= 0))  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
### <a name="validation-method-limitations"></a><span data-ttu-id="332b9-182">유효성 검사 메서드 제한 사항</span><span class="sxs-lookup"><span data-stu-id="332b9-182">Validation Method Limitations</span></span>  
 <span data-ttu-id="332b9-183">서버는 개별 속성을 설정하여 데이터가 삽입되거나 [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT 문을 사용하여 데이터가 삽입될 때가 아니라 서버에서 변환을 수행할 때 유효성 검사 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-183">The server calls the validation method when the server is performing conversions, not when data is inserted by setting individual properties or when data is inserted using a [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT statement.</span></span>  
  
 <span data-ttu-id="332b9-184">`Parse`모든 상황에서 유효성 검사 메서드를 실행 하려면 속성 setter 및 메서드에서 유효성 검사 메서드를 명시적으로 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-184">You must explicitly call the validation method from property setters and the `Parse` method if you want the validation method to execute in all situations.</span></span> <span data-ttu-id="332b9-185">이것은 요구 사항은 아니며 경우에 따라 바람직하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-185">This is not a requirement, and in some cases may not even be desirable.</span></span>  
  
### <a name="parse-validation-example"></a><span data-ttu-id="332b9-186">유효성 검사 구문 분석 예</span><span class="sxs-lookup"><span data-stu-id="332b9-186">Parse Validation Example</span></span>  
 <span data-ttu-id="332b9-187">`ValidatePoint`클래스가 클래스에서 호출 되도록 하려면 `Point` `Parse` 메서드 및 X 및 Y 좌표 값을 설정 하는 속성 프로시저에서 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-187">To ensure that the `ValidatePoint` method is invoked in the `Point` class, you must call it from the `Parse` method and from the property procedures that set the X and Y coordinate values.</span></span> <span data-ttu-id="332b9-188">다음 코드 조각에서는 `ValidatePoint` 함수에서 유효성 검사 메서드를 호출 하는 방법을 보여 줍니다 `Parse` .</span><span class="sxs-lookup"><span data-stu-id="332b9-188">The following code fragment shows how to call the `ValidatePoint` validation method from the `Parse` function.</span></span>  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
  
    ' Call ValidatePoint to enforce validation  
    ' for string conversions.  
    If Not pt.ValidatePoint() Then  
        Throw New ArgumentException("Invalid XY coordinate values.")  
    End If  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
  
    // Call ValidatePoint to enforce validation  
    // for string conversions.  
    if (!pt.ValidatePoint())   
        throw new ArgumentException("Invalid XY coordinate values.");  
    return pt;  
}  
```  
  
### <a name="property-validation-example"></a><span data-ttu-id="332b9-189">속성 유효성 검사 예</span><span class="sxs-lookup"><span data-stu-id="332b9-189">Property Validation Example</span></span>  
 <span data-ttu-id="332b9-190">다음 코드 조각에서는 `ValidatePoint` X 및 Y 좌표를 설정 하는 속성 프로시저에서 유효성 검사 메서드를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-190">The following code fragment shows how to call the `ValidatePoint` validation method from the property procedures that set the X and Y coordinates.</span></span>  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _x  
        _x = Value  
        If Not ValidatePoint() Then  
            _x = temp  
            Throw New ArgumentException("Invalid X coordinate value.")  
        End If  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _y  
        _y = Value  
        If Not ValidatePoint() Then  
            _y = temp  
            Throw New ArgumentException("Invalid Y coordinate value.")  
        End If  
    End Set  
End Property  
```  
  
```csharp  
    public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    // Call ValidatePoint to ensure valid range of Point values.  
    set   
    {  
        Int32 temp = _x;  
        _x = value;  
        if (!ValidatePoint())  
        {  
            _x = temp;  
            throw new ArgumentException("Invalid X coordinate value.");  
        }  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        Int32 temp = _y;  
        _y = value;  
        if (!ValidatePoint())  
        {  
            _y = temp;  
            throw new ArgumentException("Invalid Y coordinate value.");  
        }  
    }  
}  
```  
  
## <a name="coding-udt-methods"></a><span data-ttu-id="332b9-191">UDT 메서드 코딩</span><span class="sxs-lookup"><span data-stu-id="332b9-191">Coding UDT Methods</span></span>  
 <span data-ttu-id="332b9-192">UDT 메서드를 코딩하는 경우 사용된 알고리즘이 시간에 따라 변경될 수 있는지 여부를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-192">When coding UDT methods, consider whether the algorithm used could possibly change over time.</span></span> <span data-ttu-id="332b9-193">변경되는 경우 UDT에서 사용하는 메서드에 대해 별도의 클래스를 만들어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-193">If so, you may want to consider creating a separate class for the methods your UDT uses.</span></span> <span data-ttu-id="332b9-194">알고리즘이 변경되면 새 코드를 사용하여 클래스를 다시 컴파일하고 UDT에 영향을 주지 않고 어셈블리를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-194">If the algorithm changes, you can recompile the class with the new code and load the assembly into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without affecting the UDT.</span></span> <span data-ttu-id="332b9-195">대체로 [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY 문을 사용하여 UDT를 다시 로드할 수 있지만 이 경우 기존 데이터에서 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-195">In many cases UDTs can be reloaded using the [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY statement, but that could potentially cause problems with existing data.</span></span> <span data-ttu-id="332b9-196">예를 들어 `Currency` **AdventureWorks** 예제 데이터베이스에 포함 된 UDT는 **convertcurrency** 함수를 사용 하 여 별도의 클래스에 구현 된 통화 값을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-196">For example, the `Currency` UDT included with the **AdventureWorks** sample database uses a **ConvertCurrency** function to convert currency values, which is implemented in a separate class.</span></span> <span data-ttu-id="332b9-197">변환 알고리즘이 미래에 예기치 않은 방식으로 변경되거나 새 기능이 필요할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-197">It is possible that conversion algorithms may change in unpredictable ways in the future, or that new functionality may be required.</span></span> <span data-ttu-id="332b9-198">**Convertcurrency** 함수를 `Currency` UDT 구현에서 분리 하면 나중에 변경 하는 것을 계획할 때 유연성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-198">Separating the **ConvertCurrency** function from the `Currency` UDT implementation provides greater flexibility when planning for future changes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="332b9-199">예제</span><span class="sxs-lookup"><span data-stu-id="332b9-199">Example</span></span>  
 <span data-ttu-id="332b9-200">클래스에는 거리 `Point` 를 계산 하기 위한 세 가지 간단한 메서드인 **distance**, **Distancefrom** 및 **DistanceFromXY**가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-200">The `Point` class contains three simple methods for calculating distance: **Distance**, **DistanceFrom** and **DistanceFromXY**.</span></span> <span data-ttu-id="332b9-201">각 메서드는 `double`에서 0까지의 거리, 지정된 점에서 `Point`까지의 거리 및 지정된 X 및 Y 좌표에서 `Point`까지의 거리를 계산하는 `Point`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-201">Each returns a `double` calculating the distance from `Point` to zero, the distance from a specified point to `Point`, and the distance from specified X and Y coordinates to `Point`.</span></span> <span data-ttu-id="332b9-202">각 호출에 대 한 **Distance** 및 **DistanceFromXY** **distancefrom** 는 각 메서드에 서로 다른 인수를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-202">**Distance** and **DistanceFrom** each call **DistanceFromXY**, and demonstrate how to use different arguments for each method.</span></span>  
  
```vb  
' Distance from 0 to Point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function Distance() As Double  
    Return DistanceFromXY(0, 0)  
End Function  
  
' Distance from Point to the specified point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFrom(ByVal pFrom As Point) As Double  
    Return DistanceFromXY(pFrom.X, pFrom.Y)  
End Function  
  
' Distance from Point to the specified x and y values.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFromXY(ByVal ix As Int32, ByVal iy As Int32) _  
    As Double  
    Return Math.Sqrt(Math.Pow(ix - _x, 2.0) + Math.Pow(iy - _y, 2.0))  
End Function  
```  
  
```csharp  
// Distance from 0 to Point.  
[SqlMethod(OnNullCall = false)]  
public Double Distance()  
{  
    return DistanceFromXY(0, 0);  
}  
  
// Distance from Point to the specified point.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFrom(Point pFrom)  
{  
    return DistanceFromXY(pFrom.X, pFrom.Y);  
}  
  
// Distance from Point to the specified x and y values.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFromXY(Int32 iX, Int32 iY)  
{  
    return Math.Sqrt(Math.Pow(iX - _x, 2.0) + Math.Pow(iY - _y, 2.0));  
}  
```  
  
### <a name="using-sqlmethod-attributes"></a><span data-ttu-id="332b9-203">SqlMethod 특성 사용</span><span class="sxs-lookup"><span data-stu-id="332b9-203">Using SqlMethod Attributes</span></span>  
 <span data-ttu-id="332b9-204">`Microsoft.SqlServer.Server.SqlMethodAttribute` 클래스는 Null 호출 동작에 결정성을 지정하고 메서드가 변경자(mutator)인지 여부를 지정하기 위해 메서드 정의를 표시하는 데 사용할 수 있는 사용자 지정 특성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-204">The `Microsoft.SqlServer.Server.SqlMethodAttribute` class provides custom attributes that can be used to mark method definitions in order to specify determinism, on null call behavior, and to specify whether a method is a mutator.</span></span> <span data-ttu-id="332b9-205">이러한 속성에 대해서는 기본값이 사용되며, 사용자 지정 특성은 기본값이 아닌 값이 필요한 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-205">Default values for these properties are assumed, and the custom attribute is only used when a non-default value is needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="332b9-206">`SqlMethodAttribute` 클래스는 `SqlFunctionAttribute` 클래스에서 상속되므로 `SqlMethodAttribute`는 `FillRowMethodName`의 `TableDefinition` 및 `SqlFunctionAttribute` 필드에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-206">The `SqlMethodAttribute` class inherits from the `SqlFunctionAttribute` class, so `SqlMethodAttribute` inherits the `FillRowMethodName` and `TableDefinition` fields from `SqlFunctionAttribute`.</span></span> <span data-ttu-id="332b9-207">즉, 적합하지 않은 테이블 반환 메서드를 쓸 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-207">This implies that it is possible to write a table-valued method, which is not the case.</span></span> <span data-ttu-id="332b9-208">메서드가 컴파일되고 어셈블리를 배포 하지만, 반환 형식에 대 한 오류는 `IEnumerable` 런타임에 "' 어셈블리의 ' ' 클래스에 있는" 메서드, 속성 또는 필드 ' ' \<name> 의 \<class> \<assembly> 반환 형식이 잘못 되었습니다. "라는 메시지와 함께 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-208">The method compiles and the assembly deploys, but an error about the `IEnumerable` return type is raised at runtime with the following message: "Method, property, or field '\<name>' in class '\<class>' in assembly '\<assembly>' has invalid return type."</span></span>  
  
 <span data-ttu-id="332b9-209">다음 표에서는 UDT 메서드에 사용할 수 있는 몇 개의 관련된 `Microsoft.SqlServer.Server.SqlMethodAttribute` 속성에 대해 설명하고 해당 기본값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-209">The following table describes some of the relevant `Microsoft.SqlServer.Server.SqlMethodAttribute` properties that can be used in UDT methods, and lists their default values.</span></span>  
  
 <span data-ttu-id="332b9-210">DataAccess</span><span class="sxs-lookup"><span data-stu-id="332b9-210">DataAccess</span></span>  
 <span data-ttu-id="332b9-211">함수가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 로컬 인스턴스에 저장된 사용자 데이터에 대한 액세스를 수행하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-211">Indicates whether the function involves access to user data stored in the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="332b9-212">기본값은 `DataAccessKind`.`None`입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-212">Default is `DataAccessKind`.`None`.</span></span>  
  
 <span data-ttu-id="332b9-213">IsDeterministic</span><span class="sxs-lookup"><span data-stu-id="332b9-213">IsDeterministic</span></span>  
 <span data-ttu-id="332b9-214">동일한 입력 값과 동일한 데이터베이스 상태가 지정된 경우 함수에서 항상 동일한 값을 출력하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-214">Indicates whether the function produces the same output values given the same input values and the same database state.</span></span> <span data-ttu-id="332b9-215">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-215">Default is `false`.</span></span>  
  
 <span data-ttu-id="332b9-216">IsMutator</span><span class="sxs-lookup"><span data-stu-id="332b9-216">IsMutator</span></span>  
 <span data-ttu-id="332b9-217">메서드로 인해 UDT 인스턴스의 상태가 변경되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-217">Indicates whether the method causes a state change in the UDT instance.</span></span> <span data-ttu-id="332b9-218">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-218">Default is `false`.</span></span>  
  
 <span data-ttu-id="332b9-219">IsPrecise</span><span class="sxs-lookup"><span data-stu-id="332b9-219">IsPrecise</span></span>  
 <span data-ttu-id="332b9-220">함수가 부동 소수점 연산과 같은 부정확한 계산을 수행하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-220">Indicates whether the function involves imprecise computations, such as floating point operations.</span></span> <span data-ttu-id="332b9-221">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-221">Default is `false`.</span></span>  
  
 <span data-ttu-id="332b9-222">OnNullCall</span><span class="sxs-lookup"><span data-stu-id="332b9-222">OnNullCall</span></span>  
 <span data-ttu-id="332b9-223">Null 참조 입력 인수를 지정할 때 메서드가 호출되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-223">Indicates whether the method is called when null reference input arguments are specified.</span></span> <span data-ttu-id="332b9-224">기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-224">Default is `true`.</span></span>  
  
### <a name="example"></a><span data-ttu-id="332b9-225">예제</span><span class="sxs-lookup"><span data-stu-id="332b9-225">Example</span></span>  
 <span data-ttu-id="332b9-226">`Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator` 속성을 사용하면 UDT 인스턴스의 상태 변경을 허용하는 메서드를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-226">The `Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator` property allows you to mark a method that allows a change in the state of an instance of a UDT.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="332b9-227">에서는 UPDATE 문의 SET 절에 두 개의 UDT 속성을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-227">does not allow you to set two UDT properties in the SET clause of one UPDATE statement.</span></span> <span data-ttu-id="332b9-228">하지만 메서드를 두 멤버를 변경하는 변경자(mutator)로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-228">However, you can have a method marked as a mutator that changes the two members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="332b9-229">변경자(mutator) 메서드는 쿼리에 사용할 수 없으며,</span><span class="sxs-lookup"><span data-stu-id="332b9-229">Mutator methods are not allowed in queries.</span></span> <span data-ttu-id="332b9-230">대입문이나 데이터 수정 문에서만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-230">They can be called only in assignment statements or data modification statements.</span></span> <span data-ttu-id="332b9-231">변경자(mutator)로 표시된 메서드에서 `void`를 반환하지 않는 경우(Visual Basic의 경우 `Sub`가 아님) CREATE TYPE이 오류로 인해 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-231">If a method marked as mutator does not return `void` (or is not a `Sub` in Visual Basic), CREATE TYPE fails with an error.</span></span>  
  
 <span data-ttu-id="332b9-232">다음 문에서는 `Triangles` 메서드가 포함된 `Rotate` UDT가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-232">The following statement assumes the existence of a `Triangles` UDT that has a `Rotate` method.</span></span> <span data-ttu-id="332b9-233">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE 문에서는 `Rotate` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-233">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] update statement invokes the `Rotate` method:</span></span>  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 <span data-ttu-id="332b9-234">`Rotate` 메서드는 `SqlMethod`를 `IsMutator`로 설정하는 `true` 특성으로 데코레이팅되어 있으므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 해당 메서드를 변경자(mutator) 메서드로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-234">The `Rotate` method is decorated with the `SqlMethod` attribute setting `IsMutator` to `true` so that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can mark the method as a mutator method.</span></span> <span data-ttu-id="332b9-235">또한 이 코드에서는 `OnNullCall`을 `false`로 설정하여, Null 참조인 입력 매개 변수가 있을 경우 메서드에서 Null 참조(Visual Basic의 경우 `Nothing`)를 반환한다고 서버에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-235">The code also sets `OnNullCall` to `false`, which indicates to the server that the method returns a null reference (`Nothing` in Visual Basic) if any of the input parameters are null references.</span></span>  
  
```vb  
<SqlMethod(IsMutator:=True, OnNullCall:=False)> _  
Public Sub Rotate(ByVal anglex as Double, _  
  ByVal angley as Double, ByVal anglez As Double)   
   RotateX(anglex)  
   RotateY(angley)  
   RotateZ(anglez)  
End Sub  
```  
  
```csharp  
[SqlMethod(IsMutator = true, OnNullCall = false)]  
public void Rotate(double anglex, double angley, double anglez)   
{  
   RotateX(anglex);  
   RotateY(angley);  
   RotateZ(anglez);  
}  
```  
  
## <a name="implementing-a-udt-with-a-user-defined-format"></a><span data-ttu-id="332b9-236">사용자 정의 형식으로 UDT 구현</span><span class="sxs-lookup"><span data-stu-id="332b9-236">Implementing a UDT with a User-Defined Format</span></span>  
 <span data-ttu-id="332b9-237">사용자 정의 형식으로 UDT를 구현하는 경우 UDT 데이터 직렬화 및 역직렬화를 처리할 Microsoft.SqlServer.Server.IBinarySerialize 인터페이스를 구현하는 `Read` 및 `Write` 메서드를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-237">When implementing a UDT with a user-defined format, you must implement `Read` and `Write` methods that implement the Microsoft.SqlServer.Server.IBinarySerialize interface to handle serializing and deserializing UDT data.</span></span> <span data-ttu-id="332b9-238">또한 `MaxByteSize`의 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 속성을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-238">You must also specify the `MaxByteSize` property of the `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`.</span></span>  
  
### <a name="the-currency-udt"></a><span data-ttu-id="332b9-239">Currency UDT</span><span class="sxs-lookup"><span data-stu-id="332b9-239">The Currency UDT</span></span>  
 <span data-ttu-id="332b9-240">`Currency` UDT는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]부터 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]와 함께 설치할 수 있는 CLR 예제에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-240">The `Currency` UDT is included with the CLR samples that can be installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="332b9-241">`Currency` UDT는 특정 culture의 화폐 시스템에서 금액 처리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-241">The `Currency` UDT supports handling amounts of money in the monetary system of a particular culture.</span></span> <span data-ttu-id="332b9-242">두 개의 필드를 정의해야 합니다. `string`에 대한 `CultureInfo`은 통화를 발행한 주체(예: en-us)를 지정하고 `decimal`에 대한 `CurrencyValue`은 금액을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-242">You must define two fields: a `string` for `CultureInfo`, which specifies who issued the currency (en-us, for example) and a `decimal` for `CurrencyValue`, the amount of money.</span></span>  
  
 <span data-ttu-id="332b9-243">비교를 위해 서버에서 사용되지는 않지만 `Currency` UDT는 단일 메서드 `System.IComparable`를 노출하는 `System.IComparable.CompareTo` 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-243">Although it is not used by the server for performing comparisons, the `Currency` UDT implements the `System.IComparable` interface, which exposes a single method, `System.IComparable.CompareTo`.</span></span> <span data-ttu-id="332b9-244">이 인터페이스는 culture 내에서 통화 값을 정확하게 비교하거나 정렬해야 하는 경우에 클라이언트 쪽에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-244">This is used on the client side in situations where it is desirable to accurately compare or order currency values within cultures.</span></span>  
  
 <span data-ttu-id="332b9-245">CLR에서 실행되는 코드는 통화 값과 별도로 culture를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-245">Code running in the CLR compares the culture separately from the currency value.</span></span> <span data-ttu-id="332b9-246">[!INCLUDE[tsql](../../includes/tsql-md.md)] 코드의 경우 다음 동작에 의해 비교가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-246">For [!INCLUDE[tsql](../../includes/tsql-md.md)] code, the following actions determine the comparison:</span></span>  
  
1.  <span data-ttu-id="332b9-247">`IsByteOrdered` 특성을 true로 설정하여 디스크에 저장된 이진 표현을 비교에 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-247">Set the `IsByteOrdered` attribute to true, which tells [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use the persisted binary representation on disk for comparisons.</span></span>  
  
2.  <span data-ttu-id="332b9-248">`Write` UDT에 대해 `Currency` 메서드를 사용하여 UDT가 디스크에 유지되는 방법 및 [!INCLUDE[tsql](../../includes/tsql-md.md)] 작업을 위해 UDT 값이 비교 및 정렬되는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-248">Use the `Write` method for the `Currency` UDT to determine how the UDT is persisted on disk and therefore how UDT values are compared and ordered for [!INCLUDE[tsql](../../includes/tsql-md.md)] operations.</span></span>  
  
3.  <span data-ttu-id="332b9-249">다음 이진 형식을 사용하여 `Currency` UDT를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-249">Save the `Currency` UDT using the following binary format:</span></span>  
  
    1.  <span data-ttu-id="332b9-250">오른쪽에 Null 문자를 채워 바이트 0-19에 대한 UTF-16 인코딩 문자열로 culture를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-250">Save the culture as a UTF-16 encoded string for bytes 0-19 with padding to the right with null characters.</span></span>  
  
    2.  <span data-ttu-id="332b9-251">바이트 20 이상을 사용하여 통화의 10진수 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-251">Use bytes 20 and above to contain the decimal value of the currency.</span></span>  
  
 <span data-ttu-id="332b9-252">패딩의 목적은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드에서 한 UDT와 다른 UDT를 비교할 때 culture 바이트는 culture 바이트와 비교하고 통화 바이트 값은 통화 바이트 값과 비교하도록 culture를 통화 값과 완전히 분리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-252">The purpose of the padding is to ensure that the culture is completely separated from the currency value, so that when one UDT is compared against another in [!INCLUDE[tsql](../../includes/tsql-md.md)] code, culture bytes are compared against culture bytes, and currency byte values are compared against currency byte values.</span></span>  
  
 <span data-ttu-id="332b9-253">UDT에 대 한 전체 코드 목록을 보려면 `Currency` [SQL Server 데이터베이스 엔진 샘플](https://msftengprodsamples.codeplex.com/)에서 CLR 예제를 설치 하는 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="332b9-253">For the complete code listing for the `Currency` UDT, follow the directions for installing the CLR samples in [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).</span></span>  
  
### <a name="currency-attributes"></a><span data-ttu-id="332b9-254">통화 특성</span><span class="sxs-lookup"><span data-stu-id="332b9-254">Currency Attributes</span></span>  
 <span data-ttu-id="332b9-255">`Currency` UDT는 다음 특성을 사용하여 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-255">The `Currency` UDT is defined with the following attributes.</span></span>  
  
```vb  
<Serializable(), Microsoft.SqlServer.Server.SqlUserDefinedType( _  
    Microsoft.SqlServer.Server.Format.UserDefined, _  
    IsByteOrdered:=True, MaxByteSize:=32), _  
    CLSCompliant(False)> _  
Public Structure Currency  
Implements INullable, IComparable, _  
Microsoft.SqlServer.Server.IBinarySerialize  
```  
  
```csharp  
[Serializable]  
[SqlUserDefinedType(Format.UserDefined,   
    IsByteOrdered = true, MaxByteSize = 32)]  
    [CLSCompliant(false)]  
    public struct Currency : INullable, IComparable, IBinarySerialize  
    {  
```  
  
## <a name="creating-read-and-write-methods-with-ibinaryserialize"></a><span data-ttu-id="332b9-256">IBinarySerialize를 사용하여 읽기 및 쓰기 메서드 만들기</span><span class="sxs-lookup"><span data-stu-id="332b9-256">Creating Read and Write Methods with IBinarySerialize</span></span>  
 <span data-ttu-id="332b9-257">`UserDefined` 직렬화 형식을 선택하는 경우 `IBinarySerialize` 인터페이스를 구현하고 고유한 `Read` 및 `Write` 메서드도 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-257">When you choose `UserDefined` serialization format, you also must implement the `IBinarySerialize` interface and create your own `Read` and `Write` methods.</span></span> <span data-ttu-id="332b9-258">`Currency` UDT의 다음 프로시저에서는 `System.IO.BinaryReader` 및 `System.IO.BinaryWriter`를 사용하여 UDT를 읽고 씁니다.</span><span class="sxs-lookup"><span data-stu-id="332b9-258">The following procedures from the `Currency` UDT use the `System.IO.BinaryReader` and `System.IO.BinaryWriter` to read from and write to the UDT.</span></span>  
  
```vb  
' IBinarySerialize methods  
' The binary layout is as follow:  
'    Bytes 0 - 19: Culture name, padded to the right with null  
'    characters, UTF-16 encoded  
'    Bytes 20+: Decimal value of money  
' If the culture name is empty, the currency is null.  
Public Sub Write(ByVal w As System.IO.BinaryWriter) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Write  
    If Me.IsNull Then  
        w.Write(nullMarker)  
        w.Write(System.Convert.ToDecimal(0))  
        Return  
    End If  
  
    If cultureName.Length > cultureNameMaxSize Then  
        Throw New ApplicationException(String.Format(CultureInfo.CurrentUICulture, _  
           "{0} is an invalid culture name for currency as it is too long.", cultureNameMaxSize))  
    End If  
  
    Dim paddedName As String = cultureName.PadRight(cultureNameMaxSize, CChar(vbNullChar))  
  
    For i As Integer = 0 To cultureNameMaxSize - 1  
        w.Write(paddedName(i))  
    Next i  
  
    ' Normalize decimal value to two places  
    currencyVal = Decimal.Floor(currencyVal * 100) / 100  
    w.Write(currencyVal)  
End Sub  
  
Public Sub Read(ByVal r As System.IO.BinaryReader) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Read  
    Dim name As Char() = r.ReadChars(cultureNameMaxSize)  
    Dim stringEnd As Integer = Array.IndexOf(name, CChar(vbNullChar))  
  
    If stringEnd = 0 Then  
        cultureName = Nothing  
        Return  
    End If  
  
    cultureName = New String(name, 0, stringEnd)  
    currencyVal = r.ReadDecimal()  
End Sub  
  
```  
  
```csharp  
// IBinarySerialize methods  
// The binary layout is as follow:  
//    Bytes 0 - 19:Culture name, padded to the right   
//    with null characters, UTF-16 encoded  
//    Bytes 20+:Decimal value of money  
// If the culture name is empty, the currency is null.  
public void Write(System.IO.BinaryWriter w)  
{  
    if (this.IsNull)  
    {  
        w.Write(nullMarker);  
        w.Write((decimal)0);  
        return;  
    }  
  
    if (cultureName.Length > cultureNameMaxSize)  
    {  
        throw new ApplicationException(string.Format(  
            CultureInfo.InvariantCulture,   
            "{0} is an invalid culture name for currency as it is too long.",   
            cultureNameMaxSize));  
    }  
  
    String paddedName = cultureName.PadRight(cultureNameMaxSize, '\0');  
    for (int i = 0; i < cultureNameMaxSize; i++)  
    {  
        w.Write(paddedName[i]);  
    }  
  
    // Normalize decimal value to two places  
    currencyValue = Decimal.Floor(currencyValue * 100) / 100;  
    w.Write(currencyValue);  
}  
public void Read(System.IO.BinaryReader r)  
{  
    char[] name = r.ReadChars(cultureNameMaxSize);  
    int stringEnd = Array.IndexOf(name, '\0');  
  
    if (stringEnd == 0)  
    {  
        cultureName = null;  
        return;  
    }  
  
    cultureName = new String(name, 0, stringEnd);  
    currencyValue = r.ReadDecimal();  
}  
```  
  
 <span data-ttu-id="332b9-259">UDT에 대 한 전체 코드 목록은 `Currency` [SQL Server 데이터베이스 엔진 샘플](https://msftengprodsamples.codeplex.com/)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="332b9-259">For the complete code listing for the `Currency` UDT, see [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="332b9-260">참고 항목</span><span class="sxs-lookup"><span data-stu-id="332b9-260">See Also</span></span>  
 [<span data-ttu-id="332b9-261">사용자 정의 형식 만들기</span><span class="sxs-lookup"><span data-stu-id="332b9-261">Creating a User-Defined Type</span></span>](creating-user-defined-types.md)  
  
