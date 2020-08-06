---
title: 보고서 서버에서 사용자 지정 확장 프로그램이 검색 됨 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- rendering extensions [Reporting Services], custom extensions
- security extensions [Reporting Services]
- custom extensions [Reporting Services]
- data processing extensions [Reporting Services], custom extensions
- delivery extensions [Reporting Services]
ms.assetid: fa184bd7-11d6-4ea3-9249-bc1b13db49e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e4be596ff0f110515155f2aa14dc00aceaf85efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648767"
---
# <a name="custom-extensions-were-detected-on-the-report-server-upgrade-advisor"></a><span data-ttu-id="5e54f-102">보고서 서버에서 사용자 지정 확장 프로그램이 검색됨(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="5e54f-102">Custom extensions were detected on the report server (Upgrade Advisor)</span></span>
  <span data-ttu-id="5e54f-103">업그레이드 관리자가 구성 파일에서 사용자 지정 확장 프로그램 설정을 검색했으며, 이는 데이터 처리, 배달, 렌더링, 보안 또는 인증을 위한 하나 이상의 사용자 지정 확장이 사용자 설치에 포함되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-103">Upgrade Advisor detected custom extension settings in the configuration files, indicating that your installation includes one or more custom extensions for data processing, delivery, rendering, security, or authentication.</span></span> <span data-ttu-id="5e54f-104">업그레이드 관리자는 업그레이드된 보고서 서버와 함께 확장 프로그램 구성 설정을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-104">Upgrade will move the extension configuration settings with the upgraded report server.</span></span> <span data-ttu-id="5e54f-105">그러나 사용자 지정 확장 프로그램이 기존 보고서 서버 설치 폴더에 설치되어 있으면 업그레이드 프로세스 중 해당 사용자 지정 확장 프로그램에 대한 어셈블리 파일이 새 설치 폴더로 이동되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-105">However, if the custom extensions are installed in the existing report server installation folder, the assembly files for those custom extensions will not be moved to the new installation folder during the upgrade process.</span></span> <span data-ttu-id="5e54f-106">이 경우 업그레이드가 완료된 후 어셈블리 파일을 새 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치 폴더로 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-106">After upgrade completes, you must move the assembly files to the new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder.</span></span>  
  
||  
|-|  
|<span data-ttu-id="5e54f-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드.</span><span class="sxs-lookup"><span data-stu-id="5e54f-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="5e54f-108">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5e54f-108">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="5e54f-109">Description</span><span class="sxs-lookup"><span data-stu-id="5e54f-109">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="5e54f-110">는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 개발자가 데이터 처리, 배달, 렌더링, 보안 및 인증을 위한 사용자 지정 확장 프로그램을 만들 수 있도록 하는 확장 가능한 아키텍처를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides an extensible architecture that allows developers to create custom extensions for data processing, delivery, rendering, security, and authentication.</span></span>  
  
 <span data-ttu-id="5e54f-111">사용자 지정 확장 프로그램 또는 어셈블리가 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치에서 사용되는 경우 설치 프로그램을 사용하여 업그레이드를 수행할 수 있지만 업그레이드가 완료된 후 확장 프로그램을 새 설치 위치로 이동하거나 업그레이드 전 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-111">If custom extensions or assemblies are used in your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, you can use Setup to perform an upgrade, but you may need to move extensions to the new installation location after upgrade completes, or you may need to perform steps prior to upgrade.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e54f-112">업그레이드 관리자는 사용자 지정 코드 어셈블리가 보고서에서 항목 값, 스타일 및 서식을 계산할 용도로 사용되도록 구성되어 있는지 여부를 감지하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-112">Upgrade Advisor does not detect whether custom code assemblies are configured for use in reports to calculate item values, styles, and formatting.</span></span> <span data-ttu-id="5e54f-113">자세한 내용은 [기타 Reporting Services 업그레이드 문제](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e54f-113">For more information, see [Other Reporting Services Upgrade Issues](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md).</span></span>  
  
 <span data-ttu-id="5e54f-114">소프트웨어 공급업체로부터 사용자 지정 확장 프로그램을 구입한 경우 해당 업체에 사용자 지정 기능의 업그레이드에 대한 추가 정보를 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e54f-114">If you purchased custom extensions from a software vendor, check with the vendor for additional information about upgrading your custom functionality.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="5e54f-115">수정 동작</span><span class="sxs-lookup"><span data-stu-id="5e54f-115">Corrective Action</span></span>  
 <span data-ttu-id="5e54f-116">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 업그레이드하기 전이나 후에 수행할 단계를 확인하려면 다음 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e54f-116">Use the following sections to determine steps to perform in addition to or prior to performing an upgrade of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:</span></span>  
  
 [<span data-ttu-id="5e54f-117">사용자 지정 데이터 처리 또는 배달 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="5e54f-117">Custom data processing or delivery extensions</span></span>](#dataprocdeliver)  
  
 [<span data-ttu-id="5e54f-118">사용자 지정 렌더링 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="5e54f-118">Custom rendering extensions</span></span>](#render)  
  
 [<span data-ttu-id="5e54f-119">SQL Server 2000 보고서 서버의 사용자 지정 보안 또는 인증 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="5e54f-119">Custom security or authentication extensions on a SQL Server 2000 report server</span></span>](#secauth2000)  
  
 [<span data-ttu-id="5e54f-120">SQL Server 2005 보고서 서버의 사용자 지정 보안 또는 인증 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="5e54f-120">Custom security or authentication extensions on a SQL Server 2005 report server</span></span>](#secauth2005)  
  
 <span data-ttu-id="5e54f-121">업그레이드가 완료된 후 확장 프로그램 어셈블리를 새 설치 폴더로 이동한 다음 사용자 지정 확장 프로그램이 예상대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-121">After upgrade completes, move the extension assemblies to the new installation folder and then verify that the custom extensions work as expected.</span></span> <span data-ttu-id="5e54f-122">확장 프로그램이 작동하지 않으면 다음과 같이 다시 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-122">If your extension does not work, you might have to recompile it.</span></span>  
  
#### <a name="to-recompile-an-extension"></a><span data-ttu-id="5e54f-123">확장 프로그램을 다시 컴파일하려면</span><span class="sxs-lookup"><span data-stu-id="5e54f-123">To recompile an extension</span></span>  
  
1.  <span data-ttu-id="5e54f-124">Microsoft.ReportingServices.Interfaces.dll 파일을 원본 코드가 포함된 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-124">Copy the Microsoft.ReportingServices.Interfaces.dll file to the folder that contains your source code.</span></span>  
  
2.  <span data-ttu-id="5e54f-125">원본 파일이 포함된 프로젝트를 열고 Microsoft.ReportingServices.Interfaces.dll 파일에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-125">Open the project that contains your source files and add a reference to the Microsoft.ReportingServices.Interfaces.dll file.</span></span>  
  
3.  <span data-ttu-id="5e54f-126">솔루션을 다시 빌드하여 확장 프로그램을 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-126">Rebuild the solution to bind the extension.</span></span>  
  
 <span data-ttu-id="5e54f-127">업그레이드를 중단하려는 경우 대신 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]로 마이그레이션하는 방법을 고려해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-127">If you decide not to continue with upgrade, you might decide to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span> <span data-ttu-id="5e54f-128">사용자 지정 확장 프로그램을 마이그레이션하는 단계는이 항목의 [사용자 지정 확장 마이그레이션](#migrcustext) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5e54f-128">For steps on migrating custom extensions, see [Migrating custom extensions](#migrcustext) in this topic.</span></span>  
  
###  <a name="custom-data-processing-or-delivery-extensions"></a><a name="dataprocdeliver"></a><span data-ttu-id="5e54f-129">사용자 지정 데이터 처리 또는 배달 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="5e54f-129">Custom data processing or delivery extensions</span></span>  
 <span data-ttu-id="5e54f-130">업그레이드 관리자가 사용자 지정 데이터 처리 또는 배달 확장 프로그램을 검색할 경우 업그레이드 프로세스가 차단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-130">If Upgrade Advisor detects custom data processing or delivery extensions, the upgrade process is not blocked.</span></span> <span data-ttu-id="5e54f-131">그러나 업그레이드가 완료된 후 추가 단계를 수행해야만 이러한 확장 프로그램에서 제공하는 사용자 지정 기능이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-131">However, after upgrade completes, you might need to perform additional steps before the custom functionality provided by these extensions will work.</span></span> <span data-ttu-id="5e54f-132">예를 들어 사용자 지정 확장 프로그램 파일이 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치 폴더에 설치되어 있으면 업그레이드가 완료된 후 추가 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-132">For example, you must perform additional steps when the custom extension files are installed in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder.</span></span>  
  
##### <a name="post-upgrade-steps-for-custom-data-processing-or-delivery-extensions"></a><span data-ttu-id="5e54f-133">사용자 지정 데이터 처리 또는 배달 확장 프로그램에 대해 수행할 업그레이드 후 단계</span><span class="sxs-lookup"><span data-stu-id="5e54f-133">Post-upgrade steps for custom data processing or delivery extensions</span></span>  
  
1.  <span data-ttu-id="5e54f-134">확장 프로그램 파일을 새 보고서 서버 프로그램 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-134">Move the extension file or files to the new program folder for the report server.</span></span> <span data-ttu-id="5e54f-135">기본적으로 보고서 서버 프로그램 폴더는 Files\Microsoft SQL Server \ MSRS10_50에 있습니다. \<*instance_name*> \report server</span><span class="sxs-lookup"><span data-stu-id="5e54f-135">By default, the report server program folder is in \Program Files\Microsoft SQL Server\MSRS10_50.\<*instance_name*>\report server.</span></span>  
  
 <span data-ttu-id="5e54f-136">자세한 내용은 SQL Server 온라인 설명서의 "데이터 처리 확장 프로그램 배포" 및 "배달 확장 프로그램 구현"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e54f-136">For more information, see "Deploying a Data Processing Extension" and "Implementing a Delivery Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-rendering-extensions"></a><a name="render"></a><span data-ttu-id="5e54f-137">사용자 지정 렌더링 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="5e54f-137">Custom rendering extensions</span></span>  
 <span data-ttu-id="5e54f-138">업그레이드 관리자가 사용자 지정 렌더링 확장 프로그램을 검색할 경우 업그레이드 프로세스가 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-138">If Upgrade Advisor detects custom rendering extensions, the upgrade process is blocked.</span></span> <span data-ttu-id="5e54f-139">구성 파일에서 사용자 지정 확장 프로그램 구성 항목을 제거하여 업그레이드 프로세스를 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-139">You can continue with the upgrade process by removing the custom extension configuration entries from the configuration file.</span></span> <span data-ttu-id="5e54f-140">그러나 이렇게 하면 업그레이드가 완료된 후 사용자 지정 확장 프로그램을 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-140">However, this will cause the custom extensions to be unavailable to users after upgrade completes.</span></span> <span data-ttu-id="5e54f-141">업그레이드 후 사용자 지정 렌더링 확장 프로그램이 필요한 경우 업데이트된 렌더링 확장 프로그램을 만들거나 사용자 지정 확장 프로그램 공급업체에서 업데이트된 렌더링 확장 프로그램을 구해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-141">If you need custom rendering extensions after upgrade, you must build updated rendering extensions or obtain updated rendering extensions from a custom extension vendor.</span></span>  
  
 <span data-ttu-id="5e54f-142">업그레이드 지원을 위한 단계를 수행해야 하거나 대신 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]로 마이그레이션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-142">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5e54f-143">업데이트된 렌더링 확장 프로그램이 예상대로 작동하는지 테스트하고 확인하기 전까지는 보고서 서버를 업그레이드하거나 마이그레이션하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="5e54f-143">Do not upgrade or migrate your report server until you have tested and verified that the updated rendering extension works as expected.</span></span>  
  
##### <a name="to-upgrade-custom-rendering-extensions"></a><span data-ttu-id="5e54f-144">사용자 지정 렌더링 확장 프로그램을 업그레이드하려면</span><span class="sxs-lookup"><span data-stu-id="5e54f-144">To upgrade custom rendering extensions</span></span>  
  
1.  <span data-ttu-id="5e54f-145">최신 인터페이스가 있는 렌더링 확장 프로그램을 구합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-145">Obtain rendering extensions with the latest interfaces.</span></span>  
  
2.  <span data-ttu-id="5e54f-146">RSReportServer.config에서 이전 사용자 지정 렌더링 확장 프로그램 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-146">Remove the old custom rendering extension entry or entries from RSReportServer.config.</span></span>  
  
3.  <span data-ttu-id="5e54f-147">보고서 서버를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-147">Upgrade the report server.</span></span>  
  
4.  <span data-ttu-id="5e54f-148">업그레이드가 완료된 후 업데이트된 확장 프로그램을 보고서 서버에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-148">After upgrade completes, install the updated extensions on the report server.</span></span>  
  
 <span data-ttu-id="5e54f-149">자세한 내용은 SQL Server 온라인 설명서의 "렌더링 확장 프로그램 구현"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e54f-149">For more information, see "Implementing a Rendering Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-security-or-authentication-extensions-on-a-sql-server-2000-report-server"></a><a name="secauth2000"></a><span data-ttu-id="5e54f-150">SQL Server 2000 보고서 서버의 사용자 지정 보안 또는 인증 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="5e54f-150">Custom security or authentication extensions on a SQL Server 2000 report server</span></span>  
 <span data-ttu-id="5e54f-151">업그레이드 관리자가 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 보고서 서버에서 사용자 지정 보안 또는 인증 확장 프로그램을 검색할 경우 업그레이드 프로세스가 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-151">If Upgrade Advisor detects custom security or authentication extensions on a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] report server, the upgrade process is blocked.</span></span> <span data-ttu-id="5e54f-152">업그레이드 지원을 위한 단계를 수행해야 하거나 대신 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]로 마이그레이션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-152">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span> <span data-ttu-id="5e54f-153">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]로 넘어오면서 인터페이스가 변경되었기 때문에 어떤 방법을 선택하든 Microsoft.ReportingServices.Interfaces.dll의 최신 인터페이스로 확장 프로그램을 업데이트하고 다시 컴파일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-153">In either case, you must update and recompile the extensions with the latest interfaces in Microsoft.ReportingServices.Interfaces.dll, because the interfaces have changed between [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5e54f-154">업데이트된 보안 또는 인증 확장 프로그램이 예상대로 작동하는지 테스트하고 확인하기 전까지는 보고서 서버를 업그레이드하거나 마이그레이션하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="5e54f-154">Do not upgrade or migrate your report server until you have tested and verified that the updated security or authentication extension works as expected.</span></span>  
  
 <span data-ttu-id="5e54f-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]용으로 작성한 사용자 지정 인증 확장 프로그램을 사용 중인 경우 모델 기반 보고를 위해 새로 도입된 새 클래스와 멤버를 지원하도록 원본 코드를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-155">If you are using a custom authentication extension that you created for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must modify the source code to support new classes and members introduced for model-driven reporting.</span></span>  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2000-report-server"></a><span data-ttu-id="5e54f-156">SQL Server 2000 보고서 서버에서 사용자 지정 보안 또는 인증 확장 프로그램을 업그레이드 하려면</span><span class="sxs-lookup"><span data-stu-id="5e54f-156">To upgrade custom security or authentication extensions from a SQL Server 2000 report server</span></span>  
  
1.  <span data-ttu-id="5e54f-157">보안 또는 인증 확장 프로그램을 최신 인터페이스로 업데이트하고 다시 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-157">Update and recompile any security or authentication extensions with the latest interfaces.</span></span>  
  
2.  <span data-ttu-id="5e54f-158">RSReportServer.config에서 보안 또는 인증 확장 프로그램 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-158">Remove the security or authentication extension entry or entries from RSReportServer.config.</span></span>  
  
3.  <span data-ttu-id="5e54f-159">보고서 서버를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-159">Upgrade the report server.</span></span>  
  
4.  <span data-ttu-id="5e54f-160">업그레이드가 완료된 후 업데이트된 확장 프로그램을 보고서 서버에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-160">After upgrade completes, install the updated extensions on the report server.</span></span>  
  
 <span data-ttu-id="5e54f-161">자세한 내용은 SQL Server 온라인 설명서의 "보안 확장 프로그램 구현"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e54f-161">For more information, see "Implementing a Security Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-security-or-authentication-extensions-on-a-sql-server-2005-report-server"></a><a name="secauth2005"></a><span data-ttu-id="5e54f-162">SQL Server 2005 보고서 서버의 사용자 지정 보안 또는 인증 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="5e54f-162">Custom security or authentication extensions on a SQL Server 2005 report server</span></span>  
 <span data-ttu-id="5e54f-163">업그레이드 관리자가 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 보고서 서버에서 사용자 지정 보안 또는 인증 확장 프로그램을 검색할 경우 업그레이드 프로세스가 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-163">If Upgrade Advisor detects custom security or authentication extensions on a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] report server, the upgrade process is blocked.</span></span> <span data-ttu-id="5e54f-164">업그레이드 지원을 위한 단계를 수행해야 하거나 대신 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]로 마이그레이션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-164">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span>  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2005-report-server"></a><span data-ttu-id="5e54f-165">SQL Server 2005 보고서 서버의 사용자 지정 보안 또는 인증 확장 프로그램을 업그레이드하려면</span><span class="sxs-lookup"><span data-stu-id="5e54f-165">To upgrade custom security or authentication extensions from a SQL Server 2005 report server</span></span>  
  
1.  <span data-ttu-id="5e54f-166">RSReportServer.config에서 보안 또는 인증 확장 프로그램 구성 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-166">Remove the security or authentication extension configuration entries from RSReportServer.config.</span></span>  
  
2.  <span data-ttu-id="5e54f-167">보고서 서버를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-167">Upgrade the report server.</span></span>  
  
3.  <span data-ttu-id="5e54f-168">업그레이드가 완료된 후 구성 항목을 RSReportServer.config에 다시 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-168">After upgrade completes, add the configuration entries back in RSReportServer.config.</span></span>  
  
4.  <span data-ttu-id="5e54f-169">확장 프로그램 어셈블리가 이전 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치 폴더에 설치되어 있으면 새 설치 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-169">If the extension assemblies were installed in the old [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder, move then to the new installation folder.</span></span>  
  
 <span data-ttu-id="5e54f-170">자세한 내용은 SQL Server 온라인 설명서의 "보안 확장 프로그램 구현"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e54f-170">For more information, see "Implementing a Security Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="migrating-custom-extensions"></a><a name="migrcustext"></a><span data-ttu-id="5e54f-171">사용자 지정 확장 프로그램 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="5e54f-171">Migrating custom extensions</span></span>  
 <span data-ttu-id="5e54f-172">업그레이드를 수행하는 대신 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]로 마이그레이션하려는 경우 다음 단계를 수행하여 사용자 지정 확장 프로그램을 새 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스로 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-172">If you decide to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead performing an upgrade, use the steps to migrate custom extensions to the new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance.</span></span>  
  
##### <a name="to-migrate-custom-extensions-to-a-new-reporting-services-instance"></a><span data-ttu-id="5e54f-173">사용자 지정 확장 프로그램을 새 Reporting Services 인스턴스로 마이그레이션하려면</span><span class="sxs-lookup"><span data-stu-id="5e54f-173">To migrate custom extensions to a new Reporting Services instance</span></span>  
  
1.  <span data-ttu-id="5e54f-174">최신 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인터페이스가 있는 업데이트된 확장 프로그램을 만들거나 구합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-174">Build or obtain updated extensions with the latest [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] interfaces.</span></span>  
  
2.  <span data-ttu-id="5e54f-175">보고서 서버를 새 인스턴스로 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-175">Migrate the report server to a new instance.</span></span>  
  
3.  <span data-ttu-id="5e54f-176">새 인스턴스에서 확장 프로그램을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5e54f-176">Configure the extensions on the new instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e54f-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e54f-177">See Also</span></span>  
 [<span data-ttu-id="5e54f-178">업그레이드 관리자를 &#40;업그레이드 문제를 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5e54f-178">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
