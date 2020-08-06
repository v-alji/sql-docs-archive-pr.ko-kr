---
title: 호스트 보호 특성 및 CLR 통합 프로그래밍 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
author: rothja
ms.author: jroth
ms.openlocfilehash: 16ca1e4734e66b0eca85523764739e8f8b32634a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735364"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a><span data-ttu-id="97b71-102">호스트 보호 특성 및 CLR 통합 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="97b71-102">Host Protection Attributes and CLR Integration Programming</span></span>
  <span data-ttu-id="97b71-103">CLR(공용 언어 런타임)은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]부터 시작하여, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]와 같은 CLR 호스트에 유용할 수 있는 특성으로 .NET Framework의 일부인 관리되는 API(응용 프로그래밍 인터페이스)에 주석을 추가하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-103">The common language runtime (CLR) provides a mechanism to annotate managed application programming interfaces (APIs) that are part of the .NET Framework with certain attributes that may be of interest to a host of the CLR, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="97b71-104">이러한 HPA(호스트 보호 특성)의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-104">Examples of such host protection attributes (HPAs) include:</span></span>  
  
-   <span data-ttu-id="97b71-105">`SharedState`: API가 공유 상태(예: 정적 클래스 필드)를 만들거나 관리하는 기능을 노출하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-105">`SharedState`, which indicates whether the API exposes the ability to create or manage shared state (for example, static class fields).</span></span>  
  
-   <span data-ttu-id="97b71-106">`Synchronization`: API가 스레드 간 동기화 기능을 노출하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-106">`Synchronization`, which indicates whether the API exposes the ability to perform synchronization between threads.</span></span>  
  
-   <span data-ttu-id="97b71-107">`ExternalProcessMgmt`: API가 호스트 프로세스 제어 기능을 노출하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-107">`ExternalProcessMgmt`, which indicates whether the API exposes a way to control the host process.</span></span>  
  
 <span data-ttu-id="97b71-108">이러한 특성을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 CAS(코드 액세스 보안)를 통해 호스팅된 환경에서 허용하지 않는 HPA 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-108">Given these attributes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specifies a list of HPAs that are disallowed in the hosted environment through code access security (CAS).</span></span> <span data-ttu-id="97b71-109">CAS 요구 사항은 3가지 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 권한 집합인 `SAFE`, `EXTERNAL_ACCESS` 또는 `UNSAFE` 중 하나에 의해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-109">The CAS requirements are specified by one of three [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permission sets: `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`.</span></span> <span data-ttu-id="97b71-110">이러한 세 보안 수준 중 하나는 `CREATE ASSEMBLY` 문을 사용하여 어셈블리를 서버에 등록할 때 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-110">One of these three security levels is specified when the assembly is registered on the server, using the `CREATE ASSEMBLY` statement.</span></span> <span data-ttu-id="97b71-111">`SAFE` 또는 `EXTERNAL_ACCESS` 권한 집합 내에서 실행되는 코드는 `System.Security.Permissions.HostProtectionAttribute` 특성이 적용된 특정 유형이나 멤버를 사용해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-111">Code executing within the `SAFE` or `EXTERNAL_ACCESS` permission sets must avoid certain types or members that have the `System.Security.Permissions.HostProtectionAttribute` attribute applied.</span></span> <span data-ttu-id="97b71-112">자세한 내용은 [어셈블리 만들기](../clr-integration/assemblies/creating-an-assembly.md) 및 [CLR 통합 프로그래밍 모델 제한](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97b71-112">For more information, see [Creating an Assembly](../clr-integration/assemblies/creating-an-assembly.md) and [CLR Integration Programming Model Restrictions](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md).</span></span>  
  
 <span data-ttu-id="97b71-113">`HostProtectionAttribute`는 호스트가 허용하지 않는 특정 코드 구문을 유형이나 메서드로 식별한다는 점에서 안정성 향상 방법일 뿐 보안 권한은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-113">The `HostProtectionAttribute` is not a security permission as much as a way to improve reliability, in that it identifies specific code constructs, either types or methods, that the host may disallow.</span></span> <span data-ttu-id="97b71-114">`HostProtectionAttribute`를 사용하면 호스트의 안정성을 보호하도록 돕는 프로그래밍 모델이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-114">The use of the `HostProtectionAttribute` enforces a programming model that helps protect the stability of the host.</span></span>  
  
## <a name="host-protection-attributes"></a><span data-ttu-id="97b71-115">호스트 보호 특성</span><span class="sxs-lookup"><span data-stu-id="97b71-115">Host Protection Attributes</span></span>  
 <span data-ttu-id="97b71-116">HPA는 호스트 프로그래밍 모델에 맞지 않고 다음과 같이 안정성 위협의 증가 수준을 나타내는 형식이나 멤버를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-116">HPAs identify types or members that do not fit the host programming model and represent the following increasing levels of reliability threat:</span></span>  
  
-   <span data-ttu-id="97b71-117">심각하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-117">Are otherwise benign.</span></span>  
  
-   <span data-ttu-id="97b71-118">서버에서 관리하는 사용자 코드를 불안정하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-118">Could lead to destabilization of server-managed user code.</span></span>  
  
-   <span data-ttu-id="97b71-119">서버 프로세스 자체를 불안정하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-119">Could lead to destabilization of the server process itself.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="97b71-120">값이,,,,,,, `HostProtectionAttribute` 또는 인 열거형을 지정 하는가 있는 형식 또는 멤버의 사용을 허용 하지 `System.Security.Permissions.HostProtectionResource` `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` `SharedState` `Synchronization` `UI` 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-120">disallows the use of a type or member that has a `HostProtectionAttribute` that specifies a `System.Security.Permissions.HostProtectionResource` enumeration with a value of `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, `SharedState`, `Synchronization`, or `UI`.</span></span> <span data-ttu-id="97b71-121">이로 인해 상태를 공유할 수 있게 하거나, 동기화를 수행하거나, 종료할 때 리소스 누출을 일으키거나 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스의 무결성에 영향을 주는 멤버를 어셈블리가 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-121">This prevents the assemblies from calling members that enable sharing state, perform synchronization, might cause a resource leak on termination, or affect the integrity of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span>  
  
### <a name="disallowed-types-and-members"></a><span data-ttu-id="97b71-122">허용되지 않는 유형 및 멤버</span><span class="sxs-lookup"><span data-stu-id="97b71-122">Disallowed Types and Members</span></span>  
 <span data-ttu-id="97b71-123">다음 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 `HostProtectionResource` 값이 허용되지 않는 유형과 멤버를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-123">The following topics identify types and members whose `HostProtectionResource` values are disallowed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97b71-124">이러한 항목에 있는 목록은 지원되는 어셈블리에서 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-124">The lists in these topics were generated from the supported assemblies.</span></span>  <span data-ttu-id="97b71-125">자세한 내용은 [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97b71-125">For more information, see [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97b71-126">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="97b71-126">In This Section</span></span>  
 [<span data-ttu-id="97b71-127">Microsoft.VisualBasic.dll에 허용되지 않는 유형 및 멤버</span><span class="sxs-lookup"><span data-stu-id="97b71-127">Disallowed Types and Members in Microsoft.VisualBasic.dll</span></span>](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 <span data-ttu-id="97b71-128">HPA 값이 허용되지 않는 Microsoft.VisualBasic.dll의 유형 및 멤버가 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-128">Lists the types and members in Microsoft.VisualBasic.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="97b71-129">mscorlib.dll에 허용되지 않는 유형 및 멤버</span><span class="sxs-lookup"><span data-stu-id="97b71-129">Disallowed Types and Members in mscorlib.dll</span></span>](disallowed-types-and-members-in-mscorlib-dll.md)  
 <span data-ttu-id="97b71-130">HPA 값이 허용되지 않는 mscorlib.dll의 유형 및 멤버를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-130">Lists the types and members in mscorlib.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="97b71-131">Disallowed Types and Members In System.dll</span><span class="sxs-lookup"><span data-stu-id="97b71-131">Disallowed Types and Members in System.dll</span></span>](disallowed-types-and-members-in-system-dll.md)  
 <span data-ttu-id="97b71-132">HPA 값이 허용되지 않는 System.dll의 유형 및 멤버를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-132">Lists the types and members in System.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="97b71-133">System.Data.dll에 허용되지 않는 유형 및 멤버</span><span class="sxs-lookup"><span data-stu-id="97b71-133">Disallowed Types and Members in System.Data.dll</span></span>](disallowed-types-and-members-in-system-data-dll.md)  
 <span data-ttu-id="97b71-134">HPA 값이 허용되지 않는 System.Data.dll의 유형 및 멤버를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-134">Lists the types and members in System.Data.dll whose HPA values are disallowed.</span></span>  
  
 [<span data-ttu-id="97b71-135">System.Core.dll에 허용되지 않는 유형 및 멤버</span><span class="sxs-lookup"><span data-stu-id="97b71-135">Disallowed Types and Members in System.Core.dll</span></span>](disallowed-types-and-members-in-system-core-dll.md)  
 <span data-ttu-id="97b71-136">HPA 값이 허용되지 않는 System.Core.dll의 유형 및 멤버를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97b71-136">Lists the types and members in System.Core.dll whose HPA values are disallowed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b71-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97b71-137">See Also</span></span>  
 <span data-ttu-id="97b71-138">[CLR 통합 코드 액세스 보안](../clr-integration/security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="97b71-138">[CLR Integration Code Access Security](../clr-integration/security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="97b71-139">[CLR 통합 프로그래밍 모델 제한 사항](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md) </span><span class="sxs-lookup"><span data-stu-id="97b71-139">[CLR Integration Programming Model Restrictions](../clr-integration/database-objects/clr-integration-programming-model-restrictions.md) </span></span>  
 [<span data-ttu-id="97b71-140">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="97b71-140">Creating an Assembly</span></span>](../clr-integration/assemblies/creating-an-assembly.md)  
  
  
