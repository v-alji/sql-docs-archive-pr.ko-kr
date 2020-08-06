---
title: MSSQLSERVER_2538 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2538 (Database Engine error)
ms.assetid: 0a0f7d79-f1ba-4749-8804-fb660cca3492
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9f4ae886a6fd0abee2f7aa22c6a234c0a6c2d040
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653908"
---
# <a name="mssqlserver_2538"></a><span data-ttu-id="920af-102">MSSQLSERVER_2538</span><span class="sxs-lookup"><span data-stu-id="920af-102">MSSQLSERVER_2538</span></span>
    
## <a name="details"></a><span data-ttu-id="920af-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="920af-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="920af-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="920af-104">Product Name</span></span>|<span data-ttu-id="920af-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="920af-105">SQL Server</span></span>|  
|<span data-ttu-id="920af-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="920af-106">Event ID</span></span>|<span data-ttu-id="920af-107">2538</span><span class="sxs-lookup"><span data-stu-id="920af-107">2538</span></span>|  
|<span data-ttu-id="920af-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="920af-108">Event Source</span></span>|<span data-ttu-id="920af-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="920af-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="920af-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="920af-110">Component</span></span>|<span data-ttu-id="920af-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="920af-111">SQLEngine</span></span>|  
|<span data-ttu-id="920af-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="920af-112">Symbolic Name</span></span>|<span data-ttu-id="920af-113">DBCC_ALLOCATION_SUMMARY_PER_FILE</span><span class="sxs-lookup"><span data-stu-id="920af-113">DBCC_ALLOCATION_SUMMARY_PER_FILE</span></span>|  
|<span data-ttu-id="920af-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="920af-114">Message Text</span></span>|<span data-ttu-id="920af-115">파일 FILE.</span><span class="sxs-lookup"><span data-stu-id="920af-115">File FILE.</span></span> <span data-ttu-id="920af-116">익스텐트 수 = EXTENTS, 사용된 페이지 = USED_PAGES, 예약된 페이지 = RESERVED_PAGES.</span><span class="sxs-lookup"><span data-stu-id="920af-116">Number of extents = EXTENTS, used pages = USED_PAGES, reserved pages = RESERVED_PAGES.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="920af-117">설명</span><span class="sxs-lookup"><span data-stu-id="920af-117">Explanation</span></span>  
 <span data-ttu-id="920af-118">이 정보는 DBCC CHECKALLOC 명령에 대한 출력의 일부로,</span><span class="sxs-lookup"><span data-stu-id="920af-118">This information is part of the output from the DBCC CHECKALLOC command.</span></span> <span data-ttu-id="920af-119">지정된 데이터베이스에 대해 할당된 익스텐트, 사용된 페이지 및 예약된 페이지를 파일별로 요약하여 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="920af-119">This information is the per-file summary of allocated extents, used pages, and reserved pages for the specified database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="920af-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="920af-120">User Action</span></span>  
 <span data-ttu-id="920af-121">None</span><span class="sxs-lookup"><span data-stu-id="920af-121">None</span></span>  
  
  
