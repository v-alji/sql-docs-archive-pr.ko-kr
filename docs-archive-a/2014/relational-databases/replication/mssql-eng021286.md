---
title: MSSQL_ENG021286 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 592c788b563046e5949217c94006de2d4755f049
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730500"
---
# <a name="mssql_eng021286"></a><span data-ttu-id="beef6-102">MSSQL_ENG021286</span><span class="sxs-lookup"><span data-stu-id="beef6-102">MSSQL_ENG021286</span></span>
    
## <a name="message-details"></a><span data-ttu-id="beef6-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="beef6-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="beef6-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="beef6-104">Product Name</span></span>|<span data-ttu-id="beef6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="beef6-105">SQL Server</span></span>|  
|<span data-ttu-id="beef6-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="beef6-106">Event ID</span></span>|<span data-ttu-id="beef6-107">21286</span><span class="sxs-lookup"><span data-stu-id="beef6-107">21286</span></span>|  
|<span data-ttu-id="beef6-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="beef6-108">Event Source</span></span>|<span data-ttu-id="beef6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="beef6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="beef6-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="beef6-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="beef6-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="beef6-111">Symbolic Name</span></span>||  
|<span data-ttu-id="beef6-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="beef6-112">Message Text</span></span>|<span data-ttu-id="beef6-113">충돌 테이블 '%s'이(가) 없습니다.</span><span class="sxs-lookup"><span data-stu-id="beef6-113">Conflict table '%s' does not exist.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="beef6-114">설명</span><span class="sxs-lookup"><span data-stu-id="beef6-114">Explanation</span></span>  
 <span data-ttu-id="beef6-115">[sysmergearticles&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql)에 나열된 아티클에 대한 충돌 테이블이 실제로는 없는 경우 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="beef6-115">This error is raised if the conflict table for an article listed in [sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) does not actually exist.</span></span> <span data-ttu-id="beef6-116">병합 복제에 대해 게시된 테이블에서 열을 추가하거나 삭제해도 이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beef6-116">The error can occur when you attempt to add a column to or drop a column from a table published for merge replication.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="beef6-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="beef6-117">User Action</span></span>  
 <span data-ttu-id="beef6-118">충돌 테이블이 없는 데이터베이스에서 [DBCC CHECKDB&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)를 실행하여 데이터 일관성 문제가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="beef6-118">Execute [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database with the missing conflict table to verify there are no data consistency issues.</span></span>  
  
 <span data-ttu-id="beef6-119">구독자에 충돌 테이블이 없는 경우 해당 구독을 삭제하고 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="beef6-119">If the conflict table is missing on a Subscriber, drop the subscription and recreate it.</span></span> <span data-ttu-id="beef6-120">게시자에 충돌 테이블이 없는 경우 모든 구독을 삭제하고 해당 게시를 삭제한 다음 게시 및 모든 구독을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="beef6-120">If the conflict table is missing on a Publisher, drop all subscriptions, drop the publication, and then recreate the publication and all subscriptions.</span></span> <span data-ttu-id="beef6-121">자세한 내용은 [데이터 및 데이터베이스 개체 게시](publish/publish-data-and-database-objects.md) 및 [게시 구독](subscribe-to-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="beef6-121">For more information, see [Publish Data and Database Objects](publish/publish-data-and-database-objects.md) and [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beef6-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="beef6-122">See Also</span></span>  
 [<span data-ttu-id="beef6-123">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="beef6-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
