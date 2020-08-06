---
title: 스크립트 구성 요소를 사용하여 오류 출력 향상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 18637aa1e147ce989645ae859681929f4d0c438a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660692"
---
# <a name="enhancing-an-error-output-with-the-script-component"></a><span data-ttu-id="86d95-102">스크립트 구성 요소를 사용하여 오류 출력 향상</span><span class="sxs-lookup"><span data-stu-id="86d95-102">Enhancing an Error Output with the Script Component</span></span>
  <span data-ttu-id="86d95-103">기본적으로 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 오류 출력의 추가 열인 ErrorCode 및 ErrorColumn에는 오류 번호를 나타내는 숫자 코드와 오류가 발생한 열의 ID만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-103">By default, the two extra columns in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error output, ErrorCode and ErrorColumn, contain only numeric codes that represent an error number, and the ID of the column in which the error occurred.</span></span> <span data-ttu-id="86d95-104">이러한 숫자 값은 해당 오류 설명이 없으므로 사용이 제한적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-104">These numeric values may be of limited use without the corresponding error description.</span></span>  
  
 <span data-ttu-id="86d95-105">이 항목에서는 스크립트 구성 요소를 사용하여 데이터 흐름의 기존 오류 출력 데이터에 오류 설명을 추가하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-105">This topic describes how to add an error description column to existing error output data in the data flow by using the Script component.</span></span> <span data-ttu-id="86d95-106">예에서는 스크립트 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> 속성을 통해 사용할 수 있는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 메서드를 사용하여 미리 정의된 특정 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 오류 코드에 해당하는 오류 설명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-106">The example adds the error description that corresponds to a specific predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error code by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, available through the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the Script component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86d95-107">여러 데이터 흐름 태스크 및 여러 패키지에서 쉽게 다시 사용할 수 있는 구성 요소를 만들려면 이 스크립트 구성 요소 예제에 있는 코드를 바탕으로 사용자 지정 데이터 흐름 구성 요소를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="86d95-107">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="86d95-108">자세한 내용은 [사용자 지정 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86d95-108">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86d95-109">예제</span><span class="sxs-lookup"><span data-stu-id="86d95-109">Example</span></span>  
 <span data-ttu-id="86d95-110">이 예에서는 변환으로 구성된 스크립트 구성 요소를 사용하여 데이터 흐름의 기존 오류 출력 데이터에 오류 설명 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-110">The example shown here uses a Script component configured as a transformation to add an error description column to existing error output data in the data flow.</span></span>  
  
 <span data-ttu-id="86d95-111">데이터 흐름에서 변환으로 사용할 스크립트 구성 요소를 구성 하는 방법에 대 한 자세한 내용은 스크립트 구성 요소 [를 사용 하 여 동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)및 [스크립트 구성 요소를 사용 하 여 비동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86d95-111">For more information about how to configure the Script component for use as a transformation in the data flow, see [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)and [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="86d95-112">스크립트 구성 요소 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="86d95-112">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="86d95-113">새 스크립트 구성 요소를 만들기 전에 데이터 흐름의 업스트림 구성 요소에서 오류 또는 잘림이 발생할 경우 행을 오류 출력으로 리디렉션하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-113">Before creating the new Script component, configure an upstream component in the data flow to redirect rows to its error output when an error or truncation occurs.</span></span> <span data-ttu-id="86d95-114">테스트를 위해 오류가 발생하게 하는 방식으로 즉, 조회가 실패한 두 테이블 간에 조회 변환을 구성하여 구성 요소를 구성하려 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-114">For testing purposes, you may want to configure a component in a manner that ensures that errors will occur-for example, by configuring a Lookup transformation between two tables where the lookup will fail.</span></span>  
  
2.  <span data-ttu-id="86d95-115">데이터 흐름 디자이너 화면에 새 스크립트 구성 요소를 추가하고 이 구성 요소를 변환으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-115">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>  
  
3.  <span data-ttu-id="86d95-116">업스트림 구성 요소의 오류 출력을 새 스크립트 구성 요소에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-116">Connect the error output from the upstream component to the new Script component.</span></span>  
  
4.  <span data-ttu-id="86d95-117">**스크립트 변환 편집기**를 열고 **스크립트** 페이지의 **ScriptLanguage** 속성에서 스크립트 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-117">Open the **Script Transformation Editor**, and on the **Script** page, for the **ScriptLanguage** property, select the script language.</span></span>  
  
5.  <span data-ttu-id="86d95-118">**스크립트 편집**을 클릭하여  VSTA([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications) IDE를 열고 아래에 표시된 샘플 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-118">Click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE and add the sample code shown below.</span></span>  
  
6.  <span data-ttu-id="86d95-119">VSTA를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-119">Close VSTA.</span></span>  
  
7.  <span data-ttu-id="86d95-120">스크립트 변환 편집기의 **입력 열** 페이지에서 ErrorCode 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-120">In the Script Transformation Editor, on the **Input Columns** page, select the ErrorCode column.</span></span>  
  
8.  <span data-ttu-id="86d95-121">**입/출력** 페이지에서 ErrorDescription 이라는 형식의 새 출력 열을 추가 합니다 `String` . **ErrorDescription**</span><span class="sxs-lookup"><span data-stu-id="86d95-121">On the **Inputs and Outputs** page, add a new output column of type `String` named **ErrorDescription**.</span></span> <span data-ttu-id="86d95-122">긴 메시지를 지원할 수 있도록 새 열의 기본 길이를 255로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-122">Increase the default length of the new column to 255 to support long messages.</span></span>  
  
9. <span data-ttu-id="86d95-123">**스크립트 변환 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-123">Close the **Script Transformation Editor.**</span></span>  
  
10. <span data-ttu-id="86d95-124">스크립트 구성 요소의 출력을 적절한 대상에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-124">Attach the output of the Script component to a suitable destination.</span></span> <span data-ttu-id="86d95-125">임시 테스트용으로 구성하는 데는 플랫 파일 대상이 가장 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-125">A Flat File destination is the easiest to configure for ad hoc testing.</span></span>  
  
11. <span data-ttu-id="86d95-126">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="86d95-126">Run the package.</span></span>  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  Row.ErrorDescription = _  
    Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
  Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
    }  
}  
  
```  
  
<span data-ttu-id="86d95-127">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="86d95-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="86d95-128">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="86d95-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="86d95-129">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="86d95-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="86d95-130">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="86d95-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d95-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86d95-131">See Also</span></span>  
 <span data-ttu-id="86d95-132">[데이터 오류 처리](../data-flow/error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="86d95-132">[Error Handling in Data](../data-flow/error-handling-in-data.md) </span></span>  
 <span data-ttu-id="86d95-133">[데이터 흐름 구성 요소에서 오류 출력 사용](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="86d95-133">[Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="86d95-134">스크립트 구성 요소를 사용하여 동기 변환 만들기</span><span class="sxs-lookup"><span data-stu-id="86d95-134">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
