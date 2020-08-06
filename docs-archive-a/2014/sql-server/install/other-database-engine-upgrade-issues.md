---
title: 기타 데이터베이스 엔진 업그레이드 문제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], upgrading
ms.assetid: 78a1d8e8-fa97-476f-8777-84617d145340
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: db496112fc975304bb2d7da9d9ea1c52e6dd8bec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648764"
---
# <a name="other-database-engine-upgrade-issues"></a><span data-ttu-id="0231f-102">기타 데이터베이스 엔진 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="0231f-102">Other Database Engine Upgrade Issues</span></span>
  <span data-ttu-id="0231f-103">다음은 최신 업그레이드 관리자 버전에서 감지할 수 없는 업그레이드 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-103">The following upgrade issues cannot be detected by the current version of Upgrade Advisor.</span></span> <span data-ttu-id="0231f-104">아래에 나와 있는 문제를 검토하여 이러한 문제가 시스템에 줄 수 있는 잠재적 영향을 평가하십시오.</span><span class="sxs-lookup"><span data-stu-id="0231f-104">Review the issues listed below to evaluate their potential impact to your systems.</span></span>  
  
## <a name="multiple-database-engine-deprecated-features"></a><span data-ttu-id="0231f-105">여러 데이터베이스 엔진 기능이 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="0231f-105">Multiple Database Engine Deprecated Features</span></span>  
 <span data-ttu-id="0231f-106">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 또는 옵션은 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-106">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or options are deprecated:</span></span>  
  
-   <span data-ttu-id="0231f-107">BACKUP LOG의 NO_LOG 및 TRUNCATE_ONLY 옵션</span><span class="sxs-lookup"><span data-stu-id="0231f-107">NO_LOG and TRUNCATE_ONLY options of BACKUP LOG</span></span>  
  
-   <span data-ttu-id="0231f-108">BACKUP TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="0231f-108">BACKUP TRANSACTION</span></span>  
  
-   <span data-ttu-id="0231f-109">RESTORE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="0231f-109">RESTORE TRANSACTION</span></span>  
  
-   <span data-ttu-id="0231f-110">DUMP</span><span class="sxs-lookup"><span data-stu-id="0231f-110">DUMP</span></span>  
  
-   <span data-ttu-id="0231f-111">LOAD</span><span class="sxs-lookup"><span data-stu-id="0231f-111">LOAD</span></span>  
  
-   <span data-ttu-id="0231f-112">DBCC CONCURRENCYVIOLATION</span><span class="sxs-lookup"><span data-stu-id="0231f-112">DBCC CONCURRENCYVIOLATION</span></span>  
  
-   <span data-ttu-id="0231f-113">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="0231f-113">sp_addalias</span></span>  
  
-   <span data-ttu-id="0231f-114">sp_addgroup</span><span class="sxs-lookup"><span data-stu-id="0231f-114">sp_addgroup</span></span>  
  
-   <span data-ttu-id="0231f-115">sp_changegroup</span><span class="sxs-lookup"><span data-stu-id="0231f-115">sp_changegroup</span></span>  
  
-   <span data-ttu-id="0231f-116">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="0231f-116">sp_dropgroup</span></span>  
  
-   <span data-ttu-id="0231f-117">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="0231f-117">sp_helpgroup</span></span>  
  
-   <span data-ttu-id="0231f-118">syssegments</span><span class="sxs-lookup"><span data-stu-id="0231f-118">syssegments</span></span>  
  
 <span data-ttu-id="0231f-119">VIA 프로토콜을 사용한 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 대한 연결은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-119">Use of the VIA protocol to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is deprecated.</span></span>  
  
## <a name="new-data-types"></a><span data-ttu-id="0231f-120">새 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="0231f-120">New Data Types</span></span>  
 <span data-ttu-id="0231f-121">다음과 같은 데이터가 시스템 형식으로 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-121">The following will be reserved system types.</span></span> <span data-ttu-id="0231f-122">업그레이드하기 전이나 후에 충돌하는 기존 사용자 정의 형식의 이름을 바꾸십시오.</span><span class="sxs-lookup"><span data-stu-id="0231f-122">Rename the existing conflicting user defined types either before or after upgrade.</span></span>  
  
-   <span data-ttu-id="0231f-123">Geography</span><span class="sxs-lookup"><span data-stu-id="0231f-123">Geography</span></span>  
  
-   <span data-ttu-id="0231f-124">기하 도형</span><span class="sxs-lookup"><span data-stu-id="0231f-124">Geometry</span></span>  
  
-   <span data-ttu-id="0231f-125">Datetime2</span><span class="sxs-lookup"><span data-stu-id="0231f-125">Datetime2</span></span>  
  
-   <span data-ttu-id="0231f-126">HierarchyID</span><span class="sxs-lookup"><span data-stu-id="0231f-126">HierarchyID</span></span>  
  
## <a name="target-table-of-the-output-into-clause-cannot-have-any-defined-triggers"></a><span data-ttu-id="0231f-127">OUTPUT INTO 절의 대상 테이블에는 정의된 트리거를 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="0231f-127">Target Table of the OUTPUT INTO Clause Cannot Have Any Defined Triggers</span></span>  
 <span data-ttu-id="0231f-128">테이블에 활성화 된 트리거가 있는 경우 대상 테이블에 대 한 출력은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-128">OUTPUT INTO a target table when the table has any enabled triggers is not supported.</span></span>  
  
## <a name="compile-time-error-for-udfs-when-the-target-of-an-output-into-clause-is-a-table"></a><span data-ttu-id="0231f-129">OUTPUT INTO 절의 대상이 테이블일 경우 UDF를 컴파일할 때 오류가 발생함</span><span class="sxs-lookup"><span data-stu-id="0231f-129">Compile Time Error for UDFs When the Target of an OUTPUT INTO Clause is a Table</span></span>  
 <span data-ttu-id="0231f-130">UDF(사용자 정의 함수)를 사용하여 데이터베이스 상태 수정 동작을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-130">User-defined functions (UDF) cannot be used to perform actions that modify the database state.</span></span> <span data-ttu-id="0231f-131">예를 들어 UDF는 테이블 변수를 제외한 모든 개체에 대해 DDL(CREATE/ALTER/DROP) 또는 DML(INSERT/UPDATE/DELETE) 동작을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-131">For example, a UDF cannot perform any DDL (CREATE/ALTER/DROP) or DML (INSERT/UPDATE/DELETE) actions on any objects, except for table variables.</span></span>  
  
## <a name="merge-is-a-reserved-keyword"></a><span data-ttu-id="0231f-132">MERGE는 예약 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-132">MERGE is a Reserved Keyword</span></span>  
 <span data-ttu-id="0231f-133">MERGE는 이제 완전 예약 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-133">MERGE is now a fully-reserved keyword.</span></span> <span data-ttu-id="0231f-134">애플리케이션에 MERGE라는 개체(테이블, 열 등)가 더 이상 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-134">Applications can no longer have objects (table, column, etc.) called MERGE.</span></span>  
  
## <a name="rename-cdc-schema"></a><span data-ttu-id="0231f-135">CDC 스키마 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="0231f-135">Rename CDC Schema</span></span>  
 <span data-ttu-id="0231f-136">CDC라는 스키마 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-136">There is a schema name called CDC.</span></span> <span data-ttu-id="0231f-137">데이터베이스에 **변경 데이터 캡처가** 설정 된 경우에는이 스키마 이름을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-137">This schema name cannot be in used if **Change Data Capture** is enabled for the database.</span></span>  
  
 <span data-ttu-id="0231f-138">데이터베이스에 대 한 **변경 데이터 캡처** 를 사용 하도록 설정 하기 전에 CDC 스키마를 삭제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-138">You must drop the CDC schema before you enable **Change Data Capture** for the database.</span></span> <span data-ttu-id="0231f-139">이 작업은 업그레이드하기 전이나 후에 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-139">This step can be done before or after the upgrade.</span></span> <span data-ttu-id="0231f-140">스키마를 삭제하려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="0231f-140">To drop the schema, use the following steps:</span></span>  
  
1.  <span data-ttu-id="0231f-141">ALTER SCHEMA를 사용하여 CDC 스키마의 개체를 새 스키마 이름으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-141">Transfer the objects from CDC schema to a new schema name using ALTER SCHEMA.</span></span>  
  
2.  <span data-ttu-id="0231f-142">새 스키마에 있는 개체에 대한 사용 권한을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-142">Verify permissions for the objects in the new schema.</span></span>  
  
3.  <span data-ttu-id="0231f-143">필요에 따라 애플리케이션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-143">Make necessary modifications to the application.</span></span>  
  
4.  <span data-ttu-id="0231f-144">DROP SCHEMA를 사용하여 CDC 스키마를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0231f-144">Drop the CDC schema using DROP SCHEMA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0231f-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0231f-145">See Also</span></span>  
 [<span data-ttu-id="0231f-146">데이터베이스 엔진 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="0231f-146">Database Engine Upgrade Issues</span></span>](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  
