---
title: MSSQL_ENG004929 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b202b28eabe1feb1ed180bda0d58d2e84c7d10d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646363"
---
# <a name="mssql_eng004929"></a><span data-ttu-id="1a5df-102">MSSQL_ENG004929</span><span class="sxs-lookup"><span data-stu-id="1a5df-102">MSSQL_ENG004929</span></span>
    
## <a name="message-details"></a><span data-ttu-id="1a5df-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="1a5df-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a5df-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1a5df-104">Product Name</span></span>|<span data-ttu-id="1a5df-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1a5df-105">SQL Server</span></span>|  
|<span data-ttu-id="1a5df-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1a5df-106">Event ID</span></span>|<span data-ttu-id="1a5df-107">4929</span><span class="sxs-lookup"><span data-stu-id="1a5df-107">4929</span></span>|  
|<span data-ttu-id="1a5df-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1a5df-108">Event Source</span></span>|<span data-ttu-id="1a5df-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1a5df-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1a5df-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1a5df-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="1a5df-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1a5df-111">Symbolic Name</span></span>||  
|<span data-ttu-id="1a5df-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1a5df-112">Message Text</span></span>|<span data-ttu-id="1a5df-113">%S_MSG '%.\*ls'은(는) 복제용으로 게시 중이므로 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a5df-113">Cannot alter the %S_MSG '%.\*ls' because it is being published for replication.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1a5df-114">설명</span><span class="sxs-lookup"><span data-stu-id="1a5df-114">Explanation</span></span>  
 <span data-ttu-id="1a5df-115">이 오류는 일반적으로 트랜잭션 복제용으로 게시되는 테이블의 PRIMARY KEY 제약 조건을 삭제하려고 할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1a5df-115">This error typically occurs if you attempt to drop the primary key constraint on a table that is published for transactional replication.</span></span> <span data-ttu-id="1a5df-116">트랜잭션 복제를 사용하려면 게시된 각 테이블의 기본 키가 필요하므로 이 제약 조건은 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a5df-116">Transactional replication requires a primary key for each published table; therefore the constraint cannot be dropped.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1a5df-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1a5df-117">User Action</span></span>  
 <span data-ttu-id="1a5df-118">이 제약 조건을 삭제하려면 해당 테이블과 연결된 아티클을 먼저 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1a5df-118">To drop the constraint, first drop the article associated with the table.</span></span> <span data-ttu-id="1a5df-119">자세한 내용은 [기존 게시에 대한 아티클 추가 및 삭제](publish/add-articles-to-and-drop-articles-from-existing-publications.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a5df-119">For more information, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span> <span data-ttu-id="1a5df-120">복제되지 않은 데이터베이스에서 오류가 발생한 경우 [sp_removedbreplication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)을 실행하여 데이터베이스의 개체가 복제된 것으로 표시되지 않도록 하세요.</span><span class="sxs-lookup"><span data-stu-id="1a5df-120">If this error occurs in a database that is not replicated, execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to ensure objects in the database are not marked as replicated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5df-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a5df-121">See Also</span></span>  
 [<span data-ttu-id="1a5df-122">오류 및 이벤트 참조&#40;복제&#41;</span><span class="sxs-lookup"><span data-stu-id="1a5df-122">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
