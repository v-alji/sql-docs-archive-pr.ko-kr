---
title: 보고서 작성기 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 32be8fcc-e87d-4c45-a644-dff45776a981
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dae43dd86cd6b02c81f0fc90a05292458eb87200
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732332"
---
# <a name="report-builder-ssrs"></a><span data-ttu-id="ce8e2-102">보고서 작성기(SSRS)</span><span class="sxs-lookup"><span data-stu-id="ce8e2-102">Report Builder (SSRS)</span></span>
  <span data-ttu-id="ce8e2-103">보고서 작성기는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Microsoft Office 환경에서 작업하는 것을 선호하는 비즈니스 사용자를 위한 보고서 제작 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-103">Report Builder is a report authoring environment for business users who prefer to work in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office environment.</span></span> <span data-ttu-id="ce8e2-104">보고서를 작성할 때는 데이터를 가져올 위치, 가져올 데이터 및 데이터를 표시할 방법을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-104">When you design a report, you specify where to get the data, which data to get, and how to display the data.</span></span> <span data-ttu-id="ce8e2-105">보고서를 실행하면 보고서 처리기에서 사용자가 지정한 모든 정보를 사용하여 데이터를 검색하고 이를 보고서 레이아웃에 따라 정렬하여 보고서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-105">When you run the report, the report processor takes all the information you have specified, retrieves the data, and combines it with the report layout to generate the report.</span></span>  
  
## <a name="benefits-of-report-builder"></a><span data-ttu-id="ce8e2-106">보고서 작성기의 이점</span><span class="sxs-lookup"><span data-stu-id="ce8e2-106">Benefits of Report Builder</span></span>  
 <span data-ttu-id="ce8e2-107">보고서 작성기를 사용하면 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-107">Report Builder enables you to:</span></span>  
  
-   <span data-ttu-id="ce8e2-108">보고서 작성기 리본을 사용하여 신속하게 보고서에 항목을 추가하고 보고서 데이터 형식을 지정하며 테이블, 차트 및 지도 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-108">Use the Report Builder ribbon to quickly add items your reports, launch table, chart, and map wizards, and format report data.</span></span>  
  
-   <span data-ttu-id="ce8e2-109">보고서에 포함될 데이터를 지정할 수 있는 쿼리 디자이너를 사용하여 기본 제공 데이터 공급자의 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-109">Add data from built-in data providers by using query designers that help you specify which data to include in your report.</span></span>  
  
-   <span data-ttu-id="ce8e2-110">보고서 매개 변수 및 보고서를 읽는 사람이 데이터를 사용자 지정하여 보고서 프레젠테이션을 다양화할 수 있게 하는 기타 대화형 기능을 만들고 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-110">Create and use report parameters and other interactive features that enable your report readers to customize data and vary report presentation.</span></span>  
  
-   <span data-ttu-id="ce8e2-111">기본 제공 필드, 컬렉션, 연산자 및 함수에서 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-111">Create expressions from built-in fields, collections, operators, and functions.</span></span>  
  
-   <span data-ttu-id="ce8e2-112">보고서 서버에서 직접 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-112">Open reports directly from a report server.</span></span>  
  
-   <span data-ttu-id="ce8e2-113">로컬 또는 게시된 공유 데이터 원본 및 공유 데이터 세트를 사용하는 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-113">Preview reports that use local or published shared data sources and shared datasets.</span></span>  
  
-   <span data-ttu-id="ce8e2-114">HTML 또는 인쇄 형식으로 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-114">Preview reports in HTML or print format.</span></span>  
  
-   <span data-ttu-id="ce8e2-115">보고서를 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]등의 기타 파일 형식으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-115">Export reports to other file formats such as [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)].</span></span>  
  
-   <span data-ttu-id="ce8e2-116">보고서 및 관련 항목을 SharePoint 라이브러리, 보고서 서버 또는 로컬 컴퓨터에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-116">Save your report and related items s to a SharePoint library, a report server, or your local computer.</span></span>  
  
 <span data-ttu-id="ce8e2-117">보고서 작성기와 보고서 디자이너는 많은 기능을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-117">Report Builder and Report Designer share many features.</span></span> <span data-ttu-id="ce8e2-118">보고서 작성기에 대한 자세한 내용은 msdn.microsoft.com에서 [보고서 작성기 설명서](https://go.microsoft.com/fwlink/?LinkId=154494) 를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ce8e2-118">For more information about Report Builder, see [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8e2-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce8e2-119">See Also</span></span>  
 <span data-ttu-id="ce8e2-120">[보고서 작성기 액세스 구성](../report-server/configure-report-builder-access.md) </span><span class="sxs-lookup"><span data-stu-id="ce8e2-120">[Configure Report Builder Access](../report-server/configure-report-builder-access.md) </span></span>  
 <span data-ttu-id="ce8e2-121">[Reporting Services 도구](reporting-services-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ce8e2-121">[Reporting Services Tools](reporting-services-tools.md) </span></span>  
 [<span data-ttu-id="ce8e2-122">보고서 디자이너로 보고서 디자인&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ce8e2-122">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
