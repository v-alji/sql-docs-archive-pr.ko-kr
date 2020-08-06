---
title: 차단된 프로세스 임계값 늘리기 또는 해제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a7a90aea3fa8fb4d9c423cea1ec6008b01cde883
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646976"
---
# <a name="increase-or-disable-blocked-process-threshold"></a><span data-ttu-id="5b419-102">차단된 프로세스 임계값 늘리기 또는 해제</span><span class="sxs-lookup"><span data-stu-id="5b419-102">Increase or Disable Blocked Process Threshold</span></span>
  <span data-ttu-id="5b419-103">이 규칙은 blocked process threshold 옵션이 0(해제)으로 설정되거나 5 이상의 값(초)으로 설정되어 있는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="5b419-103">This rules checks that the blocked process threshold option is set to 0 (disabled) or set to a value higher than or equal to 5 (seconds).</span></span> <span data-ttu-id="5b419-104">blocked process threshold 옵션을 1에서 4 사이의 값으로 설정하면 교착 상태 모니터가 계속해서 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b419-104">Setting the blocked process threshold option to a value from 1 to 4 can cause the deadlock monitor to run constantly.</span></span> <span data-ttu-id="5b419-105">1에서 4 사이의 값은 문제 해결 용도로만 사용해야 하며 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 고객 서비스 지원 센터의 도움 없이 장기적으로 사용하거나 프로덕션 환경에서 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b419-105">Values 1 to 4 should only be used for troubleshooting, and never long term or in a production environment without the assistance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="5b419-106">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="5b419-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="5b419-107">이 문제를 해결하려면 blocked process threshold 옵션의 값을 5(초) 이상으로 설정하거나 값을 0으로 설정하여 blocked process threshold를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5b419-107">To resolve this problem, set the blocked process threshold option to a value of 5 (seconds) or higher, or disable blocked process threshold by setting the value to 0.</span></span> <span data-ttu-id="5b419-108">blocked process threshold를 `5` 초로 설정하려면 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5b419-108">To set the blocked process threshold to a value of `5` seconds, execute the following statement:</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="5b419-109">참조 항목</span><span class="sxs-lookup"><span data-stu-id="5b419-109">For More Information</span></span>  
 [<span data-ttu-id="5b419-110">blocked process threshold 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="5b419-110">blocked process threshold Server Configuration Option</span></span>](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b419-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b419-111">See Also</span></span>  
 [<span data-ttu-id="5b419-112">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="5b419-112">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
