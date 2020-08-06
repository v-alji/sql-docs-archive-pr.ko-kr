---
title: SQL 메일 대신 데이터베이스 메일 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a6a957b65975645bdeb9f55faee4e650b53718b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648983"
---
# <a name="use-database-mail-instead-of-sql-mail"></a><span data-ttu-id="9033b-102">SQL 메일 대신 데이터베이스 메일 사용</span><span class="sxs-lookup"><span data-stu-id="9033b-102">Use Database Mail Instead of SQL Mail</span></span>
  <span data-ttu-id="9033b-103">이 규칙은 sys.configurations 카탈로그 뷰에서 SQL Mail XPs 서버 차원 구성 옵션이 ON으로 설정되었는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="9033b-103">This rule checks the sys.configurations catalog view to determine whether the SQL Mail XPs server-wide configuration option is set to ON.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="9033b-104">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="9033b-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="9033b-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이후 버전에서는 SQL 메일이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="9033b-105">SQL Mail will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9033b-106">새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="9033b-106">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="9033b-107">메일을 보내려면 데이터베이스 메일을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="9033b-107">To send mail, use Database Mail.</span></span>  
  
 <span data-ttu-id="9033b-108">SQL 메일은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스에 대해 in-process로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9033b-108">SQL Mail runs in-process to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="9033b-109">SQL 메일이 다운되면 서버도 다운됩니다.</span><span class="sxs-lookup"><span data-stu-id="9033b-109">If SQL Mail goes down, so does the server.</span></span> <span data-ttu-id="9033b-110">데이터베이스 메일은 개별 프로세스로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 외부에서 실행되며, 확장 가능하고, 프로덕션 서버에 확장 MAPI 클라이언트 구성 요소를 설치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9033b-110">Database Mail runs outside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a separate process, is scalable, and does not require Extended MAPI client components to be installed on the production server.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="9033b-111">참조 항목</span><span class="sxs-lookup"><span data-stu-id="9033b-111">For More Information</span></span>  
 [<span data-ttu-id="9033b-112">데이터베이스 메일</span><span class="sxs-lookup"><span data-stu-id="9033b-112">Database Mail</span></span>](../database-mail/database-mail.md)  
  
## <a name="see-also"></a><span data-ttu-id="9033b-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9033b-113">See Also</span></span>  
 [<span data-ttu-id="9033b-114">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="9033b-114">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
