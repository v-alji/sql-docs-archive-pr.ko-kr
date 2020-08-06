---
title: MSSQLSERVER_8689 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cdca0a3cd9ce47ccb39ebeaf8fd1cd260aafbd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730688"
---
# <a name="mssqlserver_8689"></a><span data-ttu-id="e1f84-102">MSSQLSERVER_8689</span><span class="sxs-lookup"><span data-stu-id="e1f84-102">MSSQLSERVER_8689</span></span>
    
## <a name="details"></a><span data-ttu-id="e1f84-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="e1f84-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1f84-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="e1f84-104">Product Name</span></span>|<span data-ttu-id="e1f84-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e1f84-105">SQL Server</span></span>|  
|<span data-ttu-id="e1f84-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="e1f84-106">Event ID</span></span>|<span data-ttu-id="e1f84-107">8689</span><span class="sxs-lookup"><span data-stu-id="e1f84-107">8689</span></span>|  
|<span data-ttu-id="e1f84-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="e1f84-108">Event Source</span></span>|<span data-ttu-id="e1f84-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e1f84-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e1f84-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e1f84-110">Component</span></span>|<span data-ttu-id="e1f84-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e1f84-111">SQLEngine</span></span>|  
|<span data-ttu-id="e1f84-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="e1f84-112">Symbolic Name</span></span>|<span data-ttu-id="e1f84-113">USEPLAN_ERR_NO_DB</span><span class="sxs-lookup"><span data-stu-id="e1f84-113">USEPLAN_ERR_NO_DB</span></span>|  
|<span data-ttu-id="e1f84-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="e1f84-114">Message Text</span></span>|<span data-ttu-id="e1f84-115">USE PLAN 힌트에 지정된 데이터베이스 '%.\*ls'이(가) 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1f84-115">Database '%.\*ls', specified in the USE PLAN hint, does not exist.</span></span> <span data-ttu-id="e1f84-116">기존 데이터베이스를 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="e1f84-116">Specify an existing database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e1f84-117">설명</span><span class="sxs-lookup"><span data-stu-id="e1f84-117">Explanation</span></span>  
 <span data-ttu-id="e1f84-118">USE PLAN 힌트에 지정된 데이터베이스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1f84-118">A database that is specified in the USE PLAN hint does not exist.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e1f84-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="e1f84-119">User Action</span></span>  
 <span data-ttu-id="e1f84-120">USE PLAN 힌트에 지정된 모든 데이터베이스가 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="e1f84-120">Ensure all databases that are specified in the USE PLAN hint exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f84-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1f84-121">See Also</span></span>  
 <span data-ttu-id="e1f84-122">[쿼리 힌트&#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span><span class="sxs-lookup"><span data-stu-id="e1f84-122">[Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query) </span></span>  
 [<span data-ttu-id="e1f84-123">계획 지침</span><span class="sxs-lookup"><span data-stu-id="e1f84-123">Plan Guides</span></span>](../performance/plan-guides.md)  
  
  
