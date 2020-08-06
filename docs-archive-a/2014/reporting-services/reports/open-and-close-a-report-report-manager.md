---
title: 보고서 열기 및 닫기(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- opening reports
- closing reports
- reports [Reporting Services], opening
ms.assetid: a9db1caf-1e7d-41ee-9aed-e09fd0712f9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae9da3f95b7d754d16648e6b6a78ddfa39a499c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648285"
---
# <a name="open-and-close-a-report-report-manager"></a><span data-ttu-id="c0d72-102">보고서 열기 및 닫기(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="c0d72-102">Open and Close a Report (Report Manager)</span></span>
  <span data-ttu-id="c0d72-103">보고서 관리자를 사용하여 보고서 서버에 게시된 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-103">You can use Report Manager to view reports that have been published to a report server.</span></span> <span data-ttu-id="c0d72-104">기본적으로 모든 보고서는 HTML로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-104">By default, all reports open in HTML.</span></span> <span data-ttu-id="c0d72-105">보고서가 열린 후 다른 애플리케이션 형식으로 내보내어 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-105">After a report is open, you can export it to view it in other application formats.</span></span> <span data-ttu-id="c0d72-106">보고서에 대화형 기능이 포함되어 있거나 보고서가 대화형 데이터를 포함한 보고서 작성기 보고서인 경우 해당 링크를 클릭하여 추가 보고서 또는 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-106">If the report contains interactive features or if it is a Report Builder report that contains interactive data, you can click the links to view additional reports or data.</span></span>  
  
### <a name="to-view-a-report"></a><span data-ttu-id="c0d72-107">보고서를 보려면</span><span class="sxs-lookup"><span data-stu-id="c0d72-107">To view a report</span></span>  
  
1.  <span data-ttu-id="c0d72-108">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-108">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="c0d72-109">폴더에서 직접 찾아보거나 이름으로 검색하여 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-109">Find a report by browsing folders or searching for a report by name.</span></span> <span data-ttu-id="c0d72-110">**내용** 페이지에서 폴더 이름이나 폴더 아이콘을 클릭하여 폴더 내용을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-110">Browse folder contents by clicking a folder name or folder icon in the **Contents** page.</span></span> <span data-ttu-id="c0d72-111">페이지 맨 위에 있는 **검색 대상** 입력란에 보고서 이름 전체 또는 일부를 입력하여 보고서를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-111">Search for a report by typing all or part of the report name in the **Search for** text box at the top of the page.</span></span>  
  
3.  <span data-ttu-id="c0d72-112">보고서를 보려면 보고서 이름이나 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-112">To view a report, click a report name or an icon.</span></span> <span data-ttu-id="c0d72-113">다음 아이콘은 보고서를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-113">The following icon indicates a report:</span></span>  
  
     <span data-ttu-id="c0d72-114">![보고서 아이콘](../media/hlp-16doc.gif "보고서 아이콘")</span><span class="sxs-lookup"><span data-stu-id="c0d72-114">![Report icon](../media/hlp-16doc.gif "Report icon")</span></span>  
  
     <span data-ttu-id="c0d72-115">일부 보고서의 경우 사용자 이름 및 암호 또는 매개 변수 값을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-115">Some reports require you to provide either a user name and password or a parameter value</span></span>  
  
4.  <span data-ttu-id="c0d72-116">보고서를 닫으려면 보고서 관리자를 닫거나 **뒤로** 단추 또는 페이지 맨 위의 폴더 링크를 클릭하여 다른 페이지 또는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-116">To close the report, close Report Manager or browse to another page or folder (for example, by clicking the **Back** button or clicking a folder link at the top of the page).</span></span>  
  
     <span data-ttu-id="c0d72-117">보고서를 닫아도 브라우저 캐시에서 보고서가 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-117">Closing a report does not remove it from the browser cache.</span></span> <span data-ttu-id="c0d72-118">보고서와의 연결을 끊으려면 브라우저를 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0d72-118">You must close the browser to disconnect the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d72-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0d72-119">See Also</span></span>  
 <span data-ttu-id="c0d72-120">[보고서 작성기 및 SSRS &#40;보고서 및 기타 항목 검색&#41;](../report-builder/searching-for-reports-and-other-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c0d72-120">[Searching for Reports and Other Items &#40;Report Builder  and SSRS&#41;](../report-builder/searching-for-reports-and-other-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c0d72-121">[내용 페이지 &#40;보고서 관리자&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c0d72-121">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="c0d72-122">[보고서 작성기 및 SSRS &#40;보고서 찾기, 보기 및 관리 &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c0d72-122">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c0d72-123">보고서 서버 콘텐츠 관리&#40;SSRS 기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="c0d72-123">Report Server Content Management &#40;SSRS Native Mode&#41;</span></span>](../report-server/report-server-content-management-ssrs-native-mode.md)  
  
  
