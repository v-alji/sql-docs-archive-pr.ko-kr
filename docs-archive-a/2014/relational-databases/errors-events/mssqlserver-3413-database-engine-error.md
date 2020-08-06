---
title: MSSQLSERVER_3413 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a5d59ea61cff7051c3e1163a463c29443c553923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653899"
---
# <a name="mssqlserver_3413"></a><span data-ttu-id="1e2e2-102">MSSQLSERVER_3413</span><span class="sxs-lookup"><span data-stu-id="1e2e2-102">MSSQLSERVER_3413</span></span>
    
## <a name="details"></a><span data-ttu-id="1e2e2-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1e2e2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e2e2-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1e2e2-104">Product Name</span></span>|<span data-ttu-id="1e2e2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1e2e2-105">SQL Server</span></span>|  
|<span data-ttu-id="1e2e2-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1e2e2-106">Event ID</span></span>|<span data-ttu-id="1e2e2-107">3413</span><span class="sxs-lookup"><span data-stu-id="1e2e2-107">3413</span></span>|  
|<span data-ttu-id="1e2e2-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1e2e2-108">Event Source</span></span>|<span data-ttu-id="1e2e2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1e2e2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1e2e2-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1e2e2-110">Component</span></span>|<span data-ttu-id="1e2e2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1e2e2-111">SQLEngine</span></span>|  
|<span data-ttu-id="1e2e2-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1e2e2-112">Symbolic Name</span></span>|<span data-ttu-id="1e2e2-113">MARKDB</span><span class="sxs-lookup"><span data-stu-id="1e2e2-113">MARKDB</span></span>|  
|<span data-ttu-id="1e2e2-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1e2e2-114">Message Text</span></span>|<span data-ttu-id="1e2e2-115">데이터베이스 ID %d.</span><span class="sxs-lookup"><span data-stu-id="1e2e2-115">Database ID %d.</span></span> <span data-ttu-id="1e2e2-116">데이터베이스를 주의 대상으로 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e2e2-116">Could not mark database as suspect.</span></span> <span data-ttu-id="1e2e2-117">sys.databases.database_id의 Getnext NC 검색이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="1e2e2-117">Getnext NC scan on sys.databases.database_id failed.</span></span> <span data-ttu-id="1e2e2-118">오류 로그에서 이전 오류를 참조하여 원인을 확인하고 관련 문제를 모두 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e2e2-118">Refer to previous errors in the error log to identify the cause and correct any associated problems.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1e2e2-119">설명</span><span class="sxs-lookup"><span data-stu-id="1e2e2-119">Explanation</span></span>  
 <span data-ttu-id="1e2e2-120">카탈로그에서 사용자 데이터베이스를 SUSPECT로 표시하려는 동안 예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="1e2e2-120">There was an unexpected failure while trying to mark a user database as SUSPECT in the catalog.</span></span> <span data-ttu-id="1e2e2-121">SUSPECT 상태는 지속되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e2e2-121">The SUSPECT state will not be persisted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1e2e2-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1e2e2-122">User Action</span></span>  
 <span data-ttu-id="1e2e2-123">이전 오류를 참조하여 문제를 해결하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e2e2-123">See previous errors and correct the problem.</span></span>  
  
  
