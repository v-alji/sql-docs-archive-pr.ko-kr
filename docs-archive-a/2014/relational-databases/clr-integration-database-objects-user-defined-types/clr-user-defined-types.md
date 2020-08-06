---
title: CLR 사용자 정의 형식 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- validation [CLR integration]
- types [CLR integration]
- UserDefined serialization format [CLR integration]
- null values [CLR integration]
- serialization
- Native serialization format [CLR integration]
- databases [CLR integration]
- building database objects [CLR integration], user-defined types
- user-defined types [CLR integration]
- common language runtime [SQL Server], user-defined types
- UDTs [CLR integration]
- database objects [CLR integration], user-defined types
- turning on CLR functionality
- customizing UDT expression return types [CLR integration]
- UDTs [CLR integration], about UDTs
- comparing UDT values
- annotations [CLR integration]
- user-defined types [CLR integration], about UDTs
- variables [CLR integration]
- invoking UDT methods
- indexes [CLR integration]
ms.assetid: 27c4889b-c543-47a8-a630-ad06804f92df
author: rothja
ms.author: jroth
ms.openlocfilehash: e4e19323eeac9e0a1148924543f71aa7de5619b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661173"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="78708-102">CLR 사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="78708-102">CLR User-Defined Types</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="78708-103">를 사용하면 .NET Framework CLR(공용 언어 런타임)에서 만든 어셈블리에 대해 프로그래밍되는 데이터베이스 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-103">gives you the ability to create database objects that are programmed against an assembly created in the.NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="78708-104">CLR에서 제공하는 풍부한 프로그래밍 모델을 활용할 수 있는 데이터베이스 개체에는 트리거, 저장 프로시저, 함수, 집계 함수 및 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-104">Database objects that can take advantage of the rich programming model provided by the CLR include triggers, stored procedures, functions, aggregate functions, and types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78708-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 CLR 코드 실행 기능은 기본적으로 OFF로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-105">The ability to execute CLR code is set to OFF by default in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="78708-106">**Sp_configure** 시스템 저장 프로시저를 사용 하 여 CLR을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-106">The CLR can be enabled by using the **sp_configure** system stored procedure.</span></span>  
  
 <span data-ttu-id="78708-107">부터는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] udt (사용자 정의 형식)를 사용 하 여 서버의 스칼라 형식 시스템을 확장 함으로써 데이터베이스에 CLR 개체를 저장할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="78708-107">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you can use user-defined types (UDTs) to extend the scalar type system of the server, enabling storage of CLR objects in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="78708-108">UDT에는 여러 요소와 동작이 포함될 수 있어, 단일 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 데이터 형식으로 구성된 일반적인 별칭 데이터 형식과 차별화됩니다.</span><span class="sxs-lookup"><span data-stu-id="78708-108">UDTs can contain multiple elements and can have behaviors, differentiating them from the traditional alias data types which consist of a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system data type.</span></span>  
  
 <span data-ttu-id="78708-109">UDT는 시스템 전체에서 액세스하므로 복잡한 데이터 형식을 사용하면 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-109">Because UDTs are accessed by the system as a whole, their use for complex data types may negatively impact performance.</span></span> <span data-ttu-id="78708-110">복잡한 데이터는 일반적인 행과 테이블을 사용하여 모델링하는 것이 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="78708-110">Complex data is generally best modeled using traditional rows and tables.</span></span> <span data-ttu-id="78708-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 UDT는 다음에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="78708-111">UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are well suited to the following:</span></span>  
  
-   <span data-ttu-id="78708-112">날짜, 시간, 통화 및 확장된 숫자 형식</span><span class="sxs-lookup"><span data-stu-id="78708-112">Date, time, currency, and extended numeric types</span></span>  
  
-   <span data-ttu-id="78708-113">지형 공간 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="78708-113">Geospatial applications</span></span>  
  
-   <span data-ttu-id="78708-114">인코딩 또는 암호화된 데이터</span><span class="sxs-lookup"><span data-stu-id="78708-114">Encoded or encrypted data</span></span>  
  
 <span data-ttu-id="78708-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 UDT를 개발하는 프로세스는 다음 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="78708-115">The process of developing UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="78708-116">**UDT를 정의하는 어셈블리를 코딩 및 작성합니다.**</span><span class="sxs-lookup"><span data-stu-id="78708-116">**Code and build the assembly that defines the UDT.**</span></span> <span data-ttu-id="78708-117">UDT는 검증할 수 있는 코드를 생성하는 .NET Framework CLR(공용 언어 런타임)에서 지원하는 모든 언어를 사용하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="78708-117">UDTs are defined using any of the languages supported by the.NET Framework common language runtime (CLR) that produce verifiable code.</span></span> <span data-ttu-id="78708-118">이러한 언어에는 Visual C# 및 Visual Basic .NET 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-118">This includes Visual C# and Visual Basic .NET.</span></span> <span data-ttu-id="78708-119">데이터는 .NET Framework 클래스 또는 구조의 필드와 속성으로 노출되며 동작은 클래스 또는 구조의 메서드로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="78708-119">The data is exposed as fields and properties of a .NET Framework class or structure, and behaviors are defined by methods of the class or structure.</span></span>  
  
2.  <span data-ttu-id="78708-120">**어셈블리를 등록합니다.**</span><span class="sxs-lookup"><span data-stu-id="78708-120">**Register the assembly.**</span></span> <span data-ttu-id="78708-121">데이터베이스 프로젝트에서 Visual Studio 사용자 인터페이스를 통해 UDT를 배포하거나, 클래스 또는 구조가 포함된 어셈블리를 데이터베이스에 복사하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY 문을 사용하여 UDT를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-121">UDTs can be deployed through the Visual Studio user interface in a database project, or by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE ASSEMBLY statement, which copies the assembly containing the class or structure into a database.</span></span>  
  
3.  <span data-ttu-id="78708-122">**SQL Server에서 UDT를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="78708-122">**Create the UDT in SQL Server.**</span></span> <span data-ttu-id="78708-123">어셈블리가 호스트 데이터베이스에 로드되고 나면 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE 문을 사용하여 UDT를 만들고, 클래스 또는 구조의 멤버를 UDT의 멤버로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="78708-123">Once an assembly is loaded into a host database, you use the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TYPE statement to create a UDT and expose the members of the class or structure as members of the UDT.</span></span> <span data-ttu-id="78708-124">UDT는 단일 데이터베이스의 컨텍스트에만 있으며, 등록된 후에는 UDT를 만들 때 사용된 외부 파일에 대한 종속 관계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-124">UDTs exist only in the context of a single database, and, once registered, have no dependencies on the external files from which they were created.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="78708-125">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이전에는 .NET Framework 어셈블리에서 만든 UDT가 지원되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-125">Before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], UDTs created from .NET Framework assemblies were not supported.</span></span> <span data-ttu-id="78708-126">그러나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sp_addtype**를 사용 하 여 별칭 데이터 형식을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-126">However, you can still use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alias data types by using **sp_addtype**.</span></span> <span data-ttu-id="78708-127">CREATE TYPE 구문은 네이티브 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 정의 데이터 형식과 UDT를 만드는 데 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78708-127">The CREATE TYPE syntax can be used for creating both native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined data types and UDTs.</span></span>  
  
4.  <span data-ttu-id="78708-128">**UDT를 사용 하 여 테이블, 변수 또는 매개 변수 만들기** 부터 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 사용자 정의 형식은 테이블의 열 정의, [!INCLUDE[tsql](../../includes/tsql-md.md)] 일괄 처리의 변수 또는 함수나 저장 프로시저의 인수로 사용 될 수 있습니다 [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="78708-128">**Create tables, variables, or parameters using the UDT** Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a user-defined type can be used as the column definition of a table, as a variable in a [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, or as an argument of a [!INCLUDE[tsql](../../includes/tsql-md.md)] function or stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78708-129">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="78708-129">In This Section</span></span>  
 [<span data-ttu-id="78708-130">사용자 정의 형식 만들기</span><span class="sxs-lookup"><span data-stu-id="78708-130">Creating a User-Defined Type</span></span>](creating-user-defined-types.md)  
 <span data-ttu-id="78708-131">UDT를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="78708-131">Describes how to create UDTs.</span></span>  
  
 [<span data-ttu-id="78708-132">SQL Server의 사용자 정의 형식 등록</span><span class="sxs-lookup"><span data-stu-id="78708-132">Registering User-Defined Types in SQL Server</span></span>](registering-user-defined-types-in-sql-server.md)  
 <span data-ttu-id="78708-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 UDT를 등록하고 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="78708-133">Describes how to register and manage UDTs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="78708-134">SQL Server의 사용자 정의 형식 작업</span><span class="sxs-lookup"><span data-stu-id="78708-134">Working with User-Defined Types in SQL Server</span></span>](working-with-user-defined-types-in-sql-server.md)  
 <span data-ttu-id="78708-135">UDT를 사용하여 쿼리를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="78708-135">Describes how to create queries using UDTs.</span></span>  
  
 [<span data-ttu-id="78708-136">ADO.NET의 사용자 정의 형식 액세스</span><span class="sxs-lookup"><span data-stu-id="78708-136">Accessing User-Defined Types in ADO.NET</span></span>](accessing-user-defined-types-in-ado-net.md)  
 <span data-ttu-id="78708-137">ADO.NET의 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 사용하여 UDT 작업을 수행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="78708-137">Describes how to work with UDTs using the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in ADO.NET.</span></span>  
  
  
