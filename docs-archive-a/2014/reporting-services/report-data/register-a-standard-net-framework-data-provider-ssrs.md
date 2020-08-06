---
title: 표준 .NET Framework 데이터 공급자 등록(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- .NET Framework data providers for Reporting Services
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
ms.assetid: d92add64-e93c-4598-8508-55d1bc46acf6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5fd26f9c7fa163d9e6005d42e24c7b1483987f3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729092"
---
# <a name="register-a-standard-net-framework-data-provider-ssrs"></a><span data-ttu-id="3e857-102">표준 .NET Framework 데이터 공급자 등록(SSRS)</span><span class="sxs-lookup"><span data-stu-id="3e857-102">Register a Standard .NET Framework Data Provider (SSRS)</span></span>
  <span data-ttu-id="3e857-103">타사 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자를 사용하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 데이터 세트에 대한 데이터를 검색하려면 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자 어셈블리를 보고서 제작 클라이언트와 보고서 서버에 배포하고 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-103">To use a third-party [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider to retrieve data for a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report dataset, you need to deploy and register the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly in two locations: on the report authoring client and on the report server.</span></span> <span data-ttu-id="3e857-104">보고서 제작 클라이언트에서 데이터 공급자를 데이터 원본 유형으로 등록하고 쿼리 디자이너와 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-104">On the report authoring client, you must register the data provider as a data source type and associate it with a query designer.</span></span> <span data-ttu-id="3e857-105">그러면 보고서 데이터 세트를 만들 때 이 데이터 공급자를 데이터 원본 유형으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-105">You can then select this data provider as a type of data source when you create a report dataset.</span></span> <span data-ttu-id="3e857-106">연결된 쿼리 디자이너가 열려 이 데이터 원본 유형에 대한 쿼리 생성을 도와줍니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-106">The associated query designer opens to help you create queries for this data source type.</span></span> <span data-ttu-id="3e857-107">또한 보고서 서버에서 데이터 공급자를 데이터 원본 유형으로 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-107">On the report server, you must register the data provider as a data source type.</span></span> <span data-ttu-id="3e857-108">그러면 이 데이터 공급자를 사용하여 데이터 원본에서 데이터를 검색하는 게시된 보고서를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-108">You can then process published reports that retrieve data from a data source using this data provider.</span></span>  
  
 <span data-ttu-id="3e857-109">타사 데이터 공급자가 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램에서 사용할 수 있는 모든 기능을 제공하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-109">Third-party data providers do not necessarily provide all the functionality available with the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extensions.</span></span> <span data-ttu-id="3e857-110">자세한 내용은 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e857-110">For more information, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span> <span data-ttu-id="3e857-111">.[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e857-111">To learn about extending the functionality of a .[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]</span></span> <span data-ttu-id="3e857-112"> 데이터 공급자는 [데이터 처리 확장 프로그램 구현](../extensions/data-processing/implementing-a-data-processing-extension.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e857-112">data provider, see [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md).</span></span>  
  
 <span data-ttu-id="3e857-113">데이터 공급자를 설치하고 등록하려면 관리자 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-113">You need administrator credentials to install and register data providers.</span></span>  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-server"></a><span data-ttu-id="3e857-114">보고서 서버에 .NET Framework 데이터 공급자 등록</span><span class="sxs-lookup"><span data-stu-id="3e857-114">Registering a .NET Framework Data Provider on the Report Server</span></span>  
 <span data-ttu-id="3e857-115">보고서 서버에서 이 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자를 사용하는 게시된 보고서를 처리하려면 보고서 서버에 어셈블리를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-115">In order to process published reports that use this [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider on the report server, you need to install the assembly on the report server.</span></span> <span data-ttu-id="3e857-116">두 개의 구성 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-116">You must modify two configuration files.</span></span> <span data-ttu-id="3e857-117">rsreportserver.config를 수정하여 데이터 공급자를 등록하고</span><span class="sxs-lookup"><span data-stu-id="3e857-117">Modify rsreportserver.config to register the data provider.</span></span> <span data-ttu-id="3e857-118">rssrvpolicy.config를 수정하여 어셈블리에 대한 코드 액세스 보안 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-118">Modify rssrvpolicy.config to grant code access security permissions for the assembly.</span></span>  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-server"></a><span data-ttu-id="3e857-119">보고서 서버에 데이터 공급자 어셈블리를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="3e857-119">To install a data provider assembly on the report server</span></span>  
  
1.  <span data-ttu-id="3e857-120">보고서 서버에서 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자를 사용할 bin 디렉터리의 기본 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-120">Navigate to the default location of the bin directory on the report server on which you want to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="3e857-121">보고서 서버 bin 디렉터리의 기본 위치는 *\<drive>* : \Files\Microsoft SQL Server \ MSRS10_50. MSSQLSERVER\Reporting services\reportserver\bin입니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-121">The default location of the report server bin directory is *\<drive>*:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin.</span></span>  
  
2.  <span data-ttu-id="3e857-122">준비 위치에서 보고서 서버의 bin 디렉터리로 어셈블리를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-122">Copy your assembly from your staging location to the bin directory of the report server.</span></span> <span data-ttu-id="3e857-123">또는 GAC(전역 어셈블리 캐시)에 어셈블리를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-123">Alternatively, you can load your assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="3e857-124">자세한 내용은 MSDN에 있는 [SDK 설명서의](https://go.microsoft.com/fwlink/?linkid=63912) 어셈블리 및 전역 어셈블리 캐시 작업(Working with Assemblies and the Global Assembly Cache) [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3e857-124">For more information, see [Working with Assemblies and the Global Assembly Cache](https://go.microsoft.com/fwlink/?linkid=63912) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation on MSDN.</span></span>  
  
#### <a name="to-register-a-net-data-provider-on-the-report-server"></a><span data-ttu-id="3e857-125">보고서 서버에 .NET 데이터 공급자를 등록하려면</span><span class="sxs-lookup"><span data-stu-id="3e857-125">To register a .NET data provider on the report server</span></span>  
  
1.  <span data-ttu-id="3e857-126">bin의 ReportServer 부모 디렉터리에 RSReportServer.config 파일의 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-126">Make a backup of the RSReportServer.config file in the ReportServer parent directory for bin.</span></span>  
  
2.  <span data-ttu-id="3e857-127">RSReportServer.config를 엽니다. [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 또는 메모장과 같은 간단한 텍스트 편집기를 사용하여 이 구성 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-127">Open RSReportServer.config. You can open the configuration file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="3e857-128">RSReportServer.config 파일에서 `Data` 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-128">Locate the `Data` element in the RSReportServer.config file.</span></span> <span data-ttu-id="3e857-129">다음 위치에 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자에 대한 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-129">An entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="3e857-130">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자에 대한 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-130">Add an entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span>  
  
    |<span data-ttu-id="3e857-131">attribute</span><span class="sxs-lookup"><span data-stu-id="3e857-131">Attribute</span></span>|<span data-ttu-id="3e857-132">Description</span><span class="sxs-lookup"><span data-stu-id="3e857-132">Description</span></span>|  
    |---------------|-----------------|  
    |`Name`|<span data-ttu-id="3e857-133">데이터 공급자의 고유 이름(예: **MyNETDataProvider**)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-133">Provide a unique name for the data provider, for example, **MyNETDataProvider**.</span></span> <span data-ttu-id="3e857-134">`Name` 특성의 최대 길이는 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-134">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="3e857-135">이름은 구성 파일의 `Extension` 요소에 있는 모든 항목 중에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-135">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="3e857-136">여기에 포함하는 값은 새 데이터 원본을 만들 때 데이터 원본 유형 드롭다운 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-136">The value you include here appears in the drop-down list of data source types when you create a new data source.</span></span>|  
    |`Type`|<span data-ttu-id="3e857-137"><xref:System.Data.IDbConnection> 인터페이스를 구현하는 클래스의 정규화된 네임스페이스 뒤에 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자 어셈블리 이름(.dll 파일 확장명 포함 안 함)이 쉼표로 구분되어 결합된 목록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-137">Enter a comma-separated list that includes the fully qualified namespace of the class that implements the <xref:System.Data.IDbConnection> interface, followed by the name of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly (not including the .dll file name extension).</span></span>|  
  
     <span data-ttu-id="3e857-138">예를 들어 보고서 서버 bin 디렉터리에 배포되는 DLL의 경우 다음과 같이 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-138">For example, the entry might resemble the following for a DLL deployed to the report server bin directory:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     <span data-ttu-id="3e857-139">GAC(전역 어셈블리 캐시)에 어셈블리를 로드하는 경우 강력한 이름 속성을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-139">If you load your assembly into the global assembly cache (GAC), you must provide the strong name properties.</span></span> <span data-ttu-id="3e857-140">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-140">For example:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly,Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider"></a><span data-ttu-id="3e857-141">.NET 데이터 공급자에 대한 코드 그룹 정책을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="3e857-141">To set the code group policy for a .NET data provider</span></span>  
  
1.  <span data-ttu-id="3e857-142">bin의 ReportServer 부모 디렉터리에 rssrvpolicy.config 파일의 백업 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-142">Make a backup copy of the rssrvpolicy.config file in the ReportServer parent directory for bin.</span></span>  
  
2.  <span data-ttu-id="3e857-143">rssrvpolicy.config를 엽니다. [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]또는 메모장과 같은 간단한 텍스트 편집기를 사용 하 여 구성 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-143">Open rssrvpolicy.config. You can open the configuration file with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor such as Notepad.</span></span>  
  
3.  <span data-ttu-id="3e857-144">rssrvpolicy.config 파일에서 `CodeGroup` 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-144">Locate the `CodeGroup` element in the rssrvpolicy.config file.</span></span>  
  
4.  <span data-ttu-id="3e857-145">`FullTrust` 권한을 부여하는 데이터 공급자 어셈블리의 코드 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-145">Add a code group for the data provider assembly that grants `FullTrust` permission.</span></span> <span data-ttu-id="3e857-146">코드 그룹은 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-146">Your code group might resemble the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="3e857-147">URL 멤버 자격은 데이터 공급자에 대해 선택할 수 있는 많은 멤버 자격 조건 중 하나일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-147">URL membership is only one of many membership conditions you might select for the data provider.</span></span>  
  
### <a name="verifying-the-deployment-and-registration"></a><span data-ttu-id="3e857-148">배포 및 등록 확인</span><span class="sxs-lookup"><span data-stu-id="3e857-148">Verifying the Deployment and Registration</span></span>  
 <span data-ttu-id="3e857-149">보고서 관리자를 열고 데이터 공급자가 사용 가능한 데이터 원본 목록에 포함되어 있는지 확인하여 데이터 공급자가 보고서 서버에 배포되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-149">You can verify whether the data provider was deployed successfully to the report server by opening Report Manager and verifying that the data provider is included in the list of available data sources.</span></span> <span data-ttu-id="3e857-150">보고서 관리자 및 데이터 원본에 대한 자세한 내용은 [공유 데이터 원본 만들기, 수정 및 삭제&#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e857-150">For more information about Report Manager and data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-designer-client"></a><span data-ttu-id="3e857-151">보고서 디자이너 클라이언트에 .NET Framework 데이터 공급자 등록</span><span class="sxs-lookup"><span data-stu-id="3e857-151">Registering a .NET Framework Data Provider on the Report Designer Client</span></span>  
 <span data-ttu-id="3e857-152">데이터 원본에 대해 이 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자를 사용하는 보고서를 작성하려면 보고서 디자이너를 실행하는 클라이언트 컴퓨터에 어셈블리를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-152">In order to author reports that use this [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider for a data source, you must install the assembly on your client computer that runs Report Designer.</span></span> <span data-ttu-id="3e857-153">두 개의 구성 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-153">You must modify two configuration files.</span></span> <span data-ttu-id="3e857-154">RSReportDesigner.config를 수정하여 데이터 공급자를 데이터 원본으로 등록하고 일반 쿼리 디자이너를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-154">Modify RSReportDesigner.config to register the data provider as a data source and to use the generic query designer.</span></span> <span data-ttu-id="3e857-155">또한 RSPreviewPolicy.config를 수정하여 데이터 공급자 어셈블리에 대한 코드 액세스 보안 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-155">Modify RSPreviewPolicy.config to grant code access security permissions for the data provider assembly.</span></span>  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-designer-client"></a><span data-ttu-id="3e857-156">보고서 디자이너 클라이언트에 데이터 공급자 어셈블리를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="3e857-156">To install a data provider assembly on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="3e857-157">보고서 디자이너 클라이언트에서 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자를 사용할 PrivateAssemblies 디렉터리의 기본 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-157">Navigate to the default location of the PrivateAssemblies directory on the Report Designer client on which you want to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="3e857-158">PrivateAssemblies 디렉터리의 기본 위치는 *\<drive>* : \Files\Microsoft Visual Studio 9.0 \ common7\ide\privateassemblies입니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-158">The default location of the PrivateAssemblies directory is *\<drive>*:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
2.  <span data-ttu-id="3e857-159">준비 위치에서 보고서 디자이너 클라이언트의 PrivateAssemblies 디렉터리로 어셈블리를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-159">Copy your assembly from your staging location to the PrivateAssemblies directory of the Report Designer client.</span></span> <span data-ttu-id="3e857-160">또는 GAC(전역 어셈블리 캐시)에 어셈블리를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-160">Alternatively, you can load your assembly in the global assembly cache (GAC).</span></span> <span data-ttu-id="3e857-161">자세한 내용은 MSDN에 있는 [SDK 설명서의](https://go.microsoft.com/fwlink/?linkid=63912) 어셈블리 및 전역 어셈블리 캐시 작업(Working with Assemblies and the Global Assembly Cache) [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3e857-161">For more information, see [Working with Assemblies and the Global Assembly Cache](https://go.microsoft.com/fwlink/?linkid=63912) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation on MSDN.</span></span>  
  
#### <a name="to-register-a-net-data-provider-on-the-report-designer-client"></a><span data-ttu-id="3e857-162">보고서 디자이너 클라이언트에 .NET 데이터 공급자를 등록하려면</span><span class="sxs-lookup"><span data-stu-id="3e857-162">To register a .NET data provider on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="3e857-163">PrivateAssemblies 디렉터리에 RSReportDesigner.config 파일의 백업 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-163">Make a backup copy of the RSReportDesigner.config file in the PrivateAssemblies directory.</span></span>  
  
2.  <span data-ttu-id="3e857-164">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 또는 메모장과 같은 간단한 텍스트 편집기를 사용하여 RSReportDesigner.config를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-164">Open RSReportDesigner.config with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor such as Notepad.</span></span>  
  
3.  <span data-ttu-id="3e857-165">RSReportDesigner.config 파일에서 `Data` 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-165">Locate the `Data` element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="3e857-166">다음 위치에 데이터 공급자에 대한 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-166">An entry for the data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="3e857-167">데이터 공급자에 대한 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-167">Add an entry for the data provider.</span></span>  
  
    |<span data-ttu-id="3e857-168">특성</span><span class="sxs-lookup"><span data-stu-id="3e857-168">Attribute</span></span>|<span data-ttu-id="3e857-169">Description</span><span class="sxs-lookup"><span data-stu-id="3e857-169">Description</span></span>|  
    |---------------|-----------------|  
    |`Name`|<span data-ttu-id="3e857-170">데이터 공급자의 고유 이름(예: **MyNETDataProvider**)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-170">Provide a unique name for the data provider, for example, **MyNETDataProvider**.</span></span> <span data-ttu-id="3e857-171">`Name` 특성의 최대 길이는 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-171">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="3e857-172">이름은 구성 파일의 `Extension` 요소에 있는 모든 항목 중에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-172">The name must be unique among all entries within the `Extension` element of a configuration file.</span></span> <span data-ttu-id="3e857-173">여기에 포함하는 값은 새 데이터 원본을 만들 때 데이터 원본 유형 드롭다운 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-173">The value that you include here appears in the drop-down list of data source types when you create a new data source.</span></span>|  
    |`Type`|<span data-ttu-id="3e857-174"><xref:System.Data.IDbConnection> 인터페이스를 구현하는 클래스의 정규화된 네임스페이스 뒤에 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자 어셈블리 이름(.dll 파일 확장명 포함 안 함)이 쉼표로 구분되어 결합된 목록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-174">Enter a comma-separated list that includes the fully qualified namespace of the class that implements the <xref:System.Data.IDbConnection> interface, followed by the name of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly (not including the .dll file name extension).</span></span>|  
  
     <span data-ttu-id="3e857-175">예를 들어 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] PrivateAssemblies 디렉터리에 배포되는 DLL의 경우 다음과 같이 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-175">For example, the entry might resemble the following for a DLL deployed to the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] PrivateAssemblies directory:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     <span data-ttu-id="3e857-176">GAC에 어셈블리를 로드하는 경우 강력한 이름 속성을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-176">If you load your assembly into the GAC, you must provide the strong name properties.</span></span> <span data-ttu-id="3e857-177">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-177">For example:</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
5.  <span data-ttu-id="3e857-178">RSReportDesigner.config 파일에서 `Designer` 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-178">Locate the `Designer` element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="3e857-179">다음 위치에 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자에 대한 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-179">An entry for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Designer>  
          <Your data provider configuration information goes here>  
       </Designer>  
    </Extensions>  
    ```  
  
6.  <span data-ttu-id="3e857-180">RSReportDesigner.config 파일의 `Designer` 요소 아래에 다음 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-180">Add the following entry to the RSReportDesigner.config file under the `Designer` element.</span></span> <span data-ttu-id="3e857-181">`Name` 특성만 이전 입력에서 제공한 이름으로 바꾸면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-181">You need to replace only the `Name` attribute with the name that you provided in previous entries.</span></span>  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider-on-the-report-designer-client"></a><span data-ttu-id="3e857-182">보고서 디자이너 클라이언트에서 .NET 데이터 공급자에 대한 코드 그룹 정책을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="3e857-182">To set the code group policy for a .NET data provider on the Report Designer client</span></span>  
  
1.  <span data-ttu-id="3e857-183">PrivateAssemblies 디렉터리에 RSPreviewPolicy.config 파일의 백업 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-183">Make a backup copy of the RSPreviewPolicy.config file in the PrivateAssemblies directory.</span></span>  
  
2.  <span data-ttu-id="3e857-184">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 또는 메모장과 같은 간단한 텍스트 편집기를 사용하여 RSPreviewPolicy.config를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-184">Open RSPreviewPolicy.config with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="3e857-185">RSPreviewPolicy.config 파일에서 `CodeGroup` 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-185">Locate the `CodeGroup` element in the RSPreviewPolicy.config file.</span></span>  
  
4.  <span data-ttu-id="3e857-186">`FullTrust` 권한을 부여하는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자 어셈블리의 코드 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-186">Add a code group for the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider assembly that grants `FullTrust` permission.</span></span> <span data-ttu-id="3e857-187">코드 그룹은 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-187">Your code group might resemble the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    " C:\Program Files\Microsoft Visual Studio 9\Common7\IDE\PrivateAssemblies\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="3e857-188">URL 멤버 자격은 데이터 공급자에 대해 선택할 수 있는 많은 멤버 자격 조건 중 하나일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-188">URL membership is only one of many membership conditions you might select for the data provider.</span></span>  
  
### <a name="verifying-the-deployment-and-registration-on-the-report-designer-client"></a><span data-ttu-id="3e857-189">보고서 디자이너 클라이언트에서 배포 및 등록 확인</span><span class="sxs-lookup"><span data-stu-id="3e857-189">Verifying the Deployment and Registration on the Report Designer Client</span></span>  
 <span data-ttu-id="3e857-190">배포를 확인하려면 먼저 로컬 컴퓨터에서 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 인스턴스를 모두 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-190">Before you can verify deployment, you must close all instances of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] on your local computer.</span></span> <span data-ttu-id="3e857-191">현재 세션을 모두 종료한 후 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]에서 새 보고서 프로젝트를 만들어 데이터 공급자가 보고서 디자이너에 배포되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-191">After you have ended all current sessions, you can verify whether your data provider was deployed successfully to Report Designer by creating a new report project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="3e857-192">이때 데이터 공급자는 보고서에 대한 새 데이터 집합을 만들 때 사용 가능한 데이터 원본 유형 목록에 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-192">The data provider should be included in the list of available data source types when you create a new data set for your report.</span></span>  
  
## <a name="platform-considerations"></a><span data-ttu-id="3e857-193">플랫폼 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3e857-193">Platform Considerations</span></span>  
 <span data-ttu-id="3e857-194">64비트(x64) 플랫폼에서 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 는 32비트 WOW 모드로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-194">On a 64-bit (x64) platform, [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] runs in 32-bit WOW mode.</span></span> <span data-ttu-id="3e857-195">x64 플랫폼에서 보고서를 작성하는 경우 보고서를 미리 보려면 보고서 제작 클라이언트에 32비트 데이터 공급자가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-195">When you author reports on an x64 platform, you need 32-bit data providers installed on the report authoring client in order to preview your reports.</span></span> <span data-ttu-id="3e857-196">동일한 시스템에 보고서를 게시하는 경우 보고서 관리자를 사용하여 보고서를 보려면 x64 데이터 공급자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-196">If you publish the report on the same system, you need x64 data providers to view the report with Report Manager.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="3e857-197">는 [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]기반 플랫폼에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-197">is not supported for [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-based platforms.</span></span>  
  
 <span data-ttu-id="3e857-198">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 와 함께 설치되는 데이터 처리 확장 프로그램은 각 플랫폼에 대해 기본적으로 컴파일되어야 하며 올바른 위치에 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-198">The data processing extensions that are installed with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] must be compiled natively for each platform and installed in the correct locations.</span></span> <span data-ttu-id="3e857-199">또한 사용자 지정 데이터 공급자나 표준 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자를 등록하는 경우 이러한 공급자는 해당 플랫폼에 대해 기본적으로 컴파일되어야 하며 적절한 위치에 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-199">If you register a custom data provider or a standard [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider, it needs to be compiled natively for the appropriate platform and installed the appropriate locations.</span></span> <span data-ttu-id="3e857-200">32비트 플랫폼에서 실행하는 경우 데이터 공급자는 32비트 플랫폼에 대해 컴파일되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-200">If you are running on a 32-bit platform, the data provider must be compiled for a 32-bit platform.</span></span> <span data-ttu-id="3e857-201">64비트 플랫폼에서 실행하는 경우에는 데이터 공급자가 64비트 플랫폼에 대해 컴파일되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-201">If you are running on a 64-bit platform, the data provider must be compiled for the 64-bit platform.</span></span> <span data-ttu-id="3e857-202">64비트 인터페이스로 래핑된 32비트 데이터 공급자를 64비트 플랫폼에서 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3e857-202">You cannot use a 32-bit data provider wrapped with 64-bit interfaces on a 64 bit platform.</span></span> <span data-ttu-id="3e857-203">설치된 플랫폼에서 데이터 공급자가 작동할지 여부에 대한 자세한 내용은 해당 타사 소프트웨어를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3e857-203">Check your third-party software for information about whether the data provider will work on the installed platform.</span></span> <span data-ttu-id="3e857-204">데이터 공급자 및 플랫폼 지원에 대한 자세한 내용은 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e857-204">For more information about data providers and platform support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e857-205">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e857-205">See Also</span></span>  
 <span data-ttu-id="3e857-206">[보고서 서버 구성 및 관리&#40;SSRS 기본 모드&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="3e857-206">[Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="3e857-207">[데이터 처리 확장 프로그램 구현](../extensions/data-processing/implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="3e857-207">[Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="3e857-208">[Reporting Services 구성 파일](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="3e857-208">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="3e857-209">Reporting Services의 코드 액세스 보안</span><span class="sxs-lookup"><span data-stu-id="3e857-209">Code Access Security in Reporting Services</span></span>](../extensions/secure-development/code-access-security-in-reporting-services.md)  
  
  
