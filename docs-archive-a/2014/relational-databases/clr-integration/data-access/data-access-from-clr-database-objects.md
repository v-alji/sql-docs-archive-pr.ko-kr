---
title: CLR 데이터베이스 개체에서 데이터 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], data access
- routines [CLR integration]
- data access [CLR integration]
- ADO.NET [CLR integration]
- internal data access [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], data access
- managed code [SQL Server], database objects
- .NET Data Access Provider for SQL Server [CLR integration]
- managed code [SQL Server], data access
- SqlClient provider
- in-process data access providers [CLR integration]
ms.assetid: 9a0f4dee-71c1-42e9-a85e-52382807010f
author: rothja
ms.author: jroth
ms.openlocfilehash: d229d490a9f3a7bc6f613259ee0535218de47975
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659980"
---
# <a name="data-access-from-clr-database-objects"></a><span data-ttu-id="8fd47-102">CLR 데이터베이스 개체에서 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="8fd47-102">Data Access from CLR Database Objects</span></span>
  <span data-ttu-id="8fd47-103">CLR (공용 언어 런타임) 루틴은 실행 되는 인스턴스에 저장 된 데이터 뿐만 아니라 원격 인스턴스에 저장 된 데이터에 쉽게 액세스할 수 있습니다 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8fd47-103">A common language runtime (CLR) routine may easily access data stored in the instance of [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] in which it runs, as well as data stored in remote instances.</span></span> <span data-ttu-id="8fd47-104">루틴을 사용하여 액세스할 수 있는 특정 데이터는 해당 코드가 실행 중인 사용자 컨텍스트에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-104">Which particular data the routine can access is determined by the user context in which the code is running.</span></span> <span data-ttu-id="8fd47-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]관리 되는 클라이언트 및 중간 계층 응용 프로그램의 데이터에 대 한 .NET Framework Data Provider를 사용 하 여 CLR 데이터베이스 개체 내에서 데이터에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-105">Access data from within a CLR database object by using the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data from managed client and middle-tier applications.</span></span> <span data-ttu-id="8fd47-106">따라서 클라이언트 및 중간 계층 애플리케이션에서 ADO.NET 및 `SqlClient`에 대한 지식을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-106">Because of this, you can leverage your knowledge of ADO.NET and `SqlClient` in client and middle-tier applications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8fd47-107">기본적으로 사용자 정의 형식 메서드 및 사용자 정의 함수를 사용하여 데이터 액세스를 수행할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-107">User-defined type methods and user-defined functions are not allowed to perform data access by default.</span></span> <span data-ttu-id="8fd47-108">UDT(사용자 정의 형식) 메서드 또는 사용자 정의 함수를 사용하여 읽기 전용 데이터에 액세스하려면 `DataAccess` 또는 `SqlMethodAttribute`의 `SqlFunctionAttribute` 속성을 `DataAccessKind.Read`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-108">You must set the `DataAccess` property of `SqlMethodAttribute` or `SqlFunctionAttribute` to `DataAccessKind.Read` to enable read-only data access from user-defined type (UDT) methods or user-defined functions.</span></span> <span data-ttu-id="8fd47-109">데이터 수정 작업은 UDT 또는 사용자 정의 함수를 통해 수행할 수 없으며 이를 시도할 경우 실행 시에 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-109">Data modification operations are not allowed from UDTs or user-defined functions, and throws exceptions at execution time if attempted.</span></span>  
  
 <span data-ttu-id="8fd47-110">이 섹션에서는 CLR 데이터베이스 개체 내에서 데이터에 액세스할 때 특정 기능 및 동작 차이에 대해서만 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-110">This section discusses only the specific functional and behavioral differences when accessing data from within a CLR database object.</span></span> <span data-ttu-id="8fd47-111">ADO.NET의 기능에 대한 자세한 내용은 .NET Framework SDK에 포함된 ADO.NET 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8fd47-111">For more information about the features and functionality of ADO.NET, see the ADO.NET documentation included in the .NET Framework SDK.</span></span>  
  
 <span data-ttu-id="8fd47-112">다음 표에서는 이 섹션에서 다루는 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-112">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="8fd47-113">컨텍스트 연결</span><span class="sxs-lookup"><span data-stu-id="8fd47-113">Context Connection</span></span>](context-connection.md)  
 <span data-ttu-id="8fd47-114">SQL Server에 대한 컨텍스트 연결에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-114">Describes the context connection to SQL Server.</span></span>  
  
 [<span data-ttu-id="8fd47-115">연결에 대한 가장 및 자격 증명</span><span class="sxs-lookup"><span data-stu-id="8fd47-115">Impersonation and Credentials for Connections</span></span>](impersonation-and-credentials-for-connections.md)  
 <span data-ttu-id="8fd47-116">연결 및 연결 자격 증명 가장에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-116">Describes impersonating connections and connection credentials.</span></span>  
  
 [<span data-ttu-id="8fd47-117">ADO.NET에 대한 SQL Server In-Process 전용 확장</span><span class="sxs-lookup"><span data-stu-id="8fd47-117">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
 <span data-ttu-id="8fd47-118">in-process 전용 `SqlPipe`, `SqlContext`, `SqlTriggerContext` 및 `SqlDataRecord` 개체에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-118">Discusses the in-process specific `SqlPipe`, `SqlContext`, `SqlTriggerContext`, and `SqlDataRecord` objects.</span></span>  
  
 [<span data-ttu-id="8fd47-119">CLR 통합 및 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="8fd47-119">CLR Integration and Transactions</span></span>](../../native-client-ole-db-transactions/transactions.md)  
 <span data-ttu-id="8fd47-120">System.Transactions 네임스페이스에 제공되는 새 트랜잭션 프레임워크가 ADO.NET 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR 통합과 통합되는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-120">Describes how the new transaction framework provided in the System.Transactions namespace integrates with ADO.NET and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR integration.</span></span>  
  
 [<span data-ttu-id="8fd47-121">CLR 데이터베이스 개체에서 XML 직렬화</span><span class="sxs-lookup"><span data-stu-id="8fd47-121">XML Serialization from CLR Database Objects</span></span>](../../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)  
 <span data-ttu-id="8fd47-122">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 내에서 데이터베이스 개체의 XML 직렬화 시나리오를 구현하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8fd47-122">Explains how to enable XML serialization scenarios of CLR database objects inside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
  
