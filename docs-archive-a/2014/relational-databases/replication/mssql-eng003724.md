---
title: MSSQL_ENG003724 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dbfb68575c5ffa73276b3bbe1643381c3f0cc412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741799"
---
# <a name="mssql_eng003724"></a><span data-ttu-id="82f1a-102">MSSQL_ENG003724</span><span class="sxs-lookup"><span data-stu-id="82f1a-102">MSSQL_ENG003724</span></span>
    
## <a name="message-details"></a><span data-ttu-id="82f1a-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="82f1a-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82f1a-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="82f1a-104">Product Name</span></span>|<span data-ttu-id="82f1a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="82f1a-105">SQL Server</span></span>|  
|<span data-ttu-id="82f1a-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="82f1a-106">Event ID</span></span>|<span data-ttu-id="82f1a-107">3724</span><span class="sxs-lookup"><span data-stu-id="82f1a-107">3724</span></span>|  
|<span data-ttu-id="82f1a-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="82f1a-108">Event Source</span></span>|<span data-ttu-id="82f1a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="82f1a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="82f1a-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="82f1a-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="82f1a-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="82f1a-111">Symbolic Name</span></span>||  
|<span data-ttu-id="82f1a-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="82f1a-112">Message Text</span></span>|<span data-ttu-id="82f1a-113">%S_MSG '%.\*ls'은(는) 복제에 사용 중이므로 %S_MSG할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82f1a-113">Cannot %S_MSG the %S_MSG '%.\*ls' because it is being used for replication.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="82f1a-114">설명</span><span class="sxs-lookup"><span data-stu-id="82f1a-114">Explanation</span></span>  
 <span data-ttu-id="82f1a-115">데이터베이스의 개체가 복제되면 **sysarticles** 시스템 테이블(스냅샷 및 트랜잭션 게시의 경우) 또는 **sysmergearticles** 시스템 테이블(병합 게시의 경우)에 복제된 상태로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82f1a-115">When objects in a database are replicated, they are marked as replicated in the system table **sysarticles** (for snapshot and transactional publications) or **sysmergearticles** (for merge publications).</span></span> <span data-ttu-id="82f1a-116">복제된 개체를 삭제하려고 하면 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82f1a-116">If you attempt drop a replicated object, this error is raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="82f1a-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="82f1a-117">User Action</span></span>  
 <span data-ttu-id="82f1a-118">데이터베이스 개체를 삭제하기 전에 복제되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="82f1a-118">Ensure the database object is not replicated before attempting to drop it.</span></span> <span data-ttu-id="82f1a-119">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="82f1a-119">For example:</span></span>  
  
-   <span data-ttu-id="82f1a-120">게시 데이터베이스에서 오류가 발생한 경우 개체를 삭제하기 전에 게시에서 해당 아티클을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="82f1a-120">If the error occurs in the publication database, drop the article from the publication before dropping the object.</span></span> <span data-ttu-id="82f1a-121">자세한 내용은 [기존 게시에 대한 아티클 추가 및 삭제](publish/add-articles-to-and-drop-articles-from-existing-publications.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82f1a-121">For more information, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
-   <span data-ttu-id="82f1a-122">구독 데이터베이스에서 오류가 발생한 경우 개체를 삭제하기 전에 해당 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="82f1a-122">If the error occurs in the subscription database, drop the subscription before dropping the object.</span></span> <span data-ttu-id="82f1a-123">자세한 내용은 [게시 구독](subscribe-to-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82f1a-123">For more information, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="82f1a-124">트랜잭션 게시에 대한 구독의 경우 전체 게시 대신 개별 아티클에 대한 구독을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82f1a-124">For subscriptions to transactional publications, it is possible to drop the subscription to an individual article rather than the entire publication.</span></span> <span data-ttu-id="82f1a-125">자세한 내용은 [sp_procoption&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82f1a-125">For more information, see [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span>  
  
 <span data-ttu-id="82f1a-126">복제되지 않은 데이터베이스에서 오류가 발생한 경우 [sp_removedbreplication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)을 실행하여 데이터베이스의 개체가 복제된 것으로 표시되지 않도록 하세요.</span><span class="sxs-lookup"><span data-stu-id="82f1a-126">If this error occurs in a database that is not replicated, execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to ensure objects in the database are not marked as replicated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f1a-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82f1a-127">See Also</span></span>  
 [<span data-ttu-id="82f1a-128">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="82f1a-128">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
