---
title: SharePoint용 PowerPivot 2013에 대 한 최소 권한 구성의 예 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1e09e6c-52d3-48ab-8c70-818d5d775087
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0188f314e4c354b33d03e6e7948aed1ba4cf8be2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729916"
---
# <a name="example-of-a-minimum-privilege-configuration-for-powerpivot-for-sharepoint-2013"></a><span data-ttu-id="4d1e3-102">SharePoint 2013용 PowerPivot의 최소 권한 구성 예</span><span class="sxs-lookup"><span data-stu-id="4d1e3-102">Example of a Minimum-Privilege Configuration for PowerPivot for SharePoint 2013</span></span>
  <span data-ttu-id="4d1e3-103">이 항목은 최소 권한을 사용한 SharePoint 2013용 PowerPivot 구성 예에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-103">This topic describes an example PowerPivot for SharePoint 2013 configuration with minimum privileges.</span></span> <span data-ttu-id="4d1e3-104">이 구성은 세 가지 구성 요소 각각에 대해 다른 계정을 사용하며 계정마다 취소 수준의 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-104">The configuration utilizes a different account for each of the three components and each account has the minimum level of privileges.</span></span>  
  
## <a name="summary-of-accounts"></a><span data-ttu-id="4d1e3-105">계정 요약</span><span class="sxs-lookup"><span data-stu-id="4d1e3-105">Summary of Accounts</span></span>  
 <span data-ttu-id="4d1e3-106">SharePoint 2013용 PowerPivot은 Analysis Services 서비스 계정에 네트워크 서비스 계정 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-106">PowerPivot for SharePoint 2013 supports the use of the Network Service account for the Analysis Services service account.</span></span> <span data-ttu-id="4d1e3-107">네트워크 서비스 계정은 SharePoint 2010에서 지원하는 시나리오가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-107">The Network Service account is not a supported scenario with SharePoint 2010.</span></span> <span data-ttu-id="4d1e3-108">서비스 계정에 대 한 자세한 내용은 [Windows 서비스 계정 및 권한 구성](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) (을 참조 https://msdn.microsoft.com/library/ms143504.aspx) 하세요.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-108">For more information on Service accounts, see [Configure Windows Service Accounts and Permissions](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) (https://msdn.microsoft.com/library/ms143504.aspx).</span></span>  
  
 <span data-ttu-id="4d1e3-109">다음 표에는 최소 권한 구성에 대한 이 예에서 사용된 세 계정이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-109">The following table summarizes the three accounts used in this example of a minimum privileged configuration.</span></span>  
  
|<span data-ttu-id="4d1e3-110">Scope</span><span class="sxs-lookup"><span data-stu-id="4d1e3-110">Scope</span></span>|<span data-ttu-id="4d1e3-111">Name</span><span class="sxs-lookup"><span data-stu-id="4d1e3-111">Name</span></span>|  
|-----------|----------|  
|<span data-ttu-id="4d1e3-112">SharePoint 관리자 계정</span><span class="sxs-lookup"><span data-stu-id="4d1e3-112">SharePoint Administrator account</span></span>|<span data-ttu-id="4d1e3-113">**SPAdmin**</span><span class="sxs-lookup"><span data-stu-id="4d1e3-113">**SPAdmin**</span></span>|  
|<span data-ttu-id="4d1e3-114">SharePoint 팜 계정</span><span class="sxs-lookup"><span data-stu-id="4d1e3-114">SharePoint Farm account</span></span>|<span data-ttu-id="4d1e3-115">**SPFarm**</span><span class="sxs-lookup"><span data-stu-id="4d1e3-115">**SPFarm**</span></span>|  
|<span data-ttu-id="4d1e3-116">Analysis Services 서비스 계정</span><span class="sxs-lookup"><span data-stu-id="4d1e3-116">Analysis Services service account</span></span>|<span data-ttu-id="4d1e3-117">**SPsvc**</span><span class="sxs-lookup"><span data-stu-id="4d1e3-117">**SPsvc**</span></span>|  
  
### <a name="the-sharepoint-administrator-account-spadmin"></a><span data-ttu-id="4d1e3-118">SharePoint 관리자 계정(SpAdmin)</span><span class="sxs-lookup"><span data-stu-id="4d1e3-118">The SharePoint Administrator account (SpAdmin)</span></span>  
 <span data-ttu-id="4d1e3-119">**SPAdmin** 은 팜을 설치하고 구성하는 데 사용하는 도메인 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-119">**SPAdmin** is a domain account you use to install and configure the farm.</span></span> <span data-ttu-id="4d1e3-120">SharePoint 구성 마법사 및 SharePoint 2013용 PowerPivot 구성 도구를 실행하는 데 사용되는 계정입니다. **SPAdmin** 계정은 로컬 관리자 권한이 필요한 유일한 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-120">It is the account used to run the SharePoint Configuration Wizard and the PowerPivot Configuration Tool for SharePoint 2013.The **SPAdmin** account is the only account that requires local Administrator rights.</span></span> <span data-ttu-id="4d1e3-121">PowerPivot 구성 도구를 실행하기 전에 SharePoint에서 콘텐츠와 구성 데이터베이스를 만든 SQL Server 데이터베이스 인스턴스에 **SPAdmin** 계정 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-121">Before running the PowerPivot Configuration tool, grant the **SPAdmin** account privileges to the SQL Server database instance where SharePoint creates content and configuration databases.</span></span> <span data-ttu-id="4d1e3-122">최소 권한 시나리오에서 SPAdmin 계정을 구성하려면 해당 계정이 **securityadmin** 및 **dbcreator**역할의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-122">To configure the SPAdmin account in a minimum privilege scenario, it should be a member of the roles **securityadmin** and **dbcreator**.</span></span>  
  
### <a name="the-farm-account-spfarm"></a><span data-ttu-id="4d1e3-123">팜 계정(SPFarm)</span><span class="sxs-lookup"><span data-stu-id="4d1e3-123">The Farm account (SPFarm)</span></span>  
 <span data-ttu-id="4d1e3-124">**SPFarm** 은 SharePoint Timer Service 및 중앙 관리용 웹 애플리케이션에서 SharePoint 콘텐츠 데이터베이스에 액세스할 때 사용하는 도메인 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-124">**SPFarm** is a domain account that the SharePoint Timer service and the web application for Central Administration use to access the SharePoint content database.</span></span> <span data-ttu-id="4d1e3-125">이 계정은 로컬 관리자가 아니어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-125">This account does not need to be a local administrator.</span></span> <span data-ttu-id="4d1e3-126">SharePoint 구성 마법사는 백 엔드 SQL Server 데이터베이스에 적절한 최소 권한을 부여합니다. 최소 SQL Server 권한 구성은 **securityadmin** 및 **dbcreator**역할의 멤버 자격입니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-126">The SharePoint configuration wizard grants the proper minimal privilege in the back-end SQL Server database.The minimum SQL Server privilege configuration is membership in the roles **securityadmin** and **dbcreator**.</span></span>  
  
### <a name="the-service-account-for-powerpivot-service-spsvc"></a><span data-ttu-id="4d1e3-127">PowerPivot 서비스(SPsvc)에 대한 서비스 계정</span><span class="sxs-lookup"><span data-stu-id="4d1e3-127">The Service Account for PowerPivot Service (SPsvc)</span></span>  
 <span data-ttu-id="4d1e3-128">PowerPivot 구성 도구를 실행하기 전에 새 SharePoint 팜이 구성되지 않은 경우에는 기본적으로 PowerPivot 구성 도구에 의해 다음 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-128">If a new SharePoint farm is not configured before you run the PowerPivot Configuration tool, then by default the PowerPivot Configuration tool will create the following:</span></span>  
  
-   <span data-ttu-id="4d1e3-129">PowerPivot 서비스 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="4d1e3-129">PowerPivot Service application.</span></span>  
  
-   <span data-ttu-id="4d1e3-130">Excel Services 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="4d1e3-130">Excel Services application.</span></span>  
  
-   <span data-ttu-id="4d1e3-131">보안 저장소 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="4d1e3-131">Secure Store application.</span></span>  
  
 <span data-ttu-id="4d1e3-132">PowerPivot 구성 도구는 기본 애플리케이션 풀에서 모두 세 개의 서비스 애플리케이션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-132">The PowerPivot configuration tool configures all three of the service applications in the default application pool.</span></span> <span data-ttu-id="4d1e3-133">해당 애플리케이션 풀은 일반적으로 SPFarm 계정으로 실행되도록 구성됩니다. 이 계정은 서비스 계정에 필요 없는 많은 리소스에 액세스할 수 있습니다. 최소 권한이 지정된 환경을 만들려면 해당 애플리케이션 풀 및 웹 애플리케이션에서 사용할 새 도메인 계정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-133">That application pool is typically configured to run as the SPFarm account, which has access to many resources that a service account does not require.To make the environment a minimum-privileged environment, configure a new domain account to be use by the appropriate application pool and web application.</span></span>  
  
 <span data-ttu-id="4d1e3-134">**SharePoint 서비스 계정으로 사용할 새 도메인 계정을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="4d1e3-134">**To create a new domain account SPsvc to be used as a SharePoint Service account:**</span></span>  
  
1.  <span data-ttu-id="4d1e3-135">SharePoint 중앙 관리에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-135">In SharePoint Central Administration, click **Security**.</span></span>  
  
2.  <span data-ttu-id="4d1e3-136">**서비스 계정 구성** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-136">Click **Configure Service Accounts**</span></span>  
  
3.  <span data-ttu-id="4d1e3-137">**새 관리되는 계정을 등록하십시오.** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-137">Click **Register new managed account**.</span></span>  
  
 <span data-ttu-id="4d1e3-138">**SPSvc** 계정에 로컬 관리자 권한이 없으며, Spsvc에는 SharePoint 데이터베이스에 대한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-138">The **SPSvc** account has no local administrator privileges and SPsvc will not have any privileges in the SharePoint database.</span></span> <span data-ttu-id="4d1e3-139">SPsvc에 필요한 유일한 권한은 Analysis Services의 PowerPivot 인스턴스에 대한 관리 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-139">The only privileges SPsvc requires is administrative rights to the PowerPivot Instance of the Analysis Services.</span></span>  
  
 <span data-ttu-id="4d1e3-140">**SPsvc 계정을 사용할 적절한 애플리케이션 풀을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="4d1e3-140">**To configure the appropriate application pool to use the SPsvc account :**</span></span>  
  
1.  <span data-ttu-id="4d1e3-141">SharePoint 중앙 관리에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-141">In SharePoint Central Administration, click **Security**.</span></span>  
  
2.  <span data-ttu-id="4d1e3-142">**서비스 계정 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-142">Click **Configure Service Accounts**.</span></span>  
  
3.  <span data-ttu-id="4d1e3-143">PowerPivot 서비스 애플리케이션에서 사용한 서비스 애플리케이션 풀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-143">Select the service application pool used by the PowerPivot Service application.</span></span> <span data-ttu-id="4d1e3-144">SPSvc 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-144">Then select the SPSvc account.</span></span>  
  
 <span data-ttu-id="4d1e3-145">**PowerShell로 웹 애플리케이션에 대한 액세스 권한을 부여하려면**</span><span class="sxs-lookup"><span data-stu-id="4d1e3-145">**To Grant access to the web application with PowerShell:**</span></span>  
  
1.  <span data-ttu-id="4d1e3-146">관리자 권한으로 SharePoint 2013 관리 셸을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-146">Run the SharePoint 2013 Management Shell with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="4d1e3-147">다음 PowerShell 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d1e3-147">Run the following PowerShell code:</span></span>  
  
    ```powershell
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")
    ```  
