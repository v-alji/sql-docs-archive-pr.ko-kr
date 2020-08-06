---
title: 개발 단계 중 Analysis Services 프로젝트 및 데이터베이스 작업 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762ea6f33a94f65e7dd6895cd038d4a52d40d43e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651346"
---
# <a name="working-with-analysis-services-projects-and-databases-during-the-development-phase"></a><span data-ttu-id="81e16-102">개발 단계 중의 Analysis Services 프로젝트 및 데이터베이스 작업</span><span class="sxs-lookup"><span data-stu-id="81e16-102">Working with Analysis Services Projects and Databases During the Development Phase</span></span>
  <span data-ttu-id="81e16-103">프로젝트 모드나 온라인 모드로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 데이터베이스를 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-103">You can develop an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in either project mode or online mode.</span></span>  
  
## <a name="single-developer"></a><span data-ttu-id="81e16-104">단일 개발자</span><span class="sxs-lookup"><span data-stu-id="81e16-104">Single Developer</span></span>  
 <span data-ttu-id="81e16-105">단일 개발자가 전체 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 및 모든 요소 개체를 개발하는 경우 이 개발자는 비즈니스 인텔리전스 솔루션의 수명 주기 동안 언제든지 프로젝트 모드나 온라인 모드로 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-105">When only a single developer is developing the entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and all of its constituent objects, the developer can use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in either project mode or online mode at any time during the lifecycle of the business intelligence solution.</span></span> <span data-ttu-id="81e16-106">단일 개발자의 경우 모드 선택은 별로 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-106">In the case of a single developer, the choice of modes is not particularly critical.</span></span> <span data-ttu-id="81e16-107">원본 제어 시스템과 통합된 상태로 오프라인 프로젝트 파일을 유지 관리하면 보관 및 롤백과 같은 많은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-107">The maintenance of an offline project file integrated with a source control system has many benefits, such as archiving and rollback.</span></span> <span data-ttu-id="81e16-108">단일 개발자의 경우에는 다른 개발자와 변경 작업에 관해 통신할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-108">However, with a single developer you will not have the problem of communicating changes with another developer.</span></span>  
  
## <a name="multiple-developers"></a><span data-ttu-id="81e16-109">다중 개발자</span><span class="sxs-lookup"><span data-stu-id="81e16-109">Multiple Developers</span></span>  
 <span data-ttu-id="81e16-110">다중 개발자가 비즈니스 인텔리전스 솔루션에서 작업할 때 개발자가 원본 제어를 포함하는 프로젝트 모드로 작업하지 않으면 항상은 아니지만 대부분의 경우에서 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-110">When multiple developers are working on a business intelligence solution, problems will arise if the developers do not work in project mode with source control under most, if not all circumstances.</span></span> <span data-ttu-id="81e16-111">원본 제어는 두 명의 개발자가 동시에 같은 개체를 변경하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-111">Source control ensures that two developers are not making changes to the same object at the same time.</span></span>  
  
 <span data-ttu-id="81e16-112">예를 들어 한 개발자가 프로젝트 모드로 작업 중이며 선택한 개체를 변경한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-112">For example, suppose a developer is working in project mode and making changes to selected objects.</span></span> <span data-ttu-id="81e16-113">또한 이 개발자가 변경하는 동안 다른 개발자가 온라인 모드로 배포된 데이터베이스를 변경한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-113">While the developer is making these changes, suppose that another developer makes a change to the deployed database in online mode.</span></span> <span data-ttu-id="81e16-114">첫 번째 개발자가 수정된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 배포하려고 하면 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-114">A problem will arise when the first developer attempts to deploy his or her modified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="81e16-115">즉, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 배포된 데이터베이스 내의 개체가 변경되었음을 감지하고 개발자에게 전체 데이터베이스를 덮어써서 두 번째 개발자의 변경 내용을 덮어쓸 것인지 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-115">Namely, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] will detect that objects have changed within the deployed database and prompt the developer to overwrite the entire database, overwriting the changes of the second developer.</span></span> <span data-ttu-id="81e16-116">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 인스턴스와 덮어쓸 프로젝트 개체 간 변경 내용을 해결할 방법이 없으므로 사실상 첫 번째 개발자는 변경 내용을 모두 삭제하고 현재 버전의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 기반으로 새 프로젝트에서 다시 시작하는 수밖에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81e16-116">Since [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] has no means of resolving the changes between the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database instance and the objects in the project about to be overwritten, the only real choice the first developer has is to discard all of his or her changes and starting anew from a new project based on the current version of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
  
