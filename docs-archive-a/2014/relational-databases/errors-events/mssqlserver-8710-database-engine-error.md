---
title: MSSQLSERVER_8710 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 65fb6b3efb42c282347f560353a2b21edc337859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661674"
---
# <a name="mssqlserver_8710"></a><span data-ttu-id="d5ea3-102">MSSQLSERVER_8710</span><span class="sxs-lookup"><span data-stu-id="d5ea3-102">MSSQLSERVER_8710</span></span>
    
## <a name="details"></a><span data-ttu-id="d5ea3-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="d5ea3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5ea3-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d5ea3-104">Product Name</span></span>|<span data-ttu-id="d5ea3-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d5ea3-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d5ea3-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d5ea3-106">Event ID</span></span>|<span data-ttu-id="d5ea3-107">8710</span><span class="sxs-lookup"><span data-stu-id="d5ea3-107">8710</span></span>|  
|<span data-ttu-id="d5ea3-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d5ea3-108">Event Source</span></span>|<span data-ttu-id="d5ea3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d5ea3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d5ea3-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d5ea3-110">Component</span></span>|<span data-ttu-id="d5ea3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d5ea3-111">SQLEngine</span></span>|  
|<span data-ttu-id="d5ea3-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d5ea3-112">Symbolic Name</span></span>|<span data-ttu-id="d5ea3-113">QUERY2_CUBE_ILLEGAL_AGG_FUNC</span><span class="sxs-lookup"><span data-stu-id="d5ea3-113">QUERY2_CUBE_ILLEGAL_AGG_FUNC</span></span>|  
|<span data-ttu-id="d5ea3-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d5ea3-114">Message Text</span></span>|<span data-ttu-id="d5ea3-115">CUBE, ROLLUP 또는 GROUPING SET 쿼리에 사용되는 집계 함수는 하위 집계 병합을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ea3-115">Aggregate functions that are used with CUBE, ROLLUP, or GROUPING SET queries must provide for the merging of subaggregates.</span></span> <span data-ttu-id="d5ea3-116">이 문제를 해결하려면 집계 함수를 제거하거나 GROUP BY 절 대신 UNION ALL을 사용하여 쿼리를 작성하십시오.</span><span class="sxs-lookup"><span data-stu-id="d5ea3-116">To fix this problem, remove the aggregate function or write the query using UNION ALL over GROUP BY clauses.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d5ea3-117">설명</span><span class="sxs-lookup"><span data-stu-id="d5ea3-117">Explanation</span></span>  
 <span data-ttu-id="d5ea3-118">하위 집계 병합 방법을 제공하지 않는 CUBE, ROLLUP 또는 GROUPING SETS에 집계 함수가 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ea3-118">An aggregate function has been used with CUBE, ROLLUP, or GROUPING SETS that does not provide a method for merging subaggregates.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d5ea3-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="d5ea3-119">User Action</span></span>  
 <span data-ttu-id="d5ea3-120">이 문제를 해결하려면 집계 함수를 제거하거나 GROUP BY 절 대신 UNION ALL을 사용하여 쿼리를 작성하십시오.</span><span class="sxs-lookup"><span data-stu-id="d5ea3-120">To fix this problem, remove the aggregate function or write the query using UNION ALL over GROUP BY clauses.</span></span>  
  
  
