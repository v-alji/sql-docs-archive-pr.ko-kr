---
title: 보고서 게시 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], publishing
- publishing reports [Reporting Services]
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb54308a6b15260d4c336950f231d0ee40836430
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639375"
---
# <a name="publish-reports"></a><span data-ttu-id="c4978-102">보고서 게시</span><span class="sxs-lookup"><span data-stu-id="c4978-102">Publish Reports</span></span>
  <span data-ttu-id="c4978-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서는 프로젝트를 배포하여 보고서 서버 프로젝트의 모든 보고서 및 공유 데이터 원본을 보고서 서버에 게시하거나 단일 보고서를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-103">From[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can publish either all the reports and shared data sources in a Report Server project to a report server by deploying the project, or you can publish a single report.</span></span> <span data-ttu-id="c4978-104">보고서를 게시하기 전에 대상 보고서 서버의 URL을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-104">Before you can publish a report you must specify the URL of the target report server.</span></span> <span data-ttu-id="c4978-105">자세한 내용은 [배포 속성 설정&#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4978-105">For more information, see [Set Deployment Properties &#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md).</span></span>  
  
 <span data-ttu-id="c4978-106">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 버전의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 를 사용하여 [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] 및 [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] 보고서 모두에 대해 열기, 수정, 미리 보기, 저장 및 게시를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-106">You can use the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] version of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to open, modify, preview, save, and publish both [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] and [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] reports.</span></span> <span data-ttu-id="c4978-107">자세한 내용은 [SQL Server Data Tools의 배포 및 버전 지원&#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-107">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).</span></span>  
  
### <a name="to-publish-all-reports-in-a-project"></a><span data-ttu-id="c4978-108">프로젝트의 모든 보고서를 게시하려면</span><span class="sxs-lookup"><span data-stu-id="c4978-108">To publish all reports in a project</span></span>  
  
-   <span data-ttu-id="c4978-109">**빌드** 메뉴에서 \*\*배포 \<report project name> \*\*를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-109">On the **Build** menu, click **Deploy \<report project name>**.</span></span> <span data-ttu-id="c4978-110">또는 솔루션 탐색기에서 보고서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-110">Alternatively, in Solution Explorer, right-click the report project and then click **Deploy**.</span></span> <span data-ttu-id="c4978-111">출력 창에서 게시 프로세스의 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-111">You can view the status of the publishing process in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4978-112">보고서 서버 프로젝트를 배포할 경우 보고서 프로젝트의 공유 데이터 원본도 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-112">When you deploy a Report Server project, the shared data sources in the report project are also deployed.</span></span>  
  
### <a name="to-publish-a-single-report"></a><span data-ttu-id="c4978-113">단일 보고서를 게시하려면</span><span class="sxs-lookup"><span data-stu-id="c4978-113">To publish a single report</span></span>  
  
-   <span data-ttu-id="c4978-114">솔루션 탐색기에서 보고서를 마우스 오른쪽 단추로 클릭한 다음 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-114">In Solution Explorer, right-click the report and then click **Deploy**.</span></span> <span data-ttu-id="c4978-115">출력 창에서 게시 프로세스의 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-115">You can view the status of the publishing process in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c4978-116">보고서를 게시할 경우 보고서가 사용하는 공유 데이터 원본도 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4978-116">When you publish a report, you must also deploy the shared data sources that the report uses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4978-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c4978-117">See Also</span></span>  
 <span data-ttu-id="c4978-118">[데이터 원본 및 보고서 게시](reports/publishing-data-sources-and-reports.md) </span><span class="sxs-lookup"><span data-stu-id="c4978-118">[Publishing Data Sources and Reports](reports/publishing-data-sources-and-reports.md) </span></span>  
 <span data-ttu-id="c4978-119">[보고서 미리 보기](reports/previewing-reports.md) </span><span class="sxs-lookup"><span data-stu-id="c4978-119">[Previewing Reports](reports/previewing-reports.md) </span></span>  
 <span data-ttu-id="c4978-120">[보고서 서버에 보고서 게시](reports/publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="c4978-120">[Publishing Reports to a Report Server](reports/publishing-reports-to-a-report-server.md) </span></span>  
 <span data-ttu-id="c4978-121">[보고서 작성기 및 SSRS &#40;보고서 찾기, 보기 및 관리 &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c4978-121">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c4978-122">보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기</span><span class="sxs-lookup"><span data-stu-id="c4978-122">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
