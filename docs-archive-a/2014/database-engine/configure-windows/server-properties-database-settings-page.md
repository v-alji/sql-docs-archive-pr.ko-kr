---
title: 서버 속성(데이터베이스 설정 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.databasesettings.f1
ms.assetid: 1cebdbd3-cbfd-4a02-bba6-a5addf4e3ada
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3beb2b6aa9a34982cccdfb252941c1c779a16121
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738703"
---
# <a name="server-properties-database-settings-page"></a><span data-ttu-id="341f3-102">서버 속성(데이터베이스 설정 페이지)</span><span class="sxs-lookup"><span data-stu-id="341f3-102">Server Properties (Database Settings Page)</span></span>
  <span data-ttu-id="341f3-103">이 페이지를 사용하여 데이터베이스 설정을 보거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-103">Use this page to view or modify your database settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="341f3-104">옵션</span><span class="sxs-lookup"><span data-stu-id="341f3-104">Options</span></span>  
 <span data-ttu-id="341f3-105">**기본 인덱스 채우기 비율**</span><span class="sxs-lookup"><span data-stu-id="341f3-105">**Default index fill factor**</span></span>  
 <span data-ttu-id="341f3-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 기존 데이터를 사용하여 새 인덱스를 만들 때 각 페이지를 채우는 비율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-106">Specifies how full [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should make each page when it creates a new index using existing data.</span></span> <span data-ttu-id="341f3-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 페이지를 채울 때 페이지를 분할하는 데 시간이 걸리므로 채우기 비율은 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-107">The fill factor affects performance because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must take time to split pages when they fill up.</span></span>  
  
 <span data-ttu-id="341f3-108">기본값은 0이고 유효한 값은 0에서 100 사이입니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-108">The default value is 0; valid values range from 0 through 100.</span></span> <span data-ttu-id="341f3-109">채우기 비율을 0이나 100으로 지정하면 완전히 채워진 데이터 페이지로 이루어진 클러스터형 인덱스와 완전히 채워진 리프 페이지로 이루어진 비클러스터형 인덱스가 만들어지지만 인덱스 트리 위쪽에 약간의 공간이 남습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-109">A fill factor of 0 or 100 creates clustered indexes with full data pages and nonclustered indexes with full leaf pages, but it leaves some space within the upper level of the index tree.</span></span> <span data-ttu-id="341f3-110">채우기 비율 값 0과 100은 모든 면에서 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-110">Fill factor values 0 and 100 are identical in all respects.</span></span>  
  
 <span data-ttu-id="341f3-111">채우기 비율 값을 작게 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 인덱스의 페이지를 가득 채우지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-111">Small fill factor values cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create indexes with pages that are not full.</span></span> <span data-ttu-id="341f3-112">이 경우 각 인덱스가 더 많은 스토리지 공간을 차지하지만 이후에 데이터를 삽입할 때 페이지를 분할할 필요가 없도록 여유 공간이 생깁니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-112">Each index takes more storage space, but there is more room for subsequent insertions without requiring page splits.</span></span>  
  
 <span data-ttu-id="341f3-113">**무기한 대기**</span><span class="sxs-lookup"><span data-stu-id="341f3-113">**Wait indefinitely**</span></span>  
 <span data-ttu-id="341f3-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 새 백업 테이프를 기다리는 동안 시간 제한을 두지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-114">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will never time out while waiting for a new backup tape.</span></span>  
  
 <span data-ttu-id="341f3-115">**한 번 시도**</span><span class="sxs-lookup"><span data-stu-id="341f3-115">**Try once**</span></span>  
 <span data-ttu-id="341f3-116">필요할 때 백업 테이프를 사용할 수 없으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 시간 초과가 발생하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-116">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will time out if a backup tape is not available when needed.</span></span>  
  
 <span data-ttu-id="341f3-117">**시도 시간(분)**</span><span class="sxs-lookup"><span data-stu-id="341f3-117">**Try for minute(s)**</span></span>  
 <span data-ttu-id="341f3-118">지정한 기간 내에 백업 테이프를 사용할 수 없으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 시간 초과가 발생하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-118">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will time out if a backup tape is not available within the period specified.</span></span>  
  
 <span data-ttu-id="341f3-119">**백업 미디어 기본 보존 기간(일)**</span><span class="sxs-lookup"><span data-stu-id="341f3-119">**Default backup media retention (in days)**</span></span>  
 <span data-ttu-id="341f3-120">데이터베이스 또는 트랜잭션 로그 백업에 각 백업 미디어를 사용한 후 각 백업 미디어를 보존하는 기간에 대한 시스템 차원 기본값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-120">Provides a system-wide default for the length of time to retain each backup medium after it has been used for a database or transaction log backup.</span></span> <span data-ttu-id="341f3-121">이 옵션은 지정된 기간이 경과하기 전에는 백업을 덮어쓰지 않게 합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-121">This option helps protect backups from being overwritten until the specified number of days has elapsed.</span></span>  
  
 <span data-ttu-id="341f3-122">**백업 압축**</span><span class="sxs-lookup"><span data-stu-id="341f3-122">**Compress backup**</span></span>  
 <span data-ttu-id="341f3-123">[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (이상 버전)에서 **백업 압축 기본값** 옵션의 현재 설정의 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-123">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or later versions), indicates the current setting of the **backup compression default** option.</span></span> <span data-ttu-id="341f3-124">이 옵션에 따라 다음과 같이 백업 압축의 서버 수준 기본값이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-124">This option determines the server-level default for compressing backups, as follows:</span></span>  
  
-   <span data-ttu-id="341f3-125">**백업 압축** 상자가 비어 있으면 새 백업은 기본적으로 압축되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-125">If the **Compress backup** box is blank, new backups are uncompressed by default.</span></span>  
  
-   <span data-ttu-id="341f3-126">**백업 압축** 상자가 선택되어 있으면 새 백업은 기본적으로 압축됩니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-126">If the **Compress backup** box is checked, new backups are compressed by default.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="341f3-127">기본적으로 압축하면 CPU 사용량이 크게 늘어나고 압축 프로세스로 사용되는 추가 CPU는 동시 작업에 악영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-127">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="341f3-128">따라서 CPU 사용량이 [리소스 관리자](../../relational-databases/resource-governor/resource-governor.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-128">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).</span></span> <span data-ttu-id="341f3-129">자세한 내용은 이 항목 뒷부분의 [Resource GovernoR을 사용하여 백업 압축을 통해 CPU 사용량 제한&#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-129">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
 <span data-ttu-id="341f3-130">**sysadmin** 또는 **serveradmin** 고정 서버 역할의 멤버인 경우 **백업 압축** 상자를 클릭하여 설정을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-130">If you are a member of the **sysadmin** or **serveradmin** fixed server role, you can change the setting by clicking the **Compress backup** box.</span></span>  
  
 <span data-ttu-id="341f3-131">자세한 내용은 [백업 압축 기본값 서버 구성 옵션 보기 또는 구성](view-or-configure-the-backup-compression-default-server-configuration-option.md) 및 [백업 압축&#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="341f3-131">For more information, see [View or Configure the backup compression default Server Configuration Option](view-or-configure-the-backup-compression-default-server-configuration-option.md) and [Backup Compression &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="341f3-132">**복구 간격(분)**</span><span class="sxs-lookup"><span data-stu-id="341f3-132">**Recovery interval (minutes)**</span></span>  
 <span data-ttu-id="341f3-133">데이터베이스당 최대 복구 시간을 분 단위로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-133">Sets the maximum number of minutes per database to recover databases.</span></span> <span data-ttu-id="341f3-134">기본값 0을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 자동으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-134">The default is 0, indicating automatic configuration by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="341f3-135">기본값을 설정하면 실제 운영 시 1분 이하의 복구 시간이 사용되고 활성 데이터베이스의 경우 약 1분 간격으로 검사점이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-135">In practice, this means a recovery time of less than one minute and a checkpoint approximately every one minute for active databases.</span></span> <span data-ttu-id="341f3-136">자세한 내용은 [Configure the recovery interval Server Configuration Option](configure-the-recovery-interval-server-configuration-option.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="341f3-136">For more information, see [Configure the recovery interval Server Configuration Option](configure-the-recovery-interval-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="341f3-137">**Data**</span><span class="sxs-lookup"><span data-stu-id="341f3-137">**Data**</span></span>  
 <span data-ttu-id="341f3-138">데이터 파일의 기본 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-138">Specifies the default location for data files.</span></span> <span data-ttu-id="341f3-139">새 기본 위치로 이동하려면 찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-139">Click the browse button to navigate to a new default location.</span></span> <span data-ttu-id="341f3-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 다시 시작할 때까지는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-140">Does not take effect until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="341f3-141">**Log**</span><span class="sxs-lookup"><span data-stu-id="341f3-141">**Log**</span></span>  
 <span data-ttu-id="341f3-142">로그 파일의 기본 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-142">Specifies the default location for log files.</span></span> <span data-ttu-id="341f3-143">새 기본 위치로 이동하려면 찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-143">Click the browse button to navigate to a new default location.</span></span> <span data-ttu-id="341f3-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 다시 시작할 때까지는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-144">Does not take effect until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="341f3-145">**구성 값**</span><span class="sxs-lookup"><span data-stu-id="341f3-145">**Configured Values**</span></span>  
 <span data-ttu-id="341f3-146">이 창의 옵션에 대해 구성된 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-146">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="341f3-147">이러한 값을 변경한 후에는 **실행 값** 을 클릭하여 변경 사항이 적용되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-147">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="341f3-148">변경 내용이 적용되지 않은 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-148">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restated first.</span></span>  
  
 <span data-ttu-id="341f3-149">**실행 값**</span><span class="sxs-lookup"><span data-stu-id="341f3-149">**Running Values**</span></span>  
 <span data-ttu-id="341f3-150">이 창의 옵션에 대한 현재 실행 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-150">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="341f3-151">이 값은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="341f3-151">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341f3-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="341f3-152">See Also</span></span>  
 <span data-ttu-id="341f3-153">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="341f3-153">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="341f3-154">인덱스의 채우기 비율 지정</span><span class="sxs-lookup"><span data-stu-id="341f3-154">Specify Fill Factor for an Index</span></span>](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)  
  
  
