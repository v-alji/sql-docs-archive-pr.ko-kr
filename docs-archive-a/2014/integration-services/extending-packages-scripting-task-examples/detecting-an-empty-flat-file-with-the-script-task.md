---
title: 스크립트 태스크를 사용하여 빈 플랫 파일 검색 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- flat files
- Script task [Integration Services], empty flat files
- SSIS Script task, empty flat files
- Script task [Integration Services], examples
ms.assetid: 1b4defb8-886a-483d-8056-d1b91d37bc90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 379b11bd18752ad648fc5f24d11d9ed5bfb63e14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651769"
---
# <a name="detecting-an-empty-flat-file-with-the-script-task"></a><span data-ttu-id="a1c5c-102">스크립트 태스크를 사용하여 빈 플랫 파일 검색</span><span class="sxs-lookup"><span data-stu-id="a1c5c-102">Detecting an Empty Flat File with the Script Task</span></span>
  <span data-ttu-id="a1c5c-103">플랫 파일 원본에서는 플랫 파일의 처리를 시도하기 전에 플랫 파일에 데이터 행이 들어 있는지 여부를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-103">The Flat File source does not determine whether a flat file contains rows of data before attempting to process it.</span></span> <span data-ttu-id="a1c5c-104">그러나 데이터 행이 들어 있지 않은 파일을 건너뛰면 특히 수많은 플랫 파일을 반복하는 패키지 등에서 패키지 효율성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-104">You may want to improve the efficiency of a package, especially of a package that iterates over numerous flat files, by skipping files that do not contain any rows of data.</span></span> <span data-ttu-id="a1c5c-105">스크립트 태스크는 패키지에서 데이터 흐름의 처리를 시작하기 전에 빈 플랫 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-105">The Script task can look for an empty flat file before the package begins to process the data flow.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1c5c-106">여러 패키지에서 쉽게 다시 사용할 수 있는 태스크를 만들려면 이 스크립트 태스크 예제에 있는 코드를 바탕으로 사용자 지정 태스크를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="a1c5c-107">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="a1c5c-108">Description</span><span class="sxs-lookup"><span data-stu-id="a1c5c-108">Description</span></span>  
 <span data-ttu-id="a1c5c-109">다음 예에서는 `System.IO` 네임스페이스의 메서드로 플랫 파일 연결 관리자에서 지정한 플랫 파일을 테스트하여 해당 파일이 비어 있는지 여부나 열 머리글 또는 빈 줄과 같이 필요한 비데이터 행만 들어 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-109">The following example uses methods from the `System.IO` namespace to test the flat file specified in a Flat File connection manager to determine whether the file is empty, or whether it contains only expected non-data rows such as column headers or an empty line.</span></span> <span data-ttu-id="a1c5c-110">이 스크립트에서는 먼저 파일 크기를 확인합니다. 크기가 0바이트이면 해당 파일은 비어 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-110">The script checks the size of the file first; if the size is zero bytes, the file is empty.</span></span> <span data-ttu-id="a1c5c-111">파일 크기가 0보다 크면 스크립트에서는 줄이 더 이상 없거나 줄 수가 비데이터 행의 예상 개수를 초과할 때까지 파일의 줄을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-111">If the file size is greater than zero, the script reads lines from the file until there are no more lines, or until the number of lines exceeds the expected number of non-data rows.</span></span> <span data-ttu-id="a1c5c-112">파일의 줄 수가 비데이터 행의 예상 개수보다 작거나 같으면 해당 파일은 비어 있는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-112">If the number of lines in the file is less than or equal to the expected number of non-data rows, then the file is considered empty.</span></span> <span data-ttu-id="a1c5c-113">결과는 패키지의 제어 흐름에서 분기하는 데 사용할 수 있는 값을 갖는 사용자 변수에 부울 값으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-113">The result is returned as a Boolean value in a user variable, the value of which can be used for branching in the package's control flow.</span></span> <span data-ttu-id="a1c5c-114">`FireInformation`또한이 메서드는 **Output** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSTA (Tools for Applications)의 출력 창에 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-114">The `FireInformation` method also displays the result in the **Output** window of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="a1c5c-115">이 스크립트 태스크 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="a1c5c-115">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="a1c5c-116">이라는 플랫 파일 연결 관리자를 만들고 구성 `EmptyFlatFileTest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-116">Create and configure a flat file connection manager named `EmptyFlatFileTest`.</span></span>  
  
2.  <span data-ttu-id="a1c5c-117">`FFNonDataRows`라는 정수 변수를 만들고 해당 값을 플랫 파일에 필요한 비데이터 행의 개수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-117">Create an integer variable named `FFNonDataRows` and set its value to the number of non-data rows expected in the flat file.</span></span>  
  
3.  <span data-ttu-id="a1c5c-118">`FFIsEmpty`라는 부울 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-118">Create a Boolean variable named `FFIsEmpty`.</span></span>  
  
4.  <span data-ttu-id="a1c5c-119">스크립트 태스크의 **ReadOnlyVariables** 속성에 `FFNonDataRows` 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-119">Add the `FFNonDataRows` variable to the Script task's **ReadOnlyVariables** property.</span></span>  
  
5.  <span data-ttu-id="a1c5c-120">스크립트 태스크의 **ReadWriteVariables** 속성에 `FFIsEmpty` 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-120">Add the `FFIsEmpty` variable to the Script task's **ReadWriteVariables** property.</span></span>  
  
6.  <span data-ttu-id="a1c5c-121">코드에서 `System.IO` 네임스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-121">In your code, import the `System.IO` namespace.</span></span>  
  
 <span data-ttu-id="a1c5c-122">단일 플랫 파일 연결 관리자를 사용하는 대신 Foreach File 열거자를 사용하여 파일을 반복하는 경우에는 아래의 예제 코드를 수정하여 연결 관리자 대신 열거된 값이 저장된 변수에서 파일 이름과 경로를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-122">If you are iterating over files with a Foreach File enumerator, instead of using a single Flat File connection manager, you will need to modify the sample code below to obtain the file name and path from the variable in which the enumerated value is stored instead of from the connection manager.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a1c5c-123">코드</span><span class="sxs-lookup"><span data-stu-id="a1c5c-123">Code</span></span>  
  
```vb  
Public Sub Main()  
  
  Dim nonDataRows As Integer = _  
      DirectCast(Dts.Variables("FFNonDataRows").Value, Integer)  
  Dim ffConnection As String = _  
      DirectCast(Dts.Connections("EmptyFlatFileTest").AcquireConnection(Nothing), _  
      String)  
  Dim flatFileInfo As New FileInfo(ffConnection)  
  ' If file size is 0 bytes, flat file does not contain data.  
  Dim fileSize As Long = flatFileInfo.Length  
  If fileSize > 0 Then  
    Dim lineCount As Integer = 0  
    Dim line As String  
    Dim fsFlatFile As New StreamReader(ffConnection)  
    Do Until fsFlatFile.EndOfStream  
      line = fsFlatFile.ReadLine  
      lineCount += 1  
      ' If line count > expected number of non-data rows,  
      '  flat file contains data (default value).  
      If lineCount > nonDataRows Then  
        Exit Do  
      End If  
      ' If line count <= expected number of non-data rows,  
      '  flat file does not contain data.  
      If lineCount <= nonDataRows Then  
        Dts.Variables("FFIsEmpty").Value = True  
      End If  
    Loop  
  Else  
    Dts.Variables("FFIsEmpty").Value = True  
  End If  
  
  Dim fireAgain As Boolean = False  
  Dts.Events.FireInformation(0, "Script Task", _  
      String.Format("{0}: {1}", ffConnection, _  
      Dts.Variables("FFIsEmpty").Value.ToString), _  
      String.Empty, 0, fireAgain)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            int nonDataRows = (int)(Dts.Variables["FFNonDataRows"].Value);  
            string ffConnection = (string)(Dts.Connections["EmptyFlatFileTest"].AcquireConnection(null) as String);  
            FileInfo flatFileInfo = new FileInfo(ffConnection);  
            // If file size is 0 bytes, flat file does not contain data.  
            long fileSize = flatFileInfo.Length;  
            if (fileSize > 0)  
            {  
  
                int lineCount = 0;  
                string line;  
                StreamReader fsFlatFile = new StreamReader(ffConnection);  
                while (!(fsFlatFile.EndOfStream))  
                {  
                    Console.WriteLine (fsFlatFile.ReadLine());  
                    lineCount += 1;  
                    // If line count > expected number of non-data rows,  
                    //  flat file contains data (default value).  
                    if (lineCount > nonDataRows)  
                    {  
                        break;  
                    }  
                    // If line count <= expected number of non-data rows,  
                    //  flat file does not contain data.  
                    if (lineCount <= nonDataRows)  
                    {  
                        Dts.Variables["FFIsEmpty"].Value = true;  
                    }  
                }  
            }  
            else  
            {  
                Dts.Variables["FFIsEmpty"].Value = true;  
            }  
  
            bool fireAgain = false;  
            Dts.Events.FireInformation(0, "Script Task", String.Format("{0}: {1}", ffConnection, Dts.Variables["FFIsEmpty"].Value), String.Empty, 0, ref fireAgain);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
```  
  
<span data-ttu-id="a1c5c-124">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="a1c5c-124">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a1c5c-125">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-125">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a1c5c-126">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-126">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a1c5c-127">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="a1c5c-127">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c5c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1c5c-128">See Also</span></span>  
 [<span data-ttu-id="a1c5c-129">스크립트 태스크 예</span><span class="sxs-lookup"><span data-stu-id="a1c5c-129">Script Task Examples</span></span>](../extending-packages-scripting-task-examples/script-task-examples.md)  
  
  
