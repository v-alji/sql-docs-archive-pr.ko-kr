---
title: AUTO_SHRINK 데이터베이스 옵션을 OFF로 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 42d79ed13a691c3d39a28e7ab35a740a9f613fac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740844"
---
# <a name="set-the-auto_shrink-database-option-to-off"></a><span data-ttu-id="28c3f-102">AUTO_SHRINK 데이터베이스 옵션을 OFF로 설정</span><span class="sxs-lookup"><span data-stu-id="28c3f-102">Set the AUTO_SHRINK Database Option to OFF</span></span>
  <span data-ttu-id="28c3f-103">이 규칙은 AUTO_SHRINK 데이터베이스 옵션이 OFF로 설정되었는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="28c3f-103">This rule checks whether the AUTO_SHRINK database option is set to OFF.</span></span> <span data-ttu-id="28c3f-104">데이터베이스를 자주 축소 및 확장하면 물리적 조각화가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28c3f-104">Frequently shrinking and expanding a database can lead to physical fragmentation.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="28c3f-105">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="28c3f-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="28c3f-106">AUTO_SHRINK 데이터베이스 옵션을 OFF로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="28c3f-106">Set the AUTO_SHRINK database option to OFF.</span></span> <span data-ttu-id="28c3f-107">회수 중인 공간이 이후에 필요하지 않다면 데이터베이스를 수동으로 축소하여 해당 공간을 회수할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28c3f-107">If you know that the space that you are reclaiming will not be needed in the future, you can reclaim the space by manually shrinking the database.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="28c3f-108">참조 항목</span><span class="sxs-lookup"><span data-stu-id="28c3f-108">For More Information</span></span>  
 <span data-ttu-id="28c3f-109">Microsoft 기술 자료 문서 [315512](https://go.microsoft.com/fwlink/?linkid=117750)</span><span class="sxs-lookup"><span data-stu-id="28c3f-109">Microsoft Knowledge Base article [315512](https://go.microsoft.com/fwlink/?linkid=117750)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c3f-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28c3f-110">See Also</span></span>  
 [<span data-ttu-id="28c3f-111">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="28c3f-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
