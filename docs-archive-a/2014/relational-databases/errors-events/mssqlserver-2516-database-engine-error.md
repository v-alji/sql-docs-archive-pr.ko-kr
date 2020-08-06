---
title: MSSQLSERVER_2516 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6be0809b3560d94bb883cf3a4acfa3d2c484b8b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729516"
---
# <a name="mssqlserver_2516"></a><span data-ttu-id="5a8db-102">MSSQLSERVER_2516</span><span class="sxs-lookup"><span data-stu-id="5a8db-102">MSSQLSERVER_2516</span></span>
    
## <a name="details"></a><span data-ttu-id="5a8db-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5a8db-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5a8db-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="5a8db-104">Product Name</span></span>|<span data-ttu-id="5a8db-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5a8db-105">SQL Server</span></span>|  
|<span data-ttu-id="5a8db-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="5a8db-106">Event ID</span></span>|<span data-ttu-id="5a8db-107">2516</span><span class="sxs-lookup"><span data-stu-id="5a8db-107">2516</span></span>|  
|<span data-ttu-id="5a8db-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="5a8db-108">Event Source</span></span>|<span data-ttu-id="5a8db-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5a8db-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5a8db-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5a8db-110">Component</span></span>|<span data-ttu-id="5a8db-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5a8db-111">SQLEngine</span></span>|  
|<span data-ttu-id="5a8db-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="5a8db-112">Symbolic Name</span></span>|<span data-ttu-id="5a8db-113">DBCC_REPAIR_DIFF_MAP_INVALIDATED</span><span class="sxs-lookup"><span data-stu-id="5a8db-113">DBCC_REPAIR_DIFF_MAP_INVALIDATED</span></span>|  
|<span data-ttu-id="5a8db-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="5a8db-114">Message Text</span></span>|<span data-ttu-id="5a8db-115">복구로 인해 데이터베이스 NAME에 대한 차등 비트맵이 무효화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a8db-115">Repair has invalidated the differential bitmap for database NAME.</span></span> <span data-ttu-id="5a8db-116">차등 백업 체인이 끊어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="5a8db-116">The differential backup chain is broken.</span></span> <span data-ttu-id="5a8db-117">차등 백업을 수행하려면 전체 데이터베이스 백업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8db-117">You must perform a full database backup before you can perform a differential backup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5a8db-118">설명</span><span class="sxs-lookup"><span data-stu-id="5a8db-118">Explanation</span></span>  
 <span data-ttu-id="5a8db-119">MSSQLEngine_2515 오류가 복구되면 이 정보 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a8db-119">This informational message is returned when error MSSQLEngine_2515 is repaired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5a8db-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="5a8db-120">User Action</span></span>  
 <span data-ttu-id="5a8db-121">전체 데이터베이스 백업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8db-121">Perform a full database backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8db-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a8db-122">See Also</span></span>  
 [<span data-ttu-id="5a8db-123">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5a8db-123">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
  
