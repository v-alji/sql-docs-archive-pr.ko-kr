---
title: 연결된 서버(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB, linked servers
- OLE DB provider, linked servers
- server management [SQL Server], linked servers
- linked servers [SQL Server]
- distributed queries [SQL Server], linked servers
- servers [SQL Server], linked
- remote servers [SQL Server], linked servers
- linked servers [SQL Server], about linked servers
ms.assetid: 6ef578bf-8da7-46e0-88b5-e310fc908bb0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1de70882cdeb87ccc0ae42aa23a9b6c8b3248e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646433"
---
# <a name="linked-servers-database-engine"></a><span data-ttu-id="688c0-102">연결된 서버(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="688c0-102">Linked Servers (Database Engine)</span></span>
  <span data-ttu-id="688c0-103">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스 외부의 OLE DB 데이터 원본에 대해 명령을 실행할 수 있도록 연결된 서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-103">Configure a linked server to enable the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to execute commands against OLE DB data sources outside of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="688c0-104">일반적으로 연결된 서버는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 의 다른 인스턴스 또는 Oracle과 같은 다른 데이터베이스 제품에 있는 테이블이 포함된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]문을 실행할 수 있도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-104">Typically linked servers are configured to enable the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to execute a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that includes tables in another instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], or another database product such as Oracle.</span></span> <span data-ttu-id="688c0-105">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access 및 Excel을 포함한 많은 유형의 OLE DB 데이터 원본을 연결된 서버로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-105">Many types OLE DB data sources can be configured as linked servers, including [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access and Excel.</span></span> <span data-ttu-id="688c0-106">연결된 서버에는 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-106">Linked servers offer the following advantages:</span></span>

-   <span data-ttu-id="688c0-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]외부에서 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-107">The ability to access data from outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

-   <span data-ttu-id="688c0-108">기업 전체에 걸쳐 유형이 다른 데이터 원본에 대해 분산 쿼리, 업데이트, 명령, 트랜잭션 등을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-108">The ability to issue distributed queries, updates, commands, and transactions on heterogeneous data sources across the enterprise.</span></span>

-   <span data-ttu-id="688c0-109">다양한 데이터 원본을 유사하게 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-109">The ability to address diverse data sources similarly.</span></span>

 <span data-ttu-id="688c0-110">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 를 사용하거나 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) 문을 사용하여 연결된 서버를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-110">You can configure a linked server by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or by using the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) statement.</span></span> <span data-ttu-id="688c0-111">OLE DB Provider에 따라 필요한 매개 변수의 유형과 개수가 크게 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-111">OLE DB providers vary greatly in the type and number of parameters required.</span></span> <span data-ttu-id="688c0-112">예를 들어 일부 공급자는 [sp_addlinkedsrvlogin&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql)인스턴스 외부의 OLE DB 데이터 원본에 대해 명령을 실행할 수 있도록 연결된 서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-112">For example some providers require you to provide a security context for the connection using [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql).</span></span> <span data-ttu-id="688c0-113">일부 OLE DB Provider는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 통해 OLE DB 원본에서 데이터를 업데이트하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-113">Some OLE DB providers allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to update data on the OLE DB source.</span></span> <span data-ttu-id="688c0-114">다른 일부 공급자는 읽기 전용 데이터 액세스만 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-114">Others provide only read-only data access.</span></span> <span data-ttu-id="688c0-115">각 OLE DB Provider에 대한 자세한 내용은 해당 OLE DB Provider에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="688c0-115">For information about each OLE DB provider, consult documentation for that OLE DB provider.</span></span>

## <a name="linked-server-components"></a><span data-ttu-id="688c0-116">연결된 서버 구성 요소</span><span class="sxs-lookup"><span data-stu-id="688c0-116">Linked Server Components</span></span>
 <span data-ttu-id="688c0-117">연결된 서버 정의는 다음과 같은 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-117">A linked server definition specifies the following objects:</span></span>

-   <span data-ttu-id="688c0-118">OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="688c0-118">An OLE DB provider</span></span>

-   <span data-ttu-id="688c0-119">OLE DB 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="688c0-119">An OLE DB data source</span></span>

 <span data-ttu-id="688c0-120">*OLE DB Provider* 는 특정 데이터 원본과 상호 작용하고 관리하는 DLL입니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-120">An *OLE DB provider* is a DLL that manages and interacts with a specific data source.</span></span> <span data-ttu-id="688c0-121">*OLE DB 데이터 원본* 은 OLE DB를 통해 액세스할 수 있는 특정 데이터베이스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-121">An *OLE DB data source* identifies the specific database that can be accessed through OLE DB.</span></span> <span data-ttu-id="688c0-122">연결된 서버 정의를 통해 쿼리되는 데이터 원본은 일반적으로 데이터베이스이지만 OLE DB Provider에는 여러 파일 및 파일 형식이 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-122">Although data sources queried through linked server definitions are ordinarily databases, OLE DB providers exist for a variety of files and file formats.</span></span> <span data-ttu-id="688c0-123">여기에는 텍스트 파일, 스프레드시트 데이터 및 전체 텍스트 내용의 검색 결과가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-123">These include text files, spreadsheet data, and the results of full-text content searches.</span></span>

 <span data-ttu-id="688c0-124">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 (PROGID: SQLNCLI11)는의 공식 OLE DB 공급자입니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="688c0-124">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider (PROGID: SQLNCLI11) is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="688c0-125">분산 쿼리는 필수 OLE DB 인터페이스를 구현하는 모든 OLE DB Provider에서 실행되도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-125">distributed queries are designed to work with any OLE DB provider that implements the required OLE DB interfaces.</span></span> <span data-ttu-id="688c0-126">그러나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider와 다른 특정 공급자에 대해서만 테스트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-126">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been tested against only the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB Provider and certain other providers.</span></span>

## <a name="linked-server-details"></a><span data-ttu-id="688c0-127">연결된 서버 정보</span><span class="sxs-lookup"><span data-stu-id="688c0-127">Linked Server Details</span></span>
 <span data-ttu-id="688c0-128">다음 그림은 연결된 서버 구성의 기본 사항을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-128">The following illustration shows the basics of a linked server configuration.</span></span>

 <span data-ttu-id="688c0-129">![클라이언트 계층, 서버 계층 및 데이터베이스 서버 계층](../../database-engine/media/lsvr.gif "클라이언트 계층, 서버 계층 및 데이터베이스 서버 계층")</span><span class="sxs-lookup"><span data-stu-id="688c0-129">![Client tier, server tier, and database server tier](../../database-engine/media/lsvr.gif "Client tier, server tier, and database server tier")</span></span>

 <span data-ttu-id="688c0-130">연결된 서버는 일반적으로 분산 쿼리를 처리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-130">Typically, linked servers are used to handle distributed queries.</span></span> <span data-ttu-id="688c0-131">클라이언트 애플리케이션이 연결된 서버를 통해 분산 쿼리를 실행할 때 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 명령을 구문 분석하고 OLE DB로 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-131">When a client application executes a distributed query through a linked server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] parses the command and sends requests to OLE DB.</span></span> <span data-ttu-id="688c0-132">행 집합 요청은 공급자에 대해 쿼리를 실행하거나 공급자로부터 기본 테이블을 여는 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-132">The rowset request may be in the form of executing a query against the provider or opening a base table from the provider.</span></span>

 <span data-ttu-id="688c0-133">연결된 서버를 통해 데이터를 반환하는 데이터 원본의 경우 해당 데이터 원본에 대한 OLE DB Provider(DLL)는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스와 같은 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-133">For a data source to return data through a linked server, the OLE DB provider (DLL) for that data source must be present on the same server as the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="688c0-134">타사 OLE DB Provider를 사용하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정에는 공급자가 설치된 디렉터리 및 모든 하위 디렉터리에 대한 읽기 및 실행 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-134">When a third-party OLE DB provider is used, the account under which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service runs must have read and execute permissions for the directory, and all subdirectories, in which the provider is installed.</span></span>

## <a name="managing-providers"></a><span data-ttu-id="688c0-135">공급자 관리</span><span class="sxs-lookup"><span data-stu-id="688c0-135">Managing Providers</span></span>
 <span data-ttu-id="688c0-136">일련의 옵션을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 레지스트리에 지정된 OLE DB Provider를 로드하고 사용하는 방법을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-136">There is a set of options that control how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] loads and uses OLE DB providers that are specified in the registry.</span></span>

## <a name="managing-linked-server-definitions"></a><span data-ttu-id="688c0-137">연결된 서버 정의 관리</span><span class="sxs-lookup"><span data-stu-id="688c0-137">Managing Linked Server Definitions</span></span>
 <span data-ttu-id="688c0-138">연결된 서버를 설정할 때 연결 정보와 데이터 원본 정보를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-138">When you are setting up a linked server, register the connection information and data source information with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="688c0-139">등록한 후에는 단일 논리적 이름으로 데이터 원본을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-139">After registered, that data source can be referred to with a single logical name.</span></span>

 <span data-ttu-id="688c0-140">저장 프로시저와 카탈로그 뷰를 사용하여 연결된 서버 정의를 다음과 같이 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-140">You can use stored procedures and catalog views to manage linked server definitions:</span></span>

-   <span data-ttu-id="688c0-141">**sp_addlinkedserver**를 실행하여 연결된 서버 정의를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-141">Create a linked server definition by running **sp_addlinkedserver**.</span></span>

-   <span data-ttu-id="688c0-142">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sys.servers **시스템 카탈로그 뷰에 대해 쿼리를 실행하여 특정** 인스턴스에 정의된 연결된 서버에 대한 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-142">View information about the linked servers defined in a specific instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by running a query against the **sys.servers** system catalog views.</span></span>

-   <span data-ttu-id="688c0-143">**sp_dropserver**를 실행하여 연결된 서버 정의를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-143">Delete a linked server definition by running **sp_dropserver**.</span></span> <span data-ttu-id="688c0-144">사용자는 이 저장 프로시저를 사용하여 원격 서버를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-144">You can also use this stored procedure to remove a remote server.</span></span>

 <span data-ttu-id="688c0-145">또한 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]를 사용하여 연결된 서버를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-145">You can also define linked servers by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="688c0-146">개체 탐색기에서 **서버 개체**를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 선택하고 **연결된 서버**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-146">In the Object Explorer, right-click **Server Objects**, select **New**, and select **Linked Server**.</span></span> <span data-ttu-id="688c0-147">연결된 서버 이름을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택하면 연결된 서버 정의를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-147">You can delete a linked server definition by right-clicking the linked server name and selecting **Delete**.</span></span>

 <span data-ttu-id="688c0-148">연결된 서버에 대해 분산 쿼리를 실행할 경우 각 데이터 원본에서 쿼리할 정식 이름인, 네 부분으로 된 테이블 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-148">When you execute a distributed query against a linked server, include a fully qualified, four-part table name for each data source to query.</span></span> <span data-ttu-id="688c0-149">네 부분으로 구성 된 이름은 linked_server_name. catalog 형식 _linked_server_name.catalog_\*\*이어야 합니다. _`schema`_ \*\* _object_name_.</span><span class="sxs-lookup"><span data-stu-id="688c0-149">This four-part name should be in the form _linked_server_name.catalog_**._`schema`_.**_object_name_.</span></span>

> [!NOTE]
>  <span data-ttu-id="688c0-150">연결된 서버는 이 서버가 정의된 서버의 포인트 백(루프백)에 정의될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-150">Linked servers can be defined to point back (loop back) to the server on which they are defined.</span></span> <span data-ttu-id="688c0-151">단일 서버 네트워크에서 분산 쿼리를 사용하는 애플리케이션을 테스트할 때 루프백 서버를 유용하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-151">Loopback servers are most useful when testing an application that uses distributed queries on a single server network.</span></span> <span data-ttu-id="688c0-152">루프백 연결된 서버는 테스트를 위한 것이며 분산 트랜잭션과 같은 많은 작업에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="688c0-152">Loopback linked servers are intended for testing and are not supported for many operations, such as distributed transactions.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="688c0-153">관련 작업</span><span class="sxs-lookup"><span data-stu-id="688c0-153">Related Tasks</span></span>
 [<span data-ttu-id="688c0-154">연결된 서버 만들기 &#40;SQL Server 데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="688c0-154">Create Linked Servers &#40;SQL Server Database Engine&#41;</span></span>](create-linked-servers-sql-server-database-engine.md)

 [<span data-ttu-id="688c0-155">sp_addlinkedserver&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="688c0-155">sp_addlinkedserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)

 [<span data-ttu-id="688c0-156">sp_addlinkedsrvlogin &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="688c0-156">sp_addlinkedsrvlogin &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql)

 [<span data-ttu-id="688c0-157">sp_dropserver&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="688c0-157">sp_dropserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropserver-transact-sql)

## <a name="related-content"></a><span data-ttu-id="688c0-158">관련 내용</span><span class="sxs-lookup"><span data-stu-id="688c0-158">Related Content</span></span>
 [<span data-ttu-id="688c0-159">sys.servers&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="688c0-159">sys.servers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql)

 [<span data-ttu-id="688c0-160">sp_linkedservers&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="688c0-160">sp_linkedservers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql)


