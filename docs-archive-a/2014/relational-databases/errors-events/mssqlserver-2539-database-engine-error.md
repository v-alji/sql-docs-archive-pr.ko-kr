---
title: MSSQLSERVER_2539 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2539 (Database Engine error)
ms.assetid: e638efcc-56f4-40f9-9740-17ef67b47d79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9f061d2a827dca641bfc0c348af1328fd71856fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653907"
---
# <a name="mssqlserver_2539"></a><span data-ttu-id="6cb99-102">MSSQLSERVER_2539</span><span class="sxs-lookup"><span data-stu-id="6cb99-102">MSSQLSERVER_2539</span></span>
    
## <a name="details"></a><span data-ttu-id="6cb99-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="6cb99-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6cb99-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="6cb99-104">Product Name</span></span>|<span data-ttu-id="6cb99-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6cb99-105">SQL Server</span></span>|  
|<span data-ttu-id="6cb99-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="6cb99-106">Event ID</span></span>|<span data-ttu-id="6cb99-107">2539</span><span class="sxs-lookup"><span data-stu-id="6cb99-107">2539</span></span>|  
|<span data-ttu-id="6cb99-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="6cb99-108">Event Source</span></span>|<span data-ttu-id="6cb99-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6cb99-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6cb99-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6cb99-110">Component</span></span>|<span data-ttu-id="6cb99-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6cb99-111">SQLEngine</span></span>|  
|<span data-ttu-id="6cb99-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="6cb99-112">Symbolic Name</span></span>|<span data-ttu-id="6cb99-113">DBCC_ALLOCATION_SUMMARY_FOR_DATABASE</span><span class="sxs-lookup"><span data-stu-id="6cb99-113">DBCC_ALLOCATION_SUMMARY_FOR_DATABASE</span></span>|  
|<span data-ttu-id="6cb99-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="6cb99-114">Message Text</span></span>|<span data-ttu-id="6cb99-115">이 데이터베이스의 총 익스텐트 수 = EXTENTS, 사용된 페이지 = USED_PAGES, 예약된 페이지 = RESERVED_PAGES.</span><span class="sxs-lookup"><span data-stu-id="6cb99-115">Total number of extents = EXTENTS, used pages = USED_PAGES, reserved pages = RESERVED_PAGES in this database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6cb99-116">설명</span><span class="sxs-lookup"><span data-stu-id="6cb99-116">Explanation</span></span>  
 <span data-ttu-id="6cb99-117">이 정보는 DBCC CHECKALLOC 명령에 대한 출력의 일부로,</span><span class="sxs-lookup"><span data-stu-id="6cb99-117">This information is part of the output from the DBCC CHECKALLOC command.</span></span> <span data-ttu-id="6cb99-118">할당된 익스텐트, 사용된 페이지 및 지정된 데이터베이스에 대해 예약된 페이지를 요약해서 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6cb99-118">This information is the summary of allocated extents, used pages, and reserved pages for the specified database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6cb99-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="6cb99-119">User Action</span></span>  
 <span data-ttu-id="6cb99-120">None</span><span class="sxs-lookup"><span data-stu-id="6cb99-120">None</span></span>  
  
  
