---
title: CLR 매개 변수 데이터 매핑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlBinary data type
- SqlInt16 data type
- SqlMoney data type
- SqlString data type
- SqlSingle data type
- data types [CLR integration]
- SqlInt64 data type
- SqlDateTime data type
- SqlXml data type
- SqlBoolean data type
- SqlDecimal data type
- SqlBytes data type
- mapping data types [CLR integration]
- SqlChars data type
- SqlInt32 data type
ms.assetid: 89b43ee9-b9ad-4281-a4bf-c7c8d116daa2
author: rothja
ms.author: jroth
ms.openlocfilehash: 7025c5180eac793534961af63df9ac701c95c03f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742279"
---
# <a name="mapping-clr-parameter-data"></a><span data-ttu-id="aceb4-102">CLR 매개 변수 데이터 매핑</span><span class="sxs-lookup"><span data-stu-id="aceb4-102">Mapping CLR Parameter Data</span></span>
  <span data-ttu-id="aceb4-103">다음 표에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식, 네임 스페이스의에 대 한 CLR (공용 언어 런타임)의 해당 형식 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `System.Data.SqlTypes` 및 .NET FRAMEWORK의 해당 네이티브 clr에 해당 하는 데이터 형식을 보여 줍니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="aceb4-103">The following table lists [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, their equivalents in the common language runtime (CLR) for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the `System.Data.SqlTypes` namespace, and their native CLR equivalents in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="aceb4-104">**SQL Server 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="aceb4-104">**SQL Server data type**</span></span>|<span data-ttu-id="aceb4-105">System.Data.SqlTypes 또는 Microsoft.SqlServer.Types의 형식</span><span class="sxs-lookup"><span data-stu-id="aceb4-105">Type (in System.Data.SqlTypes or Microsoft.SqlServer.Types)</span></span>|<span data-ttu-id="aceb4-106">**CLR 데이터 형식(.NET Framework)**</span><span class="sxs-lookup"><span data-stu-id="aceb4-106">**CLR data type (.NET Framework)**</span></span>|  
|`bigint`|`SqlInt64`|<span data-ttu-id="aceb4-107">**Int64, Nullable\<Int64>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-107">**Int64, Nullable\<Int64>**</span></span>|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|<span data-ttu-id="aceb4-108">**부울, Nullable\<Boolean>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-108">**Boolean, Nullable\<Boolean>**</span></span>|  
|`char`|<span data-ttu-id="aceb4-109">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-109">None</span></span>|<span data-ttu-id="aceb4-110">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-110">None</span></span>|  
|`cursor`|<span data-ttu-id="aceb4-111">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-111">None</span></span>|<span data-ttu-id="aceb4-112">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-112">None</span></span>|  
|`date`|`SqlDateTime`|<span data-ttu-id="aceb4-113">**DateTime, Nullable\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-113">**DateTime, Nullable\<DateTime>**</span></span>|  
|`datetime`|`SqlDateTime`|<span data-ttu-id="aceb4-114">**DateTime, Nullable\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-114">**DateTime, Nullable\<DateTime>**</span></span>|  
|`datetime2`|<span data-ttu-id="aceb4-115">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-115">None</span></span>|<span data-ttu-id="aceb4-116">**DateTime, Nullable\<DateTime>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-116">**DateTime, Nullable\<DateTime>**</span></span>|  
|`DATETIMEOFFSET`|`None`|<span data-ttu-id="aceb4-117">**DateTimeOffset, Nullable\<DateTimeOffset>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-117">**DateTimeOffset, Nullable\<DateTimeOffset>**</span></span>|  
|`decimal`|`SqlDecimal`|<span data-ttu-id="aceb4-118">**Decimal, Nullable\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-118">**Decimal, Nullable\<Decimal>**</span></span>|  
|`float`|`SqlDouble`|<span data-ttu-id="aceb4-119">**Double, Nullable\<Double>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-119">**Double, Nullable\<Double>**</span></span>|  
|`geography`|`SqlGeography`<br /><br /> <span data-ttu-id="aceb4-120">`SqlGeography`는 SQL Server와 함께 설치 되 고 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [기능 팩](https://www.microsoft.com/download/details.aspx?id=53164)에서 다운로드할 수 있는 Microsoft.SqlServer.Types.dll에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-120">`SqlGeography` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="aceb4-121">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-121">None</span></span>|  
|`geometry`|`SqlGeometry`<br /><br /> <span data-ttu-id="aceb4-122">`SqlGeometry`는 SQL Server와 함께 설치 되 고 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [기능 팩](https://www.microsoft.com/download/details.aspx?id=53164)에서 다운로드할 수 있는 Microsoft.SqlServer.Types.dll에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-122">`SqlGeometry` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="aceb4-123">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-123">None</span></span>|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> <span data-ttu-id="aceb4-124">`SqlHierarchyId`는 SQL Server와 함께 설치 되 고 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [기능 팩](https://www.microsoft.com/download/details.aspx?id=53164)에서 다운로드할 수 있는 Microsoft.SqlServer.Types.dll에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-124">`SqlHierarchyId` is defined in Microsoft.SqlServer.Types.dll, which is installed with SQL Server and can be downloaded from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][feature pack](https://www.microsoft.com/download/details.aspx?id=53164).</span></span>|<span data-ttu-id="aceb4-125">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-125">None</span></span>|  
|`image`|<span data-ttu-id="aceb4-126">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-126">None</span></span>|<span data-ttu-id="aceb4-127">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-127">None</span></span>|  
|`int`|`SqlInt32`|<span data-ttu-id="aceb4-128">**Int32, Nullable\<Int32>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-128">**Int32, Nullable\<Int32>**</span></span>|  
|`money`|`SqlMoney`|<span data-ttu-id="aceb4-129">**Decimal, Nullable\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-129">**Decimal, Nullable\<Decimal>**</span></span>|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|<span data-ttu-id="aceb4-130">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-130">None</span></span>|<span data-ttu-id="aceb4-131">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-131">None</span></span>|  
|`numeric`|`SqlDecimal`|<span data-ttu-id="aceb4-132">**Decimal, Nullable\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-132">**Decimal, Nullable\<Decimal>**</span></span>|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> <span data-ttu-id="aceb4-133">`SQLChars`는 데이터 전송 및 액세스에 더 적합하고 `SQLString`은 문자열 작업에 더 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-133">`SQLChars` is a better match for data transfer and access, and `SQLString` is a better match for performing String operations.</span></span>|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|<span data-ttu-id="aceb4-134">**Char, String, Char [], Nullable\<char>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-134">**Char, String, Char[], Nullable\<char>**</span></span>|  
|`real`|<span data-ttu-id="aceb4-135">`SqlSingle`(`SqlSingle` 범위, 단, `real`보다 큼)</span><span class="sxs-lookup"><span data-stu-id="aceb4-135">`SqlSingle` (the range of `SqlSingle`, however, is larger than `real`)</span></span>|<span data-ttu-id="aceb4-136">**단일, Nullable\<Single>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-136">**Single, Nullable\<Single>**</span></span>|  
|`rowversion`|<span data-ttu-id="aceb4-137">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-137">None</span></span>|`Byte[]`|  
|`smallint`|`SqlInt16`|<span data-ttu-id="aceb4-138">**Int16, Nullable\<Int16>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-138">**Int16, Nullable\<Int16>**</span></span>|  
|`smallmoney`|`SqlMoney`|<span data-ttu-id="aceb4-139">**Decimal, Nullable\<Decimal>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-139">**Decimal, Nullable\<Decimal>**</span></span>|  
|`sql_variant`|<span data-ttu-id="aceb4-140">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-140">None</span></span>|`Object`|  
|`table`|<span data-ttu-id="aceb4-141">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-141">None</span></span>|<span data-ttu-id="aceb4-142">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-142">None</span></span>|  
|`text`|<span data-ttu-id="aceb4-143">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-143">None</span></span>|<span data-ttu-id="aceb4-144">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-144">None</span></span>|  
|`time`|<span data-ttu-id="aceb4-145">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-145">None</span></span>|<span data-ttu-id="aceb4-146">**TimeSpan, Nullable\<TimeSpan>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-146">**TimeSpan, Nullable\<TimeSpan>**</span></span>|  
|`timestamp`|<span data-ttu-id="aceb4-147">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-147">None</span></span>|<span data-ttu-id="aceb4-148">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-148">None</span></span>|  
|`tinyint`|`SqlByte`|<span data-ttu-id="aceb4-149">**바이트, Nullable\<Byte>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-149">**Byte, Nullable\<Byte>**</span></span>|  
|`uniqueidentifier`|`SqlGuid`|<span data-ttu-id="aceb4-150">**Guid, Nullable\<Guid>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-150">**Guid, Nullable\<Guid>**</span></span>|  
|`User-defined type(UDT)`|<span data-ttu-id="aceb4-151">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-151">None</span></span>|<span data-ttu-id="aceb4-152">동일한 어셈블리 또는 종속 어셈블리의 사용자 정의 형식에 바인딩된 동일한 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-152">The same class that is bound to the user-defined type in the same assembly or a dependent assembly.</span></span>|  
|<span data-ttu-id="aceb4-153">**varbinary**</span><span class="sxs-lookup"><span data-stu-id="aceb4-153">**varbinary**</span></span>|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|<span data-ttu-id="aceb4-154">**byte, Byte [], Nullable\<byte>**</span><span class="sxs-lookup"><span data-stu-id="aceb4-154">**byte, Byte[], Nullable\<byte>**</span></span>|  
|`varchar`|<span data-ttu-id="aceb4-155">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-155">None</span></span>|<span data-ttu-id="aceb4-156">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-156">None</span></span>|  
|`xml`|`SqlXml`|<span data-ttu-id="aceb4-157">없음</span><span class="sxs-lookup"><span data-stu-id="aceb4-157">None</span></span>|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a><span data-ttu-id="aceb4-158">Out 매개 변수로 자동 데이터 형식 변환</span><span class="sxs-lookup"><span data-stu-id="aceb4-158">Automatic Data Type Conversion with Out Parameters</span></span>  
 <span data-ttu-id="aceb4-159">CLR 메서드는 `out` 한정자(Microsoft Visual C#) 또는 `<Out()> ByRef`(Microsoft Visual Basic)로 입력 매개 변수를 표시하여 호출 코드나 프로그램에 정보를 반환할 수 있습니다. 입력 매개 변수가 `System.Data.SqlTypes` 네임스페이스의 CLR 데이터 형식이고 호출 프로그램이 이에 해당하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 입력 매개 변수로 지정할 경우 CLR 메서드가 데이터 형식을 반환하면 자동으로 형식 변환이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-159">A CLR method can return information to the calling code or program by marking an input parameter with the `out` modifier (Microsoft Visual C#) or `<Out()> ByRef` (Microsoft Visual Basic) If the input parameter is a CLR data type in the `System.Data.SqlTypes` namespace, and the calling program specifies its equivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type as the input parameter, a type conversion occurs automatically when the CLR method returns the data type.</span></span>  
  
 <span data-ttu-id="aceb4-160">예를 들어 다음 CLR 저장 프로시저에는 `SqlInt32`(C#) 또는 `out`(Visual Basic)로 표시된 `<Out()> ByRef` CLR 데이터 형식의 입력 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-160">For example, the following CLR stored procedure has an input parameter of `SqlInt32` CLR data type that is marked with `out` (C#) or `<Out()> ByRef` (Visual Basic):</span></span>  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 <span data-ttu-id="aceb4-161">어셈블리가 데이터베이스에서 만들어진 후에는 저장 프로시저가 `int`의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 OUTPUT 매개 변수로 지정하는 다음 Transact-SQL을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-161">After the assembly is built and created in the database, the stored procedure is created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the following Transact-SQL, which specifies a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of `int` as an OUTPUT parameter:</span></span>  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 <span data-ttu-id="aceb4-162">CLR 저장 프로시저 호출되면 `SqlInt32` 데이터 형식이 자동으로 `int` 데이터 형식으로 변환되고 호출 프로그램에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-162">When the CLR stored procedure is called, the `SqlInt32` data type is automatically converted to an `int` data type, and returned to the calling program.</span></span>  
  
 <span data-ttu-id="aceb4-163">그러나 Out 매개 변수를 통해 모든 CLR 데이터 형식을 이에 해당하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식으로 변환할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-163">Not all CLR data types can be automatically converted to their equivalent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types through an out parameter, however.</span></span> <span data-ttu-id="aceb4-164">다음 표에서는 이러한 예외를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-164">The following table lists these exceptions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aceb4-165">**CLR 데이터 형식(SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="aceb4-165">**CLR data type (SQL Server)**</span></span>|<span data-ttu-id="aceb4-166">**SQL Server 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="aceb4-166">**SQL Server data type**</span></span>|  
|`Decimal`|<span data-ttu-id="aceb4-167">smallmoney</span><span class="sxs-lookup"><span data-stu-id="aceb4-167">smallmoney</span></span>|  
|`SqlMoney`|<span data-ttu-id="aceb4-168">smallmoney</span><span class="sxs-lookup"><span data-stu-id="aceb4-168">smallmoney</span></span>|  
|`Decimal`|<span data-ttu-id="aceb4-169">money</span><span class="sxs-lookup"><span data-stu-id="aceb4-169">money</span></span>|  
|`DateTime`|<span data-ttu-id="aceb4-170">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="aceb4-170">smalldatetime</span></span>|  
|`SQLDateTime`|<span data-ttu-id="aceb4-171">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="aceb4-171">smalldatetime</span></span>|  
  
## <a name="change-history"></a><span data-ttu-id="aceb4-172">변경 내역</span><span class="sxs-lookup"><span data-stu-id="aceb4-172">Change History</span></span>  
  
|<span data-ttu-id="aceb4-173">업데이트된 내용</span><span class="sxs-lookup"><span data-stu-id="aceb4-173">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="aceb4-174">`SqlGeography`, `SqlGeometry` 및 `SqlHierarchyId` 형식이 매핑 테이블에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aceb4-174">Added `SqlGeography`, `SqlGeometry`, and `SqlHierarchyId` types to the mapping table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aceb4-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aceb4-175">See Also</span></span>  
 [<span data-ttu-id="aceb4-176">.NET Framework의 SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="aceb4-176">SQL Server Data Types in the .NET Framework</span></span>](sql-server-data-types-in-the-net-framework.md)  
  
  
