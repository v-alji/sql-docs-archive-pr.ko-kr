---
title: 데이터 흐름 구성 요소의 속성 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], properties
ms.assetid: 73000ef6-52a2-4dec-8320-0e79acf0c2c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1fd045ba076eed2d65d801015b881a477976f5d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659583"
---
# <a name="set-the-properties-of-a-data-flow-component"></a><span data-ttu-id="d48d2-102">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="d48d2-102">Set the Properties of a Data Flow Component</span></span>
  <span data-ttu-id="d48d2-103">원본, 대상 및 변환을 비롯한 데이터 흐름 구성 요소 속성을 설정하려면 다음 기능 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-103">To set the properties of data flow components, which include sources, destinations, and transformations, use one of the following features:</span></span>  
  
-   <span data-ttu-id="d48d2-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 가 제공하는 구성 요소 편집기.</span><span class="sxs-lookup"><span data-stu-id="d48d2-104">The component editors that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="d48d2-105">이러한 편집기에는 각 데이터 흐름 구성 요소의 사용자 지정 속성만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-105">These editors include only the custom properties of each data flow component.</span></span>  
  
-   <span data-ttu-id="d48d2-106">**속성** 창에는 각 요소에 대한 구성 요소 수준의 사용자 지정 속성뿐만 아니라 모든 데이터 흐름 요소에 공통적인 속성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-106">The **Properties** window lists the component-level custom properties of each element, as well as the properties common to all data flow elements.</span></span>  
  
-   <span data-ttu-id="d48d2-107">**고급 편집기** 대화 상자에서는 각 구성 요소의 사용자 지정 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-107">The **Advanced Editor** dialog box provides access to custom properties for each component.</span></span> <span data-ttu-id="d48d2-108">또한 **고급 편집기** 대화 상자에서는 모든 데이터 흐름 구성 요소에 공통적인 속성(입력, 출력, 오류 출력, 열 및 외부 열의 속성)에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-108">The **Advanced Editor** dialog box also provides access to the properties common to all data flow components-the properties of inputs, outputs, error outputs, columns, and external columns.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-a-component-editor"></a><span data-ttu-id="d48d2-109">구성 요소 편집기를 사용하여 데이터 흐름 구성 요소의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d48d2-109">To set the properties of a data flow component by using a component editor</span></span>  
  
1.  <span data-ttu-id="d48d2-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="d48d2-111">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="d48d2-112">**제어 흐름** 탭을 클릭한 후 보고 수정하려는 구성 요소 속성이 들어 있는 데이터 흐름이 포함된 데이터 흐름 태스크를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-112">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow with the component whose properties you want to view and modify.</span></span>  
  
4.  <span data-ttu-id="d48d2-113">데이터 흐름 구성 요소를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-113">Double-click the data flow component.</span></span>  
  
5.  <span data-ttu-id="d48d2-114">구성 요소 편집기에서 속성 값을 보거나 수정한 후 편집기를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-114">In the component editor, view or modify the property values, and then close the editor.</span></span>  
  
6.  <span data-ttu-id="d48d2-115">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-115">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-properties-window"></a><span data-ttu-id="d48d2-116">속성 창을 사용하여 데이터 흐름 구성 요소의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d48d2-116">To set the properties of a data flow component by using the Properties window</span></span>  
  
1.  <span data-ttu-id="d48d2-117">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="d48d2-118">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-118">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="d48d2-119">**제어 흐름** 탭을 클릭한 후 보고 수정하려는 구성 요소 속성이 들어 있는 데이터 흐름 태스크를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-119">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the component whose properties you want to view and modify.</span></span>  
  
4.  <span data-ttu-id="d48d2-120">데이터 흐름 구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-120">Right-click the data flow component, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="d48d2-121">속성 값을 보거나 수정한 후 **속성** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-121">View or modify the property values, and then close the **Properties** window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d48d2-122">여러 속성이 읽기 전용이며 수정될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-122">Many properties are read-only, and cannot be modified.</span></span>  
  
6.  <span data-ttu-id="d48d2-123">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-123">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-advanced-editor"></a><span data-ttu-id="d48d2-124">고급 편집기를 사용하여 데이터 흐름 구성 요소의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d48d2-124">To set the properties of a data flow component by using the Advanced Editor</span></span>  
  
1.  <span data-ttu-id="d48d2-125">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-125">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="d48d2-126">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-126">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="d48d2-127">**제어 흐름** 탭을 클릭한 후 보거나 수정하려는 구성 요소가 들어 있는 데이터 흐름 태스크를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-127">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the component you want to view or modify.</span></span>  
  
4.  <span data-ttu-id="d48d2-128">데이터 흐름 디자이너에서 데이터 흐름 구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **고급 편집기 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-128">In the data flow designer, right-click the data flow component, and then click **Show Advanced Editor**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d48d2-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 여러 입력을 지원하는 데이터 흐름 구성 요소에서는 **고급 편집기**를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-129">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data flow components that support multiple inputs cannot use the **Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="d48d2-130">**고급 편집기** 대화 상자에서 다음 단계 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-130">In the **Advanced Editor** dialog box, do any of the following steps:</span></span>  
  
    -   <span data-ttu-id="d48d2-131">구성 요소에서 사용하는 연결을 보고 지정하려면 **연결 관리자** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-131">To view and specify the connection that the component uses, click the **Connection Managers** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d48d2-132">**연결 관리자** 탭은 연결 관리자를 사용하여 파일 및 데이터베이스와 같은 데이터 원본에 연결하는 데이터 흐름 구성 요소에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-132">The **Connection Managers** tab is available only to data flow components that use connection managers to connect to data sources such as files and databases</span></span>  
  
    -   <span data-ttu-id="d48d2-133">구성 요소 수준의 속성을 보고 수정하려면 **구성 요소 속성** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-133">To view and modify component-level properties, click the **Component Properties** tab.</span></span>  
  
    -   <span data-ttu-id="d48d2-134">외부 열과 사용 가능한 출력 간의 매핑을 보고 수정하려면 **열 매핑** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-134">To view and modify mappings between external columns and the available output, click the **Column Mappings** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d48d2-135">**열 매핑** 탭은 원본 또는 대상을 보거나 편집하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-135">The **Column Mappings** tab is available only when viewing or editing sources or destinations.</span></span>  
  
    -   <span data-ttu-id="d48d2-136">사용 가능한 입력 열 목록을 보고 출력 열의 이름을 업데이트하려면 **입력 열** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-136">To view a list of the available input columns and to update the names of output columns, click the **Input Columns** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d48d2-137">입력 열 탭은 변환 또는 대상에서 작업할 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-137">The Input Columns tab is available only when working with transformations or destinations.</span></span> <span data-ttu-id="d48d2-138">자세한 내용은 [Integration Services Transformations](transformations/integration-services-transformations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d48d2-138">For more information, see [Integration Services Transformations](transformations/integration-services-transformations.md).</span></span>  
  
    -   <span data-ttu-id="d48d2-139">입력, 출력 및 오류 출력의 속성과 여기에 포함된 열의 속성을 보고 수정하려면 **입/출력 속성** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-139">To view and modify the properties of inputs, outputs, and error outputs, and the properties of the columns they contain, click the **Input and Output Properties** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d48d2-140">원본에는 입력이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-140">Sources have no inputs.</span></span> <span data-ttu-id="d48d2-141">대상에는 선택적 오류 출력 외에는 출력이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-141">Destinations have no outputs, except for an optional error output.</span></span>  
  
6.  <span data-ttu-id="d48d2-142">속성 값을 보거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-142">View or modify the property values.</span></span>  
  
7.  <span data-ttu-id="d48d2-143">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-143">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="d48d2-144">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d48d2-144">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d48d2-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d48d2-145">See Also</span></span>  
 [<span data-ttu-id="d48d2-146">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="d48d2-146">Integration Services Transformations</span></span>](transformations/integration-services-transformations.md)  
  
  
