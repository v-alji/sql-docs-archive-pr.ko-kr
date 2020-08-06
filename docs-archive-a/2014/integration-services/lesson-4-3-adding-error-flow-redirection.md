---
title: '3단계: 오류 흐름 리디렉션 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5683a45d-9e73-4cd5-83ca-fae8b26b488c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ceaea310cba05a940f310c01b52d5f912a53bea8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650173"
---
# <a name="step-3-adding-error-flow-redirection"></a><span data-ttu-id="332ec-102">3단계: 오류 Flow 리디렉션 추가</span><span class="sxs-lookup"><span data-stu-id="332ec-102">Step 3: Adding Error Flow Redirection</span></span>
  <span data-ttu-id="332ec-103">이전 태스크에서 설명한 대로 Lookup Currency Key 변환은 오류를 생성한 손상된 예제 플랫 파일을 처리할 때 일치하는 항목을 생성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-103">As demonstrated in the previous task, the Lookup Currency Key transformation cannot generate a match when the transformation tries to process the corrupted sample flat file, which produced an error.</span></span> <span data-ttu-id="332ec-104">변환은 오류 출력에 대해 기본 설정을 사용하므로 오류가 발생하면 변환이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-104">Because the transformation uses the default settings for error output, any error causes the transformation to fail.</span></span> <span data-ttu-id="332ec-105">변환이 실패하면 나머지 패키지도 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-105">When the transformation fails, the rest of the package also fails.</span></span>  
  
 <span data-ttu-id="332ec-106">이때 변환이 실패하도록 두는 대신 오류 출력을 사용하여 실패한 행을 구성 요소가 다른 처리 경로로 리디렉션하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-106">Instead of permitting the transformation to fail, you can configure the component to redirect the failed row to another processing path by using the error output.</span></span> <span data-ttu-id="332ec-107">별도의 오류 처리 경로를 사용하면 다양한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-107">Use of a separate error processing path lets you do a number of things.</span></span> <span data-ttu-id="332ec-108">예를 들어 데이터를 정리한 다음 실패한 행을 다시 처리하거나</span><span class="sxs-lookup"><span data-stu-id="332ec-108">For instance, you might try to clean the data and then reprocess the failed row.</span></span> <span data-ttu-id="332ec-109">나중에 유효성을 검사하고 다시 처리할 수 있도록 추가 오류 정보와 함께 실패한 행을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-109">Or, you might save the failed row along with additional error information for later verification and reprocessing.</span></span>  
  
 <span data-ttu-id="332ec-110">이 태스크에서는 Lookup Currency Key 변환을 구성하여 실패하는 모든 행을 오류 출력으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-110">In this task, you will configure the Lookup Currency Key transformation to redirect any rows that fail to the error output.</span></span> <span data-ttu-id="332ec-111">이러한 행은 데이터 흐름의 오류 분기에서 파일에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-111">In the error branch of the data flow, these rows will be written to a file.</span></span>  
  
 <span data-ttu-id="332ec-112">기본적으로 오류 출력의 추가 열인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] **ErrorCode** 및 **errorcolumn**에는 오류 번호를 나타내는 숫자 코드와 오류가 발생 한 열의 ID만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-112">By default the two extra columns in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] error output, **ErrorCode** and **ErrorColumn**, contain only numeric codes that represent an error number, and the ID of the column in which the error occurred.</span></span> <span data-ttu-id="332ec-113">이러한 숫자 값은 해당 오류 설명이 없으므로 사용이 제한적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-113">These numeric values may be of limited use without the corresponding error description.</span></span>  
  
 <span data-ttu-id="332ec-114">실패한 행을 패키지가 파일에 기록하기 전에 스크립트 구성 요소를 사용하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] API에 액세스한 다음 오류 설명을 가져와 오류 출력의 유용성을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-114">To enhance the usefulness of the error output, before the package writes the failed rows to the file, you will use a Script component to access the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] API and get a description of the error.</span></span>  
  
### <a name="to-configure-an-error-output"></a><span data-ttu-id="332ec-115">오류 출력을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="332ec-115">To configure an error output</span></span>  
  
1.  <span data-ttu-id="332ec-116">**SSIS 도구 상자**에서 **일반**을 확장 한 다음 **스크립트 구성 요소** 를 **데이터 흐름** 탭의 디자인 화면으로 끌어다 놓습니다. **Lookup Currency Key** 변환의 오른쪽에 **스크립트** 를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-116">In the **SSIS Toolbox**, expand **Common**, and then drag **Script Component** onto the design surface of the **Data Flow** tab. Place **Script** to the right of the **Lookup Currency Key** transformation.</span></span>  
  
2.  <span data-ttu-id="332ec-117">**스크립트 구성 요소 유형 선택** 대화 상자에서 **변환**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-117">In the **Select Script Component Type** dialog box, click **Transformation**, and click **OK**.</span></span>  
  
3.  <span data-ttu-id="332ec-118">**Lookup Currency Key** 변환을 클릭하고 빨간색 화살표를 새로 추가한 **Script** 변환으로 끌어 두 구성 요소를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-118">Click the **Lookup Currency Key** transformation and then drag the red arrow onto the newly added **Script** transformation to connect the two components.</span></span>  
  
     <span data-ttu-id="332ec-119">빨간색 화살표는 **Lookup Currency Key** 변환의 오류 출력을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-119">The red arrow represents the error output of the **Lookup Currency Key** transformation.</span></span> <span data-ttu-id="332ec-120">빨간색 화살표를 통해 변환을 스크립트 구성 요소에 연결하여 모든 처리 오류를 스크립트 구성 요소에 리디렉션한 다음 이 구성 요소에서 오류를 처리하고 대상에 보내도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-120">By using the red arrow to connect the transformation to the Script component, you can redirect any processing errors to the Script component, which then processes the errors and sends them to the destination.</span></span>  
  
4.  <span data-ttu-id="332ec-121">**오류 출력 구성** 대화 상자의 **오류** 열에서 **행 리디렉션**을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-121">In the **Configure Error Output** dialog box, in the **Error** column, select **Redirect row**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="332ec-122">**데이터 흐름** 디자인 화면에서 새로 추가한 **스크립트 구성 요소** 의 **스크립트 구성 요소**를 클릭한 다음 이름을 **Get Error Description**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-122">On the **Data Flow** design surface, click **Script Component** in the newly added **ScriptComponent**, and change the name to **Get Error Description**.</span></span>  
  
6.  <span data-ttu-id="332ec-123">**Get Error Description** 변환을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-123">Double-click the **Get Error Description** transformation.</span></span>  
  
7.  <span data-ttu-id="332ec-124">**스크립트 변환 편집기** 대화 상자의 **입력 열** 페이지에서 **ErrorCode** 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-124">In the **Script Transformation Editor** dialog box, on the **Input Columns** page, select the **ErrorCode** column.</span></span>  
  
8.  <span data-ttu-id="332ec-125">**입/출력** 페이지에서 **출력 0**을 확장하고 **출력 열**을 클릭한 다음 **열 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-125">On the **Inputs and Outputs** page, expand **Output 0**, click **Output Columns**, and then click **Add Column**.</span></span>  
  
9. <span data-ttu-id="332ec-126">속성에 `Name` **ErrorDescription** 을 입력 하 고 속성을 `DataType` **유니코드 문자열 [DT_WSTR]** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-126">In the `Name` property, type **ErrorDescription** and set the `DataType` property to **Unicode string [DT_WSTR]**.</span></span>  
  
10. <span data-ttu-id="332ec-127">**스크립트** 페이지에서 `LocaleID` 속성이 **영어 (미국)** 로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-127">On the **Script** page, verify that the `LocaleID` property is set to **English (United States.**</span></span>  
  
11. <span data-ttu-id="332ec-128">**스크립트 편집**을 클릭하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSTA(Tools for Applications)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-128">Click **Edit Script** to open [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="332ec-129">`Input0_ProcessInputRow` 메서드에 다음 코드를 입력하거나 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-129">In the `Input0_ProcessInputRow` method, type or paste the following code.</span></span>  
  
     <span data-ttu-id="332ec-130">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="332ec-130">[Visual Basic]</span></span>  
  
    ```  
    Row.ErrorDescription =   
      Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
    ```  
  
     <span data-ttu-id="332ec-131">[Visual C#]</span><span class="sxs-lookup"><span data-stu-id="332ec-131">[Visual C#]</span></span>  
  
    ```  
    Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
    ```  
  
     <span data-ttu-id="332ec-132">완성된 서브루틴은 다음 코드와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-132">The completed subroutine will look like the following code.</span></span>  
  
     <span data-ttu-id="332ec-133">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="332ec-133">[Visual Basic]</span></span>  
  
    ```  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription =   
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
    ```  
  
     <span data-ttu-id="332ec-134">[Visual C#]</span><span class="sxs-lookup"><span data-stu-id="332ec-134">[Visual C#]</span></span>  
  
    ```  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
        {  
  
            Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
        }  
    ```  
  
12. <span data-ttu-id="332ec-135">**빌드** 메뉴에서 **솔루션 빌드** 를 클릭하여 스크립트를 빌드하고 변경 내용을 저장한 다음 VSTA를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-135">On the **Build** menu, click **Build Solution** to build the script and save your changes, and then close VSTA.</span></span>  
  
13. <span data-ttu-id="332ec-136">**확인** 을 클릭하여 **스크립트 변환 편집기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="332ec-136">Click **OK** to close the **Script Transformation Editor** dialog box.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="332ec-137">다음 단계</span><span class="sxs-lookup"><span data-stu-id="332ec-137">Next Steps</span></span>  
 <span data-ttu-id="332ec-138">[4 단계: 플랫 파일 대상 추가] (lesson-4-4-adding-a-flat-file-destination.md</span><span class="sxs-lookup"><span data-stu-id="332ec-138">[Step 4: Adding a Flat File Destination](lesson-4-4-adding-a-flat-file-destination.md</span></span>  
  
  
