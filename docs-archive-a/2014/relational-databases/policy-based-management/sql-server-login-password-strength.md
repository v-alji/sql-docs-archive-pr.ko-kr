---
title: SQL Server 로그인 암호 강도 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b0862c3a-926b-490c-a37f-382e50146a3e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5534748fbbf810539f2dcfc22239e4b987cf0f77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729356"
---
# <a name="sql-server-login-password-strength"></a><span data-ttu-id="c9c35-102">SQL Server 로그인 암호 강도</span><span class="sxs-lookup"><span data-stu-id="c9c35-102">SQL Server Login Password Strength</span></span>
  <span data-ttu-id="c9c35-103">이 규칙은 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 "암호 정책 강제 적용"이 설정되었는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="c9c35-103">This rule checks whether "Enforce password policy" of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is enabled.</span></span> <span data-ttu-id="c9c35-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증이 설정되었고 운영 체제가 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]이전 버전인 경우 공격자는 알려진 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 암호를 반복적으로 악용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9c35-104">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is enabled and if the operating system version is earlier than [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], an attacker could repeatedly exploit a known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login password.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="c9c35-105">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="c9c35-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="c9c35-106">운영 체제를 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]으로 업그레이드하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c9c35-106">We recommend that you upgrade the operating system to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].</span></span>  
  
 <span data-ttu-id="c9c35-107">현재 환경에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증이 필요하지 않은 경우 Windows 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c9c35-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is not required in your environment, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="c9c35-108">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에 대해 "암호 정책 강제 적용"을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9c35-108">Enable "Enforce password policy" for all the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="c9c35-109">[ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) 을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에 대한 암호 정책을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c9c35-109">Use [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="c9c35-110">참조 항목</span><span class="sxs-lookup"><span data-stu-id="c9c35-110">For More Information</span></span>  
 [<span data-ttu-id="c9c35-111">암호 정책</span><span class="sxs-lookup"><span data-stu-id="c9c35-111">Password Policy</span></span>](../security/password-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="c9c35-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9c35-112">See Also</span></span>  
 [<span data-ttu-id="c9c35-113">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="c9c35-113">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
