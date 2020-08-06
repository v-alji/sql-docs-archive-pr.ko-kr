---
title: 경량 풀링 해제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13b9ccba0a3a5805dab2eec1d04cc161e6dbd6ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741911"
---
# <a name="disable-lightweight-pooling"></a><span data-ttu-id="cf570-102">경량 풀링 해제</span><span class="sxs-lookup"><span data-stu-id="cf570-102">Disable Lightweight Pooling</span></span>
  <span data-ttu-id="cf570-103">이 규칙은 서버에 경량 풀링이 해제되어 있는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="cf570-103">This rule checks that lightweight pooling is disabled on the server.</span></span> <span data-ttu-id="cf570-104">lightweightpooling을 1로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 파이버 모드 일정으로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf570-104">Setting lightweightpooling to 1 causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to switch to fiber mode scheduling.</span></span> <span data-ttu-id="cf570-105">파이버 모드는 UMS 작업자의 컨텍스트 전환으로 인해 중대한 성능 병목 상태가 발생하는 특정한 상황을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cf570-105">Fiber mode is intended for certain situations in which the context switching of the UMS workers is the important bottleneck in performance.</span></span> <span data-ttu-id="cf570-106">이런 경우는 드물기 때문에 파이버 모드가 일반 시스템의 성능이나 확장성을 향상시키는 경우는 거의 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf570-106">Because this is rare, fiber mode seldom improves performance or scalability on the typical system.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="cf570-107">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="cf570-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="cf570-108">lightweightpooling 옵션은 철저한 테스트를 수행하고 다른 모든 성능 튜닝 방법을 평가한 후에, 현재 환경에서 컨텍스트 전환이 알려진 문제인 경우에만 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf570-108">The lightweightpooling option should only be enabled after thorough testing, after all other performance tuning opportunities are evaluated, and when context switching is a known issue in your environment.</span></span>  
  
 <span data-ttu-id="cf570-109">파이버 모드를 사용하면 컨텍스트 전환을 활용하지 못해 성능이 저하될 수 있고, TLS(스레드 로컬 스토리지) 또는 스레드 소유 개체(예: 뮤텍스 - Win32 커널 개체 유형)를 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 일부 구성 요소가 파이버 모드에서 제대로 작동하지 않으므로 일상적인 작업에는 파이버 모드 일정을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cf570-109">We recommend that you do not use fiber mode scheduling for routine operation because it can decrease performance by preventing the regular benefits of context switching, and because some components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that use Thread Local Storage (TLS) or thread-owned objects, such as mutexes (a kind of Win32 kernel object), cannot function correctly in fiber mode</span></span>  
  
 <span data-ttu-id="cf570-110">경량 풀링을 제거하려면 다음 문을 실행한 다음 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cf570-110">To remove lightweight pooling, execute the following statement, and then restart the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweightpooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="cf570-111">참조 항목</span><span class="sxs-lookup"><span data-stu-id="cf570-111">For More Information</span></span>  
 [<span data-ttu-id="cf570-112">경량 풀링 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="cf570-112">lightweight pooling Server Configuration Option</span></span>](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="cf570-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf570-113">See Also</span></span>  
 [<span data-ttu-id="cf570-114">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="cf570-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
