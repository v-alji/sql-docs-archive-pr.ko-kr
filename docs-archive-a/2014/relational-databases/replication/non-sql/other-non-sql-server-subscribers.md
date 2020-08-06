---
title: 다른 SQL Server 이외 구독자 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, other types
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3849ca717e82bcf1bed5769190c9f898209a454a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638656"
---
# <a name="other-non-sql-server-subscribers"></a><span data-ttu-id="d65b8-102">다른 SQL Server 이외 구독자</span><span class="sxs-lookup"><span data-stu-id="d65b8-102">Other Non-SQL Server Subscribers</span></span>
  <span data-ttu-id="d65b8-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]에서 지원하는 -[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자 목록은 [SQL Server 이외 구독자](non-sql-server-subscribers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d65b8-103">For a list of non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers supported by [!INCLUDE[msCoName](../../../includes/msconame-md.md)], see [Non-SQL Server Subscribers](non-sql-server-subscribers.md).</span></span> <span data-ttu-id="d65b8-104">이 항목에는 ODBC 드라이버 및 OLE DB 공급자에 대한 요구 사항 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-104">This topic includes information about requirements for ODBC drivers and OLE DB providers.</span></span>  
  
## <a name="odbc-driver-requirements"></a><span data-ttu-id="d65b8-105">ODBC 드라이버 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d65b8-105">ODBC Driver Requirements</span></span>  
 <span data-ttu-id="d65b8-106">ODBC 드라이버는</span><span class="sxs-lookup"><span data-stu-id="d65b8-106">The ODBC driver:</span></span>  
  
-   <span data-ttu-id="d65b8-107">ODBC 수준-1과 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-107">Must be ODBC level-1 compliant.</span></span>  
  
-   <span data-ttu-id="d65b8-108">스레드로부터 안전해야 하며 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자가 실행되는 프로세서 아키텍처(Intel 또는 Alpha) 및 플랫폼(32비트 또는 64비트)을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-108">Must be thread-safe, and for the processor architecture (Intel or Alpha) and platform (32 bit or 64 bit) on which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor runs.</span></span>  
  
-   <span data-ttu-id="d65b8-109">트랜잭션이 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-109">Must be transaction capable.</span></span>  
  
-   <span data-ttu-id="d65b8-110">DDL(데이터 정의 언어)을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-110">Must support the Data Definition Language (DDL).</span></span>  
  
-   <span data-ttu-id="d65b8-111">읽기 전용이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-111">Cannot be read-only.</span></span>  
  
-   <span data-ttu-id="d65b8-112">**MSreplication_subscriptions**와 같은 긴 테이블 이름을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-112">Must support long table names such as **MSreplication_subscriptions**.</span></span>  
  
## <a name="replicating-using-ole-db-interfaces"></a><span data-ttu-id="d65b8-113">OLE DB 인터페이스를 통한 복제</span><span class="sxs-lookup"><span data-stu-id="d65b8-113">Replicating Using OLE DB Interfaces</span></span>  
 <span data-ttu-id="d65b8-114">OLE DB 공급자는 트랜잭션 복제에 대해 다음과 같은 개체를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-114">OLE DB providers must support these objects for transactional replication:</span></span>  
  
-   <span data-ttu-id="d65b8-115">**DataSource** 개체</span><span class="sxs-lookup"><span data-stu-id="d65b8-115">**DataSource** object</span></span>  
  
-   <span data-ttu-id="d65b8-116">**Session** 개체</span><span class="sxs-lookup"><span data-stu-id="d65b8-116">**Session** object</span></span>  
  
-   <span data-ttu-id="d65b8-117">**Command** 개체</span><span class="sxs-lookup"><span data-stu-id="d65b8-117">**Command** object</span></span>  
  
-   <span data-ttu-id="d65b8-118">**Rowset** 개체</span><span class="sxs-lookup"><span data-stu-id="d65b8-118">**Rowset** object</span></span>  
  
-   <span data-ttu-id="d65b8-119">**Error** 개체</span><span class="sxs-lookup"><span data-stu-id="d65b8-119">**Error** object</span></span>  
  
### <a name="datasource-object-interfaces"></a><span data-ttu-id="d65b8-120">DataSource 개체 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d65b8-120">DataSource Object Interfaces</span></span>  
 <span data-ttu-id="d65b8-121">다음은 데이터 원본에 연결하기 위해 필요한 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-121">The following interfaces are required to connect to a data source:</span></span>  
  
-   `IDBInitialize`  
  
-   `IDBCreateSession`  
  
-   `IDBProperties`  
  
 <span data-ttu-id="d65b8-122">공급자가 **IDBInfo** 인터페이스를 지원하는 경우 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 이 인터페이스를 사용하여 따옴테이블 붙은 식별 문자, 최대 SQL 문 길이, 테이블과 열 이름의 최대 문자 수 등의 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-122">If the provider supports the **IDBInfo** interface, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses the interface to retrieve information such as the quoted identifier character, maximum SQL statement length, and maximum number of characters in table and column names.</span></span>  
  
### <a name="session-object-interfaces"></a><span data-ttu-id="d65b8-123">Session 개체 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d65b8-123">Session Object Interfaces</span></span>  
 <span data-ttu-id="d65b8-124">필요한 인터페이스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-124">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="d65b8-125">**IDBCreateCommand**</span><span class="sxs-lookup"><span data-stu-id="d65b8-125">**IDBCreateCommand**</span></span>  
  
-   <span data-ttu-id="d65b8-126">**ITransaction**</span><span class="sxs-lookup"><span data-stu-id="d65b8-126">**ITransaction**</span></span>  
  
-   <span data-ttu-id="d65b8-127">**ITransactionLocal**</span><span class="sxs-lookup"><span data-stu-id="d65b8-127">**ITransactionLocal**</span></span>  
  
-   <span data-ttu-id="d65b8-128">**IDBSchemaRowset**</span><span class="sxs-lookup"><span data-stu-id="d65b8-128">**IDBSchemaRowset**</span></span>  
  
### <a name="command-object-interfaces"></a><span data-ttu-id="d65b8-129">Command 개체 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d65b8-129">Command Object Interfaces</span></span>  
 <span data-ttu-id="d65b8-130">필요한 인터페이스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-130">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="d65b8-131">**ICommand**</span><span class="sxs-lookup"><span data-stu-id="d65b8-131">**ICommand**</span></span>  
  
-   <span data-ttu-id="d65b8-132">**ICommandProperties**</span><span class="sxs-lookup"><span data-stu-id="d65b8-132">**ICommandProperties**</span></span>  
  
-   <span data-ttu-id="d65b8-133">**ICommandText**</span><span class="sxs-lookup"><span data-stu-id="d65b8-133">**ICommandText**</span></span>  
  
-   <span data-ttu-id="d65b8-134">**ICommandPrepare**</span><span class="sxs-lookup"><span data-stu-id="d65b8-134">**ICommandPrepare**</span></span>  
  
-   <span data-ttu-id="d65b8-135">**IColumnsInfo**</span><span class="sxs-lookup"><span data-stu-id="d65b8-135">**IColumnsInfo**</span></span>  
  
-   <span data-ttu-id="d65b8-136">**IAccessor**</span><span class="sxs-lookup"><span data-stu-id="d65b8-136">**IAccessor**</span></span>  
  
-   <span data-ttu-id="d65b8-137">**ICommandWithParameters**</span><span class="sxs-lookup"><span data-stu-id="d65b8-137">**ICommandWithParameters**</span></span>  
  
 <span data-ttu-id="d65b8-138">**IAccessor** 는 매개 변수 접근자를 만들기 위해 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-138">**IAccessor** is necessary to create parameter accessors.</span></span> <span data-ttu-id="d65b8-139">공급자가 **IColumnRowset**를 지 원하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 해당 인터페이스를 사용 하 여 열이 id 열인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-139">If the provider supports **IColumnRowset**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses that interface to determine whether a column is an identity column.</span></span>  
  
### <a name="rowset-object-interfaces"></a><span data-ttu-id="d65b8-140">Rowset 개체 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d65b8-140">Rowset Object Interfaces</span></span>  
 <span data-ttu-id="d65b8-141">필요한 인터페이스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-141">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="d65b8-142">**IRowset**</span><span class="sxs-lookup"><span data-stu-id="d65b8-142">**IRowset**</span></span>  
  
-   <span data-ttu-id="d65b8-143">**IAccessor**</span><span class="sxs-lookup"><span data-stu-id="d65b8-143">**IAccessor**</span></span>  
  
-   <span data-ttu-id="d65b8-144">**IColumnsInfo**</span><span class="sxs-lookup"><span data-stu-id="d65b8-144">**IColumnsInfo**</span></span>  
  
 <span data-ttu-id="d65b8-145">애플리케이션은 구독 데이터베이스에서 생성된 복제된 테이블의 행 집합을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-145">An application should open a rowset on a replicated table that is created in the subscription database.</span></span> <span data-ttu-id="d65b8-146">**IColumnsInfo** 와 **IAccessor** 는 이 행 집합의 데이터에 액세스하기 위해 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-146">**IColumnsInfo** and **IAccessor** are needed to access data in the rowset.</span></span>  
  
### <a name="error-object-interfaces"></a><span data-ttu-id="d65b8-147">Error 개체 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d65b8-147">Error Object Interfaces</span></span>  
 <span data-ttu-id="d65b8-148">다음 인터페이스를 사용하여 오류를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-148">Use the following interfaces to manage errors:</span></span>  
  
-   <span data-ttu-id="d65b8-149">**IErrorRecords**</span><span class="sxs-lookup"><span data-stu-id="d65b8-149">**IErrorRecords**</span></span>  
  
-   <span data-ttu-id="d65b8-150">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="d65b8-150">**IErrorInfo**</span></span>  
  
 <span data-ttu-id="d65b8-151">OLE DB 공급자에 의해 지원되는 경우에는 **ISQLErrorInfo** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d65b8-151">Use **ISQLErrorInfo** if it is supported by the OLE DB provider.</span></span>  
  
 <span data-ttu-id="d65b8-152">OLE DB 공급자에 대한 자세한 내용은 사용 중인 OLE DB 공급자와 함께 제공된 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d65b8-152">For more information about the OLE DB provider, see the documentation supplied with your OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d65b8-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d65b8-153">See Also</span></span>  
 [<span data-ttu-id="d65b8-154">Non-SQL Server Subscribers</span><span class="sxs-lookup"><span data-stu-id="d65b8-154">Non-SQL Server Subscribers</span></span>](non-sql-server-subscribers.md)  
  
  
