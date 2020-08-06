---
title: 사용 되지 않는 시스템 저장 프로시저에 대 한 참조 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system stored procedures [SQL Server]
- system stored procedures [SQL Server]
ms.assetid: 487d24fc-41d5-495e-843c-0ac974ec472f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65e7da666beaf84050dd8d60caf4cac5bfc013c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735872"
---
# <a name="remove-references-to-deprecated-system-stored-procedures"></a><span data-ttu-id="e39fe-102">더 이상 사용되지 않는 시스템 저장 프로시저에 대한 참조를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e39fe-102">Remove references to deprecated system stored procedures</span></span>
  <span data-ttu-id="e39fe-103">업그레이드 관리자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 더 이상 사용할 수 없는 문서화되지 않은 시스템 저장 프로시저 및 확장 저장 프로시저를 참조하는 문을 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="e39fe-103">Upgrade Advisor detected statements that reference undocumented system stored procedures and extended stored procedures that are no longer available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e39fe-104">이러한 개체를 참조하는 문은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e39fe-104">Statements that reference these objects will fail.</span></span> <span data-ttu-id="e39fe-105">문서화되지 않은 시스템 개체나 API는 이후 릴리스에서 알림 표시 없이 변경되거나 제거될 수 있으므로 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="e39fe-105">Do not use undocumented system objects or APIs as the functionality might change or be removed without notification in a future release.</span></span>  
  
## <a name="component"></a><span data-ttu-id="e39fe-106">구성 요소</span><span class="sxs-lookup"><span data-stu-id="e39fe-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="e39fe-107">설명</span><span class="sxs-lookup"><span data-stu-id="e39fe-107">Description</span></span>  
  
### <a name="documented-system-stored-procedures"></a><span data-ttu-id="e39fe-108">문서화된 시스템 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="e39fe-108">Documented System Stored Procedures</span></span>  
 <span data-ttu-id="e39fe-109">다음 문서화된 시스템 저장 프로시저가 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e39fe-109">The following documented system stored procedures have been removed:</span></span>  
  
-   <span data-ttu-id="e39fe-110">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="e39fe-110">sp_addalias</span></span>  
  
-   <span data-ttu-id="e39fe-111">sp_addgroup</span><span class="sxs-lookup"><span data-stu-id="e39fe-111">sp_addgroup</span></span>  
  
-   <span data-ttu-id="e39fe-112">sp_changegroup</span><span class="sxs-lookup"><span data-stu-id="e39fe-112">sp_changegroup</span></span>  
  
-   <span data-ttu-id="e39fe-113">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="e39fe-113">sp_dropgroup</span></span>  
  
-   <span data-ttu-id="e39fe-114">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="e39fe-114">sp_helpgroup</span></span>  
  
### <a name="undocumented-system-stored-procedures"></a><span data-ttu-id="e39fe-115">문서화되지 않은 시스템 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="e39fe-115">Undocumented System Stored Procedures</span></span>  
 <span data-ttu-id="e39fe-116">다음 문서화되지 않은 시스템 저장 프로시저 및 확장 저장 프로시저가 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e39fe-116">The following undocumented system stored procedures and extended stored procedures have been removed:</span></span>  
  
-   <span data-ttu-id="e39fe-117">sp_articlesynctranprocs</span><span class="sxs-lookup"><span data-stu-id="e39fe-117">sp_articlesynctranprocs</span></span>  
  
-   <span data-ttu-id="e39fe-118">sp_diskdefault</span><span class="sxs-lookup"><span data-stu-id="e39fe-118">sp_diskdefault</span></span>  
  
-   <span data-ttu-id="e39fe-119">sp_EventLog</span><span class="sxs-lookup"><span data-stu-id="e39fe-119">sp_EventLog</span></span>  
  
-   <span data-ttu-id="e39fe-120">sp_GetMBCSCharLen</span><span class="sxs-lookup"><span data-stu-id="e39fe-120">sp_GetMBCSCharLen</span></span>  
  
-   <span data-ttu-id="e39fe-121">sp_helplog</span><span class="sxs-lookup"><span data-stu-id="e39fe-121">sp_helplog</span></span>  
  
-   <span data-ttu-id="e39fe-122">sp_helpsql</span><span class="sxs-lookup"><span data-stu-id="e39fe-122">sp_helpsql</span></span>  
  
-   <span data-ttu-id="e39fe-123">sp_IsMBCSLeadByte</span><span class="sxs-lookup"><span data-stu-id="e39fe-123">sp_IsMBCSLeadByte</span></span>  
  
-   <span data-ttu-id="e39fe-124">sp_lock2</span><span class="sxs-lookup"><span data-stu-id="e39fe-124">sp_lock2</span></span>  
  
-   <span data-ttu-id="e39fe-125">sp_MSget_current_activity</span><span class="sxs-lookup"><span data-stu-id="e39fe-125">sp_MSget_current_activity</span></span>  
  
-   <span data-ttu-id="e39fe-126">sp_MSset_current_activity</span><span class="sxs-lookup"><span data-stu-id="e39fe-126">sp_MSset_current_activity</span></span>  
  
-   <span data-ttu-id="e39fe-127">sp_MSobjessearch</span><span class="sxs-lookup"><span data-stu-id="e39fe-127">sp_MSobjessearch</span></span>  
  
-   <span data-ttu-id="e39fe-128">xp_enum_ActiveScriptEngines</span><span class="sxs-lookup"><span data-stu-id="e39fe-128">xp_enum_ActiveScriptEngines</span></span>  
  
-   <span data-ttu-id="e39fe-129">xp_eventlog</span><span class="sxs-lookup"><span data-stu-id="e39fe-129">xp_eventlog</span></span>  
  
-   <span data-ttu-id="e39fe-130">xp_GetAdminGroupName</span><span class="sxs-lookup"><span data-stu-id="e39fe-130">xp_GetAdminGroupName</span></span>  
  
-   <span data-ttu-id="e39fe-131">xp_GetFileDetails</span><span class="sxs-lookup"><span data-stu-id="e39fe-131">xp_GetFileDetails</span></span>  
  
-   <span data-ttu-id="e39fe-132">xp_GetLocalSystemAccountName</span><span class="sxs-lookup"><span data-stu-id="e39fe-132">xp_GetLocalSystemAccountName</span></span>  
  
-   <span data-ttu-id="e39fe-133">xp_IsNTAdmin</span><span class="sxs-lookup"><span data-stu-id="e39fe-133">xp_IsNTAdmin</span></span>  
  
-   <span data-ttu-id="e39fe-134">xp_MSLocalSystem</span><span class="sxs-lookup"><span data-stu-id="e39fe-134">xp_MSLocalSystem</span></span>  
  
-   <span data-ttu-id="e39fe-135">xp_MSnt2000</span><span class="sxs-lookup"><span data-stu-id="e39fe-135">xp_MSnt2000</span></span>  
  
-   <span data-ttu-id="e39fe-136">xp_MSplatform</span><span class="sxs-lookup"><span data-stu-id="e39fe-136">xp_MSplatform</span></span>  
  
-   <span data-ttu-id="e39fe-137">xp_SetSecurity</span><span class="sxs-lookup"><span data-stu-id="e39fe-137">xp_SetSecurity</span></span>  
  
-   <span data-ttu-id="e39fe-138">xp_varbintohexstr</span><span class="sxs-lookup"><span data-stu-id="e39fe-138">xp_varbintohexstr</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="e39fe-139">수정 동작</span><span class="sxs-lookup"><span data-stu-id="e39fe-139">Corrective Action</span></span>  
  
### <a name="documented-system-stored-procedures"></a><span data-ttu-id="e39fe-140">문서화된 시스템 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="e39fe-140">Documented System Stored Procedures</span></span>  
 <span data-ttu-id="e39fe-141">다음 표에 따라 애플리케이션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="e39fe-141">Modify your applications according to the following table.</span></span>  
  
|<span data-ttu-id="e39fe-142">이전</span><span class="sxs-lookup"><span data-stu-id="e39fe-142">Instead of</span></span>|<span data-ttu-id="e39fe-143">단계</span><span class="sxs-lookup"><span data-stu-id="e39fe-143">Do this</span></span>|  
|----------------|-------------|  
|<span data-ttu-id="e39fe-144">sp_addalias</span><span class="sxs-lookup"><span data-stu-id="e39fe-144">sp_addalias</span></span>|<span data-ttu-id="e39fe-145">별칭을 사용자 계정 및 데이터베이스 역할의 조합으로 대체해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e39fe-145">Replace aliases with a combination of user accounts and database roles.</span></span> <span data-ttu-id="e39fe-146">자세한 내용은 SQL Server 온라인 설명서의 "CREATE USER(Transact-SQL)" 및 "CREATE ROLE(Transact-SQL)"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e39fe-146">For more information, see "CREATE USER (Transact-SQL)" and "CREATE ROLE (Transact-SQL)" in SQL Server Books Online.</span></span> <span data-ttu-id="e39fe-147">업그레이드된 데이터베이스에서는 sp_dropalias를 사용하여 별칭을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e39fe-147">Remove aliases in upgraded databases by using sp_dropalias.</span></span>|  
|<span data-ttu-id="e39fe-148">sp_addgroupsp_changegroup</span><span class="sxs-lookup"><span data-stu-id="e39fe-148">sp_addgroupsp_changegroup</span></span><br /><br /> <span data-ttu-id="e39fe-149">sp_dropgroup</span><span class="sxs-lookup"><span data-stu-id="e39fe-149">sp_dropgroup</span></span><br /><br /> <span data-ttu-id="e39fe-150">sp_helpgroup</span><span class="sxs-lookup"><span data-stu-id="e39fe-150">sp_helpgroup</span></span>|<span data-ttu-id="e39fe-151">역할을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e39fe-151">Use roles.</span></span> <span data-ttu-id="e39fe-152">자세한 내용은 SQL Server 온라인 설명서의 "서버 수준 역할" 및 "데이터베이스 수준 역할"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e39fe-152">For more information, see "Server-Level Roles" and "Database-Level Roles" in SQL Server Books Online.</span></span>|  
  
### <a name="undocmented-system-stored-procedures"></a><span data-ttu-id="e39fe-153">문서화되지 않은 시스템 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="e39fe-153">Undocmented System Stored Procedures</span></span>  
 <span data-ttu-id="e39fe-154">동일한 기능이 있는 CLR 저장 프로시저를 만들어 문서화되지 않은 시스템 저장 프로시저를 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e39fe-154">You can create CLR stored procedures with equivalent functionality to replace the undocumented system stored procedures.</span></span> <span data-ttu-id="e39fe-155">자세한 내용은 SQL Server 온라인 설명서에서 "CLR 저장 프로시저"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e39fe-155">For more information, see the topic "CLR Stored Procedures" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39fe-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e39fe-156">See Also</span></span>  
 <span data-ttu-id="e39fe-157">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="e39fe-157">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="e39fe-158">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="e39fe-158">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
