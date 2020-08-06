---
title: MSSQLSERVER_8712 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9285d4846cac5af2dd6e87ab55d5fd0610586d07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661670"
---
# <a name="mssqlserver_8712"></a><span data-ttu-id="589cb-102">MSSQLSERVER_8712</span><span class="sxs-lookup"><span data-stu-id="589cb-102">MSSQLSERVER_8712</span></span>
    
## <a name="details"></a><span data-ttu-id="589cb-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="589cb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="589cb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="589cb-104">Product Name</span></span>|<span data-ttu-id="589cb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="589cb-105">SQL Server</span></span>|  
|<span data-ttu-id="589cb-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="589cb-106">Event ID</span></span>|<span data-ttu-id="589cb-107">8712</span><span class="sxs-lookup"><span data-stu-id="589cb-107">8712</span></span>|  
|<span data-ttu-id="589cb-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="589cb-108">Event Source</span></span>|<span data-ttu-id="589cb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="589cb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="589cb-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="589cb-110">Component</span></span>|<span data-ttu-id="589cb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="589cb-111">SQLEngine</span></span>|  
|<span data-ttu-id="589cb-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="589cb-112">Symbolic Name</span></span>|<span data-ttu-id="589cb-113">USEPLAN_ERR_NO_INDEX</span><span class="sxs-lookup"><span data-stu-id="589cb-113">USEPLAN_ERR_NO_INDEX</span></span>|  
|<span data-ttu-id="589cb-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="589cb-114">Message Text</span></span>|<span data-ttu-id="589cb-115">USE PLAN 힌트에 지정된 인덱스 '%.\*ls'이(가) 없습니다.</span><span class="sxs-lookup"><span data-stu-id="589cb-115">Index '%.\*ls', specified in the USE PLAN hint, does not exist.</span></span> <span data-ttu-id="589cb-116">기존 인덱스를 지정하거나 지정된 이름의 인덱스를 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="589cb-116">Specify an existing index, or create an index with the specified name.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="589cb-117">설명</span><span class="sxs-lookup"><span data-stu-id="589cb-117">Explanation</span></span>  
 <span data-ttu-id="589cb-118">USE PLAN 힌트에 지정된 인덱스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="589cb-118">An index that is specified in the USE PLAN hint does not exist.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="589cb-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="589cb-119">User Action</span></span>  
 <span data-ttu-id="589cb-120">USE PLAN 힌트에 지정된 모든 인덱스가 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="589cb-120">Ensure all indexes that are specified in the USE PLAN hint exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="589cb-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="589cb-121">See Also</span></span>  
 <span data-ttu-id="589cb-122">[쿼리 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="589cb-122">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="589cb-123">계획 지침</span><span class="sxs-lookup"><span data-stu-id="589cb-123">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
