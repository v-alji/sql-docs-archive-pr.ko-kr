---
title: Xp_sqlagent_proxy_account 확장 저장 프로시저 사용을 새로운 저장 프로시저로 대체 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- xp_sqlagent_proxy_account
ms.assetid: 0e3cc931-6237-41dd-bf0d-0c03f4d8fff2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d124ab73f4b4315550134f28ffad232b4a1c0ec2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653134"
---
# <a name="replace-usage-of-the-xp_sqlagent_proxy_account-extended-stored-procedure-with-new-stored-procedures"></a><span data-ttu-id="2bfd3-102">xp_sqlagent_proxy_account 확장 저장 프로시저를 새로운 저장 프로시저로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-102">Replace usage of the xp_sqlagent_proxy_account extended stored procedure with new stored procedures</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2bfd3-103">에이전트는 여러 프록시를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-103">Agent supports multiple proxies.</span></span> <span data-ttu-id="2bfd3-104">새로운 저장 프로시저 집합을 사용하여 이러한 프록시를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-104">You define these proxies by using a new set of stored procedures.</span></span> <span data-ttu-id="2bfd3-105">새로운 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 저장 프로시저에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-105">For more information about the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stored procedures, see the following topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   <span data-ttu-id="2bfd3-106">"sp_add_proxy([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-106">"sp_add_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="2bfd3-107">"sp_delete_proxy([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-107">"sp_delete_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="2bfd3-108">"sp_enum_login_for_proxy([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-108">"sp_enum_login_for_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="2bfd3-109">"sp_enum_proxy_for_subsystem([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-109">"sp_enum_proxy_for_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="2bfd3-110">"sp_enum_sqlagent_subsystems([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-110">"sp_enum_sqlagent_subsystems ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="2bfd3-111">"sp_grant_proxy_to_subsystem([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-111">"sp_grant_proxy_to_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="2bfd3-112">"sp_grant_login_to_proxy([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-112">"sp_grant_login_to_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="2bfd3-113">"sp_help_proxy"([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-113">"sp_help_proxy" ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="2bfd3-114">"sp_revoke_login_from_proxy([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-114">"sp_revoke_login_from_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="2bfd3-115">"sp_revoke_proxy_from_subsystem([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-115">"sp_revoke_proxy_from_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
-   <span data-ttu-id="2bfd3-116">"sp_update_proxy([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span><span class="sxs-lookup"><span data-stu-id="2bfd3-116">"sp_update_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)])"</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2bfd3-117">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]로 업그레이드한 후에는 **xp_sqlagent_proxy_account** 확장 저장 프로시저를 사용하는 모든 문이 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-117">After you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], any statements that use the **xp_sqlagent_proxy_account** extended stored procedure will not work.</span></span> <span data-ttu-id="2bfd3-118">**xp_cmdshell** 에 대한 프록시를 설정하려면 **xp_sqlagent_proxy_account** 대신 **sp_xp_cmdshell_proxy_account**를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="2bfd3-118">Use **sp_xp_cmdshell_proxy_account** instead of **xp_sqlagent_proxy_account** to set the proxy for **xp_cmdshell**.</span></span>  
  
## <a name="component"></a><span data-ttu-id="2bfd3-119">구성 요소</span><span class="sxs-lookup"><span data-stu-id="2bfd3-119">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2bfd3-120">에이전트</span><span class="sxs-lookup"><span data-stu-id="2bfd3-120">Agent</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bfd3-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2bfd3-121">See Also</span></span>  
 [<span data-ttu-id="2bfd3-122">SQL Server 에이전트 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="2bfd3-122">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
