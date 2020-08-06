---
title: MSSQLSERVER_7910 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7910 (Database Engine error)
ms.assetid: 017a0113-2b17-40b3-a419-30bbc43d46b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60e7cca3f6973374ae7aeaa959a0b31207a1258e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650997"
---
# <a name="mssqlserver_7910"></a><span data-ttu-id="0df67-102">MSSQLSERVER_7910</span><span class="sxs-lookup"><span data-stu-id="0df67-102">MSSQLSERVER_7910</span></span>
    
## <a name="details"></a><span data-ttu-id="0df67-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="0df67-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0df67-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="0df67-104">Product Name</span></span>|<span data-ttu-id="0df67-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0df67-105">SQL Server</span></span>|  
|<span data-ttu-id="0df67-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="0df67-106">Event ID</span></span>|<span data-ttu-id="0df67-107">7910</span><span class="sxs-lookup"><span data-stu-id="0df67-107">7910</span></span>|  
|<span data-ttu-id="0df67-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="0df67-108">Event Source</span></span>|<span data-ttu-id="0df67-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0df67-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0df67-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0df67-110">Component</span></span>|<span data-ttu-id="0df67-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0df67-111">SQLEngine</span></span>|  
|<span data-ttu-id="0df67-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="0df67-112">Symbolic Name</span></span>|<span data-ttu-id="0df67-113">DBCC2_REPAIR_PAGE_ALLOCATED</span><span class="sxs-lookup"><span data-stu-id="0df67-113">DBCC2_REPAIR_PAGE_ALLOCATED</span></span>|  
|<span data-ttu-id="0df67-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="0df67-114">Message Text</span></span>|<span data-ttu-id="0df67-115">복구: 페이지 P_ID이(가) 개체 ID O_ID, 인덱스 ID I_ID, 파티션 ID PN_ID, 할당 단위 ID A_ID(TYPE 유형)에 할당되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0df67-115">Repair: The page P_ID has been allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0df67-116">설명</span><span class="sxs-lookup"><span data-stu-id="0df67-116">Explanation</span></span>  
 <span data-ttu-id="0df67-117">이 메시지는 페이지가 IAM(Index Allocation Map) 페이지의 단일 페이지 슬롯 배열에 할당되었음을 나타내는 REPAIR의 정보 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="0df67-117">This is an informational message from REPAIR that states that a page has been allocated to the single-page slot array of an Index Allocation Map (IAM) page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0df67-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="0df67-118">User Action</span></span>  
 <span data-ttu-id="0df67-119">None</span><span class="sxs-lookup"><span data-stu-id="0df67-119">None</span></span>  
  
  
