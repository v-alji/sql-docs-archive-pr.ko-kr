---
title: 스크립트 태스크를 사용하여 설치된 프린터 찾기 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- System.Drawing.Printing namespace
- printers [Integration Services]
- SSIS Script task, printers
- locating printers
- Printing namespace
- Script task [Integration Services], examples
- finding printers [SQL Server]
- Script task [Integration Services], printers
ms.assetid: 50a55014-e2c3-4ecd-84e1-3e877c55a260
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc4bc06879a55d4d07afca1011cc479dd7e7903a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736609"
---
# <a name="finding-installed-printers-with-the-script-task"></a><span data-ttu-id="10765-102">스크립트 태스크를 사용하여 설치된 프린터 찾기</span><span class="sxs-lookup"><span data-stu-id="10765-102">Finding Installed Printers with the Script Task</span></span>
  <span data-ttu-id="10765-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에서 변환된 데이터의 최종 대상은 인쇄된 보고서인 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10765-103">The data that is transformed by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages often has a printed report as its final destination.</span></span> <span data-ttu-id="10765-104">`System.Drawing.Printing`에서 네임 스페이스는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 프린터 작업을 위한 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="10765-104">The `System.Drawing.Printing` namespace in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides classes for working with printers.</span></span>

> [!NOTE]
>  <span data-ttu-id="10765-105">여러 패키지에서 쉽게 다시 사용할 수 있는 태스크를 만들려면 이 스크립트 태스크 예제에 있는 코드를 바탕으로 사용자 지정 태스크를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="10765-105">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="10765-106">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10765-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>

## <a name="description"></a><span data-ttu-id="10765-107">Description</span><span class="sxs-lookup"><span data-stu-id="10765-107">Description</span></span>
 <span data-ttu-id="10765-108">다음 예에서는 서버에 설치된 프린터 중 미국에서 사용하는 Legal 크기 용지를 지원하는 프린터를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="10765-108">The following example locates printers installed on the server that support legal size paper (as used in the United States).</span></span> <span data-ttu-id="10765-109">지원되는 용지 크기를 확인하는 코드는 프라이빗 함수에 캡슐화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10765-109">The code to check supported paper sizes is encapsulated in a private function.</span></span> <span data-ttu-id="10765-110">각 프린터에 대한 설정을 확인할 때 스크립트의 진행률을 추적할 수 있도록 스크립트에서는 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 메서드를 사용하여 Legal 크기 용지를 사용하는 프린터에 대한 정보 메시지를 발생시키거나 Legal 크기 용지를 사용하지 않는 프린터에 대해 경고를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="10765-110">To enable you to track the progress of the script as it checks the settings for each printer, the script uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method to raise an informational message for printers with legal size paper, and to raise a warning for printers without legal size paper.</span></span> <span data-ttu-id="10765-111">관련 메시지는 디자이너에서 패키지를 실행할 때 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSTA(Tools for Applications) IDE의 **출력** 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="10765-111">These messages appear in the **Output** window of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE when you run the package in the designer.</span></span>

#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="10765-112">이 스크립트 태스크 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="10765-112">To configure this Script Task example</span></span>

1.  <span data-ttu-id="10765-113">`Object` 유형의 `PrinterList`라는 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10765-113">Create the variable named `PrinterList` with type `Object`.</span></span>

2.  <span data-ttu-id="10765-114">**스크립트 태스크 편집기**의 **스크립트** 페이지에서 ReadWriteVariables 속성에 이 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="10765-114">On the **Script** page of the **Script Task Editor**, add this variable to the ReadWriteVariables property.</span></span>

3.  <span data-ttu-id="10765-115">스크립트 프로젝트에서 **System.Drawing** 네임스페이스에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="10765-115">In the script project, add a reference to the **System.Drawing** namespace.</span></span>

4.  <span data-ttu-id="10765-116">코드에서 `Imports` 문을 사용 하 여 **system.object** 와 `System.Drawing.Printing` 네임 스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="10765-116">In your code, use `Imports` statements to import the **System.Collections** and the `System.Drawing.Printing` namespaces.</span></span>

### <a name="code"></a><span data-ttu-id="10765-117">코드</span><span class="sxs-lookup"><span data-stu-id="10765-117">Code</span></span>

```vb
Public Sub Main()

    Dim printerName As String
    Dim currentPrinter As New PrinterSettings
    Dim size As PaperSize

    Dim printerList As New ArrayList
    For Each printerName In PrinterSettings.InstalledPrinters
        currentPrinter.PrinterName = printerName
        If PrinterHasLegalPaper(currentPrinter) Then
            printerList.Add(printerName)
            Dts.Events.FireInformation(0, "Example", _
                "Printer " & printerName & " has legal paper.", _
                String.Empty, 0, False)
        Else
            Dts.Events.FireWarning(0, "Example", _
                "Printer " & printerName & " DOES NOT have legal paper.", _
                String.Empty, 0)
        End If
    Next

    Dts.Variables("PrinterList").Value = printerList

    Dts.TaskResult = ScriptResults.Success

End Sub

Private Function PrinterHasLegalPaper( _
    ByVal thisPrinter As PrinterSettings) As Boolean

    Dim size As PaperSize
    Dim hasLegal As Boolean = False

    For Each size In thisPrinter.PaperSizes
        If size.Kind = PaperKind.Legal Then
            hasLegal = True
        End If
    Next

    Return hasLegal

End Function
```

```csharp
public void Main()
        {

            PrinterSettings currentPrinter = new PrinterSettings();
            PaperSize size;
            Boolean Flag = false;

            ArrayList printerList = new ArrayList();
            foreach (string printerName in PrinterSettings.InstalledPrinters)
            {
                currentPrinter.PrinterName = printerName;
                if (PrinterHasLegalPaper(currentPrinter))
                {
                    printerList.Add(printerName);
                    Dts.Events.FireInformation(0, "Example", "Printer " + printerName + " has legal paper.", String.Empty, 0, ref Flag);
                }
                else
                {
                    Dts.Events.FireWarning(0, "Example", "Printer " + printerName + " DOES NOT have legal paper.", String.Empty, 0);
                }
            }

            Dts.Variables["PrinterList"].Value = printerList;

            Dts.TaskResult = (int)ScriptResults.Success;

        }

        private bool PrinterHasLegalPaper(PrinterSettings thisPrinter)
        {

            bool hasLegal = false;

            foreach (PaperSize size in thisPrinter.PaperSizes)
            {
                if (size.Kind == PaperKind.Legal)
                {
                    hasLegal = true;
                }
            }

            return hasLegal;

        }
```

<span data-ttu-id="10765-118">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="10765-118">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="10765-119">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="10765-119">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="10765-120">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="10765-120">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="10765-121">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="10765-121">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="10765-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10765-122">See Also</span></span>
 [<span data-ttu-id="10765-123">스크립트 태스크 예</span><span class="sxs-lookup"><span data-stu-id="10765-123">Script Task Examples</span></span>](../extending-packages-scripting-task-examples/script-task-examples.md)


