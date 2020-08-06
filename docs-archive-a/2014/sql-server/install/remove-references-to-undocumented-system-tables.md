---
title: 문서화 되지 않은 시스템 테이블에 대 한 참조 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 45c38038ee3d3214e4303c0ddbe0110be926c37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735875"
---
# <a name="remove-references-to-undocumented-system-tables"></a><span data-ttu-id="86219-102">문서화되지 않은 시스템 테이블에 대한 참조를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="86219-102">Remove references to undocumented system tables</span></span>
  <span data-ttu-id="86219-103">이전 릴리스에서 문서화되지 않은 많은 시스템 테이블이 변경되었거나 더 이상 존재하지 않기 때문에 업그레이드한 후 이러한 테이블을 사용하면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86219-103">Many system tables that were undocumented in prior releases have changed or no longer exist; therefore, using these tables may cause errors after upgrading.</span></span> <span data-ttu-id="86219-104">업그레이드 관리자는 시스템 테이블 이름에 대한 참조를 찾기 때문에 시스템 테이블과 동일한 이름을 갖는 모든 사용자 테이블에 대한 참조를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="86219-104">Because Upgrade Advisor looks for references to system table names, it will report references to any user tables that have the same names as system tables.</span></span>  
  
## <a name="component"></a><span data-ttu-id="86219-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="86219-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="86219-106">설명</span><span class="sxs-lookup"><span data-stu-id="86219-106">Description</span></span>  
 <span data-ttu-id="86219-107">다음과 같은 문서화되지 않은 시스템 테이블이 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="86219-107">The following undocumented system tables are removed:</span></span>  
  
-   <span data-ttu-id="86219-108">**spt_datatype_info**</span><span class="sxs-lookup"><span data-stu-id="86219-108">**spt_datatype_info**</span></span>  
  
-   <span data-ttu-id="86219-109">**spt_datatype_info_ext**</span><span class="sxs-lookup"><span data-stu-id="86219-109">**spt_datatype_info_ext**</span></span>  
  
-   <span data-ttu-id="86219-110">**spt_provider_types**</span><span class="sxs-lookup"><span data-stu-id="86219-110">**spt_provider_types**</span></span>  
  
-   <span data-ttu-id="86219-111">**spt_server_info**</span><span class="sxs-lookup"><span data-stu-id="86219-111">**spt_server_info**</span></span>  
  
-   <span data-ttu-id="86219-112">**spt_values**</span><span class="sxs-lookup"><span data-stu-id="86219-112">**spt_values**</span></span>  
  
-   <span data-ttu-id="86219-113">**sysfulltextnotify**</span><span class="sxs-lookup"><span data-stu-id="86219-113">**sysfulltextnotify**</span></span>  
  
-   <span data-ttu-id="86219-114">**syslocks**</span><span class="sxs-lookup"><span data-stu-id="86219-114">**syslocks**</span></span>  
  
-   <span data-ttu-id="86219-115">**sysproperties**</span><span class="sxs-lookup"><span data-stu-id="86219-115">**sysproperties**</span></span>  
  
-   <span data-ttu-id="86219-116">**sysprotects_aux**</span><span class="sxs-lookup"><span data-stu-id="86219-116">**sysprotects_aux**</span></span>  
  
-   <span data-ttu-id="86219-117">**sysprotects_view**</span><span class="sxs-lookup"><span data-stu-id="86219-117">**sysprotects_view**</span></span>  
  
-   <span data-ttu-id="86219-118">**SYSREMOTE_CATALOGS**</span><span class="sxs-lookup"><span data-stu-id="86219-118">**SYSREMOTE_CATALOGS**</span></span>  
  
-   <span data-ttu-id="86219-119">**SYSREMOTE_COLUMN_PRIVILEGES**</span><span class="sxs-lookup"><span data-stu-id="86219-119">**SYSREMOTE_COLUMN_PRIVILEGES**</span></span>  
  
-   <span data-ttu-id="86219-120">**SYSREMOTE_COLUMNS**</span><span class="sxs-lookup"><span data-stu-id="86219-120">**SYSREMOTE_COLUMNS**</span></span>  
  
-   <span data-ttu-id="86219-121">**SYSREMOTE_FOREIGN_KEYS**</span><span class="sxs-lookup"><span data-stu-id="86219-121">**SYSREMOTE_FOREIGN_KEYS**</span></span>  
  
-   <span data-ttu-id="86219-122">**SYSREMOTE_INDEXES**</span><span class="sxs-lookup"><span data-stu-id="86219-122">**SYSREMOTE_INDEXES**</span></span>  
  
-   <span data-ttu-id="86219-123">**SYSREMOTE_PRIMARY_KEYS**</span><span class="sxs-lookup"><span data-stu-id="86219-123">**SYSREMOTE_PRIMARY_KEYS**</span></span>  
  
-   <span data-ttu-id="86219-124">**SYSREMOTE_PROVIDER_TYPES**</span><span class="sxs-lookup"><span data-stu-id="86219-124">**SYSREMOTE_PROVIDER_TYPES**</span></span>  
  
-   <span data-ttu-id="86219-125">**SYSREMOTE_SCHEMATA**</span><span class="sxs-lookup"><span data-stu-id="86219-125">**SYSREMOTE_SCHEMATA**</span></span>  
  
-   <span data-ttu-id="86219-126">**SYSREMOTE_STATISTICS**</span><span class="sxs-lookup"><span data-stu-id="86219-126">**SYSREMOTE_STATISTICS**</span></span>  
  
-   <span data-ttu-id="86219-127">**SYSREMOTE_TABLE_PRIVILEGES**</span><span class="sxs-lookup"><span data-stu-id="86219-127">**SYSREMOTE_TABLE_PRIVILEGES**</span></span>  
  
-   <span data-ttu-id="86219-128">**SYSREMOTE_TABLES**</span><span class="sxs-lookup"><span data-stu-id="86219-128">**SYSREMOTE_TABLES**</span></span>  
  
-   <span data-ttu-id="86219-129">**SYSREMOTE_VIEWS**</span><span class="sxs-lookup"><span data-stu-id="86219-129">**SYSREMOTE_VIEWS**</span></span>  
  
-   <span data-ttu-id="86219-130">**syssegments**</span><span class="sxs-lookup"><span data-stu-id="86219-130">**syssegments**</span></span>  
  
-   <span data-ttu-id="86219-131">**sysxlogins**</span><span class="sxs-lookup"><span data-stu-id="86219-131">**sysxlogins**</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="86219-132">수정 동작</span><span class="sxs-lookup"><span data-stu-id="86219-132">Corrective Action</span></span>  
 <span data-ttu-id="86219-133">다음 표에 따라 애플리케이션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="86219-133">Modify your applications according to the following table.</span></span>  
  
|<span data-ttu-id="86219-134">이전</span><span class="sxs-lookup"><span data-stu-id="86219-134">Instead of</span></span>|<span data-ttu-id="86219-135">Windows Server Update Services와 함께</span><span class="sxs-lookup"><span data-stu-id="86219-135">Use</span></span>|  
|----------------|---------|  
|<span data-ttu-id="86219-136">**sysfulltextnotify**</span><span class="sxs-lookup"><span data-stu-id="86219-136">**sysfulltextnotify**</span></span>|<span data-ttu-id="86219-137">OBJECTPROPERTYEX 함수의**TableFulltextPendingChanges** 속성</span><span class="sxs-lookup"><span data-stu-id="86219-137">**TableFulltextPendingChanges** property of the OBJECTPROPERTYEX function.</span></span>|  
|<span data-ttu-id="86219-138">**syslocks**</span><span class="sxs-lookup"><span data-stu-id="86219-138">**syslocks**</span></span>|<span data-ttu-id="86219-139">**sys.dm_tran_locks** 동적 관리 뷰, sp_lock 또는 **sys.syslockinfo** 호환성 뷰</span><span class="sxs-lookup"><span data-stu-id="86219-139">**sys.dm_tran_locks** dynamic management view, or sp_lock, or the **sys.syslockinfo** compatibility view.</span></span>|  
|<span data-ttu-id="86219-140">**sysproperties**</span><span class="sxs-lookup"><span data-stu-id="86219-140">**sysproperties**</span></span>|<span data-ttu-id="86219-141">**sys.extended_properties** 카탈로그 뷰 또는 **fn_listextendedproperty** 함수</span><span class="sxs-lookup"><span data-stu-id="86219-141">**sys.extended_properties** catalog view or the **fn_listextendedproperty** function</span></span>|  
|<span data-ttu-id="86219-142">**sysxlogins**</span><span class="sxs-lookup"><span data-stu-id="86219-142">**sysxlogins**</span></span>|<span data-ttu-id="86219-143">**sys.server_principals** 카탈로그 뷰 또는 **syslogins** 호환성 뷰</span><span class="sxs-lookup"><span data-stu-id="86219-143">**sys.server_principals** catalog view or **syslogins** compatibility view.</span></span>|  
|<span data-ttu-id="86219-144">모든 **spt_** 테이블</span><span class="sxs-lookup"><span data-stu-id="86219-144">all **spt_** tables</span></span>|<span data-ttu-id="86219-145">사용 가능한 대체 항목 없음</span><span class="sxs-lookup"><span data-stu-id="86219-145">No replacement available</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86219-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86219-146">See Also</span></span>  
 <span data-ttu-id="86219-147">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="86219-147">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="86219-148">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="86219-148">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
