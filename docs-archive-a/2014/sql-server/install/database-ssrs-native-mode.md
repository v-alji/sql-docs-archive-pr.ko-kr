---
title: 데이터베이스 (SSRS 기본 모드) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bb8f1841e980279d6051e3393efdf06df238f41f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660887"
---
# <a name="database-ssrs-native-mode"></a><span data-ttu-id="43b44-102">데이터베이스(SSRS 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="43b44-102">Database (SSRS Native Mode)</span></span>
  <span data-ttu-id="43b44-103">데이터베이스 페이지에서는 하나 이상의 보고서 서버 인스턴스에 내부 스토리지를 제공하는 보고서 서버 데이터베이스를 만들어 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-103">Use the Database page to create and configure the report server databases that provide internal storage for one or more report server instances.</span></span> <span data-ttu-id="43b44-104">원격 보고서 서버 데이터베이스를 사용하도록 보고서 서버를 구성하는 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 사용하여 데이터베이스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-104">If you are configuring a report server to use a remote report server database, you must use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to create the database.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="43b44-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="43b44-106">보고서 서버 데이터베이스를 만들고 연결을 구성하려면 여러 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-106">Creating a report server database and configuring the connection is a multi-step process.</span></span> <span data-ttu-id="43b44-107">이 페이지에서는 각 유형의 태스크에 대한 단계를 안내하는 마법사를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-107">To guide you through the steps, this page provides Wizards for each type of task.</span></span> <span data-ttu-id="43b44-108">사용 권한과 로그인은 자동으로 생성되거나 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-108">Permissions and logins are created or updated for you.</span></span> <span data-ttu-id="43b44-109">각 단계의 상태는 진행률 페이지에서 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-109">You can monitor the status of each step in the Progress page.</span></span> <span data-ttu-id="43b44-110">오류가 발생할 경우 오류를 클릭하면 해결 방법을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-110">If an error occurs, you can click the error for information on how to resolve it.</span></span>  
  
 <span data-ttu-id="43b44-111">보고서 서버 데이터베이스는 특정 서버 모드를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-111">A report server database must support a specific server mode.</span></span> <span data-ttu-id="43b44-112">기본 모드는 기본 모드이지만 SharePoint 제품 또는 기술에 대한 대규모 배포에서 보고서 서버를 실행하는 경우에는 SharePoint 통합 모드용으로 보고서 서버 데이터베이스를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-112">The default mode is native mode, but you can also create a report server database for SharePoint integrated mode if you are running a report server in a larger deployment of a SharePoint product or technology.</span></span> <span data-ttu-id="43b44-113">자세한 내용은 [기본 모드 보고서 서버 데이터베이스 만들기&#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43b44-113">For more information, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).</span></span>  
  
 <span data-ttu-id="43b44-114">이 페이지를 열려면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 관리자를 시작하고 탐색 창에서 **데이터베이스** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-114">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and click **Database** in the navigation pane.</span></span> <span data-ttu-id="43b44-115">자세한 내용은 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43b44-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="43b44-116">옵션</span><span class="sxs-lookup"><span data-stu-id="43b44-116">Options</span></span>  
 <span data-ttu-id="43b44-117">**SQL Server 이름**</span><span class="sxs-lookup"><span data-stu-id="43b44-117">**SQL Server Name**</span></span>  
 <span data-ttu-id="43b44-118">현재 보고서 서버 데이터베이스에서 **SQL Server 이름** 은 보고서 서버 데이터베이스를 실행하는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-118">In Current Report Server Database, **SQL Server Name** specifies the name of the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] that runs the report server database.</span></span> <span data-ttu-id="43b44-119">로컬 컴퓨터나 원격 컴퓨터에서 기본 또는 명명된 인스턴스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-119">You can use a default or named instance on a local or remote computer.</span></span>  
  
 <span data-ttu-id="43b44-120">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="43b44-120">**Database Name**</span></span>  
 <span data-ttu-id="43b44-121">서버 데이터를 저장하는 보고서 서버 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-121">Specifies the name of the report server database that stores server data.</span></span>  
  
 <span data-ttu-id="43b44-122">**보고서 서버 모드**</span><span class="sxs-lookup"><span data-stu-id="43b44-122">**Report Server Mode**</span></span>  
 <span data-ttu-id="43b44-123">보고서 서버 데이터베이스가 기본 모드를 지원하는지, 아니면 SharePoint 통합 모드를 지원하는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-123">Indicates whether the report server database supports native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="43b44-124">자세한 내용은 [Reporting Services Report Server](../../../2014/reporting-services/reporting-services-report-server.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="43b44-124">For more information, see [Reporting Services Report Server](../../../2014/reporting-services/reporting-services-report-server.md).</span></span>  
  
 <span data-ttu-id="43b44-125">**데이터베이스 변경**</span><span class="sxs-lookup"><span data-stu-id="43b44-125">**Change Database**</span></span>  
 <span data-ttu-id="43b44-126">보고서 서버 데이터베이스를 만들거나 선택하는 데 필요한 모든 단계를 안내하는 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-126">Start a wizard that guides you through all of the steps required for creating or selecting a report server database.</span></span>  
  
 <span data-ttu-id="43b44-127">**자격 증명 유형**</span><span class="sxs-lookup"><span data-stu-id="43b44-127">**Credential Type**</span></span>  
 <span data-ttu-id="43b44-128">보고서 서버에서 보고서 서버 데이터베이스에 연결할 때 사용하는 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-128">Specifies credentials that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="43b44-129">지정할 수 있는 자격 증명 유형은 서비스 계정, Windows 도메인 사용자, Windows 로컬 사용자 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 로그인입니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-129">Credential types you can specify include the service account, a Windows domain user, Windows local user, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login.</span></span> <span data-ttu-id="43b44-130">자격 증명을 선택 하는 방법에 대 한 자세한 내용은 [보고서 서버 데이터베이스 연결 구성 &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="43b44-130">For more information about selecting credentials, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="43b44-131">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="43b44-131">**User Name**</span></span>  
 <span data-ttu-id="43b44-132">Windows 자격 증명을 사용하는 경우 도메인 사용자 계정을 지정하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 자격 증명을 사용하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-132">Specifies a domain user account if you are using Windows credentials, or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login if you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credentials.</span></span> <span data-ttu-id="43b44-133">Windows 자격 증명을 사용 하는 경우 \* \<domain> \\<계정 \> \*형식으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-133">If you are using Windows credentials, specify them in this format: *\<domain>\\<account\>*.</span></span>  
  
 <span data-ttu-id="43b44-134">**암호**</span><span class="sxs-lookup"><span data-stu-id="43b44-134">**Password**</span></span>  
 <span data-ttu-id="43b44-135">계정의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-135">Specifies the password for the account.</span></span>  
  
 <span data-ttu-id="43b44-136">**자격 증명 변경**</span><span class="sxs-lookup"><span data-stu-id="43b44-136">**Change Credentials**</span></span>  
 <span data-ttu-id="43b44-137">다른 계정을 선택하거나 보고서 서버 데이터베이스에 연결하는 데 사용되는 계정에 대한 암호를 업데이트하는 데 필요한 모든 단계를 안내하는 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b44-137">Start a wizard that guides you through all of the steps required for selecting a different account or updating the password on the account that is used to connect to the report server database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b44-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="43b44-138">See Also</span></span>  
 <span data-ttu-id="43b44-139">[SSRS Configuration Manager &#40;기본 모드 보고서 서버 데이터베이스를 만듭니다&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span><span class="sxs-lookup"><span data-stu-id="43b44-139">[Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md) </span></span>  
 <span data-ttu-id="43b44-140">[Reporting Services 구성 관리자 F1 도움말 항목 &#40;SSRS 기본 모드&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="43b44-140">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="43b44-141">[SSRS 기본 모드의 보고서 서버 데이터베이스 &#40;&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="43b44-141">[Report Server Database &#40;SSRS Native Mode&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="43b44-142">보고서 서버 데이터베이스 연결 구성&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="43b44-142">Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;</span></span>](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
