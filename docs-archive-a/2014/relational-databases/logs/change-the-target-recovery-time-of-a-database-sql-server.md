---
title: 데이터베이스의 대상 복구 시간 변경(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: e466419a-d8a4-48f7-8d97-13a903ad6b15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c4331d2ade2819d172189a0de9daddecf3d9f6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649543"
---
# <a name="change-the-target-recovery-time-of-a-database-sql-server"></a><span data-ttu-id="7aa46-102">데이터베이스의 대상 복구 시간 변경(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7aa46-102">Change the Target Recovery Time of a Database (SQL Server)</span></span>
  <span data-ttu-id="7aa46-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]데이터베이스의 대상 복구 시간을 설정하거나 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-103">This topic describes how to set the change the target recovery time of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7aa46-104">기본적으로 대상 복구 시간은 0이고, 데이터베이스에서는 *복구 간격* 서버 옵션에 의해 제어되는 **자동 검사점** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-104">By default, the target recovery time is 0, and the database uses *automatic checkpoints* (which are controlled by the **recovery interval** server option).</span></span> <span data-ttu-id="7aa46-105">대상 복구 시간을 0보다 큰 값으로 설정하면 데이터베이스에서 *간접 검사점* 을 사용하고 이 데이터베이스에 대한 복구 시간의 상한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-105">Setting the target recovery time to greater than 0 causes the database to use the *indirect-checkpoints* and establishes an upper-bound on recovery time for this database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7aa46-106">장기 실행 트랜잭션으로 인해 UNDO 시간이 과도하게 길어지는 경우 주어진 데이터베이스에 대해 대상 복구 시간 설정에 지정된 상한이 초과될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-106">The upper-bound that is specified for a given database by its target recovery time setting could be exceeded if a long-running transaction causes excessive UNDO times.</span></span>  
  
-   <span data-ttu-id="7aa46-107">**시작하기 전 주의 사항:**  [제한 사항](#Restrictions), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="7aa46-107">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="7aa46-108">**대상 복구 시간을 변경하려면 다음을 사용합니다.**  [SQL Server Management Studio](#SSMSProcedure) 또는 [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="7aa46-108">**To change the target recovery time, using:**  [SQL Server Management Studio](#SSMSProcedure) or [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7aa46-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7aa46-109">Before You Begin</span></span>  
  
###  <a name="Restrictions"></a>  
  
> [!CAUTION]  
>  <span data-ttu-id="7aa46-110">간접 검사점이 구성된 데이터베이스의 온라인 트랜잭션 작업으로 인해 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-110">An online transactional workload on a database that is configured for indirect checkpoints could experience performance degradation.</span></span> <span data-ttu-id="7aa46-111">간접 검사점은 데이터베이스 복구가 대상 복구 시간 내에 완료되도록 더티 페이지 수가 특정 임계값보다 적은지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-111">Indirect checkpoints make sure that the number of dirty pages are below a certain threshold so that the database recovery completes within the target recovery time.</span></span> <span data-ttu-id="7aa46-112">복구 간격 구성 옵션은 더티 페이지 수를 사용하는 간접 검사점과 달리 트랜잭션 수를 사용하여 복구 시간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-112">The recovery interval configuration option uses the number of transactions to determine the recovery time as opposed to indirect checkpoints which makes use of number of dirty pages.</span></span> <span data-ttu-id="7aa46-113">많은 수의 DML 작업을 수신하는 데이터베이스에서 간접 검사점을 사용하도록 설정하는 경우 복구 수행에 필요한 시간이 데이터베이스의 대상 복구 시간 설정 내로 유지되도록 백그라운드 기록기가 더티 버퍼를 디스크로 적극적으로 플러시하기 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-113">When indirect checkpoints are enabled on a database receiving a large number of DML operations, the background writer can start aggressively flushing dirty buffers to disk to ensure that the time required to perform recovery is within the target recovery time set of the database.</span></span> <span data-ttu-id="7aa46-114">이로 인해 특정 시스템에서 추가 I/O 작업이 발생할 수 있으므로 디스크 하위 시스템이 I/O 임계값 위에서 또는 근처에서 작동하는 경우 성능 병목 현상에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-114">This can cause additional I/O activity on certain systems which can contribute to a performance bottleneck if the disk subsystem is operating above or nearing the I/O threshold.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7aa46-115">보안</span><span class="sxs-lookup"><span data-stu-id="7aa46-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7aa46-116">권한</span><span class="sxs-lookup"><span data-stu-id="7aa46-116">Permissions</span></span>  
 <span data-ttu-id="7aa46-117">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7aa46-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="7aa46-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="7aa46-119">**대상 복구 시간을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="7aa46-119">**To change the target recovery time**</span></span>  
  
1.  <span data-ttu-id="7aa46-120">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-120">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and expand that instance.</span></span>  
  
2.  <span data-ttu-id="7aa46-121">변경할 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **속성** 명령을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-121">Right-click the database you want to change, and click the **Properties** command.</span></span>  
  
3.  <span data-ttu-id="7aa46-122">**데이터베이스 속성** 대화 상자에서 **옵션** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-122">In the **Database Properties** dialog box, click the **Options** page.</span></span>  
  
4.  <span data-ttu-id="7aa46-123">**복구** 패널의 **대상 복구 시간(초)** 필드에서 이 데이터베이스에 대한 복구 시간의 상한으로 사용할 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-123">In the **Recovery** panel, in the **Target Recovery Time (Seconds)** field, specify the number of seconds that you want as the upper-bound on the recovery time for this database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7aa46-124">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="7aa46-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="7aa46-125">**대상 복구 시간을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="7aa46-125">**To change the target recovery time**</span></span>  
  
1.  <span data-ttu-id="7aa46-126">데이터베이스가 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-126">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the database resides.</span></span>  
  
2.  <span data-ttu-id="7aa46-127">다음 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)문을 다음과 같이 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-127">Use the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)statement, as follows:</span></span>  
  
     <span data-ttu-id="7aa46-128">TARGET_RECOVERY_TIME **=** _target_recovery_time_ { SECONDS | MINUTES }</span><span class="sxs-lookup"><span data-stu-id="7aa46-128">TARGET_RECOVERY_TIME **=**_target_recovery_time_ { SECONDS | MINUTES }</span></span>  
  
     <span data-ttu-id="7aa46-129">*target_recovery_time*</span><span class="sxs-lookup"><span data-stu-id="7aa46-129">*target_recovery_time*</span></span>  
     <span data-ttu-id="7aa46-130">0(기본값)보다 큰 경우 충돌 시 지정된 데이터베이스에 대한 복구 시간의 상한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-130">When greater than 0 (the default), specifies the upper-bound on the recovery time for the specified database in the event of a crash.</span></span>  
  
     <span data-ttu-id="7aa46-131">SECONDS</span><span class="sxs-lookup"><span data-stu-id="7aa46-131">SECONDS</span></span>  
     <span data-ttu-id="7aa46-132">*target_recovery_time* 이 초 단위로 표현됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-132">Indicates that *target_recovery_time* is expressed as the number of seconds.</span></span>  
  
     <span data-ttu-id="7aa46-133">MINUTES</span><span class="sxs-lookup"><span data-stu-id="7aa46-133">MINUTES</span></span>  
     <span data-ttu-id="7aa46-134">*target_recovery_time* 이 분 단위로 표현됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-134">Indicates that *target_recovery_time* is expressed as the number of minutes.</span></span>  
  
     <span data-ttu-id="7aa46-135">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 대상 복구 시간을 `60` 초로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7aa46-135">The following example sets the target recovery time of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to `60` seconds.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET TARGET_RECOVERY_TIME = 60 SECONDS;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7aa46-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7aa46-136">See Also</span></span>  
 <span data-ttu-id="7aa46-137">[데이터베이스 검사점&#40;SQL Server&#41;](database-checkpoints-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7aa46-137">[Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md) </span></span>  
 [<span data-ttu-id="7aa46-138">ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7aa46-138">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
