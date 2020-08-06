---
title: MSSQLSERVER_17132 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 609b9cea138db15cefd002f494620b5a1da7b208
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731672"
---
# <a name="mssqlserver_17132"></a><span data-ttu-id="85fdb-102">MSSQLSERVER_17132</span><span class="sxs-lookup"><span data-stu-id="85fdb-102">MSSQLSERVER_17132</span></span>
    
## <a name="details"></a><span data-ttu-id="85fdb-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="85fdb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85fdb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="85fdb-104">Product Name</span></span>|<span data-ttu-id="85fdb-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="85fdb-105">SQL Server</span></span>|  
|<span data-ttu-id="85fdb-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="85fdb-106">Event ID</span></span>|<span data-ttu-id="85fdb-107">17132</span><span class="sxs-lookup"><span data-stu-id="85fdb-107">17132</span></span>|  
|<span data-ttu-id="85fdb-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="85fdb-108">Event Source</span></span>|<span data-ttu-id="85fdb-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="85fdb-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="85fdb-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="85fdb-110">Component</span></span>|<span data-ttu-id="85fdb-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="85fdb-111">SQLEngine</span></span>|  
|<span data-ttu-id="85fdb-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="85fdb-112">Symbolic Name</span></span>|<span data-ttu-id="85fdb-113">INIT_NODESSPACE</span><span class="sxs-lookup"><span data-stu-id="85fdb-113">INIT_NODESSPACE</span></span>|  
|<span data-ttu-id="85fdb-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="85fdb-114">Message Text</span></span>|<span data-ttu-id="85fdb-115">설명자에 대한 메모리가 부족하여 서버를 시작하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="85fdb-115">Server startup failed due to insufficient memory for descriptor.</span></span> <span data-ttu-id="85fdb-116">불필요한 메모리 로드를 줄이거나 시스템 메모리를 늘리십시오.</span><span class="sxs-lookup"><span data-stu-id="85fdb-116">Reduce non-essential memory load or increase system memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="85fdb-117">설명</span><span class="sxs-lookup"><span data-stu-id="85fdb-117">Explanation</span></span>  
 <span data-ttu-id="85fdb-118">서버 내부 설명자를 저장할 충분한 메모리를 할당하는 데 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="85fdb-118">Failed to allocate enough memory to store server internal descriptor.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="85fdb-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="85fdb-119">User Action</span></span>  
 <span data-ttu-id="85fdb-120">시스템에 메모리를 더 많이 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="85fdb-120">Add more memory to the machine.</span></span> <span data-ttu-id="85fdb-121">일반적인 메모리 문제 해결 단계가 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85fdb-121">Generic memory troubleshooting steps may be useful.</span></span>  
  
  
