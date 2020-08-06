---
title: 동기화 중 스크립트 실행(복제 Transact-SQL 프로그래밍) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4bc217ad160a0238cc4247600d65eb32f156071f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646897"
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a><span data-ttu-id="30bad-102">동기화 중 스크립트 실행(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="30bad-102">Execute Scripts During Synchronization (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="30bad-103">복제는 트랜잭션 게시 및 병합 게시 구독자의 요청 시 스크립트 실행을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-103">Replication supports on demand script execution for Subscribers to transactional and merge publications.</span></span> <span data-ttu-id="30bad-104">이 기능은 복제 작업 디렉터리에 스크립트를 복사한 다음 **sqlcmd** 를 사용하여 구독자에서 스크립트를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-104">This functionality copies the script to the replication working directory and then uses **sqlcmd** to apply the script at the Subscriber.</span></span> <span data-ttu-id="30bad-105">구독자의 스크립트를 트랜잭션 게시에 적용할 때 오류가 발생하면 기본적으로 배포 에이전트가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-105">By default, if there is a failure when applying the script for a subscription to a transactional publication, the Distribution Agent will stop.</span></span> <span data-ttu-id="30bad-106">복제 저장 프로시저를 사용하여 프로그래밍 방식으로 실행되도록 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-106">You can specify a [!INCLUDE[tsql](../../includes/tsql-md.md)] script to execute programmatically using replication stored procedures.</span></span>  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a><span data-ttu-id="30bad-107">스냅샷, 트랜잭션 또는 병합 게시의 모든 구독자에 대해 실행되도록 스크립트를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="30bad-107">To specify a script to run for all Subscribers to a snapshot, transactional or merge publication</span></span>  
  
1.  <span data-ttu-id="30bad-108">요청 시 실행되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 작성 및 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-108">Compose and test the [!INCLUDE[tsql](../../includes/tsql-md.md)] script that will be executed on demand.</span></span>  
  
2.  <span data-ttu-id="30bad-109">게시에 대한 스냅샷 에이전트가 액세스할 수 있는 위치에 스크립트 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-109">Save the script file to a location where it can be accessed by the Snapshot Agent for the publication.</span></span>  
  
3.  <span data-ttu-id="30bad-110">게시 데이터베이스의 게시자에서 [sp_addscriptexec&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-110">At the Publisher on the publication database, execute [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql).</span></span> <span data-ttu-id="30bad-111">\*\* \@ 게시**를 지정 하 고 \*\* \@ scriptfile**에 대해 2 단계에서 만든 전체 UNC 경로를 사용 하는 스크립트 파일의 이름을, \*\* \@ skiperror\*\*에 대해 다음 값 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-111">Specify **\@publication**, the name of the script file with full UNC path created in step 2 for **\@scriptfile**, and one of the following values for **\@skiperror**:</span></span>  
  
    -   <span data-ttu-id="30bad-112">**0** - 오류가 발생하면 스크립트 실행이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-112">**0** - the agent will stop executing the script if an error is encountered.</span></span>  
  
    -   <span data-ttu-id="30bad-113">**1** - 오류가 발생하면 로그에 기록되고 스크립트는 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-113">**1** - the agent will log errors and continue executing the script when errors are encountered.</span></span>  
  
4.  <span data-ttu-id="30bad-114">지정된 스크립트는 구독을 동기화하기 위해 다음에 에이전트가 실행될 때 각 구독자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="30bad-114">The specified script will be executed at each Subscriber when the agent next runs to synchronize the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30bad-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30bad-115">See Also</span></span>  
 [<span data-ttu-id="30bad-116">데이터 동기화</span><span class="sxs-lookup"><span data-stu-id="30bad-116">Synchronize Data</span></span>](synchronize-data.md)  
  
  
