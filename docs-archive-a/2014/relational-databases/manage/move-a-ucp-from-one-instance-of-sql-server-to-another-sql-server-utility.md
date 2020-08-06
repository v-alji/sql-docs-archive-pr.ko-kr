---
title: UCP를 한 SQL Server 인스턴스에서 다른 인스턴스로 이동(SQL Server 유틸리티) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b402fd9e-0bea-4c38-a371-6ed7fea12e96
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2cf17a79c9a1bb1bd7e86e1ecb36ef671414fb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650960"
---
# <a name="move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility"></a><span data-ttu-id="6f6cd-102">UCP를 한 SQL Server 인스턴스에서 다른 인스턴스로 이동(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="6f6cd-102">Move a UCP from One Instance of SQL Server to Another (SQL Server Utility)</span></span>
  <span data-ttu-id="6f6cd-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 UCP(유틸리티 제어 지점)를 한 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]인스턴스에서 다른 인스턴스로 이동하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-103">This topic describes how to move a utility control point (UCP) from one instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to another in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6f6cd-104">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6f6cd-104">Using SQL Server Management Studio</span></span>  
  
#### <a name="move-a-ucp-from-one-instance-of-sql-server-to-another"></a><span data-ttu-id="6f6cd-105">UCP를 한 SQL Server 인스턴스에서 다른 인스턴스로 이동하려면</span><span class="sxs-lookup"><span data-stu-id="6f6cd-105">Move a UCP from one instance of SQL Server to another.</span></span>  
  
1.  <span data-ttu-id="6f6cd-106">UCP의 새 호스트 인스턴스가 될 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 새 UCP를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-106">Create a new UCP on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that will be the new host instance of the UCP.</span></span> <span data-ttu-id="6f6cd-107">자세한 내용은 [SQL Server 유틸리티 제어 지점 만들기&#40;SQL Server 유틸리티&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-107">For more information, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span>  
  
2.  <span data-ttu-id="6f6cd-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 중 기본이 아닌 정책 설정이 지정된 항목이 있으면 새 UCP에서 그대로 설정할 수 있도록 정책 임계값을 기록하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-108">If non-default policy settings have been set for any instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, make note of the policy thresholds so that you can re-establish them on the new UCP.</span></span> <span data-ttu-id="6f6cd-109">새 UCP에 인스턴스가 추가될 때는 기본 정책이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-109">Default policies are applied when instances are added to the new UCP.</span></span> <span data-ttu-id="6f6cd-110">기본 정책이 사용될 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 목록 뷰의 **정책 유형** 열에 **전역** 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-110">If default policies are in effect, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility list view displays **Global** in the **Policy Type** column.</span></span>  
  
3.  <span data-ttu-id="6f6cd-111">이전 UCP에서 모든 관리되는 인스턴스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-111">Remove all managed instances from the old UCP.</span></span> <span data-ttu-id="6f6cd-112">자세한 내용은 [SQL Server 유틸리티에서 SQL Server 인스턴스 제거](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-112">For more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
4.  <span data-ttu-id="6f6cd-113">이전 UCP에서 UMDW(유틸리티 관리 데이터 웨어하우스)를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-113">Back up the utility management data warehouse (UMDW) from the old UCP.</span></span> <span data-ttu-id="6f6cd-114">파일 이름은 Sysutility_mdw_\<GUID>_DATA이며 데이터베이스 기본 위치는 \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\입니다. 여기서 \<System drive>는 일반적으로 C:\ 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-114">The filename is Sysutility_mdw_\<GUID>_DATA, and the database default location is \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="6f6cd-115">자세한 내용은 [백업 및 복원으로 데이터베이스 복사](../databases/copy-databases-with-backup-and-restore.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-115">For more information, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
5.  <span data-ttu-id="6f6cd-116">UMDW 백업을 새 UCP로 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-116">Restore the backup of the UMDW to the new UCP.</span></span> <span data-ttu-id="6f6cd-117">자세한 내용은 [백업 및 복원으로 데이터베이스 복사](../databases/copy-databases-with-backup-and-restore.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-117">For more information, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
6.  <span data-ttu-id="6f6cd-118">인스턴스를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 관리할 수 있도록 새 UCP에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-118">Enroll instances into the new UCP to make them managed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="6f6cd-119">자세한 내용은 [SQL Server 인스턴스 등록&#40;SQL Server 유틸리티&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-119">For more information, see [Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md).</span></span>  
  
7.  <span data-ttu-id="6f6cd-120">필요한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스에 대한 사용자 지정 정책 정의를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-120">Implement custom policy definitions for the managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], as necessary.</span></span>  
  
8.  <span data-ttu-id="6f6cd-121">데이터 수집 및 집계 작업이 완료될 때까지 약 1시간 동안 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-121">Wait approximately 1 hour for data collection and aggregation operations to complete.</span></span>  
  
9. <span data-ttu-id="6f6cd-122">데이터를 새로 고치려면 **유틸리티 탐색기**에서 **관리되는 인스턴스** 노드를 마우스 오른쪽 단추로 클릭하고 **새로 고침**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-122">To refresh data, right-click the **Managed Instances** node in **Utility Explorer**, then select **Refresh**.</span></span> <span data-ttu-id="6f6cd-123">목록 뷰 데이터가 **유틸리티 탐색기** 내용 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-123">List view data are displayed in the **Utility Explorer** content pane.</span></span> <span data-ttu-id="6f6cd-124">자세한 내용은 [리소스 상태 정책 결과 보기&#40;SQL Server 유틸리티&#41;](view-resource-health-policy-results-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6cd-124">For more information, see [View Resource Health Policy Results &#40;SQL Server Utility&#41;](view-resource-health-policy-results-sql-server-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6cd-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f6cd-125">See Also</span></span>  
 <span data-ttu-id="6f6cd-126">[SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="6f6cd-126">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="6f6cd-127">SQL Server 인스턴스 등록&#40;SQL Server 유틸리티&#41;</span><span class="sxs-lookup"><span data-stu-id="6f6cd-127">Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;</span></span>](enroll-an-instance-of-sql-server-sql-server-utility.md)  
  
  
