---
title: MSSQLSERVER_2546 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c1c5f64ca0daba413f2b71c05f5b8e57b2d55df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729512"
---
# <a name="mssqlserver_2546"></a><span data-ttu-id="e4710-102">MSSQLSERVER_2546</span><span class="sxs-lookup"><span data-stu-id="e4710-102">MSSQLSERVER_2546</span></span>
    
## <a name="details"></a><span data-ttu-id="e4710-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e4710-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e4710-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e4710-104">Product Name</span></span>|<span data-ttu-id="e4710-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e4710-105">SQL Server</span></span>|  
|<span data-ttu-id="e4710-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e4710-106">Event ID</span></span>|<span data-ttu-id="e4710-107">2546</span><span class="sxs-lookup"><span data-stu-id="e4710-107">2546</span></span>|  
|<span data-ttu-id="e4710-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e4710-108">Event Source</span></span>|<span data-ttu-id="e4710-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e4710-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e4710-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e4710-110">Component</span></span>|<span data-ttu-id="e4710-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e4710-111">SQLEngine</span></span>|  
|<span data-ttu-id="e4710-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e4710-112">Symbolic Name</span></span>|<span data-ttu-id="e4710-113">DBCC_INDEX_MARKED_DISABLED</span><span class="sxs-lookup"><span data-stu-id="e4710-113">DBCC_INDEX_MARKED_DISABLED</span></span>|  
|<span data-ttu-id="e4710-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e4710-114">Message Text</span></span>|<span data-ttu-id="e4710-115">테이블 'OBJECT_NAME'의 인덱스 'INDEX_NAME'이(가) 비활성화된 것으로 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e4710-115">Index 'INDEX_NAME' on table 'OBJECT_NAME' is marked as disabled.</span></span> <span data-ttu-id="e4710-116">인덱스를 다시 작성하여 온라인 상태로 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="e4710-116">Rebuild the index to bring it online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e4710-117">설명</span><span class="sxs-lookup"><span data-stu-id="e4710-117">Explanation</span></span>  
 <span data-ttu-id="e4710-118">지정된 인덱스가 오프라인이거나 비활성화된 것으로 표시되어</span><span class="sxs-lookup"><span data-stu-id="e4710-118">The specified index is marked as offline or is disabled.</span></span> <span data-ttu-id="e4710-119">검사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e4710-119">Therefore, this index cannot be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e4710-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e4710-120">User Action</span></span>  
 <span data-ttu-id="e4710-121">ALTER INDEX를 사용하여 인덱스를 다시 작성하십시오.</span><span class="sxs-lookup"><span data-stu-id="e4710-121">Rebuild the index by using ALTER INDEX.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4710-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4710-122">See Also</span></span>  
 <span data-ttu-id="e4710-123">[ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e4710-123">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 [<span data-ttu-id="e4710-124">인덱스 다시 구성 및 다시 작성</span><span class="sxs-lookup"><span data-stu-id="e4710-124">Reorganize and Rebuild Indexes</span></span>](../indexes/indexes.md)  
  
  
