---
title: '방법: 데이터 처리 확장 프로그램을 보고서 서버에 배포 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d606096b9f2060d3cf5b9cea1f95a5345e592383
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741615"
---
# <a name="how-to-deploy-a-data-processing-extension-to-a-report-server"></a><span data-ttu-id="28e02-102">방법: 보고서 서버에 데이터 처리 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="28e02-102">How to: Deploy a Data Processing Extension to a Report Server</span></span>
  <span data-ttu-id="28e02-103">보고서 서버는 렌더링된 보고서의 데이터 검색 및 처리를 위해 데이터 처리 확장 프로그램을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-103">Report servers use data processing extensions for retrieving and processing data in rendered reports.</span></span> <span data-ttu-id="28e02-104">데이터 처리 확장 프로그램 어셈블리를 보고서 서버에 프라이빗 어셈블리로 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-104">You should deploy your data processing extension assembly to a report server as a private assembly.</span></span> <span data-ttu-id="28e02-105">또한 보고서 서버 구성 파일 RSReportServer.config에서 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-105">You also need to make an entry in the report server configuration file, RSReportServer.config.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="28e02-106">프로시저</span><span class="sxs-lookup"><span data-stu-id="28e02-106">Procedures</span></span>  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a><span data-ttu-id="28e02-107">데이터 처리 확장 프로그램 어셈블리를 배포하려면</span><span class="sxs-lookup"><span data-stu-id="28e02-107">To deploy a data processing extension assembly</span></span>  
  
1.  <span data-ttu-id="28e02-108">준비 위치에서 데이터 처리 확장 프로그램을 사용할 보고서 서버의 bin 디렉터리로 어셈블리를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-108">Copy your assembly from your staging location to the bin directory of the report server on which you want to use the data processing extension.</span></span> <span data-ttu-id="28e02-109">보고서 서버 bin 디렉터리의 기본 위치 는%ProgramFiles%\Microsoft SQL Server \ MSRS10_50입니다. \<*Instance Name*> \Reporting Services\reportserver\bin입니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-109">The default location of the report server bin directory is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<*Instance Name*>\Reporting Services\ReportServer\bin.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="28e02-110">이 단계를 수행하면 SQL Server의 최신 인스턴스로 업그레이드할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-110">This step will prevent an upgrade to a newer instance of SQL Server.</span></span> <span data-ttu-id="28e02-111">자세한 내용은 [Upgrade and Migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="28e02-111">For more information, see [Upgrade and Migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
2.  <span data-ttu-id="28e02-112">어셈블리 파일이 복사된 후 RSReportServer.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-112">After the assembly file is copied, open the RSReportServer.config file.</span></span> <span data-ttu-id="28e02-113">RSReportServer.config 파일은 ReportServer 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-113">The RSReportServer.config file is located in the ReportServer directory.</span></span> <span data-ttu-id="28e02-114">구성 파일에서 데이터 처리 확장 프로그램 어셈블리 파일에 대한 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-114">You need to make an entry in the configuration file for your data processing extension assembly file.</span></span> <span data-ttu-id="28e02-115">구성 파일은 Visual Studio 또는 메모장과 같은 간단한 텍스트 편집기를 사용하여 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-115">You can open the configuration file with Visual Studio or a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="28e02-116">RSReportServer.config 파일에서 `Data` 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-116">Locate the `Data` element in the RSReportServer.config file.</span></span> <span data-ttu-id="28e02-117">새로 만든 데이터 처리 확장 프로그램에 대한 항목이 다음 위치에 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-117">An entry for your newly created data processing extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="28e02-118">데이터 처리 확장 프로그램에 대한 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-118">Add an entry for your data processing extension.</span></span> <span data-ttu-id="28e02-119">항목에 `Extension` 및 `Name`에 대한 값과 함께 `Type` 요소가 포함되어야 하며 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-119">Your entry should include an `Extension` element with values for `Name` and `Type` and might look like the following:</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     <span data-ttu-id="28e02-120">`Name`의 값은 데이터 처리 확장 프로그램의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-120">The value for `Name` is the unique name of the data processing extension.</span></span> <span data-ttu-id="28e02-121">`Type`의 값은 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 및 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 인터페이스를 구현하는 클래스의 정규화된 네임스페이스에 대한 항목과 그 다음에 어셈블리의 이름(.dll 파일 확장명 포함 안 함)이 따라오는 형태가 포함되며 쉼표로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-121">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IExtension> and <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> interfaces, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="28e02-122">기본적으로 데이터 처리 확장 프로그램은 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-122">By default, data processing extensions are visible.</span></span> <span data-ttu-id="28e02-123">보고서 관리자와 같은 사용자 인터페이스에서 확장 프로그램을 숨기려면 `Visible` 특성을 `Extension` 요소에 추가하고 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-123">To hide an extension from user interfaces, such as Report Manager, add a `Visible` attribute to the `Extension` element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="28e02-124">확장 프로그램에 대해 `FullTrust` 권한을 부여하는 사용자 지정 어셈블리에 대한 코드 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-124">Add a code group for your custom assembly that grants `FullTrust` permission for your extension.</span></span> <span data-ttu-id="28e02-125">기본적 으로%ProgramFiles%\Microsoft SQL Server<MSRS10_50에 있는 rssrvpolicy.config 파일에 코드 그룹을 추가 하 여이 작업을 수행할 수 있습니다 \\ . \<*Instance Name*> \Reporting Services\reportserver</span><span class="sxs-lookup"><span data-stu-id="28e02-125">You do this by adding the code group to the rssrvpolicy.config file located by default in %ProgramFiles%\Microsoft SQL Server\\<MSRS10_50.\<*Instance Name*>\Reporting Services\ReportServer.</span></span> <span data-ttu-id="28e02-126">코드 그룹은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-126">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="28e02-127">URL 멤버 자격은 데이터 처리 확장 프로그램에 대해 선택할 수 있는 다수의 멤버 자격 조건 중 하나일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-127">URL membership is only one of many membership conditions you might choose for your data processing extension.</span></span> <span data-ttu-id="28e02-128">[!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 코드 액세스 보안에 대한 자세한 내용은 [보안 개발&#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="28e02-128">For more information about code access security in [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md).</span></span>  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="28e02-129">배포 확인</span><span class="sxs-lookup"><span data-stu-id="28e02-129">Verifying the Deployment</span></span>  
 <span data-ttu-id="28e02-130">웹 서비스 <xref:ReportService2010.ReportingService2010.ListExtensions%2A> 메서드를 사용하여 데이터 처리 확장 프로그램이 보고서 서버에 성공적으로 배포되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-130">You can verify whether your data processing extension was deployed successfully to the report server by using the Web service <xref:ReportService2010.ReportingService2010.ListExtensions%2A> method.</span></span> <span data-ttu-id="28e02-131">보고서 관리자를 열고 확장 프로그램이 사용 가능한 데이터 원본 목록에 포함되어 있는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28e02-131">You can also open Report Manager and verify that your extension is included in the list of available data sources.</span></span> <span data-ttu-id="28e02-132">보고서 관리자 및 데이터 원본에 대한 자세한 내용은 [공유 데이터 원본 만들기, 수정 및 삭제&#40;SSRS&#41;](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="28e02-132">For more information about Report Manager and data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e02-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="28e02-133">See Also</span></span>  
 <span data-ttu-id="28e02-134">[데이터 처리 확장 프로그램 배포](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="28e02-134">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="28e02-135">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="28e02-135">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="28e02-136">[데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="28e02-136">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="28e02-137">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="28e02-137">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
