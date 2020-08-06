---
title: 파일이 나 어셈블리 &#39;b77a5c561934e089, Version = 3.5.0.0, Culture = 중립, PublicKeyToken =&#39; 또는 해당 종속성 중 하나를 로드할 수 없습니다. 시스템은 지정된 파일을 찾을 수 없습니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f9eed7ad90c1e720d07c714e351c24ae6657717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653581"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a><span data-ttu-id="3f544-104">파일이 나 어셈블리 &#39;b77a5c561934e089, Version = 3.5.0.0, Culture = 중립, PublicKeyToken =&#39; 또는 해당 종속성 중 하나를 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-104">Could not load file or assembly &#39;Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089&#39; or one of its dependencies.</span></span> <span data-ttu-id="3f544-105">시스템은 지정된 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-105">The system cannot find the file specified.</span></span>
  <span data-ttu-id="3f544-106">SharePoint용 PowerPivot이 설치된 SharePoint 2010 환경에서는 데이터 피드 내보내기를 시도할 때 시스템에 필요한 Microsoft ADO.NET Data Services 버전이 없으면 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-106">In SharePoint 2010 environments that have PowerPivot for SharePoint, this error will occur if you attempt a data feed export and the system is missing the required version of Microsoft ADO.NET Data Services.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3f544-107">세부 정보</span><span class="sxs-lookup"><span data-stu-id="3f544-107">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f544-108">적용 대상</span><span class="sxs-lookup"><span data-stu-id="3f544-108">Applies to</span></span>|<span data-ttu-id="3f544-109">SharePoint용 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="3f544-109">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="3f544-110">제품 버전</span><span class="sxs-lookup"><span data-stu-id="3f544-110">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="3f544-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f544-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="3f544-112">원인</span><span class="sxs-lookup"><span data-stu-id="3f544-112">Cause</span></span>|<span data-ttu-id="3f544-113">ADO.NET Data Services 3.5 SP1이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-113">ADO.NET Data Services 3.5 SP1 was not found.</span></span>|  
|<span data-ttu-id="3f544-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="3f544-114">Message Text</span></span>|<span data-ttu-id="3f544-115">파일이나 어셈블리 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' 또는 여기에 종속되어 있는 파일이나 어셈블리 중 하나를 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-115">Could not load file or assembly 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.</span></span> <span data-ttu-id="3f544-116">시스템에서 지정한 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-116">The system cannot find the file specified</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3f544-117">설명</span><span class="sxs-lookup"><span data-stu-id="3f544-117">Explanation</span></span>  
 <span data-ttu-id="3f544-118">SharePoint 2010에는 SharePoint 목록을 XML 데이터 피드로 내보내는 데 사용할 수 있는 데이터 피드로 내보내기 단추가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-118">SharePoint 2010 includes an Export as Data Feed button that you can use to export a SharePoint list as an XML data feed.</span></span> <span data-ttu-id="3f544-119">또한 SharePoint 모드의 Reporting Services와 SharePoint용 PowerPivot은 모두 ADO.NET Data Services가 필요한 데이터 피드 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-119">In addition, both Reporting Services in SharePoint mode and PowerPivot for SharePoint support data feed features that require ADO.NET Data Services.</span></span>  
  
 <span data-ttu-id="3f544-120">ADO.NET Data Services가 설치되어 있지 않으면 데이터 피드를 요청할 때 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-120">If ADO.NET Data Services is not installed, this error will occur when you request a data feed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3f544-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="3f544-121">User Action</span></span>  
  
1.  <span data-ttu-id="3f544-122">SharePoint 2010에 대 한 하드웨어 및 소프트웨어 요구 사항 설명서 [하드웨어 및 소프트웨어 요구 사항 확인 (SharePoint 2010) ()](https://go.microsoft.com/fwlink/?LinkId=169734) 으로 이동 https://go.microsoft.com/fwlink/?LinkId=169734) 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-122">Go to the hardware and software requirements documentation for SharePoint 2010, [Determine Hardware and Software Requirements (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) (https://go.microsoft.com/fwlink/?LinkId=169734).</span></span>  
  
2.  <span data-ttu-id="3f544-123">**소프트웨어 필수 구성 요소 설치**에서 현재 사용 중인 운영 체제(Windows Server 2008 SP2 또는 Windows Server 2008 R2)에 맞는 ADO.NET Data Services 3.5의 링크를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-123">In **Installing software prerequisites**, find the link for ADO.NET Data Services 3.5 that corresponds to the operating system you are using.</span></span>  
  
3.  <span data-ttu-id="3f544-124">링크를 클릭하여 서비스를 설치하는 설치 프로그램을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f544-124">Click the link and run the setup program that installs the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f544-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3f544-125">See Also</span></span>  
 [<span data-ttu-id="3f544-126">SharePoint에 PowerPivot 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="3f544-126">Deploy PowerPivot Solutions to SharePoint</span></span>](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
