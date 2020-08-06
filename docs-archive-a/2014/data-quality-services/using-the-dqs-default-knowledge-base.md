---
title: DQS 기본 기술 자료 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3261c7af28bb5710ede203d1fe27c6540286e9f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647842"
---
# <a name="using-the-dqs-default-knowledge-base"></a><span data-ttu-id="efb2f-102">DQS 기본 기술 자료 사용</span><span class="sxs-lookup"><span data-stu-id="efb2f-102">Using the DQS Default Knowledge Base</span></span>
  <span data-ttu-id="efb2f-103">이 항목에서는 DQS( **)와 함께 설치되는 기본 기술 자료인**DQS 데이터 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-103">This topic describes the default knowledge base, **DQS Data**, which is installed with [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="efb2f-104">DQS 데이터는 다음과 같은 도메인이 포함된 미리 작성된 기본 기술 자료입니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-104">This is a pre-built default knowledge base that contains the following domains:</span></span>  
  
-   <span data-ttu-id="efb2f-105">**국가/지역**: 각 위치에 대해 규칙에 따른 긴 이름(국가/지역에 따라 지정되는 공식 이름)과 짧은 이름(목록, 지도 등에 사용되는 일반 이름), 2자 약어, 3자 약어 및 3자리 코드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-105">**Country/Region**: Contains the conventional long (official name as designated by the country/region ) and short names (common name used in lists, on maps, etc. ), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="efb2f-106">선행 값은 긴 국가 이름으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-106">Leading value is set to the long country name.</span></span>  
  
-   <span data-ttu-id="efb2f-107">**국가/지역(선행 3자)**: 각 위치에 대해 규칙에 따른 긴 이름(국가/지역에 따라 지정되는 공식 이름)과 짧은 이름(목록, 지도 등에 사용되는 일반 이름), 2자 약어, 3자 약어 및 3자리 코드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-107">**Country/Region (three-letter leading)**: Contains the conventional long (official name as designated by the country/region) and short names (common name used in lists, on maps, and so on), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="efb2f-108">선행 값은 국가의 3자 약어로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-108">Leading values is set to County three-letter abbreviation.</span></span>  
  
-   <span data-ttu-id="efb2f-109">**국가/지역(선행 2자)**: 각 위치에 대해 규칙에 따른 긴 이름(국가/지역에 따라 지정되는 공식 이름)과 짧은 이름(목록, 지도 등에 사용되는 일반 이름), 2자 약어, 3자 약어 및 3자리 코드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-109">**Country/Region (two-letter leading)**: Contains the conventional long (official name as designated by the country/region ) and short names (common name used in lists, on maps, etc. ), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="efb2f-110">선행 값은 국가의 2자 약어로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-110">Leading value is set to the Country two-letter abbreviation.</span></span>  
  
-   <span data-ttu-id="efb2f-111">**미국 - 지방**: 미국의 지방 목록을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-111">**US - Counties**: Contains a list of US counties.</span></span>  
  
-   <span data-ttu-id="efb2f-112">**미국 - 성**: 2000년 인구 조사에서 100번 이상 나타난 성의 목록을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-112">**US - Last Name**: Contains a list of last names (surnames) occurring 100 or more times in the Census 2000.</span></span>  
  
-   <span data-ttu-id="efb2f-113">**미국 - 위치**: 2010년 인구 조사에서 추출된 50개 주, 콜롬비아 특별구 및 푸에르토리코의 위치 목록을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-113">**US - Places**: Contains a list of places for the 50 states, the District of Columbia, and Puerto Rico extracted from the Census 2010.</span></span>  
  
-   <span data-ttu-id="efb2f-114">**미국 - 주**: 미국의 각 주에 대해 규칙에 따른 긴 이름(공식 이름)과 2자 약어를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-114">**US - State**: Contains the conventional long (official) name and two-letter abbreviation for each state in US.</span></span> <span data-ttu-id="efb2f-115">선행 값은 규칙에 따른 주 이름으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-115">Leading value is set to the conventional state name.</span></span>  
  
-   <span data-ttu-id="efb2f-116">**미국 - 주(선행 2자)**: 미국의 각 주에 대해 규칙에 따른 긴 이름(공식 이름)과 2자 약어를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-116">**US - State (2-letter heading)**: Contains the conventional long (official) name and two-letter abbreviation for each state in US.</span></span> <span data-ttu-id="efb2f-117">선행 값은 주 이름의 2자 약어로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-117">Leading value is set to the two-letter abbreviation state name.</span></span>  
  
## <a name="using-the-default-knowledge-base"></a><span data-ttu-id="efb2f-118">기본 기술 자료 사용</span><span class="sxs-lookup"><span data-stu-id="efb2f-118">Using the Default Knowledge Base</span></span>  
 <span data-ttu-id="efb2f-119">다음과 같은 방법으로 기본 DQS 기술 자료인 DQS 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-119">You can use the default DQS knowledge base, DQS Data, in the following ways:</span></span>  
  
-   <span data-ttu-id="efb2f-120">먼저 DQS에서 새 기술 자료를 만들 필요 없이 기본 기술 자료를 사용하여 정리 데이터 품질 프로젝트를 빠르게 시작하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-120">Quickly start and run a cleansing data quality project using the default knowledge base without first having to create a new knowledge base in DQS.</span></span>  
  
-   <span data-ttu-id="efb2f-121">기본 기술 자료에서 도메인 관리, 기술 자료 검색 또는 일치 정책 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-121">Run the Domain Management, Knowledge Discovery, or Matching Policy activities on the default knowledge base.</span></span> <span data-ttu-id="efb2f-122">이렇게 하려면 **Data Quality Client Home Screen** 에서 [기술 자료 열기](../../2014/data-quality-services/data-quality-client-home-screen.md)를 클릭하고 **기술 자료 열기** 화면에서 **DQS 데이터** 기술 자료를 선택한 다음 **작업 선택** 영역에서 필요한 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-122">To do so, click **Open Knowledge Base** in the [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md), select the **DQS Data** knowledge base in the **Open Knowledge Base** screen, and then select the required activity in the **Select Activity** area.</span></span> <span data-ttu-id="efb2f-123">**다음** 을 클릭하여 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-123">Click **Next** to proceed.</span></span>  
  
-   <span data-ttu-id="efb2f-124">기본 기술 자료를 사용하여 새 기술 자료를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-124">Create a new knowledge base using the default knowledge base.</span></span> <span data-ttu-id="efb2f-125">기존 기술 자료를 토대로 기술 자료를 만들려면 [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="efb2f-125">To create a knowledge base from an existing knowledge base, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md).</span></span>  
  
-   <span data-ttu-id="efb2f-126">[Integration Services의 DQS 정리 구성 요소](https://go.microsoft.com/fwlink/?LinkId=238830) 및 [Excel용 Master Data Services 추가 기능](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)에서 기술 자료를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="efb2f-126">Use it in the [DQS Cleansing component in Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) and [Master Data Services Add-in for Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb2f-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="efb2f-127">See Also</span></span>  
 [<span data-ttu-id="efb2f-128">DQS 기술 자료 및 도메인</span><span class="sxs-lookup"><span data-stu-id="efb2f-128">DQS Knowledge Bases and Domains</span></span>](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
