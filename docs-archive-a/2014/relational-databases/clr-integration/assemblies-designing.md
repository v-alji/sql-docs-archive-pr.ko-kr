---
title: 어셈블리 디자인 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- designing assemblies [SQL Server]
- assemblies [CLR integration], designing
ms.assetid: 9c07f706-6508-41aa-a4d7-56ce354f9061
author: rothja
ms.author: jroth
ms.openlocfilehash: 785ab80a529140a52ec18ef96ccaaeafd03698cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735359"
---
# <a name="designing-assemblies"></a><span data-ttu-id="8675e-102">어셈블리 디자인</span><span class="sxs-lookup"><span data-stu-id="8675e-102">Designing Assemblies</span></span>
  <span data-ttu-id="8675e-103">이 항목에서는 어셈블리를 디자인할 때 고려해야 할 다음 요소들에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-103">This topic describes the following factors you should consider when you design assemblies:</span></span>  
  
-   <span data-ttu-id="8675e-104">어셈블리 패키징</span><span class="sxs-lookup"><span data-stu-id="8675e-104">Packaging assemblies</span></span>  
  
-   <span data-ttu-id="8675e-105">어셈블리 보안 관리</span><span class="sxs-lookup"><span data-stu-id="8675e-105">Managing assembly security</span></span>  
  
-   <span data-ttu-id="8675e-106">어셈블리에 대한 제한</span><span class="sxs-lookup"><span data-stu-id="8675e-106">Restrictions on assemblies</span></span>  
  
## <a name="packaging-assemblies"></a><span data-ttu-id="8675e-107">어셈블리 패키징</span><span class="sxs-lookup"><span data-stu-id="8675e-107">Packaging Assemblies</span></span>  
 <span data-ttu-id="8675e-108">어셈블리에는 해당 클래스 및 메서드에 두 개 이상의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 루틴 및 유형에 대한 기능이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-108">An assembly can contain functionality for more than one [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] routine or type in its classes and methods.</span></span> <span data-ttu-id="8675e-109">대부분의 경우, 특히 이러한 루틴의 메서드가 상호 호출하는 클래스를 공유하는 경우에는 관련된 기능을 수행하는 루틴의 기능을 같은 어셈블리 내에 패키징하는 것이 바람직합니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-109">Most of the time, it makes sense to package the functionality of routines that perform related functions within the same assembly, especially if these routines share classes whose methods call one another.</span></span> <span data-ttu-id="8675e-110">예를 들어 CLR(공용 언어 런타임) 트리거와 CLR 저장 프로시저에 대한 데이터 항목 관리 태스크를 수행하는 클래스를 같은 어셈블리에 패키징할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-110">For example, classes that perform data entry management tasks for common language runtime (CLR) triggers and CLR stored procedures can be packaged in the same assembly.</span></span> <span data-ttu-id="8675e-111">그 이유는 이러한 클래스에 대한 메서드가 덜 관련된 태스크 보다는 상호 호출할 가능성이 높기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-111">This is because the methods for these classes are more likely to call each other than those of less related tasks.</span></span>  
  
 <span data-ttu-id="8675e-112">코드를 어셈블리에 패키징할 때는 다음을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-112">When you are packaging code into assembly, you should consider the following:</span></span>  
  
-   <span data-ttu-id="8675e-113">CLR 사용자 정의 함수에 의존하는 CLR 사용자 정의 유형 및 인덱스는 영구 데이터가 어셈블리에 의존하는 데이터베이스에 포함되도록 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-113">CLR user-defined types and indexes that depend on CLR user-defined functions can cause persisted data to be in the database that depends on the assembly.</span></span> <span data-ttu-id="8675e-114">어셈블리의 코드를 수정하면 데이터베이스에 있는 어셈블리에 의존하는 영구 데이터가 있는 경우 보다 복잡해지는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-114">Modifying the code of an assembly is frequently more complex when there is persisted data that depends on the assembly in the database.</span></span> <span data-ttu-id="8675e-115">따라서 일반적으로 사용자 정의 유형과 사용자 정의 함수를 사용하는 인덱스와 같이 영구 데이터 종속 관계에 의존하는 코드를 이러한 영구 데이터 종속 관계가 없는 코드와 구분하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-115">Therefore, it is generally better to separate code on which persisted data dependencies rely (such as user-defined types and indexes using user-defined functions) from code that does not have such persisted data dependencies.</span></span> <span data-ttu-id="8675e-116">자세한 내용은 [어셈블리 구현](assemblies-implementing.md) 및 [ALTER ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8675e-116">For more information, see [Implementing Assemblies](assemblies-implementing.md) and [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).</span></span>  
  
-   <span data-ttu-id="8675e-117">관리 코드의 조각에 더 높은 사용 권한이 필요한 경우 해당 코드를 높은 사용 권한이 필요하지 않은 코드와 별개의 어셈블리로 구분하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-117">If a piece of managed code requires higher permission, it is better to separate that code into a separate assembly from code that does not require higher permission.</span></span>  
  
## <a name="managing-assembly-security"></a><span data-ttu-id="8675e-118">어셈블리 보안 관리</span><span class="sxs-lookup"><span data-stu-id="8675e-118">Managing Assembly Security</span></span>  
 <span data-ttu-id="8675e-119">관리 코드를 실행할 때 .NET Code Access Security로 보호되는 리소스를 어셈블리에서 어느 정도까지 액세스할 수 있는지를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-119">You can control how much an assembly can access resources protected by .NET Code Access Security when it runs managed code.</span></span> <span data-ttu-id="8675e-120">이렇게 하려면 어셈블리를 만들거나 수정할 때 SAFE, EXTERNAL_ACCESS 또는 UNSAFE의 세 가지 권한 집합 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-120">You do this by specifying one of three permission sets when you create or modify an assembly: SAFE, EXTERNAL_ACCESS, or UNSAFE.</span></span>  
  
### <a name="safe"></a><span data-ttu-id="8675e-121">SAFE</span><span class="sxs-lookup"><span data-stu-id="8675e-121">SAFE</span></span>  
 <span data-ttu-id="8675e-122">SAFE는 기본 사용 권한 집합이며 가장 제한적입니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-122">SAFE is the default permission set and it is the most restrictive.</span></span> <span data-ttu-id="8675e-123">SAFE 권한을 사용하여 어셈블리에서 실행한 코드는 파일, 네트워크, 환경 변수 또는 레지스트리와 같은 외부 시스템 리소스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-123">Code run by an assembly with SAFE permissions cannot access external system resources such as files, the network, environment variables, or the registry.</span></span> <span data-ttu-id="8675e-124">SAFE 코드는 로컬 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스의 데이터에 액세스하거나 로컬 데이터베이스 외부의 리소스에 액세스하지 않는 계산 및 비즈니스 논리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-124">SAFE code can access data from the local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases or perform computations and business logic that do not involve accessing resources outside the local databases.</span></span>  
  
 <span data-ttu-id="8675e-125">대부분의 어셈블리는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 외부에 있는 리소스에 액세스할 필요 없이 계산 및 데이터 관리 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-125">Most assemblies perform computation and data management tasks without having to access resources outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8675e-126">따라서 어셈블리 사용 권한 집합으로 SAFE를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-126">Therefore, we recommend SAFE as the assembly permission set.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="8675e-127">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="8675e-127">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="8675e-128">EXTERNAL_ACCESS를 사용하면 어셈블리에서 파일, 네트워크, 웹 서비스, 환경 변수 및 레지스트리와 같은 특정 외부 시스템 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-128">EXTERNAL_ACCESS allows for assemblies to access certain external system resources such as files, networks, Web services, environmental variables, and the registry.</span></span> <span data-ttu-id="8675e-129">EXTERNAL ACCESS 권한이 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인만 EXTERNAL_ACCESS 어셈블리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-129">Only [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins with EXTERNAL ACCESS permissions can create EXTERNAL_ACCESS assemblies.</span></span>  
  
 <span data-ttu-id="8675e-130">SAFE 및 EXTERNAL_ACCESS 어셈블리에는 검증적으로 안전한 유형의 코드만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-130">SAFE and EXTERNAL_ACCESS assemblies can contain only code that is verifiably type-safe.</span></span> <span data-ttu-id="8675e-131">즉, 이러한 어셈블리에서만 유형 정의에 유효한 잘 정의된 진입점을 통해 클래스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-131">This means that these assemblies can only access classes through well-defined entry points that are valid for the type definition.</span></span> <span data-ttu-id="8675e-132">따라서 이러한 유형은 코드에서 소유하지 않은 메모리 버퍼에 임의로 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-132">Therefore, they cannot arbitrarily access memory buffers not owned by the code.</span></span> <span data-ttu-id="8675e-133">또한 이러한 어셈블리는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 프로세스의 견고성에 악영향을 줄 수 있는 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-133">Additionally, they cannot perform operations that might have an adverse effect on the robustness of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process.</span></span>  
  
### <a name="unsafe"></a><span data-ttu-id="8675e-134">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="8675e-134">UNSAFE</span></span>  
 <span data-ttu-id="8675e-135">UNSAFE는 어셈블리에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 내부 및 외부의 리소스에 대한 무제한적인 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-135">UNSAFE gives assemblies unrestricted access to resources, both within and outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8675e-136">UNSAFE 어셈블리 내에서 실행되는 코드는 비관리 코드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-136">Code that is running from within an UNSAFE assembly can call unmanaged code.</span></span>  
  
 <span data-ttu-id="8675e-137">또한 UNSAFE를 지정하면 어셈블리에 있는 코드에서 CLR 확인 프로그램에 의해 안전하지 않은 유형으로 간주되는 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-137">Also, specifying UNSAFE allows for the code in the assembly to perform operations that are considered type-unsafe by the CLR verifier.</span></span> <span data-ttu-id="8675e-138">이러한 작업은 제어되지 않는 방식으로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 프로세스 공간에서 메모리 버퍼에 액세스할 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-138">These operations can potentially access memory buffers in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process space in an uncontrolled manner.</span></span> <span data-ttu-id="8675e-139">UNSAFE 어셈블리는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 또는 공용 언어 런타임 중 하나의 보안 시스템을 손상시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-139">UNSAFE assemblies can also potentially subvert the security system of either [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or the common language runtime.</span></span> <span data-ttu-id="8675e-140">UNSAFE 권한은 숙련된 개발자 또는 관리자가 가장 신뢰할 수 있는 어셈블리에만 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-140">UNSAFE permissions should be granted only to highly trusted assemblies by experienced developers or administrators.</span></span> <span data-ttu-id="8675e-141">**Sysadmin** 고정 서버 역할의 멤버만 UNSAFE 어셈블리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-141">Only members of the **sysadmin** fixed server role can create UNSAFE assemblies.</span></span>  
  
## <a name="restrictions-on-assemblies"></a><span data-ttu-id="8675e-142">어셈블리에 대한 제한</span><span class="sxs-lookup"><span data-stu-id="8675e-142">Restrictions on Assemblies</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="8675e-143">는 어셈블리를 안정적이고 확장 가능한 방식으로 실행할 수 있도록 보장하기 위해 어셈블리에 있는 관리 코드에 특정 제한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-143">puts certain restrictions on managed code in assemblies to make sure that they can run in a reliable and scalable manner.</span></span> <span data-ttu-id="8675e-144">즉, 서버의 견고성을 손상시킬 수 있는 작업은 SAFE 및 EXTERNAL_ACCESS 어셈블리에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-144">This means that certain operations that can compromise the robustness of the server are not permitted in SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
### <a name="disallowed-custom-attributes"></a><span data-ttu-id="8675e-145">허용되지 않는 사용자 지정 특성</span><span class="sxs-lookup"><span data-stu-id="8675e-145">Disallowed Custom Attributes</span></span>  
 <span data-ttu-id="8675e-146">다음과 같은 사용자 지정 특성으로는 어셈블리에 주석을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-146">Assemblies cannot be annotated with the following custom attributes:</span></span>  
  
```  
System.ContextStaticAttribute  
System.MTAThreadAttribute  
System.Runtime.CompilerServices.MethodImplAttribute  
System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
System.Runtime.Remoting.Contexts.ContextAttribute  
System.Runtime.Remoting.Contexts.SynchronizationAttribute  
System.Runtime.InteropServices.DllImportAttribute   
System.Security.Permissions.CodeAccessSecurityAttribute  
System.STAThreadAttribute  
System.ThreadStaticAttribute  
```  
  
 <span data-ttu-id="8675e-147">또한 SAFE 및 EXTERNAL_ACCESS 어셈블리에는 다음과 같은 사용자 지정 특성으로 주석을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-147">Additionally, SAFE and EXTERNAL_ACCESS assemblies cannot be annotated with the following custom attributes:</span></span>  
  
```  
System.Security.SuppressUnmanagedCodeSecurityAttribute  
System.Security.UnverifiableCodeAttribute  
```  
  
### <a name="disallowed-net-framework-apis"></a><span data-ttu-id="8675e-148">허용되지 않는 .NET Framework API</span><span class="sxs-lookup"><span data-stu-id="8675e-148">Disallowed .NET Framework APIs</span></span>  
 <span data-ttu-id="8675e-149">허용 되지 않는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] **HostProtectionAttributes** 중 하나를 사용 하 여 주석이 추가 된 모든 API는 SAFE 및 EXTERNAL_ACCESS 어셈블리에서 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-149">Any [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] API that is annotated with one of the disallowed **HostProtectionAttributes** cannot be called from SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
```  
eSelfAffectingProcessMgmt  
eSelfAffectingThreading  
eSynchronization  
eSharedState   
eExternalProcessMgmt  
eExternalThreading  
eSecurityInfrastructure  
eMayLeakOnAbort  
eUI  
```  
  
### <a name="supported-net-framework-assemblies"></a><span data-ttu-id="8675e-150">지원되는 .NET Framework 어셈블리</span><span class="sxs-lookup"><span data-stu-id="8675e-150">Supported .NET Framework Assemblies</span></span>  
 <span data-ttu-id="8675e-151">CREATE ASSEMBLY를 사용하여 사용자 지정 어셈블리에서 참조하는 모든 어셈블리를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-151">Any assembly that is referenced by your custom assembly must be loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using CREATE ASSEMBLY.</span></span> <span data-ttu-id="8675e-152">다음 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 어셈블리는 이미 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 로드되어 있으므로 CREATE ASSEMBLY를 사용하지 않아도 사용자 지정 어셈블리에서 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8675e-152">The following [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assemblies are already loaded into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and, therefore, can be referenced by custom assemblies without having to use CREATE ASSEMBLY.</span></span>  
  
```  
custommarshallers.dll  
Microsoft.visualbasic.dll  
Microsoft.visualc.dll  
mscorlib.dll  
system.data.dll  
System.Data.SqlXml.dll  
system.dll  
system.security.dll  
system.web.services.dll  
system.xml.dll  
System.Transactions  
System.Data.OracleClient  
System.Configuration  
```  
  
## <a name="see-also"></a><span data-ttu-id="8675e-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8675e-153">See Also</span></span>  
 <span data-ttu-id="8675e-154">[어셈블리 &#40;데이터베이스 엔진&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="8675e-154">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 [<span data-ttu-id="8675e-155">CLR 통합 보안</span><span class="sxs-lookup"><span data-stu-id="8675e-155">CLR Integration Security</span></span>](security/clr-integration-security.md)  
  
  
