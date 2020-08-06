---
title: 링크 선택 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a89a555d-efa3-45d6-951e-db78ec6a2c8e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc40fe726555babee8d9940e198a93577bd6a09f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648862"
---
# <a name="choose-link-page-report-manager"></a><span data-ttu-id="0b0d4-102">링크 선택 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="0b0d4-102">Choose Link Page (Report Manager)</span></span>
  <span data-ttu-id="0b0d4-103">링크 선택 페이지를 사용하여 현재 선택한 링크된 보고서의 기반이 되는 다른 보고서를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-103">Use the Choose Link page to choose a different report upon which to base the currently selected linked report.</span></span> <span data-ttu-id="0b0d4-104">링크된 보고서는 보고서 서버에 이미 게시된 다른 보고서를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-104">Linked reports are based on other reports already published to a report server.</span></span> <span data-ttu-id="0b0d4-105">링크된 보고서는 기본 보고서의 레이아웃과 데이터를 사용하지만 별도의 속성 페이지가 있으므로 매개 변수 속성, 보안 설정, 이름, 설명 및 위치를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-105">A linked report uses the layout and data of the base report, but has separate property pages so that you can customize parameter properties, security settings, name, description, and location.</span></span>  
  
 <span data-ttu-id="0b0d4-106">링크 선택 페이지를 통해 링크된 보고서와 함께 사용할 다른 게시된 보고서를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-106">Through the Choose Link page, you can choose a different published report to use with the linked report.</span></span> <span data-ttu-id="0b0d4-107">링크된 보고서의 다른 설정(예: 보안 및 매개 변수 설정)은 링크 정보를 변경해도 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-107">Other settings of the linked report (such as security and parameter settings) are unaffected by changes to the link information.</span></span> <span data-ttu-id="0b0d4-108">보고서 서버는 선택 항목의 유효성을 검사하지 않으므로 링크된 보고서에 지정한 것과 동일한 매개 변수가 있는 보고서를 선택하도록 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-108">The report server will not validate your selection, so be sure to choose a report that has the same parameters as those you specified on the linked report.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="0b0d4-109">탐색</span><span class="sxs-lookup"><span data-stu-id="0b0d4-109">Navigation</span></span>  
 <span data-ttu-id="0b0d4-110">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-choose-link-page"></a><span data-ttu-id="0b0d4-111">링크 선택 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="0b0d4-111">To open the Choose Link page</span></span>  
  
1.  <span data-ttu-id="0b0d4-112">보고서 관리자를 열고 변경할 링크된 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-112">Open Report Manager, and locate the linked report you want to change.</span></span>  
  
2.  <span data-ttu-id="0b0d4-113">링크된 보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-113">Hover over the linked report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="0b0d4-114">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="0b0d4-115">링크된 보고서의 **일반** 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-115">This opens the **General** properties page for the linked report.</span></span>  
  
4.  <span data-ttu-id="0b0d4-116">속성 페이지의 **일반** 탭에서 **링크 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-116">On the **General** tab, on the properties page, click **Change Link**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0b0d4-117">옵션</span><span class="sxs-lookup"><span data-stu-id="0b0d4-117">Options</span></span>  
 <span data-ttu-id="0b0d4-118">**위치**</span><span class="sxs-lookup"><span data-stu-id="0b0d4-118">**Location**</span></span>  
 <span data-ttu-id="0b0d4-119">폴더 경로와 보고서 이름을 포함한 게시된 보고서의 전체 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-119">Specify the full name of the published report, including the folder path and report name.</span></span> <span data-ttu-id="0b0d4-120">보고서의 전체 이름을 입력하거나 트리 뷰를 사용하여 원하는 보고서로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-120">You can type the full name of the report or use the tree view to navigate to the report you want to use.</span></span>  
  
 <span data-ttu-id="0b0d4-121">**트리 보기**</span><span class="sxs-lookup"><span data-stu-id="0b0d4-121">**Tree view**</span></span>  
 <span data-ttu-id="0b0d4-122">보고서 서버 폴더 계층 구조의 모든 폴더를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-122">Shows all of the folders in the report server folder hierarchy.</span></span> <span data-ttu-id="0b0d4-123">트리 뷰를 사용하여 **위치** 필드를 입력하려면 보고서 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b0d4-123">To use the tree view to fill in the **Location** field, click the name of the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b0d4-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b0d4-124">See Also</span></span>  
 <span data-ttu-id="0b0d4-125">[일반 속성 페이지, 보고서 &#40;보고서 관리자&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0b0d4-125">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="0b0d4-126">[새 링크 된 보고서 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0b0d4-126">[New Linked Report Page &#40;Report Manager&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md) </span></span>  
 [<span data-ttu-id="0b0d4-127">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="0b0d4-127">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
