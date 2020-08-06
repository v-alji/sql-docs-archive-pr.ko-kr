---
title: 지원 되는 .NET Framework 라이브러리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
ms.openlocfilehash: 22f92e3eadccc869452cf35534f786724c8e259a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638839"
---
# <a name="supported-net-framework-libraries"></a><span data-ttu-id="db6a9-102">지원되는 .NET Framework 라이브러리</span><span class="sxs-lookup"><span data-stu-id="db6a9-102">Supported .NET Framework Libraries</span></span>
  <span data-ttu-id="db6a9-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 호스팅된 CLR(공용 언어 런타임)을 사용하면 관리되는 코드로 저장 프로시저, 트리거, 사용자 정의 함수, 사용자 정의 형식 및 사용자 정의 집계를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-103">With the common language runtime (CLR) hosted in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="db6a9-104">.NET Framework 클래스 라이브러리에 있는 기능을 사용하면 문자열 조작, 고급 수학 연산, 파일 액세스, 암호화 등에 대한 기능을 제공하는 미리 작성된 클래스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-104">With the functionality found in the .NET Framework class libraries, you have access to pre-built classes that provide functionality for string manipulation, advanced math operations, file access, cryptography, and more.</span></span> <span data-ttu-id="db6a9-105">임의의 관리되는 저장 프로시저, 사용자 정의 형식, 트리거, 사용자 정의 함수 또는 사용자 정의 집계에서 이러한 클래스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-105">These classes can be accessed from any managed stored procedure, user-defined type, trigger, user-defined function, or user-defined aggregate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db6a9-106">GAC (전역 어셈블리 캐시)에서 지원 되지 않는 어셈블리를 서비스 또는 업그레이드 하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 입니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-106">If you service or upgrade unsupported assemblies in the global assembly cache (GAC), your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="db6a9-107">어셈블리가 CLR 통합에 모두 존재 하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db6a9-107">If an assembly exists both in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR integration.</span></span> <span data-ttu-id="db6a9-108">지원되지 않는 .NET Framework 어셈블리를 비롯하여 데이터베이스에도 등록된 GAC의 어셈블리를 서비스 또는 업그레이드하는 경우 `ALTER ASSEMBLY` 문을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스 내의 어셈블리 복사본도 서비스 또는 업그레이드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-108">If you service or upgrade any assemblies in the GAC that are also registered in the database, including unsupported .NET Framework assemblies, make sure to also service or upgrade the copy of the assembly inside your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases with the `ALTER ASSEMBLY` statement.</span></span> <span data-ttu-id="db6a9-109">자세한 내용은 [기술 자료 문서 949080](https://support.microsoft.com/kb/949080)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="db6a9-109">For more information, see [Knowledge Base article 949080](https://support.microsoft.com/kb/949080).</span></span>  
  
## <a name="supported-libraries"></a><span data-ttu-id="db6a9-110">지원되는 라이브러리</span><span class="sxs-lookup"><span data-stu-id="db6a9-110">Supported Libraries</span></span>  
 <span data-ttu-id="db6a9-111">부터에는 지원 되는 [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] .NET Framework 라이브러리 목록이 있습니다 .이 라이브러리는와의 상호 작용에 대 한 안정성 및 보안 표준을 충족 하는지 테스트 하 여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] GAC (전역 어셈블리 캐시)에서 직접 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-111">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] has a list of supported .NET Framework libraries, which have been tested to ensure that they meet reliability and security standards for interaction with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] loads them directly from the Global Assembly Cache (GAC).</span></span>  
  
 <span data-ttu-id="db6a9-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 CLR 통합에서 지원되는 라이브러리/네임스페이스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-112">The libraries/namespaces supported by CLR integration in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are:</span></span>  
  
-   <span data-ttu-id="db6a9-113">CustomMarshalers</span><span class="sxs-lookup"><span data-stu-id="db6a9-113">CustomMarshalers</span></span>  
  
-   <span data-ttu-id="db6a9-114">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="db6a9-114">Microsoft.VisualBasic</span></span>  
  
-   <span data-ttu-id="db6a9-115">Microsoft.VisualC</span><span class="sxs-lookup"><span data-stu-id="db6a9-115">Microsoft.VisualC</span></span>  
  
-   <span data-ttu-id="db6a9-116">mscorlib</span><span class="sxs-lookup"><span data-stu-id="db6a9-116">mscorlib</span></span>  
  
-   <span data-ttu-id="db6a9-117">시스템</span><span class="sxs-lookup"><span data-stu-id="db6a9-117">System</span></span>  
  
-   <span data-ttu-id="db6a9-118">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="db6a9-118">System.Configuration</span></span>  
  
-   <span data-ttu-id="db6a9-119">System.Data</span><span class="sxs-lookup"><span data-stu-id="db6a9-119">System.Data</span></span>  
  
-   <span data-ttu-id="db6a9-120">System.Data.OracleClient</span><span class="sxs-lookup"><span data-stu-id="db6a9-120">System.Data.OracleClient</span></span>  
  
-   <span data-ttu-id="db6a9-121">System.Data.SqlXml</span><span class="sxs-lookup"><span data-stu-id="db6a9-121">System.Data.SqlXml</span></span>  
  
-   <span data-ttu-id="db6a9-122">System.Deployment</span><span class="sxs-lookup"><span data-stu-id="db6a9-122">System.Deployment</span></span>  
  
-   <span data-ttu-id="db6a9-123">System.Security</span><span class="sxs-lookup"><span data-stu-id="db6a9-123">System.Security</span></span>  
  
-   <span data-ttu-id="db6a9-124">System.Transactions</span><span class="sxs-lookup"><span data-stu-id="db6a9-124">System.Transactions</span></span>  
  
-   <span data-ttu-id="db6a9-125">System.Web.Services</span><span class="sxs-lookup"><span data-stu-id="db6a9-125">System.Web.Services</span></span>  
  
-   <span data-ttu-id="db6a9-126">System.Xml</span><span class="sxs-lookup"><span data-stu-id="db6a9-126">System.Xml</span></span>  
  
-   <span data-ttu-id="db6a9-127">System.Core.dll</span><span class="sxs-lookup"><span data-stu-id="db6a9-127">System.Core.dll</span></span>  
  
-   <span data-ttu-id="db6a9-128">System.Xml.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="db6a9-128">System.Xml.Linq.dll</span></span>  
  
## <a name="unsupported-libraries"></a><span data-ttu-id="db6a9-129">지원되지 않는 라이브러리</span><span class="sxs-lookup"><span data-stu-id="db6a9-129">Unsupported Libraries</span></span>  
 <span data-ttu-id="db6a9-130">지원되지 않는 라이브러리도 관리되는 저장 프로시저, 트리거, 사용자 정의 함수, 사용자 정의 형식 및 사용자 정의 집계에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-130">Unsupported libraries can still be called from your managed stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates.</span></span> <span data-ttu-id="db6a9-131">지원되지 않는 라이브러리는 `CREATE ASSEMBLY` 문을 사용하여 먼저 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 등록해야 코드에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-131">The unsupported library must first be registered in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, using the `CREATE ASSEMBLY` statement, before it can be used in your code.</span></span> <span data-ttu-id="db6a9-132">지원되지 않는 라이브러리를 서버에 등록하고 실행하는 경우 보안과 안정성을 검토하여 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-132">Any unsupported library that is registered and run on the server should be reviewed and tested for security and reliability.</span></span>  
  
 <span data-ttu-id="db6a9-133">예를 들어 `System.DirectoryServices` 네임스페이스는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-133">For example, the `System.DirectoryServices` namespace is not supported.</span></span> <span data-ttu-id="db6a9-134">`UNSAFE` 권한을 사용하여 System.DirectoryServices.dll 어셈블리를 등록해야 코드에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-134">You must register the System.DirectoryServices.dll assembly with `UNSAFE` permissions before you can call it from your code.</span></span> <span data-ttu-id="db6a9-135">`UNSAFE` 네임스페이스의 클래스는 `System.DirectoryServices` 또는 `SAFE`에 대한 요구 사항을 충족하지 않으므로 `EXTERNAL_ACCESS` 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="db6a9-135">The `UNSAFE` permission is necessary because classes in the `System.DirectoryServices` namespace do not meet the requirements for `SAFE` or `EXTERNAL_ACCESS`.</span></span> <span data-ttu-id="db6a9-136">자세한 내용은 [Clr 통합 프로그래밍 모델 제한](clr-integration-programming-model-restrictions.md) 및 [Clr 통합 코드 액세스 보안](../security/clr-integration-code-access-security.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db6a9-136">For more information, see [CLR Integration Programming Model Restrictions](clr-integration-programming-model-restrictions.md) and [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6a9-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db6a9-137">See Also</span></span>  
 <span data-ttu-id="db6a9-138">[어셈블리 만들기](../assemblies/creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="db6a9-138">[Creating an Assembly](../assemblies/creating-an-assembly.md) </span></span>  
 <span data-ttu-id="db6a9-139">[CLR 통합 코드 액세스 보안](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="db6a9-139">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 [<span data-ttu-id="db6a9-140">CLR 통합 프로그래밍 모델 제한 사항</span><span class="sxs-lookup"><span data-stu-id="db6a9-140">CLR Integration Programming Model Restrictions</span></span>](clr-integration-programming-model-restrictions.md)  
  
  
