---
title: Sysadmin 사용자만 작업 단계 로그 파일을 파일 시스템에 쓸 수 있습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e2bf5095ac1e6b67f6c6f3f87444879913916e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651445"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a><span data-ttu-id="2aecc-102">sysadmin 사용자만 작업 단계 로그 파일을 파일 시스템에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aecc-102">Only sysadmin users can write job step log files to the file system</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="2aecc-103">에서는 선택적으로 각 작업 단계에 대한 로그를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="2aecc-103">optionally writes a log for each job step.</span></span>  
  
## <a name="component"></a><span data-ttu-id="2aecc-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="2aecc-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2aecc-105">에이전트</span><span class="sxs-lookup"><span data-stu-id="2aecc-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="2aecc-106">Description</span><span class="sxs-lookup"><span data-stu-id="2aecc-106">Description</span></span>  
 <span data-ttu-id="2aecc-107">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 **sysadmin** 고정 서버 역할의 멤버가 소유하는 작업에 대한 로그를 파일 시스템에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aecc-107">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write logs to the file system for jobs that are owned by members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="2aecc-108">작업 소유자가 **sysadmin** 역할의 멤버가 아니지만 프록시 계정이 사용되는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 프록시 계정의 자격 증명을 사용하여 파일 시스템에 로그를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aecc-108">If the job owner is not a member of the **sysadmin** role and if the proxy account is enabled, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write logs to the file system by using the credentials of the proxy account.</span></span>  
  
 <span data-ttu-id="2aecc-109">업그레이드 후 **sysadmin** 고정 서버 역할의 멤버가 아닌 사용자는 자신이 소유한 작업에 대한 로그를 더 이상 파일 시스템에 기록할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2aecc-109">After you upgrade, jobs that are owned by users who are not members of the **sysadmin** fixed server role can no longer write logs to the file system.</span></span> <span data-ttu-id="2aecc-110">대신 이러한 사용자는 **msdb** 데이터베이스의 테이블에 로그를 기록하는 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aecc-110">Instead, these users can select the option to write their logs to a table in the **msdb** database.</span></span> <span data-ttu-id="2aecc-111">**sysadmin** 역할의 멤버는 계속 파일 시스템에 로그를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aecc-111">Members of the **sysadmin** role can still write log files to the file system.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="2aecc-112">수정 동작</span><span class="sxs-lookup"><span data-stu-id="2aecc-112">Corrective Action</span></span>  
 <span data-ttu-id="2aecc-113">업그레이드 후 **sysadmin** 역할의 멤버가 아닌 사용자가 소유하는 작업은 계속 실행될 수 있지만 로그는 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2aecc-113">After you upgrade, jobs that are owned by users who are not members of the **sysadmin** role will continue to run, but logs will not be created.</span></span> <span data-ttu-id="2aecc-114">테이블에 작업 단계를 기록하려면 **sysadmin** 역할의 멤버가 아닌 사용자가 수동으로 해당 작업을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2aecc-114">To log job steps to a table, users who are not members of the **sysadmin** role must manually update their jobs.</span></span>  
  
 <span data-ttu-id="2aecc-115">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "작업 만들기", "작업 단계 만들기" 및 "다중 작업 단계 처리"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2aecc-115">For more information, see the topics "Creating Jobs," "Creating Job Steps," and "Handling Multiple Job Steps" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aecc-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2aecc-116">See Also</span></span>  
 [<span data-ttu-id="2aecc-117">SQL Server 에이전트 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="2aecc-117">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
