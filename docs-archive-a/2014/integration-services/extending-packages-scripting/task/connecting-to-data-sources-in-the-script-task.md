---
title: 스크립트 태스크에서 데이터 원본에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- connections [Integration Services], scripts
- Integration Services packages, connections
- connection managers [Integration Services], scripts
- scripts [Integration Services], connections
- SSIS packages, connections
- packages [Integration Services], connections
- Script task [Integration Services], connections
- Connections property
- SQL Server Integration Services packages, connections
- SSIS Script task, connections
ms.assetid: 9c008380-715b-455b-9da7-22572d67c388
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2c8374271c7972498361a83e4bbe87ad12265827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731908"
---
# <a name="connecting-to-data-sources-in-the-script-task"></a><span data-ttu-id="776df-102">스크립트 태스크에서 데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="776df-102">Connecting to Data Sources in the Script Task</span></span>
  <span data-ttu-id="776df-103">연결 관리자를 사용하면 패키지에 구성된 데이터 원본에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="776df-103">Connection managers provide access to data sources that have been configured in the package.</span></span> <span data-ttu-id="776df-104">자세한 내용은 [Integration Services&#40;SSIS&#41; 연결](../../connection-manager/integration-services-ssis-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="776df-104">For more information, see [Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
 <span data-ttu-id="776df-105">스크립트 태스크에서는 **Dts** 개체의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> 속성을 통해 이러한 연결 관리자에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-105">The Script task can access these connection managers through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> property of the **Dts** object.</span></span> <span data-ttu-id="776df-106"><xref:Microsoft.SqlServer.Dts.Runtime.Connections> 컬렉션의 각 연결 관리자는 기본 데이터 원본에 연결하는 방법에 대한 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-106">Each connection manager in the <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection stores information about how to connect to the underlying data source.</span></span>  
  
 <span data-ttu-id="776df-107">연결 관리자의 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 메서드를 호출하면 해당 연결 관리자는 데이터 원본이 아직 연결되어 있지 않은 경우 데이터 원본에 연결하고 개발자가 스크립트 태스크 코드에서 사용할 수 있는 적절한 연결 및 연결 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-107">When you call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of a connection manager, the connection manager connects to the data source, if it is not already connected, and returns the appropriate connection or connection information for you to use in your Script task code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="776df-108">`AcquireConnection`을 호출하려면 먼저 연결 관리자에서 반환하는 연결 유형을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-108">You must know the type of connection returned by the connection manager before calling `AcquireConnection`.</span></span> <span data-ttu-id="776df-109">스크립트 태스크에는 `Option Strict`가 설정되어 있으므로 `Object` 형식으로 반환된 연결을 사용하려면 먼저 이 연결을 적절한 연결 유형으로 캐스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-109">Because the Script task has `Option Strict` enabled, you must cast the connection, which is returned as type `Object`, to the appropriate connection type before you can use it.</span></span>  
  
 <span data-ttu-id="776df-110">코드에서 연결을 사용하기 전에 <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> 속성에서 반환된 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 컬렉션의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> 메서드를 사용하여 기존 연결을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="776df-110">You can use the <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection returned by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> property to look for an existing connection before using the connection in your code.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="776df-111">스크립트 태스크의 관리 코드에서는 OLE DB 연결 관리자 및 Excel 연결 관리자와 같이 관리되지 않는 개체를 반환하는 연결 관리자의 AcquireConnection 메서드를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="776df-111">You cannot call the AcquireConnection method of connection managers that return unmanaged objects, such as the OLE DB connection manager and the Excel connection manager, in the managed code of a Script task.</span></span> <span data-ttu-id="776df-112">그러나 이러한 연결 관리자의 ConnectionString 속성을 읽고 system.xml 네임 스페이스의와 연결 문자열을 사용 하 여 코드에서 직접 데이터 원본에 연결할 수 있습니다. `OledbConnection` **System.Data.OleDb**</span><span class="sxs-lookup"><span data-stu-id="776df-112">However, you can read the ConnectionString property of these connection managers, and connect to the data source directly in your code by using the connection string with an `OledbConnection` from the **System.Data.OleDb** namespace.</span></span>  
>   
>  <span data-ttu-id="776df-113">관리되지 않는 개체를 반환하는 연결 관리자의 AcquireConnection 메서드를 호출해야 하는 경우에는 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 연결 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-113">If you must call the AcquireConnection method of a connection manager that returns an unmanaged object, use an [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager.</span></span> <span data-ttu-id="776df-114">[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 연결 관리자에서 OLE DB 공급자를 사용하도록 구성할 경우 이 연결 관리자는 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Data Provider for OLE DB를 사용하여 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-114">When you configure the [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager to use an OLE DB provider, it connects by using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Data Provider for OLE DB.</span></span> <span data-ttu-id="776df-115">이 경우 AcquireConnection 메서드는 `System.Data.OleDb.OleDbConnection` 관리 되지 않는 개체 대신을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-115">In this case, the AcquireConnection method returns a `System.Data.OleDb.OleDbConnection` instead of an unmanaged object.</span></span> <span data-ttu-id="776df-116">[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 연결 관리자를 Excel 데이터 원본에 사용할 수 있도록 구성하려면 **연결 관리자** 대화 상자의 **모두** 페이지에서 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Jet를 선택하고 Excel 파일을 지정한 다음 **확장 속성** 값으로 `Excel 8.0`(Excel 97 이상의 경우)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-116">To configure an [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager for use with an Excel data source, select the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Jet, specify an Excel file, and enter `Excel 8.0` (for Excel 97 and later) as the value of **Extended Properties** on the **All** page of the **Connection Manager** dialog box.</span></span>  
  
## <a name="connections-example"></a><span data-ttu-id="776df-117">연결 예</span><span class="sxs-lookup"><span data-stu-id="776df-117">Connections Example</span></span>  
 <span data-ttu-id="776df-118">다음 예에서는 스크립트 태스크 내에서 연결 관리자에 액세스하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="776df-118">The following example demonstrates how to access connection managers from within the Script task.</span></span> <span data-ttu-id="776df-119">이 예제에서는 **Test ADO.NET Connection**이라는 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 연결 관리자와 **플랫 파일 연결 관리자**라는 플랫 파일 연결 관리자를 만들고 구성했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-119">The sample assumes that you have created and configured an [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager named **Test ADO.NET Connection** and a Flat File connection manager named **Test Flat File Connection**.</span></span> <span data-ttu-id="776df-120">[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 연결 관리자는 데이터 원본에 즉시 연결하는 데 사용할 수 있는 `SqlConnection` 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-120">Note that the [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager returns a `SqlConnection` object that you can use immediately to connect to the data source.</span></span> <span data-ttu-id="776df-121">반면에 플랫 파일 연결 관리자는 경로와 파일 이름이 들어 있는 문자열만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-121">The Flat File connection manager, on the other hand, returns only a string that contains the path and file name.</span></span> <span data-ttu-id="776df-122">플랫 파일을 열어 작업하려면 `System.IO` 네임스페이스의 메서드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="776df-122">You must use methods from the `System.IO` namespace to open and work with the flat file.</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim myADONETConnection As SqlClient.SqlConnection  
    myADONETConnection = _  
        DirectCast(Dts.Connections("Test ADO.NET Connection").AcquireConnection(Dts.Transaction), _  
        SqlClient.SqlConnection)  
    MsgBox(myADONETConnection.ConnectionString, _  
        MsgBoxStyle.Information, "ADO.NET Connection")  
  
    Dim myFlatFileConnection As String  
    myFlatFileConnection = _  
        DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _  
        String)  
    MsgBox(myFlatFileConnection, MsgBoxStyle.Information, "Flat File Connection")  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
  
public class ScriptMain  
{  
  
        public void Main()  
        {  
            SqlConnection myADONETConnection = new SqlConnection();  
            myADONETConnection = (SqlConnection)(Dts.Connections["Test ADO.NET Connection"].AcquireConnection(Dts.Transaction)as SqlConnection);  
            MessageBox.Show(myADONETConnection.ConnectionString, "ADO.NET Connection");  
  
            string myFlatFileConnection;  
            myFlatFileConnection = (string)(Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);  
            MessageBox.Show(myFlatFileConnection, "Flat File Connection");  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
  
```  
  
<span data-ttu-id="776df-123">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="776df-123">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="776df-124">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="776df-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="776df-125">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="776df-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="776df-126">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="776df-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="776df-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="776df-127">See Also</span></span>  
 <span data-ttu-id="776df-128">[SSIS&#41; 연결을 &#40;Integration Services](../../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="776df-128">[Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="776df-129">연결 관리자 만들기</span><span class="sxs-lookup"><span data-stu-id="776df-129">Create Connection Managers</span></span>](../../create-connection-managers.md)  
  
  
