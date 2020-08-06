---
title: common criteria compliance enabled 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- common criteria compliance
helpviewer_keywords:
- CC (common criteria) [Database Engine]
- common criteria compliance [Database Engine]
- Risidual Information Protection [Database Engine]
- RIP (Residual Information Protection)
ms.assetid: 61766eea-c450-408d-af33-fbe7ef8c9ff2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6722d05351b8b9e80240abb4edef0633a97b6da0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646649"
---
# <a name="common-criteria-compliance-enabled-server-configuration-option"></a><span data-ttu-id="a2b2c-102">common criteria compliance enabled 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="a2b2c-102">common criteria compliance enabled Server Configuration Option</span></span>
  <span data-ttu-id="a2b2c-103">common criteria compliance enabled 옵션은 Common Criteria에 필요한 다음 요소를 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-103">The common criteria compliance enabled option enables the following elements that are required for the Common Criteria.</span></span>  
  
|<span data-ttu-id="a2b2c-104">조건</span><span class="sxs-lookup"><span data-stu-id="a2b2c-104">Criteria</span></span>|<span data-ttu-id="a2b2c-105">Description</span><span class="sxs-lookup"><span data-stu-id="a2b2c-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a2b2c-106">RIP(잔여 정보 보호)</span><span class="sxs-lookup"><span data-stu-id="a2b2c-106">Residual Information Protection (RIP)</span></span>|<span data-ttu-id="a2b2c-107">RIP를 사용하는 경우 메모리를 새 리소스에 다시 할당하기 전에 알려진 비트 패턴을 사용하여 메모리 할당을 덮어써야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-107">RIP requires a memory allocation to be overwritten with a known pattern of bits before memory is reallocated to a new resource.</span></span> <span data-ttu-id="a2b2c-108">RIP 표준이 충족되면 보안이 향상될 수 있지만 메모리 할당을 덮어쓰는 동안 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-108">Meeting the RIP standard can contribute to improved security; however, overwriting the memory allocation can slow performance.</span></span> <span data-ttu-id="a2b2c-109">common criteria compliance enabled 옵션을 설정하면 덮어쓰기가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-109">After the common criteria compliance enabled option is enabled, the overwriting occurs.</span></span>|  
|<span data-ttu-id="a2b2c-110">로그인 통계를 확인할 수 있는 기능</span><span class="sxs-lookup"><span data-stu-id="a2b2c-110">The ability to view login statistics</span></span>|<span data-ttu-id="a2b2c-111">common criteria compliance enabled 옵션을 설정하면 로그인 감사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-111">After the common criteria compliance enabled option is enabled, login auditing is enabled.</span></span> <span data-ttu-id="a2b2c-112">사용자가 성공적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 로그인할 때마다 마지막으로 성공한 로그인 시간, 마지막으로 실패한 로그인 시간 및 마지막으로 성공한 로그인 시간과 현재 로그인 시간 사이의 시도 횟수에 대한 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-112">Each time a user successfully logs in to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], information about the last successful login time, the last unsuccessful login time, and the number of attempts between the last successful and current login times is made available.</span></span> <span data-ttu-id="a2b2c-113">이러한 로그인 통계는 [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) 동적 관리 뷰를 쿼리하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-113">These login statistics can be viewed by querying the [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) dynamic management view.</span></span>|  
|<span data-ttu-id="a2b2c-114">열 GRANT가 테이블 DENY를 재정의하지 않아야 함</span><span class="sxs-lookup"><span data-stu-id="a2b2c-114">That column GRANT should not override table DENY</span></span>|<span data-ttu-id="a2b2c-115">common criteria compliance enabled 옵션을 설정하면 테이블 수준 DENY가 열 수준 GRANT보다 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-115">After the common criteria compliance enabled option is enabled, a table-level DENY takes precedence over a column-level GRANT.</span></span> <span data-ttu-id="a2b2c-116">이 옵션을 설정하지 않으면 열 수준 GRANT가 테이블 수준 DENY보다 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-116">When the option is not enabled, a column-level GRANT takes precedence over a table-level DENY.</span></span>|  
  
 <span data-ttu-id="a2b2c-117">common criteria compliance enabled 옵션은 고급 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-117">The common criteria compliance enabled option is an advanced option.</span></span> <span data-ttu-id="a2b2c-118">Common Criteria는 Enterprise Edition 및 Datacenter Edition에 대해서만 평가되고 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-118">Common criteria is only evaluated and certified for the Enterprise edition and Datacenter edition.</span></span> <span data-ttu-id="a2b2c-119">Common Criteria 인증의 최신 상태는 [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) 웹 사이트를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-119">For the latest status of common criteria certification, see the [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) Web site.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a2b2c-120">common criteria compliance enabled 옵션을 설정하는 것 외에도 Common Criteria EAL4+(Evaluation Assurance Level 4+)를 준수하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 구성하는 스크립트를 다운로드하여 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-120">In addition to enabling the common criteria compliance enabled option, you also must download and run a script that finishes configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to comply with Common Criteria Evaluation Assurance Level 4+ (EAL4+).</span></span> <span data-ttu-id="a2b2c-121">이 스크립트는 [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) 웹 사이트에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-121">You can download this script from the [Microsoft SQL Server Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319) Web site.</span></span>  
  
 <span data-ttu-id="a2b2c-122">sp_configure 시스템 저장 프로시저를 사용하여 설정을 변경하는 경우에는 show advanced options를 1로 설정할 때만 common criteria compliance enabled를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-122">If you are using the sp_configure system stored procedure to change the setting, you can change common criteria compliance enabled only when show advanced options is set to 1.</span></span> <span data-ttu-id="a2b2c-123">이 설정은 서버를 다시 시작한 후에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-123">The setting takes effect after the server is restarted.</span></span> <span data-ttu-id="a2b2c-124">가능한 값은 0과 1입니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-124">The possible values are 0 and 1:</span></span>  
  
-   <span data-ttu-id="a2b2c-125">0은 Common Criteria 준수를 설정하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-125">0 indicates that common criteria compliance is not enabled.</span></span> <span data-ttu-id="a2b2c-126">이것이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-126">This is the default.</span></span>  
  
-   <span data-ttu-id="a2b2c-127">1은 Common Criteria 준수를 설정함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-127">1 indicates that common criteria compliance is enabled.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a2b2c-128">예제</span><span class="sxs-lookup"><span data-stu-id="a2b2c-128">Examples</span></span>  
 <span data-ttu-id="a2b2c-129">다음 예에서는 Common Criteria 준수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a2b2c-129">The following example enables common criteria compliance.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'common criteria compliance enabled', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2b2c-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2b2c-130">See Also</span></span>  
 [<span data-ttu-id="a2b2c-131">서버 구성 옵션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2b2c-131">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
