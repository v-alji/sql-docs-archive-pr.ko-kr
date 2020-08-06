---
title: MSSQLSERVER_12304 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2347fc46fe5ab83ef2ff46b81500cd737ed02d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652156"
---
# <a name="mssqlserver_12304"></a><span data-ttu-id="f2d5c-102">MSSQLSERVER_12304</span><span class="sxs-lookup"><span data-stu-id="f2d5c-102">MSSQLSERVER_12304</span></span>
    
## <a name="details"></a><span data-ttu-id="f2d5c-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="f2d5c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2d5c-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="f2d5c-104">Product Name</span></span>|<span data-ttu-id="f2d5c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f2d5c-105">SQL Server</span></span>|  
|<span data-ttu-id="f2d5c-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f2d5c-106">Event ID</span></span>|<span data-ttu-id="f2d5c-107">12304</span><span class="sxs-lookup"><span data-stu-id="f2d5c-107">12304</span></span>|  
|<span data-ttu-id="f2d5c-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="f2d5c-108">Event Source</span></span>|<span data-ttu-id="f2d5c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f2d5c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f2d5c-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f2d5c-110">Component</span></span>|<span data-ttu-id="f2d5c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f2d5c-111">SQLEngine</span></span>|  
|<span data-ttu-id="f2d5c-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="f2d5c-112">Symbolic Name</span></span>|<span data-ttu-id="f2d5c-113">HK_UNSUPPORTED_IDENTITY_TABLE_VAR</span><span class="sxs-lookup"><span data-stu-id="f2d5c-113">HK_UNSUPPORTED_IDENTITY_TABLE_VAR</span></span>|  
|<span data-ttu-id="f2d5c-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="f2d5c-114">Message Text</span></span>|<span data-ttu-id="f2d5c-115">열에서 IDENTITY 속성을 사용하는 메모리 액세스에 최적화된 테이블의 사용은 고유하게 컴파일된 저장 프로시저의 컨텍스트 외부에 있는 형식을 사용할 때 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2d5c-115">Using a memory optimized table type that uses the IDENTITY property with any of its columns is not supported when using the type outside the context of a natively compiled stored procedure.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="f2d5c-116">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="f2d5c-116">User Action</span></span>  
 <span data-ttu-id="f2d5c-117">열에서 IDENTITY 속성을 사용하는 메모리 최적화 테이블 형식을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="f2d5c-117">Do not use a memory-optimized table type that uses the identity property with any of its columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d5c-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2d5c-118">See Also</span></span>  
 [<span data-ttu-id="f2d5c-119">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="f2d5c-119">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
