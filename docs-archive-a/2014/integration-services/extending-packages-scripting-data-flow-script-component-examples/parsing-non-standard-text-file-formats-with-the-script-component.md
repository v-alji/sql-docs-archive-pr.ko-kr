---
title: 스크립트 구성 요소를 사용하여 비표준 텍스트 파일 형식의 구문 분석 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- text file reading [Integration Services]
- Script component [Integration Services], non-standard text file formats
- transformations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: 1fda034d-09e4-4647-9a9f-e8d508c2cc8f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a0ca1a0d10bdad40d39a366864a07d2b0a61d13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729636"
---
# <a name="parsing-non-standard-text-file-formats-with-the-script-component"></a><span data-ttu-id="a7f6a-102">스크립트 구성 요소를 사용하여 비표준 텍스트 파일 형식의 구문 분석</span><span class="sxs-lookup"><span data-stu-id="a7f6a-102">Parsing Non-Standard Text File Formats with the Script Component</span></span>
  <span data-ttu-id="a7f6a-103">원본 데이터가 비표준 형식으로 정렬된 경우 여러 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 변환을 함께 결합하는 것보다 모든 구문 분석 논리를 단일 스크립트에 통합하는 것이 더 쉬울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-103">When your source data is arranged in a non-standard format, you may find it more convenient to consolidate all your parsing logic in a single script than to chain together multiple [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] transformations to achieve the same result.</span></span>  
  
 [<span data-ttu-id="a7f6a-104">예제 1: 행으로 구분된 레코드에 대한 구문 분석</span><span class="sxs-lookup"><span data-stu-id="a7f6a-104">Example 1: Parsing Row-Delimited Records</span></span>](#example1)  
  
 [<span data-ttu-id="a7f6a-105">예제 2: 부모 레코드와 자식 레코드 분할</span><span class="sxs-lookup"><span data-stu-id="a7f6a-105">Example 2: Splitting Parent and Child Records</span></span>](#example2)  
  
> [!NOTE]  
>  <span data-ttu-id="a7f6a-106">여러 데이터 흐름 태스크 및 여러 패키지에서 쉽게 다시 사용할 수 있는 구성 요소를 만들려면 이 스크립트 구성 요소 예제에 있는 코드를 바탕으로 사용자 지정 데이터 흐름 구성 요소를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-106">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="a7f6a-107">자세한 내용은 [사용자 지정 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
##  <a name="example-1-parsing-row-delimited-records"></a><a name="example1"></a> <span data-ttu-id="a7f6a-108">예 1: 행으로 구분된 레코드에 대한 구문 분석</span><span class="sxs-lookup"><span data-stu-id="a7f6a-108">Example 1: Parsing Row-Delimited Records</span></span>  
 <span data-ttu-id="a7f6a-109">이 예에서는 각 데이터 열이 별도의 줄에 나타나는 텍스트 파일을 가져오고 스크립트 구성 요소를 사용하여 이를 대상 테이블로 구문 분석하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-109">This example shows how to take a text file in which each column of data appears on a separate line and parse it into a destination table by using the Script component.</span></span>  
  
 <span data-ttu-id="a7f6a-110">데이터 흐름에서 변환으로 사용할 스크립트 구성 요소를 구성 하는 방법에 대 한 자세한 내용은 스크립트 구성 요소 [를 사용 하 여 동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)및 [스크립트 구성 요소를 사용 하 여 비동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-110">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="a7f6a-111">스크립트 구성 요소 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="a7f6a-111">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="a7f6a-112">다음 원본 데이터가 포함된 **rowdelimiteddata.txt**라는 텍스트 파일을 만들고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-112">Create and save a text file named **rowdelimiteddata.txt** that contains the following source data:</span></span>  
  
    ```  
    FirstName: Nancy  
    LastName: Davolio  
    Title: Sales Representative  
    City: Seattle  
    StateProvince: WA  
  
    FirstName: Andrew  
    LastName: Fuller  
    Title: Vice President, Sales  
    City: Tacoma  
    StateProvince: WA  
  
    FirstName: Steven  
    LastName: Buchanan  
    Title: Sales Manager  
    City: London  
    StateProvince:  
  
    ```  
  
2.  <span data-ttu-id="a7f6a-113">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 열고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-113">Open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="a7f6a-114">대상 데이터베이스를 선택하고 새 쿼리 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-114">Select a destination database, and open a new query window.</span></span> <span data-ttu-id="a7f6a-115">쿼리 창에서 다음 스크립트를 실행하여 대상 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-115">In the query window, execute the following script to create the destination table:</span></span>  
  
    ```  
    create table RowDelimitedData  
    (  
    FirstName varchar(32),  
    LastName varchar(32),  
    Title varchar(32),  
    City varchar(32),  
    StateProvince varchar(32)  
    )  
  
    ```  
  
4.  <span data-ttu-id="a7f6a-116">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]를 열고 ParseRowDelim.dtsx라는 새 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-116">Open [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package named ParseRowDelim.dtsx.</span></span>  
  
5.  <span data-ttu-id="a7f6a-117">패키지에 플랫 파일 연결 관리자를 추가하고 이름을 RowDelimitedData로 지정한 다음 해당 플랫 파일 연결 관리자가 이전 단계에서 만든 rowdelimiteddata.txt 파일에 연결하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-117">Add a Flat File connection manager to the package, name it RowDelimitedData, and configure it to connect to the rowdelimiteddata.txt file that you created in a previous step.</span></span>  
  
6.  <span data-ttu-id="a7f6a-118">패키지에 OLE DB 연결 관리자를 추가하고 해당 연결 관리자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 대상 테이블을 만든 데이터베이스에 연결하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-118">Add an OLE DB connection manager to the package and configure it to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the database in which you created the destination table.</span></span>  
  
7.  <span data-ttu-id="a7f6a-119">패키지에 데이터 흐름 태스크를 추가하고 SSIS 디자이너의 **데이터 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-119">Add a Data Flow task to the package and click the **Data Flow** tab of SSIS Designer.</span></span>  
  
8.  <span data-ttu-id="a7f6a-120">데이터 흐름에 플랫 파일 원본을 추가하고 해당 플랫 파일 원본이 RowDelimitedData 연결 관리자를 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-120">Add a Flat File Source to the data flow and configure it to use the RowDelimitedData connection manager.</span></span> <span data-ttu-id="a7f6a-121">**플랫 파일 원본 편집기**의 **열** 페이지에서 사용 가능한 단일 외부 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-121">On the **Columns** page of the **Flat File Source Editor**, select the single available external column.</span></span>  
  
9. <span data-ttu-id="a7f6a-122">데이터 흐름에 스크립트 구성 요소를 추가하고 이 구성 요소를 변환으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-122">Add a Script Component to the data flow and configure it as a transformation.</span></span> <span data-ttu-id="a7f6a-123">플랫 파일 원본의 출력을 스크립트 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-123">Connect the output of the Flat File Source to the Script Component.</span></span>  
  
10. <span data-ttu-id="a7f6a-124">스크립트 구성 요소를 두 번 클릭하여 **스크립트 변환 편집기**를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-124">Double-click the Script component to display the **Script Transformation Editor**.</span></span>  
  
11. <span data-ttu-id="a7f6a-125">**스크립트 변환 편집기** 대화 상자의 **입력 열** 페이지에서 사용 가능한 단일 입력 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-125">On the **Input Columns** page of the **Script Transformation Editor**, select the single available input column.</span></span>  
  
12. <span data-ttu-id="a7f6a-126">**스크립트 변환 편집기**의 **입/출력** 페이지에서 출력 0을 선택 하 고 `SynchronousInputID` 을 None으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-126">On the **Inputs and Outputs** page of the **Script Transformation Editor**, select Output 0 and set its `SynchronousInputID` to None.</span></span> <span data-ttu-id="a7f6a-127">길이가 32이고 문자열 유형이 모두 [DT_STR]인 5개의 출력 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-127">Create 5 output columns, all of type string [DT_STR] with a length of 32:</span></span>  
  
    -   <span data-ttu-id="a7f6a-128">FirstName</span><span class="sxs-lookup"><span data-stu-id="a7f6a-128">FirstName</span></span>  
  
    -   <span data-ttu-id="a7f6a-129">LastName</span><span class="sxs-lookup"><span data-stu-id="a7f6a-129">LastName</span></span>  
  
    -   <span data-ttu-id="a7f6a-130">제목</span><span class="sxs-lookup"><span data-stu-id="a7f6a-130">Title</span></span>  
  
    -   <span data-ttu-id="a7f6a-131">City</span><span class="sxs-lookup"><span data-stu-id="a7f6a-131">City</span></span>  
  
    -   <span data-ttu-id="a7f6a-132">StateProvince</span><span class="sxs-lookup"><span data-stu-id="a7f6a-132">StateProvince</span></span>  
  
13. <span data-ttu-id="a7f6a-133">스크립트 **변환 편집기**의 **스크립트** 페이지에서 **스크립트 편집** 을 클릭 하 고 예제의 클래스에 표시 된 코드를 입력 `ScriptMain` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-133">On the **Script** page of the **Script Transformation Editor**, click **Edit Script** and enter the code shown in the `ScriptMain` class of the example.</span></span> <span data-ttu-id="a7f6a-134">스크립트 개발 환경과 **스크립트 변환 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-134">Close the script development environment and the **Script Transformation Editor**.</span></span>  
  
14. <span data-ttu-id="a7f6a-135">데이트 흐름에 SQL Server 대상을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-135">Add a SQL Server Destination to the data flow.</span></span> <span data-ttu-id="a7f6a-136">SQL Server 대상이 OLE DB 연결 관리자와 RowDelimitedData 테이블을 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-136">Configure it to use the OLE DB connection manager and the RowDelimitedData table.</span></span> <span data-ttu-id="a7f6a-137">이 대상에 스크립트 구성 요소의 출력을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-137">Connect the output of the Script Component to this destination.</span></span>  
  
15. <span data-ttu-id="a7f6a-138">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-138">Run the package.</span></span> <span data-ttu-id="a7f6a-139">패키지의 실행이 완료되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상 테이블의 레코드를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-139">After the package has finished, examine the records in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination table.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Dim columnName As String  
    Dim columnValue As String  
  
    ' Check for an empty row.  
    If Row.Column0.Trim.Length > 0 Then  
        columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"))  
        ' Check for an empty value after the colon.  
        If Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd.Length > 1 Then  
            ' Extract the column value from after the colon and space.  
            columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2)  
            Select Case columnName  
                Case "FirstName"  
                    ' The FirstName value indicates a new record.  
                    Me.Output0Buffer.AddRow()  
                    Me.Output0Buffer.FirstName = columnValue  
                Case "LastName"  
                    Me.Output0Buffer.LastName = columnValue  
                Case "Title"  
                    Me.Output0Buffer.Title = columnValue  
                Case "City"  
                    Me.Output0Buffer.City = columnValue  
                Case "StateProvince"  
                    Me.Output0Buffer.StateProvince = columnValue  
            End Select  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
        string columnName;  
        string columnValue;  
  
        // Check for an empty row.  
        if (Row.Column0.Trim().Length > 0)  
        {  
            columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"));  
            // Check for an empty value after the colon.  
            if (Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd().Length > 1)  
            // Extract the column value from after the colon and space.  
            {  
                columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2);  
                switch (columnName)  
                {  
                    case "FirstName":  
                        // The FirstName value indicates a new record.  
                        this.Output0Buffer.AddRow();  
                        this.Output0Buffer.FirstName = columnValue;  
                        break;  
                    case "LastName":  
                        this.Output0Buffer.LastName = columnValue;  
                        break;  
                    case "Title":  
                        this.Output0Buffer.Title = columnValue;  
                        break;  
                    case "City":  
                        this.Output0Buffer.City = columnValue;  
                        break;  
                    case "StateProvince":  
                        this.Output0Buffer.StateProvince = columnValue;  
                        break;  
                }  
            }  
        }  
  
    }  
```  
  
##  <a name="example-2-splitting-parent-and-child-records"></a><a name="example2"></a> <span data-ttu-id="a7f6a-140">예제 2: 부모 레코드와 자식 레코드 분할</span><span class="sxs-lookup"><span data-stu-id="a7f6a-140">Example 2: Splitting Parent and Child Records</span></span>  
 <span data-ttu-id="a7f6a-141">이 예에서는 구분 행 뒤에 부모 레코드 행이 있고 그 뒤에 불특정 개수의 자식 레코드 행이 있는 텍스트 파일을 가져오고 스크립트 구성 요소를 사용하여 이를 올바르게 정규화된 부모 및 자식 대상 테이블로 구문 분석하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-141">This example shows how to take a text file, in which a separator row precedes a parent record row that is followed by an indefinite number of child record rows, and parse it into properly normalized parent and child destination tables by using the Script component.</span></span> <span data-ttu-id="a7f6a-142">이 간단한 예는 각각의 부모 및 자식 레코드에 둘 이상의 행 또는 열을 사용하는 원본 파일에 맞게 쉽게 조정할 수 있습니다. 단, 각 레코드의 시작 부분과 끝 부분을 식별할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-142">This simple example could easily be adapted for source files that use more than one row or column for each parent and child record, as long as there is some way to identify the beginning and end of each record.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a7f6a-143">이 예제는 예시 목적으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-143">This sample is intended for demonstration purposes only.</span></span> <span data-ttu-id="a7f6a-144">이 예제를 두 번 이상 실행하면 대상 테이블에 중복 키 값이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-144">If you run the sample more than once, it inserts duplicate key values into the destination table.</span></span>  
  
 <span data-ttu-id="a7f6a-145">데이터 흐름에서 변환으로 사용할 스크립트 구성 요소를 구성 하는 방법에 대 한 자세한 내용은 스크립트 구성 요소 [를 사용 하 여 동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)및 [스크립트 구성 요소를 사용 하 여 비동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-145">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="a7f6a-146">스크립트 구성 요소 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="a7f6a-146">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="a7f6a-147">다음 원본 데이터가 포함된 **parentchilddata.txt**라는 텍스트 파일을 만들고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-147">Create and save a text file named **parentchilddata.txt** that contains the following source data:</span></span>  
  
    ```  
    **********  
    PARENT 1 DATA  
    child 1 data  
    child 2 data  
    child 3 data  
    child 4 data  
    **********  
    PARENT 2 DATA  
    child 5 data  
    child 6 data  
    child 7 data  
    child 8 data  
    **********  
  
    ```  
  
2.  <span data-ttu-id="a7f6a-148">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 열고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-148">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="a7f6a-149">대상 데이터베이스를 선택하고 새 쿼리 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-149">Select a destination database, and open a new query window.</span></span> <span data-ttu-id="a7f6a-150">쿼리 창에서 다음 스크립트를 실행하여 대상 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-150">In the query window, execute the following script to create the destination tables:</span></span>  
  
    ```  
    CREATE TABLE [dbo].[Parents]([ParentID] [int] NOT NULL,  
    [ParentRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Parents] PRIMARY KEY CLUSTERED   
    ([ParentID] ASC))  
    GO  
    CREATE TABLE [dbo].[Children]([ChildID] [int] NOT NULL,  
    [ParentID] [int] NOT NULL,  
    [ChildRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Children] PRIMARY KEY CLUSTERED   
    ([ChildID] ASC))  
    GO  
    ALTER TABLE [dbo].[Children] ADD CONSTRAINT [FK_Children_Parents] FOREIGN KEY([ParentID])  
    REFERENCES [dbo].[Parents] ([ParentID])  
  
    ```  
  
4.  <span data-ttu-id="a7f6a-151">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 열고 SplitParentChild.dtsx라는 새 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-151">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package named SplitParentChild.dtsx.</span></span>  
  
5.  <span data-ttu-id="a7f6a-152">패키지에 플랫 파일 연결 관리자를 추가하고 이름을 ParentChildData로 지정한 다음 해당 플랫 파일 연결 관리자가 이전 단계에서 만든 parentchilddata.txt 파일에 연결하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-152">Add a Flat File connection manager to the package, name it ParentChildData, and configure it to connect to the parentchilddata.txt file that you created in a previous step.</span></span>  
  
6.  <span data-ttu-id="a7f6a-153">패키지에 OLE DB 연결 관리자를 추가하고 해당 연결 관리자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 대상 테이블을 만든 데이터베이스에 연결하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-153">Add an OLE DB connection manager to the package and configure it to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the database in which you created the destination tables.</span></span>  
  
7.  <span data-ttu-id="a7f6a-154">패키지에 데이터 흐름 태스크를 추가하고 SSIS 디자이너의 **데이터 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-154">Add a Data Flow task to the package and click the **Data Flow** tab of SSIS Designer.</span></span>  
  
8.  <span data-ttu-id="a7f6a-155">데이터 흐름에 플랫 파일 원본을 추가하고 해당 플랫 파일 원본이 ParentChildData 연결 관리자를 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-155">Add a Flat File Source to the data flow and configure it to use the ParentChildData connection manager.</span></span> <span data-ttu-id="a7f6a-156">**플랫 파일 원본 편집기**의 **열** 페이지에서 사용 가능한 단일 외부 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-156">On the **Columns** page of the **Flat File Source Editor**, select the single available external column.</span></span>  
  
9. <span data-ttu-id="a7f6a-157">데이터 흐름에 스크립트 구성 요소를 추가하고 이 구성 요소를 변환으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-157">Add a Script Component to the data flow and configure it as a transformation.</span></span> <span data-ttu-id="a7f6a-158">플랫 파일 원본의 출력을 스크립트 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-158">Connect the output of the Flat File Source to the Script Component.</span></span>  
  
10. <span data-ttu-id="a7f6a-159">스크립트 구성 요소를 두 번 클릭하여 **스크립트 변환 편집기**를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-159">Double-click the Script component to display the **Script Transformation Editor**.</span></span>  
  
11. <span data-ttu-id="a7f6a-160">**스크립트 변환 편집기** 대화 상자의 **입력 열** 페이지에서 사용 가능한 단일 입력 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-160">On the **Input Columns** page of the **Script Transformation Editor**, select the single available input column.</span></span>  
  
12. <span data-ttu-id="a7f6a-161">**스크립트 변환 편집기**의 **입/출력** 페이지에서 출력 0을 선택 하 고,이 이름을 parentrecords로 바꾸고, `SynchronousInputID` 을 None으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-161">On the **Inputs and Outputs** page of the **Script Transformation Editor**, select Output 0, rename it to ParentRecords, and set its `SynchronousInputID` to None.</span></span> <span data-ttu-id="a7f6a-162">다음과 같이 2개의 출력 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-162">Create 2 output columns:</span></span>  
  
    -   <span data-ttu-id="a7f6a-163">부호 있는 4바이트 정수 [DT_I4] 형식의 ParentID(기본 키)</span><span class="sxs-lookup"><span data-stu-id="a7f6a-163">ParentID (the primary key), of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="a7f6a-164">길이가 32인 문자열 [DT_STR] 형식의 ParentRecord</span><span class="sxs-lookup"><span data-stu-id="a7f6a-164">ParentRecord, of type string [DT_STR] with a length of 32.</span></span>  
  
13. <span data-ttu-id="a7f6a-165">두 번째 출력을 만들고 이름을 ChildRecords로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-165">Create a second output and name it ChildRecords.</span></span> <span data-ttu-id="a7f6a-166">새 출력의 `SynchronousInputID`는 이미 없음으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-166">The `SynchronousInputID` of the new output is already set to None.</span></span> <span data-ttu-id="a7f6a-167">다음과 같이 3개의 출력 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-167">Create 3 output columns:</span></span>  
  
    -   <span data-ttu-id="a7f6a-168">부호 있는 4바이트 정수 [DT_I4] 형식의 ChildID(기본 키)</span><span class="sxs-lookup"><span data-stu-id="a7f6a-168">ChildID (the primary key), of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="a7f6a-169">부호 있는 4바이트 정수 [DT_I4] 형식의 ParentID(외래 키)</span><span class="sxs-lookup"><span data-stu-id="a7f6a-169">ParentID (the foreign key), also of type four-byte signed integer [DT_I4]</span></span>  
  
    -   <span data-ttu-id="a7f6a-170">길이가 50인 문자열 [DT_STR] 형식의 ChildRecord</span><span class="sxs-lookup"><span data-stu-id="a7f6a-170">ChildRecord, of type string [DT_STR] with a length of 50</span></span>  
  
14. <span data-ttu-id="a7f6a-171">**스크립트 변환 편집기**의 **스크립트** 페이지에서 **스크립트 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-171">On the **Script** page of the **Script Transformation Editor**, click **Edit Script**.</span></span> <span data-ttu-id="a7f6a-172">`ScriptMain` 클래스에서 이 예에 표시된 코드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-172">In the `ScriptMain` class, enter the code shown in the example.</span></span> <span data-ttu-id="a7f6a-173">스크립트 개발 환경과 **스크립트 변환 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-173">Close the script development environment and the **Script Transformation Editor**.</span></span>  
  
15. <span data-ttu-id="a7f6a-174">데이트 흐름에 SQL Server 대상을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-174">Add a SQL Server Destination to the data flow.</span></span> <span data-ttu-id="a7f6a-175">이 대상에 스크립트 구성 요소의 ParentRecords 출력을 연결하고 해당 대상이 OLE DB 연결 관리자와 Parents 테이블을 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-175">Connect the ParentRecords output of the Script Component to this destination.Configure it to use the OLE DB connection manager and the Parents table.</span></span>  
  
16. <span data-ttu-id="a7f6a-176">데이트 흐름에 다른 SQL Server 대상을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-176">Add another SQL Server Destination to the data flow.</span></span> <span data-ttu-id="a7f6a-177">이 대상에 스크립트 구성 요소의 ChildRecords 출력을 연결하고</span><span class="sxs-lookup"><span data-stu-id="a7f6a-177">Connect the ChildRecords output of the Script Component to this destination.</span></span> <span data-ttu-id="a7f6a-178">해당 대상이 OLE DB 연결 관리자와 Children 테이블을 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-178">Configure it to use the OLE DB connection manager and the Children table.</span></span>  
  
17. <span data-ttu-id="a7f6a-179">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-179">Run the package.</span></span> <span data-ttu-id="a7f6a-180">패키지의 실행이 완료되면 두 개의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상 테이블에 있는 부모 및 자식 레코드를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-180">After the package has finished, examine the parent and child records in the two [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination tables.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Static nextRowIsParent As Boolean = False  
    Static parentCounter As Integer = 0  
    Static childCounter As Integer = 0  
  
    ' If current row starts with separator characters,  
    '  then following row contains new parent record.  
    If Row.Column0.StartsWith("***") Then  
        nextRowIsParent = True  
    Else  
        If nextRowIsParent Then  
            ' Current row contains parent record.  
            parentCounter += 1  
            Me.ParentRecordsBuffer.AddRow()  
            Me.ParentRecordsBuffer.ParentID = parentCounter  
            Me.ParentRecordsBuffer.ParentRecord = Row.Column0  
            nextRowIsParent = False  
        Else  
            ' Current row contains child record.  
            childCounter += 1  
            Me.ChildRecordsBuffer.AddRow()  
            Me.ChildRecordsBuffer.ChildID = childCounter  
            Me.ChildRecordsBuffer.ParentID = parentCounter  
            Me.ChildRecordsBuffer.ChildRecord = Row.Column0  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
    int static_Input0_ProcessInputRow_childCounter = 0;  
    int static_Input0_ProcessInputRow_parentCounter = 0;  
    bool static_Input0_ProcessInputRow_nextRowIsParent = false;  
  
        // If current row starts with separator characters,   
        // then following row contains new parent record.   
        if (Row.Column0.StartsWith("***"))  
        {  
            static_Input0_ProcessInputRow_nextRowIsParent = true;  
        }  
        else  
        {  
            if (static_Input0_ProcessInputRow_nextRowIsParent)  
            {  
                // Current row contains parent record.   
                static_Input0_ProcessInputRow_parentCounter += 1;  
                this.ParentRecordsBuffer.AddRow();  
                this.ParentRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ParentRecordsBuffer.ParentRecord = Row.Column0;  
                static_Input0_ProcessInputRow_nextRowIsParent = false;  
            }  
            else  
            {  
                // Current row contains child record.   
                static_Input0_ProcessInputRow_childCounter += 1;  
                this.ChildRecordsBuffer.AddRow();  
                this.ChildRecordsBuffer.ChildID = static_Input0_ProcessInputRow_childCounter;  
                this.ChildRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ChildRecordsBuffer.ChildRecord = Row.Column0;  
            }  
        }  
  
    }  
```  
  
<span data-ttu-id="a7f6a-181">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="a7f6a-181">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a7f6a-182">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-182">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a7f6a-183">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-183">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a7f6a-184">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-184">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f6a-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a7f6a-185">See Also</span></span>  
 [<span data-ttu-id="a7f6a-186">스크립트 구성 요소를 사용하여 동기 변환 만들기</span><span class="sxs-lookup"><span data-stu-id="a7f6a-186">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 [<span data-ttu-id="a7f6a-187">스크립트 구성 요소를 사용하여 비동기 변환 만들기</span><span class="sxs-lookup"><span data-stu-id="a7f6a-187">Creating an Asynchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
  
  
