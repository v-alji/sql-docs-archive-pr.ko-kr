---
title: MSSQLSERVER_601 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "601"
helpviewer_keywords:
- 601 (Database Engine error)
ms.assetid: 2039cc0a-9a43-4369-a04a-935e384388b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 459a983d72a91e628e8cc33636d3abd81998f1d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660620"
---
# <a name="mssqlserver_601"></a><span data-ttu-id="10b28-102">MSSQLSERVER_601</span><span class="sxs-lookup"><span data-stu-id="10b28-102">MSSQLSERVER_601</span></span>
    
## <a name="details"></a><span data-ttu-id="10b28-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="10b28-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10b28-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="10b28-104">Product Name</span></span>|<span data-ttu-id="10b28-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="10b28-105">SQL Server</span></span>|  
|<span data-ttu-id="10b28-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="10b28-106">Event ID</span></span>|<span data-ttu-id="10b28-107">601</span><span class="sxs-lookup"><span data-stu-id="10b28-107">601</span></span>|  
|<span data-ttu-id="10b28-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="10b28-108">Event Source</span></span>|<span data-ttu-id="10b28-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="10b28-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="10b28-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="10b28-110">Component</span></span>|<span data-ttu-id="10b28-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="10b28-111">SQLEngine</span></span>|  
|<span data-ttu-id="10b28-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="10b28-112">Symbolic Name</span></span>||  
|<span data-ttu-id="10b28-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="10b28-113">Message Text</span></span>|<span data-ttu-id="10b28-114">데이터 이동으로 인해 NOLOCK으로 계속 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10b28-114">Could not continue scan with NOLOCK due to data movement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="10b28-115">설명</span><span class="sxs-lookup"><span data-stu-id="10b28-115">Explanation</span></span>  
 <span data-ttu-id="10b28-116">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]이 다른 트랜잭션에 의해 업데이트 또는 삭제된 데이터를 읽으려 하므로 쿼리를 계속 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10b28-116">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot continue executing the query because it is trying to read data that was updated or deleted by another transaction.</span></span> <span data-ttu-id="10b28-117">쿼리에서 NOLOCK 잠금 힌트나 READ UNCOMMITTED 트랜잭션 격리 수준 중 하나를 사용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10b28-117">The query is using either the NOLOCK locking hint or the READ UNCOMMITTED transaction isolation level.</span></span>  
  
 <span data-ttu-id="10b28-118">일반적으로 다른 트랜잭션에 의해 변경된 데이터에 대한 액세스는 해당 데이터에 설정된 잠금으로 인해 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="10b28-118">Typically, access to data that is being changed by another transaction is denied because of locks put on the data.</span></span> <span data-ttu-id="10b28-119">그러나 NOLOCK 잠금 힌트 및 READ UNCOMMITTED 트랜잭션 격리 수준을 사용하면 다른 트랜잭션에 의해 잠긴 데이터를 쿼리가 읽을 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10b28-119">However, the NOLOCK locking hint and READ UNCOMMITTED transaction isolation level let a query read data that is locked by another transaction.</span></span> <span data-ttu-id="10b28-120">아직 커밋되지 않아 변경될 수 있는 값을 읽을 수 있으므로 이를 커밋되지 않은 읽기라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="10b28-120">This is referred to as a dirty read because you can read values that have not yet been committed and that are subject to change.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="10b28-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="10b28-121">User Action</span></span>  
 <span data-ttu-id="10b28-122">이 오류가 발생하면 쿼리가 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="10b28-122">This error cancels the query.</span></span> <span data-ttu-id="10b28-123">쿼리를 다시 전송하거나 NOLOCK 잠금 힌트를 제거하십시오.</span><span class="sxs-lookup"><span data-stu-id="10b28-123">Either resubmit the query or remove the NOLOCK locking hint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10b28-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10b28-124">See Also</span></span>  
 <span data-ttu-id="10b28-125">[MSSQLSERVER_605](mssqlserver-605-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="10b28-125">[MSSQLSERVER_605](mssqlserver-605-database-engine-error.md) </span></span>  
 <span data-ttu-id="10b28-126">[테이블 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span><span class="sxs-lookup"><span data-stu-id="10b28-126">[Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table) </span></span>  
 <span data-ttu-id="10b28-127">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="10b28-127">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="10b28-128">SET TRANSACTION ISOLATION LEVEL&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="10b28-128">SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)  
  
  
