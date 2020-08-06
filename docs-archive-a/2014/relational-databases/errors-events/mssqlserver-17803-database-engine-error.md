---
title: MSSQLSERVER_17803 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8be63b3d05bff2ebf90122f66af4297d77376fce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653926"
---
# <a name="mssqlserver_17803"></a><span data-ttu-id="72b25-102">MSSQLSERVER_17803</span><span class="sxs-lookup"><span data-stu-id="72b25-102">MSSQLSERVER_17803</span></span>
    
## <a name="details"></a><span data-ttu-id="72b25-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="72b25-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72b25-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="72b25-104">Product Name</span></span>|<span data-ttu-id="72b25-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="72b25-105">SQL Server</span></span>|  
|<span data-ttu-id="72b25-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="72b25-106">Event ID</span></span>|<span data-ttu-id="72b25-107">17803</span><span class="sxs-lookup"><span data-stu-id="72b25-107">17803</span></span>|  
|<span data-ttu-id="72b25-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="72b25-108">Event Source</span></span>|<span data-ttu-id="72b25-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="72b25-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="72b25-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="72b25-110">Component</span></span>|<span data-ttu-id="72b25-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="72b25-111">SQLEngine</span></span>|  
|<span data-ttu-id="72b25-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="72b25-112">Symbolic Name</span></span>|<span data-ttu-id="72b25-113">SRV_NOMEMORY</span><span class="sxs-lookup"><span data-stu-id="72b25-113">SRV_NOMEMORY</span></span>|  
|<span data-ttu-id="72b25-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="72b25-114">Message Text</span></span>|<span data-ttu-id="72b25-115">연결 설정 중 메모리 할당에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="72b25-115">There was a memory allocation failure during connection establishment.</span></span> <span data-ttu-id="72b25-116">필요하지 않은 메모리 로드를 줄이거나 시스템 메모리를 늘리십시오.</span><span class="sxs-lookup"><span data-stu-id="72b25-116">Reduce nonessential memory load, or increase system memory.</span></span> <span data-ttu-id="72b25-117">연결이 닫혔습니다.%.\*ls</span><span class="sxs-lookup"><span data-stu-id="72b25-117">The connection has been closed.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="72b25-118">설명</span><span class="sxs-lookup"><span data-stu-id="72b25-118">Explanation</span></span>  
 <span data-ttu-id="72b25-119">서버에 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="72b25-119">Server is running out of memory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="72b25-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="72b25-120">User Action</span></span>  
 <span data-ttu-id="72b25-121">서버에 메모리가 부족한 원인을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="72b25-121">Determine the cause for server running out of memory.</span></span> <span data-ttu-id="72b25-122">일반적인 메모리 문제 해결 단계가 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b25-122">Generic memory troubleshooting steps may be useful</span></span>  
  
  
