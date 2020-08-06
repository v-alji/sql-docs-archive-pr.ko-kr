---
title: 최대 작업자 스레드 수 설정 검사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5dbffb87f58d2beb633f43ff18680222ea62cf5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648981"
---
# <a name="verify-max-worker-threads-setting"></a><span data-ttu-id="fc970-102">최대 작업자 스레드 수 설정 검사</span><span class="sxs-lookup"><span data-stu-id="fc970-102">Verify Max Worker Threads Setting</span></span>
  <span data-ttu-id="fc970-103">이 규칙은 최대 작업자 스레드 수 서버 옵션에서 발생할 수 있는 잘못된 설정을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="fc970-103">This rule checks the max worker threads server option for potentially incorrect settings.</span></span> <span data-ttu-id="fc970-104">최대 작업자 스레드 수 옵션을 작은 값으로 설정하면 들어오는 클라이언트 요청을 적절한 시간 내에 처리하기 위한 스레드의 수가 부족하게 되어 “스레드 고갈” 상태가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc970-104">Setting the max worker threads option to a small value may prevent enough threads from servicing incoming client requests in a timely manner and could lead to "thread starvation".</span></span> <span data-ttu-id="fc970-105">옵션을 큰 값으로 설정하면 주소 공간이 낭비될 수 있습니다. 각 활성 스레드의 소비 공간이 32비트 서버의 경우 512KB, 64비트 서버의 경우 최대 4MB에 이르기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="fc970-105">However, setting the option to a large value can waste address space, because each active thread consumes 512 KB on 32-bit servers and up to 4 MB on 64-bit servers.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="fc970-106">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="fc970-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="fc970-107">최대 작업자 스레드 수 옵션을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc970-107">Set the max worker threads option to 0.</span></span> <span data-ttu-id="fc970-108">이렇게 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 사용자 요청에 따라 활성 작업자 스레드의 적정 수를 자동으로 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc970-108">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to automatically determine the correct number of active worker threads based on user requests.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="fc970-109">참조 항목</span><span class="sxs-lookup"><span data-stu-id="fc970-109">For More Information</span></span>  
 [<span data-ttu-id="fc970-110">max worker threads 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="fc970-110">Configure the max worker threads Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="fc970-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc970-111">See Also</span></span>  
 [<span data-ttu-id="fc970-112">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="fc970-112">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
