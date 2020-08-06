---
title: 패키지 개체 다시 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- GUID regenerating [Integration Services]
- reusing packages
- templates [Integration Services]
- copying packages
- regenerating package GUID
ms.assetid: 08f723bf-15b5-44bd-9a46-04e8781bfbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b7612cb2684bb842108068b062e54fbe9dee4327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729587"
---
# <a name="reuse-of-package-objects"></a><span data-ttu-id="b1499-102">패키지 개체 다시 사용</span><span class="sxs-lookup"><span data-stu-id="b1499-102">Reuse of Package Objects</span></span>
  <span data-ttu-id="b1499-103">다시 사용하려는 자주 사용되는 패키지 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-103">Frequently packages functionality that you want to reuse.</span></span> <span data-ttu-id="b1499-104">예를 들어 태스크 집합을 만든 경우 항목을 모두 그룹으로 다시 사용하거나 다른 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에서 만든 연결 관리자와 같은 단일 항목을 다시 사용하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-104">For example, if you created a set of tasks, you might want to reuse the items together as a group, or you might want to reuse a single item such as a connection manager that you created in a different [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
## <a name="copy-and-paste"></a><span data-ttu-id="b1499-105">복사 및 붙여넣기</span><span class="sxs-lookup"><span data-stu-id="b1499-105">Copy and Paste</span></span>  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="b1499-106">및 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너는 패키지 개체 복사 및 붙여넣기를 지원합니다. 여기에는 제어 흐름 항목, 데이터 흐름 항목 및 연결 관리자가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-106">and [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer support copying and pasting package objects, which can include control flow items, data flow items, and connection managers.</span></span> <span data-ttu-id="b1499-107">프로젝트 간 및 패키지 간에 복사하여 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-107">You can copy and paste between projects and between packages.</span></span> <span data-ttu-id="b1499-108">솔루션에 여러 개의 프로젝트가 포함된 경우 프로젝트 간에 복사할 수 있으며 프로젝트는 다른 유형일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-108">If the solution contains multiple projects you can copy between projects, and the projects can be of different types.</span></span>  
  
 <span data-ttu-id="b1499-109">솔루션에 여러 개의 패키지가 포함된 경우 해당 패키지 간에 복사하고 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-109">If a solution contains multiple packages, you can copy and paste between them.</span></span> <span data-ttu-id="b1499-110">패키지는 같은 프로젝트나 다른 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-110">The packages can be in the same or different [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects.</span></span> <span data-ttu-id="b1499-111">그러나 유효성 여부에 관계없이 패키지 개체에 다른 개체에 대한 종속성이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-111">However, package objects may have dependencies on other objects, without which they are not valid.</span></span> <span data-ttu-id="b1499-112">예를 들어 SQL 실행 태스크에는 연결 관리자를 사용하고 태스크가 작동하도록 이를 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-112">For example, an Execute SQL task uses a connection manager, which you must copy as well to make the task work.</span></span> <span data-ttu-id="b1499-113">또한 일부 패키지 개체는 패키지에 특정 개체를 포함해야 하며 이 개체가 없으면 복사한 개체를 패키지에 성공적으로 붙여 넣을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-113">Also, some package objects require that the package already contain a certain object, and without this object you cannot successfully paste the copied objects into a package.</span></span> <span data-ttu-id="b1499-114">예를 들면 데이터 흐름 태스크가 없는 패키지에 데이터 흐름을 붙여 넣을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-114">For example, you cannot paste a data flow into a package that does not have at least one Data Flow task.</span></span>  
  
 <span data-ttu-id="b1499-115">같은 패키지를 반복해서 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-115">You may find that you copy the same packages repeatedly.</span></span> <span data-ttu-id="b1499-116">복사 프로세스가 수행되지 않도록 하려면 이러한 패키지를 템플릿으로 지정하고 새 패키지를 만들 때 이러한 패키지를 템플릿으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-116">To avoid the copy process, you can designate these packages as templates and use them when you create new packages.</span></span>  
  
 <span data-ttu-id="b1499-117">패키지 개체를 복사하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]는 자동으로 새 GUID를 새 개체의 `ID` 속성에 할당하고 `Name` 속성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-117">When you copy a package object, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] automatically assigns a new GUID to the `ID` property of the new object and updates the `Name` property.</span></span>  
  
 <span data-ttu-id="b1499-118">변수는 복사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-118">You cannot copy variables.</span></span> <span data-ttu-id="b1499-119">태스크와 같은 개체에서 변수를 사용하는 경우 대상 패키지에 변수를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-119">If an object such as a task uses variables, then you must re-create the variables in the destination package.</span></span> <span data-ttu-id="b1499-120">반대로 전체 패키지를 복사하는 경우 패키지의 변수도 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1499-120">In contrast, if you copy the entire package, then the variables in the package are also copied.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b1499-121">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b1499-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b1499-122">패키지 개체 복사</span><span class="sxs-lookup"><span data-stu-id="b1499-122">Copy Package Objects</span></span>](../../2014/integration-services/copy-package-objects.md)  
  
-   [<span data-ttu-id="b1499-123">프로젝트 항목 복사</span><span class="sxs-lookup"><span data-stu-id="b1499-123">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)  
  
-   [<span data-ttu-id="b1499-124">패키지 템플릿으로 패키지 저장</span><span class="sxs-lookup"><span data-stu-id="b1499-124">Save a Package as a Package Template</span></span>](../../2014/integration-services/save-a-package-as-a-package-template.md)  
  
  
