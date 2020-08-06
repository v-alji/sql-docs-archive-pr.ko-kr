---
title: SQL Server 에이전트를 사용하여 원격 서버의 패키지 부하 분산 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- load-balancing [Integration Services]
- parent packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 9281c5f8-8da3-4ae8-8142-53c5919a4cfe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ea7b132d8cf86d2f211da25989df937d0db34ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652190"
---
# <a name="load-balancing-packages-on-remote-servers-by-using-sql-server-agent"></a><span data-ttu-id="94a85-102">SQL Server 에이전트를 사용하여 원격 서버의 패키지 로드 균형 조정</span><span class="sxs-lookup"><span data-stu-id="94a85-102">Load-Balancing Packages on Remote Servers by Using SQL Server Agent</span></span>
  <span data-ttu-id="94a85-103">패키지를 여러 개 실행해야 하는 경우 사용 가능한 다른 서버를 사용하는 것이 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-103">When many packages have to be run, it is convenient to use other servers that are available.</span></span> <span data-ttu-id="94a85-104">모든 패키지를 한 부모 패키지에서 관리하고 다른 서버를 사용하여 패키지를 실행하는 이 방법을 로드 균형 조정이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-104">This method of using other servers to run packages when the packages are all under the control of one parent package is called load balancing.</span></span> <span data-ttu-id="94a85-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 부하 분산은 패키지 소유자가 직접 설계해야 하며</span><span class="sxs-lookup"><span data-stu-id="94a85-105">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], load balancing is a manual procedure that must be architected by the owners of the packages.</span></span> <span data-ttu-id="94a85-106">서버에서 자동으로 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-106">Load balancing is not performed automatically by the servers.</span></span> <span data-ttu-id="94a85-107">또한 원격 서버에서 실행되는 패키지는 다른 패키지의 개별 태스크가 아닌 전체 패키지여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-107">Also, the packages that are run on the remote servers must be whole packages, not individual tasks in other packages.</span></span>  
  
 <span data-ttu-id="94a85-108">로드 균형 조정은 다음 시나리오에서 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-108">Load balancing is useful in the following scenarios:</span></span>  
  
-   <span data-ttu-id="94a85-109">패키지를 동시에 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-109">Packages can run at the same time.</span></span>  
  
-   <span data-ttu-id="94a85-110">패키지가 크고 순차적으로 실행할 경우 처리에 허용된 시간보다 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-110">Packages are large and, if run sequentially, can run longer than the time allowed for processing.</span></span>  
  
 <span data-ttu-id="94a85-111">관리자와 설계자가 처리에 추가 서버를 사용하는 것이 프로세스에 유리한지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-111">Administrators and architects can determine whether using additional servers for processing would benefit their processes.</span></span>  
  
## <a name="illustration-of-load-balancing"></a><span data-ttu-id="94a85-112">로드 균형 조정의 그림</span><span class="sxs-lookup"><span data-stu-id="94a85-112">Illustration of Load-Balancing</span></span>  
 <span data-ttu-id="94a85-113">다음 다이어그램에서는 서버의 부모 패키지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-113">The following diagram shows a parent package on a server.</span></span> <span data-ttu-id="94a85-114">부모 패키지에는 여러 개의 SQL 작업 에이전트 실행 태스크가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-114">The parent package contains multiple Execute SQL Job Agent tasks.</span></span> <span data-ttu-id="94a85-115">부모 패키지에 있는 각 태스크는 원격 서버의 SQL Server 에이전트를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-115">Each task in the parent package calls a SQL Server Agent on a remote server.</span></span> <span data-ttu-id="94a85-116">이러한 원격 서버에는 해당 서버의 패키지를 호출하는 단계가 포함된 SQL Server 에이전트 작업이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-116">Those remote servers contain SQL Server Agent jobs that include a step that calls a package on that server.</span></span>  
  
 <span data-ttu-id="94a85-117">![SSIS 부하 분산 아키텍처 개요](../media/loadbalancingoverview.gif "SSIS 부하 분산 아키텍처 개요")</span><span class="sxs-lookup"><span data-stu-id="94a85-117">![Overview of SSIS load balancing architecture](../media/loadbalancingoverview.gif "Overview of SSIS load balancing architecture")</span></span>  
  
 <span data-ttu-id="94a85-118">이 아키텍처에서 로드 균형을 조정하는 데 필요한 단계는 새로운 개념이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-118">The steps required for load balancing in this architecture are not new concepts.</span></span> <span data-ttu-id="94a85-119">대신 기존 개념 및 일반 SSIS 개체를 새로운 방식으로 사용하여 로드 균형을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-119">Instead, load balancing is achieved by using existing concepts and common SSIS objects in a new way.</span></span>  
  
## <a name="execution-of-packages-on-a-remote-instance-by-using-sql-server-agent"></a><span data-ttu-id="94a85-120">SQL Server 에이전트를 사용하여 원격 인스턴스에서 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="94a85-120">Execution of Packages on a Remote Instance by using SQL Server Agent</span></span>  
 <span data-ttu-id="94a85-121">원격 패키지 실행을 위한 기본 아키텍처에서 중앙 패키지는 다른 원격 패키지를 제어하는 SQL Server의 인스턴스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-121">In the basic architecture for remote package execution, a central package resides on the instance of SQL Server that controls the other remote packages.</span></span> <span data-ttu-id="94a85-122">다이어그램은 이 중앙 패키지, 즉 SSIS 부모를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-122">The diagram shows this central package, named the SSIS Parent.</span></span> <span data-ttu-id="94a85-123">이 부모 패키지가 있는 인스턴스는 자식 패키지를 실행하는 SQL Server 에이전트 작업의 실행을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-123">The instance where this parent package resides controls execution of the SQL Server Agent jobs that run the child packages.</span></span> <span data-ttu-id="94a85-124">자식 패키지는 원격 서버에서 SQL Server 에이전트가 제어하는 고정 일정에 따라 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-124">The child packages are not run according to a fixed schedule controlled by the SQL Server Agent on the remote server.</span></span> <span data-ttu-id="94a85-125">대신 자식 패키지는 부모 패키지가 호출하면 SQL Server 에이전트에 의해 시작되고 SQL Server 에이전트가 있는 SQL Server 인스턴스와 같은 인스턴스에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-125">Instead, the child packages are started by the SQL Server Agent when called by the parent package and are run on the same instance of SQL Server on which the SQL Server Agent resides.</span></span>  
  
 <span data-ttu-id="94a85-126">SQL Server 에이전트를 사용하여 원격 패키지를 실행하려면 부모 및 자식 패키지를 구성하고 자식 패키지를 제어하는 SQL Server 에이전트 작업을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-126">Before you can run a remote package by using SQL Server Agent, you must configure the parent and child packages and set up the SQL Server Agent jobs that control the child packages.</span></span> <span data-ttu-id="94a85-127">다음 섹션에서는 원격 서버에서 실행되는 패키지를 만들고, 구성하고, 실행하고, 유지 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-127">The following sections provide more information about how to create, configure, run, and maintain packages that run on remote servers.</span></span> <span data-ttu-id="94a85-128">이 프로세스에는 여러 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-128">There are several steps to this process:</span></span>  
  
-   <span data-ttu-id="94a85-129">원격 서버에서 자식 패키지 만들기 및 설치</span><span class="sxs-lookup"><span data-stu-id="94a85-129">Creating the child packages and installing them on remote servers.</span></span>  
  
-   <span data-ttu-id="94a85-130">패키지를 실행할 원격 인스턴스에 SQL Server 에이전트 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="94a85-130">Creating the SQL Server Agent jobs on the remote instances that will run the packages.</span></span>  
  
-   <span data-ttu-id="94a85-131">부모 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="94a85-131">Creating the parent package.</span></span>  
  
-   <span data-ttu-id="94a85-132">자식 패키지에 대한 로깅 시나리오 결정</span><span class="sxs-lookup"><span data-stu-id="94a85-132">Determine the logging scenario for the child packages.</span></span>  
  
 <span data-ttu-id="94a85-133">다음 표에서는 전체 프로세스를 안내하는 항목에 대한 링크를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-133">The following table provides links to topics that guide you through the process.</span></span>  
  
|<span data-ttu-id="94a85-134">항목</span><span class="sxs-lookup"><span data-stu-id="94a85-134">Topic</span></span>|<span data-ttu-id="94a85-135">Description</span><span class="sxs-lookup"><span data-stu-id="94a85-135">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="94a85-136">자식 패키지 구현</span><span class="sxs-lookup"><span data-stu-id="94a85-136">Implementation of Child Packages</span></span>](../implementation-of-child-packages.md)|<span data-ttu-id="94a85-137">패키지를 설치하고 해당 패키지를 실행할 SQL Server 에이전트 작업을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-137">Describes the installation of packages, and creation of the SQL Server Agent jobs to run the packages.</span></span>|  
|[<span data-ttu-id="94a85-138">부모 패키지 구현</span><span class="sxs-lookup"><span data-stu-id="94a85-138">Implementation of the Parent Package</span></span>](../implementation-of-the-parent-package.md)|<span data-ttu-id="94a85-139">여러 개의 SQL Server 에이전트 작업 실행 태스크가 포함된 부모 패키지를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-139">Describes the creation of the parent package that contains many Execute SQL Server Agent Job tasks.</span></span> <span data-ttu-id="94a85-140">각 태스크는 자식 패키지 중 하나를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-140">Each task runs one of the child packages.</span></span>|  
|[<span data-ttu-id="94a85-141">원격 서버의 로드 균형 조정된 패키지 로깅</span><span class="sxs-lookup"><span data-stu-id="94a85-141">Logging for Load Balanced Packages on Remote Servers</span></span>](../logging-for-load-balanced-packages-on-remote-servers.md)|<span data-ttu-id="94a85-142">원격 패키지에 대한 로깅 시나리오를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="94a85-142">Describes the logging scenario for the remote packages.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="94a85-143">관련 작업</span><span class="sxs-lookup"><span data-stu-id="94a85-143">Related Tasks</span></span>  
 [<span data-ttu-id="94a85-144">SQL Server 에이전트를 사용 하 여 패키지 예약</span><span class="sxs-lookup"><span data-stu-id="94a85-144">Schedule a Package by using SQL Server Agent</span></span>](../schedule-a-package-by-using-sql-server-agent.md)  
  
  
