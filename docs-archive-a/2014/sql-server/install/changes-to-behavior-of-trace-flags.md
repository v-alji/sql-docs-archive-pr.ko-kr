---
title: 추적 플래그의 동작에 대 한 변경 내용 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- trace flags [SQL Server], behavior changes
ms.assetid: d739df96-2659-4383-8e10-194657632526
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11d71e8401f6b870aaeb3f64f4145b509e3a3fe0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650511"
---
# <a name="changes-to-behavior-of-trace-flags"></a><span data-ttu-id="57ce5-102">추적 플래그의 동작에 대한 변경입니다.</span><span class="sxs-lookup"><span data-stu-id="57ce5-102">Changes to behavior of trace flags</span></span>
  <span data-ttu-id="57ce5-103">한 세션에서 설정한 전역 추적 플래그가 다른 세션에 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="57ce5-103">Global trace flags set by a session take effect in other sessions immediately.</span></span> <span data-ttu-id="57ce5-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]의 일부 추적 플래그는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57ce5-104">Some trace flags from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] do not exist in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="57ce5-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="57ce5-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="57ce5-106">Description</span><span class="sxs-lookup"><span data-stu-id="57ce5-106">Description</span></span>  
 <span data-ttu-id="57ce5-107">업그레이드하기 전에 추적 플래그를 모두 해제하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="57ce5-107">We recommend that you disable all trace flags before you upgrade.</span></span> <span data-ttu-id="57ce5-108">데이터베이스 가용성 또는 복구 모드를 수정 하는 추적 플래그는이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 성공적으로 업그레이드 하지 못하게 할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="57ce5-108">Trace flags that modify the database availability or recovery modes might prevent the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] from successfully upgrading your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="57ce5-109">이러한 추적 플래그는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 필요하고 여전히 유효하다는 것이 확인되면 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ce5-109">You can enable the trace flags after you verify that the trace flags are required and are still valid in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="57ce5-110">추적 플래그를 다시 설정해야 하는 경우에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 추가 테스트를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce5-110">If you must re-enable trace flags, you should perform additional tests on your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="57ce5-111">에서는 전역 및 세션 수준 추적 플래그를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="57ce5-111">supports global and session level trace flags.</span></span> <span data-ttu-id="57ce5-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서는 DBCC TRACEON 명령에 추가 인수 (-1)을 사용하여 추적 플래그를 로컬 또는 전역으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57ce5-112">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], trace flags can be specified as either local or global by using an additional argument (-1) in the DBCC TRACEON command.</span></span> <span data-ttu-id="57ce5-113">이 인수를 지정하지 않으면 기본값은 로컬입니다.</span><span class="sxs-lookup"><span data-stu-id="57ce5-113">If this argument is not specified, the default value is local.</span></span>  
  
 <span data-ttu-id="57ce5-114">또한 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 A 세션에서 설정한 추적 플래그가 기존 B 세션에서 자동으로 적용되지 않습니다. 대신 B 세션에서 처음으로 추적 플래그를 설정한 후에만 적용됩니다. 이 동작은 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 비결정적이지만, A 세션에서 설정한 전역 추적 플래그가 다른 동시 세션에서 즉시 설정되는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 결정적입니다.</span><span class="sxs-lookup"><span data-stu-id="57ce5-114">Also, in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], a trace flag set in session A does not automatically take effect in an already existing session B. Instead, this trace flag takes effect only after the first time any trace flag is set in session B. This behavior is nondeterministic in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] and is deterministic in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, where global trace flags set in session A are set immediately in other concurrent sessions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ce5-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57ce5-115">See Also</span></span>  
 <span data-ttu-id="57ce5-116">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="57ce5-116">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="57ce5-117">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="57ce5-117">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
