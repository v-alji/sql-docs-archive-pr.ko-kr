---
title: AlwaysOn 가용성 그룹 (SQL Server)를 사용 하 여 암호화 된 데이터베이스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, AlwaysOn Availability Groups
- TDE, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91e717a896634a7df5a96253c51207831f142cff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647244"
---
# <a name="encrypted-databases-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="c2c8d-102">AlwaysOn 가용성 그룹이 있는 암호화된 데이터베이스(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c2c8d-102">Encrypted Databases with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="c2c8d-103">이 항목에는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]과 함께 현재 암호화되었거나 최근에 암호 해독된 데이터베이스 사용에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c8d-103">This topic contains information about the using currently encrypted or recently decrypted databases with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="c2c8d-104">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="c2c8d-104">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="c2c8d-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c2c8d-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="c2c8d-106">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c2c8d-106">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c2c8d-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c2c8d-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c2c8d-108">데이터가 암호화되었거나 심지어 DEK(데이터베이스 암호화 키)를 포함하는 경우 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 또는 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 를 사용하여 데이터베이스를 가용성 그룹에 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c8d-108">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="c2c8d-109">암호화된 데이터베이스가 암호 해독된 경우라도 해당 로그 백업에는 암호화된 데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c8d-109">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="c2c8d-110">이 경우 데이터베이스에서 전체 초기 데이터 동기화를 수행하면 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c8d-110">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="c2c8d-111">로그 복원 작업에는 DEK(데이터베이스 암호화 키)에서 사용된 인증서가 필요한데 이 인증서를 사용할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c2c8d-111">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="c2c8d-112">마법사를 사용하여 암호 해독된 데이터베이스를 가용성 그룹에 추가하기에 적합하도록 만들려면</span><span class="sxs-lookup"><span data-stu-id="c2c8d-112">To make a decrypted database eligible to add to an availability group using the wizard:</span></span>  
  
    1.  <span data-ttu-id="c2c8d-113">주 데이터베이스의 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c2c8d-113">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="c2c8d-114">주 데이터베이스의 전체 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c2c8d-114">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="c2c8d-115">보조 복제본을 호스팅하는 서버 인스턴스에서 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c8d-115">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="c2c8d-116">주 데이터베이스에서 새 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c2c8d-116">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="c2c8d-117">보조 데이터베이스에서 이 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c8d-117">Restore this log backup on the secondary database.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="c2c8d-118">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c2c8d-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="c2c8d-119">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c2c8d-119">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="c2c8d-120">가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c2c8d-120">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="c2c8d-121">가용성 그룹에 데이터베이스 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c2c8d-121">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="c2c8d-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2c8d-122">See Also</span></span>  
 <span data-ttu-id="c2c8d-123">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c2c8d-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="c2c8d-124">투명한 데이터 암호화&#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="c2c8d-124">Transparent Data Encryption &#40;TDE&#41;</span></span>](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
  
