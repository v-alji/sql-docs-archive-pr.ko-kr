---
title: DQS 데이터베이스 백업 및 복원 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 489664d8c64a99d1ea4dcec79b93e5b01b28f649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647268"
---
# <a name="backing-up-and-restoring-dqs-databases"></a><span data-ttu-id="62d6f-102">DQS 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="62d6f-102">Backing Up and Restoring DQS Databases</span></span>
  <span data-ttu-id="62d6f-103">이 항목에서는 DQS 데이터베이스를 백업 및 복원하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-103">This topic describes how to back up and restore the DQS databases.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="62d6f-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="62d6f-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="62d6f-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="62d6f-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="62d6f-106">DQS 서버 설치 중에 제공한 데이터베이스 마스터 키에 대한 암호를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-106">You must know or remember the password for the database master key that you provided during the DQS server installation.</span></span>  
  
-   <span data-ttu-id="62d6f-107">DQS에서 실행 중인 작업이나 프로세스가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-107">Ensure that there are no running activities or processes in DQS.</span></span> <span data-ttu-id="62d6f-108">이는 **작업 모니터링** 화면을 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-108">This can be verified using the **Activity Monitoring** screen.</span></span> <span data-ttu-id="62d6f-109">이 화면을 사용하는 방법은 [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62d6f-109">For detailed information about working in this screen, see [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).</span></span>  
  
-   <span data-ttu-id="62d6f-110">DQS 서버에 로그온한 사용자가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-110">Ensure that there are no users logged on the DQS server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="62d6f-111">보안</span><span class="sxs-lookup"><span data-stu-id="62d6f-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="62d6f-112">권한</span><span class="sxs-lookup"><span data-stu-id="62d6f-112">Permissions</span></span>  
  
-   <span data-ttu-id="62d6f-113">백업 및 복원 작업을 수행하려면 Windows 사용자 계정이 SQL Server 인스턴스에서 sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance to perform the backup and restore operations.</span></span>  
  
-   <span data-ttu-id="62d6f-114">DQS에서 실행 중인 작업을 종료하거나 실행 중인 프로세스를 중지하려면 DQS_MAIN 데이터베이스에 대한 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-114">You must have the dqs_administrator role on the DQS_MAIN database to terminate any running activities or stop any running processes in DQS.</span></span>  
  
##  <a name="backup-and-restore-dqs-databases"></a><a name="BackupRestore"></a><span data-ttu-id="62d6f-115">DQS 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="62d6f-115">Backup and Restore DQS Databases</span></span>  
  
1.  <span data-ttu-id="62d6f-116">Microsoft SQL Server Management Studio를 시작하고 적합한 SQL Server 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-116">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="62d6f-117">개체 탐색기에서 **데이터베이스** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-117">In Object Explorer, expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="62d6f-118">DQS_STAGING_DATA 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-118">Back up the DQS_STAGING_DATA database.</span></span> <span data-ttu-id="62d6f-119">SQL Server 데이터베이스 백업에 대한 단계별 지침은 [전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62d6f-119">For step-by-step instructions for backing a SQL Server database, see [Create a Full Database Backup &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="62d6f-120">DQS_PROJECTS 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-120">Back up the DQS_PROJECTS database.</span></span>  
  
5.  <span data-ttu-id="62d6f-121">DQS_MAIN 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-121">Back up the DQS_MAIN database.</span></span>  
  
6.  <span data-ttu-id="62d6f-122">SQL Server의 현재 인스턴스에 대한 연결을 끊고 이러한 데이터베이스를 복원할 SQL Server 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-122">Disconnect from the current instance of SQL Server, and connect to the SQL Server instance where you want to restore these databases.</span></span>  
  
7.  <span data-ttu-id="62d6f-123">DQS_MAIN 데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-123">Restore DQS_MAIN database.</span></span> <span data-ttu-id="62d6f-124">SQL Server 데이터베이스를 복원 하는 방법에 대 한 단계별 지침은 [데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="62d6f-124">For step-by-step instructions to restore a SQL Server database, see [Restore a Database Backup &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).</span></span>  
  
8.  <span data-ttu-id="62d6f-125">DQS_PROJECTS 데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-125">Restore the DQS_PROJECTS database.</span></span>  
  
9. <span data-ttu-id="62d6f-126">DQS_STAGING_DATA 데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-126">Restore the DQS_STAGING_DATA database.</span></span>  
  
10. <span data-ttu-id="62d6f-127">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-127">In Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
11. <span data-ttu-id="62d6f-128">쿼리 편집기 창에서 다음 SQL 문을 복사 하 고를 *\<PASSWORD>* DQS 설치 중에 데이터베이스 마스터 키에 대해 제공한 암호로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-128">In the Query Editor window, copy the following SQL statements, and replace *\<PASSWORD>* with the password that you provided during the DQS installation for the database master key:</span></span>  
  
    ```sql  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
    ```  
  
12. <span data-ttu-id="62d6f-129">F5 키를 눌러 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-129">Press F5 to execute the statements.</span></span> <span data-ttu-id="62d6f-130">**결과** 창에서 문이 성공적으로 실행되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="62d6f-130">Check the **Results** pane to verify that the statements have executed successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d6f-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62d6f-131">See Also</span></span>  
 [<span data-ttu-id="62d6f-132">Manage DQS Databases</span><span class="sxs-lookup"><span data-stu-id="62d6f-132">Manage DQS Databases</span></span>](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
