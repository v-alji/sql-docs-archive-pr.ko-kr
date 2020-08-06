---
title: 자격 증명 변경 마법사 (SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0f2e84ec59f1241a10ce52e597920827f3afbc06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650523"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a><span data-ttu-id="64e67-102">자격 증명 변경 마법사(SSRS 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="64e67-102">Change Credentials Wizard (SSRS Native Mode)</span></span>
  <span data-ttu-id="64e67-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자는 보고서 서버 데이터베이스에 연결할 때 보고서 서버에서 사용하는 계정을 다시 구성하는 단계를 안내하는 자격 증명 변경 마법사를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager provides the Change Credentials Wizard to guide you through the steps of reconfiguring the account that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="64e67-104">자격 증명을 변경할 때 구성 관리자는 보고서 서버에서 현재 사용 중인 보고서 서버 데이터베이스의 데이터베이스 서버에 대한 모든 사용 권한과 데이터베이스 로그인 정보를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-104">When you change credentials, the Configuration Manager will update all permissions and database login information on the database server for the report server database that is actively used by the report server.</span></span>  
  
 <span data-ttu-id="64e67-105">마법사를 시작하려면 **구성 관리자의 데이터베이스 페이지에서** 자격 증명 변경 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-105">To start the wizard, click **Change Credentials** on the Database page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="64e67-106">Configuration Manager를 시작 하는 방법에 대 한 지침은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [Reporting Services 구성 관리자 &#40;기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="64e67-106">For instructions on how to start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="64e67-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
## <a name="options"></a><span data-ttu-id="64e67-108">옵션</span><span class="sxs-lookup"><span data-stu-id="64e67-108">Options</span></span>  
 <span data-ttu-id="64e67-109">**데이터베이스 서버**</span><span class="sxs-lookup"><span data-stu-id="64e67-109">**Database Server**</span></span>  
 <span data-ttu-id="64e67-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 보고서 서버 데이터베이스를 실행 하는 인스턴스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-110">Specifies the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance that runs the report server database.</span></span>  
  
 <span data-ttu-id="64e67-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 연결하려면 서버에 로그온하여 데이터베이스 정보를 업데이트할 권한이 있는 자격 증명을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-111">To connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, you must use credentials that have permission to log on to the server and update database information.</span></span> <span data-ttu-id="64e67-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자는 사용자의 현재 Windows 자격 증명을 사용하지만 사용자에게 로그인 또는 데이터베이스 권한이 없는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 로그인을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-112">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager uses your current Windows credentials, but if you do not have a login or database permissions, you can specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span>  
  
 <span data-ttu-id="64e67-113">다른 Windows 자격 증명은 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-113">You cannot specify different Windows credentials.</span></span> <span data-ttu-id="64e67-114">다른 Windows 사용자로 연결하려면 해당 사용자로 로그인한 다음 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-114">If you want to connect as a different Windows user, login as that user and then start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="64e67-115">**자격 증명**</span><span class="sxs-lookup"><span data-stu-id="64e67-115">**Credentials**</span></span>  
 <span data-ttu-id="64e67-116">보고서 서버가 보고서 서버 데이터베이스에 연결할 때 사용하는 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-116">Specifies the account by which the report server connects to the report server database.</span></span> <span data-ttu-id="64e67-117">유효한 값으로는 보고서 서버 웹 서비스의 서비스 계정, 보고서 서버를 호스팅하는 데 사용 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 정의된 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 데이터베이스 로그인 또는 Windows 계정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-117">Valid values include the service account of the Report Server Web service, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login defined on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance you are using to host the report server, or a Windows account.</span></span> <span data-ttu-id="64e67-118">Windows 계정을 사용 하는 경우 보고서 서버와 데이터베이스가 같은 컴퓨터에 있으면 로컬 계정 (\* \<computername> \\<username \> *)을 지정 하거나, 동일한 도메인의 다른 컴퓨터에 있는 경우 도메인 사용자 계정 (* \<domain> \\<사용자 이름 \> \*)을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-118">If you are using a Windows account, you can specify a local account (*\<computername>\\<username\>*) if the report server and the database are on the same computer, or a domain user account (*\<domain>\\<username\>*) if they are on different computers in the same domain.</span></span>  
  
 <span data-ttu-id="64e67-119">그러면 보고서 서버에서 지정한 계정에 대한 데이터베이스 로그인을 만들고 데이터베이스 권한을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-119">The report server will create a database login and assign database permissions for the account you specify.</span></span>  
  
 <span data-ttu-id="64e67-120">보고서 서버에서 계정 자체를 만들지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-120">The report server does not create the account itself.</span></span> <span data-ttu-id="64e67-121">지정한 계정은 이미 있어야 하며 현재 배포 구성에 대해 유효해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-121">The account you specify must already exist and it must be valid for your deployment configuration.</span></span> <span data-ttu-id="64e67-122">특히 데이터베이스가 원격 컴퓨터에 있는 경우 Windows 계정을 사용하려면 해당 컴퓨터에 대한 로그온 권한이 있는 계정을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-122">Specifically, if the database is on a remote computer and you want to use a Windows account, you must specify an account that has log on permissions on that computer.</span></span>  
  
 <span data-ttu-id="64e67-123">컴퓨터가 다른 도메인이나 트러스트되지 않은 도메인에 있는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 로그인을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-123">If the computer is in a different or non-trusted domain, consider using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span> <span data-ttu-id="64e67-124">계정을 선택 하는 방법에 대 한 자세한 내용은 [보고서 서버 데이터베이스 연결 구성 &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="64e67-124">For more information about choosing an account, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="64e67-125">**요약**</span><span class="sxs-lookup"><span data-stu-id="64e67-125">**Summary**</span></span>  
 <span data-ttu-id="64e67-126">마법사가 실행되기 전에 설정을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-126">Verify the settings before the wizard runs.</span></span>  
  
 <span data-ttu-id="64e67-127">**진행 후 마침**</span><span class="sxs-lookup"><span data-stu-id="64e67-127">**Progress and Finish**</span></span>  
 <span data-ttu-id="64e67-128">각 태스크의 진행률을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="64e67-128">Monitor the progress of each task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e67-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64e67-129">See Also</span></span>  
 <span data-ttu-id="64e67-130">[SSRS 기본 모드&#41;데이터베이스 &#40;](../../../2014/sql-server/install/database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="64e67-130">[Database &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="64e67-131">[SSRS 기본 모드 &#40;데이터베이스 변경 마법사&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="64e67-131">[Change Database Wizard &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="64e67-132">[SSRS Configuration Manager &#40;기본 모드 보고서 서버 데이터베이스를 만듭니다&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span><span class="sxs-lookup"><span data-stu-id="64e67-132">[Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span></span>  
 <span data-ttu-id="64e67-133">[Reporting Services 구성 관리자 F1 도움말 항목 &#40;SSRS 기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="64e67-133">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="64e67-134">보고서 서버 데이터베이스 연결 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="64e67-134">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
