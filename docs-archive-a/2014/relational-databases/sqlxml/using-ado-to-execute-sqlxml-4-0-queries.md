---
title: ADO를 사용하여 SQLXML 4.0 쿼리 실행
ms.custom: ''
ms.date: 12/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- query testers [SQLXML]
- test scripts
- ADO [SQLXML]
- queries [SQLXML], ADO
- SQLXML, ADO
ms.assetid: 3d54e3bb-7c5f-427e-82f8-1403a54c4f53
author: rothja
ms.author: jroth
ms.openlocfilehash: 169d20b4192e4a5b8e7b32839f2da255fc58d89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729347"
---
# <a name="using-ado-to-execute-sqlxml-40-queries"></a><span data-ttu-id="7aea1-102">ADO를 사용하여 SQLXML 4.0 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="7aea1-102">Using ADO to Execute SQLXML 4.0 Queries</span></span>
  <span data-ttu-id="7aea1-103">SQLXML의 이전 버전에서는 SQLXML IIS 가상 디렉터리와 SQLXML ISAPI 필터를 사용하여 HTTP 기반 쿼리 실행이 지원되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-103">In previous versions of SQLXML, HTTP-based query execution was supported using SQLXML IIS virtual directories and the SQLXML ISAPI filter.</span></span> <span data-ttu-id="7aea1-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터 SQLXML IIS 가상 디렉터리 및 SQLXML ISAPI 필터와 유사하고 겹치는 기능이 네이티브 XML 웹 서비스와 함께 제공되므로 SQLXML 4.0에서는 이러한 구성 요소가 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-104">In SQLXML 4.0, these components have been removed as similar and overlapping functionality is provided with native XML Web services beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="7aea1-105">또는 MDAC(Microsoft Data Access Components) 2.6 이상에서 처음 도입된 ADO(ActiveX Data Objects)에 대한 SQLXML 확장을 이용하여 쿼리를 실행하고 COM 기반 애플리케이션에서 SQLXML 4.0을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-105">As an alternative, you can execute queries and use SQLXML 4.0 with your COM-based applications, by leveraging the SQLXML extensions to ActiveX Data Objects (ADO) that were first introduced in Microsoft Data Access Components (MDAC) 2.6 and later.</span></span>  
  
 <span data-ttu-id="7aea1-106">이 항목에서는 SQLXML 및 ADO를 VBScript(Visual Basic Scripting Edition) 애플리케이션(파일 확장명이 .vbs인 스크립트)의 일부로 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-106">This topic demonstrates using SQLXML and ADO as part of a Visual Basic Scripting Edition (VBScript) application (a script with the .vbs file extension).</span></span> <span data-ttu-id="7aea1-107">SQLXML 4.0 설명서의 쿼리 예제를 다시 만들고 테스트하는 데 유용한 초기 설치 절차를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-107">It provides initial setup procedures to help you recreate and test query samples in the SQLXML 4.0 documentation.</span></span>  
  
## <a name="creating-the-sqlxml-40-test-script"></a><span data-ttu-id="7aea1-108">SQLXML 4.0 테스트 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="7aea1-108">Creating the SQLXML 4.0 Test Script</span></span>  
 <span data-ttu-id="7aea1-109">이 절차에서는 ADO 2.6 이상의 SQLXML ADO 확장을 이용하여 SQLXML 쿼리를 실행하는 데 사용할 수 있는 VBScript(.vbs) 파일인 Sqlxml4test.vbs를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-109">In this procedure, you create a VBScript (.vbs) file, Sqlxml4test.vbs, which can be used to execute SQLXML queries by leveraging the SQLXML ADO extensions in ADO 2.6 and later.</span></span>  
  
#### <a name="to-create-the-sqlxml-40-query-tester-using-ado-vbscript"></a><span data-ttu-id="7aea1-110">ADO를 사용하여 SQLXML 4.0 쿼리 테스터를 만들려면(VBScript)</span><span class="sxs-lookup"><span data-stu-id="7aea1-110">To create the SQLXML 4.0 query tester using ADO (VBScript).</span></span>  
  
1.  <span data-ttu-id="7aea1-111">아래 VBScript 코드를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-111">Copy the VBScript code below, and paste it into a text file.</span></span> <span data-ttu-id="7aea1-112">파일을 Sqlxml4test.vbs로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-112">Save the file as Sqlxml4test.vbs.</span></span>  
  
    ```vb
    WScript.Echo "Query process may take a few seconds to complete. Please be patient."  
  
    ' Note that for SQL Server Native Client to be used as the data provider,  
    ' it needs to be installed on the client computer first. Also, SQLXML extensions   
    ' for ADO are used and available in MDAC 2.6 or later.  
  
    'Set script variables.  
    inputFile = "@@FILE_NAME@@"  
    strServer = "@@SERVER_NAME@@"  
    strDatabase = "@@DATABASE_NAME@@"  
    dbGuid = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  
    ' Establish ADO connection to SQL Server and   
    ' create an instance of the ADO Command object.  
    Set conn = CreateObject("ADODB.Connection")  
    Set cmd = CreateObject("ADODB.Command")  
    conn.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Server=" & strServer & _  
              ";Database=" & strDatabase & ";Integrated Security=SSPI"  
    Set cmd.ActiveConnection = conn  
  
    ' Create the input stream as an instance of the ADO Stream object.  
    Set inStream = CreateObject("ADODB.Stream")  
    inStream.Open  
    inStream.Charset = "utf-8"  
    inStream.LoadFromFile inputFile  
  
    ' Set ADO Command instance to use input stream.  
    Set cmd.CommandStream = inStream  
  
    ' Set the command dialect.  
    cmd.Dialect = dbGuid  
  
    ' Set a second ADO Stream instance for use as a results stream.   
    Set outStream = CreateObject("ADODB.Stream")  
    outStream.Open  
  
    ' Set dynamic properties used by the SQLXML ADO command instance.   
    cmd.Properties("XML Root").Value = "ROOT"  
    cmd.Properties("Output Encoding").Value = "UTF-8"  
  
    ' Connect the results stream to the command instance and execute the command.  
    cmd.Properties("Output Stream").Value = outStream  
    cmd.Execute , , 1024  
  
    ' Echo cropped/partial results to console.  
    WScript.Echo Left(outStream.ReadText, 1023)  
  
    inStream.Close  
    outStream.Close  
    ```  
  
2.  <span data-ttu-id="7aea1-113">테스트하려는 예제와 테스트 환경에 대해 다음 스크립트 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-113">Update the following script values for the sample you are trying to test and your test environment.</span></span>  
  
    -   <span data-ttu-id="7aea1-114">"`@@FILE_NAME@@`"을 찾아 해당 템플릿 파일 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-114">Find "`@@FILE_NAME@@`" and replace it with the name of your template file.</span></span>  
  
    -   <span data-ttu-id="7aea1-115">"`@@SERVER_NAME@@`"을 찾아 해당 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 이름(예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 로컬로 실행되고 있는 경우 "`(local)`")으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-115">Find "`@@SERVER_NAME@@`" and replace it with the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (for example, "`(local)`" if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running locally).</span></span>  
  
    -   <span data-ttu-id="7aea1-116">"`@@DATABASE_NAME@@`"을 찾아 데이터베이스 이름(예를 들어 "`AdventureWorks2012`" 또는 "`tempdb`")으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-116">Find "`@@DATABASE_NAME@@`" and replace it with the name of the database (for example, either "`AdventureWorks2012`" or "`tempdb`").</span></span>  
  
     <span data-ttu-id="7aea1-117">컴퓨터에 로컬로 다시 만들려는 예제에 대한 특정 지침에 명시된 경우 다른 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-117">Update any other values if mentioned in the specific instructions for the example you are attempting to recreate locally on your computer.</span></span>  
  
3.  <span data-ttu-id="7aea1-118">파일을 저장하고 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-118">Save the file and close it.</span></span>  
  
4.  <span data-ttu-id="7aea1-119">컴퓨터에 로컬로 다시 만들려는 예제에 포함되는 XML 템플릿 또는 스키마와 같은 추가 파일을 만들었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-119">Verify that you have created any additional files, such as XML templates or schemas that are part of the sample you are attempting to recreate locally on your computer.</span></span> <span data-ttu-id="7aea1-120">이러한 파일은 테스트 스크립트 파일(Sqlxml4test.vbs)을 저장한 디렉터리와 같은 디렉터리에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-120">These files should be located in the same directory where you have saved the test script file (Sqlxml4test.vbs).</span></span>  
  
5.  <span data-ttu-id="7aea1-121">SQLXML 4.0 테스트 스크립트를 사용하는 방법에 대한 다음 섹션의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-121">Follow the instructions in the next section for how to use the SQLXML 4.0 test script.</span></span>  
  
## <a name="using-the-sqlxml-40-test-script"></a><span data-ttu-id="7aea1-122">SQLXML 4.0 테스트 스크립트 사용</span><span class="sxs-lookup"><span data-stu-id="7aea1-122">Using the SQLXML 4.0 Test Script</span></span>  
 <span data-ttu-id="7aea1-123">다음 절차에서는 Sqlxml4test.vbs 파일을 사용하여 이 설명서에서 제공하는 예제 쿼리를 테스트하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-123">The following procedure describes how to use the Sqlxml4test.vbs files to test the example queries provided in this documentation.</span></span>  
  
#### <a name="to-use-the-sqlxml-40-query-tester"></a><span data-ttu-id="7aea1-124">SQLXML 4.0 쿼리 테스터를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="7aea1-124">To use the SQLXML 4.0 query tester</span></span>  
  
1.  <span data-ttu-id="7aea1-125">다음과 같이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-125">Verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed, as follows:</span></span>  
  
    1.  <span data-ttu-id="7aea1-126">**시작** 메뉴에서 **설정**을 가리킨 다음 **제어판**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-126">From the **Start** menu, point to **Settings**, and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="7aea1-127">제어판에서 **프로그램 추가/제거** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-127">In Control Panel, open **Add or Remove Programs**</span></span>  
  
    3.  <span data-ttu-id="7aea1-128">현재 설치 된 프로그램 목록에서 **Microsoft SQL Server Native Client** 가 목록에 나타나는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-128">In the list of currently installed programs, verify that **Microsoft SQL Server Native Client** appears in the list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="7aea1-129">Native Client를 설치 해야 하 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 경우 [SQL Server Native Client 설치](../native-client/applications/installing-sql-server-native-client.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7aea1-129">If you need to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
2.  <span data-ttu-id="7aea1-130">클라이언트 컴퓨터에 대해 설치된 MDAC 버전이 2.6 이상인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-130">Verify that the version of MDAC installed for the client computer is 2.6 or later.</span></span> <span data-ttu-id="7aea1-131">MDAC 버전 정보를 확인 해야 하는 경우 Microsoft 웹 사이트에서 무료 다운로드로 제공 되는 MDAC 구성 요소 검사기 도구를 사용할 수 있습니다 [https://www.microsoft.com/](https://www.microsoft.com/) .</span><span class="sxs-lookup"><span data-stu-id="7aea1-131">If you need to verify MDAC version information, you can use the MDAC Component Checker tool, which is provided as free download from the Microsoft Web site [https://www.microsoft.com/](https://www.microsoft.com/).</span></span> <span data-ttu-id="7aea1-132">자세한 내용을 보려면 Microsoft 웹 사이트에서 "MDAC 구성 요소 검사기"를 검색 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7aea1-132">For more information, search on "MDAC Component Checker" on the Microsoft Web site.</span></span>  
  
3.  <span data-ttu-id="7aea1-133">스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-133">Execute the script.</span></span>  
  
     <span data-ttu-id="7aea1-134">명령줄에서 Cscript.exe를 사용하거나 Sqlxml4test.vbs 파일을 두 번 클릭하여 Windows 스크립트 호스트(WScript.exe)를 호출하면 VBScript 파일을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-134">You can execute the VBScript file either at the command line using Cscript.exe or by double-clicking Sqlxml4test.vbs file to invoke the Windows Script Host (WScript.exe).</span></span>  
  
     <span data-ttu-id="7aea1-135">스크립트를 실행하면 쿼리 결과를 스크립트 출력으로 반환하고 표시하기까지 스크립트를 실행하는 데 시간이 걸릴 수 있음을 경고하는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-135">When executed, the script should display a message to alert you that the script might take a few moments to execute before returning and displaying query results as script output.</span></span> <span data-ttu-id="7aea1-136">출력이 나타나면 출력 내용을 예제의 예상 출력과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="7aea1-136">When the output appears, compare its contents to the expected results for the sample.</span></span>  
  
  
