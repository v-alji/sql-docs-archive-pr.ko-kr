---
title: Foreach 루프 컨테이너 구성 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Foreach Loop containers
- containers [Integration Services], Foreach Loop
ms.assetid: 519c6f96-5e1f-47d2-b96a-d49946948c25
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 85fb399f51e22e091fac9b1d8d332b9a12e7d77e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647165"
---
# <a name="configure-a-foreach-loop-container"></a><span data-ttu-id="822b0-102">Foreach 루프 컨테이너 구성</span><span class="sxs-lookup"><span data-stu-id="822b0-102">Configure a Foreach Loop Container</span></span>
  <span data-ttu-id="822b0-103">이 절차에서는 열거자 및 컨테이너 수준의 속성 식을 비롯한 Foreach 루프 컨테이너를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-103">This procedure describes how to configure a Foreach Loop container, including property expressions at the enumerator and container levels.</span></span>  
  
### <a name="to-configure-the-foreach-loop-container"></a><span data-ttu-id="822b0-104">Foreach 루프 컨테이너를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="822b0-104">To configure the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="822b0-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="822b0-106">**제어 흐름** 탭을 클릭하고 Foreach 루프를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-106">Click the **Control Flow** tab and double-click the Foreach Loop.</span></span>  
  
3.  <span data-ttu-id="822b0-107">**Foreach 루프 편집기** 대화 상자에서 **일반** 을 클릭하고 선택적으로 Foreach 루프의 이름과 설명을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-107">In the **Foreach Loop Editor** dialog box, click **General** and, optionally, modify the name and description of the Foreach Loop.</span></span>  
  
4.  <span data-ttu-id="822b0-108">**컬렉션** 을 클릭하고 **Enumerator** 목록에서 열거자 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-108">Click **Collection** and select an enumerator type from the **Enumerator** list.</span></span>  
  
5.  <span data-ttu-id="822b0-109">열거자를 지정하고 열거자 옵션을 다음과 같이 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-109">Specify an enumerator and set enumerator options as follows:</span></span>  
  
    -   <span data-ttu-id="822b0-110">Foreach File 열거자를 사용하려면 열거할 파일이 들어 있는 폴더를 제공하고, 파일 이름 및 유형에 대한 필터를 지정하고, 정규화된 파일 이름을 반환할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-110">To usethe Foreach File enumerator, provide the folder that contains the files to enumerate, specify a filter for the file name and type, and specify whether the fully qualified file name should be returned.</span></span> <span data-ttu-id="822b0-111">또한 하위 폴더의 파일에 대해서도 동일 작업을 반복할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-111">Also, indicate whether to recurse through subfolders for more files.</span></span>  
  
    -   <span data-ttu-id="822b0-112">Foreach Item 열거자를 사용하려면 **열**을 클릭하고 **For Each Item 열** 대화 상자에서 **추가** 를 클릭하여 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-112">To use the Foreach Item enumerator, click **Columns**, and, in the **For Each Item Columns** dialog box, click **Add** to add columns.</span></span> <span data-ttu-id="822b0-113">**데이터 형식** 목록에서 각 열에 대한 데이터 형식을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-113">Select a data type in the **Data Type** list for each column, and click **OK**.</span></span>  
  
         <span data-ttu-id="822b0-114">열에 값을 입력하거나 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-114">Type values in the columns or select values from lists.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="822b0-115">새 행을 추가하려면 입력한 셀 바깥의 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-115">To add a new row, click anywhere outside the cell in which you typed.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="822b0-116">값이 열 데이터 형식과 호환되지 않으면 텍스트가 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-116">If a value is not compatible with the column data type, the text is highlighted.</span></span>  
  
    -   <span data-ttu-id="822b0-117">Foreach ADO 열거자를 사용하려면 기존 변수를 선택하거나 **ADO 개체 원본 변수** 목록에서 **새 변수** 를 클릭하여 열거할 ADO 개체의 이름이 들어 있는 변수를 지정하고 열거 모드 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-117">To use the Foreach ADO enumerator, select an existing variable or click **New variable** in the **ADO object source variable** list to specify the variable that contains the name of the ADO object to enumerate, and select an enumeration mode option.</span></span>  
  
         <span data-ttu-id="822b0-118">새 변수를 만드는 경우에는 **변수 추가** 대화 상자에서 변수 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-118">If creating a new variable, set the variable properties in the **Add Variable** dialog box.</span></span>  
  
    -   <span data-ttu-id="822b0-119">Foreach ADO.NET 스키마 행 집합 열거자를 사용하려면 기존 ADO.NET 연결을 선택하거나 **연결** 목록에서 **새 연결** 을 클릭한 후 스키마를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-119">To use the Foreach ADO.NET Schema Rowset enumerator, select an existing ADO.NET connection or click **New connection** in the **Connection** list, and then select a schema.</span></span>  
  
         <span data-ttu-id="822b0-120">필요에 따라 **제한 설정** 을 클릭하여 스키마 제한을 선택하고, 제한 값이 있는 변수를 선택하거나 제한 값을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-120">Optionally, click **Set Restrictions** and select schema restrictions, select the variable that contains the restriction value or type the restriction value, and click **OK**.</span></span>  
  
    -   <span data-ttu-id="822b0-121">Foreach From Variable 열거자를 사용하려면 **변수** 목록에서 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-121">To use the Foreach From Variable enumerator, select a variable in the **Variable** list.</span></span>  
  
    -   <span data-ttu-id="822b0-122">Foreach NodeList 열거자를 사용하려면 DocumentSourceType을 클릭하고 목록에서 원본 유형을 선택한 다음 DocumentSource를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-122">To use the Foreach NodeList enumerator, click DocumentSourceType and select the source type from the list, and then click DocumentSource.</span></span> <span data-ttu-id="822b0-123">DocumentSourceType에 대해 선택한 값에 따라 목록에서 변수 또는 파일 연결을 선택하거나, 새 변수 또는 파일 연결을 만들거나, **문서 원본 편집기**에서 XML 원본을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-123">Depending on the value selected for DocumentSourceType, select a variable or a file connection from the list, create a new variable or file connection, or type the XML source in the **Document Source Editor**.</span></span>  
  
         <span data-ttu-id="822b0-124">그런 다음 EnumerationType을 클릭하고 목록에서 열거형 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-124">Next, click EnumerationType and select an enumeration type from the list.</span></span> <span data-ttu-id="822b0-125">EnumerationType이 **Navigator, Node 또는 NodeText**이면 OuterXPathStringSourceType을 클릭하고 원본 유형을 선택한 다음 OuterXPathString을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-125">If EnumerationType is **Navigator, Node, or NodeText**, click OuterXPathStringSourceType and select the source type, and then click OuterXPathString.</span></span> <span data-ttu-id="822b0-126">OuterXPathStringSourceType에 대해 설정된 값에 따라 목록에서 변수 또는 파일 연결을 선택하거나, 새 변수 또는 파일 연결을 만들거나, 외부 XPath(XML Path Language) 식에 대한 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-126">Depending on the value set for OuterXPathStringSourceType, select a variable or a file connection from the list, create a new variable or file connection, or type the string for the outer XML Path Language (XPath) expression.</span></span>  
  
         <span data-ttu-id="822b0-127">EnumerationType이 **ElementCollection**이면 위에서 설명한 대로 OuterXPathStringSourceType 및 OuterXPathString을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-127">If EnumerationType is **ElementCollection**,set OuterXPathStringSourceType and OuterXPathString as described above.</span></span> <span data-ttu-id="822b0-128">그런 다음 InnerElementType을 클릭하고 내부 요소에 대한 열거형 형식을 선택한 다음 InnerXPathStringSourceType을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-128">Then, click InnerElementType and select an enumeration type for the inner elements, and then click InnerXPathStringSourceType.</span></span> <span data-ttu-id="822b0-129">InnerXPathStringSourceType에 대해 설정된 값에 따라 변수 또는 파일 연결을 선택하거나, 새 변수 또는 파일 연결을 만들거나, 내부 XPath 식에 대한 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-129">Depending on the value set for InnerXPathStringSourceType, select a variable or a file connection, create a new variable or file connection, or type the string for the inner XPath expression.</span></span>  
  
    -   <span data-ttu-id="822b0-130">Foreach SMO 열거자를 사용하려면 기존 ADO.NET 연결을 선택하거나 **연결** 목록에서 **새 연결** 을 클릭한 후 사용할 문자열을 입력하거나 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-130">To use the Foreach SMO enumerator, select an existing ADO.NET connection or click **New connection** in the **Connection** list, and then either type the string to use or click **Browse**.</span></span> <span data-ttu-id="822b0-131">**찾아보기**를 클릭한 경우 **SMO 열거 선택** 대화 상자에서 열거할 개체 유형과 열거 유형을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-131">If you click **Browse**, in the **Select SMO Enumeration** dialog box, select the object type to enumerate and the enumeration type, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="822b0-132">선택적으로 **컬렉션** 페이지의 **식** 텍스트 상자에서 찾아보기 단추 **(...)** 를 클릭하여 속성 값을 업데이트하는 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-132">Optionally, click the browse button **(...)** in the **Expressions** text box on the **Collection** page to create expressions that update property values.</span></span> <span data-ttu-id="822b0-133">자세한 내용은 [속성 식 추가 또는 변경](expressions/add-or-change-a-property-expression.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="822b0-133">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="822b0-134">**Property** 목록에 표시되는 속성은 열거자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-134">The properties listed in the **Property** list varies by enumerator.</span></span>  
  
7.  <span data-ttu-id="822b0-135">선택적으로 **변수 매핑** 을 클릭하여 컬렉션 값에 개체 속성을 매핑한 후 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-135">Optionally, click **Variable Mappings** to map object properties to the collection value, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="822b0-136">**변수** 목록에서 변수를 선택하거나 **\<New Variable>** 를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-136">In the **Variables** list, select a variable or click **\<New Variable>** to create a new variable.</span></span>  
  
    2.  <span data-ttu-id="822b0-137">새 변수를 추가하는 경우에는 **변수 추가** 대화 상자에서 변수 속성을 설정하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-137">If you add a new variable, set the variable properties in the **Add Variable** dialog box and click **OK**.</span></span>  
  
    3.  <span data-ttu-id="822b0-138">For Each Item 열거자를 사용하는 경우 **인덱스** 목록에서 인덱스 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-138">If you use the For Each Item enumerator, you can update the index value in the **Index** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="822b0-139">인덱스 값은 항목에서 변수로 매핑될 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-139">The index value indicates which column in the item to map to the variable.</span></span> <span data-ttu-id="822b0-140">For Each Item 열거자에서만 0이 아닌 인덱스 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-140">Only the For Each Item enumerator can use an index value other than 0.</span></span>  
  
8.  <span data-ttu-id="822b0-141">선택적으로 **식** 페이지에서 **Expressions** 를 클릭하고 Foreach 루프 컨테이너의 속성에 대한 속성 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-141">Optionally, click **Expressions** and, on the **Expressions** page, create property expressions for the properties of the Foreach Loop container.</span></span> <span data-ttu-id="822b0-142">자세한 내용은 [속성 식 추가 또는 변경](expressions/add-or-change-a-property-expression.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="822b0-142">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
9. <span data-ttu-id="822b0-143">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="822b0-143">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="822b0-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="822b0-144">See Also</span></span>  
 [<span data-ttu-id="822b0-145">Foreach 루프 컨테이너</span><span class="sxs-lookup"><span data-stu-id="822b0-145">Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
