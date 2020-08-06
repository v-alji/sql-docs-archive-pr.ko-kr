---
title: ADO를 사용 하 여 DiffGram 실행 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], SQLOLEDB Provider
- ADO [SQLXML]
- SQLXMLOLEDB Provider, DiffGrams
- data providers [SQLXML], SQLOLEDB Provider
- DiffGrams [SQLXML], ADO
ms.assetid: 741fce82-de83-4923-86eb-30acb5b9a5e6
author: rothja
ms.author: jroth
ms.openlocfilehash: b96db25fd46b1ecbbc15c8acd912743e5560f178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651592"
---
# <a name="executing-a-diffgram-by-using-ado-sqlxml-40"></a><span data-ttu-id="fe537-102">ADO를 사용하여 DiffGram 실행(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="fe537-102">Executing a DiffGram by Using ADO (SQLXML 4.0)</span></span>
  <span data-ttu-id="fe537-103">이 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 애플리케이션은 ADO를 사용하여 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결을 설정하고 DiffGram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-103">This [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic application uses ADO to establish a connection to an instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and then executes a DiffGram.</span></span> <span data-ttu-id="fe537-104">이 애플리케이션에서 DiffGram 및 XSD 스키마는 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-104">In this application, the DiffGram and the XSD schema are stored in a file.</span></span> <span data-ttu-id="fe537-105">애플리케이션은 지정된 파일에서 DiffGram을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-105">The application loads the DiffGram from the specified file.</span></span> <span data-ttu-id="fe537-106">[DiffGram 예제](diffgram-examples-sqlxml-4-0.md)에 설명 된 diffgram (및 관련 XSD 스키마)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-106">You can use any of the DiffGrams (and the associated XSD schema) described in [DiffGram Examples](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="fe537-107">다음은 예제 애플리케이션의 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-107">This is the process for the sample application:</span></span>  
  
-   <span data-ttu-id="fe537-108">**Conn** 개체 (**ADODB. Connection**) 특정 서버에서 SQL Server 실행 중인 인스턴스에 대 한 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-108">The **conn** object (**ADODB.Connection**) establishes a connection to a running instance of SQL Server on a specific server.</span></span>  
  
-   <span data-ttu-id="fe537-109">**Cmd** 개체 (**ADODB 명령**)는 설정 된 연결에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-109">The **cmd** object (**ADODB.Command**) executes on the established connection.</span></span>  
  
-   <span data-ttu-id="fe537-110">명령 언어가 DBGUID_MSSQLXML로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-110">The command dialect is set to DBGUID_MSSQLXML.</span></span>  
  
-   <span data-ttu-id="fe537-111">DiffGram은 파일에서 명령 스트림 (**Strmin**)으로 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-111">The DiffGram is copied to the command stream (**strmIn**) from a file.</span></span>  
  
-   <span data-ttu-id="fe537-112">명령의 출력 스트림은 **Strmout** 개체 (**ADODB. Stream**)을 클릭 하 여 반환 된 데이터를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-112">The command's output stream is set to the **StrmOut** object (**ADODB.Stream**) to receive any returned data.</span></span>  
  
-   <span data-ttu-id="fe537-113">SQLOLEDB 공급자를 사용하면 기본적으로 Sqlxmlx.dll에서 제공되는 Microsoft SQLXML 기능을 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-113">When you are using the SQLOLEDB Provider, by default you will get the Microsoft SQLXML functionality provided by Sqlxmlx.dll.</span></span> <span data-ttu-id="fe537-114">SQLOLEDB 공급자와 Sqlxml4.dll를 사용 하려면 SQLOLEDB 공급자 **연결** 개체에서 **sqlxml 버전** 속성을 **sqlxml. 4.0** 으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-114">To use Sqlxml4.dll with the SQLOLEDB Provider, the **SQLXML Version** property must be set to **SQLXML.4.0** on the SQLOLEDB Provider **Connection** object.</span></span>  
  
-   <span data-ttu-id="fe537-115">명령(DiffGram)이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-115">The command (DiffGram) is executed.</span></span>  
  
 <span data-ttu-id="fe537-116">예제 애플리케이션 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-116">The following code is the sample application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe537-117">코드에서 연결 문자열에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-117">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
Private Sub Command1_Click()  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmOut As New ADODB.Stream  
  Dim strmIn As New ADODB.Stream  
  
  'Open a connection to SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=SqlServerName; database=tempdb; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  strmIn.Open  
  strmIn.Charset = "UTF-8"  
  strmIn.LoadFromFile "C:\SomeFilePath\SampleDiffGram.xml"  
  strmIn.Position = 0  
  Set cmd.CommandStream = strmIn  
  
  strmOut.Open  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  cmd.Properties("Mapping Schema") = "C:\SomeFilePath\SampleDiffGram.xml"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Set cmd = Nothing  
  strmOut.Charset = "UTF-8"  
  strmOut.SaveToFile "C:\DropIt.txt", adSaveCreateOverWrite  
  strmOut.Close  
  Set strmOut = Nothing  
  
End Sub  
```  
  
### <a name="to-test-the-diffgram"></a><span data-ttu-id="fe537-118">DiffGram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="fe537-118">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="fe537-119">컴퓨터의 폴더에는 [DiffGram 예](diffgram-examples-sqlxml-4-0.md)의 예제 중 하나에서 diffgram 및 해당 XSD 스키마 중 하나를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-119">To a folder on your computer, copy any one of the DiffGrams and the corresponding XSD schema from one of the examples in [DiffGram Examples](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
2.  <span data-ttu-id="fe537-120">Visual Basic을 열고 표준 EXE 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-120">Open Visual Basic and create a Standard EXE project.</span></span>  
  
3.  <span data-ttu-id="fe537-121">프로젝트에 다음 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-121">Add these references to the project:</span></span>  
  
    ```  
    Microsoft ActiveX Data Objects 2.8 Library  
    ```  
  
4.  <span data-ttu-id="fe537-122">도구 상자에서 **CommandButton**을 클릭 한 다음 폼에 단추를 그립니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-122">In the Toolbox, click **CommandButton**, and then draw a button on the form.</span></span>  
  
5.  <span data-ttu-id="fe537-123">단추를 두 번 클릭하여 코드를 편집하고 이 항목에서 제공된 애플리케이션 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-123">Double-click the button to edit the code, and add the application code that is provided in the topic.</span></span>  
  
6.  <span data-ttu-id="fe537-124">코드에 DiffGram 및 XSD 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-124">Edit the code to specify the DiffGram and XSD file names.</span></span> <span data-ttu-id="fe537-125">연결 문자열 역시 적절하게 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-125">Also edit the connection string as appropriate.</span></span>  
  
7.  <span data-ttu-id="fe537-126">애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-126">Execute the application.</span></span> <span data-ttu-id="fe537-127">실행 결과는 사용자가 실행하는 DiffGram에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fe537-127">The result of the execution depends on what DiffGram you are executing.</span></span>  
  
  
