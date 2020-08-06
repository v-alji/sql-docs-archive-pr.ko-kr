---
title: MSSQLSERVER_2593 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2593 (Database Engine error)
ms.assetid: 2e25bc43-606a-40de-8b87-3b55b96f4a91
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecd231f38fbb36e2f98a1e9ce254165002bb56e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729507"
---
# <a name="mssqlserver_2593"></a><span data-ttu-id="41ba9-102">MSSQLSERVER_2593</span><span class="sxs-lookup"><span data-stu-id="41ba9-102">MSSQLSERVER_2593</span></span>
    
## <a name="details"></a><span data-ttu-id="41ba9-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="41ba9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41ba9-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="41ba9-104">Product Name</span></span>|<span data-ttu-id="41ba9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="41ba9-105">SQL Server</span></span>|  
|<span data-ttu-id="41ba9-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="41ba9-106">Event ID</span></span>|<span data-ttu-id="41ba9-107">2593</span><span class="sxs-lookup"><span data-stu-id="41ba9-107">2593</span></span>|  
|<span data-ttu-id="41ba9-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="41ba9-108">Event Source</span></span>|<span data-ttu-id="41ba9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="41ba9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="41ba9-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="41ba9-110">Component</span></span>|<span data-ttu-id="41ba9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="41ba9-111">SQLEngine</span></span>|  
|<span data-ttu-id="41ba9-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="41ba9-112">Symbolic Name</span></span>|<span data-ttu-id="41ba9-113">DBCC_OBJECT_ROW_PAGE_SUMMARY</span><span class="sxs-lookup"><span data-stu-id="41ba9-113">DBCC_OBJECT_ROW_PAGE_SUMMARY</span></span>|  
|<span data-ttu-id="41ba9-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="41ba9-114">Message Text</span></span>|<span data-ttu-id="41ba9-115">PAGECOUNT개 페이지에 개체 'OBJECT'에 대한 행이 ROWCOUNT개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41ba9-115">There are ROWCOUNT rows in PAGECOUNT pages for object 'OBJECT'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="41ba9-116">설명</span><span class="sxs-lookup"><span data-stu-id="41ba9-116">Explanation</span></span>  
 <span data-ttu-id="41ba9-117">이 메시지는 DBCC CHECKALLOC을 제외한 모든 DBCC 검사에서 반환하는 출력 정보의 일부이며 지정된 개체의 행과 페이지 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="41ba9-117">This message is part of the informational output that is returned by all DBCC checks, except DBCC CHECKALLOC, and indicates the row and page counts for a specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="41ba9-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="41ba9-118">User Action</span></span>  
 <span data-ttu-id="41ba9-119">None</span><span class="sxs-lookup"><span data-stu-id="41ba9-119">None</span></span>  
  
  
