---
title: 신뢰할 수 있는 비트 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 062a63dd52f4641a0ddfcbc20cb9bad3cce6dc61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648994"
---
# <a name="trustworthy-bit"></a><span data-ttu-id="b3f95-102">신뢰할 수 있는 비트</span><span class="sxs-lookup"><span data-stu-id="b3f95-102">Trustworthy Bit</span></span>
  <span data-ttu-id="b3f95-103">이 규칙은 데이터베이스의 dbo 역할이 sysadmin 고정 서버 역할에 할당되어 있고 데이터베이스의 신뢰할 수 있는 비트가 ON으로 설정되었는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f95-103">This rule determines whether the dbo role for a database is assigned to the sysadmin fixed server role and the database has its trustworthy bit set to ON.</span></span>  
  
 <span data-ttu-id="b3f95-104">이러한 조건이 충족될 경우 권한이 있는 데이터베이스 사용자가 권한을 sysadmin 역할로 승격할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3f95-104">If these conditions are met, a privileged database user can elevate privileges to the sysadmin role.</span></span> <span data-ttu-id="b3f95-105">이 역할에서 사용자는 시스템을 손상시킬 수 있는 안전하지 않은 어셈블리를 만들고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3f95-105">In this role, the user can create and run unsafe assemblies that compromise the system.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="b3f95-106">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="b3f95-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="b3f95-107">신뢰할 수 있는 비트를 OFF로 설정하거나 dbo 데이터베이스 역할에서 sysadmin 권한을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b3f95-107">Turn off the trustworthy bit or revoke sysadmin permissions from the dbo database role.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="b3f95-108">참조 항목</span><span class="sxs-lookup"><span data-stu-id="b3f95-108">For More Information</span></span>  
 [<span data-ttu-id="b3f95-109">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b3f95-109">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="b3f95-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3f95-110">See Also</span></span>  
 [<span data-ttu-id="b3f95-111">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="b3f95-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
