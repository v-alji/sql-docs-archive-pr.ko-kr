---
title: MSSQLSERVER_2511 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23e91b0d64140329639cf57f3a336cd2eab8e4e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731632"
---
# <a name="mssqlserver_2511"></a><span data-ttu-id="49307-102">MSSQLSERVER_2511</span><span class="sxs-lookup"><span data-stu-id="49307-102">MSSQLSERVER_2511</span></span>
    
## <a name="details"></a><span data-ttu-id="49307-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="49307-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49307-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="49307-104">Product Name</span></span>|<span data-ttu-id="49307-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="49307-105">SQL Server</span></span>|  
|<span data-ttu-id="49307-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="49307-106">Event ID</span></span>|<span data-ttu-id="49307-107">2511</span><span class="sxs-lookup"><span data-stu-id="49307-107">2511</span></span>|  
|<span data-ttu-id="49307-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="49307-108">Event Source</span></span>|<span data-ttu-id="49307-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="49307-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="49307-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="49307-110">Component</span></span>|<span data-ttu-id="49307-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="49307-111">SQLEngine</span></span>|  
|<span data-ttu-id="49307-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="49307-112">Symbolic Name</span></span>|<span data-ttu-id="49307-113">DBCC_KEYS_OUT_OF_ORDER</span><span class="sxs-lookup"><span data-stu-id="49307-113">DBCC_KEYS_OUT_OF_ORDER</span></span>|  
|<span data-ttu-id="49307-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="49307-114">Message Text</span></span>|<span data-ttu-id="49307-115">테이블 오류: 개체 ID %d, 인덱스 ID %d, 파티션 ID %I64d, 할당 단위 ID %I64d(%.\*ls 유형).</span><span class="sxs-lookup"><span data-stu-id="49307-115">Table error: Object ID %d, index ID %d, partition ID %I64d, alloc unit ID %I64d (type %.\*ls).</span></span> <span data-ttu-id="49307-116">페이지 %S_PGID, 슬롯 %d 및 %d의 키가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="49307-116">Keys out of order on page %S_PGID, slots %d and %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="49307-117">설명</span><span class="sxs-lookup"><span data-stu-id="49307-117">Explanation</span></span>  
 <span data-ttu-id="49307-118">지정된 인덱스에서 잘못된 키가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="49307-118">Out-of-order keys were detected in the specified index.</span></span> <span data-ttu-id="49307-119">키가 포함되어 있는 페이지가 손상되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49307-119">The page in which the keys are contained may be corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="49307-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="49307-120">User Action</span></span>  
 <span data-ttu-id="49307-121">ALTER INDEX REBUILD 문을 사용하여 지정된 인덱스를 다시 작성하십시오.</span><span class="sxs-lookup"><span data-stu-id="49307-121">Rebuild the specified index by using the ALTER INDEX REBUILD statement.</span></span>  
  
  
