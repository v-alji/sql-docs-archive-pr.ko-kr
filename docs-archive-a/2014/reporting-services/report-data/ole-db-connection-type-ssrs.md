---
title: OLE DB 연결 형식(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d00cb13b-e1c2-4300-a195-3da1430a2df1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66d4074d6bf90a23814b13da8836fd0594e8cf1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742867"
---
# <a name="ole-db-connection-type-ssrs"></a><span data-ttu-id="17479-102">OLE DB 연결 형식(SSRS)</span><span class="sxs-lookup"><span data-stu-id="17479-102">OLE DB Connection Type (SSRS)</span></span>
  <span data-ttu-id="17479-103">OLE DB 데이터 공급자의 데이터를 포함하려면 OLE DB 유형의 보고서 데이터 원본에 기초하는 데이터 세트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-103">To include data from an OLE DB data provider, you must have a dataset that is based on a report data source of type OLE DB.</span></span> <span data-ttu-id="17479-104">이 기본 제공 데이터 원본 유형은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] OLE DB 데이터 처리 확장 프로그램을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-104">This built-in data source type is based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] OLE DB data processing extension.</span></span>  
  
 <span data-ttu-id="17479-105">OLE DB는 클라이언트가 다양한 데이터 공급자에 연결할 수 있도록 하는 데이터 액세스 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="17479-105">OLE DB is a data access technology that enables clients to connect to a variety of data providers.</span></span> <span data-ttu-id="17479-106">데이터 원본 유형 OLE DB를 선택한 후에는 특정 데이터 공급자를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-106">After you select the data source type OLE DB, you must select a specific data provider.</span></span> <span data-ttu-id="17479-107">매개 변수 및 자격 증명과 같은 기능에 대한 지원은 선택하는 데이터 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="17479-107">Support for features such as parameters and credentials are dependent on the data provider that you select.</span></span>  
  
 <span data-ttu-id="17479-108">이 항목의 정보를 사용하여 데이터 원본을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17479-108">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="17479-109">단계별 지침은 [데이터 연결이 나 데이터 원본 &#40;추가 및 확인 보고서 작성기 및 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17479-109">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="17479-110">연결 문자열</span><span class="sxs-lookup"><span data-stu-id="17479-110">Connection String</span></span>  
 <span data-ttu-id="17479-111">OLE DB 데이터 처리 확장 프로그램의 연결 문자열은 원하는 데이터 공급자에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="17479-111">The connection string for the OLE DB data processing extension depends on the data provider that you want.</span></span> <span data-ttu-id="17479-112">일반적인 연결 문자열에는 데이터 공급자가 지원하는 이름/값 쌍이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="17479-112">A typical connection string contains name/value pairs that are supported by the data provider.</span></span> <span data-ttu-id="17479-113">예를 들어 다음 연결 문자열은 OLE DB provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 및 AdventureWorks 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-113">For example, the following connection string specifies the OLE DB provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and the AdventureWorks database:</span></span>  
  
```  
Provider=SQLNCLI10.1;Data Source=server; Initial Catalog=AdventureWorks  
```  
  
 <span data-ttu-id="17479-114">사용하는 연결 문자열은 연결하려는 외부 데이터 원본에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="17479-114">The connection string that you use depends on the external data source that you are connecting to.</span></span> <span data-ttu-id="17479-115">데이터 공급자별 연결 문자열 속성을 설정하려면 **데이터 원본 속성** 대화 상자의 **일반** 페이지에서 **빌드** 단추를 클릭하여 **연결 속성** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="17479-115">To set connection string properties specific to a data provider, from the **General** page of the **Data Source Properties** dialog box, click the **Build** button to open the **Connection Properties** dialog box.</span></span> <span data-ttu-id="17479-116">**데이터 연결 속성** 대화 상자를 통해 확장된 데이터 원본 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-116">Set extended data source properties through the **Data Link Properties** dialog box.</span></span>  
  
 <span data-ttu-id="17479-117">연결 문자열의 예제는 [보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17479-117">For examples of connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="17479-118">자격 증명</span><span class="sxs-lookup"><span data-stu-id="17479-118">Credentials</span></span>  
 <span data-ttu-id="17479-119">쿼리를 실행하거나 보고서를 로컬로 미리 보거나 보고서 서버의 보고서를 미리 보려면 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-119">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="17479-120">보고서를 게시한 후 보고서를 보고서 서버에서 실행할 때 데이터를 검색할 수 있는 권한이 유효하도록 데이터 원본에 대한 자격 증명을 변경해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17479-120">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="17479-121">자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하거나 [보고서 작성기에서 자격 증명을 지정](../specify-credentials-in-report-builder.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="17479-121">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
###### <a name="special-characters-in-a-password"></a><span data-ttu-id="17479-122">암호의 특수 문자</span><span class="sxs-lookup"><span data-stu-id="17479-122">Special Characters in a Password</span></span>  
 <span data-ttu-id="17479-123">암호를 입력하라는 메시지를 표시하거나 연결 문자열에 암호를 포함하도록 OLE DB 데이터 원본을 구성한 경우 사용자가 문장 부호와 같은 특수 문자가 포함된 암호를 입력하면 일부 기본 데이터 원본 드라이버에서 해당 특수 문자의 유효성을 검사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17479-123">If you configure the OLE DB data source to prompt for a password or to include the password in the connection string, and a user enters the password with special characters such as punctuation marks, some underlying data source drivers cannot validate the special characters.</span></span> <span data-ttu-id="17479-124">보고서 처리 시 "올바른 암호가 아닙니다" 메시지가 나타나면 이 문제 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17479-124">When you process the report, the message "Not a valid password" may indicate this problem.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17479-125">연결 문자열에 암호와 같은 로그인 정보를 추가하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17479-125">It is recommended that you do not add login information such as passwords to the connection string.</span></span> <span data-ttu-id="17479-126">보고서 작성기는 **데이터 원본** 대화 상자에서 자격 증명을 입력하는 데 사용할 수 있는 별도의 탭을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-126">Report Builder provides a separate tab on the **Data Source** dialog box that you can use to enter credentials.</span></span>  
  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="17479-127">매개 변수</span><span class="sxs-lookup"><span data-stu-id="17479-127">Parameters</span></span>  
 <span data-ttu-id="17479-128">일부 OLE DB 공급자는 명명되지 않은 매개 변수 및 이름이 지정되지 않은 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-128">Some OLE DB providers support unnamed parameters and not named parameters.</span></span> <span data-ttu-id="17479-129">매개 변수는 쿼리의 자리 표시자를 사용하여 위치로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="17479-129">Parameters are passed by position by using a placeholder in the query.</span></span> <span data-ttu-id="17479-130">자리 표시자 문자는 데이터 공급자가 지원하는 구문에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="17479-130">The placeholder character is determined by the syntax that is supported by the data provider.</span></span>  
  
 
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="17479-131">주의</span><span class="sxs-lookup"><span data-stu-id="17479-131">Remarks</span></span>  
 <span data-ttu-id="17479-132">OLEDB는 특정 데이터 원본에 사용할 데이터 공급자를 만들기 위한 기본 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="17479-132">OLEDB is a native technology for building data providers for specific data sources.</span></span> <span data-ttu-id="17479-133">OLEDB는 COM(구성 요소 개체 모델) 인터페이스를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-133">OLEDB is based on COM (Component Object Model) interfaces.</span></span> <span data-ttu-id="17479-134">OLEDB는 ODBC보다 뒤에 나오고 ADO.NET 데이터 공급자 이전에 나온 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="17479-134">OLEDB is a later technology than ODBC and earlier than ADO.NET data providers.</span></span> <span data-ttu-id="17479-135">OLEDB 공급자는 다른 모든 COM 구성 요소와 마찬가지로 운영 체제에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="17479-135">OLEDB data providers are registered with the operating system like any other COM component.</span></span> <span data-ttu-id="17479-136">OLEDB 데이터 공급자는 Microsoft 및 타사 공급업체를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17479-136">OLEDB data providers are available from Microsoft and third party vendors.</span></span> <span data-ttu-id="17479-137">Microsoft는 ODBC 드라이버에 대한 통신을 연결하는 OLEDB 데이터 공급자인 MSDASQL도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-137">Microsoft also provides MSDASQL, an OLEDB data provider that bridges communication to ODBC drivers.</span></span> <span data-ttu-id="17479-138">자세한 내용은 [ODBC 연결 형식&#40;SSRS&#41;](odbc-connection-type-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17479-138">For more information, see [ODBC Connection Type &#40;SSRS&#41;](odbc-connection-type-ssrs.md).</span></span>  
  
 <span data-ttu-id="17479-139">원하는 데이터를 성공적으로 검색하려면 데이터 공급자가 지원하는 쿼리 구문을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-139">To successfully retrieve the data that you want, you must provide query syntax that is supported by the data provider.</span></span> <span data-ttu-id="17479-140">매개 변수 지원은 데이터 공급자에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="17479-140">Parameter support varies by data provider.</span></span> <span data-ttu-id="17479-141">자세한 내용은 선택한 데이터 공급자와 관련된 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="17479-141">For more information, see topics that are specific to the data provider that you select.</span></span> <span data-ttu-id="17479-142">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="17479-142">For example:</span></span>  
  
-   [<span data-ttu-id="17479-143">Analysis Services OLE DB 공급자&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="17479-143">Analysis Services OLE DB Provider &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../analysis-services/dev-guide/analysis-services-ole-db-provider-analysis-services-multidimensional-data.md)  
  
-   [<span data-ttu-id="17479-144">.NET Framework Data Provider for Oracle 사용(Using the .NET Framework Data Provider for Oracle)</span><span class="sxs-lookup"><span data-stu-id="17479-144">Using the .NET Framework Data Provider for Oracle</span></span>](https://go.microsoft.com/fwlink/?LinkId=112314)  
  
-   [<span data-ttu-id="17479-145">SQL Server Native Client&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="17479-145">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
 <span data-ttu-id="17479-146">특정 OLE DB 데이터 공급자에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설명서에서 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="17479-146">For more information about specific OLE DB data providers, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="17479-147">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="17479-147">How-To Topics</span></span>  
 <span data-ttu-id="17479-148">이 섹션에서는 데이터 연결, 데이터 원본 및 데이터 세트를 사용하는 방법을 단계별로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-148">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="17479-149">데이터 연결이 나 데이터 원본 &#40;보고서 작성기 및 SSRS를 추가 하 고 확인&#41;</span><span class="sxs-lookup"><span data-stu-id="17479-149">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="17479-150">공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="17479-150">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="17479-151">데이터 세트에 필터 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="17479-151">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="17479-152">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="17479-152">Related Sections</span></span>  
 <span data-ttu-id="17479-153">설명서의 다음 섹션에서는 보고서 데이터에 대한 깊이 있는 개념 정보를 제공하며, 데이터와 관련된 보고서 부분을 정의, 사용자 지정 및 사용하는 방법을 절차적인 측면에서 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-153">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="17479-154">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-154">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="17479-155">보고서의 데이터 액세스에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-155">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="17479-156">보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="17479-156">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="17479-157">데이터 연결 및 데이터 원본에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-157">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="17479-158">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="17479-158">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="17479-159">포함된 데이터 세트 및 공유 데이터 세트에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-159">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="17479-160">데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="17479-160">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="17479-161">쿼리에 의해 생성되는 데이터 세트 필드 컬렉션에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-161">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="17479-162">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에 있는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설명서의 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="17479-162">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="17479-163">각 데이터 확장 프로그램의 플랫폼 및 버전 지원에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="17479-163">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="17479-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17479-164">See Also</span></span>  
 <span data-ttu-id="17479-165">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="17479-165">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="17479-166">[데이터 필터링, 그룹화 및 정렬 &#40;보고서 작성기 및 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="17479-166">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="17479-167">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="17479-167">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
