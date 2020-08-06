---
title: 데이터베이스 백업(백업 옵션 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.options.f1
- swb.backupdatabase.options.f1
ms.assetid: df0ddcdb-c94e-472b-b786-469ae8117b93
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ffd527ba4334244c7fd4c5d4a73099093cb8520b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661200"
---
# <a name="back-up-database-backup-options-page"></a><span data-ttu-id="76619-102">데이터베이스 백업(백업 옵션 페이지)</span><span class="sxs-lookup"><span data-stu-id="76619-102">Back Up Database (Backup Options Page)</span></span>
  <span data-ttu-id="76619-103">**데이터베이스 백업** 대화 상자의 **백업 옵션** 페이지를 사용하여 데이터베이스 백업 옵션을 확인하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-103">Use the  **Backup Options** page of the **Back Up Database** dialog box to view or modify database backup options.</span></span>  
  
 <span data-ttu-id="76619-104">**SQL Server Management Studio를 사용하여 백업을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="76619-104">**To create a backup by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="76619-105">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="76619-105">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="76619-106">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="76619-106">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="76619-107">데이터베이스 유지 관리 계획을 정의하여 데이터베이스 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-107">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="76619-108">자세한 내용은 [유지 관리 계획](../maintenance-plans/maintenance-plans.md) 및 [유지 관리 계획 마법사 사용](../maintenance-plans/use-the-maintenance-plan-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76619-108">For more information, see [Maintenance Plans](../maintenance-plans/maintenance-plans.md) and [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76619-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 백업 태스크를 지정할 때 [!INCLUDE[tsql](../../includes/tsql-md.md)][스크립트](/sql/t-sql/statements/backup-transact-sql) 단추를 클릭한 다음 스크립트에 대한 대상을 선택하여 해당되는 **BACKUP** 스크립트를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-109">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
## <a name="options"></a><span data-ttu-id="76619-110">옵션</span><span class="sxs-lookup"><span data-stu-id="76619-110">Options</span></span>  
  
### <a name="backup-set"></a><span data-ttu-id="76619-111">백업 세트</span><span class="sxs-lookup"><span data-stu-id="76619-111">Backup set</span></span>  
 <span data-ttu-id="76619-112">**백업 세트** 패널의 옵션을 사용하면 백업 작업으로 생성된 백업 세트에 대한 선택 가능한 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-112">The options of the **Backup set** panel allow for you to specify optional information about the backup set created by the back up operation.</span></span>  
  
 <span data-ttu-id="76619-113">**이름**</span><span class="sxs-lookup"><span data-stu-id="76619-113">**Name**</span></span>  
 <span data-ttu-id="76619-114">백업 세트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-114">Specify the backup set name.</span></span> <span data-ttu-id="76619-115">데이터베이스 이름과 백업 유형에 따라 기본 이름이 자동으로 제안됩니다.</span><span class="sxs-lookup"><span data-stu-id="76619-115">The system automatically suggests a default name based on the database name and the backup type.</span></span>  
  
 <span data-ttu-id="76619-116">백업 세트에 대한 자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76619-116">For information about backup sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="76619-117">**설명**</span><span class="sxs-lookup"><span data-stu-id="76619-117">**Description**</span></span>  
 <span data-ttu-id="76619-118">백업 세트에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-118">Enter a description of the backup set.</span></span>  
  
 <span data-ttu-id="76619-119">**백업 세트 만료 기한**</span><span class="sxs-lookup"><span data-stu-id="76619-119">**Backup set will expire**</span></span>  
 <span data-ttu-id="76619-120">다음 만료 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-120">Choose one of the following expiration options.</span></span> <span data-ttu-id="76619-121">**URL** 이 백업 대상으로 선택된 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-121">This option is disabled if **URL** is chosen as the backup destination.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76619-122">**이후**</span><span class="sxs-lookup"><span data-stu-id="76619-122">**After**</span></span>|<span data-ttu-id="76619-123">만료되기 전에 이 백업 세트를 덮어쓰지 않고 보존할 일 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-123">Specify the number of days that must elapse before this backup set expires and can be overwritten.</span></span> <span data-ttu-id="76619-124">이 값은 0일에서 99999일 사이일 수 있습니다. 값 0일은 백업 세트 기간 제한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-124">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span><br /><br /> <span data-ttu-id="76619-125">백업 만료 기본값은 **백업 미디어 기본 보존 기간(일)** 옵션에 설정된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="76619-125">The default value for backup expiration is the value set in the **Default backup media retention (in days)** option.</span></span> <span data-ttu-id="76619-126">이 페이지에 액세스하려면 개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택한 다음 **서버 속성** 대화 상자의 **데이터베이스 설정** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-126">To access this, right-click the server name in Object Explorer and select **Properties**; then click the **Database Settings** page of the **Server Properties** dialog box.</span></span>|  
|<span data-ttu-id="76619-127">**위치**</span><span class="sxs-lookup"><span data-stu-id="76619-127">**On**</span></span>|<span data-ttu-id="76619-128">백업 세트가 만료되어 덮어쓸 수 있는 특정 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-128">Specify a specific date when the backup set expires and can be overwritten.</span></span>|  
  
### <a name="compression"></a><span data-ttu-id="76619-129">압축</span><span class="sxs-lookup"><span data-stu-id="76619-129">Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="76619-130">(이상 버전)에서는 [백업 압축](backup-compression-sql-server.md)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-130">(or a later version) supports [backup compression](backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="76619-131">**백업 압축 설정**</span><span class="sxs-lookup"><span data-stu-id="76619-131">**Set backup compression**</span></span>  
 <span data-ttu-id="76619-132">[!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] (이상 버전)에서 다음 백업 압축 값 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-132">In [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] (or a later version), select one of the following backup compression values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76619-133">**기본 서버 설정 사용**</span><span class="sxs-lookup"><span data-stu-id="76619-133">**Use the default server setting**</span></span>|<span data-ttu-id="76619-134">서버 수준 기본값을 사용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-134">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="76619-135">이 기본값은 **백업 압축 기본값** 서버 구성 옵션으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="76619-135">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="76619-136">이 옵션의 현재 설정을 확인하는 방법에 대한 자세한 내용은 [백업 압축 기본값 서버 구성 옵션 보기 또는 구성](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="76619-136">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="76619-137">**백업 압축**</span><span class="sxs-lookup"><span data-stu-id="76619-137">**Compress backup**</span></span>|<span data-ttu-id="76619-138">서버 수준 기본값에 관계없이 백업을 압축하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-138">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="76619-139">**\*\* 중요 \*\*** 기본적으로 압축하면 CPU 사용량이 크게 늘어나고 압축 프로세스로 사용되는 추가 CPU는 동시 작업에 악영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-139">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="76619-140">따라서 CPU 사용량이 [리소스 관리자](../resource-governor/resource-governor.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-140">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="76619-141">자세한 내용은 이 항목 뒷부분의 [Resource GovernoR을 사용하여 백업 압축을 통해 CPU 사용량 제한&#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)에 의해 제한되는 세션에서 우선 순위가 낮은 압축 백업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-141">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="76619-142">**백업 압축 안 함**</span><span class="sxs-lookup"><span data-stu-id="76619-142">**Do not compress backup**</span></span>|<span data-ttu-id="76619-143">서버 수준 기본값에 관계없이 압축되지 않은 백업을 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-143">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
### <a name="encryption"></a><span data-ttu-id="76619-144">암호화</span><span class="sxs-lookup"><span data-stu-id="76619-144">Encryption</span></span>  
 <span data-ttu-id="76619-145">암호화된 백업을 만들려면 **백업 암호화** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-145">To create an encrypted backup, check the **Encrypt backup** check box.</span></span> <span data-ttu-id="76619-146">암호화 단계에 사용할 암호화 알고리즘을 선택하고 기존 인증서 또는 비대칭 키 목록의 인증서 또는 비대칭 키를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="76619-146">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="76619-147">사용 가능한 암호화 알고리즘은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-147">The available algorithms for encryption are:</span></span>  
  
-   <span data-ttu-id="76619-148">AES 128</span><span class="sxs-lookup"><span data-stu-id="76619-148">AES 128</span></span>  
  
-   <span data-ttu-id="76619-149">AES 192</span><span class="sxs-lookup"><span data-stu-id="76619-149">AES 192</span></span>  
  
-   <span data-ttu-id="76619-150">AES 256</span><span class="sxs-lookup"><span data-stu-id="76619-150">AES 256</span></span>  
  
-   <span data-ttu-id="76619-151">Triple DES</span><span class="sxs-lookup"><span data-stu-id="76619-151">Triple DES</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="76619-152">기존 백업 세트에 추가하도록 선택한 경우 암호화 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-152">The encryption option is disabled if you selected to append to existing backup set.</span></span>  
>   
>  <span data-ttu-id="76619-153">인증서나 키를 백업하고 암호화한 백업과 다른 위치에 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="76619-153">It is recommended practice to back up your certificate or keys and store them in a different location than the backup you encrypted.</span></span>  
>   
>  <span data-ttu-id="76619-154">EKM(Extensible Key Management)에 있는 키만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="76619-154">Only keys residing in the Extensible Key Management (EKM) are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76619-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76619-155">See Also</span></span>  
 <span data-ttu-id="76619-156">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="76619-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="76619-157">[트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="76619-157">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="76619-158">[파일 및 파일 그룹 백업&#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="76619-158">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 [<span data-ttu-id="76619-159">데이터베이스가 손상된 경우 트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="76619-159">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
  
