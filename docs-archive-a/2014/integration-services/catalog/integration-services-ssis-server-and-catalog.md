---
title: Integration Services (SSIS) 서버 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0da83cdac269499dfbde7a6387a4af4690c83ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652281"
---
# <a name="integration-services-ssis-server"></a><span data-ttu-id="13d4a-102">Integration Services(SSIS) 서버</span><span class="sxs-lookup"><span data-stu-id="13d4a-102">Integration Services (SSIS) Server</span></span>
  <span data-ttu-id="13d4a-103">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 패키지를 디자인하고 테스트한 후에는 이 패키지가 포함된 프로젝트를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-103">After you design and test packages in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], you can deploy the projects that contain the packages to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="13d4a-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버는 `SSISDB` 데이터베이스를 호스팅하는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-104">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server is an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the `SSISDB` database.</span></span> <span data-ttu-id="13d4a-105">데이터베이스는 패키지, 프로젝트, 매개 변수, 사용 권한, 서버 속성 및 작업 기록과 같은 개체를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-105">The database stores the following objects: packages, projects, parameters, permissions, server properties, and operational history.</span></span>  
  
 <span data-ttu-id="13d4a-106">`SSISDB` 데이터베이스는 쿼리할 수 있는 공용 보기에 개체 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-106">The `SSISDB` database exposes the object information in public views that you can query.</span></span> <span data-ttu-id="13d4a-107">또한 이 데이터베이스는 개체를 관리하기 위해 호출할 수 있는 저장 프로시저를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-107">The database also provides stored procedures that you can call to manage the objects.</span></span>  
  
 <span data-ttu-id="13d4a-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 프로젝트를 배포하려면 먼저 `SSISDB` 카탈로그를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-108">Before you can deploy the projects to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you need to create the `SSISDB` catalog.</span></span>  
  
 <span data-ttu-id="13d4a-109">SSISDB 카탈로그 기능에 대한 개요는 [SSIS 카탈로그](ssis-catalog.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13d4a-109">For an overview of the SSISDB catalog functionality, see [SSIS Catalog](ssis-catalog.md).</span></span>  
  
## <a name="high-availability"></a><span data-ttu-id="13d4a-110">고가용성</span><span class="sxs-lookup"><span data-stu-id="13d4a-110">High Availability</span></span>  
 <span data-ttu-id="13d4a-111">다른 사용자 데이터베이스와 같이 `SSISDB` 데이터베이스는 데이터베이스 미러링 및 복제를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-111">Like other user databases, the `SSISDB` database does support database mirroring and replication.</span></span> <span data-ttu-id="13d4a-112">미러링 및 복제에 대한 자세한 내용은 [데이터베이스 미러링&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13d4a-112">For more information about mirroring and replication, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="13d4a-113">또한 SSIS 및 AlwaysOn 가용성 그룹을 사용하여 SSISDB의 고가용성 및 해당 콘텐츠를 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-113">You can also provide high-availability of SSISDB and its contents by making use of SSIS and AlwaysOn Availability Groups.</span></span> <span data-ttu-id="13d4a-114">자세한 내용은 blogs.msdn.com에서 Matt Masson이 게시한 [AlwaysOn을 사용하는 SSIS](https://go.microsoft.com/fwlink/?LinkId=255873)블로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="13d4a-114">For more information, see this blog post by Matt Masson, [SSIS with AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873), at blogs.msdn.com.</span></span>  
  
##  <a name="integration-services-server-in-sql-server-management-studio"></a><a name="ssms"></a><span data-ttu-id="13d4a-115">SQL Server Management Studio의 Integration Services 서버</span><span class="sxs-lookup"><span data-stu-id="13d4a-115">Integration Services Server in SQL Server Management Studio</span></span>  
 <span data-ttu-id="13d4a-116">`SSISDB` 데이터베이스를 호스팅하는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결하면 개체 탐색기에 다음 개체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-116">When you connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the `SSISDB` database, you see the following objects in Object Explorer:</span></span>  
  
-   <span data-ttu-id="13d4a-117">**SSISDB 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="13d4a-117">**SSISDB Database**</span></span>  
  
     <span data-ttu-id="13d4a-118">`SSISDB`데이터베이스는 개체 탐색기의 **데이터베이스** 노드 아래에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-118">The `SSISDB` database appears under the **Databases** node in Object Explore.</span></span> <span data-ttu-id="13d4a-119">뷰를 쿼리하고 저장 프로시저를 호출하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버와 이 서버에 저장된 개체를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-119">You can query the views and call the stored procedures that manage the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server and the objects that are stored on the server.</span></span>  
  
-   <span data-ttu-id="13d4a-120">**Integration Services 카탈로그**</span><span class="sxs-lookup"><span data-stu-id="13d4a-120">**Integration Services Catalogs**</span></span>  
  
     <span data-ttu-id="13d4a-121">**Integration Services 카탈로그** 노드 아래에는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트 및 환경을 위한 폴더가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13d4a-121">Under the **Integration Services Catalogs** node there are folders for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects and environments.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="13d4a-122">관련 작업</span><span class="sxs-lookup"><span data-stu-id="13d4a-122">Related Tasks</span></span>  
  
-   [<span data-ttu-id="13d4a-123">SSIS 카탈로그 만들기</span><span class="sxs-lookup"><span data-stu-id="13d4a-123">Create the SSIS Catalog</span></span>](../create-the-ssis-catalog.md)  
  
-   [<span data-ttu-id="13d4a-124">Integration Services 서버의 패키지 목록 보기</span><span class="sxs-lookup"><span data-stu-id="13d4a-124">View the List of Packages on the Integration Services Server</span></span>](view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [<span data-ttu-id="13d4a-125">Deploy Projects to Integration Services Server</span><span class="sxs-lookup"><span data-stu-id="13d4a-125">Deploy Projects to Integration Services Server</span></span>](../deploy-projects-to-integration-services-server.md)  
  
-   [<span data-ttu-id="13d4a-126">SQL Server Management Studio를 사용하여 SSIS 서버에서 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="13d4a-126">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a><span data-ttu-id="13d4a-127">관련 내용</span><span class="sxs-lookup"><span data-stu-id="13d4a-127">Related Content</span></span>  
 <span data-ttu-id="13d4a-128">blogs.msdn.com의 블로그 항목, [AlwaysOn을 사용하는 SSIS](https://go.microsoft.com/fwlink/?LinkId=255873)</span><span class="sxs-lookup"><span data-stu-id="13d4a-128">Blog entry, [SSIS with AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873), at blogs.msdn.com.</span></span>  
  
  
