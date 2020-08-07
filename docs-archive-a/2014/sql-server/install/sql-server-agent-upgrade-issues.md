---
title: SQL Server 에이전트 업그레이드 문제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server Agent
- SQL Server Agent, upgrades
ms.assetid: 77e303ff-febd-4103-ae5d-6e5b85bc8009
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ac234a757510af5ebfac261ea6d3e7e57d2f426f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732288"
---
# <a name="sql-server-agent-upgrade-issues"></a><span data-ttu-id="e732c-102">SQL Server 에이전트 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="e732c-102">SQL Server Agent Upgrade Issues</span></span>
  <span data-ttu-id="e732c-103">다음 항목에서는 업그레이드에 영향을 줄 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 문제에 대해 설명하고</span><span class="sxs-lookup"><span data-stu-id="e732c-103">The following topics describe the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent issues that might affect an upgrade.</span></span> <span data-ttu-id="e732c-104">이러한 변화가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 환경에 미치는 영향을 완화하기 위해 취할 수 있는 조치에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e732c-104">The topics describe actions that you can take to help reduce the effect of these changes on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e732c-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="e732c-105">In This Section</span></span>  
  
-   [<span data-ttu-id="e732c-106">데이터베이스 유지 관리 계획이 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="e732c-106">Database maintenance plans superseded</span></span>](../../../2014/sql-server/install/database-maintenance-plans-superseded.md)  
  
-   [<span data-ttu-id="e732c-107">sysadmin 사용자만 작업 단계 로그 파일을 파일 시스템에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e732c-107">Only sysadmin users can write job step log files to the file system</span></span>](../../../2014/sql-server/install/only-sysadmin-users-can-write-job-step-log-files-to-the-file-system.md)  
  
-   [<span data-ttu-id="e732c-108">xp_sqlagent_proxy_account 확장 저장 프로시저를 새로운 저장 프로시저로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="e732c-108">Replace usage of the xp_sqlagent_proxy_account extended stored procedure with new stored procedures</span></span>](../../../2014/sql-server/install/replace-xp-sqlagent-proxy-account-extended-sp-with-new-stored-procedures.md)  
  
-   [<span data-ttu-id="e732c-109">SQL Server 에이전트 로그 전달 작업 범주로 인해 업그레이드하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="e732c-109">SQL Server Agent log shipping job category causes upgrade to fail</span></span>](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)  
  
-   [<span data-ttu-id="e732c-110">SQL Server 에이전트 서비스는 SQL Server 인증을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e732c-110">SQL Server Agent Service cannot use SQL Server Authentication</span></span>](../../../2014/sql-server/install/sql-server-agent-service-cannot-use-sql-server-authentication.md)  
  
-   [<span data-ttu-id="e732c-111">SQL Server 에이전트 작업 단계의 토큰 구문을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="e732c-111">Update token syntax in SQL Server Agent job steps</span></span>](../../../2014/sql-server/install/update-token-syntax-in-sql-server-agent-job-steps.md)  
  
-   [<span data-ttu-id="e732c-112">마스터 서버를 업그레이드하기 전에 모든 대상 서버를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="e732c-112">Upgrade all target servers before upgrading the master server</span></span>](../../../2014/sql-server/install/upgrade-all-target-servers-before-upgrading-the-master-server.md)  
  
-   [<span data-ttu-id="e732c-113">업그레이드하면 SQL Server 에이전트 사용자 프록시 계정이 임시 UpgradedProxyAccount로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="e732c-113">Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount</span></span>](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)  
  
## <a name="see-also"></a><span data-ttu-id="e732c-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e732c-114">See Also</span></span>  
 <span data-ttu-id="e732c-115">[SQL Server 2014 업그레이드 관리자 &#91;새&#93;](sql-server-2014-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="e732c-115">[SQL Server 2014 Upgrade Advisor &#91;new&#93;](sql-server-2014-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="e732c-116">업그레이드 문제 해결</span><span class="sxs-lookup"><span data-stu-id="e732c-116">Resolving Upgrade Issues</span></span>](../../../2014/sql-server/install/resolving-upgrade-issues.md)  
  
  
