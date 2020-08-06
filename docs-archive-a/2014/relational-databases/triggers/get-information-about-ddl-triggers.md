---
title: DDL 트리거에 대한 정보 가져오기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- status information [SQL Server], DDL triggers
- DDL triggers, metadata
ms.assetid: 462becea-292a-4b9e-bb98-533e89733911
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cd71d188c2f53bd9872359199c07d700688552d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660397"
---
# <a name="get-information-about-ddl-triggers"></a><span data-ttu-id="861b0-102">DDL 트리거에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="861b0-102">Get Information About DDL Triggers</span></span>
  <span data-ttu-id="861b0-103">이 섹션에 나열된 카탈로그 뷰를 사용하여 DDL 트리거에 대한 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="861b0-103">The catalog views listed in this section can be used to get information about DDL Triggers.</span></span>  
  
 <span data-ttu-id="861b0-104">**DDL 트리거를 발생시킬 수 있는 모든 이벤트 또는 이벤트 그룹에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="861b0-104">**To get information about the events or event groups on which a DDL trigger can fire.**</span></span>  
  
-   [<span data-ttu-id="861b0-105">sys.trigger_event_types&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-105">sys.trigger_event_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-trigger-event-types-transact-sql)  
  
 <span data-ttu-id="861b0-106">**트리거의 종속 관계를 보려면**</span><span class="sxs-lookup"><span data-stu-id="861b0-106">**To view the dependencies of a trigger**</span></span>  
  
-   [<span data-ttu-id="861b0-107">sys.sql_expression_dependencies&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-107">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [<span data-ttu-id="861b0-108">sys.dm_sql_referenced_entities&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-108">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [<span data-ttu-id="861b0-109">sys.dm_sql_referencing_entities&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-109">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="database-scoped-ddl-triggers"></a><span data-ttu-id="861b0-110">데이터베이스 범위 DDL 트리거</span><span class="sxs-lookup"><span data-stu-id="861b0-110">Database-Scoped DDL Triggers</span></span>  
 <span data-ttu-id="861b0-111">**데이터베이스 범위 트리거에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="861b0-111">**To get information about database-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="861b0-112">sys.triggers&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-112">sys.triggers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)  
  
 <span data-ttu-id="861b0-113">**트리거를 실행하는 데이터베이스 이벤트에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="861b0-113">**To get information about database events that fire triggers**</span></span>  
  
-   [<span data-ttu-id="861b0-114">sys.trigger_events&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-114">sys.trigger_events &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)  
  
 <span data-ttu-id="861b0-115">**데이터베이스 범위 트리거의 정의를 보려면**</span><span class="sxs-lookup"><span data-stu-id="861b0-115">**To view the definition of a database-scoped trigger**</span></span>  
  
-   [<span data-ttu-id="861b0-116">sys.sql_modules&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-116">sys.sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
 <span data-ttu-id="861b0-117">**CLR 데이터베이스 범위 트리거에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="861b0-117">**To get information about CLR database-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="861b0-118">sys.assembly_modules&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-118">sys.assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
## <a name="server-scoped-ddl-triggers"></a><span data-ttu-id="861b0-119">서버 범위 DDL 트리거</span><span class="sxs-lookup"><span data-stu-id="861b0-119">Server-Scoped DDL Triggers</span></span>  
 <span data-ttu-id="861b0-120">**서버 범위 트리거에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="861b0-120">**To get information about server-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="861b0-121">sys.server_triggers&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-121">sys.server_triggers &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)  
  
 <span data-ttu-id="861b0-122">**트리거를 실행하는 서버 이벤트에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="861b0-122">**To get information about server events that fire triggers**</span></span>  
  
-   [<span data-ttu-id="861b0-123">sys.server_trigger_events&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-123">sys.server_trigger_events &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)  
  
 <span data-ttu-id="861b0-124">**서버 범위 트리거의 정의를 보려면**</span><span class="sxs-lookup"><span data-stu-id="861b0-124">**To view the definition of a server-scoped trigger**</span></span>  
  
-   [<span data-ttu-id="861b0-125">sys.server_sql_modules&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-125">sys.server_sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)  
  
 <span data-ttu-id="861b0-126">**CLR 서버 범위 트리거에 대한 정보를 가져오려면**</span><span class="sxs-lookup"><span data-stu-id="861b0-126">**To get information about CLR server-scoped triggers**</span></span>  
  
-   [<span data-ttu-id="861b0-127">sys.server_assembly_modules&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="861b0-127">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="861b0-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="861b0-128">See Also</span></span>  
 [<span data-ttu-id="861b0-129">DDL 트리거</span><span class="sxs-lookup"><span data-stu-id="861b0-129">DDL Triggers</span></span>](../triggers/ddl-triggers.md)  
  
  
