---
title: AUTO_CLOSE 데이터베이스 옵션을 OFF로 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: db6cf5a3f82c3493a8732958594743104fccc968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740847"
---
# <a name="set-the-auto_close-database-option-to-off"></a><span data-ttu-id="d178c-102">AUTO_CLOSE 데이터베이스 옵션을 OFF로 설정</span><span class="sxs-lookup"><span data-stu-id="d178c-102">Set the AUTO_CLOSE Database Option to OFF</span></span>
  <span data-ttu-id="d178c-103">이 규칙은 AUTO_CLOSE 옵션이 OFF로 설정되었는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="d178c-103">This rule checks whether the AUTO_ CLOSE option is set OFF.</span></span> <span data-ttu-id="d178c-104">AUTO_CLOSE가 ON으로 설정된 경우 각 연결 이후에 데이터베이스를 열고 닫는 데 따르는 오버헤드가 증가하여 자주 액세스되는 데이터베이스에서 성능 저하가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d178c-104">When AUTO_CLOSE is set ON, this option can cause performance degradation on frequently accessed databases because of the increased overhead of opening and closing the database after each connection.</span></span> <span data-ttu-id="d178c-105">AUTO_CLOSE는 또한 각 연결 이후에 프로시저 캐시를 플러시합니다.</span><span class="sxs-lookup"><span data-stu-id="d178c-105">AUTO_CLOSE also flushes the procedure cache after each connection.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="d178c-106">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="d178c-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="d178c-107">데이터베이스가 자주 액세스되는 경우 데이터베이스의 AUTO_CLOSE 옵션을 OFF로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d178c-107">If a database is accessed frequently, set the AUTO_CLOSE option to OFF for the database.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="d178c-108">참조 항목</span><span class="sxs-lookup"><span data-stu-id="d178c-108">For More Information</span></span>  
 [<span data-ttu-id="d178c-109">ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d178c-109">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a><span data-ttu-id="d178c-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d178c-110">See Also</span></span>  
 [<span data-ttu-id="d178c-111">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="d178c-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
