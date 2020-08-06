---
title: 어셈블리 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
author: rothja
ms.author: jroth
ms.openlocfilehash: 9dea1f8fe57691f05274cac353a1064420309e06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735335"
---
# <a name="creating-an-assembly"></a><span data-ttu-id="4b923-102">어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="4b923-102">Creating an Assembly</span></span>
  <span data-ttu-id="4b923-103">저장 프로시저나 트리거 같은 관리되는 데이터베이스 개체는 컴파일한 다음 어셈블리라는 단위로 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-103">Managed database objects, such as stored procedures or triggers, are compiled and then deployed in units called an assembly.</span></span> <span data-ttu-id="4b923-104">관리되는 DLL 어셈블리의 경우 어셈블리에서 제공하는 기능을 사용하려면 먼저 어셈블리를 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-104">Managed DLL assemblies must be registered in [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] before the functionality the assembly provides can be used.</span></span> <span data-ttu-id="4b923-105">CREATE ASSEMBLY 문을 사용하여 어셈블리를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-105">To register an assembly in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, use the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="4b923-106">이 항목에서는 CREATE ASSEMBLY 문을 사용하여 어셈블리를 데이터베이스에 등록하는 방법과 어셈블리에 대한 보안 설정을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-106">This topic discusses how to register an assembly in a database using the CREATE ASSEMBLY statement, and how to specify the security settings for the assembly.</span></span>  
  
## <a name="the-create-assembly-statement"></a><span data-ttu-id="4b923-107">CREATE ASSEMBLY 문</span><span class="sxs-lookup"><span data-stu-id="4b923-107">The CREATE ASSEMBLY Statement</span></span>  
 <span data-ttu-id="4b923-108">CREATE ASSEMBLY 문은 데이터베이스에 어셈블리를 만드는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-108">The CREATE ASSEMBLY statement is used to create an assembly in a database.</span></span> <span data-ttu-id="4b923-109">다음은 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-109">Here is an example:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 <span data-ttu-id="4b923-110">FROM 절은 만들려는 어셈블리의 경로 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-110">The FROM clause specifies the pathname of the assembly to create.</span></span> <span data-ttu-id="4b923-111">이 경로는 UNC(Universal Naming Convention) 경로나 시스템에 대해 로컬인 물리적 파일 경로일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-111">This path can either be a Universal Naming Convention (UNC) path or a physical file path that is local to the machine.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="4b923-112">에서는 이름, culture 및 공개 키가 동일한 서로 다른 버전의 어셈블리를 등록할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-112">does not allow registering different versions of an assembly with the same name, culture and public key.</span></span>  
  
 <span data-ttu-id="4b923-113">다른 어셈블리를 참조하는 어셈블리는 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-113">It is possible to create assemblies that reference other assemblies.</span></span> <span data-ttu-id="4b923-114">에서 어셈블리를 만들면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 루트 수준 어셈블리에서 참조 하는 어셈블리도 생성 됩니다 (참조 된 어셈블리가 데이터베이스에 아직 만들어지지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="4b923-114">When an assembly is created in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also creates the assemblies referenced by the root-level assembly, if the referenced assemblies are not already created into the database.</span></span>  
  
 <span data-ttu-id="4b923-115">데이터베이스 사용자나 사용자 역할에는 데이터베이스에 어셈블리를 만들고 이를 소유할 수 있는 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-115">Database users or user roles are given permissions to create, and thereby own, assemblies in a database.</span></span> <span data-ttu-id="4b923-116">어셈블리를 만들려면 데이터베이스 사용자나 역할에 CREATE ASSEMBLY 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-116">In order to create assemblies, the database user or role should have the CREATE ASSEMBLY permission.</span></span>  
  
 <span data-ttu-id="4b923-117">어셈블리가 다른 어셈블리를 참조하려면 다음 조건을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-117">An assembly can only succeed in referencing other assemblies if:</span></span>  
  
-   <span data-ttu-id="4b923-118">호출되거나 참조되는 어셈블리를 동일한 사용자나 역할이 소유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-118">The assembly that is called or referenced is owned by the same user or role.</span></span>  
  
-   <span data-ttu-id="4b923-119">호출되거나 참조되는 어셈블리가 동일한 데이터베이스에 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-119">The assembly that is called or referenced was created in the same database.</span></span>  
  
## <a name="specifying-security-when-creating-assemblies"></a><span data-ttu-id="4b923-120">어셈블리 생성 시 보안 지정</span><span class="sxs-lookup"><span data-stu-id="4b923-120">Specifying Security When Creating Assemblies</span></span>  
 <span data-ttu-id="4b923-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 어셈블리를 만들 때 코드가 실행될 수 있는 세 가지 보안 수준인 `SAFE`, `EXTERNAL_ACCESS` 또는 `UNSAFE` 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-121">When creating an assembly into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, you can specify one of three different levels of security in which your code can run: `SAFE`, `EXTERNAL_ACCESS`, or `UNSAFE`.</span></span> <span data-ttu-id="4b923-122">`CREATE ASSEMBLY` 문이 실행될 때 코드 어셈블리에 대해 특정 검사가 수행되어 어셈블리가 서버에 등록되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-122">When the `CREATE ASSEMBLY` statement is run, certain checks are performed on the code assembly which may cause the assembly to fail to register on the server.</span></span> <span data-ttu-id="4b923-123">자세한 내용은 [CodePlex](https://msftengprodsamples.codeplex.com/)의 가장 예제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b923-123">For more information, see the Impersonation sample on [CodePlex](https://msftengprodsamples.codeplex.com/).</span></span>  
  
 <span data-ttu-id="4b923-124">`SAFE`는 기본 권한 집합이며 대부분의 시나리오에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-124">`SAFE` is the default permission set and works for the majority of scenarios.</span></span> <span data-ttu-id="4b923-125">이 보안 수준을 지정하려면 다음과 같이 CREATE ASSEMBLY 문의 구문을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-125">To specify a given security level, you modify the syntax of the CREATE ASSEMBLY statement as follows:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 <span data-ttu-id="4b923-126">`SAFE` 권한 집합으로 어셈블리를 만드는 데 위의 코드에서 세 번째 줄을 생략해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-126">It is also possible to create an assembly with the `SAFE` permission set by simply omitting the third line of code above:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 <span data-ttu-id="4b923-127">어셈블리의 코드를 `SAFE` 권한 집합으로 실행할 경우 코드는 in-process 관리 공급자를 통해 서버 내에서 계산 및 데이터 액세스만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-127">When code in an assembly runs under the `SAFE` permission set, it can only do computation and data access within the server through the in-process managed provider.</span></span>  
  
### <a name="creating-external_access-and-unsafe-assemblies"></a><span data-ttu-id="4b923-128">EXTERNAL_ACCESS 및 UNSAFE 어셈블리 만들기</span><span class="sxs-lookup"><span data-stu-id="4b923-128">Creating EXTERNAL_ACCESS and UNSAFE Assemblies</span></span>  
 <span data-ttu-id="4b923-129">`EXTERNAL_ACCESS`는 코드에서 파일, 네트워크, 레지스트리, 환경 변수 등 서버 외부의 리소스에 액세스해야 하는 시나리오를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-129">`EXTERNAL_ACCESS` addresses scenarios in which the code needs to access resources outside the server, such as files, network, registry, and environment variables.</span></span> <span data-ttu-id="4b923-130">서버에서 외부 리소스에 액세스할 때마다 서버는 관리 코드를 호출하는 사용자의 보안 컨텍스트를 가장합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-130">Whenever the server accesses an external resource, it impersonates the security context of the user calling the managed code.</span></span>  
  
 <span data-ttu-id="4b923-131">`UNSAFE` 코드 권한은 어셈블리가 안전한지 확인할 수 없거나 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API 같은 제한된 리소스에 대한 추가 액세스가 필요한 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-131">`UNSAFE` code permission is for those situations in which an assembly is not verifiably safe or requires additional access to restricted resources, such as the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API.</span></span>  
  
 <span data-ttu-id="4b923-132">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 `EXTERNAL_ACCESS` 또는 `UNSAFE` 어셈블리를 만들려면 다음 두 조건 중 하나를 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-132">To create an `EXTERNAL_ACCESS` or `UNSAFE` assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], one of the following two conditions must be met:</span></span>  
  
1.  <span data-ttu-id="4b923-133">어셈블리가 서명된 강력한 이름이거나 인증서로 서명된 Authenticode입니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-133">The assembly is strong name signed or Authenticode signed with a certificate.</span></span> <span data-ttu-id="4b923-134">이 강력한 이름(또는 인증서)이 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 내에서 비대칭 키(또는 인증서)로 생성되었고 `EXTERNAL ACCESS ASSEMBLY` 권한(외부 액세스 어셈블리의 경우) 또는 `UNSAFE ASSEMBLY` 권한(안전하지 않은 어셈블리의 경우)이 있는 해당 로그인을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-134">This strong name (or certificate) is created inside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as an asymmetric key (or certificate), and has a corresponding login with `EXTERNAL ACCESS ASSEMBLY` permission (for external access assemblies) or `UNSAFE ASSEMBLY` permission (for unsafe assemblies).</span></span>  
  
2.  <span data-ttu-id="4b923-135">DBO (데이터베이스 소유자)에는 `EXTERNAL ACCESS ASSEMBLY` (어셈블리의 경우) `EXTERNAL ACCESS` 또는 `UNSAFE ASSEMBLY` (어셈블리의 경우 `UNSAFE` ) 권한이 있고 데이터베이스에는 [신뢰할 수 있는 데이터베이스 속성이](../../security/trustworthy-database-property.md) 로 설정 되어 있습니다 `ON` .</span><span class="sxs-lookup"><span data-stu-id="4b923-135">The database owner (DBO) has `EXTERNAL ACCESS ASSEMBLY` (for `EXTERNAL ACCESS` assemblies) or `UNSAFE ASSEMBLY` (for `UNSAFE` assemblies) permission, and the database has the [TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) set to `ON`.</span></span>  
  
 <span data-ttu-id="4b923-136">위에 나열된 두 가지 조건은 어셈블리가 실행될 때는 물론 로드될 때에도 검사되며</span><span class="sxs-lookup"><span data-stu-id="4b923-136">The two conditions listed above are also checked at assembly load time (which includes execution).</span></span> <span data-ttu-id="4b923-137">두 가지 조건 중 적어도 하나는 만족해야 어셈블리가 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-137">At least one of the conditions must be met in order to load the assembly.</span></span>  
  
 <span data-ttu-id="4b923-138">서버 프로세스에서 CLR (공용 언어 런타임) 코드를 실행 하기 위해서만 데이터베이스의 신뢰할 수 있는 [데이터베이스 속성](../../security/trustworthy-database-property.md) 을로 설정 하는 것이 좋습니다 `ON` .</span><span class="sxs-lookup"><span data-stu-id="4b923-138">We recommend that the [TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) on a database not be set to `ON` only to run common language runtime (CLR) code in the server process.</span></span> <span data-ttu-id="4b923-139">이 경우 대신 master 데이터베이스의 어셈블리 파일에서 비대칭 키를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-139">Instead, we recommend that an asymmetric key be created from the assembly file in the master database.</span></span> <span data-ttu-id="4b923-140">그런 다음 이 비대칭 키에 매핑된 로그인을 만들고 로그인에 `EXTERNAL ACCESS ASSEMBLY` 또는 `UNSAFE ASSEMBLY` 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-140">A login mapped to this asymmetric key must then be created, and the login must be granted `EXTERNAL ACCESS ASSEMBLY` or `UNSAFE ASSEMBLY` permission.</span></span>  
  
 <span data-ttu-id="4b923-141">[!INCLUDE[tsql](../../../includes/tsql-md.md)]CREATE ASSEMBLY 문을 실행 하기 전에 다음 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-141">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements before running the CREATE ASSEMBLY statement.</span></span>  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  <span data-ttu-id="4b923-142">비대칭 키와 연결할 새 로그인을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-142">You must create a new login to associate with the asymmetric key.</span></span> <span data-ttu-id="4b923-143">이 로그인은 사용 권한을 부여하기 위해서만 사용됩니다. 사용자에 연결하거나 애플리케이션 내에서 사용할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-143">This login is only used to grant permissions; it does not have to be associated with a user, or used within the application.</span></span>  
  
 <span data-ttu-id="4b923-144">`EXTERNAL ACCESS` 어셈블리를 만들려면 `EXTERNAL ACCESS` 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-144">To create an `EXTERNAL ACCESS` assembly, the creator needs to have `EXTERNAL ACCESS` permission.</span></span> <span data-ttu-id="4b923-145">이 권한은 어셈블리를 만들 때 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-145">This is specified when creating the assembly:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 <span data-ttu-id="4b923-146">[!INCLUDE[tsql](../../../includes/tsql-md.md)]CREATE ASSEMBLY 문을 실행 하기 전에 다음 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-146">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements before running the CREATE ASSEMBLY statement.</span></span>  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 <span data-ttu-id="4b923-147">어셈블리가 `UNSAFE` 권한으로 로드되도록 지정하려면 어셈블리를 서버에 로드할 때 `UNSAFE` 권한 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b923-147">To specify that an assembly loads with `UNSAFE` permission, you specify the `UNSAFE` permission set when loading the assembly into the server:</span></span>  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 <span data-ttu-id="4b923-148">각 설정의 권한에 대한 자세한 내용은 [CLR Integration Security](../security/clr-integration-security.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4b923-148">For more details about the permissions for each of the settings, see [CLR Integration Security](../security/clr-integration-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b923-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b923-149">See Also</span></span>  
 <span data-ttu-id="4b923-150">[CLR 통합 어셈블리 관리](managing-clr-integration-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="4b923-150">[Managing CLR Integration Assemblies](managing-clr-integration-assemblies.md) </span></span>  
 <span data-ttu-id="4b923-151">[어셈블리 변경](altering-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="4b923-151">[Altering an Assembly](altering-an-assembly.md) </span></span>  
 <span data-ttu-id="4b923-152">[어셈블리 삭제](dropping-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="4b923-152">[Dropping an Assembly](dropping-an-assembly.md) </span></span>  
 <span data-ttu-id="4b923-153">[CLR 통합 코드 액세스 보안](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="4b923-153">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 <span data-ttu-id="4b923-154">[TRUSTWORTHY 데이터베이스 속성](../../security/trustworthy-database-property.md) </span><span class="sxs-lookup"><span data-stu-id="4b923-154">[TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) </span></span>  
 [<span data-ttu-id="4b923-155">부분적으로 신뢰할 수 있는 호출자 허용</span><span class="sxs-lookup"><span data-stu-id="4b923-155">Allowing Partially Trusted Callers</span></span>](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
  
