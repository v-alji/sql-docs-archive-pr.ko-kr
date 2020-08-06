---
title: 데이터 처리 확장 프로그램 개요 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], about extensions
ms.assetid: 1d652605-9313-4c75-98b4-ba4dcbbb222d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e589d3a4e090aee52d2590c0b2ccff435c2321a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649939"
---
# <a name="data-processing-extensions-overview"></a><span data-ttu-id="065f8-102">데이터 처리 확장 프로그램 개요</span><span class="sxs-lookup"><span data-stu-id="065f8-102">Data Processing Extensions Overview</span></span>
  <span data-ttu-id="065f8-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 데이터 처리 확장 프로그램을 통해 데이터 원본에 연결하고 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-103">Data processing extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enable you to connect to a data source and retrieve data.</span></span> <span data-ttu-id="065f8-104">이 프로그램은 데이터 원본과 데이터 세트을 연결하는 역할도 합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-104">They also serve as a bridge between a data source and a dataset.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="065f8-105">데이터 처리 확장 프로그램은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 데이터 공급자 인터페이스의 하위 집합을 본떠서 만든 것입니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-105">data processing extensions are modeled after a subset of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data provider interfaces.</span></span>

 <span data-ttu-id="065f8-106">다음 표에서는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에 포함된 데이터 처리 확장 프로그램을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-106">The following table lists the data processing extensions included with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

|<span data-ttu-id="065f8-107">데이터 처리 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="065f8-107">Data processing extension</span></span>|<span data-ttu-id="065f8-108">Description</span><span class="sxs-lookup"><span data-stu-id="065f8-108">Description</span></span>|
|-------------------------------|-----------------|
|<span data-ttu-id="065f8-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]용 데이터 처리 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="065f8-109">Data processing extension for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span></span>|<span data-ttu-id="065f8-110">.NET Framework Data Provider for SQL Server를 사용하여 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]에 연결하고 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-110">Uses the .NET Framework Data Provider for SQL Server to connect to and retrieve data from the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>|
|<span data-ttu-id="065f8-111">OLE DB용 데이터 처리 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="065f8-111">Data processing extension for OLE DB</span></span>|<span data-ttu-id="065f8-112">.NET Framework Data Provider for OLE DB를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-112">Uses the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="065f8-113">이 확장 프로그램을 사용하여 보고서 서버에서 OLE DB 공급자를 가진 데이터 원본을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-113">With this extension, the report server can query any data source that has an OLE DB provider.</span></span>|
|<span data-ttu-id="065f8-114">Oracle용 데이터 처리 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="065f8-114">Data processing extension for Oracle</span></span>|<span data-ttu-id="065f8-115">.NET Framework Data Provider for Oracle을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-115">Uses the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="065f8-116">이 확장 프로그램을 사용하여 보고서 서버에서 Oracle 클라이언트 연결 소프트웨어를 통해 Oracle 데이터 원본에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-116">With this extension, the report server can access Oracle data sources through Oracle client connectivity software.</span></span>|
|<span data-ttu-id="065f8-117">ODBC용 데이터 처리 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="065f8-117">Data processing extension for ODBC</span></span>|<span data-ttu-id="065f8-118">.NET Framework Data Provider for ODBC를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-118">Uses the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="065f8-119">이 확장 프로그램을 사용하여 보고서 서버에서 ODBC 드라이버가 있는 임의의 데이터베이스의 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-119">With this extension, the report server can access data in any database for which there is an ODBC driver.</span></span>|

 <span data-ttu-id="065f8-120">[!INCLUDE[ssRS](../../../includes/ssrs.md)] 데이터 처리 API를 사용하여 사용자 지정 데이터 처리를 보고서 서버에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-120">You can use the [!INCLUDE[ssRS](../../../includes/ssrs.md)] data processing API to add custom data processing to your report server.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="065f8-121">는 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]의 데이터 공급자를 기본적으로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-121">has built-in support for data providers in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="065f8-122">이미 완전한 데이터 공급자를 구현한 경우에는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램을 구현할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-122">If you have already implemented a full data provider, you do not need to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension.</span></span> <span data-ttu-id="065f8-123">하지만 보안 연결 자격 증명이나 서버 쪽 집계와 같은 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005 특정 기능을 포함시키려면 데이터 공급자 확장을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-123">However, you should consider extending your data provider to include functionality specific to [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005, which includes secure connection credentials and server-side aggregates.</span></span>

 <span data-ttu-id="065f8-124">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에 포함된 각 데이터 처리 확장 프로그램에서는 공통된 인터페이스 집합을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-124">Each of the data processing extensions included with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses a common set of interfaces.</span></span> <span data-ttu-id="065f8-125">이로 인해 모든 확장 프로그램에서 비슷한 기능이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-125">This ensures that each extension implements comparable functionality.</span></span>

 <span data-ttu-id="065f8-126">고유의 데이터 원본에 맞는 데이터 처리 확장 프로그램을 개발하거나, 인터페이스를 사용하여 공통 데이터베이스 인프라에 데이터 처리 층을 하나 더 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-126">You can develop data processing extensions for your own data sources, or you can use the interfaces to add an additional layer of data processing to common database infrastructures.</span></span> <span data-ttu-id="065f8-127">사용자 지정 데이터 처리 확장 프로그램을 배포하여 조직의 기존 보고서 서버에 완벽한 데이터 통합을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-127">You can deploy your custom data processing extensions to enable seamless integration of data into the existing report servers in your organization.</span></span> <span data-ttu-id="065f8-128">뿐만 아니라 소비자에게 제공하는 사용자 지정 보고 제품군의 일부로 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-128">You can also use them as part of a custom reporting suite that you provide to your consumers.</span></span>

 <span data-ttu-id="065f8-129">![데이터 처리 확장 프로그램 아키텍처](../../media/bk-dataprocess-extensions.gif "데이터 처리 확장 프로그램 아키텍처") Reporting Services 데이터 처리 확장 프로그램 아키텍처</span><span class="sxs-lookup"><span data-stu-id="065f8-129">![Data processing extension architecture](../../media/bk-dataprocess-extensions.gif "Data processing extension architecture") Reporting Services data processing extension architecture</span></span>

 <span data-ttu-id="065f8-130">사용자 지정 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램을 구현하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-130">The advantages to implementing a custom [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension include:</span></span>

-   <span data-ttu-id="065f8-131">데이터 액세스 아키텍처가 단순해지므로 유지 관리가 더 편리하고 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-131">A simplified data access architecture, often with better maintainability and improved performance.</span></span>

-   <span data-ttu-id="065f8-132">확장 프로그램 특정 기능을 소비자에게 직접 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-132">The ability to directly expose extension-specific functionality to consumers.</span></span>

-   <span data-ttu-id="065f8-133">소비자에게 제공되는 특정 인터페이스를 통해 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 내에서 데이터 원본에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-133">A specific interface for your consumers to access your data source within [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>

## <a name="data-extension-process-flow"></a><span data-ttu-id="065f8-134">데이터 확장 프로세스 흐름</span><span class="sxs-lookup"><span data-stu-id="065f8-134">Data Extension Process Flow</span></span>
 <span data-ttu-id="065f8-135">사용자 지정 데이터 확장 프로그램을 개발하기 전에 보고서 서버에서 데이터 확장 프로그램을 사용하여 어떻게 데이터를 처리하는지 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-135">Before developing your custom data extension, you should understand how the report server uses data extensions to process data.</span></span> <span data-ttu-id="065f8-136">또한 보고서 서버에서 호출되는 생성자와 메서드에 대해서도 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-136">You should also understand the constructors and methods that are called by the report server.</span></span>

 <span data-ttu-id="065f8-137">![데이터 처리 확장 프로그램에 대 한 프로세스 흐름](../../media/bk-ext-01.gif "데이터 처리 확장 프로그램의 프로세스 흐름") 보고서 서버에서 호출 하는 데이터 확장 프로그램의 단계별 프로세스 흐름</span><span class="sxs-lookup"><span data-stu-id="065f8-137">![Process flow for data processing extension](../../media/bk-ext-01.gif "Process flow for data processing extension") The step-by-step process flow of a data extension that is called by the report server</span></span>

 <span data-ttu-id="065f8-138">이 그림은 다음과 같은 이벤트 시퀀스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-138">The illustration shows the following sequence of events:</span></span>

1.  <span data-ttu-id="065f8-139">보고서 서버에서 연결 개체를 만들고 보고서와 연관된 연결 문자열 및 자격 증명을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-139">The report server creates a connection object and passes in the connection string and credentials associated with the report.</span></span>

2.  <span data-ttu-id="065f8-140">보고서의 명령 텍스트를 사용하여 명령 개체가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-140">The command text of the report is used to create a command object.</span></span> <span data-ttu-id="065f8-141">이 프로세스에서 데이터 처리 확장 프로그램에는 명령 텍스트의 구문을 분석하고 명령에 대한 매개 변수를 만드는 코드가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-141">In the process, the data processing extension may include code that parses the command text and creates any parameters for the command.</span></span>

3.  <span data-ttu-id="065f8-142">명령 개체와 매개 변수가 처리되면 데이터 판독기가 생성되어 결과 집합이 반환되고 보고서 서버에서 보고서 데이터를 보고서 레이아웃과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-142">Once the command object and any parameters are processed, a data reader is generated that returns a result set and enables the report server to associate the report data with the report layout.</span></span>

## <a name="developer-requirements"></a><span data-ttu-id="065f8-143">개발자 요구 사항</span><span class="sxs-lookup"><span data-stu-id="065f8-143">Developer Requirements</span></span>
 <span data-ttu-id="065f8-144">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램을 개발하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-144">Developing a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension requires you to have:</span></span>

-   <span data-ttu-id="065f8-145">보고서 디자이너 또는 보고서 서버가 설치된 배포 컴퓨터가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-145">A deployment computer with Report Designer or a report server installed.</span></span>

-   <span data-ttu-id="065f8-146">이상 [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK (소프트웨어 개발 키트)가 설치 된 개발 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="065f8-146">A development computer with [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] or above, or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Software Development Kit (SDK) installed.</span></span>

-   <span data-ttu-id="065f8-147">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 기능을 자세히 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-147">An in-depth understanding of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] features and capabilities.</span></span>

-   <span data-ttu-id="065f8-148">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 아키텍처, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 데이터 공급자, ADO.NET 데이터 집합 개체 및 공통 인터페이스에 대해 자세히 알고 있어야 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="065f8-148">An in-depth understanding of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] architecture, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] data providers, ADO.NET DataSet objects, and the common [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] interfaces.</span></span>

-   <span data-ttu-id="065f8-149">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual c # 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .net과 같은 언어의 개발 환경</span><span class="sxs-lookup"><span data-stu-id="065f8-149">Development experience in a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] language such as [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="065f8-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="065f8-150">See Also</span></span>
 <span data-ttu-id="065f8-151">[확장 라이브러리 Reporting Services](../reporting-services-extension-library.md) [Reporting Services 확장](../reporting-services-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="065f8-151">[Reporting Services Extensions](../reporting-services-extensions.md) [Reporting Services Extension Library](../reporting-services-extension-library.md)</span></span>


