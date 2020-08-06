---
title: 데이터 원본 및 보고서 게시 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing data sources [Reporting Services]
- publishing reports [Reporting Services]
- data sources [Reporting Services], managing
ms.assetid: 3a740f8a-1060-4ec3-938b-2305b6887ebd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 941362afde1cfe5dd3d235c9f243fb17875adadc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729036"
---
# <a name="publishing-data-sources-and-reports"></a><span data-ttu-id="06e85-102">데이터 원본 및 보고서 게시</span><span class="sxs-lookup"><span data-stu-id="06e85-102">Publishing Data Sources and Reports</span></span>
  <span data-ttu-id="06e85-103">보고서를 게시하기 전에 미리 보기를 수행하여 보고서가 실행되었을 때의 모습을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-103">Before publishing your report, you should preview the report to see how it will look when it is run.</span></span> <span data-ttu-id="06e85-104">만족스러운 결과가 나올 때까지 디자인을 계속 다듬을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-104">You can continue to refine the design until you are satisfied with the results.</span></span>  
  
 <span data-ttu-id="06e85-105">보고서를 디자인하고 테스트한 후 다른 사람과 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-105">After you design and test your report, you may want to share it with other individuals.</span></span> <span data-ttu-id="06e85-106">보고서를 공유하려면 보고서를 보고서 서버 또는 SharePoint 사이트에 게시 또는 *배포*해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-106">To share your report, you need to publish, or *deploy*, it to a report server or SharePoint site.</span></span> <span data-ttu-id="06e85-107">보고서를 게시하면 보고서 서버나 SharePoint 사이트에 대한 사용 권한이 있는 사용자가 이 보고서를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-107">After it has been published, individuals who have permissions to the report server or the SharePoint site can run your report.</span></span> <span data-ttu-id="06e85-108">또한 보고서 서버에 대한 관리자 권한이 있는 사람은 정기적으로 보고서가 업데이트되고 사용자에게 전송될 수 있도록 보고서에 대한 구독을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-108">In addition, a person with administrator permissions on the report server can create subscriptions to your report so that the report can be updated and sent to users on a regular schedule.</span></span>  
  
 <span data-ttu-id="06e85-109">공유 데이터 원본을 사용하여 보고서를 만든 경우 보고서와 같은 위치에 이 공유 데이터 원본을 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-109">If you used a shared data source to create your report, you need to publish it to the same location as the report.</span></span> <span data-ttu-id="06e85-110">보고서와 마찬가지로 공유 데이터 원본은 보고서 서버에서 별도로 관리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-110">Like reports, shared data sources can be managed separately on the report server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06e85-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="06e85-111">In This Section</span></span>  
 [<span data-ttu-id="06e85-112">보고서 미리 보기</span><span class="sxs-lookup"><span data-stu-id="06e85-112">Previewing Reports</span></span>](previewing-reports.md)  
 <span data-ttu-id="06e85-113">보고서를 게시하기 전에 미리 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-113">Describes how to preview a report before you publish it.</span></span>  
  
 [<span data-ttu-id="06e85-114">보고서 서버에 보고서 게시</span><span class="sxs-lookup"><span data-stu-id="06e85-114">Publishing Reports to a Report Server</span></span>](publishing-reports-to-a-report-server.md)  
 <span data-ttu-id="06e85-115">보고서를 보고서 서버에 게시하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-115">Describes how to publish a report to a report server.</span></span>  
  
 [<span data-ttu-id="06e85-116">SharePoint 모드의 보고서 서버에 게시된 보고서 항목에 대한 URL 예&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="06e85-116">URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;</span></span>](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)  
 <span data-ttu-id="06e85-117">보고서를 SharePoint 사이트에 게시하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="06e85-117">Describes how to publish a report to a SharePoint site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e85-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06e85-118">See Also</span></span>  
 <span data-ttu-id="06e85-119">[Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="06e85-119">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="06e85-120">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06e85-120">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="06e85-121">[페이지 레이아웃 및 렌더링 &#40;보고서 작성기 및 SSRS&#41;](../report-design/page-layout-and-rendering-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06e85-121">[Page Layout and Rendering &#40;Report Builder and SSRS&#41;](../report-design/page-layout-and-rendering-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="06e85-122">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06e85-122">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="06e85-123">[보고서 작성기 및 SSRS &#40;보고서 찾기, 보기 및 관리 &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06e85-123">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="06e85-124">[보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="06e85-124">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="06e85-125">보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="06e85-125">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-reports-report-builder-and-ssrs.md)  
  
  
