---
title: 서비스 관리를 위한 보안 요구 사항 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent service, security
- services [SQL Server], security
- SQL Server services, security
- WMI Providers [SQL Server]
- server configuration [SQL Server]
- security [SQL Server], services
- services [SQL Server], WMI
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46a777858c01bf3057093d34b29b9a2093668e97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738751"
---
# <a name="security-requirements-for-managing-services"></a><span data-ttu-id="bdac1-102">서비스 관리를 위한 보안 요구 사항</span><span class="sxs-lookup"><span data-stu-id="bdac1-102">Security Requirements for Managing Services</span></span>
  <span data-ttu-id="bdac1-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 관리하려면 SQL Server 구성 관리자 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bdac1-103">To manage the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Services, use either SQL Server Configuration Manager or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="bdac1-104">클러스터 관리자를 사용하여 클러스터형 서버에서 서비스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="bdac1-104">Manage the services on clustered servers with the Cluster Administrator.</span></span>  
  
 <span data-ttu-id="bdac1-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 관리하고 서버 구성 옵션을 설정하려면 **serveradmin** 고정 서버 역할이나 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdac1-105">To manage the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service and set the server configuration options, you must be a member of the **serveradmin** fixed server role or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="bdac1-106">Windows **Administrators** 그룹의 멤버는 서비스를 시작하거나 중지하고 Windows에서 제공하는 서버 옵션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdac1-106">Members of the Windows **Administrators** group can start and stop services and configure the server options that Windows provides.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdac1-107">정상적으로 작동하려면 서비스에 사용되는 계정은 올바른 도메인, 파일 시스템 및 레지스트리 권한으로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdac1-107">To operate properly, the accounts used for the services must be configured with the correct domain, file system, and registry permissions.</span></span> <span data-ttu-id="bdac1-108">필요한 사용 권한에 대한 자세한 내용은 [Windows 서비스 계정 및 권한 구성](configure-windows-service-accounts-and-permissions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bdac1-108">For information about the required permissions, see [Configure Windows Service Accounts and Permissions](configure-windows-service-accounts-and-permissions.md).</span></span>  
  
## <a name="windows-management-instrumentation"></a><span data-ttu-id="bdac1-109">Windows Management Instrumentation</span><span class="sxs-lookup"><span data-stu-id="bdac1-109">Windows Management Instrumentation</span></span>  
 <span data-ttu-id="bdac1-110">SQL Server 구성 관리자와 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 WMI(Windows Management Instrumentation)를 사용하여 일부 서버 속성을 표시하고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="bdac1-110">SQL Server Configuration Manager and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] use Windows Management Instrumentation (WMI) to display and modify some of the server properties.</span></span> <span data-ttu-id="bdac1-111">서비스를 관리하고 서비스 상태를 파악하려면 WMI 개체에 액세스할 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bdac1-111">To manage services and obtain the status of the services, the user must have rights to access the WMI object.</span></span> <span data-ttu-id="bdac1-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 다음 서버 속성 페이지에 WMI를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bdac1-112">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], the following server property pages use WMI:</span></span>  
  
-   <span data-ttu-id="bdac1-113">자동 시작 서비스</span><span class="sxs-lookup"><span data-stu-id="bdac1-113">Autostart Services</span></span>  
  
-   <span data-ttu-id="bdac1-114">시작 매개 변수</span><span class="sxs-lookup"><span data-stu-id="bdac1-114">Startup Parameters</span></span>  
  
-   <span data-ttu-id="bdac1-115">보안</span><span class="sxs-lookup"><span data-stu-id="bdac1-115">Security</span></span>  
  
-   <span data-ttu-id="bdac1-116">기타 서버 설정</span><span class="sxs-lookup"><span data-stu-id="bdac1-116">Misc Server Settings</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="bdac1-117">관련 작업</span><span class="sxs-lookup"><span data-stu-id="bdac1-117">Related Tasks</span></span>  
 [<span data-ttu-id="bdac1-118">WMI를 구성하여 SQL Server 도구에 서버 상태 표시</span><span class="sxs-lookup"><span data-stu-id="bdac1-118">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## <a name="related-content"></a><span data-ttu-id="bdac1-119">관련 내용</span><span class="sxs-lookup"><span data-stu-id="bdac1-119">Related Content</span></span>  
 [<span data-ttu-id="bdac1-120">구성 관리용 WMI 공급자 개념</span><span class="sxs-lookup"><span data-stu-id="bdac1-120">WMI Provider for Configuration Management Concepts</span></span>](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
