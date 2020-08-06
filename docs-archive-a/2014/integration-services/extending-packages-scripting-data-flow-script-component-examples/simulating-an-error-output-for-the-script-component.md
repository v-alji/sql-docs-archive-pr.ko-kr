---
title: 스크립트 구성 요소의 오류 출력 시뮬레이션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], error output
- error outputs [Integration Services], Script component
ms.assetid: f8b6ecff-ac99-4231-a0e7-7ce4ad76bad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bed458ce378eb26cd863811b4974b5f39429e1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729635"
---
# <a name="simulating-an-error-output-for-the-script-component"></a><span data-ttu-id="870db-102">스크립트 구성 요소의 오류 출력 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="870db-102">Simulating an Error Output for the Script Component</span></span>
  <span data-ttu-id="870db-103">오류 행의 자동 처리를 위해 스크립트 구성 요소의 출력을 오류 출력으로 직접 구성할 수는 없지만 적절할 때 추가 출력을 만들고 스크립트에 조건부 논리를 사용하여 행을 이 출력으로 전송하는 방식으로 기본 제공 오류 출력의 기능을 재현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="870db-103">Although you cannot directly configure an output as an error output in the Script component for automatic handling of error rows, you can reproduce the functionality of a built-in error output by creating an additional output and using conditional logic in your script to direct rows to this output when appropriate.</span></span> <span data-ttu-id="870db-104">오류 번호와 오류가 발생한 열의 ID를 받는 두 개의 출력 열을 추가하여 기본 제공 오류 출력의 동작을 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="870db-104">You may want to imitate the behavior of a built-in error output by adding two additional output columns to receive the error number and the ID of the column in which an error occurred.</span></span>  
  
 <span data-ttu-id="870db-105">미리 정의된 특정 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 오류 코드에 해당하는 오류 설명을 추가하려면 스크립트 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> 속성을 통해 사용할 수 있는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-105">If you want to add the error description that corresponds to a specific predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error code, you can use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, available through the Script component's <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="870db-106">예제</span><span class="sxs-lookup"><span data-stu-id="870db-106">Example</span></span>  
 <span data-ttu-id="870db-107">이 예에서는 두 개의 동기 출력을 사용하는 변환으로 구성된 스크립트 구성 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-107">The example shown here uses a Script component configured as a transformation that has two synchronous outputs.</span></span> <span data-ttu-id="870db-108">이 스크립트 구성 요소의 목적은 AdventureWorks 예제 데이터베이스의 주소 데이터에서 오류 행을 필터링하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="870db-108">The purpose of the Script component is to filter error rows from address data in the AdventureWorks sample database.</span></span> <span data-ttu-id="870db-109">이 가상 예에서는 북아메리카 고객을 대상으로 홍보 행사를 준비 중이므로 필터를 사용하여 북아메리카에 위치하지 않은 주소를 제외해야 한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-109">This fictitious example assumes that we are preparing a promotion for North American customers and need to filter out addresses that are not located in North America.</span></span>  
  
#### <a name="to-configure-the-example"></a><span data-ttu-id="870db-110">예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="870db-110">To configure the example</span></span>  
  
1.  <span data-ttu-id="870db-111">새 스크립트 구성 요소를 만들기 전에 연결 관리자를 만들고 AdventureWorks 예제 데이터베이스에서 주소 데이터를 선택하도록 데이터 흐름 원본을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-111">Before creating the new Script component, create a connection manager and configure a data flow source that selects address data from the AdventureWorks sample database.</span></span> <span data-ttu-id="870db-112">CountryRegionName 열만 확인하는 이 예의 경우 단순히 Person.vStateCountryProvinceRegion 뷰를 사용해도 되고, Person.Address, Person.StateProvince 및 Person.CountryRegion 테이블을 조인하여 데이터를 선택해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="870db-112">For this example, which only looks at the CountryRegionName column, you can simply use the Person.vStateCountryProvinceRegion view, or you can select data by joining the Person.Address, Person.StateProvince, and Person.CountryRegion tables.</span></span>  
  
2.  <span data-ttu-id="870db-113">데이터 흐름 디자이너 화면에 새 스크립트 구성 요소를 추가하고 이 구성 요소를 변환으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-113">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span> <span data-ttu-id="870db-114">**스크립트 변환 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="870db-114">Open the **Script Transformation Editor**.</span></span>  
  
3.  <span data-ttu-id="870db-115">**스크립트** 페이지에서 **ScriptLanguage** 속성에 스크립트를 코딩하는 데 사용할 스크립트 언어를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-115">On the **Script** page, set the **ScriptLanguage** property to the script language that you want to use to code the script.</span></span>  
  
4.  <span data-ttu-id="870db-116">**스크립트 편집**을 클릭하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSTA(Tools for Applications)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="870db-116">Click **Edit Script** to open [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
5.  <span data-ttu-id="870db-117">`Input0_ProcessInputRow` 메서드에 아래에 표시된 예제 코드를 입력하거나 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="870db-117">In the `Input0_ProcessInputRow` method, type or paste the sample code shown below.</span></span>  
  
6.  <span data-ttu-id="870db-118">VSTA를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="870db-118">Close VSTA.</span></span>  
  
7.  <span data-ttu-id="870db-119">**입력 열** 페이지에서 스크립트 변환에서 처리할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-119">On the **Input Columns** page, select the columns that you want to process in the Script transformation.</span></span> <span data-ttu-id="870db-120">이 예에서는 CountryRegionName 열만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-120">This example uses only the CountryRegionName column.</span></span> <span data-ttu-id="870db-121">사용 가능한 입력 열 중 선택하지 않은 열은 데이터 흐름에서 변경되지 않은 상태로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="870db-121">Available input columns that you leave unselected will simply be passed through unchanged in the data flow.</span></span>  
  
8.  <span data-ttu-id="870db-122">**입/출력** 페이지에서 두 번째의 새 출력을 추가 하 고 해당 값을 `SynchronousInputID` 입력의 ID로 설정 합니다 .이 값은 `SynchronousInputID` 기본 출력의 속성 값 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-122">On the **Inputs and Outputs** page, add a new, second output, and set its `SynchronousInputID` value to the ID of the input, which is also the value of the `SynchronousInputID` property of the default output.</span></span> <span data-ttu-id="870db-123">두 출력 모두의 `ExclusionGroup` 속성을 0이 아닌 동일한 값(예: 1)으로 설정하여 각 행이 두 출력 중 하나로만 전송되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-123">Set the `ExclusionGroup` property of both outputs to the same non-zero value (for example, 1) to indicate that each row will be directed to only one of the two outputs.</span></span> <span data-ttu-id="870db-124">새 오류 출력에 "MyErrorOutput"과 같이 알기 쉬운 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-124">Give the new error output a distinctive name, such as "MyErrorOutput."</span></span>  
  
9. <span data-ttu-id="870db-125">오류 코드, 오류가 발생한 열의 ID, 오류 설명 등 원하는 오류 정보를 캡처하는 출력 열을 새 오류 출력에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-125">Add additional output columns to the new error output to capture the desired error information, which may include the error code, the ID of the column in which the error occurred, and possibly the error description.</span></span> <span data-ttu-id="870db-126">이 예에서는 ErrorColumn 및 ErrorMessage라는 새 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="870db-126">This example creates the new columns, ErrorColumn and ErrorMessage.</span></span> <span data-ttu-id="870db-127">개발자 고유의 구현에서 미리 정의된 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 오류를 catch하려는 경우 오류 번호에 대한 ErrorCode 열을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-127">If you are catching predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] errors in your own implementation, make sure to add an ErrorCode column for the error number.</span></span>  
  
10. <span data-ttu-id="870db-128">입력 열의 ID 값은 스크립트 구성 요소에서 오류 조건을 확인하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-128">Note the ID value of the input column or columns that the Script component will check for error conditions.</span></span> <span data-ttu-id="870db-129">이 예에서는 이 열 식별자를 사용하여 ErrorColumn 값을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="870db-129">This example uses this column identifier to populate the ErrorColumn value.</span></span>  
  
11. <span data-ttu-id="870db-130">**스크립트 변환 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="870db-130">Close the **Script Transformation Editor.**</span></span>  
  
12. <span data-ttu-id="870db-131">스크립트 구성 요소의 출력을 적절한 대상에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-131">Attach the outputs of the Script component to suitable destinations.</span></span> <span data-ttu-id="870db-132">임시 테스트용으로 구성하는 데는 플랫 파일 대상이 가장 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="870db-132">Flat file destinations are the easiest to configure for ad hoc testing.</span></span>  
  
13. <span data-ttu-id="870db-133">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="870db-133">Run the package.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  If Row.CountryRegionName <> "Canada" _  
      And Row.CountryRegionName <> "United States" Then  
  
    Row.ErrorColumn = 68 ' ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America."  
    Row.DirectRowToMyErrorOutput()  
  
  Else  
  
    Row.DirectRowToOutput0()  
  
  End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
{  
  
  if (Row.CountryRegionName!="Canada"&&Row.CountryRegionName!="United States")  
  
  {  
    Row.ErrorColumn = 68; // ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America.";  
    Row.DirectRowToMyErrorOutput();  
  
  }  
  else  
  {  
  
    Row.DirectRowToOutput0();  
  
  }  
  
}  
```  
  
<span data-ttu-id="870db-134">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="870db-134">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="870db-135">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="870db-135">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="870db-136">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="870db-136">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="870db-137">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="870db-137">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="870db-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="870db-138">See Also</span></span>  
 <span data-ttu-id="870db-139">[데이터의 오류 처리](../data-flow/error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="870db-139">[Error Handling in Data](../data-flow/error-handling-in-data.md) </span></span>  
 <span data-ttu-id="870db-140">[데이터 흐름 구성 요소에서 오류 출력 사용](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="870db-140">[Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="870db-141">스크립트 구성 요소를 사용하여 동기 변환 만들기</span><span class="sxs-lookup"><span data-stu-id="870db-141">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
