---
title: ODBC 연결 형식(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 24163866-f37a-4c38-982e-c3d79bf64d4c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b2bf5ee6f3eeaa38796e4fa41f3cc0634fd128cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647451"
---
# <a name="odbc-connection-type-ssrs"></a><span data-ttu-id="c528c-102">ODBC 연결 형식(SSRS)</span><span class="sxs-lookup"><span data-stu-id="c528c-102">ODBC Connection Type (SSRS)</span></span>
  <span data-ttu-id="c528c-103">ODBC 데이터 공급자의 데이터를 포함하려면 ODBC 유형의 보고서 데이터 원본에 기초하는 데이터 세트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-103">To include data from an ODBC data provider, you must have a dataset that is based on a report data source of type ODBC.</span></span> <span data-ttu-id="c528c-104">이 기본 제공 데이터 원본 형식은 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ODBC 데이터 처리 확장 프로그램을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ODBC data processing extension.</span></span>  
  
 <span data-ttu-id="c528c-105">이 항목의 정보를 사용하여 데이터 원본을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="c528c-106">단계별 지침은 [데이터 연결이 나 데이터 원본 &#40;추가 및 확인 보고서 작성기 및 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c528c-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="c528c-107">연결 문자열</span><span class="sxs-lookup"><span data-stu-id="c528c-107">Connection String</span></span>  
 <span data-ttu-id="c528c-108">ODBC 데이터 처리 확장 프로그램의 연결 문자열은 원하는 ODBC 드라이버에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-108">The connection string for the ODBC data processing extension depends on the ODBC driver that you want.</span></span> <span data-ttu-id="c528c-109">일반적인 연결 문자열에는 드라이버가 지원하는 이름/값 쌍이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-109">A typical connection string contains name/value pairs that are supported by the driver.</span></span> <span data-ttu-id="c528c-110">예를 들어 다음 연결 문자열은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 및 AdventureWorks 데이터베이스에 대한 ODBC 드라이버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-110">For example, the following connection string specifies the ODBC driver for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and the AdventureWorks database:</span></span>  
  
```  
Driver={SQL Server Native Client 10.0};Server=server;Database=AdventureWorks;Trusted_Connection=yes;  
```  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="c528c-111">자격 증명</span><span class="sxs-lookup"><span data-stu-id="c528c-111">Credentials</span></span>  
 <span data-ttu-id="c528c-112">쿼리를 실행하거나 보고서를 로컬로 미리 보거나 보고서 서버의 보고서를 미리 보려면 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-112">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="c528c-113">보고서를 게시한 후 보고서를 보고서 서버에서 실행할 때 데이터를 검색할 수 있는 권한이 유효하도록 데이터 원본에 대한 자격 증명을 변경해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-113">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="c528c-114">암호를 입력하라는 메시지를 표시하거나 연결 문자열에 암호를 포함하도록 ODBC 데이터 원본을 구성한 경우 사용자가 문장 부호와 같은 특수 문자가 포함된 암호를 입력하면 일부 기본 데이터 원본 드라이버에서 해당 특수 문자의 유효성을 검사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-114">If you configure your ODBC data source to prompt for a password or to include the password in the connection string, and a user enters the password with special characters such as punctuation marks, some underlying data source drivers cannot validate the special characters.</span></span> <span data-ttu-id="c528c-115">보고서 처리 시 "올바른 암호가 아닙니다" 메시지가 나타나면 이 문제 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-115">When you process the report, the message "Not a valid password" might indicate this problem.</span></span> <span data-ttu-id="c528c-116">암호를 변경하는 것이 불가능한 경우 데이터베이스 관리자와 협력하여 보고서 서버에서 해당 자격 증명을 시스템 ODBC DSN(데이터 원본 이름)의 일부로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-116">If changing the password is impractical, you can work with your database administrator to store the appropriate credentials on the report server as part of a system ODBC data source name (DSN).</span></span> <span data-ttu-id="c528c-117">자세한 내용은 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서의 "OdbcConnection.ConnectionString"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c528c-117">For more information, see "OdbcConnection.ConnectionString" in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c528c-118">연결 문자열에 암호와 같은 로그인 정보를 추가하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-118">It is recommended that you do not add login information such as passwords to the connection string.</span></span> <span data-ttu-id="c528c-119">보고서 작성기는 **데이터 원본** 대화 상자에서 자격 증명을 입력하는 데 사용할 수 있는 별도의 탭을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-119">Report Builder provides a separate tab on the **Data Source** dialog box that you can use to enter credentials.</span></span>  
  
 <span data-ttu-id="c528c-120">자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하거나 [보고서 작성기에서 자격 증명을 지정](../specify-credentials-in-report-builder.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="c528c-120">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="c528c-121">주의</span><span class="sxs-lookup"><span data-stu-id="c528c-121">Remarks</span></span>  
 <span data-ttu-id="c528c-122">ODBC는 OLEDB에 앞서 도입된 초기 데이터 액세스 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-122">ODBC is an early data access technology that preceded OLEDB.</span></span> <span data-ttu-id="c528c-123">ODBC는 관계형 데이터 원본만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-123">ODBC supports only relational data sources.</span></span> <span data-ttu-id="c528c-124">ODBC 데이터 공급자를 *드라이버*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-124">ODBC data providers are called *drivers*.</span></span> <span data-ttu-id="c528c-125">ODBC 드라이버는 Microsoft 및 타사 공급업체가 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-125">ODBC drivers are provided by Microsoft and third party vendors.</span></span> <span data-ttu-id="c528c-126">예를 들어 Microsoft Office는 Office 파일 형식에 연결되는 ODBC 드라이버를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-126">For example, Microsoft Office installs ODBC drivers that connect to Office file formats.</span></span>  
  
 <span data-ttu-id="c528c-127">ODBC 연결 문자열을 작성할 수 있으려면 먼저 ODBC 드라이버가 설치되어 있고 컴퓨터 또는 시스템 DSN을 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-127">Before you can build an ODBC connection string, you must have ODBC drivers installed and build a machine or system DSN.</span></span> <span data-ttu-id="c528c-128">원하는 데이터를 성공적으로 검색하려면 드라이버가 지원하는 쿼리 구문을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-128">To successfully retrieve the data that you want, you must provide query syntax that is supported by the driver.</span></span> <span data-ttu-id="c528c-129">매개 변수 지원은 드라이버에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-129">Parameter support varies by driver.</span></span> <span data-ttu-id="c528c-130">자세한 내용은 선택한 드라이버와 관련된 항목을 참조하세요(예: [SQL Server Native Client&#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)).</span><span class="sxs-lookup"><span data-stu-id="c528c-130">For more information, see topics that are specific to the driver that you select, for example, [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md).</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="c528c-131">플랫폼 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="c528c-131">Platform and Version Information</span></span>  
 <span data-ttu-id="c528c-132">특정 ODBC 데이터 공급자에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설명서에서 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="c528c-132">For more information about specific ODBC data providers, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> <span data-ttu-id="c528c-133">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="c528c-133">How-To Topics</span></span>  
 <span data-ttu-id="c528c-134">이 섹션에서는 데이터 연결, 데이터 원본 및 데이터 세트를 사용하는 방법을 단계별로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-134">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="c528c-135">데이터 연결이 나 데이터 원본 &#40;보고서 작성기 및 SSRS를 추가 하 고 확인&#41;</span><span class="sxs-lookup"><span data-stu-id="c528c-135">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="c528c-136">공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c528c-136">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="c528c-137">데이터 세트에 필터 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c528c-137">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="c528c-138">관련 단원</span><span class="sxs-lookup"><span data-stu-id="c528c-138">Related Sections</span></span>  
 <span data-ttu-id="c528c-139">설명서의 다음 섹션에서는 보고서 데이터에 대한 깊이 있는 개념 정보를 제공하며, 데이터와 관련된 보고서 부분을 정의, 사용자 지정 및 사용하는 방법을 절차적인 측면에서 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-139">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="c528c-140">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-140">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="c528c-141">보고서의 데이터 액세스에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-141">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="c528c-142">보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="c528c-142">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="c528c-143">데이터 연결 및 데이터 원본에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-143">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="c528c-144">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c528c-144">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="c528c-145">포함된 데이터 세트 및 공유 데이터 세트에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-145">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="c528c-146">데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c528c-146">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="c528c-147">쿼리에 의해 생성되는 데이터 세트 필드 컬렉션에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-147">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="c528c-148">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에 있는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설명서의 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="c528c-148">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="c528c-149">각 데이터 확장 프로그램의 플랫폼 및 버전 지원에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c528c-149">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="c528c-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c528c-150">See Also</span></span>  
 <span data-ttu-id="c528c-151">[보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="c528c-151">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="c528c-152">[데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c528c-152">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c528c-153">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c528c-153">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
