---
title: Reporting Services WMI 공급자 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services]
- programming [Reporting Services]
ms.assetid: 22cfbeb8-4ea3-4182-8f54-3341c771e87b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: db0848ae8c988229a1804bbd4b19e6c38b68c35f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737929"
---
# <a name="access-the-reporting-services-wmi-provider"></a><span data-ttu-id="a3105-102">Reporting Services WMI 공급자 액세스</span><span class="sxs-lookup"><span data-stu-id="a3105-102">Access the Reporting Services WMI Provider</span></span>
  <span data-ttu-id="a3105-103">Reporting Services WMI 공급자는 스크립팅을 통해 기본 모드 보고서 서버 인스턴스를 관리하기 위해 두 WMI 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-103">The Reporting Services WMI provider exposes two WMI classes for administration of Native mode report server instances through scripting:</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a3105-104">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 릴리스부터는 WMI 공급자가 기본 모드 보고서 서버에 대해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-104">Starting with the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] release, the WMI provider is supported for only native mode report servers.</span></span> <span data-ttu-id="a3105-105">SharePoint 모드 보고서 서버는 SharePoint 중앙 관리 페이지 및 PowerShell 스크립트를 사용하여 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-105">SharePoint mode report servers can be managed with SharePoint Central Administration pages and PowerShell scripts.</span></span>  
  
|<span data-ttu-id="a3105-106">클래스</span><span class="sxs-lookup"><span data-stu-id="a3105-106">Class</span></span>|<span data-ttu-id="a3105-107">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="a3105-107">Namespace</span></span>|<span data-ttu-id="a3105-108">Description</span><span class="sxs-lookup"><span data-stu-id="a3105-108">Description</span></span>|  
|-----------|---------------|-----------------|  
|<span data-ttu-id="a3105-109">MSReportServer_Instance</span><span class="sxs-lookup"><span data-stu-id="a3105-109">MSReportServer_Instance</span></span>|<span data-ttu-id="a3105-110">root\Microsoft\SqlServer\ReportServer\ RS_ *\<EncodedInstanceName>* \v11</span><span class="sxs-lookup"><span data-stu-id="a3105-110">root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName>* \v11</span></span>|<span data-ttu-id="a3105-111">클라이언트에서 설치된 보고서 서버에 연결하는 데 필요한 기본 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-111">Provides basic information required for a client to connect to an installed report server.</span></span>|  
|<span data-ttu-id="a3105-112">MSReportServer_ConfigurationSetting</span><span class="sxs-lookup"><span data-stu-id="a3105-112">MSReportServer_ConfigurationSetting</span></span>|<span data-ttu-id="a3105-113">root\Microsoft\SqlServer\ReportServer\ RS_ *\<EncodedInstanceName>* \v11\Admin</span><span class="sxs-lookup"><span data-stu-id="a3105-113">root\Microsoft\SqlServer\ReportServer\RS_*\<EncodedInstanceName>* \v11\Admin</span></span>|<span data-ttu-id="a3105-114">보고서 서버 인스턴스의 설치 및 런타임 매개 변수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-114">Represents the installation and run-time parameters of a report server instance.</span></span> <span data-ttu-id="a3105-115">이러한 매개 변수는 보고서 서버의 구성 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-115">These parameters are stored in the configuration file for the report server.</span></span><br /><br /> <span data-ttu-id="a3105-116">**\*\* 중요 \*\*** 이 클래스는 관리 권한이 있어야만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-116">**\*\* Important \*\*** This class is only accessible with administrative privileges.</span></span>|  
  
 <span data-ttu-id="a3105-117">각 보고서 서버 인스턴스에 대해 위의 각 클래스 인스턴스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-117">An instance of each of the above classes is created for each report server instance.</span></span> <span data-ttu-id="a3105-118">모든 Microsoft 또는 타사 도구를 사용하여 .NET Framework 자체에서 제공하는 WMI 프로그래밍 인터페이스를 포함하여 보고서 서버에서 제공하는 WMI 개체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-118">You can use any Microsoft or third party tools to access the WMI objects exposed by the report server, including WMI programming interfaces exposed by the .NET Framework itself.</span></span> <span data-ttu-id="a3105-119">이 항목에서는 PowerShell 명령 [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx)를 사용하여 WMI 클래스 인스턴스에 액세스하고 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-119">This topic describes how to access and use the WMI class instances with the PowerShell command [Get-WmiObject](https://technet.microsoft.com/library/dd315295.aspx).</span></span>  
  
## <a name="determine-the-instance-name-in-the-namespace-string"></a><span data-ttu-id="a3105-120">네임스페이스 문자열에서 인스턴스 이름 결정</span><span class="sxs-lookup"><span data-stu-id="a3105-120">Determine the Instance Name in the Namespace String</span></span>  
 <span data-ttu-id="a3105-121">Reporting Services WMI 클래스의 네임스페이스 경로에 있는 인스턴스 이름은 명명된 Reporting Services 인스턴스를 설치할 때 지정하는 인스턴스 이름의 인코딩입니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-121">The instance name in the namespace path for the Reporting Services WMI classes is an encoding of the instance names that you specify when installing the named Reporting Services instances.</span></span> <span data-ttu-id="a3105-122">즉, 인스턴스 이름의 특수 문자가 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-122">Namely, special characters in the instance names are encoded.</span></span> <span data-ttu-id="a3105-123">예를 들어 밑줄(_)은 "_5f"로 인코딩되므로 인스턴스 이름 "My_Instance"는 WMI 네임스페이스 경로에서 "My_5fInstance"로 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-123">For example, an underline (_) is encoded as "_5f", so an instance name of "My_Instance" is encoded as "My_5fInstance" in the WMI namespace path.</span></span>  
  
 <span data-ttu-id="a3105-124">WMI 네임스페이스 경로에 보고서 서버 인스턴스의 인코딩된 인스턴스 이름을 나열하려면 다음 PowerShell 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-124">To list the encoded instance names of your report server instances in the WMI namespace path, use the following PowerShell command:</span></span>  
  
```powershell
Get-WmiObject -Namespace root\Microsoft\SqlServer\ReportServer -Class __Namespace -ComputerName hostname | Select Name  
```  
  
## <a name="access-the-wmi-classes-using-powershell"></a><span data-ttu-id="a3105-125">PowerShell을 사용하여 WMI 클래스 액세스</span><span class="sxs-lookup"><span data-stu-id="a3105-125">Access the WMI Classes Using PowerShell</span></span>  
 <span data-ttu-id="a3105-126">WMI 클래스에 액세스하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-126">To access the WMI classes, run the following command:</span></span>  
  
```powershell
Get-WmiObject -Namespace <namespacename> -Class <classname> -ComputerName <hostname>  
```  
  
 <span data-ttu-id="a3105-127">예를 들어 myrshost 호스트의 기본 보고서 서버 인스턴스에서 MSReportServer_ConfigurationSetting 클래스에 액세스하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-127">For example, to access the MSReportServer_ConfigurationSetting class on the default report server instance of the host myrshost, run the following command.</span></span> <span data-ttu-id="a3105-128">이 명령을 제대로 수행하려면 기본 보고서 서버 인스턴스가 myrshost에 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-128">The default report server instance must be installed on myrshost for this command to succeed.</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLSERER\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost  
```  
  
 <span data-ttu-id="a3105-129">이 명령 구문은 모든 클래스 속성 이름 및 값을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-129">This command syntax outputs all class property names and values.</span></span> <span data-ttu-id="a3105-130">기본 보고서 서버 인스턴스(RS_MSSQLSERVER)의 네임스페이스에서 클래스에 액세스하더라도 MSReportServer_ConfigurationSetting 클래스의 모든 인스턴스가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-130">Note that all instances of the class MSReportServer_ConfigurationSetting is returned, even though you are accessing the class in the namespace of the default report server instance (RS_MSSQLSERVER).</span></span> <span data-ttu-id="a3105-131">예를 들어 기본 보고서 서버 인스턴스 및 SHAREPOINT라는 명명된 보고서 서버 인스턴스와 함께 myrshost가 설치되어 있는 경우 이 명령은 두 WMI 개체를 반환하고 두 보고서 서버 인스턴스의 속성 이름과 값을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-131">For example, if myrshost is installed with the default report server instance and a named report server instance called SHAREPOINT, this command will return two WMI objects and output the property names and values for both report server instances.</span></span>  
  
 <span data-ttu-id="a3105-132">여러 인스턴스가 반환되는 경우 특정 클래스 인스턴스를 반환하려면 –Filter 매개 변수를 사용하여 InstanceName 등의 고유 값을 가진 속성에 따라 결과를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-132">To return a specific class instance when multiple instances are returned, use the -Filter parameter to filter the results based on properties with unique values such as InstanceName.</span></span> <span data-ttu-id="a3105-133">예를 들어 기본 보고서 서버 인스턴스의 WMI 개체만 반환하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-133">For example, to return only the WMI object for the default report server instance, use the following command:</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='MSSQLSERVER'"  
```  
  
## <a name="query-the-available-methods-and-properties"></a><span data-ttu-id="a3105-134">사용 가능한 메서드 및 속성 쿼리</span><span class="sxs-lookup"><span data-stu-id="a3105-134">Query the Available Methods and Properties</span></span>  
 <span data-ttu-id="a3105-135">Reporting Services WMI 클래스 중 하나에서 사용할 수 있는 메서드 및 속성을 보려면 Get-WmiObject의 결과를 Get-Member 명령으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-135">To see what methods and properties are available in one of the Reporting Services WMI classes, pipe the results from Get-WmiObject to the Get-Member command.</span></span> <span data-ttu-id="a3105-136">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-136">For example:</span></span>  
  
```powershell
Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost | Get-Member  
```  
  
 <span data-ttu-id="a3105-137">Reporting Services WMI 클래스의 속성 및 메서드에 대 한 설명서는 다음을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a3105-137">For documentation on the properties and methods of the Reporting Services WMI classes, see ....</span></span>  
  
## <a name="use-a-wmi-method-or-property"></a><span data-ttu-id="a3105-138">WMI 메서드 또는 속성 사용</span><span class="sxs-lookup"><span data-stu-id="a3105-138">Use a WMI Method or Property</span></span>  
 <span data-ttu-id="a3105-139">Reporting Services 클래스에 대한 WMI 개체가 있고 사용 가능한 메서드와 속성을 알면 이러한 메서드와 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-139">Once you have the WMI objects to the Reporting Services classes and know the available methods and properties, you can use these methods and properties.</span></span> <span data-ttu-id="a3105-140">예를 들어 SharePoint 통합 모드에 SHAREPOINT라는 명명된 보고서 서버 인스턴스가 있는 경우 다음 명령 시퀀스를 사용하여 SharePoint 중앙 관리 사이트의 URL을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a3105-140">For example, if you have a named report server instance in SharePoint integrated mode called SHAREPOINT, use the following command sequence to retrieve the URL for the SharePoint Central Administration site:</span></span>  
  
```powershell
$rsconfig = Get-WmiObject -Namespace "root\Microsoft\SqlServer\ReportServer\RS_MSSQLServer\v11\Admin" -Class MSReportServer_ConfigurationSetting -ComputerName myrshost -Filter "InstanceName='SHAREPOINT'"  
$rsconfig.GetAdminSiteUrl()  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3105-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3105-141">See Also</span></span>
 <span data-ttu-id="a3105-142">[Reporting Services WMI 공급자 라이브러리 참조 &#40;SSRS&#41;](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a3105-142">[Reporting Services WMI Provider Library Reference &#40;SSRS&#41;](../wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="a3105-143">RSReportServer Configuration File</span><span class="sxs-lookup"><span data-stu-id="a3105-143">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
