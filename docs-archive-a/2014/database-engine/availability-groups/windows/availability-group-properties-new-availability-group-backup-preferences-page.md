---
title: '가용성 그룹 속성: 새 가용성 그룹 (백업 기본 설정 페이지) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroupproperties.backuppreferences.f1
helpviewer_keywords:
- read-only routing
ms.assetid: 65fff22d-5963-4a8c-8b31-fe9ab247a03e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7914d4b1d7af06bcaf4f3fd05a260138e3edf5fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646661"
---
# <a name="availability-group-properties-new-availability-group-backup-preferences-page"></a><span data-ttu-id="9db50-102">가용성 그룹 속성: 새 가용성 그룹(백업 기본 설정 페이지)</span><span class="sxs-lookup"><span data-stu-id="9db50-102">Availability Group Properties: New Availability Group (Backup Preferences Page)</span></span>
  <span data-ttu-id="9db50-103">이 대화 상자를 사용하여 선택한 가용성 그룹의 백업 기본 설정을 보고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-103">Use this dialog box to view and change the backup preferences of the selected availability group.</span></span>  
  
 <span data-ttu-id="9db50-104">**가용성 그룹 속성을 보려면**</span><span class="sxs-lookup"><span data-stu-id="9db50-104">**To view availability group properties**</span></span>  
  
-   [<span data-ttu-id="9db50-105">가용성 그룹 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9db50-105">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="9db50-106">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="9db50-106">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="where-should-backups-occur"></a><span data-ttu-id="9db50-107">백업 수행 위치</span><span class="sxs-lookup"><span data-stu-id="9db50-107">Where should backups occur?</span></span>  
 <span data-ttu-id="9db50-108">**보조 사용**</span><span class="sxs-lookup"><span data-stu-id="9db50-108">**Prefer Secondary**</span></span>  
 <span data-ttu-id="9db50-109">백업이 보조 복제본에서 수행되도록 지정합니다. 주 복제본이 유일한 온라인 복제본인 경우는 예외로,</span><span class="sxs-lookup"><span data-stu-id="9db50-109">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="9db50-110">이 경우에는 백업이 주 복제본에서 수행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-110">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="9db50-111">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-111">This is the default option.</span></span>  
  
 <span data-ttu-id="9db50-112">**보조만**</span><span class="sxs-lookup"><span data-stu-id="9db50-112">**Secondary only**</span></span>  
 <span data-ttu-id="9db50-113">백업이 주 복제본에서 수행되지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-113">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="9db50-114">주 복제본이 유일한 온라인 복제본인 경우에는 백업이 수행되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-114">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
 <span data-ttu-id="9db50-115">**주**</span><span class="sxs-lookup"><span data-stu-id="9db50-115">**Primary**</span></span>  
 <span data-ttu-id="9db50-116">백업이 항상 주 복제본에서 수행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-116">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="9db50-117">이 옵션은 백업이 보조 복제본에서 실행될 때 지원되지 않는 차등 백업 만들기와 같은 백업 기능이 필요한 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-117">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
 <span data-ttu-id="9db50-118">**임의의 복제본**</span><span class="sxs-lookup"><span data-stu-id="9db50-118">**Any Replica**</span></span>  
 <span data-ttu-id="9db50-119">백업을 수행할 복제본을 선택할 때 백업 작업에서 가용성 복제본의 역할을 무시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-119">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="9db50-120">백업 작업에서는 각 가용성 복제본의 작동 상태 및 연결 상태와 함께 백업 우선 순위 등의 기타 요인을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-120">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and connected state.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9db50-121">백업 기본 설정은 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-121">There is no enforcement of the backup-preference setting.</span></span> <span data-ttu-id="9db50-122">이 기본 설정의 해석은 지정된 가용성 그룹의 데이터베이스에 대한 백업 작업으로 스크립팅하는 논리(있는 경우)에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-122">The interpretation of this preference depends on the logic, if any, that you script into back jobs for the databases in a given availability group.</span></span> <span data-ttu-id="9db50-123">자세한 내용은 [활성 보조: 보조 복제본에 백업 (AlwaysOn 가용성 그룹)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9db50-123">For more information, see [Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
## <a name="replica-backup-priorities"></a><span data-ttu-id="9db50-124">복제본 백업 우선 순위</span><span class="sxs-lookup"><span data-stu-id="9db50-124">Replica backup priorities</span></span>  
 <span data-ttu-id="9db50-125">이 표는 가용성 그룹에 대한 복제본을 호스팅하는 각 서버 인스턴스의 현재 백업 우선 순위를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-125">This grid displays the current backup priority of each server instance that hosts a replica for the availability group.</span></span> <span data-ttu-id="9db50-126">이 표를 사용하여 하나 이상의 가용성 복제본에 대한 백업 우선 순위를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-126">Use this grid to change the backup priority of one or more availability replicas.</span></span>  
  
 <span data-ttu-id="9db50-127">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="9db50-127">**Server Instance**</span></span>  
 <span data-ttu-id="9db50-128">가용성 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-128">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span>  
  
 <span data-ttu-id="9db50-129">**백업 우선 순위(최저 = 1, 최고 = 100)**</span><span class="sxs-lookup"><span data-stu-id="9db50-129">**Backup Priority (Lowest=1, Highest=100)**</span></span>  
 <span data-ttu-id="9db50-130">이 복제본에 대한 백업을 수행하기 위한 우선 순위를 지정하며 동일한 가용성 그룹의 다른 복제본을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-130">Specifies your priority for performing backups on this replica relative to the other replicas in the same availability group.</span></span> <span data-ttu-id="9db50-131">이 값은 0에서 100  사이의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-131">The value is an integer in the range of 0..100.</span></span> <span data-ttu-id="9db50-132">1은 가장 낮은 우선 순위를 나타내고 100은 가장 높은 우선 순위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-132">1 indicates the lowest priority, and 100 indicates the highest priority.</span></span> <span data-ttu-id="9db50-133">**백업 우선 순위**가 1이면 현재 사용 가능한 더 높은 우선 순위의 가용성 복제본이 없는 경우에만 해당 가용성 복제본이 백업 수행을 위해 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-133">If **Backup Priority** = 1, the availability replica would be chosen for performing backups only if no higher priority availability replicas are currently available.</span></span>  
  
 <span data-ttu-id="9db50-134">**복제본 제외**</span><span class="sxs-lookup"><span data-stu-id="9db50-134">**Exclude Replica**</span></span>  
 <span data-ttu-id="9db50-135">백업 수행을 위해 이 가용성 백업을 선택하지 않으려는 경우에 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-135">Select if you never want this availability replica to be chosen for performing backups.</span></span> <span data-ttu-id="9db50-136">이 값은 예를 들어 백업을 장애 조치할 대상으로 사용하지 않을 원격 가용성 복제본의 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9db50-136">This is useful, for example, for a remote availability replica to which you never want backups to fail over.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db50-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9db50-137">See Also</span></span>  
 <span data-ttu-id="9db50-138">[활성 보조: 보조 복제본에 백업 (AlwaysOn 가용성 그룹)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="9db50-138">[Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="9db50-139">ALTER AVAILABILITY GROUP&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9db50-139">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
