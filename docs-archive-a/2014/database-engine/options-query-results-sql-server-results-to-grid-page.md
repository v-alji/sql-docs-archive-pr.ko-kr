---
title: 옵션 (쿼리 결과-SQL Server-표 형태로 결과 생성 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToGrid
ms.assetid: f88a0f5c-e800-473b-ae23-c3943de5ed63
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f9cec7e544c295420a9ae2a25e96ea9aa82030b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734407"
---
# <a name="options-query-results-sql-server-results-to-grid-page"></a><span data-ttu-id="42526-102">옵션 (쿼리 결과-SQL Server-표 형태로 결과 생성 페이지)</span><span class="sxs-lookup"><span data-stu-id="42526-102">Options (Query Results-SQL Server-Results to Grid Page)</span></span>
  <span data-ttu-id="42526-103">이 페이지를 사용하여 쿼리 결과 집합을 표 형태로 표시하는 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42526-103">Use this page to specify the options for displaying a query result set in grid format.</span></span> <span data-ttu-id="42526-104">이러한 옵션의 변경 내용은 새로운 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 쿼리에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="42526-104">Changes to these options are applied only to new [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="42526-105">현재 쿼리에 대 한 옵션을 변경 하려면 **쿼리 메뉴에서** **쿼리 옵션** 을 클릭 하거나 쿼리 창에서 마우스 오른쪽 단추를 클릭 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 한 다음 **쿼리 옵션**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-105">To change the options for the current queries, click **Query Options** on the **Query** menu, or right-click in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window and select **Query Options**.</span></span> <span data-ttu-id="42526-106">**쿼리 옵션** 대화 상자 왼쪽 창의 **결과**에서 **표**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-106">In the left pane of the **Query Options** dialog box, under **Results**, click **Grid**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="42526-107">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="42526-107">UI element list</span></span>  
 <span data-ttu-id="42526-108">**결과 집합에 쿼리 포함**</span><span class="sxs-lookup"><span data-stu-id="42526-108">**Include the query in the result set**</span></span>  
 <span data-ttu-id="42526-109">쿼리 출력의 일부로 쿼리 텍스트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-109">Returns the text of the query as part of the query output.</span></span>  
  
 <span data-ttu-id="42526-110">**결과를 복사하거나 저장할 때 열 머리글 포함**</span><span class="sxs-lookup"><span data-stu-id="42526-110">**Include column headers when copying or saving the results**</span></span>  
 <span data-ttu-id="42526-111">결과를 클립보드로 복사하거나 파일로 저장할 때 열 머리글을 포함하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-111">Select this check box to include column headers when results are copied to the clipboard, or saved in a file.</span></span> <span data-ttu-id="42526-112">저장하거나 복사한 결과 데이터에 열 머리글 없이 데이터만 포함시키려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-112">Clear this check box if you want saved or copied result data to have only the data and not the column headings.</span></span>  
  
 <span data-ttu-id="42526-113">**실행 후 결과 삭제**</span><span class="sxs-lookup"><span data-stu-id="42526-113">**Discard results after execution**</span></span>  
 <span data-ttu-id="42526-114">쿼리 결과가 검토 창에 표시되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-114">Prevents query results from being displayed in the reviewing pane.</span></span> <span data-ttu-id="42526-115">실행 후 해당 결과는 곧바로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="42526-115">The results are discarded immediately after execution.</span></span> <span data-ttu-id="42526-116">이 옵션을 지정하면 메모리를 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42526-116">Specifying this option helps save memory.</span></span>  
  
 <span data-ttu-id="42526-117">**별도의 탭에 결과 표시**</span><span class="sxs-lookup"><span data-stu-id="42526-117">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="42526-118">쿼리 문서 창의 아래쪽 대신 새로운 탭에 결과 집합을 표시하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-118">Select this check box to display the result set in a new tab, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="42526-119">**쿼리 실행 후 결과 탭으로 전환**</span><span class="sxs-lookup"><span data-stu-id="42526-119">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="42526-120">쿼리 실행 시 화면 포커스를 결과 창으로 자동으로 이동하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-120">Click to automatically set the screen focus to the results pane upon execution of a query.</span></span>  
  
 <span data-ttu-id="42526-121">**검색한 최대 문자 수**</span><span class="sxs-lookup"><span data-stu-id="42526-121">**Maximum Characters Retrieved**</span></span>  
 <span data-ttu-id="42526-122">**비 XML 데이터**:</span><span class="sxs-lookup"><span data-stu-id="42526-122">**Non XML data**:</span></span>  
  
 <span data-ttu-id="42526-123">1에서 65535 사이의 숫자를 입력하여 각 셀에 표시될 최대 문자 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-123">Enter a number from 1 through 65535 to specify the maximum number of characters that will be displayed in each cell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42526-124">너무 많은 문자를 지정하면 결과 집합의 데이터가 잘려 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42526-124">Specifying a large number of characters may cause data in the result set to appear truncated.</span></span> <span data-ttu-id="42526-125">각 셀에 표시되는 최대 문자 수는 글꼴 크기에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="42526-125">The maximum number of characters displayed in each cell is dependent on the font size.</span></span> <span data-ttu-id="42526-126">이 입력란에 높은 값을 입력하면 큰 결과 집합이 반환될 경우 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 의 메모리 실행 속도가 느려지거나 시스템 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42526-126">When large result sets are returned, a high value in this box can cause [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to run low on memory and hinder system performance.</span></span>  
  
 <span data-ttu-id="42526-127">**XML 데이터**:</span><span class="sxs-lookup"><span data-stu-id="42526-127">**XML data**:</span></span>  
  
 <span data-ttu-id="42526-128">1mb, **2mb 또는** **5mb** **를 선택 합니다**.</span><span class="sxs-lookup"><span data-stu-id="42526-128">Select **1 MB**, **2 MB**, or **5 MB**.</span></span> <span data-ttu-id="42526-129">모든 문자를 검색하려면 **제한 없음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-129">Select **Unlimited** to retrieve all characters.</span></span>  
  
 <span data-ttu-id="42526-130">**기본값으로 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="42526-130">**Reset to Default**</span></span>  
 <span data-ttu-id="42526-131">이 페이지의 모든 값을 원래 기본값으로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42526-131">Resets all values on this page to the original default values.</span></span>  
  
  
