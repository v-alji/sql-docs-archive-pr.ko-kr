---
title: Oracle 게시를 위한 용어 설명 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], glossary
ms.assetid: e21dfa4b-6144-4be7-9cbf-ca2709b2bd9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d135fb8ea3c1678f5ef31f0d7da6a717ab628999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736183"
---
# <a name="glossary-of-terms-for-oracle-publishing"></a><span data-ttu-id="dce27-102">Oracle 게시를 위한 용어 설명</span><span class="sxs-lookup"><span data-stu-id="dce27-102">Glossary of Terms for Oracle Publishing</span></span>
  <span data-ttu-id="dce27-103">Oracle 게시를 구성 및 관리할 때 다음 Oracle 용어에 익숙해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-103">You should be familiar with the following Oracle terms when configuring and administering Oracle publishing.</span></span> <span data-ttu-id="dce27-104">전체 Oracle 용어 목록은 Oracle 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dce27-104">For a complete list of Oracle terms, see the Oracle online documentation.</span></span>  
  
 <span data-ttu-id="dce27-105">IOT(인덱스 구성 테이블)</span><span class="sxs-lookup"><span data-stu-id="dce27-105">Index Organized Tables (IOT)</span></span>  
 <span data-ttu-id="dce27-106">인덱스 순서대로 데이터가 물리적으로 디스크에 저장되는 테이블로, 클러스터형 인덱스가 있는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 테이블과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-106">A table whose data is physically sorted on disk in index order; it is similar to a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table with a clustered index.</span></span> <span data-ttu-id="dce27-107">IOT는 클러스터형 인덱스가 있는 테이블로 구독자에 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-107">An IOT is replicated to a Subscriber as a table with a clustered index.</span></span>  
  
 <span data-ttu-id="dce27-108">인스턴스</span><span class="sxs-lookup"><span data-stu-id="dce27-108">Instance</span></span>  
 <span data-ttu-id="dce27-109">Oracle 데이터베이스는 인스턴스와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-109">An Oracle database is associated with an instance.</span></span> <span data-ttu-id="dce27-110">인스턴스는 데이터베이스를 지원하는 메모리 및 백그라운드 프로세스로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-110">The instance comprises the memory and background processes supporting the database.</span></span> <span data-ttu-id="dce27-111">Oracle 인스턴스는 항상 단일 데이터베이스에 매핑되지만 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스는 여러 데이터베이스를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-111">An Oracle instance always maps to a single database, whereas an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can contain many databases.</span></span> <span data-ttu-id="dce27-112">Oracle 데이터베이스가 다중 인스턴스를 포함할 수 있는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-112">There are circumstances in which an Oracle database can have multiple instances.</span></span>  
  
 <span data-ttu-id="dce27-113">Oracle 수신기</span><span class="sxs-lookup"><span data-stu-id="dce27-113">Oracle Listener</span></span>  
 <span data-ttu-id="dce27-114">Oracle 데이터베이스 인스턴스에 대한 들어오는 네트워크 트래픽을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-114">Handles incoming network traffic for an Oracle database instance.</span></span> <span data-ttu-id="dce27-115">Oracle 데이터베이스에 대한 네트워크 연결을 구성할 때 트래픽이 전송되는 프로토콜과 수신기가 트래픽을 수신하는 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-115">When you configure network connectivity to an Oracle database, you specify the protocol through which traffic is sent and the port on which the Listener listens for traffic.</span></span> <span data-ttu-id="dce27-116">일반적으로 수신기는 Oracle 데이터베이스 인스턴스와 동일한 컴퓨터에서 실행하도록 구성되며 하나 이상의 인스턴스를 제공하도록 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-116">The Listener is typically configured to run on the same computer as the Oracle database instance and can be configured to serve one or more instances.</span></span>  
  
 <span data-ttu-id="dce27-117">ROWID</span><span class="sxs-lookup"><span data-stu-id="dce27-117">ROWID</span></span>  
 <span data-ttu-id="dce27-118">데이터베이스의 특정 행 위치를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-118">A pointer to the location of a specific row in a database.</span></span> <span data-ttu-id="dce27-119">ROWID를 사용하여 행을 검색하는 것이 테이블 검색 또는 인덱스를 사용하는 것보다 빠르므로 복제는 게시된 테이블의 변경 내용을 처리하는 중 일시적으로 ROWID를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-119">Because retrieving rows using the ROWID is faster than using a table scan or index, replication uses the ROWID temporarily during processing of published table changes.</span></span>  
  
 <span data-ttu-id="dce27-120">시퀀스</span><span class="sxs-lookup"><span data-stu-id="dce27-120">Sequence</span></span>  
 <span data-ttu-id="dce27-121">고유 번호를 생성하는 데 사용되는 데이터베이스 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-121">A database object that is used to generate unique numbers.</span></span> <span data-ttu-id="dce27-122">복제는 시퀀스를 사용하여 게시된 테이블에 대한 변경 내용의 적용 순서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-122">Replication uses sequences to order changes made to published tables.</span></span>  
  
 <span data-ttu-id="dce27-123">SQL\*Plus</span><span class="sxs-lookup"><span data-stu-id="dce27-123">SQL\*Plus</span></span>  
 <span data-ttu-id="dce27-124">Oracle 데이터베이스에 액세스하고 쿼리하는 데 사용되는 애플리케이션으로</span><span class="sxs-lookup"><span data-stu-id="dce27-124">An application used to access and query Oracle databases.</span></span> <span data-ttu-id="dce27-125">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd**와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-125">It is similar to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd**.</span></span>  
  
 <span data-ttu-id="dce27-126">동의어</span><span class="sxs-lookup"><span data-stu-id="dce27-126">Synonym</span></span>  
 <span data-ttu-id="dce27-127">개체에 대한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-127">An alias for an object.</span></span> <span data-ttu-id="dce27-128">**MSSQLSERVERDISTRIBUTOR** 특수 공용 동의어는 Oracle 게시자를 구성할 때 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-128">The special public synonym **MSSQLSERVERDISTRIBUTOR** is automatically created when an Oracle Publisher is configured.</span></span> <span data-ttu-id="dce27-129">동의어는 **HREPL_Distributor** 테이블을 참조하고 게시자에 서비스를 제공하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자에게 논리 포인터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-129">The synonym references the **HREPL_Distributor** table and provides a logical pointer to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor that services the Publisher.</span></span>  
  
 <span data-ttu-id="dce27-130">Oracle 데이터베이스가 게시된 경우 이 공용 동의어는 게시자에 서비스를 제공하도록 이미 구성된 특정 배포자를 식별하므로 다른 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자를 사용하도록 이 게시자를 구성하는 후속 시도가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-130">After an Oracle database has been published, subsequent attempts to configure this Publisher to use a different [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor will fail, because this public synonym identifies the particular Distributor already configured to service the Publisher.</span></span>  
  
 <span data-ttu-id="dce27-131">테이블스페이스</span><span class="sxs-lookup"><span data-stu-id="dce27-131">Tablespace</span></span>  
 <span data-ttu-id="dce27-132">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 파일 그룹과 거의 동일한 데이터베이스 스토리지 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-132">A unit of database storage that is roughly equivalent to a filegroup in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="dce27-133">TNS 서비스 이름</span><span class="sxs-lookup"><span data-stu-id="dce27-133">TNS Service Name</span></span>  
 <span data-ttu-id="dce27-134">TNS(Transparent Network Substrate)는 Oracle 데이터베이스에서 사용되는 통신 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-134">TNS (Transparent Network Substrate) is a communication layer used by Oracle databases.</span></span> <span data-ttu-id="dce27-135">TNS 서비스 이름은 네트워크상에서 Oracle 데이터베이스 인스턴스를 식별하는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-135">The TNS Service Name is the name by which an Oracle database instance is known on a network.</span></span> <span data-ttu-id="dce27-136">Oracle 데이터베이스에 대한 연결을 구성할 때 TNS 서비스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-136">You assign a TNS Service Name when you configure connectivity to the Oracle database.</span></span> <span data-ttu-id="dce27-137">복제는 TNS 서비스 이름을 사용하여 게시자를 식별하고 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-137">Replication uses the TNS Service name to identify the Publisher and to establish connections.</span></span>  
  
 <span data-ttu-id="dce27-138">사용자 스키마</span><span class="sxs-lookup"><span data-stu-id="dce27-138">User schema</span></span>  
 <span data-ttu-id="dce27-139">사용자 스키마는 특정 데이터베이스 개체 집합을 소유하는 데이터베이스 사용자로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-139">A user schema can be thought of as a database user who owns a particular set of database objects.</span></span> <span data-ttu-id="dce27-140">복제 관리 사용자 스키마는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] MSSQLSERVERDISTRIBUTOR **공용 동의어를 제외하고 Oracle 데이터베이스에서** 복제 프로세스로 생성된 모든 개체를 소유합니다.</span><span class="sxs-lookup"><span data-stu-id="dce27-140">The replication administrative user schema owns all objects created by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication process in the Oracle database, with the exception of the **MSSQLSERVERDISTRIBUTOR** public synonym.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce27-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dce27-141">See Also</span></span>  
 <span data-ttu-id="dce27-142">[Oracle 게시자 구성](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="dce27-142">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="dce27-143">[Oracle 게시자에 생성되는 개체](objects-created-on-the-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="dce27-143">[Objects Created on the Oracle Publisher](objects-created-on-the-oracle-publisher.md) </span></span>  
 <span data-ttu-id="dce27-144">[SQL Server 이외 게시자](non-sql-server-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="dce27-144">[Non-SQL Server Publishers](non-sql-server-publishers.md) </span></span>  
 [<span data-ttu-id="dce27-145">Oracle 게시 개요</span><span class="sxs-lookup"><span data-stu-id="dce27-145">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
