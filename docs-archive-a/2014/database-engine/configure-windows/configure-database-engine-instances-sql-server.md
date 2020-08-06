---
title: 데이터베이스 엔진 인스턴스 구성(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 84e36fcb-2c78-48e8-8e4b-bf784a3ee557
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af7408ff66d1f0e41369ba095ce51ea590d316e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661361"
---
# <a name="configure-database-engine-instances-sql-server"></a><span data-ttu-id="f8153-102">데이터베이스 엔진 인스턴스 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f8153-102">Configure Database Engine Instances (SQL Server)</span></span>
  <span data-ttu-id="f8153-103">인스턴스에서 호스팅하는 데이터베이스에 대해 정의된 성능 및 가용성 요구 사항에 맞게 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 각 인스턴스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-103">Each instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be configured to meet the performance and availability requirements defined for the databases hosted by the instance.</span></span> <span data-ttu-id="f8153-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 에는 리소스 사용과 같은 동작 및 감사 또는 트리거 재귀와 같은 기능의 가용성을 제어하는 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] includes configuration options that control behaviors such as resource usage and the availability of features such as auditing or trigger recursion.</span></span>  
  
## <a name="instance-configuration"></a><span data-ttu-id="f8153-105">인스턴스 구성</span><span class="sxs-lookup"><span data-stu-id="f8153-105">Instance Configuration</span></span>  
 <span data-ttu-id="f8153-106">데이터베이스를 프로덕션에 배포하는 경우 데이터베이스에 필요한 성능 수준 및 데이터베이스의 필수 가용성 수준과 같은 SLA(서비스 수준 계약) 정의 영역이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-106">When a database is deployed into production there is often a service level agreement (SLA) defining areas such as the levels of performance required from the database and the required availability level of the database.</span></span> <span data-ttu-id="f8153-107">일반적으로 SLA 조항에 따라 인스턴스에 대한 구성 요구 사항이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-107">The terms of the SLA typically drive configuration requirements for the instance.</span></span>  
  
 <span data-ttu-id="f8153-108">인스턴스는 일반적으로 설치한 후 즉시 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-108">An instance is usually configured immediately after it has been installed.</span></span> <span data-ttu-id="f8153-109">일반적으로 초기 구성은 인스턴스에 배포하려고 계획된 데이터베이스 유형에 대한 SLA 요구 사항에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-109">The initial configuration is usually determined by the SLA requirements of the types of databases planned to be deployed to the instance.</span></span> <span data-ttu-id="f8153-110">데이터베이스를 배포한 후 데이터베이스 관리자는 인스턴스의 성능을 모니터링하고 성능 메트릭에서 인스턴스가 SLA 요구 사항과 일치하지 않는 것으로 나타나는 경우 필요에 따라 구성 설정을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-110">After the databases have been deployed, the database administrators monitor the performance of the instance and adjust the configuration settings as needed if the performance metrics show the instance is not meeting the SLA requirements.</span></span>  
  
## <a name="configuration-tasks"></a><span data-ttu-id="f8153-111">구성 태스크</span><span class="sxs-lookup"><span data-stu-id="f8153-111">Configuration Tasks</span></span>  
  
|<span data-ttu-id="f8153-112">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="f8153-112">Task Description</span></span>|<span data-ttu-id="f8153-113">항목</span><span class="sxs-lookup"><span data-stu-id="f8153-113">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="f8153-114">다양한 인스턴스 구성 옵션과 이러한 옵션을 보거나 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-114">Describes the various instance configuration options and how to view or change these options.</span></span>|[<span data-ttu-id="f8153-115">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f8153-115">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)|  
|<span data-ttu-id="f8153-116">인스턴스에서 새 데이터 및 로그 파일의 기본 위치를 보고 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-116">Describes how to view and configure the default locations of new data and log files in the instance.</span></span>|[<span data-ttu-id="f8153-117">데이터 및 로그 파일의 기본 위치 보기 또는 변경&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f8153-117">View or Change the Default Locations for Data and Log Files &#40;SQL Server Management Studio&#41;</span></span>](view-or-change-the-default-locations-for-data-and-log-files.md)|  
|<span data-ttu-id="f8153-118">소프트 NUMA를 사용하도록 SQL Server를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-118">Describes how to configure SQL Server to use soft-NUMA.</span></span>|[<span data-ttu-id="f8153-119">소프트 NUMA &#40;SQL Server를 사용 하도록 SQL Server 구성&#41;</span><span class="sxs-lookup"><span data-stu-id="f8153-119">Configure SQL Server to Use Soft-NUMA &#40;SQL Server&#41;</span></span>](soft-numa-sql-server.md)|  
|<span data-ttu-id="f8153-120">TCP/IP 포트를 NUMA(Non-Uniform Memory Access) 노드 선호도에 매핑하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-120">Describes how to map a TCP/IP port to non-uniform memory access (NUMA) node affinity.</span></span>|[<span data-ttu-id="f8153-121">NUMA 노드에 TCP IP 포트 매핑&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f8153-121">Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;</span></span>](map-tcp-ip-ports-to-numa-nodes-sql-server.md)|  
|<span data-ttu-id="f8153-122">Windows 메모리의 페이지 잠금 정책을 사용하도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-122">Describes how to enable the Windows Lock Pages In Memory policy.</span></span> <span data-ttu-id="f8153-123">이 정책은 데이터를 실제 메모리에 유지하는 프로세스를 사용하여 시스템이 디스크의 가상 메모리로 데이터를 페이징하지 않도록 방지할 수 있는 계정을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8153-123">This policy determines which accounts can use a process to keep data in physical memory, preventing the system from paging the data to virtual memory on disk.</span></span>|[<span data-ttu-id="f8153-124">Lock Pages in Memory 옵션 설정&#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="f8153-124">Enable the Lock Pages in Memory Option &#40;Windows&#41;</span></span>](enable-the-lock-pages-in-memory-option-windows.md)|  
  
## <a name="see-also"></a><span data-ttu-id="f8153-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8153-125">See Also</span></span>  
 [<span data-ttu-id="f8153-126">데이터베이스 엔진 인스턴스&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f8153-126">Database Engine Instances &#40;SQL Server&#41;</span></span>](database-engine-instances-sql-server.md)  
  
  
