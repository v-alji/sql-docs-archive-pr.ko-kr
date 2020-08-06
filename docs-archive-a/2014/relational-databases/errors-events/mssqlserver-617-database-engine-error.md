---
title: MSSQLSERVER_617 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88e9feb7c3ac5d8cf646d2243319b2b160b7757e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734079"
---
# <a name="mssqlserver_617"></a><span data-ttu-id="ef5ca-102">MSSQLSERVER_617</span><span class="sxs-lookup"><span data-stu-id="ef5ca-102">MSSQLSERVER_617</span></span>
    
## <a name="details"></a><span data-ttu-id="ef5ca-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ef5ca-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef5ca-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ef5ca-104">Product Name</span></span>|<span data-ttu-id="ef5ca-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ef5ca-105">SQL Server</span></span>|  
|<span data-ttu-id="ef5ca-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ef5ca-106">Event ID</span></span>|<span data-ttu-id="ef5ca-107">617</span><span class="sxs-lookup"><span data-stu-id="ef5ca-107">617</span></span>|  
|<span data-ttu-id="ef5ca-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ef5ca-108">Event Source</span></span>|<span data-ttu-id="ef5ca-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ef5ca-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ef5ca-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ef5ca-110">Component</span></span>|<span data-ttu-id="ef5ca-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ef5ca-111">SQLEngine</span></span>|  
|<span data-ttu-id="ef5ca-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="ef5ca-112">Symbolic Name</span></span>|<span data-ttu-id="ef5ca-113">NODESHASH</span><span class="sxs-lookup"><span data-stu-id="ef5ca-113">NODESHASH</span></span>|  
|<span data-ttu-id="ef5ca-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="ef5ca-114">Message Text</span></span>|<span data-ttu-id="ef5ca-115">테이블의 해시를 취소하는 동안 해시 테이블에서 데이터베이스 ID %d의 개체 ID %ld에 대한 설명자를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-115">Descriptor for object ID %ld in database ID %d not found in the hash table during attempt to unhash it.</span></span> <span data-ttu-id="ef5ca-116">작업 테이블에 항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-116">A work table is missing an entry.</span></span> <span data-ttu-id="ef5ca-117">쿼리를 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-117">Rerun the query.</span></span> <span data-ttu-id="ef5ca-118">커서를 사용하는 경우에는 커서를 닫은 다음 다시 여십시오.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-118">If a cursor is involved, close and reopen the cursor.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ef5ca-119">설명</span><span class="sxs-lookup"><span data-stu-id="ef5ca-119">Explanation</span></span>  
 <span data-ttu-id="ef5ca-120">SQL Server에서 특정 항목에 대한 작업 테이블을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-120">SQL Server cannot locate the work table for a specific entry.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ef5ca-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="ef5ca-121">User Action</span></span>  
  
1.  <span data-ttu-id="ef5ca-122">커서를 사용하는 경우 커서를 닫은 다음 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-122">If a cursor is involved, close the cursor and re-open the cursor.</span></span>  
  
2.  <span data-ttu-id="ef5ca-123">쿼리를 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef5ca-123">Run the query again.</span></span>  
  
  
