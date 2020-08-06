---
title: 데이터 원본 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], about data sources
ms.assetid: 7ac81612-9822-470f-8d0f-a1dc96142fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a52889627dbe61254ac1359ae97f25ee8521b6e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652265"
---
# <a name="data-sources"></a><span data-ttu-id="1067d-102">솔루션 탐색기</span><span class="sxs-lookup"><span data-stu-id="1067d-102">Data Sources</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="1067d-103">는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에 사용할 수 있는 데이터 원본인 디자인 타임 개체를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-103">includes a design-time object that you can use in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages: the data source.</span></span>  
  
 <span data-ttu-id="1067d-104">데이터 원본 개체는 연결에 대한 참조이며 최소한 연결 문자열과 데이터 원본 식별자가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-104">A data source object is a reference to a connection, and at a minimum, it includes a connection string and a data source identifier.</span></span> <span data-ttu-id="1067d-105">또한 여기에는 설명, 이름, 사용자 이름 및 암호와 같은 추가 메타데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-105">It can also include additional metadata such a description, a name, a user name, and a password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1067d-106">패키지 배포 모델을 사용하도록 구성된 프로젝트에만 데이터 원본을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-106">You can add data sources only to projects that are configured to use the package deployment model.</span></span> <span data-ttu-id="1067d-107">프로젝트가 프로젝트 배포 모델을 사용하도록 구성된 경우 데이터 원본을 사용하는 대신 프로젝트 수준에서 만든 연결 관리자를 사용하여 연결을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-107">If a project is configured to use the project deployment model, you use connection managers created at the project level to share connections, in place of using data sources.</span></span>  
>   
>  <span data-ttu-id="1067d-108">배포 모델에 대한 자세한 내용은 [Deployment of Projects and Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1067d-108">For more information about the deployment models, see [Deployment of Projects and Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span> <span data-ttu-id="1067d-109">프로젝트를 프로젝트 배포 모델로 변환하는 방법은 [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1067d-109">For more information about converting a project to the project deployment model, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="1067d-110">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에서 데이터 원본을 사용하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-110">The advantages of using data sources in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages include the following:</span></span>  
  
-   <span data-ttu-id="1067d-111">데이터 원본에는 프로젝트 범위가 있습니다. 즉, 특정 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트에서 만든 데이터 원본은 해당 프로젝트의 모든 패키지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-111">A data source has project scope, which means that a data source created in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project is available to all the packages in the project.</span></span> <span data-ttu-id="1067d-112">데이터 원본을 한 번 정의한 다음에는 여러 패키지에서 연결 관리자를 통해 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-112">A data source can be defined one time and then referenced by connection managers in multiple packages.</span></span>  
  
-   <span data-ttu-id="1067d-113">데이터 원본은 데이터 원본 개체와 해당 패키지 참조 간의 동기화를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-113">A data source offers synchronization between the data source object and its package references.</span></span> <span data-ttu-id="1067d-114">데이터 원본과 이를 참조하는 패키지가 동일 프로젝트에 들어 있는 경우 데이터 원본 참조에 대한 연결 문자열 속성은 데이터 원본이 변경될 때 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-114">If the data source and the packages that reference it reside in the same project, the connection string property of the data source references is automatically updated when the data source changes.</span></span>  
  
## <a name="reference-data-sources"></a><span data-ttu-id="1067d-115">데이터 원본 참조</span><span class="sxs-lookup"><span data-stu-id="1067d-115">Reference Data Sources</span></span>  
 <span data-ttu-id="1067d-116">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트에 데이터 원본 개체를 추가하려면 **솔루션 탐색기** 에서 **데이터 원본** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 데이터 원본**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-116">To add a data source object to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, right-click the **Data Sources** folder in **Solution Explorer** and then click **New Data Source**.</span></span> <span data-ttu-id="1067d-117">**데이터 원본** 폴더에 항목이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-117">The item is added to the **Data Sources** folder.</span></span> <span data-ttu-id="1067d-118">다른 프로젝트에서 만든 데이터 원본 개체를 사용하려면 이를 먼저 프로젝트에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-118">If you want to use data source objects that were created in other projects, you must first add them to the project.</span></span>  
  
 <span data-ttu-id="1067d-119">패키지에서 데이터 원본 개체를 사용하려면 해당 데이터 원본 개체를 참조하는 연결 관리자를 패키지에 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-119">You use a data source object in a package by adding a connection manager that references the data source object to the package.</span></span> <span data-ttu-id="1067d-120">패키지 제어 흐름 및 데이터 흐름을 작성하기 전이나 제어 흐름 또는 데이터 흐름을 구성하는 단계에서 패키지에 연결 관리자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-120">You can add it to the package before you build the package control flow and data flows, or as a step in constructing the control flow or data flow.</span></span>  
  
 <span data-ttu-id="1067d-121">데이터 원본 개체는 데이터 원본에 대한 간단한 연결을 나타내며 데이터 저장소에서 참조되는 개체에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-121">A data source object represents a simple connection to a data source and provides access to the objects in the data store that it references.</span></span> <span data-ttu-id="1067d-122">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]AdventureWorks 샘플 데이터베이스에 연결하는 데이터 원본 개체에는 데이터베이스의 60개 테이블이 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-122">For example, a data source object that connects to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]AdventureWorks Sample Database includes all 60 tables from the database.</span></span>  
  
 <span data-ttu-id="1067d-123">데이터 원본과 이를 참조하는 연결 관리자 사이에는 종속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-123">There is no dependency between a data source and the connection managers that reference it.</span></span> <span data-ttu-id="1067d-124">데이터 원본이 더 이상 프로젝트에 속하지 않는 경우에도 패키지는 계속 유효한 상태로 남습니다. 그 이유는 연결 형식과 연결 문자열과 같은 데이터 원본에 대한 정보가 패키지 정의에 포함되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="1067d-124">If a data source is no longer part of the project, the packages continue to be valid, because information about the data source, such as its connection type and connection string, is included in the package definition.</span></span>  
  
  
