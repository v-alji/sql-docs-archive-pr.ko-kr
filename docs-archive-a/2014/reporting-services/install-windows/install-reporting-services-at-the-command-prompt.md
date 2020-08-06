---
title: Reporting Services SharePoint 모드 및 기본 모드의 명령 프롬프트 설치 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 048169b3-512c-41e4-895a-0416eff41268
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b2101c40c5136e89d4e30d9551187a2b63672da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728064"
---
# <a name="command-prompt-installation-of-reporting-services-sharepoint-mode-and-native-mode"></a><span data-ttu-id="be83e-102">Reporting Services SharePoint 모드 및 기본 모드의 명령 프롬프트 설치</span><span class="sxs-lookup"><span data-stu-id="be83e-102">Command Prompt Installation of Reporting Services SharePoint Mode and Native Mode</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="be83e-103">는 SQL Server 설치 프로그램에서 명령줄 설치를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-103">supports a command-line installation from the SQL Server setup program.</span></span> <span data-ttu-id="be83e-104">이 항목에는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]와 관련된 몇 가지 명령줄 설치 예가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-104">This topic contains several examples of command-line installations that are specific to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="be83e-105">모든 SQL Server 구성 요소에 사용할 수 있는 명령줄 옵션에 대 한 자세한 설명은 [명령 프롬프트에서 SQL Server 2014 설치](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="be83e-105">For a complete description of the command-line options available for all SQL Server components, see [Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span> <span data-ttu-id="be83e-106">이 항목에서는 SharePoint 제품용 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능에 대한 명령줄 옵션은 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-106">This topic does not describe command-line options for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span> <span data-ttu-id="be83e-107">추가 기능 명령 설치에 자세한 내용은 [rsSharePoint.msi 설치 파일을 사용하여 추가 기능 설치](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be83e-107">For information on command installation of the add-in, see [Install the add-in using the installation file rsSharePoint.msi](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint).</span></span>  
  
 <span data-ttu-id="be83e-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 모드 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]기본 모드</span><span class="sxs-lookup"><span data-stu-id="be83e-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>  
  
## <a name="rsinstallmode-native-mode"></a><span data-ttu-id="be83e-109">RSINSTALLMODE(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="be83e-109">RSINSTALLMODE (Native Mode)</span></span>  
 <span data-ttu-id="be83e-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치를 위한 기본 입력 설정은 **/RSINSTALLMODE** 입력 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-110">The primary input setting for installing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is the **/RSINSTALLMODE** input setting.</span></span> <span data-ttu-id="be83e-111">설정에는 **DefaultNativeMode** 와 **FilesOnlyMode**의 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-111">The setting has two options: **DefaultNativeMode** and **FilesOnlyMode**</span></span>  
  
 <span data-ttu-id="be83e-112">설치에 SQL Server 데이터베이스 엔진이 있는 경우 RSINSTALLMODE 기본값은 DefaultNativeMode입니다. 설치에 SQL Server 데이터베이스 엔진이 없는 경우 RSINSTALLMODE 기본값은 FilesOnlyMode입니다. DefaultNativeMode를 선택했지만 설치에 SQL Server 데이터베이스 엔진이 없는 경우 설치가 RSINSTALLMODE를 FilesOnlyMode로 자동으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-112">If the installation includes the SQL Server Database engine, the default RSINSTALLMODE is DefaultNativeMode.If the installation does not include the SQL Server Database engine, the default RSINSTALLMODE is FilesOnlyMode.If you choose DefaultNativeMode but the installation does not include the SQL Server Database engine, the installation automatically changes the RSINSTALLMODE to FilesOnlyMode.</span></span> <span data-ttu-id="be83e-113">입력 설정에 대 한 자세한 내용은 [명령 프롬프트에서 SQL Server 2014 설치](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="be83e-113">For more information on the input settings, see [Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
## <a name="rsshpinstallmode-sharepoint-mode"></a><span data-ttu-id="be83e-114">RSSHPINSTALLMODE(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="be83e-114">RSSHPINSTALLMODE (SharePoint Mode)</span></span>  
 <span data-ttu-id="be83e-115">SharePoint 모드로 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 설치하기 위한 입력 설정은 **/RSSHPINSTALLMODE**입니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-115">The input setting to install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode is **/RSSHPINSTALLMODE**.</span></span> <span data-ttu-id="be83e-116">입력 설정에는 SharePointFilesOnlyMode라는 한 옵션만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-116">The input setting has one option: SharePointFilesOnlyMode.</span></span> <span data-ttu-id="be83e-117">이 옵션은 SharePoint 모드에 필요한 모든 파일을 설치하지만 설치 후 구성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-117">The option installs all the files needed for SharePoint mode but, configuration is required following installation.</span></span> <span data-ttu-id="be83e-118">SharePoint 중앙 관리를 사용하여 이 추가 구성 단계가 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-118">The additional configuration steps are completed using SharePoint Central Administration.</span></span> <span data-ttu-id="be83e-119">자세한 내용은 [sharepoint 2010에 대 한 Sharepoint 모드 설치 Reporting Services](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="be83e-119">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>  
  
## <a name="examples-of-sharepoint-mode-installation"></a><span data-ttu-id="be83e-120">SharePoint 모드 설치 예</span><span class="sxs-lookup"><span data-stu-id="be83e-120">Examples of SharePoint Mode Installation</span></span>  
 <span data-ttu-id="be83e-121">다음 예에서는 SharePoint 모드로 SQL Server 데이터베이스 엔진 서비스 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 와 SharePoint용 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능(RS_SHPWFE)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-121">The following example installs SQL Server the database engine service and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode as well as the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint (RS_SHPWFE).</span></span>  
  
```  
setup /q /ACTION=install /FEATURES=SQL, RS_SHP, RS_SHPWFE,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE"  
```  
  
 <span data-ttu-id="be83e-122">다음 예에서는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드만 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-122">The following example installs only [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /IACCEPTSQLSERVERLICENSETERMS /FEATURES="RS_SHP" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SECURITYMODE="SQL" /SAPWD="*****" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Name]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="[Account Name]" /UPDATEENABLED="False"  
  
```  
  
 <span data-ttu-id="be83e-123">다음 예에서는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드 및 SharePoint 모드 둘 다를 포함하여 모든 SQL Server 기능을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-123">The following example installs all of the SQL Server features, including both [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode and SharePoint mode.</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT, RS_SHP,RS_SHPWFE,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSSHPINSTALLMODE="SharePointFilesOnlyMode" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="examples-of-sharepoint-mode-upgrade"></a><span data-ttu-id="be83e-124">SharePoint 모드 업그레이드 예</span><span class="sxs-lookup"><span data-stu-id="be83e-124">Examples of SharePoint Mode Upgrade</span></span>  
 <span data-ttu-id="be83e-125">다음 예에서는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-125">The following example upgrades [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="be83e-126">**RSUPGRADEPASSWORD** 는 기존 Report Server 서비스 계정의 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-126">**RSUPGRADEPASSWORD** is the password of the existing Report Server service account.</span></span> <span data-ttu-id="be83e-127">RSUPGRADEPASSWORD는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 계정이 기본 제공 계정이 아닌 한 업그레이드 시나리오에서 필수 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-127">RSUPGRADEPASSWORD is a required field in an upgrade scenario unless the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account is a built-in account.</span></span>  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[PID value]" /FTSVCACCOUNT="[DOMAIN\ACCOUNT]" /FTSVCPASSWORD="[ACCOUNTPASSSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSUPGRADEPASSWORD="******"  
```  
  
 <span data-ttu-id="be83e-128">다음 예를 사용하면 SharePoint 공유 서비스 아키텍처를 기반으로 하는 SharePoint 모드 설치를 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-128">The following example can be used to upgrade a SharePoint Mode installation that is based on the SharePoint shared service architecture.</span></span> <span data-ttu-id="be83e-129">이 예에는 ALLOWUPGRADEFORSSRSSHAREPOINTMODE 스위치가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-129">The example uses switch ALLOWUPGRADEFORSSRSSHAREPOINTMODE.</span></span> <span data-ttu-id="be83e-130">공유 서비스 아키텍처를 기반으로 하지 않는 이전 버전을 업그레이드할 때는 이 스위치가 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be83e-130">The switch is not needed for upgrading older versions that are not based on the shared service architecture:</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[Your PID Value]" /FTSVCACCOUNT="[ACCOUNT Name]" /FTSVCPASSWORD="****" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /ALLOWUPGRADEFORSSRSSHAREPOINTMODE="True"  
```  
  
## <a name="examples-of-native-mode-installation"></a><span data-ttu-id="be83e-131">기본 모드 설치 예</span><span class="sxs-lookup"><span data-stu-id="be83e-131">Examples of Native Mode Installation</span></span>  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="see-also"></a><span data-ttu-id="be83e-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="be83e-132">See Also</span></span>  
 <span data-ttu-id="be83e-133">[명령 프롬프트에서 SQL Server 2014 설치](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="be83e-133">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span></span>  
 <span data-ttu-id="be83e-134">[SysPrep 매개 변수](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep) </span><span class="sxs-lookup"><span data-stu-id="be83e-134">[SysPrep Parameters](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep) </span></span>  
 [<span data-ttu-id="be83e-135">명령 프롬프트에서 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="be83e-135">Install PowerPivot from the Command Prompt</span></span>](../../sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
  
