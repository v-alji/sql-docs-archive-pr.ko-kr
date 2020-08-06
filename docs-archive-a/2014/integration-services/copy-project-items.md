---
title: 프로젝트 항목 복사 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], copying
- packages [Integration Services], copying
- copying data source views
- copying data sources
- copying packages
- data source views [Integration Services], copying
ms.assetid: 1606c54d-20f9-49f3-a4ef-caad83a772aa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3456209c467c3b8474e130181d02304911098d2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651832"
---
# <a name="copy-project-items"></a><span data-ttu-id="70933-102">프로젝트 항목 복사</span><span class="sxs-lookup"><span data-stu-id="70933-102">Copy Project Items</span></span>
  <span data-ttu-id="70933-103">이 항목에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트 내 또는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트 간에 개체를 복사하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="70933-103">This topic describes how to copy objects within an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or between [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects.</span></span> <span data-ttu-id="70933-104">또한 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 프로젝트, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 및 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]의 다른 유형 간에 개체를 복사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70933-104">You can also copy objects between the other types of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] projects, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="70933-105">프로젝트 간에 복사하려면 프로젝트가 같은 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 솔루션의 일부여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70933-105">To copy between projects, the project must be part of the same [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] solution.</span></span> <span data-ttu-id="70933-106">자세한 내용은 [Integration Services&#40;SSIS&#41; 프로젝트](integration-services-ssis-projects-and-solutions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70933-106">For more information, see [Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md).</span></span>  
  
### <a name="to-copy-project-level-items"></a><span data-ttu-id="70933-107">프로젝트 수준 항목을 복사하려면</span><span class="sxs-lookup"><span data-stu-id="70933-107">To copy project level items</span></span>  
  
1.  <span data-ttu-id="70933-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 작업할 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트 또는 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="70933-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or solution that you want to work with.</span></span>  
  
2.  <span data-ttu-id="70933-109">복사할 프로젝트 및 항목 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="70933-109">Expand the project and item folder to copy from.</span></span>  
  
3.  <span data-ttu-id="70933-110">항목을 마우스 오른쪽 단추로 클릭하고 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70933-110">Right-click the item and click **Copy**.</span></span>  
  
4.  <span data-ttu-id="70933-111">복사할 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 마우스 오른쪽 단추로 클릭하고 **붙여넣기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="70933-111">Right-click the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to copy to and click **Paste**.</span></span>  
  
     <span data-ttu-id="70933-112">항목은 올바른 폴더에 자동으로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="70933-112">The items are automatically copied to the correct folder.</span></span> <span data-ttu-id="70933-113">패키지가 아닌 항목을 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에 복사하려는 경우 항목이 **기타** 폴더로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="70933-113">If you copy items to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that are not packages, the items are copied to the **Miscellaneous** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70933-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70933-114">See Also</span></span>  
 <span data-ttu-id="70933-115">[SSIS&#41; 패키지 Integration Services &#40;](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="70933-115">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="70933-116">패키지 개체 복사</span><span class="sxs-lookup"><span data-stu-id="70933-116">Copy Package Objects</span></span>](../../2014/integration-services/copy-package-objects.md)  
  
  
