---
title: 도메인 컨트롤러에서 SQL Server 2008로 업그레이드 하기 위한 서비스 계정 요구 사항 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0680e09548e38760f6ac317fec63152486a4e5fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650449"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a><span data-ttu-id="0c72b-102">도메인 컨트롤러에서 SQL Server 2008로 업그레이드하기 위한 서비스 계정 요구 사항</span><span class="sxs-lookup"><span data-stu-id="0c72b-102">Service account requirements for upgrading to SQL Server 2008 on a domain controller</span></span>
  <span data-ttu-id="0c72b-103">업그레이드 관리자 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 도메인 컨트롤러의 네트워크 서비스 또는 로컬 서비스 계정에서 실행 중인 인스턴스를 검색 했습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0c72b-103">Upgrade Advisor detected an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running under a Network Service or Local Service account on a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] domain controller.</span></span> <span data-ttu-id="0c72b-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 도메인 컨트롤러에 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]가 설치되어 있으면 로컬 서비스 계정 또는 네트워크 서비스 계정 권한으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c72b-104">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] domain controller, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services cannot run under Local Service account or Network Service account privileges.</span></span>  
  
## <a name="component"></a><span data-ttu-id="0c72b-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="0c72b-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="0c72b-106">수정 동작</span><span class="sxs-lookup"><span data-stu-id="0c72b-106">Corrective Action</span></span>  
 <span data-ttu-id="0c72b-107">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정을 도메인 계정이나 로컬 시스템 계정에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="0c72b-107">Make sure that all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service accounts are assigned to either Domain accounts or Local System accounts.</span></span> <span data-ttu-id="0c72b-108">업그레이드하기 전에 이러한 변경 작업을 수행하지 못하면 설치가 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c72b-108">Failure to make this change before upgrading will block Setup.</span></span> <span data-ttu-id="0c72b-109">서비스 계정 SQL 기록기 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Active Directory Helper Service는 네트워크 서비스 계정으로 하드 코딩되어 변경할 수 없으므로 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="0c72b-109">The service accounts SQL Writer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Active Directory Helper services are exceptions because they are hard-coded to the Network Service account and cannot be changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c72b-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0c72b-110">See Also</span></span>  
 <span data-ttu-id="0c72b-111">[업그레이드 문제 데이터베이스 엔진](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0c72b-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="0c72b-112">SQL Server 2014 업그레이드 관리자 &#91;새&#93;</span><span class="sxs-lookup"><span data-stu-id="0c72b-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
