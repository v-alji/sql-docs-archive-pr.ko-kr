---
title: 옵션 (쿼리 결과-SQL Server-텍스트 페이지로 결과 생성) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToText
ms.assetid: 2ccbdf17-e14f-42f1-a836-ca999a3432c9
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ece458e4bab9a57cb6692d4ac6dfdf2e8f4bd22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734403"
---
# <a name="options-query-results-sql-server-results-to-text-page"></a><span data-ttu-id="3c5ed-102">옵션 (쿼리 결과-SQL Server-텍스트 페이지로 결과 생성)</span><span class="sxs-lookup"><span data-stu-id="3c5ed-102">Options (Query Results-SQL Server-Results to Text Page)</span></span>
  <span data-ttu-id="3c5ed-103">이 페이지를 사용하여 쿼리 결과 집합을 텍스트 형식으로 표시하는 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-103">Use this page to specify the options for displaying a query result set in text format.</span></span> <span data-ttu-id="3c5ed-104">이러한 옵션의 변경 내용은 새로운 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 쿼리에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-104">Changes to these options are applied only to new [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="3c5ed-105">현재 쿼리에 대 한 옵션을 변경 하려면 **쿼리 메뉴에서** **쿼리 옵션** 을 클릭 하거나 쿼리 창에서 마우스 오른쪽 단추 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 를 클릭 한 다음 **쿼리 옵션**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-105">To change the options for the current queries, click **Query Options** on the **Query** menu, or right-click in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window, and select **Query Options**.</span></span> <span data-ttu-id="3c5ed-106">**쿼리 옵션** 대화 상자의 **결과**에서 **텍스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-106">In the **Query Options** dialog box, under **Results**, click **Text**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="3c5ed-107">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="3c5ed-107">UI element list</span></span>  
 <span data-ttu-id="3c5ed-108">**출력 형식**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-108">**Output format**</span></span>  
 <span data-ttu-id="3c5ed-109">기본적으로 결과에 공백을 채워 만든 열에 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-109">By default the output is displayed in columns created by padding the results with spaces.</span></span> <span data-ttu-id="3c5ed-110">이외에 쉼표, 탭 또는 공백을 사용하여 열을 구분하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-110">Other options are to use commas, tabs, or spaces to separate columns.</span></span> <span data-ttu-id="3c5ed-111">**사용자 지정 구분 기호** 입력란에 다른 구분 문자를 지정하려면 이 드롭다운 목록에서 **사용자 지정 구분 기호** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-111">Select **Custom delimiter** from this drop-down list to specify a different delimiting character in the **Custom delimiter** text box.</span></span>  
  
 <span data-ttu-id="3c5ed-112">**사용자 지정 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-112">**Custom delimiter**</span></span>  
 <span data-ttu-id="3c5ed-113">열을 구분할 문자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-113">Specify the character of your choice to separate columns.</span></span> <span data-ttu-id="3c5ed-114">이 입력란은 **출력 형식** 드롭다운 목록 상자에서 사용자 지정 구분 기호를 클릭한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-114">This text box is available only if you clicked Custom delimiter in the **Output format** drop-down list box.</span></span>  
  
 <span data-ttu-id="3c5ed-115">**결과 집합에 열 머리글 포함**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-115">**Include column headers in the result set**</span></span>  
 <span data-ttu-id="3c5ed-116">각 열에 열 제목을 붙이지 않으려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-116">Clear this check box if you do not want each column labeled with a column title.</span></span>  
  
 <span data-ttu-id="3c5ed-117">**결과 집합에 쿼리 포함**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-117">**Include the query in the result set**</span></span>  
 <span data-ttu-id="3c5ed-118">결과 창에서 실행되고 있는 쿼리의 텍스트를 쿼리 결과 앞에 표시하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-118">Select this check box to include the text of the query that is running in the results pane before the results of the query.</span></span>  
  
 <span data-ttu-id="3c5ed-119">**결과를 받는 대로 스크롤**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-119">**Scroll as results are received**</span></span>  
 <span data-ttu-id="3c5ed-120">결과 집합 맨 아래의 가장 최근에 반환된 레코드에 포커스를 표시하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-120">Select this check box to keep the display focus on the most recently returned records at the end of the results set.</span></span> <span data-ttu-id="3c5ed-121">받은 첫 번째 행에 포커스를 표시하려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-121">Clear this check box to keep the display focus on the first rows received.</span></span>  
  
 <span data-ttu-id="3c5ed-122">**숫자 값 오른쪽 맞춤**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-122">**Right align numeric values**</span></span>  
 <span data-ttu-id="3c5ed-123">숫자 값을 열 오른쪽에 맞추려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-123">Select this check box to align numeric values to the right of the column.</span></span> <span data-ttu-id="3c5ed-124">이렇게 하면 고정 소수 자릿수를 가진 숫자를 쉽게 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-124">This can make it easier to review numbers with a fixed number of decimal places.</span></span>  
  
 <span data-ttu-id="3c5ed-125">**쿼리 실행 후 결과 삭제**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-125">**Discard result after query executes**</span></span>  
 <span data-ttu-id="3c5ed-126">쿼리 창의 결과 창에 쿼리 결과를 표시한 후 삭제하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-126">Select this check box to discard the query results after they are displayed in the results pane of the query window.</span></span>  
  
 <span data-ttu-id="3c5ed-127">**별도의 탭에 결과 표시**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-127">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="3c5ed-128">쿼리 문서 창의 아래쪽 대신 새로운 문서 창에 결과 집합을 표시하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-128">Select this check box to display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="3c5ed-129">**쿼리 실행 후 결과 탭으로 전환**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-129">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="3c5ed-130">자동으로 화면 포커스를 결과 집합에 두려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-130">Select this check box to automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="3c5ed-131">**각 열에 표시할 최대 문자 수**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-131">**Maximum number of characters displayed in each column**</span></span>  
 <span data-ttu-id="3c5ed-132">기본값은 256자입니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-132">This value defaults to 256.</span></span> <span data-ttu-id="3c5ed-133">이보다 큰 결과 집합을 잘리지 않게 표시하려면 값을 높입니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-133">Increase this value to display larger result sets without truncation.</span></span> <span data-ttu-id="3c5ed-134">최대값은 8,192입니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-134">The maximum value is 8,192.</span></span>  
  
 <span data-ttu-id="3c5ed-135">**기본값으로 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="3c5ed-135">**Reset to Default**</span></span>  
 <span data-ttu-id="3c5ed-136">이 페이지의 모든 값을 원래 기본값으로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c5ed-136">Resets all values on this page to the original default values.</span></span>  
  
  
