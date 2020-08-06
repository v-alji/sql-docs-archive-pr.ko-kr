---
title: Integration Services 서비스(SSIS 서비스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, about Integration Services service
- SQL Server Integration Services service
- service [Integration Services],about Integration Services service
- service [Integration Services]
- SQL Server Integration Services, service
ms.assetid: 2c785b3b-4a0c-4df7-b5cd-23756dc87842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04b24f0f0d54009c50654904d606a208504f229c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742391"
---
# <a name="integration-services-service-ssis-service"></a><span data-ttu-id="7f95a-102">Integration Services 서비스(SSIS 서비스)</span><span class="sxs-lookup"><span data-stu-id="7f95a-102">Integration Services Service (SSIS Service)</span></span>
  <span data-ttu-id="7f95a-103">이 섹션의 항목에서는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 관리하는 Windows 서비스인 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-103">The topics in this section discuss the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="7f95a-104">이 서비스는 Integration Services 패키지를 생성, 저장 및 실행하는 데 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-104">This service is not required to create, save, and run Integration Services packages.</span></span> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="7f95a-105">는 이전 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 버전과의 호환성을 위한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-105">supports the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7f95a-106">부터는에서 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] `SSISDB` [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트 배포 모델을 사용 하 여 서버에 배포한 프로젝트의 데이터베이스에 개체, 설정 및 작업 데이터를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-106">Starting in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores objects, settings, and operational data in the `SSISDB` database for projects that you've deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model.</span></span> <span data-ttu-id="7f95a-107">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터베이스 엔진의 인스턴스인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서버는 데이터베이스를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-107">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, which is an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine, hosts the database.</span></span> <span data-ttu-id="7f95a-108">데이터베이스에 대한 자세한 내용은 [SSIS 카탈로그](../catalog/ssis-catalog.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f95a-108">For more information about the database, see [SSIS Catalog](../catalog/ssis-catalog.md).</span></span> <span data-ttu-id="7f95a-109">프로젝트를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포하는 방법에 대한 자세한 내용은 [Integration Services 서버에 프로젝트 배포](../deploy-projects-to-integration-services-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f95a-109">For more information about deploying projects to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
## <a name="management-capabilities"></a><span data-ttu-id="7f95a-110">관리 기능</span><span class="sxs-lookup"><span data-stu-id="7f95a-110">Management Capabilities</span></span>  
 <span data-ttu-id="7f95a-111">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서비스는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 관리를 위한 Windows 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-111">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is a Windows service for managing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="7f95a-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서비스는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-112">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is available only in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="7f95a-113">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서비스는 다음 관리 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-113">Running the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service provides the following management capabilities:</span></span>  
  
-   <span data-ttu-id="7f95a-114">원격 및 로컬에 저장된 패키지 시작</span><span class="sxs-lookup"><span data-stu-id="7f95a-114">Starting remote and locally stored packages</span></span>  
  
-   <span data-ttu-id="7f95a-115">원격 및 로컬로 실행 중인 패키지 중지</span><span class="sxs-lookup"><span data-stu-id="7f95a-115">Stopping remote and locally running packages</span></span>  
  
-   <span data-ttu-id="7f95a-116">원격 및 로컬로 실행 중인 패키지 모니터링</span><span class="sxs-lookup"><span data-stu-id="7f95a-116">Monitoring remote and locally running packages</span></span>  
  
-   <span data-ttu-id="7f95a-117">패키지 가져오기 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="7f95a-117">Importing and exporting packages</span></span>  
  
-   <span data-ttu-id="7f95a-118">패키지 스토리지 관리</span><span class="sxs-lookup"><span data-stu-id="7f95a-118">Managing package storage</span></span>  
  
-   <span data-ttu-id="7f95a-119">스토리지 폴더 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="7f95a-119">Customizing storage folders</span></span>  
  
-   <span data-ttu-id="7f95a-120">서비스가 중지될 때 실행 중인 패키지 중지</span><span class="sxs-lookup"><span data-stu-id="7f95a-120">Stopping running packages when the service is stopped</span></span>  
  
-   <span data-ttu-id="7f95a-121">Windows 이벤트 로그 보기</span><span class="sxs-lookup"><span data-stu-id="7f95a-121">Viewing the Windows Event log</span></span>  
  
-   <span data-ttu-id="7f95a-122">여러 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="7f95a-122">Connecting to multiple [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] servers</span></span>  
  
## <a name="startup-type-for-integration-services-service"></a><span data-ttu-id="7f95a-123">Integration Services 서비스 시작 유형</span><span class="sxs-lookup"><span data-stu-id="7f95a-123">Startup Type for Integration Services Service</span></span>  
 <span data-ttu-id="7f95a-124">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서비스는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]구성 요소를 설치할 때 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-124">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is installed when you install the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7f95a-125">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서비스는 기본적으로 시작되며 서비스의 시작 유형은 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-125">By default, the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is started and the startup type of the service is set to automatic.</span></span> <span data-ttu-id="7f95a-126">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 저장소에 저장된 패키지를 모니터링하려면 서비스가 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-126">The service must be running to monitor the packages that are stored in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store.</span></span> <span data-ttu-id="7f95a-127">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지 저장소는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 있는 msdb 데이터베이스 또는 파일 시스템 내의 지정된 폴더일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-127">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store can be either the msdb database in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the designated folders in the file system.</span></span>  
  
 <span data-ttu-id="7f95a-128">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서비스는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 디자인 및 실행만 하려는 경우에는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-128">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service is not required if you only want to design and execute [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="7f95a-129">하지만 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 패키지를 나열하고 모니터링하려면 이 서비스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7f95a-129">However, the service is required to list and monitor packages using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="7f95a-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="7f95a-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="7f95a-131">Integration Services 서비스 속성 설정</span><span class="sxs-lookup"><span data-stu-id="7f95a-131">Set the Properties of the Integration Services Service</span></span>](../set-the-properties-of-the-integration-services-service.md)  
  
-   [<span data-ttu-id="7f95a-132">Integration Services 서비스의 뷰 이벤트</span><span class="sxs-lookup"><span data-stu-id="7f95a-132">View Events for the Integration Services Service</span></span>](../view-events-for-the-integration-services-service.md)  
  
  
