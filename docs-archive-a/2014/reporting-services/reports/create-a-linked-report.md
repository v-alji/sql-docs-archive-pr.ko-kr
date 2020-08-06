---
title: 링크된 보고서 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed5e70c9ff8179ae05186685e21303693fc9aed7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652565"
---
# <a name="create-a-linked-report"></a><span data-ttu-id="961ce-102">링크된 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="961ce-102">Create a Linked Report</span></span>
  <span data-ttu-id="961ce-103">링크된 보고서는 기존 보고서에 대한 액세스 지점을 제공하는 보고서 서버 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-103">A linked report is a report server item that provides an access point to an existing report.</span></span> <span data-ttu-id="961ce-104">개념적으로 링크된 보고서는 프로그램을 실행하거나 파일을 열 때 사용하는 프로그램 바로 가기와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-104">Conceptually, it is similar to a program shortcut that you use to run a program or open a file.</span></span>

 <span data-ttu-id="961ce-105">링크된 보고서는 기존 보고서에서 파생되며 원본 보고서의 정의를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-105">A linked report is derived from an existing report and retains the original's report definition.</span></span> <span data-ttu-id="961ce-106">또한 항상 원본 보고서의 보고서 레이아웃과 데이터 원본 속성을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-106">A linked report always inherits report layout and data source properties of the original report.</span></span> <span data-ttu-id="961ce-107">보안, 매개 변수, 위치, 구독 및 일정을 비롯한 다른 모든 속성 및 설정은 원본 보고서와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-107">All other properties and settings can be different from those of the original report, including security, parameters, location, subscriptions, and schedules.</span></span>

 <span data-ttu-id="961ce-108">기존 보고서의 다른 버전을 추가로 만들려는 경우에 링크된 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-108">You can create a linked report when you want to create additional versions of an existing report.</span></span> <span data-ttu-id="961ce-109">예를 들어 한 지역의 판매 보고서를 사용하여 모든 판매 지역에 대한 지역별 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-109">For example, you could use a single regional sales report to create region-specific reports for all of your sales territories.</span></span>

 <span data-ttu-id="961ce-110">링크된 보고서는 일반적으로 매개 변수가 있는 보고서를 기반으로 하지만 매개 변수가 있는 보고서가 반드시 필요하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-110">Although linked reports are typically based on parameterized reports, a parameterized report is not required.</span></span> <span data-ttu-id="961ce-111">기존 보고서를 다른 설정으로 배포하고자 할 때마다 링크된 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-111">You can create linked reports whenever you want to deploy an existing report with different settings.</span></span>

### <a name="to-create-a-linked-report"></a><span data-ttu-id="961ce-112">링크된 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="961ce-112">To create a linked report</span></span>

1.  <span data-ttu-id="961ce-113">보고서 관리자에서 링크하려는 보고서가 있는 폴더로 이동한 후 옵션 메뉴를 열고 **링크된 보고서 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-113">In Report Manager, navigate to the folder containing the report that you want to link to, and then open the options menu can click **Create Linked Report**.</span></span>

2.  <span data-ttu-id="961ce-114">새 링크된 보고서의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-114">Type a name for the new linked report.</span></span> <span data-ttu-id="961ce-115">설명을 입력합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="961ce-115">Optionally type a description.</span></span>

3.  <span data-ttu-id="961ce-116">보고서를 다른 폴더에 만들려면 **위치 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-116">To select a different folder for the report, click **Change Location**.</span></span> <span data-ttu-id="961ce-117">사용할 폴더를 클릭하거나 **위치** 상자에 폴더 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-117">Click the folder you want to use, or type the folder name in the **Location** box.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)] <span data-ttu-id="961ce-118">다른 폴더를 선택하지 않으면 현재 폴더(기반이 되는 보고서가 저장되어 있는 폴더)에 링크된 보고서가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-118">If you do not select a different folder, the linked report is created in the current folder (where the report it is based on is stored).</span></span>

4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] <span data-ttu-id="961ce-119">링크된 보고서가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-119">The linked report opens.</span></span>

     <span data-ttu-id="961ce-120">링크된 보고서의 아이콘은 보고서 서버가 관리하는 다른 항목의 아이콘과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-120">A linked report's icon differs from other items managed by a report server.</span></span> <span data-ttu-id="961ce-121">다음 아이콘은 링크된 보고서를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="961ce-121">The following icon indicates a linked report:</span></span>

     <span data-ttu-id="961ce-122">![링크된 보고서 아이콘](../media/hlp-16linked.gif "링크된 보고서 아이콘")</span><span class="sxs-lookup"><span data-stu-id="961ce-122">![Linked report icon](../media/hlp-16linked.gif "Linked report icon")</span></span>

## <a name="see-also"></a><span data-ttu-id="961ce-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="961ce-123">See Also</span></span>
 <span data-ttu-id="961ce-124">[새 링크 된 보고서 &#40;페이지](../new-linked-report-page-report-manager.md) [&#41;보고서 관리자 &#40;보고서를 열고 닫습니다](../reports/open-and-close-a-report-report-manager.md) . 보고서 관리자&#41;&#40;속성 페이지 [보고서 관리자&#41;&#40;](../choose-item-location-page-report-manager.md) [일반 속성 페이지, 보고서 보고서 관리자&#41;](../general-properties-page-reports-report-manager.md) Reporting Services &#40;[개념&#41;ssrs](../reporting-services-concepts-ssrs.md) [기본 모드](../report-manager-ssrs-native-mode.md) 보고서 관리자 &#40;</span><span class="sxs-lookup"><span data-stu-id="961ce-124">[Open and Close a Report &#40;Report Manager&#41;](../reports/open-and-close-a-report-report-manager.md) [New Linked Report Page &#40;Report Manager&#41;](../new-linked-report-page-report-manager.md) [Choose Item Location Page &#40;Report Manager&#41;](../choose-item-location-page-report-manager.md) [General Properties Page, Reports &#40;Report Manager&#41;](../general-properties-page-reports-report-manager.md) [Reporting Services Concepts &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md) [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md)</span></span>


