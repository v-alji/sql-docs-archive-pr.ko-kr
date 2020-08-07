---
title: 패키지 템플릿으로 패키지 저장 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- reusing packages
- templates [Integration Services]
ms.assetid: efe66cec-3933-4f6e-8d35-fe3d300de66c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30bddb5a343e7c7aef279bc66c25be30a2cf1a12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730824"
---
# <a name="save-a-package-as-a-package-template"></a><span data-ttu-id="d3317-102">패키지 템플릿으로 패키지 저장</span><span class="sxs-lookup"><span data-stu-id="d3317-102">Save a Package as a Package Template</span></span>
  <span data-ttu-id="d3317-103">이 항목에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 새 Integration Services 패키지를 만들 때 사용자 지정 패키지를 템플릿으로 지정하고 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-103">This topic describes how to designate and use custom packages as templates when you create new Integration Services packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d3317-104">기본적으로 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서는 새 패키지를 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에 추가할 때 빈 패키지를 만드는 패키지 템플릿을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-104">By default, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] uses a package template that creates an empty package when you add a new package to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="d3317-105">이러한 기본 템플릿은 바꿀 수 없지만 새 템플릿을 추가할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-105">You cannot replace this default template, but you can add new templates.</span></span>  
  
 <span data-ttu-id="d3317-106">여러 개의 패키지를 템플릿으로 지정하여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-106">You can designate multiple packages to use as templates.</span></span> <span data-ttu-id="d3317-107">사용자 지정 패키지를 템플릿으로 구현하려면 먼저 패키지를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-107">Before you can implement custom packages as templates, you must create the packages.</span></span>  
  
 <span data-ttu-id="d3317-108">사용자 지정 패키지를 템플릿으로 사용하여 패키지를 만들면 새 패키지에 템플릿과 동일한 이름 및 GUID가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-108">When you create package using custom packages as templates, the new packages have the same name and GUID as the template.</span></span> <span data-ttu-id="d3317-109">패키지를 구분하려면 `Name` 속성 값을 업데이트하고 `ID` 속성에 대한 새 GUID를 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-109">To differentiate among packages you should update the value of the `Name` property and generate a new GUID for the `ID` property.</span></span> <span data-ttu-id="d3317-110">자세한 내용은 [SQL Server Data Tools에서 패키지 만들기](create-packages-in-sql-server-data-tools.md) 및 [패키지 속성 설정](set-package-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d3317-110">For more information, see [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) and [Set Package Properties](set-package-properties.md).</span></span>  
  
### <a name="to-designate-a-custom-package-as-a-package-template"></a><span data-ttu-id="d3317-111">사용자 지정 패키지를 패키지 템플릿으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="d3317-111">To designate a custom package as a package template</span></span>  
  
1.  <span data-ttu-id="d3317-112">파일 시스템에서 템플릿으로 사용할 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-112">In the file system, locate the package that you want to use as template.</span></span>  
  
2.  <span data-ttu-id="d3317-113">해당 패키지를 DataTransformationItems 폴더로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-113">Copy the package to the DataTransformationItems folder.</span></span> <span data-ttu-id="d3317-114">기본적으로 이 폴더는 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-114">By default this folder is in C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.</span></span>  
  
3.  <span data-ttu-id="d3317-115">템플릿으로 사용할 각 패키지에 대해 1단계와 2단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-115">Repeat steps 1 and 2 for each package that you want to use as a template.</span></span>  
  
### <a name="to-use-a-custom-package-as-a-package-template"></a><span data-ttu-id="d3317-116">사용자 지정 패키지를 패키지 템플릿으로 사용하려면</span><span class="sxs-lookup"><span data-stu-id="d3317-116">To use a custom package as a package template</span></span>  
  
1.  <span data-ttu-id="d3317-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 패키지를 만들려는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you want to create a package.</span></span>  
  
2.  <span data-ttu-id="d3317-118">솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가**를 가리킨 다음 **새 항목**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-118">In Solution Explorer, right-click the project, point to **Add**, and then click **New Item**.</span></span>  
  
3.  <span data-ttu-id="d3317-119">**새 항목 추가 - \<project name>** 대화 상자에서 템플릿으로 사용할 패키지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-119">In the **Add New Item -\<project name>** dialog box, click the package that you want to use as a template.</span></span>  
  
     <span data-ttu-id="d3317-120">템플릿 목록에 새 SSIS 패키지라는 기본 패키지 템플릿이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-120">The list of templates includes the default package template named New SSIS Package.</span></span> <span data-ttu-id="d3317-121">패키지 아이콘을 통해 패키지 템플릿으로 사용할 수 있는 템플릿을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-121">The package icon identifies templates that can be used as package templates.</span></span>  
  
4.  <span data-ttu-id="d3317-122">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3317-122">Click **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3317-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3317-123">See Also</span></span>  
 <span data-ttu-id="d3317-124">[SQL Server Data Tools에서 패키지 만들기](create-packages-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d3317-124">[Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="d3317-125">Integration Services&#40;SSIS&#41; 패키지</span><span class="sxs-lookup"><span data-stu-id="d3317-125">Integration Services &#40;SSIS&#41; Packages</span></span>](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
