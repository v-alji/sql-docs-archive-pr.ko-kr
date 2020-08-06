---
title: '방법: 데이터 처리 확장 프로그램을 보고서 디자이너에 배포 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: 3614e601-004e-4a16-8388-836ffd67e9dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56bd56e9d8eeeeff1781f22b42cf0eb1ce706fa4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741599"
---
# <a name="how-to-deploy-a-data-processing-extension-to-report-designer"></a><span data-ttu-id="e5954-102">방법: 보고서 디자이너에 데이터 처리 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="e5954-102">How to: Deploy a Data Processing Extension to Report Designer</span></span>
  <span data-ttu-id="e5954-103">보고서 디자이너에서는 보고서를 디자인하는 동안 데이터 검색 및 처리를 위해 데이터 처리 확장 프로그램을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-103">Report Designer uses data processing extensions for retrieving and processing data while you are designing reports.</span></span> <span data-ttu-id="e5954-104">데이터 처리 확장 프로그램 어셈블리를 보고서 디자이너에 프라이빗 어셈블리로 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-104">You should deploy your data processing extension assembly to Report Designer as a private assembly.</span></span> <span data-ttu-id="e5954-105">또한 보고서 디자이너 구성 파일인 RSReportDesigner.config에서 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-105">You also need to make an entry in the Report Designer configuration file, RSReportDesigner.config.</span></span>  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a><span data-ttu-id="e5954-106">데이터 처리 확장 프로그램 어셈블리를 배포하려면</span><span class="sxs-lookup"><span data-stu-id="e5954-106">To deploy a data processing extension assembly</span></span>  
  
1.  <span data-ttu-id="e5954-107">준비 위치에서 보고서 디자이너 디렉터리로 어셈블리를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-107">Copy your assembly from your staging location to the Report Designer directory.</span></span> <span data-ttu-id="e5954-108">보고서 디자이너 디렉터리의 기본 위치는 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies입니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-108">The default location of the Report Designer directory is C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
2.  <span data-ttu-id="e5954-109">어셈블리 파일이 복사된 후 RSReportDesigner.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-109">After the assembly file is copied, open the RSReportDesigner.config file.</span></span> <span data-ttu-id="e5954-110">RSReportDesigner.config 파일도 보고서 디자이너 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-110">The RSReportDesigner.config file is also located in the Report Designer directory.</span></span> <span data-ttu-id="e5954-111">구성 파일에서 데이터 처리 확장 프로그램 어셈블리 파일에 대한 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-111">You need to make an entry in the configuration file for your data processing extension assembly file.</span></span> <span data-ttu-id="e5954-112">구성 파일은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]에서 열거나 메모장과 같은 간단한 텍스트 편집기를 사용하여 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-112">You can open the configuration file with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or with a simple text editor, such as Notepad.</span></span>  
  
3.  <span data-ttu-id="e5954-113">RSReportDesigner.config 파일에서 **Data** 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-113">Locate the **Data** element in the RSReportDesigner.config file.</span></span> <span data-ttu-id="e5954-114">새로 만든 데이터 처리 확장 프로그램에 대한 항목이 다음 위치에 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-114">An entry for your newly created data processing extension should be made in the following location:</span></span>  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  <span data-ttu-id="e5954-115">, 및 특성에 대 한 값이 포함 된 **extension** 요소를 포함 하는 데이터 처리 확장 프로그램에 대 한 항목을 추가 `Name` `Type` `Visible` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-115">Add an entry for your data processing extension which includes an **Extension** element with values for the `Name`, `Type`, and `Visible` attributes.</span></span> <span data-ttu-id="e5954-116">항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-116">Your entry might look like the following:</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, AssemblyName" />  
    ```  
  
     <span data-ttu-id="e5954-117">`Name`의 값은 데이터 처리 확장 프로그램의 고유한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-117">The value for `Name` is the unique name of the data processing extension.</span></span> <span data-ttu-id="e5954-118">`Type`의 값은 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 및 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 인터페이스를 구현하는 클래스의 정규화된 네임스페이스에 대한 항목과 그 다음에 어셈블리의 이름(.dll 파일 확장명 포함 안 함)이 따라오는 형태가 포함되며 쉼표로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-118">The value for `Type` is a comma-separated list that includes an entry for the fully qualified namespace of your class that implements the <xref:Microsoft.ReportingServices.Interfaces.IExtension> and <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> interfaces, followed by the name of your assembly (not including the .dll file extension).</span></span> <span data-ttu-id="e5954-119">기본적으로 데이터 처리 확장 프로그램은 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-119">By default, data processing extensions are visible.</span></span> <span data-ttu-id="e5954-120">보고서 디자이너와 같은 사용자 인터페이스에서 확장을 숨기려면 `Visible` 특성을 **extension** 요소에 추가 하 고로 설정 `false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-120">To hide an extension from user interfaces, such as Report Designer, add a `Visible` attribute to the **Extension** element, and set it to `false`.</span></span>  
  
5.  <span data-ttu-id="e5954-121">마지막으로 확장 프로그램에 대해 **FullTrust** 권한을 부여하는 사용자 지정 어셈블리에 대한 코드 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-121">Finally, add a code group for your custom assembly that grants **FullTrust** permission for your extension.</span></span> <span data-ttu-id="e5954-122">기본 위치가 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies인 rspreviewpolicy.config 파일에 코드 그룹을 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-122">You do this by adding the code group to the rspreviewpolicy.config file located by default in C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span> <span data-ttu-id="e5954-123">코드 그룹은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-123">Your code group might look like the following:</span></span>  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 <span data-ttu-id="e5954-124">URL 멤버 자격은 데이터 처리 확장 프로그램에 대해 선택할 수 있는 다수의 멤버 자격 조건 중 하나일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-124">URL membership is only one of many membership conditions you might choose for your data processing extension.</span></span> <span data-ttu-id="e5954-125">[!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)]의 코드 액세스 보안에 대한 자세한 내용은 [보안 개발&#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5954-125">For more information about code access security in [!INCLUDE[ssRSversion2005](../../../includes/ssrsversion2005-md.md)], see [Secure Development &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md)</span></span>  
  
## <a name="generic-query-designer"></a><span data-ttu-id="e5954-126">일반 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="e5954-126">Generic Query Designer</span></span>  
 <span data-ttu-id="e5954-127">보고서 디자이너는 사용자 지정 데이터 처리 확장 프로그램에서 사용할 수 있는 일반 쿼리 디자이너를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-127">Report Designer provides a generic query designer that you can use with custom data processing extensions.</span></span> <span data-ttu-id="e5954-128">이 디자이너는 쿼리 창과 결과 창의 두 창으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-128">This designer consists of two panes: a query pane and a results pane.</span></span> <span data-ttu-id="e5954-129">일반 디자이너를 사용하여 그래픽 인터페이스에서 지원되지 않는 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-129">You can use the generic designer to write queries that are not supported by the graphical interface.</span></span> <span data-ttu-id="e5954-130">일반 쿼리 디자이너는 그래픽 쿼리 디자이너와 달리 쿼리 구문을 확인하거나 쿼리를 재구성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-130">Unlike the graphical query designer, the generic query designer does not check query syntax or restructure the query.</span></span>  
  
#### <a name="to-enable-the-generic-query-designer-for-a-custom-extension"></a><span data-ttu-id="e5954-131">사용자 지정 확장 프로그램에 대해 일반 쿼리 디자이너를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="e5954-131">To enable the generic query designer for a custom extension</span></span>  
  
-   <span data-ttu-id="e5954-132">RSReportDesigner.config 파일의 **Designer** 요소 아래에 다음 항목을 추가 하 여 특성을 `Name` 이전 항목에서 제공한 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-132">Add the following entry to the RSReportDesigner.config file under the **Designer** element, replacing the `Name` attribute with the name that you provided in previous entries.</span></span>  
  
    ```  
    <Extension Name="ExtensionName" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
## <a name="verifying-the-deployment"></a><span data-ttu-id="e5954-133">배포 확인</span><span class="sxs-lookup"><span data-stu-id="e5954-133">Verifying the Deployment</span></span>  
 <span data-ttu-id="e5954-134">배포를 확인하려면 먼저 로컬 컴퓨터에서 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 인스턴스를 모두 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-134">Before you can verify deployment, you must close all instances of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] on your local computer.</span></span> <span data-ttu-id="e5954-135">현재 세션을 모두 종료한 후 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]에서 새 보고서 프로젝트를 만들어 데이터 처리 확장 프로그램이 보고서 디자이너에 배포되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-135">After you have ended all current sessions, you can verify whether your data processing extension was deployed successfully to Report Designer by creating a new report project in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="e5954-136">이때 확장 프로그램이 보고서에 대한 새 데이터 집합을 만들 때 사용 가능한 데이터 원본 유형 목록에 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5954-136">Your extension should be included in the list of available data source types when you create a new data set for your report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5954-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5954-137">See Also</span></span>  
 <span data-ttu-id="e5954-138">[데이터 처리 확장 프로그램 배포](deploying-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="e5954-138">[Deploying a Data Processing Extension](deploying-a-data-processing-extension.md) </span></span>  
 <span data-ttu-id="e5954-139">[Reporting Services 확장 프로그램](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="e5954-139">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="e5954-140">[데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="e5954-140">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="e5954-141">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="e5954-141">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
