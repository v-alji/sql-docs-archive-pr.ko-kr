---
title: 리소스 상태 정책 결과 보기(SQL Server 유틸리티) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 80cb14fb-f4c6-4be2-ba17-eb4e4cddd35f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c4ab30ad0e87782f8187370a53747be4cf5d313d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732611"
---
# <a name="view-resource-health-policy-results-sql-server-utility"></a><span data-ttu-id="e5603-102">리소스 상태 정책 결과 보기(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="e5603-102">View Resource Health Policy Results (SQL Server Utility)</span></span>
  <span data-ttu-id="e5603-103">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]의 유틸리티 대시보드를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 관리되는 인스턴스 및 데이터 계층 애플리케이션의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 유틸리티 리소스 매개 변수를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5603-103">Use the Utility dashboard in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to view [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Utility resource parameters for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and data-tier applications.</span></span> <span data-ttu-id="e5603-104">자세한 내용은 [SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5603-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="view-sql-server-utility-resource-health-policy-results"></a><span data-ttu-id="e5603-105">SQL Server 유틸리티 리소스 상태 정책 결과 보기</span><span class="sxs-lookup"><span data-stu-id="e5603-105">View SQL Server Utility resource health policy results.</span></span>  
  
1.  <span data-ttu-id="e5603-106">유틸리티 탐색기 탐색 창을 보려면 SSMS( [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] )에서 **보기**를 클릭하고 **유틸리티 탐색기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e5603-106">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (SSMS), click **View**, then click **Utility Explorer** to view the Utility Explorer navigation pane.</span></span> <span data-ttu-id="e5603-107">내용 창을 보려면 **보기**를 클릭하고 **유틸리티 탐색기 내용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5603-107">To view the content pane, click **View**, then click **Utility Explorer Content**.</span></span>  
  
2.  <span data-ttu-id="e5603-108">탐색 창에서 ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**유틸리티에 연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5603-108">In the navigation pane, click ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Connect to Utility**.</span></span> <span data-ttu-id="e5603-109">UCP(유틸리티 제어 지점)를 만들지 않았거나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스 또는 데이터 계층 애플리케이션을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 유틸리티에 등록하지 않은 경우 [SQL Server 유틸리티 기능 및 작업](sql-server-utility-features-and-tasks.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5603-109">If you have not created a utility control point (UCP) or if you have not enrolled instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or data-tier applications into the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Utility, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
3.  <span data-ttu-id="e5603-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스 및 데이터 계층 애플리케이션의 요약 데이터를 보려면 UCP 노드를 클릭합니다(새로 고치려면 마우스 오른쪽 단추 클릭).</span><span class="sxs-lookup"><span data-stu-id="e5603-110">Click the UCP node to view summary data for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and data-tier applications (right-click to refresh).</span></span> <span data-ttu-id="e5603-111">대시보드 데이터가 내용 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5603-111">Dashboard data is displayed in the content pane.</span></span>  
  
4.  <span data-ttu-id="e5603-112">**의 관리되는 인스턴스의 목록 뷰 데이터를 보려면** 관리되는 인스턴스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 노드를 클릭합니다(새로 고치려면 마우스 오른쪽 단추 클릭).</span><span class="sxs-lookup"><span data-stu-id="e5603-112">Click the **Managed Instances** node to view list view data for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (right-click to refresh).</span></span> <span data-ttu-id="e5603-113">목록 뷰 데이터가 내용 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5603-113">List view data is displayed in the content pane.</span></span>  
  
5.  <span data-ttu-id="e5603-114">데이터 계층 애플리케이션의 목록 뷰를 보려면 **배포된 데이터 계층 애플리케이션** 노드를 클릭합니다(새로 고치려면 마우스 오른쪽 단추 클릭).</span><span class="sxs-lookup"><span data-stu-id="e5603-114">Click the **Deployed Data-tier Applications** node to view list view data for data-tier applications (right-click to refresh).</span></span> <span data-ttu-id="e5603-115">목록 뷰 데이터가 내용 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5603-115">List view data is displayed in the content pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5603-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5603-116">See Also</span></span>  
 <span data-ttu-id="e5603-117">[SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="e5603-117">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 <span data-ttu-id="e5603-118">[CPU 사용 정책에서 노이즈 줄이기&#40;SQL Server 유틸리티&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="e5603-118">[Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md) </span></span>  
 <span data-ttu-id="e5603-119">[배포된 데이터 계층 애플리케이션 세부 정보&#40;SQL Server 유틸리티&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="e5603-119">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="e5603-120">[관리되는 인스턴스 세부 정보&#40;SQL Server 유틸리티&#41;](../../database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="e5603-120">[Managed Instance Details &#40;SQL Server Utility&#41;](../../database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="e5603-121">유틸리티 관리&#40;SQL Server 유틸리티&#41;</span><span class="sxs-lookup"><span data-stu-id="e5603-121">Utility Administration &#40;SQL Server Utility&#41;</span></span>](../../database-engine/utility-administration-sql-server-utility.md)  
  
  
