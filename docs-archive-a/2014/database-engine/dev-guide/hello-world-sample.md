---
title: Hello World 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: fed6c358-f5ee-4d4c-9ad6-089778383ba7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0d5616c1d4ef6428a011c8e36be3757931039c9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742504"
---
# <a name="hello-world-sample"></a><span data-ttu-id="f1e55-102">Hello World 예제</span><span class="sxs-lookup"><span data-stu-id="f1e55-102">Hello World Sample</span></span>
  <span data-ttu-id="f1e55-103">Hello World 예제는 간단한 CLR(공용 언어 런타임) 통합 기반 저장 프로시저의 만들기, 배포 및 테스트와 관련된 기본 작업을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-103">The Hello World sample demonstrates the basic operations that are involved in creating, deploying, and testing a simple common language runtime (CLR) integration-based stored procedure.</span></span> <span data-ttu-id="f1e55-104">이 예제는 저장 프로시저에 의해 동적으로 생성되고 호출자로 반환되는 레코드를 통해 데이터를 반환하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-104">This sample also demonstrates how to return data through a record, which is dynamically constructed by the stored procedure and returned to the caller.</span></span>  
  
 <span data-ttu-id="f1e55-105">`HelloWorld`저장 프로시저는 "Hello 세계!" 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-105">The `HelloWorld` stored procedure returns the string "Hello world!"</span></span> <span data-ttu-id="f1e55-106">한 행으로 구성 된 결과 집합</span><span class="sxs-lookup"><span data-stu-id="f1e55-106">in a result set consisting of one row.</span></span> <span data-ttu-id="f1e55-107">이 예제 [에서는 클래스의](https://go.microsoft.com/fwlink/?LinkID=193572)몇 가지 사용 예를 보여 줍니다. [SqlDataRecord](https://go.microsoft.com/fwlink/?LinkID=193573) 및 microsoft. d s. [파이프](https://go.microsoft.com/fwlink/?LinkID=193571).</span><span class="sxs-lookup"><span data-stu-id="f1e55-107">This example illustrates some uses for the classes [Microsoft.SqlServer.Server.SqlMetaData](https://go.microsoft.com/fwlink/?LinkID=193572), [Microsoft.SqlServer.Server.SqlDataRecord](https://go.microsoft.com/fwlink/?LinkID=193573) and [Microsoft.SqlServer.Server.Pipe](https://go.microsoft.com/fwlink/?LinkID=193571).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f1e55-108">전제 조건</span><span class="sxs-lookup"><span data-stu-id="f1e55-108">Prerequisites</span></span>  
 <span data-ttu-id="f1e55-109">이 프로젝트를 만들고 실행하려면 다음 소프트웨어가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-109">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f1e55-110">또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="f1e55-110">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="f1e55-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 설명서 및 예제 [웹 사이트](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 무료로 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-111">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="f1e55-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개발자 [웹 사이트](https://go.microsoft.com/fwlink/?linkid=62796)에서 제공되는 AdventureWorks 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="f1e55-112">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="f1e55-113">.NET Framework SDK 2.0 이상 또는 Microsoft Visual Studio 2005 이상.</span><span class="sxs-lookup"><span data-stu-id="f1e55-113">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="f1e55-114">.NET Framework SDK는 무료로 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-114">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="f1e55-115">또한 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-115">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="f1e55-116">사용하고 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대해 CLR 통합이 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="f1e55-117">CLR 통합을 설정하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-117">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="f1e55-118">CLR 통합 사용</span><span class="sxs-lookup"><span data-stu-id="f1e55-118">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="f1e55-119">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-119">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="f1e55-120">CLR을 사용하도록 설정하려면 `ALTER SETTINGS` 서버 수준 사용 권한이 있어야 합니다. 이 사용 권한은 `sysadmin` 및 `serveradmin` 고정 서버 역할의 멤버가 암시적으로 소유합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-120">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="f1e55-121">사용하고 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 AdventureWorks 데이터베이스를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-121">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="f1e55-122">사용하고 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 관리자가 아닌 경우 설치를 완료하기 위해 관리자로부터 **CreateAssembly** 권한을 부여 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-122">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly** permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="f1e55-123">예제 빌드</span><span class="sxs-lookup"><span data-stu-id="f1e55-123">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="f1e55-124">다음 지침을 사용하여 예제를 만들고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-124">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="f1e55-125">Visual Studio 또는 .NET Framework 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-125">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="f1e55-126">필요한 경우 예제에 대한 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-126">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="f1e55-127">이 예에서는 C:\MySample을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-127">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="f1e55-128">c:\MySample에서 `HelloWorld.vb`(Visual Basic 예제용) 또는 `HelloWorld.cs`(C# 예제용)를 만들고 적합한 Visual Basic 또는 C# 예제 코드(아래)를 파일에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-128">In c:\MySample, create `HelloWorld.vb` (for the Visual Basic sample) or `HelloWorld.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="f1e55-129">선택하는 언어에 따라 다음 중 하나를 실행하여 명령줄 프롬프트에서 예제 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-129">Compile the sample code from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `vbc C:HelloWorld.vb /target:library`  
  
    -   `csc /target:library HelloWorld.cs`  
  
5.  <span data-ttu-id="f1e55-130">[!INCLUDE[tsql](../../includes/tsql-md.md)] 설치 코드를 파일에 복사하고 해당 파일을 예제 디렉터리에 `Install.sql` 로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-130">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="f1e55-131">다음을 실행하여 어셈블리 및 저장 프로시저를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-131">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql -v root = "C:\MySample\"`  
  
7.  <span data-ttu-id="f1e55-132">[!INCLUDE[tsql](../../includes/tsql-md.md)] 테스트 명령 스크립트를 파일에 복사하고 해당 파일을 예제 디렉터리에 `test.sql` 로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-132">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
8.  <span data-ttu-id="f1e55-133">다음 명령으로 테스트 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-133">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
9. <span data-ttu-id="f1e55-134">[!INCLUDE[tsql](../../includes/tsql-md.md)] 정리 스크립트를 파일에 복사하고 해당 파일을 예제 디렉터리에 `cleanup.sql` 로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-134">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
10. <span data-ttu-id="f1e55-135">다음 명령으로 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-135">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="f1e55-136">샘플 코드</span><span class="sxs-lookup"><span data-stu-id="f1e55-136">Sample Code</span></span>  
 <span data-ttu-id="f1e55-137">다음은 이 예제에 대한 코드 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-137">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="f1e55-138">C#</span><span class="sxs-lookup"><span data-stu-id="f1e55-138">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
public partial class StoredProcedures  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld()  
    {  
        Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 12);  
        SqlDataRecord greetingRecord  
            = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
        greetingRecord.SetString(0, "Hello world!");  
        SqlContext.Pipe.Send(greetingRecord);  
    }  
};  
  
```  
  
 <span data-ttu-id="f1e55-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1e55-139">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public NotInheritable Class StoredProcedures  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorld()  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 12)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, "Hello World!")  
        SqlContext.Pipe.Send(greetingRecord)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="f1e55-140">이는 어셈블리를 배포하고 데이터베이스 내에서 저장 프로시저를 만드는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 설치 스크립트(`Install.sql`)입니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-140">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedure in the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
set @SamplesPath = '$(root)'  
CREATE ASSEMBLY HelloWorld   
FROM @SamplesPath + 'HelloWorld.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorld  
--(  
--    @Greeting nvarchar(12) OUTPUT  
--)  
AS EXTERNAL NAME HelloWorld.[StoredProcedures].HelloWorld;  
GO  
```  
  
 <span data-ttu-id="f1e55-141">이는 저장 프로시저를 실행하여 예제를 테스트하는 `test.sql`입니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-141">This is `test.sql`, which tests the sample by executing the stored procedure.</span></span>  
  
```  
use AdventureWorks  
go  
execute usp_HelloWorld  
  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
```  
  
 <span data-ttu-id="f1e55-142">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 은 데이터베이스에서 어셈블리 및 저장 프로시저를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f1e55-142">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1e55-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f1e55-143">See Also</span></span>  
 [<span data-ttu-id="f1e55-144">공용 언어 런타임 &#40;CLR&#41; 통합에 대한 사용 시나리오 및 예제</span><span class="sxs-lookup"><span data-stu-id="f1e55-144">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
