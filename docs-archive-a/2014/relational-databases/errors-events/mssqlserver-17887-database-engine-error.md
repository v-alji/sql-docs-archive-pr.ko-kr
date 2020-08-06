---
title: MSSQLSERVER_17887 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 006e616d80ef7e8d083f60675b02b4e6a4e8dc24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646533"
---
# <a name="mssqlserver_17887"></a><span data-ttu-id="25722-102">MSSQLSERVER_17887</span><span class="sxs-lookup"><span data-stu-id="25722-102">MSSQLSERVER_17887</span></span>
    
## <a name="details"></a><span data-ttu-id="25722-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="25722-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25722-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="25722-104">Product Name</span></span>|<span data-ttu-id="25722-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="25722-105">SQL Server</span></span>|  
|<span data-ttu-id="25722-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="25722-106">Event ID</span></span>|<span data-ttu-id="25722-107">17887</span><span class="sxs-lookup"><span data-stu-id="25722-107">17887</span></span>|  
|<span data-ttu-id="25722-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="25722-108">Event Source</span></span>|<span data-ttu-id="25722-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="25722-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="25722-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="25722-110">Component</span></span>|<span data-ttu-id="25722-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="25722-111">SQLEngine</span></span>|  
|<span data-ttu-id="25722-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="25722-112">Symbolic Name</span></span>|<span data-ttu-id="25722-113">SRV_IO_COMP_LISTENER_NONYIELDING</span><span class="sxs-lookup"><span data-stu-id="25722-113">SRV_IO_COMP_LISTENER_NONYIELDING</span></span>|  
|<span data-ttu-id="25722-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="25722-114">Message Text</span></span>|<span data-ttu-id="25722-115">IO 완료 수신기(0x%lx) 작업자 0x%p이(가) 노드 %ld에서 잠긴 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="25722-115">IO Completion Listener (0x%lx) Worker 0x%p appears to be non-yielding on Node %ld.</span></span> <span data-ttu-id="25722-116">대략적인 CPU 사용량: 커널 %I64dms, 사용자 %I64dms, 간격: %I64d.</span><span class="sxs-lookup"><span data-stu-id="25722-116">Approx CPU Used: kernel %I64d ms, user %I64d ms, Interval: %I64d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="25722-117">설명</span><span class="sxs-lookup"><span data-stu-id="25722-117">Explanation</span></span>  
 <span data-ttu-id="25722-118">네트워크 읽기/쓰기 이벤트에 대해 I/O 완료 루틴을 실행할 때 지정된 노드의 I/O 완료 포트 수신기에 문제가 있을 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="25722-118">Indicates that there is a possible problem with the I/O Completion Port Listener on the specified node when executing the I/O Completion routine for a network read/write event.</span></span> <span data-ttu-id="25722-119">이 오류는 I/O 완료 루틴이 실행될 때 I/O 완료 포트 수신기가 반환되면 더 이상 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25722-119">This error will go away when the I/O Completion Port Listener returns from executing the I/O Completion routine.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="25722-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="25722-120">User Action</span></span>  
 <span data-ttu-id="25722-121">Microsoft CSS(고객 지원 서비스)에 문의합니다.</span><span class="sxs-lookup"><span data-stu-id="25722-121">Contact Microsoft Customer Support Services (CSS).</span></span>  
  
  
