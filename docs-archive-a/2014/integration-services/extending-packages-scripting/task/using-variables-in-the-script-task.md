---
title: 스크립트 태스크에서 변수 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2cd8fee5741c3d0e28e52c8712c3896428a05e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743384"
---
# <a name="using-variables-in-the-script-task"></a><span data-ttu-id="c313f-102">스크립트 태스크에서 변수 사용</span><span class="sxs-lookup"><span data-stu-id="c313f-102">Using Variables in the Script Task</span></span>
  <span data-ttu-id="c313f-103">스크립트 태스크에서는 변수를 통해 패키지의 다른 개체와 데이터를 교환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-103">Variables make it possible for the Script task to exchange data with other objects in the package.</span></span> <span data-ttu-id="c313f-104">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../../integration-services-ssis-variables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c313f-104">For more information, see [Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="c313f-105">스크립트 태스크에서는 `Dts` 개체의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성을 사용하여 패키지의 <xref:Microsoft.SqlServer.Dts.Runtime.Variable> 개체를 읽고 씁니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-105">The Script task uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object to read from and write to <xref:Microsoft.SqlServer.Dts.Runtime.Variable> objects in the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c313f-106"><xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> 클래스의 <xref:Microsoft.SqlServer.Dts.Runtime.Variable> 속성은 `Object` 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-106">The <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.Variable> class is of type `Object`.</span></span> <span data-ttu-id="c313f-107">스크립트 태스크에는 `Option Strict`가 설정되어 있으므로 스크립트 태스크를 사용하려면 먼저 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> 속성을 적절한 형식으로 캐스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-107">Because the Script task has `Option Strict` enabled, you must cast the <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property to the appropriate type before you can use it.</span></span>  
  
 <span data-ttu-id="c313f-108">**스크립트 태스크 편집기**의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> 및 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> 목록에 기존 변수를 추가하여 사용자 지정 스크립트에서 해당 변수를 사용할 수 있게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-108">You add existing variables to the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> and <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> lists in the **Script Task Editor** to make them available to the custom script.</span></span> <span data-ttu-id="c313f-109">변수 이름은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-109">Keep in mind that variable names are case-sensitive.</span></span> <span data-ttu-id="c313f-110">스크립트 내에서는 `Dts` 개체의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성을 통해 두 유형의 변수에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-110">Within the script, you access variables of both types through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object.</span></span> <span data-ttu-id="c313f-111">개별 변수를 읽고 쓰는 데는 `Value` 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-111">Use the `Value` property to read from and write to individual variables.</span></span> <span data-ttu-id="c313f-112">스크립트 태스크에서는 스크립트가 변수 값을 읽고 수정할 때 잠금을 투명하게 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-112">The Script task transparently manages locking as the script reads and modifies the values of variables.</span></span>  
  
 <span data-ttu-id="c313f-113"><xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> 속성에서 반환된 <xref:Microsoft.SqlServer.Dts.Runtime.Variables> 컬렉션의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 메서드를 사용하여 코드에서 변수를 사용하기 전에 해당 변수가 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-113">You can use the <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection returned by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property to check for the existence of a variable before using it in your code.</span></span>  
  
 <span data-ttu-id="c313f-114"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> 속성(Dts.VariableDispenser)을 사용하여 스크립트 태스크에서 변수를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-114">You can also use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> property (Dts.VariableDispenser) to work with variables in the Script task.</span></span> <span data-ttu-id="c313f-115"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>를 사용하는 경우 개발자가 자신의 고유 코드에서 잠금 의미 체계와 변수 값에 대한 데이터 형식 캐스팅을 모두 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-115">When using the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, you must handle both the locking semantics and the casting of data types for variable values in your own code.</span></span> <span data-ttu-id="c313f-116">디자인 타임에는 사용할 수 없지만 런타임에 프로그래밍 방식으로 만들어지는 변수를 사용하려면 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> 속성 대신 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-116">You may need to use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> property instead of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property if you want to work with a variable that is not available at design time but is created programmatically at run time.</span></span>  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a><span data-ttu-id="c313f-117">Foreach 루프 컨테이너 내에서 스크립트 태스크 사용</span><span class="sxs-lookup"><span data-stu-id="c313f-117">Using the Script Task within a Foreach Loop Container</span></span>  
 <span data-ttu-id="c313f-118">스크립트 태스크가 Foreach 루프 컨테이너 내에서 반복적으로 실행되는 경우 스크립트는 일반적으로 열거자에서 현재 항목의 내용을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-118">When a Script task runs repeatedly within a Foreach Loop container, the script usually needs to work with the contents of the current item in the enumerator.</span></span> <span data-ttu-id="c313f-119">예를 들어 Foreach File 열거자를 사용하는 경우에는 스크립트에서 현재 파일 이름을 알고 있어야 하며, Foreach ADO 열거자를 사용하는 경우에는 스크립트에서 현재 데이터 행의 열 내용을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-119">For example, when using a Foreach File enumerator, the script needs to know the current file name; when using a Foreach ADO enumerator, the script needs to know the contents of the columns in the current row of data.</span></span>  
  
 <span data-ttu-id="c313f-120">변수는 Foreach 루프 컨테이너와 스크립트 태스크 간의 이 통신을 가능하게 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-120">Variables make this communication between the Foreach Loop container and the Script task possible.</span></span> <span data-ttu-id="c313f-121">**Foreach 루프 편집기**의 **변수 매핑** 페이지에서는 열거된 단일 항목에서 반환된 각 데이터 항목에 변수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-121">On the **Variable Mappings** page of the **Foreach Loop Editor**, assign variables to each item of data that is returned by a single enumerated item.</span></span> <span data-ttu-id="c313f-122">예를 들어 Foreach File 열거자는 인덱스 0 위치의 파일 이름만 반환하므로 변수 매핑이 하나만 필요한 반면, 각 행의 여러 데이터 열을 반환하는 열거자의 경우에는 스크립트 태스크에서 사용할 각 열에 서로 다른 변수를 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-122">For example, a Foreach File enumerator returns only a file name at Index 0 and therefore requires only one variable mapping, whereas an enumerator that returns several columns of data in each row requires you to map a different variable to each column that you want to use in the Script task.</span></span>  
  
 <span data-ttu-id="c313f-123">열거 된 항목을 변수에 매핑한 후에는 스크립트 `ReadOnlyVariables` **태스크 편집기** 의 **스크립트** 페이지에 있는 속성에 매핑된 변수를 추가 하 여 스크립트에서 사용할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-123">After you have mapped enumerated items to variables, then you must add the mapped variables to the `ReadOnlyVariables` property on the **Script** page of the **Script Task Editor** to make them available to your script.</span></span> <span data-ttu-id="c313f-124">폴더의 이미지 파일을 처리하는 Foreach 루프 컨테이너 내에서의 스크립트 태스크에 대한 예제는 [스크립트 태스크를 사용한 이미지 작업](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c313f-124">For an example of a Script task within a Foreach Loop container that processes the image files in a folder, see [Working with Images with the Script Task](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).</span></span>  
  
## <a name="variables-example"></a><span data-ttu-id="c313f-125">변수 예</span><span class="sxs-lookup"><span data-stu-id="c313f-125">Variables Example</span></span>  
 <span data-ttu-id="c313f-126">다음 예에서는 스크립트 태스크에서 변수에 액세스하고 이를 사용하여 패키지 워크플로의 경로를 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-126">The following example demonstrates how to access and use variables in a Script task to determine the path of package workflow.</span></span> <span data-ttu-id="c313f-127">이 샘플에서는 및 라는 정수 변수를 만들고 `CustomerCount` `MaxRecordCount` `ReadOnlyVariables` **스크립트 태스크 편집기**에서 컬렉션에 추가 했다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-127">The sample assumes that you have created integer variables named `CustomerCount` and `MaxRecordCount` and added them to the `ReadOnlyVariables` collection in the **Script Task Editor**.</span></span> <span data-ttu-id="c313f-128">`CustomerCount` 변수에는 가져올 고객 레코드 수가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-128">The `CustomerCount` variable contains the number of customer records to be imported.</span></span> <span data-ttu-id="c313f-129">이 값이 `MaxRecordCount` 값보다 크면 스크립트 태스크에서 실패가 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-129">If its value is greater than the value of `MaxRecordCount`, the Script task reports failure.</span></span> <span data-ttu-id="c313f-130">`MaxRecordCount` 임계값 초과로 인해 실패할 경우 워크플로의 오류 경로에서 필요한 정리 작업을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-130">When a failure occurs because the `MaxRecordCount` threshold has been exceeded, the error path of the workflow can implement any required clean-up.</span></span>  
  
 <span data-ttu-id="c313f-131">이 예제를 컴파일하려면 Microsoft.SqlServer.ScriptTask 어셈블리에 대한 참조를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c313f-131">To successfully compile the sample, you need to add a reference to the Microsoft.SqlServer.ScriptTask assembly.</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
<span data-ttu-id="c313f-132">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="c313f-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c313f-133">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="c313f-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c313f-134">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="c313f-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c313f-135">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="c313f-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c313f-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c313f-136">See Also</span></span>  
 <span data-ttu-id="c313f-137">[Integration Services&#40;SSIS&#41; 변수](../../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="c313f-137">[Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="c313f-138">패키지에서 변수 사용</span><span class="sxs-lookup"><span data-stu-id="c313f-138">Use Variables in Packages</span></span>](../../use-variables-in-packages.md)  
  
  
