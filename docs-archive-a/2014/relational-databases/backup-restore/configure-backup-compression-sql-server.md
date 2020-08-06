---
title: 백업 압축 구성(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 430905eb-d218-458c-bd48-aeee6fbb7446
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f70994eb64cb6a50b538fd87f03ce7ea2fafe857
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661184"
---
# <a name="configure-backup-compression-sql-server"></a><span data-ttu-id="b2694-102">백업 압축 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b2694-102">Configure Backup Compression (SQL Server)</span></span>
  <span data-ttu-id="b2694-103">설치 시 백업 압축은 기본적으로 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-103">At installation, backup compression is off by default.</span></span> <span data-ttu-id="b2694-104">백업 압축의 기본 동작은 **백업 압축 기본값** 옵션 서버 수준 구성 옵션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-104">The default behavior for backup compression is defined by the **backup compression default** Option server-level configuration option.</span></span> <span data-ttu-id="b2694-105">그러나 단일 백업을 만들거나 일련의 일상적인 백업을 예약할 때 서버 수준 기본값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-105">However, you can override the server-level default when creating a single backup or scheduling a series of routine backups.</span></span> <span data-ttu-id="b2694-106">서버 수준 기본값을 변경하려면 [백업 압축 기본값 서버 구성 옵션 보기 또는 구성](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2694-106">To change the server-level default, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>  
  
## <a name="override-the-backup-compression-default"></a><span data-ttu-id="b2694-107">백업 압축 기본값 재정의</span><span class="sxs-lookup"><span data-stu-id="b2694-107">Override the Backup Compression Default</span></span>  
 <span data-ttu-id="b2694-108">단일 백업, 백업 작업 또는 로그 전달 구성에 대한 백업 압축 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-108">You can change the backup compression behavior for an individual backup, backup job, or log shipping configuration.</span></span>  
  
-   **[!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
     <span data-ttu-id="b2694-109">백업을 만들 때 서버 백업 압축 기본값을 재정의하려면 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 문에서 WITH NO_COMPRESSION 또는 WITH COMPRESSION을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-109">To override the server backup-compression default when creating a backup, use either WITH NO_COMPRESSION or WITH COMPRESSION in you [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="b2694-110">로그 전달 구성의 경우 [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql)를 사용하여 로그 백업의 백업 압축 동작을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-110">For a log shipping configuration, you can control the backup compression behavior of log backups by using [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql).</span></span>  
  
-   **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
     <span data-ttu-id="b2694-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 백업 압축 기본 옵션을 보거나 구성하는 방법은 [백업 압축 기본값 서버 구성 옵션 보기 또는 구성](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2694-111">For information about how to view or configure the backup compression default option for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>  
  
     <span data-ttu-id="b2694-112">다음 대화 상자에서 **백업 압축** 또는 **백업 압축 안 함** 을 지정하여 백업을 만들 때 서버 백업 압축 기본값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-112">You can override the server backup-compression default when creating a backup by specifying **Compress backup** or **Do not compress backup** in any of the following dialog boxes:</span></span>  
  
    -   [<span data-ttu-id="b2694-113">데이터베이스 백업(옵션 페이지)</span><span class="sxs-lookup"><span data-stu-id="b2694-113">Back Up Database (Options Page)</span></span>](back-up-database-backup-options-page.md)  
  
         <span data-ttu-id="b2694-114">데이터베이스를 백업할 때 개별 데이터베이스, 파일 또는 로그 백업에 대한 백업 압축을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-114">When backing up a database, you can control backup compression for an individual database, file, or log backup.</span></span>  
  
    -   [<span data-ttu-id="b2694-115">유지 관리 계획 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="b2694-115">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
         <span data-ttu-id="b2694-116">유지 관리 계획 마법사를 사용하면 예약하는 각 전체 또는 차등 데이터베이스 백업이나 로그 백업의 압축을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-116">The Maintenance Plan Wizard enables you to control backup compression for each set full or differential database backups or log backups that you schedule.</span></span>  
  
    -   <span data-ttu-id="b2694-117">Integration Services(SSIS) [데이터베이스 백업 태스크](../../integration-services/control-flow/back-up-database-task.md)</span><span class="sxs-lookup"><span data-stu-id="b2694-117">Integration Services (SSIS) [Back Up Database task](../../integration-services/control-flow/back-up-database-task.md)</span></span>  
  
         <span data-ttu-id="b2694-118">단일 데이터베이스나 여러 데이터베이스를 백업하기 위한 패키지를 만들 때 백업 압축 동작을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-118">You can control the backup compression behavior when creating a package for backing up a single database or multiple databases.</span></span>  
  
    -   [<span data-ttu-id="b2694-119">로그 전달 트랜잭션 로그 백업 설정</span><span class="sxs-lookup"><span data-stu-id="b2694-119">Log Shipping Transaction Log Backup Settings</span></span>](../databases/log-shipping-transaction-log-backup-settings.md)  
  
         <span data-ttu-id="b2694-120">로그 백업의 백업 압축 동작을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2694-120">You can control the backup compression behavior of log backups.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="b2694-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2694-121">See Also</span></span>  
 [<span data-ttu-id="b2694-122">백업 압축&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b2694-122">Backup Compression &#40;SQL Server&#41;</span></span>](backup-compression-sql-server.md)  
  
  
