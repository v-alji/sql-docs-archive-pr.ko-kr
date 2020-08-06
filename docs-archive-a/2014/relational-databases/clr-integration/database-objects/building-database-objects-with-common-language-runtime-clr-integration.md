---
title: CLR (공용 언어 런타임) 통합을 사용 하 여 데이터베이스 개체 빌드 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- database objects [CLR integration], building
- common language runtime [SQL Server], building database objects
- managed code [SQL Server], database objects
- building database objects [CLR integration]
- .NET Framework routines [SQL Server]
ms.assetid: ce34132c-bfa3-447b-9131-b6e17c672efe
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c849c095a3be1c590e6fcb3ce87a0725eb795c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652157"
---
# <a name="building-database-objects-with-common-language-runtime-clr-integration"></a><span data-ttu-id="fe740-102">CLR(공용 언어 런타임) 통합을 사용하여 데이터베이스 개체 작성</span><span class="sxs-lookup"><span data-stu-id="fe740-102">Building Database Objects with Common Language Runtime (CLR) Integration</span></span>
  <span data-ttu-id="fe740-103">을 사용 하 여 데이터베이스 개체를 빌드할 수 있습니다 [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . "CLR 루틴" 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-103">You can build database objects using the [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is referred to as a "CLR routine."</span></span> <span data-ttu-id="fe740-104">이러한 루틴에는 다음과 같은 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-104">These routines include:</span></span>  
  
-   <span data-ttu-id="fe740-105">스칼라 반환 사용자 정의 함수(스칼라 UDF)</span><span class="sxs-lookup"><span data-stu-id="fe740-105">Scalar-valued user-defined functions (scalar UDFs)</span></span>  
  
-   <span data-ttu-id="fe740-106">테이블 반환 사용자 정의 함수(TVF)</span><span class="sxs-lookup"><span data-stu-id="fe740-106">Table-valued user-defined functions (TVFs)</span></span>  
  
-   <span data-ttu-id="fe740-107">UDP(사용자 정의 프로시저)</span><span class="sxs-lookup"><span data-stu-id="fe740-107">User-defined procedures (UDPs)</span></span>  
  
-   <span data-ttu-id="fe740-108">사용자 정의 트리거</span><span class="sxs-lookup"><span data-stu-id="fe740-108">User-defined triggers</span></span>  
  
 <span data-ttu-id="fe740-109">CLR 루틴은 관리 코드에서도 구조가 동일하고</span><span class="sxs-lookup"><span data-stu-id="fe740-109">CLR routines have the same structure in managed code.</span></span> <span data-ttu-id="fe740-110">클래스의 공용 및 정적([!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET의 경우 공유) 메서드에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-110">They are mapped to public, static (shared in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET) methods of a class.</span></span> <span data-ttu-id="fe740-111">.NET Framework를 사용하면 루틴뿐만 아니라 UDT(사용자 정의 형식)와 사용자 정의 집계 함수도 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-111">In addition to routines, user-defined types (UDTs) and user-defined aggregate functions can also be defined using the .NET Framework.</span></span> <span data-ttu-id="fe740-112">UDT와 사용자 정의 집계 함수는 .NET Framework 클래스 전체에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-112">UDTs and user-defined aggregates are mapped to entire .NET Framework classes.</span></span>  
  
 <span data-ttu-id="fe740-113">.NET Framework 루틴의 각 형식에는 해당 하 [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] 는를 사용할 수 있는가 있습니다 [!INCLUDE[tsql](../../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fe740-113">Each type of .NET Framework routine has a [!INCLUDE[tsql](../../../includes/ssnoversion-md.md)] that the [!INCLUDE[tsql](../../../includes/tsql-md.md)] equivalent can be used.</span></span> <span data-ttu-id="fe740-114">예를 들어 스칼라 UDF는 모든 스칼라 식에 사용할 수 있고,</span><span class="sxs-lookup"><span data-stu-id="fe740-114">For instance, scalar UDFs can be used in any scalar expression.</span></span> <span data-ttu-id="fe740-115">TVF는 모든 FROM 절에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-115">A TVF can be used in any FROM clause.</span></span> <span data-ttu-id="fe740-116">프로시저는 EXEC 문에서 호출되거나 클라이언트 애플리케이션에서 호출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-116">A procedure can be invoked in an EXEC statement or invoked from a client application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe740-117">쿼리 최적화 프로그램에서 적절하다고 판단할 경우 공용 언어 런타임에서 CLR 개체(사용자 정의 함수, 사용자 정의 형식 또는 트리거)의 실행은 여러 스레드(병렬 계획)에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-117">Execution of a CLR object (user-defined function, user-defined type, or trigger) on the common language runtime can take place on multiple threads (parallel plan), if the query optimizer decides it is beneficial.</span></span> <span data-ttu-id="fe740-118">그러나 사용자 정의 함수는 데이터에 액세스하므로 직렬 계획에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-118">However, if a user-defined function accesses data, execution will be  on a serial plan.</span></span> <span data-ttu-id="fe740-119">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 이전의 서버 버전에서 LOB 매개 변수나 반환 값을 포함하는 사용자 정의 함수를 실행할 경우 직렬 계획에서도 해당 함수를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-119">When executed on a server version prior to [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], if a user-defined function contains LOB parameters or return values, execution also must be on a serial plan.</span></span>  
  
 <span data-ttu-id="fe740-120">다음 표에는 이 섹션에서 다루는 항목이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-120">The following table lists the topics covered in this section.</span></span>  
  
 [<span data-ttu-id="fe740-121">CLR 통합으로 작업 시작</span><span class="sxs-lookup"><span data-stu-id="fe740-121">Getting Started with CLR Integration</span></span>](getting-started-with-clr-integration.md)  
 <span data-ttu-id="fe740-122">CLR과 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 통합을 사용하여 개체를 컴파일하는 데 필요한 라이브러리와 네임스페이스에 대한 간략한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-122">Provides a brief overview of the libraries and namespaces required to compile object using CLR integration with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fe740-123">"Hello World" CLR 저장 프로시저의 예도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-123">Includes an example "Hello World" CLR stored procedure.</span></span>  
  
 [<span data-ttu-id="fe740-124">지원되는 .NET Framework 라이브러리</span><span class="sxs-lookup"><span data-stu-id="fe740-124">Supported .NET Framework Libraries</span></span>](supported-net-framework-libraries.md)  
 <span data-ttu-id="fe740-125">CLR 통합에서 지원되는 .NET Framework 라이브러리에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-125">Provides information on the .NET Framework libraries supported by CLR integration.</span></span>  
  
 [<span data-ttu-id="fe740-126">CLR 통합 프로그래밍 모델 제한 사항</span><span class="sxs-lookup"><span data-stu-id="fe740-126">CLR Integration Programming Model Restrictions</span></span>](clr-integration-programming-model-restrictions.md)  
 <span data-ttu-id="fe740-127">CLR 통합 프로그래밍의 모델 제한 사항에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-127">Provides information about CLR integration programming model restrictions.</span></span>  
  
 [<span data-ttu-id="fe740-128">.NET Framework의 SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="fe740-128">SQL Server Data Types in the .NET Framework</span></span>](../../clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
 <span data-ttu-id="fe740-129">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식과 해당되는 .NET Framework 데이터 형식에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-129">An overview of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types and their .NET Framework equivalents.</span></span>  
  
 [<span data-ttu-id="fe740-130">CLR 통합 사용자 지정 특성 개요</span><span class="sxs-lookup"><span data-stu-id="fe740-130">Overview of CLR Integration Custom Attributes</span></span>](../../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md)  
 <span data-ttu-id="fe740-131">CLR 통합 사용자 지정 특성에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-131">Provides information about CLR integration custom attributes.</span></span>  
  
 [<span data-ttu-id="fe740-132">CLR 사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="fe740-132">CLR User-Defined Functions</span></span>](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)  
 <span data-ttu-id="fe740-133">테이블 반환 함수, 스칼라 함수, 사용자 정의 집계 함수 등 여러 가지 종류의 CLR 함수를 구현하고 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-133">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="fe740-134">CLR 사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="fe740-134">CLR User-Defined Types</span></span>](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 <span data-ttu-id="fe740-135">CLR 사용자 정의 형식을 구현하고 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-135">Describes how to implement and use CLR user-defined types.</span></span>  
  
 [<span data-ttu-id="fe740-136">CLR 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="fe740-136">CLR Stored Procedures</span></span>](../../../database-engine/dev-guide/clr-stored-procedures.md)  
 <span data-ttu-id="fe740-137">CLR 저장 프로시저를 구현하고 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-137">Describes how to implement and use CLR stored procedures.</span></span>  
  
 [<span data-ttu-id="fe740-138">CLR 트리거</span><span class="sxs-lookup"><span data-stu-id="fe740-138">CLR Triggers</span></span>](../../../database-engine/dev-guide/clr-triggers.md)  
 <span data-ttu-id="fe740-139">CLR 트리거를 구현하고 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fe740-139">Describes how to implement and use CLR triggers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe740-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe740-140">See Also</span></span>  
 [<span data-ttu-id="fe740-141">공용 언어 런타임 &#40;CLR&#41; 통합 개요</span><span class="sxs-lookup"><span data-stu-id="fe740-141">Common Language Runtime &#40;CLR&#41; Integration Overview</span></span>](../common-language-runtime-integration-overview.md)  
  
  
