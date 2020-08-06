---
title: CLR 통합 프로그래밍 모델 제한 사항 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: 01a32e1460ad9c49061b39b1bdc419c7cd2f1342
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638843"
---
# <a name="clr-integration-programming-model-restrictions"></a><span data-ttu-id="06a74-102">CLR 통합 프로그래밍 모델 제한 사항</span><span class="sxs-lookup"><span data-stu-id="06a74-102">CLR Integration Programming Model Restrictions</span></span>
  <span data-ttu-id="06a74-103">관리 되는 저장 프로시저나 다른 관리 되는 데이터베이스 개체를 작성 하는 경우에는 관리 되는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 코드 어셈블리에 대 한 검사를 수행 하 고, 문을 사용 하 고, 런타임에를 사용 하 여 수행 하는 특정 코드 검사가 있습니다 `CREATE ASSEMBLY` .</span><span class="sxs-lookup"><span data-stu-id="06a74-103">When you are building a managed stored procedure or other managed database object, there are certain code checks performed by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] performs checks on the managed code assembly when it is first registered in the database, using the `CREATE ASSEMBLY` statement, and also at runtime.</span></span> <span data-ttu-id="06a74-104">실제로 런타임에 접근할 수 없는 코드 경로가 어셈블리에 있을 수 있으므로 관리 코드는 런타임에도 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-104">The managed code is also checked at runtime because in an assembly there may be code paths that may never actually be reached at runtime.</span></span>  <span data-ttu-id="06a74-105">따라서 특히 클라이언트 환경에서 실행되는 '안전하지 않은' 코드가 있는 경우 어셈블리가 차단되지 않고 호스팅된 CLR에서 실행되지 않도록 유연성 있게 타사 어셈블리를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-105">This provides flexibility for registering third party assemblies, especially, so that an assembly wouldn't be blocked where there is 'unsafe' code designed to run in a client environment but would never be executed in the hosted CLR.</span></span> <span data-ttu-id="06a74-106">관리 코드에서 충족 해야 하는 요구 사항은 어셈블리를, 또는로 등록 하 `SAFE` `EXTERNAL_ACCESS` `UNSAFE` 고, `SAFE` 가장 엄격한 하 고, 아래에 나열 되어 있는지 여부에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-106">The requirements that the managed code must meet depend on whether the assembly is registered as `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`, `SAFE` being the strictest, and are listed below.</span></span>  
  
 <span data-ttu-id="06a74-107">관리 코드 어셈블리에 적용되는 제한뿐 아니라 부여되는 코드 보안 권한도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-107">In addition to restrictions being placed on the managed code assemblies, there are also code security permissions that are granted.</span></span> <span data-ttu-id="06a74-108">CLR(공용 언어 런타임)은 관리 코드에 대해 CAS(코드 액세스 보안)라는 보안 모델을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-108">The common language runtime (CLR) supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="06a74-109">이 모델에서는 코드 ID를 기반으로 어셈블리에 사용 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-109">In this model, permissions are granted to assemblies based on the identity of the code.</span></span> <span data-ttu-id="06a74-110">`SAFE`, `EXTERNAL_ACCESS` 및 `UNSAFE` 어셈블리에는 서로 다른 CAS 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-110">`SAFE`, `EXTERNAL_ACCESS`, and `UNSAFE` assemblies have different CAS permissions.</span></span> <span data-ttu-id="06a74-111">자세한 내용은 [CLR 통합 코드 액세스 보안](../security/clr-integration-code-access-security.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="06a74-111">For more information, see [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).</span></span>  
  
## <a name="create-assembly-checks"></a><span data-ttu-id="06a74-112">CREATE ASSEMBLY 검사</span><span class="sxs-lookup"><span data-stu-id="06a74-112">CREATE ASSEMBLY Checks</span></span>  
 <span data-ttu-id="06a74-113">`CREATE ASSEMBLY` 문을 실행하면 각 보안 수준에 대해 다음과 같은 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-113">When the `CREATE ASSEMBLY` statement is run, the following checks are performed for each security level.</span></span>  <span data-ttu-id="06a74-114">감사가 실패하면 오류 메시지와 함께 `CREATE ASSEMBLY`가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-114">If any check fails, `CREATE ASSEMBLY` will fail with an error message.</span></span>  
  
### <a name="global-any-security-level"></a><span data-ttu-id="06a74-115">전역(모든 보안 수준)</span><span class="sxs-lookup"><span data-stu-id="06a74-115">Global (any security level)</span></span>  
 <span data-ttu-id="06a74-116">참조된 모든 어셈블리가 다음 조건을 하나 이상 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-116">All referenced assemblies must meet one or more of the following criteria:</span></span>  
  
-   <span data-ttu-id="06a74-117">어셈블리가 데이터베이스에 이미 등록되었습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-117">The assembly is already registered in the database.</span></span>  
  
-   <span data-ttu-id="06a74-118">어셈블리가 지원되는 어셈블리 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-118">The assembly is one of the supported assemblies.</span></span> <span data-ttu-id="06a74-119">자세한 내용은 [Supported .NET Framework Libraries](supported-net-framework-libraries.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="06a74-119">For more information, see [Supported .NET Framework Libraries](supported-net-framework-libraries.md).</span></span>  
  
-   <span data-ttu-id="06a74-120">`CREATE ASSEMBLY FROM` \* \<location> 를\* 사용 하 고 있으며 모든 참조 된 어셈블리와 해당 종속성을에서 사용할 수 있습니다 *\<location>* .</span><span class="sxs-lookup"><span data-stu-id="06a74-120">You are using `CREATE ASSEMBLY FROM`*\<location>,* and all the referenced assemblies and their dependencies are available in *\<location>*.</span></span>  
  
-   <span data-ttu-id="06a74-121">`CREATE ASSEMBLY FROM` \* \<bytes ...> 를\* 사용 하 고 있으며 모든 참조는 공백으로 구분 된 바이트를 통해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-121">You are using `CREATE ASSEMBLY FROM`*\<bytes ...>,* and all the references are specified via space separated bytes.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="06a74-122">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="06a74-122">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="06a74-123">모든 `EXTERNAL_ACCESS` 어셈블리가 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-123">All `EXTERNAL_ACCESS` assemblies must meet the following criteria:</span></span>  
  
-   <span data-ttu-id="06a74-124">정적 필드가 정보 저장에 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-124">Static fields are not used to store information.</span></span> <span data-ttu-id="06a74-125">읽기 전용 정적 필드는 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-125">Read-only static fields are allowed.</span></span>  
  
-   <span data-ttu-id="06a74-126">PEVerify 테스트에 통과합니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-126">PEVerify test is passed.</span></span> <span data-ttu-id="06a74-127">MSIL 코드 및 관련된 메타데이터가 형식 안전성 요구 사항을 충족하는지 확인하는 PEVerify 도구(peverify.exe)는 .NET Framework SDK에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-127">The PEVerify tool (peverify.exe), which checks that the MSIL code and associated metadata meet type safety requirements, is provided with the .NET Framework SDK.</span></span>  
  
-   <span data-ttu-id="06a74-128">예를 들어 `SynchronizationAttribute` 클래스를 사용한 동기화가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-128">Synchronization, for example with the `SynchronizationAttribute` class, is not used.</span></span>  
  
-   <span data-ttu-id="06a74-129">파이널라이저 메서드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-129">Finalizer methods are not used.</span></span>  
  
 <span data-ttu-id="06a74-130">다음과 같은 사용자 지정 특성은 `EXTERNAL_ACCESS` 어셈블리에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-130">The following custom attributes are disallowed in `EXTERNAL_ACCESS` assemblies:</span></span>  
  
-   <span data-ttu-id="06a74-131">System.ContextStaticAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-131">System.ContextStaticAttribute</span></span>  
  
-   <span data-ttu-id="06a74-132">System.MTAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-132">System.MTAThreadAttribute</span></span>  
  
-   <span data-ttu-id="06a74-133">System.Runtime.CompilerServices.MethodImplAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-133">System.Runtime.CompilerServices.MethodImplAttribute</span></span>  
  
-   <span data-ttu-id="06a74-134">System.Runtime.CompilerServices.CompilationRelaxationsAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-134">System.Runtime.CompilerServices.CompilationRelaxationsAttribute</span></span>  
  
-   <span data-ttu-id="06a74-135">System.Runtime.Remoting.Contexts.ContextAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-135">System.Runtime.Remoting.Contexts.ContextAttribute</span></span>  
  
-   <span data-ttu-id="06a74-136">System.Runtime.Remoting.Contexts.SynchronizationAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-136">System.Runtime.Remoting.Contexts.SynchronizationAttribute</span></span>  
  
-   <span data-ttu-id="06a74-137">System.Runtime.InteropServices.DllImportAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-137">System.Runtime.InteropServices.DllImportAttribute</span></span>  
  
-   <span data-ttu-id="06a74-138">System.Security.Permissions.CodeAccessSecurityAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-138">System.Security.Permissions.CodeAccessSecurityAttribute</span></span>  
  
-   <span data-ttu-id="06a74-139">System.Security.SuppressUnmanagedCodeSecurityAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-139">System.Security.SuppressUnmanagedCodeSecurityAttribute</span></span>  
  
-   <span data-ttu-id="06a74-140">System.Security.UnverifiableCodeAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-140">System.Security.UnverifiableCodeAttribute</span></span>  
  
-   <span data-ttu-id="06a74-141">System.STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-141">System.STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="06a74-142">System.ThreadStaticAttribute</span><span class="sxs-lookup"><span data-stu-id="06a74-142">System.ThreadStaticAttribute</span></span>  
  
### <a name="safe"></a><span data-ttu-id="06a74-143">SAFE</span><span class="sxs-lookup"><span data-stu-id="06a74-143">SAFE</span></span>  
  
-   <span data-ttu-id="06a74-144">모든 `EXTERNAL_ACCESS` 어셈블리 조건이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-144">All `EXTERNAL_ACCESS` assembly conditions are checked.</span></span>  
  
## <a name="runtime-checks"></a><span data-ttu-id="06a74-145">런타임 검사</span><span class="sxs-lookup"><span data-stu-id="06a74-145">Runtime Checks</span></span>  
 <span data-ttu-id="06a74-146">런타임에 코드 어셈블리에서 다음 조건이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-146">At runtime, the code assembly is checked for the following conditions.</span></span> <span data-ttu-id="06a74-147">이러한 조건 중 하나가 발견되면 관리 코드를 실행할 수 없으며 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-147">If any of these conditions are found, the managed code will not be allowed to run and an exception will be thrown.</span></span>  
  
### <a name="unsafe"></a><span data-ttu-id="06a74-148">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="06a74-148">UNSAFE</span></span>  
 <span data-ttu-id="06a74-149">바이트 배열에서 메서드를 호출 하 여 명시적으로 또는 네임 스페이스를 사용 하 여 암시적으로 어셈블리를 로드 하 `System.Reflection.Assembly.Load()` `Reflection.Emit` 는 것은 허용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-149">Loading an assembly-either explicitly by calling the `System.Reflection.Assembly.Load()` method from a byte array, or implicitly through the use of `Reflection.Emit` namespace-is not permitted.</span></span>  
  
### <a name="external_access"></a><span data-ttu-id="06a74-150">EXTERNAL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="06a74-150">EXTERNAL_ACCESS</span></span>  
 <span data-ttu-id="06a74-151">모든 `UNSAFE` 조건이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-151">All `UNSAFE` conditions are checked.</span></span>  
  
 <span data-ttu-id="06a74-152">지원되는 어셈블리 목록에서 다음 HPA(호스트 보호 특성) 값이 주석으로 추가된 유형과 멤버는 모두 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-152">All types and methods annotated with the following host protection attribute (HPA) values in the supported list of assemblies are disallowed.</span></span>  
  
-   <span data-ttu-id="06a74-153">SelfAffectingProcessMgmt</span><span class="sxs-lookup"><span data-stu-id="06a74-153">SelfAffectingProcessMgmt</span></span>  
  
-   <span data-ttu-id="06a74-154">SelfAffectingThreading</span><span class="sxs-lookup"><span data-stu-id="06a74-154">SelfAffectingThreading</span></span>  
  
-   <span data-ttu-id="06a74-155">동기화</span><span class="sxs-lookup"><span data-stu-id="06a74-155">Synchronization</span></span>  
  
-   <span data-ttu-id="06a74-156">SharedState</span><span class="sxs-lookup"><span data-stu-id="06a74-156">SharedState</span></span>  
  
-   <span data-ttu-id="06a74-157">ExternalProcessMgmt</span><span class="sxs-lookup"><span data-stu-id="06a74-157">ExternalProcessMgmt</span></span>  
  
-   <span data-ttu-id="06a74-158">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="06a74-158">ExternalThreading</span></span>  
  
-   <span data-ttu-id="06a74-159">SecurityInfrastructure</span><span class="sxs-lookup"><span data-stu-id="06a74-159">SecurityInfrastructure</span></span>  
  
-   <span data-ttu-id="06a74-160">MayLeakOnAbort</span><span class="sxs-lookup"><span data-stu-id="06a74-160">MayLeakOnAbort</span></span>  
  
-   <span data-ttu-id="06a74-161">UI</span><span class="sxs-lookup"><span data-stu-id="06a74-161">UI</span></span>  
  
 <span data-ttu-id="06a74-162">Hpa 및 지원 되는 어셈블리에서 허용 되지 않는 형식 및 멤버 목록에 대 한 자세한 내용은 [호스트 보호 특성 및 CLR 통합 프로그래밍](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="06a74-162">For more information about HPAs and a list of disallowed types and members in the supported assemblies, see [Host Protection Attributes and CLR Integration Programming](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).</span></span>  
  
### <a name="safe"></a><span data-ttu-id="06a74-163">SAFE</span><span class="sxs-lookup"><span data-stu-id="06a74-163">SAFE</span></span>  
 <span data-ttu-id="06a74-164">모든 `EXTERNAL_ACCESS` 조건이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a74-164">All `EXTERNAL_ACCESS` conditions are checked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a74-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06a74-165">See Also</span></span>  
 <span data-ttu-id="06a74-166">[지원 되는 .NET Framework 라이브러리](supported-net-framework-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="06a74-166">[Supported .NET Framework Libraries](supported-net-framework-libraries.md) </span></span>  
 <span data-ttu-id="06a74-167">[CLR 통합 코드 액세스 보안](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="06a74-167">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="06a74-168">[호스트 보호 특성 및 CLR 통합 프로그래밍](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md) </span><span class="sxs-lookup"><span data-stu-id="06a74-168">[Host Protection Attributes and CLR Integration Programming](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md) </span></span>  
 [<span data-ttu-id="06a74-169">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="06a74-169">Creating an Assembly</span></span>](../assemblies/creating-an-assembly.md)  
  
  
