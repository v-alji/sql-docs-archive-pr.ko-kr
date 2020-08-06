---
title: MSSQLSERVER_11409 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4249e13a3530f69978c78f2e2ca6e4583eed46a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646534"
---
# <a name="mssqlserver_11409"></a><span data-ttu-id="5e0bb-102">MSSQLSERVER_11409</span><span class="sxs-lookup"><span data-stu-id="5e0bb-102">MSSQLSERVER_11409</span></span>
    
## <a name="details"></a><span data-ttu-id="5e0bb-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5e0bb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5e0bb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="5e0bb-104">Product Name</span></span>|<span data-ttu-id="5e0bb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5e0bb-105">SQL Server</span></span>|  
|<span data-ttu-id="5e0bb-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="5e0bb-106">Event ID</span></span>|<span data-ttu-id="5e0bb-107">11409</span><span class="sxs-lookup"><span data-stu-id="5e0bb-107">11409</span></span>|  
|<span data-ttu-id="5e0bb-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="5e0bb-108">Event Source</span></span>|<span data-ttu-id="5e0bb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5e0bb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5e0bb-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5e0bb-110">Component</span></span>|<span data-ttu-id="5e0bb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5e0bb-111">SQLEngine</span></span>|  
|<span data-ttu-id="5e0bb-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="5e0bb-112">Symbolic Name</span></span>|<span data-ttu-id="5e0bb-113">ALTERCOL_COLSET_DROP</span><span class="sxs-lookup"><span data-stu-id="5e0bb-113">ALTERCOL_COLSET_DROP</span></span>|  
|<span data-ttu-id="5e0bb-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="5e0bb-114">Message Text</span></span>|<span data-ttu-id="5e0bb-115">테이블에 포함된 열 개수가 1,025개를 초과하므로 테이블 '%.\*ls'의 열 집합 '%.\*ls'을(를) 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0bb-115">Cannot drop column set '%.\*ls' in table '%.\*ls' because the table contains more than 1025 columns.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5e0bb-116">설명</span><span class="sxs-lookup"><span data-stu-id="5e0bb-116">Explanation</span></span>  
 <span data-ttu-id="5e0bb-117">테이블은 스파스나 계산 열로 지정되지 않은 열을 최대 1,024개까지 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0bb-117">Tables can contain a maximum of 1024 columns that are not designated as sparse, or computed.</span></span> <span data-ttu-id="5e0bb-118">스파스 열로 인해 테이블 열 개수가 1,024개를 초과하면 테이블에 대한 열 집합을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0bb-118">When sparse columns cause the table to exceed 1024 columns, a column set must be defined for the table.</span></span> <span data-ttu-id="5e0bb-119">참조된 테이블의 열 개수가 1,024개를 초과한 상태에서 이 열 집합을 제거하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0bb-119">The table referenced has more than 1024 columns and you have attempted to remove the column set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5e0bb-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="5e0bb-120">User Action</span></span>  
 <span data-ttu-id="5e0bb-121">테이블의 현재 열과 함께 열 집합을 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0bb-121">With the current columns in the table, you must retain the column set.</span></span>  
  
 <span data-ttu-id="5e0bb-122">열 집합을 제거하려면 먼저 테이블의 열 개수가 1,024개 미만이 될 때까지 테이블에서 열을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e0bb-122">To remove the column set, first remove columns from the table, until you have no more than 1024 columns.</span></span> <span data-ttu-id="5e0bb-123">그런 다음 열 집합을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e0bb-123">Then, you can remove the column set.</span></span>  
  
  
