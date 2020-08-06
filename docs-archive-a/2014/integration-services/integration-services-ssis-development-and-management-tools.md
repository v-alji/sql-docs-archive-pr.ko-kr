---
title: Integration Services (SSIS) 및 Studio 환경 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- studio environments [Integration Services]
- tools [Integration Services], Business Intelligence Development Studio
- Business Intelligence Development Studio, Integration Services in
- SQL Server Management Studio [Integration Services]
- SSIS, studio environments
- SQL Server Integration Services, studio environments
- tools [Integration Services], SQL Server Management Studio
ms.assetid: 4eb73e65-d9f3-4ac6-a408-abfa85afc537
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bfe0cf7ef482dce3870db8c730c597daf1d539e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651168"
---
# <a name="integration-services-ssis-and-studio-environments"></a><span data-ttu-id="b0084-102">Integration Services(SSIS) 및 Studio 환경</span><span class="sxs-lookup"><span data-stu-id="b0084-102">Integration Services (SSIS) and Studio Environments</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="b0084-103">에는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서 사용할 수 있는 두 가지 Studio가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-103">includes two studios for working with [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="b0084-104">에서는 비즈니스 솔루션에 필요한 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-104">for developing the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages that a business solution requires.</span></span> [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="b0084-105">는 패키지를 만들 수 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-105">provides the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you create packages.</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="b0084-106">에서는 프로덕션 환경에서 패키지를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-106">for managing packages in a production environment.</span></span>  
  
## <a name="sql-server-data-tools"></a><span data-ttu-id="b0084-107">SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="b0084-107">SQL Server Data Tools</span></span>  
 <span data-ttu-id="b0084-108">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서는 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-108">Working in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="b0084-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사를 실행하여 원본에서 대상으로 데이터를 복사하는 기본 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-109">Run the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard to create basic packages that copy data from a source to a destination.</span></span>  
  
-   <span data-ttu-id="b0084-110">복잡한 제어 흐름, 데이터 흐름, 이벤트 기반 논리 및 로깅이 포함된 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-110">Create packages that include complex control flow, data flow, event-driven logic, and logging.</span></span>  
  
-   <span data-ttu-id="b0084-111">[!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너의 문제 해결 및 모니터링 기능과 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 디버깅 기능을 사용하여 패키지를 테스트하고 디버깅합니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-111">Test and debug packages by using the troubleshooting and monitoring features in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, and the debugging features in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="b0084-112">패키지 및 패키지 개체의 속성을 런타임에 업데이트하는 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-112">Create configurations that update the properties of packages and package objects at run time.</span></span>  
  
-   <span data-ttu-id="b0084-113">패키지 및 종속 요소를 다른 컴퓨터에 설치할 수 있는 배포 유틸리티를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-113">Create a deployment utility that can install packages and their dependencies on other computers.</span></span>  
  
-   <span data-ttu-id="b0084-114">패키지의 복사본을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 데이터베이스, [!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 저장소 및 파일 시스템에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-114">Save copies of packages to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
 <span data-ttu-id="b0084-115">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에 대한 자세한 내용은 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0084-115">For more information about [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], see [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx).</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="b0084-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b0084-116">SQL Server Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="b0084-117">에서는 패키지를 관리하고 실행 중인 패키지를 모니터링하고 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 및 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체의 영향과 데이터 계보를 확인하는 데 사용되는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-117">provides the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service that you use to manage packages, monitor running packages, and determine impact and data lineage for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="b0084-118">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서는 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-118">Working in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="b0084-119">조직 요구에 맞게 패키지를 구성할 수 있는 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-119">Create folders to organize packages in a way that is meaningful to your organization.</span></span>  
  
-   <span data-ttu-id="b0084-120">패키지 실행 유틸리티를 사용하여 로컬 컴퓨터에 저장된 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-120">Run packages that are stored on the local computer by using the Execute Package utility.</span></span>  
  
-   <span data-ttu-id="b0084-121">패키지 실행 유틸리티를 실행하여 **dtexec** 명령 프롬프트 유틸리티(dtexec.exe)를 실행할 때 사용할 명령줄을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-121">Run the Execute Package utility to generate a command line to use when you run the **dtexec** command prompt utility (dtexec.exe).</span></span>  
  
-   <span data-ttu-id="b0084-122">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 데이터베이스, [!INCLUDE[ssIS](../includes/ssis-md.md)] 패키지 저장소 및 파일 시스템에서 패키지를 가져오고 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0084-122">Import and export packages to and from the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
