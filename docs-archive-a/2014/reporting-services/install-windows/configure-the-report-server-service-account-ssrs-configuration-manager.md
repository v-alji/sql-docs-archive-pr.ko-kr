---
title: 보고서 서버 서비스 계정 구성(SSRS 구성 관리자) | Microsoft Docs
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: ''
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: b860a9c916f7dd9c1bdef4f5218845c66239ebe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729119"
---
# <a name="configure-the-report-server-service-account-ssrs-configuration-manager"></a><span data-ttu-id="0af7c-102">보고서 서버 서비스 계정 구성(SSRS 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="0af7c-102">Configure the Report Server Service Account (SSRS Configuration Manager)</span></span>

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="0af7c-103">는 예약된 보고서 처리와 구독 배달에 사용되는 백그라운드 처리 애플리케이션, 보고서 서버 웹 서비스 및 보고서 관리자를 포함하는 단일 서비스로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-103">is implemented as a single service that contains a Report Server Web service, Report Manager, and a background processing application that is used for scheduled report processing and subscription delivery.</span></span> <span data-ttu-id="0af7c-104">이 항목에서는 서비스 계정을 처음 구성하는 방법 Reporting Services 구성 도구를 사용하는 계정이나 암호를 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-104">This topic explains how the service account is initially configured and how to modify the account or password using the Reporting Services Configuration tool.</span></span>  
  
## <a name="initial-configuration"></a><span data-ttu-id="0af7c-105">초기 구성</span><span class="sxs-lookup"><span data-stu-id="0af7c-105">Initial Configuration</span></span>

 <span data-ttu-id="0af7c-106">설치하는 동안 보고서 서버 서비스 계정이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-106">The Report Server service account is defined during Setup.</span></span> <span data-ttu-id="0af7c-107">`NetworkService` 계정과 같은 도메인 사용자 계정이나 기본 제공 계정으로 보고서 서버 서비스를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-107">You can run the service under a domain user account or a built-in such as `NetworkService` account.</span></span> <span data-ttu-id="0af7c-108">기본 계정이 없습니다. 설치 마법사의 [서버 구성-서비스 계정](../../sql-server/install/server-configuration-service-accounts.md) 페이지에서 지정한 계정이 보고서 서버 서비스의 초기 계정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-108">There is no default account; whatever account you specify in the [Server Configuration - Service Accounts](../../sql-server/install/server-configuration-service-accounts.md) page of the Installation Wizard becomes the initial account of the Report Server service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0af7c-109">보고서 서버 웹 서비스 및 보고서 관리자가 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 애플리케이션이더라도 이들은 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 계정에서 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-109">Although the Report Server Web service and Report Manager are [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications, they do not run under the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account.</span></span> <span data-ttu-id="0af7c-110">단일 서비스 아키텍처는 동일한 보고서 서버 프로세스 ID 내에서 두 ASP.NET 애플리케이션을 모두 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-110">The single service architecture runs both ASP.NET applications within the same Report Server process identity.</span></span> <span data-ttu-id="0af7c-111">이것은 이전 버전에서의 중요한 변경 사항으로 보고서 서버 웹 서비스 및 보고서 관리자는 IIS에서 지정된 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 작업자 프로세스 ID에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-111">This is an important change from previous releases, where both the Report Server Web service and Report Manager ran under the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] worker process identity specified in IIS.</span></span>
  
## <a name="changing-the-service-account"></a><span data-ttu-id="0af7c-112">서비스 계정 변경</span><span class="sxs-lookup"><span data-stu-id="0af7c-112">Changing the Service Account</span></span>

 <span data-ttu-id="0af7c-113">서비스 계정 정보를 보고 다시 구성하려면 항상 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-113">To view and reconfigure service account information, always use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="0af7c-114">서비스 ID 정보는 내부적으로 여러 위치에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-114">Service identity information is stored internally in multiple locations.</span></span> <span data-ttu-id="0af7c-115">이 도구를 사용하면 계정 또는 암호를 변경할 때마다 모든 참조가 적절히 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-115">Using the tool ensures that all references are updated accordingly whenever you change the account or password.</span></span> <span data-ttu-id="0af7c-116">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구는 보고서 서버를 사용 가능한 상태로 유지하기 위한 다음과 같은 추가 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-116">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool performs the following additional steps to ensure the report server remains available:</span></span>  
  
- <span data-ttu-id="0af7c-117">로컬 컴퓨터에서 생성된 보고서 서버 그룹에 새 계정을 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-117">Automatically adds the new account to the report server group created on the local computer.</span></span> <span data-ttu-id="0af7c-118">이 그룹은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 파일의 보안을 유지하는 ACL(액세스 제어 목록)에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-118">This group is specified in the access control lists (ACLs) that secure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] files.</span></span>  
  
- <span data-ttu-id="0af7c-119">보고서 서버 데이터베이스 호스팅에 사용되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 대한 로그인 권한을 자동으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-119">Automatically updates the login permissions on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance used to host the report server database.</span></span> <span data-ttu-id="0af7c-120">새 계정이 **RSExecRole**에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-120">The new account will be added to the **RSExecRole**.</span></span>  
  
     <span data-ttu-id="0af7c-121">이전 계정에 대한 데이터베이스 로그인은 자동으로 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-121">The database login for the old account will not be removed automatically.</span></span> <span data-ttu-id="0af7c-122">더 이상 사용하지 않는 계정을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-122">Be sure to remove accounts that are no longer in use.</span></span> <span data-ttu-id="0af7c-123">자세한 내용은 SQL Server 온라인 설명서의 [보고서 서버 데이터베이스 관리&#40;SSRS 기본 모드&#41;](../report-server/report-server-database-ssrs-native-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0af7c-123">For more information, see [Administer a Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) in SQL Server Books Online.</span></span>  
  
     <span data-ttu-id="0af7c-124">처음에 서비스 계정을 사용하도록 보고서 서버 데이터베이스 연결을 구성한 경우에만 데이터베이스 권한이 새 서비스 계정에 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-124">Granting database permissions to new service account only occurs if you configured the report server database connection to use the service account in the first place.</span></span> <span data-ttu-id="0af7c-125">도메인 사용자 계정 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 로그인을 사용하도록 보고서 서버 데이터베이스 연결을 구성한 경우에는 연결 정보는 서비스 계정 업데이트의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-125">If you configured the report server database connection to use a domain user account or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login, the connection information is not affected by the service account update.</span></span>  
  
- <span data-ttu-id="0af7c-126">새 계정의 프로필 정보를 포함하도록 자동으로 암호화 키를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-126">Automatically updates the encryption key to include the profile information of the new account.</span></span>  
  
    > [!NOTE]  
    > <span data-ttu-id="0af7c-127">보고서 서버가 스케일 아웃 배포에 속할 경우 업데이트하는 보고서 서버만 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-127">If the report server is part of the scale-out deployment, only the report server that you are updating is affected.</span></span> <span data-ttu-id="0af7c-128">따라서 배포에 포함된 다른 보고서 서버의 암호화 키는 서비스 계정을 변경해도 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-128">The encryption keys for other report servers in the deployment are unaffected by the service account change.</span></span>  
  
 <span data-ttu-id="0af7c-129">계정을 설정 하는 방법에 대 한 지침은 [서비스 계정 구성 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0af7c-129">For instructions on how to set the account, see [Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).</span></span>  
  
## <a name="choosing-an-account"></a><span data-ttu-id="0af7c-130">계정 선택</span><span class="sxs-lookup"><span data-stu-id="0af7c-130">Choosing an Account</span></span>

 <span data-ttu-id="0af7c-131">다음 계정 유형으로 실행되도록 보고서 서버 서비스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-131">You can configure the Report Server service to run under any of these account types:</span></span>  
  
- <span data-ttu-id="0af7c-132">최소 권한 Windows 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="0af7c-132">Least-privileged Windows user account</span></span>  
  
- <span data-ttu-id="0af7c-133">NetworkService</span><span class="sxs-lookup"><span data-stu-id="0af7c-133">NetworkService</span></span>  
  
- <span data-ttu-id="0af7c-134">LocalSystem</span><span class="sxs-lookup"><span data-stu-id="0af7c-134">LocalSystem</span></span>  
  
- <span data-ttu-id="0af7c-135">LocalService</span><span class="sxs-lookup"><span data-stu-id="0af7c-135">LocalService</span></span>  
  
 <span data-ttu-id="0af7c-136">계정 유형을 선택하는 가장 좋은 방법이 한 가지만 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-136">There is no single best approach for choosing an account type.</span></span> <span data-ttu-id="0af7c-137">계정마다 고려해야 하는 장단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-137">Each account has advantages and disadvantages that you must consider.</span></span> <span data-ttu-id="0af7c-138">프로덕션 서버에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 배포하는 경우에는 악의적인 공격자가 공유 계정을 침해할 경우 광범위한 손상을 방지할 수 있게 도메인 사용자 계정으로 서비스를 실행하도록 구성하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-138">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on a production server, best practices suggest that you configure the service to run under a domain user account so that you can avoid widespread damage if a shared account is compromised by a malicious user.</span></span> <span data-ttu-id="0af7c-139">이렇게 하면 이 계정의 로그온 활동을 감사하기도 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-139">It also makes it easier to audit the logon activity for this account.</span></span> <span data-ttu-id="0af7c-140">Windows 사용자 계정을 사용하는 데 대한 절충안으로 Kerberos 인증을 사용하는 네트워크에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 배포하는 경우에는 이 사용자 계정으로 보고서 서버 서비스를 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-140">A trade-off to using a Windows user account is that if you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a network that uses Kerberos authentication, you must register the service with the user account.</span></span> <span data-ttu-id="0af7c-141">자세한 내용은 [보고서 서버의 SPN&#40;서비스 사용자 이름&#41; 등록](../report-server/register-a-service-principal-name-spn-for-a-report-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0af7c-141">For more information, see [Register a Service Principal Name &#40;SPN&#41; for a Report Server](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).</span></span>  
  
 <span data-ttu-id="0af7c-142">이 섹션의 다음 지침과 링크를 통해 배포에 가장 적합한 방법을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-142">The following guidelines and links in this section can help you decide on an approach that is best for your deployment.</span></span>  
  
- <span data-ttu-id="0af7c-143">[서비스 계정은 SSRS 기본 모드&#41;&#40;](../../sql-server/install/service-account-ssrs-native-mode.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-143">[Service Account &#40;SSRS Native Mode&#41;](../../sql-server/install/service-account-ssrs-native-mode.md).</span></span>  
  
- <span data-ttu-id="0af7c-144">SQL Server 온라인 설명서의[Windows 서비스 계정 및 권한 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)</span><span class="sxs-lookup"><span data-stu-id="0af7c-144">[Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) in SQL Server Books Online.</span></span>  
  
- <span data-ttu-id="0af7c-145">[서비스 및 서비스 계정 보안 계획 가이드](http://usergroup.doubletake.com/file_cabinet/download/0x000021733).</span><span class="sxs-lookup"><span data-stu-id="0af7c-145">[The Services and Service Accounts Security Planning Guide](http://usergroup.doubletake.com/file_cabinet/download/0x000021733).</span></span>  
  
## <a name="updating-an-expired-password"></a><span data-ttu-id="0af7c-146">만료된 암호 업데이트</span><span class="sxs-lookup"><span data-stu-id="0af7c-146">Updating an Expired Password</span></span>

 <span data-ttu-id="0af7c-147">보고서 서버 서비스가 도메인 계정으로 실행되며 Reporting Services 구성 도구를 사용하여 이 서비스를 업데이트할 수 있게 되기 전에 암호가 만료된 경우 새 암호를 지정할 때까지 해당 서비스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-147">If the Report Server service runs under a domain account and the password expires before you can update it in the Reporting Services Configuration tool, the service will not start until you specify a new password.</span></span> <span data-ttu-id="0af7c-148">이 서비스를 시작할 수 없으면 계정을 업데이트하기 위해 해당 서버에 연결하도록 Reporting Services 구성 도구를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-148">If the service cannot be started, you cannot use the Reporting Services Configuration tool to connect to that server to update the account.</span></span> <span data-ttu-id="0af7c-149">이런 경우 여러 가지 도구를 사용하여 서버를 다시 온라인으로 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-149">In this case, you must use a combination of tools to bring the server back online.</span></span>  
  
 <span data-ttu-id="0af7c-150">암호를 다시 설정하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-150">To reset the password, do the following:</span></span>  
  
1. <span data-ttu-id="0af7c-151">**시작** 메뉴에서 **제어판**, **관리 도구**를 차례로 가리킨 다음 **서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-151">On the **Start** menu, point to **Control Panel**, point to **Administrator Tools**, and click **Services**.</span></span>  
  
2. <span data-ttu-id="0af7c-152">**SQL Server Reporting Services**를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-152">Right-click **SQL Server Reporting Services**, select **Properties**.</span></span>  
  
3. <span data-ttu-id="0af7c-153">**로그온**을 클릭하고 새 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-153">Click **Log On**, and type the new password.</span></span>  
  
4. <span data-ttu-id="0af7c-154">암호를 업데이트한 후 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 시작하고 서비스 계정 페이지에서 암호를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-154">After you update the password, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and update the password in the Service Account page.</span></span> <span data-ttu-id="0af7c-155">이 추가 단계는 보고서 서버에서 내부적으로 저장한 계정 정보를 업데이트하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-155">This additional step is necessary to update the account information that is stored internally by the report server.</span></span>  
  
 <span data-ttu-id="0af7c-156">[!INCLUDE[ssDE](../../includes/ssde-md.md)]의 서비스 계정 암호가 만료된 경우에는 보고서 서버에 연결하려고 할 때 `rsReportServerDatabaseUnavailable` 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-156">If the service account password for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] expires, the `rsReportServerDatabaseUnavailable` error occurs when you try to connect to the report server.</span></span> <span data-ttu-id="0af7c-157">이 오류를 해결하려면 암호를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-157">Resetting the password resolves this error.</span></span>  
  
## <a name="configuring-the-report-server-service-for-a-sharepoint-integrated-report-server"></a><span data-ttu-id="0af7c-158">SharePoint 통합 보고서 서버를 위한 보고서 서버 서비스 구성</span><span class="sxs-lookup"><span data-stu-id="0af7c-158">Configuring the Report Server Service for a SharePoint Integrated Report Server</span></span>

 <span data-ttu-id="0af7c-159">SharePoint 통합 모드에서 보고서 서버를 실행 중이며 다음 조건 중 하나가 참인 경우 SharePoint 구성 데이터베이스에 저장된 서비스 계정 정보를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-159">If you are running a report server in SharePoint integrated mode, you must update the service account information that is stored in the SharePoint configuration database if either of the following conditions are true:</span></span>  
  
- <span data-ttu-id="0af7c-160">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 계정이 수정된 경우(예: NetworkService에서 도메인 사용자 계정으로 전환).</span><span class="sxs-lookup"><span data-stu-id="0af7c-160">Modifying the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account (for example, switching from NetworkService to a domain user account).</span></span>  
  
- <span data-ttu-id="0af7c-161">SharePoint 팜이 추가 SharePoint 웹 애플리케이션을 포함하도록 확장된 경우.</span><span class="sxs-lookup"><span data-stu-id="0af7c-161">Extending a SharePoint farm to include an additional SharePoint Web application.</span></span> <span data-ttu-id="0af7c-162">서버 팜이 보고서 서버 통합을 위해 구성되고 새로 추가된 애플리케이션이 팜에 있는 다른 애플리케이션과 다른 사용자 계정에서 실행되도록 구성된 경우 데이터베이스 액세스 정보를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-162">If the server farm is configured for report server integration, and newly added application is configured to run under a different user account than other applications in the farm, you must update the database access information.</span></span>  
  
 <span data-ttu-id="0af7c-163">데이터베이스 액세스 정보를 다시 설정한 다음에는 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 서비스를 다시 시작하여 기존 연결이 더 이상 사용되지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-163">After you reset the database access information, you should then restart the [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] service to ensure that the old connection is no longer used.</span></span>  
  
1. <span data-ttu-id="0af7c-164">**관리 도구**에서 **SharePoint 2010 중앙 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-164">In **Administrative Tools**, click **SharePoint 2010 Central Administration**.</span></span>  
  
2. <span data-ttu-id="0af7c-165">**애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-165">Click **Application Management**.</span></span>  
  
3. <span data-ttu-id="0af7c-166">Reporting Services 섹션에서 **데이터베이스 액세스 권한 부여**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-166">In the Reporting Services section, click **Grant Database Access**.</span></span>  
  
4. <span data-ttu-id="0af7c-167">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-167">Click **OK**.</span></span> <span data-ttu-id="0af7c-168">자격 증명 입력 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-168">The Enter Credentials dialog box appears.</span></span>  
  
5. <span data-ttu-id="0af7c-169">보고서 서버를 호스팅하는 컴퓨터의 로컬 관리자 그룹 멤버인 사용자의 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-169">Enter the credentials of a user who is a member of the Local Administrator's group on the computer that hosts the report server.</span></span> <span data-ttu-id="0af7c-170">자격 증명은 서비스 계정 정보를 조회하기 위해 보고서 서버 컴퓨터에 한 번 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-170">The credentials will be used for a one-time connection to the report server computer for the purpose of retrieving service account information.</span></span> <span data-ttu-id="0af7c-171">각 서비스 계정에 대해 만든 데이터베이스 로그인은 SharePoint 데이터베이스에서 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-171">The database login that is created for each service account will be updated in SharePoint databases.</span></span>  
  
6. <span data-ttu-id="0af7c-172">서비스를 다시 시작하려면 **작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-172">To restart the service, click **Operations**.</span></span>  
  
7. <span data-ttu-id="0af7c-173">토폴로지 및 서비스에서 **서버 제공 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-173">In Topology and Services, click **Services on Server**.</span></span>  
  
8. <span data-ttu-id="0af7c-174">Windows SharePoint Services 웹 애플리케이션의 경우 **중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-174">For Windows SharePoint Services Web Application, click **Stop**.</span></span>  
  
9. <span data-ttu-id="0af7c-175">서비스가 중지될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-175">Wait for the service stop.</span></span>  
  
10. <span data-ttu-id="0af7c-176">**시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-176">Click **Start**.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="0af7c-177">SharePoint 제품 및 기술을 사용하려면 Reporting Services SharePoint 모드 같은 서비스 구성에 사용할 도메인 계정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0af7c-177">SharePoint products and technologies require domain accounts for service configuration like reporting services SharePoint mode.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0af7c-178">다음 단계</span><span class="sxs-lookup"><span data-stu-id="0af7c-178">Next Steps</span></span>

 <span data-ttu-id="0af7c-179">Ssrs [기본 모드 &#40;](../../sql-server/install/service-account-ssrs-native-mode.md) ssrs [Configuration Manager&#41;서비스 계정 &#40;서비스 계정 구성](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)&#41;&#40;[기본 모드](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) Configuration Manager [보고서 서버 url&#41;ssrs Reporting Services 구성 관리자](configure-report-server-urls-ssrs-configuration-manager.md) &#40;</span><span class="sxs-lookup"><span data-stu-id="0af7c-179">[Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) [Service Account &#40;SSRS Native Mode&#41;](../../sql-server/install/service-account-ssrs-native-mode.md) [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)</span></span>
