---
title: 잠금 구성 옵션의 기본값 유지 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a1d1dcf82d9cd0ef8ef2c15cb68ef78b53a8a54a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646966"
---
# <a name="keep-the-locks-configuration-option-default-value"></a><span data-ttu-id="17bfb-102">잠금 구성 옵션의 기본값 유지</span><span class="sxs-lookup"><span data-stu-id="17bfb-102">Keep the Locks Configuration Option Default Value</span></span>
  <span data-ttu-id="17bfb-103">이 규칙은 잠금 구성 옵션의 값을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="17bfb-103">This rule checks the value of the locks configuration option.</span></span> <span data-ttu-id="17bfb-104">이 옵션은 사용 가능한 잠금의 최대 개수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="17bfb-104">This option determines the maximum number of available locks.</span></span> <span data-ttu-id="17bfb-105">이 옵션은 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 이 잠금에 사용하는 메모리 양을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="17bfb-105">This limits how much memory the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses for locks.</span></span> <span data-ttu-id="17bfb-106">기본 설정은 0을 사용하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 시스템 요구 사항의 변화를 기준으로 동적으로 잠금 구조를 할당하거나 할당 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17bfb-106">The default setting of 0 enables the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to allocate and deallocate lock structures dynamically based on changing system requirements.</span></span>  
  
 <span data-ttu-id="17bfb-107">잠금이 0이 아니면, 일괄 처리 작업이 중지되고, 지정된 값이 초과될 경우 "잠금 부족" 오류 메시지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="17bfb-107">If locks is nonzero, batch jobs will stop, and an "out of locks" error message will be generated, if the value specified is exceeded.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="17bfb-108">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="17bfb-108">Best Practices Recommendations</span></span>  
 <span data-ttu-id="17bfb-109">sp_configure 시스템 저장 프로시저를 다음과 같이 사용하여 잠금 값을 기본 설정으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="17bfb-109">Use the sp_configure system stored procedure to change the value of locks to its default setting by using the following statement:</span></span>  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## <a name="for-more-information"></a><span data-ttu-id="17bfb-110">참조 항목</span><span class="sxs-lookup"><span data-stu-id="17bfb-110">For More Information</span></span>  
 [<span data-ttu-id="17bfb-111">locks 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="17bfb-111">Configure the locks Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [<span data-ttu-id="17bfb-112">sys.dm_tran_locks&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17bfb-112">sys.dm_tran_locks &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
 [<span data-ttu-id="17bfb-113">sys.dm_os_wait_stats&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17bfb-113">sys.dm_os_wait_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)  
  
 [<span data-ttu-id="17bfb-114">Microsoft 기술 자료 문서 271509</span><span class="sxs-lookup"><span data-stu-id="17bfb-114">Microsoft Knowledge Base article 271509</span></span>](https://go.microsoft.com/fwlink/?linkid=117788)  
  
## <a name="see-also"></a><span data-ttu-id="17bfb-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17bfb-115">See Also</span></span>  
 [<span data-ttu-id="17bfb-116">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="17bfb-116">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
