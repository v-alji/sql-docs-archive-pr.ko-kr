---
title: 가장 및 CLR 통합 보안 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- execution context [CLR integration]
- user impersonation [CLR integration]
- context [CLR integration]
ms.assetid: 1495a7af-2248-4cee-afdb-9269fb3a7774
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2313733c5a24f28c44571dd230ddc58fc9a1264
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742503"
---
# <a name="impersonation-and-clr-integration-security"></a><span data-ttu-id="de9ea-102">가장 및 CLR 통합 보안</span><span class="sxs-lookup"><span data-stu-id="de9ea-102">Impersonation and CLR Integration Security</span></span>
  <span data-ttu-id="de9ea-103">관리 코드에서 외부 리소스를 액세스할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 루틴이 실행되고 있는 현재 실행 컨텍스트를 자동으로 가장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-103">When managed code accesses external resources, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not automatically impersonate the current execution context under which the routine is executing.</span></span> <span data-ttu-id="de9ea-104">`EXTERNAL_ACCESS` 및 `UNSAFE` 어셈블리의 코드에서는 현재 실행 컨텍스트를 명시적으로 가장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-104">Code in `EXTERNAL_ACCESS` and `UNSAFE` assemblies can explicitly impersonate the current execution context.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de9ea-105">가장의 동작 변경 내용에 대 한 자세한 내용은 [2014 SQL Server 데이터베이스 엔진 기능에 대 한 주요 변경 내용](../breaking-changes-to-database-engine-features-in-sql-server-2016.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="de9ea-105">For information on behavior changes in impersonation, see [Breaking Changes to Database Engine Features in SQL Server 2014](../breaking-changes-to-database-engine-features-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="de9ea-106">In-process 데이터 액세스 공급자는 현재 보안 컨텍스트와 연관된 토큰을 검색하는 데 사용할 수 있는 응용 프로그래밍 인터페이스 `SqlContext.WindowsIdentity`를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-106">The in-process data access provider provides an application programming interface, `SqlContext.WindowsIdentity`, that can be used to retrieve the token associated with the current security context.</span></span> <span data-ttu-id="de9ea-107">`EXTERNAL_ACCESS` 및 `UNSAFE` 어셈블리의 관리 코드에서는 이 메서드를 사용하여 컨텍스트를 검색할 수 있고 .NET Framework `WindowsIdentity.Impersonate` 메서드를 사용하여 해당 컨텍스트를 가장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-107">Managed code in `EXTERNAL_ACCESS` and `UNSAFE` assemblies can use this method to retrieve the context and use the .NET Framework `WindowsIdentity.Impersonate` method to impersonate that context.</span></span> <span data-ttu-id="de9ea-108">사용자 코드에서 명시적으로 가장할 때는 다음과 같은 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-108">The following restrictions apply when user code explicitly impersonates:</span></span>  
  
-   <span data-ttu-id="de9ea-109">관리 코드가 가장된 상태에 있는 경우 in-process 데이터 액세스가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-109">In-process data access is not allowed when managed code is in an impersonated state.</span></span> <span data-ttu-id="de9ea-110">코드에서 가장을 실행 취소한 다음 in-process 데이터 액세스를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-110">Code can undo impersonation and then call in-process data access.</span></span> <span data-ttu-id="de9ea-111">이를 위해서는 원래 `WindowsImpersonationContext` 메서드의 반환 값(`Impersonate` 개체)을 저장하고 이 `Undo`에서 `WindowsImpersonationContext` 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-111">Note that this requires storing the return value (a `WindowsImpersonationContext` object) of the original `Impersonate` method, and calling the `Undo` method on this `WindowsImpersonationContext`.</span></span>  
  
     <span data-ttu-id="de9ea-112">이 제한 사항은 in-process 데이터 액세스가 항상 세션에 대해 유효한 현재 보안 컨텍스트의 컨텍스트에서 발생한다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-112">This restriction means that when in-process data access occurs, it is always in the context of the current security context in effect for the session.</span></span> <span data-ttu-id="de9ea-113">이 사항은 관리 코드 내에서 명시적 가장으로 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-113">It cannot be modified by explicit impersonation within managed code.</span></span>  
  
-   <span data-ttu-id="de9ea-114">`UNSAFE` 어셈블리를 통해 스레드를 만들고 코드를 비동기적으로 실행하는 것과 같이 관리 코드를 비동기적으로 실행하고 있는 경우에는 in-process 데이터 액세스가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-114">For managed code executing asynchronously (for example, through `UNSAFE` assemblies creating threads and running code asynchronously), in-process data access is never allowed.</span></span> <span data-ttu-id="de9ea-115">이는 가장을 사용하는 경우와 사용하지 않는 경우에 모두 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-115">This is true whether or not there is impersonation.</span></span>  
  
 <span data-ttu-id="de9ea-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 다른 가장된 컨텍스트에서 코드가 실행되고 있는 경우 in-process 데이터 액세스 호출을 수행할 수 없습니다. In-process 데이터 액세스를 호출하기 전에 먼저 가장 컨텍스트를 실행 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-116">When code is running in an impersonated context that is different from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it cannot perform in-process data access calls; it should undo the impersonation context before making in-process data access calls.</span></span> <span data-ttu-id="de9ea-117">관리 코드에서 in-process 데이터 액세스를 수행하는 경우 관리 코드에 대한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 진입점의 원래 실행 컨텍스트가 항상 권한 부여를 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-117">When in-process data access is made from managed code, the original execution context of the [!INCLUDE[tsql](../../includes/tsql-md.md)] entry point into the managed code is always used for authorization.</span></span>  
  
 <span data-ttu-id="de9ea-118">`EXTERNAL_ACCESS` 어셈블리와 `UNSAFE` 어셈블리는 모두 앞에서 설명한 대로 현재 보안 컨텍스트를 자발적으로 가장하지 않는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정을 사용하여 운영 체제 리소스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-118">Both `EXTERNAL_ACCESS` assemblies and `UNSAFE` assemblies access operating system resources with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account, unless they voluntarily impersonate the current security context as previously described.</span></span> <span data-ttu-id="de9ea-119">따라서 `EXTERNAL_ACCESS` 어셈블리의 작성자에게는 `SAFE` 로그인 수준 권한으로 지정되는 `EXTERNAL ACCESS` 어셈블리보다 높은 신뢰 수준이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-119">Because of this, the authors of `EXTERNAL_ACCESS` assemblies require a higher level of trust than those of `SAFE` assemblies, which is specified by the `EXTERNAL ACCESS` login-level permission.</span></span> <span data-ttu-id="de9ea-120">따라서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정에서 코드를 실행하도록 트러스트된 로그인에게만 `EXTERNAL ACCESS` 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9ea-120">Only logins who are trusted to run code under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account should be granted the `EXTERNAL ACCESS` permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9ea-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de9ea-121">See Also</span></span>  
 <span data-ttu-id="de9ea-122">[CLR 통합 보안](../../relational-databases/clr-integration/security/clr-integration-security.md) </span><span class="sxs-lookup"><span data-stu-id="de9ea-122">[CLR Integration Security](../../relational-databases/clr-integration/security/clr-integration-security.md) </span></span>  
 [<span data-ttu-id="de9ea-123">연결에 대한 가장 및 자격 증명</span><span class="sxs-lookup"><span data-stu-id="de9ea-123">Impersonation and Credentials for Connections</span></span>](../../relational-databases/clr-integration/data-access/impersonation-and-credentials-for-connections.md)  
  
  
