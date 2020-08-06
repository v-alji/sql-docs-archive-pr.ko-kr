---
title: MSSQL_REPL020011 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL020011 error
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 646f25740ebb007f8d04a89690d3b712781efcc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736208"
---
# <a name="mssql_repl020011"></a><span data-ttu-id="e3731-102">MSSQL_REPL020011</span><span class="sxs-lookup"><span data-stu-id="e3731-102">MSSQL_REPL020011</span></span>
    
## <a name="message-details"></a><span data-ttu-id="e3731-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="e3731-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3731-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e3731-104">Product Name</span></span>|<span data-ttu-id="e3731-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e3731-105">SQL Server</span></span>|  
|<span data-ttu-id="e3731-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e3731-106">Event ID</span></span>|<span data-ttu-id="e3731-107">20011</span><span class="sxs-lookup"><span data-stu-id="e3731-107">20011</span></span>|  
|<span data-ttu-id="e3731-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e3731-108">Event Source</span></span>|<span data-ttu-id="e3731-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e3731-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e3731-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e3731-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="e3731-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e3731-111">Symbolic Name</span></span>||  
|<span data-ttu-id="e3731-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e3731-112">Message Text</span></span>|<span data-ttu-id="e3731-113">'%2'에서 '%1'을(를) 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e3731-113">The process could not execute '%1' on '%2'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e3731-114">설명</span><span class="sxs-lookup"><span data-stu-id="e3731-114">Explanation</span></span>  
 <span data-ttu-id="e3731-115">로그 판독기 에이전트가 **sp_replcmds**(프로세스가 \<ServerName>에서 'sp_replcmds'를 실행할 수 없음) 또는 **sp_repldone**(프로세스가 \<ServerName>에서 'sp_repldone'를 실행할 수 없음)을 실행하는 경우와 같이 트랜잭션 복제 처리 중 여러 상황에서 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3731-115">This error can be raised in a number of circumstances during transactional replication processing, such as when the Log Reader Agent executes **sp_replcmds** (The process could not execute 'sp_replcmds' on \<ServerName>) or **sp_repldone** (The process could not execute 'sp_repldone' on \<ServerName>).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e3731-116">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e3731-116">User Action</span></span>  
 <span data-ttu-id="e3731-117">방금 백업에서 복원한 데이터베이스에서 이 오류가 발생한 경우에는 **sp_replrestart** 실행을 비롯해 백업 및 복원 설명서에서 간략하게 설명한 단계를 수행했는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3731-117">If this error is raised in a database that you have just restored from a backup, ensure you have followed the steps outlined in the backup and restore documentation, including executing **sp_replrestart** if appropriate.</span></span> <span data-ttu-id="e3731-118">자세한 내용은 [스냅샷 및 트랜잭션 복제의 백업 및 복원을 위한 전략](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e3731-118">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).</span></span>  
  
 <span data-ttu-id="e3731-119">이 오류는 내부 처리 오류입니다. 이 오류가 복원이 아닌 다른 상황에서 발생한 경우에는 일반적으로 복제를 제거하고 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3731-119">This error is an internal processing error and if it is raised in circumstances other than a restore, it typically indicates that replication must be removed and reconfigured.</span></span> <span data-ttu-id="e3731-120">복제를 제거할 수 없으면 고객 지원 담당자에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="e3731-120">If you cannot remove replication, contact customer support for assistance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3731-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3731-121">See Also</span></span>  
 <span data-ttu-id="e3731-122">[오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e3731-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="e3731-123">[sp_replcmds&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e3731-123">[sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) </span></span>  
 [<span data-ttu-id="e3731-124">sp_repldone&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e3731-124">sp_repldone &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql)  
  
  
