---
title: 리소스 상태 정책 정의 수정(SQL Server 유틸리티) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.UTILITY.ADMINISTRATION.F1
ms.assetid: 27bec0b6-92e9-448e-8c70-fe36802cf128
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d2651a2dd0b4994a6dacaad6c01d3f1ec68c98e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650962"
---
# <a name="modify-a-resource-health-policy-definition-sql-server-utility"></a><span data-ttu-id="9417a-102">리소스 상태 정책 정의 수정(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="9417a-102">Modify a Resource Health Policy Definition (SQL Server Utility)</span></span>
  <span data-ttu-id="9417a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 리소스 상태 정책 정의를 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-103">This topic describes how to modify a resource health policy definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="9417a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 리소스 사용률 정책을 수정하려면 먼저 UCP(유틸리티 제어 지점)를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-104">Before you modify a resource utilization policy in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, you must create a utility control point (UCP).</span></span> <span data-ttu-id="9417a-105">자세한 내용은 [SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9417a-105">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9417a-106">유틸리티 리소스 사용률 정책은 데이터 계층 애플리케이션 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스에 대해 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-106">Utility resource utilization policies can be configured for data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9417a-107">리소스 사용률 정책은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 모든 데이터 계층 애플리케이션 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스에 대해 전역으로 정의하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 각 데이터 계층 애플리케이션 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스에 대해 개별적으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-107">Resource utilization policies can be defined globally for all data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, or they can be defined individually for each data-tier application and for each managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="9417a-108">전역 정책을 구현하고 개별 데이터 계층 애플리케이션 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스가 자체 정책 정의를 구성하도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-108">You can also implement global policies and have individual data-tier applications or managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configured with their own policy definitions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9417a-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="9417a-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="modify-global-resource-utilization-policies-in-a-sql-server-utility"></a><span data-ttu-id="9417a-110">SQL Server 유틸리티에서 전역 리소스 사용률 정책 수정</span><span class="sxs-lookup"><span data-stu-id="9417a-110">Modify global resource utilization policies in a SQL Server Utility.</span></span>  
  
1.  <span data-ttu-id="9417a-111">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 UCP에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-111">Connect to the UCP in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="9417a-112">유틸리티 탐색기 탐색 창에서 **유틸리티 관리** 를 클릭하여 전역 모니터링 정책을 보거나 수정한 다음 유틸리티 탐색기 내용 창에서 **정책** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-112">In the Utility Explorer navigation pane, click **Utility Administration** to view or modify global monitoring policies, then click the **Policy** tab in the Utility Explorer content pane.</span></span>  
  
3.  <span data-ttu-id="9417a-113">유틸리티 탐색기 내용 창에서 화살표나 정책 설명을 클릭하여 **전역 데이터 계층 모니터링 정책 설정** 또는 **전역 관리되는 인스턴스 모니터링 정책 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-113">In the Utility Explorer content pane, select **Set global data-tier monitoring policies** or **Set global managed instance monitoring policies** by clicking on the arrow or the policy description.</span></span>  
  
4.  <span data-ttu-id="9417a-114">정책 설명 오른쪽에 있는 컨트롤을 사용하여 미달 사용 또는 초과 사용 정책 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-114">Use the controls on the right side of the policy descriptions to set underutilization or overutilization policy thresholds.</span></span>  
  
5.  <span data-ttu-id="9417a-115">필요에 따라 **적용**, **삭제**또는 **기본값 복원** 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-115">Use the **Apply**, **Discard**, or **Restore Default** buttons as needed.</span></span> <span data-ttu-id="9417a-116">정책 변경이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 대시보드와 목록 뷰 세부 정보에 전파되고 표시되려면 최대 15분이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-116">The policy change can take up to 15 minutes to propagate back to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard and list view details.</span></span>  
  
6.  <span data-ttu-id="9417a-117">데이터를 새로 고치려면 유틸리티 탐색기 탐색 창에서 **유틸리티 관리** 노드를 마우스 오른쪽 단추로 클릭하고 **새로 고침**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-117">To refresh data, right-click on the **Utility Administration** node in the Utility Explorer navigation pane, and select **Refresh**.</span></span>  
  
#### <a name="modify-resource-health-policy-definitions-for-an-individual-data-tier-application-or-an-individual-managed-instance-of-sql-server-in-a-sql-server-utility"></a><span data-ttu-id="9417a-118">SQL Server 유틸리티에서 개별 데이터 계층 애플리케이션 또는 개별 SQL Server 관리되는 인스턴스의 리소스 상태 정책 정의 수정</span><span class="sxs-lookup"><span data-stu-id="9417a-118">Modify resource health policy definitions for an individual data-tier application or an individual managed instance of SQL Server in a SQL Server Utility</span></span>  
  
1.  <span data-ttu-id="9417a-119">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 UCP에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-119">Connect to the UCP in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="9417a-120">유틸리티 탐색기의 탐색 창에서 **배포된 데이터 계층 애플리케이션**을 클릭하거나 **관리되는 인스턴스**를 클릭하여 개별 데이터 계층 애플리케이션 또는 관리되는 인스턴스의 모니터링 정책을 보거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-120">In the Utility Explorer navigation pane, click **Deployed Date-tier Applications**, or click **Managed Instances**, to view or modify monitoring policies for an individual data-tier application or managed instance.</span></span>  
  
3.  <span data-ttu-id="9417a-121">유틸리티 탐색기 내용 창 목록 뷰에서 수정하려는 정책이 있는 데이터 계층 애플리케이션 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 이름을 클릭한 다음 **정책 정보** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-121">In the Utility Explorer content pane list view, click the data-tier application or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name whose policies you would like to modify, then click on the **Policy Details** tab.</span></span>  
  
4.  <span data-ttu-id="9417a-122">화살표나 정책 설명을 클릭하여 보거나 수정하려는 정책을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-122">Select the policy to view or modify by clicking on the arrow or the policy description.</span></span> <span data-ttu-id="9417a-123">전역 정책이 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-123">Global policies are selected by default.</span></span>  
  
5.  <span data-ttu-id="9417a-124">전역 정책을 무시하고 지정된 데이터 계층 애플리케이션의 개별 정책 정의를 구현하려면 라디오 단추를 **전역 정책 재정의** 로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-124">Select the radio button to **Override the global policy** to override global policies and implement an individual policy definition for the specified data-tier application.</span></span>  
  
6.  <span data-ttu-id="9417a-125">정책 설명 오른쪽에 있는 컨트롤을 사용하여 미달 사용 또는 초과 사용 정책 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-125">Use the controls on the right side of the policy description to set underutilization or overutilization policy thresholds.</span></span>  
  
7.  <span data-ttu-id="9417a-126">필요에 따라 **적용**, **삭제**또는 **기본값 복원** 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-126">Use the **Apply**, **Discard**, or **Restore Default** buttons as needed.</span></span> <span data-ttu-id="9417a-127">정책 변경이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 대시보드와 목록 뷰 세부 정보에 전파되고 표시되려면 최대 15분이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-127">The policy change can take up to 15 minutes to propagate back to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard and list view details.</span></span>  
  
8.  <span data-ttu-id="9417a-128">데이터를 새로 고치려면 유틸리티 탐색기 탐색 창에서 **배포된 데이터 계층 애플리케이션** 노드를 마우스 오른쪽 단추로 클릭하고 **새로 고침**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9417a-128">To refresh data, right-click on the **Deployed Data-tier Applications** node in the Utility Explorer navigation pane, and select **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9417a-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9417a-129">See Also</span></span>  
 <span data-ttu-id="9417a-130">[SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="9417a-130">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="9417a-131">리소스 상태 정책 결과 보기&#40;SQL Server 유틸리티&#41;</span><span class="sxs-lookup"><span data-stu-id="9417a-131">View Resource Health Policy Results &#40;SQL Server Utility&#41;</span></span>](view-resource-health-policy-results-sql-server-utility.md)  
  
  
