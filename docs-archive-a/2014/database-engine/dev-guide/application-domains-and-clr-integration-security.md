---
title: 응용 프로그램 도메인 및 CLR 통합 보안 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 85d6e66b1d51cc9d7c5829b8e83c510bea750e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648545"
---
# <a name="application-domains-and-clr-integration-security"></a><span data-ttu-id="9da0f-102">애플리케이션 도메인 및 CLR 통합 보안</span><span class="sxs-lookup"><span data-stu-id="9da0f-102">Application Domains and CLR Integration Security</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="9da0f-103">는 동일한 애플리케이션 도메인의 동일한 소유자에 속하는 어셈블리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9da0f-103">loads assemblies belonging to the same owner in the same application domain.</span></span> <span data-ttu-id="9da0f-104">동일한 애플리케이션 도메인에서 실행되는 어셈블리 집합으로 인해 어셈블리는 .NET Framework 리플렉션 애플리케이션 프로그래밍 인터페이스나 다른 수단을 사용하여 실행 시 서로를 검색할 수 있으며 런타임에 바인딩된 방식으로 어셈블리를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9da0f-104">By virtue of a set of assemblies running in the same application domain, assemblies are able to discover each other at execution time using the.NET Framework reflection application programming interfaces or other means, and can call into them in late-bound fashion.</span></span> <span data-ttu-id="9da0f-105">이러한 호출은 동일한 소유자에 속하는 어셈블리에 대해 수행되기 때문에 해당 호출에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용 권한이 검사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9da0f-105">Because such calls are occurring against assemblies belonging to the same owner, there are no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permissions checked for these calls.</span></span> <span data-ttu-id="9da0f-106">애플리케이션 도메인의 어셈블리 배치 체계는 주로 확장성, 보안 및 격리 목적에 맞게 디자인되어 있으며 이후 릴리스에서 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9da0f-106">The placement scheme of assemblies in application domains is designed primarily to achieve scalability, security, and isolation goals, and can potentially change in future releases.</span></span> <span data-ttu-id="9da0f-107">따라서 런타임에 바인딩 메커니즘을 통해 동일한 애플리케이션 도메인의 어셈블리를 찾는 것은 피해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da0f-107">Hence, you should not rely on finding assemblies in the same application domain through late-bound mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da0f-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9da0f-108">See Also</span></span>  
 [<span data-ttu-id="9da0f-109">CLR 통합 보안</span><span class="sxs-lookup"><span data-stu-id="9da0f-109">CLR Integration Security</span></span>](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
