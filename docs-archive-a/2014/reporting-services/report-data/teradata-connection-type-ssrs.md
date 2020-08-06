---
title: Teradata 연결 형식(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 73e51c82a824bb607d75c2e78cfc9b0f37476e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653215"
---
# <a name="teradata-connection-type-ssrs"></a><span data-ttu-id="f14ae-102">Teradata 연결 형식(SSRS)</span><span class="sxs-lookup"><span data-stu-id="f14ae-102">Teradata Connection Type (SSRS)</span></span>
  <span data-ttu-id="f14ae-103">보고서에 Teradata 관계형 데이터베이스의 데이터를 포함하려면 Teradata 유형의 보고서 데이터 원본을 기반으로 하는 데이터 세트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-103">To include data from a Teradata relational database in your report, you must have a dataset that is based on a report data source of type Teradata.</span></span> <span data-ttu-id="f14ae-104">이 기본 제공 데이터 원본 유형은 .NET Managed Provider for Teradata 데이터 처리 확장 프로그램을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-104">This built-in data source type is based on the .NET Managed Provider for Teradata data processing extension.</span></span>  
  
 <span data-ttu-id="f14ae-105">이 항목의 정보를 사용하여 데이터 원본을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="f14ae-106">단계별 지침은 [데이터 연결이 나 데이터 원본 &#40;추가 및 확인 보고서 작성기 및 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f14ae-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="f14ae-107">연결 문자열</span><span class="sxs-lookup"><span data-stu-id="f14ae-107">Connection String</span></span>  
 <span data-ttu-id="f14ae-108">데이터 원본 연결에 사용할 자격 증명 및 연결 정보는 데이터베이스 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="f14ae-108">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="f14ae-109">다음 연결 문자열 예에서는 유니코드를 사용하는 IP 주소로 지정된 서버의 Teradata 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-109">The following connection string example specifies a Teradata database on the server specified with an IP address:</span></span>  
  
```  
data source=<IP Address>  
```  
  
 <span data-ttu-id="f14ae-110">연결 문자열 예제는 [보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f14ae-110">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="f14ae-111">자격 증명</span><span class="sxs-lookup"><span data-stu-id="f14ae-111">Credentials</span></span>  
 <span data-ttu-id="f14ae-112">쿼리를 실행하거나 보고서를 로컬로 미리 보거나 보고서 서버의 보고서를 미리 보려면 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-112">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="f14ae-113">보고서를 게시한 후 보고서를 보고서 서버에서 실행할 때 데이터를 검색할 수 있는 권한이 유효하도록 데이터 원본에 대한 자격 증명을 변경해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-113">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="f14ae-114">자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하거나 [보고서 작성기에서 자격 증명을 지정](../specify-credentials-in-report-builder.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="f14ae-114">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  

##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="f14ae-115">주의</span><span class="sxs-lookup"><span data-stu-id="f14ae-115">Remarks</span></span>  
 <span data-ttu-id="f14ae-116">Teradata 데이터 원본을 연결하려면 시스템 관리자가 Teradata 데이터베이스에서 데이터를 검색할 수 있도록 하는 .NET Data Provider for Teradata 버전을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-116">Before you can connect a Teradata data source, the system administrator must have installed the version of the .NET Data Provider for Teradata that supports retrieving data from the Teradata database.</span></span> <span data-ttu-id="f14ae-117">이 데이터 공급자는 보고서 작성기와 동일한 컴퓨터뿐 아니라 보고서 서버에도 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-117">This data provider must be installed on the same computer as Report Builder and also on the report server.</span></span>  
  
 <span data-ttu-id="f14ae-118">이 데이터 공급자는 일부 보고서 배달 모드만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-118">Not all report delivery modes are supported by this data provider.</span></span> <span data-ttu-id="f14ae-119">이 데이터 처리 확장 프로그램에서는 데이터 기반 구독을 통한 보고서 배달이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-119">Delivering reports through data-driven subscriptions is not supported for this data processing extension.</span></span> <span data-ttu-id="f14ae-120">자세한 내용은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)의 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 설명서에서 [구독자 데이터에 외부 데이터 원본 사용&#40;데이터 기반 구독&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f14ae-120">For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  

##  <a name="report-models"></a><a name="Models"></a> <span data-ttu-id="f14ae-121">보고서 모델</span><span class="sxs-lookup"><span data-stu-id="f14ae-121">Report Models</span></span>  
 <span data-ttu-id="f14ae-122">Teradata 데이터 원본에 기반을 둔 보고서 모델에서 데이터 세트를 만들려면 모델이 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 모델 디자이너에서 디자인되어 보고서 서버에 게시되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-122">To create a dataset from a report model that is based on a Teradata data source, the model must be designed in Model Designer in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and published on a report server.</span></span>  

##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="f14ae-123">관련 단원</span><span class="sxs-lookup"><span data-stu-id="f14ae-123">Related Sections</span></span>  
 <span data-ttu-id="f14ae-124">설명서의 다음 섹션에서는 보고서 데이터에 대한 깊이 있는 개념 정보를 제공하며, 데이터와 관련된 보고서 부분을 정의, 사용자 지정 및 사용하는 방법을 절차적인 측면에서 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-124">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="f14ae-125">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-125">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="f14ae-126">보고서의 데이터 액세스에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-126">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="f14ae-127">보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="f14ae-127">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="f14ae-128">데이터 연결 및 데이터 원본에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-128">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="f14ae-129">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f14ae-129">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="f14ae-130">포함된 데이터 세트 및 공유 데이터 세트에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-130">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="f14ae-131">데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f14ae-131">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="f14ae-132">데이터 세트 쿼리에 의해 생성되는 필드 컬렉션에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-132">Provides information about the field collection that is generated by the dataset query.</span></span>  
  
 <span data-ttu-id="f14ae-133">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에 있는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 설명서의 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="f14ae-133">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="f14ae-134">각 데이터 확장 프로그램의 플랫폼 및 버전 지원에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-134">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 [<span data-ttu-id="f14ae-135">.NET Framework Data Provider for Teradata에서 SQL Server 2008 Reporting Services 사용</span><span class="sxs-lookup"><span data-stu-id="f14ae-135">Using SQL Server 2008 Reporting Services with the .NET Framework Data Provider for Teradata</span></span>](https://go.microsoft.com/fwlink/?LinkID=130848)  
 <span data-ttu-id="f14ae-136">이 데이터 확장 프로그램을 사용하는 방법에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f14ae-136">Provides detailed information about working with this data extension.</span></span>  

## <a name="see-also"></a><span data-ttu-id="f14ae-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f14ae-137">See Also</span></span>  
 <span data-ttu-id="f14ae-138">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="f14ae-138">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="f14ae-139">[데이터 필터링, 그룹화 및 정렬 &#40;보고서 작성기 및 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f14ae-139">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f14ae-140">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f14ae-140">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
