---
title: MSSQLSERVER_17128 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e08c668acd0a8b2decb14da338b8d1f1e650de5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730720"
---
# <a name="mssqlserver_17128"></a><span data-ttu-id="5bdc9-102">MSSQLSERVER_17128</span><span class="sxs-lookup"><span data-stu-id="5bdc9-102">MSSQLSERVER_17128</span></span>
    
## <a name="details"></a><span data-ttu-id="5bdc9-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5bdc9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5bdc9-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="5bdc9-104">Product Name</span></span>|<span data-ttu-id="5bdc9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5bdc9-105">SQL Server</span></span>|  
|<span data-ttu-id="5bdc9-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="5bdc9-106">Event ID</span></span>|<span data-ttu-id="5bdc9-107">17128</span><span class="sxs-lookup"><span data-stu-id="5bdc9-107">17128</span></span>|  
|<span data-ttu-id="5bdc9-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="5bdc9-108">Event Source</span></span>|<span data-ttu-id="5bdc9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5bdc9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5bdc9-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5bdc9-110">Component</span></span>|<span data-ttu-id="5bdc9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5bdc9-111">SQLEngine</span></span>|  
|<span data-ttu-id="5bdc9-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="5bdc9-112">Symbolic Name</span></span>|<span data-ttu-id="5bdc9-113">INIT_NOBUFSPACE</span><span class="sxs-lookup"><span data-stu-id="5bdc9-113">INIT_NOBUFSPACE</span></span>|  
|<span data-ttu-id="5bdc9-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="5bdc9-114">Message Text</span></span>|<span data-ttu-id="5bdc9-115">initdata: 커널 버퍼용 메모리가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bdc9-115">initdata: No memory for kernel buffers.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5bdc9-116">설명</span><span class="sxs-lookup"><span data-stu-id="5bdc9-116">Explanation</span></span>  
 <span data-ttu-id="5bdc9-117">버퍼 풀의 초기 메모리 할당 또는 예약이 실패하여 SQL Server가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bdc9-117">The buffer pool's initial memory allocations or reservations have failed, and SQL Server exits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5bdc9-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="5bdc9-118">User Action</span></span>  
 <span data-ttu-id="5bdc9-119">일반적으로 이 오류는 최소 시스템 요구 사항보다 훨씬 작은 머신에서 SQL Server를 시작하는 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5bdc9-119">Usually caused by starting SQL Server on an extremely small machine - far smaller than the minimum system requirements.</span></span>  
  
  
