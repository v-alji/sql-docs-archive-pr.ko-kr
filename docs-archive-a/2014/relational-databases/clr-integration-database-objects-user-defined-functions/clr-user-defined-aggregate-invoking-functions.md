---
title: CLR 사용자 정의 집계 함수 호출 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- aggregate functions [CLR integration]
- invoking user-defined aggregate functions
- user-defined functions [CLR integration]
ms.assetid: 5a188b50-7170-4069-acad-5de5c915f65d
author: rothja
ms.author: jroth
ms.openlocfilehash: 74e92563e01d0065c40619f3208aaf74691496c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651728"
---
# <a name="invoking-clr-user-defined-aggregate-functions"></a><span data-ttu-id="ea3cf-102">CLR 사용자 정의 집계 함수 호출</span><span class="sxs-lookup"><span data-stu-id="ea3cf-102">Invoking CLR User-Defined Aggregate Functions</span></span>
  <span data-ttu-id="ea3cf-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT 문에서 시스템 집계 함수에 적용되는 모든 규칙을 따르는 CLR(공용 언어 런타임) 사용자 정의 집계를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-103">In [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statements, you can invoke common language runtime (CLR) user-defined aggregates, subject to all the rules that apply to system aggregate functions.</span></span>  
  
 <span data-ttu-id="ea3cf-104">다음 추가 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-104">The following additional rules apply:</span></span>  
  
-   <span data-ttu-id="ea3cf-105">현재 사용자에게 사용자 정의 집계에 대한 `EXECUTE` 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-105">The current user must have `EXECUTE` permission on the user-defined aggregate.</span></span>  
  
-   <span data-ttu-id="ea3cf-106">사용자 정의 집계는 schema_name 형식의 두 부분으로 된 이름을 사용 하 여 호출 해야 합니다 *. udagg_name*.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-106">User-defined aggregates must be invoked using a two-part name in the form of *schema_name.udagg_name*.</span></span>  
  
-   <span data-ttu-id="ea3cf-107">사용자 정의 집계의 인수 형식은 문에 정의 된 대로 집계의 *input_type* 일치 하거나 암시적으로 변환 될 수 있어야 합니다 `CREATE AGGREGATE` .</span><span class="sxs-lookup"><span data-stu-id="ea3cf-107">The argument type of the user-defined aggregate must match or be implicitly convertible to the *input_type* of the aggregate, as defined in the `CREATE AGGREGATE` statement.</span></span>  
  
-   <span data-ttu-id="ea3cf-108">사용자 정의 집계의 반환 형식은 문의 *return_type* 와 일치 해야 합니다 `CREATE AGGREGATE` .</span><span class="sxs-lookup"><span data-stu-id="ea3cf-108">The return type of the user-defined aggregate must match the *return_type* in the `CREATE AGGREGATE` statement.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="ea3cf-109">예 1</span><span class="sxs-lookup"><span data-stu-id="ea3cf-109">Example 1</span></span>  
 <span data-ttu-id="ea3cf-110">테이블의 열에서 가져온 문자열 값 집합을 연결하는 사용자 정의 집계 함수의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-110">The following is an example of a user-defined aggregate function that concatenates a set of string values taken from a column in a table:</span></span>  
  
 <span data-ttu-id="ea3cf-111">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea3cf-111">[C#]</span></span>  
  
```  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
using System.IO;  
using System.Text;  
  
[Serializable]  
[SqlUserDefinedAggregate(  
    Format.UserDefined, //use clr serialization to serialize the intermediate result  
    IsInvariantToNulls = true, //optimizer property  
    IsInvariantToDuplicates = false, //optimizer property  
    IsInvariantToOrder = false, //optimizer property  
    MaxByteSize = 8000) //maximum size in bytes of persisted value  
]  
public class Concatenate : IBinarySerialize  
{  
    /// <summary>  
    /// The variable that holds the intermediate result of the concatenation  
    /// </summary>  
    private StringBuilder intermediateResult;  
  
    /// <summary>  
    /// Initialize the internal data structures  
    /// </summary>  
    public void Init()  
    {  
        this.intermediateResult = new StringBuilder();  
    }  
  
    /// <summary>  
    /// Accumulate the next value, not if the value is null  
    /// </summary>  
    /// <param name="value"></param>  
    public void Accumulate(SqlString value)  
    {  
        if (value.IsNull)  
        {  
            return;  
        }  
  
        this.intermediateResult.Append(value.Value).Append(',');  
    }  
  
    /// <summary>  
    /// Merge the partially computed aggregate with this aggregate.  
    /// </summary>  
    /// <param name="other"></param>  
    public void Merge(Concatenate other)  
    {  
        this.intermediateResult.Append(other.intermediateResult);  
    }  
  
    /// <summary>  
    /// Called at the end of aggregation, to return the results of the aggregation.  
    /// </summary>  
    /// <returns></returns>  
    public SqlString Terminate()  
    {  
        string output = string.Empty;  
        //delete the trailing comma, if any  
        if (this.intermediateResult != null  
            && this.intermediateResult.Length > 0)  
        {  
            output = this.intermediateResult.ToString(0, this.intermediateResult.Length - 1);  
        }  
  
        return new SqlString(output);  
    }  
  
    public void Read(BinaryReader r)  
    {  
        intermediateResult = new StringBuilder(r.ReadString());  
    }  
  
    public void Write(BinaryWriter w)  
    {  
        w.Write(this.intermediateResult.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="ea3cf-112">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="ea3cf-112">[Visual Basic]</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.IO  
Imports System.Text  
  
<Serializable(), SqlUserDefinedAggregate(Format.UserDefined, IsInvariantToNulls:=True, IsInvariantToDuplicates:=False, IsInvariantToOrder:=False, MaxByteSize:=8000)> _  
Public Class Concatenate  
    Implements IBinarySerialize  
  
    ''' <summary>  
    ''' The variable that holds the intermediate result of the concatenation  
    ''' </summary>  
    Private intermediateResult As StringBuilder  
  
    ''' <summary>  
    ''' Initialize the internal data structures  
    ''' </summary>  
    Public Sub Init()  
        Me.intermediateResult = New StringBuilder()  
    End Sub  
  
    ''' <summary>  
    ''' Accumulate the next value, not if the value is null  
    ''' </summary>  
    ''' <param name="value"></param>  
    Public Sub Accumulate(ByVal value As SqlString)  
        If value.IsNull Then  
            Return  
        End If  
  
        Me.intermediateResult.Append(value.Value).Append(","c)  
    End Sub  
    ''' <summary>  
    ''' Merge the partially computed aggregate with this aggregate.  
    ''' </summary>  
    ''' <param name="other"></param>  
    Public Sub Merge(ByVal other As Concatenate)  
        Me.intermediateResult.Append(other.intermediateResult)  
    End Sub  
  
    ''' <summary>  
    ''' Called at the end of aggregation, to return the results of the aggregation.  
    ''' </summary>  
    ''' <returns></returns>  
    Public Function Terminate() As SqlString  
        Dim output As String = String.Empty  
  
        'delete the trailing comma, if any  
        If Not (Me.intermediateResult Is Nothing) AndAlso Me.intermediateResult.Length > 0 Then  
            output = Me.intermediateResult.ToString(0, Me.intermediateResult.Length - 1)  
        End If  
  
        Return New SqlString(output)  
    End Function  
  
    Public Sub Read(ByVal r As BinaryReader) Implements IBinarySerialize.Read  
        intermediateResult = New StringBuilder(r.ReadString())  
    End Sub  
  
    Public Sub Write(ByVal w As BinaryWriter) Implements IBinarySerialize.Write  
        w.Write(Me.intermediateResult.ToString())  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="ea3cf-113">코드를 **MyAgg.dll**컴파일하면에서 다음과 같이 집계를 등록할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ea3cf-113">Once you compile the code into **MyAgg.dll**, you can register the aggregate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as follows:</span></span>  
  
```  
CREATE ASSEMBLY MyAgg FROM 'C:\MyAgg.dll';  
GO  
CREATE AGGREGATE MyAgg (@input nvarchar(200)) RETURNS nvarchar(max)  
EXTERNAL NAME MyAgg.Concatenate;  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ea3cf-114">/clr:pure 컴파일러 옵션을 사용하여 컴파일된 Visual C++ 데이터베이스 개체(예: 스칼라 반환 함수)는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-114">Visual C++ database objects, such as scalar-valued functions, that have been compiled with the /clr:pure compiler option are not supported for execution in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ea3cf-115">대부분의 집계와 마찬가지로, 많은 논리가 `Accumulate` 메서드에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-115">As with most aggregates, the bulk of the logic is in the `Accumulate` method.</span></span> <span data-ttu-id="ea3cf-116">여기서 `Accumulate` 메서드에 매개 변수로 전달되는 문자열이 `StringBuilder` 메서드에서 초기화된 `Init` 개체에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-116">Here, the string that is passed in as a parameter to the `Accumulate` method is appended to the `StringBuilder` object that was initialized in the `Init` method.</span></span> <span data-ttu-id="ea3cf-117">`Accumulate` 메서드가 처음으로 호출된 것이 아닐 경우 전달된 문자열을 추가하기 전에 `StringBuilder`에 쉼표도 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-117">Assuming that this is not the first time the `Accumulate` method has been called, a comma is also appended to the `StringBuilder` prior to appending the passed-in string.</span></span> <span data-ttu-id="ea3cf-118">계산 태스크를 마칠 때 `Terminate` 메서드가 호출되고 `StringBuilder`가 문자열로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-118">At the conclusion of the computational tasks, the `Terminate` method is called, which returns the `StringBuilder` as a string.</span></span>  
  
 <span data-ttu-id="ea3cf-119">예를 들어 다음 스키마가 있는 테이블을 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-119">For example, consider a table with the following schema:</span></span>  
  
```  
CREATE TABLE BookAuthors  
(  
   BookID   int       NOT NULL,  
   AuthorName    nvarchar(200) NOT NULL  
);  
```  
  
 <span data-ttu-id="ea3cf-120">그런 후에 다음 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-120">Then insert the following rows:</span></span>  
  
```  
INSERT BookAuthors VALUES(1, 'Johnson'),(2, 'Taylor'),(3, 'Steven'),(2, 'Mayler'),(3, 'Roberts'),(3, 'Michaels');  
```  
  
 <span data-ttu-id="ea3cf-121">그러면 다음 쿼리는 다음과 같은 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-121">The following query would then produce the following result:</span></span>  
  
```  
SELECT BookID, dbo.MyAgg(AuthorName)  
FROM BookAuthors  
GROUP BY BookID;  
```  
  
|<span data-ttu-id="ea3cf-122">BookID</span><span class="sxs-lookup"><span data-stu-id="ea3cf-122">BookID</span></span>|<span data-ttu-id="ea3cf-123">작성자 이름</span><span class="sxs-lookup"><span data-stu-id="ea3cf-123">Author Names</span></span>|  
|------------|------------------|  
|<span data-ttu-id="ea3cf-124">1</span><span class="sxs-lookup"><span data-stu-id="ea3cf-124">1</span></span>|<span data-ttu-id="ea3cf-125">Johnson</span><span class="sxs-lookup"><span data-stu-id="ea3cf-125">Johnson</span></span>|  
|<span data-ttu-id="ea3cf-126">2</span><span class="sxs-lookup"><span data-stu-id="ea3cf-126">2</span></span>|<span data-ttu-id="ea3cf-127">Taylor, Mayler</span><span class="sxs-lookup"><span data-stu-id="ea3cf-127">Taylor, Mayler</span></span>|  
|<span data-ttu-id="ea3cf-128">3</span><span class="sxs-lookup"><span data-stu-id="ea3cf-128">3</span></span>|<span data-ttu-id="ea3cf-129">Roberts, Michaels, Steven</span><span class="sxs-lookup"><span data-stu-id="ea3cf-129">Roberts, Michaels, Steven</span></span>|  
  
## <a name="example-2"></a><span data-ttu-id="ea3cf-130">예제 2</span><span class="sxs-lookup"><span data-stu-id="ea3cf-130">Example 2</span></span>  
 <span data-ttu-id="ea3cf-131">다음 예제에서는 `Accumulate` 메서드에 매개 변수 두 개를 가진 집계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-131">The following sample shows an aggregate that has two parameters on the `Accumulate` method.</span></span>  
  
 <span data-ttu-id="ea3cf-132">[C#]</span><span class="sxs-lookup"><span data-stu-id="ea3cf-132">[C#]</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
[Serializable]  
[SqlUserDefinedAggregate(  
    Format.Native,  
    IsInvariantToDuplicates = false,  
    IsInvariantToNulls = true,  
    IsInvariantToOrder = true,  
    IsNullIfEmpty = true,  
    Name = "WeightedAvg")]  
public struct WeightedAvg  
{  
    /// <summary>  
    /// The variable that holds the intermediate sum of all values multiplied by their weight  
    /// </summary>  
    private long sum;  
  
    /// <summary>  
    /// The variable that holds the intermediate sum of all weights  
    /// </summary>  
    private int count;  
  
    /// <summary>  
    /// Initialize the internal data structures  
    /// </summary>  
    public void Init()  
    {  
        sum = 0;  
        count = 0;  
    }  
  
    /// <summary>  
    /// Accumulate the next value, not if the value is null  
    /// </summary>  
    /// <param name="Value">Next value to be aggregated</param>  
    /// <param name="Weight">The weight of the value passed to Value parameter</param>  
    public void Accumulate(SqlInt32 Value, SqlInt32 Weight)  
    {  
        if (!Value.IsNull && !Weight.IsNull)  
        {  
            sum += (long)Value * (long)Weight;  
            count += (int)Weight;  
        }  
    }  
  
    /// <summary>  
    /// Merge the partially computed aggregate with this aggregate  
    /// </summary>  
    /// <param name="Group">The other partial results to be merged</param>  
    public void Merge(WeightedAvg Group)  
    {  
        sum += Group.sum;  
        count += Group.count;  
    }  
  
    /// <summary>  
    /// Called at the end of aggregation, to return the results of the aggregation.  
    /// </summary>  
    /// <returns>The weighted average of all inputed values</returns>  
    public SqlInt32 Terminate()  
    {  
        if (count > 0)  
        {  
            int value = (int)(sum / count);  
            return new SqlInt32(value);  
        }  
        else  
        {  
            return SqlInt32.Null;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="ea3cf-133">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="ea3cf-133">[Visual Basic]</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> _  
<Serializable(), SqlUserDefinedAggregate(Format.Native, _  
IsInvariantToDuplicates:=False, _  
IsInvariantToNulls:=True, _  
IsInvariantToOrder:=True, _  
IsNullIfEmpty:=True, _  
Name:="WeightedAvg")> _  
Public Class WeightedAvg  
  
    ''' <summary>  
    ''' The variable that holds the intermediate sum of all values multiplied by their weight  
    ''' </summary>  
    Private sum As Long  
  
    ''' <summary>  
    ''' The variable that holds the intermediate sum of all weights  
    ''' </summary>  
    Private count As Integer  
  
    ''' <summary>  
    ''' The variable that holds the intermediate sum of all weights  
    ''' </summary>  
    Public Sub Init()  
        sum = 0  
        count = 0  
    End Sub  
  
    ''' <summary>  
    ''' Accumulate the next value, not if the value is null  
    ''' </summary>  
    ''' <param name="Value">Next value to be aggregated</param>  
    ''' <param name="Weight">The weight of the value passed to Value parameter</param>  
    Public Sub Accumulate(ByVal Value As SqlInt32, ByVal Weight As SqlInt32)  
        If Not Value.IsNull AndAlso Not Weight.IsNull Then  
            sum += CType(Value, Long) * CType(Weight, Long)  
            count += CType(Weight, Integer)  
        End If  
    End Sub  
  
    ''' <summary>  
    ''' Merge the partially computed aggregate with this aggregate.  
    ''' </summary>  
    ''' <param name="Group">The other partial results to be merged</param>  
    Public Sub Merge(ByVal Group As WeightedAvg)  
        sum = Group.sum  
        count = Group.count  
    End Sub  
  
    ''' <summary>  
    ''' Called at the end of aggregation, to return the results of the aggregation.  
    ''' </summary>  
    ''' <returns>The weighted average of all inputed values</returns>  
    Public Function Terminate() As SqlInt32  
        If count > 0 Then  
            ''                        int value = (int)(sum / count);  
            ''          return new SqlInt32(value);  
            Dim value As Integer = CType(sum / count, Integer)  
            Return New SqlInt32(value)  
        Else  
            Return SqlInt32.Null  
        End If  
    End Function  
End Class  
```  
  
 <span data-ttu-id="ea3cf-134">C# 또는 Visual Basic 원본 코드를 컴파일한 후, 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-134">After you compile the C# or Visual Basic source code, run the following [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  <span data-ttu-id="ea3cf-135">이 스크립트에서는 DLL을 WghtAvg.dll이라고 하고 C 드라이브의 루트 디렉터리에 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-135">This script assumes that the DLL is called WghtAvg.dll and is in the root directory of your C drive.</span></span>  <span data-ttu-id="ea3cf-136">테스트라는 데이터베이스도 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-136">A database called test is also assumed.</span></span>  
  
```  
use test;  
go  
  
-- sp_configure 'clr enabled', 1;  
-- go  
  
--- RECONFIGURE WITH OVERRIDE;  
-- go  
  
IF EXISTS (SELECT name FROM systypes WHERE name = 'MyTableType')  
   DROP TYPE MyTableType;  
go  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'WeightedAvg')  
   DROP AGGREGATE WeightedAvg;  
go  
  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'MyClrCode')  
   DROP ASSEMBLY MyClrCode;  
go  
  
CREATE ASSEMBLY MyClrCode FROM 'C:\WghtAvg.dll';  
GO  
  
CREATE AGGREGATE WeightedAvg (@value int, @weight int) RETURNS int  
EXTERNAL NAME MyClrCode.WeightedAvg;  
go  
  
CREATE TYPE MyTableType AS table (ItemValue int, ItemWeight int);  
go  
  
DECLARE @myTable AS MyTableType;  
  
INSERT INTO @myTable VALUES(1, 4), (6, 1);  
  
SELECT dbo.WeightedAvg(ItemValue, ItemWeight) FROM @myTable;  
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea3cf-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea3cf-137">See Also</span></span>  
 [<span data-ttu-id="ea3cf-138">CLR 사용자 정의 집계</span><span class="sxs-lookup"><span data-stu-id="ea3cf-138">CLR User-Defined Aggregates</span></span>](clr-user-defined-aggregates.md)  
  
  
