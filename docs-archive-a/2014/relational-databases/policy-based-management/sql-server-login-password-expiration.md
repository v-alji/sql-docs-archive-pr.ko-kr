---
title: SQL Server 로그인 암호 만료 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 678e8e9c6b567014bdd49e89d043165bc48d168a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646385"
---
# <a name="sql-server-login-password-expiration"></a><span data-ttu-id="8e427-102">SQL Server 로그인 암호 만료</span><span class="sxs-lookup"><span data-stu-id="8e427-102">SQL Server Login Password Expiration</span></span>
  <span data-ttu-id="8e427-103">이 규칙은 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 "암호 만료"가 설정되었는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="8e427-103">This rule checks whether "Password expiration" of each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is enabled.</span></span> <span data-ttu-id="8e427-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증이 설정되었고 운영 체제가 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]이전 버전인 경우 공격자는 알려진 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 암호를 반복적으로 악용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e427-104">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is enabled and if the operating system version is earlier than [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], an attacker could repeatedly exploit a known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login password.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="8e427-105">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="8e427-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="8e427-106">운영 체제를 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]으로 업그레이드하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8e427-106">We recommend that you upgrade the operating system to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].</span></span>  
  
 <span data-ttu-id="8e427-107">현재 환경에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증이 필요하지 않은 경우 Windows 인증을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8e427-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is not required in your environment, use Windows Authentication.</span></span> <span data-ttu-id="8e427-108">자세한 내용은 [인증 모드 선택](../security/choose-an-authentication-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e427-108">For more information, see [Choose an Authentication Mode](../security/choose-an-authentication-mode.md).</span></span>  
  
 <span data-ttu-id="8e427-109">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에 대해 "암호 만료"를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e427-109">Enable "Password expiration" for all the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="8e427-110">[ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) 을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에 대한 암호 정책을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8e427-110">Use [ALTER LOGIN](/sql/t-sql/statements/alter-login-transact-sql) to configure the password policy for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="8e427-111">참조 항목</span><span class="sxs-lookup"><span data-stu-id="8e427-111">For More Information</span></span>  
 [<span data-ttu-id="8e427-112">암호 정책</span><span class="sxs-lookup"><span data-stu-id="8e427-112">Password Policy</span></span>](../security/password-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="8e427-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e427-113">See Also</span></span>  
 [<span data-ttu-id="8e427-114">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="8e427-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
