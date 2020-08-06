---
title: MSSQLSERVER_17083 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17083 (Database Engine error)
ms.assetid: 6c83737d-0531-4fd9-88f6-2da5a150532d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 598cf9b0182178aa13a6d8b965ac10bedaaf5d15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653932"
---
# <a name="mssqlserver_17083"></a><span data-ttu-id="118a0-102">MSSQLSERVER_17083</span><span class="sxs-lookup"><span data-stu-id="118a0-102">MSSQLSERVER_17083</span></span>
    
## <a name="details"></a><span data-ttu-id="118a0-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="118a0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="118a0-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="118a0-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="118a0-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="118a0-105">Event ID</span></span>|<span data-ttu-id="118a0-106">17083</span><span class="sxs-lookup"><span data-stu-id="118a0-106">17083</span></span>|  
|<span data-ttu-id="118a0-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="118a0-107">Event Source</span></span>|<span data-ttu-id="118a0-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="118a0-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="118a0-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="118a0-109">Component</span></span>|<span data-ttu-id="118a0-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="118a0-110">SQLEngine</span></span>|  
|<span data-ttu-id="118a0-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="118a0-111">Symbolic Name</span></span>|<span data-ttu-id="118a0-112">P3_HEKATON_NOT_ATOMIC</span><span class="sxs-lookup"><span data-stu-id="118a0-112">P3_HEKATON_NOT_ATOMIC</span></span>|  
|<span data-ttu-id="118a0-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="118a0-113">Message Text</span></span>|<span data-ttu-id="118a0-114">고유하게 컴파일된 저장 프로시저의 본문은 ATOMIC 블록이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="118a0-114">The body of a natively compiled stored procedure must be an ATOMIC block.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="118a0-115">설명</span><span class="sxs-lookup"><span data-stu-id="118a0-115">Explanation</span></span>  
 <span data-ttu-id="118a0-116">고유하게 컴파일된 저장 프로시저의 본문에 ATOMIC 블록이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="118a0-116">The body of a natively compiled stored procedure did not have an ATOMIC block.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="118a0-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="118a0-117">User Action</span></span>  
 <span data-ttu-id="118a0-118">고유하게 컴파일된 저장 프로시저의 본문에는 ATOMIC 블록이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="118a0-118">A natively compiled stored procedure must contain an ATOMIC block.</span></span> <span data-ttu-id="118a0-119">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="118a0-119">For example:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
 <span data-ttu-id="118a0-120">자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="118a0-120">For more information, see [In-Memory OLTP &#40;In-Memory Optimization&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="118a0-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="118a0-121">See Also</span></span>  
 [<span data-ttu-id="118a0-122">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="118a0-122">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
