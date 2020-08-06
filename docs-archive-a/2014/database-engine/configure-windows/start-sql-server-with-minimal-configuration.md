---
title: 최소 구성으로 SQL Server 시작 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5c78fc10be584803b438b2cd125a77400ff369b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646629"
---
# <a name="start-sql-server-with-minimal-configuration"></a><span data-ttu-id="47325-102">최소 구성으로 SQL Server 시작</span><span class="sxs-lookup"><span data-stu-id="47325-102">Start SQL Server with Minimal Configuration</span></span>
  <span data-ttu-id="47325-103">서버를 시작할 수 없게 하는 구성 문제가 있는 경우 최소 구성 시작 옵션을 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-103">If you have configuration problems that prevent the server from starting, you can start an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the minimal configuration startup option.</span></span> <span data-ttu-id="47325-104">이 옵션은 시작 옵션 **-f**입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-104">This is the startup option **-f**.</span></span> <span data-ttu-id="47325-105">최소 구성으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 시작하면 자동으로 서버가 단일 사용자 모드로 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-105">Starting an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with minimal configuration automatically puts the server in single-user mode.</span></span>  
  
 <span data-ttu-id="47325-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스를 최소 구성 모드로 시작할 경우 다음에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="47325-106">When you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in minimal configuration mode, note the following:</span></span>  
  
-   <span data-ttu-id="47325-107">한 명의 사용자만 서버에 연결할 수 있고 CHECKPOINT 프로세스는 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-107">Only a single user can connect, and the CHECKPOINT process is not executed.</span></span>  
  
-   <span data-ttu-id="47325-108">원격 액세스와 미리 읽기는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-108">Remote access and read-ahead are disabled.</span></span>  
  
-   <span data-ttu-id="47325-109">시작 저장 프로시저는 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-109">Startup stored procedures do not run.</span></span>  
  
 <span data-ttu-id="47325-110">서버를 최소 구성으로 시작한 후에는 해당 서버 옵션 값을 변경하고 서버를 중지한 다음 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-110">After the server has been started with minimal configuration, you should change the appropriate server option value or values, stop, and then restart the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="47325-111">**sqlcmd** 유틸리티 및 관리자 전용 연결(DAC)을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-111">Use the **sqlcmd** utility and the dedicated administrator connection (DAC) to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="47325-112">일반 연결을 사용하는 경우 최소 구성 모드로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하기 전에 SQL Server 에이전트 서비스를 중단하십시오.</span><span class="sxs-lookup"><span data-stu-id="47325-112">If you use a typical connection, stop the SQL Server Agent service before connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in minimal configuration mode.</span></span> <span data-ttu-id="47325-113">그렇지 않으면 SQL Server 에이전트 서비스가 연결을 사용함으로써 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-113">Otherwise, the SQL Server Agent service uses the connection, thereby blocking it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47325-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-114">See Also</span></span>  
 <span data-ttu-id="47325-115">[SQL Server 에이전트 서비스 시작, 중지 또는 일시 중지](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span><span class="sxs-lookup"><span data-stu-id="47325-115">[Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md) </span></span>  
 <span data-ttu-id="47325-116">[데이터베이스 관리자를 위한 진단 연결](diagnostic-connection-for-database-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="47325-116">[Diagnostic Connection for Database Administrators](diagnostic-connection-for-database-administrators.md) </span></span>  
 <span data-ttu-id="47325-117">[sqlcmd 유틸리티](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="47325-117">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="47325-118">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="47325-118">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="47325-119">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="47325-119">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="47325-120">데이터베이스 엔진 서비스 시작 옵션</span><span class="sxs-lookup"><span data-stu-id="47325-120">Database Engine Service Startup Options</span></span>](database-engine-service-startup-options.md)  
  
  
