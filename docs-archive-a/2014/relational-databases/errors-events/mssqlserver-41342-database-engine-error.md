---
title: MSSQLSERVER_41342 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c0269322b30cee88e5ba3d50b6d391464b735f54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652870"
---
# <a name="mssqlserver_41342"></a><span data-ttu-id="74157-102">MSSQLSERVER_41342</span><span class="sxs-lookup"><span data-stu-id="74157-102">MSSQLSERVER_41342</span></span>
    
## <a name="details"></a><span data-ttu-id="74157-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="74157-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74157-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="74157-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="74157-105">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="74157-105">Event ID</span></span>|<span data-ttu-id="74157-106">41342</span><span class="sxs-lookup"><span data-stu-id="74157-106">41342</span></span>|  
|<span data-ttu-id="74157-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="74157-107">Event Source</span></span>|<span data-ttu-id="74157-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="74157-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="74157-109">구성 요소</span><span class="sxs-lookup"><span data-stu-id="74157-109">Component</span></span>|<span data-ttu-id="74157-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="74157-110">SQLEngine</span></span>|  
|<span data-ttu-id="74157-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="74157-111">Symbolic Name</span></span>|<span data-ttu-id="74157-112">HK_HW_NOT_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="74157-112">HK_HW_NOT_SUPPORTED</span></span>|  
|<span data-ttu-id="74157-113">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="74157-113">Message Text</span></span>|<span data-ttu-id="74157-114">시스템의 프로세서 모델은 *construct* 만들기를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74157-114">The model of the processor on the system does not support creating *construct*.</span></span> <span data-ttu-id="74157-115">이 오류는 일반적으로 오래된 프로세서에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="74157-115">This error typically occurs with older processors.</span></span> <span data-ttu-id="74157-116">지원되는 모델에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="74157-116">See [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online for information on supported models.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="74157-117">설명</span><span class="sxs-lookup"><span data-stu-id="74157-117">Explanation</span></span>  
 <span data-ttu-id="74157-118">메모리 액세스에 최적화된 테이블에는 128비트 값에 대해 원자성 비교 및 교환 작업을 지원하는 프로세서 모델이 필요하며 프로세서 모델에서 CMPXCHG16B 어셈블리 명령어를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74157-118">Memory-optimized tables require a processor model that supports atomic compare-and-exchange operations on 128-bit values, which require the assembly instruction CMPXCHG16B.</span></span> <span data-ttu-id="74157-119">몇몇 이전 AMD 프로세서 모델은 CMPXCHG16B 명령어를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74157-119">Certain older AMD processor models do not support the CMPXCHG16B instruction.</span></span> <span data-ttu-id="74157-120">또한 특정 가상화 환경에서는 기본적으로 이 명령어를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="74157-120">Also, certain virtualization environments do not enable this instruction by default.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="74157-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="74157-121">User Action</span></span>  
 <span data-ttu-id="74157-122">프로세서를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="74157-122">Upgrade your processor.</span></span> <span data-ttu-id="74157-123">프로세서에서 명령어를 지원하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](을)를 가상 머신에서 실행하는 경우에는 CMPXCHG16B 명령어를 지원하도록 구성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="74157-123">If your processor supports the instruction and you are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a virtual machine, change the configuration to support the instruction CMPXCHG16B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74157-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74157-124">See Also</span></span>  
 [<span data-ttu-id="74157-125">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="74157-125">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
