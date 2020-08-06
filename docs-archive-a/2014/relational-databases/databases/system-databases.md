---
title: 시스템 데이터베이스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system databases [SQL Server]
- displaying system database data
- modifying system data
- viewing system database data
ms.assetid: 30468a7c-4225-4d35-aa4a-ffa7da4f1282
author: stevestein
ms.author: sstein
ms.openlocfilehash: 65deee685c2205a7c6e41ed86f71c69639555d7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728311"
---
# <a name="system-databases"></a><span data-ttu-id="07746-102">시스템 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="07746-102">System Databases</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="07746-103">에 포함된 시스템 데이터베이스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07746-103">includes the following system databases.</span></span>  
  
|<span data-ttu-id="07746-104">시스템 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="07746-104">System database</span></span>|<span data-ttu-id="07746-105">Description</span><span class="sxs-lookup"><span data-stu-id="07746-105">Description</span></span>|  
|---------------------|-----------------|  
|[<span data-ttu-id="07746-106">master 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="07746-106">master Database</span></span>](master-database.md)|<span data-ttu-id="07746-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 대한 모든 시스템 수준 정보를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="07746-107">Records all the system-level information for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="07746-108">msdb 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="07746-108">msdb Database</span></span>](msdb-database.md)|<span data-ttu-id="07746-109">SQL Server 에이전트에서 알림과 작업을 예약하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07746-109">Is used by SQL Server Agent for scheduling alerts and jobs.</span></span>|  
|[<span data-ttu-id="07746-110">model 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="07746-110">model Database</span></span>](model-database.md)|<span data-ttu-id="07746-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 생성되는 모든 데이터베이스에 대한 템플릿으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07746-111">Is used as the template for all databases created on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="07746-112">**model** 데이터베이스의 크기, 정렬, 복구 모델 또는 데이터베이스 옵션의 수정 내용은 이후에 생성되는 모든 데이터베이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07746-112">Modifications made to the **model** database, such as database size, collation, recovery model, and other database options, are applied to any databases created afterward.</span></span>|  
|[<span data-ttu-id="07746-113">Resource 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="07746-113">Resource Database</span></span>](resource-database.md)|<span data-ttu-id="07746-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 포함된 시스템 개체가 들어 있는 읽기 전용 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="07746-114">Is a read-only database that contains system objects that are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="07746-115">시스템 개체는 실제로는 **Resource** 데이터베이스에 저장되지만 논리적으로는 모든 데이터베이스의 **sys** 스키마에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="07746-115">System objects are physically persisted in the **Resource** database, but they logically appear in the **sys** schema of every database.</span></span>|  
|[<span data-ttu-id="07746-116">tempdb 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="07746-116">tempdb Database</span></span>](tempdb-database.md)|<span data-ttu-id="07746-117">임시 개체나 중간 결과 집합을 보관하기 위한 작업 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="07746-117">Is a workspace for holding temporary objects or intermediate result sets.</span></span>|  
  
## <a name="modifying-system-data"></a><span data-ttu-id="07746-118">시스템 데이터 수정</span><span class="sxs-lookup"><span data-stu-id="07746-118">Modifying System Data</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="07746-119">에서는 사용자가 시스템 테이블, 시스템 저장 프로시저 및 카탈로그 뷰와 같은 시스템 개체의 정보를 직접 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07746-119">does not support users directly updating the information in system objects such as system tables, system stored procedures, and catalog views.</span></span> <span data-ttu-id="07746-120">대신 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 사용자가 시스템을 완전히 관리하고 데이터베이스의 모든 사용자와 개체를 관리하는 데 사용할 수 있는 완전한 관리 도구 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="07746-120">Instead, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a complete set of administrative tools that let users fully administer their system and manage all users and objects in a database.</span></span> <span data-ttu-id="07746-121">여기에는 다음과 같은 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="07746-121">These include the following:</span></span>  
  
-   <span data-ttu-id="07746-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]등의 관리 유틸리티</span><span class="sxs-lookup"><span data-stu-id="07746-122">Administration utilities, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="07746-123">SQL-SMO API.</span><span class="sxs-lookup"><span data-stu-id="07746-123">SQL-SMO API.</span></span> <span data-ttu-id="07746-124">이 도구를 통해 프로그래머는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 관리할 수 있는 완전한 기능을 애플리케이션에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07746-124">This lets programmers include complete functionality for administering [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in their applications.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="07746-125">스크립트 및 저장 프로시저.</span><span class="sxs-lookup"><span data-stu-id="07746-125">scripts and stored procedures.</span></span> <span data-ttu-id="07746-126">시스템 저장 프로시저와 [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07746-126">These can use system stored procedures and [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statements.</span></span>  
  
 <span data-ttu-id="07746-127">이러한 관리 도구는 시스템 개체의 변경 내용으로부터 애플리케이션을 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="07746-127">These tools shield applications from changes in the system objects.</span></span> <span data-ttu-id="07746-128">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 새 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 새로 추가되는 기능을 지원하기 위해 시스템 테이블을 변경해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07746-128">For example, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sometimes has to change the system tables in new versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support new functionality that is being added in that version.</span></span> <span data-ttu-id="07746-129">시스템 테이블을 직접 참조하는 SELECT 문을 실행하는 애플리케이션은 대개 시스템 테이블의 이전 형식을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="07746-129">Applications issuing SELECT statements that directly reference system tables are frequently dependent on the old format of the system tables.</span></span> <span data-ttu-id="07746-130">사이트는 시스템 테이블에서 선택되는 애플리케이션을 다시 작성해야만 새 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07746-130">Sites may not be able to upgrade to a new version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until they have rewritten applications that are selecting from system tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="07746-131">에서는 시스템 저장 프로시저, DDL 및 SQL-SMO 게시 인터페이스를 고려하며 이러한 인터페이스와 이전 버전과의 호환성을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="07746-131">considers the system stored procedures, DDL, and SQL-SMO published interfaces, and works to maintain the backward compatibility of these interfaces.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="07746-132">에서는 시스템의 작업을 수정할 수 있기 때문에 시스템 테이블에 정의된 트리거는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07746-132">does not support triggers defined on the system tables, because they might modify the operation of the system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07746-133">시스템 데이터베이스는 UNC 공유 디렉터리에 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07746-133">System databases cannot reside on UNC share directories.</span></span>  
  
## <a name="viewing-system-database-data"></a><span data-ttu-id="07746-134">시스템 데이터베이스 데이터 보기</span><span class="sxs-lookup"><span data-stu-id="07746-134">Viewing System Database Data</span></span>  
 <span data-ttu-id="07746-135">애플리케이션에 필요한 정보를 얻기 위해 불가피한 경우가 아니면 시스템 테이블을 직접 쿼리하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 작성하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="07746-135">You should not code [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that directly query the system tables, unless that is the only way to obtain the information that is required by the application.</span></span> <span data-ttu-id="07746-136">대신 다음 항목을 사용하여 애플리케이션에서 카탈로그나 시스템 정보를 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07746-136">Instead, applications should obtain catalog and system information by using the following:</span></span>  
  
-   <span data-ttu-id="07746-137">시스템 카탈로그 뷰</span><span class="sxs-lookup"><span data-stu-id="07746-137">System catalog views</span></span>  
  
-   <span data-ttu-id="07746-138">SQL-SMO</span><span class="sxs-lookup"><span data-stu-id="07746-138">SQL-SMO</span></span>  
  
-   <span data-ttu-id="07746-139">WMI(Windows Management Instrumentation) 인터페이스</span><span class="sxs-lookup"><span data-stu-id="07746-139">Windows Management Instrumentation (WMI) interface</span></span>  
  
-   <span data-ttu-id="07746-140">ADO, OLE DB, ODBC 등의 애플리케이션에 사용되는 데이터 API의 카탈로그 함수, 메서드, 특성 또는 속성</span><span class="sxs-lookup"><span data-stu-id="07746-140">Catalog functions, methods, attributes, or properties of the data API used in the application, such as ADO, OLE DB, or ODBC.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="07746-141">시스템 저장 프로시저 및 기본 제공 함수</span><span class="sxs-lookup"><span data-stu-id="07746-141">system stored procedures and built-in functions.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="07746-142">관련 작업</span><span class="sxs-lookup"><span data-stu-id="07746-142">Related Tasks</span></span>  
 [<span data-ttu-id="07746-143">시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="07746-143">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [<span data-ttu-id="07746-144">개체 탐색기에서 시스템 개체 숨기기</span><span class="sxs-lookup"><span data-stu-id="07746-144">Hide System Objects in Object Explorer</span></span>](../../ssms/object/object-explorer.md)  
  
## <a name="related-content"></a><span data-ttu-id="07746-145">관련 내용</span><span class="sxs-lookup"><span data-stu-id="07746-145">Related Content</span></span>  
 [<span data-ttu-id="07746-146">카탈로그 뷰&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07746-146">Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
 [<span data-ttu-id="07746-147">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="07746-147">Databases</span></span>](databases.md)  
  
  
