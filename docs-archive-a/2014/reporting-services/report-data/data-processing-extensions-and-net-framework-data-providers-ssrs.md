---
title: 데이터 처리 확장 프로그램과 .NET Framework 데이터 공급자(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
- report data [Report Builder], accessing
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fd84af68af54b165c75317280bc19bb23da53366
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729116"
---
# <a name="data-processing-extensions-and-net-framework-data-providers-ssrs"></a><span data-ttu-id="4c65e-102">데이터 처리 확장 프로그램과 .NET Framework 데이터 공급자(SSRS)</span><span class="sxs-lookup"><span data-stu-id="4c65e-102">Data Processing Extensions and .NET Framework Data Providers (SSRS)</span></span>
  <span data-ttu-id="4c65e-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]와 함께 설치되는 구성 요소로, 특정 유형의 데이터 원본에서 데이터를 검색하고 보고서 디자인 및 보고서 처리를 지원하기 위한 추가 기능을 제공하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-103">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extension is a component installed with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], designed to retrieve data from a specific type of data source and to provide extra functionality to support report design and report processing.</span></span> <span data-ttu-id="4c65e-104">먼저 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자는 특정 유형의 데이터 원본에서 데이터를 검색하고 수정할 수 있는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] System.Data <xref:System.Data> 또는 타사 제공 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-104">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider is a component available from [!INCLUDE[msCoName](../../includes/msconame-md.md)] or third-party sources that supports <xref:System.Data> interfaces that allow you to retrieve and to modify data from a specific type of data source.</span></span>  
  
## <a name="understanding-a-data-processing-extension"></a><span data-ttu-id="4c65e-105">데이터 처리 확장 프로그램 이해</span><span class="sxs-lookup"><span data-stu-id="4c65e-105">Understanding a Data Processing Extension</span></span>  
 <span data-ttu-id="4c65e-106">먼저 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램은 <xref:System.Data> 인터페이스의 하위 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-106">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extension supports a subset of the <xref:System.Data> interfaces.</span></span> <span data-ttu-id="4c65e-107">데이터 처리 확장 프로그램에는 데이터 원본에 대한 읽기 전용 액세스 권한만 필요하므로 쓰기 및 업데이트용 인터페이스는 구현되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-107">Data processing extensions require only read-only access to a data source, so the interfaces for write and update are not implemented.</span></span> <span data-ttu-id="4c65e-108">각 데이터 처리 확장 프로그램은 보고서 처리를 지원하는 사용자 지정 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-108">Each data processing extension can provide custom features to support report processing.</span></span> <span data-ttu-id="4c65e-109">예를 들어 데이터 처리 확장 프로그램은 다음과 같은 유형의 기능을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-109">For example, a data processing extension might support the following types of features:</span></span>  
  
-   <span data-ttu-id="4c65e-110">연결 문자열과 별도로 자격 증명 관리</span><span class="sxs-lookup"><span data-stu-id="4c65e-110">Managing credentials separately from the connection string</span></span>  
  
-   <span data-ttu-id="4c65e-111">다중값 매개 변수 지원</span><span class="sxs-lookup"><span data-stu-id="4c65e-111">Supporting multivalue parameters</span></span>  
  
-   <span data-ttu-id="4c65e-112">데이터 원본에서 계산된 서버 집계 검색</span><span class="sxs-lookup"><span data-stu-id="4c65e-112">Retrieving server aggregates, which are calculated on the data source</span></span>  
  
-   <span data-ttu-id="4c65e-113">데이터 원본에서 데이터 속성 및 데이터 값 검색</span><span class="sxs-lookup"><span data-stu-id="4c65e-113">Retrieving data properties as well as data values from the data source</span></span>  
  
## <a name="understanding-a-data-provider"></a><span data-ttu-id="4c65e-114">데이터 공급자 이해</span><span class="sxs-lookup"><span data-stu-id="4c65e-114">Understanding a Data Provider</span></span>  
 <span data-ttu-id="4c65e-115">먼저 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자(드라이버)는 데이터 원본의 데이터를 읽고, 쓰고, 업데이트하기 위한 표준 <xref:System.Data> 인터페이스 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-115">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider (sometimes known as a driver) supports a standard set of <xref:System.Data> interfaces for reading, writing, and updating data on a data source.</span></span> <span data-ttu-id="4c65e-116">데이터 공급자는 특정 유형의 데이터 원본에 사용 가능한 데이터 처리 확장 프로그램이 없는 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-116">A data provider can be used when there is no data processing extension available for a specific type of data source.</span></span> <span data-ttu-id="4c65e-117">많은 타사 표준 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-117">Many third-party standard [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data providers are available.</span></span>  
  
 <span data-ttu-id="4c65e-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에는 확장 가능한 데이터 공급자 아키텍처가 있으므로 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램에서 제공하는 추가 기능을 포함하는 사용자 지정 데이터 처리 확장 프로그램을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-118">Because [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] has an extensible data provider architecture, you can build a custom data processing extension to include the extra functionality supplied by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data processing extensions.</span></span> <span data-ttu-id="4c65e-119">자세한 내용은 [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4c65e-119">For more information, see [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md).</span></span> <span data-ttu-id="4c65e-120">타사 데이터 처리 확장 프로그램의 경우 타사 데이터 처리 확장 프로그램과 함께 제공되는 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4c65e-120">For third-party data processing extensions, see the documentation that comes with the third-party data processing extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c65e-121">먼저 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자나 사용자 지정 데이터 처리 확장 프로그램을 설치하고 등록해야만 데이터 원본의 데이터에 액세스하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-121">A [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider or custom data processing extension must be installed and registered before it can be used to access data from a data source.</span></span> <span data-ttu-id="4c65e-122">데이터 처리 확장 프로그램은 보고서를 작성하기 위한 보고 클라이언트와 게시된 보고서를 보기 위한 보고서 서버에 모두 설치 및 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-122">The data processing extension must be installed and registered both on the reporting client to author the report and on the report server to view the published report.</span></span> <span data-ttu-id="4c65e-123">모든 데이터 공급자가 서버 환경에서 작동하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="4c65e-123">Not all data providers are designed to work in a server environment.</span></span> <span data-ttu-id="4c65e-124">자세한 내용은 [표준 .NET Framework 데이터 공급자 등록&#40;SSRS&#41;](register-a-standard-net-framework-data-provider-ssrs.md) 및 [데이터 처리 확장 프로그램 배포](../extensions/data-processing/deploying-a-data-processing-extension.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4c65e-124">For more information, see [Register a Standard .NET Framework Data Provider &#40;SSRS&#41;](register-a-standard-net-framework-data-provider-ssrs.md).and [Deploying a Data Processing Extension](../extensions/data-processing/deploying-a-data-processing-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c65e-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4c65e-125">See Also</span></span>  
 <span data-ttu-id="4c65e-126">[데이터 처리 확장 프로그램 개요](../extensions/data-processing/data-processing-extensions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4c65e-126">[Data Processing Extensions Overview](../extensions/data-processing/data-processing-extensions-overview.md) </span></span>  
 [<span data-ttu-id="4c65e-127">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4c65e-127">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
