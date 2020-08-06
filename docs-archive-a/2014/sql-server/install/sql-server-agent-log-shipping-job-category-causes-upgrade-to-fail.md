---
title: 로그 전달 작업 범주 SQL Server 에이전트 업그레이드 실패 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
- job categories [SQL Server Agent]
ms.assetid: ef05ce53-c6ce-42ec-9df8-46c951626424
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2f5947e8fc8d459388fe35d86c75666e25b5d907
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742779"
---
# <a name="sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail"></a><span data-ttu-id="ab0b4-102">SQL Server 에이전트 로그 전달 작업 범주로 인해 업그레이드하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-102">SQL Server Agent log shipping job category causes upgrade to fail</span></span>
  <span data-ttu-id="ab0b4-103">로그 전달이라는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 범주가 있으면 업그레이드 프로세스가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-103">The upgrade process will fail if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job category named Log Shipping exists.</span></span>  
  
## <a name="component"></a><span data-ttu-id="ab0b4-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ab0b4-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ab0b4-105">에이전트</span><span class="sxs-lookup"><span data-stu-id="ab0b4-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="ab0b4-106">설명</span><span class="sxs-lookup"><span data-stu-id="ab0b4-106">Description</span></span>  
 <span data-ttu-id="ab0b4-107">로그 전달이라는 시스템 작업 범주가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-107">There is a system job category named Log Shipping.</span></span> <span data-ttu-id="ab0b4-108">업그레이드하려는 설치에 로그 전달이라는 사용자가 만든 작업 범주가 이미 있으면 업그레이드하기 전에 이 작업 범주의 이름을 바꿔야 합니다. 그렇지 않으면 업그레이드 프로세스가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ab0b4-108">If an installation that is being upgraded already contains a user-created job category named Log Shipping, you must rename the job category before you upgrade; otherwise, the upgrade process will fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab0b4-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab0b4-109">See Also</span></span>  
 <span data-ttu-id="ab0b4-110">[업그레이드 후에는 로그 전달이 실행 되지 않습니다.](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md) </span><span class="sxs-lookup"><span data-stu-id="ab0b4-110">[Log shipping will not run after upgrading](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md) </span></span>  
 <span data-ttu-id="ab0b4-111">[업그레이드 하면 SQL Server 에이전트 사용자 프록시 계정이 임시 UpgradedProxyAccount 변경 됩니다.](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span><span class="sxs-lookup"><span data-stu-id="ab0b4-111">[Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span></span>  
 [<span data-ttu-id="ab0b4-112">SQL Server 에이전트 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="ab0b4-112">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
