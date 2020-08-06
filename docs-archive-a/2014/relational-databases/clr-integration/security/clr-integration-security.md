---
title: CLR 통합 보안 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- authorization [CLR integration]
- common language runtime [SQL Server], security
- database objects [CLR integration], security
ms.assetid: 05d7a471-c5d5-4730-b903-e4edc8157bb4
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d99d32a061d8fe78a8ac3642a503cceb45f3809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649580"
---
# <a name="clr-integration-security"></a><span data-ttu-id="51010-102">CLR 통합 보안</span><span class="sxs-lookup"><span data-stu-id="51010-102">CLR Integration Security</span></span>
  <span data-ttu-id="51010-103">[!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)]Clr (공용 언어 런타임)의 보안 모델은 다른 형식의 clr 및 [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] 서버에서 실행 되는 다른 clr 개체 또는 문 내에서 실행 되는 clr이 아닌 개체 간 액세스를 관리 하 고 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-103">The security model of the [!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)] common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] statement or another CLR object running in the server.</span></span> <span data-ttu-id="51010-104">개체 간의 호출을 링크라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-104">The calls between objects are referred to as links.</span></span> <span data-ttu-id="51010-105">이러한 개체에 대해 수행되는 보안 검사의 유형은 관련된 링크의 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="51010-105">The types of security checks performed on these objects depend on the types of links involved.</span></span>  
  
 <span data-ttu-id="51010-106">CLR 통합 보안 모델의 목표는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="51010-106">The CLR integration security model has the following goals:</span></span>  
  
-   <span data-ttu-id="51010-107">기본적으로에서 관리 되는 사용자 코드를 실행 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-107">By default, running managed user code on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="51010-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 견고성을 손상할 수 있는 작업을 수행하려면 높은 수준의 사용 권한으로 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-108">Performing operations that potentially compromise the robustness of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] should be protected by appropriate high-level permissions.</span></span>  
  
-   <span data-ttu-id="51010-109">관리되는 사용자 코드에서 데이터베이스의 사용자 데이터나 다른 사용자 코드에 무단으로 액세스하지 못하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-109">Managed user code should not gain unauthorized access to user data or other user code in the database.</span></span> <span data-ttu-id="51010-110">사용자 정의 코드는 해당 코드를 호출한 사용자 세션의 보안 컨텍스트에서 해당 보안 컨텍스트에 대한 올바른 권한을 사용하여 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-110">User-defined code should run under the security context of the user-session that invoked it, and with the correct privileges for that security context.</span></span>  
  
-   <span data-ttu-id="51010-111">사용자 코드를 로컬 데이터 액세스 및 계산용으로만 사용하여 사용자 코드에서 서버 외부의 리소스에 액세스하지 못하도록 제어해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-111">There should be controls for restricting user code from accessing any resources outside the server, using it strictly for local data access and computation.</span></span>  
  
-   <span data-ttu-id="51010-112">사용자 정의 코드가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 프로세스에서 실행된다는 것 때문에 시스템 리소스에 무단으로 액세스할 수 있게 되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51010-112">User-defined code should not be able to gain unauthorized access to system resources by virtue of running in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="51010-113">CLR의 코드 액세스 기반 보안 모델을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-113">with the code access-based security model of the CLR.</span></span> <span data-ttu-id="51010-114">이러한 통합된 보안 방법의 일부 이점에 대해 이 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-114">Some of the advantages of this combined approach to security are discussed in this section.</span></span>  
  
 <span data-ttu-id="51010-115">다음 표에서는 이 섹션에서 다루는 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-115">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="51010-116">CLR 통합 코드 액세스 보안</span><span class="sxs-lookup"><span data-stu-id="51010-116">CLR Integration Code Access Security</span></span>](clr-integration-code-access-security.md)  
 <span data-ttu-id="51010-117">관리 코드에 대한 CAS(코드 액세스 보안) 모델을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-117">Discusses the code access security (CAS) model for managed code.</span></span>  
  
 [<span data-ttu-id="51010-118">호스트 보호 특성 및 CLR 통합 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="51010-118">Host Protection Attributes and CLR Integration Programming</span></span>](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 <span data-ttu-id="51010-119">SAFE 및 EXTERNAL_ACCESS 어셈블리에서 허용되지 않는 HPA(호스트 보호 특성)에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-119">Provides information about the host protection attribute (HPA) values that are disallowed in SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
 [<span data-ttu-id="51010-120">CLR 통합 보안의 링크</span><span class="sxs-lookup"><span data-stu-id="51010-120">Links in CLR Integration Security</span></span>](../../../database-engine/dev-guide/links-in-clr-integration-security.md)  
 <span data-ttu-id="51010-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 사용자 코드 조각이 상호 호출하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-121">Describes how pieces of user-code can call each other in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="51010-122">가장 및 CLR 통합 보안</span><span class="sxs-lookup"><span data-stu-id="51010-122">Impersonation and CLR Integration Security</span></span>](../../../database-engine/dev-guide/impersonation-and-clr-integration-security.md)  
 <span data-ttu-id="51010-123">관리 코드에서 가장을 사용하여 외부 리소스에 액세스하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-123">Discusses how managed code accesses external resources using impersonation.</span></span>  
  
 [<span data-ttu-id="51010-124">부분적으로 신뢰할 수 있는 호출자 허용</span><span class="sxs-lookup"><span data-stu-id="51010-124">Allowing Partially Trusted Callers</span></span>](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
 <span data-ttu-id="51010-125">관리되는 메서드에서 다른 어셈블리에 포함된 클래스의 메서드를 호출할 때 발생하는 문제를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-125">Discusses issues that arise when a managed method invokes a method in a class contained in another assembly.</span></span>  
  
 [<span data-ttu-id="51010-126">애플리케이션 도메인 및 CLR 통합 보안</span><span class="sxs-lookup"><span data-stu-id="51010-126">Application Domains and CLR Integration Security</span></span>](../../../database-engine/dev-guide/application-domains-and-clr-integration-security.md)  
 <span data-ttu-id="51010-127">애플리케이션 도메인에 어셈블리를 로드하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51010-127">Describes how assemblies are loaded into application domains.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51010-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51010-128">See Also</span></span>  
 [<span data-ttu-id="51010-129">CLR 통합 어셈블리 관리</span><span class="sxs-lookup"><span data-stu-id="51010-129">Managing CLR Integration Assemblies</span></span>](../assemblies/managing-clr-integration-assemblies.md)  
  
  
