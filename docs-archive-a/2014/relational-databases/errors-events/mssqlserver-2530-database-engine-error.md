---
title: MSSQLSERVER_2530 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 30b57aae907d6f0acc4d1c0e6021bf936621c69e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646525"
---
# <a name="mssqlserver_2530"></a><span data-ttu-id="76701-102">MSSQLSERVER_2530</span><span class="sxs-lookup"><span data-stu-id="76701-102">MSSQLSERVER_2530</span></span>
    
## <a name="details"></a><span data-ttu-id="76701-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="76701-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76701-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="76701-104">Product Name</span></span>|<span data-ttu-id="76701-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="76701-105">SQL Server</span></span>|  
|<span data-ttu-id="76701-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="76701-106">Event ID</span></span>|<span data-ttu-id="76701-107">2530</span><span class="sxs-lookup"><span data-stu-id="76701-107">2530</span></span>|  
|<span data-ttu-id="76701-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="76701-108">Event Source</span></span>|<span data-ttu-id="76701-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="76701-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="76701-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="76701-110">Component</span></span>|<span data-ttu-id="76701-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="76701-111">SQLEngine</span></span>|  
|<span data-ttu-id="76701-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="76701-112">Symbolic Name</span></span>|<span data-ttu-id="76701-113">DBCC_INDEX_IS_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="76701-113">DBCC_INDEX_IS_OFFLINE</span></span>|  
|<span data-ttu-id="76701-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="76701-114">Message Text</span></span>|<span data-ttu-id="76701-115">테이블 "%.\*ls"의 인덱스 "%.\*ls"이(가) 비활성화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="76701-115">The index "%.\*ls" on table "%.\*ls" is disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="76701-116">설명</span><span class="sxs-lookup"><span data-stu-id="76701-116">Explanation</span></span>  
 <span data-ttu-id="76701-117">지정된 인덱스가 비활성화되어 있으므로 DBCC 문을 계속 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76701-117">The DBCC statement cannot proceed because the specified index is disabled.</span></span> <span data-ttu-id="76701-118">인덱스는 비활성화되면 다시 작성되거나 삭제 및 다시 생성될 때까지 비활성화된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="76701-118">After an index is disabled, it remains in a disabled state until it is rebuilt or dropped and re-created.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="76701-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="76701-119">User Action</span></span>  
  
1.  <span data-ttu-id="76701-120">다음 중 한 가지 방법을 사용하여 비활성화된 인덱스를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="76701-120">Enable the disabled index by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="76701-121">REBUILD 절과 함께 ALTER INDEX 문</span><span class="sxs-lookup"><span data-stu-id="76701-121">ALTER INDEX statement with the REBUILD clause</span></span>  
  
    -   <span data-ttu-id="76701-122">DROP_EXISTING 절과 함께 CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="76701-122">CREATE INDEX with the DROP_EXISTING clause</span></span>  
  
    -   <span data-ttu-id="76701-123">DBCC DBREINDEX</span><span class="sxs-lookup"><span data-stu-id="76701-123">DBCC DBREINDEX</span></span>  
  
2.  <span data-ttu-id="76701-124">해당 DBCC 문을 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="76701-124">Rerun the DBCC statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76701-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76701-125">See Also</span></span>  
 <span data-ttu-id="76701-126">[인덱스 및 제약 조건 사용](../indexes/enable-indexes-and-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="76701-126">[Enable Indexes and Constraints](../indexes/enable-indexes-and-constraints.md) </span></span>  
 <span data-ttu-id="76701-127">[ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="76701-127">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="76701-128">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="76701-128">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="76701-129">DBCC DBREINDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="76701-129">DBCC DBREINDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)  
  
  
