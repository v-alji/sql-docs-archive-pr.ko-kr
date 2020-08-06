---
title: CLR 트리거 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- CRL triggers
- DML triggers, CLR triggers
- DDL triggers, CLR triggers
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
author: rothja
ms.author: jroth
ms.openlocfilehash: 3afd841b4f1f9ca567a93c0a20c0a7609a5b45e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660416"
---
# <a name="create-clr-triggers"></a><span data-ttu-id="a3e70-102">CLR 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="a3e70-102">Create CLR Triggers</span></span>
  <span data-ttu-id="a3e70-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR(공용 언어 런타임)에 만들어진 어셈블리에 프로그래밍된 데이터베이스 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-103">You can create a database object inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is programmed in an assembly created in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR).</span></span> <span data-ttu-id="a3e70-104">CLR에서 제공하는 다양한 기능의 프로그래밍 모델을 활용할 수 있는 데이터베이스 개체에는 DML 트리거, DDL 트리거, 저장 프로시저, 함수, 집계 함수 및 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-104">Database objects that can leverage the rich programming model provided by the CLR include DML triggers, DDL triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
 <span data-ttu-id="a3e70-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 CLR 트리거(DML 또는 DDL)를 만드는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-105">Creating a CLR trigger (DML or DDL) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] involves the following steps:</span></span>  
  
-   <span data-ttu-id="a3e70-106">.NET Framework 지원 언어로 트리거를 클래스로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-106">Define the trigger as a class in a .NET Framework-supported language.</span></span> <span data-ttu-id="a3e70-107">CLR에서 트리거를 프로그래밍하는 방법은 [CLR 트리거](../../database-engine/dev-guide/clr-triggers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a3e70-107">For more information about how to program triggers in the CLR, see [CLR Triggers](../../database-engine/dev-guide/clr-triggers.md).</span></span> <span data-ttu-id="a3e70-108">그런 다음 적절한 언어 컴파일러를 사용하여 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 에서 어셈블리를 빌드하기 위한 클래스를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-108">Then, compile the class to build an assembly in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] using the appropriate language compiler.</span></span>  
  
-   <span data-ttu-id="a3e70-109">CREATE ASSEMBLY 문을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 어셈블리를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-109">Register the assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the CREATE ASSEMBLY statement.</span></span> <span data-ttu-id="a3e70-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 어셈블리에 대한 자세한 내용은 [어셈블리&#40;데이터베이스 엔진&#41;](../clr-integration/assemblies-database-engine.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a3e70-110">For more information about assemblies in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Assemblies &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md).</span></span>  
  
-   <span data-ttu-id="a3e70-111">등록된 어셈블리를 참조하는 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-111">Create the trigger that references the registered assembly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3e70-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 에서 SQL Server 프로젝트를 배포하면 해당 프로젝트에 대해 지정된 데이터베이스에 어셈블리가 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-112">Deploying a SQL Server Project in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registers an assembly in the database that was specified for the project.</span></span> <span data-ttu-id="a3e70-113">또한 프로젝트를 배포하면 모든 메서드에 대해 `SqlTrigger` 특성으로 주석 지정으로 지정하기 위해 데이터베이스에 CLR 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-113">Deploying the project also creates CLR triggers in the database for all methods annotated with the `SqlTrigger` attribute.</span></span> <span data-ttu-id="a3e70-114">자세한 내용은 [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a3e70-114">For more information, see [Deploying CLR Database Objects](../clr-integration/deploying-clr-database-objects.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3e70-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 CLR 코드 실행 기능은 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-115">The ability of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute CLR code is off by default.</span></span> <span data-ttu-id="a3e70-116">관리 코드 모듈을 참조하는 데이터베이스 개체를 만들고 변경하고 삭제할 수 있지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_configure(Transact-SQL) [을 사용하여](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) clr enabled 옵션 [을 설정하지 않는 한 이러한 참조는](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)에서 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e70-116">You can create, alter, and drop database objects that reference managed code modules, but these references will not execute in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unless the [clr enabled Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) is enabled using [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>  
  
 <span data-ttu-id="a3e70-117">**어셈블리를 생성, 수정 또는 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="a3e70-117">**To create, modify, or drop an assembly**</span></span>  
  
-   [<span data-ttu-id="a3e70-118">CREATE ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a3e70-118">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [<span data-ttu-id="a3e70-119">ALTER ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a3e70-119">ALTER ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [<span data-ttu-id="a3e70-120">DROP ASSEMBLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a3e70-120">DROP ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 <span data-ttu-id="a3e70-121">**CLR 트리거를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="a3e70-121">**To create a CLR trigger**</span></span>  
  
-   [<span data-ttu-id="a3e70-122">CREATE TRIGGER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a3e70-122">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="a3e70-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3e70-123">See Also</span></span>  
 <span data-ttu-id="a3e70-124">[DML 트리거](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="a3e70-124">[DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="a3e70-125">[CLR&#40;공용 언어 런타임&#41; 통합 프로그래밍 개요](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="a3e70-125">[Common Language Runtime &#40;CLR&#41; Integration Programming Concepts](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md) </span></span>  
 [<span data-ttu-id="a3e70-126">CLR 데이터베이스 개체에서 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="a3e70-126">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
