---
title: 로컬 패키지의 출력 로드 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6799e593ab9d5ae1a9358bf54f4927838991ebd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740143"
---
# <a name="loading-the-output-of-a-local-package"></a><span data-ttu-id="9ad18-102">로컬 패키지의 출력 로드</span><span class="sxs-lookup"><span data-stu-id="9ad18-102">Loading the Output of a Local Package</span></span>
  <span data-ttu-id="9ad18-103">[!INCLUDE[vstecado](../../includes/vstecado-md.md)]을 사용하여 출력을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상에 저장한 경우 또는 **System.IO** 네임스페이스의 클래스를 사용하여 출력을 플랫 파일 대상에 저장한 경우 클라이언트 애플리케이션에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 출력을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-103">Client applications can read the output of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages when the output is saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinations by using [!INCLUDE[vstecado](../../includes/vstecado-md.md)], or when the output is saved to a flat file destination by using the classes in the **System.IO** namespace.</span></span> <span data-ttu-id="9ad18-104">하지만 데이터를 지속하기 위한 중간 단계 없이 클라이언트 애플리케이션이 메모리에서 직접 패키지의 출력을 읽을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-104">However, a client application can also read the output of a package directly from memory, without the need for an intermediate step to persist the data.</span></span> <span data-ttu-id="9ad18-105">이 솔루션의 핵심은 `Microsoft.SqlServer.Dts.DtsClient` `IDbConnection` `IDbCommand` **IDbDataParameter** 네임 스페이스에서, 및 인터페이스 **System.Data** 의 특수 구현을 포함 하는 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-105">The key to this solution is the `Microsoft.SqlServer.Dts.DtsClient` namespace, which contains specialized implementations of the `IDbConnection`, `IDbCommand`, and **IDbDataParameter** interfaces from the **System.Data** namespace.</span></span> <span data-ttu-id="9ad18-106">Microsoft.SqlServer.Dts.DtsClient.dll 어셈블리는 기본적으로 **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-106">The assembly Microsoft.SqlServer.Dts.DtsClient.dll is installed by default in **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.</span></span>

> [!NOTE]
>  <span data-ttu-id="9ad18-107">이 항목에서 설명하는 절차를 수행하려면 데이터 흐름 태스크와 부모 개체의 DelayValidation 속성이 기본값인 **False**로 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-107">The procedure described in this topic requires that the DelayValidation property of the Data Flow task and of any parent objects be set to its default value of **False**.</span></span>

## <a name="description"></a><span data-ttu-id="9ad18-108">설명</span><span class="sxs-lookup"><span data-stu-id="9ad18-108">Description</span></span>
 <span data-ttu-id="9ad18-109">이 절차에서는 DataReader 대상을 사용하는 패키지의 출력을 메모리에서 직접 로드하는 클라이언트 애플리케이션을 관리 코드로 개발하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-109">This procedure demonstrates how to develop a client application in managed code that loads the output of a package with a DataReader destination directly from memory.</span></span> <span data-ttu-id="9ad18-110">여기에 요약된 단계는 뒷부분의 코드 예제에서 자세히 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-110">The steps summarized here are demonstrated in the code sample that follows.</span></span>

#### <a name="to-load-data-package-output-into-a-client-application"></a><span data-ttu-id="9ad18-111">데이터 패키지 출력을 클라이언트 애플리케이션으로 로드하려면</span><span class="sxs-lookup"><span data-stu-id="9ad18-111">To load data package output into a client application</span></span>

1.  <span data-ttu-id="9ad18-112">패키지에서 DataReader 대상이 클라이언트 애플리케이션으로 읽어 올 출력을 받도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-112">In the package, configure a DataReader destination to receive the output that you want to read into the client application.</span></span> <span data-ttu-id="9ad18-113">DataReader 대상 이름은 나중에 클라이언트 애플리케이션에서 사용되므로 이 대상에 알기 쉬운 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-113">Give the DataReader destination a descriptive name, since you will use this name later in your client application.</span></span> <span data-ttu-id="9ad18-114">또한 DataReader 대상의 이름을 적어 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-114">Make a note of the name of the DataReader destination.</span></span>

2.  <span data-ttu-id="9ad18-115">개발 프로젝트에서 `Microsoft.SqlServer.Dts.DtsClient` 어셈블리 **Microsoft.SqlServer.Dts.DtsClient.dll**를 찾아 네임 스페이스에 대 한 참조를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-115">In the development project, set a reference to the `Microsoft.SqlServer.Dts.DtsClient` namespace by locating the assembly **Microsoft.SqlServer.Dts.DtsClient.dll**.</span></span> <span data-ttu-id="9ad18-116">기본적으로 이 어셈블리는 **C:\Program Files\Microsoft SQL Server\100\DTS\Binn**에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-116">By default, this assembly is installed in **C:\Program Files\Microsoft SQL Server\100\DTS\Binn**.</span></span> <span data-ttu-id="9ad18-117">C # 또는 문을 사용 하 여 네임 스페이스를 코드로 가져옵니다 `Using` [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` .</span><span class="sxs-lookup"><span data-stu-id="9ad18-117">Import the namespace into your code by using the C# `Using` or the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` statement.</span></span>

3.  <span data-ttu-id="9ad18-118">코드에서 `DtsClient.DtsConnection` **dtexec.exe** 패키지를 실행 하는 데 필요한 명령줄 매개 변수를 포함 하는 연결 문자열을 사용 하 여 형식의 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-118">In your code, create an object of type `DtsClient.DtsConnection` with a connection string that contains the command-line parameters required by **dtexec.exe** to run the package.</span></span> <span data-ttu-id="9ad18-119">자세한 내용은 [dtexec Utility](../packages/dtexec-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ad18-119">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span> <span data-ttu-id="9ad18-120">그런 다음 이 연결 문자열을 사용하여 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-120">Then open the connection with this connection string.</span></span> <span data-ttu-id="9ad18-121">**dtexecui** 유틸리티를 사용하여 필요한 연결 문자열을 시각적으로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-121">You can also use the **dtexecui** utility to create the required connection string visually.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9ad18-122">예제 코드에서는 `/FILE <path and filename>` 구문을 사용하여 파일 시스템에서 패키지를 로드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-122">The sample code demonstrates loading the package from the file system by using the `/FILE <path and filename>` syntax.</span></span> <span data-ttu-id="9ad18-123">그러나 `/SQL <package name>` 구문을 사용하여 MSDB 데이터베이스에서 패키지를 로드하거나 `/DTS \<folder name>\<package name>` 구문을 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 저장소에서 패키지를 로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-123">However you can also load the package from the MSDB database by using the `/SQL <package name>` syntax, or from the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package store by using the `/DTS \<folder name>\<package name>` syntax.</span></span>

4.  <span data-ttu-id="9ad18-124">이전에 만든 `DtsClient.DtsCommand`을 사용하는 `DtsConnection` 형식의 개체를 만들고 이 개체의 `CommandText` 속성을 패키지의 DataReader 대상 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-124">Create an object of type `DtsClient.DtsCommand` that uses the previously created `DtsConnection` and set its `CommandText` property to the name of the DataReader destination in the package.</span></span> <span data-ttu-id="9ad18-125">그런 다음 이 명령 개체의 `ExecuteReader` 메서드를 호출하여 패키지 결과를 새 DataReader로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-125">Then call the `ExecuteReader` method of the command object to load the package results into a new DataReader.</span></span>

5.  <span data-ttu-id="9ad18-126">필요할 경우 `DtsDataParameter` 개체에서 `DtsCommand` 개체의 컬렉션을 사용하여 패키지의 출력을 간접적으로 매개 변수화함으로써 패키지에 정의된 변수에 값을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-126">Optionally, you can indirectly parameterize the output of the package by using the collection of `DtsDataParameter` objects on the `DtsCommand` object to pass values to variables defined in the package.</span></span> <span data-ttu-id="9ad18-127">패키지 내에서는 이러한 변수를 쿼리 매개 변수로 사용하거나 식에 사용하여 DataReader 대상에 반환되는 결과에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-127">Within the package, you can use these variables as query parameters or in expressions to affect the results returned to the DataReader destination.</span></span> <span data-ttu-id="9ad18-128">**DtsClient** `DtsDataParameter` 클라이언트 응용 프로그램의 개체와 함께 사용 하려면 먼저 DtsClient 네임 스페이스의 패키지에서 이러한 변수를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-128">You must define these variables in the package in the **DtsClient** namespace before you can use them with the `DtsDataParameter` object from a client application.</span></span> <span data-ttu-id="9ad18-129">( **변수** 창에서 **변수 열 선택** 도구 모음 단추를 클릭 하 여 **네임 스페이스** 열을 표시 해야 할 수도 있습니다.) 클라이언트 코드에서의 컬렉션에를 추가 하는 경우 `DtsDataParameter` `Parameters` `DtsCommand` 변수 이름에서 DtsClient 네임 스페이스 참조를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-129">(You may need to click the **Choose Variable Columns** toolbar button in the **Variables** window to display the **Namespace** column.) In your client code, when you add a `DtsDataParameter` to the `Parameters` collection of the `DtsCommand`, omit the DtsClient namespace reference from the variable name.</span></span> <span data-ttu-id="9ad18-130">예:</span><span class="sxs-lookup"><span data-stu-id="9ad18-130">For example:</span></span>

    ```
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));
    ```

6.  <span data-ttu-id="9ad18-131">DataReader의 `Read` 메서드를 필요한 만큼 반복적으로 호출하여 출력 데이터 행을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-131">Call the `Read` method of the DataReader repeatedly as needed to loop through the rows of output data.</span></span> <span data-ttu-id="9ad18-132">클라이언트 애플리케이션에서 이 데이터를 사용하거나 나중에 사용할 수 있도록 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-132">Use the data, or save the data for later use, in the client application.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="9ad18-133">이 DataReader 구현의 `Read` 메서드는 마지막 데이터 행을 읽은 후 `true`를 한 번 더 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-133">The `Read` method of this implementation of the DataReader returns `true` one more time after the last row of data has been read.</span></span> <span data-ttu-id="9ad18-134">따라서 `Read`가 `true`를 반환하는 동안 DataReader를 반복하는 일반적인 코드를 사용하기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-134">This makes it difficult to use the usual code that loops through the DataReader while `Read` returns `true`.</span></span> <span data-ttu-id="9ad18-135">예상한 개수의 행을 읽은 후 코드에서 `Read` 메서드를 마지막으로 한 번 더 호출하지 않고 DataReader나 연결을 닫으려고 하면 처리되지 않은 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-135">If your code attempts to close the DataReader or the connection after reading the expected number of rows, without an additional, final call to the `Read` method, the code will raise an unhandled exception.</span></span> <span data-ttu-id="9ad18-136">그러나 `Read`가 여전히 `true`를 반환하지만 마지막 행이 전달된 경우에 코드에서 이 마지막 루프 반복의 데이터를 읽으려고 하면 "SIS IDataReader가 결과 집합의 끝을 지났습니다."라는 메시지와 함께 처리되지 않은 `ApplicationException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-136">However, if your code attempts to read data on this final iteration through a loop, when `Read` still returns `true` but the last row has been passed, the code will raise an unhandled `ApplicationException` with the message, "The SSIS IDataReader is past the end of the resultset."</span></span> <span data-ttu-id="9ad18-137">이 동작은 다른 DataReader 구현의 동작과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-137">This behavior is different from that of other DataReader implementations.</span></span> <span data-ttu-id="9ad18-138">따라서 `Read`가 `true`를 반환하는 동안 DataReader에서 루프를 사용하여 행을 읽으려면 `ApplicationException` 메서드를 마지막으로 성공적으로 호출할 때 예상된 이 `Read`을 catch, 테스트 및 삭제하는 코드를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-138">Therefore, when using a loop to read through the rows in the DataReader while `Read` returns `true`, you need to write code to catch, test, and discard this anticipated `ApplicationException` on the last successful call to the `Read` method.</span></span> <span data-ttu-id="9ad18-139">예상 행 수를 이미 아는 경우에는 행을 처리한 다음 DataReader와 연결을 닫기 전에 `Read` 메서드를 한 번 이상 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-139">Or, if you know in advance the number of rows expected, you can process the rows, and then call the `Read` method one more time before closing the DataReader and the connection.</span></span>

7.  <span data-ttu-id="9ad18-140">`Dispose` 개체의 `DtsCommand` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-140">Call the `Dispose` method of the `DtsCommand` object.</span></span> <span data-ttu-id="9ad18-141">이 메서드는 `DtsDataParameter` 개체를 사용한 경우에 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-141">This is particularly important if you have used any `DtsDataParameter` objects.</span></span>

8.  <span data-ttu-id="9ad18-142">DataReader와 연결 개체를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-142">Close the DataReader and the connection objects.</span></span>

## <a name="example"></a><span data-ttu-id="9ad18-143">예제</span><span class="sxs-lookup"><span data-stu-id="9ad18-143">Example</span></span>
 <span data-ttu-id="9ad18-144">다음 예에서는 단일 집계 값을 계산하고 해당 값을 DataReader 대상에 저장하는 패키지를 실행한 다음 DataReader에서 이 값을 읽어 Windows Form의 입력란에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-144">The following example runs a package that calculates a single aggregate value and saves the value to a DataReader destination, and then reads this value from the DataReader and displays the value in a text box on a Windows Form.</span></span>

 <span data-ttu-id="9ad18-145">패키지의 출력을 클라이언트 애플리케이션으로 로드할 때는 매개 변수를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-145">The use of parameters is not required when loading the output of a package into a client application.</span></span> <span data-ttu-id="9ad18-146">매개 변수를 사용 하지 않으려면 **DtsClient** 네임 스페이스에서 변수 사용을 생략 하 고 개체를 사용 하는 코드를 생략 하면 `DtsDataParameter` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-146">If you do not want to use a parameter, you can omit the use of the variable in the **DtsClient** namespace, and omit the code that uses the `DtsDataParameter` object.</span></span>

#### <a name="to-create-the-test-package"></a><span data-ttu-id="9ad18-147">테스트 패키지를 만들려면</span><span class="sxs-lookup"><span data-stu-id="9ad18-147">To create the test package</span></span>

1.  <span data-ttu-id="9ad18-148">새 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-148">Create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="9ad18-149">예제 코드에서는 패키지 이름으로 "DtsClientWParamPkg.dtsx"를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-149">The sample code uses "DtsClientWParamPkg.dtsx" as the name of the package.</span></span>

2.  <span data-ttu-id="9ad18-150">DtsClient 네임스페이스에 String 형식의 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-150">Add a variable of type String in the DtsClient namespace.</span></span> <span data-ttu-id="9ad18-151">예제 코드에서는 변수 이름으로 Country를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-151">The sample code use Country as the name of the variable.</span></span> <span data-ttu-id="9ad18-152">**변수** 창에서 **변수 열 선택** 도구 모음 단추를 클릭하여 **네임스페이스** 열을 표시해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-152">(You may need to click the **Choose Variable Columns** toolbar button in the **Variables** window to display the **Namespace** column.)</span></span>

3.  <span data-ttu-id="9ad18-153">[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 예제 데이터베이스에 연결하는 OLE DB 연결 관리자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-153">Add an OLE DB connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database.</span></span>

4.  <span data-ttu-id="9ad18-154">패키지에 데이터 흐름 태스크를 추가하고 데이터 흐름 디자인 화면으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-154">Add a data flow task to the package and switch to the Data Flow design surface.</span></span>

5.  <span data-ttu-id="9ad18-155">데이터 흐름에 OLE DB 원본을 추가하고, 이 데이터 원본에서 이전에 만든 OLE DB 연결 관리자와 다음 SQL 명령을 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-155">Add an OLE DB source to the data flow and configure it to use the OLE DB connection manager created previously, and the following SQL command:</span></span>

    ```
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?
    ```

6.  <span data-ttu-id="9ad18-156">을 클릭 하 `Parameters` 고 **쿼리 매개 변수 설정** 대화 상자에서 0 쿼리의 단일 입력 매개 변수를 DtsClient:: Country 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-156">Click `Parameters` and, in the **Set Query Parameters** dialog box, map the single input parameter in the query, Parameter0, to the DtsClient::Country variable.</span></span>

7.  <span data-ttu-id="9ad18-157">데이터 흐름에 집계 변환을 추가하고 OLE DB 원본의 출력을 변환에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-157">Add an Aggregate transformation to the data flow, and connect the output of the OLE DB source to the transformation.</span></span> <span data-ttu-id="9ad18-158">집계 변환 편집기를 열고 모든 입력 열 (\*)에 대해 "모두 계산" 작업을 수행 하 고 집계 된 값을 CustomerCount 별칭으로 출력 하도록 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-158">Open the Aggregate Transformation Editor and configure it to perform a "Count all" operation on all input columns (\*) and to output the aggregated value with the alias CustomerCount.</span></span>

8.  <span data-ttu-id="9ad18-159">데이터 흐름에 DataReader 대상을 추가하고 집계 변환의 출력을 DataReader 대상에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-159">Add a DataReader destination to the data flow and connect the output of the Aggregate transformation to the DataReader destination.</span></span> <span data-ttu-id="9ad18-160">예제 코드에서는 DataReader 이름으로 "DataReaderDest"를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-160">The sample code uses "DataReaderDest" as the name of the DataReader.</span></span> <span data-ttu-id="9ad18-161">대상에 대해 사용 가능한 단일 입력 열인 CustomerCount를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-161">Select the single available input column, CustomerCount, for the destination.</span></span>

9. <span data-ttu-id="9ad18-162">패키지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-162">Save the package.</span></span> <span data-ttu-id="9ad18-163">다음에 만들 테스트 애플리케이션에서는 이 패키지를 실행하고 메모리에서 직접 출력을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-163">The test application created next will run the package and retrieve its output directly from memory.</span></span>

#### <a name="to-create-the-test-application"></a><span data-ttu-id="9ad18-164">테스트 애플리케이션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="9ad18-164">To create the test application</span></span>

1.  <span data-ttu-id="9ad18-165">새 Windows Forms 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-165">Create a new Windows Forms application.</span></span>

2.  <span data-ttu-id="9ad18-166">`Microsoft.SqlServer.Dts.DtsClient` **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**에서 동일한 이름의 어셈블리를 찾아 네임 스페이스에 대 한 참조를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-166">Add a reference to the `Microsoft.SqlServer.Dts.DtsClient` namespace by browsing to the assembly of the same name in **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.</span></span>

3.  <span data-ttu-id="9ad18-167">다음 예제 코드를 복사하여 폼의 코드 모듈에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-167">Copy and paste the following sample code into the code module for the form.</span></span>

4.  <span data-ttu-id="9ad18-168">`dtexecArgs` **dtexec.exe** 에서 패키지를 실행 하는 데 필요한 명령줄 매개 변수를 포함 하도록 필요에 따라 변수 값을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-168">Modify the value of the `dtexecArgs` variable as required so that it contains the command-line parameters required by **dtexec.exe** to run the package.</span></span> <span data-ttu-id="9ad18-169">예제 코드는 파일 시스템에서 패키지를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-169">The sample code loads the package from the file system.</span></span>

5.  <span data-ttu-id="9ad18-170">필요에 따라 변수 값을 수정 `dataReaderName` 하 여 패키지에 있는 DataReader 대상의 이름을 포함 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-170">Modify the value of the `dataReaderName` variable as required so that it contains the name of the DataReader destination in the package.</span></span>

6.  <span data-ttu-id="9ad18-171">폼에 단추와 입력란을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-171">Put a button and a text box on the form.</span></span> <span data-ttu-id="9ad18-172">샘플 코드에서는를 `btnRun` 단추의 이름으로 사용 하 고를 `txtResults` 텍스트 상자의 이름으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-172">The sample code uses `btnRun` as the name of the button, and `txtResults` as the name of the text box.</span></span>

7.  <span data-ttu-id="9ad18-173">애플리케이션을 실행하고 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-173">Run the application and click the button.</span></span> <span data-ttu-id="9ad18-174">그러면 패키지가 실행되는 동안 잠깐 일시 중지된 후 패키지에서 계산한 집계 값, 즉 캐나다의 고객 수가 폼의 입력란에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ad18-174">After a brief pause while the package runs, you should see the aggregate value calculated by the package (the count of customers in Canada) displayed in the text box on the form.</span></span>

### <a name="sample-code"></a><span data-ttu-id="9ad18-175">샘플 코드</span><span class="sxs-lookup"><span data-stu-id="9ad18-175">Sample Code</span></span>

```vb
Imports System.Data
Imports Microsoft.SqlServer.Dts.DtsClient

Public Class Form1

  Private Sub btnRun_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRun.Click

    Dim dtexecArgs As String
    Dim dataReaderName As String
    Dim countryName As String

    Dim dtsConnection As DtsConnection
    Dim dtsCommand As DtsCommand
    Dim dtsDataReader As IDataReader
    Dim dtsParameter As DtsDataParameter

    Windows.Forms.Cursor.Current = Cursors.WaitCursor

    dtexecArgs = "/FILE ""C:\...\DtsClientWParamPkg.dtsx"""
    dataReaderName = "DataReaderDest"
    countryName = "Canada"

    dtsConnection = New DtsConnection()
    With dtsConnection
      .ConnectionString = dtexecArgs
      .Open()
    End With

    dtsCommand = New DtsCommand(dtsConnection)
    dtsCommand.CommandText = dataReaderName

    dtsParameter = New DtsDataParameter("Country", DbType.String)
    dtsParameter.Direction = ParameterDirection.Input
    dtsCommand.Parameters.Add(dtsParameter)

    dtsParameter.Value = countryName

    dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default)

    With dtsDataReader
      .Read()
      txtResults.Text = .GetInt32(0).ToString("N0")
    End With

    'After reaching the end of data rows,
    ' call the Read method one more time.
    Try
      dtsDataReader.Read()
    Catch ex As Exception
      MessageBox.Show("Exception on final call to Read method:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception on final call to Read method", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    ' The following method is a best practice, and is
    '  required when using DtsDataParameter objects.
    dtsCommand.Dispose()

    Try
      dtsDataReader.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing DataReader:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing DataReader", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Try
      dtsConnection.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing connection:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing connection", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Windows.Forms.Cursor.Current = Cursors.Default

  End Sub

End Class
```

```csharp
using System;
using System.Windows.Forms;
using System.Data;
using Microsoft.SqlServer.Dts.DtsClient;

namespace DtsClientWParamCS
{
  public partial class Form1 : Form
  {
    public Form1()
    {
      InitializeComponent();
      this.btnRun.Click += new System.EventHandler(this.btnRun_Click);
    }

    private void btnRun_Click(object sender, EventArgs e)
    {
      string dtexecArgs;
      string dataReaderName;
      string countryName;

      DtsConnection dtsConnection;
      DtsCommand dtsCommand;
      IDataReader dtsDataReader;
      DtsDataParameter dtsParameter;

      Cursor.Current = Cursors.WaitCursor;

      dtexecArgs = @"/FILE ""C:\...\DtsClientWParamPkg.dtsx""";
      dataReaderName = "DataReaderDest";
      countryName = "Canada";

      dtsConnection = new DtsConnection();
      {
        dtsConnection.ConnectionString = dtexecArgs;
        dtsConnection.Open();
      }

      dtsCommand = new DtsCommand(dtsConnection);
      dtsCommand.CommandText = dataReaderName;

      dtsParameter = new DtsDataParameter("Country", DbType.String);
      dtsParameter.Direction = ParameterDirection.Input;
      dtsCommand.Parameters.Add(dtsParameter);

      dtsParameter.Value = countryName;

      dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default);

      {
        dtsDataReader.Read();
        txtResults.Text = dtsDataReader.GetInt32(0).ToString("N0");
      }

      //After reaching the end of data rows,
      // call the Read method one more time.
      try
      {
        dtsDataReader.Read();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception on final call to Read method:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception on final call to Read method", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      // The following method is a best practice, and is
      //  required when using DtsDataParameter objects.
      dtsCommand.Dispose();

      try
      {
        dtsDataReader.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing DataReader:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing DataReader", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      try
      {
        dtsConnection.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing connection:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing connection", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      Cursor.Current = Cursors.Default;

    }
  }
}
```

<span data-ttu-id="9ad18-176">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="9ad18-176">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9ad18-177">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="9ad18-177">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9ad18-178">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="9ad18-178">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9ad18-179">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="9ad18-179">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ad18-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ad18-180">See Also</span></span>
 <span data-ttu-id="9ad18-181">[로컬 실행과 원격 실행의 차이점 이해](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) 프로그래밍 방식으로 [원격 패키지](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) 를 프로그래밍 [방식](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) 으로 로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="9ad18-181">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) [Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) [Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)</span></span>


