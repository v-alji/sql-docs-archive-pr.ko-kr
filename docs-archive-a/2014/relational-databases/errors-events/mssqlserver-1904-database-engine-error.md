---
title: MSSQLSERVER_1904 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 568cfe7499c041c2ee6a8ac3698b31698171bece
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650073"
---
# <a name="mssqlserver_1904"></a><span data-ttu-id="552d8-102">MSSQLSERVER_1904</span><span class="sxs-lookup"><span data-stu-id="552d8-102">MSSQLSERVER_1904</span></span>
    
## <a name="details"></a><span data-ttu-id="552d8-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="552d8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="552d8-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="552d8-104">Product Name</span></span>|<span data-ttu-id="552d8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="552d8-105">SQL Server</span></span>|  
|<span data-ttu-id="552d8-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="552d8-106">Event ID</span></span>|<span data-ttu-id="552d8-107">1904</span><span class="sxs-lookup"><span data-stu-id="552d8-107">1904</span></span>|  
|<span data-ttu-id="552d8-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="552d8-108">Event Source</span></span>|<span data-ttu-id="552d8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="552d8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="552d8-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="552d8-110">Component</span></span>|<span data-ttu-id="552d8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="552d8-111">SQLEngine</span></span>|  
|<span data-ttu-id="552d8-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="552d8-112">Symbolic Name</span></span>|<span data-ttu-id="552d8-113">KEYCOUNT</span><span class="sxs-lookup"><span data-stu-id="552d8-113">KEYCOUNT</span></span>|  
|<span data-ttu-id="552d8-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="552d8-114">Message Text</span></span>|<span data-ttu-id="552d8-115">테이블 '%.\*ls'의 %S_MSG '%.\*ls'에 있는 %S_MSG 키 목록에 %d개의 열 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552d8-115">The %S_MSG '%.\*ls' on table '%.\*ls' has %d column names in %S_MSG key list.</span></span> <span data-ttu-id="552d8-116">인덱스 또는 통계 키 열 목록의 최대 한계는 %d개입니다.</span><span class="sxs-lookup"><span data-stu-id="552d8-116">The maximum limit for index or statistics key column list is %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="552d8-117">설명</span><span class="sxs-lookup"><span data-stu-id="552d8-117">Explanation</span></span>  
 <span data-ttu-id="552d8-118">지정된 인덱스 또는 통계의 키 열 목록이 허용되는 최대 열 개수를 초과했습니다.</span><span class="sxs-lookup"><span data-stu-id="552d8-118">The key column list for the specified index or statistics exceeds the maximum number of columns allowed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="552d8-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="552d8-119">User Action</span></span>  
 <span data-ttu-id="552d8-120">지정된 최대 열 개수를 초과하지 않도록 키 열 목록을 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="552d8-120">Modify the key column list to include no more than the specified maximum number of columns.</span></span>  
  
 <span data-ttu-id="552d8-121">비클러스터형 인덱스의 경우 CREATE INDEX 문에 INCLUDE 절을 사용하여 인덱스에 열을 키가 아닌 열로 추가하는 것을 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="552d8-121">For nonclustered indexes, consider using the INCLUDE clause in the CREATE INDEX statement to add columns to the index as nonkey columns.</span></span> <span data-ttu-id="552d8-122">이 방법을 사용하면 키 열 개수가 현재 인덱스 크기 제한인 최대 16개를 초과하는 것을 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552d8-122">This method avoids exceeding the current index size limitation of a maximum of 16 key columns.</span></span> <span data-ttu-id="552d8-123">자세한 내용은 [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="552d8-123">For more information, see [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="552d8-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="552d8-124">See Also</span></span>  
 <span data-ttu-id="552d8-125">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="552d8-125">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="552d8-126">CREATE STATISTICS&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="552d8-126">CREATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-statistics-transact-sql)  
  
  
