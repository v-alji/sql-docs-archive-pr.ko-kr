---
title: Analysis Services |에서 사용 되는 도구 및 응용 프로그램 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36bbcbca4323a9ce327b5fa89398dfb20da319c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647281"
---
# <a name="tools-and-applications-used-in-analysis-services"></a><span data-ttu-id="f15fd-102">Analysis Services에서 사용되는 도구 및 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="f15fd-102">Tools and applications used in Analysis Services</span></span>
  <span data-ttu-id="f15fd-103">Analysis Services 모델을 개발하고 Analysis Services 인스턴스에서 연결된 데이터베이스를 관리하기 위해 필요한 도구 및 애플리케이션을 찾으세요.</span><span class="sxs-lookup"><span data-stu-id="f15fd-103">Find the tools and applications you'll need for building Analysis Services models, and managing the associated databases on an Analysis Services instance.</span></span>

## <a name="analysis-services-model-designers"></a><span data-ttu-id="f15fd-104">Analysis Services 모델 디자이너</span><span class="sxs-lookup"><span data-stu-id="f15fd-104">Analysis Services Model Designers</span></span>
 <span data-ttu-id="f15fd-105">테이블 형식 및 다차원 모델은 Visual Studio 셸에서 작성된 솔루션의 프로젝트 템플릿에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-105">Tabular and multidimensional models are created from project templates in a solution built inside the Visual Studio shell.</span></span> <span data-ttu-id="f15fd-106">프로젝트 템플릿은 Analysis Services 솔루션을 구성하는 모델, 큐브, 차원 및 역할을 만들기 위해 디자이너를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-106">The project template provides the designers for creating models, cubes, dimensions, and roles that comprise an Analysis Services solution.</span></span>

### <a name="download-sql-server-data-tools-for-business-intelligence-ssdt-bi"></a><span data-ttu-id="f15fd-107">SQL Server Data Tools for Business Intelligence(SSDT-BI) 다운로드</span><span class="sxs-lookup"><span data-stu-id="f15fd-107">Download SQL Server Data Tools for Business Intelligence (SSDT-BI)</span></span>
 <span data-ttu-id="f15fd-108">이전에는 BIDS(Business Intelligence Development Studio)라고 하던 SSDT-BI([!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] for Business Intelligence)는 Analysis Services 모델, Reporting Services 보고서 및 Integration Services 패키지를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] for Business Intelligence (SSDT-BI), previously known as Business Intelligence Development Studio (BIDS), is used to create Analysis Services models, Reporting Services reports, and Integration Services packages.</span></span> <span data-ttu-id="f15fd-109">다음 위치에서 SSDT-BI를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-109">You can download SSDT-BI from the following locations:</span></span>

-   [<span data-ttu-id="f15fd-110">Visual Studio 2013용 SSDT-BI 다운로드</span><span class="sxs-lookup"><span data-stu-id="f15fd-110">Download SSDT-BI for Visual Studio 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=396526)

-   [<span data-ttu-id="f15fd-111">Visual Studio 2012용 SSDT-BI 다운로드</span><span class="sxs-lookup"><span data-stu-id="f15fd-111">Download SSDT-BI for Visual Studio 2012</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=273673)

 <span data-ttu-id="f15fd-112">이전 버전의 SSDT-BI 또는 BIDS가 컴퓨터에 설치되어 있는 경우 최신 버전이 이전 버전과 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-112">If you have a prior version of SSDT-BI or BIDS installed on your computer, the newer version is installed side-by-side the previous version.</span></span> <span data-ttu-id="f15fd-113">특정 버전의 서버에 연결된 프로젝트 및 솔루션을 수정할 수 있도록 하기 위해 최신 및 이전 버전의 디자인 도구를 단일 워크스테이션에서 실행하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-113">It's common to run newer and older versions of the design tools on a single workstation so that you can modify projects and solutions tied to specific versions of the server.</span></span>

> [!NOTE]
>  <span data-ttu-id="f15fd-114">Visual Studio 2012 및 Visual Studio 2013 버전의 SSDT를 다운로드할 수 있는 몇몇 사이트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-114">There are several download sites for the Visual Studio 2012 and Visual Studio 2013 versions of SSDT.</span></span> <span data-ttu-id="f15fd-115">대부분의 다운로드에는 BI 프로젝트 템플릿이 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-115">Most do not include the BI project templates.</span></span> <span data-ttu-id="f15fd-116">위의 링크를 사용하면 올바른 버전을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-116">Using the links above will get you the correct version.</span></span> <span data-ttu-id="f15fd-117">비즈니스 인텔리전스 프로젝트 템플릿 폴더가 표시 되는 경우 올바른 버전의 SSDT가 있는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-117">You'll know that you have the correct version of SSDT-BI if you see the Business Intelligence project templates folder.</span></span> <span data-ttu-id="f15fd-118">이 폴더에는 Analysis Services, Reporting Services 및 Integration Services의 프로젝트 템플릿이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-118">This folder contains the project templates for Analysis Services, Reporting Services and Integration Services.</span></span> <span data-ttu-id="f15fd-119">SSDT-BI를 설치한 방법에 따라 SQL Server 데이터베이스의 추가 프로젝트 템플릿이 표시될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-119">Depending on how you installed SSDT-BI, you might also see an additional project template for SQL Server databases.</span></span>

 <span data-ttu-id="f15fd-120">![SSDT의 새 프로젝트 템플릿](media/ssdt-biprojects.png "SSDT의 새 프로젝트 템플릿")</span><span class="sxs-lookup"><span data-stu-id="f15fd-120">![New Project templates in SSDT](media/ssdt-biprojects.png "New Project templates in SSDT")</span></span>

## <a name="administrative-tools"></a><span data-ttu-id="f15fd-121">관리 도구</span><span class="sxs-lookup"><span data-stu-id="f15fd-121">Administrative tools</span></span>

### <a name="sql-server-management-studio"></a><span data-ttu-id="f15fd-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f15fd-122">SQL Server Management Studio</span></span>
 <span data-ttu-id="f15fd-123">Management Studio는 Analysis Services를 비롯하여 모든 SQL Server 기능의 기본 관리 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-123">Management Studio is the primary administration tool for all SQL Server features, including Analysis Services.</span></span> <span data-ttu-id="f15fd-124">SQL Server Management Studio는 선택적 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-124">SQL Server Management Studio is an optional component.</span></span> <span data-ttu-id="f15fd-125">Windows Server 2012의 앱 페이지에서 다른 SQL Server 애플리케이션에 표시되지 않는 경우 SQL Server 설치 프로그램을 실행하여 설치에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-125">If you don't see it with other SQL Server applications on the Apps page in Windows Server 2012, run SQL Server Setup to add it to your installation.</span></span>

### <a name="sql-server-profiler"></a><span data-ttu-id="f15fd-126">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="f15fd-126">SQL Server Profiler</span></span>
 <span data-ttu-id="f15fd-127">공식적으로는 더 이상 사용되지 않는 SQL Server Profiler를 통해 연결, MDX 쿼리 실행 및 기타 서버 작동을 간편하게 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-127">Although it's officially deprecated, SQL Server Profiler provides an easy way to monitor connections, MDX query execution, and other server operations.</span></span> <span data-ttu-id="f15fd-128">SQL Server Profiler는 기본적으로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-128">SQL Server Profiler is installed by default.</span></span> <span data-ttu-id="f15fd-129">Windows Server 2012의 앱에서 SQL Server 애플리케이션과 함께 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-129">You can find it with SQL Server applications on Apps in Windows Server 2012.</span></span>

### <a name="powershell"></a><span data-ttu-id="f15fd-130">PowerShell</span><span class="sxs-lookup"><span data-stu-id="f15fd-130">PowerShell</span></span>
 <span data-ttu-id="f15fd-131">PowerShell 명령을 사용하여 많은 관리 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-131">You can use PowerShell commands to perform many administrative tasks.</span></span> <span data-ttu-id="f15fd-132">자세한 내용은 [Analysis Services PowerShell](analysis-services-powershell.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f15fd-132">See [Analysis Services PowerShell](analysis-services-powershell.md) for more information.</span></span>

### <a name="community-and-third-party-tools"></a><span data-ttu-id="f15fd-133">커뮤니티 및 타사 도구</span><span class="sxs-lookup"><span data-stu-id="f15fd-133">Community and Third-party tools</span></span>
 <span data-ttu-id="f15fd-134">커뮤니티 코드 샘플은 [Analysis Services codeplex 페이지](https://sqlsrvanalysissrvcs.codeplex.com/) (영문)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f15fd-134">Check the [Analysis Services codeplex page](https://sqlsrvanalysissrvcs.codeplex.com/) for community code samples.</span></span> <span data-ttu-id="f15fd-135">[포럼](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) 은 Analysis Services를 지 원하는 타사 도구에 대 한 권장 사항을 검색할 때 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f15fd-135">[Forums](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) can be helpful when seeking recommendations for third-party tools that support Analysis Services.</span></span>
