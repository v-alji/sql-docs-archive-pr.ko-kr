---
title: 스크립트 구성 요소를 사용하여 ODBC 대상 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 10adff11a7e1db24d9a244c3e83949a010b606c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652216"
---
# <a name="creating-an-odbc-destination-with-the-script-component"></a><span data-ttu-id="4f594-102">스크립트 구성 요소를 사용하여 ODBC 대상 만들기</span><span class="sxs-lookup"><span data-stu-id="4f594-102">Creating an ODBC Destination with the Script Component</span></span>
  <span data-ttu-id="4f594-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 일반적으로 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 대상 및 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for ODBC를 사용하여 ODBC 대상에 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you typically save data to an ODBC destination by using an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination and the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for ODBC.</span></span> <span data-ttu-id="4f594-104">그러나 단일 패키지에서 사용할 임시 ODBC 대상을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-104">However, you can also create an ad hoc ODBC destination for use in a single package.</span></span> <span data-ttu-id="4f594-105">이 임시 ODBC 대상을 만들려면 다음 예와 같이 스크립트 구성 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-105">To create this ad hoc ODBC destination, you use the Script component as shown in the following example.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f594-106">여러 데이터 흐름 태스크 및 여러 패키지에서 쉽게 다시 사용할 수 있는 구성 요소를 만들려면 이 스크립트 구성 요소 예제에 있는 코드를 바탕으로 사용자 지정 데이터 흐름 구성 요소를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="4f594-106">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="4f594-107">자세한 내용은 [사용자 지정 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4f594-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f594-108">예제</span><span class="sxs-lookup"><span data-stu-id="4f594-108">Example</span></span>  
 <span data-ttu-id="4f594-109">다음 예제에서는 기존 ODBC 연결 관리자를 사용하여 데이터 흐름에서 받은 데이터를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 저장하는 대상 구성 요소를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-109">The following example demonstrates how to create a destination component that uses an existing ODBC connection manager to save data from the data flow into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="4f594-110">이 예는 [스크립트 구성 요소를 사용하여 대상 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md) 항목에서 예로 보여 준 사용자 지정 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 대상의 수정된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-110">This example is a modified version of the custom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination that was demonstrated in the topic, [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="4f594-111">그러나 이 예에서 사용자 지정 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 대상은 ODBC 연결 관리자를 사용하고 데이터를 ODBC 대상에 저장하도록 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-111">However, in this example, the custom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination has been modified to work with an ODBC connection manager and save data to an ODBC destination.</span></span> <span data-ttu-id="4f594-112">이러한 수정 내용에는 다음과 같은 변경 내용도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-112">These modifications also include the following changes:</span></span>  
  
-   <span data-ttu-id="4f594-113">ODBC 연결 관리자의 `AcquireConnection` 메서드는 네이티브 개체를 반환하므로 관리 코드에서 이 메서드를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-113">You cannot call the `AcquireConnection` method of the ODBC connection manager from managed code, because it returns a native object.</span></span> <span data-ttu-id="4f594-114">따라서 이 예제에서는 연결 관리자의 연결 문자열을 사용하여 관리되는 ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자를 통해 데이터 원본에 직접 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-114">Therefore, this sample uses the connection string of the connection manager to connect to the data source directly by using the managed ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider.</span></span>  
  
-   <span data-ttu-id="4f594-115">`OdbcCommand`에는 위치 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-115">The `OdbcCommand` expects positional parameters.</span></span> <span data-ttu-id="4f594-116">매개 변수의 위치는 명령 텍스트에서 물음표(?)로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-116">The positions of the parameters are indicated by the question marks (?) in the text of the command.</span></span> <span data-ttu-id="4f594-117">반면 `SqlCommand`에는 명명된 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-117">(In contrast, a `SqlCommand` expects named parameters.)</span></span>  
  
 <span data-ttu-id="4f594-118">이 예에서는 **AdventureWorks** 예제 데이터베이스의 **Person.Address** 테이블을 사용하고,</span><span class="sxs-lookup"><span data-stu-id="4f594-118">This example uses the **Person.Address** table in the **AdventureWorks** sample database.</span></span> <span data-ttu-id="4f594-119">이 예에서는 데이터 흐름을 통해이 테이블의 첫 번째 및 네 번째 열인 **int \* AddressID**\* 및 **nvarchar (30) City** 열을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-119">The example passes the first and fourth columns, the **int\*AddressID**\* and **nvarchar(30)City** columns, of this table through the data flow.</span></span> <span data-ttu-id="4f594-120">동일한 데이터가 [특정 유형의 스크립트 구성 요소 개발](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md) 항목의 원본, 변환 및 대상 예제에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-120">This same data is used in the source, transformation, and destination samples in the topic, [Developing Specific Types of Script Components](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="4f594-121">스크립트 구성 요소 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="4f594-121">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="4f594-122">**AdventureWorks** 데이터베이스에 연결하는 ODBC 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-122">Create an ODBC connection manager that connects to the **AdventureWorks** database.</span></span>  
  
2.  <span data-ttu-id="4f594-123">**AdventureWorks** 데이터베이스에서 다음 Transact-SQL 명령을 실행하여 대상 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-123">Create a destination table by running the following Transact-SQL command in the **AdventureWorks** database:</span></span>  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  <span data-ttu-id="4f594-124">데이터 흐름 디자이너 화면에 새 스크립트 구성 요소를 추가하고 이 구성 요소를 대상으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-124">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>  
  
4.  <span data-ttu-id="4f594-125">업스트림 원본 또는 변환의 출력을 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 대상 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-125">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="4f594-126">변환하지 않고 원본을 대상에 직접 연결할 수 있습니다. 이 예제가 작동하려면 업스트림 구성 요소의 출력에는 **AdventureWorks** 예제 데이터베이스의 **Person.Address** 테이블에서 적어도 **AddressID** 및 **City** 열이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-126">(You can connect a source directly to a destination without any transformations.) To ensure that this sample works, the output of the upstream component must include at least the **AddressID** and **City** columns from the **Person.Address** table of the **AdventureWorks** sample database.</span></span>  
  
5.  <span data-ttu-id="4f594-127">**스크립트 변환 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-127">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="4f594-128">**입력 열** 페이지에서 **AddressID** 및 **City** 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-128">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>  
  
6.  <span data-ttu-id="4f594-129">**입/출력** 페이지에서 입력의 이름을 **MyAddressInput**과 같이 더 알기 쉬운 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-129">On the **Inputs and Outputs** page, rename the input with a more descriptive name such as **MyAddressInput**.</span></span>  
  
7.  <span data-ttu-id="4f594-130">**연결 관리자** 페이지에서 **MyODBCConnectionManager**와 같이 알기 쉬운 이름으로 ODBC 연결 관리자를 추가하거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-130">On the **Connection Managers** page, add or create the ODBC connection manager with a descriptive name such as **MyODBCConnectionManager**.</span></span>  
  
8.  <span data-ttu-id="4f594-131">**스크립트** 페이지에서 **스크립트 편집**을 클릭 한 다음 클래스에서 아래에 표시 된 스크립트를 입력 `ScriptMain` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-131">On the **Script** page, click **Edit Script**, and then enter the script shown below in the `ScriptMain` class.</span></span>  
  
9. <span data-ttu-id="4f594-132">스크립트 개발 환경을 닫고 **스크립트 변환 편집기**를 닫은 다음 예제를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4f594-132">Close the script development environment, close the **Script Transformation Editor**, and then run the sample.</span></span>  
  
    ```vb  
    Imports System.Data.Odbc  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim odbcConn As OdbcConnection  
        Dim odbcCmd As OdbcCommand  
        Dim odbcParam As OdbcParameter  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connectionString As String  
            connectionString = Me.Connections.MyODBCConnectionManager.ConnectionString  
            odbcConn = New OdbcConnection(connectionString)  
            odbcConn.Open()  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            odbcCmd = New OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
                "VALUES(?, ?)", odbcConn)  
            odbcParam = New OdbcParameter("@addressid", OdbcType.Int)  
            odbcCmd.Parameters.Add(odbcParam)  
            odbcParam = New OdbcParameter("@city", OdbcType.NVarChar, 30)  
            odbcCmd.Parameters.Add(odbcParam)  
  
        End Sub  
  
        Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
            With odbcCmd  
                .Parameters("@addressid").Value = Row.AddressID  
                .Parameters("@city").Value = Row.City  
                .ExecuteNonQuery()  
            End With  
  
        End Sub  
  
        Public Overrides Sub ReleaseConnections()  
  
            odbcConn.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.Data.Odbc;  
    ...  
    public class ScriptMain :  
        UserComponent  
    {  
        OdbcConnection odbcConn;  
        OdbcCommand odbcCmd;  
        OdbcParameter odbcParam;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            string connectionString;  
            connectionString = this.Connections.MyODBCConnectionManager.ConnectionString;  
            odbcConn = new OdbcConnection(connectionString);  
            odbcConn.Open();  
  
        }  
  
        public override void PreExecute()  
        {  
  
            odbcCmd = new OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " +  
                "VALUES(?, ?)", odbcConn);  
            odbcParam = new OdbcParameter("@addressid", OdbcType.Int);  
            odbcCmd.Parameters.Add(odbcParam);  
            odbcParam = new OdbcParameter("@city", OdbcType.NVarChar, 30);  
            odbcCmd.Parameters.Add(odbcParam);  
  
        }  
  
        public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
        {  
  
            {  
                odbcCmd.Parameters["@addressid"].Value = Row.AddressID;  
                odbcCmd.Parameters["@city"].Value = Row.City;  
                odbcCmd.ExecuteNonQuery();  
            }  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            odbcConn.Close();  
  
        }  
    }  
    ```  
  
<span data-ttu-id="4f594-133">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="4f594-133">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4f594-134">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4f594-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4f594-135">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4f594-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4f594-136">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="4f594-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f594-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4f594-137">See Also</span></span>  
 [<span data-ttu-id="4f594-138">스크립트 구성 요소를 사용하여 대상 만들기</span><span class="sxs-lookup"><span data-stu-id="4f594-138">Creating a Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
