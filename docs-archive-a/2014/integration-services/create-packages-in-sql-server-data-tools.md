---
title: SQL Server Data Tools에서 패키지 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 330e0271421dc620f7c4fad9c6944331ebe94881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649603"
---
# <a name="create-packages-in-sql-server-data-tools"></a><span data-ttu-id="a0101-102">SQL Server Data Tools에서 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="a0101-102">Create Packages in SQL Server Data Tools</span></span>
  <span data-ttu-id="a0101-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에서 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너를 사용하여 만드는 패키지는 파일 시스템에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-103">The packages that you create in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer are saved to the file system.</span></span> <span data-ttu-id="a0101-104">패키지를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 또는 패키지 저장소에 저장하려면 패키지 복사본을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-104">To save a package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store, you need to save a copy of the package.</span></span> <span data-ttu-id="a0101-105">자세한 내용은 [패키지의 복사본 저장](../../2014/integration-services/save-a-copy-of-a-package.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0101-105">For more information, see [Save a Copy of a Package](../../2014/integration-services/save-a-copy-of-a-package.md).</span></span>  
  
 <span data-ttu-id="a0101-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 다음 방법 중 하나를 사용하여 새 패키지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can create a new package by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="a0101-107">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에 포함된 패키지 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-107">Use the package template that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] includes.</span></span>  
  
-   <span data-ttu-id="a0101-108">사용자 지정 템플릿 사용</span><span class="sxs-lookup"><span data-stu-id="a0101-108">Use a custom template</span></span>  
  
     <span data-ttu-id="a0101-109">새 패키지를 만드는 데 사용자 지정 패키지를 템플릿으로 사용하려면 해당 패키지를 DataTransformationItems 폴더로 복사하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-109">To use custom packages as templates for creating new packages, you simply copy them to the DataTransformationItems folder.</span></span> <span data-ttu-id="a0101-110">기본적으로 이 폴더는 C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-110">By default, this folder is in C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.</span></span>  
  
-   <span data-ttu-id="a0101-111">기존 패키지를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-111">Copy an existing package.</span></span>  
  
     <span data-ttu-id="a0101-112">다시 사용하려는 기능이 기존 패키지에 있는 경우 이러한 패키지의 개체를 복사하여 붙여넣으면 새 패키지에서 제어 흐름 및 데이터 흐름을 훨씬 빠르게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-112">If existing packages include functionality that you want to reuse, you can build the control flow and data flows in the new package more quickly by copying and pasting objects from other packages.</span></span> <span data-ttu-id="a0101-113">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에서 복사 및 붙여넣기를 사용하는 방법은 [패키지 개체 다시 사용](reuse-of-package-objects.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0101-113">For more information about using copy and paste in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, see [Reuse of Package Objects](reuse-of-package-objects.md).</span></span>  
  
     <span data-ttu-id="a0101-114">기존 패키지를 복사하거나 사용자 지정 패키지를 템플릿으로 사용하여 새 패키지를 만드는 경우 기존 패키지의 이름과 GUID도 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-114">If you create a new package by copying an existing package or by using a custom package as a template, the name and the GUID of the existing package are copied as well.</span></span> <span data-ttu-id="a0101-115">새 패키지와 복사한 원본 패키지를 구분하려면 새 패키지의 이름 및 GUID를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-115">You should update the name and the GUID of the new package to help differentiate it from the package from which it was copied.</span></span> <span data-ttu-id="a0101-116">예를 들어 패키지에 동일한 GUID가 포함된 경우 로그 데이터가 속한 패키지를 식별하기가 훨씬 더 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-116">For example, if packages have the same GUID, it is more difficult to identify the package to which log data belongs.</span></span> <span data-ttu-id="a0101-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 속성 창을 사용하여 `ID` 속성에서 GUID를 다시 생성하고 `Name` 속성의 값을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-117">You can regenerate the GUID in the `ID` property and update the value of the `Name` property by using the Properties window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a0101-118">자세한 내용은 [패키지 속성 설정](set-package-properties.md) 및 [dtutil 유틸리티](dtutil-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0101-118">For more information, see [Set Package Properties](set-package-properties.md) and [dtutil Utility](dtutil-utility.md).</span></span>  
  
-   <span data-ttu-id="a0101-119">템플릿으로 지정한 사용자 지정 패키지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-119">Use a custom package that you have designated as a template.</span></span>  
  
-   <span data-ttu-id="a0101-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사 실행</span><span class="sxs-lookup"><span data-stu-id="a0101-120">Run the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard</span></span>  
  
     <span data-ttu-id="a0101-121">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 간단한 가져오기 또는 내보내기 수행하는 완전한 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-121">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard creates a complete package for a simple import or export.</span></span> <span data-ttu-id="a0101-122">이 마법사는 연결, 원본 및 대상을 구성하고 가져오기 또는 내보내기를 즉시 실행하는 데 필요한 데이터 변환을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-122">This wizard configures the connections, source, and destination, and adds any data transformations that are required to let you run the import or export immediately.</span></span> <span data-ttu-id="a0101-123">필요에 따라 나중에 다시 실행하기 위해 패키지를 저장하거나 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 패키지를 향상시키고 구체화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-123">You can optionally save the package to run it again later, or to refine and enhance the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="a0101-124">그러나 패키지를 저장하는 경우에는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 패키지를 변경하거나 실행하기 전에 기존 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]프로젝트에 패키지를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-124">However, if you save the package, you must add the package to an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project before you can change the package or run the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
 <span data-ttu-id="a0101-125">다음 절차에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 패키지를 만들거나 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-125">The following procedures describe how to create or delete a package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a0101-126">기본 패키지 템플릿을 사용하여 기본 패키지를 만드는 방법을 보여 주는 비디오는 [기본 패키지 만들기(SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=131023)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0101-126">For a video that demonstrates how to create a basic package using the default package template, see [Creating a Basic Package (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131023).</span></span>  
  
### <a name="to-create-a-package-in-sql-server-data-tools-using-the-package-template"></a><span data-ttu-id="a0101-127">패키지 템플릿을 사용하여 SQL Server Data Tools에서 패키지를 만들려면</span><span class="sxs-lookup"><span data-stu-id="a0101-127">To create a package in SQL Server Data Tools using the Package Template</span></span>  
  
1.  <span data-ttu-id="a0101-128">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 패키지를 만들려는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-128">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you want to create a package.</span></span>  
  
2.  <span data-ttu-id="a0101-129">솔루션 탐색기에서 **SSIS 패키지** 폴더를 마우스 오른쪽 단추로 클릭한 후 **새 SSIS 패키지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-129">In Solution Explorer, right-click the **SSIS Packages** folder, and then click **New SSIS Package**.</span></span>  
  
3.  <span data-ttu-id="a0101-130">선택적으로 제어 흐름, 데이터 흐름 태스크 및 이벤트 처리기를 패키지에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-130">Optionally, add control flow, data flow tasks, and event handlers to the package.</span></span> <span data-ttu-id="a0101-131">자세한 내용은 [제어 흐름](control-flow/control-flow.md), [데이터 흐름](data-flow/data-flow.md) 및 [Integration Services&#40;SSIS&#41; 이벤트 처리기](integration-services-ssis-event-handlers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0101-131">For more information, see [Control Flow](control-flow/control-flow.md), [Data Flow](data-flow/data-flow.md), and [Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md).</span></span>  
  
4.  <span data-ttu-id="a0101-132">**파일** 메뉴에서 **선택한 항목 저장** 을 클릭하여 새 패키지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-132">On the **File** menu, click **Save Selected Items** to save the new package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a0101-133">빈 패키지를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0101-133">You can save an empty package.</span></span>  
  
  
