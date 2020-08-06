---
title: 사용자 정의 집계 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: c278b746-6323-4b32-b460-239915acc067
author: rothja
ms.author: jroth
ms.openlocfilehash: c91179cb194bbfb79e8e7a8476e9725877b88afa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740783"
---
# <a name="create-user-defined-aggregates"></a><span data-ttu-id="85897-102">사용자 정의 집계 만들기</span><span class="sxs-lookup"><span data-stu-id="85897-102">Create User-defined Aggregates</span></span>
  <span data-ttu-id="85897-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 내에 CLR 어셈블리로 프로그래밍된 데이터베이스 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85897-103">You can create a database object inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is programmed in a CLR assembly.</span></span> <span data-ttu-id="85897-104">CLR에서 제공하는 풍부한 프로그래밍 모델을 활용할 수 있는 데이터베이스 개체에는 트리거, 저장 프로시저, 함수, 집계 함수 및 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85897-104">Database objects that can leverage the rich programming model provided by the CLR include triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
 <span data-ttu-id="85897-105">[!INCLUDE[tsql](../../includes/tsql-md.md)]에서 제공되는 기본 제공 집계 함수와 마찬가지로 사용자 정의 집계 함수는 값 집합에 대한 계산을 수행한 후 단일 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="85897-105">Like the built-in aggregate functions provided in [!INCLUDE[tsql](../../includes/tsql-md.md)], user-defined aggregate functions perform a calculation on a set of values and return a single value.</span></span>  
  
 <span data-ttu-id="85897-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 다음과 같은 방식으로 사용자 정의 집계 함수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85897-106">Creating a user-defined aggregate function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] involves the following steps:</span></span>  
  
-   <span data-ttu-id="85897-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 지원 언어의 클래스로 사용자 정의 집계 함수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="85897-107">Define the user-defined aggregate function as a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-supported language.</span></span> <span data-ttu-id="85897-108">CLR로 사용자 정의 집계를 프로그래밍하는 방법은 [CLR 사용자 정의 집계](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85897-108">For more information about how to program user-defined aggregates in the CLR, see [CLR User-Defined Aggregates](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md).</span></span> <span data-ttu-id="85897-109">그런 다음 적절한 언어 컴파일러로 정의된 클래스를 컴파일하여 CLR 어셈블리를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="85897-109">Compile this class to build a CLR assembly using the appropriate language compiler.</span></span>  
  
-   <span data-ttu-id="85897-110">CREATE ASSEMBLY 문을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 어셈블리를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="85897-110">Register the assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="85897-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 어셈블리에 대한 자세한 내용은 [어셈블리&#40;데이터베이스 엔진&#41;](../clr-integration/assemblies-database-engine.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85897-111">For more information about assemblies in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Assemblies &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md).</span></span>  
  
-   <span data-ttu-id="85897-112">CREATE AGGREGATE 문을 사용하여 등록된 어셈블리를 참조하는 사용자 정의 집계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="85897-112">Create the user-defined aggregate that references the registered assembly using the CREATE AGGREGATE statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85897-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 에서 SQL Server 프로젝트를 배포하면 해당 프로젝트에 대해 지정된 데이터베이스에 어셈블리가 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="85897-113">Deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="85897-114">또한 프로젝트를 배포하면 `SqlUserDefinedAggregate` 특성으로 주석이 지정된 모든 클래스 정의에 대해 데이터베이스에서 사용자 정의 집계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="85897-114">Deploying the project also creates a user-defined aggregate in the database for all class definitions annotated with the `SqlUserDefinedAggregate` attribute.</span></span> <span data-ttu-id="85897-115">자세한 내용은 [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85897-115">For more information, see [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85897-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 CLR 코드 실행 기능은 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85897-116">The ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute CLR code is off by default.</span></span> <span data-ttu-id="85897-117">관리 코드 모듈을 참조하는 데이터베이스 개체를 만들고 변경하고 삭제할 수 있지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_configure(Transact-SQL) [를 사용하여](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) clr enabled 옵션 [을 설정하지 않는 한 이러한 참조는](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)에서 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85897-117">You can create, alter and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unless the [clr enabled Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) is enabled using [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
 <span data-ttu-id="85897-118">**어셈블리를 생성, 수정 또는 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="85897-118">**To create, modify, or drop an assembly**</span></span>  
  
-   [<span data-ttu-id="85897-119">CREATE ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85897-119">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [<span data-ttu-id="85897-120">ALTER ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85897-120">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [<span data-ttu-id="85897-121">DROP ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85897-121">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="85897-122">**사용자 정의 집계를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="85897-122">**To create a user-defined aggregate**</span></span>  
  
-   [<span data-ttu-id="85897-123">CREATE AGGREGATE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="85897-123">CREATE AGGREGATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-aggregate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="85897-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85897-124">See Also</span></span>  
 [<span data-ttu-id="85897-125">CLR&#40;공용 언어 런타임&#41; 통합 프로그래밍 개요</span><span class="sxs-lookup"><span data-stu-id="85897-125">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
