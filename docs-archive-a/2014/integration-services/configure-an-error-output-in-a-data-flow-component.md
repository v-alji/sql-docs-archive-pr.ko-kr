---
title: 데이터 흐름 구성 요소에서 오류 출력 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- errors [Integration Services], data flow components
- components [Integration Services], data flow
- error outputs [Integration Services]
ms.assetid: 53d7eeea-927d-4b45-8ea9-084e65ad5390
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ebd44383e27daa465576bb056a67f6dacad87b0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741196"
---
# <a name="configure-an-error-output-in-a-data-flow-component"></a><span data-ttu-id="effcf-102">데이터 흐름 구성 요소에서 오류 출력 구성</span><span class="sxs-lookup"><span data-stu-id="effcf-102">Configure an Error Output in a Data Flow Component</span></span>
  <span data-ttu-id="effcf-103">많은 데이터 흐름 구성 요소가 오류 출력을 지원하며 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너는 구성 요소에 따라 오류 출력을 다르게 구성할 수 있는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-103">Many data flow components support error outputs, and depending on the component, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides different ways to configure an error output.</span></span> <span data-ttu-id="effcf-104">오류 출력을 구성하는 것 외에도 오류 출력의 열을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-104">In addition to configuring an error output, you can also configure the columns of an error output.</span></span> <span data-ttu-id="effcf-105">이 작업에는 구성 요소에서 추가한 **ErrorCode** 및 **ErrorColumn** 열의 구성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-105">This includes configuring the **ErrorCode** and **ErrorColumn** columns that are added by the component.</span></span>  
  
## <a name="configuring-an-error-output"></a><span data-ttu-id="effcf-106">오류 출력 구성</span><span class="sxs-lookup"><span data-stu-id="effcf-106">Configuring an Error Output</span></span>  
 <span data-ttu-id="effcf-107">다음 두 가지 옵션을 사용하여 오류 출력을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-107">To configure an error output, you have two options:</span></span>  
  
-   <span data-ttu-id="effcf-108">**오류 출력 구성** 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-108">Use the **Configure Error Output** dialog box.</span></span> <span data-ttu-id="effcf-109">이 대화 상자를 사용하면 오류 출력을 지원하는 데이터 흐름 구성 요소의 오류 출력을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-109">You can use this dialog box to configure an error output on any data flow component that supports an error output.</span></span>  
  
-   <span data-ttu-id="effcf-110">구성 요소의 편집기 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-110">Use the editor dialog box for the component.</span></span> <span data-ttu-id="effcf-111">일부 구성 요소는 해당 편집기 대화 상자에서 직접 오류 출력을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-111">Some components let you configure error outputs directly from their editor dialog box.</span></span> <span data-ttu-id="effcf-112">그러나 ADO.NET 원본, 열 가져오기 변환, OLE DB 명령 변환 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 대상의 편집기 대화 상자에서는 오류 출력을 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-112">However, you cannot configure error outputs from the editor dialog box for the ADO NET source, the Import Column transformation, the OLE DB Command transformation, or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact destination.</span></span>  
  
 <span data-ttu-id="effcf-113">다음 절차에서는 이러한 대화 상자를 사용하여 오류 출력을 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-113">The following procedures describe how to use these dialog boxes to configure error outputs.</span></span>  
  
#### <a name="to-configure-an-error-output-using-the-configure-error-output-dialog-box"></a><span data-ttu-id="effcf-114">오류 출력 구성 대화 상자를 사용하여 오류 출력을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="effcf-114">To configure an error output using the Configure Error Output dialog box</span></span>  
  
1.  <span data-ttu-id="effcf-115">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="effcf-116">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="effcf-117">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **데이터 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-117">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="effcf-118">오류의 원본에 해당하는 구성 요소에서 빨간 색 화살표로 표시된 오류 출력을 데이터 흐름의 다른 구성 요소로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-118">Drag the error output, represented by the red arrow, from the component that is the source of the errors to another component in the data flow.</span></span>  
  
5.  <span data-ttu-id="effcf-119">구성 요소 입력의 각 열에 대해 **오류 출력 구성** 대화 상자의 **오류** 및 **잘림** 열에 있는 동작을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-119">In the **Configure Error Output** dialog box, select an action in the **Error** and **Truncation** columns for each column in the component input.</span></span>  
  
6.  <span data-ttu-id="effcf-120">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-120">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
#### <a name="to-add-an-error-output-using-the-editor-dialog-box-for-the-component"></a><span data-ttu-id="effcf-121">구성 요소의 편집기 대화 상자를 사용하여 오류 출력을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="effcf-121">To add an error output using the editor dialog box for the component</span></span>  
  
1.  <span data-ttu-id="effcf-122">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-122">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="effcf-123">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-123">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="effcf-124">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **데이터 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-124">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="effcf-125">오류 출력을 구성할 데이터 흐름 구성 요소를 두 번 클릭한 다음 구성 요소에 따라 다음 단계 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-125">Double-click the data flow components in which you want to configure an error output and, depending on the component, do one of the following steps:</span></span>  
  
    -   <span data-ttu-id="effcf-126">**오류 출력 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-126">Click **Configure Error Output**.</span></span>  
  
    -   <span data-ttu-id="effcf-127">**오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-127">Click **Error Output**.</span></span>  
  
5.  <span data-ttu-id="effcf-128">각 열에 대한 **오류** 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-128">Set the **Error** option for each column.</span></span>  
  
6.  <span data-ttu-id="effcf-129">각 열에 대한 **잘림** 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-129">Set the **Truncation** option for each column.</span></span>  
  
7.  <span data-ttu-id="effcf-130">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-130">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="effcf-131">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-131">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="configuring-error-output-columns"></a><span data-ttu-id="effcf-132">오류 출력 열 구성</span><span class="sxs-lookup"><span data-stu-id="effcf-132">Configuring Error Output Columns</span></span>  
 <span data-ttu-id="effcf-133">오류 출력 열을 구성하려면 **고급 편집기** 대화 상자의 **입/출력 속성** 탭을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-133">To configure the error output columns, you have to use the **Input and Output Properties** tab of the **Advanced Editor** dialog box.</span></span>  
  
#### <a name="to-configure-error-output-columns"></a><span data-ttu-id="effcf-134">오류 출력 열을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="effcf-134">To configure error output columns</span></span>  
  
1.  <span data-ttu-id="effcf-135">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-135">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="effcf-136">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-136">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="effcf-137">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **데이터 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-137">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="effcf-138">구성하려는 오류 출력 열이 있는 구성 요소를 마우스 오른쪽 단추로 클릭하고 **고급 편집기 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-138">Right-click the component whose error output columns you want to configure and click **Show Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="effcf-139">**입/출력 속성** 탭을 클릭하고 **\<component name> 오류 출력**을 확장한 다음, **출력 열**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-139">Click the **Input and Output Properties** tab and expand **\<component name> Error Output** and then expand **Output Columns**.</span></span>  
  
6.  <span data-ttu-id="effcf-140">열을 클릭하고 속성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-140">Click a column and update its properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="effcf-141">열 목록은 구성 요소 입력 내의 열, 이전 오류 출력에서 추가한 **ErrorCode** 및 **ErrorColumn** 열, 현재 구성 요소에서 추가한 **ErrorCode** 및 **ErrorColumn** 열을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-141">The list of columns includes the columns in the component input, the **ErrorCode** and **ErrorColumn** columns added by previous error outputs, and the **ErrorCode** and **ErrorColumn** columns added by this component.</span></span>  
  
7.  <span data-ttu-id="effcf-142">**확인.**</span><span class="sxs-lookup"><span data-stu-id="effcf-142">Click **OK.**</span></span>  
  
8.  <span data-ttu-id="effcf-143">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="effcf-143">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effcf-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="effcf-144">See Also</span></span>  
 [<span data-ttu-id="effcf-145">데이터 오류 처리</span><span class="sxs-lookup"><span data-stu-id="effcf-145">Error Handling in Data</span></span>](data-flow/error-handling-in-data.md)  
  
  
