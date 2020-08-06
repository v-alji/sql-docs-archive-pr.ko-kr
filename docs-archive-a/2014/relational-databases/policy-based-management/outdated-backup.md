---
title: 오래된 백업 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c6a944b08b15d591a9bbce47a0c0c6a8de3eb54a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652769"
---
# <a name="outdated-backup"></a><span data-ttu-id="30695-102">오래된 백업</span><span class="sxs-lookup"><span data-stu-id="30695-102">Outdated Backup</span></span>
  <span data-ttu-id="30695-103">이 규칙은 최근 데이터베이스 백업이 있는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="30695-103">This rule checks that a database has recent backups.</span></span> <span data-ttu-id="30695-104">여러 가지 오류로 인한 데이터 손실로부터 데이터베이스를 보호하기 위해서는 정기적인 백업을 예약하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="30695-104">Scheduling regular backups is important for protecting your databases against data loss from many different failures.</span></span> <span data-ttu-id="30695-105">적절한 데이터 백업 빈도는 데이터베이스의 복구 모델, 가능한 데이터 손실에 대한 비즈니스 요구 사항 및 데이터베이스 업데이트 빈도에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="30695-105">The appropriate frequency for backing up data depends on the recovery model of the database, on business requirements about potential data loss, and on how frequently the database is updated.</span></span> <span data-ttu-id="30695-106">자주 업데이트되는 데이터베이스의 경우 백업 사이의 작업 손실 가능성이 빠르게 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="30695-106">In a frequently updated database, the work-loss exposure increases fairly quickly between backups.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="30695-107">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="30695-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="30695-108">데이터 손실로부터 데이터베이스를 보호하는 데 충분한 빈도로 백업을 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="30695-108">We recommend that you perform backups frequently enough to protect databases against data loss.</span></span>  
  
 <span data-ttu-id="30695-109">단순 복구 모델과 전체 복구 모델 모두 데이터 백업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="30695-109">The simple recovery model and full recovery model both require data backups.</span></span> <span data-ttu-id="30695-110">두 복구 모델에서 모두 전체 백업을 보충하는 차등 백업을 통해 데이터 손실 위험을 효과적으로 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30695-110">For either recovery model, you can supplement your full backups with differential backups to efficiently reduce the risk of data loss.</span></span>  
  
 <span data-ttu-id="30695-111">전체 복구 모델을 사용하는 데이터베이스의 경우 로그 백업을 자주 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="30695-111">For a database that uses the full recovery model, we recommend that you take frequent log backups.</span></span> <span data-ttu-id="30695-112">매우 중요한 데이터가 포함된 프로덕션 데이터베이스의 경우 일반적으로 1분에서 15분 사이의 간격으로 로그 백업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="30695-112">For a production database that contains very important data, log backups would typically be taken every one to fifteen minutes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30695-113">백업 예약을 위해서는 데이터베이스 유지 관리 계획을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="30695-113">The recommended method for scheduling backups is a database maintenance plan.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="30695-114">참조 항목</span><span class="sxs-lookup"><span data-stu-id="30695-114">For More Information</span></span>  
 [<span data-ttu-id="30695-115">시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30695-115">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [<span data-ttu-id="30695-116">복구 모델&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30695-116">Recovery Models &#40;SQL Server&#41;</span></span>](../backup-restore/recovery-models-sql-server.md)  
  
 [<span data-ttu-id="30695-117">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30695-117">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 [<span data-ttu-id="30695-118">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30695-118">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
 [<span data-ttu-id="30695-119">유지 관리 계획</span><span class="sxs-lookup"><span data-stu-id="30695-119">Maintenance Plans</span></span>](../maintenance-plans/maintenance-plans.md)  
  
 [<span data-ttu-id="30695-120">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="30695-120">Transaction Log Backups &#40;SQL Server&#41;</span></span>](../backup-restore/transaction-log-backups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="30695-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30695-121">See Also</span></span>  
 [<span data-ttu-id="30695-122">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="30695-122">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
