---
title: 배포 데이터베이스에서 복제 된 명령 및 기타 정보 보기 (복제 Transact-sql 프로그래밍) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fb5850277d685f2ecf6471fa4bf9814579b2843e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741807"
---
# <a name="view-replicated-commands-and-other-information-in-the-distribution-database-replication-transact-sql-programming"></a><span data-ttu-id="9901c-102">배포 데이터베이스의 복제된 명령 및 기타 정보 보기(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="9901c-102">View Replicated Commands and Other Information in the Distribution Database (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="9901c-103">트랜잭션 복제를 사용하는 경우 트랜잭션 명령은 배포 에이전트에서 해당 명령을 모든 구독자에 전파하거나 구독자의 배포 에이전트에서 변경 내용을 끌어올 때까지 배포 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9901c-103">When using transactional replication, transaction commands are stored in the distribution database until the Distribution Agent propagates them to all Subscribers or a Distribution Agent at the Subscriber pulls the changes.</span></span> <span data-ttu-id="9901c-104">이와 같이 배포 데이터베이스에서 보류 중인 명령은 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9901c-104">These pending commands in the distribution database can be viewed programmatically using replication stored procedures.</span></span> <span data-ttu-id="9901c-105">자세한 내용은 [복제 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9901c-105">For more information, see [Replication Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql).</span></span>  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a><span data-ttu-id="9901c-106">배포 데이터베이스의 모든 트랜잭션 게시에서 복제된 명령을 보려면</span><span class="sxs-lookup"><span data-stu-id="9901c-106">To view replicated commands from all transactional publications in the distribution database</span></span>  
  
1.  <span data-ttu-id="9901c-107">배포 데이터베이스의 배포자에서 [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9901c-107">At the Distributor on the distribution database, execute [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql).</span></span>  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a><span data-ttu-id="9901c-108">트랜잭션 복제를 사용하여 게시된 특정 데이터베이스 또는 특정 아티클에서 배포 데이터베이스의 복제된 명령을 보려면</span><span class="sxs-lookup"><span data-stu-id="9901c-108">To view replicated commands in the distribution database from a specific article or from a specific database published using transactional replication</span></span>  
  
1.  <span data-ttu-id="9901c-109">(옵션) 게시 데이터베이스의 게시자에서 [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9901c-109">(Optional) At the Publisher on the publication database, execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql).</span></span> <span data-ttu-id="9901c-110">\*\* \@ 게시\*\* 및 \*\* \@ 아티클을\*\*지정 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9901c-110">Specify **\@publication** and **\@article**.</span></span> <span data-ttu-id="9901c-111">결과 집합의 **article id** 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9901c-111">Note the value of **article id** in the result set.</span></span>  
  
2.  <span data-ttu-id="9901c-112">배포 데이터베이스의 배포자에서 [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9901c-112">At the Distributor on the distribution database, execute [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql).</span></span> <span data-ttu-id="9901c-113">필드 \*\* \@ Article_id\*\*에 대해 2 단계의 문서 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9901c-113">(Optional) Specify the article ID from step 2 for **\@article_id**.</span></span> <span data-ttu-id="9901c-114">필드 \*\* \@ Publisher_database_id\*\*에 대 한 게시 데이터베이스의 ID를 지정 합니다 .이 ID는 [sys.debug](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 카탈로그 뷰의 **database_id** 열에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9901c-114">(Optional) Specify the ID of the publication database for **\@publisher_database_id**, which can be obtained from the **database_id** column in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9901c-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9901c-115">See Also</span></span>  
 [<span data-ttu-id="9901c-116">프로그래밍 방식으로 복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="9901c-116">Programmatically Monitor Replication</span></span>](../monitoring-replication.md)  
  
  
