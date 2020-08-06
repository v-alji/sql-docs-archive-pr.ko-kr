---
title: 상태 정책 구성(SQL Server 유틸리티) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c5ee466dd2d5bac2ea64364bfc78de8f2f5bea10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647689"
---
# <a name="configure-health-policies-sql-server-utility"></a><span data-ttu-id="b334c-102">상태 정책 구성(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="b334c-102">Configure Health Policies (SQL Server Utility)</span></span>
  <span data-ttu-id="b334c-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 유틸리티 대시보드를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스 및 데이터 계층 애플리케이션의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 리소스 매개 변수를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b334c-103">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility resource parameters for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and data-tier applications.</span></span> <span data-ttu-id="b334c-104">자세한 내용은 [SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b334c-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 <span data-ttu-id="b334c-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 상태 정책 결과를 보려면 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 유틸리티 제어 지점에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b334c-105">To view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility health policy results, connect to a utility control point from [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="b334c-106">자세한 내용은 [유틸리티 탐색기를 사용하여 SQL Server 유틸리티 관리](use-utility-explorer-to-manage-the-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b334c-106">For more information, see [Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b334c-107">유틸리티 상태 정책은 데이터 계층 애플리케이션 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스에 대해 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b334c-107">Utility health policies can be configured for data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b334c-108">상태 정책은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 모든 데이터 계층 애플리케이션 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스에 대해 전역으로 정의하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 각 데이터 계층 애플리케이션 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스에 대해 개별적으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b334c-108">Health policies can be defined globally for all data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, or they can be defined individually for each data-tier application and for each managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
## <a name="monitoring-policies-for-data-tier-applications"></a><span data-ttu-id="b334c-109">데이터 계층 애플리케이션의 정책 모니터링</span><span class="sxs-lookup"><span data-stu-id="b334c-109">Monitoring Policies for Data-tier Applications</span></span>  
 <span data-ttu-id="b334c-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 계층 애플리케이션의 초과 사용 및 미달 사용 정책은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b334c-110">Overutilization and underutilization policies for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data-tier applications are as follows:</span></span>  
  
-   <span data-ttu-id="b334c-111">데이터 계층 애플리케이션 프로세서 사용률</span><span class="sxs-lookup"><span data-stu-id="b334c-111">Data-tier application processor utilization.</span></span>  
  
-   <span data-ttu-id="b334c-112">데이터베이스 파일을 위한 데이터 계층 애플리케이션 파일 공간</span><span class="sxs-lookup"><span data-stu-id="b334c-112">Data-tier application file space for database files.</span></span>  
  
-   <span data-ttu-id="b334c-113">스토리지 볼륨을 위한 데이터 계층 애플리케이션 파일 공간</span><span class="sxs-lookup"><span data-stu-id="b334c-113">Data-tier application file space for storage volumes.</span></span>  
  
-   <span data-ttu-id="b334c-114">컴퓨터 프로세서 사용률</span><span class="sxs-lookup"><span data-stu-id="b334c-114">Computer processor utilization.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b334c-115">스토리지 볼륨 및 프로세서 사용률은 데이터 계층 애플리케이션의 읽기 전용 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="b334c-115">Storage volume and processor utilization are read-only policies for data-tier applications.</span></span>  
  
 <span data-ttu-id="b334c-116">데이터 계층 애플리케이션의 전역 모니터링 정책을 보거나 변경하는 방법은 [유틸리티 관리&#40;SQL Server 유틸리티&#41;](../../database-engine/utility-administration-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b334c-116">For more information about viewing or changing global monitoring policies for data-tier applications, see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="b334c-117">개별 데이터 계층 애플리케이션의 모니터링 정책을 보거나 변경하는 방법은 [배포된 데이터 계층 애플리케이션 세부 정보&#40;SQL Server 유틸리티&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b334c-117">For more information about viewing or changing monitoring policies for individual data-tier applications, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md).</span></span>  
  
## <a name="monitoring-policies-for-managed-instances-of-sql-server"></a><span data-ttu-id="b334c-118">SQL Server의 관리되는 인스턴스의 모니터링 정책</span><span class="sxs-lookup"><span data-stu-id="b334c-118">Monitoring Policies for Managed Instances of SQL Server</span></span>  
 <span data-ttu-id="b334c-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스의 초과 사용 및 미달 사용 정책은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b334c-119">Overutilization and underutilization policies for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are as follows:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b334c-120">인스턴스 프로세스 사용률</span><span class="sxs-lookup"><span data-stu-id="b334c-120">instance processor utilization.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b334c-121">인스턴스 파일 공간</span><span class="sxs-lookup"><span data-stu-id="b334c-121">instance file space for database files.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="b334c-122">스토리지 볼륨의 인스턴스 파일 공간</span><span class="sxs-lookup"><span data-stu-id="b334c-122">instance file space for storage volumes.</span></span>  
  
-   <span data-ttu-id="b334c-123">컴퓨터 프로세서 사용률</span><span class="sxs-lookup"><span data-stu-id="b334c-123">Computer processor utilization.</span></span>  
  
 <span data-ttu-id="b334c-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스의 전역 모니터링 정책을 보거나 변경하는 방법은 [유틸리티 관리&#40;SQL Server 유틸리티&#41;](../../database-engine/utility-administration-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b334c-124">For more information about viewing or changing global monitoring policies for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="b334c-125">개별 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스의 모니터링 정책을 보거나 변경하는 방법은 [관리되는 인스턴스 세부 정보&#40;SQL Server 유틸리티&#41;](../../database-engine/managed-instance-details-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b334c-125">For more information about viewing or changing monitoring policies for individual managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Managed Instance Details &#40;SQL Server Utility&#41;](../../database-engine/managed-instance-details-sql-server-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b334c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b334c-126">See Also</span></span>  
 <span data-ttu-id="b334c-127">[SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="b334c-127">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="b334c-128">CPU 사용 정책에서 노이즈 줄이기&#40;SQL Server 유틸리티&#41;</span><span class="sxs-lookup"><span data-stu-id="b334c-128">Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;</span></span>](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  
