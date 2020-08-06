---
title: UDT 데이터 검색 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SqlDataReader object
- ADO.NET [CLR integration]
- binding UDTs [CLR integration]
- UDTs [CLR integration], ADO.NET
- assemblies [CLR integration], user-defined types
- query parameters [CLR integration]
- user-defined types [CLR integration], ADO.NET
- bytes [CLR integration]
ms.assetid: 6a98ac8c-0e69-4c03-83a4-2062cb782049
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9133ea45069f76e7590f6b74d3c1e1cb98c7bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652876"
---
# <a name="retrieving-udt-data"></a><span data-ttu-id="c8503-102">UDT 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="c8503-102">Retrieving UDT Data</span></span>
  <span data-ttu-id="c8503-103">클라이언트에서 UDT(사용자 정의 형식)를 만들려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 UDT로 등록된 어셈블리를 클라이언트 애플리케이션에서 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-103">In order to create a user-defined type (UDT) on the client, the assembly that was registered as a UDT in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database must be available to the client application.</span></span> <span data-ttu-id="c8503-104">UDT 어셈블리는 애플리케이션과 같은 디렉터리나 GAC(전역 어셈블리 캐시)에 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-104">The UDT assembly can be placed in the same directory with the application, or in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="c8503-105">사용자의 프로젝트에서 어셈블리에 대한 참조를 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-105">You can also set a reference to the assembly in your project.</span></span>  
  
## <a name="requirements-for-using-udts-in-adonet"></a><span data-ttu-id="c8503-106">ADO.NET에서 UDT 사용을 위한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c8503-106">Requirements for Using UDTs in ADO.NET</span></span>  
 <span data-ttu-id="c8503-107">클라이언트에서 UDT를 만들려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 로드된 어셈블리와 클라이언트의 어셈블리가 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-107">The assembly loaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the assembly on the client must be compatible in order for the UDT to be created on the client.</span></span> <span data-ttu-id="c8503-108">`Native` 직렬화 형식으로 정의된 UDT의 경우 어셈블리가 구조적으로 호환되어야 하며,</span><span class="sxs-lookup"><span data-stu-id="c8503-108">For UDTs defined with the `Native` serialization format, the assemblies must be structurally compatible.</span></span> <span data-ttu-id="c8503-109">`UserDefined` 형식으로 정의된 어셈블리의 경우 클라이언트에서 어셈블리를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-109">For assemblies defined with the `UserDefined` format, the assembly must be available on the client.</span></span>  
  
 <span data-ttu-id="c8503-110">클라이언트에 UDT 어셈블리의 복사본이 없어도 테이블의 UDT 열에서 원시 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-110">You do not need a copy of the UDT assembly on the client in order to retrieve the raw data from a UDT column in a table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8503-111">**SqlClient** 는 udt 버전이 일치 하지 않거나 다른 문제가 발생 하는 경우 udt를 로드 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-111">**SqlClient** may fail to load a UDT in the event of mismatched UDT versions or other problems.</span></span> <span data-ttu-id="c8503-112">이 경우에는 일반적인 문제 해결 메커니즘을 사용하여 호출 애플리케이션에서 UDT를 포함하는 어셈블리를 찾지 못하는 이유를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="c8503-112">In this case, use regular troubleshooting mechanisms to determine why the assembly containing the UDT cannot be found by the calling application.</span></span> <span data-ttu-id="c8503-113">자세한 내용은 .NET Framework 설명서에서 제목이 "관리 디버깅 도우미를 사용하여 오류 진단"인 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c8503-113">For more information, read the topic titled "Diagnosing Errors with Managed Debugging Assistants" in the .NET Framework documentation.</span></span>  
  
## <a name="accessing-udts-with-a-sqldatareader"></a><span data-ttu-id="c8503-114">SqlDataReader를 사용하여 UDT 액세스</span><span class="sxs-lookup"><span data-stu-id="c8503-114">Accessing UDTs with a SqlDataReader</span></span>  
 <span data-ttu-id="c8503-115">클라이언트 코드에서 `System.Data.SqlClient.SqlDataReader`를 사용하여 UDT 열을 포함하는 결과 집합을 검색할 수 있습니다. 이러한 결과 집합은 개체의 인스턴스로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-115">A `System.Data.SqlClient.SqlDataReader` can be used from client code to retrieve a result set that contains a UDT column, which is exposed as an instance of the object.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c8503-116">예제</span><span class="sxs-lookup"><span data-stu-id="c8503-116">Example</span></span>  
 <span data-ttu-id="c8503-117">이 예에서는 `Main` 메서드를 사용하여 새로운 `SqlDataReader` 개체를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-117">This example shows how to use the `Main` method to create a new `SqlDataReader` object.</span></span> <span data-ttu-id="c8503-118">코드 예제 내에서는 다음 동작이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-118">The following actions occur within the code example:</span></span>  
  
1.  <span data-ttu-id="c8503-119">Main 메서드가 새 `SqlDataReader` 개체를 만들고 Point라는 UDT 열이 있는 Points 테이블에서 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-119">The Main method creates a new `SqlDataReader` object and retrieves the values from the Points table, which has a UDT column named Point.</span></span>  
  
2.  <span data-ttu-id="c8503-120">Point UDT는 정수로 정의된 X 및 Y 좌표를 공개합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-120">The Point UDT exposes X and Y coordinates defined as integers.</span></span>  
  
3.  <span data-ttu-id="c8503-121">UDT는 `Distance` 메서드와 `GetDistanceFromXY` 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-121">The UDT defines a `Distance` method and a `GetDistanceFromXY` method.</span></span>  
  
4.  <span data-ttu-id="c8503-122">예제 코드에서 UDT의 기능을 설명하기 위해 기본 키 및 UDT 열의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-122">The sample code retrieves the values of the primary key and UDT columns in order to demonstrate the capabilities of the UDT.</span></span>  
  
5.  <span data-ttu-id="c8503-123">예제 코드에서 `Point.Distance` 및 `Point.GetDistanceFromXY` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-123">The sample code calls the `Point.Distance` and `Point.GetDistanceFromXY` methods.</span></span>  
  
6.  <span data-ttu-id="c8503-124">콘솔 창에 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-124">The results are displayed in the console window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8503-125">애플리케이션에 이미 UDT 어셈블리에 대한 참조가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-125">The application must already have a reference to the UDT assembly.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module ReadPoints  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the value of the UDT  
                Dim pnt As Point = CType(rdr(1), Point)  
  
             ' You can also use GetSqlValue and GetValue  
             ' Dim pnt As Point = CType(rdr.GetSqlValue(1), Point)  
             ' Dim pnt As Point = CType(rdr.GetValue(1), Point)  
  
                ' Print values  
                Console.WriteLine( _  
                 "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}", _  
                  id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance())  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
         & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
namespace Microsoft.Samples.SqlServer  
{  
class ReadPoints  
{  
static void Main()  
{  
  string connectionString = GetConnectionString();  
  using (SqlConnection cnn = new SqlConnection(connectionString))  
  {  
    cnn.Open();  
    SqlCommand cmd = new SqlCommand(  
       "SELECT ID, Pnt FROM dbo.Points", cnn);  
    SqlDataReader rdr = cmd.ExecuteReader();  
  
    while (rdr.Read())  
    {  
      // Retrieve the value of the Primary Key column  
      int id = rdr.GetInt32(0);  
  
        // Retrieve the value of the UDT  
        Point pnt = (Point)rdr[1];  
  
        // You can also use GetSqlValue and GetValue  
        // Point pnt = (Point)rdr.GetSqlValue(1);  
        // Point pnt = (Point)rdr.GetValue(1);  
  
        Console.WriteLine(  
        "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}",   
        id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance());  
    }  
  rdr.Close();  
  Console.WriteLine("done");  
  }  
  static private string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,   
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="binding-udts-as-bytes"></a><span data-ttu-id="c8503-126">UDT를 바이트로 바인딩</span><span class="sxs-lookup"><span data-stu-id="c8503-126">Binding UDTs as Bytes</span></span>  
 <span data-ttu-id="c8503-127">UDT 열에서 원시 데이터를 검색하려는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-127">In some situations, you may want to retrieve the raw data from the UDT column.</span></span> <span data-ttu-id="c8503-128">로컬에서 데이터의 형식을 사용할 수 없거나 UDT의 인스턴스를 인스턴스화하지 않으려는 경우가 그러한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-128">Perhaps the type is not available locally, or you do not wish to instantiate an instance of the UDT.</span></span> <span data-ttu-id="c8503-129">의 **GetBytes** 메서드를 사용 하 여 바이트 배열로 원시 바이트를 읽을 수 있습니다 `SqlDataReader` .</span><span class="sxs-lookup"><span data-stu-id="c8503-129">You can read the raw bytes into a byte array using the **GetBytes** method of a `SqlDataReader`.</span></span> <span data-ttu-id="c8503-130">이 메서드는 지정한 열 오프셋의 바이트 스트림을 지정한 버퍼 오프셋에서 시작하는 배열의 버퍼로 읽어 들입니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-130">This method reads a stream of bytes from the specified column offset into the buffer of an array starting at a specified buffer offset.</span></span> <span data-ttu-id="c8503-131">또 다른 옵션은 **Getsqlbytes** 또는 **GetSqlBinary** 메서드 중 하나를 사용 하 고 단일 작업으로 모든 내용을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-131">Another option is to use one of the **GetSqlBytes** or **GetSqlBinary** methods and read all of the contents in a single operation.</span></span> <span data-ttu-id="c8503-132">어느 경우에나 UDT 개체는 인스턴스화되지 않으므로 클라이언트 어셈블리에서 UDT에 대한 참조를 설정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-132">In either case, the UDT object is never instantiated, so you do not need to set a reference to the UDT in the client assembly.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c8503-133">예제</span><span class="sxs-lookup"><span data-stu-id="c8503-133">Example</span></span>  
 <span data-ttu-id="c8503-134">이 예제에서는를 사용 하 여 바이트 배열에 **지점** 데이터를 원시 바이트로 검색 하는 방법을 보여 줍니다 `SqlDataReader` .</span><span class="sxs-lookup"><span data-stu-id="c8503-134">This example shows how to retrieve the **Point** data as raw bytes into a byte array using a `SqlDataReader`.</span></span> <span data-ttu-id="c8503-135">이 코드는 `System.Text.StringBuilder`를 사용하여 원시 바이트를 콘솔 창에 표시될 문자열 표현으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-135">The code uses a `System.Text.StringBuilder` to convert the raw bytes to a string representation to be displayed in the console window.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the raw bytes into a byte array  
                Dim buffer(31) As Byte  
                Dim byteCount As Integer = _  
                 CInt(rdr.GetBytes(1, 0, buffer, 0, 31))  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", buffer(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
        string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand("SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Retrieve the raw bytes into a byte array  
                byte[] buffer = new byte[32];  
                long byteCount = rdr.GetBytes(1, 0, buffer, 0, 32);  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", buffer[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
### <a name="example-using-getsqlbytes"></a><span data-ttu-id="c8503-136">GetSqlBytes를 사용하는 예</span><span class="sxs-lookup"><span data-stu-id="c8503-136">Example Using GetSqlBytes</span></span>  
 <span data-ttu-id="c8503-137">이 예제에서는 **Getsqlbytes** 메서드를 사용 하 여 단일 작업에서 **Point** 데이터를 원시 바이트로 검색 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-137">This example shows how to retrieve the **Point** data as raw bytes in a single operation using the **GetSqlBytes** method.</span></span> <span data-ttu-id="c8503-138">이 코드는 `StringBuilder`를 사용하여 원시 바이트를 콘솔 창에 표시될 문자열 표현으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-138">The code uses a `StringBuilder` to convert the raw bytes to a string representation to be displayed in the console window.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Use SqlBytes to retrieve raw bytes  
                Dim sb As SqlBytes = rdr.GetSqlBytes(1)  
                Dim byteCount As Long = sb.Length  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", sb(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
         string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Use SqlBytes to retrieve raw bytes  
                SqlBytes sb = rdr.GetSqlBytes(1);  
                long byteCount = sb.Length;  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", sb[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="working-with-udt-parameters"></a><span data-ttu-id="c8503-139">UDT 매개 변수 작업</span><span class="sxs-lookup"><span data-stu-id="c8503-139">Working with UDT Parameters</span></span>  
 <span data-ttu-id="c8503-140">사용자의 ADO.NET 코드에서 UDT를 입력 및 출력 매개 변수 모두로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-140">UDTs can be used as both input and output parameters in your ADO.NET code.</span></span>  
  
## <a name="using-udts-in-query-parameters"></a><span data-ttu-id="c8503-141">쿼리 매개 변수에 UDT 사용</span><span class="sxs-lookup"><span data-stu-id="c8503-141">Using UDTs in Query Parameters</span></span>  
 <span data-ttu-id="c8503-142">`SqlParameter` 개체의 `System.Data.SqlClient.SqlCommand`를 설정할 때 UDT를 매개 변수 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-142">UDTs can be used as parameter values when setting up a `SqlParameter` for a `System.Data.SqlClient.SqlCommand` object.</span></span> <span data-ttu-id="c8503-143">`SqlDbType.Udt` 컬렉션에 대해 `SqlParameter` 메서드를 호출할 때는 매개 변수가 UDT임을 나타내기 위해 `Add` 개체의 `Parameters` 열거형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-143">The `SqlDbType.Udt` enumeration of a `SqlParameter` object is used to indicate that the parameter is a UDT when calling the `Add` method to the `Parameters` collection.</span></span> <span data-ttu-id="c8503-144">`UdtTypeName`개체의 속성을 `SqlCommand` 사용 하 여 데이터베이스에서 UDT의 정규화 된 이름을 *schema_name. object_name* 구문을 사용 하 여 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-144">The `UdtTypeName` property of a `SqlCommand` object is used to specify the fully qualified name of the UDT in the database using the *database.schema_name.object_name* syntax.</span></span> <span data-ttu-id="c8503-145">꼭 필요한 것은 아니지만 정규화된 이름을 사용하면 코드가 명확해집니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-145">Although it is not required, using the fully qualified name removes ambiguity from your code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8503-146">클라이언트 프로젝트에서 UDT 어셈블리의 로컬 복사본을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-146">A local copy of the UDT assembly must be available to the client project.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c8503-147">예제</span><span class="sxs-lookup"><span data-stu-id="c8503-147">Example</span></span>  
 <span data-ttu-id="c8503-148">이 예의 코드에서는 `SqlCommand` 및 `SqlParameter` 개체를 만들어 테이블의 UDT 열에 데이터를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-148">The code in this example creates `SqlCommand` and `SqlParameter` objects to insert data into a UDT column in a table.</span></span> <span data-ttu-id="c8503-149">또한 `SqlDbType.Udt` 열거형을 사용하여 데이터 형식을 지정하며, `UdtTypeName` 개체에 `SqlParameter` 속성을 사용하여 데이터베이스에 UDT의 정규화된 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c8503-149">The code uses the `SqlDbType.Udt` enumeration to specify the data type, and the `UdtTypeName` property of the `SqlParameter` object to specify the fully qualified name of the UDT in the database.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports system.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim ConnectionString As String = GetConnectionString()  
    Dim cnn As New SqlConnection(ConnectionString)  
    Using cnn  
      Dim cmd As SqlCommand = cnn.CreateCommand()  
      cmd.CommandText = "INSERT INTO dbo.Points (Pnt) VALUES (@Point)"  
      cmd.CommandType = CommandType.Text  
  
      Dim param As New SqlParameter("@Point", SqlDbType.Udt)      param.UdtTypeName = "TestPoint.dbo.Point"      param.Direction = ParameterDirection.Input      param.Value = New Point(5, 6)      cmd.Parameters.Add(param)  
  
      cnn.Open()  
      cmd.ExecuteNonQuery()  
      Console.WriteLine("done")  
    End Using  
  End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  string ConnectionString = GetConnectionString();  
     using (SqlConnection cnn = new SqlConnection(ConnectionString))  
     {  
       SqlCommand cmd = cnn.CreateCommand();  
       cmd.CommandText =   
         "INSERT INTO dbo.Points (Pnt) VALUES (@Point)";  
       cmd.CommandType = CommandType.Text;  
  
       SqlParameter param = new SqlParameter("@Point", SqlDbType.Udt);       param.UdtTypeName = "TestPoint.dbo.Point";       param.Direction = ParameterDirection.Input;       param.Value = new Point(5, 6);       cmd.Parameters.Add(param);  
  
       cnn.Open();  
       cmd.ExecuteNonQuery();  
       Console.WriteLine("done");  
     }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8503-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8503-150">See Also</span></span>  
 [<span data-ttu-id="c8503-151">ADO.NET의 사용자 정의 형식 액세스</span><span class="sxs-lookup"><span data-stu-id="c8503-151">Accessing User-Defined Types in ADO.NET</span></span>](accessing-user-defined-types-in-ado-net.md)  
  
  
