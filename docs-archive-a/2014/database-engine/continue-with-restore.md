---
title: 복원 계속 Microsoft Docs
description: SQL Server에서 복원 계속 대화 상자를 사용 하 여 다음 백업 세트를 복원할지 여부를 나타냅니다.
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.continuerestore.f1
ms.assetid: 987ac05f-57c0-49a9-9903-9889717aae4f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c7a438ac7b8696d2f57bdf93ff86030cf607e682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740312"
---
# <a name="continue-with-restore"></a><span data-ttu-id="32556-103">복원 계속</span><span class="sxs-lookup"><span data-stu-id="32556-103">Continue with Restore</span></span>
  <span data-ttu-id="32556-104">**복원 계속** 대화 상자를 사용하여 다음 백업 세트를 복원할지 여부를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32556-104">Use the **Continue with Restore** dialog box to indicate whether you want to restore the next backup set.</span></span> <span data-ttu-id="32556-105">예를 들어 테이프를 바꾸기 위해 복원 작업을 지연하려면 계속할 준비가 될 때까지 기다렸다가 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="32556-105">To delay the restore operation, for example, to swap tapes, wait until you are ready to proceed before you click **OK**.</span></span>  
  
 <span data-ttu-id="32556-106">**아니요** 를 클릭하면 데이터베이스가 복원 중인 상태로 복원 시퀀스가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="32556-106">Clicking **No** terminates the restore sequence, leaving the database in the restoring state.</span></span> <span data-ttu-id="32556-107">나중에 복원을 계속하려면 **데이터베이스 복원** 작업이나 **트랜잭션 로그 복원** 태스크를 적절하게 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="32556-107">To continue with the restore later, use either the **Restore Database** or **Restore Transaction Log** task, as appropriate.</span></span>  
  
## <a name="options"></a><span data-ttu-id="32556-108">옵션</span><span class="sxs-lookup"><span data-stu-id="32556-108">Options</span></span>  
 <span data-ttu-id="32556-109">**미디어 세트**</span><span class="sxs-lookup"><span data-stu-id="32556-109">**Media set**</span></span>  
 <span data-ttu-id="32556-110">다음 미디어 세트 이름을 표시합니다(사용 가능한 경우).</span><span class="sxs-lookup"><span data-stu-id="32556-110">Displays the next media set name (if available).</span></span>  
  
 <span data-ttu-id="32556-111">**백업 세트**</span><span class="sxs-lookup"><span data-stu-id="32556-111">**Backup set**</span></span>  
 <span data-ttu-id="32556-112">백업 세트 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="32556-112">Displays the backup set name.</span></span>  
  
 <span data-ttu-id="32556-113">**백업 세트 설명**</span><span class="sxs-lookup"><span data-stu-id="32556-113">**Backup set description**</span></span>  
 <span data-ttu-id="32556-114">백업 세트에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="32556-114">Displays the backup set description.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32556-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32556-115">See Also</span></span>  
 <span data-ttu-id="32556-116">[백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="32556-116">[View the Contents of a Backup Tape or File &#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md) </span></span>  
 <span data-ttu-id="32556-117">[논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="32556-117">[View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md) </span></span>  
 <span data-ttu-id="32556-118">[데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="32556-118">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md) </span></span>  
 [<span data-ttu-id="32556-119">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32556-119">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
  
