---
title: 마스터 서버를 업그레이드 하기 전에 모든 대상 서버 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 031fedc4af4b058704cef1da8df846397b235305
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646815"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a><span data-ttu-id="5968e-102">마스터 서버를 업그레이드하기 전에 모든 대상 서버를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="5968e-102">Upgrade all target servers before upgrading the master server</span></span>
  <span data-ttu-id="5968e-103">마스터 서버를 업그레이드하기 전에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하고 있고 대상 서버로 구성된 모든 컴퓨터를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="5968e-103">Before you upgrade the master server, upgrade all computers that are running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are configured as target servers.</span></span>  
  
## <a name="component"></a><span data-ttu-id="5968e-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5968e-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5968e-105">에이전트</span><span class="sxs-lookup"><span data-stu-id="5968e-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="5968e-106">Description</span><span class="sxs-lookup"><span data-stu-id="5968e-106">Description</span></span>  
 <span data-ttu-id="5968e-107">다중 서버 환경에서 관리를 자동화하려면 마스터 서버와 대상 서버가 적어도 하나씩 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5968e-107">To automate administration in multiserver environments, you must have at least one master server and at least one target server.</span></span> <span data-ttu-id="5968e-108">마스터 서버는 대상 서버에 작업을 배포하거나 대상 서버에서 이벤트를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="5968e-108">A master server distributes jobs to, and receives events from, target servers.</span></span> <span data-ttu-id="5968e-109">또한 마스터 서버에서는 대상 서버에서 실행되는 작업에 대한 작업 정의의 중앙 복사본을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5968e-109">A master server also stores the central copy of job definitions for jobs that are run on target servers.</span></span>  
  
 <span data-ttu-id="5968e-110">현재 서버가 마스터 서버로 구성된 경우 마스터 서버를 업그레이드하기 전에 모든 대상 서버를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="5968e-110">If the current server is configured as a master server, upgrade all of your target servers first before you upgrade the master server.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="5968e-111">수정 동작</span><span class="sxs-lookup"><span data-stu-id="5968e-111">Corrective Action</span></span>  
 <span data-ttu-id="5968e-112">마스터 서버를 업그레이드하기 전에 모든 대상 서버를 업그레이드할 수 없는 경우 대상 서버를 모두 제거하고 업그레이드한 후 대상 서버를 모두 다시 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5968e-112">If you cannot upgrade all target servers before you upgrade the master server, you must defect all target servers and reenlist them after you upgrade.</span></span>  
  
 <span data-ttu-id="5968e-113">자세한 내용은 온라인 설명서의 "엔터프라이즈에서 관리 자동화", "How to: 대상 서버에서 마스터 서버에서 대상 서버 제거" 및 "방법: 대상 서버를 마스터에 등록" 항목을 참조 하십시오 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5968e-113">For more information, see the topics "Automating Administration across an Enterprise," "How to: Defect a Target Server from a Master Server," and "How to: Enlist a Target Server to a Master" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5968e-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5968e-114">See Also</span></span>  
 <span data-ttu-id="5968e-115">[업그레이드 문제 SQL Server 에이전트](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="5968e-115">[SQL Server Agent Upgrade Issues](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="5968e-116">SQL Server 에이전트 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="5968e-116">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
