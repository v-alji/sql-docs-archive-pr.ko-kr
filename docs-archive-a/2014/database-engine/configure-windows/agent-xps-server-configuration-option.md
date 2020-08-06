---
title: Agent XPs 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 541c81ea8d9f782a9c1ea391824b90a6fee772d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652345"
---
# <a name="agent-xps-server-configuration-option"></a><span data-ttu-id="82398-102">Agent XPs 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="82398-102">Agent XPs Server Configuration Option</span></span>
  <span data-ttu-id="82398-103">**Agent XPs** 옵션을 사용하여 이 서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 확장 저장 프로시저를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82398-103">Use the **Agent XPs** option to enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures on this server.</span></span> <span data-ttu-id="82398-104">이 옵션을 해제하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 탐색기에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에이전트 노드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82398-104">When this option is not enabled, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node is not available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer.</span></span>  
  
 <span data-ttu-id="82398-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 도구를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 시작하면 이러한 확장 저장 프로시저가 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="82398-105">When you use the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] tool to start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, these extended stored procedures are enabled automatically.</span></span> <span data-ttu-id="82398-106">자세한 내용은 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82398-106">For more information, see [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="82398-107">에이전트 서비스 상태에 관계없이 이러한 확장 저장 프로시저가 활성화되어 있지 않으면 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 노드의 콘텐츠를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82398-107">Object Explorer does not display the contents of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent node unless these extended stored procedures are enabled regardless of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service state.</span></span>  
  
 <span data-ttu-id="82398-108">사용 가능한 값은</span><span class="sxs-lookup"><span data-stu-id="82398-108">The possible values are:</span></span>  
  
-   <span data-ttu-id="82398-109">**0**은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 확장 저장 프로시저를 사용할 수 없음을 나타냅니다(기본값).</span><span class="sxs-lookup"><span data-stu-id="82398-109">**0**, indicating that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures are not available (the default).</span></span>  
  
-   <span data-ttu-id="82398-110">**1**은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 확장 저장 프로시저를 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="82398-110">**1**, indicating that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures are available.</span></span>  
  
 <span data-ttu-id="82398-111">이 설정은 서버를 중지했다가 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="82398-111">The setting takes effect immediately without a server stop and restart.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="82398-112">예제</span><span class="sxs-lookup"><span data-stu-id="82398-112">Examples</span></span>  
 <span data-ttu-id="82398-113">다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 확장 저장 프로시저를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82398-113">The following example enables the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent extended stored procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="82398-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82398-114">See Also</span></span>  
 <span data-ttu-id="82398-115">[관리 태스크 자동화&#40;SQL Server 에이전트&#41;](../../ssms/agent/sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="82398-115">[Automated Administration Tasks &#40;SQL Server Agent&#41;](../../ssms/agent/sql-server-agent.md) </span></span>  
 [<span data-ttu-id="82398-116">SQL Server 에이전트 서비스 시작, 중지 또는 일시 중지</span><span class="sxs-lookup"><span data-stu-id="82398-116">Start, Stop, or Pause the SQL Server Agent Service</span></span>](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
