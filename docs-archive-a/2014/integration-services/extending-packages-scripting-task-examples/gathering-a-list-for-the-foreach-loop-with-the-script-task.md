---
title: 스크립트 태스크를 사용하여 ForEach 루프에 사용할 목록 수집 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], Foreach loops
- Script task [Integration Services], examples
- SSIS Script task, Foreach loops
ms.assetid: 694f0462-d0c5-4191-b64e-821b1bdef055
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 039860da121efaa52115bb515b158ea10373e459
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729632"
---
# <a name="gathering-a-list-for-the-foreach-loop-with-the-script-task"></a><span data-ttu-id="667d2-102">스크립트 태스크를 사용하여 ForEach 루프에 사용할 목록 수집</span><span class="sxs-lookup"><span data-stu-id="667d2-102">Gathering a List for the ForEach Loop with the Script Task</span></span>
  <span data-ttu-id="667d2-103">Foreach from Variable 열거자는 변수에서 해당 열거자에 전달된 목록의 항목을 열거하고 각 항목에 대해 동일한 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-103">The Foreach from Variable Enumerator enumerates over the items in a list that is passed to it in a variable and performs the same tasks on each item.</span></span> <span data-ttu-id="667d2-104">스크립트 태스크에서 사용자 지정 코드를 사용하여 이러한 용도로 사용할 목록을 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-104">You can use custom code in a Script task to populate a list for this purpose.</span></span> <span data-ttu-id="667d2-105">이 열거자에 대한 자세한 내용은 [Foreach 루프 컨테이너](../control-flow/foreach-loop-container.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="667d2-105">For more information about the enumerator, see [Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="667d2-106">여러 패키지에서 쉽게 다시 사용할 수 있는 태스크를 만들려면 이 스크립트 태스크 예제에 있는 코드를 바탕으로 사용자 지정 태스크를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="667d2-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="667d2-107">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="667d2-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="667d2-108">Description</span><span class="sxs-lookup"><span data-stu-id="667d2-108">Description</span></span>  
 <span data-ttu-id="667d2-109">다음 예에서는 `System.IO` 네임스페이스에서 메서드를 사용하여 컴퓨터에서 만든 날짜 또는 수정한 날짜가 사용자가 변수에 지정한 일 수를 경과하지 않았거나 경과한 Excel 통합 문서의 목록을 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-109">The following example uses methods from the `System.IO` namespace to gather a list of Excel workbooks on the computer that are either newer or older than a number of days specified by the user in a variable.</span></span> <span data-ttu-id="667d2-110">이 예에서는 C 드라이브의 디렉터리에서 확장명이 .xls인 파일을 재귀적으로 검색하고 각 파일을 마지막으로 수정한 날짜를 검사하여 목록에 포함할 파일인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-110">It searches directories on Drive C recursively for files that have the .xls extension and examines the date on which each file was last modified to determine whether the file belongs in the list.</span></span> <span data-ttu-id="667d2-111">그런 다음 조건에 맞는 파일을 `ArrayList`에 추가하고 이 `ArrayList`를 Foreach 루프 컨테이너에서 나중에 사용할 수 있도록 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-111">It adds qualifying files to an `ArrayList` and saves the `ArrayList` to a variable for later use in a Foreach Loop container.</span></span> <span data-ttu-id="667d2-112">Foreach 루프 컨테이너는 Foreach from Variable 열거자를 사용하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-112">The Foreach Loop container is configured to use the Foreach from Variable enumerator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="667d2-113">Foreach from Variable 열거자와 함께 사용하는 변수는 `Object` 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-113">The variable that you use with the Foreach from Variable Enumerator must be of type `Object`.</span></span> <span data-ttu-id="667d2-114">이 변수에 추가하는 개체는 `System.Collections.IEnumerable`, `System.Runtime.InteropServices.ComTypes.IEnumVARIANT`, `System.ComponentModel IListSource` 또는 `Microsoft.SqlServer.Dts.Runtime.Wrapper.ForEachEnumeratorHost` 인터페이스 중 하나를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-114">The object that you place in the variable must implement one of the following interfaces: `System.Collections.IEnumerable`, `System.Runtime.InteropServices.ComTypes.IEnumVARIANT`, `System.ComponentModel IListSource`, or `Microsoft.SqlServer.Dts.Runtime.Wrapper.ForEachEnumeratorHost`.</span></span> <span data-ttu-id="667d2-115">`Array` 또는 `ArrayList`는 일반적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-115">An `Array` or `ArrayList` is commonly used.</span></span> <span data-ttu-id="667d2-116">`ArrayList`가 사용되는 경우에는 `Imports` 네임스페이스에 대한 참조 및 `System.Collections` 문이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-116">The `ArrayList` requires a reference and an `Imports` statement for the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="667d2-117">`FileAge` 패키지 변수에 각기 다른 양수 및 음수 값을 사용하여 이 태스크를 시험해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-117">You can experiment with this task by using different positive and negative values for the `FileAge` package variable.</span></span> <span data-ttu-id="667d2-118">예를 들어 만든 지 5일이 지나지 않은 파일을 검색하려면 5를 입력하고, 만든 지 3일이 지난 파일을 검색하려면 -3을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-118">For example, you can enter 5 to search for files created in the last five days, or enter -3 to search for files that were created more than three days ago.</span></span> <span data-ttu-id="667d2-119">드라이브에 검색할 폴더가 많은 경우 이 태스크를 수행하는 데 1~2분 정도 소요될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-119">This task may take a minute or two on a drive with many folders to search.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="667d2-120">이 스크립트 태스크 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="667d2-120">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="667d2-121">`FileAge`라는 정수 형식의 패키지 변수를 만들고 양의 정수나 음의 정수 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-121">Create a package variable named `FileAge` of type integer and enter a positive or negative integer value.</span></span> <span data-ttu-id="667d2-122">값이 양수이면 코드는 만든 날짜 또는 수정한 날짜가 지정된 일 수를 경과하지 않은 파일을 검색하고, 값이 음수이면 지정된 일 수를 경과한 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-122">When the value is positive, the code searches for files newer than the specified number of days; when negative, for files older than the specified number of days.</span></span>  
  
2.  <span data-ttu-id="667d2-123">Foreach from Variable 열거자에서 나중에 사용할 수 있도록 스크립트 태스크에서 수집된 파일 목록을 받을 `FileList`라는 `Object` 형식의 패키지 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-123">Create a package variable named `FileList` of type `Object` to receive the list of files gathered by the Script task for later use by the Foreach from Variable Enumerator.</span></span>  
  
3.  <span data-ttu-id="667d2-124">스크립트 태스크의 `ReadOnlyVariables` 속성에 `FileAge` 변수를 추가하고, `ReadWriteVariables` 속성에 `FileList` 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-124">Add the `FileAge` variable to the Script task's `ReadOnlyVariables` property, and add the `FileList` variable to the `ReadWriteVariables` property.</span></span>  
  
4.  <span data-ttu-id="667d2-125">코드에서 `System.Collections` 및 `System.IO` 네임스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="667d2-125">In your code, import the `System.Collections` and the `System.IO` namespaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="667d2-126">코드</span><span class="sxs-lookup"><span data-stu-id="667d2-126">Code</span></span>  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Collections  
Imports System.IO  
  
Public Class ScriptMain  
  
  Private Const FILE_AGE As Integer = -50  
  
  Private Const FILE_ROOT As String = "C:\"  
  Private Const FILE_FILTER As String = "*.xls"  
  
  Private isCheckForNewer As Boolean = True  
  Dim fileAgeLimit As Integer  
  Private listForEnumerator As ArrayList  
  
  Public Sub Main()  
  
    fileAgeLimit = DirectCast(Dts.Variables("FileAge").Value, Integer)  
  
    ' If value provided is positive, we want files NEWER THAN n days.  
    '  If negative, we want files OLDER THAN n days.  
    If fileAgeLimit < 0 Then  
      isCheckForNewer = False  
    End If  
    ' Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit)  
  
    listForEnumerator = New ArrayList  
  
    GetFilesInFolder(FILE_ROOT)  
  
    ' Return the list of files to the variable  
    '  for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: " & listForEnumerator.Count.ToString, "Results", Windows.Forms.MessageBoxButtons.OK, Windows.Forms.MessageBoxIcon.Information)  
    Dts.Variables("FileList").Value = listForEnumerator  
  
    Dts.TaskResult = ScriptResults.Success  
  
  End Sub  
  
  Private Sub GetFilesInFolder(ByVal folderPath As String)  
  
    Dim localFiles() As String  
    Dim localFile As String  
    Dim fileChangeDate As Date  
    Dim fileAge As TimeSpan  
    Dim fileAgeInDays As Integer  
    Dim childFolder As String  
  
    Try  
      localFiles = Directory.GetFiles(folderPath, FILE_FILTER)  
      For Each localFile In localFiles  
        fileChangeDate = File.GetLastWriteTime(localFile)  
        fileAge = DateTime.Now.Subtract(fileChangeDate)  
        fileAgeInDays = fileAge.Days  
        CheckAgeOfFile(localFile, fileAgeInDays)  
      Next  
  
      If Directory.GetDirectories(folderPath).Length > 0 Then  
        For Each childFolder In Directory.GetDirectories(folderPath)  
          GetFilesInFolder(childFolder)  
        Next  
      End If  
  
    Catch  
      ' Ignore exceptions on special folders such as System Volume Information.  
    End Try  
  
  End Sub  
  
  Private Sub CheckAgeOfFile(ByVal localFile As String, ByVal fileAgeInDays As Integer)  
  
    If isCheckForNewer Then  
      If fileAgeInDays <= fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    Else  
      If fileAgeInDays > fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    End If  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Math;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Collections;  
using System.IO;  
  
public partial class ScriptMain : Microsoft.SqlServer.Dts.Tasks.ScriptTask.VSTARTScriptObjectModelBase  
    {  
  
        private const int FILE_AGE = -50;  
  
        private const string FILE_ROOT = "C:\\";  
        private const string FILE_FILTER = "*.xls";  
  
        private bool isCheckForNewer = true;  
        int fileAgeLimit;  
        private ArrayList listForEnumerator;  
  
        public void Main()  
  {  
  
    fileAgeLimit = (int)(Dts.Variables["FileAge"].Value);  
  
    // If value provided is positive, we want files NEWER THAN n days.  
    // If negative, we want files OLDER THAN n days.  
    if (fileAgeLimit<0)  
    {  
      isCheckForNewer = false;  
    }  
    // Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit);  
  
    ArrayList listForEnumerator = new ArrayList();  
  
    GetFilesInFolder(FILE_ROOT);  
  
    // Return the list of files to the variable  
    // for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: "+ listForEnumerator.Count, "Results",   
MessageBoxButtons.OK, MessageBoxIcon.Information);  
    Dts.Variables["FileList"].Value = listForEnumerator;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  
  }  
  
        private void GetFilesInFolder(string folderPath)  
        {  
  
            string[] localFiles;  
            DateTime fileChangeDate;  
            TimeSpan fileAge;  
            int fileAgeInDays;  
  
            try  
            {  
                localFiles = Directory.GetFiles(folderPath, FILE_FILTER);  
                foreach (string localFile in localFiles)  
                {  
                    fileChangeDate = File.GetLastWriteTime(localFile);  
                    fileAge = DateTime.Now.Subtract(fileChangeDate);  
                    fileAgeInDays = fileAge.Days;  
                    CheckAgeOfFile(localFile, fileAgeInDays);  
                }  
  
                if (Directory.GetDirectories(folderPath).Length > 0)  
                {  
                    foreach (string childFolder in Directory.GetDirectories(folderPath))  
                    {  
                        GetFilesInFolder(childFolder);  
                    }  
                }  
  
            }  
            catch  
            {  
                // Ignore exceptions on special folders, such as System Volume Information.  
            }  
  
        }  
  
        private void CheckAgeOfFile(string localFile, int fileAgeInDays)  
        {  
  
            if (isCheckForNewer)  
            {  
                if (fileAgeInDays <= fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
            else  
            {  
                if (fileAgeInDays > fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
  
        }  
  
    }  
```  
  
<span data-ttu-id="667d2-127">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="667d2-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="667d2-128">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="667d2-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="667d2-129">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="667d2-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="667d2-130">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="667d2-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="667d2-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="667d2-131">See Also</span></span>  
 <span data-ttu-id="667d2-132">[Foreach 루프 컨테이너](../control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="667d2-132">[Foreach Loop Container](../control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="667d2-133">Foreach 루프 컨테이너 구성</span><span class="sxs-lookup"><span data-stu-id="667d2-133">Configure a Foreach Loop Container</span></span>](../configure-a-foreach-loop-container.md)  
  
  
