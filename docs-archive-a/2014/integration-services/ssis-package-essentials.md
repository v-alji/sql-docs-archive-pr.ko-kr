---
title: SSIS 패키지 Essentials | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package requirements
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c58ddc13b5c149b84fa550f312782b02786d062
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734316"
---
# <a name="ssis-package-essentials"></a><span data-ttu-id="484ae-102">SSIS 패키지 주요 사항</span><span class="sxs-lookup"><span data-stu-id="484ae-102">SSIS Package Essentials</span></span>
  <span data-ttu-id="484ae-103">패키지는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 기능을 구현하여 데이터를 추출, 변환 및 로드하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="484ae-103">A package is the object that implements [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] functionality to extract, transform, and load data.</span></span> <span data-ttu-id="484ae-104">패키지는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 의 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]디자이너를 사용하여 만들거나</span><span class="sxs-lookup"><span data-stu-id="484ae-104">You create a package by using the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="484ae-105">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사나 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 연결 프로젝트 마법사를 사용하여 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="484ae-105">You can also create a package by running the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard or the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Connections Project Wizard.</span></span> <span data-ttu-id="484ae-106">자세한 내용은 SSIS 디자이너 및 [프로젝트 가져오기 마법사](../../2014/integration-services/import-project-wizard.md)의 [SQL Server Data Tools에서 패키지를 만듭니다](create-packages-in-sql-server-data-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="484ae-106">For more information, [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) in SSIS Designer and [Import Project Wizard](../../2014/integration-services/import-project-wizard.md).</span></span>  
  
 <span data-ttu-id="484ae-107">기본 패키지에는 다음 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="484ae-107">A basic package includes the following elements:</span></span>  
  
 <span data-ttu-id="484ae-108">**제어 흐름 요소**</span><span class="sxs-lookup"><span data-stu-id="484ae-108">**Control flow elements**</span></span>  
 <span data-ttu-id="484ae-109">이 필수 요소는 다양한 기능을 수행하고 구조를 제공하며 요소의 실행 순서를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="484ae-109">These required elements perform various functions, provide structure, and control the order in which elements run.</span></span> <span data-ttu-id="484ae-110">주 제어 흐름 요소는 태스크, 컨테이너 및 선행 제약 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="484ae-110">The main control flow elements are tasks, containers, and precedence constraints.</span></span> <span data-ttu-id="484ae-111">패키지에는 적어도 하나의 제어 흐름 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="484ae-111">There must be at least one control flow element in a package.</span></span>  
  
 <span data-ttu-id="484ae-112">자세한 내용은 [Control Flow](control-flow/control-flow.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="484ae-112">For more information, see [Control Flow](control-flow/control-flow.md).</span></span>  
  
 <span data-ttu-id="484ae-113">**데이터 흐름 요소**</span><span class="sxs-lookup"><span data-stu-id="484ae-113">**Data flow elements**</span></span>  
 <span data-ttu-id="484ae-114">이 선택적 요소는 데이터를 추출하고 수정하며 데이터 원본으로 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="484ae-114">These optional elements extract data, modify data, and load data into data sources.</span></span> <span data-ttu-id="484ae-115">주 데이터 흐름 요소는 원본, 변환 및 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="484ae-115">The main data flow elements are sources, transformations, and destinations.</span></span> <span data-ttu-id="484ae-116">패키지의 데이터 흐름 요소가 아니어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="484ae-116">There does not have to be any data flow elements in package.</span></span>  
  
 <span data-ttu-id="484ae-117">자세한 내용은 [Data Flow](data-flow/data-flow.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="484ae-117">For more information, see [Data Flow](data-flow/data-flow.md).</span></span>  
  
 <span data-ttu-id="484ae-118">기본 패키지를 만드는 방법에 대 한 예는 [1 단원: 프로젝트 및 기본 패키지 만들기](lesson-1-create-a-project-and-basic-package-with-ssis.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="484ae-118">For an example of how to create a basic package, see [Lesson 1: Creating the Project and Basic Package](lesson-1-create-a-project-and-basic-package-with-ssis.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="484ae-119">관련 작업</span><span class="sxs-lookup"><span data-stu-id="484ae-119">Related Tasks</span></span>  
  
-   [<span data-ttu-id="484ae-120">SQL Server Data Tools에서 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="484ae-120">Create Packages in SQL Server Data Tools</span></span>](create-packages-in-sql-server-data-tools.md)  
  
-   [<span data-ttu-id="484ae-121">제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="484ae-121">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [<span data-ttu-id="484ae-122">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="484ae-122">Set the Properties of a Task or Container</span></span>](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
-   [<span data-ttu-id="484ae-123">데이터 흐름에서 구성 요소 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="484ae-123">Add or Delete a Component in a Data Flow</span></span>](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
## <a name="related-content"></a><span data-ttu-id="484ae-124">관련 내용</span><span class="sxs-lookup"><span data-stu-id="484ae-124">Related Content</span></span>  
  
1.  <span data-ttu-id="484ae-125">MSDN.Microsoft.com의 비디오, [기본 패키지 만들기(SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=131023)</span><span class="sxs-lookup"><span data-stu-id="484ae-125">Video, [Creating a Basic Package (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131023), on MSDN.Microsoft.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="484ae-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="484ae-126">See Also</span></span>  
 <span data-ttu-id="484ae-127">[SSIS&#41; 패키지 Integration Services &#40;](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="484ae-127">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="484ae-128">선행 제약 조건</span><span class="sxs-lookup"><span data-stu-id="484ae-128">Precedence Constraints</span></span>](control-flow/precedence-constraints.md)  
  
  
