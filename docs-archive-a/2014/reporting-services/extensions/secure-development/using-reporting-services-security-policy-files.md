---
title: Reporting Services 보안 정책 파일 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- CodeGroup elements
- configuration files [Reporting Services]
- code access security [Reporting Services], security policies
- security policies [Reporting Services]
- security configuration files [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: 2280fff6-3de7-44b1-87da-5db0ec975928
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15c5422741137505bc29a2de861fca1420e455d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660903"
---
# <a name="using-reporting-services-security-policy-files"></a><span data-ttu-id="8393a-102">Reporting Services 보안 정책 파일 사용</span><span class="sxs-lookup"><span data-stu-id="8393a-102">Using Reporting Services Security Policy Files</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="8393a-103">는 설치 중에 파일 시스템으로 복사되는 세 개의 구성 파일에 구성 요소 보안 정책 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-103">stores component security policy information in three configuration files that are copied to the file system during setup.</span></span> <span data-ttu-id="8393a-104">이러한 구성 파일에는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 코드 어셈블리에 대한 내부용 보안 정책과 사용자 정의 보안 정책의 조합이 들어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-104">These configuration files can contain a combination of internal-use and user-defined security policies for code assemblies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="8393a-105">세 개의 구성 파일은 보고서 서버 및 Windows 서비스, 보고서 관리자 웹 애플리케이션, 보고서 디자이너 미리 보기 창과 같은 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 세 개 보안 개체 구성 요소에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-105">The three configuration files correspond to three securable components in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]: The report server and Windows service, the Report Manager Web application, and the Report Designer preview window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8393a-106">보고서 디자이너에는 보고서 프로젝트를 **DebugLocal** 모드에서 시작할 때 실행되는 팝업 미리 보기 창과 미리 보기 탭이라는 두 개의 미리 보기 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-106">There are two preview modes for Report Designer: the preview tab and the pop-up preview window that is launched when your Report Project is started in **DebugLocal** mode.</span></span> <span data-ttu-id="8393a-107">**미리 보기** 탭은 보안 개체 구성 요소가 아니며 보안 정책 설정을 적용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-107">The **Preview** tab is not a securable component and does not apply security policy settings.</span></span> <span data-ttu-id="8393a-108">미리 보기 창은 보고서 서버 기능을 시뮬레이션하기 위한 것이므로 보고서 디자이너에서 사용자 지정 어셈블리 및 사용자 지정 확장 프로그램을 사용하기 위해 사용자나 관리자가 수정해야 하는 정책 구성 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-108">The preview window is meant to simulate the report server functionality and therefore has a policy configuration file that you or an administrator must modify to use custom assemblies and custom extensions in Report Designer.</span></span>  
  
 <span data-ttu-id="8393a-109">보안 정책 구성 파일에는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 어셈블리에 대한 보안 클래스 정보, 기본 명명된 권한 집합 및 코드 그룹이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-109">The security policy configuration files contain security class information, some default named permission sets, and the code groups for assemblies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="8393a-110">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 정책 구성 파일은 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]의 컴퓨터 및 엔터프라이즈 수준 정책과 관련된 코드 그룹 계층 및 권한 집합을 결정하는 Security.config 파일과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-110">The policy configuration files of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] are similar to the Security.config file that determines the code group hierarchy and permission sets associated with machine and enterprise level policies in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="8393a-111">이 파일의 위치는 C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\CONFIG\security.config입니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-111">The location of this file is C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\CONFIG\security.config.</span></span>  
  
## <a name="policy-files-in-reporting-services"></a><span data-ttu-id="8393a-112">Reporting Services의 정책 파일</span><span class="sxs-lookup"><span data-stu-id="8393a-112">Policy Files in Reporting Services</span></span>  
 <span data-ttu-id="8393a-113">다음 표에서는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 정책 구성 파일, 해당 위치(기본 설치 가정) 및 해당 기능을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-113">The following table lists the policy configuration files in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], their locations (assuming a default installation), and their respective functions.</span></span>  
  
|<span data-ttu-id="8393a-114">파일 이름</span><span class="sxs-lookup"><span data-stu-id="8393a-114">File name</span></span>|<span data-ttu-id="8393a-115">위치(기본 설치)</span><span class="sxs-lookup"><span data-stu-id="8393a-115">Location (default installation)</span></span>|<span data-ttu-id="8393a-116">Description</span><span class="sxs-lookup"><span data-stu-id="8393a-116">Description</span></span>|  
|---------------|---------------------------------------|-----------------|  
|<span data-ttu-id="8393a-117">rssrvpolicy.config</span><span class="sxs-lookup"><span data-stu-id="8393a-117">rssrvpolicy.config</span></span>|<span data-ttu-id="8393a-118">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer</span><span class="sxs-lookup"><span data-stu-id="8393a-118">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer</span></span>|<span data-ttu-id="8393a-119">보고서 서버의 정책 구성 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-119">The report server policy configuration file.</span></span> <span data-ttu-id="8393a-120">보고서가 보고서 서버에 배포되면 이러한 보안 정책은 주로 보고서 식 및 사용자 지정 어셈블리에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-120">These security policies primarily affect report expressions and custom assemblies once a report is deployed to a report server.</span></span> <span data-ttu-id="8393a-121">이 정책 파일은 보고서 서버에 배포된 사용자 지정 데이터, 배달, 렌더링 및 보안 확장 프로그램에도 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-121">This policy file also affects custom data, delivery, rendering and security extensions deployed to the report server.</span></span>|  
|<span data-ttu-id="8393a-122">rsmgrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="8393a-122">rsmgrpolicy.config</span></span>|<span data-ttu-id="8393a-123">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager</span><span class="sxs-lookup"><span data-stu-id="8393a-123">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager</span></span>|<span data-ttu-id="8393a-124">보고서 관리자의 정책 구성 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-124">Report Manager policy configuration file.</span></span> <span data-ttu-id="8393a-125">이러한 보안 정책은 사용자 지정 배달을 위한 구독 사용자 인터페이스 확장 프로그램과 같이 보고서 관리자를 확장하는 모든 어셈블리에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-125">These security policies affect all assemblies that extend Report Manager; for example, subscription user interface extensions for custom delivery.</span></span>|  
|<span data-ttu-id="8393a-126">rspreviewpolicy.config</span><span class="sxs-lookup"><span data-stu-id="8393a-126">rspreviewpolicy.config</span></span>|<span data-ttu-id="8393a-127">C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies</span><span class="sxs-lookup"><span data-stu-id="8393a-127">C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies</span></span>|<span data-ttu-id="8393a-128">보고서 디자이너의 독립 실행형 미리 보기 정책 구성 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-128">The Report Designer stand-alone preview policy configuration file.</span></span> <span data-ttu-id="8393a-129">이러한 보안 정책은 미리 보기 및 개발 중에 보고서에 사용되는 사용자 지정 어셈블리 및 보고서 식에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-129">These security policies affect custom assemblies and report expressions that are used in reports during preview and development.</span></span> <span data-ttu-id="8393a-130">이러한 정책은 보고서 디자이너에 배포된 데이터 처리 확장 프로그램과 같은 사용자 지정 확장 프로그램에도 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-130">These policies also affect custom extensions, such as data processing extensions, that are deployed to Report Designer.</span></span>|  
  
## <a name="modifying-configuration-files"></a><span data-ttu-id="8393a-131">구성 파일 수정</span><span class="sxs-lookup"><span data-stu-id="8393a-131">Modifying Configuration Files</span></span>  
 <span data-ttu-id="8393a-132">구성 설정은 XML 요소나 특성으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-132">Configuration settings are specified as either XML elements or attributes.</span></span> <span data-ttu-id="8393a-133">XML과 구성 파일에 대해 이해하고 있으면 텍스트나 코드 편집기를 사용하여 사용자 정의 가능한 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-133">If you understand XML and configuration files, you can use a text or code editor to modify user-definable settings.</span></span> <span data-ttu-id="8393a-134">보안 구성 파일에는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 정책 수준과 관련된 코드 그룹 계층 및 권한 집합에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-134">Security configuration files contain information about the code group hierarchy and permission sets associated with a policy level in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="8393a-135">정책 변경 내용이 정책 파일의 올바른 XML 구성 요소에 해당하도록 .NET Framework 구성 유틸리티(Mscorcfg.msc) 또는 코드 액세스 보안 정책 유틸리티(Caspol.exe)를 사용하여 Security.config 파일에서 보안 정책을 먼저 수정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-135">It is recommended that you use the .NET Framework Configuration Utility (Mscorcfg.msc) or Code Access Security Policy Utility (Caspol.exe) to modify security policies in the Security.config file first, so that policy changes correspond to valid XML configuration elements for policy files.</span></span> <span data-ttu-id="8393a-136">이 작업을 수행한 다음에는 Security.config에서 새 코드 그룹 및 권한 집합을 잘라내어 코드 권한을 추가하는 구성 요소의 정책 파일에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-136">Once you have done that, you can cut and paste the new code groups and permission sets from Security.config to the policy file for the component to which you are adding code permissions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8393a-137">변경하기 전에 정책 구성 파일을 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-137">You should backup your policy configuration files prior to making any changes.</span></span>  
  
 <span data-ttu-id="8393a-138">이 방법을 사용하면 두 가지 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-138">Using this approach accomplishes two things.</span></span> <span data-ttu-id="8393a-139">첫 번째로, 시각적 도구를 사용하여 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에 대한 코드 그룹 및 권한 집합을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-139">First, it enables you to use a visual tool to build your code groups and permission sets for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="8393a-140">이렇게 하는 것이 완전히 새로 XML 구성 요소를 쓰는 것보다 훨씬 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-140">This is much easier than writing XML configuration elements from scratch.</span></span> <span data-ttu-id="8393a-141">두 번째로, 잘못된 XML 요소 및 특성으로 인해 보안 정책 구성 파일이 손상되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-141">Secondly, it ensures that you do not corrupt the security policy configuration files with malformed XML elements and attributes.</span></span> <span data-ttu-id="8393a-142">코드 액세스 보안 정책 유틸리티에 대한 자세한 내용은 MSDN에서 Reporting Services 보안 정책 파일 사용을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8393a-142">For more information about the Code Access Security Policy Utility, see Using Reporting Services Security Policy Files on MSDN.</span></span>  
  
 <span data-ttu-id="8393a-143">정책 구성 파일을 수정하기 전에 이 섹션 및 관련 항목에 제공된 모든 정보를 읽어 보아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-143">Before modifying policy configuration files, you should read all the information available in this section and related topics.</span></span> <span data-ttu-id="8393a-144">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 정책 구성을 수정하면 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구성 요소가 외부 코드 모듈을 실행하는 방식에 심각한 보안 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-144">Modifying the policy configuration of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] can have a significant security impact on how [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] components execute external code modules.</span></span>  
  
## <a name="placement-of-codegroup-elements-for-extensions"></a><span data-ttu-id="8393a-145">확장 프로그램에 대한 CodeGroup 요소 배치</span><span class="sxs-lookup"><span data-stu-id="8393a-145">Placement of CodeGroup Elements for Extensions</span></span>  
 <span data-ttu-id="8393a-146">보안 정책 파일에서의 CodeGroup 요소 배치는 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-146">The placement of CodeGroup elements in a security policy file is important.</span></span> <span data-ttu-id="8393a-147">개발하는 확장 프로그램 및 사용자 지정 어셈블리에 대해 사용자 지정 코드 그룹을 다음과 같이 URL 멤버 자격 "$CodeGen$/\*"의 기존 항목 바로 아래에 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-147">For extensions and custom assemblies that you develop, it is recommended that you place your custom code groups directly below the existing entry for the URL membership "$CodeGen$/\*", as indicated by the following:</span></span>  
  
```  
<CodeGroup  
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust">  
    <IMembershipCondition   
        class="UrlMembershipCondition"  
        version="1"  
        Url="$CodeGen$/*"  
    />  
</CodeGroup>  
<CodeGroup   
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust"  
    Name="MyCustomCodeGroup"  
    Description="Code group for my custom extension">  
        <IMembershipCondition class="UrlMembershipCondition"  
        version="1"  
        Url="C:\Program Files\Microsoft SQL Server\MSSQL\Reporting Services\ReportServer\bin\MyAssembly.dll"  
        />  
</CodeGroup>  
```  
  
 <span data-ttu-id="8393a-148">추가 코드 그룹을 차례로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8393a-148">Additional code groups can be added one after another.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8393a-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8393a-149">See Also</span></span>  
 [<span data-ttu-id="8393a-150">보안 정책 이해</span><span class="sxs-lookup"><span data-stu-id="8393a-150">Understanding Security Policies</span></span>](understanding-security-policies.md)  
  
  
