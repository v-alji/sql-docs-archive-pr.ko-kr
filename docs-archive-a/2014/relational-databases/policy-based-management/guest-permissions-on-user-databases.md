---
title: 사용자 데이터베이스에 대한 게스트 사용 권한 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 344c5fd0639876998f1585c32fac5f7599f664e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646981"
---
# <a name="guest-permissions-on-user-databases"></a><span data-ttu-id="6869d-102">사용자 데이터베이스에 대한 게스트 사용 권한</span><span class="sxs-lookup"><span data-stu-id="6869d-102">Guest Permissions on User Databases</span></span>
  <span data-ttu-id="6869d-103">이 규칙은 게스트 사용자에게 데이터베이스에 대한 액세스 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6869d-103">This rule determines whether the guest user has permission to access the database.</span></span> <span data-ttu-id="6869d-104">이 규칙은 사용자 데이터베이스에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6869d-104">This rule applies to user databases only.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="6869d-105">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="6869d-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="6869d-106">필요한 경우가 아니라면 게스트 사용자의 데이터베이스 액세스 권한을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="6869d-106">Revoke the guest user permission to access the database if it is not required.</span></span>  
  
 <span data-ttu-id="6869d-107">guest 사용자는 삭제할 수 없지만 master, tempdb 또는 msdb 이외의 데이터베이스 내에서 REVOKE CONNECT FROM GUEST를 실행하면 guest 사용자의 CONNECT 권한이 취소되므로 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6869d-107">The guest user cannot be dropped, but guest user can be disabled by revoking its CONNECT permission by executing REVOKE CONNECT FROM GUEST within any database other than master, tempdb, or msdb.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="6869d-108">참조 항목</span><span class="sxs-lookup"><span data-stu-id="6869d-108">For More Information</span></span>  
 [<span data-ttu-id="6869d-109">SQL Server 보안 설정</span><span class="sxs-lookup"><span data-stu-id="6869d-109">Securing SQL Server</span></span>](../security/securing-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="6869d-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6869d-110">See Also</span></span>  
 [<span data-ttu-id="6869d-111">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="6869d-111">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
