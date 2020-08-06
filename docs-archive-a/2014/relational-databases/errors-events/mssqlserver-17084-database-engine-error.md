---
title: MSSQLSERVER_17084 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17084 (Database Engine error)
ms.assetid: e579d104-3307-4edd-8587-b14ecbc02ed9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 59b0fc3e0884ddd89809767a068b937b5c145f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653927"
---
# <a name="mssqlserver_17084"></a><span data-ttu-id="3e36f-102">MSSQLSERVER_17084</span><span class="sxs-lookup"><span data-stu-id="3e36f-102">MSSQLSERVER_17084</span></span>
    
## <a name="details"></a><span data-ttu-id="3e36f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3e36f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3e36f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="3e36f-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="3e36f-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="3e36f-105">Event ID</span></span>|<span data-ttu-id="3e36f-106">17084</span><span class="sxs-lookup"><span data-stu-id="3e36f-106">17084</span></span>|  
|<span data-ttu-id="3e36f-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="3e36f-107">Event Source</span></span>|<span data-ttu-id="3e36f-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3e36f-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3e36f-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="3e36f-109">Component</span></span>|<span data-ttu-id="3e36f-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3e36f-110">SQLEngine</span></span>|  
|<span data-ttu-id="3e36f-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="3e36f-111">Symbolic Name</span></span>|<span data-ttu-id="3e36f-112">P3_ATOMIC_WITH_MISSING_OPTION</span><span class="sxs-lookup"><span data-stu-id="3e36f-112">P3_ATOMIC_WITH_MISSING_OPTION</span></span>|  
|<span data-ttu-id="3e36f-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3e36f-113">Message Text</span></span>|<span data-ttu-id="3e36f-114">BEGIN ATOMIC 문의 WITH 절은 '%ls' 옵션에 대한 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e36f-114">The WITH clause of BEGIN ATOMIC statement must specify a value for the option '%ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3e36f-115">설명</span><span class="sxs-lookup"><span data-stu-id="3e36f-115">Explanation</span></span>  
 <span data-ttu-id="3e36f-116">BEGIN ATOMIC 문의 WITH 절이 옵션 값을 지정하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3e36f-116">The WITH clause of BEGIN ATOMIC statement did not specify a value for an option.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3e36f-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3e36f-117">User Action</span></span>  
 <span data-ttu-id="3e36f-118">`ATOMIC` 블록에는 `WITH` 옵션 `TRANSACTION ISOLATION LEVEL` 및 `LANGUAGE`에 대한 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3e36f-118">`ATOMIC` blocks require values for the `WITH` options `TRANSACTION ISOLATION LEVEL` and `LANGUAGE`.</span></span> <span data-ttu-id="3e36f-119">예::</span><span class="sxs-lookup"><span data-stu-id="3e36f-119">For example::</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
 <span data-ttu-id="3e36f-120">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e36f-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e36f-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e36f-121">See Also</span></span>  
 [<span data-ttu-id="3e36f-122">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="3e36f-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
